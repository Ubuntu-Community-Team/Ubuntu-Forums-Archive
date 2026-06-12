---
title: "Nagios3-Ubuntu 8.04"
date: 2009-10-25
forum: Server Platforms
---

### Post by KevKing on 2009-10-25
Followed the install guide at [http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html](http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html) and installed like a dream.  No errors were shown on installation.
I can login at the web interface no problem, but it will only display 2 options.  Home and documentation.  All other menu options come up with internal server error and dont display anything.

Any ideas as to what might be happening or missing?

---

### Post by RurouniAkira on 2010-01-18
Your user does not have the permission... 

Go in /etc/nagios3/cfg.cgi file and add the user that you are using to the allowed for xxxx stuff that you need !

> # SYSTEM/PROCESS INFORMATION ACCESS
# This option is a comma-delimited list of all usernames that
# have access to viewing the Nagios process information as
# provided by the Extended Information CGI (extinfo.cgi).  By
# default, *no one* has access to this unless you choose to
# not use authorization.  You may use an asterisk (*) to
# authorize any user who has authenticated to the web server.

authorized_for_system_information=nagiosadmin



# CONFIGURATION INFORMATION ACCESS
# This option is a comma-delimited list of all usernames that
# can view ALL configuration information (hosts, commands, etc).
# By default, users can only view configuration information
# for the hosts and services they are contacts for. You may use
# an asterisk (*) to authorize any user who has authenticated
# to the web server.

authorized_for_configuration_information=nagios



# SYSTEM/PROCESS COMMAND ACCESS
# This option is a comma-delimited list of all usernames that
# can issue shutdown and restart commands to Nagios via the
# command CGI (cmd.cgi).  Users in this list can also change
# the program mode to active or standby. By default, *no one*
# has access to this unless you choose to not use authorization.
# You may use an asterisk (*) to authorize any user who has
# authenticated to the web server.

authorized_for_system_commands=nagios



# GLOBAL HOST/SERVICE VIEW ACCESS
# These two options are comma-delimited lists of all usernames that
# can view information for all hosts and services that are being
# monitored.  By default, users can only view information
# for hosts or services that they are contacts for (unless you
# you choose to not use authorization). You may use an asterisk (*)
# to authorize any user who has authenticated to the web server.


authorized_for_all_services=nagios
authorized_for_all_hosts=nagios



# GLOBAL HOST/SERVICE COMMAND ACCESS
# These two options are comma-delimited lists of all usernames that
# can issue host or service related commands via the command
# CGI (cmd.cgi) for all hosts and services that are being monitored.
# By default, users can only issue commands for hosts or services
# that they are contacts for (unless you you choose to not use
# authorization).  You may use an asterisk (*) to authorize any
# user who has authenticated to the web server.

authorized_for_all_service_commands=nagios
authorized_for_all_host_commands=nagios 

Cheers !

---

