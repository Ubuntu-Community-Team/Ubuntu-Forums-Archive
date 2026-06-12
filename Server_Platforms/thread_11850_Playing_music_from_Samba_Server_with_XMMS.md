---
title: "Playing music from Samba Server with XMMS"
date: 2005-01-19
forum: Server Platforms
---

### Post by kibbea on 2005-01-19
I have Ubuntu set up as a Samba file server.  My Windows Clients can see the server and access the music files with Winamp.  They do not have a problem playing music across the network.  

However, when I am in Nautilus on my Ubuntu box I cannot play anything from XMMS.  The XMMS opens with the file name but does not play anything.  In fact, I can't see the server shares when trying to access them from XMMS.

Is there something that I need to do in Linux to get access to the samba shares for programs like XMMS.  I have no problems seeing the shares and browsing them in Nautilus or gaining access to the file server.

It would appear to me that there must be something else that I need to do, such as mount the shares or something that would let my program use those files.

Thanks for any recommendations.

---

### Post by nocturn on 2005-01-20
[QUOTE=kibbea]I have Ubuntu set up as a Samba file server.  My Windows Clients can see the server and access the music files with Winamp.  They do not have a problem playing music across the network.  

However, when I am in Nautilus on my Ubuntu box I cannot play anything from XMMS.  The XMMS opens with the file name but does not play anything.  In fact, I can't see the server shares when trying to access them from XMMS.

Is there something that I need to do in Linux to get access to the samba shares for programs like XMMS.  I have no problems seeing the shares and browsing them in Nautilus or gaining access to the file server.

It would appear to me that there must be something else that I need to do, such as mount the shares or something that would let my program use those files.

Thanks for any recommendations.[/QUOTE]

Your browsing the shares from Nautilus?

For XMMS and others to work, you will need to mount them (search mount smbfs on google).

---

### Post by kibbea on 2005-01-20
Thanks for the reply.

I tried using the "smbmount" command but it does not seem to be on my system.  It returns a "command not found" message.  I have searched the drive for the "smbmount" command but did not find it on my machine. I have the stock Warty installation on my Linux client box.  The server has samba server on it.  Do I need to have more than the samba client running on the client machine.  The program smbfs seems to be a program that calls "smbmount".  If smbfs comes with smbmount then I will download it.

---

### Post by jdong on 2005-01-20
you must install smbfs to use smbmount. You should really call **mount -t smbfs (usual arguments to smbmount)**, as this is more generic (i.e. they may change the smbmount command to something else in a future version).

---

### Post by kibbea on 2005-01-21
Thanks jdong.

I was able to mount the samba shares after installing smbfs.  Now XMMS works as expected.

---

