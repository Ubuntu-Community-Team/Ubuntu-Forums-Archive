---
title: "Virtualbox 3.0.0 is out...anyone tried it yet?"
date: 2009-07-01
forum: Virtualisation
---

### Post by Mattaus on 2009-07-01
Title says it all really. Has anyone had a chance to give it a try? Unfortunately the only Virtualbox I'm using is on XP (Linux Guest) and I'm not sure I can even upgrade without losing my machine (Obviously not a question I can ask here as its windows related)

More importantly has anyone tried the 3D acceleration aspects of it? I know people were having problems doing so with the beta but maybe things have changed with the final release?

I for one hope this works or helps get some serious work underway. If I can get some gaming going in a Virtual machine I can finally give Windows the kiss of death!

---

### Post by HotShotDJ on 2009-07-01
> **Mattaus said:**
> Title says it all really. Has anyone had a chance to give it a try? Unfortunately the only Virtualbox I'm using is on XP (Linux Guest) and I'm not sure I can even upgrade without losing my machine (Obviously not a question I can ask here as its windows related)You won't loose your virtual machines if you upgrade.  This is true no matter what your host operating system is.

---

### Post by ubersolid on 2009-07-01
I've tried it. Can tell you that these games works on it, haven't tested more.
10800 Zombies, works, is a bit slow.
Resident Evil 2, works.
Fallout Tactics, works, hangs for a few seconds now and again.
Civilization 4, doesn't work.

This on a fedora 11 host, with Windows XP Pro with SP3 as guest.

---

### Post by zoomy942 on 2009-07-01
any try guild wars?  Also, with my hardware and my stupid intel graphics, would this even be worth trying?

---

### Post by doorknob60 on 2009-07-01
SimCity 4 works, but it has a sofwtware rendering engine so I don't think it's using 3D accelleration. It still works though :) (stopped working in Wine with latest version...meh)

---

### Post by bodhi.zazen on 2009-07-01
Upgrade went fine, have not gotten to testing video yet.

---

### Post by Mattaus on 2009-07-01
I might give it a go tonight and see how my mileage goes. At least this appears to be a step in the right direction!

---

### Post by Joeb454 on 2009-07-01
Works fine for me, though I'm not a heavy VM user, so I can't really say much more than that :)

---

### Post by zoomy942 on 2009-07-01
i have found that on my single CPU but dual core PC's, using the SMP slows it down a great deal. Also, so far, 3d hasnt been great, but i need to test it more.

---

### Post by nemodot on 2009-07-01
I'm now playing AOE II on it, looks good.

---

### Post by juancarlospaco on 2009-07-01
The best for desktop, suck at Servers, dont have centralized managment console, but the best on desktop.
:)

---

### Post by Mattaus on 2009-07-01
Argh I'm such a nub! I only just remembered that I currently have no Linux host machine and all my Ubuntu installs are virtual - except for my HTPC but that's working well so I'm not going to mess with it. So I can't test the gaming on an XP virtual machine under a Linux host because I simply don't have one! Would testing on an XP guest under a Vista host be even remotely useful? (albeit pretty stupid in the first place lol)

Also, from the known issues section of the Virtualbox user manual:

> Direct 3D support in Windows guests: For this to work, the Guest Additions must be installed in Windows "safe mode". Press F8 when the Windows guest is booting and select "Safe mode", then install the Guest Additions. Otherwise Windows' file protection mechanism will interfere with the replacement DLLs installed by VirtualBox and keep restoring the original Windows system DLLs.

---

### Post by crazyfrog1234 on 2009-07-02
Hi, I have installed vbox 2.2.4 but I can't uninstall it to upgrade to 3.0.0. Can anybody help me ?

---

### Post by cybergalvez on 2009-07-02
Using it now, the upgrade went without a hitch, haven't tried the new 3D yet, but will soon

---

### Post by Jose Catre-Vandis on 2009-07-02
> **crazyfrog1234 said:**
> Hi, I have installed vbox 2.2.4 but I can't uninstall it to upgrade to 3.0.0. Can anybody help me ?

I'm with you crazyfrog1234.

This is what I did, open a terminal:

Check version:
```
VBoxManage -v
```

mine was "2.2.4r49487". You need the first two digits, in my case 2.2

then uninstall:
```
sudo dpkg -r virtualbox-2.2
```

then install new version:
```
sudo dpkg -i virtualbox-3.0_3.0.0-49315_Ubuntu_jaunty_i386.deb
```

you might get a complaint about broken dependencies so:
```
sudo apt-get install -f
```

and the installation should complete :)

---

