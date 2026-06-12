---
title: "Forced to use Windows for a day....."
date: 2010-02-05
forum: The Cafe
---

### Post by HDave on 2010-02-05
This week I was forced to use Windows again for the first time in a long time because the Intuit online payroll system (incredibly) uses activeX controls and my usual firefox-user-agent-switch trick didn't work.  :-(

In order to make the experience bearable, I took it upon myself to set up some of my favorite Ubuntu apps:
 * Tomboy
 * KeePass2
 * Pidgin
 * SSH Client
 * Openoffice
 * Firefox

I skipped Thunderbird and Songbird because I don't plan on using that machine very much.  

Anyway, it really made the entire experience bearable and also got me thinking two thoughts:

 1) I don't use these apps just because they are open source, I use them because they are the BEST apps in the world at what they do.
 2) How simple it would be to get Windows users to switch to Linux if *all* their favorite apps were crossplatform.   I mean who doesn't want faster, better, cheaper.

In my opinion, if the Adobe products, Quickbooks, and Microsoft Office with Outlook were available on Ubuntu, Windows would be dead in 2 nano-seconds.

With Adobe migrating all their products to their cross-platform AIR framework, we could be there in a few years.  Also, in a few years, the OpenChange project could allow Evolution or Thunderbird to be a real "Outlook for Linux".  Now we need to work in Intuit....

---

### Post by JDShu on 2010-02-05
Now when it comes to computers, I just read and hear about stuff. But what I do hear is that ActiveX is really insecure. Isn't it really scary to let a payroll program use ActiveX?

---

### Post by Grenage on 2010-02-05
> In my opinion, if the Adobe products, Quickbooks, and Microsoft Office with Outlook were available on Ubuntu, Windows would be dead in 2 nano-seconds.

There's rather a bit more to Windows than a few applications.  Easy centralised management is one of the main reasons big corps use MS products.

---

### Post by timmy_sprinkles on 2010-02-05
> **HDave said:**
> 
In my opinion, if the Adobe products, Quickbooks, and Microsoft Office with Outlook were available on Ubuntu, Windows would be dead in 2 nano-seconds.

I doubt Windows would be destroyed that quickly. If I was to be the head of a big corporation, I'd want a product that has liability.

---

### Post by SecretCode on 2010-02-05
> **Grenage said:**
> Easy centralised management is one of the main reasons big corps use MS products.

No ... easy centralised management has been developed for Windows networks because big corps use Windows. Big corps use Windows because it's too difficult to change. 

> **timmy_sprinkles said:**
> If I was to be the head of a big corporation, I'd want a product that has liability.

There are plenty of companies providing Linux server platforms and support with contracts. If a market develops for corporate Linux desktops, companies will offer contracted support.

---

### Post by SecretCode on 2010-02-05
Back on topic, I'm all for cross-platform apps. The Mozilla family, OpenOffice, VLC, Eclipse, and many smaller things like Tomboy.

---

### Post by doas777 on 2010-02-05
> **JDShu said:**
> Now when it comes to computers, I just read and hear about stuff. But what I do hear is that ActiveX is really insecure. Isn't it really scary to let a payroll program use ActiveX?

activeX is not inherently insecure, any more than any programming technology is. i can write a program to delete all my files. is that a security hole or a feature?

activeX is a means to access the MS Common Object Model (COM) for programming access, when the code is being run from a browser, but is designed to be executed on the client machine (like web java or javascript) rather than on the server (like ASP, JSP, HSP, CF, etc). just think of COM as a runtime like java or .net. 

so like any programming technology, activeX is neither good nor evil. it all comes down to the trust you place in the coder.

---

### Post by pwnst*r on 2010-02-05
> **HDave said:**
> 

In my opinion, if the Adobe products, Quickbooks, and Microsoft Office with Outlook were available on Ubuntu, Windows would be dead in 2 nano-seconds.



That's far fetched and would never happen.  There are lots of other programs that are specific to the Windows environment (desktop or server) that would make your claim negligible.  Also, it's nice to have more choices for an OS, proprietary or not.

---

### Post by doas777 on 2010-02-05
> **SecretCode said:**
> No ... easy centralised management has been developed for Windows networks because big corps use Windows. Big corps use Windows because it's too difficult to change. 

There are plenty of companies providing Linux server platforms and support with contracts. If a market develops for corporate Linux desktops, companies will offer contracted support.

see, I disagree a little, just because i've seen some of the alternative systems like Novell 6's eDirectory/zenworks. it's just not good compared to AD/GP.

I advised my CIO last year, that while I woudl love to see us move more stuff to linux, we would lose the enterprise-zen-one-spiffyness that we had spent creating. our customers are our workstation users primarily, so client configuration is a very important part of our infrastructure.

---

### Post by SecretCode on 2010-02-05
> **doas777 said:**
> see, I disagree a little, just because i've seen some of the alternative systems

I'm not saying the windows management solutions aren't among the easiest and best - I'm just saying it's only that way because windows is dominant. I was around at the dawn of "Microsoft LAN Manager". Things have come a **long** way.

It's all part of the "lock in". And no other vendor or technology can change that in a big way in a short time.

---

### Post by Giant Speck on 2010-02-05
LOL forced...

---

### Post by koenn on 2010-02-05
> **doas777 said:**
> 
I advised my CIO last year, that while I woudl love to see us move more stuff to linux, we would lose the enterprise-zen-one-spiffyness that we had spent creating. our customers are our workstation users primarily, so client configuration is a very important part of our infrastructure.
Isn't that actually what SecretCode said : you're invested in Windows, and changing would be too hard / costly (money, time, and effort-wise).

And you *need* AD/GPO because you're dealing with an environment that's basically a collection of *personal* computers that got networked.
An environment built around, say, server-based computing, would require far less AD and GPO.

---

### Post by HDave on 2010-02-05
> **JDShu said:**
> Now when it comes to computers, I just read and hear about stuff. But what I do hear is that ActiveX is really insecure. Isn't it really scary to let a payroll program use ActiveX?

I think so.  It's also flaky.   Then again, what Intuit product isn't flaky?

---

### Post by HDave on 2010-02-05
> **Grenage said:**
> There's rather a bit more to Windows than a few applications.  Easy centralised management is one of the main reasons big corps use MS products.

Samba4 + OpenLDAP + GOsa + PAM = Identity managed pc infrastructure

I admit it is not quite as put together as AD, but soon it will surpass AD.

---

### Post by HDave on 2010-02-05
> **SecretCode said:**
> Back on topic, I'm all for cross-platform apps. The Mozilla family, OpenOffice, VLC, Eclipse, and many smaller things like Tomboy.

It was actually the use of Firefox and Thunderbird on Windows that led me to try Ubuntu in the very first place!

---

### Post by sudoer541 on 2010-02-05
> **HDave said:**
> This week I was forced to use Windows again for the first time in a long time because the Intuit online payroll system (incredibly) uses activeX controls and my usual firefox-user-agent-switch trick didn't work.  :-(

In order to make the experience bearable, I took it upon myself to set up some of my favorite Ubuntu apps:
 * Tomboy
 * KeePass2
 * Pidgin
 * SSH Client
 * Openoffice
 * Firefox

I skipped Thunderbird and Songbird because I don't plan on using that machine very much.  

Anyway, it really made the entire experience bearable and also got me thinking two thoughts:

 1) I don't use these apps just because they are open source, I use them because they are the BEST apps in the world at what they do.
 2) How simple it would be to get Windows users to switch to Linux if *all* their favorite apps were crossplatform.   I mean who doesn't want faster, better, cheaper.

In my opinion, if the Adobe products, Quickbooks, and Microsoft Office with Outlook were available on Ubuntu, Windows would be dead in 2 nano-seconds.

With Adobe migrating all their products to their cross-platform AIR framework, we could be there in a few years.  Also, in a few years, the OpenChange project could allow Evolution or Thunderbird to be a real "Outlook for Linux".  Now we need to work in Intuit....


cool story bro!!!

---

### Post by sudoer541 on 2010-02-05
btw try windows 7 and your face will turn from this ---->:( to this ---->:D

guaranteed!!!

---

### Post by Icehuck on 2010-02-05
> **HDave said:**
> 
 * Pidgin

BEST apps in the world at what they do.
 

Pidgin best IM app in the world? O'RLY?

---

### Post by RiceMonster on 2010-02-05
lol @ Openoffice being the best

Maybe in terms of price.

---

### Post by Dharmachakra on 2010-02-05
> **RiceMonster said:**
> lol @ Openoffice being the best

Maybe in terms of price.

Trueeee that. I'd use Office 2007 over OpenOffice any day.

I'm quite happy with the number of cross-platform applications flying around. Most of the applications I used everyday are available on Windows. I just wish some of the OSX applications my sister uses were available for Linux.

---

### Post by HDave on 2010-02-05
> **RiceMonster said:**
> lol @ Openoffice being the best

Maybe in terms of price.

You are so right -- forgot that I had that lumped in there.  I am a daily user open office, and I HATE HATE HATE it.  But that's a story for another thread...

---

