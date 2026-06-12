---
title: "Active Directory and Samba Share"
date: 2009-01-12
forum: Server Platforms
---

### Post by Aysah on 2009-01-12
I have a quick (hopefully) question about Active Directory Users and Samba Shares.  I convinced my company into buying a an 8TB server to use as a NAS server and have successfully set up a Hardware RAID 6 and installed Fedora on it.  After lack of community support I'm now looking into ubuntu.

Is it possible to set up samba shares with permissions that utlizes usernames and groups from our ActiveDirectory (WindowsServer2003)?  If so, can someone just point me into the right direction or better yet a guide?

It has been a frustrating two weeks to get this to work and ANY help would be appreciated

---

### Post by pdtpatrick on 2009-01-12
Im just going to tell you how we have ours setup here .. we use Kerberos and LDAP for authentication via AD (btw i think you might need the unix plugin for AD so you can have the user&#347; UID in there) so when they log into linux, that would be their UID. 

In any case, the same would go for ubuntu, you will have to edit your smb.conf file so that it authenticate using LDAP. There is an ubuntu wiki documentation on how to do that. Google Ubuntu LDAP authentication or Ubuntu Active Directory Authentication and it will come up.

---

### Post by koenn on 2009-01-12
> **Aysah said:**
> 
Is it possible to set up samba shares with permissions that utlizes usernames and groups from our ActiveDirectory (WindowsServer2003)?  If so, can someone just point me into the right direction or better yet a guide?

start with this : [http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)
and this : [http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)
it's Debian/Ubuntu oriented but the mechanism should also work for Fedora. 
Has links to the official SAMBA documentation, where you can also find recipies and howtos for this sort of thing

> **Aysah said:**
> 
It has been a frustrating two weeks to get this to work and ANY help would be appreciated
Shouldn't you have looked into this sort of thing **before** you start implementing it, or better yet, before you sell the idea to your company ? Weird.

---

### Post by pdtpatrick on 2009-01-12
You make a valid point koenn  -- but i figured since he already sold the idea to the company then might as well help him instead of asking that question.

---

### Post by Aysah on 2009-01-12
> **koenn said:**
> start with this : [http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)
and this : [http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)
it's Debian/Ubuntu oriented but the mechanism should also work for Fedora. 
Has links to the official SAMBA documentation, where you can also find recipies and howtos for this sort of thing


Shouldn't you have looked into this sort of thing **before** you start implementing it, or better yet, before you sell the idea to your company ? Weird.

I'll definitely look into the wiki and whatnot... Thanks again.  In regards to do some research before hand, we did.  We utilize RedHat for our FTP servers in our DMZ zones so we never had to struggle with Domain Authentications.  

After the idea came up we looked up Domain Integration and all the documentation that came up for Fedora and Redhat made it seem very straight forward but when the actually time came...well... it wasn't.  

But thanks again for your help guys, and hopefully all goes smooth.  If not, I'll be back   :)

---

### Post by koenn on 2009-01-12
> **pdtpatrick said:**
> You make a valid point koenn  -- but i figured since he already sold the idea to the company then might as well help him instead of asking that question.
I figured that since I've seen quite a bit of these "i'm setting up a server for my company  and now i [urgently] need help doing this or that"-threads I might as well remind people that some research and testing before doing things for real, is not a bad idea.
:)

---

### Post by koenn on 2009-01-12
> **Aysah said:**
> 
After the idea came up we looked up Domain Integration and all the documentation that came up for Fedora and Redhat made it seem very straight forward but when the actually time came...well... it wasn't.  

It's done quite a lot so probably you can pull it of, but in my experience, matching standard protocols such as those usually implemented in open source, with Microsoft's usually not very standard-compliant implementation of those protocols, is always hairy.

Have fun :)

---

### Post by Aysah on 2009-01-12
So to make a long story short... It still doesn't work.  It turns out that all of our DomainControllers do not utilizes Kerberos authentication (so I'm told by my admin).  He said that he made a judgement call and stuck with just using LDAP.  

Being that almost every tutorial I have found online regarding setting this up uses Kerberos in some way or another, im starting to lose the light at the end of the tunnel.

Is there a way to add an Ubuntu Server to a Domain and setup share without using any authentication with Kerberos?

---

### Post by pdtpatrick on 2009-01-12
[http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10](http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10) 

Look for something like the above. 

you should be able to use LDAP to authenticate.

---

### Post by Aysah on 2009-01-14
Frustrating doesn't even begin to describe me at the moment lol...  So I feel like I'm almost there but something is definitely missing.  When I run 'wbinfo -u' or 'wbinfo -g' I get a list of all my ActiveDirectory users and groups which is awesome but I can't use them for whatever reason.

After I run 'sudo chown cmccrum:systems temp' I get an error back saying Invalid User.  So the file server seems to see my active directory users from my domain server but won't let me use them.  Any Ideas?

If needed, I can post configuration files to help get to a solutions..  I'm begging, if anybody knows anything...lol just help a fellow out

---

### Post by koenn on 2009-01-15
try replacing the user and group in "chown cmccrum:systems temp" with full names, like DOMAIN+username;DOMAIN+groupname.
the '+' is a winbind separator, you may have to define that in your smb.conf.

Also, in your smb.conf, your workgroup name and domain name (realm) don't match, which is unusual. This could be the reason the 'use default domain' doesn't work.
The reference to winbind for group in your /etc/nsswitch.conf also looks wrong so you might not really getting the group names.

do
```

	getent passwd
	getent group

```
to see if nsswitch is working and see the user/group accounts in a format that Linux understands

---

