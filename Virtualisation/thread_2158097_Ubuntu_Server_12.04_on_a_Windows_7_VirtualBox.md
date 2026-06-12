---
title: "Ubuntu Server 12.04 on a Windows 7 VirtualBox?"
date: 2013-06-27
forum: Virtualisation
---

### Post by php111 on 2013-06-27
Hey everyone,

I have a Windows 7 desktop PC 32-bit. I am looking for a tutorial that will get Unbuntu Server 12.04 running on a Windows 7 VirtualBox. Could I also run the recommended 64-bit Unbuntu Server in a VirtualBox even though I have a Windows 7 32-bit? Could someone please link me to where I could find these tutorials?

Thank you,

---

### Post by Toz on 2013-06-27
Moving to the ***Virtualisation*** subform.

Regarding a 64-bit vm guest on a 32-bit host, see: [http://askubuntu.com/questions/180761/can-i-use-virtualbox-with-a-64-bit-image-in-a-32-bit-host]("http://askubuntu.com/questions/180761/can-i-use-virtualbox-with-a-64-bit-image-in-a-32-bit-host").

Regarding a tutorial for installing Ubuntu Server 12.04 in a vm on a Windows host, see: [http://cybrwrld.blogspot.ca/2012/10/feel-ubuntu-ubuntu-on-virtual-box.html]("http://cybrwrld.blogspot.ca/2012/10/feel-ubuntu-ubuntu-on-virtual-box.html").

---

### Post by php111 on 2013-06-27
Thank you so much! I'll check those out.

EDIT: fix typo.

---

### Post by php111 on 2013-06-27
I'm sorry but I looked at the 64-bit host link and I read it but I'm confused. I don't know how or what hardware or software to look for to see if it supports it.

Could you or someone please help me?

---

### Post by php111 on 2013-06-28
I could see no one is trying to help me?

I'm not understanding the VirtualBox thing. I get too many errors such as audio and messages about HOST Keys and Auto Capture Keyboard and Mouse and when I press capture my mouse disappears and I can't make it pass the language screen and my mouse won't work. I don't understand about those errors either.

---

### Post by steeldriver on 2013-06-28
> **php111 said:**
> I could see no one is trying to help me?

Please be patient - this is a volunteer forum, members are in different timezones and we are not always awake right when you post your request

> **php111 said:**
> I'm not understanding the VirtualBox thing. I get too many errors such  as audio and messages about HOST Keys and Auto Capture Keyboard and  Mouse and when I press capture my mouse disappears and I can't make it  pass the language screen and my mouse won't work. I don't understand  about those errors either.

It's hard to give you specific advice here - it sounds like you have successfully installed some kind of guest OS but beyond that what exactly do you need help with? If you're just "not understanding the VirtualBox thing" then there's not much I can suggest except reading the Oracle documentation and experimenting - I'm pretty sure I created and then tossed at least a couple of VMs when I first started, before I got things set up 'right'. 

Regarding the 64 versus 32 bits I believe the situation is that you will be able to run a 64 guest (Ubuntu) on a 32 bit Windows host OS provided that the CPU itself is 64 bit and supports hardware virtualization (effectively bypassing the 32-bit restriction of the host OS). The latter is something you may need to enable in BIOS.  If you are running an instance of Windows XP Mode (even a long ago hibernated one, or a legacy app that runs in XP Mode) you may need to resurrect and kill that first since it may have 'claimed' the hardware.

---

### Post by php111 on 2013-06-28
I'm very really sorry for not being patient.

[http://filesharingtalk.com/threads/281331-NaQ-s-Complete-Setup-Guide-for-Linux-Seedboxes-%28Fedora-Core-CentOS-Debian-Ubuntu%29](http://filesharingtalk.com/threads/281331-NaQ-s-Complete-Setup-Guide-for-Linux-Seedboxes-%28Fedora-Core-CentOS-Debian-Ubuntu%29)

By looking at that particular guide/tutorial: May yourself or someone tell me if they are using the GUI or the Server without the GUI and what version?

---

### Post by CharlesA on 2013-06-29
They are using a GUI (or adding a GUI after install). I'm not quite sure I'd recommend it though, as they have disabled quite a few security features of Fedora and haven't really mentioned much for Debian.

They also are installing Firestarter which conflicts with UFW and is no longer maintained on Ubuntu.

---

### Post by coldraven on 2013-06-29
You can get a ready made Ubuntu 12.04 VirtualBox  image here:
[http://virtualboxes.org/images/](http://virtualboxes.org/images/)

---

### Post by php111 on 2013-06-29
Thank you so very much to everyone,

With the image, all I need to do is create the hard drive using VHD settings and mount the image from that link and use it like the ones from Ubuntu.com, except its already an image for me, right?

If I'm incorrect, then could someone please correct with the proper steps?

---

### Post by CharlesA on 2013-06-29
Sound about right.
[http://virtualboxes.org/doc/register-and-load-a-downloaded-image/](http://virtualboxes.org/doc/register-and-load-a-downloaded-image/)

---

### Post by php111 on 2013-06-29
> **CharlesA said:**
> Sound about right.
[http://virtualboxes.org/doc/register-and-load-a-downloaded-image/](http://virtualboxes.org/doc/register-and-load-a-downloaded-image/)

Thank you very much!

---

### Post by php111 on 2013-06-30
Sorry, but 32-bit works but I get a message when I tried 64-bit that said something like I have an i686 CPU. I did not at understand the 32-bit and 64-bit hosts from the first page of this thread. I admit its confusing and I'm not understanding at all what was said.

---

### Post by CharlesA on 2013-06-30
You will have issues running a 64-bit guest on a 32-bit host. I don't really remember the requirements off hand because I have always run 64-bit OSes on my VM hosts.

I do not they seem kinda touchy, so I'd just stick with a 32-bit guest.

---

### Post by php111 on 2013-06-30
I don't even have x64 anyway. I just checked the ACPI in Hardware and I have x86 based which is an i686 CPU (32-bit). It can't be done. No go.

---

### Post by CharlesA on 2013-06-30
Then you should be fine to use 32-bit guests. If you run into any problems, let us know.

---

