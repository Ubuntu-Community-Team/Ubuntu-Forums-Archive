---
title: "is WebDAV the best option?"
date: 2010-09-14
forum: Server Platforms
---

### Post by jonny.milano on 2010-09-14
What is the best option for internet wide "samba-like" file sharing? WebDAV?

---

### Post by capscrew on 2010-09-14
> **jonny.milano said:**
> What is the best option for internet wide "samba-like" file sharing? WebDAV?

WebDAV has nothing to do with Samba or the SMB protocol for that matter.  Nothing is the same.

---

### Post by jonny.milano on 2010-09-14
> **capscrew said:**
> WebDAV has nothing to do with Samba or the SMB protocol for that matter.  Nothing is the same.

I understand that the protocols are different but does WebDAV not serve the same general purpose as Samba (file sharing)?

---

### Post by capscrew on 2010-09-15
> **jonny.milano said:**
> I understand that the protocols are different but does WebDAV not serve the same general purpose as Samba (file sharing)?

I guess it really boils down to what "file sharing" means.  If I mail you a CD of files that could be thought of as "file sharing" too.

To my way of thinking it really is a matter of how you want to use the various protocols.  

Essentially there are 2 modes of you can use.  Transfer of files or mount remote file systems.  Which are you looking for?  Below is a very basic overview of the choices.

**WebDAV **was created to be able to upload and download files visually using a web browser to a remote host.

**FTP **is a protocol to transfer files to and from a remote host.

----------

**Samba **allows you to mount a remote file system to your file system using the SMB protocol

**NFS **uses RPC to mount a remote *nix file system to your *nix file system.

---

### Post by jonny.milano on 2010-09-15
capsrew, that is a great explanation. Thanks! So I guess I would be looking to mount the server as a network drive on Windows and Linux machines. I'm assuming that Samba is not suited to this over the internet??

---

### Post by capscrew on 2010-09-15
> **jonny.milano said:**
> capsrew, that is a great explanation. Thanks! So I guess I would be looking to mount the server as a network drive on Windows and Linux machines. I'm assuming that Samba is not suited to this over the internet??

You are right.  Samba is really for LAN use only.  

I'm not sure what you mean by "*mount the server as a network drive on Windows and Linux machines*".  You can mount local partitions to mount points in the file system or mount SMB resources (Samba shares) to mount points in the file system or File system exports (NFS) to mount points in the file system.  You can't "*mount the server as a network drive on Windows and Linux machines"*

None of the above are WAN technologies.  Certainly not secure for the public internet.  If you are looking for a ***secure ***method of transferring files via the public internet then I would use SSH and a sFTP client.

But then again, I have no idea what your situation really is.  What are you attempting to do?  What are you trying to provide?

---

### Post by jonny.milano on 2010-09-16
Oh I am just curious, wanting to learn more. I had thought that Samba would not be suited to WAN. I guess I should have said "mount server share as a network drive in windows and as a mounted share in ubuntu". Samba and network drives are very easy to use in Windows. They appear in all save dialogs and in the Windows Explorer. FTP is not as seamless in regards to graphical file management in Windows, nor Ubuntu. So a technology that allows one to mount a server share over the internet doesn't really exist? Other than Samba, that we are saying is not secure enough?

---

### Post by capscrew on 2010-09-16
> **jonny.milano said:**
> Oh I am just curious, wanting to learn more. I had thought that Samba would not be suited to WAN. I guess I should have said "mount server share as a network drive in windows and as a mounted share in ubuntu". 

Both Ubuntu (Samba) and Windows mount the resource the same way.  The names may change but what happens is the same. 
> 
Samba and network drives are very easy to use in Windows. They appear in all save dialogs and in the Windows Explorer.
The protocol SMB is tightly integrated into the Windows file manager (Windows Explorer).  Samba brings SMB functionality to the *nix world but it is not directly incorporated into a file manager (i.e Nautilus).> 
FTP is not as seamless in regards to graphical file management in Windows, nor Ubuntu. 
FTP is part of TCP/IP and was developed independent of any OS or graphical filemanager> 
So a technology that allows one to mount a server share over the internet doesn't really exist? 
Not in the sense of mounting a remote directory to a local filesystem.  There are alternatives with cloud computing.  [**_Dropbox _**]("http://en.wikipedia.org/wiki/Dropbox_(service)")being one of them.  > 
Other than Samba, that we are saying is not secure enough? Security is a big part of it. There are technical reasons too.

---

### Post by jonny.milano on 2010-09-16
capscrew, this is very helpful! yes, i have a dropbox account but would be nice to find a free, open source option. for now, i will setup webDav and play with it. thanks again for all this info.

---

