---
title: "Ubuntu servers, Mac clients, Solaris NFS home dirs, tying it all together with LDAP!"
date: 2010-10-28
forum: Server Platforms
---

### Post by samosamo on 2010-10-28
I have been playing with this for the better part of two weeks now. I wanted to know if you guys had any ideas on how to make this work PROPERLY. I've experienced a few challenges so far but I will save them for later because I'm really interested in what you guys have to say.

THE GOAL:
Store users and groups in LDAP
Serve NFS home directories via an OpenSolaris server
Have multiple Linux servers and multiple Mac clients automount these home folders

A little about the environment:
NFS server: OpenSolaris 2009.06 w/ ZFS
LDAP server: Undecided, but considering MacOS X Server w/ OpenDirectory (*see below for more)
- Ubuntu servers (10.04)
- MacOS X 10.6 clients

OpenDirectory:
Just to be clear: OpenDirectory is actually OpenLDAP with some extra schemas to make this a complete solution to manage Mac clients.  I would much rather use this (or any other "complete solution," per your suggestion) than roll my own OpenLDAP server because I do not have enough LDAP experience.

---

### Post by the_original_billq on 2010-10-28
Are you just looking for comments, or are you having a problem?

I guess if I were to comment, it would be, what purpose does OpenSolaris bring to the table?  You can run an NFS server just as well from Linux.  If it's just due to ZFS, [http://packages.ubuntu.com/lucid/otherosfs/zfs-fuse]("http://packages.ubuntu.com/lucid/otherosfs/zfs-fuse") it's there.

You don't really mention hardware at all, or what your Ubuntu servers are going to be doing, so I can't really comment there at all.

Regarding LDAP, there are a number of solutions available.  Typically your choice of naming service is dictated by what features you're looking for, the size of your deployment, and your admin experience.  At home I use NIS because I have less than 20 users, I'm not concerned about internal attacks (well, I'm not so sure about my wife:-)), it provides an easy way to manage my hosts and users all in one spot, and I'm very familiar with how to set it up and use it.  I also have a Samba LDAP service that I push the NIS data to, which makes my Windows users happy.

You also don't mention the size of your deployment.  So no recommendations can be made based on the number of users you're going to support.

Maybe you should consider re-wording your post into a question, and provide additional details to get a bit better response.

-Bill

---

### Post by samosamo on 2010-10-28
Thanks, actually I didn't ask a question yet.  I'm not at that point.  I'm trying to get a conversatiion going so I left my post open-ended to get posts JUST like yours about how other people have this set up.

Kind of off topic but FYI I chose OpenSolaris so I may run ZFS (and NFS for that matter) in the OS for which it was designed.  I am not interested in running an emulation in userspace on a Linux system.  If I had to, I would just use mdadm as I have done in the past.

In my testing I am mostly concerned about how to specify the homeDirectory in LDAP.  For example, OSX seems to like NFS servers mounted at /home (so does Solaris) whereas Linux has /home on the local filesystem and seems to want NFS servers mounted at /net.  How may I specify two different homeDirectory for two OSs?  Probably impossible.

---

### Post by the_original_billq on 2010-10-28
I setup an auto.home map that just contains:

```

*     -vers=3,hard,intr,nosuid,rsize=32768,wsize=32768 nfs-server:/export/home/&

```

Then an auto.master that contains:
```

/home   yp:auto.home -nobrowse

```

You can implement the same thing in LDAP.

---

### Post by samosamo on 2010-10-28
> **the_original_billq said:**
> I setup an auto.home map that just contains:

```

*     -vers=3,hard,intr,nosuid,rsize=32768,wsize=32768 nfs-server:/export/home/&

```

Then an auto.master that contains:
```

/home   yp:auto.home -nobrowse

```

You can implement the same thing in LDAP.

I have definitely considered this and it is the preferred way to go on UNIX (OSX and Solaris) but does not seem to be the Linux way.  An example of how this would be a bad idea would be the local admin's home is at /home and in the event of a network outage or similar event, the local admin would not be able to login and fix the problem.

---

### Post by the_original_billq on 2010-10-29
> **samosamo said:**
> I have definitely considered this and it is the preferred way to go on UNIX (OSX and Solaris) but does not seem to be the Linux way.  An example of how this would be a bad idea would be the local admin's home is at /home and in the event of a network outage or similar event, the local admin would not be able to login and fix the problem.

Your local home can really be anywhere, and can even be under /home.  If automount isn't running, the directory will still be there.

When doing cross-platform integration, you will need to make choices that make sense for the majority of your users.  Most users expect their home to be in /home/user_name, regardless of it being an NFS/automount or local on the machine.  We have a very large RedHat deployment for servers, Ubuntu workstations, and are migrating off of a legacy Solaris environment.  We enable root on Ubuntu, and use /root as root's home dir across all three platforms.  I can't really talk about how we secure everything, but I think that's beyond the scope, here.  The point I'm trying to make is this - just because it's the native way of doing something doesn't mean it can't be tweaked or changed when it makes sense to do so from a management or use perspective.

-Bill

---

### Post by samosamo on 2010-10-29
> **the_original_billq said:**
> Your local home can really be anywhere, and can even be under /home.  If automount isn't running, the directory will still be there.

When doing cross-platform integration, you will need to make choices that make sense for the majority of your users.  Most users expect their home to be in /home/user_name, regardless of it being an NFS/automount or local on the machine.  We have a very large RedHat deployment for servers, Ubuntu workstations, and are migrating off of a legacy Solaris environment.  We enable root on Ubuntu, and use /root as root's home dir across all three platforms.  I can't really talk about how we secure everything, but I think that's beyond the scope, here.  The point I'm trying to make is this - just because it's the native way of doing something doesn't mean it can't be tweaked or changed when it makes sense to do so from a management or use perspective.

-Bill

Using root is a great idea to fix that problem.  Don't kill me for saying this though, but it's not ideal since enabling root is not the "Ubuntu" way ;)

I have good news though, it seems that across all three platforms automounting NFS servers at /net is working well.  Solaris and OSX work natively, while Ubuntu just needs autofs installed with just defaults.  I then make the LDAP homeDirectory /net/nfsserver/home/username.  It is working!  I'm wondering if it is normal to see that your home is actually mounted at /net?

The only challenge I'm having using /net for homes is one for the OSX forums but I'll write it here too.  OSX users set for "Mobile Accounts" in OpenDirectory (laptop users, basically) don't get their files synced back to the server when home is mounted at /net.  I only got it working for /Network/Servers which is the GUI way for mounting NFS.  I'll post on an Apple forum and see if I can fix that.

---

### Post by samosamo on 2010-10-29
This guy makes interesting use of symbolic links on each client to make it work.  Its worth taking a look at: [http://macdevcenter.com/pub/a/mac/2007/06/27/discover-the-power-of-open-directory-part-2.html?page=3](http://macdevcenter.com/pub/a/mac/2007/06/27/discover-the-power-of-open-directory-part-2.html?page=3)

---

