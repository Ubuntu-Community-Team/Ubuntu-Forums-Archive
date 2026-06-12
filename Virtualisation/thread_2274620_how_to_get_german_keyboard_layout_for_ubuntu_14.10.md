---
title: "how to get german keyboard layout for ubuntu 14.10 running in oracle virtual box?"
date: 2015-04-21
forum: Virtualisation
---

### Post by dirk-lehmann on 2015-04-21
Dear Sir or Madame,

I was wondering if anyone can let me know how to get the german keyboard layout in my virtual maschine running ubuntu 14.10.

I tried allready:

*sudo dpkg-reconfigure keyboard-configuration*
[I]sudo dpkg-reconfigure console-setup
sudo apt-get install language-pack-de language-pack-de-base
sudo apt-get update
sudo apt-get install console-data[/I]

Everything points on german keyboard layout with qwertz-keyboard and UFT-8 coding and *Kombiniert - Latein, slawisches Kyrillisch, Griechisch* charset.

But nothing works. I allways have a american (us) keyboard layout in my terminal.

How to change my terminal to a german keyboard layout ?!?

Best regards,

Dirk Lehmann, Bad Kissingen

---

### Post by TheFu on 2015-04-21
Seems you've done everything I would try already.
Perhaps it is the terminal program? Which other terminals have you tried? rxvt?

---

### Post by dirk-lehmann on 2015-04-23
I use the ubuntu 14.10 shell (terminal) and no GUI.
The OS is running in a Oracle virtual maschine (latest version).

---

### Post by TheFu on 2015-04-23
Is utf8 the default character set?  I'm still reaching - don't have clue. Here resetting the console-setup has worked, but I have US keyboards and need to access other languages.

Sorry.

---

