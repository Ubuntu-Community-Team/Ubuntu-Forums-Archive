---
title: "Upgrade to Ubuntu Pro for a more secure system???"
date: 2023-03-09
forum: Ubuntu, Linux and OS Chat
---

### Post by operator-error on 2023-03-09
Forgive me if this topic has already been discussed, but for about a week now I've been getting the following message whenever I update my software via the terminal:

[FONT=monospace][COLOR=#000000]Get more security updates through Ubuntu Pro with 'esm-apps' enabled: [/COLOR]
  libimage-magick-perl imagemagick libopenexr25 libmagickcore-6.q16-6-extra 
  libimage-magick-q16-perl libmagickwand-6.q16-6 imagemagick-6.q16 
  libeditorconfig0 libmagickcore-6.q16-6 imagemagick-6-common 
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)

So now I have to pay for a subscription in order to keep my PC secure??? Wow, just wow.
[/FONT]

---

### Post by ian-weisser on 2023-03-09
> **operator-error said:**
> [FONT=monospace]So now I have to pay for a subscription in order to keep my PC secure??? Wow, just wow.
[/FONT]

Yes, it's been discussed many times before.
And, as we have said before, you have misinterpreted the message.

You have lost nothing.
EVERYTHING you had for free before is still free. All packages in Main get free security patches via the Security Repo. Nothing there has changed.

But what about all your software that was not in Main? What about Universe?
Well, you were simply not getting security patches for those. And you did not know.
Now you know.
That's all that the scary output is saying.

---

### Post by papakanush2 on 2023-03-10
And, if you scroll down on that web site you posted, you'll see that the Ubuntu Pro subscription is free for personal use, for up to 5 machines for 10 years instead of 5 for LTS, plus other benefits. I think Canonical is being quite generous here.

---

### Post by yetimon_64 on 2023-03-10
> **operator-error said:**
> ...[FONT=monospace]So now I have to **pay** for a subscription in order to keep my PC secure???...
[/FONT]
**No**, you won't have to pay anything unless you use it on more than 5 physical machines. You just have to open an account by registering with an email address.

> **papakanush2 said:**
> ... I think Canonical is being quite generous here.
+1. Very generous in my opinion. I have 2 laptops (physical machines) with a total of 5 Ubuntu installations. One laptop has 3 Ubuntu installs, Bionic, Focal and Jammy; the second has 2 installs, Ubuntu Jammy and Xubuntu Jammy, all of these installations are using the ESM updates. Though I should note any Xubuntu installs will have unsupported packages eventually, and when Xubuntu support ends I'll likely convert those installations over to a more basic Ubuntu system and add openbox or I3wm to them.

@OP,  All this extended support on 5 Ubuntu installations on 2 laptops has not cost me anything at all financially.
The subscription also enables me to use the kernel livepatch service (though I disable that one; I'm not sure I really need such a service) along with a realtime kernel and other security options more useful for business users. I generally only use the two ESM support options though there are other options/services available as well.

Regards, yeti.

---

### Post by donald187 on 2023-03-10
I signed up for the free Ubuntu Pro.  I see one can detach your machine from Ubuntu Pro in the Software & Updates app but on the Ubuntu Pro dashboard... 

[https://ubuntu.com/pro/dashboard](https://ubuntu.com/pro/dashboard)

...I see no way to do that.  I've found this question on both AskUbuntu and Reddit but not one answer. 

 Don't forget to detach if you reinstall :P.

EDIT:  I understand that one can use "sudo pro detach". :)

---

### Post by donald187 on 2023-03-10
I'm actually fairly amazed that Ubuntu can offer this free for personal use.  I mean patching takes people, and people take money.

---

### Post by yetimon_64 on 2023-03-10
> **donald187 said:**
> ...  I see one can detach your machine from Ubuntu Pro in the Software & Updates app but **[not]** on the Ubuntu Pro dashboard ....
I assume you mean "not" on the Ubuntu Pro dashboard. I cannot see a listing of attached installations, just the number of active machines. However there is a link there to a guide showing how to set up a pro subscription and along with "pro --help" there is a "detach" command. If for some reason the Software & Updates GUI fails an installation could be detached from either a terminal or from the Linux console.

As well as doing so in Software & Updates this can also be done in the terminal/console with...
```
sudo pro detach [YOUR_TOKEN]
```

---

### Post by donald187 on 2023-03-10
> **yetimon_64 said:**
> I assume you mean "not" on the Ubuntu Pro dashboard. 

Sorry.  I should have added in ellipses (as I have now).  "but on the Ubuntu Pro dashboard I see no way to do that." is what I meant.

> However there is a link there to a guide showing how to set up a  pro subscription and along with "pro --help" there is a "detach"  command. If for some reason the Software & Updates GUI fails an  installation could be detached from either a terminal or from the Linux  console.

As well as doing so in Software & Updates this can also be done in the terminal/console with...
```
sudo pro detach [YOUR_TOKEN]
```
Yeah, I saw that.

---

### Post by DigiAngel on 2023-03-12
I was going to start my own thread, but I'll use this one.  I had several screenshots, but I can't include them inline, and don't really want to bother with an image hoster.  So here's what I've seen so far:

Installing ubuntu 22 gets you the "Enable Ubuntu Pro" window right out of the box.

Anytime I ssh into a box now I get:
23 additional security updates can be applied with ESM Apps.
Learn more about enabling ESM Apps service at [https://ubuntu.com/esm](https://ubuntu.com/esm)

So.....now I ask this hard, unpopular question:  When did ubuntu get so lame?  If I wanted whiny ads for money I'd be running windows.

---

### Post by DuckHook on 2023-03-13
My even harder more unpopular question is:

When did *users* get so lame?

If self&#8209;promotion is a crime, then be the first to check yourself into jail. We all do it. But we hide it under self&#8209;serving euphemisms like "networking", "personal growth", "career enhancement", "making new friends", "putting our best foot forward" and a thousand others. Anyone with a LinkedIn profile is advertising themselves. So is anyone with a Facebook profile, or a Tinder profile, or a blog. Dressing up for a night out on the town is self&#8209;promotion. So is combing your hair and putting on make&#8209;up.

But if an organization that gives away almost all of its product for free even mentions that it has the temerity to offer *extended—and **only** extended—*services for a charge, then suddenly a certain contingent of users gets their panties in a knot and the sky is falling.

This whine has been posted on these forums ad nauseum.

Give your heads a shake, people.

---

### Post by yetimon_64 on 2023-03-13
> **DuckHook said:**
> ...services for a charge... Basically only for business users, maybe for some of the more hardcore Linux users with more than 5 machines. As a home user with 2 laptops (physical machines) with 5 Ubuntu installations ("rather enthusiastic" dual-booter here ;)) I haven't had to pay one single penny for the service thanks to the generosity of Canonical.
> **DuckHook said:**
> My even harder more unpopular question is:

When did *users* get so lame? ...

Give your heads a shake, people.Yep, exactly. Good post. Cheers, yeti. :)

---

### Post by maglin2 on 2023-03-14
People become loyal and emotionally attached to products. A lot of money can be made out of this trait and from selling ways for brands to maximise it.

People then feel upset and betrayed if they think the product is failing to maintain the values that caused them to invest their loyalty.

It's not logical, but then human behaviour that is purely logical we tend to consider syndromatic/sociopathic.

All part of life's rich tapestry.

---

### Post by BBQdave on 2023-03-14
> **DuckHook said:**
> ...if an organization that gives away almost all of its product for free even mentions that it has the temerity to offer *extended—and **only** extended—*services for a charge, then suddenly a certain contingent of users gets their panties in a knot and the sky is falling.

Maybe it's always been this way, but there does seem to be a level of entitlement, with users now a days, when things change or break or develop. The World has stopped moving! Catastrophe!

Been kicking around with GNU/Linux for around 20 years. Purchased books to learn Linux and Unix - to make a particular GNU/Linux disro work. Probably my favorite set up was my first, Yellow Dog Linux on an iBook. Not a cake walk to make that work :)

Fast forward to now, and what an amazing choice of GNU/Linux distros that are graphically easy to install. And stable!

To new GNU/Linux users, the work to gather knowledge is worth the power and freedom you will gain.

The news letter here in Ubuntu Forums has an interesting article on Flathub. A glimpse into some of the challenges and possible answers for the GNU/Linux community.

As said by so many, including DuckHook, whining gains you nothing. And there's so much more to be gained with GNU/Linux :)

---

### Post by DuckHook on 2023-03-14
> **maglin2 said:**
> People become loyal and emotionally attached to products. A lot of money can be made out of this trait and from selling ways for brands to maximise it.

People then feel upset and betrayed if they think the product is failing to maintain the values that caused them to invest their loyalty.

It's not logical, but then human behaviour that is purely logical we tend to consider syndromatic/sociopathic.

All part of life's rich tapestry.
I appreciate your observation. It is true that we conduct ourselves based on long habituated expectations. But when those expectations are unrealistic or, in this case, hypocritical, then it is time for us to re&#8209;examine and change them.

We cannot expect Canonical to keep giving us all of this awesomeness for nothing. They are not a charity (and even charities ask for money). Even if Canonical operates so ultra&#8209;efficiently that they employ but 0.5% of the staff employed by the proprietary giants, these are still people who must be paid. I don't see any of those who are complaining the loudest giving away their working time for free. In fact, they likely demand the most they can ask for their work, so why do their expectations suddenly go into magical reverse for Canonical?

Yes, we can all contribute in different ways. My contribution is to help out others. I figure that I'm doing my share by providing support. This is part of the indirect economic ecosystem that FOSS has fostered over the years, but we must never lose sight of the fact that it's still an ***economic*** ecosystem. And forum contributions only go so far: it can't pay for salaries, rent, utilities or even a cup of coffee.

Canonical can decide to hoodwink us the way that Red Hat does (I'm not dissing RH. They are just offering a necessary economic model that works for them). RH has elevated its name brand entirely into the paid sphere. You can't even get on their forums without a paid account. They then created a second brand, Fedora, that is basically a test bed in which nonpaying users are guinea pigs. There's no LTS in Fedora. It is, for all intents and purposes, a rolling release. When things go wrong, the guinea pigs just have to live with it until the devs get around to fixing it. If you want real stability in Fedora, you have to pay to upgrade to Red Hat.

Is that what the whiners and the gripers want? For Canonical to say: "Tell you what. LTS is no longer available without payment. We will offer only standard releases for free. You will have to put up with the six&#8209;month upgrade hamster wheel, frequent breakages, regressions and incompatibilities, but that's the price you pay for getting something at no charge. If you want 5&#8209;year support, you will have to pay for our new something&#8209;else version." That would certainly deal with the unrealistic expectations I suppose.

I don't know about you, but I would consider the above as the real disaster; not this tiny smidgeon of self&#8209;promotion that I can so easily ignore when I upgrade.

The only thing that Canonical has been "guilty" of is spoiling us.

---

### Post by BBQdave on 2023-03-14
> **DuckHook said:**
> We cannot expect Canonical to keep giving us all of this awesomeness for nothing. They are not a charity (and even charities ask for money). Even if Canonical operates so ultra&#8209;efficiently that they employ but 0.5% of the staff employed by the proprietary giants, these are still people who must be paid. I don't see any of those who are complaining the loudest giving away their working time for free. In fact, they likely demand the most they can ask for their work, so why do their expectations suddenly go into magical reverse for Canonical?

That's the challenge. And though maybe not the answer folks want, but I see it as a natural progress with GNU/Linux and business. You want Free (freedom) in OS, then you're a guinea pig and (hopefully) helping the GNU/Linux community. You want free (as in free beer) then you're a guinea pig and possibly the product.

You want LTS, you pay money. You want current stable applications, possibly through SNAP or FLATPAK, you pay money.

I'm an amateur photographer. My next go with Debian 12, will be to use the default software. No SNAP. No FLATPAK. And to see how that works with my amateur photography. Now if I step up to professional photography, I would expect to pay for software and equipment for my business. Can I use software in the GNU/Linux realm, sure. But I should be paying, whether through donations or time to help the projects. I don't code, so financial contribution for me.

I see Flathub and Snap-store becoming paid services and products. And I agree with that. Pay the devs of GIMP for the latest AI photo function, because I enjoy it or it's needed for business.
Don't want GIMP at that level, have it for free with your favorite GNU/Linux distro. Might be a release or two old, but it works great and you might be providing data for testing of new features in future GIMP.

If you are enjoying GNU/Linux and not making it into a business, than support the community you are part of.

If you are using GNU/Linux for business endeavors, you financially pay for the tools you are using.

---

### Post by bernard010 on 2023-03-14
@donald187  Use &#8216;sudo pro detach&#8217; command.

---

### Post by DuckHook on 2023-03-14
There is an aspect of people's relationship with FOSS that has always bothered me. Deeply.

Too often, the people who use it treat it as a one&#8209;way valve. They think they are entitled to get it for free. But they feel no obligation to give anything in return.

Nothing else in life works this way. Nothing.

So, why do people think that FOSS is this lone, crazy, magical exception?

The topic of this thread is but one illustration of this theme. Some people take exception to Canonical offering over&#8209;and&#8209;above services for money. This presupposes that they are somehow "deserving" of tons of amazing stuff for nothing in return.

In point of fact, we *do* get tons of amazing stuff for nothing in return. The proper response to such a windfall is to quietly count our lucky blessings and not call attention to the gross asymmetry, in fear that the party offering it to us might come to their senses and stop offering it. The response that we *actually* get is for (some) people to get even more demanding. More entitled. More strident. More presumptuous.

In any other walk of life, this would be nuts. But in FOSS, this asymmetry has been normalized to the point that people treat it as the background of their lives. Well, we have to stop doing that. Stop taking this amazing windfall for granted.

It would help for us to stop using words like "product" when it comes to FOSS. Proprietary software is a "product". You pay for it. You are expected to trade something of value to gain access to it. Even then, you don't own it. It is fenced in with all sorts of terms and conditions and limitations. It's a product.

But FOSS is not a product. You pay nothing for it. You don't have to trade something of value to gain access to it. In every sense that counts, you own it. You can tinker with it, modify it, twist it into whatever shape you want and no one will sue you. The only condition that it imposes on you is that if you make your modified version available to the public, that you also publish the source code so that others in turn may tinker, modify and twist it to their needs. It is more like a calling… a philosophy.

Maybe if we treat it this way, we will be able to muster the respect that it deserves. I dunno. Then again, maybe some people will never get it and will just forever feel entitled.

---

### Post by donald187 on 2023-03-14
> **bernard010 said:**
> @donald187  Use &#8216;sudo pro detach&#8217; command.

Thanks.  Yes, I saw that.  Apparently this is a local computer thing and not an unsubscribe thing one does on one's Pro dashboard. 

 Truth is I thought they might be keeping a record of "subscribed machines" that would have to be unsubscribed if one were to reinstall Ubuntu without detaching first.  But perhaps they are just keeping a record of "active machines" as is posted on one's Pro dashboard.

---

### Post by maglin2 on 2023-03-14
I don't know about others, but I didn't start using Ubuntu Desktop because it was free, or because I espoused the FOSS ideals.
I started using it because Windows 7 was a nightmare. Endless problems with updates. Conflicts between the security applications (that everyone said I absolutely needed) and the OS. Blue screens of death. Sluggish performance on a brand new reasonable spec machine.
If Windows 7 had worked for me like XP did I would still be using it.
So I looked for something else that might work on the machine. Linux was suggested by the shop who sold me it.
I tried PCLinuxOS first. It worked a lot better than Windows, but there was a bit of a learning curve. I still have a soft spot for it though.
Then I tried Ubuntu 12.04 and was blown away. 
Everything worked, it was fast, beautiful and (to me) completely intuitive at the GUI level - and I had no need for anything other than the GUI, because nothing ever went wrong.
If there had been a three month free trial then canonical had wanted money I would have paid.
I still feel much the same way. 
I do now perceive a down side in this though.
If there was profit in Ubuntu desktop I think it pretty soon would be being run by a company with very different values to Canonical.

---

### Post by BBQdave on 2023-03-14
> **maglin2 said:**
> I don't know about others, but I didn't start using Ubuntu Desktop because it was free, or because I espoused the FOSS ideals. I started using it because Windows 7 was a nightmare.

That's how they get ya :)

Mac os9 was challenging, and my first OS. Loading GNU/Linux was an alternative, to hopefully something better.

With the GNU/Linux community, you have collaboration, helpful guidance, control of your pc, and growth :)

I think a balance can be struck to compensate those who develop GNU/Linux, and still have a community of free open development.

Hopefully the OP will gain an understanding of what it means to be in a community and the responsibility that goes along with the benefits.

---

### Post by DuckHook on 2023-03-14
> **maglin2 said:**
> I don't know about others, but I didn't start using Ubuntu Desktop because it was free, or because I espoused the FOSS ideals.

--snip--

If there was profit in Ubuntu desktop I think it pretty soon would be being run by a company with very different values to Canonical.
I'm very realistic about Canonical. They are not saints, nor should they be. They are just as happy to increase profits as the next guy. It's just that they chose FOSS as their stock in trade and the nature of FOSS limits how badly any company can go rogue. So, although you may not have initially cottoned on to Ubuntu because of FOSS ideals, it's important to understand that it's those ideals that make FOSS companies behave better than most.

There's nothing inherently wrong with trying to increase profits. We all do this when we seek the highest pay for the jobs that we do, so how can we begrudge it to Canonical?

If we keep these two things in mind, then seeing some self&#8209;promotion in Canonical's interfaces is not only to be expected, but welcomed. I want them to be profitable so that they hire the best devs. I want them to be profitable so that they will stick around for decades to come putting out good stuff. I want them to be profitable so that they have the resources to support forums like ours. However, profitability is not what keeps Canonical in line.

Desktop Ubuntu maintains its community integrity not because Canonical is a uniquely virtuous company—though they are clearly better than most—but because any attempt to privatize it will instantly cause it to be forked, with the vast majority of users flocking to the fork. This is what happened with Openoffice &#8594; Libreoffice, Owncloud &#8594; Nextcloud, and many others. Companies that accept the benefits of FOSS and that have built themselves up by leveraging FOSS understand this dynamic very clearly. Those that do not have disappeared from the ecosystem. This is possible only because the copyleft nature of FOSS makes it easy to make that fork. People benefit from FOSS ideals whether they realize it or not.
> **BBQdave said:**
> …I think a balance can be struck to compensate those who develop GNU/Linux, and still have a community of free open development…
I believe that Canonical is a good company. Unlike Red Hat (which is not a bad company), Canonical has made the decision to keep its brand monolithic and intact. I think that this is a gesture of respect extended to those of us who comprise its user base. They could have pulled a Red Hat and split the guinea pigs off from their paying customers. I would not begrudge them that. But they have decided that everyone will get the same benefits and only those who need *more* than 5 years of support and who have more than 5 computers should pay. This is very generous. I would argue that it is a degree of generosity that we have no right to even expect. Those who actually ***criticize*** it are crazy.

Canonical gives us this largess by making money from extended services, cloud services and corporate services. Far from criticizing them for promoting such services, we should be cheering them on.

---

### Post by BBQdave on 2023-03-15
> **DuckHook said:**
> I believe that Canonical is a good company. Unlike Red Hat (which is not a bad company), Canonical has made the decision to keep its brand monolithic and intact. I think that this is a gesture of respect extended to those of us who comprise its user base. They could have pulled a Red Hat and split the guinea pigs off from their paying customers. I would not begrudge them that. But they have decided that everyone will get the same benefits and only those who need *more* than 5 years of support and who have more than 5 computers should pay. This is very generous. I would argue that it is a degree of generosity that we have no right to even expect. Those who actually ***criticize*** it are crazy.

Agree.

It amazed me that Canonical offered the extra support - free, through Ubuntu Pro. You have access to enterprise level support, for personal use, for FREE!

If I hazard a guess, maybe the marketing idea to provide this for free, you get a sample, an idea of what is available. So in my situation, where I was on the board of directors for a homeschool group of 300 families, I would recommend Ubuntu Pro paid services to meet our organization's needs. I'm familiar with the distro, familiar with the GNU/Linux community, and here's a trusted community and service. Grass roots grown business :)

---

### Post by regor210 on 2023-04-13
'I Am Because We Are': The African Philosophy of Ubuntu.

$100 a year to run a secure system my cost. ummm. 

I have to think this over.

maybe move to Debian?

---

### Post by ian-weisser on 2023-04-13
> **regor210 said:**
> $100 a year to run a secure system my cost. ummm.

Re-reading the earlier posts in this thread, which dispel a lot of FUD, may be worthwhile for you.

---

### Post by BBQdave on 2023-04-13
> **ian-weisser said:**
> Re-reading the earlier posts in this thread, which dispel a lot of FUD, may be worthwhile for you.

Or even just read the previous post, my post :D

Where I talk about the FREE! Ubuntu Pro service. It's FREE, the opposite of $100. Pay no money for Ubuntu Pro service.
Did I mention, it's FREE! :P

Joking aside, it is amazing that Canonical offers an incredible distro (free) with patches from an open source community (free) and just to add a little more support... Canonical's paid staff provides Ubuntu specific patches free to individual users using a free distro. Again, amazing :)

---

### Post by regor210 on 2023-04-14
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libavformat58 libavfilter7 ffmpeg python3-mediainfodll imagemagick
  libswresample3 libswresample3 libzmq5 libmagickwand-6.q16-6 libmediainfo0v5
  libpostproc55 imagemagick-6.q16 libavcodec58 libavcodec58 libavutil56
  libavutil56 libavdevice58 libswscale5 libsdl2-2.0-0 libsdl2-2.0-0 libmysofa1
  libmagickcore-6.q16-6 libavresample4 imagemagick-6-common
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)

There's a lot not getting getting upgraded/updated here. Not what i would call FUD.

---

### Post by DuckHook on 2023-04-14
> **regor210 said:**
> There's a lot not getting getting upgraded/updated here. Not what i would call FUD.
Perhaps you need to understand the larger lay of the land:

You never got those updates before. They are all part of the Universe repo and are mostly frozen in place once the version status goes from beta to released. More importantly, apps in the Universe repo are not even officially supported by Canonical. They are the responsibility of the larger "Ubuntu community" like the app authors themselves, community volunteers or the upstream repos from which they are simply copied. This is made very clear in Canonical's docs. Canonical includes them essentially as a courtesy to their users: "extra goodies" if you will. This has been the case throughout Canonical's existence.

So, nothing has changed. Nothing is being taken away from you. You can't be deprived of what you never had in the first place.

But they are now offering ***official*** support for apps in the Universe repo if you subscribe to Pro. This is an extra offering. Frankly, it is a marvellous offering and constitutes an opportunity for users that is over and above what we have always had. The fact that everyone gets such an enhancement for free (on five machines) is quite generous.

If you don't want it, then continue to use Ubuntu as you always have and you are missing nothing. If you decide to take them up on their offer, then register as a Pro user and get something that you never had before.

This was explained quite clearly in the previous posts. I'm merely repeating what has already been written.

---

### Post by DuckHook on 2023-04-14
It bears adding that I, as an official "Ubuntu Member", qualify for free Pro enhancements on 50 machines. Yet I have not bothered to register for Pro at all. I am happy with the way that Ubuntu has always worked and see no reason to get updates to my Universe apps. The community tends to look after security patches well enough, so the added enhancements are usually for more current features which are mostly bells, whistles and pretty dresses. Since I'm happy with the way that my apps work and invariably upgrade every two years with each new LTS, I'm not that far behind in any case, so keeping up with the absolute latest is not worth the added exposure and instability.

---

### Post by lammert-nijhof on 2023-04-15
I use Ubuntu Pro for some older Ubuntu Virtualbox VMs: 14.04; 16.04 and since today 18.04, because coming week the 5 years will pass. I use the Ubuntu 16.04 VM every day for my banking. The VM is encrypted by Virtualbox and I use it exclusively for banking, no other browsing nor emails. The firewall is closed for inbound traffic. For Firefox and LibreOffice I use the latest stable snaps. 

Note that I combined the most hated Canonical products in 16.04; Unity; Snaps and Ubuntu Pro :)

---

### Post by Shobuz99 on 2023-04-20
> **duckhook said:**
> i appreciate your observation. It is true that we conduct ourselves based on long habituated expectations. But when those expectations are unrealistic or, in this case, hypocritical, then it is time for us to re&#8209;examine and change them.

We cannot expect canonical to keep giving us all of this awesomeness for nothing. They are not a charity (and even charities ask for money). Even if canonical operates so ultra&#8209;efficiently that they employ but 0.5% of the staff employed by the proprietary giants, these are still people who must be paid. I don't see any of those who are complaining the loudest giving away their working time for free. In fact, they likely demand the most they can ask for their work, so why do their expectations suddenly go into magical reverse for canonical?

Yes, we can all contribute in different ways. My contribution is to help out others. I figure that i'm doing my share by providing support. This is part of the indirect economic ecosystem that foss has fostered over the years, but we must never lose sight of the fact that it's still an ***economic*** ecosystem. And forum contributions only go so far: It can't pay for salaries, rent, utilities or even a cup of coffee.

Canonical can decide to hoodwink us the way that red hat does (i'm not dissing rh. They are just offering a necessary economic model that works for them). Rh has elevated its name brand entirely into the paid sphere. You can't even get on their forums without a paid account. They then created a second brand, fedora, that is basically a test bed in which nonpaying users are guinea pigs. There's no lts in fedora. It is, for all intents and purposes, a rolling release. When things go wrong, the guinea pigs just have to live with it until the devs get around to fixing it. If you want real stability in fedora, you have to pay to upgrade to red hat.

Is that what the whiners and the gripers want? For canonical to say: "tell you what. Lts is no longer available without payment. We will offer only standard releases for free. You will have to put up with the six&#8209;month upgrade hamster wheel, frequent breakages, regressions and incompatibilities, but that's the price you pay for getting something at no charge. If you want 5&#8209;year support, you will have to pay for our new something&#8209;else version." that would certainly deal with the unrealistic expectations i suppose.

I don't know about you, but i would consider the above as the real disaster; not this tiny smidgeon of self&#8209;promotion that i can so easily ignore when i upgrade.

The only thing that canonical has been "guilty" of is spoiling us.

[size=5]bam![/size]

---

### Post by ck-ricochet on 2024-01-03
> **ian-weisser said:**
> Yes, it's been discussed many times before.
And, as we have said before, you have misinterpreted the message. 

I recently updated Ubuntu 22.04 and encountered this message for the first time too. Updater still functions as before - the only exception being the gatekeeper Pro is now identified as the "more secure system". That's not difficult to misinterpret. The subsequent information kindly provided by you, and others are beneficial to the Ubuntu community. As always, without exception, it's necessary and insightful. Always appreciated too.

But it's not accurate to suggest the message was misinterpreted, when the information simply conveyed the gatekeeper to updater. Which hasn't existed as far as I've experienced - since the early millennium. Hence, the what the? ;) I can empathise with the OP. It's not meant as contrite. Open Software, by definition of the word "open" doesn't normally have gatekeepers. :o The end user isn't to blame for poor messaging of the change to the definition, open software - for at least 14 years (in my experience).

Canonical is absolutely free to change how it does business, but it has more responsibility to take on the messaging of it's changes - than just blaming the end user once it arrives. If there are a million users, then a million and one explanations may be required - or links to the website that explain the changes and why. End users aren't being paid for their free use of the open software, but the open software enterprise still benefits from the bugs they flush out. Creating a more refined end product, for the revenue income streams they develop separately. The end user is contributing by pointing out the flaws - including PR.

---

### Post by ck-ricochet on 2024-01-03
> **DuckHook said:**
> My even harder more unpopular question is:

When did *users* get so lame?

Since Canonical directly marketed (specifically Ubuntu) to non-technical people to take up their free open software. Ubuntu was made entirely to be user friendly, and differentiate itself from other free open software dists, requiring more tech savvy operators. Don't blame the end-user for what was the company's PR directive for expansion, at the time.

Now demand has outstripped supply, increasing wages are required to pay for a more stable product. This is understandable and I don't quibble over reasonable changes, to a good product.

What is poor form is changing direction, after well over a decade promoting itself as a (free) stable alternative to MS - then let the heat reach the audience as unnecessary complaining. I'm sure the directors spent months discussing how they could introduce a gatekeeper to software access, that didn't look like one. Otherwise it would compromise their branding. Kudos for maintaining an equilibrium necessary for change without compromising their brand. But any poorly explained changes to end users, isn't the end users fault. 

> **DuckHook said:**
> If self&#8209;promotion is a crime, then be the first to check yourself into jail. We all do it. But we hide it under self&#8209;serving euphemisms like "networking", "personal growth", "career enhancement", "making new friends", "putting our best foot forward" and a thousand others. Anyone with a LinkedIn profile is advertising themselves. So is anyone with a Facebook profile, or a Tinder profile, or a blog. Dressing up for a night out on the town is self&#8209;promotion. So is combing your hair and putting on make&#8209;up.

These are personal activities people can opt into without a gatekeeper. There are no options with new changes to updater. Requiring a subscription to Pro, in order to dismiss it. A more comparable situation using your example, would be someone entering your room, combing your hair and putting on your make up for you - then chewing you out as ungrateful for finding it all rather disturbing. Especially when this arrangement was not an issue before - opting into what make-up you chose and how to comb your hair. 

> **DuckHook said:**
> This whine has been posted on these forums ad nauseum.

Give your heads a shake, people.

Poor messaging and introduction to end users, is why negative feedback it's becoming entrenched. If Pro was made an option, and not a gatekeeper, through disabling it from showing in updater altogether (without a subscription) people could move on. Enjoying what they've had before (update wise) without constant reminders from updater, to subscribe to Pro. Why is this the first feature, end-users haven't been able to disable in Ubuntu before? That's a pretty big shift away from user-friendliness, and people noticed. Lots of people. It was made obvious by not being able to disable it.

It's bloated software when users are given optional features, that cannot be disabled when using apps. A change in company directive, does not require psychoanalysing individual responses to self-promotion. It's the company directive that changed. Not the end users. There is no adequate messaging to breach the gap, which reflects poorly on company PR.

---

### Post by ck-ricochet on 2024-01-03
> **DuckHook said:**
> We cannot expect Canonical to keep giving us all of this awesomeness for nothing.

I'm not stalking your posts (honestly) you just raise some interesting points I have a slightly different take on. One of those is how Canonical is giving away all this freedom for nothing. If they had to pay a team of coders to test the bugs in their distros, it would cost a lot more money over a longer timescale. When users choose to sacrifice their time learning how a certain distro works, then sending feedback when it doesn't work as expected, they are shortening the expense and development schedule for a stable distro. 

End users have a symbiotic relationship with free software developers, which benefits both parties. As end users, participate in the development schedule without pay. 

> **DuckHook said:**
> I don't see any of those who are complaining the loudest giving away their working time for free.

It took me an incredible amount of time to learn Ubuntu. Over a decade and I'm still learning. That required sacrificing free time, and no-one was paying me to support a free software company to improve their end product. Nor did I expect them to. There are many value added products which Canonical gains revenue from in the software marketplace, separate to Ubuntu distros. Which have come about a lot quicker, because of user participation in free software distros. That's the back-end we contributed to, but see no financial gain from. Which I'm okay with. That's the symbiotic relationship both parties benefit from.

> **DuckHook said:**
> My contribution is to help out others. I figure that I'm doing my share by providing support. This is part of the indirect economic ecosystem that FOSS has fostered over the years, but we must never lose sight of the fact that it's still an ***economic*** ecosystem. And forum contributions only go so far: it can't pay for salaries, rent, utilities or even a cup of coffee.

A wonderful contribution I may add. Without more knowledgeable mentors helping budding users, the company doesn't get to expand with new developments shelved instead. It needs end users and people to teach how to use. But Canonical isn't pulling chump change here. They're making well over 140 million p/a, with around 5 mill profit. I support their progress and expansion too. Just not by rolling end-users under the bus via poor messaging and implementation of new distos.

> **DuckHook said:**
> Is that what the whiners and the gripers want? For Canonical to say: "Tell you what. LTS is no longer available without payment. We will offer only standard releases for free. You will have to put up with the six&#8209;month upgrade hamster wheel, frequent breakages, regressions and incompatibilities, but that's the price you pay for getting something at no charge. If you want 5&#8209;year support, you will have to pay for our new something&#8209;else version." That would certainly deal with the unrealistic expectations I suppose.

I have confidence, Canonical can continue to steer this symbiotic relationship successfully, between free community participation and increasing backend revenue streams, on shorter time frames. It's been successfully managing it for (approaching) 20 years now. They can handle community feedback without getting sensitive about it. Because it's quite literally their bread and butter. Free feedback becomes a reduced cost, income revenue - they didn't even have to pay or coerce the participants to see the value in participating.

> **DuckHook said:**
> The only thing that Canonical has been "guilty" of is spoiling us.

And making money from it, LOL. Which as I said previously, I support. We work symbiotically, or we don't work at all. Which is why it bothers me to see the end-users providing quite strong feedback, for a poorly communicated and rolled out feature that completely changed the user experience. With the only response to stop complaining and be grateful. Even if only an unofficial response. I place more value on my contribution over the 10+ years sacrificed free time, and I hope you do too.

 As you're not just providing free support - you're literally building the next generation of end-users for free. Your sacrificed free time, while also working for income - has ensured a company can make almost 5 mill in profit. They're not making chump change, so your contribution to education, shouldn't be treated as chump change either. None of the end users are just receiving a free product from a generous company. It's an exchange of symbiotic proportions. If the feedback is strong, there's a substantial reason for it.

---

### Post by ian-weisser on 2024-01-03
> **ck-ricochet said:**
> What is poor form is changing direction, after well over a decade...

Yawn. Scheduled releases. Default application arguments. Changed support calendars. Upstart. Systemd. Ifupdown. Unity. Return to Gnome. Netplan. Snap packages.

"changing direction" happens all the time in the Open Source community. And some folks claim the sky is falling each time.
Trying New Things happens all the time in the Open Source community. And some folks claim each experiment is a harbinger of doom.

There is nothing preventing the community from rebuilding apt without the Pro patches and uploading the result. Community MOTUs exist for a reason.
That nobody has bothered suggests the complaints about Pro messages are somewhat more clutching-of-pearls than real outrage.

The Pro messages also show an important point: Folks weren't getting those security updates before...and did not know about it. Now they know.

Canonical and Ubuntu have a long history of "poor messaging". That's a GOOD thing: They are run by technical people, not marketers. They have lots of transparency, whether folks choose to look or not. Most decisions (with some big exceptions) have been made in the open after tedious discussion.

---

### Post by TheFu on 2024-01-03
Ubuntu LTS support is free. They ask for nothing in return.

Ubuntu PRO is **not** free because they require "something" in return.  

Whether that "something" is acceptable or not is an individual question.  Anyone running Ubuntu has already provided a huge amount of trust to Canonical. Is the little bit more they ask for to get PRO a big deal or not?  That's a line not to be crossed by some people, while others will easily cross it.

---

### Post by SeijiSensei on 2024-01-03
I just registered for a free Pro key and upgraded my system with the esm packages. Looked like the only thing that was upgraded was, of all things, VLC. Since I only use that to watch files downloaded to my network, I doubt whatever security vulnerability existed in VLC or its related packages mattered to me.

---

### Post by Dennis N on 2024-01-03
Use Software Updater instead of the terminal for upgrades. It does NOT mention Pro. 

That said, I enrolled my Ubuntu 18.04 when the extended support was first offered, and I'm happy with the service and the 10 years support. No other Linux does this as far as I know.

---

### Post by ck-ricochet on 2024-01-03
All that may be true, ian-weisser except the estimation that Canonical is run by technical people, not marketers. Because when first releasing Ubuntu, Canonical used a marketing campaign to appeal to the Windows crowd. What made Ubuntu unique among other Linux distros, was spreading the message it could be used similarly to Windows. Plug and play. Intentional strategy about messaging was employed, that you don't have to be technical to have an alternative OS.

Canonical's website designers were on the same brief, making it seamlessly easy to install Ubuntu, to people who had never heard of an ISO file before or partitioning hard-drives. Canonical is run by business people who employ a host of individuals - some with technical skill, some with marketing, but they're all tapping into the free software community to encourage expansion, innovation and flushing out problems to fix the end product. If it was just run by technical people, Canonical wouldn't be turning a 5 mill profit, after making over 140 mill. Only through winning a huge market share back from Windows, was it possible, and they achieved it specifically through messaging. 

Without demand from non-technical individuals, Canonical could not compete with Windows on the backend. Otherwise they would have to pay all those technicians and bug fixers (like Windows does) which isn't Canonical's strategy. My point isn't to silence what others in the community feel about certain feedback. It's to bring transparency to how Canonical brought profit to the free software marketplace. So Windows had to eventually adopt it as part of their own OS options. Specifically through the demand for Ubuntu, making it as plug and play, as possible. That plug and play crowd came with the messaging. They didn't cost a cent to employ, but through their rapid reporting of issues, and willingness to speak up (paired with the technical group) Canonical still remains a viable alternative to Windows. 

If it was just about making money, they would be doing what Windows is by now. So there is something very different and deliberate to Canonical's strategy. Transparency? Yes. Community support? Religiously. Making money? As long as we can all fulfil our contributions as a community. It's not dependent on any one of us, but it certainly requires all of us. 

Next time you're thinking - here we go again, more complainers. Replace it with - they're part of the free labour community, Canonical turned 5 mill profit on. I'm glad they became the market-share to compete with Windows. You might not like everything they say, or how they say it, but without their demand Ubuntu wouldn't be what it is today, as fast as it got here. They are the numbers Canonical needed. No-one in the free software community, got to where we are presently - alone.

---

### Post by lammert-nijhof on 2024-01-06
I have three Ubuntu VMs running on Ubuntu Pro from the time, that it was still called "Extended Security Maintenance".  The three distros are 14.04; 16.04 and 18.04, I'm happy, that they give me the possibility to enjoy them safely for 10 years.  
I proudly announce, that I combined all major functions, despised by the Canonical haters, in one system.  I still use Ubuntu 16.04 ESM daily almost hourly for banking, it has them all; Unity; Snaps and Ubuntu Pro.  I use the latest stable snaps for Firefox and LibreOffice, especially Calc.

---

