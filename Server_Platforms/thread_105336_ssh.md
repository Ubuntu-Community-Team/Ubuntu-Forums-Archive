---
title: "ssh"
date: 2005-12-18
forum: Server Platforms
---

### Post by Daminator on 2005-12-18
I'm not sure if this is the right place to post this (please point me to the right place if it isn't), but 'ssh' is driving me crazy!

I'm trying to use 'unison' to syncronise files between two machines.

The unison part isn't a problem (yet :) ) as I can't get past the stage of getting 'ssh' working. No matter what I do, I just get 'connection refused'.

I assume the problem is with my router settings rather than Ubuntu itself, but I've tried everything and it just wont work. I've opened ports on my DG834 router before for things like BitTorrent and RealVNC, but this has me beat.

Can anyone help??

---

### Post by grendelkhan on 2005-12-18
dumb question, do you have ssh-server installed and running?

---

### Post by StonePiano on 2005-12-19
[QUOTE=grendelkhan]dumb question, do you have ssh-server installed and running?[/QUOTE]

Not such a dumb question.  I ran redhat for a few years before ubuntu.  I had never really thought about the ssh server software.  Your post led me to a solution within 10 minutes:

1. Download and install openssh-server using synaptic package manager.
2. Then in my case I had to enable remote login.
3. Everything worked!

Many thanks for the post.
StonePiano

---

### Post by grendelkhan on 2005-12-19
[QUOTE=StonePiano]I ran redhat for a few years before ubuntu.  I had never really thought about the ssh server software. [/QUOTE]

The **EXACT** same thing happened to me, which is why I thought to ask the question!

---

### Post by Daminator on 2005-12-19
Not a dumb question at all.
'I don't know' is my dumb answer, which implys that it could well be the problem!
I've followed a couple of tutorials on getting ssh to work (using cygwin on the windows side of things) and none of them have said anything about this.
Can anyone point me in the direction of an ssh guide that could help?

---

### Post by Daminator on 2005-12-19
I just got through :-)

Looked up starting 'sshd' through 'cygwin' on windows and just got through to it from the linux laptop.

Not got time to configure Unison and check it all out now because I'm away for a few days now, but the main stumbling block seems to have gone. Thanks for the pointer.

---

