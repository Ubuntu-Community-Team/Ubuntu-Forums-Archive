---
title: "SELinux breaks cups"
date: 2008-04-10
forum: Server Platforms
---

### Post by irober02 on 2008-04-10
I'm giving ubuntu-8.04-beta-server-amd64 a go on my new home server. It installed fine and mostly running well. Sharing files and (hopefully) a printer via samba is the major task for the server.

I've installed SELinux (learning opportunity) and one outstanding problem is getting cups running. 

When I (re)install cupsys and cupsys-client I get the following:

The following NEW packages will be installed:
  cupsys cupsys-client
0 upgraded, 2 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B/1970kB of archives.
After this operation, 10.5MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package cupsys.
(Reading database ... 30319 files and directories currently installed.)
Unpacking cupsys (from .../cupsys_1.3.7-1ubuntu2_amd64.deb) ...
Selecting previously deselected package cupsys-client.
Unpacking cupsys-client (from .../cupsys-client_1.3.7-1ubuntu2_amd64.deb) ...
Setting up cupsys (1.3.7-1ubuntu2) ...
Unable to find apparmor_parser, installation problem?: Failed.
invoke-rc.d: initscript apparmor, action "force-reload" failed.
 * Starting Common Unix Printing System: cupsd                                                                                           start-stop-daemon: Unable to start /usr/sbin/cupsd: Permission denied (Permission denied)
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 2
Setting up cupsys-client (1.3.7-1ubuntu2) ...

Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

and syslog displays:

Apr 11 10:03:49 tunnelball kernel: [56186.723703] audit(1207874029.018:9): security_compute_sid:  invalid context unconfined_u:system_r:cupsd_t for scontext=unconfined_u:unconfined_r:unconfined_t tcontext=system_u:object_r:cupsd_exec_t tclass=process

Looks like an SELinux problem to me.

I've done quite a bit of web crawling to find a solution. There are a number of parallel experiences but no resolutions. Any suggestions (other than apt-get remove selinux!)?

---

### Post by HermanAB on 2008-04-10
Well, you are lucky if that is the only thing SELinux breaks...

---

### Post by irober02 on 2008-04-19
I'm a glutton for punishment! :-}

Seriously, SE Linux has been adopted at work so this is an opportunity to learn the details...

I've logged a bug about this and temporarilly switched to SELinux permissive mode -I know, I know but I'm keeping an eye on syslog and there are just a few policy problems to resolve and no suspicious activity.

The SE Linux project have reported a fix that is now in the pipeline. Don't know how long it will take to make it to ubuntu/heron. I'm not that fussed until, at least, heron is out of beta -they did give fair warning about beta software.

---

### Post by irober02 on 2008-04-20
Updates over the last few days seem to have fixed this problem. Following the policy packages being updated syslog stopped reporting the selinux errors. I've since put it back into enforcing mode with no major problems. I haven't made tha the boot default yet though.

---

