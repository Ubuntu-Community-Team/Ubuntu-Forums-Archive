---
title: "Samba fails to start after upgrade to 16.04"
date: 2016-11-14
forum: Server Platforms
---

### Post by elperrillo on 2016-11-14
Hi, I hope anybody can help me with this.

I just upgraded from 12.04 all the way to 16.04 and now samba does not want to start, when I do:

> sudo smb start 

I get the following error:

[FONT=Courier New]
Command 'service' is available in '/usr/sbin/service'
The command could not be located because '/usr/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
service: command not found[/FONT]

However, I am logged in as root.

Any ideas?, thanks in advance.

---

### Post by darkod on 2016-11-14
What do you mean by "logged in as root"? Usually root is disabled in ubuntu, do you have it enabled?

And if you are really running commands as root, don't use sudo in front. That's only for non-root users that have sudo rights.

Also, the service names are smbd and nmbd, and latest ubuntu 16.04 now uses systemd (but the old way still works).

Try something like this (as non-root user):
```
sudo service smbd start
sudo service nmbd start
```

Or the new systemd way:
```
sudo systemctl start smbd.service nmbd.service
```

Which version of samba do you have:
```
samba -V
```

If you did not have it installed from the repositories, it probably didn't even upgrade correctly to the latest samba version available in 16.04. How did you install it back in the 12.04 days?

---

### Post by elperrillo on 2016-11-14
Hi, thank you for your response.

Yes, I am logged in as root. I used to use "sudo" in front of everything I type at the command prompt so that the system does not ask me to type the command again, sudo always works, that is why I do it that way.

If I run both of the commands you gave as another user I get the following:

[FONT=Courier New]administrator@ubuntusrv:~$ sudo service smbd start
smbd start/running, process 3506
administrator@ubuntusrv:~$ sudo service nmbd start
start: Job is already running: nmbd[/FONT]

If I do it with the new "systemd" way, I get:

[FONT=Courier New]Failed to start smbd.service: Unknown unit: smbd.service
See system logs and 'systemctl status smbd.service' for details.
Failed to start nmbd.service: Unknown unit: nmbd.service
See system logs and 'systemctl status nmbd.service' for details.[/FONT]

If I do samba -V, I get:
[FONT=Courier New]
Version 4.3.11-Ubuntu[/FONT]

I do not remember how I installed samba in the first place, I have had this server since version 7 and have been upgrading it for years.

---

### Post by darkod on 2016-11-14
Well, smbd seems to be running. Why do you think samba is not running? Something is not working?

You can also see more running services with:
```
sudo netstat -plunt
```

---

### Post by elperrillo on 2016-11-14
It is not working because I can no longer access my Samba shares. If log in to a Webmin console that I have, it  shows me that I have samba installed and gives me the option to start it but when I do it gives me an error and If I use terminal and try to start it that way it gives me the error I posted and the beginning. I have no idea why it claims it is working when I run those commands as another user other than root. If I run:

> sudo netstat -plunt

It gives me a list of services but no nmbd or smdb 

[FONT=Century Gothic][FONT=Courier New]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State               PID/Program name
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN              1599/perl
tcp        0      0 127.0.0.1:5910          0.0.0.0:*               LISTEN              3009/Xvnc
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN              2229/sshd
tcp        0      0 127.0.0.1:3350          0.0.0.0:*               LISTEN              1665/xrdp-sesman
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN              2109/cupsd
tcp        0      0 0.0.0.0:3389            0.0.0.0:*               LISTEN              1663/xrdp
tcp6       0      0 :::22                   :::*                    LISTEN              2229/sshd
tcp6       0      0 :::631                  :::*                    LISTEN              2109/cupsd
tcp6       0      0 :::3128                 :::*                    LISTEN              1522/(squid-1)
udp        0      0 0.0.0.0:5353            0.0.0.0:*                                   789/avahi-daemon: r
udp        0      0 0.0.0.0:10000           0.0.0.0:*                                   1599/perl
udp        0      0 0.0.0.0:59319           0.0.0.0:*                                   789/avahi-daemon: r
udp        0      0 0.0.0.0:35355           0.0.0.0:*                                   1522/(squid-1)[/FONT][/FONT]

---

### Post by darkod on 2016-11-14
Not being able to access shares is not always directly linked to the service running. In fact, the same happened to me when upgrading from 12.04 to 14.04. When asked I told it to keep my smb.conf but the shares couldn't be accessed after that.

So I purged/reinstalled samba and used the original smb.conf only making small changes and copying my shares section from my smb.conf.

But in your case it's obvious that samba service is not running. Does apt-get report any misconfiguration, or any packages pending configuration maybe?

```
sudo apt-get install -f
```

That should fix any broken dependencies.

You could also try reinstalling samba but before that keep a copy of your smb.conf and any important custom settings because you might need to purge samba in which case it will install the default smb.conf probably.

---

### Post by elperrillo on 2016-11-14
Thank you for your response, I fixed the issue. I actually had two errors on my smb.conf file.

> map to guest = bad user
security = share

were both wrong, the correct values for Ubuntu 16.04 should be:

> map to guest = bad password
security = user

Once I did this, I did a

> sudo apt-get update

and then

> sudo apt-get install samba

and everything was back to normal, I could see all my samba shares and mu CUPS printers.

Again thank you very much for taking the time to help me, you are a great person.

---

### Post by darkod on 2016-11-15
No problem, glad you got it working. Please mark the thread as Solved, you can do that in Thread Tools above the first post.

---

### Post by Morbius1 on 2016-11-15
> Thank you for your response, I fixed the issue. I actually had two errors on my smb.conf file.

[QUOTE]                                                         map to guest = bad user
security = share                      
were both wrong, the correct values for Ubuntu 16.04 should be:

                                                         map to guest = bad password
security = user                      [/QUOTE]
The reason the default Ubuntu smb.conf uses "Bad User" is because of the difference with using "Bad Password". 

Let's say you have this configured with "Bad Password" and you have a share requiring credentials. The client passes the correct user name but makes a typo on the password ( one you created for that user in smbpasswd ) . That user automatically becomes a guest user ( nobody ).

Configured with "Bad User" the client still passes that correct user name but mangled password. That user will be prompted for credentials again until he corrects the password.

"Bad User" and "Bad Password" would have the same affect only if the server has not set up a samba user with a corresponding samba password for that client user.

[COLOR=#0000cd]**EDIT**: Though I might pass along a humorous note on "Bad Password: from man smb.conf:[/COLOR]
> Bad Password - Means user logins with an invalid password are treated as a guest login and mapped into the guest
               account. Note that this can cause problems as it means that any user incorrectly typing their password will be
               silently logged on as "guest" - and will not know the reason they cannot access files they think they should - there
               will have been no message given to them that they got their password wrong. Helpdesk services will hate you if you
               set the map to guest parameter this way :-).

---

### Post by chubbtech on 2016-12-06
I've been getting update errors for months now.  All related to samba it would appear.  here's part of the output from "[COLOR=#000000][FONT=&quot]sudo apt-get install -f"[/FONT][/COLOR]

Setting up samba (2:4.3.11+dfsg-0ubuntu0.16.04.1) ...
Job for smbd.service failed because the control process exited with error code. See "systemctl status smbd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript smbd, action "start" failed.
dpkg: error processing package samba (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of winbind:
 winbind depends on samba (= 2:4.3.11+dfsg-0ubuntu0.16.04.1); however:
  Package samba is not configured yet.


dpkg: error processing package winbind (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnss-winbind:amd64:
 libnss-winbind:amd64 depends on winbind (= 2:4.3.11+dfsg-0ubuntu0.16.04.1); however:
  Package winbind is not configured yet.


dpkg: error processing package libnss-winbind:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-winbind:amd64:
 libpam-winbind:amd64 depends on winbind (= 2:4.3.11+dfsg-0ubuntu0.16.04.1); however:
  Package winbind is not configured yet.


dpkg: error processing package libpam-winbind:amd64 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.23-0ubuntu4) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                      No apport report written because MaxReports is reached already
                                                                                                                    Errors were encountered while processing:
 samba
 winbind
 libnss-winbind:amd64
 libpam-winbind:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

