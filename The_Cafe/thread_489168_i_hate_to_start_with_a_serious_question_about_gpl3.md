---
title: "i hate to start with a serious question about gpl3 but..."
date: 2007-07-01
forum: The Cafe
---

### Post by noob4eva on 2007-07-01
one thing i've always wondered about the gpl (keep in mind i've released software i wrote under the gpl, i've been familiar with it for years and read it more than once) is whether you can release UNmodified binaries of programs without the source.

the consensus (regardless of the actual license) has always seemed to be "yes, absolutely- sure."

of course, this applies to ubuntu in many ways. i was happy to get an ubuntu cd- an entire cd, way more than i can download (much of the world still uses dialup, and although usa is largely highspeed, i'm not.) in anything close to a reasonable amount of time, all for free- mail ordered. great.

no source, that's okay. i can make copies of my (now very old) ubuntu cd, and i can give them to friends, and they can make copies, and so on. i like my old copy of ubuntu. it's no longer supported, but it requires a lot less ram than newer versions. a lot less.

i've been defending the gpl3 for over an hour- this is not gpl3 fud, this is a real concern. in fact i just spent half an hour reading the license, you can too at: [http://www.fsf.org/licensing/licenses/gpl.html](http://www.fsf.org/licensing/licenses/gpl.html)

section 9 really bothers me, it renews my curiousity about distributing binaries without source (remember source is usually bigger than the binaries.) and if ubuntu was released under gpl3, i couldn't do anything with it- i couldn't give it to friends, because, i just can't afford to download the source, it would take a week or more of just not having internet access. the source doesn't come with the disc.

if i've made any mistakes here, please correct me- i want to be wrong about this. i believe, that in gpl2, you could distribute UNmodified binaries without source, it was no big deal. before i talk more, i'll leave this snippet from the newer gpl faq at the fsf page:

> **I downloaded just the binary from the net. If I distribute copies, do I have to get the source and distribute that too?**

    Yes. The general rule is, if you distribute binaries, you must distribute the complete corresponding source code too. The exception for the case where you received a written offer for source code is quite limited.

[http://www.fsf.org/licensing/licenses/gpl-faq.html#TOCUnchangedJustBinary](http://www.fsf.org/licensing/licenses/gpl-faq.html#TOCUnchangedJustBinary)

so if i download a 10mb vlc player (windows and linux, gpl) then i have to get the (probably 20mb) source also, for a total of 30mb. that's hours of downloading. doesn't make it very easy for me to promote open source, even if anyone can get this stuff online, if they look. 

there's an exception for people seeding torrents and running ftp servers. that's not me, however. and i'll still be able to copy the ubuntu cd and give it to friends- but this sort of thing seems to be a lot more restricted under the gpl3. i could be wrong. i hope so, and i've done hours of reading now, none of which has resolved my confusion. (nor have a couple years of experience with gpl2.) 

this also potentially affects future copies of openoffice, which i just found a windows version of on my year-old copy of ubuntu. i didn't get the source. 

sorry for the long post. i would have made it shorter if i really knew how. "just do" - i've tried that.

i also tried to find the best place to post this. i won't mind if it's moved, i only *hope* i get some reply. really, i can redistribute lots of (unmodified) gpl software to people, provided that i'm wrong about this. if i'm right, i really can't redistribute much of anything at all. i'd hate that, it would make free software almost as useless to me as "proprietary os" is :( almost.

---

### Post by a12ctic on 2007-07-01
Unless someone asks for the source I doubt it'd be a problem.

---

### Post by H.E. Pennypacker on 2007-07-01
Dude, don't worry about.  Just hand out your CDs.  The GLPv3, I am sure, does not have any intentions of stopping people like you.  I am sure it has a problem with malicious people, but not with people who don't have easy means of sharing the license, especially since it is widely available.  Tell your friends to read the license if they want online.

---

### Post by needtolookatascreenshot on 2007-07-01
These provisions only apply if you distribute the software, not if you simply use it:

Downloading only binaries to your computer to use the software: No problem.

Distributing only binaries without making the source available: Problem.

---

### Post by saulgoode on 2007-07-01
It is an intriguing question. If you look at the fine print on a Ship-it package, you will see a "written offer" describing how the source code can be obtained. If you make an unmodified copy of that Ship-it CD and give it to someone else, you would be fulfilling the GPL license requirements (both V2 and V3) if you included that information with your copy (either written on the CD or on a slip of paper).

If instead you download an ISO image of the same CD, burn a copy, and give that copy to someone, you should have to provide them a similar "written offer" for the source -- and the FSF seems to be saying that you have to be the one providing the source (if requested). To be honest, I disagree with this stance (assuming I am understanding it correctly). You might have to "insure" that a copy of the source is available and, while technically you can't insure the existence of Ubuntu repositories (for 3 years), as long as you accept the responsibility of providing the source should something happen to the Ubuntu's servers, I should consider that sufficient. The worst (and very unlikely) case is that the Ubuntu sources became unavailable, you would be found in violation of the license and prevented from providing further copies.

TUCA

---

### Post by koenn on 2007-07-01
I too think that this occasional giving out copies is OK. 
You might be required to provide source code if requested, but you can charge money in return to cover your costs,  so you could- if you absolutely want to comply with the letter of the license -  pay someone else (with broadband :) ) to download source code and burn it on CD / DVD, then get your money back from those who want you to deliver the source code. If you offer a download link as a free alternative, I doubt many people will bother you for the source. 
You can also claim that the source is available "from the cd" through the packet manager (source packages). 
In reality, I don't think anyone's interested in prohibiting occasional, non-commercial redistribution of unmodified binaries.

---

### Post by ssam on 2007-07-01
> Source code for ubuntu can be downloaded from archive.ubuntu.com or can be ordered from Canonical at the cost of the media and shipping
from the back of a dapper shipit CD.

I think it would be fair for you to say

"Source code for ubuntu can be ordered from me at the cost of the media and shipping"

if anyone takes up that request, you just order a copy of the source code from canonical, and charge those costs to the person you are giving it too. the only case this would not cover would be if canonical disappeared (this is unlikely as there is a fund to keep it going even mark shutleworth leaves).

In gpl infringement cases there is usually an order for the infringer to comply or cease distribution. only if you refused to comply or cease distribution would it get taken any further.

---

### Post by saulgoode on 2007-07-01
I was wrong about the FSF saying that you need to provide the source code yourself. Section 3c of the GPL2 allows that, *for non-commercial distribution* of unmodified copies, it is sufficient to merely provide the information about source code availability as it was given to you. It is only if you intended to market the software that you need to provide the code yourself (assuming you are asked).

> 3.  You may copy and distribute the Program (or a work based on it, under Section 2) in object code or executable form under the terms of Sections 1 and 2 above provided that you also do one of the following:

    a) ...
    b) ...
    c) Accompany it with the information you received as to the offer to distribute corresponding source code. (This alternative is allowed only for noncommercial distribution and only if you received the program in object code or executable form with such an offer, in accord with Subsection b above.) 

---

### Post by noob4eva on 2007-07-01
saul, you're a genius. (the rest of you are absolutely wonderful, too) of course i'm talking about the future, ie gpl3, but gpl3, section 6 seems to cover (in similar words) what you spotted in version 2, section 3:

> You may convey a covered work in object code form under the terms of sections 4 and 5, provided that you also convey the machine-readable Corresponding Source under the terms of this License, in one of these ways:

    * a) ...
    * b) [this subsection of the gpl3 covers koenns suggestion]
    * c) **Convey individual copies of the object code with a copy of the written offer to provide the Corresponding Source. This alternative is allowed only occasionally and noncommercially, and only if you received the object code with such an offer, in accord with subsection 6b.**
    * d) [edit for ease of reading...] You need not require recipients to copy the Corresponding Source along with the object code. If the place to copy the object code is a network server, the Corresponding Source may be on a different server **(operated by you or a third party)** that supports equivalent copying facilities, provided you maintain clear directions next to the object code saying where to find the Corresponding Source. Regardless of what server hosts the Corresponding Source, you remain obligated to ensure that it is available for as long as needed to satisfy these requirements.

the really interesting things is, if the source falls off the internet (or you can't find it anymore) then **technically,** you are forbidden to distribute the software at all. 

and that's where a12ctic's and ssam's advice comes in. if someone complains that you're violating the gpl by offering free binary copies (as it's all you have) then you'd technically have to start getting source or stop givng out that version. and i suppose that's a very big if in the first place.

and i was only talking about non-commercial distribution. if i was making any money from it at all, i'd be forced to comply, and i don't mind that- that's business, and the customers would cover the costs.

thanks everybody.

---

### Post by Extreme Coder on 2007-07-01
BTW, I just want to know which exact Ubuntu version are you using, because every newer version of ubuntu was faster for me, not slow.

---

### Post by noob4eva on 2007-07-04
breezy, which seems to want half as much ram as the later versions, right? i would have switched to xubuntu, but someone that tried it (all the people i know are looking for lighter distros) said it wasn't that much faster.

---

### Post by jiminycricket on 2007-07-04
Peer to Peer like Bittorrent also gains an exception in GPLv3, all you need to do is point to the source.

---

