---
title: "SMB has difficulties with windows machines"
date: 2009-02-12
forum: Server Platforms
---

### Post by hashbrowns on 2009-02-12
I'm running a simple ubuntu server that needs to act as a file server, for computers that are NOT on a domain, but all in different workgroups. The labs use both Linux machines and Windows XP machines, and the linux ones seem to work fine.

However, even though I've checked my share paths and my permissions (and because it works fine in Linux) I'm confused as to why whenever I try to access about 3/4 of my shares from XP, it comes back with the error:
```

\\porsche\images is not accessible. You may not have permission to use this network resource. Contact the administrator [heh] of this server to find out if you have access permissions.

The network path was not found.
```

I assume that lots of people have had this problem before but I can't find out the right tweaks to make this work without problems. I've double checked my smb.conf file and testparmed, and I can find no problems. 

If possible, I'd like to do this completely server side without changing client settings much, or even at all, because we have a computer class that is always reformatting half the lab machines anyway, which would make my settings changes useless after a week.

---

### Post by DerHesse on 2009-02-12
Hi cookie,
network path not found probably means: network path not found. 
Seems you have a name resolution problem. 
You might want to check if you can suceed using the ip-adress instead of machine name or use the fully qualified domain name. 
Of course you should as well connect the share as a valid user ("connect as" option if necessary) 
 
Greetz

---

### Post by bigbearomaha on 2009-02-12
I don't know what OS versions are on all your Windows machines.  if you want a simple file share server, that's easy enough to do.

If you do not have a domain controller or dns server setup in the lab or bldg, then you might best be served by accessing the server by it's IP addy.

 Linux side samba does not by default support encrypted passwords.   i don't know if you are offering anonymous open access to the shared dir or not.

If you do use logins to the shares, you will need to make sure the server is setup to accept encrypted passwords.

These are just some things to think over while trying to get it all out there.

Big Bear

---

### Post by hashbrowns on 2009-02-12
Thank you both for your quick responses, I should have clarified more of course. The systems are all either running 8.10 or Windows XP SP3.

I know that that server is being recognized, because I can go directly to \\porsche without a problem, and I can even see all of the shares that I have created in smb.conf - it's when I click on them that I get the error message, so I don't think it's an issue with netbios names instead of IP addresses being the best to be used.

I want to be able to offer anonymous access to MOST parts of the server, that I want all the students to get into. Then I want some parts of the server to only be for admin staff, who will have their own group, and their own usernames and share folders as well. However, there is no requirements for their passwords to be encrypted; can't I do logins to the shares without encryption, Big Bear?

Another problem is that it seems like all the samba guides I find have different subtlies between all of them, like some have "null passwords = yes" but some have "null passwords = true" and it's supposed to mean the same thing, to use that as an example. It's a little bit hard to follow for someone who's recently came from the GUI-filled world of server 2003. :)

---

### Post by bigbearomaha on 2009-02-12
For one, you can change the hosts to non encrypted passwords, but you said you wanted a server centered solution. So  I gave that info.

You don't need a DE installed to get a 'visual' experience in admin.  Webmin will give you that visual experience without needing to install a GUI on the machine. and the samba module will guide you in the setting up ofyour shares as well.

for more specific info on how to use webmin to setup samba check this link:
[URL="http://doxfer.com/Webmin/SambaWindowsFileSharing"]
http://doxfer.com/Webmin/SambaWindowsFileSharing[/URL]

Hope it helps.

Big Bear

---

### Post by hashbrowns on 2009-02-18
Actually, it was a slightly more embarrassing problem. :redface: I used an autostart linux program which changed the names of my media from my given names, to the defaults (sdb1, sdc1, etc) and so my samba links were no longer valid.

Really weird that it did that (and didn't tell me) but after I realized that and changed the .conf file, everything seems to be working fine now.

---

