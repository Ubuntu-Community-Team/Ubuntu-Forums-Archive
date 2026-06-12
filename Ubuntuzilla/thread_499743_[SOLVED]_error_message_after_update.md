---
title: "[SOLVED] error message after update"
date: 2007-07-12
forum: Ubuntuzilla
---

### Post by the.phantom on 2007-07-12
i did the t-bird update from 1.0.5.12 to 2.0.0.4 on my test system without any trouble usiing 4.1.1

on my main computer i had used your old script to update it
(gksudo thunderbird &)
and it said no new updates  and it was also 1.0.5.12

so i used the new script and all went well (kinda)
and now when i launch t-bird i get this message at the bottom of the t-bird window

[IMG]http://rcip.com/mitch/errormsg.jpg[/IMG]
and i did save the terminal messages and it downloaded 1.05.12 and then a bit later downloaded 2.0.4

so this isn't too big a post this is that part, but i have the full log  if needed!!!!!

Suggested packages:
  mozilla-thunderbird-typeaheadfind mozilla-thunderbird-inspector mozilla-firefox
  mozilla-thunderbird-enigmail
The following packages will be upgraded:
  mozilla-thunderbird
1 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 10.8MB of archives.
After unpacking 176kB of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main mozilla-thunderbird 1.5.0.12-0ubuntu0.6.10 [10.8MB]
Fetched 10.8MB in 3m27s (52.0kB/s)                                                                       
Preconfiguring packages ...
(Reading database ... 127914 files and directories currently installed.)
Preparing to replace mozilla-thunderbird 1.5.0.7-0ubuntu1 (using .../mozilla-thunderbird_1.5.0.12-0ubuntu0.6.10_i386.deb) ...
Unpacking replacement mozilla-thunderbird ...
Setting up mozilla-thunderbird (1.5.0.12-0ubuntu0.6.10) ...


A Thunderbird profile has been found at ~/.mozilla-thunderbird. Do you want to make a backup of your Mozilla Thunderbird profile at ~/.mozilla-thunderbird? Note that if you store your email there, this may take quite a bit of disk space. You may wish to check the size of that directory and the amount of free disk space before you answer this question. Make backup? [y/n]: 
Please enter 'y' or 'n': y

Backing up old thunderbird preferences


Downloading Thunderbird archive from the Mozilla site

--20:35:49--  [ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-US/thunderbird-2.0.0.4.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-US/thunderbird-2.0.0.4.tar.gz)
           => `thunderbird-2.0.0.4.tar.gz'
Resolving releases.mozilla.org... 64.50.236.214, 130.239.18.158, 130.239.18.159, ...
Connecting to releases.mozilla.org|64.50.236.214|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR thunderbird-2.0.0.4.tar.gz ... done.
Length: 11,428,434 (11M) (unauthoritative)

100%[==============================================================>] 11,428,434   161.76K/s    ETA 00:00

20:37:02 (154.21 KB/s) - `thunderbird-2.0.0.4.tar.gz' saved [11428434]


Downloading Thunderbird signature from the Mozilla site

--20:37:02--  [ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-US/thunderbird-2.0.0.4.tar.gz.asc](ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-US/thunderbird-2.0.0.4.tar.gz.asc)
           => `thunderbird-2.0.0.4.tar.gz.asc'
Resolving releases.mozilla.org... 64.50.236.214, 130.239.18.158, 130.239.18.159, ...
Connecting to releases.mozilla.org|64.50.236.214|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/thunderbird/releases/2.0.0.4/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR thunderbird-2.0.0.4.tar.gz.asc ... done.
Length: 186 (unauthoritative)

100%[==============================================================>] 186           --.--K/s             

20:37:03 (34.47 KB/s) - `thunderbird-2.0.0.4.tar.gz.asc' saved [186]


Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.



do you know of any way to fix it, and maybe salvage my settings?

thanks

---

### Post by nanotube on 2007-07-13
hey!
besides that error message on the bottom, everything else works, is that correct?
if so, then i had the same thing. all i had to do was to delete one file. 
see this thread for details:
[http://ubuntuforums.org/showthread.php?t=418896&highlight=offlinemenuitem](http://ubuntuforums.org/showthread.php?t=418896&highlight=offlinemenuitem)

in brief, delete file /opt/thunderbird/chrome/offline.manifest
```
sudo rm /opt/thunderbird/chrome/offline.manifest
```

hope that does it for you :)

---

### Post by the.phantom on 2007-07-13
UPDATE


all is well in Ubuntu land again!

i used the new script to remove the botched install
and it worked fine i was back at 1.0.5.12


then in used the new script again to install

NOTE your new scripts sure saved my behind, i had it save the backup
so it did go back when i did the remove
and then the install worked !!!!!!

one small question
this is what i show in my home folder now
[IMG]http://rcip.com/mitch/mozilla.jpg[/IMG]

can i safely delete all but the latest backup?

thanks

---

### Post by nanotube on 2007-07-13
excellent. :)

about your backups: if everything is working well, then yes, you can safely delete all the "backup" folders.

i will note, however, that it is a good idea to have at least one, relatively current, backup of all your files /somewhere/. :) hard drives die, computers crash, data gets corrupted... you know, all the stuff you hope never happens to you, but that still happens with an alarming regularity. :)

---

