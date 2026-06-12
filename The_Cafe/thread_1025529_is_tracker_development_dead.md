---
title: "is tracker development dead"
date: 2008-12-30
forum: The Cafe
---

### Post by tgpraveen on 2008-12-30
i recently configured and ran tracker as i wanted a good search program.

tracker is ok. though it does not search inside doc or odt type files only inside pdf.

also there are NO search parameters that can be given.

so i wanted to see a roadmap or something. but when i looked up the tracker homepage shows that the last release was like an year ago. this is very sad.

as both vista and mac have very good search progs.

tracker lacks a lot and to see there aint development on it is  kinda depressing.

anyone else knows whats going on?

---

### Post by Sef on 2008-12-30
> so i wanted to see a roadmap or something. but when i looked up the tracker homepage shows that the last release was like an year ago. this is very sad.

as both vista and mac have very good search progs.

tracker lacks a lot and to see there aint development on it is  kinda depressing.

anyone else knows whats going on? 	

The last release was last March, but development is still going on.  Not all applications have frequent releases.

---

### Post by tgpraveen on 2008-12-30
well glad to hear that it is not abandoned. but such long intervals between releases is kinda not good. u know it means that 8.04 and 8.10 have the sames version and who knows maybe even9.04 might have it.

anyways do u know anything abt new features in next release and when it might come out?

---

### Post by dixon on 2008-12-30
Give beagle a try ;)

---

### Post by tgpraveen on 2008-12-30
well wasnt beagle replaced by tracker on ubuntu for some reasons. 

so guess am gonna be with tracker only.

---

### Post by UbuWu on 2008-12-30
> **tgpraveen said:**
> 
anyways do u know anything abt new features in next release and when it might come out?

1 	Tracker 0.6.90
2 	============= (UNRELEASED)
3 	
4 	Major refactoring work
5 	* Cleaner code, some things moved to libaries.
6 	* Refactored DBus interface: Now with introspection! (The method names don't
7 	change, but the objects do, so the client applications must be updated)
8 	* New DB access code (libtracker-db library).
9 	* New binary, tracker-indexer, created so to separate indexing functionality
10 	away from user requests in the daemon.
11 	
12 	GLib's GIO usage
13 	* In-house file monitoring dropped.
14 	* Addition of unit tests.
15 	* TST (GUI search) migrated away from the deprecated gnome-vfs2
16 	
17 	Miscellaneous
18 	* Added support for indexing removable media.
19 	* Added support for the mobile email client, Modest. This adds to Evolution,
20 	Thunderbird, and KMail, among supported clients.
21 	* Added support for OR search operations.
22 	* Initial xesam support.
23 	* New functionality to estimate remaining indexing time period.

---

### Post by pt123 on 2008-12-30
their releases are slow
no updates/blogs or what new features are in the works

sadly this is common among Linux application developers

at one stage Ubuntu seemed keen on having tracker as a key backend component to applications, but luckily they realised how buggy and unstable it was

---

### Post by RPG Master on 2008-12-30
Do you think they would consider using Beagle as the default desktop search?

Trackers junk. :P

---

### Post by BIGtrouble77 on 2008-12-31
> **RPG Master said:**
> Do you think they would consider using Beagle as the default desktop search?

Trackers junk. :P

Junk?  Have you tried Beagle.  It's mono and it sucks.  I really wish Miguel de Icaza would focus his time making gnome better rather than creating mono apps no one asked for.

---

### Post by pt123 on 2008-12-31
please Gnome-Do uses Mono and it is not crap. Likewise Tomboy.

---

### Post by directhex on 2008-12-31
> **RPG Master said:**
> Do you think they would consider using Beagle as the default desktop search?

Trackers junk. :P

Beagle was replaced due to terrible stability issues

---

### Post by BIGtrouble77 on 2008-12-31
> **pt123 said:**
> please Gnome-Do uses Mono and it is not crap. Likewise Tomboy.

GnomeDo and Tomboy are nice little apps, but why did they need to be written in Mono?  The only reason they are written in Mono is to create gnome dependencies on Mono so it can gain some traction.  They could have just as easily been written in python.

---

### Post by gnomeuser on 2008-12-31
> **directhex said:**
> Beagle was replaced due to terrible stability issues

Which have since been solved, luckily. I happily use Beagle on a day to day basis. I have not once been able to hit a 100% cpu case in Beagle the last year. Sadly since Joe Shaw changed jobs we no longer have people dedicated to work on Beagle, mostly dbera who appears to do Beagle work as a sparetime project. So development has slowed a bit.

Tracker seems to be in a sorry situation where they wanted to do a big change and now the diff between head and the last release is huge. Furthermore head isn't really working well apparently, not well enough to get tested by users at least. This again means issues are not being hit. Not exactly release early, release often.

---

### Post by gnomeuser on 2008-12-31
> **BIGtrouble77 said:**
> GnomeDo and Tomboy are nice little apps, but why did they need to be written in Mono?  The only reason they are written in Mono is to create gnome dependencies on Mono so it can gain some traction.  They could have just as easily been written in python.

Yes shame on the developers (who both have absolutely no relationship with Novell) for picking tools they like rather than tools you like to bring you good applications for free.

I always find it extremely annoying when people say this kind of application could just as well have been implemented using X instead of Mono. There were no such applications before, using Mono allowed these developers to focus on innovation instead of implementation. 

Look at the Banshee development, each major release is rapid. Banshee is one of the applications that receive the most patches from first time programmers and programmers from the windows platform tracked on GNOMEs bugzilla. Banshee is stable and with each update comes a multitude of new features. The developers are responsive to problems and feature requests. Any other such applications have not added significantly to the feature set in years. This is down to picking tools that let you do the job and let you do it well - Mono does this.

---

### Post by directhex on 2008-12-31
> **gnomeuser said:**
> I always find it extremely annoying when people say this kind of application could just as well have been implemented using X instead of Mono.

The "I demand this app's developers use Python instead" line is a popular one amongst people who A) don't have a clue how to program and B) believe smear sites full of daily lies which I won't name here

---

### Post by plun on 2008-12-31
> **gnomeuser said:**
> Which have since been solved, luckily. I happily use Beagle on a day to day basis. I have not once been able to hit a 100% cpu case in Beagle the last year. Sadly since Joe Shaw changed jobs we no longer have people dedicated to work on Beagle, mostly dbera who appears to do Beagle work as a sparetime project. So development has slowed a bit.

Tracker seems to be in a sorry situation where they wanted to do a big change and now the diff between head and the last release is huge. Furthermore head isn't really working well apparently, not well enough to get tested by users at least. This again means issues are not being hit. Not exactly release early, release often.

Well... Tracker seems to be alive.

[http://mail.gnome.org/archives/tracker-list/2008-December/thread.html](http://mail.gnome.org/archives/tracker-list/2008-December/thread.html)

You are writing a lot of "skilled FUD" about everything and I don't know where you are getting everything from....???

---

### Post by Xanatos Craven on 2008-12-31
For the record, I'm a tracker user. Don't give enough of a rat's carcass to switch to something else, as long as I can do indexed searches at all.

> **plun said:**
> Well... Tracker seems to be alive.
Pointless statement. Neither that guy, nor anybody else worth responding to, is saying tracker is dead.

> You are writing a lot of "skilled FUD" about everything and I don't know where you are getting everything from....???
And you're making a really vague, antagonizing claim that doesn't point to any specific factual inaccuracy.

---

### Post by gnomeuser on 2008-12-31
> **plun said:**
> Well... Tracker seems to be alive.

[http://mail.gnome.org/archives/tracker-list/2008-December/thread.html](http://mail.gnome.org/archives/tracker-list/2008-December/thread.html)

You are writing a lot of "skilled FUD" about everything and I don't know where you are getting everything from....???

Using the term FUD would imply that I am factually wrong. Yet you have not shown any evidence of me being so, making this a baseless personal attack. I do believe I am entitled to either evidence backing up this claim or an apology, I'll leave the choice up to you.

I happen to be in a situation where I have plenty of time to research matters of personal interest. I know a lot of people in the Linux community and knowing where to go for informed opinions is important. Blogs, forums, mailing lists, personal email, it's all basically legwork it just takes time. Of course 10 years of experience in the Linux community definitely helps as well.

I have always made it a point not to hide my identity, I think if people are to trust what I say it has to be backed by evidence and it can't come from an anonymous voice.

David Nielsen
[http://davidnielsen.wordpress.com/](http://davidnielsen.wordpress.com/)

---

### Post by foxmulder881 on 2008-12-31
I can't stand Tracker. A quick "sudo apt-get remove tracker" command is one of the first things I do when I perform a fresh install of Ubuntu.

Personally, I'm usually quite good at remembering (or a rough idea of) where I put files on my hard drive. And I use the "find" command from a terminal. If I do need to use a gui search tool, I just launch "gnome-search-tool" which works ok.

---

### Post by BIGtrouble77 on 2008-12-31
> **gnomeuser said:**
> Yes shame on the developers (who both have absolutely no relationship with Novell) for picking tools they like rather than tools you like to bring you good applications for free.

I always find it extremely annoying when people say this kind of application could just as well have been implemented using X instead of Mono. There were no such applications before, using Mono allowed these developers to focus on innovation instead of implementation. 

Look at the Banshee development, each major release is rapid. Banshee is one of the applications that receive the most patches from first time programmers and programmers from the windows platform tracked on GNOMEs bugzilla. Banshee is stable and with each update comes a multitude of new features. The developers are responsive to problems and feature requests. Any other such applications have not added significantly to the feature set in years. This is down to picking tools that let you do the job and let you do it well - Mono does this.
What you say is great and all, but the novell/microsoft IP agreement is the problem here.  I agree that developers should use the best tools for the job, but not at the expense of the community. 

From Wikipedia:> 
On November 2, 2006, Microsoft and Novell announced a joint agreement whereby Microsoft agreed to not sue Novell&#8217;s customers for patent infringement.[10] According to Mono project leader Miguel de Icaza,[11] this agreement extends to Mono but only for Novell developers and customers.


Mono may be ok for porting some business related .NET apps, but not for anything else until this IP bs is sorted out.  Native linux apps should NOT be written in mono.  


-bt

---

### Post by Polygon on 2009-01-01
ive tried beagle. i have had much more success in tracker, not to mention the index (for a 35gb partition) was REALLY BIG, like 5 gb or something compared to less then a gb for tracker.

---

### Post by andamaru on 2009-01-01
sorry for thread jacking, but has anyone got mono to index applications, it won't do that on opensuse or Ubuntu for me. You can continue the mono flamewar now.

---

### Post by tgpraveen on 2009-01-01
> **BIGtrouble77 said:**
> What you say is great and all, but the novell/microsoft IP agreement is the problem here.  I agree that developers should use the best tools for the job, but not at the expense of the community. 

From Wikipedia:

Mono may be ok for porting some business related .NET apps, but not for anything else until this IP bs is sorted out.  Native linux apps should NOT be written in mono.  


-bt
well said

---

### Post by directhex on 2009-01-01
> **BIGtrouble77 said:**
> What you say is great and all, but the novell/microsoft IP agreement is the problem here.  I agree that developers should use the best tools for the job, but not at the expense of the community.

"IP" is meaningless. If you mean the Microsoft/Novell customer patent indemnification cross-licensing deal, then everyone loves to talk about Mono, but not the fact that the deal covered thousands of other apps.

> On November 2, 2006, Microsoft and Novell announced a joint agreement whereby Microsoft agreed to not sue Novell&#8217;s customers for patent infringement.[10] According to Mono project leader Miguel de Icaza,[11] this agreement extends to Mono but only for Novell developers and customers.

As with pretty much every other app in SLES in late 2006.

Which patents are you saying Mono violates? If you can identify one, then it can be worked around or rewritten to avoid it.

> Native linux apps should NOT be written in mono.

Are you the one who's going to crash through Free Software developers' windows to say "NO! YOU MAY ONLY CODE FROM THIS LIST OF PERMITTED LANGUAGES"? Mono was explicitly written for native app development, not for porting. DotGNU Portable.NET (The FSF's CLI framework) was developed for porting.

---

### Post by gnomeuser on 2009-01-01
> **directhex said:**
> "IP" is meaningless. If you mean the Microsoft/Novell customer patent indemnification cross-licensing deal, then everyone loves to talk about Mono, but not the fact that the deal covered thousands of other apps.


It's also forgotten that the deal does not cover either Microsoft nor Novell. Just their customers, meaning that Novell e.g. can still sue Microsoft for infringing on their Groupwise patents (remembering that the deal goes both ways).

This means that any project under each unbrella needs to take the same care to avoid patents as always. Hence the stance of the Mono project has always been to workaround patents or get them invalidated should one be potentially infringed upon. To this day this policy has not been enacted, not one patent has been pointed out as being infringed upon. This goes back before the Microsoft/Novell interoperability deal, before Novell even bought Ximian (Miguel and Nat' company which orginally developed things like Evolution and Mono).

The deal does not mean as many people think that Novell have Carte Blanche to infringe on Microsoft patents. They have no such right, they have to show the same care as always. The deal _solely_ deals with the customers of the respective companies. Now how given that is it in Novell or Microsofts best interest to actively and knowingly infringe on patents in each others products.. it simply is not.

---

### Post by BIGtrouble77 on 2009-01-01
> **directhex said:**
> "IP" is meaningless. If you mean the Microsoft/Novell customer patent indemnification cross-licensing deal
You're really nit-picking here, you obviously knew what I meant.  We're on opposite side of this argument that's been rehashed a brazilian times so this is probably not the best place to continue it.

I don't agree with the spirit of the agreement, I think it compromised the community and opened of a channel for more litigation. I also think de Icaza's comment that only novel and it's customers are allowed to use mono is disturbing.

---

### Post by zekopeko on 2009-01-01
> **BIGtrouble77 said:**
> You're really nit-picking here, you obviously knew what I meant.  We're on opposite side of this argument that's been rehashed a brazilian times so this is probably not the best place to continue it.

I don't agree with the spirit of the agreement, I think it compromised the community and opened of a channel for more litigation. I also think de Icaza's comment that only novel and it's customers are allowed to use mono is disturbing.

could you provide a link to Icazas's statement? i'm interested.

---

### Post by BIGtrouble77 on 2009-01-01
> **zekopeko said:**
> could you provide a link to Icazas's statement? i'm interested.

Check out "Mono and Microsoft's Patents" section:
[http://en.wikipedia.org/wiki/Mono_(software](http://en.wikipedia.org/wiki/Mono_(software))

---

### Post by directhex on 2009-01-01
> **BIGtrouble77 said:**
> You're really nit-picking here, you obviously knew what I meant.

But they're enormously different things, and the distinction is paramount.

A patent cross-licensing deal means "you can use our patents, we can use yours, yay". That's NOT what was agreed here, partly because GPLv2 forbids it.

If Microsoft violate a Novell patent (e.g. Novell own patents to the fundamentals of online commerce), then Novell can sue for infringement. The deal says that Novell can sue Microsoft, but may not sue Microsoft customers.

Going after customers is a cheap trick used in assorted disputes - e.g. SCO used it to squeeze people for their $700 Linux licenses. However, the distinction here is critical - it would be EXTREMELY costly for either party to violate patents and end up in a lawsuit. Both companies will still actively seek to avoid each others' patents.

> We're on opposite side of this argument that's been rehashed a brazilian times so this is probably not the best place to continue it.

Really? Opposite sides? Want to explain my position, then?

> I don't agree with the spirit of the agreement, I think it compromised the community and opened of a channel for more litigation.

Possibly. If any patent violation can be proven in anything included in SLES in late 2006, then yes, that could be the case - if either party were to feel that the benefits of litigation outweighed the risks of assorted backlashes.

Personally, I think the FUD and division in the community is more valuable to Microsoft than any attempts to sue anyone with bogus patents.

> I also think de Icaza's comment that only novel and it's customers are allowed to use mono is disturbing.

Great paraphrasing there, well done Wikipedia. Here's the cited link: [http://tirania.org/blog/archive/2006/Nov-04.html](http://tirania.org/blog/archive/2006/Nov-04.html)

Here are some choice quotes which have mysteriously not been mentioned: 

> These are my personal opinions, and do not represent in any way Novell's official position

[quote=miguel]Q: Which Patents Does Mono Infringe?

I do not know of any patents which Mono infringes.

Although Novell provides most of the work to develop Mono, Mono is still a community project with many constituents and collaborators from companies, universities, governments and individuals, and as such we will continue to work and operate as a community project.

This means that we will continue to follow the rules that we have set for ourselves when it comes to patents[/quote]

> Q: Is it now possible to integrate code that uses Microsoft patents today?

Although it is possible, we will not integrate such code, as Mono is a community project.

And, more interestingly, nowhere in that link does the supposed quote used on Wikipedia exist - the citation, added back in November 2006 by user "Jeffreymcmanus" is flat wrong.

---

### Post by BIGtrouble77 on 2009-01-01
> **directhex said:**
> But they're enormously different things, and the distinction is paramount.
I used the term 'IP'. It's about ambiguous as you can get.  
  
> **directhex said:**
> 
A patent cross-licensing deal means "you can use our patents, we can use yours, yay". That's NOT what was agreed here, partly because GPLv2 forbids it.This is what MS has stated: "In addition, Microsoft promised not to assert patents against developers being paid to create code for OpenSuse, Smith said."  MS can still intimidate businesses with litigation even if the the GPL protects them.

> **directhex said:**
> 
Going after customers is a cheap trick used in assorted disputes - e.g. SCO used it to squeeze people for their $700 Linux licenses. However, the distinction here is critical - it would be EXTREMELY costly for either party to violate patents and end up in a lawsuit. Both companies will still actively seek to avoid each others' patents.
Who do you really think funded SCO?  [http://www.businessweek.com/technology/content/mar2004/tc20040311_8915_tc119.htm](http://www.businessweek.com/technology/content/mar2004/tc20040311_8915_tc119.htm)

> **directhex said:**
> 
Really? Opposite sides? Want to explain my position, then?
What's with the defensiveness?  You've made your thoughts pretty clear to this point.

> **directhex said:**
> 
Personally, I think the FUD and division in the community is more valuable to Microsoft than any attempts to sue anyone with bogus patents.
This is unfortunate.  The community really depends on each entity being treated fairly and equally.  When those ideals go out the window then, yes, there will be divisions.  


> **directhex said:**
> 
user "Jeffreymcmanus" is flat wrong.
The problem is that MS' interpretation of this agreement is very different from Novel's.  If you follow Novell's and Icaza's rosy interpretation then you can only look at this as a win win situation.  If you read Steve Ballmer's comments, it's very disturbing. 
[http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9005258](http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9005258)

These guys don't agree on what they agreed on.  I don't like the agreement, it compromised the community, it successfully created divisions and it only served to benefit Novell at everyone else's expense.  

Sorry for thread-jacking. I really would just like to agree to disagree at this point.

---

### Post by gnomeuser on 2009-01-01
> **BIGtrouble77 said:**
> 

The problem is that MS' interpretation of this agreement is very different from Novel's.  If you follow Novell's and Icaza's rosy interpretation then you can only look at this as a win win situation.  If you read Steve Ballmer's comments, it's very disturbing. 
[http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9005258](http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9005258)

These guys don't agree on what they agreed on.  I don't like the agreement, it compromised the community, it successfully created divisions and it only served to benefit Novell at everyone else's expense.  


Because Steve Ballmer wasn't a loudmouth who make unsubstaniated claims about Linux before this deal.. This guy has gone off on Linux for years and what has happened? Absolutely, positively nothing. He doesn't even have a business case to make for actually suing Linux even if we assume that he has the means (which nobody has shown he has). Pretty much every single big client of theirs use Linux as well, they would actively be hurting their own revenue model.

Aside this the OIN would countersue Microsoft using their full patent portfolio, thus creating a climate of mutually assure destruction should such a theorical situation ever occure. Hardly something which is in anyones best interest, let alone Microsofts. 

Now I shall ask anyone who thinks Mono infringes on patents to kindly cease attacking the Mono project, it's developers or users without providing the patent numbers involved. The Mono project unlike most big projects have a policy in place to handle such issues. Please be part of the solution not the problem, by repeating the claim you are only hurting Linux.

---

### Post by BIGtrouble77 on 2009-01-01
> **gnomeuser said:**
> Because Steve Ballmer wasn't a loudmouth who make unsubstaniated claims about Linux before this deal.. This guy has gone off on Linux for years and what has happened? Absolutely, positively nothing. 
That's positively not true.  Ballmer has a loud mouth, he is a moron sometimes, but the corporate enterprise listens to him.  His tactics have had an effect.  

> **gnomeuser said:**
> 
Aside this the OIN would countersue Microsoft using their full patent portfolio, thus creating a climate of mutually assure destruction should such a theorical situation ever occure. Hardly something which is in anyones best interest, let alone Microsofts. 

I agree 100%.  The patent system is the problem.

> **gnomeuser said:**
> 
Now I shall ask anyone who thinks Mono infringes on patents to kindly cease attacking the Mono project, it's developers or users without providing the patent numbers involved. 
I don't personally  think Mono infringes on anything, and I didn't mean to suggest it did.  All I did was point to Microsoft and Novell's statements.  Novell chose to be subsidised by MS at the community's expense.  For as much as Novell has done for the FOSS community(and it has been huge), I don't really trust them to work in the best interest of the community anymore.     

> **gnomeuser said:**
> 
by repeating the claim you are only hurting Linux.
So by not supporting george bush am I a bad american too?

I don't mean to sound abrasive.  I don't mind a little bit of enthusiastic talk, no offence intended.

-bt

---

