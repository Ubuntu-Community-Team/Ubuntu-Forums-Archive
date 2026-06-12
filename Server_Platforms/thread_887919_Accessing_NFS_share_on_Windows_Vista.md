---
title: "Accessing NFS share on Windows Vista"
date: 2008-08-12
forum: Server Platforms
---

### Post by samosamo on 2008-08-12
I've been using Samba for years but I've always wanted to try NFS. I've been googling for hours. I've gone as far as to set up the nfs server on ubuntu, but I have no idea how to configure Vista as the client. I enabled both "Services for NFS" and "Subsystem for UNIX-based applications" (but I haven't installed the 500mb SDK, did I need that)?

After this I have to get OSX to work as a client, I hope thats easier. Anyone have any tips for me ?

---

### Post by samosamo on 2008-08-12
OK so I set it up in OSX, it was easy as one "mount" command (what else did you expect?) and WOW... 6.5MB/s over a wifi-N connection.  That is more than double what I was getting with CIFS.  I'm never using samba again !

Someone point me in the right direction of using Windows as a client, please!

---

### Post by jerome1232 on 2008-08-13
[http://support.microsoft.com/kb/324055](http://support.microsoft.com/kb/324055)

first result on google :) I might try this out but I like samba so far

---

### Post by cariboo on 2008-08-13
I've found speed issues with samba when transfering large numbers of files. My prefered method of transfering files locally is via ftp.

Jim

---

### Post by jlowery354 on 2008-08-13
If you did something like in this HOWTO: topic [http://ubuntuforums.org/showthread.php?t=652640]("http://ubuntuforums.org/showthread.php?t=652640") go to start, network, and click your server's name. Then click the username for the fileserver and enter the username and password

---

### Post by samosamo on 2008-08-13
> **jerome1232 said:**
> [http://support.microsoft.com/kb/324055](http://support.microsoft.com/kb/324055)

first result on google :) I might try this out but I like samba so far

You see the date on that article?  Its for XP. Vista has NFS support built-in (it just needs to be turned on)

---

### Post by samosamo on 2008-08-13
> **jlowery354 said:**
> If you did something like in this HOWTO: topic [http://ubuntuforums.org/showthread.php?t=652640]("http://ubuntuforums.org/showthread.php?t=652640") go to start, network, and click your server's name. Then click the username for the fileserver and enter the username and password

That is completely unrelated to this thread...

---

### Post by jerome1232 on 2008-08-13
> **samosamo said:**
> You see the date on that article?  Its for XP. Vista has NFS support built-in (it just needs to be turned on)
No honestly I just glanced at it I saw windows xp and decided it was up to date enough :)

---

### Post by windependence on 2008-08-13
> **samosamo said:**
> OK so I set it up in OSX, it was easy as one "mount" command (what else did you expect?) and WOW... 6.5MB/s over a wifi-N connection.  That is more than double what I was getting with CIFS.  I'm never using samba again !

Someone point me in the right direction of using Windows as a client, please!
Actually, on my Macbook Pro I didn't have to do anything and I shouldn't since the underlying OS is Darwin (BSD). I just connected to the network share. Of course I had to export the NFS share from the server.

-Tim

---

### Post by samosamo on 2008-08-13
> **windependence said:**
> Actually, on my Macbook Pro I didn't have to do anything and I shouldn't since the underlying OS is Darwin (BSD). I just connected to the network share. Of course I had to export the NFS share from the server.

-Tim

You mean it saw it in Finder?  I had trouble with that, possibly because I'm running Samba and NFS servers on the same machine?  Even so, its simple enough.

---

### Post by HermanAB on 2008-08-13
The better versions of Vista has NFS support.  The El'Cheapo versions don't:
[http://www.stevencrowder.com/?q=node/6](http://www.stevencrowder.com/?q=node/6)

Anyhoo, the easiest way to share files is via FTP actually.

Cheers,

Herman

---

### Post by samosamo on 2008-08-13
Second page and still no answer???

I have Vista Ultimate. That is the best version.

I am not interested in FTP.  I am interested in NFS.

---

### Post by eggert on 2008-08-13
Maybe this is useful information for you ?

[http://www.vistax64.com/vista-networking-sharing/40707-nfs-server-how-get-nfs-share-vista.html](http://www.vistax64.com/vista-networking-sharing/40707-nfs-server-how-get-nfs-share-vista.html)

hope this helps.

---

### Post by samosamo on 2008-08-14
> **eggert said:**
> Maybe this is useful information for you ?

[http://www.vistax64.com/vista-networking-sharing/40707-nfs-server-how-get-nfs-share-vista.html](http://www.vistax64.com/vista-networking-sharing/40707-nfs-server-how-get-nfs-share-vista.html)

hope this helps.

That link is for starting an NFS server, not a client... I can't imagine why something so simple seems so difficult.

---

### Post by jerome1232 on 2008-08-14
Your question has already been answered, try reading the links given to you, from [http://www.stevencrowder.com/?q=node/6](http://www.stevencrowder.com/?q=node/6)
> If you're going to try to get the NFS client working in Vista, you have to have either Enterprise edition or Ultimate edition. The other versions, from what I can tell, do not have NFS client support.

To get started, I needed to install two things:
and then it goes on to explain how to get vista working as an nfs client

---

### Post by MemoryDump on 2008-10-23
> **jerome1232 said:**
> Your question has already been answered, try reading the links given to you, from [http://www.stevencrowder.com/?q=node/6](http://www.stevencrowder.com/?q=node/6)

and then it goes on to explain how to get vista working as an nfs client

I've followed these instructions however I still can't seem to mount NFS shares in Vista. Vista won't even let me browse NFS shares. Is there any other settings in Vista I have to set/disable?

The servers can see each other no problem. I've even tried disabling my Vista firewall to see if this helped. (it didn't)

this is so frustrating :(

---

