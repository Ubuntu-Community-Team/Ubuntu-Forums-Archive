---
title: "Samba changes date on my files"
date: 2007-02-12
forum: Server Platforms
---

### Post by leifoelgaard on 2007-02-12
Hi all

I've got a problem with my server. It is a Clarkconnect 4.0 and is working as a file server using Samba. It is working in a mixed environment with XP and Ubuntu machines.

The problem is when ever i copy a file from an Ubuntu machine to the shared drive on the server it changes the date stamp from e.g 2004-01-10 to the present date. Why is that? Is it Ubuntu or is it Samba (or maybe even Clarkconnect?). I have looked all over the place (might have overlooked something though) but with no luck. Help is needed.

Regards Leif

---

### Post by leifoelgaard on 2007-02-13
Anyone? - Please

/Leif

---

### Post by leifoelgaard on 2007-02-18
To repeat Pink Floyd: "Is there anybody out there?"  :) 

I have now reinstalled my server with Ubuntu 6.06 LTS and SAMBA (and nothing else).

And still i have this problem! 

Now it is a "Ubuntu only" environment! So the problem lies somewhere here or?

It is a really anoying problem that a lot of people must have so if somebody has a clue i am sure an answer or suggestion will bring about a lot of happy faces.

BR,

Leif

---

### Post by leifoelgaard on 2007-02-18
Yes i know - i'm pretty persistent :-)

Apparently others have had this problem before me [URL="http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=4626"] but as far i see it does unfortunately not solve the problem.

Is there a problem nobody has encountered before or am i just all alone.

/Leif

Edit:

Link: [http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=4626]("http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=4626")

---

### Post by leifoelgaard on 2007-02-20
Arghhhh - been barking up the wrong tree!

Tried copying from XP to server - IT WORKS without changing the date! So i tried using mount and then 'sudo cp -p' from Ubuntu - and it worked as well!

So it's not the server but the way Ubuntu copies files via the network. I should probably move this thread to another forum but i don't how.

Any way to make Ubuntu (Nautilus) use the '-p' switch as default?

/Leif

---

### Post by sanitycheck on 2008-03-09
I just noticed I have the same problem, but in Kubuntu 7.10 on the workstation and Kubuntu 7.10 on the SMB server.  

If I mount the remote smb server share using the mount command:

```
sudo mount -t cifs -o username=myusername,uid=myusername,gid=myusername //smbserver/share /mnt/smbserver-mountpoint
```

...and copy files, the dates stay the same.  

If I copy files by first connecting to:

```
smb://smbserver/share
``` 

...in Dolphin, the dates of the files copied change to the current date and time.

I hope someone knows a solution to this problem.

---

