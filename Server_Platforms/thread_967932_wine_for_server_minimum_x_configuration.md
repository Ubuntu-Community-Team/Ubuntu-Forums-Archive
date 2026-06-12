---
title: "wine for server: minimum x configuration?"
date: 2008-11-02
forum: Server Platforms
---

### Post by ais77 on 2008-11-02
Hello!

I need to run one windoze application (USDownloader - to be exact) on my home Ubuntu 8.04 server (with SSH-only access, even no monitor attached).

Consider to use wine (as it worked with USD perfiectly on my previous Ubuntu 7.10 desktop installation).

Actually USD won't be used via any GUI interface (due to reasons described above) - I plan to use USD via it's web-interface only. So - I don't need any GUI output of USDf (and also - FineReader used by USD to do the recognition job).

My the questions are:
1. do I have to install xserver-xorg to run GUI-based apps under wine?
2. do I have to install any display managers (if so - will fluxbox be the smaller one?)
3. what should be the minimal settings of X and display managers to keep server-platform efficiency (in terms of RAM and CPU usage)? I.e. - 640x480x256 will be enough, let's say - if I don't care about GUI output - or not?
Thank you in advace for any suggestions or even directions to look trough.

---

### Post by dantrevino on 2008-12-09
I dont see xserver in the dependencies:


dan@chaos ~ % apt-cache showpkg wine
Package: wine
Versions: 
1.0.1-0ubuntu2 (/var/lib/apt/lists/ftp.usf.edu_pub_ubuntu_dists_intrepid_universe_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/ftp.usf.edu_pub_ubuntu_dists_intrepid_universe_binary-i386_Packages
                  MD5: fa993a61c86771e1ee226f191fbcb7af


Reverse Depends: 
  wine-gecko,wine
  pq,wine 0.9.46
  pptview,wine
  wine-dev,wine 1.0.1-0ubuntu2
  nsis,wine
  lmms,wine
  gnome-volume-manager,wine
  education-desktop-other,wine
Dependencies: 
1.0.1-0ubuntu2 - procps (0 (null)) binfmt-support (2 1.1.2) libasound2 (4 1.0.17) libaudio2 (0 (null)) libaudiofile0 (2 0.2.3-4) libc6 (2 2.7) libesd-alsa0 (18 0.2.35) libesd0 (2 0.2.35) libgl1-mesa-glx (16 (null)) libgl1 (0 (null)) libglu1-mesa (16 (null)) libglu1 (0 (null)) libgphoto2-2 (2 2.4.0) libgphoto2-port0 (2 2.4.0) libice6 (2 1:1.0.0) liblcms1 (2 1.15-1) libldap-2.4-2 (2 2.4.7) libsm6 (0 (null)) libx11-6 (0 (null)) libxau6 (0 (null)) libxext6 (0 (null)) libxml2 (2 2.6.27) libxslt1.1 (2 1.1.18) libxt6 (0 (null)) libxxf86vm1 (0 (null)) dpkg (2 1.14.12ubuntu3) msttcorefonts (0 (null)) xdg-utils (0 (null)) ttf-liberation (0 (null)) winbind (0 (null)) wine-gecko (0 (null)) binfmt-support (3 1.1.2) libwine (0 (null)) libwine-alsa (0 (null)) libwine-arts (0 (null)) libwine-capi (0 (null)) libwine-cms (0 (null)) libwine-esd (0 (null)) libwine-gl (0 (null)) libwine-gphoto2 (0 (null)) libwine-jack (0 (null)) libwine-ldap (0 (null)) libwine-nas (0 (null)) libwine-print (0 (null)) libwine-sane (0 (null)) libwine-twain (0 (null)) wine-doc (0 (null)) wine-utils (0 (null)) winesetuptk (0 (null)) xwine (0 (null)) libwine-alsa (0 (null)) libwine-arts (0 (null)) libwine-capi (0 (null)) libwine-cms (0 (null)) libwine-esd (0 (null)) libwine-gl (0 (null)) libwine-gphoto2 (0 (null)) libwine-jack (0 (null)) libwine-ldap (0 (null)) libwine-nas (0 (null)) libwine-print (0 (null)) libwine-sane (0 (null)) libwine-twain (0 (null)) wine-doc (0 (null)) wine-utils (0 (null)) winesetuptk (0 (null)) xwine (0 (null)) 
Provides: 
1.0.1-0ubuntu2 - 
Reverse Provides:

---

### Post by john-doe on 2009-04-28
Have you been able to achieve this implementation?

If you didn't and still interested I found a way.

X server is not a dependency on wine, but if an windows app run with wine wants to draw a window and no display is found it will simply die. A workarround to this is to use Xvfv ( a sort of virtual frame buffer). It will provide a display for the app to draw its windows on.
I will post a tutorial in my blog this week. There are some tutorials but are all a copy of an only one that I don't know who the original author is. But that tutorial does not explain that mono (under wine and installed through winetricks) is needed in order to run the VB.net(?) scripts to decrypt the Megaupload captcha (the process is VERY cpu-hungry though).
I even created an init script you can put into your init.d and link to a runlevel. I'll explain a lot more of the implementation on my blog though.

You can email me if I forget to update this post with the tutorial next week :p

PS: I thought I was the only one trying to achieve this.
PS2: There is a less painful way: using [JDownloader]("http://jdownloader.org/") which is java and will work just out of the box. But I like the hardest ways, you learn the most out of them ;)

---

