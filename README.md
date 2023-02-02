# mattermost-delete-posts

This script deletes old posts from all channels in GitLab Mattermost.  Pinned
posts are excluded.  Posts are first soft deleted and later removed from the
database.

The script and the systemd unit files need to be installed on a GitLab server
and run as user mattermost.

## DEPENDENCIES

Requires DBD::Pg.  Install the package libdbd-pg-perl on Debian-based systems
and the package perl-DBD-Pg on RPM-based systems.

## INSTALLATION

Adapt the variables and SQL statements in the script "delete-posts" to your
needs.  Put the script into "/usr/local/sbin" and the systemd unit files into
"/etc/systemd/system".  Enable the timer with "systemctl enable --now
delete-posts.timer".

## LIMITATIONS

Deleting posts from the Mattermost database is officially not supported, but
the Team Edition doesn't provide retention policies.

Reload the Mattermost web interface with Ctrl + Shift + R in order to reflect
the changes.

## LICENSE AND COPYRIGHT

Copyright (C) 2023 Andreas Vögele

This program is free software; you can redistribute and modify it under the
terms of the ISC license.
