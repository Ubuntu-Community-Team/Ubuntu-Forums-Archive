---
title: "Stupid/late question regarding MP3 support"
date: 2006-03-12
forum: The Cafe
---

### Post by desperatecoffee on 2006-03-12
So, does this--

[http://www.fluendo.com/press/releases/PR-2005-05.html](http://www.fluendo.com/press/releases/PR-2005-05.html)

--mean that MP3 will be officially supported in Dapper?

---

### Post by woedend on 2006-03-12
there were arguments about this a while back when news first came out about fluendo.  I believe I read that it wouldnt be included in ubuntu by default.

---

### Post by bjweeks on 2006-03-12
[QUOTE=woedend]there were arguments about this a while back when news first came out about fluendo.  I believe I read that it wouldnt be included in ubuntu by default.[/QUOTE]

No it won't there are many oss mp3 decoders but there are still patents.

---

### Post by doclivingston on 2006-03-12
The Fluendo MP3 binary plugin is fully patent licensed.

However, distributing the binary plugin with GPL-licensed applications that use it is a violation of the GPL. This leads to an issue with three solutions:

a) Don't use the Fluendo binaries, and have Ubuntu build from source. This results in it not being patent licenced.
b) Don't distribute them together. i.e. it won't be out-of-the-box, but if you download and install the plugin yourself, it will be fully legal.
c) Don't ship GPL-licenced applications that will use the plugin with Ubuntu. This means dropping Rhythmbox; it means amaroK-gstreamer couldn't be shipped as default. There is some debate, but there may also be problems if an application uses the Fluendo plugin and a GPL'd plugin (e.g. the cd-ripping ones) at the same time, which may affect Banshee.


Basically, if you download it yourself, eventhing is fine. Shipping it in Ubuntu solves the patent issue, but it still has legal problems.

---

### Post by bjweeks on 2006-03-12
[QUOTE=doclivingston]The Fluendo MP3 binary plugin is fully patent licensed.

However, distributing the binary plugin with GPL-licensed applications that use it is a violation of the GPL. This leads to an issue with three solutions:

a) Don't use the Fluendo binaries, and have Ubuntu build from source. This results in it not being patent licenced.
b) Don't distribute them together. i.e. it won't be out-of-the-box, but if you download and install the plugin yourself, it will be fully legal.
c) Don't ship GPL-licenced applications that will use the plugin with Ubuntu. This means dropping Rhythmbox; it means amaroK-gstreamer couldn't be shipped as default. There is some debate, but there may also be problems if an application uses the Fluendo plugin and a GPL'd plugin (e.g. the cd-ripping ones) at the same time, which may affect Banshee.


Basically, if you download it yourself, eventhing is fine. Shipping it in Ubuntu solves the patent issue, but it still has legal problems.[/QUOTE]


So it fixes nothing as you, as you can just install mad now.

---

### Post by doclivingston on 2006-03-12
[QUOTE=bjweeks]So it fixes nothing as you, as you can just install mad now.[/QUOTE]

If you download and install the mad plugin, you don't have a patent licence for the MP3 patents.
If you download and install the Fluendo mp3 plugin, you have a fully-licenced MP3 decoder.

If you live somewhere without software patents, the difference is meaningless. If you live somewhere with software patents, it means you couldn't get sued for patent infringement (not that they are likely to ever sue end-users).

---

### Post by bjweeks on 2006-03-12
[QUOTE=doclivingston]If you download and install the mad plugin, you don't have a patent licence for the MP3 patents.
If you download and install the Fluendo mp3 plugin, you have a fully-licenced MP3 decoder.

If you live somewhere without software patents, the difference is meaningless. If you live somewhere with software patents, it means you couldn't get sued for patent infringement (not that they are likely to ever sue end-users).[/QUOTE]

You don't need a licence to use mp3...

---

### Post by doclivingston on 2006-03-12
[QUOTE=bjweeks]You don't need a licence to use mp3...[/QUOTE]

Yes, you do (which is the reason most distros don't ship decoders).

If you use Windows, Microsoft has paid for the licence.
If you use MacOS, Apple has paid for the licence.
If you use a distro which ships a mp3 decoder, they either have paid for it or are ignoring the legal risk of being sued.

---

### Post by bjweeks on 2006-03-12
[QUOTE=doclivingston]Yes, you do (which is the reason most distros don't ship decoders).

If you use Windows, Microsoft has paid for the licence.
If you use MacOS, Apple has paid for the licence.
If you use a distro which ships a mp3 decoder, they either have paid for it or are ignoring the legal risk of being sued.[/QUOTE]

Care to back that up?

---

### Post by doclivingston on 2006-03-12
[http://en.wikipedia.org/wiki/Mp3#Licensing_and_patent_issues](http://en.wikipedia.org/wiki/Mp3#Licensing_and_patent_issues)
[http://www.mp3licensing.com/royalty/index.html](http://www.mp3licensing.com/royalty/index.html)  (PC Software Applications: MP3 decoder)

---

### Post by bjweeks on 2006-03-12
[QUOTE=doclivingston][http://en.wikipedia.org/wiki/Mp3#Licensing_and_patent_issues](http://en.wikipedia.org/wiki/Mp3#Licensing_and_patent_issues)
[http://www.mp3licensing.com/royalty/index.html](http://www.mp3licensing.com/royalty/index.html)  (PC Software Applications: MP3 decoder)[/QUOTE]

"the Fraunhofer Institute sent a letter to several developers of MP3 software stating that a license was required to "distribute and/or sell decoders and/or encoders"."

---

### Post by bjweeks on 2006-03-12
This topic has been talked to death, you should try reading some of the old threads on it.

---

### Post by Jucato on 2006-03-12
Now I'm confused...
You need a license to develop coders/decoders for MP3, right?
But do you also need a license to use these codecs, which you will need to play MP3's? :confused: 
Argh! This is making my head ache...

---

### Post by bjweeks on 2006-03-12
[QUOTE=Fenyx]Now I'm confused...
You need a license to develop coders/decoders for MP3, right?
But do you also need a license to use these codecs, which you will need to play MP3's? :confused: 
Argh! This is making my head ache...[/QUOTE]

You need a license to develop coders/decoders for MP3, right?
But do you also need a license to use these codecs, which you will need to play MP3's?

No.
No.

You need a license distribute a player that can encode or decode mp3's or to stream mp3's for profit.

---

### Post by woedend on 2006-03-12
Do I need a license to distribute mp3, mp3PRO or mp3surround encoded content?

Yes. A license is needed for commercial (i.e., revenue-generating) use of mp3/mp3PRO in broadcast systems (terrestrial, satellite, cable and/or other distribution channels), streaming applications (via Internet, intranets and/or other networks), other content distribution systems (pay-audio or audio-on-demand applications and the like) or for use of mp3/mp3PRO on physical media (compact discs, digital versatile discs, semiconductor chips, hard drives, memory cards and the like).

**However, no license is needed for private, non-commercial activities (e.g., home-entertainment, receiving broadcasts and creating a personal music library), not generating revenue or other consideration of any kind or for entities with associated annual gross revenue less than US$ 100 000.00. **

from bjweeks second link

---

### Post by bjweeks on 2006-03-12
To sum it up. Ubuntu can NOT ship with mp3 surport with out paying 60,000 but can put the decoder in the repos so users can install it.

---

### Post by ComplexNumber on 2006-03-12
[quote=doclivingston]Yes, you do (which is the reason most distros don't ship decoders).

If you use Windows, Microsoft has paid for the licence.
If you use MacOS, Apple has paid for the licence.
** If you use a distro which ships a mp3 decoder, they either have paid for it or are ignoring the legal risk of being sued**.[/quote] isn't that the reason why fluendu paid the licence? in other words, so distros can have mp3 support out of the box. if ubuntu isn't including it by default, its a fault of ubuntu. the situation now on linux is exactly the same as it is on apple and windows. if you can do it on them, you can now do it on linux. end of story.


> 
 In order to improve the GNU/Linux and Unix multimedia experience Fluendo announced today the immediate availability of their MP3 plug-in for the GStreamer  multimedia framework. The MP3 decoder is available free of charge both for  individual end users and GNU/Linux and Unix distribution makers.

 In addition to making their licensed binary plug-in available to the public  Fluendo also released the source code to this MP3 plug-in under the very  permissive MIT license allowing all kind of developers and companies  access to it.

 The GStreamer plug-in will allow playback of the popular MP3 format using many popular open source applications like the Banshee music player and  Totem media player. **While various MP3 playback solutions already are  available this one will allow MP3 working out of the box with  any distribution entering into our distribution agreement.**
   
[source]("http://www.fluendo.com/press/releases/PR-2005-05.html")

---

### Post by bjweeks on 2006-03-12
[QUOTE=ComplexNumber]isn't that the reason why fluendu paid the licence? in other words, so distros can have mp3 support out of the box. if ubuntu isn't including it by default, its a fault of ubuntu. the situation now on linux is exactly the same as it is on apple and windows. if you can do it on them, you can now do it on linux. end of story.[/QUOTE]

Wrong. If ubuntu ships it they still have to pay the licence fees.

---

### Post by ComplexNumber on 2006-03-12
[quote=bjweeks]Wrong. If ubuntu ships it they still have to pay the licence fees.[/quote] i'm right, you're wrong. read what i've said again.

---

### Post by bjweeks on 2006-03-12
[QUOTE=ComplexNumber]i'm right, you're wrong. read it again.[/QUOTE]

Then what is the point of them chargeing for it if one person pays the licence fees?

I don't think ubuntu will enter any distribution agreement anyways.

---

### Post by bjweeks on 2006-03-12
> Must not be distributed under a licence specific to Ubuntu. The rights attached to the software must not depend on the program's being part of Ubuntu system. So we will not distribute software for which Ubuntu has a "special" exemption or right, and we will not put our own software into Ubuntu and then refuse you the right to pass it on.

ubuntu.com

---

### Post by ComplexNumber on 2006-03-12
[quote=bjweeks]ubuntu.com[/quote] can't see that quote there. can you give me a direct link to where it mentions your quote, please?

---

### Post by bjweeks on 2006-03-12
[QUOTE=ComplexNumber]can't see that quote there. can you give me a direct link to where it says that, please?[/QUOTE]

[http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing)

---

### Post by ComplexNumber on 2006-03-12
that doesn't imply that a licence needs to be paid to use mp3 out of the box. it also doesn't imply any reason why they can't use fluendo's plugin. like i say, its obviously ubuntu's choice that they don't include mp3 out of the box when they have every right to now.
that quote just means that ubuntu shouldn't have anything that is specific to ubuntu...perhaps so that it avoids breaking compatibility with other debian systems.

---

### Post by bjweeks on 2006-03-12
[QUOTE=ComplexNumber]that doesn't imply that a licence needs to be paid to use mp3 out of the box. it also doesn't imply any reason why they can't use fluendo's plugin.[/QUOTE]

They have said won't pay. If they have to enter "distribution agreement" that I can't then they won't

---

### Post by ComplexNumber on 2006-03-12
[quote=bjweeks]They have said won't pay. If they have to enter "distribution agreement" that I can't then they won't[/quote] but there is nothing to pay. the fluendo plugin is under the GPL. its the same as anything else thats included in ubuntu.

---

### Post by bjweeks on 2006-03-12
[QUOTE=ComplexNumber]but there is nothing to pay. the fluendo plugin is under the GPL.[/QUOTE]

and so is mad.

---

### Post by ComplexNumber on 2006-03-12
[quote=bjweeks]and so is mad.[/quote] mad is different and has 'loopholes.


> **License**

  MAD is available under the terms of the [GNU General Public License, Version 2]("http://www.underbit.com/resources/license/gpl/"), for either permanent use or for evaluation prior to obtaining a commercial license. Please note that under the GPL, there is absolutely [no warranty]("http://www.underbit.com/resources/license/gpl/#warranty") of any kind.
  Commercial, non-GPL licensing is also available. Please [contact us]("http://www.underbit.com/contact/") to discuss possible license terms.
 [source]("http://www.underbit.com/products/mad/")




there is no good reason why mp3 can't be included out of the box in ubuntu.

---

### Post by bjweeks on 2006-03-12
[QUOTE=ComplexNumber]mad is different
****


[source]("http://www.underbit.com/products/mad/")





mad needs a commercial licence to be used out of the box. mp3 doesn't now if fluendo's plugin is used.[/QUOTE]

Its still under the gpl.

---

### Post by doclivingston on 2006-03-12
[QUOTE=ComplexNumber]but there is nothing to pay. the fluendo plugin is under the GPL. its the same as anything else thats included in ubuntu.[/QUOTE]

No it isn't.

The source is BSD licenced. However if you compile from source, you are not covered under Fluendo's patent licence.


The binary plugin shipped by Fluendo is under a special licence. You cannot redistribute it to third parties (e.g. shipping Ubuntu to users) without signing something with Fluendo. This restriction conflicts with section 7 of the GPL, which does not let you place limits on redistribution to third parties.

As such you cannot distribute together the combination of the Fluendo plugin binary and a GPL-licenced application that uses it (e.g. Rhythmbox, amaroK-gstreamer). Doing so is a violation of the GPL, and as such you could get sued by copyright holders of said application.


There is no legal problems distributing the plugin, *if you do not distribute GPL'd applications with it*. So it's okay if you download it separately.

---

### Post by doclivingston on 2006-03-12
[http://mail.gnome.org/archives/rhythmbox-devel/2006-January/msg00005.html](http://mail.gnome.org/archives/rhythmbox-devel/2006-January/msg00005.html)

[quote=Christian Schaller (Fluendo guy)]The problem is that this plugin is not GPL compatible as it is using patent rights we don't have the rights to pass on the way the GPL demands.[/quote]

---

### Post by bjweeks on 2006-03-12
[QUOTE=doclivingston][http://mail.gnome.org/archives/rhythmbox-devel/2006-January/msg00005.html](http://mail.gnome.org/archives/rhythmbox-devel/2006-January/msg00005.html)[/QUOTE]

I don't get the point as the pantent holders have said you CAN download a mp3 deocder and use it.

---

### Post by mstlyevil on 2006-03-12
[QUOTE=bjweeks]I don't get the point as the pantent holders have said you CAN download a mp3 deocder and use it.[/QUOTE]

You can, but they still restrict third party distribution by unlicensed vendors.

---

### Post by desperatecoffee on 2006-03-12
Wow. Lots of responses here; thanks everyone.

DocLivingston, your explanations make perfect sense. Bjweeks and ComplexNumber, I have no clue what you're arguing about, but I hope we're all satisfying our urge to argue about something.

Groovy.

---

### Post by Dragonbite on 2006-07-07
There's a business opportunity (not sure how much it'll make though): pay the damn [$0.75 per unit royalty]("http://www.mp3licensing.com/royalty/") and SELL a plug-in or codec or whatever that a user (probably in the US since that's one of the few places it's "illegal") can install to legally play MP3s (like a gstreamer plug-in).

Combined with bandwidth, hosting and development costs it would come out to wha? a couple bucks?!


Canonical can even offer it and charge people a whopping $2 or $3 per unit (make a tiny profit off of it) which could help make it a more desirable alternative for enterprises and OEMs because it would be seen as a "somebody is making sure it is 100% legal AND provides what (if) is needed! One-stop-shopping!"

I know I may be the exception, but I'd prefer to be all-legal AND eat my cake too!

---

### Post by doclivingston on 2006-07-07
> **Dragonbite said:**
> There's a business opportunity (not sure how much it'll make though): pay the damn [$0.75 per unit royalty]("http://www.mp3licensing.com/royalty/") and SELL a plug-in or codec or whatever that a user (probably in the US since that's one of the few places it's "illegal") can install to legally play MP3s (like a gstreamer plug-in).

Fluendo have done this for GStreamer plugins, and you don't even have to pay to use it. You can have a fully patent-licensed MP3 decoder.

Shipping it in a distro has some issues (the licence on it isn't compatable with GPL-licenced stuff, when shipped together), which is why Ubuntu doesn't come with it.

---

### Post by Adamant1988 on 2006-07-07
Although I've long been a supporter of everything 'just working' I think the solution provided for Edgy Eft is one of the better options.

It's illegal to distribute a plugin but it is not illegal to make it available (Like fluendo).  As I've read in the Wiki/Launchpad for edgy "easycodecinstallation" they're planning on making it so that codecs will be made easier to find and install based on your need of them.  
in otherwords you won't get the message about a needed codec until you actually try to play the media type. 

This solution isn't perfect BUT it is a grey area where the ideals of people who will only use foss are supporter (they're not forced to 'help the domination of proprietary formats') and the needs of the average home user (The codecs are made easily available and in the case of fluendo, legal.)

Win-Win.

---

### Post by NoTiG on 2006-07-07
does anyone else think something is seriously wrong here ? the purpose of copy rights is to encourage innovation... but we are using Mp3... which is INFERIOR to ogg... and not to mention that ogg is free. We should be using ogg shouldnt we ? what is wrong with the world

---

### Post by Adamant1988 on 2006-07-07
Ipod doesn't support OGG...that's my reason.

---

### Post by detyabozhye on 2006-09-21
Fluendo distorts sound. =)

---

### Post by FISHERMAN on 2006-09-22
> **Adamant1988 said:**
> Ipod doesn't support OGG...that's my reason.

[RockBox]("http://www.rockbox.org/")

---

