---
title: "FTP server with active directory authentication"
date: 2012-07-10
forum: Server Platforms
---

### Post by neuling1 on 2012-07-10
Hi guys,

I'm an apprentice and I have to install an web- and ftp-server running ubuntu.

So far I think I won't have any problems installing the web-server...here I will use the apache but considering the FTP-server I have some questions.

Basically I just have to know, which FTP-server running on ubuntu is the best or which one makes it possible to have authentication with active directory accounts because the server will run within an active directory environment.

I've read that this is possible with samba but samba is not really equal to ftp, isn't it!? Can I use the vsftpd for that and is there any HowTo documentation?

If someone could help me with that I would be very thankful.

---

### Post by compiledkernel on 2012-07-10
Your going to have to do a cross ldap / active directory like setup.  It wont work terribly well either.  This may be a bigger headache than a blessing.  Its best to just use native ldap solutions than trying to get a nix machine to jive with AD, which by the way is a HUGE pain and often doesnt work properly.  

But here , this is the kind of hybridization youll have to use  

[http://en.gentoo-wiki.com/wiki/Active_Directory_Authentication_using_LDAP](http://en.gentoo-wiki.com/wiki/Active_Directory_Authentication_using_LDAP)

---

### Post by neuling1 on 2012-07-11
Hi compiledkernel,

thank you very much for your answer.
Hmm...ok. I really thought that a hybrid system with a linux ftp-server which allows windows clients to log on is a common solution...at least my boss told me so :)

Ok, so you think it would be the best solution to go with a native windows ftp-server and not a ftp-server running on linux!?

---

### Post by compiledkernel on 2012-07-12
No. Im saying that your best bet is to synch your openldap'd ftp server with your AD server.

Look at this attempt. [http://ubuntuforums.org/showthread.php?t=1846796](http://ubuntuforums.org/showthread.php?t=1846796)

Synchronization is the key.  To my knowledge there is no way to integrate openldap and AD.

---

### Post by luvshines on 2012-07-21
> **neuling1 said:**
> Hi compiledkernel,

thank you very much for your answer.
Hmm...ok. I really thought that a hybrid system with a linux ftp-server which allows windows clients to log on is a common solution...at least my boss told me so :)

Ok, so you think it would be the best solution to go with a native windows ftp-server and not a ftp-server running on linux!?

Maybe you have already figured it out, but vsftpd can be setup with Active Directory authentication.
I have been using this for the past 3 years now

---

### Post by neuling1 on 2012-07-30
Thanks for the hint!

My boss decided to use CrushFTP but I will propose your vsftp solution to him.

---

