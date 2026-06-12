---
title: "Authenticate Windows Domain Users to Ubuntu Share"
date: 2010-04-27
forum: Server Platforms
---

### Post by SonicSteve on 2010-04-27
Hi There,

Although I'm not new to Ubuntu, I am new to the server end of things. I'm hoping some of you guys can help.

Firstly I have setup an Ubuntu 10.04 Desktop (NOT SERVER) 
I want it to share an application to a group of Windows Domain (active directory) users. So I need the Ubuntu machine to recognize the Active Directory users and groups. 
I have installed Likewise open and joined the machine to the domain. 
I'm thinking that this machine will need to synchronize the Active Directory like a domain controller would. 

Can anyone help with this or suggest another approach?

Thanks.

---

### Post by snpz on 2010-04-28
Have you logged in using your AD user name?!
Successfully joined domain?

---

### Post by R.Bucky on 2010-04-28
Use this tutorial. I use it at for joining to SBS08 without issue. [http://rbucky.com/blog/how-to-join-ubuntu-to-microsoft-active-directory-domain-using-likewise-open/](http://rbucky.com/blog/how-to-join-ubuntu-to-microsoft-active-directory-domain-using-likewise-open/)

---

### Post by SonicSteve on 2010-04-28
> **R.Bucky said:**
> Use this tutorial. I use it at for joining to SBS08 without issue. [http://rbucky.com/blog/how-to-join-ubuntu-to-microsoft-active-directory-domain-using-likewise-open/](http://rbucky.com/blog/how-to-join-ubuntu-to-microsoft-active-directory-domain-using-likewise-open/)

This is only half of the equation. It's nice that Ubuntu can authenticate to Windows Servers, but I want to be able to do the reverse. 

Honestly I haven't tried to log into the domain yet. The real issue is that I need the Ubuntu machine to act like an active directory server. I need to be able to share a folder and have the security of the Ubuntu machine recognize and accept credentials from Active Directory (windows server) users and groups. 

I've done some reading and it seems like Samba 4 will implement Active Directory, I'm trying to find a way to do it now using other technology.

---

### Post by arrrghhh on 2010-04-28
I was going to mention what you already know - Samba4 is *supposed* to bring this capability, but it has been in development for a very long time.  If Microsoft has anything to say about it, they will surely try and break it with an update, they don't want Linux boxes being domain controllers!

---

### Post by SonicSteve on 2010-04-28
> **arrrghhh said:**
> I was going to mention what you already know - Samba4 is *supposed* to bring this capability, but it has been in development for a very long time.  If Microsoft has anything to say about it, they will surely try and break it with an update, they don't want Linux boxes being domain controllers!


Absolutely,
Any time a proprietary company who is only interested in profit controls a vital technology you can bet they'll break it if we fix it. I would bet Active Directory sp1 will come out shortly after the competition cracks it. 

However I'm still hoping.

EDIT Samba 4 is in Alpha 11, 11 was released January of 2010. Definitely not fit for production use. Just imagine this;
Hey guys, I saved us thousands on hardware and licensing costs, but at any moment our Active Directory could crash. 
Can you say lead balloon?

---

### Post by koenn on 2010-04-28
> **SonicSteve said:**
> This is only half of the equation. It's nice that Ubuntu can authenticate to Windows Servers, but I want to be able to do the reverse. 

Honestly I haven't tried to log into the domain yet. The real issue is that I need the Ubuntu machine to act like an active directory server. I need to be able to share a folder and have the security of the Ubuntu machine recognize and accept credentials from Active Directory (windows server) users and groups. 

I've done some reading and it seems like Samba 4 will implement Active Directory, I'm trying to find a way to do it now using other technology.

This doesn't make sense. At all.
If your Ubunbtu server is an AD server, why would it have to use users/groups from an other (windows) AD server ? 
Or: If You have a domain already (from the Windows server), and you're planning to use accounts/groups from that domain, why on earth would you want or need to make that Ubuntu server a AD Domain Controller as well.


You just need to join the ubuntu server to the AD domain (as a member server, not a DC). This makes the domain accounts know to the ubuntu server, so you can use them for filesystem security and samba permissions.
That's all.  Any current Samba can do that, but you need to get the domain integration right first (eg with likewise-open), and configure samba correctly. 
If you want "windows style" ACLs with that rather than unix style permissions, you need to install and set up posix acl as well.

---

### Post by SonicSteve on 2010-04-28
> **koenn said:**
> This doesn't make sense. At all.
If your Ubunbtu server is an AD server, why would it have to use users/groups from an other (windows) AD server ? 
Or: If You have a domain already (from the Windows server), and you're planning to use accounts/groups from that domain, why on earth would you want or need to make that Ubuntu server a AD Domain Controller as well.


You just need to join the ubuntu server to the AD domain (as a member server, not a DC). This makes the domain accounts know to the ubuntu server, so you can use them for filesystem security and samba permissions.
That's all.  Any current Samba can do that, but you need to get the domain integration right first (eg with likewise-open), and configure samba correctly. 
If you want "windows style" ACLs with that rather than unix style permissions, you need to install and set up posix acl as well.


OK then,

To be clear, what I want is;
1. Ubuntu machine to host a samba share,
2. We have a Windows 2k3 server domain using Active Directory.
3. This share needs to be available to elementary library users, there is a group called elemlib, and there are 24 elib accounts, elib1, elib2, elib3 and so on.
4. I want to be able to specify on the Ubuntu share that these users have access. I want to be able to specify permissions as well not just give full control to the entire school.

If this can be done with Access control lists then awesome, that's what I need to learn. I have never setup something like this. I'm trying to avoid using multiple windows servers. As well as find "creative" solutions that will move us away from the dependency we have on Microsoft. This is baby step 1.

---

### Post by koenn on 2010-04-28
> **SonicSteve said:**
> OK then,
a group called elemlib, and there are 24 elib accounts, elib1, elib2, elib3 and so on.
and these are AD domain users / groups, right ?


here's a small guide:
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)
you can probably replace the winbind and kerberos stuff by likewise-open

that should allow you to set user/group/others permissions for your domain accounts. 

If you want to do it Windows style, add posix acl:
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)

---

### Post by SonicSteve on 2010-04-28
> **koenn said:**
> 
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)

[http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)

These sites are no longer in service. In fact my ISP flags them as potentially malicious.

---

### Post by arrrghhh on 2010-04-28
> **SonicSteve said:**
> These sites are no longer in service. In fact my ISP flags them as potentially malicious.

LOL mine doesn't.  I'm at work, site loaded no problem.  We have pretty strict filters as well, so I'm not sure why your ISP would think they're malicious... Unless they just have something against Belgians?

---

### Post by koenn on 2010-04-28
> **SonicSteve said:**
> These sites are no longer in service. In fact my ISP flags them as potentially malicious.
I copied those links out of my browser address bar when I posted them, they were working then. 

And every site is *potentially* dangerous. It's the ones that are [I]reallyI] malicious that you have to worry about.

---

### Post by koenn on 2010-04-28
> **arrrghhh said:**
>  ... Unless they just have something against Belgians?
that must be it  :)

---

