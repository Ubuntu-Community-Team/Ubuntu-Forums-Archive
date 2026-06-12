---
title: "Problem at the workplace... Thunderbird/Exchange"
date: 2006-01-26
forum: Server Platforms
---

### Post by DigitalDuality on 2006-01-26
Ok, well i've decided to try out Ubuntu in a business environment from a end user's standpoint.  Unfortunately i, at the moment, use thunderbird to connect to our exchange server.  This i was aware of before i went in to this.

My problem is probably more windows oriented.  It's an Exchange 2003 server.  If i go into the System Manager for Exchange, there's a Pop3 virtual server and an option for me to start it.  SMTP works of course since exchange requires that.

I go to start the POP3 service and it kicks me this error message about not being able to start the service.

Can Exchange handle incoming POP3 and Exchange simuntaneously?   Should i attempt to create a new Pop3 virtual server? How could this effect pre-existing Exchange connections?

---

### Post by localzuk on 2006-01-26
I think this would be better suited to a Microsoft forum. However, from the system that is in use at our university, it should be able to use POP3 and exhange connections at the same time.

---

### Post by DigitalDuality on 2006-01-26
[QUOTE=localzuk]I think this would be better suited to a Microsoft forum. However, from the system that is in use at our university, it should be able to use POP3 and exhange connections at the same time.[/QUOTE]
Well unfortunately MS forums are made up of a bunch of certified @$$holes who don't know the difference between a GUI and an OS, so i tend to avoid them.

If i'd get better help there i'll try it out, but i thought of approaching a rather friendly knowledgable community first. :)

---

### Post by dk_pa on 2006-01-26
Kinda ironic because we had just recently setup a new Exchange 2003 Server on MS Server 2003 and it did the same shit!  Just the usual questions I guess of is it up to date on service packs and stuff.  After the updates that we have ran and SP's on the Exchange server I should try to start it again.  I know, not much help, but kinda just throwing that out there =)

---

### Post by DigitalDuality on 2006-01-26
[QUOTE=dk_pa]Kinda ironic because we had just recently setup a new Exchange 2003 Server on MS Server 2003 and it did the same shit!  Just the usual questions I guess of is it up to date on service packs and stuff.  After the updates that we have ran and SP's on the Exchange server I should try to start it again.  I know, not much help, but kinda just throwing that out there =)[/QUOTE]
All of our service packs and windows updates have been done.  I make sure that gets done the say they come out most of the time.

---

### Post by localzuk on 2006-01-26
That's understandable - being surrounded by MS zealots in my part of the dept should have told me that.

I had a little look around and came up with:

[http://www.msexchange.org/tutorials/Connecting_POP_And_IMAP_Clients_To_MS_Exchange_Server.html](http://www.msexchange.org/tutorials/Connecting_POP_And_IMAP_Clients_To_MS_Exchange_Server.html)
[http://www.windowsnetworking.com/articles_tutorials/Windows_POP3_Service.html](http://www.windowsnetworking.com/articles_tutorials/Windows_POP3_Service.html)
[http://www.isaserver.org/img/upl/exchangekit/2003securepop3/2003securepop3.htm](http://www.isaserver.org/img/upl/exchangekit/2003securepop3/2003securepop3.htm)

Hope these help.

---

### Post by Glut on 2006-01-26
You can run MAPI and POP at the same time - though I'm of the opinion that IMAP is prolly a better bet for a business environment. FWIW doesn't Evolution allow connections through MAPI?

---

### Post by LordHunter317 on 2006-01-26
[QUOTE=DigitalDuality]Well unfortunately MS forums are made up of a bunch of certified @$$holes who don't know the difference between a GUI and an OS, so i tend to avoid them.[/quote]:rolleyes: You're obviously just visting the wrong forums (seriously).

Anyway, don't use POP3, use IMAP.

---

### Post by hscottyh on 2006-01-26
You can use evolution and connect to exchange through the owa interface.

I read my work email at home like this.

---

### Post by SuperMike on 2006-01-26
Why use Exchange? I could rattle off countless problems with it in an M$ forum. My employer, a global company, frustrates and baffles me by continuing to use it with all the problems it has. But that's for another day. Instead, why not just do what the ISPs do? The strategy that the ISPs use works for them and thousands of their users. It should work for any business, as far as I'm concerned. Plus, you can provide more features and options than Exchange. My solution?

* Linux-based IMAP server. Pick from dozens.

* Linux-based LDAP server that blends well with an IMAP server. (If your IMAP server of choice is designed for this.) Pick from dozens of these.

* Mozilla Thunderbird mail and newsgroups reader. And when you connect to a local NNTP server with folders for every company department, it's even cooler!

* Linux-based webmail front end (for those people who prefer that interface). Pick from dozens of these, but some of my favorites are SquirrelMail, Horde, and EdgeDesk.

* NNTP Server (to act as a kind of "Public Folders" with a folder (or more) for each department). Pick from dozens of these.

* For calendaring, give them a shortcut to the web front end for this such as what's provided in SquirrelMail, Horde, or EdgeDesk.

* For an "M$ SharePoint" replacement, if you mix Mambo and something like SquirrelMail, Horde, and especially EdgeDesk, you have a pretty healthy set of features and can start to build department and subworkgroup intranet websites and applications.

---

### Post by LordHunter317 on 2006-01-27
[QUOTE=SuperMike]Why use Exchange? I could rattle off countless problems with it in an M$ forum.[/quote]I'd love to hear some of those.

> Instead, why not just do what the ISPs do? The strategy that the ISPs use works for them and thousands of their users.Because what they're expect to provide isn't what a company is.  I expect an ISP to retain enough mail until I can download it locally (a few MB).  I expect my work to retain all my mail forever (within reason, erring on my side).  And most corporations do tend to that side.

> It should work for any business, as far as I'm concerned.Which shows you've never done any planning or deployment of this before.  If only the storage issues alone make it a bigger deal.

>  Plus, you can provide more features and options than Exchange.No, you cannot.  Are you even aware of what Exchange is capable of?  Statements like this make any comparsion by you highly questionable.  Excatly what can Linux do that Exchange cannot?

> * Linux-based IMAP server. Pick from dozens.Except, it's not that simple.  Depending on your availablity and performance needs, you're probably only limited to one option: Cyrus.  And using Cyrus takes away most of the "flexability" you get on a Linux solution, like Maildirs and the like.  Davecot and Courier don't scale as far as Cyrus does.  So no, it's not that simple.  

pquote]* Linux-based LDAP server that blends well with an IMAP server. (If your IMAP server of choice is designed for this.) Pick from dozens of these.[/quote]Umm, there's only real two free options: OpenLDAP and Fedora Directory Server.  The one isn't scalable or reliable, the other is an undocumented mess.  

> * Mozilla Thunderbird mail and newsgroups reader. And when you connect to a local NNTP server with folders for every company department, it's even cooler!Using NNTP in this day and age for this sort of thing is just dumb.  IMAP shared folders are a superior solution, provided your IMAP server sanely supports them (Courier, plz die kthnxbai)

> * NNTP Server (to act as a kind of "Public Folders" with a folder (or more) for each department). Pick from dozens of these.The very fact you even suggested NNTP makes me question everything you've said.  NNTP isn't mean for 'Public Folders' like activity.  It's mean for newsgroup posting, which means fixed posts that are retained and then deleted.  That doesn't fit well with any corporate retention policy I've ever heard of, unless you gave the end users the ability to cancel the messages they post, and had the ability to save canceled messages forever.

---

### Post by DigitalDuality on 2006-01-27
It's not my call to use or not use exchange.  The system at work was bought and paid for a year ago. It hasn't worn out it's value yet.  

I've been trying to set up a mail server at home on Ubuntu... and i've just about given up and i'm about to go the Mercury/Pegasus route on Win 2k.

---

### Post by cebesius on 2006-08-31
> **DigitalDuality said:**
> Ok, well i've decided to try out Ubuntu in a business environment from a end user's standpoint.  Unfortunately i, at the moment, use thunderbird to connect to our exchange server.  This i was aware of before i went in to this.

My problem is probably more windows oriented.  It's an Exchange 2003 server.  If i go into the System Manager for Exchange, there's a Pop3 virtual server and an option for me to start it.  SMTP works of course since exchange requires that.

I go to start the POP3 service and it kicks me this error message about not being able to start the service.

Can Exchange handle incoming POP3 and Exchange simuntaneously?   Should i attempt to create a new Pop3 virtual server? How could this effect pre-existing Exchange connections?

All of these people trashing MS when they clearly don't have much experience doing any real admin work on such a system.  If you don't have something constructive to say...

I happened upon this thread searching for an answer to my own Thunderbird -> Exchange woes, but unfortunately the topic is unrelated.  BUT, I do know the answer to your question, even if it is from January 2006.  To put this thread to a useful close (for others having the same issue):

1.  Open the Services snap-in under Administrative Tools.
2.  Find the Microsoft Exchange POP3 service, open its properties.
3.  Switch the startup type from Disabled to Automatic. (why MS has disabled it by default is *beyond* me)
4.  Go back to Exchange System Manager and start your Default POP3 Virtual Server.

Please, people, KNOW about a subject BEFORE you talk trash!  ;-)

---

### Post by jimm on 2006-08-31
It is disabled by default because its a security weak point. 

I would investigate the Evolution + Exchange option. Should be a nicer solution for you than POP / IMAP.

There is however, no issue with using POP / IMAP clients against exchange other than the security issues with POP.

I am not sure what your problem was with getting POP started, but if you post the exact error I can probably help you out. It should be fairly simple to get going once all your ducks are in a row :-)

Post a reply if you are still having problems and I'll pitch in... 

Good on ya for trying out Ubuntu in this way! Very keen to see how get on. I have done it before and its quite usable, however you do feel the pain every now and then in the MS world :-) I had to keep a VM of XP handy to help me out every now and then!


Thanks,
James

---

### Post by jimm on 2006-08-31
> **SuperMike said:**
> Why use Exchange? I could rattle off countless problems with it in an M$ forum. My employer, a global company, frustrates and baffles me by continuing to use it with all the problems it has. But that's for another day. Instead, why not just do what the ISPs do? The strategy that the ISPs use works for them and thousands of their users. It should work for any business, as far as I'm concerned. Plus, you can provide more features and options than Exchange. 

I am loath to get into this... but...

Dude... Love or hate MS, Exchange is one of the best Enterprise email solutions out there. There aint much on Linux that comes close. It is in fact why many company's DONT move to Linux backends. There is nothing baffling about using it at all.

For a _start_ email storage for enterprise levels of mail under linux is tricky (mbox and maildirs dont cut it, which means you need to get your head into a DB soltution) and this is one of Exchange's weakest points as well!

Why do you assume ISP's dont use Exchange? I know of many that do... You might find the front-end MTA is sendmail or something, but the backend is Exchange. Even the front-end could be exchange as well with 2003. The MTA in E2003 is much better than in the bad old days. Its RFC compliant and works a lot like sendmail with a nice GUI admin interface. 

As to more features and options on Linux... Have you looked at the MS MTA and or the rest of Exchange? It's pretty feature rich and matches anything I have seen on Linux and in fact exceeds it in most places.

Unfortunatly you can loath MS for its business practises and _some_ of its shoddy software, but a whole ton of what they produce is excellent. Politics aside MS still make the best desktop OS and the best Enterprise email platform IMHO. Now if you want to talk web servers and databases thats another story :-)

Don't get me wrong I am a huge Linux fan, no doubt about it. But I am also a horses for courses type guy, and throwing in Linux cos it aint MS don't fly. My pet hate is companies that chuck in an MS (or any other for that matter) solution just because of the old "nobody got fired for buying IBM (MS)" mentality. You should be putting in the solution / platform that suits your needs best, to often its easy to opt for a bad MS soltuion over a good Linux (or anything) one just because the descision makers are to weak willed or lazy to do an open minded consulting exercise.

With that in mind... Unfortunatly from my point of view, email in the enterprise aint one that suits Linux backends yet...

> **SuperMike said:**
>  

My solution?

* Linux-based IMAP server. Pick from dozens.



Well you can't really. Many of them dont support the storage backends you need to use if you are hosting terrabytes of corporate mail. Another thing you need to worry about incidently is compliance... These days you don't only need to store it until the user has finished with it, but you need to archive it as well. So you have to factor that in...

> **SuperMike said:**
>  
* Linux-based LDAP server that blends well with an IMAP server. (If your IMAP server of choice is designed for this.) Pick from dozens of these.


Again... You dont have that much choice. RedHat or Fedora (maybe). And you still have integration issues. Athough thats not really a problem.

> **SuperMike said:**
>  
* Mozilla Thunderbird mail and newsgroups reader. And when you connect to a local NNTP server with folders for every company department, it's even cooler!

* Linux-based webmail front end (for those people who prefer that interface). Pick from dozens of these, but some of my favorites are SquirrelMail, Horde, and EdgeDesk.


Yup. Have you tried Horde or SquirrelMail with hundreds of users? It don't work to well without some clever load balancing. Exchange is the same with webmail, but it has an architecture designed in that allows you to distribute the load. 

> **SuperMike said:**
>  
* NNTP Server (to act as a kind of "Public Folders" with a folder (or more) for each department). Pick from dozens of these.


Except for the way replication works I guess you could say that...

> **SuperMike said:**
> 
* For calendaring, give them a shortcut to the web front end for this such as what's provided in SquirrelMail, Horde, or EdgeDesk.


For sure. However... Have you ever tried to convince a CIO or exec user (i.e. the folk that decide what email system you are about to use?) to move away from an all integrated PIM client like Outlook? ... Good luck! MS have done Outlook very well and again it is a reason why Linux is still to take off on the desktop. 

> **SuperMike said:**
> 
* For an "M$ SharePoint" replacement, if you mix Mambo and something like SquirrelMail, Horde, and especially EdgeDesk, you have a pretty healthy set of features and can start to build department and subworkgroup intranet websites and applications.


Well SharePoint is another discussion (horses for courses) and I'd agree... Depending on what you are trying to achieve, SharePoint may not be the best option. It is far back in the bunch of CMS/DMS/Collaboration (or whatever it is) tools out there.

Having lived in the corporate messaging (and other places!) world for a while now, Exchange is not a hard choice to make and for all the right reasons! 

Thanks,
James

---

### Post by dazedandconfused on 2006-08-31
Hiya,

If you go into /etc/apt/sources.list and remove the hash from the non ubuntu sites you can install Ximian Connector which will allow you to log into Exchange 2003 and access the shared calender, notes etc. as well as your mail via Evolution.


On Ubuntu, the package is called evolution-exchange. I tried this on our exchange server but it was too old a version (on NT4) and we replaced it with egroupware but I remember getting Evolution working with a win2k exchange server at the last place I worked and it was stable.

Cheers,

Jools

---

