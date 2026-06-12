---
title: "Small office setup"
date: 2010-01-05
forum: Server Platforms
---

### Post by jokke91 on 2010-01-05
Hi!
I need help/tips for a small office setup with Ubuntu.
We have about four workstations and a server. What we need is authenticating with the server, and when you log on, you should see your own desktip and documents idnependent on which workstation you use. Could this be solved by placing the user's home on a server share?
We also need a server share accessible from both Linux, Windows an Mac, readable and writeable, as some prefers to bring their laptops to the office.

I've read a little bit about terminal servers, but using the workstations as thin clients sounds like a waste, as they're just as powerful as the server. "Fat" clients sounds better, but I would like a simple configuration which does not require very much mainteneance.

---

### Post by AlexanderDGreat on 2010-01-05
Great. You need to research first for Authenticating to Karmic Koala Samba PDC. Use LDAP for that. As File Sharing, you will need NFS for Unix and Samba for Windows. Don't want to discourage you, but Fat Clients are complicated and requires intermediate knowledge of LTSP.

---

### Post by jokke91 on 2010-01-05
Well, I don't think LTSP is the way to go for us. So what i'm looking for is a solution with the requirements i've already stated.

But is it possible to install the home directories on a server share?

---

### Post by Lars Noodén on 2010-01-05
> **jokke91 said:**
> ... what i'm looking for is a solution with the requirements i've already stated.

But is it possible to install the home directories on a server share?

Samba should meet those requirements (kerberos/ldap) and do well for file sharing and server-based home directories.  If you're starting to look at larger numbers, or multiple offices in different locations, then you might also look at AFS for file sharing.  

The Windows clients don't play well with anything else, or even with their own brand of server, so if there is any way at all to phase them out (not unheard of anymore) then that helps a lot.

---

### Post by jokke91 on 2010-01-05
Thanks for the help. The windows clients doesn't need authentication, only access to the shared files. I know very well how hard it is to make them communicate with anything at all (there's a reason why we're switching to Ubuntu)...

We won't need to connect to other offices, but we might expand the network with a few more computers. Everything will be on the same LAN, though.

---

### Post by cbranco on 2010-01-06
Maybe you want to try _[COLOR=Blue][eBox]("http://www.ebox-platform.com/")[/COLOR]_

---

### Post by jokke91 on 2010-01-07
Okay, I think I'll go for the OpenLDAP+Samba solution. But I Can't seem to find an updated tutorial on how to do this in Karmic. Could someone be so nice to either point me to a guide, or explain me how to do this?

I'm new to LDAP, and I woud like to learn something instead of just typing commands, so please explain the parts which are not obvious :)

---

### Post by AlexanderDGreat on 2010-01-07
Try harder on your searches mate. :) [http://ubuntuforums.org/showthread.php?t=1313472](http://ubuntuforums.org/showthread.php?t=1313472)

---

### Post by steveneddy on 2010-01-08
From a link in my sig:

hope it help with info

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#OpenLDAP](http://ubuntuguide.org/wiki/Ubuntu:Karmic#OpenLDAP)

---

### Post by AlexanderDGreat on 2010-01-08
Here's more: [http://ubuntuforums.org/showthread.php?t=1330637]("http://ubuntuforums.org/showthread.php?t=1330637")

---

### Post by jokke91 on 2010-01-08
Thank you very much for the help. The guide in the last post seems like exactly what i've been looking for!

Now I'm finished backing up documents, so I'll start switching from Windows Server and Windows 7 to Ubuntu! No more Group Policy, cryptic error messages or malware... :D

---

