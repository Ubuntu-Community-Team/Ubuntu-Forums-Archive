---
title: "Can't run updates. libxaw7 conflict."
date: 2012-04-04
forum: Server Platforms
---

### Post by geonel on 2012-04-04
I updated from 11.10 to 12.04(Beta) recently but had a problem. Now I always get conflict errors and cannot run any updates. It all has to do with libxaw7:i386 which I believe is a vestige from install google earth and or picassa.

I get the following errors:

my_input_prompt:$ apt-get update -f
.
.
.

Errors were encountered while processing:
 libxaw7
 libxaw7:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
my_input_prompt:$ 

my_input_prompt:$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libgexiv2-0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libxaw7
The following packages will be upgraded:
  libxaw7
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/201 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libxaw7 (--configure):
 libxaw7:amd64 2:1.0.9-3 cannot be configured because libxaw7:i386 is in a different version (2:1.0.9-3ubuntu1)
dpkg: error processing libxaw7:i386 (--configure):
 libxaw7:i386 2:1.0.9-3ubuntu1 cannot be configured because libxaw7:amd64 is in a different version (2:1.0.9-3)
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libxaw7
 libxaw7:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
my_input_prompt:$ 


Any attempts to that I have tried so far to rectify the error cannot be done because of the error. Thanks for any help you can give me.

---

### Post by Paddy Landau on 2012-04-05
I see no one has answered you, so I'll give it a try, but I am not an expert so let's cross fingers.

Try these commands, in order. Continue even if one of them fails.
```
sudo apt-get purge libgexiv2-0
sudo apt-get update
sudo apt-get --fix-broken install
sudo dpkg --configure --pending
sudo apt-get dist-upgrade
```Reboot, then try the normal updates again. Let us know what happens.

---

### Post by geonel on 2012-04-05
All apt-get commands get hung up because of the conflict.
I went to package manager and using it was able to see the broken packages and removed libxaw7:i386 then installed libxaw7 and we appear to have removed the conflict. Sorry I'm not more knowledgeable to offer a better explanation. Thanks so much for trying to help.

I really needed to get this fixed because it was keeping me from fixing the adobe-flashplugin issue that I'm having that is making the golfers look like smurfs at the Masters tournament.

---

### Post by geonel on 2012-04-05
This is resolved. I don't know how to mark it so or even if I'm supposed to.

---

### Post by Paddy Landau on 2012-04-06
I'm glad you managed to solve the problem.

Here is how to [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

