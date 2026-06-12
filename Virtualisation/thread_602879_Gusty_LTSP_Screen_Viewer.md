---
title: "Gusty LTSP Screen Viewer"
date: 2007-11-04
forum: Virtualisation
---

### Post by bazz on 2007-11-04
I upgraded to using Gusty with LTSP. The multiple screen sessions has been solved in this release however I can no longer use the screen viewer in the Thin Client Manager. I installed x11vnc on the thin client by doing the following

sudo mount --bind /dev /opt/ltsp/i386/dev
sudo mount -t proc none /opt/ltsp/i386/proc
# Make sure that resolv will work iin chroot
sudo cp /etc/resolv.conf /opt/ltsp/i386/etc/

Now chroot the /opt/ltsp/i386
sudo chroot /opt/ltsp/i386
sudo apt-get install x11vnc

I also installed ssh the same way. On Feisty all this worked. What I have noticed is that on feisty If I were to vnc to the machine I would do 
vncviewer IPAddress:0 (the ipaddress would be the ip from the dhcp server for the thin client)
And all would be good. Same idea with ssh for example ssh user@ipaddress. (once again the IP is from the DHCP server)

Now on Gusty I have found it wants to use the LTSP servers IP for everything. How can I get this to use the ip supplied from the dhcp server?
For example say the server has an ip of 192.168.1.1 and the client has 192.168.1.5
On feisty I would do vncviewer 192.168.1.5:0 and vnc would work. Same with ssh. Example ssh user@192.168.1.5
On gusty to use vncviewer I can only do vncviewer 192.168.1.1:1 (the server IP)
If I do vncviewer 192.168.1.5:0 I get unable to connect to host connection refused (111)

---

### Post by Lem on 2007-11-06
This one has me stumped too currently.. Did you get any further with this?

---

### Post by bazz on 2007-11-06
Yes a bit.
I just did a system update with the pre release updates repos. enabled and the screen viewer works, but ssh i get permission denied.

---

### Post by SpiritIsReality on 2007-11-09
howdy
bump. haha!
trails

---

### Post by bazz on 2007-11-09
Why bunmp? The screen viewer works with the update, just not ssh.

---

### Post by Lem on 2007-11-12
> **bazz said:**
> Yes a bit.
I just did a system update with the pre release updates repos. enabled and the screen viewer works, but ssh i get permission denied.

I wasn't aware of this repo. Can you post details?

---

### Post by bazz on 2007-11-12
I think it is this
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe

---

