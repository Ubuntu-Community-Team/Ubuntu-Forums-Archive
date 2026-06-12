---
title: "Removing Roxen Web Server"
date: 2010-07-01
forum: Server Platforms
---

### Post by espmartin on 2010-07-01
Hello All,

I need to remove the Roxen web server. I had a fully functional LAMP install, but installed Roxen as a test. Now I need to remove it, but all documentation on their site does not show how to remove it.

So, what do I need to do? I've used the command line, but it still remains...

---

### Post by blomman9 on 2010-08-06
This is taken from the Mac OS X Roxen installation guide:

[SIZE="3"]Roxen files and directories[/SIZE]

Files and directories used for Mac OS X version.

The following directories and files are created when Roxen is installed. To uninstall, remove any of these files and directories as necessary.
[FONT="Courier New"]/etc/roxen/default/[/FONT] – the configuration directory for the default Roxen server configuration. Several server instances can be installed in parallel, in which case each will have a unique configuration directory (e.g. [FONT="Courier New"]/etc/roxen/mysite/[/FONT]).
[FONT="Courier New"]/var/roxen/default/[/FONT] – The data directory for the default Roxen server. It contains the database, site repository, local modules, feed directories, cache directories etc.
[FONT="Courier New"]/var/log/roxen/default/[/FONT] – The log directory for the default Roxen server, including both the access log in Common Log Format as well as the debug log.
[FONT="Courier New"]/var/roxen/default/var/run/default.pid[/FONT] – The process id file for the default Roxen server. [FONT="Courier New"]/etc/hostconfig[/FONT] – Contains the line “ROXEN=-YES-” used for the Startup Items. [FONT="Courier New"]/Library/StartupItems/Roxen/[/FONT] – The script to automatically start Roxen servers. /Applications/Roxen/ – Various helper applications for Roxen. [FONT="Courier New"]/usr/local/lib/roxen-x.y.z-abc/[/FONT] – The binary directory for the Roxen server.
[FONT="Courier New"]/usr/local/lib/roxen/[/FONT] – Helper applications for the Roxen server.
[FONT="Courier New"]/usr/local/bin/roxen[/FONT] – Helper script for the Roxen server.
[FONT="Courier New"]/usr/local/bin/roxen-uninstall[/FONT] – Helper script to uninstall Roxen.
[FONT="Courier New"]/usr/local/bin/roxen-create-server[/FONT] – Script to create new server configurations (typically other configurations than [FONT="Courier New"]/etc/roxen/default/[/FONT]).

By checking and deleting old folders, I hope this'll help get rid of Roxen.

---

