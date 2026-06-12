---
title: "Recovery Password"
date: 2008-05-16
forum: Ubuntu Brainstorm
---

### Post by picopir8 on 2008-05-16
I would like to see a screen at install that allows me to set the root password.  I am NOT asking that the root account be activated, just that the password be set.  Presently, someone can simply reboot the computer in single user mode and become root without entering a single password.  However, if the root password is specified, then it must entered when booting in single user mode.

---

### Post by smartboyathome on 2008-05-16
They won't do this, but you could propose it to ubuntu-devel-discuss mailing list and see what other developers think.

---

### Post by tom56 on 2008-05-18
What's the point of this? You need physical access to the machine to boot recovery mode, and if you have physical access then the security of the machine is already compromised. This would just cause problems with people who forget passwords.

---

### Post by aysiu on 2008-05-18
tom56 is correct.

Your idea here is to give the illusion of security, not real security.

---

### Post by picopir8 on 2008-05-18
I totally disagree.  Someone also needs to have physical access to my car to steal it but I still take precautions to ensure I dont leave keys in the car or leave the doors open.

Right now the present login screen provides a grater illusion of security. Why enter passwords at all to log in?  Why not just enter your user name?  If something should not be done out of fear of providing an illusion of security then by that logic we should get rid of all login passwords.

Physical access security risks should not be ignored/excused simply because there are other such risks.  An effort should be made across the board to close all security risks.

Personally I do simply what almost every IT department does.  I set my root password and then lock down my BIOS to prevent booting off external media.  Adding the root password prevents someone from gaining access unless they have a liveCD or other bootable media.  Most people do not carry such things around with them so it does improve security substantially.  Locking down the BIOS prevents people from booting off something that could give them access. That prevents access from just bout everyone else.  Someone could still open the computer and remove the hard drive, but that would certainly catch someones eye in an office and take substantially longer to accomplish.

---

### Post by aysiu on 2008-05-18
I think you're confused.

Setting a BIOS password, Grub password, and root password will slow down the compromise, providing the malicious party doesn't just steal the computer altogether and abscond with it to another location in which they'll have all the time in the world to reset the BIOS or physically remove the hard drive.

As for your car analogy, perhaps you're also experiencing a false sense of security there, too. Malicious parties have no qualms about breaking car windows and stealing things you have there, which is why a lot of people advise you not to leave valuables in your car. I know a lot of people who just leave their cars unlocked, because they don't want people breaking their car windows (which are costly to replace), and they know they have nothing valuable in their cars to steal.

So, yes, physical access to the car usually means access to the car's contents, just as physical access to the computer usually means access to the computer's contents.

There is a point, though, where the analogy breaks down. Generally speaking, you have control over who has physical access to your computer. You do not, however, unless you have the luxury of a private garage at all times, have as much control over who has physical access to your car.

The lock on a car is handy when you are leaving the car for only an hour or so in a relatively safe neighborhood, just to know people aren't snooping. Having lived in a major metropolitan area for the past seven years (in which time, my car was broken into four times), I can tell you that locking the car if you leave it overnight in the street (as those without the luxury of a private garage often have to do) *does* give people physical and total access to your car.

Home computers are generally physically accessed only by friends and family members. If you don't trust your friends and family members, and they have any knowledge of computers, you should not give them physical access to your computer. If, however, they know very little about computers, they won't know what to do at root@ubuntu:~$ anyway.

And, remember, this is just a default, not a mandate. If you're in an atypical situation in which malicious parties have access to your computer for only five minutes at a time, then setting Grub, BIOS, and root passwords may actually do some good. You always have that option. No one can stop you from doing that.

---

### Post by picopir8 on 2008-05-18
Again, if its not worth adding a root password and if we should simply limit physical access then why have a local login password at all?

I agree, a root password and locking down the BIOS simply slows people down, but that does not mean it should not be done.  Yes we choose the people who we allow in our homes.  But a lot of people have mischievous kids, some have snoopy housekeepers, or devious roomates, etc. People who run small businesses may have cleaning crews and other people who may have physical access to the computer.  These people most likely are not going to risk taking the computer apart because it takes a while and they might get caught in the process.

And yes, we still can go in and set the password, but that goes back to my first question. Why not do the same with the user passwords then?  If it is worth putting a password to the user accounts then it should be worth doing the same for the root account.

---

### Post by aysiu on 2008-05-18
Because most people do not have malicious intents but may do general snooping if it's easy enough for them. And most people (family members / friends) have no clue how to snoop or mess with stuff at root@ubuntu:~$

So basically think of it in terms of these scenarios: [list][*]No one touches your computer except people you absolutely trust [*]No one touches your computer except people you trust for the most part but who wouldn't know what to do at a root terminal anyway [*]People you don't trust somehow have physical access to your computer[/list] Ubuntu, as it's set up now works fine for both of the first two scenarios, and setting a root password, etc. wouldn't be much help (except, as we both agree on, to slow down the compromise - assuming you've somehow bolted the computer to the ground so that it can't be stolen) anyway.

Generally speaking, mischievous family members don't want to ruin your life. They just want to play around. They might change your wallpaper to something embarrassing, for example. But they're not going to want to delete all your data or make your computer unbootable. And, if they had that kind of intention, what would just stop them from taking a sledgehammer to your computer?

---

### Post by picopir8 on 2008-05-19
Okay, last post, i promise!:)

I am more concerned about the third group of people.  In a perfect world you could prevent people you do not trust from using your computer, but people in college dorms often do not have a say because they may not know their roommate(s) that well.  An untrustworthy roommate is not likely to steal a computer or opening it up because their is a high risk of getting caught.  But they might be very willing to try and break in and steal personal information.  Also parents might want to restrict their kids access, and there is know doubt that if a kid is using a linux computer, it wont take long for them to know more about it than most parents.  The kid might not be doing anything damaging to the parent but they might be doing something that the parent does not want them to do.

Even if you do not lock down your BIOS, a password does provide more security because it prevents someone from simply rebooting the computer to get access.  It forces them to use a liveCD (which can then be blocked by locking down BIOS).  So it does have a positive effect on security and AFAIK does not introduce any negative effects, so I see no reason to leave it unset.

We both seem to understand the hole and its implications but I think we have a different view of the problem.  The present philosophy gathered from the previous posts (sorry for paraphrasing) is: limit physical access to the computer to untrusted people (or take appropriate steps to secure it yourself), and even if some sneak through, they probably wont know what to do at the command line.  However, I think that most people believe the standard install to be fairly secure and are not taking additional steps to make it more secure or limiting access as much as they should.  I know I fell into that group until the first time I booted into single user mode and was surprised that there was no password protection. 

I understand the need to balance security and ease of use, so I guess if the root password is not set by default, then there needs to be a way to communicate to new users that their computer is not totally secure since someone can reboot in single user mode to gain access.

---

