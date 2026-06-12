---
title: "Jack realtime not working with RT-Kernel"
date: 2010-12-18
forum: Ubuntu Studio
---

### Post by pepsifx357 on 2010-12-18
Hi guys, I've got an Ubuntu Server Lucid 10.04.1 lTS setup with the 2.6.31-11-rt kernel installed.

I've setup pretty much everything I knew to setup and it still says that I don't have permission to use the realtime priority.

My audio.conf is this:

```
@audio   -  rtprio     100
@audio   -  memlock    1535133
@audio   -  nice      -10

```

And just to make sure, my limits.conf is this:

```
@audio   -  rtprio     100
@audio   -  memlock    1535133
@audio   -  nice      -10

```

I've added my name to the group audio by using this:

```
usermod -a -G audio ben
```

I installed members and came up with this proof that I'm on the audio group.

```
ben@core:~$ members --all audio
ben
ben@core:~$ 

```

However, when I start qjackctl it gives me this...

```
JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
After applying these changes, please re-login in order for them to take effect.
You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again!
```

It runs fine when I uncheck realtime processing, but that's not really what I want.

What is the deal with this?

---

### Post by AutoStatic on 2010-12-18
Hello pepsifx357, you can try removing the lines from your */etc/security/limits.conf* file and only use */etc/security/limits.d/audio.conf*. And you don't need the nice setting, you can leave that line out. And what does the **groups** command return in a terminal when you're logged in as ben?

---

### Post by pepsifx357 on 2010-12-18
I removed the lines from /etc/security/limits.conf and got this from jack:

```
Please check your /etc/security/limits.conf for the following lines
and correct/add them:
  @audio          -       rtprio          100
  @audio          -       nice            -10
After applying these changes, please re-login in order for them to take effect.
```


The groups output is this:

```
ben@core:~$ groups
ben audio
ben@core:~$ 

```

---

### Post by AutoStatic on 2010-12-18
Then try deleting */etc/security/limits.d/audio.conf* and run **sudo dpkg-reconfigure -p high jackd**. This should reconfigure jackd and also come up with a pop-up screen asking you if you want JACK to be able to run in real-time.

---

### Post by pepsifx357 on 2010-12-18
Ok, I deleted it and ran dpkg-reconfigure.  Here's what I get now:

```
JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
Please check your /etc/security/limits.conf for the following lines
and correct/add them:
  @audio          -       rtprio          100
  @audio          -       nice            -10
After applying these changes, please re-login in order for them to take effect.
You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again!
```

---

### Post by AutoStatic on 2010-12-18
Weird, what does **ulimit -l** output?

---

### Post by pepsifx357 on 2010-12-18
1535133

That is the number that jack told me to put for the memlock instead of unlimited.

---

### Post by AutoStatic on 2010-12-18
OK that works, so it's not a PAM issue.
How does your */etc/security/limits.d/audio.conf* file look now? And did you log out and log in again after reconfiguring JACK?

---

### Post by pepsifx357 on 2010-12-18
I did a reboot and started jack again here's what I got this time:

```
JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
Please check your /etc/security/limits.conf for the following lines
and correct/add them:
  @audio          -       rtprio          100
  @audio          -       nice            -10
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1535133
After applying these changes, please re-login in order for them to take effect.
You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again!
```

---

### Post by Pablo_F on 2010-12-18
Hi, as a reminder, changes in users & groups and security limits need a computer reboot.

What are the outputs of:

cat /etc/security/limits.conf /etc/security/limits.d/audio.conf |grep -v "#"

whoami && ulimit -r -l


On the other hand, ben is not a member of the admin group? Are you (ben) able to run commands as administrator (with sudo)?. I think it is safer adding a user to a group by means of:

sudo adduser user group 

instead of usermod. 

Cheers, Pablo

---

### Post by pepsifx357 on 2010-12-18
ok, for the first ***mand I got:

```
ben@core:~$ cat /etc/security/limits.conf /etc/security/limits.d/audio.conf |grep -v "#"


@audio   -  rtprio     99
@audio   -  memlock    unlimited

```

And for the second ***mand I get this:

```
ben@core:~$ whoami && ulimit -r -l
ben
real-time priority              (-r) 99
max locked memory       (kbytes, -l) unlimited

```

Edit: Is there a reason that the forum censored *** in ***mand?

---

### Post by AutoStatic on 2010-12-19
No idea.
Could you also post the outcome of **cat ~/.jackdrc** ? Thanks!

---

### Post by pepsifx357 on 2010-12-19
I'm just as stumped.  When I last tried this, it was with an 8.04 LTS version and I didn't have these problems.


```
ben@core:~$ cat ~/.jackdrc
/usr/bin/jackd -r -dalsa -dhw:0 -r88200 -p1024 -n2

```

Edit: Oh, and by the way, I'm using a RME HDSP MADI card with a 96KHZ converter.  I usually use a sample rate of 88.2Khz.

---

### Post by AutoStatic on 2010-12-21
Could you try running QjackCtl/JACK with another account? It has to be a member of the audio group of course.

---

### Post by pepsifx357 on 2010-12-21
That's kinda where I think the problem is.  I'm not sure if either jack doesn't make a valid group having access to RT or my name is not getting on the audio group for some reason.  I'm also confused as to why it is pointing to /etc/security/limit.conf yet most of the tutorials are pointing towarsd /etc/security/limits.d/audio.conf.  I'll try making another name but I don't think it's going to work.  I read some where that one of the kernels were disabled by default to work in Real Time.  But I thought it was a newer kernel.  I've been at this setup for about 2 years now, I hate to say it, but I'm almost ready to throw in the towel on linux for my studio.

---

### Post by Pablo_F on 2010-12-21
Hi, 

From [ftp://kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_limits.html](ftp://kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_limits.html)

> By default limits are taken from the /etc/security/limits.conf config file. Then individual *.conf files from the /etc/security/limits.d/ directory are read. 

So it doesn't matter much in which of the two files the relevant lines are written. Anyway, the output of "ulimit -l -r" is OK so you should be using realtime mode. The jackd command you showed recently is "no realtime" (-r option). That is a bad idea.

A common error is thinking that you have to tick realtime mode in qjackctl if and only if you are running a realtime kernel. I am not sure if you are aware that this is not true. Check FAQ in jackaudio.org. In short, you need realtime mode in jackd (and rtprio and memlock privileges for the user running jackd), but a linux-rt kernel is not always needed.  

What seems very strange is that ben is member of ben and audio groups and no more.  No admin, for example. I think you messed up with the usermod command as I did a short time ago. 

Maybe, you could consider entering IRC, #ubuntustudio or #opensourcemusicians or #jack or #ardour channels at irc.freenode.net. Interactive help is much faster and often better if you are lucky. For example, from the web browser: [http://webchat.freenode.net/](http://webchat.freenode.net/)

Cheers, Pablo

---

### Post by pepsifx357 on 2010-12-22
> **Pablo_F said:**
> 
What seems very strange is that ben is member of ben and audio groups and no more.  No admin, for example. I think you messed up with the usermod command as I did a short time ago.


Well after running ```
usermod -a -G ben audio
``` I got kicked out of admin and got locked out from using sudo.  I had to use a recovery console to put myself back in again.  My groups are all messed up.  At this point I have no Idea what is going on with my name group or permissions.  Probably best to start over again.

---

### Post by Pablo_F on 2010-12-22
> Well after running

usermod -a -G ben audio

I got kicked out of admin and got locked out from using sudo. I had to use a recovery console to put myself back in again

The same happened to me but I won't try again to see what I did wrong. I think that "**su**peruser: **do** **add user** **pablo** to **audio** group" (sudo adduser pablo audio) is far more intuitive and it has never messed up anything in my computer.

I hope you can solve the issues. Reinstalling is not a bad idea at this point, IMO.

Cheers, Pablo

---

### Post by AutoStatic on 2010-12-23
> **Pablo_F said:**
> I think it is safer adding a user to a group by means of:

sudo adduser user group 

instead of usermod.usermod should do the job just fine. It's the preferred method on RHEL systems, at least that's what I had to use during training.

I wouldn't reinstall just because of one single file that might got messed up, in this case */etc/group*. Is it possible to post the content of that file? It is also possible to modify this file manually.

---

### Post by Pablo_F on 2010-12-23
> usermod should do the job just fine. It's the preferred method on RHEL systems, at least that's what I had to use during training.

I am sure you are right Auto. I think the reason of our failure was doing:

usermod -a -G username audio  ----> DON'T DO THIS or you will mess up your groups!

instead of the correct option:

usermod -a -G audio username

Cheers! Pablo

---

### Post by pepsifx357 on 2010-12-23
```
ben@core:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:ben
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:
mlocate:x:105:
ssh:x:106:
netdev:x:107:
landscape:x:108:
ben:x:1000:
lpadmin:x:109:
sambashare:x:110:
admin:x:111:
messagebus:x:112:
winbindd_priv:x:113:
haldaemon:x:114:

```

> usermod -a -G username audio ----> DON'T DO THIS or you will mess up your groups!

I probably did do that on accident.

---

### Post by pepsifx357 on 2011-01-11
Ok, I tried again with a fresh install and I get the same thing.


I downloaded and installed members and I get this.

> ben@ben-desktop:~$ whoami
ben


> ben@ben-desktop:~$ groups
ben adm dialout cdrom plugdev lpadmin admin sambashare


> ben@ben-desktop:~$ members audio
speech-dispatcher


What is the deal?

audio is not even a group?  I thought jack created that group whenever it installed.

When I added my name to the group audio I used this code verbatim.

> useradd -G audio ben

Was that right?

This is really confusing the hell outta me.

I got it to work.  I went to Ubuntu's user and groups manager and did it from there.  Apparently useradd -G DOES NOT WORK.

---

### Post by Pablo_F on 2011-01-12
> Quote:
ben@ben-desktop:~$ groups
ben adm dialout cdrom plugdev lpadmin admin sambashare
Quote:
ben@ben-desktop:~$ members audio
speech-dispatcher
What is the deal? audio is not even a group?

audio is a group but ben doesn't belong to it. Not yet.

> Quote:
useradd -G audio ben
Was that right?

It does not seem so. Note that useradd is a different command. It is the first time that it is mentioned in this thread.

 I know three ways of adding ben to the audio group. The three of them are valid:

1) sudo user**mod** -a -G audio ben

2) sudo adduser ben audio

3) Ubuntu's user and groups manager

You did it, anyway. 

Cheers! Pablo

---

### Post by pepsifx357 on 2011-01-12
Ok, from a command line only standpoint, what is the best way to view ALL of the groups on your machine?  When I typed in groups it showed my name and other various names that looked like groups.  But not the audio group.

Also, what controls users and groups?  Is it PAM?  If so, I need to read up on that something serious so I won't run into any problems again.

Thanks guys

---

### Post by Pablo_F on 2011-01-12
Hi Ben.

*groups* only shows the groups that the current user (the user with throws said command) belongs to.

I am not a Linux expert and I don't think this is the best board to discuss this but there are some basic files in any Linux system which are /etc/passwd and /etc/group.

Cheers! Pablo

---

### Post by AutoStatic on 2011-01-12
> **pepsifx357 said:**
> Ok, from a command line only standpoint, what is the best way to view ALL of the groups on your machine? The **groups** command.

> **pepsifx357 said:**
> When I typed in groups it showed my name and other various names that looked like groups.  But not the audio group.Then there is no audio group or your */etc/groups* file contains errors.

> **pepsifx357 said:**
> Also, what controls users and groups?In fact there are two files that tell the system which users and groups are available on that specific system, like Pablo already pointed out those are */etc/passwd* and */etc/groups*. No other files tell the system which users and groups are available, unless you use an external authentication mechanism/user database like Winbind, Kerberos, LDAP or NIS.

> **pepsifx357 said:**
> Is it PAM?No, PAM are the Pluggable Authentication Modules. PAM takes care of what happens when users log on in any way, through gdm, ssh, in a virtual terminal, ftp etc. (to put it simply). Check your */etc/pam.d/* for that. And some of those modules get their settings from */etc/security/* like the pam_limits module which takes it settings from */etc/security/limits.d/*.

> **pepsifx357 said:**
> If so, I need to read up on that something serious so I won't run into any problems again.Maybe you could read something on how users, groups and permissions work on GNU/Linux. I don't have a link ready that quickly though. But it's a bit beyond the scope of setting up a low-latency realtime audio environment.

---

### Post by Pablo_F on 2011-01-12
> Quote:
Originally Posted by pepsifx357 View Post
Ok, from a command line only standpoint, what is the best way to view ALL of the groups on your machine?
The groups command.

No, that is not correct. Try "man groups"

>  groups - print the groups a user is in

Not all the groups!

With:

cat /etc/group

You see all the groups that are present in your system and the users belonging to each of them.

Cheers! Pablo

---

### Post by AutoStatic on 2011-01-12
Yup you're right Pablo. So if you run the **groups** command and it doesn't print the audio group then you're not a member of that group.

---

### Post by pepsifx357 on 2011-01-14
I get it now...Thanks for the help guys!

---

