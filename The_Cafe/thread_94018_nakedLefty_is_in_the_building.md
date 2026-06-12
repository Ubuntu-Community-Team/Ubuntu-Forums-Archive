---
title: "nakedLefty is in the building"
date: 2005-11-23
forum: The Cafe
---

### Post by nakedLefty on 2005-11-23
Hi just wanted to pop by and let every single one of you Ubuntu users know that nakedLefty has joined the forum, and that I am very much looking forward to asking all of you for help in matters concerning Unbuntu and Linux in general.

I might also be persuaded to talk about other stuff :)

Good to be here... hope you all don't mind me being here :)

/nakedLefty

---

### Post by 23meg on 2005-11-23
Welcome to the Building; enjoy your stay and don't hesitate to ask for help; that's why we're all here, to help each other.

---

### Post by nakedLefty on 2005-11-23
Well now that you mention it... :) I'm experiencing a "crc error .. system halted"-problem.

It occured on the 2nd boot up of Ubuntu after having updated the system with the new kernel. 

I am able to boot with the "old" kernel as there is entries for both in Grub... but keep getting the "crc error" if I don't do anything during boot.

I tried to run the memtest from Grub too... and quit it after one full pass... thought that was enough, which didnt seem to reveal any trouble with my memory.

please help :)

/nL

---

### Post by Stormy Eyes on 2005-11-23
Remove the new kernel with **apt-get remove**, do **apt-get update**, and try installing the new kernel again. You might have gotten a bad kernel.

---

### Post by nakedLefty on 2005-11-23
Okay will do... I was thinking it might be something like that... but with my lack of "exp" using Linux I thought it best to check with you nice people :) -- I'll keep you boys updated on the progress.

Wish me luck guys - I'm going in.

/nL

---

### Post by Pablo_Escobar on 2005-11-23
Welcome Lefty and happy posting :) 

PS. Just don't show the naked part in the Building, it can cause some terror :D

---

### Post by nakedLefty on 2005-11-23
hehe... well judging from our respective picture, I reckon that the majority of people in this forum would rather see my bits than mokey-boys bit... should it ever come to that. (which it hopefully won't... as I'm rather the shy type and rarely show my bits)

But thank you for the warm welcome Pablo

---

### Post by nakedLefty on 2005-11-23
hmm... I did the "apt-get remove linux-image-2.6.12-10-386" and it seemed to uninstall the packages it had installed this morning. And cleaned up nicely, and restored the /boot/grub/menu.lst to it's previous state.... and rebooted fine.

Now however, it doesn't seem to want to acknowldge that there's anything to update, neither in a xterm or using the "update manager" ?!?!

Any ideas on how to procede?
[oh and sorry about the spelling errors, english isn't my mother tounge]

Please advise red one?

/nL

---

### Post by Stormy Eyes on 2005-11-23
If there's nothing to update, then there's nothing to update. You could try installing the new kernel again, use the one you've got, or get the sources from kernel.org and build it yourself. Do you have a reason for wanting to upgrade your kernel?

---

### Post by nakedLefty on 2005-11-23
Hey Stormy, 

Well it's not like a dying wish that I should have the 2.6.12.10 if I remember correctly, it just struck me as being odd, that I installed it this morning... it turned out not really to work, I uninstalled it and removed the packages (?!? i think), and now it's not in "Ubuntu auto update" thing anymore... Have they "retractet" it causes it was causing problems or ?

Also I mean I think it said something about security updates in the details when I looked at it this morning... but as you say, if it doesn't list any updates, then there's no reason to try and find something to update... just odd it was there this morning, and now it's gone :) [wax on - wax off]

/nL

---

### Post by Stormy Eyes on 2005-11-23
[QUOTE=nakedLefty]Also I mean I think it said something about security updates in the details when I looked at it this morning... but as you say, if it doesn't list any updates, then there's no reason to try and find something to update... just odd it was there this morning, and now it's gone :) [wax on - wax off][/QUOTE]

Maybe the kernel *was* defective, then. I'm using Dapper and haven't upgraded in a while, so I wouldn't know.

---

### Post by nakedLefty on 2005-11-23
Okay.  well thanks for helping me get rid of the bad "seed" I had installed.

---

### Post by Stormy Eyes on 2005-11-23
[QUOTE=nakedLefty]Okay.  well thanks for helping me get rid of the bad "seed" I had installed.[/QUOTE]

No problem.

---

### Post by erikpiper on 2005-11-23
Wait- you were trying to install a 386 kernel? Mabe I am reading this wrong...

Anything above a Pentium pro is a 686 (p2 p3 p4 AMD)
Amd optimized kernels are k7 (I believe...)
And I have no experience with 64 bit procs

Welcome!

---

### Post by nakedLefty on 2005-11-23
Hey ePiper, no or well I don't know, I just had that cute little "update available" icon in the "task bar", and installed all of the updates that were available.

I have no idea really if it was a 3x86 sepcific kernel... and would really think weird stuff about the Ubuntu team if they would "suggest" that as a "update" in that manner. Then again, I could haven maybe been a little more reading-like rather than mouse-button-tricker-happy-camper-like.

At any rate, it's gone now and my system is running as it was before installing that package(s).

/nL

---

