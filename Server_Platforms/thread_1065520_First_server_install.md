---
title: "First server install"
date: 2009-02-10
forum: Server Platforms
---

### Post by Steelcityjim on 2009-02-10
I have just installed 8.10 on and old desktop that I had laying around.  This is my first attempt at utilizing a server and have very basic knowledge of linux.  I have a windows network in my home that i want to use this as a file server and possibly host a web page as I gain some knowledge. I was able to install the software and samba.  I see the server on my network and it shows as my server name with samba.  

I am however having a problem mounting the shared drive.  I have tried the fdisk -1 command but it does not list my drives.  can anyone provde some good directions for mounting the share drive?

---

### Post by hyper_ch on 2009-02-10
it's not "1" but "l"

```

sudo fdisk -l

```

but then, what drive do you try to mount where?

---

### Post by Steelcityjim on 2009-02-10
Im looking to mount what i believe to be the 5th partion as a windows drive on my ubunto server.  although im not seeing the 5th partion listed with the sudo fdisk -i command.  Gives me the following
usage: fdisk (-b ssz) (-u) dish change partition table
fdksi -i (-b ssz) (-u) disl list partion table
fdisk -s partition give partiino size in blocks
fdisk -v give fdisk version
here disk is someting like /dev/dev/sda
and partition is something like /dev/hda7

any help?

---

### Post by volkswagner on 2009-02-11
> **hyper_ch said:**
> it's not "1" but "l"

```

sudo fdisk -l

```

but then, what drive do you try to mount where?

As hyper_ch mentioned you have the syntax wrong.

you need to use the letter "ell" as in j k [COLOR="Red"]"l"[/COLOR] m n.

I a not sure if this is a language or keyboard issue or just user error.

Just copy and paste the following.

```
sudo fdisk -l
```

---

### Post by Steelcityjim on 2009-02-11
Great success.  Ok that listed my drives.  I have the following partitions
dev/sda1
dev/sda2
dev/sda5
dev/sda6
dev/sda7
dev/sda5

I would like to mount dev/sda5 as the windows share drive can anyone assist?

---

