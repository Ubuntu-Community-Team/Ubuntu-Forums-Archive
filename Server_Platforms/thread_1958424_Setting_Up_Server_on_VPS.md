---
title: "Setting Up Server on VPS"
date: 2012-04-14
forum: Server Platforms
---

### Post by jonedney on 2012-04-14
Hello everone.

I'm relatively new to Linux and I'm very fascinated by Ubuntu, so I've decided to use my VPS and Ubuntu 10.04 LTS to set up my web server for my web sites.

I'm currently going through an installation wiki for ISPConfig 3 for installing the software on an Ubuntu server from scratch.  I've made it to the point in the installation where it's requesting that I install Apache, but it doesn't seem to install.  Below is some output.

I enter:
```
apt-get install apache2
```

I see:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-worker apache2.2-bin apache2.2-common
Suggested packages:
  apache2-suexec apache2-suexec-custom ufw
The following NEW packages will be installed:
  apache2 apache2-mpm-worker
The following packages will be upgraded:
  apache2.2-bin apache2.2-common
2 upgraded, 2 newly installed, 0 to remove and 42 not upgraded.
Need to get 0B/3035kB of archives.
After this operation, 127kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

Obviously, I select Y and hit enter, to see:
```
apache2 (2.2.15-1) unstable; urgency=low

  * This release adds and enables mod_reqtimeout, which limits the time
    Apache waits for a client to send a complete request. This helps to
    mitigate against certain denial of service attacks. In case of problems
    with slow clients, the timeout values can be adjusted in
    /etc/apache2/mods-available/reqtimeout.conf , or the module can be
    disabled with "a2dismod reqtimeout".

 -- Chuck Short <zulcss@ubuntu.com> Tue, 13 Apr 2010 09:09:34 -0400

/tmp/tmp4jDY5v (END)
```

It does not do anything else after this, I have to Ctrl+C to get back to the root command prompt.  When I try and verify the installation by running 'apache2 -V' I get this error:
```
-bash: apache2: command not found
```

If anyone can provide some insight, I would appreciate it.  This has been a great learning experience, as I've downloaded Ubuntu 12.04 LTS Beta and have been playing with it on my desktop also.

Thank you,
Jon

---

### Post by jonedney on 2012-04-14
As a reference, this is the URL to the installation steps I am currently working on.  Step 14 is where Apache is installed.  I've also tried to install Apache separate due to the error as mentioned above, without luck.

Thank you,
JOn

---

### Post by roelforg on 2012-04-14
What does apt-get say before that message where it hangs?
I think it's either unpacking or configuring and that takes time.

---

### Post by jonedney on 2012-04-14
The moment I say Yes to wanting to install, it immediately goes to that message.

It may be worth noting, that it seems like it is a "new screen" within PuTTy (if that makes sense).  When I hit yes, all the previous lines disapear and that message shows up.  

Additionally, I've let it sit on that screen for roughly 10-15 minutes in case it was working and there was just no indication, but still nothing.

Thank you,
Jon

---

### Post by sj1410 on 2012-04-14
did you try doing a apt-get update before doing a apt-get install.

---

### Post by jonedney on 2012-04-14
Hello,

Yes, I did run the update prior to trying to install Apache.  I just ran it again and here is where it is pulling updates from, maybe these links aren't current?


```
root@server:~# apt-get update
Hit http://archive.ubuntu.com lucid Release.gpg
Hit http://archive.ubuntu.com lucid-updates Release.gpg
Hit http://archive.ubuntu.com lucid-security Release.gpg
Hit http://archive.ubuntu.com lucid Release
Hit http://archive.ubuntu.com lucid-updates Release
Hit http://archive.ubuntu.com lucid-security Release
Hit http://archive.ubuntu.com lucid/main Packages
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/universe Packages
Reading package lists... Done
```

Thanks,
Jon

---

### Post by sj1410 on 2012-04-14
links are latest, 

try 

```

apt-get clean
apt-get install apache2

```

---

### Post by jonedney on 2012-04-14
The apt-get clean command didn't output any feedback, is that how it is supposed to work?

Additionally, there are a couple additional lines that showed up this time, prior to my original posted message.


```
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid-updates/main apache2.2-common 2.2.14-5ubuntu8.9 [291kB]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid-updates/main apache2.2-bin 2.2.14-5ubuntu8.9 [2740kB]
Get:3 http://archive.ubuntu.com/ubuntu/ lucid-updates/main apache2-mpm-worker 2.2.14-5ubuntu8.9 [2366B]
Get:4 http://archive.ubuntu.com/ubuntu/ lucid-updates/main apache2 2.2.14-5ubuntu8.9 [1488B]
Fetched 3035kB in 5s (540kB/s)
Reading changelogs... Done

```

After the reading changelogs line, it goes to the message from my original post.

Thank you,
Jon

---

### Post by sj1410 on 2012-04-14
apt-get clean deletes the downloaded .deb files from cache, the new message shows them downloading again.

try 

```

aptitude install apache2

```

and paste the complete output

---

### Post by jonedney on 2012-04-14
```
root@server:~# aptitude install apache2
-bash: aptitude: command not found
```

I ran into this problem earlier when I was running commands.  I wasn't able to find information on if that command not working was an OS defect or not, so I was using 'apt-get' instead.

Thank you,
Jon

---

### Post by sj1410 on 2012-04-14
Aptitude is installed by default in all version prior to Maverick. anyways try

```

apt-get install aptitude

```

---

### Post by jonedney on 2012-04-14
I've ran 'apt-get install aptitude' and it was successful.  I ran 'aptitude install apache2' and receive the same error as initially reported.

This version of Ubuntu I am running is whatever is considered 'default'.  Prior to beginning to install any applications on my VPS, should there have been any adjustments to the OS that I may not be aware of since I'm new to Linux?  I did run 'apt-get update' and updated the system before beginning this process.

Thank you,
Jon

---

### Post by jonedney on 2012-04-14
Bump.

I've been researching around the net all day and can't seem to find anything that would explain this.

Thank you,
Jon

---

### Post by jonedney on 2012-04-14
Well, oddly enough this script seems to have done the trick:

apt-get install apache2 apache2-utils

---

### Post by haqking on 2012-04-14
glad you got it sorted.

Feel free to come on IRC anytime for assistance.

and remember no need to logon as root as sudo is preferred, its ok if you know what you are doing but by your own admission your new to it so start of with best practices.

read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

Peace

---

### Post by jonedney on 2012-04-16
Thank you for your help and your tips.  I'm definitely having continued interest and looking forward to getting to know Linux & Ubuntu more, and be able to help instead of be helped.

Thanks again!
Jon

---

