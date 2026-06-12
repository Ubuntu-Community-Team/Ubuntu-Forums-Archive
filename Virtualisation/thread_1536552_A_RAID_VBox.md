---
title: "A RAID VBox?"
date: 2010-07-22
forum: Virtualisation
---

### Post by uRock on 2010-07-22
I am trying to help a friend, but I haven't been able to find what we need. Has anyone seen any documentation for setting up a virtual RAID install?

Thanx,
uRock

---

### Post by pricetech on 2010-07-22
If by "virtual RAID" you mean Software RAID, you'll need to start with the alternate CD, which will give you an option to build a RAID array at install time.

It that's not what you're talking about, then a little more clarification is in order.

---

### Post by uRock on 2010-07-22
He's trying to do a Windows install with software RAID. I was thinking there may be something that had to be set up within the VBox software prior to installing. If not, then he'll have to get help from a Windows forum.

---

### Post by fjgaude on 2010-07-22
You mean that the RAID is software on two or more drives? With VBox installed on the RAID, and then you are trying to install Windows as a guest on VBox?

What is the host OS?

---

### Post by pricetech on 2010-07-22
I'm not aware of any versions of windows that will support software RAID except the Server versions.

There may something third party, but nothing that I know about.

---

### Post by uRock on 2010-07-22
The friend is taking an A+ class and trying to install Windows in a VBox on a system with no RAID, but he needs to have RAID within the VBox. The fun part comes from the lack of direction given by A+ text books. If it is something that has to be created by Windows within the VBox, then he will be S.O.L.

---

### Post by fjgaude on 2010-07-22
He will have to install Windows Server to get software RAID as guest within VBox. Good luck with that! <smile>

I run a Ubuntu host with software RAID, **mdadm**, VMware Player, and WinXP as a guest accessing the RAID as its database.

---

### Post by uRock on 2010-07-22
> **fjgaude said:**
> He will have to install Windows Server to get software RAID as guest within VBox. Good luck with that! <smile>

I run a Ubuntu host with software RAID, **mdadm**, VMware Player, and WinXP as a guest accessing the RAID as its database.
I told him to get enroled in the school's MSDNAA and get his copy of 98, XP Pro, Vista Business, 7 Pro, and server 2008, but his teacher is slow to get it done.

---

### Post by pricetech on 2010-07-23
I think you can still get a demo of Server 2008, but I won't swear to it.  A technet subscription used to give you limited versions of Server, but I don't know if it still does.

A couple of other options maybe.

By the way, it's called "Hyper-V" in Server 2k8.

---

### Post by uRock on 2010-07-23
> **pricetech said:**
> I think you can still get a demo of Server 2008, but I won't swear to it.  A technet subscription used to give you limited versions of Server, but I don't know if it still does.

A couple of other options maybe.

By the way, it's called "Hyper-V" in Server 2k8.

Thanks, I'll pass that on.

---

