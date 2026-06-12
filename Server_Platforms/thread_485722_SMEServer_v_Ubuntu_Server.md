---
title: "SMEServer v Ubuntu Server"
date: 2007-06-27
forum: Server Platforms
---

### Post by AlistairH on 2007-06-27
I have a little experience of SMEServer v 7 having installed a few servers for a client. However, since I'm keen to extol the virtues of Ubuntu on the desktop instead of Windows I'm wondering if it would make more sense to concentrate my server efforts on Ubuntu as well.

Given that my knowledge of linux in general is limited, though it is getting better all the time, I'm interested in finding out what options are available to me for the quick and easy installation and administration of Ubuntu server keeping in mind that I am very much from a GUI background and found the SMEServer web based admin facility ideal.

Also, as I am not available to my clients 24/7 I envisage situations were some of my clients may need limited administrations rights - adding/modifying users settings and passwords for example. They would almost certainly require an easy to use GUI administration interface.

In the vast majority of cases, the servers would be acting as file/print servers though the killer application would undoubtedly be a MS Exchange alternative. Which is interesting in itself in that none of my clients, of which the largest has 30 users, uses Exchange to anything like the level it is capable of. Simple email and the sharing of diaries is generally their limit.

Also, although I'd like to introduce my clients to Ubuntu on the desktop, realistically it is unlikely that many would move away from Windows - simply because of the impact it would have on the users. 'Old dogs and new tricks' springs to mind. Consequently, the server would need to run Samba.

So to sum up, I'm looking to implement Ubuntu server as my linux offering of choice rather than SMEServer and would appreciate your thoughts on the best ways to provide an easy to use GUI based administrative function without the need to get one's hands dirty - at least some of the time anyway.

Thanks in advance.

Alistair

---

### Post by drifting on 2007-06-30
I have used both SME and Ubuntu for a while.

If you are selling a product to customers stick with SME, it is a dedicated server product that takes the pain out of configuration.

If however you want to know how the other half live, and further your knowledge then Ubuntu etc is the way to go. EXPECT a great deal of pain and frustration, poor documentation written by academics for academics. Ubuntu was my choice because of the great forum and user contributed docs (They have saved my bacon so many times). Man pages are the spawn of satan as far as I am concerned.

For the desktop Ubuntu is the dogs!

Regards Paul.

---

### Post by darkog on 2007-06-30
> **AlistairH said:**
> I have a little experience of SMEServer v 7 having installed a few servers for a client. However, since I'm keen to extol the virtues of Ubuntu on the desktop instead of Windows I'm wondering if it would make more sense to concentrate my server efforts on Ubuntu as well.

Ubu server is quite good. I would not use it if 99.9% reliability is expected. It's a little too "bleeding edge" for my tastes.

> **AlistairH said:**
> Also, as I am not available to my clients 24/7 I envisage situations were some of my clients may need limited administrations rights - adding/modifying users settings and passwords for example. They would almost certainly require an easy to use GUI administration interface.

[Webmin]("http://www.webmin.com/") is a very popular one which has been around for a while, has lots of docs and a fairly large community. Web  based.

> **AlistairH said:**
> In the vast majority of cases, the servers would be acting as file/print servers though the killer application would undoubtedly be a MS Exchange alternative. Which is interesting in itself in that none of my clients, of which the largest has 30 users, uses Exchange to anything like the level it is capable of. Simple email and the sharing of diaries is generally their limit.

This reasoning does not really add up. Your clients also probably only use 5% of the functionality of Word,  doesn't mean you are going to try to switch them to Abiword or WordPad?

There are a lot of MS Exchange replacements & clones out there  --- what you DON'T want to do is convince your clients to go with something that might get the life support plugged out of it.  An example being the Hula project, where is was [touted]("http://software.newsforge.com/article.pl?sid=05/04/18/2024247&tid=74&tid=132") as the Exchange killer with a big company behind it, only to have the carpet [pulled]("http://linux.wordpress.com/2006/11/29/novell-abandons-hula/") from under it's legs. 

What drives Exchange popularity is the Outlook mail client and mobile devices such as Blackberries and Treo's. If you can convince them to move away from Outlook -- that would be a step in the right direction. The mobile devices are harder because most of them come ready for Outlook and Exchange out of the box. 

Try to get them to switch to Thunderbird or something and take it from there. 

> **AlistairH said:**
> Also, although I'd like to introduce my clients to Ubuntu on the desktop, realistically it is unlikely that many would move away from Windows - simply because of the impact it would have on the users. 'Old dogs and new tricks' springs to mind. Consequently, the server would need to run Samba.

You could phase it in -- reuse/recycle an old machine, put a ver. of Ubu on it  and get them to slowly get used to it.

---

