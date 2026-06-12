---
title: "VirtualBox Help!!!!!!!!!!!!!!"
date: 2009-02-06
forum: Virtualisation
---

### Post by M!SF!TS on 2009-02-06
Okay, i got VirtualBox and everything went FLAWLESSLY on the linux side of thing, BUT!!!!!!!!!!!!! i went to install Vista... and i got a error...

i did a ASCII artwork creation on my last thread, and was politely asked to NEVER EVER EVER!!! try ASCII art work agian so i took a screen shot: so PLEASE check out the screen shot so you can see the problem for your self, and here are also some details on what versions of what i am running...

Ubuntu 8.10
VirtualBox 2.1
Windows Vista installation C.D.


Thanks Much... if i get VirtualBox to work where i can load Vista to work and THEN, get PureEdge to work (the only program i need windows for and is no open source alternative, and PureEdge dont work under wine... i will be "windows free" so to say even though i have it under a VM)

HELP!!!!!!!!!!!!!!!

---

### Post by HermanAB on 2009-02-06
I'm wondering whether you really need to run that program on Vista?  You may have better luck installing Expee instead.

BTW, there is nothing wrong with ASCII art.  Whoever objected must have had a bad hair day.

Cheers,

Herman

---

### Post by HotShotDJ on 2009-02-06
> **M!SF!TS said:**
> Okay, i got VirtualBox and everything went FLAWLESSLY on the linux side of thing, BUT!!!!!!!!!!!!! i went to install Vista... and i got a error...I took a look at the error.  I've seen this kind of thing when trying to install software from a shared folder (solution: copy from shared folder onto the virtual disk) but not when trying to install from a CD.  First of all... is "D:\" the CD drive?  Or is it an ISO image -- if you are using an ISO image, it is possible that there is some corruption in that file.  Next, are you using a full retail version of Vista, or is this a CD provided by the computer manufacturer?  If it is a CD provided by the computer manufacturer, is it an installation CD or is it a "recovery" CD?  Based on the stage of the installation where the error took place, I suspect you are using either a full retail CD or an OEM installation CD.  OEM versions can sometimes cause problems for virtualization. (I was lucky, my computer manufacturer provided an installation CD that worked exactly like a full retail CD... not all do.)

Something you might try (it may or may not help) is to enable "passthrough" for your CD drive.  Open VirtualBox and select the VM you want to use to install Vista, but don't start the VM yet.  Click on "Settings" and then CD/DVD-ROM.  Make sure "Mount CD/DVD Drive" is checked (it probably already is) and then select "Host CD/DVD Drive" and make sure your CD/DVD drive is selected.  Now, check "Enable Passthrough"

Now, start the installation and see what happens.

---

### Post by Ng Oon-Ee on 2009-02-07
Just another 'yes, try this' from me. Shared folders in VBox seem slightly flaky, some things don't run from them that DO run from your virtual hard disk etc. I think it could be something to do with shared folders having the NTFS file-system in your Ubuntu machine, maybe an ext3 shared folder wouldn't have that problem?

---

