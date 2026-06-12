---
title: "Please Explain Mir"
date: 2013-12-01
forum: Ubuntu, Linux and OS Chat
---

### Post by cessanfrancisco on 2013-12-01
I've been reading about Mir and all the controversy, yet I am still confused.  I understand that Mir is intended to replace X11 so that Ubuntu can run Unity 8, and apparently this cannot be done with Wayland.

So what is all the controversy about?  Can someone please give me an objective perspective on the pros, cons, and reasons for Mir?

Thanks in advance.

---

### Post by TenPlus1 on 2013-12-01
[http://en.wikipedia.org/wiki/Mir_%28software%29](http://en.wikipedia.org/wiki/Mir_%28software%29)

---

### Post by buzzingrobot on 2013-12-01
As a user, I find the Mir-Wayland controversies pretty uninteresting and distracting.  Both are a long way from showing up in any distribution I'm likely to use.  When they do, if either offers me definite advantages, I will likely move to a distribution that uses it.  

That said, Canonical and the communities supporting Wayland are pursuing different goals for different reasons.  Much of the noise is ideological posturing about the different values exposed by the realization that those differences exist.

---

### Post by neu5eeCh on 2013-12-01
> **buzzingrobot said:**
> As a user, I find the Mir-Wayland controversies pretty uninteresting and distracting.

I, as a user, find the Mir-Wayland controversy **very** interesting. There's more at stake than just two display servers. There are two philosophies competing, two visions for how a linux destop/multi-platform OS can compete in the larger marketplace and what kind of company Canonical (Shuttleworth) thinks it has to be. Even more interesting to me is that Google is apparently planning for ChromeOS to ride on Wayland. It's all like a very complicated game of chess and the stakes are high. 

Related: Just days after Redhat announced 6.5, Oracle was "proud" to announce its immediate re-release of Redhat 6.5 as Oracle Linux 6.5 (I mean, c'mon, they can't even change the version number?). Ellison must laugh his hind-end off every time -- and you just know this gets under Redhat's skin. Shuttleworth sees that, doesn't want some Larry Ellison re-branding Ubuntu, and creates MIR.

As the Wikipedia article points out: "This means that, despite not being the sole copyright holder, Canonical  are free to relicense your code under a proprietary license". He  concludes that this creates asymmetry where "you end up with a situation  that looks awfully like Canonical wanting to squash competition by  making it impossible for anyone else to sell modified versions of  Canonical's software in the same market".     

So, Shuttleworth probably thinks that Linux can't compete in the marketplace if just any competitor can waltz off with your hard work and re-brand it. Redhat is probably a cautionary tale in Shuttleworth's opinion. How I read Shuttleworth in five words or less: "Richard Stallman can shove it."

---

### Post by buzzingrobot on 2013-12-01
> **VTPoet said:**
> I, as a user, find the Mir-Wayland controversy **very** interesting. There's more at stake than just two display servers. There are two philosophies competing...the stakes are high. 

The "philosophies" of all this -- and I think they hardly merit that term -- don't concern me, and I don't see why they should.  My only interest is in the software that may or may not be made available to me, somewhere in the future. 

The "stakes are high" for Canonical because it's a business trying to make a profit.  It makes sense to me that Canonical would attempt to decrease its reliance on code maintained by people it cannot control -- community developers -- because, as a business it needs, among other things, to contract to follow a schedule. They would be foolish to promise, by contract, delivery of Product X on Date Y if that product depended on code from some independent FOSS developer with no enforceable obligation to Canonical.

That's the inevitable and inherent tension between FOSS-as-a-community and FOSS as a component of products created by a for-profit business.  I'd guess Google would deal with similar issues re: Wayland by throwing its own developers at problems, something for which they have considerably more resources than Canonical.

>  Related: Just days after Redhat announced 6.5, Oracle was "proud" to announce its immediate re-release of Redhat 6.5 as Oracle Linux 6.5 (I mean, c'mon, they can't even change the version number?).

Oracle is doing what CentOS and others have done for much longer:  Remove RedHat branding and trademarks from Red Hat source, rebuild it, and release it. RedHat is on record as being OK with the approach CentOS takes.  Having established the precedent, there's not much they can do about Oracle doing the same thing.  Now, Oracle is competing with RedHat on the support side, but they've been doing that all along.


> ...despite not being the sole copyright holder, Canonical  are free to relicense your code under a proprietary license...

Copyright is not licensing. If someone doesn't want Canonical, or anyone else, to adopt their FOSS code and release it under a different license, then they need to change *their* license rather than rely on copyright. if they do think their copyright is sufficient to prevent that, they should find lawyers and bring an action against Canonical.

>  Shuttleworth probably thinks that Linux can't compete in the marketplace if just any competitor can waltz off with your hard work and re-brand it. Redhat is probably a cautionary tale...

The Red Hat comparison does not work here.  Red Hat is not in the business of selling software or any product that incorporates its software. The history of Linux as a retail product -- selling the software -- is abysmal. No one, frankly, has ever sustained a business selling retail Linux. The most obvious example of that is, in fact, Red Hat, which began as a small business marketing shrinkwrapped Linux boxes on retail shelves. If Shuttleworth, or anyone else, believes the ability of competitors to grab your FOSS code and release it under their own name -- or for potential customers to simply grab and build the code -- effectively squashes their chance of profitably selling their product, they are absolutely correct.  

> "Richard Stallman can shove it."

RMS and his ideology have nothing at all to do with for-profit business.  It's not so much a matter of telling RMS to "shove it" as it is a matter of his irrelevancy in Canonical's affairs.

---

### Post by neu5eeCh on 2013-12-01
> **buzzingrobot said:**
> My only interest is in the software that may or may not be made available to me, somewhere in the future.

And yet, here you are, engaging in a conversation on the subject. I sense cognitive dissonance. 

> **buzzingrobot said:**
> RedHat is on record as being OK with the approach CentOS takes.

And RedHat is on record as _not_ being OK with the approach Oracle takes.

> **buzzingrobot said:**
> The Red Hat comparison does not work here.  

Yes it does. :popcorn: 

> **buzzingrobot said:**
> Red Hat is not in the business of selling software or any product that incorporates its software.

Wrong. Red Hat wouldn't exist if it weren't selling it's software. "Oh no," you triumphantly proclaim, "they only sell support contracts!" Well then, why develop the software called "RedHat"? Why not just copy Oracle Linux. Oh... wait a minute...


> **buzzingrobot said:**
> RMS and his ideology have nothing at all to do with for-profit business.

Really? Well, I guess you know Stallman better than Stallman. [He begs to differ.]("http://levi.maaia.com/os/section_who/stallman.htm")

"Stallman                                 has remained sharply                                 opposed to the combination                                 of the GPL with for-profit                                 business solutions.  Stallman                                 believes that all software                                 should be free and                                 that the business of                                 software hurts further                                 development.  He                                 remains committed to                                 the strict ideas of                                 Free Software, believing                                 that all software should                                 be free and that there                                 is no place for non-free                                 or proprietary software."

---

### Post by deadflowr on 2013-12-01
> **cessanfrancisco said:**
> I've been reading about Mir and all the controversy, yet I am still confused.  I understand that Mir is intended to replace X11 so that Ubuntu can run Unity 8, and apparently this cannot be done with Wayland.

So what is all the controversy about?  Can someone please give me an objective perspective on the pros, cons, and reasons for Mir?

Thanks in advance.


From the horses mouth
[https://wiki.ubuntu.com/Mir/Spec](https://wiki.ubuntu.com/Mir/Spec)

---

### Post by buzzingrobot on 2013-12-01
Sophistry.

Red Hat can't stop Oracle or anyone else from recompiling and releasing its source. Oracle is unpopular in the FOSS world so it's unlikely -- bad politics -- that RH will say anything good about Oracle. 

 RH does not *sell* its source.  You can't go anywhere and *buy* a retail box with a Red Hat DVD of RHEL inside.  You can either download the source or buy a service contract.  Once upon a time, you could buy RH in a box.  I did, lots of them.  Then, RH got smart and figured out you can not sell CD's of software when any Joe Schmoe can download the source, build it, and give it away. 

Sure, RH can't sell support for RHEL if RHEL doesn't exist in the first place.  That wasn't the point.


> "Stallman                                 has remained sharply                                 opposed to the combination                                 of the GPL with for-profit                                 business solutions.  Stallman                                 believes that all software                                 should be free and                                 that the business of                                 software hurts further                                 development.  He                                 remains committed to                                 the strict ideas of                                 Free Software, believing                                 that all software should                                 be free and that there                                 is no place for non-free                                 or proprietary software."

You will have to convince me that anything RMS says about business needs to be listened to by business people, or pretty much anyone else. Businesses exist to make a profit. They vanish if there's no profit.  Stallman's notions of free software don't work in a market environment because his ideology demands businesses allow others to acquire/copy/distribute the very thing they are trying to sell.  That's the Achille's Heel of Linux-as-a-retail-product. Canonical is just one example of that tension at work. Canonical cares about making money and the community cares about fuzzy-wuzzy openness and all that. The two concerns are fundamentally in conflict.

---

### Post by neu5eeCh on 2013-12-02
> **buzzingrobot said:**
> Oracle is unpopular in the FOSS world so it's unlikely -- bad politics -- that RH will say anything good about Oracle. 

Yes, I know. Since you made the somewhat irrelevant point that RH is "okay" with CENTOS (irrelevant because they don't compete with RH's core business -- unlike ORACLE) I just thought I'd mention that RH doesn't like ORACLE and let you connect the dots. I'm not sure you did. In case you didn't, I just spelled it out.

> **buzzingrobot said:**
> Sure, RH can't sell support for RHEL if RHEL doesn't exist in the first place.

Thank you. You might be interested to know that Whitehurts also considers RH to be a software company, hence the following comment from him:

"SuSE often comes in at a lower price point than  RHEL, but most people would prefer to have a common code base like RHEL  plus CentOS than a cheaper but always fee-based enterprise SuSE."

Note: He doesn't say anything about service contracts. He talks about things like "code base", another word for software. Now, niggling over the fact that they don't _literally_ sell software is... well... sophistry. If, as you yourself admitted, RH has nothing to offer without its software, then posturing over literalism is the very essence of semantics and sophistry.

> **buzzingrobot said:**
> You will have to convince me that anything RMS says about business needs to be listened to by business people...

No I don't, cause that was never my point. If you have a problem with "business people" who pay RMS lip service, then take that up with Shuttleworth.

And that brings me back to MIR and Wayland. The whole point of my original reply was to say that I, as a user, find the conflict interesting. So does the OP. Shuttleworth is taking desktop linux in an interesting direction and clearly has philosophical differences with many in the larger community, including Stallman.

---

### Post by philinux on 2013-12-02
Moved to U L and OS chat.

---

### Post by buzzingrobot on 2013-12-02
> **VTPoet said:**
> Yes, I know. Since you made the somewhat irrelevant point that RH is "okay" with CENTOS (irrelevant because they don't compete with RH's core business -- unlike ORACLE) I just thought I'd mention that RH doesn't like ORACLE and let you connect the dots. I'm not sure you did. In case you didn't, I just spelled it out. 

  I was specifically addressing the futility of trying to sell Linux in the retail market thanks to the impact of the GPL and other FOSS licensing schemes.  Whether Red Hat likes Oracle or not isn't relevant to that.

[qoute]Thank you. You might be interested to know that Whitehurts also considers RH to be a software company...[/quote]

No idea who Whitehurts is.  In any case, as for the nomenclature used to label RH or Suse or Oracle... well, see above. Labels don't change anything: No one sells retail Linux because it contains its own poison pill.


> No I don't, cause that was never my point. If you have a problem with "business people" who pay RMS lip service, then take that up with Shuttleworth.

My issue isn't to do with "lip service" paid to RMS by anyone.  RMS is pretty irrelevant to my life.  I've always attributed all the words about community and "freedom" from Shuttleworth and Canonical as so much corporate PR hype, no more to be taken seriously than hype from Apple or Microsoft. (Seems many people did, though. Don't know why.  People are all the same.)    Even if Canonical and Shuttleworth were/are sincere, they *cannot* build a successful, profitable, business and *simultaneously* remain faithful to the tenets of FOSS *and* avoid running afoul of FOSS culture. They need to choose between making money or meeting the expectations the self-defined FOSS community sets for them. They can't do both. The objectives are mutually exclusive. 

> ...I, as a user, find the conflict interesting. So does the OP. Shuttleworth is taking desktop linux in an interesting direction and clearly has philosophical differences with many in the larger community, including Stallman.

I'm happy to see examples of innovation like Mir and Wayland.  Software development is a conservative arena, and FOSS contains elements that make it particularly conservative.  But, I find the noise and the chatter and the debates surrounding Mir and Wayland to be eye-glazingly boring. (One side seems to expect adherence to cultural norms to take precedence over how software is made.  That strikes me as people who think they know better trying to control how other people behave.)  I'll happily wait to see who delivers the goods.

---

### Post by grier-devon on 2013-12-02
I did some reading up on the topic myself and I remember the Mir announcement, I think one thing that bothers me is when Mir was announced Wayland had done some work but was not moving forward with any real purpose. Canonical looked at Wayland and found the cost it would take to build Wayland saying no one jumped in would have been the same cost to build there own as stated in Ubuntu onAir. What bothers me is since Canonical is the one building a display server every other company and community is jumping on Wayland. As far as I know any one could adopt and start developing Mir but all the other communities and companies are making this a race with Wayland because they simple do not want to be associated with Canonical.

The only area I oppose Mir is the end cost. Eventually other companies and open source communities would have to adopt Wayland, when you have more hands from different sources working on a project the cost for each individual source declines largely. This is the point of open source, GNU and Linux as a competitor in the proprietary world we live in, if Canonical in the end with the 16.04 release remains the only one using Mir their cost to Wayland will be much higher and in my opinion this defeats ONE of the main perks to open source development.

With that said I will admit I am rooting for Mir. Look at Windows, if I develop an application for Windows 8 and want it to run on the Microsoft ecosystem then I must port it from Windows 8 to RT and then to Phone 8 and even do a port to the Xbox. The point of Mir from what I get from Ubuntu onAir is build the app once to the specification of Mir and then let the display server handle re sizing and adjustment of the application. Or another good example is the ipad, the ipad essentially has different repositories based on which screen size, so if I build an app for the ipad I must port it to work on the smaller sceen of the ipad mini to also have it available on there. Yet again this is the point of Mir.

---

### Post by buzzingrobot on 2013-12-02
> **grier-devon said:**
> ... Eventually other companies and open source communities would have to adopt Wayland, when you have more hands from different sources working on a project the cost for each individual source declines largely. This is the point of open source, GNU and Linux as a competitor in the proprietary world we live in, if Canonical in the end with the 16.04 release remains the only one using Mir their cost to Wayland will be much higher and in my opinion this defeats ONE of the main perks to open source development.


The risk of Canonical being the only eventual user of Mir seems something entirely for Canonical to face.  Canonical is developing it for their use in their products.  If someone else wants to use it and adheres to the licensing requirements, I'm sure Canonical would be pleased.  But, it ought to be clear that's not why they are developing Mir.

I see no way for Canonical, as a business, to depend on any community-developed display server, like Wayland, to meet its desire for a single cross-device server.  If, at some point in time, Wayland did meet their requirements, they have no guarantee that future Wayland iterations would leave it still meeting their needs. They could, of course, essentially fork it, to bring it in line with their requirements.  But, then, why not just go off on their own, as they've done?

Canonical here is in a position roughly analagous to Apple's vis-a-vis use of open source as they developed OS X. At some point, the needs and interests of the corporation mean that it isn't worth the risk to leave critical pieces of software subject to the interests and capacities of others, especially something as shifting and amorphuos as the FOSS development community.

---

### Post by lykwydchykyn on 2013-12-02
> **buzzingrobot said:**
> 
I see no way for Canonical, as a business, to depend on any community-developed display server, like Wayland, to meet its desire for a single cross-device server.  If, at some point in time, Wayland did meet their requirements, they have no guarantee that future Wayland iterations would leave it still meeting their needs.

I'm curious as to which device you think Wayland will not work with?

I'm also curious why it's safe for Canonical to depend on community-developed kernels, drivers, toolkits, C libraries, applications, bootloader, etc. etc.; but somehow the *display server* is too critical to leave to "the community"?

---

### Post by grier-devon on 2013-12-02
> **lykwydchykyn said:**
> I'm curious as to which device you think Wayland will not work with?

I'm also curious why it's safe for Canonical to depend on community-developed kernels, drivers, toolkits, C libraries, applications, bootloader, etc. etc.; but somehow the *display server* is too critical to leave to "the community"?

Not to mention one of the biggest contributes to Wayland is Intel, which last time I checked is a corporation which shares Canonical's vision. Both Intel and Samsung have a great deal of interest in the Tizen project, Intel is focusing on the gnome desktop version of Tizen as they demo early this year and Samsung is focused on a mobile version for phone and tablets which Japan has already received. The concept is for "convergence" where applications will work between both desktops flawlessly. In this case you have two companies in which need essentially relying on the success of Wayland with community efforts.

---

### Post by buzzingrobot on 2013-12-02
> **lykwydchykyn said:**
> I'm curious as to which device you think Wayland will not work with?

I'm also curious why it's safe for Canonical to depend on community-developed kernels, drivers, toolkits, C libraries, applications, bootloader, etc. etc.; but somehow the *display server* is too critical to leave to "the community"?

It isn't a matter of Wayland working with one device or the other, or its technical merits.  it's about controlling software that is critical to their notion of a single multi-device platform.  

So far, with the obvious exception of Gnome, Canonical have been able to get away with relying on community projects that have interests and schedules of their own. Maybe that will change, too. But, Canonical can't make schedules and meet contractual commitments if it lacks control of the critical pieces of its product. Otherwise, they could miss deadlines, etc., simply because some guy in the community decided to take some time off.

---

### Post by grier-devon on 2013-12-02
> **buzzingrobot said:**
> It isn't a matter of Wayland working with one device or the other, or its technical merits.  it's about controlling software that is critical to their notion of a single multi-device platform.  

So far, with the obvious exception of Gnome, Canonical have been able to get away with relying on community projects that have interests and schedules of their own. Maybe that will change, too. But, Canonical can't make schedules and meet contractual commitments if it lacks control of the critical pieces of its product. Otherwise, they could miss deadlines, etc., simply because some guy in the community decided to take some time off.

So what happen with Xmir and 13.10, did some paid employ take some time off and not get the bug fixed so we could have dual monitor suport which lead to Xmir missing it's dead line?

Plus as I mentioned Intel and Samsung have a much heavier schedule with actual promises to consumers and vendors which will require there efforts of an open source community to get Wayland and Tizen where they need to be on time. It is good to see two large companies have faith in open source development and those on the front line hacking away to make it work.

---

### Post by buzzingrobot on 2013-12-02
> **grier-devon said:**
> So what happen with Xmir and 13.10, did some paid employ take some time off and not get the bug fixed so we could have dual monitor suport which lead to Xmir missing it's dead line?
[/qoute]

They missed a deadline.  Either the deadline was unrealistic or something else unexpected happened.  The point, though, is that paid employees take time off when the employer allows it, not when they feel like it. And, if the deadline was missed because one or more Canonical employees were inadequate or incompetent, they can be dismissed and more qualified replacements hired.  Canonical can't do that if they rely on the community. 

 As I keep saying, it's all about control.  If your product depends on volunteers who may or may not write code you can use, or who may or may not even be trustworthy at all, why would you *not* move things in-house? 

The fundamental interests of the FOSS community and for-profit business are mutually exclusive. Why is that so difficult to comprehend?  

[quote]Plus as I mentioned Intel and Samsung have a much heavier schedule with actual promises to consumers and vendors which will require there efforts of an open source community to get Wayland and Tizen where they need to be on time. It is good to see two large companies have faith in open source development and those on the front line hacking away to make it work.

It's a business choice, a judgement call.  Intel and Samsung would do exactly the same thing if they thought they needed to in order to preserve profits. (And they have orders of magnitude more money and other resources than Canonical -- a small company -- to throw at any effort the community fails to deliver appropriately.)   Don't imagine for a second that they're putting the interests of the community ahead of their own interests. Some of their current interests coincide with community interests, but as soon as they diverge, any rational business would cut off the community in a second.

---

### Post by philinux on 2013-12-02
I have mir running on 13.10 just fine but by default it wont be running until 14.10

[http://www.phoronix.com/scan.php?page=news_item&px=MTUyNTY](http://www.phoronix.com/scan.php?page=news_item&px=MTUyNTY)

[http://news.softpedia.com/news/Canonical-Confirms-Mir-Will-Be-Default-in-Ubuntu-14-10-403067.shtml](http://news.softpedia.com/news/Canonical-Confirms-Mir-Will-Be-Default-in-Ubuntu-14-10-403067.shtml)

The info is out there with a simple net search.

---

