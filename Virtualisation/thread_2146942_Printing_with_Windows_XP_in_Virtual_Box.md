---
title: "Printing with Windows XP in Virtual Box"
date: 2013-05-20
forum: Virtualisation
---

### Post by Shallowmind on 2013-05-20
Hello
I have tried everything I can think to print from Windows XP but I cannot make it work.  I thought that connecting my printer to the same USB port that I used to get information into my Windows XP virtual machine would give me access to my printer.  But that does not seem to be the case.  

So what can I do to print from the VM?  

Or how can I save files from the VM (Win XP) onto a USB memory disk and then open them in Ubuntu for printing?  Is this even possible?

What I need to print are reports and files from QuickBooks for my tax man.

Thanks

---

### Post by sudodus on 2013-05-20
You need to be member of the ***vboxusers*** group in the host operating system

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

and you need to install the ***extension pack***

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

[URL="https://forums.virtualbox.org/viewtopic.php?f=24&t=36752"]https://forums.virtualbox.org/viewtopic.php?f=24&t=36752

[/URL]

---

### Post by holycow131415 on 2013-05-20
Install vb from the website and not the repos. Then install the ext pack. Reboot computer and youll be good to go.

---

### Post by supremedalek on 2013-05-20
Er, you can add the vbox repo to the list of repos you use and then install vbox from the repos. [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) has instructions for that, under **Debian-based Linux distributions**. Then you can go back to [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) and get the **VirtualBox 4.2.12 Oracle VM VirtualBox Extension Pack** as holycow131415 suggested.

Now, if you want both machines to print to the same printer, you could setup the printer in ubuntu so it can be accessed in the network and then have XP look for a network printer.

---

### Post by Shallowmind on 2013-05-21
> **supremedalek said:**
> 

Now, if you want both machines to print to the same printer, you could setup the printer in ubuntu so it can be accessed in the network and then have XP look for a network printer.


This is what I would like to do.  But I'm not sure how to on either Ubuntu or Windows.  

Thanks for all your replies.

---

### Post by Shallowmind on 2013-05-22
OK. So I am a member of the vboxusersgroup.  And I have updated and got extension packs for Virtual Box.  This changed nothing.  
I tried the CUPS approach.  But the VM (windows XP) will not connect to that at all.  It is like it doesn't even recognize it at all.

Then when I boot the VM I get the message that is shown in the screen shot: See attachment

Does this have anything to do with the problem?  

Thanks

---

### Post by SeijiSensei on 2013-05-22
Run samba on the host to share the printer, then connect to it from the Windows guest.

---

### Post by sudodus on 2013-05-22
It is possible but tricky to get the USB connection in VirtualBox. You need to tweak it a little and try different settings. Anyway, can you connect to any USB device at all? For example a USB pendrive? In that case it should be possible to connect also to a USB writer. 

Did you notice the small icon for USB connections on the bottom panel of the virtual machine window? Right-click on it to connect to a USB device.

I am talking about a connection between Windows in VirtualBox and a USB connected printer (connected to the host machine). You should not connect via CUPS.

You need the printer driver for that particular Windows version as if it were a normal installation of Windows.

---

### Post by rewyllys on 2013-05-22
When you're in Windows XP in VirtualBox, click on "Devices" in the VirtualBox menu, and then choose the option "USB Devices".  You will be shown one or more boxes with device names.  Click on the box corresponding to the printer.  That should establish the connection.

---

### Post by Shallowmind on 2013-05-22
Everyone thanks for the replies.

---

### Post by Shallowmind on 2013-05-22
> **sudodus said:**
> It is possible but tricky to get the USB connection in VirtualBox. You need to tweak it a little and try different settings. Anyway, can you connect to any USB device at all? For example a USB pendrive? In that case it should be possible to connect also to a USB writer. 

Did you notice the small icon for USB connections on the bottom panel of the virtual machine window? Right-click on it to connect to a USB device.

I am talking about a connection between Windows in VirtualBox and a USB connected printer (connected to the host machine). You should not connect via CUPS.

You need the printer driver for that particular Windows version as if it were a normal installation of Windows.

I did notice the small icon USB connections.  When I right click on it and pick what I think is the proper USB device I get that same screen as shown above.
Thanks

---

### Post by Shallowmind on 2013-05-22
> **rewyllys said:**
> When you're in Windows XP in VirtualBox, click on "Devices" in the VirtualBox menu, and then choose the option "USB Devices".  You will be shown one or more boxes with device names.  Click on the box corresponding to the printer.  That should establish the connection.

When I do this I get the same warning as posted above (screen shot).

Thanks for your help

---

### Post by Shallowmind on 2013-05-22
> **SeijiSensei said:**
> Run samba on the host to share the printer, then connect to it from the Windows guest.

Ok so I downloaded Samba.  But I don't have a clue how to connect to it from the VM guest.

Thanks

---

### Post by monkeybrain2012 on 2013-05-22
Is there any reason why you cannot print from Ubuntu?

---

### Post by Shallowmind on 2013-05-22
> **monkeybrain2012 said:**
> Is there any reason why you cannot print from Ubuntu?

I'm sorry I did not mean to mislead.  I can print from Ubuntu but not from the VM.  I would just copy and paste but QB will not allow that, and I cannot email from QB.  

Thanks

---

### Post by sudodus on 2013-05-23
- How did you install the extension pack?

- Can you connect to any USB device, for example a pendrive?

- If no go, you may need to uninstall and reinstall virtualbox. See also post #4.

---

### Post by Bucky Ball on 2013-05-23
*Thread moved to **Virtualisation**.*

---

### Post by Shallowmind on 2013-05-23
> **sudodus said:**
> - How did you install the extension pack?

- Can you connect to any USB device, for example a pendrive?

- If no go, you may need to uninstall and reinstall virtualbox. See also post #4.

I installed the latest version of Virtual Box from the prompt screen that appears when I open VB.  After I installed that another prompt screen appeared to install the extension pack, so I did this as well.
I can connect a USB memory stick and it will indicate it is connected and let me "look" in it.  This is how I was able to move my Quick Books files into QB on the VM.

However this is not the same USB port (?) that my printer is connected to.  When I click on the USB icon at the bottom right it shows an unkown device connected to a USB port (back of computer).  When I try to use this (I am fairly certain it is the printer) the computer stops all activity for about 10 seconds the screen goes slighty dull and then the warning prompt that I attached in another post pops up.  

Thanks for your help

---

### Post by sudodus on 2013-05-23
> **Shallowmind said:**
> I installed the latest version of Virtual Box from the prompt screen that appears when I open VB.  After I installed that another prompt screen appeared to install the extension pack, so I did this as well.
I can connect a USB memory stick and it will indicate it is connected and let me "look" in it.  This is how I was able to move my Quick Books files into QB on the VM.

However this is not the same USB port (?) that my printer is connected to.  When I click on the USB icon at the bottom right it shows an unkown device connected to a USB port (back of computer).  When I try to use this (I am fairly certain it is the printer) the computer stops all activity for about 10 seconds the screen goes slighty dull and then the warning prompt that I attached in another post pops up.  

Thanks for your help

You can connect a USB memory stick and it will indicate it is connected and let me "look" in it. This means that USB is working for you. This is a big step forward :-)

The next step is to recognize the USB printer. You have to install the Windows driver for that particular printer, like you have to do in a regular Windows installed directly into a computer. Install it from a CD or a downloaded file into your Windows inside Virtualbox! Then the printer should be recognized in a similar way as your USB memory stick.

---

### Post by JKyleOKC on 2013-05-24
I have a similar setup, and found that I needed to define filters in the VBox USB settings to trap the USB ports away from the host system and assign them to the VM. I could then  install my printers (an HP laser and an Epson all-in-one) in WinXP just as if it were an initial installation in a physical device, using the HP and Epson CDs. With this approach, I cannot print direct via CUPS from the host system -- but by setting the printers to be shared by the XP VM, and configuring CUPS on the host to look for them as network printers, can now print from both systems.

When I tried the other approach, with the printers being driven by the host system, shared, and the XP VM using them as network printers, I was able to print plain text but most of the special features of the printers were missing. Doing it as I describe here left all the special features intact. The trick, I believe, is to define those filters as described in the VBox manual and help screens, so that the VM takes over the ports with no interference by the host system.

---

