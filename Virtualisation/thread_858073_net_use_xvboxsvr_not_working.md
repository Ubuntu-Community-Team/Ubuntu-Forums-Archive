---
title: "net use x:\\vboxsvr\ not working"
date: 2008-07-13
forum: Virtualisation
---

### Post by ashvala on 2008-07-13
Hey,

I am using Ubuntu Hardy Heron 8.04 on my PC...
I just installed VirtualBox on my PC to try Vista, and I want to use a LAN connection on vista.
I put my folder on share & used the net use x:\\vboxsvr\ but it doesnt work at all!
can you help me?

Thank you
Ashvala

---

### Post by fogster74 on 2008-07-13
Hi there,

I've been having trouble getting this working in Linux with XP as the guest and have posted my solution (or at least, what I did before it magically started working!) here: [http://ubuntuforums.org/showthread.php?p=5376994#post5376994](http://ubuntuforums.org/showthread.php?p=5376994#post5376994)

However, it does seems that there are separate issues for Vista (over XP) and it might be worth googling 'VirtualBox Vista vboxsvr' and trying those first :-)

With kindest regards,

S

---

### Post by HotShotDJ on 2008-07-13
> **ashvala said:**
> I just installed VirtualBox on my PC to try VistaWhat version of VirtualBox are you using?  Shared folders don't work with Vista in all versions prior to 1.6.2

---

### Post by saratchandra on 2008-07-13
You should also include the shared folder name and use anything other than x: for the network drive.

---

### Post by ashvala on 2008-07-13
Dude, I am using 1.6.2 but it still doesnnt work!

---

### Post by saratchandra on 2008-07-14
Whats the name of the shared folder you're using?

---

### Post by ashvala on 2008-07-14
it is /home/ash

---

### Post by saratchandra on 2008-07-14
type
> net use M:\\vboxsvr\ash
in windows command line

---

### Post by no1wantdthisname on 2008-07-14
First of all, are you including the space after x: ?
Secondly, there should be the shared folder name after \\vboxsvr\
I.E.

```

net use x: \\vboxsvr\(shared name)

```

---

### Post by orfeu on 2008-07-15
good

---

