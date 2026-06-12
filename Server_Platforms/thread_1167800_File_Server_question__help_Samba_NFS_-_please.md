---
title: "File Server question / help Samba NFS - please"
date: 2009-05-23
forum: Server Platforms
---

### Post by bertmanphx on 2009-05-23
Hello,
I've been running versions of Ubuntu and/or SuSE for a couple of years now.  I have a computer set up as a file server.  It works but, I have a couple questions:

1.  I want to share a directory to the four users on the server of Photos.  Should I put that share in a different location other than a users Home?  Is there a place that is better suited?

2.  Should I do this with NFS?  Is there a benefit?  Keep in mind that I sometimes use my laptop to log on to the server, and Samba seems to work better with the "roaming" laptop.

Thank you,

bertman

---

### Post by Sef on 2009-05-23
Moved to Server Platforms.

---

### Post by HermanAB on 2009-05-23
Howdy,

A NFS server is easier to set up than a Samba server.  It may also be faster. However, to use NFS with Windows clients, you need to install Microsoft Services for UNIX (Free download from MS Technet).

My personal preference is NFS, sine you only need to configure two lines - one on the server and one on the client.  Samba has hundreds of configuration options, meaning lots of things to get wrong.

---

### Post by bertmanphx on 2009-05-24
HermanAB,
Thanks for the input.
There is not any windows clients on this network, so that's not a problem for me. :)

I have tried NFS, but don't really know how to make a directory or location globally shared to more than one user.  I know the UID is paramount....I'll continue to research it.

bertman

---

### Post by bertmanphx on 2009-05-26
Hello,
I managed to export a directory via NFS that can be written to by different users.

Now, how to I change the permission of a directory, such that any file placed into, or created within will be writable by all users that have access?

I want to place photos into this directory, that can be altered by more than the person that placed them there.

Any help is appreciated.

Thanks,

bertman

---

