---
title: "Virtual machine - Check for consistency of data"
date: 2010-05-22
forum: Virtualisation
---

### Post by wulf-dieter on 2010-05-22
Situation: My production hard disk D: in NFTS format is used by Ubuntu 10.4, my virtual machine XP-Prof (in Ubuntu), and my stand-alone XP-Professional installation.

Problem: Very often either the virtual XP or the stand alone XP start up and check my D: drive for inconsistencies - in one case (extreme) a file was actually lost, that I had saved in the virtual machine on the D:-drive, i.e. I did not see it under Ubuntu, after shutting down the virtual machine, and I did not see the file in the stand-alone XP which had started with checking the D: drive and I actually saw the checking routine handling that particular file (name).

Question: 1) Do I have this problem because of the D: drive being in NFTS-format?
               2) Should this common production drive D: better be in Fat 32-format?
               3) If 1 and 2 are YES, how do I convert my D: NFTS into D: Fat 32?   
                   (I once did that the other way round (Fat 32 to NFTS), but have no clue to
                     do it NFTS to Fat 32):confused:

---

### Post by dcstar on 2010-05-23
> **wulf-dieter said:**
> Situation: My production hard disk D: in NFTS format is used by Ubuntu 10.4, my virtual machine XP-Prof (in Ubuntu), and my stand-alone XP-Professional installation.

Problem: Very often either the virtual XP or the stand alone XP start up and check my D: drive for inconsistencies - in one case (extreme) a file was actually lost, that I had saved in the virtual machine on the D:-drive, i.e. I did not see it under Ubuntu, after shutting down the virtual machine, and I did not see the file in the stand-alone XP which had started with checking the D: drive and I actually saw the checking routine handling that particular file (name).

Question: 1) Do I have this problem because of the D: drive being in NFTS-format?
               2) Should this common production drive D: better be in Fat 32-format?
               3) If 1 and 2 are YES, how do I convert my D: NFTS into D: Fat 32?   
                   (I once did that the other way round (Fat 32 to NFTS), but have no clue to
                     do it NFTS to Fat 32):confused:

If your VMs are checking disks already mounted by Linux then you are just asking for trouble.

Only one OS should **ever** have control of a disk, if you have followed the insane advice around the place on allowing VMs direct access to host disks then you will get issues that may result in data loss.

---

### Post by wulf-dieter on 2010-05-26
> **dcstar said:**
> If your VMs are checking disks already mounted by Linux then you are just asking for trouble.

Only one OS should **ever** have control of a disk, if you have followed the insane advice around the place on allowing VMs direct access to host disks then you will get issues that may result in data loss.


Well it is ONE virtual XP (in VW under Linux) and ONE real stand-alone XP . The Problem occurs only with data (text files) created using Word 2003 in the virtual XP in VM in Linux. It happened again yesterday - a Word-file was created on TUE and saved in the VM XP on D:. After shutting down the VM XP, the file was visible in Ubuntu 10.4 with OpenOffice. Changing OS to the non-virtual XP the file was visible and could be opened usung Word.
Starting up the VM-XP on WED resulted in doing the consistency test and I saw the index for that particular file being erased by the system and of course I could not open the file.
Switching over to the non-virtual XP same result, however there was a WORD generated safety backup that I could use to continue my translation. 
The data loss before also had to do with a Word file created and saved using the VM-XP
So far it has never occured with a file using the non-virtual OSs, neither Obuntu 9.4, 9.10, 10.4 nor XP-Prof.
:confused:
So what is the issue here? 
Fat 32 required for VM-machines?
Improper dismounting of D: in Ubuntu when starting up the VM-XP?

---

