---
title: "Partial Upgrade wait"
date: 2012-02-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by williammanda on 2012-02-11
Anyone have any idea when the dependences will be resolved for this latest partial upgrade? I have been waiting since earlier Friday morning. It's been almost 30 hours. I'm trying to test mythtv but it is dependent on some of the files that are tyed up with the distribution upgrade.

PS
I have over 350 files waiting.

---

### Post by paul_in_london on 2012-02-11
> **williammanda said:**
> Anyone have any idea when the dependences will be resolved for this latest partial upgrade? I have been waiting since earlier Friday morning. It's been almost 30 hours. I'm trying to test mythtv but it is dependent on some of the files that are tyed up with the distribution upgrade.

PS
I have over 350 files waiting.

I have 4 packages held back at the moment:

```
paul@precise-64:~$ sudo aptitude full-upgrade
The following packages will be upgraded: 
  libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 libwebkitgtk-1.0-0{b} libwebkitgtk-3.0-0{b} 
4 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.8 MB of archives. After unpacking 182 kB will be freed.
The following packages have unmet dependencies:
  libwebkitgtk-3.0-0: Depends: libwebkitgtk-3.0-common (>= 1.7.5) but 1.7.4-0ubuntu1 is installed.
  libwebkitgtk-1.0-0: Depends: libwebkitgtk-1.0-common (>= 1.7.5) but 1.7.4-0ubuntu1 is installed.
The following actions will resolve these dependencies:

      Remove the following packages:                         
1)      evolution-data-server                                
2)      gnome-control-center                                 
3)      gnome-online-accounts                                
4)      gnome-session-fallback                               
5)      gnome-user-guide                                     
6)      gnome-web-photo                                      
7)      libfolks-eds25                                       
8)      libgoa-1.0-0                                         
9)      libwebkitgtk-1.0-0                                   
10)     libwebkitgtk-3.0-0                                   
11)     libyelp0                                             
12)     metacity                                             
13)     midori                                               
14)     mutter                                               
15)     ubuntu-docs                                          
16)     yelp                                                 
17)     zenity                                               

      Leave the following dependencies unresolved:           
18)     gedit recommends zenity                              
19)     gedit recommends yelp                                
20)     gnome-bluetooth recommends gnome-control-center      
21)     gnome-online-accounts recommends gnome-control-center
22)     gnome-terminal recommends yelp                       
23)     libfolks25 recommends libfolks-eds25                 
24)     mousetweaks recommends gnome-control-center          
25)     gnome-panel recommends gnome-session-fallback        
26)     gnome-panel recommends gnome-control-center          
27)     gnome-panel recommends evolution-data-server         
28)     gnome-shell recommends gnome-control-center          
29)     gnome-shell recommends gnome-session-fallback        
30)     gnome-shell recommends gnome-user-guide              


Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
paul@precise-64:~$
```

Maybe if you try **apt-get upgrade** or **aptitude safe-upgrade** you'll be able to upgrade some of yours.

---

### Post by keithpeter on 2012-02-11
Hello All

I've got 6 it wants to remove and 5 held back.

```
keith@xeon:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED
  apturl gir1.2-webkit-3.0 nautilus-share rhythmbox-plugins software-center
  ubuntu-desktop
The following NEW packages will be installed
  indicator-applet-complete libgstreamer-plugins-bad0.10-0 libopenal1
  libspandsp2 libvpx1 libzvbi-common libzvbi0 linux-headers-3.2.0-15
  linux-headers-3.2.0-15-generic linux-image-3.2.0-15-generic
The following packages have been kept back:
  gwibber libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0
  libwebkitgtk-1.0-0 libwebkitgtk-3.0-0
The following packages will be upgraded:
  apparmor gir1.2-javascriptcoregtk-3.0 gnome-control-center-data gnome-panel
  gnome-panel-data gstreamer0.10-plugins-bad kbd libavcodec-extra-53
  libavutil-extra-51 linux-generic linux-headers-generic linux-image-generic
  psmisc
13 upgraded, 10 newly installed, 6 to remove and 5 not upgraded.
Need to get 61.2 MB of archives.
After this operation, 212 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

---

### Post by mc4man on 2012-02-11
Same deal as the other thread on software-center, when the 1386 webkit build finishes & publishes you'll be able to proceed on 64 bit

---

### Post by williammanda on 2012-02-11
When the upgrades are available, please post.
Thanks

---

### Post by Harry33 on 2012-02-11
> **williammanda said:**
> When the upgrades are available, please post.
Thanks

See here for yourself:

[https://launchpad.net/ubuntu/precise/+source/webkit/1.7.5-0ubuntu3](https://launchpad.net/ubuntu/precise/+source/webkit/1.7.5-0ubuntu3)

---

### Post by williammanda on 2012-02-11
For my knowledge, how long does it take to go through the building process and is that only step or is there more to it?
Thanks

---

### Post by williammanda on 2012-02-11
> **Harry33 said:**
> See here for yourself:

[https://launchpad.net/ubuntu/precise/+source/webkit/1.7.5-0ubuntu3](https://launchpad.net/ubuntu/precise/+source/webkit/1.7.5-0ubuntu3)

Looked the site and I'm a little confused. I pulled up the 386 build at 6:30 and it said it had been working for 55 minutes. I just looked again at 7:28 and it said it had been working for 1 hour. Interesting it changed 5 minutes over an hour time span. But anyway...what is the expectation for completion?

---

### Post by paul_in_london on 2012-02-11
> **williammanda said:**
> Looked the site and I'm a little confused. I pulled up the 386 build at 6:30 and it said it had been working for 55 minutes. I just looked again at 7:28 and it said it had been working for 1 hour. Interesting it changed 5 minutes over an hour time span. But anyway...what is the expectation for completion?

Difficult to say really.

Just now I was able to do:

```
Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
paul@precise-64:~$ sudo aptitude full-upgrade^C
paul@precise-64:~$ sudo aptitude safe-upgrade                                   
Resolving dependencies...                
The following packages will be upgraded:
  desktop-base 
1 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 6,497 kB of archives. After unpacking 0 B will be used.
Do you want to continue? [Y/n/?] Y

```

It'll sort itself out eventually.

---

### Post by williammanda on 2012-02-11
Finally working!

---

