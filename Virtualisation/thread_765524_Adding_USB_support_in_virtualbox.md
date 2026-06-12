---
title: "Adding USB support in virtualbox"
date: 2008-04-24
forum: Virtualisation
---

### Post by marc.knuckle on 2008-04-24
this link seems to be saying how to enable usb support,[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html) ,but i am lost at the beginning as the terminal states that the group 'vboxusers' doesn't exist.  
help please

---

### Post by Paco758 on 2008-04-24
There is a great tutorial for adding USB support in Hardy here:

[http://forum.notebookreview.com/showthread.php?t=242936]("http://forum.notebookreview.com/showthread.php?t=242936")

As of today (24 April 2008), VirtualBox hasn't added a repo for the hardy version. I was able to install the deb package labeled for gutsy and install it without a problem, but beware. This sort of thing is tricky sometimes, and most certainly don't add the gutsy repo in hardy. Best to be patient. 

For now though, it works just fine. 

The problem of the vboxusers could be one of two things: 1) you need to add the group, or 2) you need to add your username to the group.

**Adding Groups vboxusers and usbusers**

*Shell:*

1) Add the group:

```
sudo groupadd vboxusers
```

2) Add your username to that group:

```
sudo gpasswd -a <yourusername> usbusers
```

While you're at it, since you are adding USB support, do this too (as mentioned in the tutorial above).

```
sudo groupadd usbusers
sudo gpasswd -a <yourusername> usbusers
```

*Admin Tools:*

In the menu, go to **System > Administration > Users and Groups**

This should come up.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=67042&stc=1&d=1209077414[/IMG]

Press the "**Unlock**" button at the bottom. The Groups Dialog will open:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=67043&stc=1&d=1209077414[/IMG]

Press the "Manage Groups" button on the right.

Check to see if the groups "vboxusers" and "usbusers" are in the list. If they are, click properties and tick the box next to your username.

If not, click "**Add Group**" on the right and and the group named "vboxusers" and tick the box next to your username. Do the same for "usbusers" and make a note of the group ID number, as you will need it for making the changes necessary for full USB support. 

Next, carefully follow the instructions in 
[the link mentioned above]("http://forum.notebookreview.com/showthread.php?t=242936") and you will be all set. 

Just remember not to add the repo, but rather to just download the deb package for 7.10 Gutsy (either 32 of 64 bit depending on your architecture, of course). 

Post again if you need some more help. I just got this thing running on a 64 bit Hardy install and managed to convert a vmware image that I had been using before. I am pretty pleased with the way that VirtualBox works. It's way better than the vmware 2.0 beta, IMHO. 

Good luck.

---

### Post by marc.knuckle on 2008-04-25
i am trying to follow one of the steps, the one with udev in it but it is saying access denied?

---

### Post by Paco758 on 2008-04-25
When editing all of these files, you must open them with 

```
sudo gedit ...
```

or it will deny you access since they are part of the system files. That was specified with the first file, but it goes for the rest of them as well. So it will be:

```
sudo gedit /etc/udev/rules.d/40-permissions.rules
```

Add these to the end of the file:

```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GROUP="usbusers", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"
```

and 

```
sudo gedit /etc/fstab
```

Add this line after your other volumes (be careful not to change anything else):

```
none /proc/bus/usb usbfs devgid=120,devmode=664 0 0
```

You're almost there. Keep plugging.

---

### Post by marc.knuckle on 2008-04-25
cheers paco758, brilliant. it now sees it straight away and also autoplays:KS

---

### Post by Paco758 on 2008-04-25
Awesome. I'm glad that you got it working. Cheers.

---

### Post by marc.knuckle on 2008-04-25
hello again.  i just tried fiddling with the screen settings to allow full screen as there is a beige border around the ubuntu window. it seemed that it was maybe that it was only showing as 1024 758 when the screen is 17"(???).  when i rebooted it seems to have messed up so i set it to generic and now it seems to have lost the guest additions as the mouse is getting trapped etc.  when i double clicked the install guest additions it just took me to the cd but when dounle clicking it didn't do anything so i unmounted it but now i am lost.
it now says when logging in that resolutions have failed and then says it will run in low graphics. how do i get it back to how it was a few minutes ago as in no problems when booting up?

---

### Post by marc.knuckle on 2008-04-25
sorted.  for some reason it had lost the guest additions so i followed a youtube howto for installing guest additions through the terminal and it was fine.  i then went back into screens etc and changed the resolution to the higher setting and restarted and voila.

---

### Post by Paco758 on 2008-04-25
When I installed the other day it asked me if I wanted to install the guest additions after I had rebooted the virtual machine. It downloaded and mounted an .iso file and then ran a windows installer dialog on it. 

About halfway through that process the installer appeared to hang, but when I minimized the dialog, I noticed that it had not actually hung, rather it had given me a warning about non Windows approved software, which I told it to disregard, and it finished the install, rebooted and the auto-resize works just fine. 

Glad you figured it out. I was just going to suggest going through it again, step by step, but that it was you did. Sweet.

---

### Post by marc.knuckle on 2008-04-27
hey mate, another piece of help needed if poss.
i am trying to share a folder in ubuntu so my xp pc(the host) can see it.  it is okay the other way around as i can see the xp folders that i shared while in ubuntu.  i have created a new folder in ubuntu and named it share folder-ubuntu and clicked it.  i thought i had set it to share but it isn't in 'my network places' in xp but my laptop shared folders are(the laptop is ANOTHER computer running win2000) so the workgroup is setup right.

---

### Post by Paco758 on 2008-04-27
Make sure that your new folder in Ubuntu is shared properly. Make sure that the workgroup in VBox is the name that Ubuntu is using for its Windows Network/Samba network. 

Then try:

Open virtual machine. Go to **Devices > Shared Folders** and then click the **[+]** button. Select the folder in the Linux filesystem and see if it works. I was just able to add a new folder that wasn't even shared on the Ubuntu side, which is nice, because it makes that folder only accessible by the vm and not to others on the same workgroup. I think. 

Let me know if that works for you.

---

### Post by marc.knuckle on 2008-04-27
cheers paco, could you firstly help me make sure i have the first part of your advise setup right to start with.

---

### Post by Paco758 on 2008-04-27
Either go into the Synaptic and search for **samba**. If it is not installed, install it. 

Or:

```
sudo apt-get install samba
```

---

### Post by marc.knuckle on 2008-04-27
samba must be installed already as i can see the xp folder already and i do think i remember setting it up.

it is this bit i just wanted a pointer on
'Make sure that your new folder in Ubuntu is shared properly. Make sure that the workgroup in VBox is the name that Ubuntu is using for its Windows Network/Samba network.'

---

### Post by Paco758 on 2008-05-08
Sorry for the long response time mate. I moved back to the United States from Egypt for the summer, just got back up and running. 

I'm not sure what is missing here. Did you try "Devices > Shared Folders" once the Virtualbox Windows machine is running? You should be able to select "Machine Folders" and then click the "Add folder" button on the right. Another dialog will pop up and then you have to select the add folder button again. From there you will be able to select any folder you want to share with the Virtualbox Windows machine. 

Let me know if that works.

---

### Post by dRock1286 on 2008-05-13
> **Paco758 said:**
> There is a great tutorial for adding USB support in Hardy here:

[http://forum.notebookreview.com/showthread.php?t=242936]("http://forum.notebookreview.com/showthread.php?t=242936")

...

Good luck.

This is a great article and got my usb working flawlessly.  Now if I can only find my install CD for my printer...  :D

Thanks!

---

### Post by Mhurst1 on 2008-05-13
> **dRock1286 said:**
> This is a great article and got my usb working flawlessly.  Now if I can only find my install CD for my printer...  :D

Thanks!
Just download it from there website :D

---

### Post by turboopugsleylx on 2010-01-07
Guys I have followed everything this thread says and I am still not seeing a USB in my Vbox OSE....please help!

I am added into vboxusers and usbusers groups tried reinstalling Vbox and nothing! still no usb showing up....

Help please....

---

### Post by wangsuda on 2010-01-07
> **turboopugsleylx said:**
> Guys I have followed everything this thread says and I am still not seeing a USB in my Vbox OSE....please help!

I am added into vboxusers and usbusers groups tried reinstalling Vbox and nothing! still no usb showing up....

Help please....
Have you tried this: [http://ubuntuforums.org/showthread.php?t=1365287](http://ubuntuforums.org/showthread.php?t=1365287)

---

### Post by SeattleOtaku on 2010-01-07
> **turboopugsleylx said:**
> Guys I have followed everything this thread says and I am still not seeing a USB in my Vbox OSE....please help!

The OSE version doesn't include USB support; you need the PUEL (Personal-Use/Evaluation, "closed-source") one from Sun:
[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by turboopugsleylx on 2010-01-08
well I finally got it working.....but guess what...as soon as I did my Amarok music player stopped working...any help?  I check and tried switching the audio cards booted in windows and the one used by amarok to ensure they were different and still the issue remains...can anyone help with this?

---

