---
title: "Help With Installing Dropbox"
date: 2019-03-03
forum: Ubuntu/Debian BASED
---

### Post by ivan23m on 2019-03-03
Hello

I need help with installing Dropbox, certain messages show up that you can see in screenshots and I am not sure what to do to complete the installation. I would ask for a step by step guide, I do use Linux a few years but I am not an expert. I use Zorin Lite 12.4.

Thank You

---

### Post by westie457 on 2019-03-03
Where did you get Dropbox from, it should be available in the repos.
Try this first., ```
 sudo apt -f install
```
Let us know what happens.

---

### Post by ivan23m on 2019-03-03
I installed it from the website dropbox.com/connect, scanned the image on the PC with my mobile device, then downloaded dropbox_2019.01.31_i386.deb, then installed it with sudo dpkg -i.

---

### Post by westie457 on 2019-03-03
Maybe I forgot something in my first reply. Try ```
sudo apt update
sudo apt upgrade
sudo apt install -f #No package names
```

If this fails to install the needed files post the complete terminal output back here between [code] tags, the second has /code between the straight brackets.
The screenshots are difficult to read.

Thankyou.

---

### Post by ivan23m on 2019-03-05
Can you clarify what " post the complete terminal output back here between [code] tags, the second has /code between the straight brackets'', especially "between [code] tags, the second has /code between the straight brackets''" means? And the last command, '''sudo install -f'', do you just write file name after that?

---

### Post by ajgreeny on 2019-03-05
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by ivan23m on 2019-03-05
```


ivan23m@ivan23m-desktop:~$ sudo apt update
[sudo] password for ivan23m: 
Hit:1 http://hr.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://hr.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:3 http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu xenial InRelease
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]     
Hit:5 http://hr.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Ign:6 http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu xenial InRelease
Hit:7 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial InRelease
Hit:9 http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu xenial InRelease
Hit:10 http://ppa.launchpad.net/zorinos/patches/ubuntu xenial InRelease        
Hit:11 http://ppa.launchpad.net/zorinos/stable/ubuntu xenial InRelease         
Err:12 http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu xenial Release
  404  Not Found
Ign:8 http://www.getdeb.net/ubuntu xenial-getdeb InRelease                     
Err:13 http://www.getdeb.net/ubuntu xenial-getdeb Release
  403  Forbidden
Hit:14 https://packages.zorinos.com/patches xenial InRelease
Hit:15 https://packages.zorinos.com/stable xenial InRelease
Reading package lists... Done 
W: Target Packages (apps/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages (apps/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Translations (apps/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Translations (apps/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11 (apps/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11-icons (apps/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
E: The repository 'http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.getdeb.net/ubuntu xenial-getdeb Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (apps/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages (apps/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Translations (apps/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Translations (apps/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11 (apps/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11-icons (apps/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
ivan23m@ivan23m-desktop:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ivan23m@ivan23m-desktop:~$ cd /home/ivan23m/Downloads/
ivan23m@ivan23m-desktop:~/Downloads$ sudo apt install -f dropbox_2019.01.31_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dropbox_2019.01.31_i386.deb
E: Couldn't find any package by glob 'dropbox_2019.01.31_i386.deb'
E: Couldn't find any package by regex 'dropbox_2019.01.31_i386.deb'


```

---

### Post by ajgreeny on 2019-03-05
Unfortunately using **dpkg -i** will not deal with any missing dependencies in the way that apt does.

You can either install gdebi and use that to install the dropbox_2019.01.31_i386.deb package, or if zorin allows you can try ```
sudo apt install /path/to/dropbox_2019.01.31_i386.deb
```

---

### Post by ivan23m on 2019-03-05
I have actually managed to install it on my own an hour ago. Thank you.

---

### Post by ajgreeny on 2019-03-05
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction and also let us know what the solution was as it is a great help to users with the same problem searching the forum.

---

