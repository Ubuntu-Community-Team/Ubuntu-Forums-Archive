---
title: "Can't install google chrome."
date: 2017-03-28
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2017-03-28
Here is the out put:

```
henry@wyatt:~$ cd Downloads
henry@wyatt:~/Downloads$ ls -a
.  ..  google-chrome-stable_current_amd64.deb
henry@wyatt:~/Downloads$ sudo apt install google-chrome-stable_current_amd64.deb
[sudo] password for henry:          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package google-chrome-stable_current_amd64.deb
E: Couldn't find any package by glob 'google-chrome-stable_current_amd64.deb'
E: Couldn't find any package by regex 'google-chrome-stable_current_amd64.deb'
henry@wyatt:~/Downloads$
```

I tried software installer but it would not respond.

Henry

---

### Post by cariboo on 2017-03-28
try:

```
sudo apt install ./google-chrome-stable_current_amd64.deb
```

---

### Post by Hewjr100 on 2017-03-28
Here is the output:


```
henry@wyatt:~/Downloads$ sudo apt install ./google-chrome-stable_current_amd64.deb
[sudo] password for henry:          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'google-chrome-stable' instead of './google-chrome-stable_current_amd64.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 google-chrome-stable : Depends: libappindicator1 but it is not installable
E: Unable to correct problems, you have held broken packages.
henry@wyatt:~/Downloads$ cd
henry@wyatt:~$ sudo apt install libappindicator1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libappindicator1
henry@wyatt:~
```

---

### Post by Hewjr100 on 2017-03-28
Ok ran the following:

```
sudo apt --fix-broken install
```

After that it installed properly.

Henry

---

### Post by Cavsfan on 2017-03-29
I just installed it **sudo apt install chromium-browser** and it installed without any problem.

```
cavsfan@Le-Beast:~$ apt-cache policy chromium-browser
chromium-browser:
  Installed: 56.0.2924.76-0ubuntu2.1343
  Candidate: 56.0.2924.76-0ubuntu2.1343
  Version table:
 *** 56.0.2924.76-0ubuntu2.1343 500
        500 http://us.archive.ubuntu.com/ubuntu zesty/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

