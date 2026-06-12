---
title: "What is the easiest method of virtualisation in Hardy?"
date: 2008-05-09
forum: Virtualisation
---

### Post by Game_boy on 2008-05-09
I am completely confused by the links/tutorials/etc. I have found on this forum and elsewhere - there are seemingly hundreds of methods and nowhere explains the advantages/disadvantages. In addition, not a single one specifies Ubuntu 8.04 (even the Ubuntu Wiki) despite the major changes to virtualisation in 8.04.

So, what is the easiest Hardy-"supported" (i.e. intended by developers) method of virtualising for example Fedora or Opensuse? I just want to try other distributions and I don't need 3D or seamless integration or anything - I just want it to be usable enough to get an impression of them.

Feel free to point me at the most appropriate tutorial/post if necessary.

---

### Post by hdotcom on 2008-05-10
Hi there,

You might want to try VirtualBox 1.6. I am not quite sure if its on Ubuntu's repository yet but am sure there is a deb file that you can download from their website. The new version (1.6) supports Hardy and the installation does not require any hacks.

I've tried both versions of VB (Windows and Ubuntu) and it works extremely well.

Rgds,

H.

---

### Post by theZoid on 2008-05-14
> **hdotcom said:**
> Hi there,

You might want to try VirtualBox 1.6. I am not quite sure if its on Ubuntu's repository yet but am sure there is a deb file that you can download from their website. The new version (1.6) supports Hardy and the installation does not require any hacks.

I've tried both versions of VB (Windows and Ubuntu) and it works extremely well.

Rgds,

H.

No hacks required to get USB working?  thanks!

---

### Post by Nampla on 2008-05-14
I personally run vmware server on probably 7 ubuntu machines.  I love vmware server.  But it depends on what your doing.  I have a special POS system that requires win 2000, and also Quckbooks on 3 win xp vm.  I have no real usb devices to use (like ipods, cameras, etc..) Print and file sharing thru Samba once configured is great. VMware works flawlessly and help is abundant!!!.  I have experimented with virtualbox but found the usb and networking a little to convoluted for me.  

Good luck

---

### Post by lex1 on 2008-05-14
theres a howto at howtoforge.com with xen and hardy take a look


lex1

---

### Post by jen1963 on 2008-05-14
I have an XP Pro VM purring in VirtualBox under Hardy. I blogged about it here:

[http://tuxwerx.com/Blogs/?p=21]("http://tuxwerx.com/Blogs/?p=21")

Hope it helps...

---

### Post by theZoid on 2008-05-14
> **jen1963 said:**
> I have an XP Pro VM purring in VirtualBox under Hardy. I blogged about it here:

[http://tuxwerx.com/Blogs/?p=21]("http://tuxwerx.com/Blogs/?p=21")

Hope it helps...

Hi Jen....I also have a post pertaining to getting usb working (link in my sig), but what I am wondering is if all the hacks still need to be done in VB non free 1.6.0.  I have that version installed after uninstalling 1.5.6, and usb works great.  But I don't know if all or some of the hacks are required for usb to work in the new version.

ps....good to see you have the correct pol. affiliation :D

---

### Post by jen1963 on 2008-05-14
There seem to be a bunch of USB hacks for VB on different forums. Some work on some machines and others work on different machines.
The only thing I can suggest is to try the different hacks to see which one works on your puter.
USB support & VM backup\Restore are the only 2 really weak areas in VB it seems.
I hope within the next release or 2 Sun gets the last few bugs out.

---

### Post by lilloki2000 on 2008-06-05
I am a total noob with Linux but with a little poking and looking arround I got win xp virtualized on Hardy using qemu.

1. Head to Applications and go to Add Remove
2. Search Qemu and you should come up with three options, Qemu, an auxillrary program to speed it up and a GUI for qemu.
3. Mark all three and install them
4. Load up the Qemu gui front end and poof easy to use Virtualization software.
5. In the upper left corner of the front end under file there will be a button that says make new machine. Click it and Qemu will make a disk image for installing the OS, Make sure you give yourself enough room for the OS your installing.
6.Find the Hard drive button on the front end and Have it directed at the image file you just made.
7. Right below that there is a cdrom section in the little box for that one have it using the iso of your os and check the boot from cdrom box.
8. Hit start on the Front end and it should load up and start installing the OS on the Image.

There now you have a virtualized OS Congrats

note:It only seems capable of only using 1gb of ram, Also i could not get it to recognise my DVDROM probably due to my lack of experience but just make an iso of what OS your trying to install and it should work. Another problem i have had is it will not Recognise my graphics card on my Virtual OS still working on that. 

Hope this helps ^.^:guitar:

*edit* the Front end is QTemu, Also While Qemu is probably easier to set up than Virtualbox Virtual box has beeter performance and more options

---

