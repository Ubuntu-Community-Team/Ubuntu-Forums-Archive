---
title: "What VERR_SYMBOL_NOT_FOUND means?"
date: 2016-02-23
forum: Virtualisation
---

### Post by artss2 on 2016-02-23
I use xubuntu 12.04 image from here [http://virtualboxes.org/images/ubuntu/](http://virtualboxes.org/images/ubuntu/). But when launching it in Vbox 4.2.36 version i got *symbol not found* error. Is it due to obsloete vboxversion? How to check the version of vdi image?
I know I could do it by VboxManage in command prompt of Windows XP. But my Vbox folder is not on C disk but on D, so
I do not now how to laucnh it from D in CMD prompt.
Despite - what are the options for SYMBOL_NOT_FOUND error (ERROR [COM]: aRC=E_FAIL (0x80004005))? 
I use WinXP with 512 mb that is apt for ubuntu 12.04 but of cause not whole memory could be allocated for VM Ubuntu - So yesterday my vM was not able to lauch of xubuntu 12.04 install due lack of memory -- so I used already created image but with error pf SYMBOL_NOT_FOUND. I unchecked pae option that is not supported by my PC, and USB support with pointing device (as no additions on is installed) - but error got?

---

### Post by MAFoElffen on 2016-02-24
Usually in the first line that it says 
```

rc=VERR_SYBOL_NOT_FOUND"

```
Then in that same line, after that text, there should be a  
```

szErr="<moduleName> returned VERR_SYMBOL_NOT_FOUND"

```
Then 2 lines after that should be a more specific module name...

This is a VirtualBox Error stating that there is a mismake in the modules of VirtuaoBox itself. This error usually happens just after an upgrade, when the modules are updated, but the old modules are still loaded in memory. (but those are no longer located on disk.)

Have you rebooted your host since then and retried? (that usually fixes the above error on an update...)

---

### Post by artss2 on 2016-02-24
So can I upload this [http://downloads.sourceforge.net/virtualboximage/xubuntu_1204.7z](http://downloads.sourceforge.net/virtualboximage/xubuntu_1204.7z) xubuntu VB image ([http://virtualboxes.org/images/xubuntu/](http://virtualboxes.org/images/xubuntu/)) to Vbox [COLOR=#000000]4.2.36  -- what version is it, you can probably check it easier?
Can the error be in absence of additions on? //I did not restarted PC despite I did not created Vbox there at first?
So is it possible to install xubuntu or lubuntu (non-pae) at PC with just 360-380 real mb memory (formal 512 mb), and use it for c/c++ development, in Codeblocks for example?[/COLOR]

---

### Post by MAFoElffen on 2016-02-24
You should not allocate more that 1/2 of your hosts memory to a VM. Fact is most hypervisors will throw as error if that is done.

Having said that- Lubuntu will run in 256MB. Running Xubuntu... it would run in what you said, but runs better in 512 MB and above.

---

### Post by artss2 on 2016-02-27
Ready Xubuntu image from the site works, and about 250 mb is enough for memory consuption. But I need every time, to restart PC to absolve the VERR_SYMBOL_NOT_FOUND -- E_FAIL (0x80004005). What is the reason?
Except it -- I can list my ZTE MF 100 modem in LSUSB, despite not installing no driver on ubuntu directly. But when got connection -- no google search even happened -- when checked by <ifconfig ppp0> I got just PX 62 bts, and  TX 101 bts, that is just technical not reals bytes transfer??
I did not installed usb-modeswithch as zte is appeared and allow network connection -- should the reason to be in it? As I later installed through the dpkg and all another depended packages -- minicom, but nothing changed?

---

### Post by MAFoElffen on 2016-02-28
Try this from a terminal in your Ubuntu guest (add the user to the vbox user group:
```

sudo usermod -a -G vboxusers userName

```

---

