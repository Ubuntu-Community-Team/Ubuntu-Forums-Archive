---
title: "Active Directory"
date: 2006-04-08
forum: Server Platforms
---

### Post by chimpus on 2006-04-08
Does exactly what it says on the subject.

More of a general linux subject but If or when will Linux have an Active Directory solution / equal ( I like AD)???

Any thoughts

---

### Post by LordHunter317 on 2006-04-08
[QUOTE=chimpus]Does exactly what it says on the subject.

More of a general linux subject but If or when will Linux have an Active Directory solution / equal ( I like AD)???

Any thoughts[/QUOTE]Possibly with Samba 4.  That's the goal of the v4 release, at any rate.

---

### Post by baastie on 2006-04-09
It kinda already has with OpenLDAP en definitely with eDirectory from Novell...
But eDir is only 'supported' on SuSE and ( I still believe ) Red Hat...

---

### Post by LordHunter317 on 2006-04-09
[QUOTE=baastie]It kinda already has with OpenLDAP en definitely with eDirectory from Novell...
But eDir is only 'supported' on SuSE and ( I still believe ) Red Hat...[/QUOTE]
No, LDAP isn't even remotely comparable to AD.

---

### Post by baastie on 2006-04-09
I said 'kinda' :) , 

but if you're putting it that way, samba 4 will do AD stuff, but not nearly the whole AD stuff...

---

### Post by rverrips on 2006-04-22
Apologies - I've removed my posting to avoid a flame-war on a topic which is obviously very debatable and totally non-ubuntu related ...

---

### Post by LordHunter317 on 2006-04-22
> **rverrips]Active Directoy is what Microsoft gave the networking world in response to the Novell Directory Services (i.e. NDS) - NDS originally only ran on Novell Netware and simply put, was a centralised solution to manage everything relating to netware, from users and groups, to workstations, to applications and their installation / deployment, (with ZENworks), to printer servers, to printers, to backup-queues, etc. etc.[/quote]Not quite.  The NT3.5 domains stuff was the response to NDS and Zenworks, though it didn't see serious use until NT4. AD came much, much later.  MS is still trying to get the world to move from NT4 PDCs to AD in some incarnation.

It also needs to be made clear that NDS + Zenworks is required to do everything above, and Zenworks is utter crap.

> Microsoft introduced Active Directory to aim an be the same and but (and this is a personal perspective) they failed terribly.Nonsense.  They have the best directory server and network management stuff out there.

>  If you've every tried to figure out why your entire network can't access the internet only to find that the Microsoft DNS server isn't working 'cause of some "drag-drop" you might share this view. Don't blame your inability to use the tools on MS.  I've never had this problem.

> Although tight integration exists between Exchange 2000/2003 and AD, striking example of how AD isn't "there yet" can be seen in how Microsoft Products like Systems Management Server and Operations Manager each contain their own data storage facilities - Admittedly they all "talk" together and sync with Active Directory,And?  LDAP isn't really a generally purpose data store, and generally has terrible write performance.  SMS and OM need to store more data than that.

> but Novell made sure that all the data storage for ZENWorks was/is done directly in NDSYou've failed to show how this is a positive.

> It's thus no surprise that NDS has since been reworked and is now called eDirectory and can be used for Linux environments, and to manage all Novell software that runs on Linux (Linux is a loose term here, as it only really includes Suse) servers and workstations, as well Windows environments -Not quite.  Again, you must also have Zenworks.  eDirectory is exclusive of that.

> Example is Groupwise (Novell's Exchange Challenger) user and agents are all managed purely through eDirectory.Just like Exchange?  You've failing to show how Novell is better.  I think you're fanboi at this point said:**
> Microsoft are apparently addressing these concerns with Windows Server 2003 SR2What concerns?  2003 R2 was already released.  Did you even know what day it is?  

> but I doubt AD will be as integrated a solution as eDirectory anytime soon -AD is far more integrated then you seem to believe.  I'm not even sure you know why SMS doesn't store everything in AD, or why it shouldn't.

> I believe Novell is aiming purely at the corporates and solutions for them.Which is why everyone is still using Netware...

> There's been talk 'round Redhat who took the Netscape Directory Services and renamed to be Redhat Directory servers, but I haven't got any working experience with it.Fedora Directory Server, you mean.

> Anyway, NDS (i.e. eDirectory) and AD both have the ability to publish the information they contain through the LDAP protocol, but they're by no means intended to be LDAP servers only.You're wrong about the former.

> So to answer your question, Linux has something MUCH better than Active Directory, if you're looking for a centralised managed point of users and groups, it's call Network Information Services,Now I know you have no clue what you're talking about.  Things like LDAP were built in a response to the terrible hell that is NIS.  Hell, *even Sun who wrote the NIS protocol is moving people to LDAP and Kerberos5.* 

> I don't know of any projects that are actively seeking to be a comprehensive directory service for cross-platform applications and resources other then Novell eDirectory.Samba, as I said, will emulated Active Directory in version4.  It will be usuable for both Windows, Linux, and several UNIX.

Your gross ignorance on this matters isn't helping anyone.

---

### Post by baastie on 2006-04-22
" Not quite. The NT3.5 domains stuff was the response to NDS and Zenworks,  though it didn't see serious use until NT4. AD came much, much later. MS is still trying to get the world to move from NT4 PDCs to AD in some incarnation.

It also needs to be made clear that NDS + Zenworks is required to do everything above, and Zenworks is utter crap"

Uhmm, the NT3.5 and NT 4 crap was to compete with netware 3 bindery and NetWare 4 ( first NDS release ). Since NT4 domain structure couldn't remotely compete with NDS M$ response was Active Directory, which started to work after they bought Banyan Systems ( Banyan Vines Directory ).

As for ZENworks being crap... I'm working on both sides, including the darkside. And MS has nothing that works as good as ZENworks..

---

### Post by LordHunter317 on 2006-04-23
[QUOTE=rverrips]Apologies - I've removed my posting to avoid a flame-war on a topic which is obviously very debatable and totally non-ubuntu related ...[/QUOTE]Which is rather silly, seeing as the entire post is quoted, and I have no intention of deleting anything.

[quote=basstie]Uhmm, the NT3.5 and NT 4 crap was to compete with netware 3 bindery and NetWare 4 ( first NDS release ).[/quote]And?  That doesn't change the correctness of my response: that was the direct competition when NDS was first released.  Active Directory didn't come until much, much later.  Too much to be a practical competitor, and Netware was already mostly dead to NT4 at that point.

NT4 is in fact so popular, I know several shops that still run it in large quantities (though mostly on the desktop) and are slowly phasing it out.

> As for ZENworks being crap... I'm working on both sides, including the darkside. And MS has nothing that works as good as ZENworks..The industry disagrees you with heavily.  No one uses Netware anymore.  No one uses ZENworks on Linux, even.

---

### Post by baastie on 2006-04-23
[QUOTE=LordHunter317]Which is rather silly, seeing as the entire post is quoted, and I have no intention of deleting anything.[/QUOTE]

:) 

> And?  That doesn't change the correctness of my response: that was the direct competition when NDS was first released.  Active Directory didn't come until much, much later.  Too much to be a practical competitor, and Netware was already mostly dead to NT4 at that point.

I disagree on that point ( of NetWare already being dead ), NetWare was losing ground to NT4, but got it's *** kicked when W2K with AD was launched
and now with 2003 it's even more difficult. But I do see that many of our customers are interested in ( all ) the linux stuff from Novell.

>  NT4 is in fact so popular, I know several shops that still run it in large quantities (though mostly on the desktop) and are slowly phasing it out. 

As was the case with NetWare 3....

>  The industry disagrees you with heavily.  No one uses Netware anymore.  No one uses ZENworks on Linux, even.

That doesn't mean that MS has better tools to do the same stuff. 'If' you have eDirectory on *nix, Windows or Netware or run it in combination with AD and deploy ZENworks it manages your Windows clients with ease ( even without the Novell Client... )....

I for one hope that the linux part will do Novell good. And for linux it isn't bad either...

---

### Post by LordHunter317 on 2006-04-23
[QUOTE=baastie]I disagree on that point ( of NetWare already being dead ), NetWare was losing ground to NT4, but got it's *** kicked when W2K with AD was launched
and now with 2003 it's even more difficult.[/quote]It was pretty dead in the enteprise pre-AD.  The reason being was that you could run NT4 on the desktop and the server.  You couldn't do that with Netware.  That killed it.  It wasn't totally dead, but AD was just a final blow rather than the main strike.  That's the important part.  Calling AD a direct competitor implies it was the main competition, which isn't entirely truthful.  MS was already competiting, and winning, for sometime.

> As was the case with NetWare 3....Note *was*.  My point is lots of huge companies still have lots of NT4 desktops today.  That being said, the few Netware shops left will probably run Netware forever.

> That doesn't mean that MS has better tools to do the same stuff.You'll have to define 'better' then.  Nearly the whole world clearly feels MS' tools are better.

---

### Post by baastie on 2006-04-23
The difference was not running NT4.0 on the server and desktop. The big difference was Exchange ( because of Outlook ), Terminal Server ( with Citrix making it usefull back with NT4.0 ), the lack of an ( decent ) IP stack with NetWare till 5.x. and programming with dll vs nlm's...

And I don't think the whole world disagrees, there are still Novell shops running, people who are thinking of going back to Novell.
Many *nix shops ( look how fast linux is growing the last 2 years and people getting aware of linux ) who will never turn to MS and of course Apple.
If I look at the amount of posts you have put in just these forums i can't image that you are believing it yourself that nearly the whole world feels like that.

Nearly the whole world clearly feels MS' tools are better..... there's allot of ignorance among managers who think Outlook is the world and Bill Gates is president of the US... pfff... Instead of thinking for themselves they just follow because everybody else does..

If MS is the best for you company choose MS but not because you heard it on the golf course !

If you wan't to define better, put up a test environment with mixed AD and eDirectory and then test ZENworks, you'll probably notice that it has come along way since it was 'crap' ( :) ).

---

### Post by LordHunter317 on 2006-04-23
[QUOTE=baastie]The difference was not running NT4.0 on the server and desktop. The big difference was Exchange ( because of Outlook ), Terminal Server ( with Citrix making it usefull back with NT4.0 ), the lack of an ( decent ) IP stack with NetWare till 5.x. and programming with dll vs nlm's...[/quote]Well, all of that helped too, yes :)

> And I don't think the whole world disagrees, there are still Novell shops running, people who are thinking of going back to Novell.They're an almost statistically meaningless quantity.  Even counting NLD and SuSE you still don't have a notable marketshare number.

> Many *nix shops ( look how fast linux is growing the last 2 years and people getting aware of linux ) who will never turn to MS and of course Apple.I've yet to meet a pure UNIX shop.  They're all augmenting their stuff.   Likewise, very few pure Windows shops.

Apple doesn't compete in the server market at all, and as such isn't relevant.

> If I look at the amount of posts you have put in just these forums i can't image that you are believing it yourself that nearly the whole world feels like that.The marketshare numbers clearly prove that MS is the domniant provider for directory services.

> If you wan't to define better, put up a test environment with mixed AD and eDirectory and then test ZENworks, you'll probably notice that it has come along way since it was 'crap' ( :) ).That's still a meaningless definition.

---

