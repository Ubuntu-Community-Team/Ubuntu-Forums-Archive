---
title: "No run directory defined for saslauthd, not starting"
date: 2010-01-27
forum: Server Platforms
---

### Post by sbin on 2010-01-27
Here is an update on the initial post (italicized below):

I seem to be missing a subdirectory for saslauthd, and don't know how to remedy that. I applied the instructions in "The Perfect Server - Ubuntu Karmic Koala (Ubuntu 9.10) [ISPConfig 2] - Page 5," [http://how2forge.org/perfect-server-ubuntu-9.10-karmic-koala-ispconfig-2-p5](http://how2forge.org/perfect-server-ubuntu-9.10-karmic-koala-ispconfig-2-p5) , (except that I am using the same commercially issued CA certificate for TLS that I use for my website). I created the directory (mkdir -p /var/spool/postfix/var/run/saslauthd), but there are no files in that directory, nor any links to any files. So here is what I have:
[INDENT][COLOR=Red]root@black:/# /etc/init.d/saslauthd start[/COLOR]
[COLOR=Red] [COLOR=Black]/etc/default/saslauthd: 55: -m: not found[/COLOR][/COLOR]
[COLOR=Red]  [COLOR=Black]* Starting SASL Authentication Daemon saslauthd[/COLOR][/COLOR][COLOR=Black]
[/COLOR] [COLOR=Black]  * No run directory defined for saslauthd, not starting[/COLOR]
[COLOR=Red] root@black:/# cat /etc/default/saslauthd |grep OPTIONS*[/COLOR]
[COLOR=Red][COLOR=Black] MECH_OPTIONS=""[/COLOR][/COLOR]
[COLOR=Red][COLOR=Black] # WARNING: DO NOT SPECIFY THE -d OPTION.[/COLOR][/COLOR]
[COLOR=Red][COLOR=Black] OPTIONS=-c -m /var/spool/postfix/var/run/saslauthd -r[/COLOR][/COLOR]
[COLOR=Red] root@black:/# cd -[/COLOR]
[COLOR=Red] [COLOR=Black]/var/spool/postfix/var/run/saslauthd[/COLOR][/COLOR]
[COLOR=Red] [COLOR=Black]root@black:/var/spool/postfix/var/run/saslauthd# ls -la[/COLOR][/COLOR]
[COLOR=Red][COLOR=Black] total 0[/COLOR][/COLOR]
[COLOR=Red][COLOR=Black] drwxr-xr-x 2 root root  6 2010-01-27 21:53 .[/COLOR][/COLOR]
[COLOR=Red][COLOR=Black] drwxr-xr-x 3 root root 22 2010-01-27 21:51 ..[/COLOR][/COLOR]
[COLOR=Red] [COLOR=Red]root@black:/var/spool/postfix/var/run/saslauthd#[/COLOR][/COLOR]
[/INDENT]Why would this tutorial instruct the user to create an empty directory for files that are needed to run saslauthd? [SIZE=3]What am I missing here?[/SIZE]
[I]

I have a fresh install of Ubuntu Server 9.10 (64-bit), running Postfix, Courier, and the default LAMP stack. Postfix is accepting mail and allowing users imap access, but not allowing smptd sending, as evidenced in the title of this post. Here is some output from the command line:[/I][INDENT][I]root@black:~# service saslauthd restart
/etc/default/saslauthd: 55: -m: not found
 * No run directory defined for saslauthd, cannot stop
/etc/default/saslauthd: 55: -m: not found
 * Starting SASL Authentication Daemon saslauthd
 * No run directory defined for saslauthd, not starting

[/I]  [/INDENT]*And also:*[INDENT][I]root@black:/# find -name saslauth*
./var/lib/update-rc.d/saslauthd
./var/spool/postfix/var/run/saslauthd
./var/spool/postfix/var/run/saslauthd-r
./etc/default/saslauthd
./etc/init.d/saslauthd
./usr/share/man/man8/saslauthd.8.gz
./usr/sbin/saslauthd


[/I]   [/INDENT]*This is a snippet from /etc/postfix/master.cf:*[INDENT][I]#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
[/I] [/INDENT]*I suspect that there is something that I am not grasping about chroot. Any help?*

---

### Post by sbin on 2010-01-29
The solution was to add the missing quotes for /etc/default/saslauthd, line #55: [COLOR=Red][COLOR=Black]OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd -r":popcorn:[/COLOR][/COLOR]

---

