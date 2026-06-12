---
title: "Interesting read: impact of Windows Vista"
date: 2006-12-24
forum: The Cafe
---

### Post by ubuntu27 on 2006-12-24
I have received a interesting mail from Ubuntu Development Mailing List.
Let me copy and paste.

         From:       K.S 	
  
	to		 [email]ubuntu-devel-discuss@lists.ubuntu.com[/email]	 
	date		Dec 23, 2006 3:57 PM	 
	subject	       Concerns about Windows Vista implications for Linux/Ubuntu	 
	mailed-by		lists.ubuntu.com


Hi,

You may have read this already and it might be old news, but what do
you think? This is being discussed on EFFI's (Electronic Frontier
Foundation Finland) list currently. I haven't double checked &
verified any of the references of the article and can not know for
sure if it is 100% true, but might worth be checking out if you
haven't done it already:

[http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.txt](http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.txt)

Particularly concerning detail can be read below:
"Elimination of Open-source Hardware Support"

Also "Denial-of-Service via Driver Revocation"

In other words, the article claims that first of all, to meet the
Vista requirements, hardware vendors must not release open source
drivers and they must keep anything else about specs confidential but
the marketing specifications listed on their web sites for consumers.
And secondly in the case they do release the info of some particular
card or chip type, Microsoft can at any time disable the card (when
next automatical update occurs) which has Linux support or which is
being used in Linux with reverse engineered drivers done for Linux
which essentially removes the card from market which could mean (if
the above analysis is true at all) hard time (even harder than now) to
get any support for any Windows compatible hardware for Linux,
especially if the hardware vendors get scared and stop releasing even
binary drivers for Linux not to speak of yet alone the open source
drivers. I hope the reality doesn't turn out to be this bad.

Anyhow the question is, how is Linux and particularly Ubuntu (which
somewhat prefers open source drivers) going to deal with the driver
issue if the vendors will increasingly be closed and further away from
openness and Linux thanks to the obviously deliberate "Windows-only"
locking implemented by Microsoft?

Best Regards,
KS
---

--
Ubuntu-devel-discuss mailing list
[email]Ubuntu-devel-discuss@lists.ubuntu.com[/email]
Modify settings or unsubscribe at: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss)

---

### Post by towsonu2003 on 2006-12-24
do we have anyone who was around when XP was released with the "approved XP drivers" feature? (what was the name of that thing?)

were similar speculations around when XP was released? and what happened after XP was released? did linux suffer?

this is not polemic, I'm really asking :mrgreen:

---

### Post by woedend on 2006-12-24
ah, its just a load of crap.  microsoft knows better than to try that, and has no good reason to.  and perhaps they are only referring to drivers shipped in by default.  
I can see a lot of companies telling MSOFT to shove it, and I seriously doubt that they would disable hardware because of this.

---

### Post by Tomosaur on 2006-12-24
Looks like Microsoft sees all computer hardware as 'Windows Peripherals'. I would argue that it would force a more radical approach to linux development, probably with people intentionally flouting 'the law' to get things done. Linux developers really aren't the type to just call it a day, so I wouldn't expect this to have any effect other than to make the devs even more determined.

As for Windows' ability to 'disable' cards - well that's irrelevant if the user never boots back into Windows again - they'd never know.

---

### Post by chaosgeisterchen on 2006-12-24
This will only drive the people away from Windows I assume. Microsoft cannot force hardware vendors to stop supporting open source. If - for instance - Intel releases an open source driver and the next day, millions of business computers are shut down by Microsoft, they can close down their company to come up for all the lost turnover the companies suffered.

---

### Post by JAPrufrock on 2006-12-24
Windows is always walking a fine line between playing hardball with vendors/consumers and fending off anti-trust lawsuits. MS will have to play with a softer ball if a less conservative government is elected in the next US presidential and congressional elections.

---

### Post by bonzodog on 2006-12-24
No, I don't think there is any truth to this - Bill gates himself has admitted that Open Source is the way forward for Software development. 

Also, one of the central reasons for the MS/Novell deal was interoperability - making Hardware vendors stop production of Open Source drivers would go against the whole thing and Novell would jump on MS like rabid dogs. 

AND, it would start yet more massive EU court cases, as it also breaks half a dozen EU trading laws, and they would be forced to shut down an entire section of the world market, prevented from trading inside the EU.

---

### Post by ubuntu27 on 2006-12-25
a reply to that mail from Dev-list:


I had written a rather long response in which I had asserted that you
were misinterpreting the meaning of that section, which I believed was
saying that open source drivers would preclude the effectiveness of the
HFS. I do not believe this to be true, and this is also very different
from disallowing open source drivers altogether. However, upon carefully
reading it again I noticed that the author did assert that the
specification required that "the operational details of
the device be kept confidential". If this is true, it would cause
problems for Linux drivers. However, I cannot find the source for this
assumption, and the author merely states "a number of
the sources used were non-public". I am disinclined to believe such a
bold statement without any evidence. It would certainly be a drastic
change in the behaviour of companies like Intel to suddenly stop giving
out specs and releasing open source drivers.

I also think that the author is exaggerating many issues, and creating a
false impression of what will happen, probably because it seems that
many of the sources from Microsoft are exaggerating many issues and
creating a false impression of what will happen. Considering the speed
at which protections have been broken in the past, if drivers or devices
which are breached will have their signatures revoked as Microsoft
asserts, Vista users will have a very unpleasant experience. Microsoft
would destroy themselves if they were to revoke drivers and punish users
in the way that they describe. If such absurdly draconian measures were
enforced, consumers simply wouldn't buy premium content, and the market
for "non-participating devices" would be large enough that manufacturers
would continue to make them. However, I must say that I am disappointed
at the author's attempt to link this to "homeland security" and claims
that the protection will endanger lives, tactics which even Microsoft
did not use.

Most of this discussion probably belongs on sounder instead of
devel-discuss, unless I am mistaken in my understanding of the
devel/devel-discuss split, which seems to have caused considerable
confusion as the the proper lists.

Yours,
C.E

---

### Post by mushroom on 2006-12-25
Microsoft trying to pull something like that would end up making them more monopolistic than they already are. Though the result of litigation would be a slap on the wrist for such a giant, deliberately disallowing the use of a piece of hardware because it supports other OSes would be really dangerous, even for MS.

---

