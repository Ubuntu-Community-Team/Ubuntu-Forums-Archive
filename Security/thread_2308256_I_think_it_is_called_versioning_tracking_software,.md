---
title: "I think it is called versioning tracking software, software that audits /etc... or ot"
date: 2016-01-01
forum: Security
---

### Post by Elishasmantle on 2016-01-01
Hello,

There is a platform used for auditing changes made to system files. 

It was a type of auditing software.

Can someone tell me of a type of software for Ubuntu that does this?

Currently, I am using a documents with files or directories  modify /etc/hosts , resolv.conf smb.conf , etc... to track and recall my changes but it gets hard to always document changes and is cumbersome.

A auditing solution would be much easier to track and revert changes if needed.

Thank You,

elishasmantle

---

### Post by coldraven on 2016-01-01
> It was a type of auditing software.
I don't know the answer to that question but I suppose you could use LVM to take snaphots of your root partition. 
I've never used it so maybe start another thread on that subject.
[http://www.howtogeek.com/211937/how-to-use-lvm-on-ubuntu-for-easy-partition-resizing-and-snapshots/?PageSpeed=noscript](http://www.howtogeek.com/211937/how-to-use-lvm-on-ubuntu-for-easy-partition-resizing-and-snapshots/?PageSpeed=noscript)

---

### Post by 1clue on 2016-01-01
You could set up a git repository for /etc, but I would recommend a private repo rather than github.

Another option would be tripwire or similar.

---

### Post by bashiergui on 2016-01-02
> **1clue said:**
> Another option would be tripwire or similar.
What the OP is describing sounds exactly like tripwire to me.

---

### Post by 1clue on 2016-01-02
Yes, tripwire or similar is what people typically use for this, but the OP referenced version tracking software and finding out what was changed and how, tripwire doesn't do that.

@op:  

Tripwire is an intrusion detector and cleanup aid. It takes a lot of effort to use correctly, but it's very definitely worth it.

Git is a version control system, IMO it's the best one out there.  It's for software developers to keep track of lots and lots of files in a directory, so that one or dozens or thousands of developers can work on the same code and share the results without trampling on each other much.  It was written originally by Linus Torvalds to manage the Linux kernel sources. I've been using version control software for software development and other things for at least 20 years now.  This is very definitely the best one I've ever tried for any scenario I've ever used.

---

### Post by Elishasmantle on 2016-01-02
Hello,

My error in wording.

I am looking for a file audit program like tripwire.

Versioning software is the incorrect term.

I'm trying to find an app / suite that will keep track of any /etc file changes, .conf file changes, etc...
As I am learning Linux it is just too confusing remembering changes I have made to which / what files.

I'm saving HowTO's on ftp server setup, Samba, and other type on installs and have been doing a .bak of the original files and have a document I am trying to make notes in, but I am familiar with Windows Side deployments, automation and am wanting to use some tools available like tripwire to take some of the headaches away of this learning curve.

My apologies for using the incorrect terminology in the post.

Thank You,

Elishasmantle

---

