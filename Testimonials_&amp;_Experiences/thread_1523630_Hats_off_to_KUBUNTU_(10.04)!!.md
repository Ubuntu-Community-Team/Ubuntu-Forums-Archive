---
title: "Hats off to KUBUNTU (10.04)!!"
date: 2010-07-03
forum: Testimonials &amp; Experiences
---

### Post by pushkarajthorat on 2010-07-03
This Kubuntu version is mindblowing, wonderful integration of Ubuntu with KDE 4 i should say this is perfect piece usability(M$ Win is left in desktop long back :)), 
kde-desktop, dolphin, and other KDE applications just rocks.
The Ubuntu guys has made great efforts to integrate the KDE apps, I should say it is done their job perfectly, all the KDE piece are of execellent quality.
I am working with this for now couple of weeks and I have no complaints till now.

Thanks for sharing such a great thing with us! Long live open source!
I am proud of you guys.

-Pushkaraj

---

### Post by VeeDubb on 2010-07-03
How do you feel about redundancy between distro-specific system configuration tools and KDE system tools?

It's been a long time since I ran a KDE system, but that was one of three major concerns that made me switch to gnome a number of years ago.

In fact, let me recount my concerns, and you tell me if you think they're still valid today.  If they're not, I may switch to Kubuntu because I'm not happy with the development progress of gnome, and I fear that gnome-shell may be not only a long way from public release, but a very long time from being stable.  (shades of the first release of KDE4)

1. Last time I tried, there was a HUGE ammount of redundancy between the various KDE tools for system configuration, and the distro specific tools for doing a lot of the same stuff.  It meant that sometimes, something as simple as opening up the KDE Control Center and closing it could change settings made elsewhere in the system.

2. The KDE sound system took over total control of all system sound, and I found that many applications, especially games played through wine, would have no sound unless I completely disabled the KDE sound system.

3. The naming really bugged me.  Up to a point, you can get away with trading 'c' for 'k' but they just took it too far.  I'm sure this is still an issue, but if it's the only one, I could live with it.

---

### Post by pushkarajthorat on 2010-07-04
> **VeeDubb said:**
> How do you feel about redundancy between distro-specific system configuration tools and KDE system tools?

I have not discovered this release till extent, if you want me to check and verify something you wanted to do with KDE please tell.

> **VeeDubb said:**
> I'm not happy with the development progress of gnome
Yes, this is a main reason why I tried KDE, I could not even open "My Computer" from desktop. This was causing nautulis to crash and I didnot found working solution.

> **VeeDubb said:**
> 
1. Last time I tried, there was a HUGE ammount of redundancy between the various KDE tools for system configuration, and the distro specific tools for doing a lot of the same stuff.  It meant that sometimes, something as simple as opening up the KDE Control Center and closing it could change settings made elsewhere in the system.

I did checked for KDE Control Center, but I could found single utility to change the setting - /usr/bin/systemsettings which can be invoked thru start menu. I could not found something kcon* in the program list when I pressed two tabs after kcon.

> **VeeDubb said:**
> 
2. The KDE sound system took over total control of all system sound, and I found that many applications, especially games played through wine, would have no sound unless I completely disabled the KDE sound system.
I dont have wine installed.

> **VeeDubb said:**
> 
3. The naming really bugged me.  Up to a point, you can get away with trading 'c' for 'k' but they just took it too far.  I'm sure this is still an issue, but if it's the only one, I could live with it.
This still exist. console -is- still konsole. This is the list of all k* utilities:

k3b kcalc kdm killall5 knotes kreadconfig ktorrent  k3bsetup kcheckrunning kdmctl kimpanel knotify4 kres-migrator ktraderclient  kabc2mutt kcminit kdostartupconfig4 kioclient koi8rxterm krfb ktrash  kabcclient kcminit_startup keditbookmarks kjs kolabwizard kross ktupnptest  kaccess kcmshell4 keditfiletype kjscmd konqueror krunner kubuntu-debug-installer  kaddressbook kcookiejar4 kerneloops klipper konsole ksendemail kubuntu-firefox-installer  kaddressbookmigrator kde4 kerneloops-submit kmag konsoleprofile kshell4 kuiserver  kapplymousetheme kde4-config keytool kmail kontact ksmserver kvkbd  karm kde4-menu kfile4 kmail_antivir.sh kopete ksnapshot kvm-ok  kate kdebugdialog kfind kmail_clamav.sh kopete_latexconvert.sh ksplashsimple kwalletd  katesnippetstng_editor kde-cp kfmclient kmailcvt korgac ksplashx kwalletmanager  kbackgroundsnapshot kded4 kfontinst kmail_fprot.sh korganizer ksplashx_scale kwin  kbd_mode kdeinit4 kfontview kmail-migrator kpackagekit kstart kwin_killer_helper  kbdrate kdeinit4_shutdown kglobalaccel kmail_sav.sh kppp kstartupconfig4 kwin_rules_dialog  kblankscrn.kss kdeinit4_wrapper khelpcenter kmenuedit kppplogview ksvgtopng kwrapper4  kbluetooth kde-mv khotnewstuff4 kmimetypefinder kquitapp ksysguard kwriteconfig kbluetooth-devicemanager kde-open khotnewstuff-upload kmix krandom.kss ksysguardd kwrited kbluetooth-inputwizard kdepasswd kiconfinder kmixctrl krandrtray ksystemlog kxkb kbookmarkmerger kdesudo kill kmousetool krdb ksystraycmd  kbuildsycoca4 kdialog killall knetworkmanager krdc ktimetracker

---

### Post by NightwishFan on 2010-07-04
I believe the KDE sound system (currently phonon) only controls KDE applications. The culprit would be something to do with pulseaudio. I suggest setting the hardware access to be direct (for wine):

Press alt+f2 and type: regedit

Navigate to here and set the registry keys as stated, create them if necessary.

```
|
+-Software
   |
   +-Wine
      |
      +-Alsa Driver
      |  |
|  +->UseDirectHW
      |      [When set to y, direct hardware access is used
      |       (can prevent buffer underruns in some cases)]


```

---

### Post by Half-Left on 2010-07-04
KDE4 doesn't manage sound. It's all done through Phonon which just uses backends like Xine or Gstreamer or Pulseaudio.

I don't see what 10.4 has done, since it's almost the same as upstream KDE4.

---

