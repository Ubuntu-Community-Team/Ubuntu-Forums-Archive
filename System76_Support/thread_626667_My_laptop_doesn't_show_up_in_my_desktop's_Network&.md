---
title: "My laptop doesn't show up in my desktop's Network&gt;Places"
date: 2007-11-29
forum: System76 Support
---

### Post by betes on 2007-11-29
I have a brand new gazv5 laptop (which I'm loving).  The Network>Places menu on both the laptop and my Ubuntu desktop show only my desktop and "Windows Network".  The two computers can ping each other, so why doesn't the laptop show up in the network places? Edit: I realized I should probably add, the desktop has a wired connection to my lynksys router and the laptop has a wireless connection to the same router.

Thats my only technical question, but I'm also in need of some advice. I'm a brand new linux user.  I want to be able to share folders and files between my machines.  I know there is a bewildering amount of information on this available via google and the various documentation sites, but I can't find any clear answer on the best way to do this.  Various sites recommend different methods/programs and recommend against other methods/programs.  I've gotten the farthest in reading about NFS, but it seems this only allows one way sharing (from server to client).  Is that correct? Can anyone provide some advice on what method to use (I don't need advice on how to do it, because I can find that elsewhere).   

Thanks for any help  and thanks to system76 for making a laptop that is so much fun to use.

Edit: So I've managed to set up NFS and can get files from server to client.  So the second part of my question is not pressing...unless someone has some sage advice they are eager to share.  As for the first part of my question, I was asking this because I though that the GUI "shared folders" would allow me to see these folders through Network>Places.  Now that I have NFS I see that that's not necessary.  I still wonder if its a possibility, but since I now have some form of file sharing running this post can be considered low priority.

---

### Post by palintheus on 2007-11-30
You need to install samba on your ubuntu machine to be able to see it on your windows network.

---

### Post by betes on 2007-11-30
Thanks for your response.  I actually don't have a windows network, as far as I know.  I have a dual boot Ubuntu-Windows desktop and a System76 Ubuntu Laptop, but I literally never booted into Windows since I set up my LAN.  However, for some reason under the Network>Places menu of the laptop and the desktop there is an icon for Windows Network.  And there isn't an icon for the laptop.  That was my original question.  Why doesn't the laptop show up in the Network>Places menu? 

 But, as I said above, now that I've got file sharing working through NFS I realize I don't need the laptop to show up in order to share files between it and the desktop.  So now its not a pressing question, but I'm just curious.

---

### Post by palintheus on 2007-11-30
Sorry I read "Windows Network" and assumed you had a windows machine you were trying to access...

---

### Post by octathlon on 2007-11-30
There are lots of how-tos out there.  I just saw this one mentioned on tuxmachines that looks like it will work for you:
[http://www.linuxlove.org/2007/11/30/sharing-ubuntu-directories-over-local-network-with-samba/](http://www.linuxlove.org/2007/11/30/sharing-ubuntu-directories-over-local-network-with-samba/)

---

