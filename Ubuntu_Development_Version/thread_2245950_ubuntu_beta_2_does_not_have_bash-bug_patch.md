---
title: "ubuntu beta 2 does not have bash-bug patch"
date: 2014-09-27
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-09-27
Beta2 is a security vulnerability in the *live* session. It does not have the bash-bug patch included.

See for yourself here.

[http://ubuntuforums.org/showthread.php?t=2245682&p=13128872#post13128872](http://ubuntuforums.org/showthread.php?t=2245682&p=13128872#post13128872)

utopic-desktop-amd64.iso

```

ubuntu@ubuntu:~$ env x='() { :;}; echo vulnerable' bash -c 'echo hello'
vulnerable
hello
ubuntu@ubuntu:~$ 



```

*note*

I do not use persistent drive option with SDC , only discard on shutdown while in live session.

---

### Post by zika on 2014-09-27
Did You apply _available_ upgrades for the version You've tried?

---

### Post by ventrical on 2014-09-27
> **zika said:**
> Did You apply _available_ upgrades for the version You've tried?

On my installs , yes ... but if you look above, I'm talking about the "live" session.

---

### Post by sudodus on 2014-09-27
> **ventrical said:**
> On my installs , yes ... but if you look above, I'm talking about the "live" session.

It is possible to update/upgrade the live session, but 'nobody' would have thought of doing that, if you had not warned us about it. Anyway, we (the testers) should quickly move on to the current daily build anyway :-P

---

### Post by Elfy on 2014-09-27
there was talk about respinning the beta on thursday - obviously didn't happen

---

### Post by ventrical on 2014-09-27
> **sudodus said:**
> It is possible to update/upgrade the live session, but 'nobody' would have thought of doing that, if you had not warned us about it. Anyway, we (the testers) should quickly move on to the current daily build anyway :-P

Agreed... in the process now.

My aplologies to any ...  I usually do not upgrade 'live'. (actually I  have tired in the past - only live-persisitve will update/upgrade ). I usually just test 'live' and then hard install .. but that bug is fixed for hard install upon update/upgrade.

..zsyncing daily ...

---

### Post by ventrical on 2014-09-27
> **sudodus said:**
> It is possible to update/upgrade the live session, but 'nobody' would have thought of doing that, if you had not warned us about it. Anyway, we (the testers) should quickly move on to the current daily build anyway :-P

As suspected .. locked down tighter than a mouse's ear.

```

Read utopic-desktop-amd64.iso. Target 100.0% complete.      
verifying download...checksum matches OK
used 1176059904 local, fetched 0

```

Perhaps yourself or zika could walk me through how-to update/upgrade 'live' non persisitve USB iso.

Thanks

Regards..

---

### Post by ventrical on 2014-09-27
> **Elfy said:**
> there was talk about respinning the beta on thursday - obviously didn't happen
ditto..

---

### Post by ventrical on 2014-09-27
Baffling as it may seem (to me) I,

```

sudo apt-get update
sudo apt-get dist-upgrade

```

and it is upgrading! I would always get errors when using this method unless persistive.

Always a first for somthing:)

... and yes .. we only want to upgrade the   bash  pkg.

but update did no good.

Now..

```

ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ env x='() { :;}; echo vulnerable' bash -c 'echo hello'
ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$ vulnerable
vulnerable: command not found
ubuntu@ubuntu:~$ hello
The program 'hello' can be found in the following packages:
 * hello
 * hello-traditional (You will have to enable component called 'universe')
Try: sudo apt-get install <selected package>
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 


```

...

```

ubuntu@ubuntu:~$ apt-cache policy bash
bash:
  Installed: 4.3-9ubuntu3
  Candidate: 4.3-9ubuntu3
  Version table:
 *** 4.3-9ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ utopic/main amd64 Packages
        100 /var/lib/dpkg/status
ubuntu@ubuntu:~$ 


```

---

### Post by Elfy on 2014-09-27
did you use a different terminal

---

### Post by ventrical on 2014-09-27
> **Elfy said:**
> did you use a different terminal

I use Ctrl + Alt + F1 and/or Ctrl+Alt+t.

Ctrl+Alt+t in the iso 'live' session case. Why ? No good?

---

### Post by Elfy on 2014-09-27
I think I read somewhere that if you did foo in terminal and then bar without starting a new terminal - you'd still see vulnerable

so if you env x='() { :;}; echo vulnerable' bash -c 'echo hello' then apt-get update/grade then env x='() { :;}; echo vulnerable' bash -c 'echo hello' it'd be the same

all that aside - the beta image is just that - this one's probably not the best we've seen ;)

---

### Post by zika on 2014-09-27
> **ventrical said:**
> Perhaps yourself or zika could walk me through how-to update/upgrade 'live' non persisitve USB iso.

Thanks

Regards..I'll pass...
Thanks.
Regards.

---

### Post by ventrical on 2014-09-28
> **Elfy said:**
> I think I read somewhere that if you did foo in terminal and then bar without starting a new terminal - you'd still see vulnerable

so if you env x='() { :;}; echo vulnerable' bash -c 'echo hello' then apt-get update/grade then env x='() { :;}; echo vulnerable' bash -c 'echo hello' it'd be the same

all that aside - the beta image is just that - this one's probably not the best we've seen ;)

Thanks.

That saves me a lot of work. :)

---

### Post by ventrical on 2014-09-28
> **zika said:**
> I'll pass...
Thanks.
Regards.

Your welcome.
:)

---

### Post by ventrical on 2014-09-29
> **Elfy said:**
> I think I read somewhere that if you did foo in terminal and then bar without starting a new terminal - you'd still see vulnerable

so if you env x='() { :;}; echo vulnerable' bash -c 'echo hello' then apt-get update/grade then env x='() { :;}; echo vulnerable' bash -c 'echo hello' it'd be the same

all that aside - the beta image is just that - this one's probably not the best we've seen ;)

It's been upgraded yet again.

Enable proposed  repo from software sources:
then

```

ubuntu@ubuntu:~$ sudo apt-get install bash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bash is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ apt-cache policy bash
bash:
  Installed: 4.3-9ubuntu1
  Candidate: 4.3-9ubuntu1
  Version table:
 *** 4.3-9ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ utopic/main amd64 Packages
        100 /var/lib/dpkg/status
ubuntu@ubuntu:~$ sudo apt-get install bash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  bash-doc
The following packages will be upgraded:
  bash
1 upgraded, 0 newly installed, 0 to remove and 124 not upgraded.
Need to get 582 kB of archives.
After this operation, 12.3 kB disk space will be freed.
Get:1 http://archive.ubuntu.com/ubuntu/ utopic/main bash amd64 4.3-9ubuntu4 [582 kB]
Fetched 582 kB in 1s (292 kB/s)
(Reading database ... 183289 files and directories currently installed.)
Preparing to unpack .../bash_4.3-9ubuntu4_amd64.deb ...
Unpacking bash (4.3-9ubuntu4) over (4.3-9ubuntu1) ...
Processing triggers for install-info (5.2.0.dfsg.1-4) ...
Processing triggers for man-db (2.6.7.1-1) ...
ubuntu@ubuntu:~$ env x='() { :;}; echo vulnerable' bash -c 'echo hello'
hello
ubuntu@ubuntu:~$ 

```

Works good in 'live' system after booting from latest iso.

Regards..

---

