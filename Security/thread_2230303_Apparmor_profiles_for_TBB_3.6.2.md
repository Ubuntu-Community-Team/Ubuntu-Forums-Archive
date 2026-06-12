---
title: "Apparmor profiles for TBB 3.6.2"
date: 2014-06-18
forum: Security
---

### Post by Nobody Nessie on 2014-06-18
I hope my question will be in the good forum. I already removed all applications that I do not need (and that I will never need) and all the others that have something to do with Internet have their own apparmor profiles defined and "enforced". I am looking for an OpenBSD router, but later, maybe ! However, in my Internet applications "chain", it happens that I use Tor (TBB exactly), but almost only as a daemon (I do not use the Tor Bundle Browser as I do not really need it). The problem (and advantage) is that the TorProject update their TBB as soon as a vulnerability or bug is discovered. It is easy to update : Installing the new one in place of the old one. But here is my problem : I am not skilled enough to adapt their respective apparmor profiles each time. The following are those I found [here](https://github.com/adrelanos/Inoffical-TBB-AppArmor) (3 of them were enough and perfectly working on my computer with the TBB 3.6.0) :  

home.nobody.tor-browser_en-US.Browser.firefox :  

```
# Last Modified: Mon Dec 16 15:39:17 2013 #include   /home/nobody/tor-browser_en-US/Browser/firefox {   #include    #include     network tcp,    deny /etc/host.conf r,   deny /etc/hosts r,   deny /etc/nsswitch.conf r,   deny /etc/resolv.conf r,   deny /proc/*/mountinfo r,   deny @{HOME}/.config/user-dirs.dirs r,   deny @{HOME}/.gtk-bookmarks r,   deny @{HOME}/.local/share/recently-used.xbel* rw,    /bin/dash rix,   /dev/dri/card0 rw,   /etc/X11/cursors/* r,   /etc/drirc r,   /etc/fonts/** r,   /etc/gnome-vfs-2.0/modules/ r,   /etc/gnome-vfs-2.0/modules/default-modules.conf r,   /etc/gnome-vfs-2.0/modules/extra-modules.conf r,   /etc/mailcap r,   /etc/mime.types r,   /etc/passwd r,   /lib{,32,64}/*.so mr,   /lib{,32,64}/*.so.* mr,   /home/nobody/tor-browser_en-US/.mozilla/ w,   /home/nobody/tor-browser_en-US/.mozilla/*/ w,   /home/nobody/tor-browser_en-US/Browser/** r,   /home/nobody/tor-browser_en-US/Browser/*.so mr,   /home/nobody/tor-browser_en-US/Browser/browser/components/*.so mr,   /home/nobody/tor-browser_en-US/Browser/components/*.so mr,   /home/nobody/tor-browser_en-US/Browser/firefox rix,   /home/nobody/tor-browser_en-US/Data/Browser/ r,   /home/nobody/tor-browser_en-US/Data/Browser/** rwk,   /home/nobody/tor-browser_en-US/Desktop/ rw,   /home/nobody/tor-browser_en-US/Desktop/** rw,   /home/nobody/tor-browser_en-US/Downloads/ rw,   /home/nobody/tor-browser_en-US/Downloads/** rw,   /home/nobody/tor-browser_en-US/Tor/tor Px,   /run/** r,   /sys/devices/system/cpu/present r,   /tmp/.X0-lock r,   /usr/lib{,32,64}/** mr,   /usr/share/fonts/** r,   /usr/share/** r,   /var/cache/fontconfig/* r,   owner @{HOME}/.config/** r,   owner @{HOME}/.icons/ r,   owner @{HOME}/.icons/** r,   owner @{HOME}/.local/share/icons/ r,   owner @{HOME}/.themes/** r,   @{PROC}/[0-9]*/maps r,   @{PROC}/[0-9]*/mounts r,   @{PROC}/[0-9]*/stat r,   @{PROC}/[0-9]*/task/*/stat r,   @{PROC}/cpuinfo r,   @{PROC}/filesystems r,   @{PROC}/meminfo r,   @{PROC}/stat r,  }
```   


home.nobody.tor-browser_en-US.start-tor-browser :  

```
# Last Modified: Fri Sep 27 11:10:44 2013 #include   /home/nobody/tor-browser_en-US/start-tor-browser {   #include    #include     capability sys_ptrace,     /bin/cat rix,   /bin/dash ix,   /bin/grep rix,   /bin/ps rix,   /bin/sed rix,   /dev/pts/[0-9]* rw,   /dev/tty rw,   /etc/magic r,   /home/nobody/tor-browser_en-US/Browser/firefox Px,   /home/nobody/tor-browser_en-US/Tor/tor r,   /home/nobody/tor-browser_en-US/start-tor-browser r,   @{PROC}/ r,   @{PROC}/[0-9]*/status r,   @{PROC}/[0-9]*/stat r,   @{PROC}/[0-9]*/cmdline r,   @{PROC}/meminfo r,   @{PROC}/sys/kernel/pid_max r,   @{PROC}/tty/drivers r,   @{PROC}/uptime r,   /{,var/}run/utmp r,   /dev/ptmx rw,   /usr/bin/dirname rix,   /usr/bin/expr rix,   /usr/bin/file rix,   /usr/bin/getconf rix,   /usr/bin/id rix,   /usr/bin/ldd rix,   /usr/lib{,32,64}/** mr,   /usr/share/file/magic.mgc r,   /usr/share/file/magic/ r,  }
```   


home.nobody.tor-browser_en-US.Tor.tor :  

```
# Last Modified: Sat Sep 28 08:34:35 2013 #include   /home/nobody/tor-browser_en-US/Tor/tor {   #include     network tcp,   network udp,    /etc/host.conf r,   /etc/nsswitch.conf r,   /etc/passwd r,   /etc/resolv.conf r,   /home/nobody/tor-browser_en-US/Tor/tor mr,   /home/nobody/tor-browser_en-US/Data/Tor/* rw,   /home/nobody/tor-browser_en-US/Data/Tor/lock rwk,   /home/nobody/tor-browser_en-US/Lib/*.so mr,   /home/nobody/tor-browser_en-US/Lib/*.so.* mr,   @{PROC}/meminfo r,   @{PROC}/sys/kernel/random/uuid r,   /sys/devices/system/cpu/ r,  }
```  

I tried to disable them one by one to find where to search, but I got nothing interesting. Maybe some other members of this forum are in the same situation, or have already found the solution ? In fact, the only thing I care, it is to enforce the right application(s), the one (or those) that can be attacked/exploited from Internet (e.g. my TBB has never any acess to Internet, but I may be wrong : all applications are as a systemic whole that can be attacked : start-tor-browser, Tor and Firefox ?). But I am still working on it ! :D Thanks !

---

### Post by Nobody Nessie on 2014-06-20
Excepted for small details, you can add the following line in "home.nobody.tor-browser_en-US.Tor.tor" to get bridges :

```
/home/nobody/tor-browser_en-US/Tor/PluggableTransports/obfsproxy.bin Ux,
```

---

### Post by Meebee on 2014-07-03
The thread title says your problem has been solved... So does that mean you have working TBB 3.6.2 profiles for Ubuntu 14.04?

---

