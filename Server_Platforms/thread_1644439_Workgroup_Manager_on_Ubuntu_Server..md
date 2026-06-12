---
title: "Workgroup Manager on Ubuntu Server."
date: 2010-12-13
forum: Server Platforms
---

### Post by anotherli on 2010-12-13
I've googled, found guides and used them but none of them work.

I'm trying to set up a Ubuntu Server 10.10 so that I can manage users/groups with Workgroup Manager. And I could really use some help.
As far as I can tell I need to install OpenLDAP to make it work, right?
I want the configuration to be flexible enough so that I can use both Mac and Win clients.
I have no idea where to start...

Got Ubuntu Server installed on a MacBook.
Using another MacBook as a client.
I'm not that great with Ubuntu. Got some experience with the terminal and I want to use it as well. Don't want a GUI on the server.

Ask away if you need to know anything else.

---

### Post by anotherli on 2010-12-13
Actually it doesn't have to be Ubuntu Server. Could be any other Linux distribution and it doesn't have to be pure terminal. As long as it works in the end 's all good.

---

### Post by anotherli on 2010-12-13
So far I have managed to install netatalk and avahi on the server. So it shows up in the finder on the mac client.
This worked perfectly at first (last week) but now I get an "you entered an invalid username or password"-error if I try to connect to the server via finder but I can ssh without any problems.

Not sure if this is even relevant but can't hurt.

---

### Post by anotherli on 2010-12-22
Sad bump :(

---

### Post by anotherli on 2010-12-22
[http://blog.michael.kuron-germany.de/2009/04/building-your-own-opendirectory-server-on-linux/](http://blog.michael.kuron-germany.de/2009/04/building-your-own-opendirectory-server-on-linux/)

This looks really promising. Unfortunately it's too advanced for me.
For example:
"Copy this file to your OpenLDAP server and add it to your slapd.conf."
I do not know how to do that and the guide is very "shallow". It probably tells you what you need to do but since I'm pretty new to Linux I have no way to "translate" it.

---

### Post by anotherli on 2011-01-03
Think I almost got it. Installed LDAP, netatalk, smb and got it to "work". At least not spewing error messages.

Now I'm trying to actually connect Workgroup Manager to the server. I type in IP, username and password but get the error message:
"The address you entered is not reachable. Please check your network connection"

I'm pretty sure that I can reach it since I'm currently logged in via ssh to the server. Anyone know what could be causing this?

Browsing servers in Workgroup Manager shows me a couple servers at work. Why is mine not showing up? Could I announce it with avahi maybe?

Help really appreciated :)

---

### Post by samosamo on 2011-01-04
I recognize what you are trying to do.  While possible only in theory, it is beyond the scope of this support forum to deploy a complete MacOS workgroup solution using Linux. It's beyond the scope of any forum on the entire internet. Save yourself the trouble and install MacOS X Server.

---

### Post by anotherli on 2011-01-04
> **samosamo said:**
> I recognize what you are trying to do.  While possible only in theory, it is beyond the scope of this support forum to deploy a complete MacOS workgroup solution using Linux. It's beyond the scope of any forum on the entire internet. Save yourself the trouble and install MacOS X Server.

Really? :(
I thought that as long as I get a solid Open Directory running everything would work peachy with Workgroup Manager.

---

### Post by samosamo on 2011-01-04
> **anotherli said:**
> Really? :(
I thought that as long as I get a solid Open Directory running everything would work peachy with Workgroup Manager.

I'm speaking from experience.  Save yourself the headache and use MacOS X Server for what it is designed to do.  Is there a reason you choose to do it the hard way?  It seems you have Apple hardware available to you so you should be able to do it.

---

### Post by samosamo on 2011-01-04
> **kevinthecomputerguy said:**
> Anotherli, please ignore samosamo, he has no idea what he is talking about.
 
He should stop offering file share advice when he has no idea what he is talking about.

Did you seriously just follow me into this thread?

---

### Post by kevinthecomputerguy on 2011-01-04
Just commenting on bad advise that i find, not my fault your name keeps coming up.

---

### Post by samosamo on 2011-01-04
You're commenting on bad fileshare advice, in an LDAP thread?  Sure...

---

### Post by anotherli on 2011-01-05
> **samosamo said:**
> I'm speaking from experience.  Save yourself the headache and use MacOS X Server for what it is designed to do.  Is there a reason you choose to do it the hard way?  It seems you have Apple hardware available to you so you should be able to do it.

It's kind of a school/work project. With Apple discontinuing Xserve I want to create an alternative.
Why? Because you're not allowed to run MacOS X Server on non-Apple hardware and the only Apple hardware to run it on will be Mac Pros and Minis and that's not really an alternative to 1U racks. They're too big and clumsy.
There are rumors that Mac Server will be permitted to be virtualized but still only rumors and even if it's true it would be nice to be able to pull this off. Cheaper and what-not.

---

### Post by samosamo on 2011-01-05
> **anotherli said:**
> It's kind of a school/work project. With Apple discontinuing Xserve I want to create an alternative.
Why? Because you're not allowed to run MacOS X Server on non-Apple hardware and the only Apple hardware to run it on will be Mac Pros and Minis and that's not really an alternative to 1U racks. They're too big and clumsy.
There are rumors that Mac Server will be permitted to be virtualized but still only rumors and even if it's true it would be nice to be able to pull this off. Cheaper and what-not.

Yeah I heard about that. Damn shame what Apple has done. No regard for enterprise Mac users and their IT staff. I do some work for a Mac shop too.  We have ~50 Xserves in production, some of which run software that only runs on MacOS X Server and nothing else.  No idea what we will do.

Well, I underestimated what you were trying to do at first. Sorry about that. That doesn't change that what you're trying to do is a huge pain in the ***.  I can't offer any advice on getting it to work.  I can just say that personally, BEFORE I go through all the headache, I'm waiting for Apple to either confirm that MacOS X Server is or isn't dead and if it is, to present us with an alternative solution for managing Mac users, groups, and computers.

---

### Post by samosamo on 2011-01-05
I just noticed your post from 2 weeks ago where you had trouble loading the apple.schema.  Have you figured that out yet?  That a very important step and could lead to WGM failing to connect to the server.

---

### Post by m00dawg on 2011-01-05
I have been able to get LDAP authentication working so users can login to OS X from OpenLDAP. The problem I am currently having is that the /home directory mapping is not working. A local /home/<user> is created but without the UID/GID of the user - hence that user cannot write to their home-dir.

I too have seen the either outdated or sparse articles on populating the Apple schema. I was able to create an LDIF by doing:

```

root@domainator:/home/tim# cat schema_convert.conf 
include /etc/ldap/schema/core.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/nis.schema
include samba.schema
include apple_auxillary.schema
include apple.schema

slapcat -f schema_convert.conf -F ldif_output -n0

```

Trouble is that the results are for cn=config and I was not able to actually import that using:

```

root@domainator:/home/tim# ldapadd -Y EXTERNAL -H ldapi:/// -f ldif_output/cn\=config.ldif 
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=config"
ldap_add: Constraint violation (19)
	additional info: structuralObjectClass: no user modification allowed

```

That's not a permissions issue, I don't think, because if I can do this:

```

root@domainator:/home/tim# ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=nis,cn=schema,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
	additional info: olcAttributeTypes: Duplicate attributeType: "1.3.6.1.1.1.1.2"

```

I assume that, once I get the schema in there, that I can then using LDAP Account Manager (web-app) or something else to add fields to the users as needed to get to the next step (which is NFS automounting).

OS X Server might be ok though my boss wants to simplify things and try to have a single machine that is the authentication source for both Windows and OS X. If OS X Server can do that easily we might have an option though I too am really bummed about the loss of X-Serve. Plus, I dunno about Workgroup Manager working with OpenLDAP, but apart from that if the only thing keeping network directories from working is the damn Apple schema, that problems does not seem insurmountable.

I may have to do that for Samba as well (since it may need a different path for home directories)...good times. I can only imagine how complicated x.500 is. That must be a different but very real kind of hell.

---

### Post by m00dawg on 2011-01-05
I dunno how helpful this is, but this Apple class mentions setting up stuff using LDAP:

[http://training.apple.com/itpro/snow301](http://training.apple.com/itpro/snow301)

"...In working with Mac OS X, students learn how to use network accounts and Kerberos authentication with any common directory service, such as Apple's Open Directory, Microsoft's Active Directory, or an industry-standard LDAP server."

So, this makes me think that, yes, indeed, it can be made to work and someone over at Apple knows how to do it.

---

### Post by m00dawg on 2011-01-05
Well, it turns out I'm just stupid.

The reason my home directory was not writable was because it already existed from a previous test setup. Now that I figured that out, in my case, OpenLDAP does all I need it to without having to use any of the Apple extensions.

I'm not even sure what value they actually add if all I am trying to do is authenticate using LDAP. Perhaps for getting Kerberos to work but even that seems like it can be done with a standard OpenLDAP solution.

Sadly, the problem of Workgroup Manager not working for me is still true but using LDAP Account Manager (LAM) works for me at least for now.

That doesn't solve the original problem in this thread, but wanted to round out my chapter within it :)

Good luck! If you do get Workgroup Manager working, that'd be pretty hot!

---

### Post by anotherli on 2011-01-19
Looks like I'll be scrapping the project. Not much left of my internship.
But since I'm still a bit interested.
May be badly formulated - but what does Workgroup Manager "need"? 
If you can get other ldap-based programs to work why not Workgroup Manager? What makes it different?

---

### Post by m00dawg on 2011-01-19
Workgroup Manager offers tight integration with OS X. Think of it like the front-end for OS X's Open Directory. Open Directory itself is like Active Directory for OS X. So it has a number of extensions over a standard LDAP solution, which is also why it is fairly difficult to setup outside of OS X Server.

Basic authentication, network home dirs, etc. can all be done with OpenLDAP with little to no modification of the base schemas.

---

### Post by Mogga on 2011-06-27
I believe the core problem you're having is authenticating to openldap with WGM. It's my understanding that it relies on Password Server to authenticate as opposed to an admin DN. Hence the reason why you can connect to OD with a username and password instead of a DN.

If you look at an OD server you'll see an additional flag in the kerberos kdc config file  ( /var/db/krb5kdc/kdc.conf )

pws_enabled = yes

This flag is not documented in any kerberos docs I've found. It's apple specific. It might be possible using sasl proxies.

Here's a few URLs to help the search if you haven't figured this out yet:

[http://blog.michael.kuron-germany.de/2009/04/building-your-own-opendirectory-server-on-linux/](http://blog.michael.kuron-germany.de/2009/04/building-your-own-opendirectory-server-on-linux/)
[http://deepport.net/archives/setting-up-a-linux-server-for-os-x-clients/](http://deepport.net/archives/setting-up-a-linux-server-for-os-x-clients/)
[http://hermanbanken.nl/2011/01/22/openldap-server-mac-osx-clients/](http://hermanbanken.nl/2011/01/22/openldap-server-mac-osx-clients/)
[http://www.stanford.edu/group/macosxsig/blog/2008/02/samba_openldap_kerberos_afp_le_1.html](http://www.stanford.edu/group/macosxsig/blog/2008/02/samba_openldap_kerberos_afp_le_1.html)

Please report back if you figure this out. It's been a side project for me as well for the last 6 months or so every now and then. It's not essential but it'd be 'nice'.

---

