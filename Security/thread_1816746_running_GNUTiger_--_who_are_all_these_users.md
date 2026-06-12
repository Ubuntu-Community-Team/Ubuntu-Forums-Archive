---
title: "running GNU/Tiger -- who are all these users?"
date: 2011-08-02
forum: Security
---

### Post by sneakyimp on 2011-08-02
I'm running Tiger on my Ubuntu 10.04 server, trying to harden it against attack.  There's a long list of users that come with a fresh system install and I don't know why they exist, what they are for, or whether it's safe to disable login or deny them cron capabilities.  Can someone help me understand what to do about these users?

daemon
bin
sys
sync
games
man
lp
news
uucp
proxy
www-data
backup
list
irc
gnats
nobody
libuuid
syslog
messagebus
haldaemon
landscape

NOTE:  I don't have apache installed yet, and so wonder why www-data is already a user. Also, why do we have news, irc, and games users?

---

### Post by bodhi.zazen on 2011-08-02
Those are all system daemons and are used by the relevant server.

I do not know of any documentation in one place of what they are are or what the default list is in Ubuntu.

If you did a fresh install, you are looking at it ;)

If you are going to use a tools such as tiger, your next step is to use google to check for answers as I doubt anyone here is going to type an answer to all the output of tiger on a default install.

See also : [http://ubuntuforums.org/showpost.php?p=9265631&postcount=6](http://ubuntuforums.org/showpost.php?p=9265631&postcount=6)

The documentation with tiger is quite good, but long and detailed.

There is an attempt to get a wiki page going, and as it is a community maintained wiki, I suggest people answer on the wiki and link the wiki page to the forums ;)

[https://help.ubuntu.com/community/InstallingSecurityTools](https://help.ubuntu.com/community/InstallingSecurityTools)

Feel free to start a wiki page.

---

### Post by sneakyimp on 2011-08-02
Thanks for your post. I've read most of the tigerexp explanations (I ran with -e and/or -E). There are a few items (such as limiting cron via allow/deny) which I'm afraid to do because I don't want to break something.

As for news, irc, and games -- why do these users exist?  I'm not running an irc, news, or game server on my system.  Can I delete these accounts?  Will they break anything?

---

### Post by bodhi.zazen on 2011-08-02
> **sneakyimp said:**
> Thanks for your post. I've read most of the tigerexp explanations (I ran with -e and/or -E). There are a few items (such as limiting cron via allow/deny) which I'm afraid to do because I don't want to break something.

As for news, irc, and games -- why do these users exist?  I'm not running an irc, news, or game server on my system.  Can I delete these accounts?  Will they break anything?

You should be able to remove those users if you wish. Make a copy of the files, edit them, and then see if you broke anything. If you did, resotre from backup.

alternately you can set their default shells to /bin/false

---

### Post by sneakyimp on 2011-08-02
I have changed their default shells to /bin/false.

Who is the 'list' user? I've tried googling and just get millions of posts about how to list all the users.

---

### Post by scorp123 on 2011-08-03
> **sneakyimp said:**
>  Who is the 'list' user? Probably only relevant if you were running a so called "Mailing List" service. Hence that name.

---

### Post by sneakyimp on 2011-08-03
i find it odd that such a user would be included in a default install of on OS.  Doesn't seem very clean.

---

### Post by scorp123 on 2011-08-03
> **sneakyimp said:**
> i find it odd that such a user would be included in a default install of on OS.  Doesn't seem very clean. They might have created these pre-defined user accounts in order to create some sort of uniformity within this distribution, so you won't run into too much trouble later on if ever you install a package that expects one of those names to exist. It makes the job of giving support a lot easier. 

I mean nobody is stopping you to e.g. install the Apache web server and have it run under an account name such as "sevenofnine", or install a mailing list server and have it running under an account name "redqueen" ... But good luck getting support with that.

And the fact that those accounts already exist in your system will hopefully prevent anyone from using an account of the same name for any other purposes, and thus prevent trouble with any packages that might expect to use those user accounts.

So from that POV it makes a lot of sense and it isn't so odd at all.

---

### Post by sneakyimp on 2011-08-03
Thanks for the thoughtful response.  Yes that does make sense.  Suppose I were to set the default shell for these users to /bin/false in /etc/passwd.  Is that going to cause problems later?  For example, if I install apache as www-data ?

---

### Post by scorp123 on 2011-08-03
> **sneakyimp said:**
>  Suppose I were to set the default shell for these users to /bin/false in /etc/passwd.  Is that going to cause problems later?  For example, if I install apache as www-data ? Some products expect to be able to open a bash shell and then run scripts, commands, etc. under that different user identity. So setting their default shell to something invalid or to something that will block access to a shell might indeed cause strange side effects, e.g. a server process wants to open a shell because it has some cleaning-up to do ... but it can't do that anymore because you blocked it.

Of course: I can understand why you ask this and what you are thinking: "Let's block access to the shell and I will be safer."

Except that you don't realise that you are already safe and that this step isn't necessary.

Here is why:

Having a shell entry in /etc/passwd means zip. That alone per se still will not get you into the system!

What really matters is /etc/shadow! Only and solely if an account has a valid password hash inside that file it will be able to login. Otherwise: Nope. No password = No login.

Example from my system (Ubuntu 10.10, 64-bit):
```

> sudo cat /etc/shadow

[sudo] password for sysadm: 
root:$6$1234567890LOTSOFMUMBOJUMBORIGHTHERE*!!1234567890/:15181:0:99999:7:::
daemon:*:14889:0:99999:7:::
bin:*:14889:0:99999:7:::
sys:*:14889:0:99999:7:::
sync:*:14889:0:99999:7:::
games:*:14889:0:99999:7:::
man:*:14889:0:99999:7:::
lp:*:14889:0:99999:7:::
mail:*:14889:0:99999:7:::
news:*:14889:0:99999:7:::
uucp:*:14889:0:99999:7:::
proxy:*:14889:0:99999:7:::
www-data:*:14889:0:99999:7:::
backup:*:14889:0:99999:7:::
list:*:14889:0:99999:7:::
irc:*:14889:0:99999:7:::
gnats:*:14889:0:99999:7:::
nobody:*:14889:0:99999:7:::
libuuid:!:14889:0:99999:7:::
syslog:*:14889:0:99999:7:::
messagebus:*:14889:0:99999:7:::
avahi-autoipd:*:14889:0:99999:7:::
avahi:*:14889:0:99999:7:::
couchdb:*:14889:0:99999:7:::
usbmux:*:14889:0:99999:7:::
speech-dispatcher:!:14889:0:99999:7:::
kernoops:*:14889:0:99999:7:::
pulse:*:14889:0:99999:7:::
rtkit:*:14889:0:99999:7:::
saned:*:14889:0:99999:7:::
hplip:*:14889:0:99999:7:::
gdm:*:14889:0:99999:7:::
sysadm:$6$1234567890MOREMUMBOJUMBORIGHTHERE*!!1234567890:15181:0:99999:7:::
sshd:*:15181:0:99999:7:::
```

Quiz question: Which accounts above are able to login ... and which ones aren't?

Bingo. Those with an encrypted password on the second position are able to login. On my system that's exactly two accounts:

- root (because I enabled it)
- sysadm (because sometimes using "sudo" is good enough)

And here is /etc/passwd for comparison:

```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:105::/var/run/dbus:/bin/false
avahi-autoipd:x:103:108:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:104:109:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
couchdb:x:105:113:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
usbmux:x:106:46:usbmux daemon,,,:/home/usbmux:/bin/false
speech-dispatcher:x:107:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
kernoops:x:108:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:109:114:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:110:117:RealtimeKit,,,:/proc:/bin/false
saned:x:111:118::/home/saned:/bin/false
hplip:x:112:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:113:120:Gnome Display Manager:/var/lib/gdm:/bin/false
sysadm:x:1000:1000:The guy with sudo access,,,:/home/sysadm:/bin/bash
sshd:x:114:65534::/var/run/sshd:/usr/sbin/nologin
```

So ....

All these accounts in /etc/shadow that don't have a valid password can't login ... so why do some of these accounts still have a valid shell? Isn't that a contradiction?

It isn't. Here is why:

Some processes may be started with "root" super powers during system start-up. For some applications this is necessary e.g. so they may open TCP ports below 1024 (anything below TCP port 1024 requires "root" priviledges!). One good example is e.g. the SSH daemon which needs to open port 22 TCP.

But once the process has done what it needed to do those "root" super powers are total overkill and way to dangerous to keep around. So many processes will thus "su" (switch user account) into an account with way less powers and thus auto-restrict themselves and only perform the few little duties that remain (e.g. compress logfiles, write a status message to the log, etc.) to be performed.

And for that some of them need to have a valid shell!

You can test this yourself:

- Open a terminal
- become root, e.g. by executing **sudo -i**
- once you're "root", become the "WWW Data" daemon: **su - www-data**
- and now try to do something really stupid with your home directory in **/home** ... YOU CAN'T. Because you just threw all your super-powers out of the window and you can't do any harm; you could only harm your own few files in **/var/www-data** and that's it ... And this is *good*


System services do pretty much *exactly* that. Hence why some of them may indeed need a valid shell so maintenance scripts (usually owned by "root"!) etc. may "su" into their accounts and perform jobs and maintenance tasks. Your system still isn't at risk per se because those accounts have no password set, so they can't login.

BTW, as system administrator this is also something you'd have to check and keep an eye open for: Do any of those accounts such as "nobody" or "www-data" have passwords all of a sudden??? Now *that* would be a pretty strong sign that someone has somehow broken into the system and is probably using those normally "password-less" accounts as backdoor ... 


I hope this helped? BTW, there is also a nice manual page explaining all that:

**man shadow**

---

### Post by sneakyimp on 2011-08-03
Thanks for the excellent detail.  I have noticed something though.  I have two user accounts on my machine which are only permitted to login using a key pair (public key is in ~/.ssh.authorized_keys).  These accounts have a ! in that second field:
```

root:!*:15174:0:99999:7:::
daemon:*:15174:0:99999:7:::
bin:*:15174:0:99999:7:::
sys:*:15174:0:99999:7:::
sync:*:15174:0:99999:7:::
games:*:15174:0:99999:7:::
man:*:15174:0:99999:7:::
lp:*:15174:0:99999:7:::
mail:*:15174:0:99999:7:::
news:*:15174:0:99999:7:::
uucp:*:15174:0:99999:7:::
proxy:*:15174:0:99999:7:::
www-data:*:15174:0:99999:7:::
backup:*:15174:0:99999:7:::
list:*:15174:0:99999:7:::
irc:*:15174:0:99999:7:::
gnats:*:15174:0:99999:7:::
nobody:*:15174:0:99999:7:::
libuuid:!:15174:0:99999:7:::
syslog:*:15174:0:99999:7:::
messagebus:*:15174:0:99999:7:::
haldaemon:*:15174:0:99999:7:::
sshd:*:15174:0:99999:7:::
landscape:*:15174:0:99999:7:::
ubuntu:!$6$/6afNJmq$eDaS3bIYQJ6njjHMPgi7PCi/5xf1quu6m4b1f/rf1lKP7DvBhq4Xq3oQ0JxJ3X3lC./0sGACp3DakNJOxpZyF1:15174:0:99999:7:::
sneakyimp:!:15175:0:99999:7:::
sneakyimps_boss:!:15176:0:99999:7:::
postfix:*:15183:0:99999:7:::

```

What does the ! signify versus the * ?  Is it unsafe for these accounts to have empty passwords?  They are both listed in sudoers but i have password login disabled -- keys are *required* for login.  I'm pretty fuzzy on the need for a password if I have an elaborate key protecting the account already.

---

### Post by scorp123 on 2011-08-03
> **sneakyimp said:**
>  What does the ! signify versus the * ? man shadow:
```

... 
If the password field contains some string that is not a valid result of crypt(3), 
for instance ! or *, the user will not be able to use a unix password to log in
(but the user may log in the system by other means).

This field may be empty, in which case no passwords are required to authenticate 
as the specified login name. However, some applications which read the /etc/shadow
file may decide not to permit any access at all if the password field is empty.

[B]A password field which starts with a exclamation mark means 
that the password is locked. The remaining characters on the line 
represent the password field before the password was locked.[/B]

...
```

> **sneakyimp said:**
>  keys are *required* for login. Excellent.

> **sneakyimp said:**
>  I'm pretty fuzzy on the need for a password if I have an elaborate key protecting the account already. In your case it simply means that a password is still there, but it's disabled, they can't use it to login. And just as the manual page above says: they could use other means to get in ... in your case: SSH keys.

Everything working tip top + as designed. :)

---

