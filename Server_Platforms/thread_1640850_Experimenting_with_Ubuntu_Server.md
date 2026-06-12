---
title: "Experimenting with Ubuntu Server"
date: 2010-12-08
forum: Server Platforms
---

### Post by micajah on 2010-12-08
In trying to help our office modernize its IT infrastructure, one of the key components is maintaing our server. We have around 50-60 people who need access to a local server - primarily for secure general file storage. These employees are geographically dispersed.  We currently use some(?) version of Windows Server which is maintained and updated by a IT company we keep on retainer. After doing some very basic research on Ubuntu Server, I would like to try and incorporate a pilot program utilizing the Ubuntu Server software.


I was successful in installing Ubuntu Server on an unused PC that I put a clean hard drive in. I have been following the direction of the Official Ubuntu Server manual to assist in the server setup, and this has progressed my cause up to a point. Having no experience maintaing any server nor a background in Linux to fall back on have been points of frustration for me. 

Can I run an Ubuntu Server alongside our current Windows server without bring everything to a screeching halt? Additionally, I am the only mac computer in an office filled with varying version of windows. 

I have begun to configure samba but need some direction from the community as to updating the workgroup so my mac can connect to the Ubuntu Server. What do I need to put in the workgroup part of the /etc/samba/smb.conf directory?

I have no doubt there will be face palms by the community after reading this thread, but I am trying my best to teach myself the Ubuntu way. Thanks in advance for those who are able to help.

---

### Post by SeijiSensei on 2010-12-08
> **micajah said:**
> Can I run an Ubuntu Server alongside our current Windows server without bring everything to a screeching halt? Additionally, I am the only mac computer in an office filled with varying version of windows. 

Yes.  I'd recommend giving it a static IP and hostname and adding an entry for it in the Windows Server's DNS records.  Then you can refer to it as something like testserver.example.com.

> I have begun to configure samba but need some direction from the community as to updating the workgroup so my mac can connect to the Ubuntu Server. What do I need to put in the workgroup part of the /etc/samba/smb.conf directory?

The workgroup definition is arbitrary; it should match whatever the Windows domain or workgroup is set to.  Same holds true for your Mac.

---

### Post by micajah on 2010-12-08
@ SeijiSensei, thank you for your help

---

