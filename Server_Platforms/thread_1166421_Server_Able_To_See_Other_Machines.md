---
title: "Server Able To See Other Machines"
date: 2009-05-21
forum: Server Platforms
---

### Post by roystreet on 2009-05-21
Hi..I am new at running linux as a server.  I have successfully :) a ubuntu server about a week ago.  I'm only using it for a file server & it has been incredibly dependable in that short time.  I expected it to be though!  Anyway, all of my windows machines can see the server & samba works wonderfully.  Permissions are working great, etc.  I also have an external drive that plugs directly to the network so all computers can read/write to it.  
   My question is this...How can I from the command prompt (On my sever) connect to that external drive & copy some to the server.  I'm going to make my external drive a place for long-term backups which means I won't be using it as much.  It contains files on it that I eventually want on the server so I can access it any time. I'm fairly new at using the command prompt & I've done research & haven't been able to find what I'm looking for.
    In fact, I don't know how to see any machine on the network from the command prompt.

Thanks for your help,
   ~roystreet

---

### Post by malikp on 2009-05-21
Please tell how you connect the external drive to the server.
Is that USB drive? How you mount the drive?
also of you show df and mount out put will help to answer your question.

---

### Post by apel_2804 on 2009-05-22
Ok, is it kind of a nas drive with a nfs/ftp/samba share or is it direct attached to the server via usb/firewire?

---

### Post by roystreet on 2009-05-22
It connects via the LAN.  It shows up as another computer on the network.

---

### Post by llamaX on 2009-05-22
Likely SMB: mount -t smbfs -o username=ChangeMe,password=ChangeMe //ServerIP/Share /mountpath

---

### Post by roystreet on 2009-05-22
> **llamaX said:**
> Likely SMB: mount -t smbfs -o username=ChangeMe,password=ChangeMe //ServerIP/Share /mountpath

Are you saying that at the command prompt, type in:
mount -t smbfs -o username=ChangeMe,password=ChangeMe //ServerIP/Share /mountpath


Just to note, it does not require any password or username to log into the external drive.  So would I still need to input username, passowrd, etc?

Could I just type at the command prompt:
mount -t smbfs -o //ServerIP/Share /mountpath

I'm still learning the commands here, so you are really helping me.

Thanks

---

### Post by llamaX on 2009-05-22
Interesting that it doesn't take any login info.  I've never encountered this before so I ran off to do a little testing.  You'll probably want:

sudo mount -t smbfs //server/share /path/to/mount

And indeed, you type it into the console.

In case you're not familiar with sudo: it runs the command as root; the first prompt will be from sudo for your user's login password.  Then you'll get another prompt for a second password -- this is for the SMB share.  Since there is no password, anything should work here; I just hit return.

If that works, you should be able to automate it a bit further by added in just "-o password=gooses" or such after the mount type.

---

### Post by roystreet on 2009-05-22
(I was referring to the external drive doesn't need user info, sudo is definitely password protected)

I have it set up that way. The router is it's security.  Plus I only have it powered up when I'm backing up some files & then I power it down.  The file server on the other hand has security because it will always be on.

I will probably end up maybe powering up the drive every couple months or less.

There seemed to be some issues a long time ago with the security on that drive, but since I wasn't using it on a regular basis I threw up my hands.  It wasn't worth it to me when it's on such a short amount of time.

**Now I just need to figure out what command will copy files from the drive share I'm mounting to the share on the server.
**Any ideas?
Thanks for your help.
~roystreet

---

