---
title: "Should xp stay or should it go now."
date: 2009-08-13
forum: Testimonials &amp; Experiences
---

### Post by vedek on 2009-08-13
Hi guys,
 
I made an earlier post about my online exploits and i want to further add to my full experience of ubuntu.
 
 
I had 2 pc's and i backed all up and got ready to move to just one my netbook, but i accidentally deleted my data or else it didn't back up correctly so now i have a empty pc, now i really like ubuntu, i have had a few kinks which i posted but didn't get replied to. but i eventually manage to fix them myself, i now have xp sitting on my drive taking up 70Gigs of space and being honest i dont use it hardly ever, i have kinda been keeping xp on for the just incase scenario of ubuntu not working but the more i get used to it the more unlikely i realise that to be, so do i throw away all vestiages of windows or do i keep it for the highly unlikely event of ubuntu failure.
 
 
part of me knows that i have learnt enough to cope without windows but the leap isn't easy,

---

### Post by fela on 2009-08-13
Yes, if you feel comfortable with using Linux, then I say get rid of windows forever! It's best though if you have an XP installation disk or recovery partition until you feel 100% that you can live without windows.

You can also just force yourself to not even think about windows. Just get rid of it and remove everything windows from your brain. If you only think about using Linux then you're sure to fix 'most all of your problems with it (if you have any, that is).

So yeah, get rid of windows! :)

---

### Post by adempewolff on 2009-08-13
If you have the hardware for virtualization (modern processor, 2gb memory, etc), kill it and install it in VirtualBox with like 15GB of hd space allocated to it, it probably won't take up morethat 10GB unless you install programs, and then if you ever need it to run a proprietary program/hardware/etc you don't have to reboot.

---

### Post by JohnFH on 2009-08-13
Why is the leap not easy?  You've already done it.  What 'just-in-case' scenario would there be for ubuntu to die completely that you couldn't recover from?  

I made the switch fairly quickly - went from first discovering Ubuntu to Ubuntu-only household within a few months.  5 machines (2 desktops, laptop, netbook and media server) all running Ubuntu and the only sign of Windows is in a single virtual hard disk that hasn't been turned on this year.

---

### Post by fela on 2009-08-13
Well I used Linux natively before I even ran windows in my house. The first OS was MacOS, then OSX, then I got my own computer and started running Linux on it (windows still hadn't even entered my brain yet). I then heard about this concept of the 'windows' OS, I was determined to try it out. I got a copy of XP, installed it on my computer and immediately had to go to the bathroom to vomit. The UI looked like it had been drawn by a six year old kid in primary school!

Then I persevered with it, and got a few programs running.

Obviously I kept a Linux partition on my disk all along, good thing aswell because I went back to Linux in about 2 weeks. Which is quite short for me as when I try things out I like to persevere with them - but in the case of windows persevering didn't seem to make it any better, worse actually.

But then I built a gaming rig - and subsequently couldn't find any good games for Linux (apart from minesweeper of course :P).

So I installed the new 'windows VISTA' on it, then quickly uninstalled it as, although the UI might look quite alot nicer than XP the system sure isn't. So I installed XP back onto my old vista partition and got a few games for that, and here I am. One XFS Linux partition, one NTFS Windows XP partition.

EDIT: just wanna make clear that I use Linux pretty much ALL of the time, last time I booted windows was...I forget, haha!

Am I rare in that I used Linux before I tried windows?

---

### Post by fennec_fox on 2009-08-13
If you haven't turned it on in awhile and you can't think of any reason to keep it then I'd say you're wasting space. I kept windows installed for awhile as a security blanket but, after awhile I realized it was completely unnecessary. I booted it up to check and found antivirus, antispyware, windows update and everything out of date by months and when I looked at the programs I realized everything I had installed I already had better on linux or had installed in wine. 

You said you don't use it so I think you're fairly safe on getting rid of it.

Do you want free space or space that you just don't ever use? If you have a ton of HD space then it's probably not even worth considering but, it sounds like it's just unused space. 

I think you are certainly rare to have used linux before windows haha but, great job on that. You got an entirely different perspective than most people and that's a good thing. Many users (myself included when I first started using linux) are locked into the windows desktop and have trouble perceiving anything else. It's kind of funny that you said the xp interface looks like a little kid drew it. I had a hard time adjusting to any of the linux interfaces but, now that I have I completely agree haha. 

Great to hear a different perspective; even if you ended up thinking windows was great I'd still be glad to hear a different perspective.

---

### Post by vedek on 2009-08-13
> **JohnFH said:**
> Why is the leap not easy? You've already done it. What 'just-in-case' scenario would there be for ubuntu to die completely that you couldn't recover from? 
 
You do make a good point actually, i suppose i am just making excuses when i know that it makes sense to go all out. will all my files deleted nothing is really holding me to keep the xp partition so i guess tonight its format time again or is there another way to do it

---

### Post by adempewolff on 2009-08-13
use gparted to delete the windows partition and then resize the Ubuntu (or seperate /home partiton, which is usually a good idea) partition over it.  unless you want to install everything from scratch, which sometimes isn't a bad idea.  There is never a better time to get your entire setp exactly how you want it than when you haven't installed anything important/put many files on it yet.

I would recommend trying out virtualbox though.  Even though you will probably rarely need to use windows (god knows I boot into it a few times a month at most), being able to easily start it up without restarting will erase any tiny regrets you might have ever had on removing windows.


edit: and if you don't have your xp installation media (I don't think you mentioned if you did), there are ways to convert an existing xp partition into a virtualized one.  I would resize the partition to much smaller before doing this though.

---

### Post by HappyFeet on 2009-08-13
> **vedek said:**
> so i guess tonight its format time again or is there another way to do it

You could use the gparted live cd (or ubuntu live cd) to remove the xp partition, then resize ubuntu's partition. But then you will have to reinstall grub from an ubuntu live cd.

If you are not comfortable resizing partitions, and what not, a reinstall will do the trick.

---

### Post by fela on 2009-08-13
> **fennec_fox said:**
> I think you are certainly rare to have used linux before windows haha but, great job on that. You got an entirely different perspective than most people and that's a good thing. Many users (myself included when I first started using linux) are locked into the windows desktop and have trouble perceiving anything else. It's kind of funny that you said the xp interface looks like a little kid drew it. I had a hard time adjusting to any of the linux interfaces but, now that I have I completely agree haha. 

Great to hear a different perspective; even if you ended up thinking windows was great I'd still be glad to hear a different perspective.

Well there really isn't any one 'Linux interface' - as it's not designed by any one body. Linux is made by the users, for the users, in contrast to by the company, for the users as in the case of MS windows.

BTW, what made you think I ended up thinking Windows was great? I hate windows! I only use it for gaming right now (I play games when my friends come round only). Well, I only keep the partition on there in case I need to do any video editing or something in the future, or maybe some obscure photoshop thingy. I wouldn't keep a partition wasting space just for games.

---

### Post by vedek on 2009-08-14
windows finally got the boot last night. i am going to add a discovery blog type thing problems that i encounter and fixes that i have got. Also programs that i download and how i got them to work, plus it will also have my work from college i am taking a linux+ course.

---

### Post by fela on 2009-08-14
> **vedek said:**
> windows finally got the boot last night. i am going to add a discovery blog type thing problems that i encounter and fixes that i have got. Also programs that i download and how i got them to work, plus it will also have my work from college i am taking a linux+ course.

Great :)

I hope all goes well for you on Ubuntu. If you get a problem, don't just go back to windows as I have seen alot of people do. Persevere at it and you'll end up loving Ubuntu much more than Windows. :guitar:

---

### Post by vedek on 2009-08-14
i will only leave linux if it doesn't do what i need, and linux provides me with everything i need, i post the issues i have in the forum because not only will it help my problem but perhaps if someone is having the same problem then it will help them as well. I consider myself to be a techie i have been using computers since 3.1 and dispite the gaping differences that microsoft would have you believe there are more than a few similarities, i love linux because it is challanging it is expanding my skills and abilities and that why i love linux because i will be technically better once i get to know it.

plus i am as stubborn as a mule i don't give up i fix it as you might have seen on my requests for help i normally fix it within a few hours, which is a problem that i feel needs fixing we need to persuade people to look for there own fixes, they might think that we are being harsh and unsuportive but in the long run they might just thank us.


spiel over

---

### Post by fennec_fox on 2009-08-14
> **fela said:**
> Well there really isn't any one 'Linux interface' - as it's not designed by any one body. Linux is made by the users, for the users, in contrast to by the company, for the users as in the case of MS windows.

BTW, what made you think I ended up thinking Windows was great? I hate windows! I only use it for gaming right now (I play games when my friends come round only). Well, I only keep the partition on there in case I need to do any video editing or something in the future, or maybe some obscure photoshop thingy. I wouldn't keep a partition wasting space just for games.

I'm sorry. I didn't word my post as I should have. What I meant was it took me awhile to get used to the idea that there wasn't really an individual interface. Anything can be customized however you want.

Where I really messed up was when I said the windows things. What I meant to say was that even if you actually somehow ended up thinking windows was great it was good to hear a different perspective. I understood you really disliked windows from your first post.

---

### Post by fela on 2009-08-14
> **fennec_fox said:**
> i'm sorry. I didn't word my post as i should have. What i meant was it took me awhile to get used to the idea that there wasn't really an individual interface. Anything can be customized however you want.

Where i really messed up was when i said the windows things. What i meant to say was that even if you actually somehow ended up thinking windows was great it was good to hear a different perspective. I understood you really disliked windows from your first post.

ok! :p

---

### Post by vedek on 2009-08-14
well with windows out the door and a broken disc off to redmond:P i have to ask myself was the transition as smooth as it was ment to be hell yeah, is it difficult installing everything back to the ubuntu i had installed up to yesterday nope,

do i regret sending windows completely packing yeah for a min, but then i realise that i am thinking stupid thoughts and start the arduous 195 file update. ;) 

10mins later i am staring at a new desktop and realize just how many files i want to download and that i need to configure to get ubuntu back to the way it was - should take another 10mins i think :P

---

### Post by Tamlynmac on 2009-08-14
[> ]("http://ubuntuforums.org/member.php?u=877195")[vedek]("http://ubuntuforums.org/member.php?u=877195")
			 		   		 		 		windows finally got the boot last night. i am going to add a discovery blog type thing problems that i encounter and fixes that i have got.

It's just that nostalgic letting go syndrome. Fear not. I've been using Ubuntu exclusively >3 years and have no desire to ever use Window again.

Might I suggest you get involved in a FOSS project of interest and not only join the community but become a proactive member. I've contributed to a couple of FOSS projects, as I'm not in a position to help any other way. The feeling of knowing I contributed is great and adds a new dimension to being part of the community.

There are many ways to get involved besides $$ (beta testing, etc). It's a great way to give back to the community and assure/enhance the future of FOSS.

Good Luck and I hope your Ubuntu experience emulates or eclipses my own.

---

### Post by Support the 2nd on 2009-08-15
I have wanted to get rid of my XP partition, but as much as I might get flamed for this....Gimp is garbage.  I need Photoshop and Illustrator.  But I have stumbled on a few times that XP came in handy...and it involved screwing up my screen resolution/driver file (xorg?) where my comp booted to a black screen and that was it.  I don't recall even being able to get a command line.  It was really nice being able to boot over and post to the forums for help.  :)
I am still not well versed in Linux, but I use it as default for everything but graphics.

---

### Post by HappyFeet on 2009-08-15
I must be getting old, because all the disagreements I've seen,I don't understand.

---

### Post by HappyFeet on 2009-08-15
> **Support the 2nd said:**
> Gimp is garbage.

Then you must be one of 1% that actually uses 5% of what photoshop has to offer. Please, it's getting old. Why is it that every person is all of a sudden photoshop expert? Are people that desperate to lie and use windows as if it was good?

---

### Post by Support the 2nd on 2009-08-15
> **HappyFeet said:**
> Then you must be one of 1% that actually uses 5% of what photoshop has to offer. Please, it's getting old. Why is it that every person is all of a sudden photoshop expert? Are people that desperate to lie and use windows as if it was good?

You are right.  I am a liar and you are better than me.

Why is it that all of the sudden, armatures think everyone else is an armature?

---

### Post by solwic on 2009-08-15
> **Support the 2nd said:**
> You are right.  I am a liar and you are better than me.

Why is it that all of the sudden, armatures think everyone else is an armature?

Believe you were going for "amateur" there, and HappyFeet has a point.  For nearly all purposes, GIMP does everything Photoshop does, if a bit differently.  Personally, I think if you're one of those using the few features that Photoshop has and GIMP doesn't, then you ought to know how to have both Windows and Ubuntu on the same machine.  You can even run Windows in a VM, inside Ubuntu, and then voila!  Everybody wins.  :)

But hey, use what works for you, chief.  We're not twisting your arm, here.  :)

---

### Post by Dullstar on 2009-08-15
I had once heard that Linux was practically a nightmare in the land of user-friendliness, but I was so fed up with Windows that I used Wubi.  I pretty much figured out GNOME in a day or two.  Now I realize how clucky the XP interface is.

For those of you who still think that Linux is not user friendly, try Ubuntu with GNOME.  If you can be bothered to do things differently, it'll take a day to learn.

---

