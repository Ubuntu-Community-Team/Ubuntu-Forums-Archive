---
title: "[IDEA]: Auto-detect existing /home partition during installation"
date: 2007-04-17
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2007-04-17
**Summary:**
An option in the installer to preserve an existing /home partition

**Rationale:**
Many users prefer to keep a separate /home partition in case they either have to reinstall or they want to reinstall (not everyone likes upgrades). Even experienced users can accidentally put a check (or tick) mark on the wrong partition for reformatting, but especially beginner users may not know how to preserve their /home partition during a reinstallation.

**Scope and Use Cases:**
Nicola asked a lot of questions on the forums before she installed Ubuntu. She did a lot of Google searching too. After much consideration, she decided to take others' advice and create a separate /home partition so that her settings and personal files would be preserved in case she ever reinstalled Ubuntu.

She had been using Dapper for a long time and decided moving to Gutsy would be... gutsy. But upgrading from Dapper to Edgy to Feisty and then to Gutsy would take *forever*, even on her broadband connection. So she decides for a reinstall. Amazingly, the installer says, "You seem to have a /home partition as /dev/hda2. Would you like to preserve its contents and have Ubuntu installed to /dev/hda1?" She says "Yes," of course, and is glad the installer was smart enough to recognize that.

**Implementation Plan:**
Part of Ubiquities scanning of partitions would have to scan the contents of the partitions and not just their sizes, locations, and filesystem types. It would look for any partition whose top-level directory was /home and that had two levels down from it something like .dmrc.

**Blueprint**:
[https://blueprints.launchpad.net/ubuntu/+spec/home-partition-integration-with-installer](https://blueprints.launchpad.net/ubuntu/+spec/home-partition-integration-with-installer)

P.S. This idea is separate from but would work really well in conjunction with...
[[IDEA] Gutsy should default to setting up a separate home partition](http://ubuntuforums.org/showthread.php?t=410093)
[[IDEA] Autodetect accounts in existing /home ](http://ubuntuforums.org/showthread.php?t=410584)

---

### Post by viciouslime on 2007-04-17
> **aysiu said:**
> Well, that brings up a second point. Rather than scrapping the whole "create a /home partition by default" idea, how about making it so that a reinstallation is able to detect an existing /home partition and, by default, use it instead of reformatting it. (Again, you could always override the default if you did want to reformat the partition.)

It shouldn't be too difficult for the installer to scan the contents of the partition and see if there's anything that looks like a /home directory.

Perfect! Then the user could be presented with a choice, something like "A previous installation of ubuntu has been detected, would you like to preserve the contents of your home folder (your documents and application settings) when you reinstall?"

---

### Post by rsambuca on 2007-04-17
> **aysiu said:**
> Well, that brings up a second point. Rather than scrapping the whole "create a /home partition by default" idea, how about making it so that a reinstallation is able to detect an existing /home partition and, by default, use it instead of reformatting it. (Again, you could always override the default if you did want to reformat the partition.)

It shouldn't be too difficult for the installer to scan the contents of the partition and see if there's anything that looks like a /home directory.

Now that is a tremendous idea.

---

### Post by harun on 2007-04-17
> **viciouslime said:**
> Perfect! Then the user could be presented with a choice, something like "A previous installation of ubuntu has been detected, would you like to preserve the contents of your home folder (your documents and application settings) when you reinstall?"

I would like it very much if it worked this way.

---

### Post by viciouslime on 2007-04-17
> **viciouslime said:**
> Perfect! Then the user could be presented with a choice, something like "A previous installation of ubuntu has been detected, would you like to preserve the contents of your home folder (your documents and application settings) when you reinstall?"

Ahhh this post has been moved, wondered where it had gone! Lol. Yeh good idea to separate this from my thread.

---

### Post by oomingmak on 2007-04-21
So how does it work at the moment then?

What would you do have to do currently to ensure your home partition is safe during a re-install?

---

### Post by aamukahvi on 2007-04-21
> **aysiu said:**
> **Implementation Plan:**
It would look for any partition whose top-level directory was /home and that had two levels down from it something like .dmrc.
It's kind of hard to tell if a partition is /home when it's unmounted, if not from existing fstab. The partition in question is just mounted _under_ /home in the root file system. And .dmrc would be 1 level down.

Nice idea, +1.

---

### Post by aysiu on 2007-04-21
> **oomingmak said:**
> So how does it work at the moment then?

What would you do have to do currently to ensure your home partition is safe during a re-install? Right now, you select to **Manually Edit the Partition Table,** and then you choose to mount the partition at /home and uncheck the box that says **Reformat.**

> **aamukahvi said:**
> It's kind of hard to tell if a partition is /home when it's unmounted, if not from existing fstab. The partition in question is just mounted _under_ /home in the root file system. And .dmrc would be 1 level down.

Nice idea, +1. Yeah, it sounds great in theory, but I have no idea how difficult it is to implement.

---

### Post by tgoose on 2007-04-22
Is not the default in Ubuntu to install no separate /home partition anyway? Not that I think that's a good idea, but I'm pretty sure I had to manually set a separate partition. If so, that behaviour needs to be changed before any detection is worthwhile, or there won't **be** a partition to detect!

---

### Post by davegod75 on 2007-04-22
I like this concept.  It has my vote

---

### Post by aysiu on 2007-04-22
> **tgoose said:**
> Is not the default in Ubuntu to install no separate /home partition anyway? Not that I think that's a good idea, but I'm pretty sure I had to manually set a separate partition. If so, that behaviour needs to be changed before any detection is worthwhile, or there won't **be** a partition to detect!
Yes, this goes hand in hand with the idea to have a /home partition set up by default (a default that can be overridden if people prefer not to have one).

---

### Post by madman91 on 2007-04-22
+1
Me as well.
Would definitely make my dad less queasy when upgrading Ubuntu :)

---

### Post by aysiu on 2007-04-25
I see a potential snag in the implementation part of things.

Is there an easy way for the Ubuntu installer to detect a *buntu /home partition and distinguish it from a SuSE /home or a Mepis /home?

I've often heard it said that mixing /home partitions from different distros can result in breakage. Is that true? If so, maybe the installer should detect the /home from another distro and then warn you about not using it?

---

### Post by migla on 2007-04-25
> **aysiu said:**
> I see a potential snag in the implementation part of things.

Is there an easy way for the Ubuntu installer to detect a *buntu /home partition and distinguish it from a SuSE /home or a Mepis /home?

I've often heard it said that mixing /home partitions from different distros can result in breakage. Is that true? If so, maybe the installer should detect the /home from another distro and then warn you about not using it?

If one uses the same usernames with different distros in one shared /home, I guess it can get messy with configuration files... 

I don't think there should be any confusion if one uses different usernames?

It would be great if configurations for different distros lived in different hidden subdirs, but that would probably be almost impossible, since every distro/application should adhere to it, right?

---

### Post by jethro10 on 2007-04-26
I am also a +1 for this.

This is sorta done right now with an existing windows partition by "Importing" stuff to keep your experience similar.
So why not with an existing Ubuntu partition/folder/home etc.
J

---

### Post by galv on 2007-04-26
I think it is a good idea. I vote for it :)

---

### Post by 23meg on 2007-05-01
aysiu, this idea is also going into the composite Ubiquity enhancements spec we're drafting. We can mark your blueprint as superseded by it afterwards. Let me know if you have any questions.

[EDIT:The spec is [here]("https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-forumideas").]

---

### Post by daengbo on 2007-10-17
For new installs, /home should be mounted noexec in order to limit the possibilities of viruses and trojans. There are under 35 now, but when  gets enough market share, more will appear. We should be secure now, before we need it. This /home partition by default blueprint needs to happen to make upgrades easier and to make the install more secure.

On a side note, I'd like to see the separate /home partition used in conjunction with a new type of upgrade, where a list of currently installed packages is used to wipe / and install from scratch.

---

### Post by smartboyathome on 2007-10-17
> **daengbo said:**
> On a side note, I'd like to see the separate /home partition used in conjunction with a new type of upgrade, where a list of currently installed packages is used to wipe / and install from scratch.

This, like many other ideas, will fall by the wayside because ubuntu tries to keep their installer as simple as possible. :(

---

### Post by drf_av on 2007-10-17
+1

---

### Post by webonomic on 2007-12-10
> **smartboyathome said:**
> This, like many other ideas, will fall by the wayside because ubuntu tries to keep their installer as simple as possible. :(

Simplicity for who?  On one hand, they can keep the installer simple for developers.  But on the other hand, this feature makes it simpler for a large subset of Ubuntu users to upgrade.

I'd vote for the later, because it adds to customer retention.  

I would also think the feature has potential to attract new users from other OS's - especially some Windows users who have experienced the headaches and frustration of the Windows upgrade feature.

---

### Post by maybeway36 on 2007-12-10
What if I have two Linux distros one one computer? If it is implemented, it should be as a new option, not as the default.

---

