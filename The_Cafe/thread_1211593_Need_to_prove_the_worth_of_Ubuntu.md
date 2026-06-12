---
title: "Need to prove the worth of Ubuntu"
date: 2009-07-12
forum: The Cafe
---

### Post by Tutigan on 2009-07-12
Hi guys, I work in IT as a sysadmin, and have asked if I can use my ubuntu laptop on our domain... this is the e-mail I got back. Please help me answer these and prove the worth of Ubuntu to my senior sysadmins. (I know it's long... sorry)

"Just so you know we are not biased against Linux I would put to you a few questions  that I would need to understand about Ubuntu or any Linux distro in a domain environment  before it would be considered a serious OS option.
The mention of WINE , Xen or any virtual environment will make your response to that point void.

I estimate I can load and have on the domain a windows OS and cover all of the below business requirements in no longer than 5 hours.
Another sysadmin has been able to demonstrate the MAC OS is mostly capable. Can you do that with Linux?

How in the past have you handled Authentication with a Windows 2003 domain controller? 
All our machines are members of the domain.
How will you run the logon scripts?

What antivirus will you be using? (No I do not accept that Linux has no viruses).

How will you access your Exchange mail properly, e.g. see other users shared calendars and access and update your calendar?
What will you do when we move to Exchange 2007 in the next 3-6 months?

Are you positive your printer drivers will support all our printers correctly? Printing a Text file is not the benchmark, one of each of the following products files is a test.

What Office Productivity applications will you use for creating documents that are fully supported by the other users in the workshop.
Word 2007 xml formats
Excel 2007 “ “
PowerPoint 2007
And the killers are
Visio 2007
Project 2007

How will you create an Office application macro if required for a customer.

How will you access our new intranet which is based on .NET and supports IE  and Office application automation?

How will you make PPTP connections to our customers sites?
How will you make Cisco VPN connections to our customers sites?
How will you make RDP connections to windows machines? Even those using a 6.1 backend.
Can you create a RDP link and send it to a customer confident it will work because you have tested on your OS?

Can you guarantee all services not required will not be accidentally switched on? (i.e. DHCP which will wreak havoc within our network)

How will you talk a client through using their O/S if you don’t run a similar OS to them?

What reason would there be for running Linux on the domain? Unlike the MAC OS we do not have any installed base of users.
Is there anything within the OS that makes it a better choice over a windows OS in a domain environment?

Please address all the above and we will consider your request. Remember you would need to be able to achieve this is an acceptable time period."

---

### Post by joeyknuccione on 2009-07-12
Unfortunately for me, Ubuntu is dead in the water because of little to no modem support. I often have to stay in "backwoods" locations with dialup my only option. Sad to say, I've had to rely on Windose in order to maintain connectivity.
If and when Ubuntu can support dialup, I will be kicking Satan to the curb.

---

### Post by Gizenshya on 2009-07-12
The real question is why use those solutions that force one to use Windows?  What is actually gained by the Windows version over the Linux version?

The word client is mentioned.  If this is a service organization (or the department you're working in provides a service) then there may very well be good reasons.

For example, adopting OpenOffice.org's office suite as a business is often not practical.  Send someone an odt format document and watch their reaction.  The business standard is Microsoft Office.  The reasons do not matter, all that matters is what the standard is.  If OpenOffice.org's office suite were 100% compatible, then it would work.  But Microsoft keeps changing things to keep it below that 100% mark.

He mentioned macros.  Yeah, try running macros from a doc file and watch how fast it screws up.  They try to call windows components and god knows what all else, and it is just hell.

---

### Post by Tutigan on 2009-07-12
> **Tutigan said:**
> What antivirus will you be using? (No I do not accept that Linux has no viruses)

Don't worry about this one, can answer this myself!

---

### Post by Tutigan on 2009-07-12
> **Gizenshya said:**
> The real question is why use those solutions that force one to use Windows?  What is actually gained by the Windows version over the Linux version?

The word client is mentioned.  If this is a service organization (or the department you're working in provides a service) then there may very well be good reasons.

We provide a range of services from web design to Technology & Integration.
I work in T&I. The others in my department all use windows except for two who use MAC OS X.
I use ubuntu almost everywhere except for hardcore gaming and at work, and want to cut it down to XP only for home gaming.
Plus, if I can convince them, it will help to spread the word of Ubuntu!

---

### Post by fballem on 2009-07-12
> **Tutigan said:**
> Hi guys, I work in IT as a sysadmin, and have asked if I can use my ubuntu laptop on our domain... this is the e-mail I got back. Please help me answer these and prove the worth of Ubuntu to my senior sysadmins. (I know it's long... sorry)

"Just so you know we are not biased against Linux I would put to you a few questions  that I would need to understand about Ubuntu or any Linux distro in a domain environment  before it would be considered a serious OS option.
The mention of WINE , Xen or any virtual environment will make your response to that point void.

I estimate I can load and have on the domain a windows OS and cover all of the below business requirements in no longer than 5 hours.
Another sysadmin has been able to demonstrate the MAC OS is mostly capable. Can you do that with Linux?

How in the past have you handled Authentication with a Windows 2003 domain controller? 
All our machines are members of the domain.
How will you run the logon scripts?

What antivirus will you be using? (No I do not accept that Linux has no viruses).

How will you access your Exchange mail properly, e.g. see other users shared calendars and access and update your calendar?
What will you do when we move to Exchange 2007 in the next 3-6 months?

Are you positive your printer drivers will support all our printers correctly? Printing a Text file is not the benchmark, one of each of the following products files is a test.

What Office Productivity applications will you use for creating documents that are fully supported by the other users in the workshop.
Word 2007 xml formats
Excel 2007 “ “
PowerPoint 2007
And the killers are
Visio 2007
Project 2007

How will you create an Office application macro if required for a customer.

How will you access our new intranet which is based on .NET and supports IE  and Office application automation?

How will you make PPTP connections to our customers sites?
How will you make Cisco VPN connections to our customers sites?
How will you make RDP connections to windows machines? Even those using a 6.1 backend.
Can you create a RDP link and send it to a customer confident it will work because you have tested on your OS?

Can you guarantee all services not required will not be accidentally switched on? (i.e. DHCP which will wreak havoc within our network)

How will you talk a client through using their O/S if you don’t run a similar OS to them?

What reason would there be for running Linux on the domain? Unlike the MAC OS we do not have any installed base of users.
Is there anything within the OS that makes it a better choice over a windows OS in a domain environment?

Please address all the above and we will consider your request. Remember you would need to be able to achieve this is an acceptable time period."

Actually, you will not be able to use ubuntu for two reasons:

1. If you are a service organisation, and I think that you are, and your clients do not have linux, then there is no reason for you to be installing linux.

2. The real killer is Visio - there is currently no linux program that can read or write Visio files. I made a conscious decision to abandon my visio files when I converted to ubuntu. In your case, you do not have an option, and they have made it very clear that they will not entertain WINE - and I cannot blame them.

You will need to use Windows or Mac - at least until Linux can provide a way to work with Visio files.

Sorry,

---

### Post by Tutigan on 2009-07-12
> **fballem said:**
> 1. If you are a service organisation, and I think that you are, and your clients do not have linux, then there is no reason for you to be installing linux.


We are.
But my laptop only sits on my desk in the office and goes home at the end of the day, no client sees it.
If I need to take a laptop with me, I take a loan one.

And even if you think the argument is lost, humour me and help me answer all these questions.
Please.

---

### Post by LepeKaname on 2009-07-12
When you work in a Microsoft World, there are no so many alternatives... As was already told you will not able to fulfill Office suite (including Visio, Project, macros, etc.) requirements. If you are going to develop in .NET there is no another option. 

I know how you may feel as we like to work with Linux, but trying to do so in this situation it doesn't look convenient. You are going to enter in mayor problems than solutions if you use Linux there. 

If you don't like to use Windows (as me), then get another job!

---

### Post by aysiu on 2009-07-12
If you can't answer those questions yourself, perhaps you should not be using Linux at work.

I think the senior admin who wrote that brings up legitimate concerns (except the antivirus bit). The most important thing at your job is that you do your job, not that you run your preferred OS. If you can prove that you can easily do your job and not interfere with others' jobs by running your preferred OS, then great. Otherwise, just stick with Windows.

---

### Post by LepeKaname on 2009-07-12
> Ubuntu or any Linux distro in a domain environment before it would be considered a serious OS option.

I forgot to comment that Ubuntu (and any other distro as well) is by far a better OS than Windows (and a serious OS). I think they are Win-Blinded in that point. 

Just because Linux can't join the "microsoft-closed-only party" that doesn't make it less valuable.

This point kind of hurt me.... sorry I had to comment it.

---

### Post by fballem on 2009-07-12
> **Tutigan said:**
> We are.
And even if you think the argument is lost, humour me and help me answer all these questions.
Please.

Others have suggested that since you cannot satisfy _all_ of the specified requirements, then the argument is done. I don't know all of the answers, but in the situation you've given, then you will either have to continue to work with Windows or change jobs.

Please forgive the presumption on my part, but I'd like to suggest that if you decide to continue to work with Windows - i.e. keep your job - make very certain that your attitude reflects a true acceptance of your decision. No grumbling and no chip on your shoulder that you can't use your favourite operating system. Many of us are in similar situations, but from your employer's perspective, they are looking for an absolute professional attitude on the part of their employees - particularly those who deal with customers. I don't know you, so I don't know if I needed to offer the advice, so I hope that you will take it in the spirit in which it was offered.

Regards,

---

### Post by Tutigan on 2009-07-12
As people have pointed out (and so many more will), M$ is a closed party.
My logic in doing this was to prove to my colleagues that it doesn't have to be a closed party. If we could incorporate Linux, perhaps even migrate some servers to Linux, it would be good etc etc etc.

But as others will hasten to point out, it is obvious my colleagues are a bit stuck in their windows-ways.

Thanks for all the replies guys, I guess I'll give up this battle.

---

### Post by fballem on 2009-07-12
> **Tutigan said:**
> 
Thanks for all the replies guys, I guess I'll give up this battle.

Gracefully, of course! :lolflag:

---

### Post by juancarlospaco on 2009-07-12
The mail response is stupid, they aren't _Senior_ Sysadmins, 

To mention,** MS RDP its not safe**, its Vulnerable by Man-in-the-middle Attacks,
you can be pwned using MS RDP on your Servers.

MS AD handle LDAP Authentication, so Linux can Authenticate too.

You have OpenSource ClamAV or Commercial Antivirus are avaliable for Linux.

Using Macros on MS Office Documents are a **BIG security problem**, 
using MS ActiveX its a **BIG security problem**.

On a Network made by_ real _Senior Sysadmins..., 
an unwanted DHCP server doesn't wreak the network.
You can break the Network from Windows by running a DHCP too.

By the way some items can not be done on MAC OS X too.
*[SIZE="1"]example:"How will you talk a client through using their OS if you don’t run a similar OS to them?"[/SIZE]*

:p

---

