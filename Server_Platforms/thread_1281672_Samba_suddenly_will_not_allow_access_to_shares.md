---
title: "Samba suddenly will not allow access to shares"
date: 2009-10-03
forum: Server Platforms
---

### Post by ialdobaeth on 2009-10-03
Running jaunty server on a headless box.

Just a day ago, after no known updates to the server, my wife's Windows PC suddenly stopped being able to connect to the samba shares on my server, giving an error about not having enough storage space.  So I tested with my ubuntu laptops and, while my NFS mounts still work great (thankfully), I'm no longer able to mount the samba shares in any way.

When running smbclient, I get the following:

```

root@toxicserver $smbclient //toxicserver/homes -U charles
Enter charles's password: 
Domain=[AVALON] OS=[Unix] Server=[Samba 3.3.2]
Server not using user level security and no password supplied.
tree connect failed: NT_STATUS_NO_MEMORY

```

smbtree gives me the following:

```

AVALON
	\\TOXICSERVER    		toxicserver server (Samba, Ubuntu)
		\\TOXICSERVER\IPC$           	IPC Service (toxicserver server (Samba, Ubuntu))
		\\TOXICSERVER\share          	shared
		\\TOXICSERVER\print$         	Printer Drivers
		\\TOXICSERVER\homes          	Home Directories

```


I'm pretty stumped here.

---

### Post by swerdna on 2009-10-04
Have you tried the obvious -- reboot of the switch/es and/or router/s and the server?

---

### Post by ialdobaeth on 2009-10-04
Yup.  Full reboot, plenty of restarting of samba.  I'm completely flummoxed.

-charles

---

### Post by brettg on 2009-10-04
Perhaps [this]("http://newsgroups.derkeiler.com/Archive/Comp/comp.sys.mac.system/2005-09/msg01201.html") may help?

---

### Post by SoundFriend on 2009-10-05
I updated my Jaunty server today.  Samba shares disappeared.
The update had overwritten my smb.conf file.  Nice!

Fortunately I was able to restore it from a backup.  

It has proved a good idea to back up essential configuration files like this.  

I hope you can find a backup file somewhere.

John

---

### Post by ialdobaeth on 2009-10-05
brettg:
I ran across that article myself, and even though I'm not using my server for printing (darn Lexmark printers), I gave the fix a shot to no avail.

After this problem began, I replaced my samba.conf file with a backup I had sitting around.  Oddly enough, I still got the exact same error.

---

### Post by Roasted on 2009-10-07
> **SoundFriend said:**
> I updated my Jaunty server today.  Samba shares disappeared.
The update had overwritten my smb.conf file.  Nice!

Fortunately I was able to restore it from a backup.  

It has proved a good idea to back up essential configuration files like this.  

I hope you can find a backup file somewhere.

John

Quoting for the unbelievably important practice this is to do.

I was messing around with a GUI to control samba and I screwed something up royally. I had no idea what to do or even what I did, because I was doing like 7 things at once so I couldn't even trace my memory to what was what on what computer, etc. Ultimately, I did a complete removal --purge of samba, deleting every trace of Samba.

I reinstalled Samba, pulled my smb.conf backup, bam. Literally within 60 seconds time I was up and running again.

---

### Post by ialdobaeth on 2009-10-09
Well, I did a complete purge of samba, then reinstalled it and used a nearly-unmodified smb.conf file.  Irritatingly enough, I'm getting the exact same error.  However, at this point, at least I know it's probably not the smb.conf file causing the problem.

---

### Post by ialdobaeth on 2009-10-09
After following various suggestions on the internet, I'm even more bewildered than before.  Attempting to mount the share via smbmount gives me:
```
mount error(12): Cannot allocate memory
```

From there, my search led me to a known problem that can be fixed by adding/modifying the IRPStackSize registry key on a Windows box.  Since this ain't a Windows box I'm dealing with, so that obviously gets me nowhere.  

As far as I can tell, I'm the only person on earth with this problem on a linux server.

But if I fail to fix this problem for long enough, maybe I can finally convince my wife to use Ubuntu on her laptop :)

---

### Post by ialdobaeth on 2009-11-05
Well, Samba is now working again.  I had to disable share level security, but that's okay. 

Now to install my new hard drive...

---

### Post by Roasted on 2009-11-05
> **ialdobaeth said:**
> Well, Samba is now working again.  I had to disable share level security, but that's okay. 

Now to install my new hard drive...

If you re-add share level security, do you re-introduce the error?

How are you doing security now? Or do you have it wide open?

---

### Post by ialdobaeth on 2009-11-06
Yeah, switching to Share level security causes that error to show up again.  So now I'm using User level security.  It requires Windows users to type in a username and password, but at the moment I'm okay with that.

---

