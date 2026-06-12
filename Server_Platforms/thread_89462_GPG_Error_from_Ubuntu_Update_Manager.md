---
title: "GPG Error from Ubuntu Update Manager"
date: 2005-11-12
forum: Server Platforms
---

### Post by Robert A. Matthews on 2005-11-12
Hi Folks!

Whilst doing a reload in Ubuntu Update Manager I
was presented with the following warning:

"The following problems were found on your system:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: 
The following signatures were invalid: BADSIG 40976EAF437D05B5 
Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"

Any idea what this is about - and what I can do to
fix it?

Thanks in advance,

Robert A. Matthews

---

### Post by aysiu on 2005-11-13
Follow the instructions in my sig. It'll give you up-to-date repositories with no errors.

---

### Post by OldSeaDog on 2005-11-16
I followed the instructions to the letter with the exception that I used the Canadian archives and I also have the problem, as follows:

W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

I can run sudo apt-get update until hell freezes over and the same error will appear.  What I think I need is a new SIG!  I must be in the 3 digit world in tried by now...

I have also tried Aptitude as well as Synaptic repeatedly.

BTW, I emailed ftpmaster, but got no reply, so...

---

### Post by Oceola on 2005-11-16
I get a similar error when i try and access the Hoary Hedgehog disc.
I folloed the instructions of "apt-cdrom add" and it had worked before, unless someone sees a syntax error. I do this from a terminal and get prompted to place the disc and hit enter, however there is still no recognition. Did someone change the passwords so the disc isn't recognized anymore?:confused:

---

### Post by aysiu on 2005-11-16
[QUOTE=OldSeaDog]I followed the instructions to the letter with the exception that I used the Canadian archives and I also have the problem, as follows:

W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems[/QUOTE] You're not following them to the letter if you're using the Canadian archives (or the US ones or the GB ones or the FR ones). Follow them to the letter--the errors will be gone.

[quote=Oceola]I get a similar error when i try and access the Hoary Hedgehog disc.
I folloed the instructions of "apt-cdrom add" and it had worked before, unless someone sees a syntax error. I do this from a terminal and get prompted to place the disc and hit enter, however there is still no recognition. Did someone change the passwords so the disc isn't recognized anymore?[/quote] What does your /etc/apt/sources.list looks like?

---

### Post by Crazy Man on 2005-11-16
Followed it to the letter...still getting the error.

---

### Post by aysiu on 2005-11-16
[QUOTE=Crazy Man]Followed it to the letter...still getting the error.[/QUOTE] Yeah, I don't believe you. I just popped in my live Hoary CD **followed the instructions to the letter** for Hoary, and got a perfectly fine ```
sudo apt-get update
```. See the screenshot attached. ```
ubuntu@ubuntu:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
ubuntu@ubuntu:~$ sudo gedti /etc/apt/sources.list
sudo: gedti: command not found
ubuntu@ubuntu:~$ sudo gedit /etc/apt/sources.list
ubuntu@ubuntu:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com hoary Release.gpg [189B]
Get:2 http://archive.ubuntu.com hoary-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:4 http://archive.ubuntu.com hoary-backports Release.gpg [189B]
Get:5 http://archive.ubuntu.com hoary Release [26.2kB]
Get:6 http://security.ubuntu.com hoary-security Release [16.9kB]
Get:7 http://archive.ubuntu.com hoary-updates Release [16.8kB]
Get:8 http://archive.ubuntu.com hoary-backports Release [11.3kB]
Get:9 http://archive.ubuntu.com hoary/main Packages [490kB]
Get:10 http://security.ubuntu.com hoary-security/main Packages [76.6kB]
Get:11 http://security.ubuntu.com hoary-security/restricted Packages [14B]
Get:12 http://security.ubuntu.com hoary-security/main Sources [17.5kB]
Get:13 http://security.ubuntu.com hoary-security/restricted Sources [14B]
Get:14 http://security.ubuntu.com hoary-security/universe Packages [50.3kB]
Get:15 http://security.ubuntu.com hoary-security/universe Sources [7121B]
Hit http://archive.ubuntu.com hoary/restricted Packages
Get:16 http://archive.ubuntu.com hoary/main Sources [175kB]
Hit http://archive.ubuntu.com hoary/restricted Sources
Get:17 http://archive.ubuntu.com hoary/universe Packages [2169kB]
Get:18 http://archive.ubuntu.com hoary/universe Sources [857kB]
Get:19 http://archive.ubuntu.com hoary/multiverse Packages [88.4kB]
Get:20 http://archive.ubuntu.com hoary/multiverse Sources [48.4kB]
Get:21 http://archive.ubuntu.com hoary-updates/main Packages [18.6kB]
Get:22 http://archive.ubuntu.com hoary-updates/restricted Packages [14B]
Get:23 http://archive.ubuntu.com hoary-updates/main Sources [5509B]
Get:24 http://archive.ubuntu.com hoary-updates/restricted Sources [14B]
Get:25 http://archive.ubuntu.com hoary-backports/main Packages [11.5kB]
Get:26 http://archive.ubuntu.com hoary-backports/restricted Packages [14B]
Get:27 http://archive.ubuntu.com hoary-backports/universe Packages [26.3kB]
Get:28 http://archive.ubuntu.com hoary-backports/multiverse Packages [1536B]
Fetched 4114kB in 3m18s (20.8kB/s)
Reading package lists... Done
ubuntu@ubuntu:~$
```

---

### Post by HJThis on 2005-11-16
Hello,To all

@aysiu

Just like to say thanks i did as said & ya no more error here.


BOL ;)

---

### Post by Sycho.Squirrell on 2005-11-16
Followed the enabling extra repositories to the letter and i get me the same error.
i only have this problem on my hoary machine. Both my breezy boxes are working fine. Any ideas or suggestions would be greatly appreciated.
Thanks in advance.
:p 

```

 apt-get update

```

```


Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Fetched 17.2kB in 1s (15.3kB/s)
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```

---

### Post by Sycho.Squirrell on 2005-11-16
Not to worry, i solved my problem. Just moved my sources.list file to sources.backup and created a blank sources.list file. Ran apt-get update
when that completed, moved the sources.list file back and ran apt-get update again. Seems to have done the trick this time. Till next time i hope this is of some help!

---

### Post by cstudent on 2005-11-16
[QUOTE=Sycho.Squirrell]Not to worry, i solved my problem. Just moved my sources.list file to sources.backup and created a blank sources.list file. Ran apt-get update
when that completed, moved the sources.list file back and ran apt-get update again. Seems to have done the trick this time. Till next time i hope this is of some help![/QUOTE]

Excellent. That worked for me too. Thanks for passing on your wisdom.

Bill

---

### Post by bryan986 on 2005-11-17
Yes,  you can use that method, but then sooner or later it will break again, which is why they need to fix it and stop marking it as NOTABUG in bugzilla...

---

### Post by Oceola on 2005-11-17
[quote="aysiu"]What does your /etc/apt/sources.list looks like?[/quote]

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted.

All the other repositories have been updated and work fine. I also have all of them commented out through synaptics but have gone in and edited them for the updates manually through sudo gedit, but maintain the list throught the synaptics settings panels to show the disabled repositories. I'm on dialup and the multiple download of packages affects the speed mercilously.  

It's just the cd-rom disc which gives the gpg read error through synaptics anymore. Uncommented or through the apt-cdrom add command advised in the notice's panel.

---

