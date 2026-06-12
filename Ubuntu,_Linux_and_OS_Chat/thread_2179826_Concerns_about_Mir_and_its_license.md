---
title: "Concerns about Mir and its license"
date: 2013-10-10
forum: Ubuntu, Linux and OS Chat
---

### Post by TamarinNOR on 2013-10-10
I have a concern about the license for Mir. While it is released under a free license, it seems that the license agreement to Canonical for Mir grants some unfair rights to the company. So if they want to, they can release the software under a proprietary license.

First of all, I don't really like this idea, but it does also sound fairly unfair for other parts of the community that involves in the development for  Mir. I get the feeling that it sounds like a BSD-license, only that no other that Canonical themselves (except the owners of the code contributed) can change the license to the code.

I do believe many in the community want to contribute to project that follows the ideology of free software to always remain free, and I do believe many might feel that work they put in to the project might be used on premises they won't like in the future. And is it any reason for other distributions to use a solution and contribute to this when another company has these possibilities?

Also, could this also be one of the reasons Intel decided not so support Mir officially.

I also wonder what this will mean for projects like Steam for Linux, application support, and driver support over Mir and Wayland.


This is the part I feel is a little iffy (from Wikipedia: Mir (software)):

> Longtime [Linux kernel]("http://en.wikipedia.org/wiki/Linux_kernel") developer Matthew Garrett criticized choice of licensing for Canonical's software projects, particularly Mir. Unlike [X.Org Server]("http://en.wikipedia.org/wiki/X.Org_Server") and Wayland, both under [MIT License]("http://en.wikipedia.org/wiki/MIT_License"), Mir is licensed under [GPLv3]("http://en.wikipedia.org/wiki/GPLv3")  &#8211; "an odd one" for "GPLv3-hostile markets" &#8211; but contributors are  required to sign an agreement that "grants Canonical the right to  relicense your contribution under their choice of license. This means  that, despite not being the sole copyright holder, Canonical are free to  relicense your code under a proprietary license". He concludes that  this creates asymmetry where "you end up with a situation that looks  awfully like Canonical wanting to squash competition by making it  impossible for anyone else to sell modified versions of Canonical's  software in the same market". Garrett&#8217;s concerns were echoed by [Bradley M. Kuhn]("http://en.wikipedia.org/wiki/Bradley_M._Kuhn"), Executive Director of the [Software Freedom Conservancy]("http://en.wikipedia.org/wiki/Software_Freedom_Conservancy").

I would only like to know if this is the case or not. I don't think I would like to use a distribution that grants these rights to one company.

---

### Post by grahammechanical on 2013-10-10
And this is the reason you joined the forum? To put these "concerns" to us? Have you written to Canonical about this? Are you a developer? Do you wish to contribute to the development of Mir? Your "concerns" are nothing to do with Mir. This contributor's agreement is not something new. It applies to developers wishing to add code to any Canonical project. And these "concerns" have been raised before.

Get the facts from the source

[http://www.canonical.com/contributors](http://www.canonical.com/contributors)

[http://www.harmonyagreements.org/docs/ha-cla-i.html](http://www.harmonyagreements.org/docs/ha-cla-i.html)

[http://harmonyagreements.org/](http://harmonyagreements.org/)

If you have not read those easily found pages, then I will consider this post to be an attempt at FUD.

Do you not finding it interesting that Canonical is being attacked on the choice of license, which is, by the way, a the latest version of the GPL. This version of the GPL caused a lot of controversy when it was released. It seemed that one little bit of GPLv3 code would force all the rest of the code to become GPLv3 code whatever the license it was originally given. It seems that some have still not come to terms with GPLv3. That is typical FOSS - disputes and arguments!

---

### Post by ssam on 2013-10-10
The copyright assignment don't really make much difference to anyone outside canonical/ubuntu. If anyone out side wanted to they could make a branch of the code with their own patches and improvements. Canonical wont allow those patches back into the official repo, but anyone else can use them. Only Ubuntu users would loose out.

The GNU project also demand copyright assignment for their projects.

(People outside ubuntu are more likely to want to use wayland than mir. They both do the same thing, but wayland aims to be a more general solution, where mir is predominately  designed to work with unity).

---

### Post by TamarinNOR on 2013-10-10
**@**[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")**:**
Just my personal. I don't really care if you find my reasoning for choosing one distribution over another for weird, but there was a reason for moving away from Windows, and it was not because I wasn't satisfied with the user experience. Nevertheless, I feel I have had much better experience with Linux as I have gotten to know it.

But is this part of the regular GPLv3: "contributors are required to sign an agreement that grants Canonical  the right to relicense your contribution under their choice of license."?

And what you say about FUD, it is what I got from these two pages:

[http://en.wikipedia.org/wiki/Mir_%28software%29](http://en.wikipedia.org/wiki/Mir_%28software%29)
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MjI](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MjI)

I don't really see how it can be much of a problem to discuss these things here, this would probably be the best place to ask about this. And if it is not the case, it it is nothing more then FUD, then I should just overlook these statements. But still, if it is FUD, it still does not make Ubuntu look good.

I have used Ubuntu since first version of Ubuntu was available, even though I have always tested other distributions now and then. I am no programmer. I had another account for an email I do not use anymore a long time ago, but that was mainly for launchpad to use the Ubuntu store, so made a new one, and yes, this is what I wanted to know.

---

### Post by monkeybrain20122 on 2013-10-10
There is a long thread here [http://phoronix.com/forums/showthread.php?81489-Mir-s-GPLv3-License-Is-Now-Raising-Concerns](http://phoronix.com/forums/showthread.php?81489-Mir-s-GPLv3-License-Is-Now-Raising-Concerns)

You may find some comments informative.

---

### Post by TamarinNOR on 2013-10-10
**@**[**[COLOR=#000000]monkeybrain20122[/COLOR]**]("http://ubuntuforums.org/member.php?u=1843403"):
Read most of them now. They seem to pretty much confirm what I got in mind from reading the page on Wikipedia, but there are some justifications to it pointed out there. As well as it is written in the agreement, so it is not like they are trying to hide it from anyone. 

It still leads to more fragmentation in the Linux community, and would be a mess if everyone ended up doing things like this.

Also, if distribution X decides to join in on the development of Mir, and also wants to make their proprietary license for mobile phone use or other uses, how would that be possible? I don't see why developers would want to give someone this right, without being able to do the same thing themselves. It really looks like Canonical wants to do a lot by themselves and it seems to distance them more and more from the rest of the community.

**@ssam:**
Since it is released under GPLv3, it could always come a fork of it if needed for some reason, that is a given possibility. But if people added to the project without signing the agreement, would this end up in more fragmentation and incompatibility between the two versions over time?

---

### Post by monkeybrain20122 on 2013-10-10
> **TamarinNOR said:**
> 

Also, if distribution X decides to join in on the development of Mir, and also wants to make their proprietary license for mobile phone use or other uses, how would that be possible? I don't see why developers would want to give someone this right, without being able to do the same thing themselves. It really looks like Canonical wants to do a lot by themselves and it seems to distance them more and more from the rest of the community.


But that is not possible with Wayland under MIT license anyway. In that case the mobile vendors can simply lock everything without having to pay a dime, I am not sure how it would be better in terms of openness.

---

### Post by TamarinNOR on 2013-10-11
So with one Canonical is the only one who can, with MIT, everyone can. True, MIT might not lead to more openess, but it feels more fair to everyone that contributes that no one gets extra benefits. Canonical might but themselves a little on the side with the rest of the community with this license, and for doing their own thing, but they might have had in mind that this will be developed within Canonical and its own community.

What will this mean for developers for hardware drivers, applications and games? Will this cause more work and could end up in difference in compatibility and performances due to lack of focus to either of the graphical servers? And how much extra work/effort will be needed to support both solutions?

---

### Post by monkeybrain20122 on 2013-10-11
> **TamarinNOR said:**
> So with one Canonical is the only one who can, with MIT, everyone can. True, MIT might not lead to more openess, but it feels more fair to everyone that contributes that no one gets extra benefits. Canonical might but themselves a little on the side with the rest of the community with this license, and for doing their own thing, but they might have had in mind that this will be developed within Canonical and its own community.



Maybe I misunderstood, but my understanding is that under the MIT license NO ONE in the community has control if vendors choose to lock down their devices, but in Canonical's scheme if vendors choose to lock down their devices they have to buy the right from Canonical. "The community" has no control and won't be benefited financially under either scheme. So "everyone can" is a wrong characterisation, under MIT the vendors don't need to ask the community for permission for locking down.

Basically, my understanding is that the licensing terms grant Canonical the right to sell exceptions but under MIT "exceptions" are "free",--technically not even exceptions under MIT,-- it is more freedom for vendors and manufacturers but not for the community.

---

### Post by ventrical on 2013-10-11
> **TamarinNOR said:**
> I have a concern about the license for Mir. While it is released under a free license, it seems that the license agreement to Canonical for Mir grants some unfair rights to the company. So if they want to, they can release the software under a proprietary license.
...
Also, could this also be one of the reasons Intel decided not so support Mir officially.



I have found that the unity-system-compositor works  best on Intel Graphics.. so it's news to me.

---

### Post by ventrical on 2013-10-11
Ok.. I got the picture now.

[http://www.omgubuntu.co.uk/2013/09/intel-remove-xmir-support-in-xorg-video-driver](http://www.omgubuntu.co.uk/2013/09/intel-remove-xmir-support-in-xorg-video-driver)

 The Ubuntu movers and shakers move real fast sometimes.

---

### Post by grahammechanical on 2013-10-12
@ventrical

When Canonical attempted to get Unity code into Gnome 3 shell the Gnome organisation blocked it. Now Intel has blocked Canonical's attempt to get Xmir code into Intel's open source driver. Canonical devs will continue patching the driver at this end. And people complain that Canonical goes its own way and they fail to give credit to the fact that Canonical has no objection to other developers using Mir code or Unity code.

What will people make of the fact that the next release of Cinnamon does not need Gnome DE. Cinnamon is no longer just a user interface but it is also its own desktop environment. Will people accuse those devs of fragmenting FOSS in the same way they have accused Canonical of doing this with Unity and Mir? I smell hypocrisy.

[http://www.webupd8.org/2013/10/cinnamon-20-released-becomes-entire.html#more](http://www.webupd8.org/2013/10/cinnamon-20-released-becomes-entire.html#more)

This blog gives another reason why Ubuntu has to go its own way.

[http://www.chriscoulson.me.uk/blog/?p=196](http://www.chriscoulson.me.uk/blog/?p=196)

> [COLOR=#444444][FONT=Ubuntu]The main difficulty with this is that the upstream projects generally don’t support their releases with updates for the duration that we require in Ubuntu – this means that it becomes the distribution’s responsibility to provide security maintenance for 5 years.  [/FONT][/COLOR]

And what will you and I do? We'll just keep on testing. I have to chuckle when I think of the mess that installing these alternative desktop will make of someone's OS.

> **Important: in my test under Ubuntu 13.10, installing Cinnamon broke the Unity session (I was unable to log in to Unity until I removed Cinnamon; this didn't occur in Ubuntu 13.04) so use it at your own risk!**

And they will expect Canonical to fix it.

Regards.

---

### Post by ian-weisser on 2013-10-12
The re-licensing and copyright-assignment boilerplates are not intended  to be a mechanism for a company to steal your contribution...though they  certainly could be abused that way (and we do need to prevent that!) The original intent is to keep the project open and successful in an environment of many contributors.

Sometimes, successful software needs to be re-licensed to *keep* it open and successful. Projects sometimes discover that their hastily-chosen license during startup no longer fits their needs. Time makes old licenses unpopular and incompatible, and newer license versions supersede the old. For example, GPL is on version 3. Someday, there will probably be a version 4. And then a version 5. 

One recent example of this issue discussed by the Ubuntu Technical Board  (openssl):  [https://lists.ubuntu.com/archives/technical-board/2013-June/001653.html](https://lists.ubuntu.com/archives/technical-board/2013-June/001653.html) .  A workaround was required because an old-but-vital project is unable (not unwilling) to re-license the software to be GPL-compatible.

---

### Post by ventrical on 2013-10-13
> **grahammechanical said:**
> @ventrical

When Canonical attempted to get Unity code into Gnome 3 shell the Gnome organisation blocked it. Now Intel has blocked Canonical's attempt to get Xmir code into Intel's open source driver. Canonical devs will continue patching the driver at this end. And people complain that Canonical goes its own way and they fail to give credit to the fact that Canonical has no objection to other developers using Mir code or Unity code.

What will people make of the fact that the next release of Cinnamon does not need Gnome DE. Cinnamon is no longer just a user interface but it is also its own desktop environment. Will people accuse those devs of fragmenting FOSS in the same way they have accused Canonical of doing this with Unity and Mir? I smell hypocrisy.

[http://www.webupd8.org/2013/10/cinnamon-20-released-becomes-entire.html#more](http://www.webupd8.org/2013/10/cinnamon-20-released-becomes-entire.html#more)

This blog gives another reason why Ubuntu has to go its own way.

[http://www.chriscoulson.me.uk/blog/?p=196](http://www.chriscoulson.me.uk/blog/?p=196)



And what will you and I do? We'll just keep on testing. I have to chuckle when I think of the mess that installing these alternative desktop will make of someone's OS.



And they will expect Canonical to fix it.

Regards.

   I think in the above examples that it may be neccesary to issue disclaimers for the various DEs like Mint, Cinnamon, Mate .. etc that if you install over an Alternate DE from the repos that you will interfect your systems with irregular  and, possibly, unresolvable depends. I recall that we (The testers) campaigned about how CCSM was borking desktops with the Unity Plugin and so they finally put in a disclamer note about that - and even fixed it to some extent. 

  Then again .. it is about money and compensations to the hard work that coders do. Some get  paid by Canonical, others don't , they do it out of  merit for the good of the project overall. But we all have to eat and pay bills, don't we?

  I don't know enough yet about how the whole wayland/weston/mir situation got carfunkled but it was obvious , from my perspective, that Canonical was waiting for  a prompter delivery of a workable wayland compositor and all we got  (or at least all I got) was somthing that looked like an old blanket or curtain type thingy that did absoultely nothing. Canonical may not admit that they were frustrated by being left to , more or less, dangle out there so they decided to  get busy and now we actually have a workable Mir compositor that does not seem to interfect any depends at atm. Changing horses in mid stream is not always a bad idea - especially if the horse your on  decides to dig in and not budge. Upstream, downstream...yes , as testers we have to go against the grain but there are times that we have no choice really but to go with the flow. In the end though, I am the decider who owns my machines and I decide what goes in and what goes out  and with my newer test models it only takes a few minutes to do fresh installs. We may not always see it but we as testers have a unique advantage over developers. It's called "feedback" which without then those programs and scripts and patches that developers put out would become insular and virtually meaningless and /or reach only a small pittance of an end_users group. Our input has become a commodity. Inter-developer reliance on testing has proven that most DEs would be rendered to a more or less banal state (like Cent OS.. oy!) Cadence testing ?? Iv'e seen old bugs that never even got looked at, or , if they did, just got dissed while devs just walked on by.

  I can almost hear Richard Stallman saying .."see .. see".. :)

Regards..


 regards..

---

### Post by TamarinNOR on 2013-10-18
> **ventrical said:**
> I have found that the unity-system-compositor works  best on Intel Graphics.. so it's news to me.

Not sure if I worded myself correctly, but was thinking about this:
[http://arstechnica.com/information-technology/2013/09/intel-rejection-of-ubuntus-mir-patch-forces-canonical-to-go-own-way/](http://arstechnica.com/information-technology/2013/09/intel-rejection-of-ubuntus-mir-patch-forces-canonical-to-go-own-way/)

EDIT:Sorry, should have read all the posts ... I see you posted another link.

---

### Post by ian-weisser on 2013-10-18
Intel's September 2013 reversion of the Canonical Mir patch to xf86-video-intel is due to politics, not licensing. The patch met all criteria for acceptance...and was originally accepted.

---

### Post by TamarinNOR on 2013-10-18
> **ian-weisser said:**
> The re-licensing and copyright-assignment boilerplates are not intended  to be a mechanism for a company to steal your contribution...though they  certainly could be abused that way (and we do need to prevent that!) The original intent is to keep the project open and successful in an environment of many contributors.

Sometimes, successful software needs to be re-licensed to *keep* it open and successful. Projects sometimes discover that their hastily-chosen license during startup no longer fits their needs. Time makes old licenses unpopular and incompatible, and newer license versions supersede the old. For example, GPL is on version 3. Someday, there will probably be a version 4. And then a version 5. 

One recent example of this issue discussed by the Ubuntu Technical Board  (openssl):  [https://lists.ubuntu.com/archives/technical-board/2013-June/001653.html](https://lists.ubuntu.com/archives/technical-board/2013-June/001653.html) .  A workaround was required because an old-but-vital project is unable (not unwilling) to re-license the software to be GPL-compatible.

That has been stated towards the Linux kernel itself some years ago as well I believe, when GPLv3 came out. And it can be a problem. As far as this is considered, I am totally agreeing. And licenses as MIT and BSD might not preserve the openness for future extensions or development of the software.

This agreement does however only give Canonical the right to re-license it, not some other part, like Linux Foundation, and it does not seem to be anyone mentioning any reassurance in the agreement that limits Canonical to change the license in any direction they want. And if bigger parts of the community were to support Mir, their contribution would either not make it into the official Canonical version, unless they do add contributions to Mir only released under GPLv3 without signing the agreement. I do still wonder how the Linux community would be like if every distro made such an agreement.

---

### Post by Gyokuro on 2013-10-18
That topic about why the Linux kernel sticks with it's license got discussed to death and Linus and various major kernel hackers made it clear why it stays as it is - what I do not get is why various people belief that they will "gain" something if the kernel get relicensed to GPL3 and nor I want to discuss this in detail as I'm sure that a forum moderator will delete my post or close this thread. The made argument that X11 is licensed under a MIT license is a bad one is somehow a stupid argument - such people should check the origin of X11 ([https://en.wikipedia.org/wiki/Project_Athena](https://en.wikipedia.org/wiki/Project_Athena)) and should repeat said argument and it will show that they do not understand or plain ignore the facts. However MIR and it's license is a complete different story - in short - in case I sign the CLA - I grant Canonical all rights that they can do with my code whatever they want - develop it further under an opensource license or relicense it under a closed one and sell it for myself this is a Nogo and therefore I will never sign the CLA  nor I want to support it via patches and with this behaviour they are able to control the further development of Ubuntu's graphic stack - plain and simple - only to control it's direction. Intel's decision to drop said patch is a political one - the same goes for MIR and people should stop whining about how bad Intel's decision is - Canonicals history in regard to MIR is not better and a lot of people can remember the story about Gnome and libindicator and have not forgotten it. Today's post ([http://www.markshuttleworth.com/archives/1295](http://www.markshuttleworth.com/archives/1295)) about Ubuntu in general and MIR especially makes me only wonder - whether the poster is aware about the background of the original Boston Tea Party ([https://en.wikipedia.org/wiki/Boston_Tea_Party](https://en.wikipedia.org/wiki/Boston_Tea_Party)) I do not know but even if I risk to get bained - it's completly bull***** or marketing bla bla.

---

### Post by ian-weisser on 2013-10-18
> **TamarinNOR said:**
> This agreement does however only give Canonical the right to re-license it, [...] and it does not seem to be anyone mentioning any reassurance in the agreement that limits Canonical to change the license in any direction they want. And if bigger parts of the community were to support Mir, their contribution would either not make it into the official Canonical version, unless they do add contributions to Mir only released under GPLv3 without signing the agreement. I do still wonder how the Linux community would be like if every distro made such an agreement.

The community will look the same way it does today. Because the community already has several solutions to that issue.

 For example: If your contribution to a project is large, then you can release it as your own lib under it's own (compatible) license for the project to use. You retain control of your code. 

Alternately, you can create a competing project with a permanent license.

Alternately, you can fork the older (free) version of a newly-closed project.

Lots of other organizational and legal possibilities. This seems like a long-solved problem...as long as you realize that no problem nor solution are perfect.

---

### Post by TamarinNOR on 2013-10-19
> **Gyokuro said:**
> That topic about why the Linux kernel sticks with it's license got discussed to death and Linus and various major kernel hackers made it clear why it stays as it is - what I do not get is why various people belief that they will "gain" something if the kernel get relicensed to GPL3 and nor I want to discuss this in detail as I'm sure that a forum moderator will delete my post or close this thread. The made argument that X11 is licensed under a MIT license is a bad one is somehow a stupid argument - such people should check the origin of X11 ([https://en.wikipedia.org/wiki/Project_Athena](https://en.wikipedia.org/wiki/Project_Athena)) and should repeat said argument and it will show that they do not understand or plain ignore the facts. However MIR and it's license is a complete different story - in short - in case I sign the CLA - I grant Canonical all rights that they can do with my code whatever they want - develop it further under an opensource license or relicense it under a closed one and sell it for myself this is a Nogo and therefore I will never sign the CLA  nor I want to support it via patches and with this behaviour they are able to control the further development of Ubuntu's graphic stack - plain and simple - only to control it's direction. Intel's decision to drop said patch is a political one - the same goes for MIR and people should stop whining about how bad Intel's decision is - Canonicals history in regard to MIR is not better and a lot of people can remember the story about Gnome and libindicator and have not forgotten it. Today's post ([http://www.markshuttleworth.com/archives/1295](http://www.markshuttleworth.com/archives/1295)) about Ubuntu in general and MIR especially makes me only wonder - whether the poster is aware about the background of the original Boston Tea Party ([https://en.wikipedia.org/wiki/Boston_Tea_Party](https://en.wikipedia.org/wiki/Boston_Tea_Party)) I do not know but even if I risk to get bained - it's completly bull***** or marketing bla bla.
I have not payed that much attention to that discussion, just remember a quote from Linus about it, saying it was pretty much impossible.

So what would be the pros and cons of having a graphical server released under pure GPL, or something like LGPL, or a license like MIT?

---

### Post by MartyBuntu on 2013-10-19
> **ian-weisser said:**
> 
 For example: If your contribution to a project is large, then you can release it as your own lib under it's own (compatible) license for the project to use. You retain control of your code. 



I anticipate this will be the route for many devs, at least initially.

---

### Post by TamarinNOR on 2013-10-20
> **MartyBuntu said:**
> I anticipate this will be the route for many devs, at least initially.

But will any contributions be accepted to MIR without signing the CLA?

---

### Post by ian-weisser on 2013-10-20
> **TamarinNOR said:**
> But will any contributions be accepted to MIR without signing the CLA?

Mir depending upon an independent lib does not require a CLA by either party. An independent lib is separately licensed, of course.

---

