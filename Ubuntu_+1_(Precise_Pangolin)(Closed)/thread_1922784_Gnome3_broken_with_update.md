---
title: "Gnome3 broken with update"
date: 2012-02-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Bobhuber on 2012-02-09
Todays update 02/09/2012  has broken gnome. Not sure where to start. If I login under Unity,log out and then log in under gnome without rebooting  I can get to the desktop. At that point if I attempt to open anything the desktop freezes and forces reboot. If I attempt to boot into gnome (fresh boot) I get to the desktop with no launcher or functionality at all. 
Note all this is being done in virtualbox. I've attempted to boot into previous kernel with no success. It seems that the problem lies with the other updates (+50 meg). Booting into Unity seems to work OK.

---

### Post by Quackers on 2012-02-09
Have a look here
[http://ubuntuforums.org/showthread.php?t=1922796](http://ubuntuforums.org/showthread.php?t=1922796)

---

### Post by Bobhuber on 2012-02-09
> **Quackers said:**
> Have a look here
[http://ubuntuforums.org/showthread.php?t=1922796](http://ubuntuforums.org/showthread.php?t=1922796)
Oh well. Story of my life. Day late and a dollar short LOL.

---

### Post by Harry33 on 2012-02-09
Right, this seems to affect Unity in systems using nvidia-current.
Not Gnome-shell nor Gnome-panel.

---

### Post by sammiev on 2012-02-09
Gnome3 problems today after the updates as well. Been great till now so a little set back. :)

---

### Post by hugmenot on 2012-02-09
Well, gnome-shell freezes for me and I have Intel.

For me it was related to libcanberra.

---

### Post by jbicha on 2012-02-09
I'm getting occasional freezes also with Intel on GNOME Shell 3.2.

What makes you think this has anything to do with libcanberra?

---

### Post by DougieFresh4U on 2012-02-10
Well 'dist-upgrade' wanted to remove all this:
```
The following packages will be REMOVED:
  apturl{a} awn-applet-webapplet{a} banshee{a} banshee-extension-soundmenu{a} banshee-extension-ubuntuonemusicstore{a} cairo-dock{a} cairo-dock-core{u} cairo-dock-data{u} 
  cairo-dock-plug-ins{a} cairo-dock-plug-ins-integration{u} devhelp{a} empathy{a} evolution-data-server{a} gimp{a} gir1.2-gst-plugins-base-0.10{u} gir1.2-gstreamer-0.10{u} 
  gir1.2-gudev-1.0{u} gir1.2-javascriptcoregtk-3.0{u} gir1.2-rb-3.0{a} gir1.2-webkit-3.0{a} gnome-control-center{a} gnome-online-accounts{a} gnome-session-fallback{a} gnome-user-guide{a} 
  gwibber{a} indicator-datetime{a} indicator-power{a} libdevhelp-3-0{a} libdiscid0{u} libdmapsharing-3.0-2{u} libept1{u} libetpan15{u} libfolks-eds25{a} libgdata1.9-cil{u} libgoa-1.0-0{a} 
  libgtkglext1{u} libjavascriptcoregtk-1.0-0{u} libjavascriptcoregtk-3.0-0{u} libmusicbrainz3-6{u} libndesk-dbus-glib1.0-cil{u} libndesk-dbus1.0-cil{u} librhythmbox-core5{a} 
  libsyncdaemon-1.0-1{a} libubuntuone-1.0-1{a} libubuntuone1.0-cil{a} libvpx0{u} libwebkitgtk-1.0-0{a} libwebkitgtk-3.0-0{a} libyelp0{a} linux-headers-3.2.0-14{u} 
  linux-headers-3.2.0-14-generic{u} metacity{a} nautilus-sendto-empathy{a} nautilus-share{a} oneconf{a} python-debtagshw{u} python-mako{u} python-markupsafe{u} 
  python-ubuntuone-control-panel{a} python-webkit{a} rhythmbox{a} rhythmbox-data{u} rhythmbox-plugin-cdrecorder{a} rhythmbox-plugins{a} shotwell{a} software-center{a} 
  software-center-aptdaemon-plugins{u} ubuntu-desktop{a} ubuntu-docs{a} ubuntu-sso-client{a} ubuntuone-client{a} ubuntuone-client-gnome{a} ubuntuone-control-panel{a} 
  ubuntuone-control-panel-gtk{a} unity-2d{a} yelp{a} zenity{a} 
```
But of course I didn't go through with it. Normal 'upgrade' did just fine.
Just saying. :P

---

### Post by prusswan on 2012-02-10
> **DougieFresh4U said:**
> Well 'dist-upgrade' wanted to remove all this:
```
The following packages will be REMOVED:
  apturl{a} awn-applet-webapplet{a} banshee{a} banshee-extension-soundmenu{a} banshee-extension-ubuntuonemusicstore{a} cairo-dock{a} cairo-dock-core{u} cairo-dock-data{u} 
  cairo-dock-plug-ins{a} cairo-dock-plug-ins-integration{u} devhelp{a} empathy{a} evolution-data-server{a} gimp{a} gir1.2-gst-plugins-base-0.10{u} gir1.2-gstreamer-0.10{u} 
  gir1.2-gudev-1.0{u} gir1.2-javascriptcoregtk-3.0{u} gir1.2-rb-3.0{a} gir1.2-webkit-3.0{a} gnome-control-center{a} gnome-online-accounts{a} gnome-session-fallback{a} gnome-user-guide{a} 
  gwibber{a} indicator-datetime{a} indicator-power{a} libdevhelp-3-0{a} libdiscid0{u} libdmapsharing-3.0-2{u} libept1{u} libetpan15{u} libfolks-eds25{a} libgdata1.9-cil{u} libgoa-1.0-0{a} 
  libgtkglext1{u} libjavascriptcoregtk-1.0-0{u} libjavascriptcoregtk-3.0-0{u} libmusicbrainz3-6{u} libndesk-dbus-glib1.0-cil{u} libndesk-dbus1.0-cil{u} librhythmbox-core5{a} 
  libsyncdaemon-1.0-1{a} libubuntuone-1.0-1{a} libubuntuone1.0-cil{a} libvpx0{u} libwebkitgtk-1.0-0{a} libwebkitgtk-3.0-0{a} libyelp0{a} linux-headers-3.2.0-14{u} 
  linux-headers-3.2.0-14-generic{u} metacity{a} nautilus-sendto-empathy{a} nautilus-share{a} oneconf{a} python-debtagshw{u} python-mako{u} python-markupsafe{u} 
  python-ubuntuone-control-panel{a} python-webkit{a} rhythmbox{a} rhythmbox-data{u} rhythmbox-plugin-cdrecorder{a} rhythmbox-plugins{a} shotwell{a} software-center{a} 
  software-center-aptdaemon-plugins{u} ubuntu-desktop{a} ubuntu-docs{a} ubuntu-sso-client{a} ubuntuone-client{a} ubuntuone-client-gnome{a} ubuntuone-control-panel{a} 
  ubuntuone-control-panel-gtk{a} unity-2d{a} yelp{a} zenity{a} 
```
But of course I didn't go through with it. Normal 'upgrade' did just fine.
Just saying. :P

u are lying, that can only be a partial upgrade!

---

### Post by hugmenot on 2012-02-10
> **jbicha said:**
> I'm getting occasional freezes also with Intel on GNOME Shell 3.2.

What makes you think this has anything to do with libcanberra?

When I disable desktop sounds it stops freezing all the time:
[https://bugs.launchpad.net/bugs/929447](https://bugs.launchpad.net/bugs/929447)

---

### Post by dino99 on 2012-02-10
> **hugmenot said:**
> When I disable desktop sounds it stops freezing all the time:
[https://bugs.launchpad.net/bugs/929447](https://bugs.launchpad.net/bugs/929447)



was true yesterday when you reported it, but very late yesterday it was fixed, so you should not get that issue now, and marked your report as fixed if its true for you.

---

### Post by DougieFresh4U on 2012-02-10
> **prusswan said:**
> u are lying, that can only be a partial upgrade!
I see that SOME of the packages have sorted themselves out BUT this is whats showing now, and I only use terminal not update manager for updating:
```
dougie@oneric64bit:~$ **sudo aptitude dist-upgrade**
The following packages will be upgraded: 
  gir1.2-javascriptcoregtk-3.0 gir1.2-soup-2.4 gir1.2-webkit-3.0 language-pack-en language-pack-gnome-en libidl0 libjack-jackd2-0 libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 libnm-glib-vpn1 
  libnm-glib4 libnm-util2 libsoup-gnome2.4-1 libsoup2.4-1 libwebkitgtk-1.0-0{b} libwebkitgtk-3.0-0{b} network-manager 
17 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.7 MB of archives. After unpacking 15.4 kB will be freed.
The following packages have unmet dependencies:
  libwebkitgtk-3.0-0: Depends: libwebkitgtk-3.0-common (>= 1.7.5) but 1.7.4-0ubuntu1 is installed.
  libwebkitgtk-1.0-0: Depends: libwebkitgtk-1.0-common (>= 1.7.5) but 1.7.4-0ubuntu1 is installed.
The following actions will resolve these dependencies:

      Remove the following packages:                                                   
1)      apturl                                                                         
2)      awn-applet-webapplet                                                           
3)      banshee                                                                        
4)      banshee-extension-soundmenu                                                    
5)      banshee-extension-ubuntuonemusicstore                                          
6)      cairo-dock                                                                     
7)      cairo-dock-plug-ins                                                            
8)      devhelp                                                                        
9)      empathy                                                                        
10)     evolution-data-server                                                          
11)     gimp                                                                           
12)     gir1.2-rb-3.0                                                                  
13)     gir1.2-webkit-3.0                                                              
14)     gnome-control-center                                                           
15)     gnome-online-accounts                                                          
16)     gnome-session-fallback                                                         
17)     gnome-user-guide                                                               
18)     gwibber                                                                        
19)     indicator-datetime                                                             
20)     indicator-power                                                                
21)     libdevhelp-3-0                                                                 
22)     libfolks-eds25                                                                 
23)     libgoa-1.0-0                                                                   
24)     librhythmbox-core5                                                             
25)     libsyncdaemon-1.0-1                                                            
26)     libubuntuone-1.0-1                                                             
27)     libubuntuone1.0-cil                                                            
28)     libwebkitgtk-1.0-0                                                             
29)     libwebkitgtk-3.0-0                                                             
30)     libyelp0                                                                       
31)     metacity                                                                       
32)     nautilus-sendto-empathy                                                        
33)     nautilus-share                                                                 
34)     oneconf                                                                        
35)     python-ubuntuone-control-panel                                                 
36)     python-webkit                                                                  
37)     rhythmbox                                                                      
38)     rhythmbox-plugin-cdrecorder                                                    
39)     rhythmbox-plugins                                                              
40)     shotwell                                                                       
41)     software-center                                                                
42)     ubuntu-desktop                                                                 
43)     ubuntu-docs                                                                    
44)     ubuntu-sso-client                                                              
45)     ubuntuone-client                                                               
46)     ubuntuone-client-gnome                                                         
47)     ubuntuone-control-panel                                                        
48)     ubuntuone-control-panel-gtk                                                    
49)     unity-2d                                                                       
50)     yelp                                                                           
51)     zenity                                                                         

      Leave the following dependencies unresolved:                                     
52)     deja-dup recommends ubuntuone-client                                           
53)     deja-dup recommends ubuntuone-control-panel                                    
54)     empathy-common recommends yelp                                                 
55)     gcalctool recommends yelp                                                      
56)     gedit recommends zenity                                                        
57)     gedit recommends yelp                                                          
58)     gimp-data recommends gimp                                                      
59)     gnome-bluetooth recommends gnome-control-center                                
60)     gnome-control-center-data recommends gnome-control-center (>= 1:3.2.2-2ubuntu7)
61)     gnome-media recommends gnome-control-center                                    
62)     gnome-online-accounts recommends gnome-control-center                          
63)     gnome-terminal recommends yelp                                                 
64)     gucharmap recommends yelp                                                      
65)     indicator-datetime recommends evolution-data-server                            
66)     libfolks25 recommends libfolks-eds25                                           
67)     mousetweaks recommends gnome-control-center                                    
68)     rhythmbox-data recommends rhythmbox                                            
69)     unity recommends indicator-datetime                                            
70)     unity recommends indicator-power                                               
71)     unity-2d-panel recommends indicator-datetime                                   
72)     unity-greeter recommends indicator-datetime                                    
73)     unity-greeter recommends indicator-power                                       
74)     update-manager recommends gir1.2-webkit-3.0                                    
75)     avant-window-navigator recommends awn-applet-webapplet                         
76)     cairo-dock-core recommends cairo-dock                                          
77)     cairo-dock-core recommends cairo-dock-plug-ins                                 
78)     gnome-panel recommends gnome-session-fallback                                  
79)     gnome-panel recommends gnome-control-center                                    
80)     gnome-panel recommends evolution-data-server                                   


Accept this solution? [Y/n/q/?] 

```

---

### Post by Harry33 on 2012-02-10
The problem you have there is that the source webkit is not ready to be installed.
Packages libwebkitgtk-1.0-common and libwebkitgtk-3.0-common (v. 1.7.5) are still not yet built (there was a build failure).
So, by force installing libwebkitgtk-1.0-0 and libwebkit-3.0-0, at least these packages are removed:
gimp, gnome-control-center, gnome-session-fallback, libgoa-1.0-0, metacity and zenity.

When using development releases you need to know what you are doing.
You need to know when the complete source has not been thoroughly built and ready to be installed.
Otherwise, you just break your system.

Learn to use Synaptic. It will help a bit.

---

### Post by DougieFresh4U on 2012-02-10
> **Harry33 said:**
> The problem you have there is that the source webkit is not ready to be installed.
Packages libwebkitgtk-1.0-common and libwebkitgtk-3.0-common (v. 1.7.5) are still not yet built (there was a build failure).
So, by force installing libwebkitgtk-1.0-0 and libwebkit-3.0-0, at least these packages are removed:
gimp, gnome-control-center, gnome-session-fallback, libgoa-1.0-0, metacity and zenity.

When using development releases you need to know what you are doing.
You need to know when the complete source has not been thoroughly built and ready to be installed.
Otherwise, you just break your system.

Learn to use Synaptic. It will help a bit.
Yes I am aware of that. I was just messing around with the one that called me a liar regarding partial upgrades.\\:D/
I have been onboard with all the testing since I became a member of the forums and aware of 'you are using a development blah blah blah and expect breakage blah blah blah........' but I thank you for your input and you do give some great knowledge and I do read most of your post Harry33 :):)

---

### Post by prusswan on 2012-02-10
> **DougieFresh4U said:**
> Yes I am aware of that. I was just messing around with the one that called me a liar regarding partial upgrades.\\:D/
I have been onboard with all the testing since I became a member of the forums and aware of 'you are using a development blah blah blah and expect breakage blah blah blah........' but I thank you for your input and you do give some great knowledge and I do read most of your post Harry33 :):)

You would have done a partial upgrade as offered if you proceeded with yes, and that would be the most likely explanation for whatever breakage you may have

---

### Post by Bobhuber on 2012-02-10
Nothing but partial upgrades offered today (no I didn't). The desktop is pretty much unusable with gnome3 until they do something different. Constant crashes with everything. 
02/09/2012 10:00 PM - Eastern USA

---

### Post by DougieFresh4U on 2012-02-10
> **prusswan said:**
> You would have done a partial upgrade as offered if you proceeded with yes, and that would be the most likely explanation for whatever breakage you may have

No breakage, running smoothly.
I will check in the morning to see if all has sorted out or not.
I'm sorry to see that some people go through with partial
upgrades and then all the drama that comes with partial upgrades.

---

### Post by Harry33 on 2012-02-11
The build of the source webgit failed again.
See here:
[https://launchpad.net/ubuntu/precise/+source/webkit/1.7.5-0ubuntu3](https://launchpad.net/ubuntu/precise/+source/webkit/1.7.5-0ubuntu3)

The problem is that the 32-bit (i386) build failed. The *-common packages are there.
So neither architecture is installable.

---

### Post by dino99 on 2012-02-11
Here is the MAIN ERROR:

sudo aptitude dist-upgrade

dont use "dist-upgrade" if the release is not out (seems logic, but not for everyone :()

---

### Post by keithpeter on 2012-02-11
> **dino99 said:**
> dont use "dist-upgrade" if the release is not out (seems logic, but not for everyone :()

Hello dino99 and all

newbie to testing alert:

I've been doing dist-upgrades once a day usually later in the evening without any issues. i.e. no packages labelled as being removed. 

This morning, the dist-upgrade wanted to remove packages so I just did an upgrade instead.

I've been working on the assumption that the dist-upgrade command is the one I need to ensure that the newer kernels and base libraries get updated instead of being held back.

So, should I just be upgrading? 

If so, how do I track the newer kernels?

Code block below shows this morning's (Saturday 10am ish UK time zone) dist-upgrade results...

Because I just did an upgrade I still have 3.2.0-14-generic.

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
  checkbox checkbox-gtk cpp-4.6 debconf debconf-i18n firefox
  firefox-globalmenu firefox-gnome-support firefox-locale-en g++-4.6 gcc-4.6
  gcc-4.6-base gcc-4.6-base:i386 gir1.2-javascriptcoregtk-3.0
  gir1.2-panelapplet-4.0 gnome-control-center-data gnome-panel
  gnome-panel-data gstreamer0.10-plugins-bad indicator-messages
  indicator-status-provider-mc5 libavcodec-extra-53 libavutil-extra-51 libgcc1
  libgcc1:i386 libgfortran3 libgomp1 libgomp1:i386 libgwibber-gtk2 libgwibber2
  libindicate-gtk3 libindicate5 libindicator-messages-status-provider1
  libnih-dbus1 libnih1 libpanel-applet-4-0 libquadmath0 libstdc++6
  libstdc++6:i386 libstdc++6-4.6-dev libxi-dev libxi6 libxi6:i386
  linux-generic linux-headers-generic linux-image-generic login passwd
  policykit-1-gnome python-indicate telepathy-indicator wget
  x11proto-input-dev xserver-common xserver-xorg-core
  xserver-xorg-input-synaptics
56 upgraded, 10 newly installed, 6 to remove and 5 not upgraded.
Need to get 109 MB of archives.
After this operation, 212 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
```

---

### Post by dino99 on 2012-02-11
To clarify:

So, should I just be upgrading?  YES

If so, how do I track the newer kernels? Thats why the meta-package(s) exist :)

e.g. synaptic package description : 

 linux-generic-pae
This package will always depend on the latest complete generic Linux kernel
available.

---

