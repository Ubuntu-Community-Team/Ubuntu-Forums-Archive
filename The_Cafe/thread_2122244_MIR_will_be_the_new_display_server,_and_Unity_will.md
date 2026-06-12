---
title: "MIR will be the new display server, and Unity will be ported to Qt"
date: 2013-03-04
forum: The Cafe
---

### Post by ZarathustraDK on 2013-03-04
[http://www.omgubuntu.co.uk/2013/03/canonical-announce-custom-display-server-mir-not-wayland-not-x](http://www.omgubuntu.co.uk/2013/03/canonical-announce-custom-display-server-mir-not-wayland-not-x)
[http://www.omgubuntu.co.uk/2013/03/unity-next-project-announced](http://www.omgubuntu.co.uk/2013/03/unity-next-project-announced)

[IMG]http://cdn.memegenerator.net/instances/250x250/30199807.jpg[/IMG]

---

### Post by GameX2 on 2013-03-04
> **ZarathustraDK said:**
> [http://www.omgubuntu.co.uk/2013/03/canonical-announce-custom-display-server-mir-not-wayland-not-x](http://www.omgubuntu.co.uk/2013/03/canonical-announce-custom-display-server-mir-not-wayland-not-x)
[http://www.omgubuntu.co.uk/2013/03/unity-next-project-announced](http://www.omgubuntu.co.uk/2013/03/unity-next-project-announced)



I saw the second link on FaceBook, thanks to OMG Ubuntu.

"Unity's moving away from Compiz..."
I've read both articles, but I'm not sure to understand.

Does that mean all the kickass Compiz effects (Some cool, others useful) will be gone ?! :O

Thanks for the confirmation.

---

### Post by ZarathustraDK on 2013-03-04
> **GameX2 said:**
> Does that mean all the kickass Compiz effects (Some cool, others useful) will be gone ?! :O

Thanks for the confirmation.

My guess is they'll recreate the effects currently present in a default-install, but stuff like wobbly windows, painting with fire etc. will probably have to wait for someone to have enough spare time.

On the up-side we get flickerless boot-up and salvation from the more buggy side of Compiz (hopefully) + a slew of other stuff. The specification-link in the article already has me convinced that this is a good thing(tm) :)

---

### Post by tartalo on 2013-03-04
Interesting reading:
[https://wiki.ubuntu.com/MirSpec](https://wiki.ubuntu.com/MirSpec)

---

### Post by Dry Lips on 2013-03-04
Hmmm... I wonder what will happen to the development of Wayland now that the biggest Linux distro has ditched it... :-k




> [COLOR=#555555][FONT=Arial]I'm also starting to doubt that [/FONT][/COLOR]**Lubuntu, Kubuntu or Xubuntu will continue to exist after so many changes: rolling release, new display server, focus on Ubuntu Touch, etc. At least, in their current form: based on Ubuntu. Using Debian on the other hand should be a lot easier so maybe they'll switch to it? I guess we should find that out soon, after the Lubuntu, Xubuntu and Kubuntu teams analyze their options.**
[http://www.webupd8.org/2013/03/ubuntu-to-build-its-own-display-server.html](http://www.webupd8.org/2013/03/ubuntu-to-build-its-own-display-server.html)

---

### Post by alphacrucis2 on 2013-03-04
A display server is a pretty massive undertaking. I hope this turns out well.

---

### Post by mJayk on 2013-03-04
I don't fully understand the implications of this tbh.  I feel it could go badly and further distance Ubuntu from other Linux flavors, which again could be good but I can see bad points.

---

### Post by Erik1984 on 2013-03-04
I wonder how this will work out for the Ubuntu derivatives. Will Kubuntu start using Mir + Kwin for example or will they 'simply' keep X and their own compositors?

---

### Post by Dry Lips on 2013-03-04
Ubuntu going down the Apple path?

[https://plus.google.com/107555540696571114069/posts/hzRy1rJaafc](https://plus.google.com/107555540696571114069/posts/hzRy1rJaafc)

---

### Post by ZarathustraDK on 2013-03-04
> **mJayk said:**
> I don't fully understand the implications of this tbh.  I feel it could go badly and further distance Ubuntu from other Linux flavors, which again could be good but I can see bad points.

It's a strange conundrum. On one side there's a lot of people screaming about how Canonical is trying to "take control of Linux" by forcing a new display-server, all the while the same people demand utter subservience to the mighty X.org. On the other side there's Ubuntu trying to drag these people kicking and screaming into an age where the main graphical software component isn't 25 years old.

I'm with Ubuntu on this one. As long as the software stays open source, people shouldn't mind. It's not their money, and it's not their time being spent.

If it had been just another music-player then people would have nodded and went about their business; I'd frankly rather see a new display server IMHO, but when it comes to big components like these then suddenly EVERYBODY is mayor in Sim City and want to decide which basket all the eggs should be put in :-/

---

### Post by ZarathustraDK on 2013-03-04
> **Euroman said:**
> I wonder how this will work out for the Ubuntu derivatives. Will Kubuntu start using Mir + Kwin for example or will they 'simply' keep X and their own compositors?

KDE is Qt-based, so Mir + Kwin makes sense, considering a lot of Qt-compatibility-code must be made for Mir when Unity transfers from GTK to Qt/qml, I venture.

---

### Post by Dry Lips on 2013-03-04
Kristian Høgsberg's (Wayland guy) take on this:[URL="https://plus.google.com/100409717163242445476/posts/jDq6BAgdpkG"]

https://plus.google.com/100409717163242445476/posts/jDq6BAgdpkG[/URL]

---

### Post by JDShu on 2013-03-04
I agree with Kristian Høgsberg. This seems like a spectacularly bad idea and reeks of NIH. If Canonical can pull this off, that would be great - but that's like me saying if I can win an Olympic event, that would be great.

I'm not sure where Canonical's confidence in their ability to solve difficult a engineering problem without domain knowledge (evidently) comes from. To me it sounds a lot like arrogance.

---

### Post by JDShu on 2013-03-04
LOL crash and burn.

[http://en.wikipedia.org/wiki/Deorbit_of_Mir](http://en.wikipedia.org/wiki/Deorbit_of_Mir)

---

### Post by ZarathustraDK on 2013-03-04
Hmmm... a lot of the friction seems to stem from Canonical's unwillingness to develop in the open (as in, everybody gets a say in what goes into the final product).

I don't know. When I read through all those googleplus-posts it seems like there's a schism between the "democratic" slow development of the community that often goes nowhere (gets stranded because nobody makes a call/has the inertia to make a call), and "Dictatorial" fast development Canonical offers by powering money and work-hours into it. Both have its strength and weaknesses. I can understand why Aaron is upset, seeing as he's sitting smack-dab in the middle of it, but I wouldn't equate that with him necessarily being right.

Again I'd say: As long as the code is open and free, I have no qualms with it. If Ubuntu HAS to play a dictator (someone that'll take a bold step with its inertia while the community bickers), then THAT (open source) is what will separate the benevolent king from the fachist madman. Heaven knows, Linus Torvalds are making these kind of far-reaching decisions on a regular basis, he just doesn't catch any flack because every distro is his "servant".

---

### Post by alphacrucis2 on 2013-03-04
> **ZarathustraDK said:**
> Hmmm... a lot of the friction seems to stem from Canonical's unwillingness to develop in the open (as in, everybody gets a say in what goes into the final product).

I don't know. When I read through all those googleplus-posts it seems like there's a schism between the "democratic" slow development of the community that often goes nowhere (gets stranded because nobody makes a call/has the inertia to make a call), and "Dictatorial" fast development Canonical offers by powering money and work-hours into it. Both have its strength and weaknesses. I can understand why Aaron is upset, seeing as he's sitting smack-dab in the middle of it, but I wouldn't equate that with him necessarily being right.

Again I'd say: As long as the code is open and free, I have no qualms with it. If Ubuntu HAS to play a dictator (someone that'll take a bold step with its inertia while the community bickers), then THAT (open source) is what will separate the benevolent king from the fachist madman. Heaven knows, Linus Torvalds are making these kind of far-reaching decisions on a regular basis, he just doesn't catch any flack because every distro is his "servant".


There's been nothing to stop Canonical engaging with the Wayland devs to influence the development and even make significant contributions but it appears they just decided to go their own way. Likely this decision was made quite a long time ago and we are just learning about it now.

---

### Post by 3rdalbum on 2013-03-04
Wayland has been five years in development and you still can't run a desktop on it. It seems that the best you can do is run individual applications inside Weston, inside Virtualbox. Five years of development!

I don't think Canonical can afford to wait maybe another five years for Wayland to really be ready. If they can get Mir to run Unity, Qt5 and GTK 3 within the next 12 months they can get the benefits soon, and leapfrog Wayland.

Remember USB support on Linux. Two years into it, the team still had no usable code. Linus basically chucked it all out, started over, and wrote the USB stack in a couple of weeks. And it still works well. Sometimes, it just works better to get software usable quickly, and then add features to it later.

---

### Post by BigCityCat on 2013-03-04
My take is the community doesn't like it or it doesn't turn out how you like then use something else. Develop something else and make it better. I take a wait and see approach. I also have no problem with profits. People aren't entitled to a free product. I know a lot of people have contributed a lot and Ubuntu benefits from this. I guess people could question Ubuntu's contribution but marketing isn't cheap either. I had no idea what Linux was 5 years ago, then I heard about Ubuntu. Why because Ubuntu is marketing itself, and it's gonna take money to push it the next level. The community can not develop everything that makes Linux great quickly enough to be relevant. I know a lot of people would rather live in obscurity though. I'm interested to see where it goes. I hope it succeeds. I hope they stay true to the GPL and if they don't then we will move on and develop something else.

---

### Post by glln0v on 2013-03-04
I like that Canonical is talking about security/privacy as a reason for creating MIR. X has major security issues.

Based on Canonical's wiki, this sounds like an awesome plan. I just hope they can pull it off.

---

### Post by buzzingrobot on 2013-03-04
Canonical will take a lot of flack from parts of the development community for going its own way here, rather than simply patching X and/or Wayland.  

As a user, though, I'm happy to see someone in open source try something new for a change, rather that stick with the conservative gradualism that we typically see. 

I suspect Canonical has seen that relying on the  efforts of others in the community who function independently of Canonical means it loses some degree of control of its products. This is the trade off that comes with cooperation and leveraging code in open source:  You're often dependent on the code produced by people you can't control. 

You can go it alone and still remain in harmony with open source tenets.  But, you're likely to offend folks who find the communal aspect of open source at least as important as the code.

---

### Post by jejones3141 on 2013-03-05
Looks like NIH to me. People involved with Wayland have said that Canonical's claimed reasons for not using Wayland are bogus (see [https://plus.google.com/100409717163242445476/posts/jDq6BAgdpkG]("https://plus.google.com/100409717163242445476/posts/jDq6BAgdpkG") and [http://www.phoronix.com/scan.php?page=news_item&px=MTMxNzY]("http://www.phoronix.com/scan.php?page=news_item&px=MTMxNzY")). If Canonical thinks Wayland isn't progressing quickly enough, they could consider helping. Perhaps that would be in the spirit of ubuntu.

---

### Post by 3rdalbum on 2013-03-05
> **jejones3141 said:**
> If Canonical thinks Wayland isn't progressing quickly enough, they could consider helping. Perhaps that would be in the spirit of ubuntu.

Please. With Canonical's help it will still take another five years, AND Canonicals engineers will be wasting their time trying to push through changes that the rest of the project will deny because they are suspicious of Ubuntu.

Like Gnome.

---

### Post by prodigy_ on 2013-03-05
Qt? Ugh. I thought Unity couldn't get any worse than it already was. I stand corrected.

---

### Post by ZarathustraDK on 2013-03-05
> **3rdalbum said:**
> Please. With Canonical's help it will still take another five years, AND Canonicals engineers will be wasting their time trying to push through changes that the rest of the project will deny because they are suspicious of Ubuntu.

Like Gnome.

Exactly, a lot of the criticism feels like sour berries over Wayland getting snubbed in favor of Mir. Even if Ubuntu went with Wayland, it's still a new display server and fragmentation would occur. X.org will continue to exist because it's useful in certain environments, but Mir and Wayland will duke it out, winner taking all, status quo restored now with a better display server.

---

### Post by buzzingrobot on 2013-03-05
> **jejones3141 said:**
> Looks like NIH to me. People involved with Wayland have said that Canonical's claimed reasons for not using Wayland are bogus (see [https://plus.google.com/100409717163242445476/posts/jDq6BAgdpkG](https://plus.google.com/100409717163242445476/posts/jDq6BAgdpkG) and [http://www.phoronix.com/scan.php?page=news_item&px=MTMxNzY](http://www.phoronix.com/scan.php?page=news_item&px=MTMxNzY)). If Canonical thinks Wayland isn't progressing quickly enough, they could consider helping. Perhaps that would be in the spirit of ubuntu.

Wayland devs can't be considered unbiased observers.  They have their own agenda.

What Canonical has done here is directly analogous to, say, a bicycle manufacturer deciding to make its own pedals because the people it was depending on to supply pedals were taking too long to turn out a new kind of pedal that, even when delivered, wouldn't do the job.

That's a bit labored, but the point is that deciding you don't want to depend on a "community" of independent third parties to deliver a core component of your product is a rational business decision.

---

### Post by Dry Lips on 2013-03-05
> [COLOR=#000000][FONT=verdana]For those wondering, the C++ code-base that makes up Mir does require Canonical's CLA (Contributor License Agreement)[/FONT][/COLOR]
Source: [http://www.phoronix.com/scan.php?page=news_item&px=MTMxNzY](http://www.phoronix.com/scan.php?page=news_item&px=MTMxNzY)

I'm not too much into this whole licensing bit, but what kind of consequences does it have that MIR is licensed under Canonical's own license, and not a normal GNU license?

---

### Post by addegsson on 2013-03-05
> **prodigy_ said:**
> Qt? Ugh. I thought Unity couldn't get any worse than it already was. I stand corrected.

Qt is superior to GTK.

---

### Post by ZarathustraDK on 2013-03-05
> **Dry Lips said:**
> Source: [http://www.phoronix.com/scan.php?page=news_item&px=MTMxNzY](http://www.phoronix.com/scan.php?page=news_item&px=MTMxNzY)

I'm not too much into this whole licensing bit, but what kind of consequences does it have that MIR is licensed under Canonical's own license, and not a normal GNU license?

[http://www.canonical.com/contributors](http://www.canonical.com/contributors)

> With the contributor agreement chosen by Canonical, the Harmony CLA, the contributor gives Canonical a licence to use their contributions. The contributor continues to own the copyright in the contribution, with full rights to re-use, re-distribute, and continue modifying the contributed code, allowing them to also share that contribution with other projects.

Mir is, according to the launchpad entry, licensed under "GNU GPL v3, GNU LGPL v3, MIT / X / Expat Licence, Other/Open Source (Boost Software License - Version 1.0)". The Contributor License Agreement, I suspect, is simply hammering out that contributors own their own code (which will probably be required to abide by the mentioned licenses), but Canonical has final say in the project known as Mir. I don't see forking the project is disallowed anywhere yet.

---

### Post by grahammechanical on 2013-03-05
> **Dry Lips said:**
> Source: [http://www.phoronix.com/scan.php?page=news_item&px=MTMxNzY](http://www.phoronix.com/scan.php?page=news_item&px=MTMxNzY)

I'm not too much into this whole licensing bit, but what kind of consequences does it have that MIR is licensed under Canonical's own license, and not a normal GNU license?

That agreement is an agreement between someone who contributes code to a Ubuntu code project. It sets up a legal agreement between the programmer and Canonical so that the contributor does not have his code stolen. Please read about it. [http://www.canonical.com/contributors](http://www.canonical.com/contributors) Note this:

> [SIZE=2][COLOR=#333333][FONT=Ubuntu Beta]This agreement establishes a relationship between us and the contributor, gives details on what it means when the contributor grants permission for their work to be included in a project, and enables us to be better stewards of these projects.[/FONT][/COLOR][/SIZE]

> [COLOR=#333333][FONT=Ubuntu Beta]The contributor continues to own the copyright in the contribution, with full rights to re-use, re-distribute, and continue modifying the contributed code, allowing them to also share that contribution with other projects.[/FONT][/COLOR]

Canonical is not creating its own form of Free Software License. Nor is it forcing any programmer to relinquish ownership of their code. This contibutor agreement is based upon this: [http://www.harmonyagreements.org/docs/ha-cla-i.html](http://www.harmonyagreements.org/docs/ha-cla-i.html)  and [http://en.wikipedia.org/wiki/Contributor_License_Agreement](http://en.wikipedia.org/wiki/Contributor_License_Agreement)

Information please. Not dis-information.

---

### Post by prodigy_ on 2013-03-05
> **Dry Lips said:**
> Source: [http://www.phoronix.com/scan.php?page=news_item&px=MTMxNzY](http://www.phoronix.com/scan.php?page=news_item&px=MTMxNzY)

I'm not too much into this whole licensing bit, but what kind of consequences does it have that MIR is licensed under Canonical's own license, and not a normal GNU license?
Coupled with migration to Qt? Expect closed source proprietary "extensions" down the road.

---

### Post by castrojo on 2013-03-05
> **prodigy_ said:**
> Coupled with migration to Qt? Expect closed source proprietary "extensions" down the road.

Link?

---

### Post by prodigy_ on 2013-03-05
> **castrojo said:**
> Link?
\\gut-feeling\based-on\previous-experience

---

### Post by glln0v on 2013-03-05
This whole thing strikes me as a repeat of Unity-shell vs Gnome3-shell. After trying both out, I'm grateful that Canonical pushed ahead on Unity.

The thing I don't understand is how Kristian Høgsberg is saying that all the technical reasons for switching to MIR don't exist. The links I've read make it sound like he's saying you can already do everything Canonical is planning to do with MIR using Wayland. If true, this is wierd that Canonical is saying otherwise. I read previously that Canonical wasn't going to use GRUB2 because of some Secure-Boot legal concerns. Yet they came to this decision without even talking to FSF. This is bizarre. Is Canonical mistaken about Wayland capabilities? Have they talked to Wayland developers about their concerns? 

I'm just a non-technical outsider looking in, reading the blogs and such. This is the picture and questions I'm left with.

I hope Canonical can pull off the Unity vision/convergeance. Other than some serious privacy concerns with the DASH sending my personal information elsewhere, I really like the Unity environment. My hope is that they make privacy/security a top-focus from here on out so users get the benefit on all form factors (Desktop, Phone, Tablet, TV).

---

### Post by mr john on 2013-03-05
> "we cannot control that other project so we create our own"



Our distro, our choice. Well, really Marks choice, as Ubuntu isn't a democracy.

---

### Post by ZarathustraDK on 2013-03-05
Quoted from the Mir-spec page:

> Why Not Wayland / Weston?

An obvious clarification first: Wayland is a protocol definition that defines how a client application should talk to a compositor component. It touches areas like surface creation/destruction, graphics buffer allocation/management, input event handling and a rough prototype for the integration of shell components. However, our evaluation of the protocol definition revealed that the Wayland protocol does not meet our requirements. First, we are aiming for a more extensible input event handling that takes future developments like 3D input devices (e.g. Leap Motion) into account. Please note though that Wayland's input event handling does not suffer from the security issues introduced by X's input event handling semantics (thanks to Daniel Stone and Kristian Høgsberg for pointing this out). With respect to mobile use-cases, we think that the handling of input methods should be reflected in the display server protocol, too. As another example, we consider the shell integration parts of the protocol as privileged and we'd rather avoid having any sort of shell behavior defined in the client facing protocol.

However, we still think that Wayland's attempt at standardizing the communication between clients and the display server component is very sensible and useful, but due to our different requirements we decided to go for the following architecture w.r.t. to protocol-integration:

A protocol-agnostic inner core that is extremely well-defined, well-tested and portable.
An outer-shell together with a frontend-firewall that allow us to port our display server to arbitrary graphics stacks and bind it to multiple protocols.
In summary, we have not chosen Wayland/Weston as our basis for delivering a next-generation user experience as it does not fulfill our requirements completely. More to this, with our protocol- and platform-agnostic approach, we can make sure that we reach our goal of a consistent and beautiful user experience across platforms and device form factors. However, Wayland support could be added either by providing a Wayland-specific frontend implementation for our display server or by providing a client-side implementation of libwayland that ultimately talks to Mir.

As I understand it, there are some basic, structural differences with regards to Wayland from Canonicals POV (read: what they're intending to use it for, not that the project itself is completely bunk).

---

### Post by ZarathustraDK on 2013-03-05
...aaaaaaand here's the first prototype in action with working desktop, on a tablet: [http://www.omgubuntu.co.uk/2013/03/ubuntus-new-display-server-mir-gets-demoed-video](http://www.omgubuntu.co.uk/2013/03/ubuntus-new-display-server-mir-gets-demoed-video)

I could get used to this steady stream of rabbits getting pulled out of the hat :)

---

### Post by CarpKing on 2013-03-05
If Wayland wasn't quite capable of what they wanted to do, they should have contributed until it was.  If their ideas got rejected, then maybe they would be justified in going their own way.  Instead they just made their own thing without telling anyone their issues beforehand.  This whole thing wreaks of NIH syndrome. First the DE (also various smaller pieces I guess), now the display server.  I suppose the next step is writing their own kernel.  

Distro-hoppers, how is Debian looking these days?

---

### Post by mamamia88 on 2013-03-05
> **CarpKing said:**
> If Wayland wasn't quite capable of what they wanted to do, they should have contributed until it was.  If their ideas got rejected, then maybe they would be justified in going their own way.  Instead they just made their own thing without telling anyone their issues beforehand.  This whole thing wreaks of NIH syndrome. First the DE (also various smaller pieces I guess), now the display server.  I suppose the next step is writing their own kernel.  

Distro-hoppers, how is Debian looking these days?

Exactly they would have probably got there quicker by cooperating with others and donating time and money to bring it up to snuff rather than starting from ground zero. That being said they can do what they want and I look forward to testing it out.

---

### Post by Dry Lips on 2013-03-05
What do you think about these articles:
[URL="http://www.phoronix.com/scan.php?page=news_item&px=MTMxNzc"]

http://www.phoronix.com/scan.php?page=news_item&px=MTMxNzc[/URL]

and

[http://www.phoronix.com/scan.php?page=news_item&px=MTMxODA](http://www.phoronix.com/scan.php?page=news_item&px=MTMxODA)

---

### Post by iamkuriouspurpleoranj on 2013-03-05
Debian 7 will go stable any time in the next 6 months. People say it's imminent but in fact the Debian project is currently having difficulty squashing bugs. Really, if anyone here is able to help out, they need you over at Debian.

---

### Post by prodigy_ on 2013-03-05
> **CarpKing said:**
> Distro-hoppers, how is Debian looking these days?
Debian's fine.

---

### Post by MadmanRB on 2013-03-05
For me the move to QT is a good thing, I mean QT is no longer fully closed source and is freely used in KDE/ Razor QT
Plus QT apps in general are way better then GTK ones.

---

### Post by lykwydchykyn on 2013-03-05
Developing a display server is one thing.  Getting 20+ years of applications to suddenly be compatible with it is what takes time.

---

### Post by ZarathustraDK on 2013-03-05
Somewhat related question here: If Unity transfers to Qt/qml will Ubuntu then see a default software shift as well, I'm thinking Rhythmbox --> Amarok?

---

### Post by MadmanRB on 2013-03-05
> **lykwydchykyn said:**
> Developing a display server is one thing.  Getting 20+ years of applications to suddenly be compatible with it is what takes time.
I think this is the main reason for this move, after all QT is a long established toolkit and its incredibly flexible (thus why Nokia took interest in it, in hopes of using it for mobile technology)
So why use a untried untested thing like wayland?

> **ZarathustraDK said:**
> Somewhat related question here: If Unity transfers to Qt/qml will Ubuntu then see a default software shift as well, I'm thinking Rhythmbox --> Amarok?
I hope so as that may lead to dolphin being default in Ubuntu, a file manager eleventy billion times better then nutalus.

---

### Post by capink on 2013-03-05
> **lykwydchykyn said:**
> Developing a display server is one thing.  Getting 20+ years of applications to suddenly be compatible with it is what takes time.


Most applications have nothing to do with X. They are dependant on the toolkit (Qt & Gtk). Once you port the toolkits to Mir, almost all the applications will automatically be compatible. The few applications that use X directly, will be supported by launching rootless X session.

---

### Post by Roasted on 2013-03-05
> **addegsson said:**
> Qt is superior to GTK.

I've heard this said before. I've also heard the argument go the other direction as well with people voting on GTK being superior. While I am admittedly not a developer by any means, I do have to question what it is exactly that makes Qt superior to GTK. I'm pretty agnostic when it comes to desktop environments, and I've tested out Gnome Shell 3.6, the latest Unity, and KDE 4.10 pretty extensively for a few weeks each. Judging entirely on the outside and overall workings of the environments and software, there is absolutely no contest that Gnome Shell feels the easiest to use out of the gate, much more polished, and rather configurable given the array of available extensions as opposed to KDE and Unity. Not to say something like KDE isn't configurable, it's easily the most configurable hands down, but there's just so much stuff *everywhere* that I feel like it needs to be toned down a bit. I also wasn't impressed with the continual plasma crash every time I shut down the computer... But perhaps that's another story. 

My findings may be entirely preferential and apply only to me and nobody else, but I do have to honestly question from an unbiased standpoint how something supposedly "inferior" can still look and feel superior in every way. Sure you can polish a dog turd and you still have a dog turd in the end, but I can say even as a KDE lover that I've certainly had less issues in GTK land than any Qt oriented land I've spent time in. My 2c.

---

### Post by prodigy_ on 2013-03-05
> **Roasted said:**
> I also wasn't impressed with the continual plasma crash every time I shut down the computer...
Plasma is supposed to crash, bro. KDE fans like it this way. ;)

---

### Post by Dry Lips on 2013-03-05
**Canonical's Mir Project Retracts Wayland Criticism**
[http://www.phoronix.com/scan.php?page=news_item&px=MTMxODY](http://www.phoronix.com/scan.php?page=news_item&px=MTMxODY)

---

### Post by fontis on 2013-03-05
IMO?
About effin time. Regardless of what happens, this undertaking is huge and I have great hopes for it. If any one has ever had any incentive for getting the ball rolling, and the means to do so, is Canonical and Ubuntu. 

Hopefully, this will mean that Unity can actually turn into a really fast and fluid experience instead of suffering the limitations in which it's stuck with now.
For all purposes, X is all good and wonderful, but something better is needed for the future.

---

### Post by tartalo on 2013-03-05
> **ZarathustraDK said:**
> Somewhat related question here: If Unity transfers to Qt/qml will Ubuntu then see a default software shift as well, I'm thinking Rhythmbox --> Amarok?
Since QT will be supported earlier and probably better, I'd expect that. 
It makes sense, KDE is ahead in mobile support (Plasma Active), by the time Mir hits Ubuntu many KDE/QT apps will be well tested in touch interfaces.
EDIT: Oh! And don't forget all the QT apps in Meego, Mer and related projects.

---

### Post by MadmanRB on 2013-03-05
> **prodigy_ said:**
> Plasma is supposed to crash, bro. KDE fans like it this way. ;)

Plasma has stabilized greatly over tyhge last few years.
Plasma crashing has nothing to do with QT, its more of a flaw with the compsitor.
Razor-QT doesnt use plasma and does seem far more stable because of it.
But Plasma is really starting to shine.

---

### Post by georgelappies on 2013-03-05
> **addegsson said:**
> Qt is superior to GTK.

+1 in every single way.

---

### Post by georgelappies on 2013-03-05
> **ZarathustraDK said:**
> Somewhat related question here: If Unity transfers to Qt/qml will Ubuntu then see a default software shift as well, I'm thinking Rhythmbox --> Amarok?

A Rhythmbox --> Clementine move might be better ;)

---

### Post by evilsoup on 2013-03-05
So... Unity is moving away from Canonical's crazy internally-developed compositor (Compiz_*_) to Qt, which is more mature, more stable, and has a wider developer-base than Canonical hires... and at the same time, they're ignoring Wayland/Weston and going with their own in-house solution for the compositor?

So in two LTSs time, are we going to see Canonical give up on this folly and switch to Wayland, just like they've given up on Compiz now?

If they were forking the code, I would understand that - since pushing out a working product quickly is important to them. But starting an in-house project from scratch is crazy; they're missing out on the main advantage of open-source. Definitely just NIH.


_*_: I know that Compiz wasn't originally a Ubuntu project, but they *did* hire in the main dev rather than just using Mutter or whatever

---

### Post by ZarathustraDK on 2013-03-05
> **Dry Lips said:**
> **Canonical's Mir Project Retracts Wayland Criticism**
[http://www.phoronix.com/scan.php?page=news_item&px=MTMxODY](http://www.phoronix.com/scan.php?page=news_item&px=MTMxODY)

Not to pick a side here, but that article is fair and balanced in the Fox News sense of the line.

Multiple quotes/statements from the Mir-detractors vs. speculation based on a (warranted) edit of a wiki.

We need to hear the Canonical side to this story, not these prescient assumptions about how Canonical is in your base killing your doodz.

---

### Post by lykwydchykyn on 2013-03-05
> **MadmanRB said:**
> I think this is the main reason for this move, after all QT is a long established toolkit and its incredibly flexible (thus why Nokia took interest in it, in hopes of using it for mobile technology)
So why use a untried untested thing like wayland?

How is Mir any more tried or tested than wayland??

> **capink said:**
> Most applications have nothing to do with X. They are dependant on the toolkit (Qt & Gtk). Once you port the toolkits to Mir, almost all the applications will automatically be compatible. The few applications that use X directly, will be supported by launching rootless X session.

How is this situation different from wayland?

> **Roasted said:**
> While I am admittedly not a developer by any means, I do have to question what it is exactly that makes Qt superior to GTK. I'm pretty agnostic when it comes to desktop environments, and I've tested out Gnome Shell 3.6, the latest Unity, and KDE 4.10 pretty extensively for a few weeks each. Judging entirely on the outside and overall workings of the environments and software, there is absolutely no contest that Gnome Shell feels the easiest to use out of the gate, much more polished, and rather configurable given the array of available extensions as opposed to KDE and Unity. 

If you're judging QT vs GTK on the basis of KDE vs GNOME, you really aren't talking from an informed standpoint.  The KDE project has a vision for a desktop that's different from the GNOME team, and people are bound to like one or the other.  Toolkit has nothing to do with it.  There is nothing inherent in QT that forces you to create a desktop environment like KDE (case in point, razor-qt), just like there is nothing inherent in GTK that forces you to make a desktop like GNOME (case in point, LXDE, XFCE, others...).

If you want a developer's perspective, GTK is just a graphics toolkit.  QT is a multi-faceted development library that covers graphics, sound, networking, database access, and tons of other stuff.  It abstracts just about anything you'd want to do when writing software, so that you can compile your code for multiple platforms without rewriting.  It's well-designed and awesome.  

That doesn't mean GTK is bad, but it's just a different animal with different intentions.  

And for goodness sake, people; QT has been available under a GPL license since before Ubuntu existed.  Let's get over the licensing FUD please.

---

### Post by llanitedave on 2013-03-05
> **lykwydchykyn said:**
> 
If you want a developer's perspective, GTK is just a graphics toolkit.  QT is a multi-faceted development library that covers graphics, sound, networking, database access, and tons of other stuff.  It abstracts just about anything you'd want to do when writing software, so that you can compile your code for multiple platforms without rewriting.  It's well-designed and awesome.  

That doesn't mean GTK is bad, but it's just a different animal with different intentions.  

And for goodness sake, people; QT has been available under a GPL license since before Ubuntu existed.  Let's get over the licensing FUD please.

I was waiting for someone to say this.  There's nothing wrong with GTK, but QT is simply at another level.

And it's both amusing and tiresome to read all the grouches pontificating about what Canonical *should* be doing, as if each and every one of them has some special sacred insight.

---

### Post by Roasted on 2013-03-05
> **lykwydchykyn said:**
> If you're judging QT vs GTK on the basis of KDE vs GNOME, you really aren't talking from an informed standpoint.  The KDE project has a vision for a desktop that's different from the GNOME team, and people are bound to like one or the other.  Toolkit has nothing to do with it.  There is nothing inherent in QT that forces you to create a desktop environment like KDE (case in point, razor-qt), just like there is nothing inherent in GTK that forces you to make a desktop like GNOME (case in point, LXDE, XFCE, others...).

If you want a developer's perspective, GTK is just a graphics toolkit.  QT is a multi-faceted development library that covers graphics, sound, networking, database access, and tons of other stuff.  It abstracts just about anything you'd want to do when writing software, so that you can compile your code for multiple platforms without rewriting.  It's well-designed and awesome.  

That doesn't mean GTK is bad, but it's just a different animal with different intentions.  


I'll be the first to admit that I am indeed looking at it from the standpoint of KDE vs Gnome, and I acknowledge that it may not be entirely accurate to do that. As somebody who's not a developer that's all I can base my opinion on. Bottom line is, I'm an end user, so I want things to work smoothly and quickly without fuss. As a result I begin to wonder why the QT vs GTK argument is even relevant if the end goal is where the real golden ticket is, since that's what (in my opinion) really counts. That being said, I'm sure there are some merits to be had on the developer/maintainer level with working on either side of the court. But as an end user, I can tell you I've never had a "GTK" crash of any sort.

---

### Post by lykwydchykyn on 2013-03-05
> **Roasted said:**
>  But as an end user, I can tell you I've never had a "GTK" crash of any sort.

You've never had any piece of software that uses GTK crash on you?

---

### Post by Roasted on 2013-03-05
> **lykwydchykyn said:**
> You've never had any piece of software that uses GTK crash on you?

At least, I can't recall a time where I had that happen. On the flip side I was having plasma crashes each time the system should be shut off or rebooted. That may have been due to a specific problematic widget, though.

EDIT - For what it's worth, it was an additional clock widget it seems. I nuked it and have logged out and restarted a number of times now without a single plasma crash. Hmm... Now for a fun project - making KDE resemble Gnome Shell.

---

### Post by ssam on 2013-03-06
> **3rdalbum said:**
> Wayland has been five years in development and you still can't run a desktop on it. It seems that the best you can do is run individual applications inside Weston, inside Virtualbox. Five years of development!

I don't think Canonical can afford to wait maybe another five years for Wayland to really be ready. If they can get Mir to run Unity, Qt5 and GTK 3 within the next 12 months they can get the benefits soon, and leapfrog Wayland.


Writing a display server is a big task. A large team taking 5 years is not unreasonable. It would be very impressive if Canonical can get anything working in 1 year.

Their aims are very close to those of Wayland/western. Judging from the IRC log ( [http://pastebin.com/KjRm3be1](http://pastebin.com/KjRm3be1) ) the technical reasons for MIR are small (server-side buffers). The initially stated reasons about input were wrong, so it looks like the MIR developers have not looked in detail at how wayland works. So it seems that the reasons for MIR are mostly political/business.

---

### Post by Paqman on 2013-03-06
> **ssam said:**
> Writing a display server is a big task. A large team taking 5 years is not unreasonable. It would be very impressive if Canonical can get anything working in 1 year.


Since they've already got working prototypes it seems they've been working on it for some time.

---

### Post by buzzingrobot on 2013-03-06
> **ssam said:**
> ... it seems that the reasons for MIR are mostly political/business.

Dunno about the politics, but if I was running a business and wanted a display server I could use on every platform my products targeted, I'd rather develop it in-house than depend on the (be held hostage to?) different interests of developers who I can't control, i.e., Wayland.

---

### Post by ZarathustraDK on 2013-03-06
> **buzzingrobot said:**
> Dunno about the politics, but if I was running a business and wanted a display server I could use on every platform my products targeted, I'd rather develop it in-house than depend on the (be held hostage to?) different interests of developers who I can't control, i.e., Wayland.

Mhm, and partners like AMD and Nvidia would probably be reluctant to support your project if you don't have full control to make choices about the aspect that's supposed to be the reason for your partnership in the first place.

---

### Post by lykwydchykyn on 2013-03-06
> **buzzingrobot said:**
> Dunno about the politics, but if I was running a business and wanted a display server I could use on every platform my products targeted, I'd rather develop it in-house than depend on the (be held hostage to?) different interests of developers who I can't control, i.e., Wayland.

If you're a Linux distro, 9/10 of your product (at least) is developed by third-party projects you can't control.  They can do what they want for all I care, but it's a little sad when a major distro can't work with upstream; it's more sad that they have to spread FUD about other projects to justify it.  

Where does this end?

---

### Post by ssam on 2013-03-06
> **Paqman said:**
> Since they've already got working prototypes it seems they've been working on it for some time.
youtube has plenty of demos of wayland (my favourite [https://www.youtube.com/watch?v=_FjuPn7MXMs](https://www.youtube.com/watch?v=_FjuPn7MXMs) )

its a big step from showing a demo, to having something supports all the features a display server needs. copy+paste, input hotplugging, output hotplugging, colour correction, drag and drop, video acceleration, network/remote etc. and to give it the testing required to find the bugs. even with a team of wizards this sounds like several years of work, solving a lot of the same issues that the wayland devs have already solved.

> **buzzingrobot said:**
> Dunno about the politics, but if I was running a business and wanted a display server I could use on every platform my products targeted, I'd rather develop it in-house than depend on the (be held hostage to?) different interests of developers who I can't control, i.e., Wayland.

i can't image how or why the wayland devs would stop canonical porting wayland to a new platform. wayland (like X) is under a MIT licence so canonical could do in an in-house secret port, and never release the source if thats what they wanted. if they are paranoid that someone else will steal their hard work, make a phone/tablet and compete with them for market, then i am not sure opensource software is the right thing for them.

---

### Post by buzzingrobot on 2013-03-06
> **lykwydchykyn said:**
> If you're a Linux distro, 9/10 of your product (at least) is developed by third-party projects you can't control.  They can do what they want for all I care, but it's a little sad when a major distro can't work with upstream; it's more sad that they have to spread FUD about other projects to justify it.  

Where does this end?

Well, Canonical is considerably more than a Linux distribution. 

There's always been a tension between the commercial vendors and their dependence on independent developers who, at best, have only overlapping interests. At worst, they can walk away from something the vendors rely on.  

Canonical tries to make money selling services and support, like Red Hat and Suse.  Unlike them, however, it also wants to be a player in consumer devices. That desire will, inevitably, drive them into needing more control over the development of the software used in those devices. The only way to ensure that is to develop in house.

The ultimate tension might come if Canonical develops software that gives them an obvious commercial advantage in one part of the consumer device market.  But, because it would be released as open source, their competitors could quickly use it to negate that competitive edge.

---

### Post by Dry Lips on 2013-03-06
> **Paqman said:**
> Since they've already got working prototypes it seems they've been working on it for some time.

*[COLOR=#000000][FONT=verdana]"A video by one of the Mir developers shows Unity running on Mir. But it's running Unity through an X Server via the "XMir" project. [...]  [/FONT][/COLOR][COLOR=#000000][FONT=verdana]XMir is to Mir as XWayland [/FONT][/COLOR][COLOR=#000000][FONT=verdana]is to Wayland. [...] [/FONT][/COLOR]*[COLOR=#000000][FONT=verdana]*XMir is basically an in-session root-less X Server running atop Mir. This is how legacy X11 applications will continue to be supported by Mir and is the same approach that Wayland developers did for running X applications on their display server."*

Source: [/FONT][/COLOR][http://www.phoronix.com/scan.php?page=news_item&px=MTMxODQ](http://www.phoronix.com/scan.php?page=news_item&px=MTMxODQ)


I'm no expert on the issue, and this is probably not the best way to phrase it, but perhaps you could say that what they really are demonstrating is an X emulator? In that case they are far from having a "working prototype".

---

### Post by VeeDubb on 2013-03-06
> **Dry Lips said:**
> Hmmm... I wonder what will happen to the development of Wayland now that the biggest Linux distro has ditched it... :-k

I would say there's really only two reasonably likely outcomes.

a. Wayland falls by the wayside.

b. Ubuntu fails.


Every significant desktop linux distro out there runs X.  

Having different distros running different display servers would cripple the entire linux community.

It appears that most of the major distros have recognized that X needs to be replaced, and up until now, Wayland seemed to be the new direction.  

By abandoning Wayland in favor of MIR, Ubuntu is putting all their eggs in one basket and hoping that it will be so awesome that every major distro follows them or gives up and dies.  If that happens, then great.  More people running one distro means better support, a more active community, and most importantly it means that software developers will focus more on Ubuntu.  It's a giant bag of win.  The problem is that if everybody else moves forward with Wayland, Ubuntu will be the odd-man out.  Commercially produced software will be non-existent, and the community will suffer, wither and die.

Effectively, canonical is playing chicken with the rest of the linux world.

---

### Post by Roasted on 2013-03-06
> **VeeDubb said:**
> I would say there's really only two reasonably likely outcomes.

a. Wayland falls by the wayside.

b. Ubuntu fails.


Every significant desktop linux distro out there runs X.  

Having different distros running different display servers would cripple the entire linux community.

It appears that most of the major distros have recognized that X needs to be replaced, and up until now, Wayland seemed to be the new direction.  

By abandoning Wayland in favor of MIR, Ubuntu is putting all their eggs in one basket and hoping that it will be so awesome that every major distro follows them or gives up and dies.  If that happens, then great.  More people running one distro means better support, a more active community, and most importantly it means that software developers will focus more on Ubuntu.  It's a giant bag of win.  The problem is that if everybody else moves forward with Wayland, Ubuntu will be the odd-man out.  Commercially produced software will be non-existent, and the community will suffer, wither and die.

Effectively, canonical is playing chicken with the rest of the linux world.

I think it's a little thick to consider that Ubuntu (or the Linux community) could die. Worst case scenario is I see both Wayland and Mir co-existing just fine, however which one will be commercially supported is another story.

Does anybody have any sort of idea what Mir would be licensed with? (likely a silly question due to the young announcement). Reason I ask is some people are like no big deal it'll be open source etc. What concerns me is to what kind of open source license it'll be. Didn't Canonical license Unity in a way that would force developers to contribute upstream to Canonical only or something? I thought I remember reading that the Unity license was open source with a twist. I wonder if Mir will be the same way.

I can't help but to continuously look at Red Hat during all of this. Not to point any fingers, but don't the majority of Gnome developers work for Red Hat/Fedora to begin with? One could argue that this sort of in-house catering is already done elsewhere. I suppose a display manager could be a different beast, but a desktop environment is far from minor.

---

### Post by VeeDubb on 2013-03-06
> **Roasted said:**
> I think it's a little thick to consider that Ubuntu (or the Linux community) could die. Worst case scenario is I see both Wayland and Mir co-existing just fine, however which one will be commercially supported is another story.

I never intended to suggest that the linux community as a whole would die.  I was referring specifically to the Ubuntu community.  That said, many distros have died out over the years, and many others have faded from the limelight to obscurity.  There's nothing thick about looking at historical precedent and drawing reasonable conclusions based on established patterns.

I can't even begin to count the number of times that I've helped or been helped by someone running a different flavor of linux.  If we ever reach a point where Ubuntu is running MIR and everybody else is on Wayland, that comes to a screeching halt.  We become an isolated community.  

Further, while I don't believe it would kill the linux community, I do believe that a world with "Wayland and Mir coexisting just fine" would set back the commercial availability of software by years.  One of the biggest complaints of commercial developers has been how deeply fractured the linux world is.  This can make it difficult create an application that works without any headaches across multiple distros.  That's gotten MUCH better over the last few years, but developers hesitant to port their work to an already small community (by comparison) are going to be even more hesitant when they have to either do it twice or choose which of two even smaller communities to support.  Those that do continue to develop commercial software will either pick whichever is more prevalent (not Mir) or they'll continue to write software for X, which will be sub-par in XMir or XWayland.

Granted, Mir could take the linux world by storm and crush Wayland.  I'd be fine with that.  But if it doesn't, I just don't see this ending well for Canonical.

---

### Post by Dry Lips on 2013-03-06
> **Roasted said:**
> 
Does anybody have any sort of idea what Mir would be licensed with? 

[http://ubuntuforums.org/showthread.php?t=2122244&page=3&p=12542431#post12542431](http://ubuntuforums.org/showthread.php?t=2122244&page=3&p=12542431#post12542431)

---

### Post by Cheesemill on 2013-03-06
> **VeeDubb said:**
> Further, while I don't believe it would kill the linux community, I do believe that a world with "Wayland and Mir coexisting just fine" would set back the commercial availability of software by years.  One of the biggest complaints of commercial developers has been how deeply fractured the linux world is.  This can make it difficult create an application that works without any headaches across multiple distros.  That's gotten MUCH better over the last few years, but developers hesitant to port their work to an already small community (by comparison) are going to be even more hesitant when they have to either do it twice or choose which of two even smaller communities to support.  Those that do continue to develop commercial software will either pick whichever is more prevalent (not Mir) or they'll continue to write software for X, which will be sub-par in XMir or XWayland.

Most software development isn't targeted for X, it is written using a particular toolkit such as GTK or QT.

Once GTK and QT have been developed to a stage where they can use Weyland, Mir or X as a backend then software doesn't need to know or even care what display server you are running, as all of the communication with the display server is handled by whichever toolkit you are using.

---

### Post by tartalo on 2013-03-06
> **VeeDubb said:**
> developers hesitant to port their work to an already small community (by comparison) are going to be even more hesitant when they have to either do it twice or choose which of two even smaller communities to support.  Those that do continue to develop commercial software will either pick whichever is more prevalent (not Mir) or they'll continue to write software for X, which will be sub-par in XMir or XWayland.

But, don't GTK and QT toolkits save those headaches to the app developers? How many user apps talk directly to X?

The graphic card drivers are however a different issue, Mir plans to use the Android driver infrastructure, and that would be different to X or Wayland, in this area the kind of problems you predict seem more possible to me.

EDIT: Beaten by Cheesemill

---

### Post by lykwydchykyn on 2013-03-06
> **tartalo said:**
> But, don't GTK and QT toolkits save those headaches to the app developers? How many user apps talk directly to X?


Window managers, for one.  

Applications that don't use GTK or QT, or require older versions of these toolkits, will be in trouble.

---

### Post by alexfish on 2013-03-06
It will be interesting to see the results when implimented.

Brave move or not , when we have lowpower / Mhtz cpu with high power graphics , then if something stands in the way , something will give.

here is an aspect to look at , If got the lastest highest spec machine and the graphics don't run any faster than an Amiga from 80's,

we have to be asking ourselves a question.

I know what I will be doing.

BR

Alex

PS I saw somewhere about support for x11 , this should enable developers enough time to adjust , will it or will it not.

---

### Post by BigCityCat on 2013-03-06
I think this puts a lot of pressure on the Wayland devs to get Wayland ready quickly. They will be ready before MIR is ready by a long shot imho. Lets face it, Ubuntu has over promised and under delivered too many times to be believed. I'm not saying I am against the move to MIR. I'm just stating the obvious. I have a feeling Ubuntu will have MIR ready for the mobile but the desktop will suffer greatly. They will lose a huge amount of their users and that will alienate corporate interest because Ubuntu's track record of decision making and following through can't be relied on. Without their user base they have nothing to push adoption by manufacturers. This is a very risky move for them. They really need to reassure their users. I don't think empty words will do.

---

### Post by prodigy_ on 2013-03-06
> **BigCityCat said:**
> I think this puts a lot of pressure on the Wayland devs to get Wayland ready quickly.
Ready for what? They have a stable version (currently 1.0.5) and both GTK+ and Qt support it. 

Wayland is ready but there are still no binary drivers for it (from nVidia and AMD). The situation could change but now they'll continue to make drivers for X.Org most likely waiting for the war to end. And this is how Mir will hurt everyone in the Linux community. Not just Ubuntu users, not just Wayland developers, everyone.

---

### Post by viperdvman on 2013-03-06
I too wonder what will become of Kubuntu, Xubuntu, Lubuntu, and Ubuntu Studio when Ubuntu makes the move to Mir. Not only that, what will become of the tons of Ubuntu-based distros out there, especially Linux Mint? I know Ubuntu will still support X for those apps that require it,but  how long will it continue to support X before all those distros have to decide? Are they going to go with Mir as well? And that brings forth another question... will Mir support all the different desktop environments (GNOME, KDE, Xfce, LXDE, E17, Pantheon, Openbox, etc.) out there like X currently does? If it will, and there's enough legacy support for older hardware, older software, etc.... then there shouldn't be too much to worry about. But for now, there are **far FAR** more questions, lots of FUD, etc. regarding Ubuntu's decision to develop their own display server.

There are definitely some big changes ahead for all of the Linux community in light of this news... way bigger than even the implimentation of **systemd **in some of the big distros (i.e. Fedora and Arch). Wayland was already promising itself to be the next big thing, possibly as **the** replacement for X. That in itself was going to be a big step in the evolution of Linux. Now the problem is we have Canonical bringing out Mir, another display server thrown into the fray, making Linux even more fragmented than it already is. The problem is: When Mir does take off, where will software and hardware support development go and who will they favor? Will it lean more toward Ubuntu and thus Mir, will it lean toward Wayland if it does finally take off, or will it stick with X? The biggest questions as far as software development and hardware support will definitely be aimed straight at AMD and NVidia. Are they going to end up choosing a side, and thus dictate which direction the Linux community goes, or will it support multiple display servers? And in addition to that... will they still support older hardware on whatever display server they decide to favor? I know AMD already doesn't support their older hardware with their newest Linux drivers.

It'd be quite interesting to see what happens to the Linux community whenever Mir takes off. Though I do wonder:

What does Linus Torvalds think about all this?

---

### Post by Mikeb85 on 2013-03-07
Unless Canonical hired a whole bunch of devs away from Microsoft or Apple, I don't see this ending well.  The move to QT is a good one, they should have done that from the beginning though.  Mir?  Reminds me of the space station.  Not a good omen.  

But what's even worse for Canonical is this:  Ubuntu is not stable.  I've had a ton of issues with both 12.04 and 12.10, and I have fairly standard hardware, and don't mess with things.  They have no vendors for their smartphone and tablet OS yet.  They have no major vendor for the desktop OS.  

I'm typing this on openSUSE 12.3 right now.  KDE 4.10 is great, and SUSE 12.3 is great.  Fast and stable (on my Thinkpad).  And it's not officially released yet.  But already giving me less trouble than Ubuntu.  

I'm afraid Ubuntu will more than likely underwhelm on every platform, if I were to place a wager that anything could rival Apple and MS, it would be that no desktop Linux will truly rival them, and the only mobile Linux operating system with a shot at the iOS/Android duopoly is Sailfish by Jolla.  Desktop Linux is nothing more than a developer platform these days (and maybe a niche gaming OS in the future), and I think that will become more apparent as time goes by...

---

### Post by VeeDubb on 2013-03-07
> **Cheesemill said:**
> Most software development isn't targeted for X, it is written using a particular toolkit such as GTK or QT.

> **tartalo said:**
> But, don't GTK and QT toolkits save those headaches to the app developers? How many user apps talk directly to X?


Very true, and I stand corrected on that score.  That said, I still see doom for Ubuntu as one of the two most likely outcomes.  As for whether doom or glory is more likely, I still think the jury is out.

> **prodigy_ said:**
> Wayland is ready but there are still no binary drivers for it (from nVidia and AMD)

And for MANY end users, myself included, this is an absolute deal breaker.  In fact, this 'may' be one of the things that pushes Mir/Ubuntu to the forefront. If they're in talks with AMD and nVidia, they may be able to get working drivers out first.  Of course, they still have several years of catch-up to do, including the aforementioned GTK/QT support.

---

### Post by Paqman on 2013-03-07
> **Dry Lips said:**
> *[COLOR=#000000][FONT=verdana]"A video by one of the Mir developers shows Unity running on Mir. But it's running Unity through an X Server via the "XMir" project. [...]  [/FONT][/COLOR][COLOR=#000000][FONT=verdana]XMir is to Mir as XWayland [/FONT][/COLOR][COLOR=#000000][FONT=verdana]is to Wayland. [...] [/FONT][/COLOR]*[COLOR=#000000][FONT=verdana]*XMir is basically an in-session root-less X Server running atop Mir. This is how legacy X11 applications will continue to be supported by Mir and is the same approach that Wayland developers did for running X applications on their display server."*

Source: [/FONT][/COLOR][http://www.phoronix.com/scan.php?page=news_item&px=MTMxODQ](http://www.phoronix.com/scan.php?page=news_item&px=MTMxODQ)


I'm no expert on the issue, and this is probably not the best way to phrase it, but perhaps you could say that what they really are demonstrating is an X emulator? In that case they are far from having a "working prototype".

Ah. That seems like a bit of a fudge then.

However, having X compatibility as an early milestone seems like a sensible thing to do.

I'm not quite so sure why there's such a lot of loyalty to Wayland from folks. Why does it matter if Canonical develops their own display server? Google did the same when they took a Linux base to make Chrome and Android, and Apple did the same for BSD/Darwin to make OS X. It seems like a new display stack is something several major software engineering companies have independently decided needs to be done. X is clearly not good enough, and there doesn't seem to be a lot of support behind Wayland yet either.

---

### Post by georgelappies on 2013-03-07
> **viperdvman said:**
> I too wonder what will become of Kubuntu, Xubuntu, Lubuntu, and Ubuntu Studio when Ubuntu makes the move to Mir. Not only that, what will become of the tons of Ubuntu-based distros out there, especially Linux Mint? I know Ubuntu will still support X for those apps that require it,but  how long will it continue to support X before all those distros have to decide? Are they going to go with Mir as well? And that brings forth another question... will Mir support all the different desktop environments (GNOME, KDE, Xfce, LXDE, E17, Pantheon, Openbox, etc.) out there like X currently does? If it will, and there's enough legacy support for older hardware, older software, etc.... then there shouldn't be too much to worry about. But for now, there are **far FAR** more questions, lots of FUD, etc. regarding Ubuntu's decision to develop their own display server.

There are definitely some big changes ahead for all of the Linux community in light of this news... way bigger than even the implimentation of **systemd **in some of the big distros (i.e. Fedora and Arch). Wayland was already promising itself to be the next big thing, possibly as **the** replacement for X. That in itself was going to be a big step in the evolution of Linux. Now the problem is we have Canonical bringing out Mir, another display server thrown into the fray, making Linux even more fragmented than it already is. The problem is: When Mir does take off, where will software and hardware support development go and who will they favor? Will it lean more toward Ubuntu and thus Mir, will it lean toward Wayland if it does finally take off, or will it stick with X? The biggest questions as far as software development and hardware support will definitely be aimed straight at AMD and NVidia. Are they going to end up choosing a side, and thus dictate which direction the Linux community goes, or will it support multiple display servers? And in addition to that... will they still support older hardware on whatever display server they decide to favor? I know AMD already doesn't support their older hardware with their newest Linux drivers.

It'd be quite interesting to see what happens to the Linux community whenever Mir takes off. Though I do wonder:

What does Linus Torvalds think about all this?

Good post. Personally I hope that Mir does take off and that it is succesfull. Linux has to move on and not just keep trying to play catch-up when it comes to multimedia input / output. Seeing Canonical commit to starting this new technology is encouraging.

---

### Post by georgelappies on 2013-03-07
> **Paqman said:**
> Ah. That seems like a bit of a fudge then.

However, having X compatibility as an early milestone seems like a sensible thing to do.

I'm not quite so sure why there's such a lot of loyalty to Wayland from folks. Why does it matter if Canonical develops their own display server? Google did the same when they took a Linux base to make Chrome and Android, and Apple did the same for BSD/Darwin to make OS X. It seems like a new display stack is something several major software engineering companies have independently decided needs to be done. X is clearly not good enough, and there doesn't seem to be a lot of support behind Wayland yet either.

+1 Rather then fighting those who attempt to inovate, join a side and make it happen.

---

### Post by capink on 2013-03-07
> **Mikeb85 said:**
> Unless Canonical hired a whole bunch of devs away from Microsoft or Apple, I don't see this ending well.  The move to QT is a good one, they should have done that from the beginning though.  Mir?  Reminds me of the space station.  Not a good omen.  



There has been some hints in the past months that Ubuntu is not going to depend on Wayland. Yet, they delayed the annoucement until now, why? I think they did not want to make an announcement without being sure they can deliver. So they assembled a team to work on their new display server. And after some months of develoments, when they saw encouraging signs from their work, they went ahead and made the annoucement. I still think that April 2014 is very optimistic though.

---

### Post by alexfish on 2013-03-07
> **mr john said:**
> Our distro, our choice. Well, really Marks choice, as Ubuntu isn't a democracy.


Nor is this


Today we have a system based on so many layers , so your tying down the cpu time and development time to produce a result

Front end , user input .

get the info , 

render it to pixbuff using lib-a

take pixbuff-a and render it using lib-b

take pixbuff-b render it using lib-c

get root permision to render - ok

server gives permission to send pix-buff , ok , send pixbuff ,

Oops - Display Manager - forgot about  this one - "also decides what you can render"

server then renders to the gpu - 

gpu then renders to screen - What ?

---

### Post by Dry Lips on 2013-03-12
Here is an interesting article:[B]


LightDM Caught Off-Guard By Mir, Plans For Wayland
[/B][http://www.phoronix.com/scan.php?page=news_item&px=MTMyNTg](http://www.phoronix.com/scan.php?page=news_item&px=MTMyNTg)

---

### Post by Sableyes on 2013-03-12
Mir, something to be super excited about, a fresh new display server that may be better than Wayland. I imagine though every distro outside of Ubuntu will be to busy laying the hate on Canonical and in-fighting to make the move to Mir. Can anyone honestly imagine all the distro's saying 'Yeah lets use that new awesome display server *'made by canonical'* that replaces X, which we all know badly needs replacing'.

---

### Post by ZarathustraDK on 2013-03-12
> **Sableyes said:**
> Mir, something to be super excited about, a fresh new display server that may be better than Wayland. I imagine though every distro outside of Ubuntu will be to busy laying the hate on Canonical and in-fighting to make the move to Mir. Can anyone honestly imagine all the distro's saying 'Yeah lets use that new awesome display server *'made by canonical'* that replaces X, which we all know badly needs replacing'.

As it stands now that phrase might as well be "Yeah lets use that new awesome display server *'that can run games'* that replaces X, which we all know badly needs replacing'.

It really is an even matchup, Ubuntu may be alone compared to the community, but they got numbers and amd/nvidia-support. Lots of stuff can happen that'll influence the outcome in either direction, although amd/nvidia switching allegiance is not one of them, as that would entail them bending to intels and red hats whims, as I understand it.

---

### Post by tjeremiah on 2013-03-12
whatever they do I hope the scale plugin for compiz remains or improves.

---

### Post by lykwydchykyn on 2013-03-13
I have a feeling compiz is not going to survive this transition.  As I understand it, development of compiz is over; it would take a major effor to port it to a new display manager.

I'm sure the same effects & features will be there, but they'll be re-written from scratch.

---

### Post by mr john on 2013-03-13
Another internetz flamewar about vapourware... And as always I'll wait for the result before passing judgement. If anything ever comes of this I'll vote by using the best distro for my needs.

---

### Post by hainen on 2013-03-13
> **mr john said:**
> Another internetz flamewar about vapourware... And as always I'll wait for the result before passing judgement. If anything ever comes of this I'll vote by using the best distro for my needs.

Wayland isn't vaporware anymore, I have Arch Linux on one of  my computers and they ship Wayland and Weston in the extra repository, the same in which they have Xorg. More and more gtk3 applications has begun to work in Weston out of the box lately.

---

### Post by Dry Lips on 2013-03-13
Wayland certainly isn't vapourware, but there have been people questioning whether or not Canonical actually have the expertise and the manpower required to build something like MIR from scratch. 

I'm not sure myself, I'm no expert on the questions involved so I cannot tell whether or not what they say is true. So at least according to some people it is possible that MIR is a dead end, that they will tie up a lot of resources in this project and will have to abandon it in the end. That would of course be bad for Ubuntu...

---

### Post by Gyokuro on 2013-03-13
Wayland/Weston is not vapourware as it is already running can be tested and there are already efforts to bring in wayland support in major toolkits. MIR developers have to code all this support and hope that all this code get included in various upstream toolkits  (and hope that this changes get accepted) in a very short time frame. I found an email about Gnome's ongoing wayland support:  [https://mail.gnome.org/archives/release-team/2013-March/msg00087.html](https://mail.gnome.org/archives/release-team/2013-March/msg00087.html) 

With all past posts it seems that developers are more interested in to do more wayland work as nobody knows which code get published from Canonical devs. That skunk works coding is fine for closed source projects but not for open source projects.

---

### Post by ZarathustraDK on 2013-03-13
> **Gyokuro said:**
> With all past posts it seems that developers are more interested in to do more wayland work as nobody knows which code get published from Canonical devs. That skunk works coding is fine for closed source projects but not for open source projects.

From wikipedia:
> A skunkworks project is one typically developed by a small and loosely structured group of people who research and develop a project primarily for the sake of radical innovation.

Everett Rogers defines skunkworks as follows: "[It] is an especially enriched environment that is intended to help a small group of individuals design a new idea by escaping routine organizational procedures. The R&D workers in a skunkworks are usually highly selected, given special resources, and work on a crash basis to create an innovation." 

---

### Post by llanitedave on 2013-03-13
> **Gyokuro said:**
> Wayland/Weston is not vapourware as it is already running can be tested and there are already efforts to bring in wayland support in major toolkits. MIR developers have to code all this support and hope that all this code get included in various upstream toolkits  (and hope that this changes get accepted) in a very short time frame. I found an email about Gnome's ongoing wayland support:  [https://mail.gnome.org/archives/release-team/2013-March/msg00087.html](https://mail.gnome.org/archives/release-team/2013-March/msg00087.html) 

With all past posts it seems that developers are more interested in to do more wayland work as nobody knows which code get published from Canonical devs. That skunk works coding is fine for closed source projects but not for open source projects.

Open source is not about how you write code, but about how you distribute code.

---

### Post by alphacrucis2 on 2013-03-13
Oddly enough, the MIR announcement might actually be good for wayland because it seems to have lit a fire under the gnome & kde devs to get a move on with their support for for wayland.

---

### Post by JDShu on 2013-03-13
> **alphacrucis2 said:**
> Oddly enough, the MIR announcement might actually be good for wayland because it seems to have lit a fire under the gnome & kde devs to get a move on with their support for for wayland.

Hate driven development is a powerful thing. Probably won't last though.

---

### Post by alphacrucis2 on 2013-03-13
> **JDShu said:**
> Hate driven development is a powerful thing. Probably won't last though.

I don't think it's hate. More of a competition thing.

---

### Post by hainen on 2013-03-14
> **JDShu said:**
> Hate driven development is a powerful thing. Probably won't last though.

I think it's mostly a way to show suport to there upstream. Both KDE and GNOME has worked with the prepartaion for wayland a time now. At least the KWIN developer has blogged about it sometimes and I think it exist a year old experimental port of gnome mutter to wayland.
edit a example [https://phab.enlightenment.org/phame/live/1/post/enlightenment_and_efl_backing_wayland/](https://phab.enlightenment.org/phame/live/1/post/enlightenment_and_efl_backing_wayland/)

---

### Post by tjeremiah on 2013-05-14
Unity 8 Running on Mir :popcorn:
[video=youtube;E9AzRxsnfTE]https://www.youtube.com/watch?v=E9AzRxsnfTE&feature[/video]
[www.youtube.com/watch?v=E9AzRxsnfTE&feature=player_embedded]("www.youtube.com/watch?v=E9AzRxsnfTE&feature=player_embedded")

---

### Post by VeeDubb on 2013-05-15
Judging by that video, Mir is looking pretty awesome for this stage of the game.  Wayland took much longer than that to go from zero to running a desktop with X.  If ubuntu keeps it up, there's actually a chance they'll overtake Wayland.

On the down-side, Unity Next looks like a tablet interface.  If I wanted a tablet interface on my 23.5" desktop monitor I'd just run Windows 8.  Unity is fine at this point, and I've actually gotten to really enjoy a lot of its features, but if the default Ubuntu desktop ever looks and functions like that monstrosity, I'm done with Ubuntu.

---

### Post by tjeremiah on 2013-05-15
> **VeeDubb said:**
> Judging by that video, Mir is looking pretty awesome for this stage of the game.  Wayland took much longer than that to go from zero to running a desktop with X.  If ubuntu keeps it up, there's actually a chance they'll overtake Wayland.

On the down-side, Unity Next looks like a tablet interface.  If I wanted a tablet interface on my 23.5" desktop monitor I'd just run Windows 8.  Unity is fine at this point, and I've actually gotten to really enjoy a lot of its features, but if the default Ubuntu desktop ever looks and functions like that monstrosity, I'm done with Ubuntu.

From the video this is said to be the phone/tablet version. Looking forward to seeing the desktop version in motion.

---

### Post by landersohn on 2013-05-16
ZarathustraDK
I agree with your post #10 but ONLY if there remain options. I personally do not like integrated GUI's like Apple had and I really dislike Unity: I can't find anything. Maybe that's simply what I am used to for the last 25 years or so and I am a dinosaur but on the other hand that is no good reason to force people to change their habits. I am using Ubuntu for actual work to make a living and do not have the time to get used to new paradigms that offer in IMO no benefit whatsoever over what I am doing today. Change is good, change without benefit is waste.

---

### Post by sdowney717 on 2013-05-16
Will MIR work better with older video hardware to deliver smooth video performance of internet video?

I have an older laptop with nvidia go 6150 and it struggles with internet video. Such as full screen lags, stutter.
Audio video can get out of sync.

---

### Post by smellyman on 2013-05-16
> **VeeDubb said:**
> Judging by that video, Mir is looking pretty awesome for this stage of the game.  Wayland took much longer than that to go from zero to running a desktop with X.  If ubuntu keeps it up, there's actually a chance they'll overtake Wayland.

On the down-side, Unity Next looks like a tablet interface.  If I wanted a tablet interface on my 23.5" desktop monitor I'd just run Windows 8.  Unity is fine at this point, and I've actually gotten to really enjoy a lot of its features, but if the default Ubuntu desktop ever looks and functions like that monstrosity, I'm done with Ubuntu.

As tjeremiah pointed out, it is the phone/tablet interface and NOT unity 8.  It was just a vid to show Mir on the Desktop.

---

