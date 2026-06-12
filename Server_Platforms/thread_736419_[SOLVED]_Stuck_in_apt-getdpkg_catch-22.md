---
title: "[SOLVED] Stuck in apt-get/dpkg catch-22?"
date: 2008-03-26
forum: Server Platforms
---

### Post by tubezninja on 2008-03-26
Hi folks,

Well, I've really gotten myself into a bind this time.  I did an 'apt-get upgrade' earlier today on my server and saw that an updated version of dovecot was available, so I had it downloaded and installed.   During the install process, I was notified that my local dovecot.conf file differed from the new package, and was asked if I wanted to replace it.  I said "no."

That was mistake #1.

After apt-get did its thing, I got an error stating that a config option in my dovecot.conf file was deprecated.  Knowing now I probably should've replace my config file when I had the chance, I thought that maybe if I uninstall and then reinstall using apt-get I'll be fine.

Unfortunately, that was not the case, as it didn't touch my config file the second time.  So, I tried deleting it.

That was mistake #2.   And now I'm in a spot of bother.

Now, uninstalling dovecot-common, dovecot-imapd or dovecot-pop3d offers up this message:

```
sudo apt-get remove dovecot-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dovecot-common dovecot-imapd dovecot-pop3d
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 6504kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing dovecot-pop3d (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
dpkg: error processing dovecot-imapd (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
dpkg: error processing dovecot-common (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 dovecot-pop3d
 dovecot-imapd
 dovecot-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Okay, fine, I need to reinstall.  So I try that, and then I get:

```
$ sudo apt-get install dovecot-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dovecot-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/3099kB of archives.
After unpacking 0B of additional disk space will be used.
Selecting previously deselected package dovecot-common.
(Reading database ... 24712 files and directories currently installed.)
Preparing to replace dovecot-common 1:1.0.5-1ubuntu2.2 (using .../dovecot-common_1%3a1.0.5-1ubuntu2.2_amd64.deb) ...
invoke-rc.d: initscript dovecot, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript dovecot, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/dovecot-common_1%3a1.0.5-1ubuntu2.2_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Selecting previously deselected package dovecot-imapd.
Preparing to replace dovecot-imapd 1:1.0.5-1ubuntu2.2 (using .../dovecot-imapd_1%3a1.0.5-1ubuntu2.2_amd64.deb) ...
Unpacking replacement dovecot-imapd ...
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: error processing /var/cache/apt/archives/dovecot-imapd_1%3a1.0.5-1ubuntu2.2_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Selecting previously deselected package dovecot-pop3d.
Preparing to replace dovecot-pop3d 1:1.0.5-1ubuntu2.2 (using .../dovecot-pop3d_1%3a1.0.5-1ubuntu2.2_amd64.deb) ...
Unpacking replacement dovecot-pop3d ...
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: error processing /var/cache/apt/archives/dovecot-pop3d_1%3a1.0.5-1ubuntu2.2_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/dovecot-common_1%3a1.0.5-1ubuntu2.2_amd64.deb
 /var/cache/apt/archives/dovecot-imapd_1%3a1.0.5-1ubuntu2.2_amd64.deb
 /var/cache/apt/archives/dovecot-pop3d_1%3a1.0.5-1ubuntu2.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I've done some searching in the forums before posting, and I tried the following remedies:

1.  the -force-yes option
Did'n't work. Exact same error messages.


2. Tried "sudo dpkg --force-remove-reinstreq"  No dice.  I get:

```
 $ sudo dpkg --force-remove-reinstreq --remove dovecot-common
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 24711 files and directories currently installed.)
Removing dovecot-common ...
invoke-rc.d: initscript dovecot, action "stop" failed.
dpkg: error processing dovecot-common (--remove):
 subprocess pre-removal script returned error exit status 1
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dovecot-common

``` 


So it seems like it refuses to install or uninstall, even if I attempt to force it.  And I'm stuck i this catch-22.  I can't uninstall becuase the packages are in a very bad state and I should install them... But I can't install them, either, because, well, the packages are incomplete.

Is there anything else I can try at this point?  Any help would greatly appreciated.

---

### Post by tubezninja on 2008-03-26
Welp, managed to solve the problem myself.  The solution was a bit tedious and rather brute-force, but seems to have worked.

The "scorched-earth" solution: find everything with the name "dovecot" and remove it:

```
sudo apt-get find / -name dovecot
```

Everything that was listed in the output, I put an 'rm -r' in front of.  (Note: Be VERY careful doing this!  You could really mess up a system this way.  I did because, well, I figured I didn't have much else to lose, and was just short of reinstalling from scratch anyway.)

From there, I issued the following commands:

```
sudo dpkg --force-all --purge dovecot-common
sudo dpkg --force-all --purge dovecot-pop3d
sudo dpkg --force-all --purge dovecot-imapd
```

These went without a hitch this time.  Funny how if an installation is only partially broken, dpkg won't help, but if you break the packages quite a bit more, well then it's glad to assist! :)

And lastly, the reinstall:

```
sudo apt-get install dovecot-common dovecot-imapd dovecot-pop3d
```

apt-get did complain about permissions not being right here and then, but then went on to correct them.  All seems to be working again!

In retrospect, this was a drastic move.  Again, I wouldn't recommend anyone deleting files willy-nilly unless they truly had nothing to lose, had backed up all necessary data, and was about to reinstall from scratch if nothing else worked.

---

