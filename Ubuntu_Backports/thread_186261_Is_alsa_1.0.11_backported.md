---
title: "Is alsa 1.0.11 backported"
date: 2006-06-01
forum: Ubuntu Backports
---

### Post by didobuntu on 2006-06-01
Hi all,
I just need an info. Is the alsa-1.0.11 backported to drapper ?
I have an intel chipset with realtek ALC880 which, following alsa project, is supported by the last release of alsa.
I tried to compile the alsa-driver but no success ... I downloaded the adequate linux-headers, the gcc version is 4.0, but render a lot of errors ... ](*,) 

Do I have to compile it with gcc-3.4 or others ?

Thanks for your help

---

### Post by didobuntu on 2006-06-01
Another question I forgotten,
How to enable the backport repos if alsa-1.0.11 is there ? In synaptic too ?

---

### Post by strikeforce on 2006-06-02
I don't believe alsa will be backported due to libraries included and linked to other programs.

This is generally the reason why things aren't backported.

Backports for dapper have not opened yet they will open when etch is starting to get ported across.

---

### Post by e_liming on 2006-06-02
[QUOTE=strikeforce]I don't believe alsa will be backported due to libraries included and linked to other programs.

This is generally the reason why things aren't backported.

Backports for dapper have not opened yet they will open when etch is starting to get ported across.[/QUOTE]

So I guess I will get the same reply if I open a request for X.org 7.1? I know the ABI is changed but I really want to try the latest driver for my Savage chip.

---

### Post by geearf on 2006-06-04
I don't think Xorg will be backported either, just wait for edgy.

---

### Post by ajack on 2006-06-05
[QUOTE=didobuntu]Another question I forgotten,
How to enable the backport repos if alsa-1.0.11 is there ? In synaptic too ?[/QUOTE]

I did a request for alsa-1.0.11 for dapper at URL:

[https://launchpad.net/distros/ubuntu/+ticket/1000](https://launchpad.net/distros/ubuntu/+ticket/1000)

Hope this helps... now waiting... :-\"

---

### Post by jbinto on 2006-06-21
Without alsa 1.0.11, I cannot capture audio with emu10k1. I only get left channel audio.

In gentoo, a **year** ago, I solved this problem easily by emerge'ing unstable ~x86 alsa-libs. Dapper does not offer alsa 1.0.11 in any way shape or form and if I wanted to go around messing my libraries up manually, I'd be using LFS or something.

Does anyone have an idiot proof way of getting alsa 1.0.11 working in dapper? I'm not confident enough with ubuntu's structure and the whole dpkg thing to continue.

---

### Post by nicweb on 2006-06-22
I really need alsa 1.0.11 too ... the current version is not working with my Samsung X60 onboard soundcard and I think several other people have similar issues.

Is there any way to get alsa 1.0.11 to the update repos?

---

### Post by didobuntu on 2006-06-24
I followed the instruction to compile the alsa driver version 1.0.11 from the alsa projet web site and alson following this [howto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") ... but nothing ... I get the following compilation error ..

In file included from /home/nedjar/Tempo/alsa-driver-1.0.11/include/sound/driver.h:47,
                 from /home/nedjar/Tempo/alsa-driver-1.0.11/acore/hwdep.c:22:
/home/nedjar/Tempo/alsa-driver-1.0.11/include/adriver.h:697: erreur: redefinition of «jiffies_to_msecs»
include/linux/jiffies.h:256: erreur: previous definition of «jiffies_to_msecs» was here
/home/nedjar/Tempo/alsa-driver-1.0.11/include/adriver.h:716: erreur: redefinition of «msecs_to_jiffies»
include/linux/jiffies.h:278: erreur: previous definition of «msecs_to_jiffies» was here
In file included from /home/nedjar/Tempo/alsa-driver-1.0.11/include/adriver.h:807,
                 from /home/nedjar/Tempo/alsa-driver-1.0.11/include/sound/driver.h:47,
                 from /home/nedjar/Tempo/alsa-driver-1.0.11/acore/hwdep.c:22:
include/linux/pci.h:424: erreur: syntax error before numeric constant
In file included from /home/nedjar/Tempo/alsa-driver-1.0.11/include/sound/driver.h:47,
                 from /home/nedjar/Tempo/alsa-driver-1.0.11/acore/hwdep.c:22:
/home/nedjar/Tempo/alsa-driver-1.0.11/include/adriver.h: Dans la fonction «snd_pci_orig_save_state» :
/home/nedjar/Tempo/alsa-driver-1.0.11/include/adriver.h:1048: erreur: too many arguments to function «pci_save_state»
/home/nedjar/Tempo/alsa-driver-1.0.11/include/adriver.h: Dans la fonction «snd_pci_orig_restore_state» :
/home/nedjar/Tempo/alsa-driver-1.0.11/include/adriver.h:1052: erreur: too many arguments to function «pci_restore_state»
make[3]: *** [/home/nedjar/Tempo/alsa-driver-1.0.11/acore/hwdep.o] Erreur 1
make[2]: *** [/home/nedjar/Tempo/alsa-driver-1.0.11/acore] Erreur 2
make[1]: *** [_module_/home/nedjar/Tempo/alsa-driver-1.0.11] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.15-25-686 »
make: *** [compile] Erreur 2

... After two fresh installs of Drappper .. nothing ... my Asus W2Jc is driving me crazy ](*,)

---

### Post by Curious_Squid on 2006-07-10
I'll jump on the this bandwagon! I need 1.0.11 to stop my laptop screeching at me when I try and play sound!

---

### Post by Burkey on 2006-07-10
Me too, LG P1 Express Dual with ALC880

---

### Post by yopnono on 2006-07-11
Have any one tried the also from edgy?

[http://packages.ubuntu.com/edgy/sound/alsa-base](http://packages.ubuntu.com/edgy/sound/alsa-base)

Package: alsa-base (1.0.11-3ubuntu1)

---

### Post by shm on 2006-07-17
Hi to all
you can install alsa 1.0.11 from sources using apt

follow this topic [http://forum.ubuntu.ru/index.php?topic=3280.from1152879489](http://forum.ubuntu.ru/index.php?topic=3280.from1152879489)

sorry for my english.

---

