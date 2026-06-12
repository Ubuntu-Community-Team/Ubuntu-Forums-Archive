---
title: "Apparmor profile skype 4.1.0.20 - Ubuntu 12.04"
date: 2012-11-25
forum: Security
---

### Post by NikTh on 2012-11-25
Hello , 

I've found a working apparmor profile for skype. I want to restrict this program. 
```
**apt-cache policy skype**
skype:
  Installed: 4.1.0.20.0-0ubuntu0.12.04.1
  Candidate: 4.1.0.20.0-0ubuntu0.12.04.1
  Version table:
 *** 4.1.0.20.0-0ubuntu0.12.04.1 0
        500 http://archive.canonical.com/ubuntu/ precise/partner i386 Packages
        100 /var/lib/dpkg/status
``````
**lsb_release -rcd ; uname -r** 
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
3.2.0-33-generic-pae
```
_Here is the apparmor-profile I use right now. _

```
#include <tunables/global>
 /usr/bin/skype {
    #include <abstractions/base>
    #include <abstractions/user-tmp>
    #include <abstractions/audio>
    #include <abstractions/nameservice>
    #include <abstractions/ssl_certs>
    #include <abstractions/fonts>
    #include <abstractions/X>
    #include <abstractions/freedesktop.org>
    #include <abstractions/kde>
     /usr/bin/skype mr,
    /opt/skype/skype pix,
    /opt/skype/** kmr,
    /usr/share/fonts/X11/** m,
     @{PROC}/*/net/arp r,
    @{PROC}/sys/kernel/ostype r,
    @{PROC}/sys/kernel/osrelease r,
     /dev/ r,
    /dev/tty rw,
        /dev/snd/* mrw,
        /dev/shm/ r,
        /dev/shm/pulse-shm-* mrw,
    /etc/pulse/client.conf r,
    /dev/pts/* rw,
    /dev/video* mrw,
    /var/lib/dbus/machine-id r,
    @{HOME}/Downloads/* krw,
    @{HOME}/Downloads/ krw,
     /etc/xdg/Trolltech.conf rk,
    /usr/share/locale-langpack/* mr,
    /usr/share/glib-2.0/schemas/gschemas.compiled rm,
    /sys/devices/system/cpu/cpu0/cpufreq/* r,
     @{HOME}/.Skype/ rw,
    @{HOME}/.Skype/** krw,
    /usr/share/skype/** kmr,
    /usr/share/skype/sounds/*.wav kr,
     deny @{HOME}/.mozilla/ r, # no idea what it needs there
    deny @{PROC}/[0-9]*/fd/ r,
    deny @{PROC}/[0-9]*/task/ r,
    deny @{PROC}/[0-9]*/task/** r,
 }
```Found it [here]("http://eternalwalkabout.wordpress.com/2012/08/07/skype-4-0-on-ubuntu-12-04-apparmor/"). 

Is there a way to improve it ? I'm calling the apparmor guru guys here. I'm ready to test any improvement. 

Thanks

---

### Post by Zburatorul on 2012-12-02
I think this is a majorly important thread. I just installed this profile as well. Seems to work so far. Caught skype trying to access /etc/passwd. I wonder for what purposes.

Note: running 12.04, skype 4.1.0.20, aa-enforce-ing skype with the profile from [http://eternalwalkabout.wordpress.com/2012/02/01/ubuntu-11-10-skype-apparmor-profile/](http://eternalwalkabout.wordpress.com/2012/02/01/ubuntu-11-10-skype-apparmor-profile/)

---

### Post by Soul-Sing on 2012-12-02
why in /opt? The new release comes with reg. updates.
why copy/paste complete profiles? when you could make your own?
whereis skype: skype: /usr/bin/skype /usr/bin/X11/skype /usr/share/skype

---

### Post by DanR01 on 2012-12-02
[FONT=Arial] 			 		   		 		 		> I think this  is a majorly important thread. I just installed this profile as well.  Seems to work so far. Caught skype trying to access /etc/passwd. I  wonder for what purposes.

The command 

```
ls -l
```

accesses /etc/passwd. Your encrypted password is stored in /etc/shadow. [FONT=Arial]/etc/passwd [/FONT]is used to map user IDs to usernames. It is not a sign that Skype is trying to subvert your system.


[/FONT]

---

### Post by Zburatorul on 2012-12-02
> **DanR01 said:**
> [FONT=Arial] 			 		   		 		 		

The command 

```
ls -l
```

accesses /etc/passwd. Your encrypted password is stored in /etc/shadow. [FONT=Arial]/etc/passwd [/FONT]is used to map user IDs to usernames. It is not a sign that Skype is trying to subvert your system.


[/FONT]

I had in the meantime done some googling to discover what you just wrote. Okay, so that's not bad.

Nevertheless, any specific fear aside, I think I would still like to start a general practice of creating profiles for any closed-source applications that I need to run.

---

### Post by NikTh on 2012-12-02
> **Zburatorul said:**
>  I think I would still like to start a general practice of creating profiles for any closed-source applications that I need to run.
Me too :) 

So I posted this profile and waiting for improvements - additions and/or unnecessary entries like @Soul-Sing mentioned. 

Well , the best restriction (for me) remains the VB. (something like sandbox) , but apparmor is there (pre-installed) and I want to learn how to use it. 

I'm not capable (right now) to create my own profiles , I'm reading posts - tutorials - forum stickies .. I will figure it out sometime.  :) 

Thanks for answers

---

### Post by vasa1 on 2012-12-02
> **NikTh said:**
> ...
So I posted this profile and waiting for improvements - additions and/or **unnecessary** entries ...
In the profile in the first post, there is this: "#include <abstractions/kde>". Do you think it is necessary if you're not running Kubuntu? Or is Skype a qt app that somehow needs some kde stuff? Farther down there's "/etc/xdg/Trolltech.conf rk," which may also be qt-related.

BTW, the default evince profile also has "/etc/passwd r,".

---

### Post by NikTh on 2012-12-03
> **vasa1 said:**
> In the profile in the first post, there is this: "#include <abstractions/kde>". Do you think it is necessary if you're not running Kubuntu? Or is Skype a qt app that somehow needs some kde stuff? Farther down there's "/etc/xdg/Trolltech.conf rk," which may also be qt-related.

BTW, the default evince profile also has "/etc/passwd r,".

Hey , thanks vasa1 :) 

Yes I understood this about kde entries . Are not necessary if you don't use KDE. And Trolltech.conf is also for Kde , yes. 

**cat /etx/xdg/Trolltech.conf**
```
[qt]
4.8\libraryPath=/usr/lib/kde4/plugins
``` 
Of course Library Path not exist at my installation. 

I'm reading to understand what this **#include <abbstractions/blah..blah>** are and which of these I have to use , and when.. 
the other configurations  , I think I understand them.. (about the paths - allow - deny and the permissions ,r,m,k,....) 

Thanks

---

