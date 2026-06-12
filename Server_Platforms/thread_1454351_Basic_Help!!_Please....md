---
title: "Basic Help!! Please..."
date: 2010-04-14
forum: Server Platforms
---

### Post by risen75 on 2010-04-14
Ok.. now before i get the RTFM replies.. i'm actually trying to figure out where to look.. but if anyone is willing to just give me the answer i won't turn it down...

Ok.. i'm trying to setup my server box.. it's being setup as a web server, file server, and setup for me to be able to access it remotely (aka i do pc repair for windows users and it'd be nice to just know where ALL of my software tools are and get to them from there) 

anyways.. these things are almost all setup right now.. but the one thing i'm having issues with.. is the fact that this box does have 2 hard drives in it and i want to use both of them.. now i'm running straight command line and i can't find the info i need to reformat the second HDD (which is currently NTFS formated) and use it in this system... i'm running 9.04 as a server.. NO GUI INSTALLED! i need this with straight command line...

What do i need to look for to figure this out? :( 
i'm having trouble figuring this out and it's really getting annoying..

like i said.. i'm having trouble finding it.. that's why i'm asking for the assistance of the group on finding the info i need.. (i'm not just being a lazy n00b) 
Thanks :)

---

### Post by koenn on 2010-04-14
you need fdisk or parted to remove/create  partitions and to find the device name of the disk you want formatted.

'formatting' is done withe mkfs (make filesystem)

```
man fdisk
man parted
man mkfs
```
^ that's the RTFM part

---

### Post by volkswagner on 2010-04-14
You need to find the drive device location.

```
sudo fdisk -l
```

You need NTFS support unless you really want to reformat it.

```
sudo apt-get install ntfs-3g
```

Create a directory to mount it.

```
sudo mkdir /home/yourusername/ntfsdrivename
```

or any other location.

Mount it...Make sure you are positive of the /dev/location from above...very easy if your drives are different size.

```
sudo mount -t ntfs-3g /dev/foundinviafdisk /your/mount/location
```

You will then need to create an entry in /etc/fstab for it to automatically mount at boot time.

Some reading you can do.
```
man mount
```

```
man ntfs-3g
```

```
man fstab
```

---

### Post by risen75 on 2010-04-14
ok.. now here's the next dumb question... how do i figure out the actual location? 

/dev/what?

they are different sizes one is 80GB and the other is 120GB...

but mounting would be nice instead of reformatting..

---

### Post by koenn on 2010-04-14
read the first 2 lines in volkswagner's reply.
or the first line in my previous post.

---

### Post by risen75 on 2010-04-14
wow.. i apologize... i'm not all here today.. i'm sorry didn't see that.. thanks guys :)

---

