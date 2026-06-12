---
title: "How to protect system from cloning?"
date: 2014-09-07
forum: Security
---

### Post by Oneprotection on 2014-09-07
Hello there,

I would like to protect a Linux system from cloning, I don't mind if the  cloned hard drive works in the same computer, but I need to avoid it to  work in other one, even if it uses exactly same mainboard model and  rest of computer parts. I want the cloned system to get frozen or simply  restart continously if it's used in another computer.

I found a thread in other forum that talks about a test of the NIC interface's MAC. It could be a good solution.

The issue is that I have no information at all about how to do it, nor  the software to use. Of course, I would like it to be as "unbreakable"  as possible.

Many regards in advance

---

### Post by pqwoerituytrueiwoq on 2014-09-07
a mac address are not 100% unique, the PCI card in my mom's pc matches the one in my dad's motherboard
i would suggest password protecting the bios/boot menu/boot options
that will not stop someone from taking the hdd out of the computer to clone it though, so put a physical lock on the case to keep them from opening it
don't give end users root access

---

### Post by bashiergui on 2014-09-07
> I would like to protect a Linux system from cloning, I don't mind if the cloned hard drive works in the same computer, but I need to avoid it to work in other one, even if it uses exactly same mainboard model and rest of computer parts. I want the cloned system to get frozen or simply restart continously if it's used in another computer.I didn't know the Mad Cloner was out striking innocent computers again!

What are you trying to accomplish? Even if you can sabotage clones of your machine, there are other methods for copying your drive that will remain effective.

---

### Post by Oneprotection on 2014-09-07
> **pqwoerituytrueiwoq said:**
> a mac address are not 100% unique, the PCI card in my mom's pc matches the one in my dad's motherboard
i would suggest password protecting the bios/boot menu/boot options
that will not stop someone from taking the hdd out of the computer to clone it though, so put a physical lock on the case to keep them from opening it
don't give end users root access

Many thanks for your answer, pqwoerituytrueiwoq, I really appreciate your time and interest.

I can't install a physical lock on the case, neither lock bios or boot menu. The user must be able to use the computer, add new drives or even format hard drive using a tool in a usb drive if he needs. It's even desirable that user can make a backup of the system disk via cloning, and restoring it when needed. BUT I don't want the user to clone disk and use the operative system and all configurations and programs in a different machine, since it's intended to be used only on this computer (I hope that my explanation is ok, hehe)

TPM could be a great solution, but it means adding more hardware since it's not included on motherboard, so it's discard.

I know that there is no infallible method for this, but is better having a security method that can be skipped to have no security method at all. If I add some kind of protection, at least the user will have to make some research.

I've been reading something about hostid, and if I can tie the operative system to something depending on hardware, it is an important "first step", no matter even if there is the coincidence that another machine has the same MAC or hostid, but at least it will not work in most other computers (that have different MAC/hostid).

Many thanks again, I hope someone can lend me a hand.

Regards

> **bashiergui said:**
> I didn't know the Mad Cloner was out striking innocent computers again!

What are you trying to accomplish? Even if you can sabotage clones of  your machine, there are other methods for copying your drive that will  remain effective.

Thanks for your interest, bashiergui,

I think in my reply to pqwoerituytrueiwoq in this same post I've explain what I need. Of course I know there no completely safe way, but I would try the best possible solution. At this moment, by simply using clonezilla the user can use the system on another machine, so anything that make it not work is a good start.

Regards

---

### Post by CharlesA on 2014-09-07
> **Oneprotection said:**
> I think in my reply to pqwoerituytrueiwoq in this same post I've explain what I need. Of course I know there no completely safe way, but I would try the best possible solution. At this moment, by simply using clonezilla the user can use the system on another machine, so anything that make it not work is a good start.

Regards

No possible as far as I know. The whole point of cloning is to create an image of your machine and then restore it to whatever. I don't know of anything that keeps it specific to one machine other than those Dell/HP/whatever restore partition utilities.

---

### Post by Oneprotection on 2014-09-07
Many thanks, CharlesA,

I've been reading and any kind of drive encryption seems useless at all since the same clonezilla is capable of making a clone in raw mode. So my only option seems to be to tie the boot to the MAC of the NIC or the serial number of the hard drive.

Any help on this?

Regards

---

### Post by uRock on 2014-09-07
The only thing I can think of would be a custom script that looks at hardware, then does bad things when it doesn't see the listed hardware. This could ruin the install if the user changed out parts. 

If you are wanting this as an anti-forensic protection, then it wouldn't do any good. Forensic experts don't usually execute softwares from clones. If they did, then it would be after making multiple copies, because allowing it to execute could destroy evidence.

I honestly can't see the reasoning for such a code, unless you are getting paid to install a system and fear the client will copy and share the install with others.

---

### Post by pqwoerituytrueiwoq on 2014-09-07
maybe detecting hte motherboard will do it
```
sudo hwinfo --bios 2>/dev/null| grep -i UUID
sudo hwinfo --bios 2>/dev/null| grep -i serial:
```
i think hwinfo has to be pulled from a older release though
perhaps you can test that value of what that returns

---

### Post by Oneprotection on 2014-09-07
> **uRock said:**
> The only thing I can think of would be a custom script that looks at hardware, then does bad things when it doesn't see the listed hardware. This could ruin the install if the user changed out parts. 

If you are wanting this as an anti-forensic protection, then it wouldn't do any good. Forensic experts don't usually execute softwares from clones. If they did, then it would be after making multiple copies, because allowing it to execute could destroy evidence.

I honestly can't see the reasoning for such a code, unless you are getting paid to install a system and fear the client will copy and share the install with others.

Hi uRock,

There is nothing dark o illegal on this, hehe, it's **exactly** what you say at the end:

> you are getting paid to install a system and fear the client will copy and share the install with others.

Any kind of encryption is unuseless since the own clonezilla supports raw cloning (that could clone a disk even if encrypted). In this point, even when I know nothing is going to be 100% safe, my best bet is some kind of testing if the MAC of the NIC or the serial number of the hard drive has change.

I've see that threre is a hdpart command on linux that seems to return among other data the serial number of the disk, so it would be perfect. My problem is that I have no idea of how to do it, so I would really thank you if can lend me a hand or guide me to the correct direction.

Many thanks in advance.


> **pqwoerituytrueiwoq said:**
> maybe detecting hte motherboard will do it
```
sudo hwinfo --bios 2>/dev/null| grep -i UUID
sudo hwinfo --bios 2>/dev/null| grep -i serial:
```
i think hwinfo has to be pulled from a older release though
perhaps you can test that value of what that returns


I'm trying and tell you, if the result with 2 motherboards with same model is different I understand we're on the right way, aren't us?

Many thanks

---

### Post by uRock on 2014-09-07
So, if the user's NIC or HDD stops working and he/she installs a new one, then he/she may have to pay you to come and "allow" the system to work with the new one?

---

### Post by Oneprotection on 2014-09-07
> **uRock said:**
> So, if the user's NIC or HDD stops working and he/she installs a new one, then he/she may have to pay you to come and "allow" the system to work with the new one?

It's not my aim at all, If i have to "allow the system to work" I'll do by free, I simply want to avoid copying the system to a third person.




Hi again, [B]pqwoerituytrueiwoq

[/B]I've try and the  commands you posted me returns nothing. I've try "hwinfo" and "sudo  hwinfo" and I get "command not found". I've try "sudo apt-get install  hwinfo" and it seems like "hwinfo" doesn't exist, even when I googled it  and I've found info

Regards

---

### Post by pqwoerituytrueiwoq on 2014-09-07
like i said it would have to be pulled from a old version, i have it cause i upgrade from a older version
[http://packages.ubuntu.com/raring/hwinfo](http://packages.ubuntu.com/raring/hwinfo)

---

### Post by HermanAB on 2014-09-08
You don't have to do anything.

if the clonee is your little kid sister, then there is no problem.

If the clonee is a Hipster Windows Sysadmin, then his Windows tools won't work, so then there is no problem.

If the clonee is a common Linux user, then he will post his question on Ubuntu Forums, will get a ton of conflicting advice and scary command line instructions causing him to accidentally format his whole disk drive and lose all his family photos, so then there is no problem. 

If the clonee is a Guru Bearded Linux Sysadmin, then nothing you can do will be able to stop him, so don't even bother trying.

---

### Post by Oneprotection on 2014-09-09
> **pqwoerituytrueiwoq said:**
> like i said it would have to be pulled from a old version, i have it cause i upgrade from a older version
[http://packages.ubuntu.com/raring/hwinfo](http://packages.ubuntu.com/raring/hwinfo)

Many thanks for the answer, pqwoerituytrueiwoq, and sorry for not answering before, I've been quite busy.

I've try to download from this link and those links fails, but I've look for the "hwinfo_16.0-2.2_amd64.deb" and found in another place so I downloaded. Now when I try to install the .deb it says that dependencies can't be meet and don't install. I'll try to get a solution and tell.

Many thanks

---

### Post by uRock on 2014-09-09
The link in the post you quoted has the dependency packages.

---

### Post by JKyleOKC on 2014-09-09
> **Oneprotection said:**
> I've try "hwinfo" and "sudo  hwinfo" and I get "command not found". I've try "sudo apt-get install  hwinfo" and it seems like "hwinfo" doesn't exist, even when I googled it  and I've found info

RegardsThis may give you some ideas. If you redirect the output to a text file instead of piping it to "grep" you will be able to tell which of these entries is likely to be unique to the machine. The 8 lines following "serial: Z2AXBSXH" are serial numbers of the 8 disk partitions on this machine, and the first (duplicated) is either the CPU or the motherboard (unless it's the whole box, since this is an HP factory-built unit).
```
sudo lshw|grep serial
    serial: 3CR2231L7N
       serial: 3CR2231L7N
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
             serial: 9653EB8
             serial: SerNum1
                serial: Z2AXBSXH
                   serial: 18fe-69d8
                   serial: 5d4104e6-9ad2-40fd-b74a-5c9d3bdbf0e0
                   serial: 9c8bffbe-9eb0-2e4e-9041-8acba3a7aa8a
                   serial: d243571a-c488-6e4f-a3a9-6746302a021a
                   serial: e56e008a-d2b1-4a6f-8f4f-dfcf5deb5900
                   serial: 648a2f16-8a11-4023-ae2d-cfb5fa7cff12
                   serial: 7d54672b-bbd5-461b-b4fb-fc5a91297553
                   serial: 9bf9ebed-6a1a-4f3b-8917-5395fedda61a
        *-serial
                serial: e8:40:f2:d4:51:2d
       serial: N/A

```You could create a hash code using several such serial numbers, and use that during the boot process -- or you could just run the "lshw" program followed by an appropriate "grep" command to isolate one or two of them.

I remember reading somewhere that Microsoft does something similar to this to verify their "activation" that began with WinXP.

You might also find good possibilities by searching the /var/log/dmesg and /var/log/syslog files at each power-up...

Hope this helps!

EDIT: I repeated this with "grep -C 2 serial" to see two lines each side of each match, and found that "Z2AXBSXH" is the serial number of the hard drive itself; that might be the best to use since a different drive would not have the same number. The 8 partition serial numbers might well change if the user added or removed partitions. The "3CR2231L7N" is the motherboard which would be even better...

---

### Post by whitesmith on 2014-09-10
You could always look at the wealth of output produced by lshw and extract UUIDs and the like from there. Naturally your code would have to be written in a compiled language to prevent a casual user from learning what you're doing and bypassing the protection scheme.

[edit] This was written before noticing JKyleOKC's post, which also advocates using lshw's data for a similar purpose.

---

