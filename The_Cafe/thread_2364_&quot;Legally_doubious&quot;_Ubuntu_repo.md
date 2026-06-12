---
title: "&quot;Legally doubious&quot; Ubuntu repo"
date: 2004-10-27
forum: The Cafe
---

### Post by Lovechild on 2004-10-27
I noticed that a lot of the needed debs for making Ubuntu useful, meaning audio/video codecs and so on are spread on several repos.

I'm hereby proposing that we collect them all in a complete project that will support current stable and current development. This would allow Ubuntu to keep Universe as a "debian-legal" clean repo, while also allowing users to easily add these needed packages to their system in one uniform and easy manner.

---

### Post by im_ka on 2004-10-27
good idea.
maybe we could combine the project with this one: [http://ubuntuforums.org/showthread.php?t=2353](http://ubuntuforums.org/showthread.php?t=2353)

:)

---

### Post by Lovechild on 2004-10-27
[QUOTE=im_ka]good idea.
maybe we could combine the project with this one: [http://ubuntuforums.org/showthread.php?t=2353](http://ubuntuforums.org/showthread.php?t=2353)

:)[/QUOTE]

I think that project is more of a Universe thing - but anything that's legally shady, I would like to take under this projects wings to shelter Ubuntu from those evil lawyers..

Regardless people are welcome to contact me to help set this up, meanwhile I'll go learn how to make debs (don't look at me like that, I'm used to ebuilds and abs PKGBUILDs).

We also need a cool name.

---

### Post by im_ka on 2004-10-27
oops, sorry for deleting that message, i wanted to edit it...

anyways, i fully support your idea. some ideas:
marillat mplayer
j2re (the source is mentioned somewhere)

it'd be nice if the user would only have to add one source to get the "doubious" apps.

btw, i've been using arch too :)

---

### Post by Lovechild on 2004-10-27
I was thinking we start with gstreamer and related apps seeing as that will have the biggest impact on Ubuntu.

but sure mplayer and so on would be fine candidates as well..

---

### Post by daniels on 2004-10-28
There's a huge problem, and it's right in the subject -- 'legally dubious'.

We've been reasonably liberal in what we ship, so most anything we've left out will get us sued if we ship it, we believe.  That applies to a separate tree, doubly so if we acknowledge right off the bat that they're legally dubious.

As much as I would love to see Ubuntu support all video/audio/whatever codecs out of the box, shipping the DLLs needed to support WMV (for example) would get us sued for blatantly violating the licence.  And that's a risk we cannot afford to take.

---

### Post by tolle on 2004-10-29
I assume it wouldn't be a part of the official Ubuntu distro but rather just something on the side, like the various repositories for fedora and redhat. I assume that wouldn't create a problem for the people that does the work at the ordinary Ubuntu tree. However, IANAL so I'm probably wrong.

---

### Post by im_ka on 2004-10-29
but if some1 does it unofficially, independent from the official ubuntu project...

christian marillat provides "legally dubious" packages for debian on his own server. does he get sued? gotta ask my law professor about this :)

---

### Post by Lovechild on 2004-10-30
As I said, it would be done outside of the Ubuntu tree fully unsupported or related to Ubuntu development - like livna.org is for Fedora.

The point would be to keep Ubuntu's back clean legally but still allow the users to pick the formats they needs - even though I prefer open standards and such we do sometimes need that .avi file to play or people will think we suck donkey butt.

I'm more than willing to stick my neck out for now, I would like to see them try suing me - most of the stuff we would provide like DVD playback would be perfectly legal at least here in Denmark - and I'm not the moral judge of what people will use it for, or where for that matter, as there would be no profit motive either mp3 support should be fine (it's as far as I can tell legal for none profit), only stuff that requires you to have a license before use like mpeg4 (XVID etc.) would be a problem as well as maybe the NTFS module for the kernel I'm not so sure about the legality of that especially if we were to provide it as a modified installer to allow partition resizing - so maybe a small chat with a lawyer before providing that would be a good idea. 

That being said, something like ICQ/MSN/AIM support which we provide in gaim, in the Ubuntu tree, isn't entirely legal either.

---

### Post by mark on 2004-10-30
[QUOTE=daniels]There's a huge problem, and it's right in the subject -- 'legally dubious'.

We've been reasonably liberal in what we ship, so most anything we've left out will get us sued if we ship it, we believe.  That applies to a separate tree, doubly so if we acknowledge right off the bat that they're legally dubious.

As much as I would love to see Ubuntu support all video/audio/whatever codecs out of the box, shipping the DLLs needed to support WMV (for example) would get us sued for blatantly violating the licence.  And that's a risk we cannot afford to take.[/QUOTE]
Sadly, I must agree with Daniel.  Here in the US of A, litigation of all sorts has become so popular, you'd think it was a sport.  And IP issues have begun to loom very large in this arena.

Unfortunately, I don't have an answer.  I wish I did - I'd like to have all the "bell 'n whistles" as much as anyone.  But I don't think setting up a "rogue" repository (or even encouraging one) is a good answer at this point.  There's too much potential for backlash of all kinds - legal, ethical, moral - and the wrong kind of publicity could be *very* damaging.  I really like using Linux and I don't want to see the community get a "black eye" over this.

For myself, I'm simply going to make the best use of what I have and wait for those that are a lot smarter than me to come up with a "squeaky-clean" solution.

Mark

---

### Post by coyote on 2004-10-30
I agree as well.

It was no problem to Google the necessary information that would tell me  how to make Totem play DVD's, etc.........Information is not illegal.

However, what I choose to do with it may well be?

Ubuntu as a "primetime free Debian distro" should not incorporate "questionable" packages.

They are readily available in other Debian depositories if you want them. Any "Linux savvy" user can figure out how to proceed from there. If you aren't Linux savvy, it ain't that hard to learn, man!!!

I love this Ubuntu  Distro!!! Let's do everything we can to keep it going forever, legally or otherwise!!!  :grin:

---

### Post by Lovechild on 2004-10-30
you guys just don't listen do you?

---

### Post by Visceral Monkey on 2004-10-30
First off, I did a double take when I saw lovechild and his logo. I'm use to seeing him on the Gentoo forums and I'm finding many, many ex-gentoo users who've moved over to Ubuntu. I wonder why that is?

I think what love is saying is that we could use a non-official repo that contains these items. Nothing Ubuntu itself has to be involved with. I guess the next question is would there be a problem if someone posted links to such repos on the Ubuntu forums? If so, it's pointless since the entire object is to make it easier to people to do a quick forums search, find the repo and add it to their synaptic, etc.

But I agree, it's something we could use.

Someone else pointed out "the debian mentality" or something to that effect. Here's my take on this: This is Ubuntu, based on Debian. It's not Debian itself and there's no reason we have to sink to the fanatical depths that the Debain community has. I love this distro, I don't like the semi-religious dogma that comes with Debian and personally believe it will only reduce the potential Ubuntu has to nothing more than Debian with a few patches thrown in. Maybe I'm just way off base here.

---

### Post by Lovechild on 2004-10-31
Wow, someone who listened.

Anyways the reasons I moved from Gentoo are pretty public by now, you can even google them I think.

But in general I think people are getting over the whole "*ZOINK* OMG, my portage is SOOOO much faster, j00 stewpid binary n00b" thing, now only the people who like the custom type distro that Gentoo gives you, uses it. I admit readily that the Gentoo community is by far the most fun distro community I know. If I ever get a 10GHz SMP setup I'll probably do Gentoo again, but compiling glibc on a 1600+ just isn't fun for me anymore (when I did it on my 90MHz pentium it was even less fun).

---

### Post by mark on 2004-10-31
[QUOTE=Lovechild]you guys just don't listen do you?[/QUOTE] Actually, I believe I do.

My comments were based largely on my "geopolitical" location.  As I mentioned, litigation here in the US based on intellectual property rights and/or patent infringement have been on the upswing lately.  I appreciate the fact that the situation is different in Denmark and recognize that you can do things there that we can't do here, in the "land of the fee & the home of the brave(est lawyer)".

My primary point was that it would be unfortunate to see Canonical run into any such legal dispute at this (relatively) early stage of the game.

Regards,

Mark

---

### Post by Lovechild on 2004-10-31
Canonical would be perfectly safe as long as they don't in anyway officially say that this project is supported - users can referer to the repo safely just like users of fedora referer to livna.org.

the sentence "completely and totally unsupported, might blow up your PC, make your soda taste bland, remove your sex appeal and, but not limited to making you blind"  does wonders.

---

### Post by cseg on 2004-10-31
The Xandros distribution has a couple of user-supported repositories with user-created dep packages.  I think it would be great to see the same thing for Ubuntu (with the proper caveats).

---

### Post by daniels on 2004-11-01
Ubuntu as a project cannot, and will not, create, or sanction, any 'legally dubious' distribution.  It is a  properly legal, above-board, project, sponsored by a law-abiding corporation, and we see no reason to change this, obviously.

---

### Post by im_ka on 2004-11-01
[QUOTE=daniels]Ubuntu as a project cannot, and will not, create, or sanction, any 'legally dubious' distribution.  It is a  properly legal, above-board, project, sponsored by a law-abiding corporation, and we see no reason to change this, obviously.[/QUOTE]

that being said, written, clarified, engraved in stone we could/should setup the repo.

---

### Post by chard on 2004-11-01
[QUOTE=im_ka]that being said, written, clarified, engraved in stone we could/should setup the repo.[/QUOTE]
 Please do, it would be a great service to use Linux newbies.

---

### Post by Visceral Monkey on 2004-11-02
I think we should move ahead with this with the understanding it is totally user supported and not connected officaly to Ubuntu in anyway. If anyone needs assistance, I'll do whatever I can..which might not be a lot but I'll try :)

---

### Post by mr_ed on 2004-11-03
[QUOTE=Lovechild]Regardless people are welcome to contact me to help set this up, meanwhile I'll go learn how to make debs (don't look at me like that, I'm used to ebuilds and abs PKGBUILDs).[/QUOTE]

Heh.  I thought I recognised the name.  ;)  I just moved over from Arch to Ubuntu the other day.  :)

To build .deb files, easiest way is to download checkinstall off the universe repos.

Do
./configure
make
checkinstall as user (instead of make install as root)

---

### Post by fng on 2004-11-03
Great idea Lovechild
2 thumbs up from a converted gentoo-er :)

There are a lot of programs in the portage tree, that arent even in universe/multiverse.  Sucha repo should be a good start  getting those programs into ubuntu.

Reading the 'Debian New Maintainers' Guide' as we speak.

---

### Post by Visceral Monkey on 2004-11-03
Anyone have a link on how to build ubuntu/debian packages? Also, and this might seem like a strange question, Is it possible/desireable to build packages for 686 or should we stick to 386 for all? I wonder if performance/speed would even be noticeable?

---

### Post by fng on 2004-11-04
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

---

### Post by fng on 2004-11-08
*bump*

---

### Post by r_a_trip on 2004-11-29
A repostitory for Ubuntu, containing packages that are not universally "clean" enough to ship with Ubuntu, should be hosted on a server in a territory where they are not "legally dubious".

The repository should have a page with disclaimers that they are not affiliated with Cannonical or the Ubuntu project in anyway and that use of the packages might not be legal in certain jurisdictions. It should mention that it is the responsibilty of the the user to determine if the use of these packages is legal in their territory.

If such an endeavour is handled in this manner, I don't think there would be problems to start such a "Humanity" repository.

---

### Post by poofyhairguy on 2004-11-29
[QUOTE=Lovechild]I think that project is more of a Universe thing - but anything that's legally shady, I would like to take under this projects wings to shelter Ubuntu from those evil lawyers..

Regardless people are welcome to contact me to help set this up, meanwhile I'll go learn how to make debs (don't look at me like that, I'm used to ebuilds and abs PKGBUILDs).

We also need a cool name.[/QUOTE]

--Developers close ears---

This is exactly what Ubuntu needs. Sure, for some people the debian respitories work, but not for all! I am still mad that I can't find an Mplayer package that will work on my machine. 
 ](*,)  ](*,) 

I've tried them all. But if someone had a repo where the packages were native to Ubuntu, they would work much better. 

A Livina.org type repo is THE BIGGEST THING ubuntu lacks. I can see why they don't include this stuff, but most desktop users want it! Its the only thing fedora has we don't.

As far as a name, how about Mandela? 

As far as packages, needs custom compiled:

mplayer
gstreamer
java
video card packages
ms fonts
xmms


 =P~  =P~

---

### Post by easy_target on 2004-11-29
Excellent idea! I myself spent long hours googling and still could not find some of the information I needed. To put everything (media wise) in a single rep would be the dream of every " ubuntista". 
I understand Daniels'  and the rest of  the Canonical crew's point, but if that is not linked to them in any way, and is located in 'neutral' territory, what harm can it do (lawyers please advise) ?
It would do wonders for a n00b like me!

---

### Post by poptones on 2004-11-29
You are using the *official* ubuntu community forum to discuss what is essentially a warez server. I realize in an ideal world this would not be the case, but until the US and the richer nations of euroupe are taken over by leaders who truly believe in a *free* market we're stuck with this reality.

*The first rule of warez clubs is you do not talk about warez clubs...*

---

### Post by boobytrapped on 2004-11-29
How are other distributions, such as gentoo, handling this situation?  I know that on a gentoo box, installing mplayer is a peice of cake (as far as fetching source/configuring is concerned -- after that it takes a century to compile, but let me not digress).

Can we take a leaf from other distribution's books on this topic?

---

### Post by poofyhairguy on 2004-11-29
[QUOTE=boobytrapped]How are other distributions, such as gentoo, handling this situation?  I know that on a gentoo box, installing mplayer is a peice of cake (as far as fetching source/configuring is concerned -- after that it takes a century to compile, but let me not digress).

Can we take a leaf from other distribution's books on this topic?[/QUOTE]

Sure, we can use Debians. Just put it in a repo where the laws are different. Then its legal.

---

### Post by MaZiNgA on 2004-11-30
All right let me get some things straight because I'm confused:
I like using some of these things on my ubuntu:
*nvidia-glx
*java
*mp3 playback
*totem-xine with w32codecs playback
*libdvdcss2
*I also found a link of a cedega .deb that says it was compiled from CVS...but haven't downloaded it yet...
*flash-plugin
*realplayer

Now can someone PLEASE explain to me which of these programs/libraries are 
-free/non-free?
-legal/illegal?

And probably how can some distros have support for these packages...
Thank you

---

### Post by r_a_trip on 2004-11-30
[QUOTE=MaZiNgA]All right let me get some things straight because I'm confused:
I like using some of these things on my ubuntu:
*nvidia-glx
*java
*mp3 playback
*totem-xine with w32codecs playback
*libdvdcss2
*I also found a link of a cedega .deb that says it was compiled from CVS...but haven't downloaded it yet...
*flash-plugin
*realplayer

Now can someone PLEASE explain to me which of these programs/libraries are 
-free/non-free?
-legal/illegal?

And probably how can some distros have support for these packages...
Thank you[/QUOTE]
 *nvidia-glx
-- legal/non-Free. Just download at [www.nvidia.com](www.nvidia.com) and use the installer.
*java
-- legal/non-Free. See also restricted formats in the Ubuntu wiki.
*mp3 playback
-- shady/non-Free. The sourcecode for Lame is free as an instructional tool, but compiling it and encode an mp3 seems is illegal.
*totem-xine with w32codecs playback
-- totem-xine - legal/Free -- w32codecs -- illegal/non-Free. MS does not allow their components to be used outside of Windows.
*libdvdcss2
-- shady/non-Free. Same as mp3. The sourcecode is instructional. Compiling and watching a DVD is an offense.
*I also found a link of a cedega .deb that says it was compiled from CVS...but haven't downloaded it yet...
-- legal/Free. CVS cedega doesn't have the secret sauce that makes the commercial version so popular.
*flash-plugin
--legal/non-Free
*realplayer
--legal/non-Free

---

### Post by MaZiNgA on 2004-11-30
Wow! Thank you a lot r_a_trip! It's been a while since I've seen such a straight answer..!
Now that's bad methinks..Lots of vital stuff an average user uses seem to be non-free...Is there a hope in the horizon that this will ever change? Debian's (and Ubuntu's) dream is to provide sth that's 100% free...
Some distros provide these things but...if I get it right:
-if you include mp3, libdvdcss2,w32codecs you eventually get sued
-you *can* provide all the others but you don't *want* to because it's opposed to your ethos?
Please give me some positive answer because "dark the future I see"...:p

---

### Post by TravisNewman on 2004-11-30
I HEARD that the libdvdcss decision had been overturned, but I could be wrong. Basically, I think I heard that the courts said that they weren't there to protect anyone's profits, they were there to protect everyone's rights, and that included the rights of users to watch dvds when they purchase them. Is this correct or am I thinking of another case? I'm almost sure that it's this one, but... ADD ;)

---

### Post by poptones on 2004-12-06
W32 codecs are not free, but what about the divx codec? What about ffdshow? AVi is not a protected file format (MS did lose that one) and the ffdshow codec is a well regarded open source project that has even had to deal with OTHER commercial products locking away its IP without regard to the GPL. I would think that would be just fine to include and it would allow folks to enjoy most of their AVIs OOTB.

---

### Post by jdong on 2004-12-06
Ok, I think Daniel has made his point. Ubuntu will NOT violate copyright laws or misuse other people's properties -- material or intellectual.

We don't have time to deal with borderline stuff, like recently overturned rulings, etc... The thought of legal action is haunting.


Let's stop now before we get on anyone's nerves, especially a dev's!

---

