---
title: "Problems Installing MS Office 2010 in VirtualBox"
date: 2012-04-29
forum: Virtualisation
---

### Post by No1StoppedMe on 2012-04-29
So I'm running Ubuntu 12.04 with Virtual Box running Windows 7 Pro 64-bit and I'm trying to install MS Office 2010. When I try to run the 32-bit setup I get the following error:

"D:\x86\ProPLusr.WW\OSETUP.DLL digital signature does not validate or is not present."

And when I try to run the MS Office 64-bit setup I get this:

"Setup cannot continue because a required file is either corrupted or not available. Run Setup again from the original cource disc or download location."

Now I know the disk is still good because I installed MS Office using it today on my new laptop but for some reason it's giving me problems in Virtual Box. Any ideas?

---

### Post by xGrp on 2012-04-30
I think you should install version 2007 with winetrick, make sure the volume be office12.iso

1.- Open winetricks

2.- install app

3.- choise Office 2007 pro

4- when winetricks ask for CD, just put it into drive and follow instructions

alternative way (use Libre Office and kexi for DB)

:)

---

### Post by Habitual on 2012-04-30
I used to get similar errors on **copied** media (CDs). 
Even after years of installing my slipstreamed SP3 copy of a Retail SP2 CD, that copy died also.

Eventually, I tossed out all my copied media disks and kept the Original WinXP/SP2 disk that I purchased from MS.  I believe media quality on CDs has taken a dump since it's conception,

Yes, I purchased Window XP from Microsoft. 
Funny, that CD has NEVER given me any issue what-so-ever.

Is your installation media on original Media? (NOT a copy of one)

---

### Post by hackerseraph on 2012-04-30
Why not try dragging the setup files from the cd onto the desktop and running them from there? Perhaps there is an issue passing the drive through ?

---

### Post by No1StoppedMe on 2012-04-30
> **Habitual said:**
> I used to get similar errors on **copied** media (CDs). 
Even after years of installing my slipstreamed SP3 copy of a Retail SP2 CD, that copy died also.

Eventually, I tossed out all my copied media disks and kept the Original WinXP/SP2 disk that I purchased from MS.  I believe media quality on CDs has taken a dump since it's conception,

Yes, I purchased Window XP from Microsoft. 
Funny, that CD has NEVER given me any issue what-so-ever.

Is your installation media on original Media? (NOT a copy of one)

It's an .ISO image downloaded from Microsoft's MSDN site. Legal product key and everything. For some reason it is giving me issues in Virtual Box only. As I said it installed fine yesterday on my new laptop so I know it's not a problem with the disk.

---

### Post by No1StoppedMe on 2012-04-30
> **hackerseraph said:**
> Why not try dragging the setup files from the cd onto the desktop and running them from there? Perhaps there is an issue passing the drive through ?

You mean dragging them onto the Windows desktop being run in Virtual Box? I've never thought of trying that. Can you give me more details?

---

### Post by Habitual on 2012-04-30
> **hackerseraph said:**
> Why not try dragging the setup files from the cd onto the desktop and running them from there? Perhaps there is an issue passing the drive through ?

I'd try this method.^^^^ :)
Copy the files from the media to disk, or mount the the ISO and find/run the setup.exe inside the Vbox guest. Alternately, mounting the disk, or ISO in the Linux Host and share that folder/mnt/ point.

Also, it may help to reburn the media at MAX_SPEED -1

HTH.

---

### Post by No1StoppedMe on 2012-04-30
Thanks for your help and suggestions guys. I don't know what was causing the issue but I just upgraded to the new version of Virtual Box that was released today and that seems to have fixed the problem. I was able to run the setup files from the disk with no problems after the upgrade. If that hadn't have worked I would have of course tried your suggestion. Thanks for the input. Next time if I have a similar problem I'll be sure to explore your solution.

---

### Post by Habitual on 2012-04-30
Glad it all worked out.
+1

---

### Post by Copper Bezel on 2012-11-23
For future reference, I believe I've isolated No1StoppedMe's solution: be sure that the host optical drive is set to passthrough. 

I experienced this problem under Ubuntu 12.04 LTS with the most recent VirtualBox non-OSE version built for 12.04 and with Windows 7 Home Premium as the guest OS. 

I got exactly the same error dialogue as attested above. As is often the case, MS Office was the reason I needed the Windows virtual machine in the first place, so I was stymied at this error. The copy of MS Office was on a special institutional license, so a special disk, but I'd previously installed it in Wine without hassle (on a machine where I couldn't use virtualization instead.)

I also noticed, however, that when I inserted the Office installer disk, it mounted both to the guest OS and to the host, so the optical drive didn't seem to be on passthrough, which I thought was the default setting. Setting the device to passthrough allowed Windows to manipulate the disk directly and retrieve the signature, and installation continued without error.

---

### Post by dcstar on 2012-11-27
> **No1StoppedMe said:**
> Thanks for your help and suggestions guys. I don't know what was causing the issue but I just upgraded to the new version of Virtual Box that was released today and that seems **to have fixed the problem.**

Then MARK the thread.

---

### Post by Copper Bezel on 2012-11-27
He hasn't posted since that one in April. I only replied to the thread (necroing it) so that the next person to Google the problem, as I'd done, would have the fix for it.

---

