---
title: "Ubuntu Server 14.04 will not read usb sticks after gparted format"
date: 2015-03-01
forum: Server Platforms
---

### Post by DD1 on 2015-03-01
Lets make this more difficult then it has to be.

Gparted apparently doesnt work between desktop and server editions, even though its the same O.S., server is just missing a gui and has a few server commands. Even win 7 reads it. All my computers read the stick but the server. The server use to read it until I used gparted on it. Insert first sentence here; (xxxxxxxxxxxxx)

If gparted doesnt work the way its suppose to, then get rid of it. Is there another way to make this work without spending another day of wasted time on it. If I have to I will throw another gui on the server because that apparently works, even though I dont want it on there. Go figure.

---

### Post by volkswagner on 2015-03-01
Calm down ;)

This is likely not a problem with Gparted nor the way the disk is formatted.
Can you tell us how you tried to mount the drive?

With usb drive inserted please post output of the following.

```
sudo fdisk -l
```
```
sudo mount
```

The server edition does not have many of the auto mount applications/utilities included in the desktop versions.

---

### Post by lukeiamyourfather on 2015-03-03
> **volkswagner said:**
> The server edition does not have many of the auto mount applications/utilities included in the desktop versions.

What they said. If you want Ubuntu Server to automatically mount USB drives then install usbmount package.

```
sudo apt-get install usbmount
```

[https://help.ubuntu.com/community/Mount/USB#Automounting_.28Ubuntu_Server.29](https://help.ubuntu.com/community/Mount/USB#Automounting_.28Ubuntu_Server.29)

---

