---
title: "no more GRUB2 for me I'm full thanks canonical"
date: 2010-05-30
forum: Testimonials &amp; Experiences
---

### Post by bradmayne04 on 2010-05-30
the things I went through w/ that bootloader.  Did you know GRUB2 isn't even a ver. 2?  It's still a beta!! It's listed officially as "1.97 beta 4" on boot.  I tried to upgrade to lucid.  That messed up my whole drive!  It started off that the MBR was out of whack after install and I couldn't boot into win 7.  No big deal I thought!  I'll pull out the ms dos recovery disk I have and all will be well!  I'll pull up the old c: and do a chkdsk, possibly change the MBR if chkdsk doesn't fix your win 7 boot.  Nope.  Wrong.  No good.  I then tried some unix tools as I could boot into lucid just not boot into win7.  I changed the boot w/ testdisk.  I then began getting errors when trying to boot into win7.  Actually it was more of a design.  It looked like this: ====S
Then I would have to manually reset the pc through the power button.  I then ran dos tools again.  Which fixed the =====S problem and brought me back to where I originally was which was being able to boot into lucid lynx from GRUB2 but not win 7.  When trying to boot into win 7 I would get sent back to the GRUB2 Operating System selection screen.  I ended up having to reformat the whole drive.  I tried everything to save the win7 partition but it just wasn't happening.  I tried everything.  I posted on this for the better part of 2 days.  I wish old fred many thanks for more idea's.  Everytime I was pulling my hair out there were different idea's.  Though none worked I now have a  much deeper understanding about GRUB2 and the processes involved.  I don't know why grub2 added ext 4.  There's a lot of things that have changed on the windows side too.  Win 7 does not boot like XP AT ALL.  So there were problem's on both sides.  Anyway's I went back to using karmic.  I think I'm going to stay w/ that distro for awhile.

---

### Post by drs305 on 2010-05-30
bradmayne04,

I'm sorry you have had so much trouble with Grub 2. I don't see a request for assistance in this post, so it would perhaps be more appropriate in the Testimonials and Experiences forum.

If you aren't seeking help I'll move this thread after giving you a chance to respond here.

One note: If you were happy with Grub, or even if you weren't, it never made it to version 1.0. Legacy grub is 0.97 and was so for years.

---

### Post by bradmayne04 on 2010-05-30
Well you can move this thread if ya want.  I don't know why your sayin it never got past ver. 1.0.  I will show you from synaptic that I have ver. 1.97 installed now.

---

### Post by Ozymandias_117 on 2010-05-30
> **bradmayne04 said:**
> Well you can move this thread if ya want.  I don't know why your sayin it never got past ver. 1.0.  I will show you from synaptic that I have ver. 1.97 installed now.

That's Grub2, not Grub Legacy...

---

### Post by drs305 on 2010-05-30
What I was saying was that the Grub we were all accustomed to (now commonly called Grub legacy) never made it past version 0.97. There was never a version 1.0.

I believe Grub 2 started with 1.96 and is now at 1.98. There may or may not ever be a Grub 2.0 and the developers aren't too concerned with it.

Thread moved from ABT to T&E.

---

### Post by philinux on 2010-05-30
@bradmayne, also sorry to here your tale. If I had come across your support thread I would have directed you to the General Help forum stick where a solution is shown.

---

### Post by dE_logics on 2010-05-30
You can move back to the old GRUB.


Why didn't you just update-grub when you where in Ubuntu...that solves the problems.

---

### Post by mastablasta on 2010-05-31
> **bradmayne04 said:**
> the things I went through w/ that bootloader. Did you know GRUB2 isn't even a ver. 2? It's still a beta!! It's listed officially as "1.97 beta 4" on boot. I tried to upgrade to lucid. That messed up my whole drive! It started off that the MBR was out of whack after install and I couldn't boot into win 7. No big deal I thought! I'll pull out the ms dos recovery disk I have and all will be well! I'll pull up the old c: and do a chkdsk, possibly change the MBR if chkdsk doesn't fix your win 7 boot. Nope. Wrong. 
 
 
Damn skippy it's wrong! chkdsk doesn't fix boot. fixmbr fixes boot for windows (at least on XP) and the first thing i would od in this case would be to throw in the system CD , go to conosle and try fixmbr (stands for: fix main boot record)command.

---

### Post by wilee-nilee on 2010-05-31
Just for the record all your problems were due to user errors. You disregarded legitimate fixes, blah blah-ed oldfred to begin with until I pointed out that he was a person to listen to, Take some personality responsibility man. Blaming a operating system for not understanding what your doing is not going to help you in the future.

I know I am not supposed to respond in this way in this section but if the mod in charge of this section looks through this persons threads they will see that I am correct here. This user updated to Lucid and installed grub in W7.

---

### Post by Sef on 2010-05-31
Locked.  Too close to debate and support now.

---

