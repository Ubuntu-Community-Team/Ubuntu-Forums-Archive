---
title: "What happened to Mplayer, Win32 codecs and Acroread?"
date: 2005-04-29
forum: Repositories &amp; Backports
---

### Post by Blob on 2005-04-29
Newbie has followed the ubuntuguide.org to the letter and I can't get the above noted programs installed using apt-get. I'm able to download and install almost everything else that I want.

Apparently these packages are no longer there. Have these programs been discontinued?

thanks

---

### Post by Professor X on 2005-04-29
Did you enable the extra repositories?  Did you remember to type ```
sudo apt-get update
```?

---

### Post by Blob on 2005-04-29
Yes, I did uncomment all the reposotories as per the guide, perhaps, I did not do it right? I will try to do it again.

Am I right in assuming that Mplayer is a program and not just a reference to any multiplayer?

Thanks.

---

### Post by Blob on 2005-04-29
This is what I typed in and this is what I got. I checked the repositories and they are uncommented as per the guide instructions:




bob@ubuntu:~$ sudo apt-get -t hoary install mplayer-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-386

---

### Post by Leif on 2005-04-29
It's not just uncommenting, you also need to add the marillat repositories. Have you done this ?

---

### Post by mendicant on 2005-04-29
Use aptitude in preference to apt-get.
Make sure you have multiverse in /etc/apt/sources.list:
```

% grep multiverse /etc/apt/sources.list | grep -v " *#"

```
Make sure you've updated your list of packages:
```

% sudo aptitude update
% aptitude search mplayer ## results in something like the following:
v   mplayer                         -
v   mplayer-386                     -
i   mplayer-586                     - The Ultimate Movie Player For Linux
v   mplayer-686                     -
v   mplayer-custom                  -
v   mplayer-doc                     -
i A mplayer-fonts                   - Fonts for mplayer
v   mplayer-k6                      -
v   mplayer-k7                      -
v   mplayer-nogui                   -

```

Now:

% sudo aptitude install mplayer-386 

should work.

---

### Post by mendicant on 2005-04-29
Oh, and the grep should return you at least one line indicating that you've got multiverse in your sources.list.

---

### Post by Blob on 2005-04-29
Hi Mendicant, I inserted the line below in a terminal window and nothing happened:

grep multiverse /etc/apt/sources.list | grep -v " *#"

I then did sudo aptitude update and got this:

bob@ubuntu:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary Release
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates Release [16.8kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/restricted Sources
Fetched 34.1kB in 3s (10.3kB/s)
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
bob@ubuntu:~$ aptitude search mplayer
E: /home/bob/.aptitude/config - Unable to open %s for writing (13 Permission denied)
bob@ubuntu:~$


Can you let me know what to type exactly the way they do it in the unbunguguide.org? I'm too new to linux, so nothing is obvious.
Thanks,

---

### Post by Blob on 2005-04-29
[QUOTE=Leif]It's not just uncommenting, you also need to add the marillat repositories. Have you done this ?[/QUOTE]
 How do you add the marillat repositories?

Thanks,

---

### Post by Leif on 2005-04-29
Please follow these instructions : [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by Blob on 2005-04-29
What a moron I am---I did not notice that more repositories were added after uncommenting----Thanks for That!! That will teach not to read carefully.

---

