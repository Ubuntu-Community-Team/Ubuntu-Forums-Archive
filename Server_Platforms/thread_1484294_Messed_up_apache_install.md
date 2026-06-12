---
title: "Messed up apache install?"
date: 2010-05-15
forum: Server Platforms
---

### Post by pepijn on 2010-05-15
Hey, 

A question from a noob who is setting up a lamp server (10.04).

I ran the following commands in the folder /var/lib. I should have run them in /var/lib/foswiki to set the access rights.

After that apache2 won't start anymore. My question is: should I  do a reinstall of the server, or did this not affect anything in /var/lib?

I know this is a stupid mistake (i ate my shoe following the incident). But can someone please help me out?


```
find . -type d -print -exec chmod -v 755 {} \;
find data -name '*.txt' -type f -exec chmod -v 644 {} \;
find data pub -name '*,v' -type f -exec chmod -v 444 {} \;
find lib -type f -exec chmod -v 444 {} \;
find locale -type f -exec chmod -v 444 {} \;
find pub -type f -exec chmod -v 644 {} \;
find bin -type f -exec chmod -v 555 {} \;
find bin/logos -type f -exec chmod -v 444 {} \;
find templates -type f -exec chmod -v 444 {} \;
find tools -type f -exec chmod -v 555 {} \;
chmod -v 644 lib/LocalSite.cfg
chmod -v 644 data/.htpasswd
chmod -v 644 data/mime.types
chmod -v 644 bin/LocalLib.cfg.txt bin/.htaccess.txt
chmod -v 444 bin/setlib.cfg
chmod -v 444 tools/extender.pl
chmod -v 444 working/tmp/README working/README working/registration_approvals/README
chmod -v 444 working/work_areas/README
chmod -v 660 working/.htaccess
chmod -v 444 AUTHORS COPYING COPYRIGHT index.html INSTALL.html LICENSE pub-htaccess.txt readme.txt
chmod -v 444 robots.txt root-htaccess.txt subdir-htaccess.txt FoswikiHistory.html
chmod -v 444 foswiki_httpd_conf.txt ReleaseNotes01x00.html
```

Before apache2 was up and running with ssl enabled (no errors), afterward I got this error message:

```
(98)Address already in use: make_sock: could not bind to address 192.29.31.198:80
no listening sockets available, shutting down
Unable to open logs

```

this is the tail of /var/log/apache2/error.log

```
[Fri May 14 19:44:03 2010] [error] Init: Private key not found
[Fri May 14 19:44:03 2010] [error] SSL Library Error: 218710120 error:0D094068:asn1 encoding routines:d2i_ASN1_SET:bad tag
[Fri May 14 19:44:03 2010] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Fri May 14 19:44:03 2010] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
[Fri May 14 19:44:03 2010] [error] SSL Library Error: 218734605 error:0D09A00D:asn1 encoding routines:d2i_PrivateKey:ASN1 lib
[Fri May 14 19:44:42 2010] [info] Init: Seeding PRNG with 656 bytes of entropy
[Fri May 14 19:44:43 2010] [info] Loading certificate & private key of SSL-aware server
[Fri May 14 19:44:43 2010] [info] Init: Requesting pass phrase via builtin terminal dialog

```

btw: I'm not sure if this question should be in beginner talk, if so i'm happy to move it.

---

### Post by pepijn on 2010-05-17
I did some more research on the Foswiki (.org) install. It didn't really mess with anything.

The apache2 error (after reboot) has a different reason. It is described by 'poirot' in this thread:

[http://ubuntuforums.org/archive/index.php/t-774692.html](http://ubuntuforums.org/archive/index.php/t-774692.html)

however, he does not get an answer to his question:

> Thanks guys,

If I understand correctly, the nature of the certificate I create determines the behaviour of apache to some degree. It prevents me from restarting apache unless I have the passphrase. I am fine with this, it seems a sensible security measure.

However, the set up I have is currently for testing and developing so I reboot the machine all the time.

On rebooting, apache used to just work. I could point my browser at [https://localhost/](https://localhost/) and my development system would be presented.

Since the upgrade and the new certificate (which I am beginning to understand) I can't do this, apache seems to be running but corrupted in some way. I need to kill all apache processes before restarting apache each time I reboot.


```
graeme@graeme-home:~$ sudo killall apache2
graeme@graeme-home:~$ sudo /etc/init.d/apache2 restart
```



If I just restart without killing the processes I get this


```
graeme@graeme-home:~$ sudo /etc/init.d/apache2 restart
[sudo] password for graeme:
* Restarting web server apache2
httpd (no pid file) not running
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```
So my problem is minor but irritating, apache seems to lock itself up on reboot. Is this an intentional result of the certificate I have used? Should I simply consider a less secure certificate for development?

Thanks for the help, I am feeling happier already.

It seems to me that this is a serious bug. Apache2 does work, but there is something in the ubuntu server startup that is preventing the input of the pass phrase.

If someone knows a solution to this problem, it would be greatly appreciated!

---

### Post by pepijn on 2010-06-04
Solved in this thread: [http://ubuntuforums.org/showthread.php?t=774692](http://ubuntuforums.org/showthread.php?t=774692)

---

