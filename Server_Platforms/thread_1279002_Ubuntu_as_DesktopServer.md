---
title: "Ubuntu as Desktop/Server"
date: 2009-09-30
forum: Server Platforms
---

### Post by fenrisW0lf on 2009-09-30
Hi all,

I have been using Ubuntu since August (of this year) and I really love it as a desktop. I have found no compelling reasons to switch back to windows.

Anyhow, I have a NetBSD server (personal use only) that I have currently running. It is running headless and is used to strictly share host my mercurial repositories and dokuwiki. On occasion it acts as an ftp server. All of these features are used strictly by me. I have been using NetBSD since August of 2005 so it made the transition to Linux easier. 

Since the server is only used by me to sync files and repositories between my personal laptops and other computers I was thinking of moving that functionality over to my Ubuntu box.

My question is, is this a good idea having my desktop (primary use machine) act as a server? Are there any special situations that I should be aware of?

Normally, I keep servers and desktops on their own boxes. However in this case combining the server and my desktop into one computer would be advantageous in both power savings and space savings (I am losing my home office to my son as the new baby will be taking over his room :)).

I plan on running the following services:
- Apache - over ssl
    -Dokuwiki
    -mercurial repositories
- cron scripts that interact with internet based machines

The above services would replace everything that my NetBSD box is currently doing. In addition to those services I would like a way to be able to stream music, share photos and tunnel http connections (over ssh) through this box as well.

Will this work OK? Or should I just keep my NetBSD box? My biggest concern is protecting the box from intruders. Currently my SSH service into the NetBSD box is on a non-standard port and uses a 64 character password. I am planning on implementing a key based system to access ssh. I haven't had any problems (knock on wood!) so far.

How would I keep my server configuration files separate from my desktop? I can keep the server data files on a separate partition or hard disk. But I am unsure how the configuration files would be separated.

---

### Post by Krijk on 2009-09-30
> **fenrisW0lf said:**
> Hi all,

I have been using Ubuntu since August (of this year) and I really love it as a desktop. I have found no compelling reasons to switch back to windows.

Anyhow, I have a NetBSD server (personal use only) that I have currently running. It is running headless and is used to strictly share host my mercurial repositories and dokuwiki. On occasion it acts as an ftp server. All of these features are used strictly by me. I have been using NetBSD since August of 2005 so it made the transition to Linux easier. 

Since the server is only used by me to sync files and repositories between my personal laptops and other computers I was thinking of moving that functionality over to my Ubuntu box.

My question is, is this a good idea having my desktop (primary use machine) act as a server? Are there any special situations that I should be aware of?

Normally, I keep servers and desktops on their own boxes. However in this case combining the server and my desktop into one computer would be advantageous in both power savings and space savings (I am losing my home office to my son as the new baby will be taking over his room :)).

I plan on running the following services:
- Apache - over ssl
    -Dokuwiki
    -mercurial repositories
- cron scripts that interact with internet based machines

The above services would replace everything that my NetBSD box is currently doing. In addition to those services I would like a way to be able to stream music, share photos and tunnel http connections (over ssh) through this box as well.

Will this work OK? Or should I just keep my NetBSD box? My biggest concern is protecting the box from intruders. Currently my SSH service into the NetBSD box is on a non-standard port and uses a 64 character password. I am planning on implementing a key based system to access ssh. I haven't had any problems (knock on wood!) so far.

How would I keep my server configuration files separate from my desktop? I can keep the server data files on a separate partition or hard disk. But I am unsure how the configuration files would be separated.

If you want to keep everything seperated you can use VMware-server on Ubuntu. I use it a lot and a NetBSD-server won't use many resources.

---

### Post by fenrisW0lf on 2009-09-30
A vmware server is a good idea, but I don't think I need to separate them out that much ;)

I would like to make my desktop more usable when I am on the road or away from home. The NetBSD server handles my mercurial repositories which I can sync with my laptop over a secure ssl connection and my documents and programming are available and always in sync. I would like to consolidate that functionality into my Ubuntu desktop. 

I was wondering if there are draw backs to having server software on a machine that is used as a desktop when I am at home?

Cheers,
Troy

---

### Post by nandemonai on 2009-09-30
> **fenrisW0lf said:**
> A vmware server is a good idea, but I don't think I need to separate them out that much ;)

I would like to make my desktop more usable when I am on the road or away from home. The NetBSD server handles my mercurial repositories which I can sync with my laptop over a secure ssl connection and my documents and programming are available and always in sync. I would like to consolidate that functionality into my Ubuntu desktop. 

I was wondering if there are draw backs to having server software on a machine that is used as a desktop when I am at home?

Cheers,
Troy

The only real downside is this:

1. No server kernel
2. Additional overhead of running desktop software

:)

---

### Post by undecim on 2009-09-30
I don't see any problem with this. When I had arch on my desktop computer, I ran it as both a desktop and a server (mostly configured as a server, as far as optimizations, etc.)

If you are only using it for when you are at another computer, you usually won't have much overhead from other apps. I think you should go for it. The space and power savings will definitely be worth it.

---

### Post by fenrisW0lf on 2009-10-01
Thanks all, I suspected that it wouldn't hurt to use my desktop as a server based on my usage patterns. If in the future the work load goes up I'll invest in a proper server.

---

