---
title: "Can anyone help identify this hard disk?"
date: 2010-06-11
forum: Server Platforms
---

### Post by louis--taylor on 2010-06-11
Hello, I'm not sure whether this is the right place in the forums, but...

Some administrators from a local school have given me a "RM systembase AX" server, because they where getting rid of it. It has no storage inside the hard disk holder thingys. As I have never owned a server before (I have had a deprived childhood...), I have no idea what media I need to buy to put inside.

Images of the disk holder things are here:
[http://dl.dropbox.com/u/3746044/P1110829.JPG](http://dl.dropbox.com/u/3746044/P1110829.JPG)
[http://dl.dropbox.com/u/3746044/P1110828.JPG](http://dl.dropbox.com/u/3746044/P1110828.JPG)

Can anyone help?

---

### Post by cascade9 on 2010-06-11
They will be some sort of SSI, probably hotswappable. 

I would guess that LVD 160 SCSI discs lived in those drive bays, but thats just from a forum post. Its probably the system speced here- 

[http://www.rm.com/Account/PartDescription.asp?PartNo=0DV-413](http://www.rm.com/Account/PartDescription.asp?PartNo=0DV-413)

---

### Post by louis--taylor on 2010-06-23
Sorry for the long delay!
Thank you for this information, I now have some disks inside and ready to go!

One problem I am having is an red light with an exclamation mark next to it keeps flashing and the server beeps continually when turned on. I thought this only happened because of the absence of hard disks, but it happens with them installed!

Any ideas what I am doing wrong?

---

### Post by lisati on 2010-06-23
My first thought is that maybe there's a setting somewhere in BIOS that needs to be changed.

---

### Post by CharlesA on 2010-06-23
It's probably set for RAID or something. I know there was a server at work that ran a RAID 5 on 5 SCSI disks that would have an exclaimation point if one of the drives wasn't detected.

---

### Post by louis--taylor on 2010-06-24
Any idea where about in the BIOS I would find the RAID settings?

Anyway, I am given this message when I press "F2 for setup":
[IMG]http://dl.dropbox.com/u/3746044/server_message.jpg[/IMG]

It says: > Unresolved configuration mismatch between disk(s) and NVRAM on the adapter Is this important?

---

### Post by TRoe on 2010-06-24
The adapter doesn't recognize your hard drive. Try <CTRL><M> and see if you can set it up to recognize the drive.

---

### Post by louis--taylor on 2010-06-24
I am attempting to configure the disks now. The formatter tells me that both of the disks with the ID 0 and 1 have failed. I know that both of those hard disks are OK, since they have been tested in another computer.

[IMG]http://dl.dropbox.com/u/3746044/raid_bios_config.jpg[/IMG]

---

### Post by TRoe on 2010-06-24
Did you check the jumper settings on the drives?

---

### Post by louis--taylor on 2010-06-25
How do I do that?

---

