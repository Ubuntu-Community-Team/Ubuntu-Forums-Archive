---
title: "wipe harddrives of v440 server"
date: 2012-05-02
forum: Server Platforms
---

### Post by charm_quark on 2012-05-02
hi guys, i was reading about an old thread about installing Ubuntu on a v440,

 i am sort of in the same predicament . it seems that place where I'm on intern-ship are donating there V440 sun server to some university, ( i am instructed to wipe out the data from the disk)

back-story: i have 2 sets of server,

 11 hp, that i used ubuntu 10.04 as a live disk and using *shred* i wiped out the drive..

the second set are 90 sun v440 server, ( well just so you know i'm not well versed with it)
is there any way i can accomplish the same task, ( and i've started dowloading 7.10) for sparc support. 

help !!

---

### Post by mistamidget on 2012-05-02
You should be able to do a base installation onto one drive and when partitoning mount all the others.
When installed do a
df to see the /dev/path for all the drives
then do a
dd if=/dev/null of=/dev/path for each drive, doing the / drive last.

---

### Post by charm_quark on 2012-05-02
cool will try that, but i need to find the syntax to boot from stick :) ,

---

### Post by Cheesemill on 2012-05-02
It might be quicker and easier to just plug the drives into an x86 machine and then just use a Live CD to write one pass of 0's using dd.

---

### Post by Jonathan L on 2012-05-02
Hi Charm Quark

> plug the drives into an x86 machine and then just use a Live CD to write one pass of 0's using dd.

My normal disk wiping procedure is to plug in a 3mm HSS drill through the drive a few times (not joking).  If I want to reuse it, I normally repartition to a single partition of the whole drive, and then
```
dd if=/dev/zero of=/dev/thatpartition
```

If I want to sell it, I normally put a basic OS of some kind on it.  if you've got 100 to do, I'd set up a PXE booting network and do them in batches.

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by mistamidget on 2012-05-02
Only ever played with up to the Ultra2 but wouldn't be surprised if it doesn't boot from USB.
What happens when you type 'boot usb' in OBP
Probably be best to burn image to a CD to boot from in my opinion.
then type 'boot cdrom'

---

### Post by |{urse on 2012-05-02
@op DBAN is cool for that [http://www.dban.org/download](http://www.dban.org/download)

---

### Post by |{urse on 2012-05-02
Have a look [here]("http://www.dban.org/node/39") too. The interface is very simple and does many disks (personal record of 14 mixed ide and sata as a jbod array) at once.

---

### Post by charm_quark on 2012-05-04
well, it does not boot from stick to my dismay

> It might be quicker and easier to just plug the drives into an x86  machine and then just use a Live CD to write one pass of 0's using dd.  well it seem that i  have access to only 1 ibm server that can read ScSI drives,  and just a reminder 90 server's 4 drives each = 360 drives 

80 gb each...... 

and i forgot the main part, there is no VGA card, so i'm accessing the servers through serial cable.  

i have currently acquired a solaris disk and I am using it to "pugre" _[(sun forum).,]("https://forums.oracle.com/forums/thread.jspa?threadID=2383306&tstart=0")_
 but that is taking ages, ( one drive, i started the format yesterday at 5pm, and today at 5 pm, it is still running).. deadline is sort of the coming Friday..

---

### Post by |{urse on 2012-05-04
[http://www.pendrivelinux.com/install-dban-to-a-usb-flash-drive-using-windows/](http://www.pendrivelinux.com/install-dban-to-a-usb-flash-drive-using-windows/) <-- easy.

*Important* "Remove your thumb drive after dban has loaded, but before it has started wiping drives."

---

### Post by Cheesemill on 2012-05-04
> **|{urse said:**
> [http://www.pendrivelinux.com/install-dban-to-a-usb-flash-drive-using-windows/](http://www.pendrivelinux.com/install-dban-to-a-usb-flash-drive-using-windows/) <-- easy.

*Important* "Remove your thumb drive after dban has loaded, but before it has started wiping drives."
I think you're misssing the point.
DBAN doesn't work on SPARC, only on the x86 architecture.

---

### Post by Cheesemill on 2012-05-04
How about using the SPARC version of SystemRescueCD and using it to run dd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by |{urse on 2012-05-04
Dban has support for all 32-bit x86 machines as well as beta builds for Cisco Routers, Sparc, PowerPC and HP PA-RISC hardware architecture.

Sysresccd is just amazing too though.

---

### Post by Cheesemill on 2012-05-04
> **|{urse said:**
> Dban has support for all 32-bit x86 machines as well as beta builds for Cisco Routers, Sparc, PowerPC and HP PA-RISC hardware architecture.

Sysresccd is just amazing too though.
I stand corrected. You learn something every day don't you :)

---

### Post by |{urse on 2012-05-04
Actually I'm torn as to whether to suggest sysreccd instead now that you reminded me of it. Sysreccd + partimage = awesome. You can create custom image-on-disk os reinstallation disks with it. Nice to be able to hand it to a customer and say "Your server image is on this DVD, I wrote a bash script that will install it using dd and partimage with a single keystroke, I even included a 3rd party script that will automatically rebuild your array if you need to before install" That distro has scored me serious points in the past.

---

### Post by hawkmage on 2012-05-04
You may not be able to boot a v440 from USB media, this feature is available if the OBP (Open Boot PROM) version is 4.27 or later.  

Also with the v440 you are lucky since it has a SCSI host adapter an not the Sun Fibre Channel host adapter since I have had issues with Debian and BSD based OSs supporting the FC host adapter on the Sunblade 1000 I have.

---

### Post by charm_quark on 2012-05-28
well i did fail, at booting from usb, so I burnt 20 CD's and i wipe them out.

---

