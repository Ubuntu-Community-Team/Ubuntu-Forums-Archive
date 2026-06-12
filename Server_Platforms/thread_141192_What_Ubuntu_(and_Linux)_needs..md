---
title: "What Ubuntu (and Linux) needs."
date: 2006-03-07
forum: Server Platforms
---

### Post by Soleil-Raid on 2006-03-07
I was recently comparing my experiences with a fellow sys-admin. We both work in small (around ten people) IT-centered companies. I work in a predominately Linux company, and he has mostly Windows servers, and although both of us have servers in the other camp, they are mostly for testing purposes, rather than day to day usage. Both of us spend most of our time coding, rather than sys-admin work.

It turns out the difference seems to be that things on the Microsoft side of the border are easier to setup, but my counter-part spends most his 'sys-admin time' doing triage work, while I spend way too long trying to get things up and running - but can generally expect them to run without help once they're working. 

An excellent example of this was during the construction of the general infrastructure to handle centralized users. He deployed Active Directory. I spent six months slowly building up the proper setup for Kerberos, LDAP, DNS, DHCP, and all the other components that are essentially Active Directory - right down to the protocols. Lets for the sake of argument call this setup under Linux the L-OD, the 'Linux Open Directory' (yeah, I know Apple already has something by a similar name).

As it turns out, MS-AD and L-OD are essentially the same thing, except that MS mangles the Kerberos protocol by stuffing LDAP inside it (no joke), and uses SMB rather than NFS for file sharing. The big difference is, L-OD is a royal PITA to set up, and lacks many of the extra things that make MS-AD nice to use. No, really.

Linux actually has most of the tools to replicate MS-AD functionality, the problem is that they're often obscure, badly documented, and generally not very good at talking to each other.

For example, I recently wanted to automatically add users to the local console groups on log in through gdm on DISPLAY=:0. Turns out that this functionality is accomplished through the use of the pam module groups, that uses the local file /etc/security/group.conf.

This works quite well, but it requires me to push the altered file out to all the machines on the network, which means I have to either use root, or sudo in on every computer. Logically, this is information that could be held on LDAP. Perhaps users that are/aren't in a particular group can't log into workstations locally. This would make things much easier from a administrative point of view.

I digress - the main point of difference seems to be between adding users and machines to the network, and configuration of failover.

Adding machines;
MS-AD; Run "Add machine to Domain wizard."
L-OD; Add machine info to dhcpd.conf, bind, restart dhcpd and bind. Also for Windows machines, Manually create machine entry, and import to  LDAP. Run smbpasswd -m. Run "Add machine to Domain wizard on client." Create the Kerberos entry for the machine, and any services that need their own entry, and push them out the keytab on the machine. Push out local cert-authority certificates. Push out the Kerberos realm file (use DNS), and the two-dozen changed files for PAM and GNOME.

Adding Users;
MS-AD; Run "Add user to Domain wizard."
L-OD; Add user to /home/ and /projects/ and chmod them on file server, Manually create user and groups entries, and import to LDAP. Create user in Kerberos.

Well that's not so hard is it? I can script a lot of that right?

What about if I need to get trained monkeys (like say; in a large company) to do this? And can we do this without invoking root at every opportunity?

Also; Now, just to make it even more fun. I've had to work most of this out from scratch. Documentation is sorely lacking, and where it does exist, seems to often proscribe some practices that are at-best niave ("I'll only ever have machines I've set up"), and at worst flat-out insecure (storing passwords in LDAP is just wrong), and don't account for the reality of large networks, where not everyone is the same, and there's multiple administrators of varying parts of the network.

By way of example - the engineering and artistic pool will need their own local server for their multi-gigabyte files, the programmers will probably want local root, and the admin staff are probably going to have to reset passwords accounts in their area a lot, but in no way should have root access otherwise.

This is all possible to do, but it's just such a complete pain under Linux without massive amounts of bug-prone scripting, that I'm left wondering if it's worth the bother. Worse yet, I can't help feeling that other people have already written the same scripts somewhere else. I still haven't managed to get NFSv4 working yet, and my DHCP and LDAP failover seem to be a little buggy. 

---

What I'm getting at here is that we've had all the tools for some time now, but the enterprise quality management and - dare I say it - integration - just doesn't seem to be there. It shouldn't take a genius to add a couple of new users or machines to the network. Worse yet, there's no standardization between faculties. An experienced sys-admin shifting from one company to another is going to feel like they have to learn a bunch of tools all over again, all with their own quirks.

This seems like the sort of project Ubuntu could get it's teeth into, and clean up the market.

Am I the only one who feels this way?

---

### Post by colo on 2006-03-07
Afaik, Samba4 will include an AD-drop-in-replacement of some sort.
And there's some soon-to-be-released, colorful directory service in the pipe over at Novell (or was it Red Hat?), if my mind does not play tricks on me right now.

---

### Post by az on 2006-03-07
[QUOTE=Soleil-Raid]
This seems like the sort of project Ubuntu could get it's teeth into, and clean up the market.

Am I the only one who feels this way?[/QUOTE]

Dapper will have a formal server release.  I would expect more people contribute to the server BOF's at the next Ubuntu summit.  That's where goals for the next release are set.

---

### Post by LordHunter317 on 2006-03-07
> **Soleil-Raid]An excellent example of this was during the construction of the general infrastructure to handle centralized users. He deployed Active Directory. I spent six months slowly building up the proper setup for Kerberos, LDAP, DNS, DHCP, and all the other components that are essentially Active Directory - right down to the protocols.[/quote]Active Directory goes   substantially beyond that.  You're ignoring the centralized *computer* management capabilites, which are arguably more important the user ones.


> MS mangles the Kerberos protocol by stuffing LDAP inside it (no joke),No, they don't.  They if anything, did the other, and not really then.

What they did do was use an LDAP schema and some legal K5 extensions that tie Active Directory very strongly to the NT security model.

> This works quite well, but it requires me to push the altered file out to all the machines on the network, which means I have to either use root, or sudo in on every computer.Or, far better, a tool that does this for you, like cfengine.

> L-OD said:**
> Or you could use DDNS, like Windows does.  This however, does require some configuration off the bat.  Blame ISC. :mad:

[quote]Also for Windows machines, Manually create machine entry, and import to  LDAP. Run smbpasswd -m.You don't need to do either, it's possible to configure Samba to automate both tasks.

[quote]What about if I need to get trained monkeys (like say; in a large company) to do this?You only have to write the scripts once, which is your only consolance.

> and at worst flat-out insecure (storing passwords in LDAP is just wrong),No more wrong than storing them in the shadow file.

> I still haven't managed to get NFSv4 working yet,Don't.  Just give in and use Samba.  Linux's NFSv4 implementation is still very immature anyway (read: more useless than v3 and v2).

> What I'm getting at here is that we've had all the tools for some time now, but the enterprise quality management and - dare I say it - integration - just doesn't seem to be there.Welcome to UNIX.  And people wonder why MS has such a huge server following.

---

### Post by Soleil-Raid on 2006-03-07
[QUOTE=LordHunter317]Active Directory goes   substantially beyond that.  You're ignoring the centralized *computer* management capabilites, which are arguably more important the user ones.[/QUOTE]

Which is what I'm getting at -  it might not seem that way, but that's what I'm thinking at any rate. 

> 
No, they don't.  They if anything, did the other, and not really then.

What they did do was use an LDAP schema and some legal K5 extensions that tie Active Directory very strongly to the NT security model.


My understanding is that Samba can't do Kerberos authentication using MIT Kerberos and OpenLDAP, without getting a Windows box to do the intermediatry bit, which seems to be missing the point of having Samba and Kerberos.

> 
Or you could use DDNS, like Windows does.  This however, does require some configuration off the bat.  Blame ISC. :mad:

You don't need to do either, it's possible to configure Samba to automate both tasks.

You only have to write the scripts once, which is your only consolance.


Well, this is the thing, I'd like to be able to run a single interface, tell it to add a machine permanantly, and specify if it's simply a host (such as a users laptop or PDA), or SMB/AD enabled, or Unix/L-OD enabled, and get something else to do the boring stuff for me, which is what I thought computers were supposed to do.

> 
No more wrong than storing them in the shadow file.

Except that a shadow file doesn't travel across the network. (Unless you export /etc/, use NIS, or some other practice where you believe that your physical network is secure.) but in any case, Kerberos provides single-sign on, and is good at being a properly secure authentication protocol because that's what it was designed to be, and provides support for stuff like smart cards. LDAP is designed to be a directory server, and it's good at that.

> 
Don't.  Just give in and use Samba.  Linux's NFSv4 implementation is still very immature anyway (read: more useless than v3 and v2).

Can't. Samba doesn't support symlinks and hard links. These are a flat out requirement here (alternative is copying multiple gigabytes of files round for every time a developer runs a test in a project), nor does smb on Linux seem to support ACLs (the other reason I really want NFSv4).

> 
Welcome to UNIX.  And people wonder why MS has such a huge server following.

My thoughts exactly.

---

### Post by LordHunter317 on 2006-03-07
[QUOTE=Soleil-Raid]Which is what I'm getting at -  it might not seem that way, but that's what I'm thinking at any rate.[/quote]Well, yes, I realized that as I finished it.  You'll have to forgive me for being slow, I'm in the pre-spring break crunch.

> My understanding is that Samba can't do Kerberos authentication using MIT Kerberos and OpenLDAP,You can authenticate against a Windows AD server without Samba in the picture, if you're trying to suggest that's impossible.

What you cannot do is *authorize*, but that's as much of a failing of the standard writers.

If you mean, serve AD, then no, it can't.  The K5 implementation is extended (in legal ways, but extended nonetheless) and the LDAP stuff is a bit funky.  My understanding is it could conceptually be done with OpenLDAP but it's far eaiser not to.

> Except that a shadow file doesn't travel across the network.Yeah, but if your machine has network access... and you see the point, I think.

> but in any case, Kerberos provides single-sign on, and is good at being a properly secure authentication protocol because that's what it was designed to be, and provides support for stuff like smart cards. LDAP is designed to be a directory server, and it's good at that.That doesn't exclude storing password hases in the directory server, *per se*.  It's not like Kerberos fully solves the storage problem either, though it probably does it better than any solution you could come up with trivially.

> Can't. Samba doesn't support symlinks and hard links.Well, you can't create them, yes.

> nor does smb on Linux seem to support ACLs (the other reason I really want NFSv4).Yes, it does, and does well.  It takes some trickery to setup though, and things aren't fully transparent for Windows users, but it's better than nothing.

---

### Post by Soleil-Raid on 2006-03-08
[QUOTE=LordHunter317]Well, yes, I realized that as I finished it.  You'll have to forgive me for being slow, I'm in the pre-spring break crunch.

You can authenticate against a Windows AD server without Samba in the picture, if you're trying to suggest that's impossible.

What you cannot do is *authorize*, but that's as much of a failing of the standard writers.

If you mean, serve AD, then no, it can't.  The K5 implementation is extended (in legal ways, but extended nonetheless) and the LDAP stuff is a bit funky.  My understanding is it could conceptually be done with OpenLDAP but it's far eaiser not to.

Yeah, but if your machine has network access... and you see the point, I think.

That doesn't exclude storing password hases in the directory server, *per se*.  It's not like Kerberos fully solves the storage problem either, though it probably does it better than any solution you could come up with trivially.
[/QUOTE]
True. The problem I have is that I can't just point a samba server at generic LDAP and Kerberos servers and say "Make it happen." Regardless of whose fault it is, it's still really annoying. Getting a bit off topic though.


> Yes, it does, and does well.  It takes some trickery to setup though, and things aren't fully transparent for Windows users, but it's better than nothing.

Argh, not being clear. The existing working relationship does not seem to support setting and reading ACLs from a samba server when mounting on a Linux box. Which is a PITA. It does work here on  Win2K3 accessing a samba/breezy server though.

Anyhoo - What I'm trying to get at is that I'd really like to be able to quickly deploy generic work group servers, and then easily add a backup server for one or more protocols - preferably all of them, without all this faffing about that I currently have to do.

I call it faffing, because judging from what I've read in my google searchs, I'm repeating the same learning curve to implement the same thing as a whole bunch of other people, in pretty much the same way. Perhaps it's because I'm a programmer on the side, but I really dislike doing the same thing that's already done before. I can't help feeling that this shouldn't be that hard to do.

While I'm on the subject, It would be nice to have a decent networked file system. Eg; One with intergrated Kerberos support, encryption, ACLs, Linux, Mac and Windows support, preferably client side caching, and automatic fallover. Oh, and a pony. ;)

Actually, I think this does exist in the form of AFS. Too bad it's got a 2 GB file size limit.

---

### Post by Glut on 2006-03-08
> 
What you cannot do is authorize, but that's as much of a failing of the standard writers.
You can authorize using AD LDAP, if you insert your own LDAP entries at account creation. This makes maintenance a bitch, but hey it's possible.

---

