---
title: "Trying to install Windows 7 in VB"
date: 2009-05-15
forum: Virtualisation
---

### Post by OldTimeTech on 2009-05-15
I downloaded Windoze 7 and it is an .iso file.

But when I go to load it, this is the message I get:

Failed to open the CD/DVD image /home/marianne/Windows 7/7100.0.090421-1700_x64fre_client_en-us_retail_ultimate-grc1culxfrer_en_dvd.iso.
Cannot register the CD/DVD image '/home/marianne/Windows 7/7100.0.090421-1700_x64fre_client_en-us_retail_ultimate-grc1culxfrer_en_dvd.iso' with UUID {1aff9ad9-5281-4c66-bdb6-e6f1bc18409a} because a CD/DVD image '/home/marianne/Windows 7/7100.0.090421-1700_x64fre_client_en-us_retail_ultimate-grc1culxfrer_en_dvd.iso' with UUID {7ab7be1d-8305-47d7-a166-ffb2cac70acd} already exists in the media registry ('/home/marianne/.VirtualBox/VirtualBox.xml').

I'm still trying "google" this and go through the forums for this...any help would be appreciated.

---

### Post by maflynn on 2009-05-15
Did you try burning the iso file to a dvd and install from there?  Sounds like the install process is looking for the dvd in the drive and its not there.

---

### Post by OldTimeTech on 2009-05-15
burned the iso to a dvd as an iso through gnomebaker at 2x, because what I had been reading on windows 7 forum is that it needs to be burned real slow.

---

### Post by jkarcz on 2009-05-15
In VB, I've seen that "cannot register" thing sometimes.  In my case, I had an iso file loaded in the media registry, then moved the iso file and didn't remove it from the registry.  Then I tried to reload it in the media registry and it wouldn't let me.

I think I just removed the old one first and everything worked for me.

---

### Post by OldTimeTech on 2009-05-15
Well actually I found out that my cd/dvd was not first in my bios, so the VB couldn't find the DVD I had burned.

But then when I tried to setup Windoze 7, it wanted to either wipe out my windoze XP that I already had loaded in VB or it couldn't find the drive...so my best guess at this point is it not loadable in VB.

---

### Post by NetworkGuy on 2009-05-15
Turn off all your virtual machines you have running before you do the Windows 7 Install.

Did you check the virtualbox web site to see if maybe they have tips on installing Windows 7 RC?

---

### Post by OldTimeTech on 2009-05-15
Had the winXP shut off.

Will check VB site and see if they have anything.

---

### Post by NetworkGuy on 2009-05-15
Make sure you specify a new virtual hard drive.   If setup correctly, each VM should not know anything about any other VM running.   

Sounds like you tried to do your install and accidentally setup your VM using the virtual XP hard drive.

---

### Post by OldTimeTech on 2009-05-15
Well, I won't disagree that I could of done that...

But it was looking for a drive to load it too and couldn't make it go on to just load...

I'm working off a Ubuntu machine with VB and as I said, I've already had XP loaded.  I have the newest VB 2.2.2 and Ubuntu is 8.04....

---

### Post by miwaypet on 2009-05-15
> already exists in the media registry ('/home/marianne/.VirtualBox/VirtualBox.xml').

The problem lies right where it is stated. Make sure you can see your hidden folders, Computer>Edit>Preferences. In your /home folder you should see the/.Virtualbox folder.

```
sudo gedit /home/<your Name>/.VirtualBox/VirtualBox.xml
```

In the code there will be a line with windows 7 in it. You should carefully delete that line. If you are not sure which one it is. Copy the file and paste it here. I will help pick it out.

Michael

---

### Post by OldTimeTech on 2009-05-15
Thanks Michael....

But on this site, I found my answer....

[http://www.makeuseof.com/tag/test-windows-7-rc-on-a-virtual-machine-part-2/](http://www.makeuseof.com/tag/test-windows-7-rc-on-a-virtual-machine-part-2/)

For some when I made the first Windows 7 drive it didn't show up in the window on the install.  So, I went back deleted that Windows 7 and followed the instructions on the above site and as I write this it is loading into VB...So cool!!!

And I really appreciate everyone's help, now if I could just remember where to post make this show solved I would be in Great shape...alzheimers goes along with the title...LOL!!!

---

### Post by NetworkGuy on 2009-05-15
Edit your initial post.   Change the title to add solved:

---

### Post by OldTimeTech on 2009-05-15
Thanks Network Guy....I will do now!

---

