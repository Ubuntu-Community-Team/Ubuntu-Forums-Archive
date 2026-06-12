---
title: "[SOLVED] VMware Tools"
date: 2008-07-17
forum: Virtualisation
---

### Post by squashpup on 2008-07-17
I installed VMWare Player today, and I've downloaded and extracted the setup.exe for VMWare Tools twice (100+ mb download)  Both times, I get an error message when I try to start the installation:

"Error reading setup initialization file"

Does anyone know where I can get a decent working copy of VMWare Tools for version 2.0.4?  I've been tearing my hair out all day on this.

Thanks...

---

### Post by bodhi.zazen on 2008-07-17
It helps if you give more details, host OS ??? guest OS ???

I advise you install vmware server, it is freely available and more powerful then vmware player.

vmware server includes vmware tools, you install it from the vmware menu with the guest running. Details of installation depend on guest OS.

---

### Post by squashpup on 2008-07-17
Host: Xubuntu Hardy

Guest: Windows XP Pro

does Server install the same way as player?

---

### Post by dpj23 on 2008-07-17
yes vm server can be installed from repositories...  just like player can be...

---

### Post by bodhi.zazen on 2008-07-18
> **squashpup said:**
> Host: Xubuntu Hardy

Guest: Windows XP Pro

does Server install the same way as player?

similar :

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

---

### Post by jazzcommunication on 2008-07-18
if you have vmplayer already running, then install vmware tools....bit tricky :) download the vmware workstation for linux.taz.gz (208mb) from the vmware site, with "ark"(i use kubuntu) look for the windows.iso in the tar.gz file and extract only this file (20mb)
in terminal : mkdir /tmp/vmware_tools
              sudo mount -o loop windows.iso /tmp/vmware_tools
with your filemanager goto the tmp/vmware_tools directory
and copy the whole directory to your thumbdrive or whatever can be read by vmplayer... start vmplayer with your favorit VM, and run the setup from your thumbdrive
this will install vmtools inside vmplayer
now you will have a nice screen size instead of the 600*400... :)

I use vmplayer with win2k only for communication and programming my plc's because i did not get my software package working under wine..
Make sure you regulary copy your important files from your VMdrive to another partition :) success

---

### Post by squashpup on 2008-07-18
jazz -  That's the exact process I used three times (by the time I was done with it).  Never did work...each time, when I ran the setup program, it threw an error message.

I took the good advice to download Server.  Lots more features than Player,  and installed from a .pl file just like Player does.  I had to download xinetd to get it to work, but it works.  Woohoo!

Thanks for all your help folks...no more Player for me, and I've got XP up and running in Server at full screen with no statusbars, just like I wanted.

---

### Post by bodhi.zazen on 2008-07-18
Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help 
[indent]... and users looking for solutions.[/indent]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

