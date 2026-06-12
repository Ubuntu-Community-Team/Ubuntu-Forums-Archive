---
title: "Sharing Debian = Banned from Uni network"
date: 2009-01-16
forum: The Cafe
---

### Post by dbbolton on 2009-01-16
A student (whom I know personally) at [West Virginia University]("http://www.wvu.edu") recently had his internet privileges revoked for sharing Debian through Vuze. The reason given was "sharing copyright material".  My question is this: was this revocation justified? 

If memory serves, item 1 of the DFSG is Free Redistribution.

For those so inclined, here is the AUP to which all University students must agree to earn internet privileges: [http://www.resnet.wvu.edu/policy/resnet.html](http://www.resnet.wvu.edu/policy/resnet.html)

You may notice that the use file sharing software is discouraged but not forbidden. None of the reasons for which the University reserves the right to revoke internet access seems to have been violated to me.

---

### Post by saulgoode on 2009-01-16
**ALL** of the packages in Debian Main permit re-distribution. There are some packages in Non-free and Contrib which do not permit re-distribution (technically Non-free and Contrib are not part of Debian).

---

### Post by Grant A. on 2009-01-16
> **dbbolton said:**
> "sharing copyright material".

How dare he steal from a GPL project. :lol:

---

### Post by Polygon on 2009-01-16
go to the person in charge of the network or the administration or whatever and present your case. Im sure at least the techies should understand

---

### Post by lykwydchykyn on 2009-01-16
Technically speaking, Debian is copyrighted. It's distribution license allows you to distribute it freely, with a few stipulations.  But it is still copyrighted.

Of course, if the school is being that literal, then technically the only files you can share would be public domain.  As far as I understand US law, anything you write is copyrighted until you say otherwise, so even sharing original works could constitute sharing "copyrighted material". 

Of course, technically his machine is configured as a server, which seems to be against the policy.

---

### Post by dbbolton on 2009-01-16
> **saulgoode said:**
> **ALL** of the packages in Debian Main permit re-distribution. There are some packages in Non-free and Contrib which do not permit re-distribution (technically Non-free and Contrib are not part of Debian).
I'm pretty sure that the Debian CD images contain nothing but free software. I know that the non-free repositories are disabled by default.

> **lykwydchykyn said:**
> Technically speaking, Debian is copyrighted. It's distribution license allows you to distribute it freely, with a few stipulations. But it is still copyrighted.

Of course, if the school is being that literal, then technically the only files you can share would be public domain. As far as I understand US law, anything you write is copyrighted until you say otherwise, so even sharing original works could constitute sharing "copyrighted material". 

Of course, technically his machine is configured as a server, which seems to be against the policy.


Under the list of reserved rights to revoke network access, "Violation of U.S. Copyright Law" is explicitly stated. I'm pretty sure that Debian's copyrights don't forbid redistribution. 

If they were banning him for using his computer as a server, then shouldn't that have been mentioned in the notice of why they revoked his network access?

---

### Post by lykwydchykyn on 2009-01-16
> **dbbolton said:**
> 
Under the list of reserved rights to revoke network access, "Violation of U.S. Copyright Law" is explicitly stated. I'm pretty sure that Debian's copyrights don't forbid redistribution. 


I was referring to this part at the end of that paragraph:
> 
or downloading/distributing copyrighted materials over computer networks (via peer-to-peer programs) or through other means. 

Most of the time they say "unauthorized copying", which would not be true of debian, but if they wanted to get technical, they could point to that section.  But by that same token, if they take it that literally you couldn't share anything but public domain materials.

> 
If they were banning him for using his computer as a server, then shouldn't that have been mentioned in the notice of why they revoked his network access?

I doubt that's the reason they were, though technically they could cite that.  What I think really happened is that someone who has no clue what Debian is saw him sharing an iso and made an assumption.

Of course, I don't know for sure if distributing a debian CD image obligates you to comply with the GPL requirements of offering source code for all GPL materials, etc.  If they have someone savvy with all that on staff, that may have been the reason.  But I'm cynical so I'm going to guess it was ignorance.

I'm not trying to defend the university here, I'm just taking a wild stab at answering your question.  I think he needs to appeal, bottom line.  I'd be curious to know what they say.

---

### Post by Bölvaður on 2009-01-16
give us a mail so we can share our thoughts (and keeping the mails clean)

---

### Post by saulgoode on 2009-01-16
> **dbbolton said:**
> I'm pretty sure that the Debian CD images contain nothing but free software. I know that the non-free repositories are disabled by default.
Understood. I wasn't sure if "sharing Debian" meant that the files being shared were Debian CD images.


> **lykwydchykyn said:**
> Of course, I don't know for sure if distributing a debian CD image obligates you to comply with the GPL requirements of offering source code for all GPL materials, etc. 
For non-commercial distribution of unmodified binaries, the GPL (version 2, ref. Section 3c) specifies that you need to inform the recipient how to obtain the source. Under such distribution conditions, the GPL does not specify that you must provide the source yourself.

---

### Post by dbbolton on 2009-01-16
> **Bölvaður said:**
> give us a mail so we can share our thoughts (and keeping the mails clean)
Do you mean, how can you contact the university?

---

### Post by bruce89 on 2009-01-16
My computer here is right now sharing copyrighted material - it's called the Web.

Anway, this is clearly another case of people being stupid / ignorant.

---

### Post by DaAlexMax on 2009-01-16
I wouldn't recommend anyone post any contact information for the university here, lest we have another one of [these](http://www.wkowtv.com/Global/story.asp?S=9682258&nav=menu1362_2) incidents on our hands again.

If people care that much, they can figure out the appropriate phone numbers themselves.

In any case, the university was just covering their tail, since most uses for bittorrent in college is downloading illegal copyright material.  It's better to 'shoot first and ask questions later' from a liability standpoint, because would you as the IT manager rather have one angry student or a possible lawsuit from the **AA on your hands?

---

### Post by Skripka on 2009-01-16
> **dbbolton said:**
> A student (whom I know personally) at [West Virginia University]("http://www.wvu.edu") recently had his internet privileges revoked for sharing Debian through Vuze. The reason given was "sharing copyright material".  My question is this: was this revocation justified? 

If memory serves, item 1 of the DFSG is Free Redistribution.

For those so inclined, here is the AUP to which all University students must agree to earn internet privileges: [http://www.resnet.wvu.edu/policy/resnet.html](http://www.resnet.wvu.edu/policy/resnet.html)

You may notice that the use file sharing software is discouraged but not forbidden. None of the reasons for which the University reserves the right to revoke internet access seems to have been violated to me.

Odds are, odds are your associate got "caught" one of 2 ways:


[LIST]
[*] Vuze uses some port/address for file sharing, and they were sniffing for the usage of that port--and hence he was presumed guilty.
[/LIST]
 
or


[LIST]
[*] His "sharing" of Debian was eating so much bandwidth, that the admins assumed that he was file-sharing (rightly), and further assumed that since 95% of file sharing is illegal copyrighted IP (assumed wrongly)-the killed his net access.
[/LIST]
 
You'll also note this line in the ToS:

*Network use that inhibits or interferes with the use of the network by others is prohibited. *

and

*Any network use that consumes large amounts of bandwidth and causes poor     network performance*

_***That alone is reason for his network access to be cut***_--since most educational institutions have massive bandwidth problems, especially at peak hours.  I love FOSS- but sharing FOSS, or mp3s, or videos, or whatever that prevents other users from academic work while at university, on uni computer networks-p*sses me off.  I've had many nights of yore that prevented me from being able to get things done as a result of networks being taken down by users' sharing and whatnot.

---

### Post by dbbolton on 2009-01-16
> **Skripka said:**
> Odds are, odds are your associate got "caught" one of 2 ways:


[LIST]
[*] Vuze uses some port/address for file sharing, and they were sniffing for the usage of that port--and hence he was presumed guilty.
[/LIST]
 
or


[LIST]
[*] His "sharing" of Debian was eating so much bandwidth, that the admins assumed that he was file-sharing (rightly), and further assumed that since 95% of file sharing is illegal copyrighted IP (assumed wrongly)-the killed his net access.
[/LIST]
 
You'll also note this line in the ToS:

*Network use that inhibits or interferes with the use of the network by others is prohibited. *

and

*Any network use that consumes large amounts of bandwidth and causes poor     network performance*

_***That alone is reason for his network access to be cut***_--since most educational institutions have massive bandwidth problems, especially at peak hours.  I love FOSS- but sharing FOSS, or mp3s, or videos, or whatever that prevents other users from academic work while at university, on uni computer networks-p*sses me off.  I've had many nights of yore that prevented me from being able to get things done as a result of networks being taken down by users' sharing and whatnot.
That would be fine, except they didn't mention any of these reason in the revocation of service notice. They said it was due to sharing copyrighted material. No other reason was given.

---

### Post by samjh on 2009-01-16
> **dbbolton said:**
> A student (whom I know personally) at [West Virginia University]("http://www.wvu.edu") recently had his internet privileges revoked for sharing Debian through Vuze. The reason given was "sharing copyright material".  My question is this: was this revocation justified? 

If memory serves, item 1 of the DFSG is Free Redistribution.

For those so inclined, here is the AUP to which all University students must agree to earn internet privileges: [http://www.resnet.wvu.edu/policy/resnet.html](http://www.resnet.wvu.edu/policy/resnet.html)

You may notice that the use file sharing software is discouraged but not forbidden. None of the reasons for which the University reserves the right to revoke internet access seems to have been violated to me.

Has your friend formally applied to have the access restored?

---

### Post by phrostbyte on 2009-01-16
> **lykwydchykyn said:**
> I was referring to this part at the end of that paragraph:

Most of the time they say "unauthorized copying", which would not be true of debian, but if they wanted to get technical, they could point to that section.  But by that same token, if they take it that literally you couldn't share anything but public domain materials.



I doubt that's the reason they were, though technically they could cite that.  What I think really happened is that someone who has no clue what Debian is saw him sharing an iso and made an assumption.

Of course, I don't know for sure if distributing a debian CD image obligates you to comply with the GPL requirements of offering source code for all GPL materials, etc.  If they have someone savvy with all that on staff, that may have been the reason.  But I'm cynical so I'm going to guess it was ignorance.

I'm not trying to defend the university here, I'm just taking a wild stab at answering your question.  I think he needs to appeal, bottom line.  I'd be curious to know what they say.

Well if you want to get really technical, then you basically can not use the university network to surf the Internet or check your e-mail at all, since mostly everything (Google, e-mails, etc.) are automatically copyrighted.\

Clearly what they mean is violating copyright.

---

### Post by MikeTheC on 2009-01-16
If they *know* he was sharing out a copy of Debian, and their truly only complaint was it's being copyrighted material, then perhaps the student in question could ask the university if the following *other* U.S. universities are also in violation of copyright law because they actively distribute copies of Debian:

[list][*] Michigan State University - ftp.egr.msu.edu
[*] Massachusetts Institute of Technology - debian.lcs.mit.edu
[*] Pennsylvania State University - carroll.aset.psu.edu
[*] University of Colorado at Denver - cudlug.cudenver.edu
[*] Stony Brook University - debian.ams.sunysb.edu
[*] University of Illinois at Urbana-Champagne - debian.cites.uiuc.edu
[*] Binghamton University - debian.cs.binghamton.edu
[*] University of Chicago - debian.uchicago.edu
[*] Georgia Tech - ftp.gtlib.gatech.edu
[*] University of Delaware - ftp.lug.udel.edu
[*] University of Notre Dame - ftp.ndlug.nd.edu
[*] University of Georgia - ftp.uga.edu
[*] University of Texas at Austin - ftp.utexas.edu
[*] Indiana University - ftp.uwsg.indiana.edu
[*] University of California at Berkeley - linux.csua.berkeley.edu
[*] Michigan Technological University - lug.mtu.edu
[*] Columbia University - mirror.cc.columbia.edu
[*] University of Wisconsin-Madison - mirror.cs.wisc.edu
[*] University of Idaho - mirror.its.uidaho.edu
[*] Rochester Institute of Technology - mirror.rit.edu
[*] Johns Hopkins University - mirrors.acm.jhu.edu
[*] University of Southern California - mirrors.usc.edu
[*] St. Mary's University - natasha.stmarytx.edu
[*] University of California at Santa Cruz - sluglug.ucsc.edu[/list]

---

### Post by Skripka on 2009-01-16
> **dbbolton said:**
> That would be fine, except they didn't mention any of these reason in the revocation of service notice. They said it was due to sharing copyrighted material. No other reason was given.

Fair enough.  But I'll put my money on they didn't bother investigating beyond either port # and or consistently large bandwidth usage...if prompted by the accused, they may change their reasoning, and rightfully so.  By appealing one verdict the person here basically admits being guilty on another clause of the ToS.

---

