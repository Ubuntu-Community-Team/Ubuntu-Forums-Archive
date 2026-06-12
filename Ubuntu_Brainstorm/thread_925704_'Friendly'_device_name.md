---
title: "'Friendly' device name"
date: 2008-09-20
forum: Ubuntu Brainstorm
---

### Post by jfbilodeau on 2008-09-20
Good day!

Yesterday, I ended up rebooting my machine, which caused a disk check to take place. I'm very pleased that it's now possible to cancel the disk check, but as I was watching it, I realized that some users may be intimidated by the display.

The screen is warm and friendly, but the line that says 'Checking /dev/sda3...' is probably meaningless to most users, and may be intimidating.

Linux has done a lot to provide a user-friendly environment, but dropping device names like that can make the OS look 'complex' or too 'technical.'

I would like to propose that 'technical' names like sda1, hdb1, eth0 and so one be paired with a 'friendly' name. I know that this is already done in many places, like the wonderful network manager applet. But I think it would be both beneficial and less intimidating for the user to educate them about the meaning of lines line /dev/sda3.

For example, a message like this may be seen as friendlier, while indirectly educating users about the terminology. Furthermore, advanced users loose nothing:

Checking third partition of the disk A (/dev/sda3)...
or
Checking /dev/sda3 (SATA Disk 1 (A), partition 3)...

Or any combination/variation on the above.

Just my $0.02 CAD for what it's worth! Hope everyone has a great day!

---

### Post by InfinityCircuit on 2008-09-21
Why is six words that say "third" and "A" more "friendly" than /dev/sda3?

You can use e2label to label your disks if you want, or just install on lvm and then you can name the lvm sections whatever you want.

---

### Post by jfbilodeau on 2008-09-21
> **InfinityCircuit said:**
> Why is six words that say "third" and "A" more "friendly" than /dev/sda3?

You can use e2label to label your disks if you want, or just install on lvm and then you can name the lvm sections whatever you want.

I'm trying to find ways to 'educate' newcomers to Linux about what a statement like /dev/sda3 means. Both of us knows what that means, but my mother, who also uses Ubuntu, would have no clue as to what is /dev/sda3.

LVM is a nice solution, but I don't think it really solves the problem. If someone asked me what is sda3, I can't reply 'Install LVM and call it whatever you want!' ;)

If someone asks you what /dev/sda3 mean, what would you answer? How would you word it?

J-F

---

### Post by smartboyathome on 2008-09-21
I don't like that idea. Linux's names are there for a reason. I think that if you really wanted this, you'd have to take it up with the devs themselves on the [ubuntu-devel-discuss mailing list.]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss")

---

### Post by jfbilodeau on 2008-09-21
> **smartboyathome said:**
> I don't like that idea. Linux's names are there for a reason. I think that if you really wanted this, you'd have to take it up with the devs themselves on the [ubuntu-devel-discuss mailing list.]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss")

Thanks for the reply. I'm not talking about taking away or changing the device names. I'm talking about displaying both the Linux name as well as a 'friendly' name in messages that end-users will see. Furthermore, I'm not suggesting that we 'dumb-down' the command-line or /dev.

The names are there for a reason, and I think it would be nice if we could help 'educate' users by briefly describing what does 'Checking /dev/sda3...' means when they see it. Otherwise, I'm afraid that expecting users to either know or not care about device names will only further the impression that Linux is 'complex' and that one needs to know arcane knowledge to be able to use it.

If my suggestion is totally silly, I would appreciate if you could help me understand why displaying 'friendly' device names with the actual device name is a bad idea.

Thanks,

J-F

---

### Post by smartboyathome on 2008-09-21
I guess it could say "Checking disk (partition /dev/sda3)...", which would help people understand a little more. But honestly, I still think you should take this up with the devs, as they are the ones who have control over Ubuntu and they don't check this board.

---

### Post by cardinals_fan on 2008-09-21
I wasn't born understanding the device names.  I learned them, just as all new users who spend time with them learn them.

Bottom line: they are fine as is.

---

### Post by jfbilodeau on 2008-09-22
Please help me understand. I'm totally confused.

For starters, this forum is call Ubuntu *Idea* Pool. under section *Development & Programming*. Now, I'm told that the developers don't hang out around here, and I'm pointed to a mailing list. Thanks for the info, but I'm confused about the role of the forum now.

Also, as per my suggestion, I fail to understand the logic of it's fine as it is for two reason:
1. I'm not talking about changing anything. I'm talking about complementing existing messages with a bit more details for users that don't already know the meaning of device names.
2. There's an air of arrogance in implying that one has to learn the device names themselves.

From the logic posted on the reply, I'm getting the impression that it's wrong for Gnome to call a CD-ROM as such. Instead, there's should be a link on my desktop called /dev/scd0 because it's fine as it is. Let the user figure it out! For that matter, let's not even put a link. We should let the user figure out how to mount a device. After all, we learned device names. Why should then not go through the same initiation?

I initially learned Linux by compiling the darn thing from scratch. I did it this way because to me, that's fun. However, for the folks around me that use Ubuntu, they like it because it's for **Human** being.

Anyway. I'm ranting...sorry for the vent.

J-F

---

### Post by Slug71 on 2008-09-22
> **cardinals_fan said:**
> I wasn't born understanding the device names.  I learned them, just as all new users who spend time with them learn them.

Bottom line: they are fine as is.

You and a lot of us would learn them but for newbies that no nothing about Linux can feel quite overwhelmed by all the new things to learn and the same can be said when introducing older people like parents to Linux who found even Windows 3.1 and 95 overwhelming when first introduced to a PC because all they were used to were typewriters.

I think its a good idea. He's just asking for a few words to be added. 

Bottom line is, Linux can seem a big learning curve for those that have never used it and even though Linux has come a long way over the last 4/5 years, it still does turn a lot of people away from it and the easier things get and the more we can do to make it seem more "friendly" the better it can be for them and us that have already used it for a while and have good knowledge of it as this will bring more and more people to Linux which means better support. Hardware and Software.

---

