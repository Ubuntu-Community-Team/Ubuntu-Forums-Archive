---
title: "Adding a server - first step"
date: 2008-11-16
forum: Server Platforms
---

### Post by happyhacker on 2008-11-16
I am going to add a server to our network of 18 PCs for initially file sharing. Some of our files need to be shared some not (leave them on the relevant PCs). My first couple of questions (new to this BTW):

1. I am going to install Ubuntu at home and take it to the office to connect. Will this compromise the Ubuntu setup if it has seen my home network and then next switchon is a different network?

2. Currently all our PCs (mix of XP and Vista) are P2P and there are some workgroups (random and not used). What tidying should I perform on the P2P network before I introduce the server?

Advice appreciated on these starter points and anything else I sould consider.

---

### Post by Iowan on 2008-11-16
It *shouldn't* be a problem if server "wakes up" in a different net.  Addressing will require attention.  I presume you'll be installing Samba to share files to Windows machines.  Somehow, that seems to be getting trickier with each new release - and Vista apparently has a few new twists of it's own.

---

### Post by cariboo on 2008-11-16
Samba setup on the server side really hasn't changed that much since version three came out. I have been using essentially the same smb.conf since samba 3 came out. 

I have a pretty simple setup, where each user has their own private directory, and shared Data, Movie and Music directories. The Data directory everybody has read/write permissions and the Music and Movie directories are read only.

It is the desktop where file sharing is getting complicated, Canonical in their effort to make it easy for anyone to create a home network has changed things enough that new documentation is needed, that documentation has not been created yet, or at least I haven't been able to find anything yet.

JIm

---

### Post by happyhacker on 2008-11-17
> **Iowan said:**
> Somehow, that seems to be getting trickier with each new release - and Vista apparently has a few new twists of it's own.

Hmm, don't put me off! let's hope those who take the releases forward have got the end users in mind.

---

### Post by happyhacker on 2008-11-19
Going to do the install this morning, thanks for the feedback.

---

### Post by Iowan on 2008-11-19
> **cantthinkofanickname said:**
> Hmm, don't put me off! let's hope those who take the releases forward have got the end users in mind.Not trying to put you off, just an alert that not everything gets easier as the release numbers get bigger.  I think it's a safe bet that the answer to any rough areas you encounter can be found here on the forum,somewhere. :)

---

