---
title: "The ongoing CNR debate: an alternate suggestion..."
date: 2006-03-03
forum: The Cafe
---

### Post by darkmatter on 2006-03-03
We've all seen the debate regarding Linspire's CNR service and Ubuntu... and though we all have our opinions (I, personally, fully support the idea), the subject got me thinking of package management in general... and how suck a service could be possibly integrated with Ubuntu... so here is a brief introduction as to the source of the idea and the method in which it could work (forgive me if anything is off... I am not 100% certian as to the inner workings of CNR)

I've always liked the 'catalog' style of CNR's warehouse... It is very thorough in the way it presents the description of an application to the user *SCREENIES!!*=)(many of which may not know what said app is otherwise... particularily new users) and for some time now have been in the planning stages of a desktop/distro project to help... polish... linux in terms of its presentation, as well as creating some new approaches to things like file management and the like... one of those ideas was a CNR-inspired package utility to offer a more graphical frontend to apt. Although I never worked out the particulars of how the app would be... the current debates got me thinking about it again... only now with the idea of added CNR (or CNR-like service) so here is my proposal for integrating such a service into Ubuntu. This may seem a little... rough... so please forgive me... I'm mostly laying this out as I go along ;)

The general idea:

A gtk+ frontend to apt that cmbines both the features of Synaptic/CNR in a single interface.

The repositories could be divided into two main categories: 'Warehouse' (like CNR: pretty per-app pages... nicely formatted with all the screenies and the like) and 'Other' (which would display a standard list of the repository contents in the same manner as Synaptic currently does). However the 'Warehouse' would not be exclusively 'CNR' type content in the Linspire way (subscription services), but could/would give free access to an apt 'Warehouse' if we could get people to contribute content/help rebuild the primary repos/mirror some content (such as the page descriptions for the apps), allowing free access to the repositories that already exist, with the added bonus of a CNR-like presentation for those repositories (spit and polish baby :mrgreen: )

As for CNR (just look at it as 'value-added' content)... I would assume the service works by importing a subscription key into the software. If that is indeed the case... then pay-for services such as LEGAL codecs (for those who live in countries victimized by legislations), dvd playback, etc., as well as added bonuses such as, for example, Star Office and/or items like the shareware files needed to run some native linux ports of games (not all of us have windows versions ;)), could be kept in a separate, subscription only repository. You would need to purchase a subscription to recieve a passkey to  said repo, but it would give you access to value added features (some licenses could even be included in the subscription... like codecs) as well as the opportunity to purchase proprietary software for linux, with the balance being charged to your account for the repo should you choose to purchase anything. Trying to access codecs, etc in the main repos without a pass would display a notification that these are items which, according to legislation in certian countries, cannot be used legally without purchasing a license, and therefore may only be accessed with a subscription whch covers the license as well as gives you access to added features/software not otherwise available for download/install (perhaps even a secure server tied to the repo could store account information, allowing the user to quickly install previously purchased items should they ever need to reinstall the os??)

For users who live in countries not victim to legislation regarding w32codecs, etc. they can simply add their favorite repo to the 'Other' category and fetch the packages themselves... without need to pay for a sevice they have no use for. Thus balancing the equation by taking into account the fact that not all need/want to pay for such. the choice (and, depending on location, potential legal issues-- are the users responsibility)

You may ask: what is the possible benefit of such an implementation?? I can think of several possibilities myself... here are a few:

1) Instead of cluttering an installation with multiple frontends for software installation, you instead have one that can handle the job of all (Synaptic meets CNR/gnome-app-install)

2) All benefit from improved package descriptions when available (not just CNR subscribers)

3) You still have the choice to pay or not to pay. Though, obviously, subscription service would entitle you to added features, etc. The choice would still be yours.

Anyway... thats a rough (very) idea of how I think CNR integration, as well as general package management enhancement could be/should be implemented in a smooth and integrated manner... please excuse any typos and the like... it's 5:10 am... I haven't slept, and I'm to lazy to proof-read ;)

Opinions??? Love it? Hate it?

Speak your mind!! :D

---

### Post by bonzodog on 2006-03-03
hrm...no, I like the current system. I can see where you are coming from though, with this. I like synaptic, and also am now fairly fluent with apt.I think that the add/remove applications item in the menu ought to just be linked to synaptic. Synaptic itself could do with some minior modification though, it's layout is a little confusing to most people.

---

### Post by Swab on 2006-03-03
Integrating CNR into Ubuntu's default package management system would, in my opinion by totally at odds with the Ubuntu philosophy...  Ubuntu would be encouraging the use of closed source, closed standards codecs and so on... 

I might be OK with CNR being available in the repos, but if it's default, or worse still part of the standard package management system, then I'm out of here.

---

### Post by Arktis on 2006-03-03
We must continue to seek the mass adoption of open alternatives.  We must not fall prey to the sacrifice of putting short term gain over the long term.  We must not place ease of use over future benefit.

---

### Post by darkmatter on 2006-03-03
[QUOTE=Arktis]We must continue to seek the mass adoption of open alternatives.  We must not fall prey to the sacrifice of putting short term gain over the long term.  We must not place ease of use over future benefit.[/QUOTE]

I'm not talking about sacrificing freedom here. This is just a deviation of the original concept of how it COULD be implemented in Ubuntu's possible adoption of optional CNR services. As stated, the CNR aspect would have its own section, with a disclaimer/explaination regarding the services offered. It would not be promoting the use of those services, nor including the closed source CNR client... the client itself would not be CNR, and would be open, it would (likely) download some additional libraries to enable CNR functionality for those who desired it, and as stated, would inform the user that the services in question are OPTIONAL if they desire to use them, but are not manditory.

How is allowing more choice to the use out of box affecting future benefit??? It is the individuals choice whether or not to implement the services, and the client would still WORK without them.... for free and with enhanced content.

It's not an issue of the philosophy behind Ubuntu... its an issue of finding a way for clean integration of additional services for those who desire them, with the knowledge that some of those services are not 'free' as in speech or as in beer... In the end... it would still be my choice, or yours, as to whether or not to use the service.. (personally, I wouldn't use 'enhanced' subscription services... I don't need nor want them, but there are many who would/do)

Personally, I'd just like to see better content in package management for new users (screenies, etc... the majority of users actually need stuff like that to help them decide... oddly enough) 

I just think... from a polish point of view... and in terms of making Ubuntu feel more professional, that the option to enable such a service by default, without the need to be 'closed' about it, or by ramming it down a users throat, but instead giving them an informed option, is possible (more than possible... it can literally be done) without infringing on the ubuntu philosophy or needing any type of 'sacrifice'..

Remember... above all, the Ubuntu philosopy is about the freedom of choice... And in the end, it is we, the user, that decides what we do with our system... and not the community or some lofty ideal... 

After all, you can look at it this way... we have proprietary drivers, restricted kernel modules, even Suns JRE and other non-free, closed source items in the repos as well as in a default install. By your logic... aren't those a  'sacrifice' for short term gain and ease of use?? If so, should they not be removed to 'purify' the distro for future benefit???

If Ubuntu ever did that... it would burn and sink FAST...

Just my random thoughts... :)

---

### Post by Brunellus on 2006-03-03
hate it.  CNR is not part of the Ubuntu core, and should not be.  It could be integrated as a separate add-on.  But the impression should not be given that Ubuntu is actively promoting nonfree software.  

I have no objection to CNR;  I do object to CNR being as tightly integrated as you want it to be.

---

### Post by BoyOfDestiny on 2006-03-03
[QUOTE=darkmatter]I'm not talking about sacrificing freedom here. This is just a deviation of the original concept of how it COULD be implemented in Ubuntu's possible adoption of optional CNR services. As stated, the CNR aspect would have its own section, with a disclaimer/explaination regarding the services offered. It would not be promoting the use of those services, nor including the closed source CNR client... the client itself would not be CNR, and would be open, it would (likely) download some additional libraries to enable CNR functionality for those who desired it, and as stated, would inform the user that the services in question are OPTIONAL if they desire to use them, but are not manditory.

How is allowing more choice to the use out of box affecting future benefit??? It is the individuals choice whether or not to implement the services, and the client would still WORK without them.... for free and with enhanced content.

It's not an issue of the philosophy behind Ubuntu... its an issue of finding a way for clean integration of additional services for those who desire them, with the knowledge that some of those services are not 'free' as in speech or as in beer... In the end... it would still be my choice, or yours, as to whether or not to use the service.. (personally, I wouldn't use 'enhanced' subscription services... I don't need nor want them, but there are many who would/do)

Personally, I'd just like to see better content in package management for new users (screenies, etc... the majority of users actually need stuff like that to help them decide... oddly enough) 

I just think... from a polish point of view... and in terms of making Ubuntu feel more professional, that the option to enable such a service by default, without the need to be 'closed' about it, or by ramming it down a users throat, but instead giving them an informed option, is possible (more than possible... it can literally be done) without infringing on the ubuntu philosophy or needing any type of 'sacrifice'..

Remember... above all, the Ubuntu philosopy is about the freedom of choice... And in the end, it is we, the user, that decides what we do with our system... and not the community or some lofty ideal... 

After all, you can look at it this way... we have proprietary drivers, restricted kernel modules, even Suns JRE and other non-free, closed source items in the repos as well as in a default install. By your logic... aren't those a  'sacrifice' for short term gain and ease of use?? If so, should they not be removed to 'purify' the distro for future benefit???

If Ubuntu ever did that... it would burn and sink FAST...

Just my random thoughts... :)[/QUOTE]

I agree with many of your points, but I have issues with a few.

If users want some sort of gtk2 front-end different from synaptic... Ubuntu has it... It's called Add/Remove Applications. If you think screenshots are necessary suggest it, or perhaps links to the software home pages etc... In dapper it even has checkboxes "show unsupported apps" and "show proprietary apps". No one is charging me though. That's where the difference lies. No special fees, it's for ANYONE (Ubuntu philosophy).

We also have fans of the GPL here... There is focus on freedom of what you can do with code. If the front-end and/or codecs are closed, that is being limited. However, you mention this occurs with non-free stuff being included. Absolutely true. I try and use the free alternatives if possible. I get the choice to use 'radeon' instead of 'fglrx'. 

As for should Ubuntu start removing them (at least from the default install), I would say so once a viable open alternative exists. The choice should remain (keep the non-free in the repos).

Anyway, I don't really mind the CNR thing, as I said in the other thread I wouldn't use it anyway. What I would mind is if it brings some form of "product activation" DRM scheme, etc. I feel this goes against Ubuntu and Free Software (read as GPL).

---

### Post by darkmatter on 2006-03-03
Valid points... I'm an OSS zealot myself... but even moreso I'm about the freedom to CHOOSE. I'm just saying allow the choice to be easier... or more appropriately... more polished... for the user... if you look at my second post... the client I propose is not CNR proper... but allows access to CNR services for those who desire them... its not a DRM activation scheme... just an integration of cnr for those who decide to enable that functionallity... and thus install the additional component from some repo in doing so... the thing being... that instead of downloading a seperate client, it would integrate the core functionality (as in a modular library) into the package manager... though that modular component would still be closed... it would not affect the free nature of the client nor involve some 'lockout' to the free repos, etc.

Like I said... it not what *I* want... its just an idea as to how integrating the option of CNR could be handled... to make it fit in smoothly for those who desire it... I'm all for promoting open standards... use them nearly exclusively (except cases of backwards compatibility)... I'm just against shoving those standards down others throats... when the OSS community or members of it do as such... it make us seem like nothing more than a 'free' eqivalent of Microsoft and its business partners...

What I really want??? A CNR style (as in web content) package management frontend for apt... free and open (both speech and beer)... the CNR thing is just an Ubuntu specific idea as to how to integrate CNR for those who decide to utilize it...

Anyway... don't know if that makes much sense... and I need sleep before I continue talking about it... the sheep are getting rather impatient... they want to be counted ;)

---

### Post by BoyOfDestiny on 2006-03-03
I hear ya. :) (I'm a fan of old games, which tend to be closed... Although a "lucky" few do get open sourced or donated to public domain. I do run them inside free software apps ;)... Not much different from viewing a pdf or watching a dvd in Linux in my book.

Anyway, the closest thing I've heard of for web package installs.

Klik

[http://klik.atekon.de/](http://klik.atekon.de/)

Have a good night.

---

### Post by darkmatter on 2006-03-03
Yup... and yup to klik as well... know about that one... but it would still be nice for package management to have all the pretty content.... with a gconf option for experienced users to kill it... obviously :)

Thank ya'... thank ya' very much

night all

ELVIS HAS LEFT THE BUILDING!

---

### Post by frodon on 2006-03-03
Why not a package for CNR but no logo, icons, references or any front-end in ubuntu by default, that's really clear for me.
A package is enough, doing more will surely decrease the number of ubuntu users (including myself).

---

### Post by midwinter on 2006-03-03
Anything more than a package in the restricted repo, would be, for me, too much.

---

### Post by bugmenot on 2006-03-03
> Hi Kevin

There is no easy way to say it, so i'll say it.

All this sounds to me like linspire(lindows) attempt to coup
Ubuntu(software/users/developers).

Linspire is increasingly becoming irrelevent, as ubuntu's ease of
use grows......
with the features which add to ease of use in Ubuntu being free,
users are begining to question the purchase of linspire over ubuntu.

as i see it, ubuntu has climbed over Fedora to get just below suse in ratings

So i propose the following actions:-
>start selling ubuntu in lieu of linspire
>find a new value add service, that you can ethically charge for
(in lieu of ease of use CNR service)
>IDEA: Start a QA firm, that helps other software firms port their apps
to run on Ubuntu, natively or under wine(ala codeweavers)
>IDEA: start a firm selling training videos, so that users can skip the howto's
Videos detailing how to install >17000 software packages from Debian repositories will be welcome.
>people have found niche's like montavista linux, find something else.

In conclusion what i am trying to say is that instead of a business,
hell bent on selling a commodity(hardware/software DVDs)
Sell Services, poeple need to be shown the way

Freaky IDEA
One fine day, a shopper buys complete commodity hardware from
say walmart, he/she gets a coupon to avail the personal services of
an Ubuntu nazi, you know the guy from LUG install fest,
the coupon has a charge $18 say.SO the geek configures everything for
this shopper, and teaches him a few tricks, shows him/her the way
...in short its the $18 coupon is a membership to a lug,
go run wild with the idea

probably enter into a contract with kinko's for printing manuals, and fedexing
it to the customer.

QED

---

### Post by John.Michael.Kane on 2006-03-03
As a user who is willing to read howto's or linux books, and spend the time to learn how to compile a program or just install a deb, I would have no need or use for cnr, if cnr is going to pushed then it should pushed at the users who "NEED" it.. also if cnr is going to be used for mulitmedia codec's only then maybe they should make a multimeda only version of ubuntu with cnr marketed for home music/video studo users. since most of the post seem to be geared with codec talk.

Just my thoughts...

---

### Post by Bandit on 2006-03-03
Not Bad, BUT.... Many users do not want CNR intergrated into the OS that closely. I know I dont and I am for CNR offering its services.

But, I would like to see a catalog frontend for Ubuntu Synaptic/Apt per say.
There are many programs in the repositories that most users even my self dont know about. 
This would be a GREAT idea to discover what Ubuntu offers.
Maybe you can make a catalog and offer keywords that pull up the program in Synaptic or Adept for the user to install. Now thats a smashing idea.. :D

Cheers,
Joey

---

### Post by LuisC-SM on 2006-03-03
[QUOTE=frodon]Why not a package for CNR but no logo, icons, references or any front-end in ubuntu by default, that's really clear for me.
A package is enough, doing more will surely decrease the number of ubuntu users (including myself).[/QUOTE]
Not a bad idea.

I've been using Ubuntu in one of my desktops for 5 months maybe a little bit more, and I've been using Linspire and Lindows for almost one year.
The reason why I turned to linux was not far the same as the  99.9% of the poeple who was tired of M$ Windowze.

When I found Linspire, (after seeking for around one week in which distro I will install in all my PCs), I thought I was in heaven. I got rid of M$.

Later, I found Ubuntu and just loved it, as much as I love Linspire. 

Ubuntu gave me the chance to learn Linux just the way I wanted to learn (the hard way). I even requested 15 disks to give them away to my friends and coleages who were using M$ window$. From all the disks I gave away, only ONE is using it as a dual boot, the rest didn't even care and even made some hard (IMHO) jokes about Linux.
Nevertheless, that didn't stop me about trying to turn topeople into linux. and some weeks ago 2 of this people turned 100% into Linux by installing Linspire.
Linspire; as Ubuntu, is not made for everybody, not every body likes the chocolat or the lemon. It's only a matter of tastes. Which to me is oour Linux world.
I paid for CNR $US 50.00 (NOT $20.00), and this 50 bucks I paid have made my life so easy with my children that we do not worry anymore or even think about window$. My youngest daughter (8 years old) is using Ubuntu and she is so happy,,, My wife and my other 2 daughters are using Linspire and they are really happy.
I believe in Linux as I believe in freedom, in this laptop right now I have Linspire but I used to have Ubuntu, the only reason why I use it is because of codecs, otherwise it'll still be in Ubuntu.
Ubuntu gave me the choice that I was looking for, Ubuntu; as Linspire, made me believe in Linux. Months ago I spent thousands of dollars with wiindow$ and I spent thousands of headaches and hard nights due to viruses and pc hungs, reformatings, etc.
Linux has changed my life I will NEVER go back to window$ (that's a fact). The only 2 distros that I love are Ubuntu and Linspire. Either one in it's own way, if Ubuntu will include CNR as an OPTION, I will be very happy as far as CNR made my life easier, plust the cost will be even cheaper than it was 11 months ago.

Kind Regards

Luis C. Suárez

---

