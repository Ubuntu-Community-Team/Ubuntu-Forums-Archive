---
title: "remote /home for users across clients with differing versions of Ubuntu"
date: 2013-06-07
forum: Server Platforms
---

### Post by BandD on 2013-06-07
I am in the process of setting up an Ubuntu server that will act as a file server/SSO/DNS/etc. for a small business with 3 client machines (more coming in the near future) and about 6 regular users.  I'm planning on setting up LDAP, Kerberos, and NFS to accomplish this. 

The clients are running 12.04.2 and 13.04 (with one OSX machine).  The 12.04 machine can't run 13.04 because the graphics driver is broken for that particular graphics card and the 13.04 machine can't run 12.04 for a similar reason.  So I am stuck with 2 clients that are running differing versions of Ubuntu.

I'd like to create a Single Sign On type of environment so no matter which client someone logs into, they can access all of thier files, firefox bookmarks, thunderbird contacts, etc.

Will having each user's /home on the server be affected by the differing versions of Ubuntu on each client machine?  

If so, how can I make a guide similar to [this]("http://www.danbishop.org/2012/06/02/ubuntu-12-04-ultimate-server-guide/3/#autofs-ldap") work across clients using various versions of Ubuntu? 

Thanks.

---

### Post by newbie-user on 2013-06-11
I recently did this while transitioning from 10.04 to 12.04. Just point the client computers to the server for /home. The only problem is for the individual applications, when they might have different configurations for different versions. I didn't have any problems with user files or firefox bookmarks. Don't know about thunderbird, though.

---

### Post by SeijiSensei on 2013-06-11
I've used the same partition for /home across multiple Ubuntu releases.  While there may be some configuration differences between, say, desktop environments (in my case, the contents of ~/.kde), the application software usually knows how to handle this situation.  As for Thunderbird, I use IMAP so all my folders and the like are stored on the mail server.  My contacts and so forth are in ~/.thunderbird and have persisted across version upgrades.

BandD, the best advice I can give you is to test this out by migrating a single client machine to an NFS-mounted /home and see what goes wrong, if anything.  Back up the original contents of /home before you switch, though mounting the NFS share over the existing /home should not affect the contents of the original directory.

---

### Post by BandD on 2013-06-13
Thank you both for you answers.  I'm greatly encouarged and will give it a go.  I'll report back once I do.

Thanks again for sharing your experiences.

---

