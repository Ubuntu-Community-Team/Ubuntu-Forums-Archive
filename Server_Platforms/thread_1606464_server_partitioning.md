---
title: "server partitioning"
date: 2010-10-26
forum: Server Platforms
---

### Post by chideock on 2010-10-26
I used the server alternate cd and followed instruction on
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) and
[http://doc.ubuntu.com/ubuntu/serverguide/C/advanced-installation.html](http://doc.ubuntu.com/ubuntu/serverguide/C/advanced-installation.html)

When at partitioning there is a requirement to set the "bootable flag" to ON. It is set off automatically.

How does one set the flag to ON because I have tried several times using several different combos of keyboard letters, including single strokes - like just pressing "enter" and can not get the flag to change from "off" to "on"?

Thanks:(

---

### Post by the_original_billq on 2010-10-26
I usually use parted..

```

parted -i /dev/hda
>set 1 boot on
>quit

```

[http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html]("http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html")

---

### Post by chideock on 2010-10-26
Thanks for that I will file it away.

However, unless I can set the "boot flag" in the manual set-up the install will not continue properly to configure the RAID and partitioning properly as per the "How-to"s I quoted above.

How does one set the flag in the manual partition for the server setup with install of RAID as per the guides I quoted?

[B]"8.As with the swap partition, select the *"Use as:"* line at the                top, changing it to *"physical volume for RAID"*. Also select the                *"Bootable flag:"* line to change the value to                *"on"*. Then choose *"Done setting up partition"*"

[/B]This is the instruction that I am referring to.

Thanks

---

### Post by psusi on 2010-10-26
The boot flag has no meaning to anything other than the windows boot code.  Don't worry about it.

---

### Post by chideock on 2010-10-26
So I ignore this one instruction on the guide and continue. I will try again however it seems to me the system will not continue, but I will try again and post the result.

Thanks

---

### Post by koenn on 2010-10-26
bootable flag is an ON/OFF thing, so you toggler it with the spacebar, probably


I'd be surprised you need that flag for linux, it's something DOS needed to identify the "active partition". Maybe software RAID also needs it, I wouldn't know.

---

### Post by chideock on 2010-10-26
I did that and the spacebar did not toggle the flag to yes.

????? Bug ??????

---

### Post by chideock on 2010-10-26
I have redone my install. Changing the flag to 'yes' is required for the install to complete properly.

Any ideas how to do this?

---

### Post by koenn on 2010-10-26
go to this step (see attachment)
select 'bootable flag' & hit enter

---

### Post by chideock on 2010-10-26
Did that also the flag did not change.

---

### Post by psusi on 2010-10-26
> **chideock said:**
> Changing the flag to 'yes' is required for the install to complete properly.


Why do you think that?

---

### Post by chideock on 2010-10-26
Why do you not think that?

A suggestion as the how to get the flag to change to yes would be of help. I have tried just enter, just the spacebar, just tab, and any other combination of keystrokes and methods to reset the flag - not happening.

Checking a post in the Installation section I am not the only having the exact same problem. I have reloaded the server cd more than 10 times in attempts to do things differently and all to the same effect no change to yes on the flag and the install will not proceed from that point with the flag set in NO.

Following the instructions here [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) " Installation Software RAID". The "bootable flag" can not be changed by any method I have tried as mentioned above. So I ignored changing the flag and continued with the rest of the sintructions to #9 Once done, select finish.. I do that - select finish - and the server returns to the partition menu and then faults out with ERROR!! "Unable to satisfy all constraints on the partition." After that the server install fails and I am into starting from cleaning the HDs and reloading from scratch.

Using 2 HD want to setup a RAID 1.

I have tried the advanced Install from here [http://doc.ubuntu.com/ubuntu/serverguide/C/advanced-installation.html](http://doc.ubuntu.com/ubuntu/serverguide/C/advanced-installation.html) - same problem.

and

I have tried using Maverick 10.10 CD (not alternate) install same issue.

The system should allow the flag to be set and it does not.

---

### Post by psusi on 2010-10-26
Maybe it should allow it to be set, but it does not matter and should continue just fine without it.  Maybe you forgot to define a root ( / ) partition and that's the problem?

---

### Post by chideock on 2010-10-26
No I followed both sets of instruction to the letter. What I have found out is that both these sets of instruction are wrong, at least for the most current versions of Ubuntu 10.10 and Ubuntu server.

Use this link as a guide [http://www.youtube.com/watch?v=-x2rZe2Z9as&NR=1](http://www.youtube.com/watch?v=-x2rZe2Z9as&NR=1)

It works and one finds that one does not have to even bother with the "boot flag"

---

### Post by koenn on 2010-10-27
> **chideock said:**
> Did that also the flag did not change.
worked for me when i checked and made that screenshot. 
That was with an 8.04 mini iso (just wanted to check which key would toggle it)

so there may be a problem with the version you're using - you might want to check if there's a bug report or a mention in the documentation about this.

---

### Post by Yhetti on 2010-10-28
Traditionally you've needed to set the bootable (or, more correctly, "active") flag by hand.  It looks like the 10.10 installer does it automagically as part of the grub2 install.  I had the same problem: could not toggle on/off.  After the install and first boot, an fdisk -l /dev/sda verifies that the bootable/active flag is indeed set, even though the UI wouldn't allow it during the install.

---

### Post by chideock on 2010-10-29
It seems that the instructions are wrong in having one try to change the "bootable flag". That should be ignored.

I found that I had undiscovered errors on the live Cd I had burned which probably was causing my problems in getting a system installed. I see now that the Live CD has a Cd-ROM error checker using that first would probably have solved some of the problems.

I managed even then to get a system up with 2 RAID partitions, swap and "/" root but have had no luck with more partitions than that. I tried a new 10.04.1 CD but the system errored out in tring to install the system files on a 3 partition setup - root, swap and /home.

What size would I need for a root partition to get the system installed?

---

### Post by psusi on 2010-10-29
> **chideock said:**
> What size would I need for a root partition to get the system installed?

10-20 gb.

---

### Post by chideock on 2010-10-29
psusi

Thanks i have not been using that much. Was using 6Gig. Will up the amount.

---

