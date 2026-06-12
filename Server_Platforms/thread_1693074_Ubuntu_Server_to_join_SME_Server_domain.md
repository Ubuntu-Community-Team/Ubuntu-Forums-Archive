---
title: "Ubuntu Server to join SME Server domain"
date: 2011-02-22
forum: Server Platforms
---

### Post by pooke on 2011-02-22
Hi, I have encountered an issue when connecting Ubuntu Server as a CLIENT to a SME Server domain using VirtualBox.

I have the correct IP address settled. In the Samba config (US) I have the SME Server's IP address on WINS server, Password server etc. The error I get is "cannot join as a standalone computer".

Any ideas how to fix this? Thanks in advance.

---

### Post by mciverza on 2011-02-22
the quickest way to fix this is to use linux-style filesharing, called NFS.
(which is probably enabled on SME server by default)

For me, the usual process for joining any machine to the samba controlled domain requires creating a machine account for that server, otherwise it won't be permitted to join the domain.

Are you certain that the SME server is acting as a domain controller, that might be an option which was disabled at run time.

(FYI, there is an Ubuntu-based alternative to SME server, called zentyal, which is available from zentyal.org)

---

### Post by pooke on 2011-02-24
Thanks a lot for your answer. One quickie though: What do you mean by 'machine account for that server'?
 
Regards

---

### Post by pooke on 2011-02-26
bump...
 
Yes, I launched the SME server manager in the web browser and it's acting as a DC.
 
Machine acc: Does this mean I create a User in SME Server named sysadmin (name of my US user) OR dc01-ubuntu (name of the machine)? Then I do net join ....... -U sysadmin (or dc01-ubuntu)?
 
Thanks.

---

### Post by pooke on 2011-02-27
Wow, anyone? This can't be only SME related.

---

### Post by koenn on 2011-02-27
> **pooke said:**
> bump...
Machine acc: Does this mean I create a User in SME Server named sysadmin (name of my US user) OR dc01-ubuntu (name of the machine)? Then I do net join ....... -U sysadmin (or dc01-ubuntu)?
 
Thanks.
no, it means you need to create a _computer_ account
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/domain-member.html#ads-create-machine-account](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/domain-member.html#ads-create-machine-account)

and the -U <user> you need there is a Domain Admin account

---

### Post by mciverza on 2011-02-27
+1 koenn

The machine account, is so that samba knows of the computer, just like Windows has "machine accounts". The machine account must be the same as the computer's samba netbios name (the computer that you are trying to add to the domain).

But an administrative user account is required to join the computer to the domain.

---

### Post by pooke on 2011-02-27
Thanks for answers!

So in my samba config I do this: (SME Server)

workgroup = ALEX
security = domain

password server = sme server ip
wins server = sme server ip

Now I do this:
[B]net ads join -U dc01-ubuntu%12345 in SME Server.

Now?
[/B]

---

### Post by koenn on 2011-02-27
> **pooke said:**
> Thanks for answers!

...

Now I do this:
[B]net ads join -U dc01-ubuntu%12345 in SME Server.

Now?
[/B]
you can also do it later.

Do you have any idea what a Domain Admin account is ?

---

