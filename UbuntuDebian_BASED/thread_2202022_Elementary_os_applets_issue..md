---
title: "Elementary os applets issue."
date: 2014-01-27
forum: Ubuntu/Debian BASED
---

### Post by robert49 on 2014-01-27
Hi comunity. 
I have just installed elementary OS and I want some of the beautiful applets ubuntu has. I have installed them but they don't work, first of all the weather indicator does not start at all for me to do the settings. Then the cpu meter does not apear on the top bar. Is this a general problem or am I doing something wrong?

---

### Post by RadicaX on 2014-01-27
Ahh Welcome to the forums. To let you know, it might of been easier to get a reply for Elementary OS in the other OS/distro support a little lower on the forums.

Could you give a bit more information perhaps about your set up too? Like what is your computer like? What Graphics card does it use, the specs. Some of the Applets are based on that Cairo-dock thing I imagine you mean? like under the cafe and where people show snapshots of their desktops?

I might not be able to help much, I most certainly will try, and I know if someone else sees your problem, I am sure they will help.

---

### Post by robert49 on 2014-01-27
[FONT=arial]Oh that was a fast reply. I apreciate that! Aftev the "[COLOR=#000000]lshw -C video" I have a ATI radeon HD 4650 with 1gb of video memory. 4 gigs of RAM and a 2.66 quad core Intel processor. SO i understand I have posted in the wrong section,I am sorry because i don't want to bother any admin/mod with moving my post :(. This situation will not repeat.

Edit : also i have a bit of lag, what can be the cause? I installed the os by a tutorial in youtube ^^[/COLOR][/FONT]

---

### Post by mörgæs on 2014-01-27
> **RadicaX said:**
> it might of been easier to get a reply for Elementary OS in the other OS/distro support a little lower on the forums.


Yes, moved.

---

### Post by robert49 on 2014-01-27
Thank you kind sir ^^

---

### Post by robbie 348 on 2014-01-27
This page gives some good info post install of EoS
[http://www.elementaryupdate.com/2013/08/top-things-to-do-after-installing-luna.html](http://www.elementaryupdate.com/2013/08/top-things-to-do-after-installing-luna.html)

---

### Post by robert49 on 2014-01-27
I have installed most of the stuff in there, found another weather indicator different than "my weather indicator". It starts but it doesn't let me choose the location. Some sort of bug i read on the internet.

---

### Post by RadicaX on 2014-01-27
Okay thank you for all the info. Hmm, and you followed the instructions on this site you say? Hmm, it sounds like some of the packages might be messed up or something. You could try re-installing the weather indicator. What is it? Is it the Gazette one found on the site? 

```
cd /etc/gazette
```

```
ls
```

if you do not use Gazette, just change the name with the program you do use, we will be able to see the files in there and check if anything is missing I would imagine. (Comparing can be of great help when you are unsure.)

You could also report the apps to the people that make it, this might help you. And do you have your firewall up? That could be blocking it going to the net to check for things.

---

### Post by robert49 on 2014-01-28
Well lots of reports have been made. The issue is under observation. I tried gazette but it is sorta spaz out at the begining when i open it via terminal. It goes crazy and i need to click it to become clear so i just uninstalled it. I guess i have to wait for the applets to get fixed. Many people have this issue so i think they will hurry a update that will probably fix the bugs. I also tried Bucharest as the capital of my country and it still didn't work, i tried London and it was the same story. I will keep searching. I tried like 2-3 types of fixes with dconf Editor and installing new versions but after all it was the same story. I am using Weather Indicator ( not my weather indicator, this one is not even starting) and the cd command is not working :-s robert@Robert-Computer:~$ cd /etc/indicator-weatherbash: cd: /etc/indicator-weather: No such file or directory .


EDIT : 
```
 robert@Robert-Computer:~$ cd /etc/ indicator-weatherrobert@Robert-Computer:/etc$ ls
acpi                    hdparm.conf          pcmcia
adduser.conf            host.conf            perl
adjtime                 hostname             pkcs11
alternatives            hosts                pm
anacrontab              hosts.allow          pnm2ppa.conf
apg.conf                hosts.deny           polkit-1
apm                     hp                   ppp
apparmor                icedtea-web          preload.conf
apparmor.d              ifplugd              profile
apport                  ImageMagick          profile.d
apt                     init                 protocols
at.deny                 init.d               pulse
ati                     initramfs-tools      python
at-spi2                 inputrc              python2.7
avahi                   insserv              rc0.d
bash.bashrc             insserv.conf         rc1.d
bash_completion         insserv.conf.d       rc2.d
bash_completion.d       iproute2             rc3.d
bindresvport.blacklist  issue                rc4.d
blkid.conf              issue.net            rc5.d
blkid.tab               java-6-openjdk       rc6.d
bluetooth               kbd                  rc.local
brlapi.key              kernel               rcS.d
brltty                  kernel-img.conf      resolvconf
brltty.conf             ldap                 resolv.conf
ca-certificates         ld.so.cache          rmt
ca-certificates.conf    ld.so.conf           rpc
calendar                ld.so.conf.d         rsyslog.conf
chatscripts             legal                rsyslog.d
chromium-browser        libnl-3              samba
colord.conf             libpaper.d           sane.d
conky                   libreoffice          securetty
ConsoleKit              lightdm              security
console-setup           locale.alias         sensors3.conf
cron.d                  localtime            sensors.d
cron.daily              logcheck             services
cron.hourly             login.defs           sgml
cron.monthly            logrotate.conf       shadow
crontab                 logrotate.d          shadow-
cron.weekly             lsb-base             shells
cups                    lsb-base-logging.sh  skel
cupshelpers             lsb-release          snmp
dbus-1                  ltrace.conf          speech-dispatcher
debconf.conf            magic                ssh
debian_version          magic.mime           ssl
default                 mailcap              sudoers
defoma                  mailcap.order        sudoers.d
deluser.conf            manpath.config       sysctl.conf
depmod.d                mime.types           sysctl.d
dhcp                    mke2fs.conf          systemd
dhcp3                   modprobe.d           terminfo
dictionaries-common     modules              timezone
dkms                    motd                 tor
doc-base                mtab                 torsocks.conf
dpkg                    mtab.fuselock        ts.conf
emacs                   mtools.conf          ucf.conf
environment             mysql                udev
fonts                   nanorc               ufw
foomatic                netscsid.conf        update-manager
fstab                   network              update-motd.d
fstab.d                 NetworkManager       update-notifier
fuse.conf               networks             UPower
gai.conf                newt                 upstream-release
gconf                   nsswitch.conf        usb_modeswitch.conf
gdb                     ntp.conf             usb_modeswitch.d
ghostscript             obex-data-server     vim
ginn                    ODBCDataSources      VisualBoyAdvance.cfg
gnome                   odbc.ini             vlc
gnome-app-install       odbcinst.ini         vtrgb
gnome-settings-daemon   openal               wgetrc
groff                   OpenCL               wodim.conf
group                   opt                  wpa_supplicant
group-                  os-release           X11
grub.d                  pam.conf             xdg
gshadow                 pam.d                xml
gshadow-                papersize            zsh_command_not_found
gtk-2.0                 passwd
gtk-3.0                 passwd-

```

---

### Post by RadicaX on 2014-01-28
> **robert49 said:**
> Well lots of reports have been made. The issue is under observation. I tried gazette but it is sorta spaz out at the begining when i open it via terminal. It goes crazy and i need to click it to become clear so i just uninstalled it. I guess i have to wait for the applets to get fixed. Many people have this issue so i think they will hurry a update that will probably fix the bugs. I also tried Bucharest as the capital of my country and it still didn't work, i tried London and it was the same story. I will keep searching. I tried like 2-3 types of fixes with dconf Editor and installing new versions but after all it was the same story. I am using Weather Indicator ( not my weather indicator, this one is not even starting) and the cd command is not working :-s robert@Robert-Computer:~$ cd /etc/indicator-weatherbash: cd: /etc/indicator-weather: No such file or directory .

```
 robert@Robert-Computer:~$ cd /etc/ indicator-weatherrobert@Robert-Computer:/etc$ ls
acpi                    hdparm.conf          pcmcia
adduser.conf            host.conf            perl
adjtime                 hostname             pkcs11
alternatives            hosts                pm
anacrontab              hosts.allow          pnm2ppa.conf
apg.conf                hosts.deny           polkit-1
apm                     hp                   ppp
apparmor                icedtea-web          preload.conf
apparmor.d              ifplugd              profile
apport                  ImageMagick          profile.d
apt                     init                 protocols
at.deny                 init.d               pulse
ati                     initramfs-tools      python
at-spi2                 inputrc              python2.7
avahi                   insserv              rc0.d
bash.bashrc             insserv.conf         rc1.d
bash_completion         insserv.conf.d       rc2.d
bash_completion.d       iproute2             rc3.d
bindresvport.blacklist  issue                rc4.d
blkid.conf              issue.net            rc5.d
blkid.tab               java-6-openjdk       rc6.d
bluetooth               kbd                  rc.local
brlapi.key              kernel               rcS.d
brltty                  kernel-img.conf      resolvconf
brltty.conf             ldap                 resolv.conf
ca-certificates         ld.so.cache          rmt
ca-certificates.conf    ld.so.conf           rpc
calendar                ld.so.conf.d         rsyslog.conf
chatscripts             legal                rsyslog.d
chromium-browser        libnl-3              samba
colord.conf             libpaper.d           sane.d
conky                   libreoffice          securetty
ConsoleKit              lightdm              security
console-setup           locale.alias         sensors3.conf
cron.d                  localtime            sensors.d
cron.daily              logcheck             services
cron.hourly             login.defs           sgml
cron.monthly            logrotate.conf       shadow
crontab                 logrotate.d          shadow-
cron.weekly             lsb-base             shells
cups                    lsb-base-logging.sh  skel
cupshelpers             lsb-release          snmp
dbus-1                  ltrace.conf          speech-dispatcher
debconf.conf            magic                ssh
debian_version          magic.mime           ssl
default                 mailcap              sudoers
defoma                  mailcap.order        sudoers.d
deluser.conf            manpath.config       sysctl.conf
depmod.d                mime.types           sysctl.d
dhcp                    mke2fs.conf          systemd
dhcp3                   modprobe.d           terminfo
dictionaries-common     modules              timezone
dkms                    motd                 tor
doc-base                mtab                 torsocks.conf
dpkg                    mtab.fuselock        ts.conf
emacs                   mtools.conf          ucf.conf
environment             mysql                udev
fonts                   nanorc               ufw
foomatic                netscsid.conf        update-manager
fstab                   network              update-motd.d
fstab.d                 NetworkManager       update-notifier
fuse.conf               networks             UPower
gai.conf                newt                 upstream-release
gconf                   nsswitch.conf        usb_modeswitch.conf
gdb                     ntp.conf             usb_modeswitch.d
ghostscript             obex-data-server     vim
ginn                    ODBCDataSources      VisualBoyAdvance.cfg
gnome                   odbc.ini             vlc
gnome-app-install       odbcinst.ini         vtrgb
gnome-settings-daemon   openal               wgetrc
groff                   OpenCL               wodim.conf
group                   opt                  wpa_supplicant
group-                  os-release           X11
grub.d                  pam.conf             xdg
gshadow                 pam.d                xml
gshadow-                papersize            zsh_command_not_found
gtk-2.0                 passwd
gtk-3.0                 passwd-

```

Okay, this helps to show all the things you have on your computer at the moment. While some of it is different, we can see a lot the same too compared to our own set up. It is odd looking through it though, I do not see the files of any of the things. 

I am not seeing anything about Gazette in there, I can see stuff like for example tor, which tells us you use the TOR browser. I would also think you ran some kind of server with some of the things on there. But this might be why the programs are having some problems. It might not of installed in the right place. (Somehow my sister installed skype in the temporary internet files once, beats the heck out of me how.) 

hmm. Do you know the people that make these said programs? I will do a bit of looking around myself, because I have no clue why they should not be there. I am thinking that might be the problem.

edit: 
Did you update pywapi?

---

### Post by robert49 on 2014-01-28
I don't think i updated pywapi. The tor browser does not work either,i installed it because i am a member of a forum on the darknet but it's not working, but i am using the one from my phone. I had gazette but i uninstalled it.

---

### Post by RadicaX on 2014-01-28
Yes then, it sounds like some of the packages are just missing some of the things.

[https://launchpad.net/weather-indicator](https://launchpad.net/weather-indicator) This is to the launchpad, and they say they need pywapi. 

[https://launchpad.net/~pywapi-devel/+archive/ppa](https://launchpad.net/~pywapi-devel/+archive/ppa) to which you will have to install the ppa for too. (which you can do with an apt-get command.) or I believe by hitting the link there, pick the one that says newest. Odds are for all the apps giving you trouble, things like that have happened. Try this out and if you need some help or want commands just say, I will post them.

---

### Post by robert49 on 2014-01-28
Yea i will need help with the commands. I know some of them but if i don't get the right package name i get stuck :P

---

### Post by RadicaX on 2014-01-28
Okay, for the most part, it should let you just copy the code on the site to add the PPA... The issue here is if we can do it with Elementary... I am thinking it is based on Ubuntu 12.04? hmm, that is an issue... 

```
sudo add-apt-repository **ppa:pywapi-devel/ppa**
```
```
sudo apt-get update
```

This should give you the things updated and ready to add what you need. Now just try installing Weather-indicator again.

```
sudo apt-get install indicator-weather
```

Tell me if that works, if not we will have to try another code.

---

### Post by robert49 on 2014-01-28
no it's not working :(, it doesn't show the temperature,it's just the icon up there :(

---

### Post by RadicaX on 2014-01-28
The icon is up though?! Okay one moment... This is problematic, at least it is coming up... Let us try checking for something.

```
cd /bin/indicator-weather
```

```
ls
```

If the top one messes up.

```
cd /bin
``` 

```
ls
```

And please post input here, keep it open too, we are going to do a bit of digging to see if anything is there if it does open.

---

### Post by robert49 on 2014-01-28
```
robert@Robert-Computer:~$ cd /bin/ indicator-weatherrobert@Robert-Computer:/bin$ ls
bash                  fgrep           nc.openbsd               setfacl
bunzip2               findmnt         netcat                   setfont
busybox               fuser           netstat                  setupcon
bzcat                 fusermount      nisdomainname            sh
bzcmp                 getfacl         ntfs-3g                  sh.distrib
bzdiff                grep            ntfs-3g.probe            sleep
bzegrep               gunzip          ntfs-3g.secaudit         ss
bzexe                 gzexe           ntfs-3g.usermap          static-sh
bzfgrep               gzip            ntfscat                  stty
bzgrep                hostname        ntfsck                   su
bzip2                 init-checkconf  ntfscluster              sync
bzip2recover          initctl2dot     ntfscmp                  tailf
bzless                ip              ntfsdecrypt              tar
bzmore                kbd_mode        ntfsdump_logfile         tempfile
cat                   kill            ntfsfix                  touch
chacl                 less            ntfsinfo                 true
chgrp                 lessecho        ntfsls                   ulockmgr_server
chmod                 lessfile        ntfsmftalloc             umount
chown                 lesskey         ntfsmove                 uname
chvt                  lesspipe        ntfstruncate             uncompress
cp                    ln              ntfswipe                 unicode_start
cpio                  loadkeys        open                     vdir
dash                  login           openvt                   vmmouse_detect
date                  lowntfs-3g      pidof                    which
dbus-cleanup-sockets  ls              ping                     whiptail
dbus-daemon           lsblk           ping6                    ypdomainname
dbus-uuidgen          lsmod           plymouth                 zcat
dd                    mkdir           plymouth-upstart-bridge  zcmp
df                    mknod           ps                       zdiff
dir                   mktemp          pwd                      zegrep
dmesg                 more            rbash                    zfgrep
dnsdomainname         mount           readlink                 zforce
domainname            mountpoint      rm                       zgrep
dumpkeys              mt              rmdir                    zless
echo                  mt-gnu          rnano                    zmore
egrep                 mv              running-in-container     znew
false                 nano            run-parts
fgconsole             nc              sed
robert@Robert-Computer:/bin$ 

```

---

### Post by RadicaX on 2014-01-28
It is not in there at all.

That is not good.  did some searching around on another forums though. (the elementary forums.) And found something of interest, a guy who was using the My-weather-indicator had it working, but someone else could not get it to work, turns out the kernal was not working right with it, and by reverting to an older kernal, it all of a sudden worked.

I wonder if that would work for this too?

[http://elementaryforum.org/forum/support-assistance/3rd-party-application/4578-my-weather-indicator](http://elementaryforum.org/forum/support-assistance/3rd-party-application/4578-my-weather-indicator)

Hmm... besides not finding the packages, which is beyond me why I am not seeing any of them on there at all regardless where we look, you could try this and see if it works. I do not know how you would try an older kernal though. you might need to make a post about that asking for help. (I would explain this problem too.) and see what they have to say. I am very sorry I am not of more help, I will keep looking into it to see if I can figure it out too though.

---

### Post by robert49 on 2014-01-28
Ok then, thank you for your effort! If it is from the kernel i do believe the elementary OS team is looking into this problem. After all this is an WIP project and I should expect improvements. The rest of the applets work, applets like system monitor, rss feed. I will look into reverting to a older version of the kernel. I will keep you posted :P

---

### Post by RadicaX on 2014-01-28
Okay, please do, if you find a fix before I or anyone else, this would benefit anyone else looking for the fix and that come along this post.

P.S. You are welcome by the way, sorry I was not of more help. I will keep you informed on anything I find out.

---

