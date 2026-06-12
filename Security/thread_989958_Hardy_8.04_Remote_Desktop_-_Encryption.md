---
title: "Hardy 8.04 Remote Desktop - Encryption??"
date: 2008-11-22
forum: Security
---

### Post by candtalan on 2008-11-22
I am starting to use Remote Desktop with the eventual intention of administering a relatives PC.

I see that Remote Desktop has an encryption checkbox......

What encryption is this? 

If it is ok to use, then what matching encryption is required to be used at the computer which will be hoping to connect and exercise control please?

---

### Post by Dave_Connor on 2008-11-22
I think it is LUKS and it is suppose to help against unwanted use of your machine. But keep regular un-encrypted backups of your data on external drives so if something happens and you can't un-encrypt your hardisk you won't get screwed.

---

### Post by Lars Noodén on 2008-11-22
You'll probably want to tunnel the connection via SSH instead of relying on Remote Desktop's encryption.

It would be a nice addition to Krfb and Krdc to have built-in OpenSSL support or SSH tunnelling.

---

### Post by teddks on 2008-11-22
I believe it adds SSL to the default of cleartext VNC. It is NOT disk encryption and it has NOTHING to do with LUKS, just to clarify.

---

### Post by candtalan on 2008-11-23
> **teddks said:**
> I believe it adds SSL to the default of cleartext VNC. It is NOT disk encryption and it has NOTHING to do with LUKS, just to clarify.

Thanks. It is easy to set the vnc server end (that is, the remote, target, PC, 192.168.1.6) for vnc encryption - it appears that I simply check the box 'encrypted'.

However, I cannot get a connection from the other pc.

Without encryption I just need to use:
vncviewer 192.168.1.6
and I get a vnc session - great!.

But if the encryption is required, how must I change the viewer session I wonder?

tia

---

### Post by teddks on 2008-11-23
> **candtalan said:**
> Thanks. It is easy to set the vnc server end (that is, the remote, target, PC, 192.168.1.6) for vnc encryption - it appears that I simply check the box 'encrypted'.

However, I cannot get a connection from the other pc.

Without encryption I just need to use:
vncviewer 192.168.1.6
and I get a vnc session - great!.

But if the encryption is required, how must I change the viewer session I wonder?

tia

You would need to have the opposite side supporting encryption. In the default Ubuntu vnc server, that's done via System>Preferences>Remote Desktop (go to the tab on the right, then hit 'force encryption').

---

### Post by candtalan on 2008-11-23
> **teddks said:**
> You would need to have the opposite side supporting encryption. In the default Ubuntu vnc server, that's done via System>Preferences>Remote Desktop (go to the tab on the right, then hit 'force encryption').

using terminal to connect to another machine on my lan
vncviewer 192.168.1.6

I do not get success, even if both machines have remote desktop set to allow viewing by others and also to require encryption:

```

user@novatech1:~$ vncviewer 192.168.1.6
VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Sun Nov 23 14:44:02 2008
 CConn:       connected to host 192.168.1.6 port 5900
 CConnection: Server supports RFB protocol version 3.7
 CConnection: Using RFB protocol version 3.7
 CConnection: No matching security types
 main:        No matching security types
```

Looking further, I see another thread which also suggests ssl, although the signs are that this feature has not been got to work, even recently.
[http://ubuntuforums.org/showthread.php?t=869813](http://ubuntuforums.org/showthread.php?t=869813)

Remote desktop works well without the encryption checked. However, I would only want to use it (without good encryption) on my local lan, protected from the internet by a router.

I have also found how to use the vnc option -via, which transparently uses ssh and of course requires ssh to have been installed first, on both machines.
[http://ubuntuforums.org/showthread.php?t=990436](http://ubuntuforums.org/showthread.php?t=990436)

---

