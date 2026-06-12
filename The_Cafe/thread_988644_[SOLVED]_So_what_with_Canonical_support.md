---
title: "[SOLVED] So what with Canonical support?"
date: 2008-11-20
forum: The Cafe
---

### Post by newuserincalgary on 2008-11-20
Hi,

Anybody know what gives with Canonical? I have sent them two emails asking for some idea of what sort of support they provide for their $250 annual desktop support package. So far no response....doesn't give me the warm and fuzzies about spending 250 bucks for support if they can't even acknowledge an email.

The fact of the matter is I have had an extremely difficult and frustrating experience trying to get either Ubuntu 8.04 or 8.10 installed and running. I had 8.10 up and working until I ran update manager...now it doesn't even come close to booting up....went back and thought I would try 8.04 (being the long term support version I thought it would be more stable) but no luck....won't boot either....anyway I am at the point of wanting to pay someone to help me get it going....

Is Canonical only interested in large corporate customers? If so, they should take the individual user support option off their website....

Anybody ever talk to anybody at Canonical?????

---

### Post by Dr Small on 2008-11-20
Email is a unreliable means of communication; Indeed, so much as to be similar to snail-mail. Alot of things happen when you send an email to a person. It could be inevitably lost, delayed or never sent from the SMTP server. I wouldn't necessarily blame Canonical. 

Of course, if they did receive the emails, then I would blame them.

Just my 2 cents ;)

---

### Post by newuserincalgary on 2008-11-20
Well there isn't much choice here, there are no phone numbers on their website.....

Anybody know how to get hold of someone from Canonical????

---

### Post by smoker on 2008-11-20
> **newuserincalgary said:**
> Well there isn't much choice here, there are no phone numbers on their website.....

Anybody know how to get hold of someone from Canonical????

not sure if you'll get a quick response, or any, but you could try here:
[]("http://www.markshuttleworth.com/archives/tag/canonical")
[http://www.markshuttleworth.com/contact-details](http://www.markshuttleworth.com/contact-details)

---

### Post by kernelhaxor on 2008-11-20
> **Dr Small said:**
> Email is a unreliable means of communication; Indeed, so much as to be similar to snail-mail. Alot of things happen when you send an email to a person. It could be inevitably lost, delayed or never sent from the SMTP server. I wouldn't necessarily blame Canonical. 

Oh common the odds of that are very low .. I can't remember the last time I sent an email and it just got lost (I mean without a bounce error message) ..

It is reasonable to assume that Canonical received the email.

---

### Post by Dr Small on 2008-11-20
> **kernelhaxor said:**
> Oh common the odds of that are very low .. I can't remember the last time I sent an email and it just got lost (I mean without a bounce error message) ..

It is reasonable to assume that Canonical received the email.
If the SMTP server is having problems, it could have never been delivered and you will never get a bounce error. I have actually had that happen quite frequently with my webhosting provider's SMTP server.

---

### Post by ciscosurfer on 2008-11-20
> **Dr Small said:**
> If the SMTP server is having problems, it could have never been delivered and you will never get a bounce error. I have actually had that happen quite frequently with my webhosting provider's SMTP server.Frequently? Time to get a new provider ;-)

---

### Post by Dr Small on 2008-11-20
> **ciscosurfer said:**
> Frequently? Time to get a new provider ;-)
Nah. I solved the problem myself, but setting up the Outgoing mail to go through my SMTP server on the network ;)

---

### Post by AllenGG on 2008-11-20
Let's take this "new users' "  complaint seriously, and it definitely relates to BUG #! in Launchpad.
                             [SIZE=4]   [Bug #1]("https://bugs.launchpad.net/ubuntu/+bug/1")[/SIZE]
Paid or paying for, support is a logical choice for many people, not just the home user or student.
First: to the NewuserinCalagary, is there a Linux user group near you ?
Second, look at the [SIZE=4][COLOR=Sienna][Forums]("http://ubuntuforums.org/index.php")[/COLOR][/SIZE]
Finally, try version 8.10, and run is an "OEM" install.  UNLESS you're trying to dual-boot .
In fact 8.10 is easier to install or repair than any Windows (MS) version that I've had to deal with. (Too many)
If you're still having problems send me an IM through here.
Allengg

---

### Post by newuserincalgary on 2008-11-20
Thanks AllanGG....

Don't know if the is a Linux User's group anywhere near here....seems likely that there would be...I will see what I can find....

Regarding the FORUMS....I have spent more time than I can afford the last few days searching through the forums to see what can be done or if anyone else has been having similar issues....the closest thing that I can find to a solution is the possibility the initrd pkg cannot access the ext3 boot partition properly...i am going to try a fresh install after changing my boot partition to ext2 and wiping it clean...others have said that ext3 is fine....at this piont it is worth a shot....it would seem wierd that the boot partition would have to be ext2 as ext3 seems to be a more robust format with the journaling feature...????

Oops....i am installing 8.10, it was working for a while until I ran update manager....8.04 won't run at all

and I am doing a dual boot....unfortunately, i have a few windows apps that i need to use for work....hopefully after I get Ubuntu up and running, i can run the XP apps in VMware window or something like that...

---

### Post by tvtech on 2008-11-20
> **newuserincalgary said:**
> Hi,

Anybody know what gives with Canonical? I have sent them two emails asking for some idea of what sort of support they provide for their $250 annual desktop support package. So far no response....doesn't give me the warm and fuzzies about spending 250 bucks for support if they can't even acknowledge an email.

The fact of the matter is I have had an extremely difficult and frustrating experience trying to get either Ubuntu 8.04 or 8.10 installed and running. I had 8.10 up and working until I ran update manager...now it doesn't even come close to booting up....went back and thought I would try 8.04 (being the long term support version I thought it would be more stable) but no luck....won't boot either....anyway I am at the point of wanting to pay someone to help me get it going....

Is Canonical only interested in large corporate customers? If so, they should take the individual user support option off their website....

Anybody ever talk to anybody at Canonical?????

search the forums, see if there are any reviews on it!  go to [www.google.com/linux](www.google.com/linux) do a search about it see if there's any reviews there, I'd imagine that they'll probably get you considerably better service if you pay for it.

---

### Post by ciscosurfer on 2008-11-20
If this hasn't been said already, and just to be clear, you must pay for support from Canonical before you receive support from Canonical.  Inquiries about receiving Canonical support can be made and you can receive a return call as documented on [their site]("http://www.canonical.com/").  Otherwise, the community forums, the official help documentation, and the community wikis are your best-bet (and they're free).

From reading the other threads you've started, it sounds like you've borked your system (messing with GRUB, et cetera).  The absolute fastest thing you can do right now is to save important documents and config files that you want to restore and then do a clean install of the OS (like you just mentioned).  It's good to understand how the OS works, but I would recommend that at least in the beginning, try not to get caught up in some of the minutiae. If you want to dual-boot, there are wiki pages and official help as well that should help you along.  And they are a wise place to start when unsure about topics (installing, partitioning, configuration, filesystems, basic commands, how to traverse, et cetera).

I understand it can be frustrating when things don't work: been there, done that.  Try to stay calm and understand that everyone here is giving best-effort attempts (some help is better than others). Good places to start can be found in my signature located beneath this post--they are a good "jumping off" point.

---

### Post by newuserincalgary on 2008-11-20
i have ABSOLUTELY no problem with paying for support before I get support.....I just want to know what sort of support I can expect BEFORE I spend my money....is this an unreasonable expectation??

All I asked of Canonical was for someone to clarify what level of support I would get for 250 bucks....so far no response....

I have not messed up the install...it messed up itself...it is possible that i have compounded the problem by trying to do some of the things i found in the forums....i have not just sat here and posted whining complaints....i have spent a LOT of time on the forums trying to figure this out on my own....

---

### Post by Ripfox on 2008-11-20
> **newuserincalgary said:**
> i have ABSOLUTELY no problem with paying for support before I get support.....I just want to know what sort of support I can expect BEFORE I spend my money....is this an unreasonable expectation??

no

> **newuserincalgary said:**
> it messed up itself

no

---

### Post by ciscosurfer on 2008-11-21
@newuserincalgary,

Okay.  I think you need to take a breath.  The saying goes something like, "You catch more flies with honey than with vinegar".  

My last post obviously upset you even further and so I apologize if it did.  I meant no disrespect.  I am, however, curious to know what you would expect out of any support contract?  The Canonical support page seems fairly straightforward to me:
 > 
Ubuntu for Desktop Support
For users of Ubuntu products on desktop or laptop computers. Buying support provides the reassurance of expertise an email or call away. Includes Live Phone Support (9-5 or 24/7),                                         Email Support, Security Upgrades, Product Upgrades, Web-based Systems Management [Landscape].  
They also state you may prefer localized support and they provide a link to that page.  The also provide other contact links to inquire about any service they offer.

Support contracts in general offer peace of mind, assurance, and essentially someone to hold your hand.  This level of service probably doesn't include on-site service/repair. They also offer industry-standard SLA's.  They offer you Ubuntu experts, many of whom are also Ubuntu developers.  The communication protocol is via phone, email, and web.  You can ask them anything you want.  They'll do their best to provide you with an answer to your questions or problems.  This is what a support contract is all about.  If you want someone to come to you for service/repair, that would incur an additional charge, as most industry contracts work this way.

I urge you to continue trying to get in touch with them if that is what you prefer.  No, it shouldn't be so difficult to do so, but the world isn't perfect and things do happen that may cause delays.  They are also listed in the phone book if you want to call them directly and ask them questions about what a $250 support contract entails.  I'm willing to bet soup to nuts they'll tell you the same thing I've just outlined for you.  What I've presented to you seems logical to me for the amount they are asking.  Most people (minus Enterprise users/admins) who find themselves in a situation where they would like/need paid support don't usually have questions like "what do I get for the money", though it's a completely valid question.  They want help and they want it now.

That's my story, and I'm stickin' to it. :-D

---

### Post by fatality_uk on 2008-11-21
I think the information you are looking for isn't that hard to find.
[http://www.canonical.com/services/support](http://www.canonical.com/services/support)
[http://www.canonical.com/services/support/sla](http://www.canonical.com/services/support/sla)

From the SLA
> 4 Scope of coverage
Canonical will provide installation, configuration, maintenance and management support for Ubuntu Desktop Edition on
appropriate computer systems. Canonical will support the Customer on any version of Ubuntu Desktop Edition that suits
the Customer's requirements as long as it's within its life-cycle.
Canonical &#8211; Ubuntu Desktop Edition Support Service Description EN v1.2                                       Page 1
Canonical will provide a reasonable level of assistance to the Customer to install Ubuntu on computer systems built from
an officially supported computer architecture. Canonical is not able to guarantee that Ubuntu can be installed on all
computer systems. For the avoidance of doubt, Canonical is able to make a level of effort with hardware issues that take
place on systems that have been specified by Canonical as Certified.
Canonical will support all the software defined within the standard desktop support packages. A full list of supported
packages for each release is provided upon request.
The Ubuntu distribution is a collection of many elements of Open Source software. Canonical will not be able to resolve
all issues, even on packages that are supported. For any supported application Canonical will attempt to provide a
Resolution which will consist of a workaround or a full solution. However, Ubuntu is a complex software product and
specific issues may be difficult to resolve, so no guarantee on resolution or time to fix can be provided.


Read the SLA's. They answer the OPquestion.

Alternatively, [http://www.canonical.com/contact/sales](http://www.canonical.com/contact/sales) posts a question to the support sales team who will usually give you a call within 2-3 day. Always been my experience.

---

### Post by newuserincalgary on 2008-11-27
OK, they finally got back to me and this is resolved, albeit a bit slower than I would have liked......8-[

---

