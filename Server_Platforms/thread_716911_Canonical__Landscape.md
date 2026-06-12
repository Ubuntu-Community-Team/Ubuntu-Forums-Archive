---
title: "Canonical / Landscape"
date: 2008-03-06
forum: Server Platforms
---

### Post by mmichalik on 2008-03-06
I was reading on Canonical's website that there isn't going to be an GNU / GPL open source version of Landscape.  Users who do not have subscriptions to Canonicals support services will have to pay $150.00 per node to use it.

This is a great program, it's too bad it will be charged for like that.  I understand that Canonical has to make money so, I'm not complaining, just saying......

Does anyone know of a similar product that is available without cost?

---

### Post by thk on 2008-03-06
Webmin?

Can't blame them for trying to make a buck. Still, it explains a lot about the lack of interest in eg LDAP integration. They would be competing with their own product. A shame as gutsy is currently useless in a client - server environment. LDAP clients freeze during boot and NFS shares do not mount correctly without intervention. Sad state of affairs. The network was the machine...

---

### Post by Yann2 on 2008-03-07
I am also very disappointed by the turn Canonical takes. What is the point trying to prove the use of opensource to countries and companies, if Canonical is developing closed source software itself? 

I learnt recently with Zimbra (which is not fully free, which got bought by yahoo, which may get bought by MS) that you should never trust non completely free software. 

Even if I am a paying customer (which my company will be quite soon), why should I trust this more? Let's ditch landscape and prefer true, opensource software.

---

### Post by mmichalik on 2008-03-07
I'm using webmin now and it does the job pretty well but, I was hoping for something that would provide single signon capabilities.

I'm not opposed to paying for it, if it's truly a good product.  I would just like to be able to use a open source version of it so that when we pitch it to our clients, we have an intimate knowledge of it.

---

### Post by Vadi on 2008-03-07
> **Yann2 said:**
> I am also very disappointed by the turn Canonical takes. What is the point trying to prove the use of opensource to countries and companies, if Canonical is developing closed source software itself? 

I learnt recently with Zimbra (which is not fully free, which got bought by yahoo, which may get bought by MS) that you should never trust non completely free software. 

Even if I am a paying customer (which my company will be quite soon), why should I trust this more? Let's ditch landscape and prefer true, opensource software.

a) Ubuntu wouldn't be possible without closed-source software to begin with (where did mark shuttleworth make his fortune?), b) the majority of applications developed by Canonical are open-source, up to the point of brainstorm & the forums customization. Nevermind their flagship product.

I really see no problem with this, and support their move - they do need to be financially stable. And I'm not sure how much money are those support contracts (who has one here?) are bringing in.

---

### Post by obnibolongo on 2008-03-08
Well, I am a bit confused here, as I see a landscape-client and start thinking if there is a landscape-server.

Anyway, someone has already filled in a bug with such concerns in it ^^

[Bug #163030 in landscape-client (Ubuntu)]("https://bugs.launchpad.net/ubuntu/+source/landscape-client/+bug/163030"), description: "Against Ubuntu Promise".

---

### Post by Vadi on 2008-03-08
People have no business sense at all and take all of this for granted. Makes me very, very sad.

---

### Post by tubezninja on 2008-03-08
> **Vadi said:**
> People have no business sense at all and take all of this for granted. Makes me very, very sad.

I don't think anyone here is against a company making a buck, if that was what their stated intent and mission is.  But it's difficult to deny that Landscape's release model runs afoul of the [philosophy]("http://www.ubuntu.com/community/ubuntustory/philosophy") espoused by ubuntu.  Landscape is software.  Why is not free?  And why can't Canonical focus on making money off perhaps a monitoring/notification service that would mate with landscape as opposed to charging for software outright?

One also has to look at the fact that webmin is no longer in the package repositories, and no other FOSS alternative is there to replace it.  What gives?

I have to say, in my trial so far Landscape is promising.   But it would have to be much, much better than it is for me to consider paying $150/year/node for it, or even recommending it to where I work for their much larger fleet of servers.

---

### Post by Vadi on 2008-03-08
Er.

Ubuntu is made by Canonical.

Landscape is made by Canonical.

Landscape is not a product, a child, or whatever of Ubuntu. It has no relation to ubuntu in that sense.

Does Canonical have the same philosophy as Ubuntu? If yes, then I agree with you. But if no, then nothing is wrong.

I don't know what notification service are you talking about, sorry. I only understand that this is a monitoring app that you can use in a lab/work to see what all of your ubuntus are up to. But would *you* consider buying that side product?

---

### Post by faulkes on 2008-03-08
I have debated whether or not to post in this thread.

> **scaredpoet said:**
> I don't think anyone here is against a company making a buck, if that was what their stated intent and mission is.  But it's difficult to deny that Landscape's release model runs afoul of the [philosophy]("http://www.ubuntu.com/community/ubuntustory/philosophy") espoused by ubuntu.  Landscape is software.  Why is not free?  And why can't Canonical focus on making money off perhaps a monitoring/notification service that would mate with landscape as opposed to charging for software outright?


That is an issue Canonical will have to address with the community and I
fully expect that they will do so.  That doesn't mean we will like the 
answer but I significantly doubt they will ignore the concerns which 
are raised.

In fact, I have already pointed Canonical at this forum post although I 
doubt there will be an official post here from them.  Furthermore this
very issue will be raised at the next server team meeting.

> 
One also has to look at the fact that webmin is no longer in the package repositories, and no other FOSS alternative is there to replace it.  What gives?


There are numerous discussions available on the ML's which state why
webmin is no longer in the package archives.  I will not redress the issue
here.

There is ebox, which is a suitable alternative and is being heavily worked
on for Hardy, packages for 8.04 are already in Chuck Short's PPA for
testing.  I also believe there are packages for Gutsy.

> 
I have to say, in my trial so far Landscape is promising.   But it would have to be much, much better than it is for me to consider paying $150/year/node for it, or even recommending it to where I work for their much larger fleet of servers.

That is part and parcel of developing an application and giving people access
to try it out, for Canonical, that is valuable feedback and you should give
it to them, with specifics.

Not all decisions that happen (i.e. webmin) are Canonical decisions - 
we work with debian as an upstream.  We also work as a community,
people who put in their own time and effort.

For the record, I am not a Canonical employee and I am not arguing for
or against any way they choose to do business.  

Faulkes

---

### Post by tubezninja on 2008-03-08
> **Vadi said:**
> Er.

Ubuntu is made by Canonical.

Landscape is made by Canonical.

Landscape is not a product, a child, or whatever of Ubuntu. It has no relation to ubuntu in that sense.


Well then that settles it.  If has no relation to ubuntu, then I have no reason to use it or recommend it! :D  For it not to be related, it simply has too much control over the ubuntu servers it claims to work with, and I find that to be too much of a risk.

Thanks for clearing that up!

---

### Post by tubezninja on 2008-03-08
> **faulkes said:**
> 
That is part and parcel of developing an application and giving people access
to try it out, for Canonical, that is valuable feedback and you should give
it to them, with specifics.

If this is feedback I need to give Canonical, then I will, but that does raise concerns for me.  There are open source tools out there that do much the same thing as Landscape, and they should be well aware of them.  Canonical has yet to state a case for why a server admin should pay $150/node for much the same through their offering.

At any rate, I've used it for 48 hours now.  I see the features and see the shortcomings.  I think I'm already set in my decision not to use this.  I'll be sure to send my writeup/critique with my cancellation request.

---

### Post by Vadi on 2008-03-08
Simple curiosity.

What *would* you pay for?

---

### Post by tubezninja on 2008-03-09
I've already [indicated]("http://ubuntuforums.org/showpost.php?p=4476342&postcount=8") what I would pay for.

...Oh I'm sorry, was your post rhetorical sarcasm? :)

---

### Post by Vadi on 2008-03-09
That wasn't really an indication as I saw it, just an idea to charge not for the main package, but for something extra. You didn't really specify that you'd be getting that extra thing, and given your view of the app so far, I assumed you were just looking to get the main thing free.

Whatev though, don't care myself. I'm just unhappy with the amount of unthankfullness and lack of business sense some people have been displaying in the FOSS community - I don't think it's healthy at all to be sawing the branch you're sitting on.

---

### Post by tubezninja on 2008-03-09
> **Vadi said:**
> That wasn't really an indication as I saw it, just an idea to charge not for the main package, but for something extra. You didn't really specify that you'd be getting that extra thing

I would submit that it's more you're refusing to see the point in favor of making a blanket implication that FOSS-folks are just a bunch of freeloaders.  I don't see that as the case at all.  I don't begrudge Canonical for making money; in fact, I've pushing for some support contracts to be purchased at work.  Some of us also [donate]("http://www.ubuntu.com/community/donations").

The point I'm trying to make is that is Canonical has espoused a commitment to FOSS, and then in another turn has said "here's this other package that we think is great, but oh, you have to pay for it."  When someone does that, it negates the whole "right to free software" thing.  And then one has to wonder: Where *ELSE* will this line start to get fuzzy?  How far along are we until the only supported version of ubuntu is named "Paying Platypus?"

(And yes, I realize... or at least HOPE... what I'm asking is hyperbole, but still, one has to wonder...)


 > Whatev though, don't care myself. I'm just unhappy with the amount of unthankfullness and lack of business sense some people have been displaying in the FOSS community

Then... and I say this not tounge in cheek, but honestly asking... why do you continue to stay involved?  A business-driven person like yourself would be more in tune with your goals (and your skills would be more appreciated, it seems) in a profit-driven corporate software development environment, wouldn't you say?

And I'm not asking "why don't you leave."  Clearly there has to be some redeeming qualities that you see here that compel you to continue participation.  What are they?

---

### Post by mmichalik on 2008-03-09
HI everyone,

It wasn't my intent to start a philosophical debate about the why's and why not's of Canonicals decision to charge for their landscape product.  I'm ALL for them making money on this and any other product / service they support, produce, provide or back.  That's their decision and I respect it 100%.

All I was asking for was a suggestion for a suitable replacement product, if there are any.  If landscape is as good as it looks like it can be, then I would buy it for our office (for Proof of Concept) and deploy it at client sites.

But, if there is a decent option out there, that only helps me provide a lower TCO for our clients.  Which, is important in any business decision.

Although I do appreciate the lively debate.

So, back to my original question, does anyone know of a suitable option for this?  My biggest goal is to find a single sign-on management system.

Thanks,

Mike

---

### Post by Vadi on 2008-03-09
I do know of the donations link, thanks! In fact I donate money to quite a few projects that I come across. As for the rest, I'll comply with the OP. If you want to understand me point (you don't quite from the last post, since you assumed quite a negative opinion and even asked what I was doing here), PM me.

---

### Post by tubezninja on 2008-03-10
> **Vadi said:**
>  since you assumed quite a negative opinion and even asked what I was doing here), PM me.

I did neither, and made pains to make it clear I was doing neither.  I'm sorry you feel that way.  Considering you seem intent on casting anything I say as a negative however, I don't see how PMing you could be of any benefit, let alone continuing the discussion.  "Agreeing to disagree"  can get cliche, but I guess that's just what we're going to have to do here.

Going back to the OP's post: 

[quote=mmichalik] All I was asking for was a suggestion for a suitable replacement product, if there are any. If landscape is as good as it looks like it can be, then I would buy it for our office (for Proof of Concept) and deploy it at client sites.[/quote]

You could give [webmin]("http://www.webmin.com/") a try.  It's probably as close as you're going to get to an open, web-based graphical system for server monitoring.  You could also give [eBox]("http://ebox-platform.com/") a try.  Both packages will require a bit of elbow-grease to set up and get working, but once you have a procedure down, you can probably turn these solutions around for clients fairly quickly.  

You may even want to consider setting up eBox on one server, webmin on another, and landscape on a third so that you can compare the three options and see which one is best.  You **might** find features that make Landscape worth the price point.  Or, you might conclude that the elbow grease might be worth saving that money.  It's all subjective.

EDIT: There's also  [cPanel]("http://www.cpanel.net/purchase/cpwhm_pricing.htm").  But it is also a commercial package, and FAR pricier than landscape.

---

### Post by netlogic on 2008-03-10
People have to pay bills. We can't make everything on the net free. People's time is money.  I am glad they are creating a different revenue stream product line, so they can afford to give away other service such as Ubuntu. I hope some people understand people have to eat. That goes for GPL developers too.

---

### Post by mmichalik on 2008-03-10
scaredpoet,

Thank you for the suggestions.  I use Webmin extensively right now on all 5 servers.  It's a really good tool for server side maintenance.

I will give ebox a look and see how it works as well.

It appears that I will have to just set up OpenLDAP and get everything working via that, for single sign-on capabilities or purchase Landscape.  Like I said, I'm not opposed to paying for it at all.

---

### Post by bluefrog on 2008-03-11
[http://www.ocsinventory-ng.org/index.php?page=English](http://www.ocsinventory-ng.org/index.php?page=English)
[http://www.glpi-project.org/spip.php?lang=en](http://www.glpi-project.org/spip.php?lang=en)

is certainly more what you are looking for.

James Dupin

---

### Post by mmichalik on 2008-03-11
I will check those out.

thanks Bluefrog!

---

### Post by thenetduck on 2008-04-24
Honestly, 

I think Canonical is giving a sweet deal when it comes to updates etc because I feel like I should be paying for the servers that host my constant updates etc. 

As far as code goes, I don't have a problem paying for it... once :). I think the point of Open Source is that improvements can be made and given to others to make improvements. 

If I download the program from the main developers of the software, and not a torrent I wouldn't mind paying. With that said, I know most people would just download it somewhere else for free. 

I don't have a moral delema with licensed software because "I don't own it" I am using other peoples software. With open source software, it's mine, I own it. I think it's just two different ways of thinking. Because the idea now days is the more you own, the more you are worth, companies have capitalized on the idea of "owning" software that they license. 

So what does everything I just typed mean? 
It means, I think we should pay for programmers work, because like it was stated, they have worked and need to eat. I don't believe that information should be sold, but I still don't think is "wrong" to sell it. I think it creates better synergy when it's not sold and given. If your going to license, the license, but don't have a double standard, it's just not cool. If canonical would make it open source then charge for using the product on their server, I think that would be better. 

I guess the real question is, how do you pay millions of open source programmers that help on a certain project? 

I think this is at the core of the discussion. 

The Net Duck

---

