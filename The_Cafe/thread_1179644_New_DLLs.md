---
title: "New DLLs?"
date: 2009-06-05
forum: The Cafe
---

### Post by compnut41 on 2009-06-05
I have this friend who has gone down the rabbit hole of windows vista and windows 7 and is trying to drag me down with him. He is currently giving me a hard time for using Ubuntu. His favorite attack is an article called why everyone hates Linux, one of the major complaints being that it cannot run commercial software.

"Why doesn't Linux just make some open source "Win32 DLLs" and get past the whole compatibility issues. I mean don't they want to actual attract people." Well that is close enough to what he said, and it got me thinking, why not?

My question is who actually thinks this is a good idea, and if not what reasons why not. I gave him a weak rebuttal which isn't going to hold until Monday and I kind of need some help.

---

### Post by .Maleficus. on 2009-06-05
For starters, Linux doesn't use DLLs, Linux uses .so (shared object) files.  Second, there is already a valiant attempt being made in a project called Wine, which basically does what you want.  For more info:

[http://www.winehq.org](http://www.winehq.org)

---

### Post by ad_267 on 2009-06-05
Just ignore them. Obviously you don't have any problems not being able to run PhotoShop, AutoCAD etc natively so does it really matter for most users that these applications aren't available for Linux?

For most commercial applications there are open source alternatives that are just as good.

---

### Post by DigitalDuality on 2009-06-05
d

---

### Post by DeadSuperHero on 2009-06-05
I'll bet your friend uses OS2\Warp. What a stud.

---

### Post by hansdown on 2009-06-05
Take comfort in remaining silent compnut41.

You may someday be able to help your buddy with problems that his system may encounter.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by Tibuda on 2009-06-06
And remember this:

[QUOTE="Mark Shuttleworth"][URL="https://wiki.ubuntu.com/MeetingLogs/openweekJaunty/AskMark"]we need to make a success of our own platform on our own terms
if Linux is just another way to run Windows apps, we can't win
OS/2 tried that
[/URL][/QUOTE]

---

### Post by compnut41 on 2009-06-06
> **Mr. Psychopath said:**
> I'll bet your friend uses OS2\Warp. What a stud.

Widows seven Beta actualy

---

### Post by albinootje on 2009-06-06
> **compnut41 said:**
> I have this friend who has gone down the rabbit hole of windows vista and windows 7 

Perhaps you can point them to some articles where navy submarines had to wait for MS-Windows problems :)

And ask him why almost all the new intel based netbooks come pre-installed with that obsolete (and insecure) OS called XP.

For the rest just ignore him about this kind of silly OS-debate, make friends with other Linux users, and do things that make yourself and others happy.

---

### Post by albinootje on 2009-06-06
> **compnut41 said:**
> Widows seven Beta actualy

Ah, the Microsoft Windows 7 free-of-charge trial version to let the customers forget the Vista disaster, and have them locked-in before the real nr. 7 cash flows into Microsoft pockets again.

Will Vista users get 7 for free when it comes out ? Or will they get a free XP downgrade instead ?

---

### Post by Delever on 2009-06-06
Tell your friend that wine project is basically what he suggested - ton of windows DLLs rewritten for Linux.

When programmer writes a C program, he can write it in such way that it compiles to DLL for windows, for linux, and also for other systems. Those windows DLLs are simply written ONLY for windows. We have our own in Linux.

---

### Post by forrestcupp on 2009-06-06
> **Delever said:**
> Tell your friend that wine project is basically what he suggested - ton of windows DLLs rewritten for Linux.

When programmer writes a C program, he can write it in such way that it compiles to DLL for windows, for linux, and also for other systems. Those windows DLLs are simply written ONLY for windows. We have our own in Linux.

You beat me to it.  That's exactly what Wine is.  The only thing about it is that you can't expect them to work miracles.  It took them almost 16 years to get to version 1.0.  Reverse engineering the inner workings of a proprietary operating system is not an easy task that can just be done quickly.

They've done a great job getting Wine as compatible as it is with what they've had to work with.

---

### Post by 3rdalbum on 2009-06-06
It's called Winelib.

But you don't even need to link against Winelib. Any program written with a view to portability will run with Wine. That's why you can run the Windows versions of Firefox, Gimp, Blender etc perfectly in Wine. You can even run the Windows versions of some open-source games perfectly in Wine.

---

### Post by Mohamedzv2 on 2009-06-06
WINE tries to make its own DLLs that lets Linux run windows software

---

