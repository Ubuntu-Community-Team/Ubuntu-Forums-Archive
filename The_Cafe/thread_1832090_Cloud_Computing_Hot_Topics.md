---
title: "Cloud Computing Hot Topics?"
date: 2011-08-24
forum: The Cafe
---

### Post by PartisanEntity on 2011-08-24
Hi everyone,

Several months ago I decided to enroll in a Masters program in Creative Media.

For my next paper, I would like to write about Cloud Computing. One of the topics I am thinking of writing about is how Cloud Computing affects our privacy.

But that's quite a common topic so I am wondering if there is something more interesting I could write about.

Anyone work in this field? What are the current "Hot Topics"?

Thanks!

---

### Post by Dragonbite on 2011-08-24
I don't quite work in what would be called "cloud", it is an office-wide only Intranet.

But since I got a Cr-48 test pilot Chromebook back in December, I have been steadily (until this week) been moving more and more to a could-based computing focus.  

There is a difference with a cloud-based experience and to take the most advantage of it is a change in thinking, as well as moving a lot of what you take for granted moving between systems, now has to be moved online and accessed in a totally different manner (with different strengths and weaknesses).

Of course there is the negatives of cloud computing; requiring a network connection, if server/company goes under you are SOL, security of accounts, "who owns it", etc.  Why not do something on the positive side of cloud computing.

Researching is pretty simple, too.  Place Chrome/Chromium on a couple machines and use that as your entire computing usage; documents, email, calendar, images, etc.

I say Chrome in part because of the synchronization aspect means the two are kept with the same bookmarks,apps, extensions, etc. and the use of 2 computers means you can't "cheat" and copy your files from one system to the other :)

I use Chrome while at work and it is handy that if I run across a bookmark or app or extension that looks interesting, I add it. If I need to work on a document, I use Google Docs. Then when I am home, I don't have to synchronize with UbuntuOne/Dropbox (which requires both systems to install something), I just fire up the browser and give it a moment to synchronize, or fire up Google Docs and continue with what I was working on.

Currently for the best effect you will likely end up using Google since their products (email, calendar, contacts, tasks, pictures and documents) are integrated (open an email attachment in Google Docs without having to download-upload).  There are a lot of other applications as well, and some are very, very good!

I don't know if I am making much sense here. If you want to further discuss it, just let me know.

---

### Post by Old_Grey_Wolf on 2011-08-24
When people say cloud computing they may be talking about different things. It is a very overloaded term.

The following is not very precise; however, you aren't getting an Engineering Degree. I hope it explains the differences to you.

There is Infrastructure-as-a-Service (IaaS) that is virtual compute resources, virtual storage resources, and virtual network resources. You could think of that as your computer's hardware; however, we are talking about a cloud of virtual hardware.

Then there is Platform-as-a-Service (PaaS) this adds to IaaS by adding operating systems, DNS services, authentication services (such as, Active Directory, LDAP), and possibly software patch repositories and the like. You could think of that as your computer's operating system; Microsoft's Windows Update, YUM, or APT patch service; and login user id/password authentication; however, we are talking about a cloud of services.

Next is Software-as-a-Service (SaaS) this adds to PaaS by adding applications; such as, office applications, web applications, and data services; such as, storage services like Ubuntu one. You could think of that as your computer's applications for word processing, spreadsheets, databases, web apps, multimedia apps, etc.; however, we are talking about a cloud of services. 

I think you are talking about SaaS if your degree is in Creative Media.

I work in IaaS and PaaS. One of the topics I see discussed is related to disaster recovery or fault tolerance; were you try to keep your service running if you loose an entire datacenter due to power failure, or a datacenter's storage malfunctions, etc. This happened to Amazon's Elastic Cloud recently. Some ideas involve multiple datacenters located at different locations that mirror each other so that if one fails one of the other datacenters takes over, and how that can be implemented.

SaaS probably has the same disaster recovery or fault tolerance problem. If the infrastructure that the Software Service runs on fails, can you switch to another datacenter without loss of data? If the Software Service fails at one location's datacenter, can it switch to another datacenter without loss? Is there any way that a single datacenter can make the system redundant so that it can continue to provide the Software Service if only some of datacenter's servers, storage, or networks are not functioning? Think about what happens when your computer crashes while you are editing a document, and try to relate that to a cloud.

---

### Post by christopher.wortman on 2011-08-25
SaaS in mind. I currently use Office 365 offered by Microsoft. It is wonderful. I can edit and save local documents and sync them with my Live account from Kubuntu. Then at work use Office 365 and edit and sync with Windows (because we are forced to use it there). It all syncs then at home if I notice an issue, I know all I need to do is log in and edit it. If done properly, SaaS like this is amazing! I get all the abilities of MS Office 2010 on Linux for $65 a year which is paid for by my boss then comes out of taxes as a work expense. The documents can be saved to the hard drive and synced with skydrive.

Side thought, you can write off Windows, and MS Office as a work expense on your taxes and get every cent you paid to Microsoft at the end of the year, so in effect Office and Windows are just as free as beer as you can legally get. I say buy them on Dec 31, when you file your taxes on Jan 2, you will have all the money you put into it back by the 10th in time to pay rent :-P

---

### Post by Dragonbite on 2011-08-25
> **christopher.wortman said:**
> SaaS in mind. I currently use Office 365 offered by Microsoft. It is wonderful. I can edit and save local documents and sync them with my Live account from Kubuntu. Then at work use Office 365 and edit and sync with Windows (because we are forced to use it there). It all syncs then at home if I notice an issue, I know all I need to do is log in and edit it. If done properly, SaaS like this is amazing! I get all the abilities of MS Office 2010 on Linux for $65 a year which is paid for by my boss then comes out of taxes as a work expense. The documents can be saved to the hard drive and synced with skydrive.

Side thought, you can write off Windows, and MS Office as a work expense on your taxes and get every cent you paid to Microsoft at the end of the year, so in effect Office and Windows are just as free as beer as you can legally get. I say buy them on Dec 31, when you file your taxes on Jan 2, you will have all the money you put into it back by the 10th in time to pay rent :-P

Is Office365 more capable than Office Live current offering?  I like this scenario you described (and I don't apologize for using Windows at work, it isn't my choice).

If Office365 is no better than their Live offerings, then I don't have any compelling reason to switch (yet).

---

