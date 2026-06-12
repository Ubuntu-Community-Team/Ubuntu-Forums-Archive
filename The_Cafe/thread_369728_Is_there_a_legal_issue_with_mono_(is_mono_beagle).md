---
title: "Is there a legal issue with mono? (is mono beagle?)"
date: 2007-02-24
forum: The Cafe
---

### Post by billdotson on 2007-02-24
I heard that one of the higher rated bugs is that mono could possibly be a legal issue.  Mono has been crashing all the time on my system and it gets really annoying

---

### Post by koenn on 2007-02-25
[http://en.wikipedia.org/wiki/Mono_%28software%29](http://en.wikipedia.org/wiki/Mono_%28software%29)

There may be some patent issues (see wikipedia article) but they wouldn't cause your system to crash

---

### Post by billdotson on 2007-02-25
so what patent issues are they?  I am would rather not have to read an entire article, just know the basics.

---

### Post by Kernel Sanders on 2007-02-25
> **billdotson said:**
> so what patent issues are they?  I am would rather not have to read an entire article, just know the basics.

I believe that mono is a little too close to the .NET framework, leading to potential lawsuits from MS

Thats what i've read anyway....

---

### Post by koenn on 2007-02-25
> **billdotson said:**
> so what patent issues are they?  I am would rather not have to read an entire article, just know the basics.
then just read the part about patents
[http://en.wikipedia.org/wiki/Mono_%28software%29#Mono_and_Microsoft.27s_patents](http://en.wikipedia.org/wiki/Mono_%28software%29#Mono_and_Microsoft.27s_patents)
> Mono's implementation of those components of the .NET stack not submitted to the ECMA for standardization has been the source of patent violation concerns for much of the life of the project. In particular, discussion has taken place about whether Microsoft could destroy the Mono project through patent suits. The problematic parts are not the core technologies submitted to the ECMA or the Unix/Gnome-specific parts. The patent concerns primarily relate to technologies developed by Microsoft on top of the .NET Framework, such as ASP.NET, ADO.NET and Windows Forms, i.e. parts composing Mono's Windows compatibility stack. These technologies are today not fully implemented in Mono and not required for developing Mono-applications. Not providing a patented capability would weaken the interoperability, but it would still provide the free software / open source software community with good development tools, which is the primary reason for developing Mono.

---

### Post by Bloodfen Razormaw on 2007-02-25
There is no known patent issue in Mono.  None.  Even Red Hat, which previously had tried to push Java to the exclusion of Mono, using patents as a dubious excuse to do it, has since given in and admitted it has no patent issues.

Being similar to .NET (which is exactly its point, since it is a CLI and BCL implementation) does not make a patent infringement.  Microsoft can't patent .NET.  It can't patent Windows Forms.  It can't patent ASP.NET.  Products cannot be patented.  Microsoft could only patent certain processes or ideas that are part of .NET.  For Microsoft to patent a part of .NET, it must a) not be a part of the standard, and b) must be new.  Since very little of the .NET runtime is new (in fact, its still far less advanced than Smalltalk VMs were 20 years ago), and I assure you, having looked over a huge amount of the BCL code that there is nothing new in terms of the algorithms behind their classes (indeed, most are very out of date; have a laugh at their hashing algorithms if you need a perk-up), and what little in the BCL is new is part of the standard (meaning Microsoft gave up the right to sue over it when they submitted it for standardization), there is not a single thing to worry about.  If anyone can find anything new about the non-standard libraries like Windows Forms or ASP.NET, I'd like to hear what they are.

---

### Post by Kernel Sanders on 2007-02-25
> **Bloodfen Razormaw said:**
> There is no known patent issue in Mono.  None.  Even Red Hat, which previously had tried to push Java to the exclusion of Mono, using patents as a dubious excuse to do it, has since given in and admitted it has no patent issues.

Being similar to .NET (which is exactly its point, since it is a CLI and BCL implementation) does not make a patent infringement.  Microsoft can't patent .NET.  It can't patent Windows Forms.  It can't patent ASP.NET.  Products cannot be patented.  Microsoft could only patent certain processes or ideas that are part of .NET.  For Microsoft to patent a part of .NET, it must a) not be a part of the standard, and b) must be new.  Since very little of the .NET runtime is new (in fact, its still far less advanced than Smalltalk VMs were 20 years ago), and I assure you, having looked over a huge amount of the BCL code that there is nothing new in terms of the algorithms behind their classes (indeed, most are very out of date; have a laugh at their hashing algorithms if you need a perk-up), and what little in the BCL is new is part of the standard (meaning Microsoft gave up the right to sue over it when they submitted it for standardization), there is not a single thing to worry about.  If anyone can find anything new about the non-standard libraries like Windows Forms or ASP.NET, I'd like to hear what they are.

Cool, thanks for the clarification :)

---

### Post by koenn on 2007-02-25
> **Bloodfen Razormaw said:**
> Products cannot be patented. 
[http://en.wikipedia.org/wiki/Image:Ejector_seat_with_patents_crooped.jpg](http://en.wikipedia.org/wiki/Image:Ejector_seat_with_patents_crooped.jpg)

---

### Post by Bloodfen Razormaw on 2007-02-25
If you are trying to make a counterexample, you failed.  A product is a specific implementation of an idea.  You can only patent the general invention.  An automobile is a patentable idea.  The Model T is not.  An ejector seat is patentable.  The Ubuntu brand Linux-Based Ejection Safety System (tm) is not.  The virtual machine is patentable (but not by Microsoft, since they didn't invent it).  The .NET Framework CLI virtual machine is not.

---

### Post by koenn on 2007-02-25
Yes, I was trying to make a counterexample - an ejector seat imo is a product, and can obviously be patented (or the technology that distinguishes from other ejector seats can be patented). But it may all just depend on my and your definition of 'product'. 

I don't know much about patent law, or any law whatsoever - and so far I've only been citing other peoples opinions, i.c. the wikipedia article that says "discussion has taken place about whether Microsoft could destroy the Mono project through patent suits.  ... The patent concerns primarily relate to technologies developed by Microsoft on top of the .NET Framework, such as ASP.NET, ADO.NET and Windows Forms". 

I queried a patent database and found this :
[http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-bool.html&r=17&f=G&l=50&co1=AND&d=PTXT&s1=net&s2=microsoft.ASNM.&OS=net+AND+AN/microsoft&RS=net+AND+AN/microsoft](http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-bool.html&r=17&f=G&l=50&co1=AND&d=PTXT&s1=net&s2=microsoft.ASNM.&OS=net+AND+AN/microsoft&RS=net+AND+AN/microsoft)
 So I'd say Microsoft has indeed patents on (components / parts / procedures / techniques ...in) the .NET environment and it wouldn't supprise me if they, sooner or later, accuse Mono of infringement on those pattents - whether that would be justified or not is a different matter. 

What one can or can not patent depends very much on where you live. This is illustrated by  the discussion on to what extend "software" is patentable.

---

### Post by Bloodfen Razormaw on 2007-02-25
Whether or not they have patents is irrelevant.  The current way the patent office is run in the United States is to only enforce patent law when a challenge is made.  Whether or not a patent is legitimate is rarely evaluated at the time of submission.  Any attempt to enforce a patent would mean that it would be evaluated and almost certainly result in the invalidation of the patent (in the case you give, Microsoft was beaten to the punch by Smalltalk-based web application frameworks by many, many years, and if Microsoft tried to enforce their patent that would come out and they lose the patent).

Some other examples: Microsoft just submitted a patent for their object test bench feature in Visual Studio, an idea which they took from another IDE (and even gave credit to that IDE at the time!).  Amazon's one-click purchasing patent is on the road to invalidation since that feature was first being used over a decade earlier.  Having a patent doesn't matter if it is not legally valid.

---

### Post by koenn on 2007-02-25
drifting away from the mono issue now, but

1- doesn't Microsoft succesfully claim patent infringements, then settles out of court for a pay-off ? 

2- If they'd go to court to enforce their claims, at least they'd have the money to pay an army of lawers to put on a good, long-lasting show  - and the legal costs alone could be enough to bleed their oponents to death

---

### Post by Bloodfen Razormaw on 2007-02-25
Microsoft actually doesn't regularly go after people for patents.  They aren't normally one of the shoddy companies that tries to make all their money collecting and enforcing patents.  Compared to some other software companies Microsoft is not very litigious at all.  Even when they do make patent threats, as against Linux recently, we've seen nothing at all come of it.  And they haven't even tried to claim Mono infringes on patents.

Microsoft can't sue Mono developers, because Mono is developed by Novell and Novell has a patent sharing agreement.  Even if they could and did sue Mono, Novell is more than wealthy enough to take Microsoft on, and even worse, to return fire, as Novell has a tremendous patent portfolio they could leverage against Microsoft.  Attempts to sue users of a product for a legal infringement supposedly committed by the product developer are dubious, at best, and just an empty threat to make money.  SCO has tried that, suing several large corporations that use Linux, saying they are responsible for copyright infringement supposedly committed by Linux developers at IBM, with no success so far.

---

### Post by randeepjalli0 on 2008-02-16
> **Bloodfen Razormaw said:**
> Microsoft actually doesn't regularly go after people for patents.  They aren't normally one of the shoddy companies that tries to make all their money collecting and enforcing patents.  Compared to some other software companies Microsoft is not very litigious at all.  Even when they do make patent threats, as against Linux recently, we've seen nothing at all come of it.  And they haven't even tried to claim Mono infringes on patents.

Microsoft can't sue Mono developers, because Mono is developed by Novell and Novell has a patent sharing agreement.  Even if they could and did sue Mono, Novell is more than wealthy enough to take Microsoft on, and even worse, to return fire, as Novell has a tremendous patent portfolio they could leverage against Microsoft.  Attempts to sue users of a product for a legal infringement supposedly committed by the product developer are dubious, at best, and just an empty threat to make money.  SCO has tried that, suing several large corporations that use Linux, saying they are responsible for copyright infringement supposedly committed by Linux developers at IBM, with no success so far.

I think that goes back to one of the issues involving the partership that Novell and Microsoft made, it only protects customers of the distro's who signed agreements with microsoft. As far as I know, Canonical has no such agreement with Microsoft, so as far as including mono based software, or any software with mono as a dependency I think we need to be asking ourselves,"Is it worth the risk". Personally, I don't think it is and right now, other than beagle, there aren't any real projects written in .NET that seem worth it. As far as including beagle, personally I think we should use something like tracker or one of the other search program, and beagle as well as mono should be in the restricted repo. If anybody from Canonical has any wisdom to shed on this maybe they should chime in?

---

### Post by climatewarrior on 2008-02-16
But Canonical is in Europe and they don't have software patents in Europe. Aren't they supposed to be immune to that?

---

### Post by phrostbyte on 2008-02-16
> **Bloodfen Razormaw said:**
> Microsoft actually doesn't regularly go after people for patents.  They aren't normally one of the shoddy companies that tries to make all their money collecting and enforcing patents.  Compared to some other software companies Microsoft is not very litigious at all.  Even when they do make patent threats, as against Linux recently, we've seen nothing at all come of it.  And they haven't even tried to claim Mono infringes on patents.

Microsoft can't sue Mono developers, because Mono is developed by Novell and Novell has a patent sharing agreement.  Even if they could and did sue Mono, Novell is more than wealthy enough to take Microsoft on, and even worse, to return fire, as Novell has a tremendous patent portfolio they could leverage against Microsoft.  Attempts to sue users of a product for a legal infringement supposedly committed by the product developer are dubious, at best, and just an empty threat to make money.  SCO has tried that, suing several large corporations that use Linux, saying they are responsible for copyright infringement supposedly committed by Linux developers at IBM, with no success so far.

You could to well to read the Novell-Microsoft agreement. The agreement only protects Novell customers from patent lawsuits from Microsoft. Key word is "Novell customer". That doesn't include Ubuntu users, over even openSuSE users. That's why everyone got pissed off at Novell, they basically tried to sell Linux out for some cash (Microsoft gave them hundreds of millions of dollars for this deal).

SCO tried to sue IBM and a wealth of Linux companies and users for copyright infringement, and unlike Microsoft, they have/had no case at all, they have never been able to prove any form of copyright infringement.

Microsoft could be a huge threat to Linux. The only thing stopping them right now is anti-trust law and the Open Invention Network, who owns patents that Microsoft violates with a pact that if Microsoft sues a Linux user, they must retaliate against Microsoft. So there is nothing really to worry about. Patent law is basically nuclear warfare, everyone violates everyone else's patents. So no one except patent trolls (company who try to get generic patents for the sole purposes of suing others) usually attempts to sue.

That being said, Mono likely violates hundreds of Microsoft patents. [Here]("http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-bool.html&r=1&f=G&l=50&co1=AND&d=PTXT&s1=%22ASP.NET%22&OS=%22ASP.NET%22&RS=%22ASP.NET%22") is just one example.

---

### Post by khensucat on 2008-02-16
> **Bloodfen Razormaw said:**
> Microsoft actually doesn't regularly go after people for patents.  They aren't normally one of the shoddy companies that tries to make all their money collecting and enforcing patents.

True. But they seem quite capable at setting up and funding proxies to do this sort of thing for them in spades ;-)

That said, Mono doesn't bother me. I trust the Mr. Shuttleworth didn't make his billions by being stupid, and his "mafia" comments have lead me to believe he wouldn't allow anything into his baby (and now cashcow) Ubuntu that would leave it open to lawsuit. Or at least "successful" lawsuit. 

And, I prefer the Banshee player, so Mono gives me no pause on a moral level, either.

---

### Post by dbera on 2008-02-16
> **randeepjalli0 said:**
>  As far as including beagle, personally I think we should use something like tracker or one of the other search program, and beagle as well as mono should be in the restricted repo. If anybody from Canonical has any wisdom to shed on this maybe they should chime in?

Tracker replaced beagle as the default desktop search in Gutsy and in Hardy beagle was moved from Main to Universe.

---

### Post by MountainX on 2008-04-02
> **Bloodfen Razormaw said:**
> Products cannot be patented.  Microsoft could only patent certain processes or ideas that are part of .NET.  

You have it backwards. Ideas cannot be patented. Products can.

---

### Post by MountainX on 2008-04-02
> **Bloodfen Razormaw said:**
> If you are trying to make a counterexample, you failed.  A product is a specific implementation of an idea.  You can only patent the general invention.  An automobile is a patentable idea.  The Model T is not.  An ejector seat is patentable.  The Ubuntu brand Linux-Based Ejection Safety System (tm) is not.  The virtual machine is patentable (but not by Microsoft, since they didn't invent it).  The .NET Framework CLI virtual machine is not.

This is very misleading.  As I said in my previous post, you have an incorrect understanding of what can be patented. Ideas cannot be patented. Specific implementations of an idea can be.

---

### Post by MountainX on 2008-04-02
> **koenn said:**
> drifting away from the mono issue now, but

1- doesn't Microsoft succesfully claim patent infringements, then settles out of court for a pay-off ? 

2- If they'd go to court to enforce their claims, at least they'd have the money to pay an army of lawers to put on a good, long-lasting show  - and the legal costs alone could be enough to bleed their oponents to death

Exactly. Many open source projects would not have the funding to prove that Microsoft's patents aren't valid. 

This very discussion shows the siippery slope we are going down already.

---

