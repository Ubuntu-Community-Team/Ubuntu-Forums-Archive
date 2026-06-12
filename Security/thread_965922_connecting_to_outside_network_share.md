---
title: "connecting to outside network share??"
date: 2008-10-31
forum: Security
---

### Post by DoubleMcLovin on 2008-10-31
Ok, so heres the scenario:
My neighbour wanted to install a program loaded on a DVD. She doesn't have a dvd player so this is a problem.
I take the DVD home and begin making an ISO file of it, planning to mount it virtually on that computer.
Now, rather then crafting some kind of removable HDD to walk over there, I would much rather just send it over a network. So I set up a network share on that computer. I can connect to her wifi, but the signal is so low, it would take me a very long time to send this file. And she does have a VNC server enabled, and I do have full access to her router, all with her full permission.


So my question is really simple, is there a way to (while staying on my current LAN connection) connect to my neighbours computer to transfer files (with full permissions) easily?

---

### Post by anystupidname on 2008-10-31
I'd suggest you compress the DVD iso into a 7zip file, forward port 22 TCP through her router to the computer and scp the file over.

Alternative options exist such as uploading the file to a file dropper account and pulling it back down directly onto their box.

I'm assuming you already know how to loop mount it...
mount -o loop disk1.iso /mnt/disk

---

### Post by DoubleMcLovin on 2008-11-01
well hers is a windows computer. Shoulda mentioned that I suppose lol. So I was just gonna use Daemon tools to mount the iso file. But I think 7zips are gonna be my best bet and just cary over like 5 cd's =\ was hoping to avoid that option, but I just came back and found that my wifi transfer failed half way through due to timeout. Can you recommend a good way to 7zip? I'm on hardy and don't have that option by default it seems.

---

### Post by cariboo on 2008-11-01
WHy not go out and buy a 8Gb usb device, you can always use it for other things once you've transfered the file. They are fairly inexpesive. I just bought one last week for $30.00CDN.

Jim

---

### Post by kevdog on 2008-11-01
Use ssh.  Its very easy to setup, and its secure.  You can even set up a reverse tunnel.

---

### Post by DoubleMcLovin on 2008-11-01
> **kevdog said:**
> Use ssh.  Its very easy to setup, and its secure.  You can even set up a reverse tunnel.

Will the SSH copy timeout with a 4GB single file transfer? I had that error with FTP transfer and wifi transfer

---

### Post by anystupidname on 2008-11-02
If you're doing the transfer through the internet instead of direct to her wifi router (which u said has a poor signal) there should not be a timeout. Furthermore, if you use an FTP app that supports resume, it won't matter if there are any timeouts. I like the idea of a flash thumb drive too. You have plenty of options here dude.

---

