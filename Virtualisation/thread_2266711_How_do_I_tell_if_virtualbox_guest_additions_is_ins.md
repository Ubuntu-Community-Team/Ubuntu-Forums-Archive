---
title: "How do I tell if virtualbox guest additions is installed and working correctly?"
date: 2015-02-24
forum: Virtualisation
---

### Post by PopsTheSailor on 2015-02-24
I'm running Ubuntu 14.04 as my host and have Virtualbox version 4.3.10_ubuntu r93012 running with Win 7. How do I tell if Guest Additions in installed. When I try to load it (Devices/Insert Guest Additions CD Image) the menu just goes away and nothing happens.

---

### Post by coldraven on 2015-02-25
From here:
[https://www.virtualbox.org/manual/ch04.html#additions-windows](https://www.virtualbox.org/manual/ch04.html#additions-windows)
> In the "Devices" menu in the virtual machine's menu bar,         VirtualBox has a handy menu item named "Insert Guest Additions CD image",         which mounts the Guest Additions ISO file inside your virtual machine.         A Windows guest should then automatically start the Guest Additions         installer, which installs the Guest Additions into your Windows         guest. Other guest operating systems (or if automatic start of         software on CD is disabled) need manual start of the installer.

AFAIR when you run your Windows guest you should see the iso as a little CD icon. Try double clicking it.

---

### Post by PopsTheSailor on 2015-02-25
Yes, I understand all of that. What I'm saying is that when I click on Insert Guest Additions CD image nothing happens. If I look in both Synaptic and Ubuntu Software Center both show Guest Additions as installed. I'd like to understand how I verify that "Guest Additions" is indeed actually installed.

---

### Post by slickymaster on 2015-02-25
Run the following command in terminal:```
lsmod | grep -io vboxguest | xargs modinfo | grep -iw version
```

---

### Post by QIII on 2015-02-25
Hello!

It is normal for the menu to disappear with no apparent effect.  But that doesn't mean the additions are installed.

You should either see a disk icon on the launch panel or find a mounted "CD" in your file manager.  To actually install the additions, you have to run the VBoxGuestAdditiins script from there.

---

### Post by PopsTheSailor on 2015-02-25
When I ran 
lsmod | grep -io vboxguest | xargs modinfo | grep -iw version 

I got a "ERROR: missing module or filename" message. If I look under my CD devices it shows the Guest Additions ISO file. 
Does that mean it's installed or only available to install? Do I try and run the ISO file or is it enough that it shows up?

---

### Post by QIII on 2015-02-25
The script for Windows has to be run.

---

### Post by slickymaster on 2015-02-25
> **QIII said:**
> Hello!

It is normal for the menu to disappear with no apparent effect. But that doesn't mean the additions are installed.

You should either see a disk icon on the launch panel or find a mounted "CD" in your file manager. To actually install the additions, you have to run the VBoxGuestAdditiins script from there.

Do this ^^^

---

### Post by PopsTheSailor on 2015-02-25
Sorry, I guess I'm being a bit dense here. When you say run the script for windows are you talking about this:

lsmod | grep -io vboxguest | xargs modinfo | grep -iw version

So I click on Start then CMD to get to a dos prompt and then run above or is there a different script.

---

### Post by slickymaster on 2015-02-25
> **PopsTheSailor said:**
> Sorry, I guess I'm being a bit dense here. When you say run the script for windows are you talking about this:

lsmod | grep -io vboxguest | xargs modinfo | grep -iw version

So I click on Start then CMD to get to a dos prompt and then run above or is there a different script.

I'm sorry because it seems that I confused you. That's a command line to use at a terminal window in your Ubuntu system to check if you have the Guest Additions installed on it.

What you have to do is what QIII said in [his post]("http://ubuntuforums.org/showthread.php?t=2266711&p=13234717&viewfull=1#post13234717")

---

### Post by PopsTheSailor on 2015-02-25
OK, got it. And no, it isn't you. I'm just being a dunce today. One last question. Should I install the Direct 3D Support that says it is experimental? I ask because the main reason I'm trying to get GA installed is because I have a flight simulator package that uses heavy graphics but I don't know if I should opt for the Direct 3D.

Thank you for the help!

---

### Post by slickymaster on 2015-02-25
Well that's totally up to you. Can't advise you there since I've never used any software that would need Direct 3D.

There's nothing like experimenting both options though, and see if there's a real gain in using it

---

