---
title: "RC iso install choice - no confirmation - and use unallocated"
date: 2012-04-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by candtalan on 2012-04-23
Using 12.04  32 bit iso daily build of today, I think this is rc, not sure. The live session went ok in  my test machine (which only runs ubuntu 12.04 in 2D, not 3D) and I intended to look at the initial actions in the install from live session. I had not really intended to proceed with the full install at this stage. The choice I used was the default - install 'Ubuntu along side' them, and it proceeded from that screen. However to my surprise there was no 'confirm' action, say to confirm the choice in case of mistaken  mouse click, the install actually went immediately ahead, copying files etc. 
Back at the ranch, I used gparted to examine which partition the installer had chosen in this situation.  It is a complex machine structure with four hard drives, multi booting from whichever grub was last used. XP and Win 7 also. There are many partitions, some used for backup reasons, and several large un partitioned  unallocated spaces. The install seemed to be going ahead using a previously unallocated space of 86GB, which is nice because the ability to install easily into unallocated space had been missing for a few ubuntu versions. The install process went quickly (it is already finished! ). I would have been happier if I had been asked  just to 'confirm my choice before fully proceeding to write to disc.

Is the lack of 'confirm' action a bug?

edit
mm. not sure yet that it silently installed into an unallocated partition, am checking.
edit2
it did NOT install into the partition I had hastily seen using gparted showing there, during the early part of the install as 'target', it seems to have installed over the pre existing [ubuntu 12.04 beta 2 updated]. 
I cannot give this any more time just now, but it really needs to be checked out more.

---

### Post by kansasnoob on 2012-04-23
Sadly that's the way it works:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/964331](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/964331)

I have a lot of history with this, I'm Erick Brunzell on Launchpad, so please see:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/964331/comments/5](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/964331/comments/5)

and:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

It looks like we may get a real "fix" for this in Q, I'm hopeful.

---

### Post by candtalan on 2012-04-23
> **kansasnoob said:**
> Sadly that's the way it works:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/964331](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/964331)

I have a lot of history with this, I'm Erick Brunzell on Launchpad, so please see:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/964331/comments/5](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/964331/comments/5)

and:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

It looks like we may get a real "fix" for this in Q, I'm hopeful.

Hi Erick, thanks. In my case here, something  slightly different also seems to have happened.
During the early stage of install as I mentioned,  I am fairly sure gparted indicated that a big  unpartitioned space was at that time, indicated as 'Target'. However, during the actual installation I did not notice any activity labelled as formatting' or 'making filesystem'. And when now finally running the instaled ubuntu 12.04 as mentioned, the new install has been done over on top of the pre installed 12.04, I think without formatting. All of which makes some, if not perfect, sense. However, it means that it is doing quite a bit MORE than -installing 'alongside'. I do like the idea of it installing  alongside and silently using  unpartitioned space, as long as it is an intended and proven function. Many newcomers will shrink Windows and then want to install alongside. If it is reliable, I can prompt those newcomers in that direction.

But, now, installing silently OVER my test 12.04 as a warm reinstall is not quite what I had expected.... :-)

---

### Post by kansasnoob on 2012-04-23
It shouldn't do what you're describing then. I'd suggest filing a new bug report, maybe just mention the bugs that I listed, and please do also subscribe me.

Since Colin Watson has indicated serious interest in rebuilding ubiquity in Q he needs to know of every possible glitch.

At the very least it will light a fire where it needs to be lit :biggrin:

---

### Post by candtalan on 2012-04-23
> **kansasnoob said:**
> It shouldn't do what you're describing then. I'd suggest filing a new bug report, maybe just mention the bugs that I listed, and please do also subscribe me.

Since Colin Watson has indicated serious interest in rebuilding ubiquity in Q he needs to know of every possible glitch.

At the very least it will light a fire where it needs to be lit :biggrin:

will aim to do that

mm. Having a problem knowing how to file a bug without apparently having a package owning the bug - Ubiquity? Ubiquity  probably only runs during install (?) So what do I do to raise a new bug  after installation about an installation process problem?

I think I have found how to do it ...
No I have not, ubuntu-bug needs, requites, a package or pid. Still mystified
ok, I think I found a way apport-cli  (etc)

---

### Post by kansasnoob on 2012-04-23
Copy-n-paste the following into your web browsers address bar:

```
http://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug?no-redirect
```

Possible title: Precise ubiquity used unintended space/partition

Describe the problem in the best detail possible and, from the effected machine, include the full output of:

```
sudo parted -l
```

Then reference the aforementioned bugs as related but not true duplicates and explain why the behavior seems quite different. Colin Watson is by far one of the best devs I've ever worked with so if he gets assigned, which I'd guess to be the case, you'll find him to be very patient and helpful.

Also when filing a bug that way it's best to provide a brief, simple hardware profile.

---

### Post by candtalan on 2012-04-23
Thanks Erick, filed:

Precise ubiquity used unintended space/partition
Ubuntu &#8220;ubiquity&#8221; package. Bug #987253

---

### Post by kansasnoob on 2012-04-23
Could I get you to make sure the bug is marked as public?

It's in the upper right hand corner :)

Thanks for being so patient and cooperative.

---

### Post by jerrylamos on 2012-04-23
> **kansasnoob said:**
> .... Colin Watson has indicated serious interest in rebuilding ubiquity in Q he needs to know of every possible glitch....

Whee!  Fun!  I like submitting valid launchpad bugs, and "Ubiquity" is a real prizewinner for me generating lots of bugs!  "Q" installs should be a lot of fun with new code and new bugs!

Jerry

---

### Post by kansasnoob on 2012-04-23
> **kansasnoob said:**
> Could I get you to make sure the bug is marked as public?

It's in the upper right hand corner :)

Thanks for being so patient and cooperative.

I was probably just being impatient :redface:

I'm now subscribed and effected.

---

### Post by candtalan on 2012-04-23
> **kansasnoob said:**
> Could I get you to make sure the bug is marked as public?

It's in the upper right hand corner :)

Thanks for being so patient and cooperative.

It shows as Public currently is that ok?

---

### Post by kansasnoob on 2012-04-23
> **jerrylamos said:**
> Whee!  Fun!  I like submitting valid launchpad bugs, and "Ubiquity" is a real prizewinner for me generating lots of bugs!  "Q" installs should be a lot of fun with new code and new bugs!

Jerry

As soon as Precise testing is totally done I'm going to share my limited knowledge with the new testing team so things will get better, independent of any one individuals ability (or lack thereof) ;)

---

### Post by kansasnoob on 2012-04-23
> **candtalan said:**
> It shows as Public currently is that ok?

Great! You did a great job :guitar:

Thank you very much.

---

### Post by nm_geo on 2012-04-23
> **kansasnoob said:**
> As soon as Precise testing is totally done I'm going to share my limited knowledge with the new testing team so things will get better, independent of any one individuals ability (or lack thereof) ;)

In all my along-side installs (albeit not hundreds) I have never had an over-write like the one listed.  I would like to see if I can re-create it though so I better subscribe to the bug huh?


I for one am looking forward to your sharing kansas.  "May the Force be with U"

---

