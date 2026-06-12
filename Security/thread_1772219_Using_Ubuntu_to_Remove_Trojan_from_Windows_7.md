---
title: "Using Ubuntu to Remove Trojan from Windows 7"
date: 2011-05-31
forum: Security
---

### Post by coniferoussuffragist on 2011-05-31
Hopefully this is the appropriate place to post this.
 
I stupidly clicked on a spam link on my roommate's computer (I must have forgotten that I wasn't using Ubuntu and had to be much more careful) and the computer is now infected by a nasty Trojan.  (I unfortunately cannot remember the name right now, but it is a Trojan.)  Now, her computer will barely start up under the normal Windows 7 without a blue screen of death appearing, with the IRQL_NOT_LESS_OR_EQUAL error message.
 
I stumbled upon this: [http://maketecheasier.com/remove-windows-viruses-with-linux/2010/02/02/](http://maketecheasier.com/remove-windows-viruses-with-linux/2010/02/02/) and I thought I would give it a shot.
 
I don't have a flash-drive, and I'm rather tight on cash at the moment, so instead of creating a USB stick with the OS they recommended, I used my live CD of Ubuntu 10.4.  I installed Clam, and ran the update as it says, and it seemed to work alright.  When I started the scan, however, (excluding .doc files), the first message that came up was that the software was out of date, but the scan proceeded, and so I figured all was alright.  The scan took about an hour 45, and when it was done, it reported that 0 files were infected, and that there were 4 errors.  I crossed my fingers and hoped that these errors were the problem and Clam fixed it, but alas, this was not the case.  The computer is still just as screwed up.
 
Does anyone have any suggestions?  Maybe the updates couldn't be saved because I was using a live CD instead of a USB?  Hopefully this isn't the case, because I really don't want to have to go and buy a flashdrive, but I will if I must.  Can a portion of an external harddrive be used as a boot drive?
 
Thank you!

---

### Post by mastablasta on 2011-05-31
did you scan the hard drive? Try another antivirus programme that comes with linux version ([AVG Free]("http://free.avg.com/us-en/download.prd-alf"), [Avast!]("http://www.avast.com/linux-home-edition") , [http://www.makeuseof.com/tag/free-linux-antivirus-programs/](http://www.makeuseof.com/tag/free-linux-antivirus-programs/). or there are also liveCDs available that will do the clean.
 
2 or even 4GB USB key (all you need) costs like 8 or 9 EUR. maybe you can get it with 1GB that costs even less.
 
also what happened to you could have happened to your roommate as well. they should put some antivirus software (plenty of descent free ones out there such as Avast! or Avira Antivirus) and a firewall (again descent free ones such as Zone alarm or Comodo firewall). that should keep it relatively safe. also don't run computer as administrator. i've picked up one just the other week but antivirus intercepted and cleaned it. if it got passed it the firewall would have stoped it.

---

### Post by searchfgold6789 on 2011-05-31
> **mastablasta said:**
> 
also what happened to you could have happened to your roommate as well. they should put some antivirus software (plenty of descent free ones out there such as Avast! or Avira Antivirus) and a firewall (again descent free ones such as Zone alarm or Comodo firewall). that should keep it relatively safe. also don't run computer as administrator. i've picked up one just the other week but antivirus intercepted and cleaned it. if it got passed it the firewall would have stoped it.
I think that the safest way to repair the non-bootable computer is to boot from an AVG live CD. It is used at the computer repair shop I help out at, and always finds and fixes the problem. Do a Priority 3 upgrade and it will be saved to your RAM and then do a scan. After the scan is finished go in and use ClamWin or AVG Free from the local computer. It's a good idea to keep something like AVG free on the machine, but things like Zone Alarm are really not necessary, if you can get something that will protect your computer better, and also stay out of the way and not lag down your computer. I also find the AVG Link Scanner very helpful.
So, I wish you good luck ;)
 - search

---

### Post by coniferoussuffragist on 2011-05-31
Thank you both for your help!

Search, could you walk me through setting up an AVG Live CD and the steps I would take to boot my system with such?  Thank you!

---

### Post by Mark Phelps on 2011-05-31
If you go to the Kaspersky website, you will find links for downloading the following:
1) Kaspersky Rescue CD
2) tdsskiller utility

Download the first to a PC and then burn a CD from it.  Then, boot the PC from that, do an AV file update via the Internet, and run the antivirus scan.

Once that is done copy the second to the infected Windows PC and run it.  IF there is a rootkit, the utility will find it and remove it.

---

### Post by coniferoussuffragist on 2011-05-31
> **Mark Phelps said:**
> If you go to the Kaspersky website, you will find links for downloading the following:
1) Kaspersky Rescue CD
2) tdsskiller utility
 
Download the first to a PC and then burn a CD from it. Then, boot the PC from that, do an AV file update via the Internet, and run the antivirus scan.
 
Once that is done copy the second to the infected Windows PC and run it. IF there is a rootkit, the utility will find it and remove it.
 
Thank you, Mark.  Is there a way for me to download these programs without paying for them?  It seems most of the products on the website cost money.
 
Thanks.

---

### Post by searchfgold6789 on 2011-05-31
[LIST=1]
[*]Go download the [image for the AVG Rescue CD]("http://download.avg.com/filedir/inst/avg_arl_cdi_all_100_110314a3648.iso")
[*]Once it finished, use a program like [Brasero]("apt:brasero") (for Linux) or [imgburn]("http://www.fdccdn.net/33772/imgburn/SetupImgBurn_2.5.5.0.exe") (for Windows) to burn the image onto a blank CD using a CD burner.
[*]Once it is finished, reboot with the CD in the CD-ROM drive.
[*]Once you get to a screen that says "boot:" type "arl" and press enter.
[*]Wait  for everything to load. Press enter to agree to the license agreement,  which basically states AVG's copyright ownage of the software and your  disability to copy it.
[*]Press enter again to start a virus definition update.
[*]Press enter again to upgrade from the internet.
[*]Press the down-arrow twice to select 'optional update' and press the spacebar. Then press Enter to continue.
[*]Press Enter at the next menu to start a scan.
[*]Press Enter to select volume scanning.
[*]Select your Windows partition with the up and down arrow keys, then press Space to select it and press Enter.
[*]Press Enter again at the Program Options menu.
[*]Press  Enter to officially begin a scan of your C:\ drive which will take a  couple hours, depending on many things like processor speed and disk  space, as well as fragmentation if that is an issue.
[*]Once it  finishes, select 'deal with each file separately' so you can take an  overview of the virus's path of destruction through your files.
[/LIST]
Good Luck,
 - search

---

### Post by coniferoussuffragist on 2011-05-31
> **searchfgold6789 said:**
> [LIST=1]
[*]Go download the [image for the AVG Rescue CD]("http://download.avg.com/filedir/inst/avg_arl_cdi_all_100_110314a3648.iso")
[*]Once it finished, use a program like [Brasero]("apt:brasero") (for Linux) or [imgburn]("http://www.fdccdn.net/33772/imgburn/SetupImgBurn_2.5.5.0.exe") (for Windows) to burn the image onto a blank CD using a CD burner.
[*]Once it is finished, reboot with the CD in the CD-ROM drive.
[*]Once you get to a screen that says "boot:" type "arl" and press enter.
[*]Wait for everything to load. Press enter to agree to the license agreement, which basically states AVG's copyright ownage of the software and your disability to copy it.
[*]Press enter again to start a virus definition update.
[*]Press enter again to upgrade from the internet.
[*]Press the down-arrow twice to select 'optional update' and press the spacebar. Then press Enter to continue.
[*]Press Enter at the next menu to start a scan.
[*]Press Enter to select volume scanning.
[*]Select your Windows partition with the up and down arrow keys, then press Space to select it and press Enter.
[*]Press Enter again at the Program Options menu.
[*]Press Enter to officially begin a scan of your C:\ drive which will take a couple hours, depending on many things like processor speed and disk space, as well as fragmentation if that is an issue.
[*]Once it finishes, select 'deal with each file separately' so you can take an overview of the virus's path of destruction through your files.
[/LIST]Good Luck,
- search
 
Thanks so much, search!  The only problem that I foresee is that we use wifi provided by our apt complex.  I do not have an ethernet cord or access to a wired connection.  Will I be able to connect via wireless if I boot the system with AVG?
 
Unfortunately I'm at work right now, so that is why I'm unable to try these things out.
 
Also... would I be able to use a Mac to burn the disk?  that is the only other computer I have access too, unless I am able to get my other problem resolved: [http://ubuntuforums.org/showthread.php?t=1772222](http://ubuntuforums.org/showthread.php?t=1772222).
 
thanks once again for all of the help!

---

### Post by spynappels on 2011-05-31
> **mastablasta said:**
> i've picked up one just the other week but antivirus intercepted and cleaned it. if it got passed it the firewall would have stoped it.

Seriously? A firewall would have caught a virus or trojan if the AV didn't? Would you like to explain that for us? 

All a firewall does is allow or deny TCP/IP connections to and from your computer or network, based on a pre-defined set of rules. It does not stop infections. It may stop them communicating with the mothership if your rules are restrictive enough, but it does not stop infection.

Sorry for the hijack, but firewall myths really bug me.

---

### Post by searchfgold6789 on 2011-05-31
Yes! you can burn the CD using a Mac using this guide: [http://www.psychocats.net/ubuntu/maciso](http://www.psychocats.net/ubuntu/maciso)
I don't honestly know if you can update using a wireless connection. What you I know you *can*  do is download the updates to a directory (e.g. a USB thumb drive  >.>) using the menu from Step 7, and then boot again from the CD  and use the same menu to update from the files on the thumb drive.

---

### Post by coniferoussuffragist on 2011-05-31
> **searchfgold6789 said:**
> Yes! you can burn the CD using a Mac using this guide: [http://www.psychocats.net/ubuntu/maciso](http://www.psychocats.net/ubuntu/maciso)
I don't honestly know if you can update using a wireless connection. What you I know you *can*  do is download the updates to a directory (e.g. a USB thumb drive  >.>) using the menu from Step 7, and then boot again from the CD  and use the same menu to update from the files on the thumb drive.

I really appreciate all of your help.  Unfortunately, I'm such an amateur I can't even figure out how to download the right updates to a directory.  I can't do it from the boot menu because no matter what computer I use, I can't get on the internet since I don't have wired access.  Do you know how I could create a directory on an external HD using a mac/PC running Ubuntu off of a Live CD?

---

### Post by coniferoussuffragist on 2011-05-31
Also, when it comes time to scan the partition, do you have any idea which volume the Windows partition would be?  I'm seeing three one that's 1.5G, one that's 223.3G, and one that's 8.1G.  I'm assuming that it is without a doubt the 223.3G one, but I just want to be sure, because I have no idea what the hell I'm doing.

---

### Post by mastablasta on 2011-06-01
> **spynappels said:**
> Seriously? A firewall would have caught a virus or trojan if the AV didn't? Would you like to explain that for us? 
 
All a firewall does is allow or deny TCP/IP connections to and from your computer or network, based on a pre-defined set of rules. It does not stop infections. It may stop them communicating with the mothership if your rules are restrictive enough, but it does not stop infection.
 
Sorry for the hijack, but firewall myths really bug me.
 
you are quite right, however trojan is mostly useless unless it can connect "home" (or to internet) so this prevents it. while viruses as they were are now rare. Also Comodo firewall includes additional protective measures (they call it defense+) which can sometimes recognise trojan and block it. it can't remove or quarantine them though.
 
> Defense+, is designed to provide protection against unknown malware. It is designed to restrict the actions of unknown applications, and restrict access to important files, folders, settings and the [Windows Registry]("http://ubuntuforums.org/wiki/Windows_Registry"). Defense+ employs Default Deny Protection, by default refusing any unknown file permission to install or execute except when specifically allowed by the user or when the file appears on Comodo's whitelist

---

### Post by mastablasta on 2011-06-01
> **coniferoussuffragist said:**
> Also, when it comes time to scan the partition, do you have any idea which volume the Windows partition would be? I'm seeing three one that's 1.5G, one that's 223.3G, and one that's 8.1G. I'm assuming that it is without a doubt the 223.3G one, but I just want to be sure, because I have no idea what the hell I'm doing.
 
 
you will need to scan them all.
 
Even without upgrade you might be able to find and remove the virus.
 
Not sure about kaspersky but often other antivirus programmes have an option of Home use - ie. if you register and accept the terms that you will not use it commercially (e.g for busniess) it is free of charge. a key is provided in this case to unlock it for home use. 
 
This is the link to Kaspersky rescue disk.
[http://support.kaspersky.com/viruses/rescuedisk?level=2](http://support.kaspersky.com/viruses/rescuedisk?level=2)
 
i don'r see any payment requirement... maybe they pop up later?

---

### Post by ohadcn on 2011-06-01
i had similar problem few months ago, i tried avg/kasperky rescue disk, clam/nod32 from ubuntu live cd, win 7 built-in rescue tools and none of them helped (nod32 detected and removed the virus, but the computer remained unbootable).

cause i have no windows installation media i installed ubuntu on other partition of the machine, somehow installing ubuntu repaired windows! probably the virus infected the mbr or bcd and ubuntu instaltation write it's own mbr and fix it.

if that the case i think no anti virus will help you cause there is no virus - just not a good mbr.
you can install a bootloader of your choice and configure it to load windows.
(you can use ubuntu live cd to install grub)

[edit]

you wrote you are an amateur so i will describe how to install grub:

boot into the live cd and get into the live system.
open a console (alt+f2->x-terminal-emulator)

run:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda 
sudo grub-mkconfig -o=/mnt/boot/grub/grub.cfg /dev/sda

```then reboot.

---

### Post by mastablasta on 2011-06-01
you can get a recovery disk from microsoft to install the MBR.
 
it can be downloaded or requested provided you we using the legal copy of windows.

---

### Post by spynappels on 2011-06-01
> **mastablasta said:**
> you are quite right, however trojan is mostly useless unless it can connect "home" (or to internet) so this prevents it. while viruses as they were are now rare. Also Comodo firewall includes additional protective measures (they call it defense+) which can sometimes recognise trojan and block it. it can't remove or quarantine them though.

You are right that trojans are normally designed to phone home or open ports and in this scenario a firewall may help, but defense+ is not firewall fuctionality, and the functions it carries out are already "built-in" to the Linux way of doing things.

I don't want to drag this discussion off topic, but if a person thinks that the defense+ functionality is part of a firewall, and that as such any firewall should do the same, they are letting themselves in for a world of hurt (on non-*nix systems anyway). Firewalls ONLY allow or deny network traffic.

---

### Post by mastablasta on 2011-06-01
> **spynappels said:**
> You are right that trojans are normally designed to phone home or open ports and in this scenario a firewall may help, but defense+ is not firewall fuctionality, and the functions it carries out are already "built-in" to the Linux way of doing things.

My suggestion was ment for his roomate using windows 7 that got accidentally infected by a nasty trojan.
 
> 
I don't want to drag this discussion off topic, but if a person thinks that the defense+ functionality is part of a firewall, and that as such any firewall should do the same, they are letting themselves in for a world of hurt (on non-*nix systems anyway). Firewalls ONLY allow or deny network traffic.
 
It's a feature of Comodo firewall. Some other free ones have similar features. Again they are handy in windows environment that got infected by accident (see the OP). ;-)
 
Another thing i just remembere (not sure if this is still the case in Win7, but winXP has a couple of ports (3 or 4) open by default. And it's a good idea to close them. Agin not necessary in linux.

---

### Post by spynappels on 2011-06-01
> **mastablasta said:**
> My suggestion was ment for his roomate using windows 7 that got accidentally infected by a nasty trojan.
 

 
It's a feature of Comodo firewall. Some other free ones have similar features. Again they are handy in windows environment that got infected by accident (see the OP). ;-)
 
Another thing i just remembere (not sure if this is still the case in Win7, but winXP has a couple of ports (3 or 4) open by default. And it's a good idea to close them. Agin not necessary in linux.

Yeah, I lost sight of that for a sec. For Windows Anti-Virus, Firewall, Anti-Malware etc is essential. Glad I'm using Linux;)

---

