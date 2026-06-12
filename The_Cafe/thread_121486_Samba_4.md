---
title: "Samba 4"
date: 2006-01-25
forum: The Cafe
---

### Post by KingBahamut on 2006-01-25
"Samba creator Andrew Tridgell has officially released a technology preview of Samba 4 at the Linux.conf.au conference in New Zealand, ending a three-year wait for users. But wait before upgrading those servers. 'It may eat your cat,' says the Samba team in a statement, 'but is far more likely to choose to munch on your password database.'" From the article: "'Samba 4 supports the server-side of the Active Directory logon environment used by Windows 2000 and later, so we can do full domain join and domain logon operations with these clients,' the group said in a statement on its Web site, noting this feature was 'the main emphasis' for the new software."

External Links
[http://www.zdnet.com.au/news/software/soa/New_Samba_targets_Active_Directory/0,2000061733,39234687,00.htm](http://www.zdnet.com.au/news/software/soa/New_Samba_targets_Active_Directory/0,2000061733,39234687,00.htm)


All I have to say it, Yeah. AD server-side recognition. 

Of course, I dont think im brave enough to actually implement it yet.

---

### Post by SlowJet on 2006-01-25
Best news I've seen on the Ubuntu site concerning development.

Here is the release notes.
(If only I knew how to make deb's?


[http://us1.samba.org/samba/history/samba-4.0.0tp1.html](http://us1.samba.org/samba/history/samba-4.0.0tp1.html) 

SJ

---

### Post by BSDFreak on 2006-01-25
[quote=KingBahamut]"Samba creator Andrew Tridgell has officially released a technology preview of Samba 4 at the Linux.conf.au conference in New Zealand, ending a three-year wait for users. But wait before upgrading those servers. 'It may eat your cat,' says the Samba team in a statement, 'but is far more likely to choose to munch on your password database.'" From the article: "'Samba 4 supports the server-side of the Active Directory logon environment used by Windows 2000 and later, so we can do full domain join and domain logon operations with these clients,' the group said in a statement on its Web site, noting this feature was 'the main emphasis' for the new software."

External Links
[http://www.zdnet.com.au/news/software/soa/New_Samba_targets_Active_Directory/0,2000061733,39234687,00.htm]("http://www.zdnet.com.au/news/software/soa/New_Samba_targets_Active_Directory/0,2000061733,39234687,00.htm")


All I have to say it, Yeah. AD server-side recognition. 

Of course, I dont think im brave enough to actually implement it yet.[/quote]

It's somewhat nice but from what i have seen it has resulted in a load of .core.

I'll give it 6-8 or i'll convert the entire networking subsections to a better methology than SMB.

Vista will bring a VERY nice NFS implementation so i don't know why anyone would bother with SMB for dev.

---

### Post by KingBahamut on 2006-01-25
While it is still early to tell what will happen with v4 of Samba, it isnt premature to be excited about it. 

Honestly all attempts on Microsoft's part to make unix interoperability work has been if anything a "joke".  I remain skeptical on anything that MS promises will work on the fly in the realm of interoperability, specially where unix is concerned.

---

### Post by BSDFreak on 2006-01-25
[quote=KingBahamut]While it is still early to tell what will happen with v4 of Samba, it isnt premature to be excited about it. 

Honestly all attempts on Microsoft's part to make unix interoperability work has been if anything a "joke".  I remain skeptical on anything that MS promises will work on the fly in the realm of interoperability, specially where unix is concerned.[/quote]

You know, being uninformed and ranting doesn't really add anything to any discussion.

It's not harder than to use google, i think even you can manage that.

It's not a "promise" it's the current beta implementation.

You'd think that people on this forum would know how to use a search engine but nuh -uh... windows is BAAAAAAAAAAAAAAAAD, nothing known will ever change that for some users that refuse to act as if they were actually adults.

---

### Post by tufkakf on 2006-01-25
[QUOTE=KingBahamut]While it is still early to tell what will happen with v4 of Samba, it isnt premature to be excited about it. 

Honestly all attempts on Microsoft's part to make unix interoperability work has been if anything a "joke".  I remain skeptical on anything that MS promises will work on the fly in the realm of interoperability, specially where unix is concerned.[/QUOTE]

Not to mention that NFS is terrible, SMB is better and that Samba4 certainly is one of the most exciting things hapening in Linuxland at the moment.

---

### Post by BSDFreak on 2006-01-25
[quote=tufkakf]Not to mention that NFS is terrible, SMB is better and that Samba4 certainly is one of the most exciting things hapening in Linuxland at the moment.[/quote]

SMB sucks hairy donkey balls, NFS in it's latest implementation is pretty damn awesome.

I know where you are coming from, five years ago i'd say the same thing, with the latest developments i'd say that SMB is pure crap in comparison though.

---

### Post by KingBahamut on 2006-01-25
BSDFreak, I never ascribed to the windows fight. I learned on a Sun machine long before windows was a thought, and mainframes before that. So Im not a windows hater by reason of use, I just never had a use for it to start. 

Heck back then SunOS was BSD and not SystemV , I wish wed see a return to those days.

---

### Post by KingBahamut on 2006-01-25
As far as anything else goes however, I will say that both SMB and NFS have merit. The technical merits of Vista have yet to be seen. Beta 1 was in my opinion a good thing for MS , showing them that cramming too much into one release is detrimental. Thus the actual release showing a less of a percentage of release features (WinFS included, which for all intents and purposes would help them , and I have no idea why they are excluding it).  Of course most of this is just as promising as Monad , which from what I have read (ORielly's book on Monad [http://www.amazon.com/gp/product/0596100094/qid=1138216159/sr=8-1/ref=pd_bbs_1/104-8814244-5083148?n=507846&s=books&v=glance](http://www.amazon.com/gp/product/0596100094/qid=1138216159/sr=8-1/ref=pd_bbs_1/104-8814244-5083148?n=507846&s=books&v=glance) ) is a mockery of anything remotely resembling shell scripting or anything desireable out of that.  Still to praise about the these merits in Vista now is certainly premature if anything else. Ill give Vista its fair shot "When I see it working", not in beta, and not just talk from developers and users, not in discussions on a forum based on what you read. Working. Thats when Vista gets its fair shot from me.

---

### Post by BSDFreak on 2006-01-25
[quote=KingBahamut]BSDFreak, I never ascribed to the windows fight. I learned on a Sun machine long before windows was a thought, and mainframes before that. So Im not a windows hater by reason of use, I just never had a use for it to start. 

Heck back then SunOS was BSD and not SystemV , I wish wed see a return to those days.[/quote]

You'll have to excuse me, that rant about MS not being capable doesn't ring well with their new network stack that is fuckinge awesome so i just put you down as an ms hater, my mistake.

Yeah, the BSD init makes more sense. but then again, there are a few BSD's out there and even some Linux's like Slack that has taken the init to heart.

'tis all good with me though, yet i think that the experimental versions of NFS are showing some things that SAMBA lack.

Anywayz, sorry for the harsh words.

Stay strong!

---

### Post by tufkakf on 2006-01-25
NFS still sucks, but anyway, the big news is not about SMB, or NFS, but that Samba can now work as an AD controler, which is awesome. Samba can now really replace AD in millions of companies. Great!

---

### Post by KingBahamut on 2006-01-25
Its not a matter of hate BDSF, just a matter of proof. When Microsoft proves to me they have a viable and functioning product, and one that will do what they say it will do, then Ill be happy to laud it. Until then , I remain skeptical for whatever of a number of reasons. The current release build for instance and its annoying Windows Defender aspect. How far can Microsoft dumb down the interface to the user and still remain smooth operation wise. From what Ive read on Defender it asks questions for EVERYTHING that the OS does, on whatever level that access occurs. 

Of course in trying to garuntee security, which for all intents and purposes they cant , so why try, they come to a user interface that is both annoying and obtrusive. Those facts alone discount any great functionality , NFSwise or Network Stack-wise , that the OS can provide.  Along with SaaS stuff like AV and AntiSpyware, both of which shouldnt cost money to the user( what is MS quoting its subscription prices for on both of those fronts yearly? ), and block out the right of companies like Symantec and Mcafee to do business with them makes Vista if anything as undesireable as it comes. 

Even worse than that, Unsigned drivers wont run on Vista, or so its been stated, to garuntee authenticity. Thats just pure greed in my opinion. That just blocks out the hardware manufacturers that want to build hardware to run on MS product but cant afford the money to pay them.

Now those alone are only a fraction of the things I could complain about Vista based on what Ive heard. The negatives are the same , if not outweigh, the positives for using the product. 

WinFS wont even be implemented into the final retail release , another aspect of Vista that makes it undesireable to me until its implemented. 

------------------------------------

Back to Samba, Stay on Track BSDFreak. 

yes I think this is a positive moving direction for interoperability. There are still hundreds of arch's that are running win2k , and as its becomes a legacy product, Samba Driven DCs can give those companies new life to their server base without shelling more money. Novell as a company already targets legacy 2k and nt4 companies , this kind of development will only drive its success more.

---

### Post by BSDFreak on 2006-01-25
[quote=tufkakf]NFS still sucks, but anyway, the big news is not about SMB, or NFS, but that Samba can now work as an AD controler, which is awesome. Samba can now really replace AD in millions of companies. Great![/quote]

Yeah, that being x5 as fast as SMB because of the native implementation sucks ASS!

Christ i wish that people woul take a clue and do a search at least...

---

### Post by BSDFreak on 2006-01-25
[size=1]*Removed by Artificial Intelligence*[/size]

---

### Post by tufkakf on 2006-01-25
[QUOTE=BSDFreak]Yeah, that being x5 as fast as SMB because of the native implementation sucks ASS!
[/QUOTE]
How is smb not native???
Anyway, I can only repeat it, this is _not_ about NFS vs. SMB.

[QUOTE=BSDFreak]
Christ i wish that people woul take a clue and do a search at least...[/QUOTE]
I can certainly agree with you here...

---

