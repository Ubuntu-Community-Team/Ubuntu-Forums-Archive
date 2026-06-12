---
title: "Zimbra replacement - Ubuntu 12.04.5 LTS"
date: 2015-06-23
forum: Server Platforms
---

### Post by mcparty2 on 2015-06-23
Hi Folks,

I am looking to remove Zimbra (version 8.5.0_GA_3042.FOSS) from my server and replace it with a much simpler front end like Roundcube, or Rainloop.
The Zimbra installation is using the postfix MTA and nginx.

Has anyone undertaken such a a project and able to offer advice? I have a few users who would rather not loose their emails :) The Zimbra Community wiki doesn't appear to be of assistance in these matters.

Best wishes,

---

### Post by TheFu on 2015-06-24
Ive never done this. Too addicted to enterprise calendaring myself, but Zimbra definitely is a hog - especially the 8.x releases.

If I were trying this, I'd use an imap backup/restore technique.  It would be nice if the built-in zimbra expert methods worked, but I wouldn't believe it would as a method to transfer to a different system.

The easiest way would be to setup both systems and have the users transfer through drag-n-drop after making the imap connections to both.  Of course, the user community would need to be sophisticated enough to handle that.

---

### Post by volkswagner on 2015-06-25
There are free tools out there for server to server IMAP migration.

I have had great results using [IMAPtools]("http://www.athensfbc.com/imap_tools/"). Rick is well deserving of his asking price for the toolset. He is very responsive with support.

---

### Post by mcparty2 on 2015-06-25
Thanks for the advice. The caveat is, I need to remove Zimbra and install it's replacement on the same server. 
So, I suppose I should locally locate and back up all mailboxes. remove zimbra, install replacement import mail... it seems too simple, I am sure there will be a few hair pulling moments.

---

### Post by volkswagner on 2015-06-25
Does the server have enough resources to install KVM and create a virtual machine for new mail server?

---

### Post by TheFu on 2015-06-25
The imap transfer tools need both IMAP servers to be running concurrently - IME.  I don't think you can run Zimbra's IMAP server parts without the rest of it running too.

But I haven't tried.

How many users and how much storage are we talking about?

---

### Post by mcparty2 on 2015-06-25
> Does the server have enough resources to install KVM and create a virtual machine for new mail server?

Sadly not, no virtualisation support :( I like your thinking though, I’m sure there must be a simpler way.


> How many users and how much storage are we talking about?

I have 3 domains with about 5 users on each... So 15 mailboxes. Less than 10G of data

---

### Post by TheFu on 2015-06-25
This is trivial. You can create an LXC container, load up postfix/dovecot into that "container" with a new IP, then manually migrate the IMAP data over for each user 1 at a time.  No need for a tool. That would be overkill for this.  Just connect a client to both systems and drag-n-drop over.

LXC requires a 3.x kernel and some minor grub/cgroup stuff setup which doesn't impact anything else. 
   [http://blog.jdpfu.com/2014/10/21/fast-and-easy-lxc-deployment-for-development](http://blog.jdpfu.com/2014/10/21/fast-and-easy-lxc-deployment-for-development) is how I did the lxc stuff.

---

