---
title: "virtualisation within ltsp"
date: 2007-11-09
forum: Virtualisation
---

### Post by Lem on 2007-11-09
If I run vmware or virtualbox within ltsp, how would it react? 

ie. if I wanted to make XP available to my clients and ran it within a vm in the ltsp build, would I get problems if more than one client wanted to use it?
Would it even work in the first place?

---

### Post by bazz on 2007-11-10
> **Lem said:**
> If I run vmware or virtualbox within ltsp, how would it react? 

ie. if I wanted to make XP available to my clients and ran it within a vm in the ltsp build, would I get problems if more than one client wanted to use it?
Would it even work in the first place?

There are a few catches.
You need to set the permissions on the VMware files for the user that will be on the Windows LTSP thinclient. I created a folded in the root directory called vmware machines and did a chroot 777 on it. Makes it a bit easer. One thing I would not do is build VMware machines in a users home directory. I played around with that once before and had problems.
What your talking about I have done this for an automation lab and it works nice. But if you are looking for multiple users to use one vmware machine at the same time....it will not work. You need a machine for each user, or users can log on the machine one at a time. However if you use win4lin you just export the profile. Win4lin has some real cool stuff, but its a bit processor intense. If your interested in Win4lin I suggest you should read the manual. 
I think you also need to add a license number for the user in VMware. Also you may want to create an .xsession file in the users home directory.
As for VirtuaBox...I have no idea how to get it to work, however I hope to find out sometime.

---

### Post by Lem on 2007-11-11
How about running the vm on server and having clients RDP into it over LTSP? Virtualbox has a nice VRDP server built in.

Hmm.. might have to do some tinkering and see what works best!

---

### Post by bazz on 2007-11-11
You can do that, but at this point I dont know how. What I'm trying to do is make it all transparent to the end user, so It looks like they boot into a windows machine. 
I will be playing around with Virtualbox sometime in the future. I like the usb thin client they have.
But yes what you are talking about will/should work. Let me know what   and how you come up with.

---

