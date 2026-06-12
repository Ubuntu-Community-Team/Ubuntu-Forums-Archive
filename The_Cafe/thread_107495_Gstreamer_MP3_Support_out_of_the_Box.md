---
title: "Gstreamer MP3 Support out of the Box"
date: 2005-12-23
forum: The Cafe
---

### Post by shidai.liu on 2005-12-23
In order to improve the GNU/Linux and Unix multimedia experience Fluendo announced today the immediate availability of their MP3 plug-in for the GStreamer multimedia framework. The MP3 decoder is available free of charge both for individual end users and GNU/Linux and Unix distribution makers.
...

[http://www.fluendo.com/press/releases/PR-2005-05.html](http://www.fluendo.com/press/releases/PR-2005-05.html)

---

### Post by poofyhairguy on 2005-12-23
Fluendo decided to pony up the cash for MP3's

[http://www.fluendo.com/press/releases/PR-2005-05.html](http://www.fluendo.com/press/releases/PR-2005-05.html)

We all will benefit! Legal Linux MP3 player out of the box!

---

### Post by JimmyJazz on 2005-12-23
hot damn! (no really I mean it I'm excited)

---

### Post by awaldram on 2005-12-23
Now that is Cool

---

### Post by markr on 2005-12-23
Does this mean that Rythmbox will support MP3 out of the box??  Cool....

---

### Post by Gandalf on 2005-12-23
That's cool, hopefully we get gst-10 with supported Totem and GNU mp3 on breezy, too bad breezy refuse to run on vmware so i can test it :'(

---

### Post by bonega on 2005-12-23
That's freaking sweet!

Sadly not free free, but huge nevertheless.
(not source free depending on which country you live in)

---

### Post by curtis on 2005-12-23
Wow this really is good, I hope it gets included.

---

### Post by curuxz on 2005-12-23
I dont think so, only their application because they must have optained a licence. Though rythumbox could always install it at the same time and then 'borrow' parts of the other program to keep it legal and out of the box...

Anyway thats my reading of the legal situation others may disagree :)

---

### Post by asimon on 2005-12-23
[quote=http://www.fluendo.com/press/releases/PR-2005-05.html]
this one will allow MP3 working out of the box with any distribution entering into our distribution agreement.[/quote]
So, the distro has to sign a contract with Fluendo to be able to distribute it? Somhow I don't think that is in line with Ubuntu's public commitemet, which "is entirely committed to the principles of free software development". So I think this is a no-no for main, maybe the Ubuntu Foundation can sign such a contract to push it to multiverse. Or -- and I hope not -- make a compromise, put it into main, installed by default, and depart a little bit more from the free software ideal...

---

### Post by shidai.liu on 2005-12-23
[QUOTE=asimon]So, the distro has to sign a contract with Fluendo to be able to distribute it? Somhow I don't think that is in line with Ubuntu's public commitemet, which "is entirely committed to the principles of free software development". So I think this is a no-no for main, maybe the Ubuntu Foundation can sign such a contract to push it to multiverse. Or -- and I hope not -- make a compromise, put it into main, installed by default, and depart a little bit more from the free software ideal...[/QUOTE]

In addition to making their licensed binary plug-in available to the public Fluendo also released the source code to this MP3 plug-in under the very permissive MIT license allowing all kind of developers and companies access to it.

---

### Post by -Rick- on 2005-12-23
Nice!
I believe that kde will use gstreamer instead of arts in later versions so free mp3 for everyone :)

---

### Post by asimon on 2005-12-23
[QUOTE=shidai.liu]In addition to making their licensed binary plug-in available to the public Fluendo also released the source code to this MP3 plug-in under the very permissive MIT license allowing all kind of developers and companies access to it.[/QUOTE]
Nonetheless to be able to redistribute it, i.e. have the package on archive.ubuntu.com or on the cds you need a written and signed contract with fluendo. Not the stuff you usually associate with Free Software. If you are not free to redistribute it, it's not Free Software, no matter what license they use for the source. The right to freely redistribute the software is one defining characeristica of Free Software.

EDIT: So in my book it's open source, but not free software. And Ubuntu is commited to free software, not open source. But I forgot the 'restricted' repo, maybe that is a good place for it. There are already propritary device drivers there. For many user's out-of-the-box mp3 support is a very high wish, thus having it there make sense, even if it's not in the free software spirit.

---

### Post by asimon on 2005-12-23
[quote=poofyhairguy]We all will benefit! Legal Linux MP3 player out of the box![/quote]
But it's not Free Software. You are not permitted to redistribute it without a written and sigend contract with Fluendo. Open source, yes, free as beer, yes, Free Software, no.

There is also [ this thread](http://ubuntuforums.org/showthread.php?t=107493). One is a duplicate. :-)

---

### Post by Wolki on 2005-12-23
More details here:
[http://www.fluendo.com/resources/fluendo_mp3.php](http://www.fluendo.com/resources/fluendo_mp3.php)

---

### Post by KLineD on 2005-12-23
Excellent news no matter what. I just hope this can be installed by default so end users get a nicer out of the box experience. If this can't be done, at least it should make mp3 support installing even easier as it is today.

---

### Post by lithorus on 2005-12-23
From [http://www.fluendo.com/resources/fluendo_mp3.php](http://www.fluendo.com/resources/fluendo_mp3.php)
> Issues to be aware of

If you are living in a country where the mp3 patents don't apply you can of course use the source code provided by Fluendo (or anyone else) to get legal mp3 support onto your Unix/GNU/Linux desktop.

On the other hand, if you live in a country where the patents apply, or if you are a distribution maker who sells your distribution in countries where the patents apply, then you need the licensed binary from Fluendo. This of course is no problem, but be aware that even if our binary is made from MIT licensed source code the resulting binary combined with our license is not free software, at least not GPL-compatible. This means that if you ship GStreamer with our binary mp3 plug-in, you need to be sure that you don't ship any GPL-licensed plug-ins that could end up being used together with the mp3 plug-in, as this would violate the GPL. And you don't want to violate the GPL. You also need to make sure you don't ship any GPL-licensed players which would use this plug-in.

Luckily most GStreamer plug-ins are LGPL and there are already playback applications out there with licensing terms that allow them to be used with non-free plug-ins. The Totem media player and the Banshee music player are two examples. 
Sounds like an even bigger no-no....

---

### Post by angkor on 2005-12-23
[QUOTE=poofyhairguy]Fluendo decided to pony up the cash for MP3's

[http://www.fluendo.com/press/releases/PR-2005-05.html](http://www.fluendo.com/press/releases/PR-2005-05.html)

We all will benefit! Legal Linux MP3 player out of the box![/QUOTE]

Very nice, thanx Fluendo!

---

### Post by xequence on 2005-12-23
Whoever Fluendo is, they have my respect ;)

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-23
The easier you make the "transition" the less likely it is to actually be a "transition." Look at DTV in the US - we have been making the "transitition" from analog broadcasts for two decades now, and it still ain't done.

You can already get mp3 support by adding the proper repositories and clicking a couple of buttons. I fail to see how this could make it any easier to get mp3 support in ubuntu without ubuntu compromising the *free* ethos.

---

### Post by jc87 on 2005-12-23
Now we only need to able to legally play WMV stuff out of the box , if only Microsoft would allow us to .... oh wait , what i was thinking , the words Microsoft and allow doesnt fit in the same sentence:rolleyes:.

---

### Post by kamstrup on 2005-12-23
This seems to be "the best we can achieve" with the patent encumbered mp3 format. Mp3-support will never [1] be eligible to the term "free software" because of patent-problems, no matter how people implement support for it.

[1]: Unless there is a world wide rejection of software patents. -- And that, my friends, will be the day you see monkeys flying out of my arse :-)

---

### Post by lolocaust on 2005-12-23
I for one will remain optimistic, and that companies will realise that suing each other for the smallest of software tidbits is rediculous. I will await the day people get fed up of software patents, and I also await the flying butt-monkeys :D

---

### Post by asimon on 2005-12-23
> **&#1055 said:**
> I fail to see how this could make it any easier to get mp3 support in ubuntu without ubuntu compromising the *free* ethos.
What this brings to people is a binary, which contains a fully lisenced* mp3 decoder. The stuff they already can download is not licensed, and thus illegal in many countries. As if the (majority of) people using mp3 care ... ;-)

But Ubuntu isn't as strict regarding free software as for example Fedora. I think Fedora would never include a non-free codec. But Ubuntu already ships propritary stuff in restricted, thus I wouldn't wonder if they include a Fluendo licensed binary. The word 'entirely' on ubuntu.com is already not true today, including this codec won't change it in any way.

*) The license only applies to the binary, if you compile the source your own the product won't be licensed anymore. Thus people who wan't to release custom distributions based on Ubuntu will probably need an other contract with Fluendo.

EDIT: Actually I find this all perverse. How much of all the mp3s people have is actually legal? 2%? 5%? 10%? Legally lisenced software to play illegal downloaded mp3s? Funny.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-23
> ...contains a fully lisenced* mp3 decoder. The stuff they already can download is not licensed, and thus illegal in many countries. As if the (majority of) people using mp3 care ...

Actually, no. because Faunhoffer owns the licensing rights to MP3 and they have said expelicitly that mp3 is completely legal for **individuals**. They even have made it legal for *limited distribution* if you have a small company and little net worth. What is not legal is large scale distribution of mp3 technology without a license. There is nothing at all illegal about me or you using LAME even if we got it from an offshore repository. That doesn't make it legal for Canonical to *distribute* LAME in binary form without paying a fee to Fraunhoffer.

So far as perversion... I have many legal MP3s. Many I ripped myself from CDs I purchased (OK, thoe are not MP3 - they are flac), and many I purchased online. I also downloaded many from newsgroups... which is itself not illegal and not necessarily against the wishes of the owners. For example, I discovered Shiva in Exile via a usenet download. that project appears on Magnatune, and Magnatune encourages others to redistribute the works of their artists. This is exactly what someone did - and when I found, after enjoying the CD via the MP3 download, that I could purchase a lossless copy of the CD for eight bucks via Magnatune that's exactly what I did. As a result other Magnatune artists have recieved money from me and Magnatune has a regular shopper (and fan).

---

### Post by asimon on 2005-12-23
> **&#1055 said:**
> What is not legal is large scale distribution of mp3 technology without a license.
I think we can count distributing lame, mad, gstreamer-mad, etc. via servers like archive.ubuntu.com as large scale distribution, not? And if this distribution is illegal, I suppose that if I download such a package this download is illegal too. But this is a case which I better let the lawyers handle, because I am absolutly not sure.

And most (free) mp3 codecs are under GPL. IIRC the GPL cancels your right to distribute it at all if there are patents (non royality-free) involved, because the GPL wants that any patent is freely licensed for anyone's use, not only for indiviuals. I.e. for example the GPL allows that lame can be used by big money-making enterprises freely. But the mp3 patents forbid this. Conflict. The only way patent and license are fullfilled is if lame is not distributed at all, otherwise you either don't fullfill the GPL or the patent.

> **&#1055 said:**
> 
That doesn't make it legal for Canonical to *distribute* LAME in binary form without paying a fee to Fraunhoffer.
What I wonder is if the distribution of a package is illegal in the first place, can it then still be legal for me to download and use such a package? I guess the anwer depends on where you live. Anyway I don't know the answer for this case even for the place where I live. At least for music in Germany I know that if the source is illegal then the download is it too.

> **&#1055 said:**
> 
I also downloaded many from newsgroups... which is itself not illegal and not necessarily against the wishes of the owners.
Most of the time the owners are not the artists themselves but the big music companies and in some countries it's illegal to download from such sources, if they IP owner hasn't given it's okay.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-23
> I think we can count distributing lame, mad, gstreamer-mad, etc. via servers like archive.ubuntu.com as large scale distribution, not? And if this distribution is illegal,

I'm very tempted to say "duh" here... only because that's what I jsut said. You say it as if it was some sort of epiphany for you.. *hey moe, why don't we just go in the window over there?*

>  I suppose that if I download such a package this download is illegal too

Ummm... not unless you are downloading ten thousand copies. as I **just** pointed out, the IP owner has said they do not care to enforce their rights upon anyone not distributing more than ten thousand copies or upon any entity not worth more than a certain amount of money. That makes any individual *download* for purely personal use inherently legal. The IP owner sets the terms of the contract, and that's what they have said. Unless you're trying to defend republishing that download there's no need for lawyers to get involved. *Theoretically* their terms have even allowed limited p2p sharing of their technology, since any single user could limit their distribution to, say, 1000 copies per year and still allow access to the technology to anyone within that p2p community. that's just conjecture - but the fact is the owner of MP3 has said personal use of the technology (including limited redistribution) is explicitly allowed.

> Most of the time the owners are not the artists themselves but the big music companies and in some countries it's illegal to download from such sources, if they IP owner hasn't given it's okay.

It is up to the copyright owner to enforce their rights, not the government. The government can facilitate enforcement, but there is no mandate upon any owner to enforce those rights except where and when they see fit. If Britney gets posted to usenet it is up to Britney's "massas" to enforce their rights - primarily that means getting the material removed from the servers. Copying for myself that material from a server without their permission may not be strictly legal, but it is also not strictly illegal - I have no way of knowing, in advance, if those owners want to allow my download or not. This is one reason I would very much like to see development of a *robust* DRM system - at that point you could be reasonably assured your use of a given file (like my Shiva in Exile example) was not against the wishes of the copyright owner.

---

### Post by asimon on 2005-12-23
> **&#1055 said:**
> Ummm... not unless you are downloading ten thousand copies. as I **just** pointed out, the IP owner has said they do not care to enforce their rights upon anyone not distributing more than ten thousand copies or upon any entity not worth more than a certain amount of money.

This was not my question. For Music for example we have a law which makes every single download from a illegal source illegal. Does such a thing applies to software also? I guess yes.

> **&#1055 said:**
> 
That makes any individual *download* for purely personal use inherently legal. The IP owner sets the terms of the contract, and that's what they have said.
Of course that doesn't solve the conflict with GPL in the case with lame (and many others), which garantees me that I can use it for non-personal use too.

> **&#1055 said:**
> 
It is up to the copyright owner to enforce their rights, not the government. The government can facilitate enforcement, but there is no mandate upon any owner to enforce those rights except where and when they see fit. If Britney gets posted to usenet it is up to Britney's "massas" to enforce their rights - primarily that means getting the material removed from the servers.

But irrelevant. It would be illegal no matter if someone gets sued or not.

> **&#1055 said:**
> 
Copying for myself that material from a server without their permission may not be strictly legal, but it is also not strictly illegal
Absolutely wrong. In some countries it's illegal. No discussion here. Maybe not where you live but at other places.

> **&#1055 said:**
> 
I have no way of knowing, in advance, if those owners want to allow my download or not.
This is one reason I would very much like to see development of a *robust* DRM system - at that point you could be reasonably assured your use of a given file (like my Shiva in Exile example) was not against the wishes of the copyright owner.
This is the strangest reason I ever heard for wanting DRM.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-23
> This was not my question. For Music for example we have a law which makes every single download from a illegal source illegal.

Ummmm.. where the hell do you live? There is no such law in the US because there is no such thing as an "illegal source." Even kazaa et al being held responsible for facilitating and fostering software piracy doesn't make kazaa an "illegal source." The fact such a company gets sued out of existence for these things still does not make them an "illegal source." The only place you're likely to find "illegal sources" is in countries like China and Cuba and Saudi Arabia and those prohibitions have nothing whatsoever to do with international copyright treaties. 

> *Copying for myself that material from a server without their permission may not be strictly legal, but it is also not strictly illegal*
Absolutely wrong. In some countries it's illegal. No discussion here. Maybe not where you live but at other places.

I'm calling your bluff. Let's see some citations.

The limitations put upon mp3 by the owners of that technology *explicitly allow* individual use and limited distribution of their technology. the only way this contract could be unenforceable is if the technology is regulated or forbidden by the government. Are you saying there are countries where MP3 technology itself has been made illegal?

> Of course that doesn't solve the conflict with GPL in the case with lame (and many others), which garantees me that I can use it for non-personal use too.

Then this doesn't change anything because the license in question here applies only a *decoder*. It does not allow you to *encode* the content. Likewise, the limitations by Fraunhoffer still do not conflict on the grounds of professional use because Fraunhoffer does not regulate the tools used, only the technology itself. So long as you pay Fraunhoffer their fees for your fifty thousand webcast listeners they don't care whether you use their encoder or LAME.

---

### Post by asimon on 2005-12-24
> **&#1055 said:**
> Ummmm.. where the hell do you live? There is no such law in the US because there is no such thing as an "illegal source." Even kazaa et al being held responsible for facilitating and fostering software piracy doesn't make kazaa an "illegal source." The fact such a company gets sued out of existence for these things still does not make them an "illegal source." The only place you're likely to find "illegal sources" is in countries like China and Cuba and Saudi Arabia and those prohibitions have nothing whatsoever to do with international copyright treaties.
In Germany it's both illegal, to distribute nonlisenced music, and for people it's illegal to download it.

> **&#1055 said:**
> 
The limitations put upon mp3 by the owners of that technology *explicitly allow* individual use and limited distribution of their technology. the only way this contract could be unenforceable is if the technology is regulated or forbidden by the government. Are you saying there are countries where MP3 technology itself has been made illegal?
We're mixing discussion of legal/illegal content downloads, patents, and copyright. I guess this is the reason for the confusion. What you just wrote is true, I guess we talked at cross-purposes.
From the patent site your allowed to limited distribute this stuff. But from the copyright lisence your allowed much more. Thus there can be cases where you fillfill the copyight lisence but not the patent rights.

> **&#1055 said:**
> 
Then this doesn't change anything because the license in question here applies only a *decoder*. It does not allow you to *encode* the content. Likewise, the limitations by Fraunhoffer still do not conflict on the grounds of professional use because Fraunhoffer does not regulate the tools used, only the technology itself. So long as you pay Fraunhoffer their fees for your fifty thousand webcast listeners they don't care whether you use their encoder or LAME.
Yes, but if you have to pay, then the distributions rights under the GPL are void in which case the distribution was illegal.

---

### Post by macewan on 2005-12-24
Fluendo is happy to announce a cost free MP3 plugin for the GStreamer framework. This plugin will allow both users and distributors to get out of the box MP3 support together with GStreamer using applications. You can read more about it in the Fluendo [press release]("http://www.fluendo.com/press/releases/PR-2005-05.html") and on the [Fluendo MP3 page]("http://www.fluendo.com/resources/fluendo_mp3.php").

via: [http://gnomedesktop.org/node/2533]("http://gnomedesktop.org/node/2533")

---

### Post by Sheinar on 2005-12-24
Edit: Nevermind.

---

### Post by The Warlock on 2005-12-24
[QUOTE=asimon]In Germany it's both illegal, to distribute nonlisenced music, and for people it's illegal to download it.[/quote]

Still no such thing as an "illegal source", unless the law is very different than I think it is. If there is copyrighted and uncopyrighted (or public domain or GPL or what have you) material on a server, and I (legally) download the uncopyrighted works, is that illegal because they came from a server that breaks the law, an "illegal source"?

(If so, you have a pretty dain bramaged legal system over there. No worries, though, as the Ubuntu main repo is in the United States, whose copyright law is fucked up in other ways, but not that one)

---

### Post by asimon on 2005-12-24
[QUOTE=The Warlock]Still no such thing as an "illegal source", unless the law is very different than I think it is. If there is copyrighted and uncopyrighted (or public domain or GPL or what have you) material on a server, and I (legally) download the uncopyrighted works, is that illegal because they came from a server that breaks the law, an "illegal source"?[/quote]

Probably there is a better and more correct term for this as "illegal source", but I don't know the correct english term, sorry. The situation with our new copyright law is that copying of music is allowed for your private environment (court rulings speak of a maximum of 7 copies for friends etc.). The law gives you this right to copy music content for private use without the need of any lisence. But if someone offers content for public download, it's no longer private and the respective law paragraph don't apply in this case. And the current legal consens is that if the copy on the server is illegal, then the download is it too. And as I sayed that is for music content only. It does not apply for software. For Software, our copyright law doesn't give you the right to copy it for private purposes at all. That is handled by the lisence of the software.

EDIT: To answer your question. No, if you download GPL or public domain software from some server, than it's perfectly legal because those lisences allow you to download this stuff, even if the server also offers for example pirated software. As long as you don't download them, you're fine. IANAL.

[QUOTE=The Warlock]
(If so, you have a pretty dain bramaged legal system over there. No worries, though, as the Ubuntu main repo is in the United States, whose copyright law is fucked up in other ways, but not that one)[/QUOTE]
Actually our legal system is brain damaged in so many multiple ways it's terrible. But where isn't it? ;-)

To come back to topic, [Thomas Stichele (who I think works for Fluendo) blogged a summary about the plugin](http://thomas.apestaart.org/log/index.php?p=333). Something which I haven't read anywhere before is that the sound quality of the Fluendo plugin is not as good (yet) as mad.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-24
> Yes, but if you have to pay, then the distributions rights under the GPL are void in which case the distribution was illegal.

There's nothing in the gpl saying you cannot charge for software. There's nothing in the gpl saying you cannot use licensed technology. IBM, for example, has made a very big deal about allowing essentially unlimited license to its patents within the context of GPL - ie "we own it but we won't assert our rights so long as you play fair."

This is exactly what Fraunhoffer has done. Fact is they own the right to MP3 in all its flavors - they own the technology itself, not just specific implimentations of it. If you are running an mp3 webcasting site they will allow you to build an audience before they assert their rights - but once you are of sufficient size one could reasonably expect you to be profitable, they want their licensing fees. To make it "easy" they have even set limits on annual fees, etc - but paid they must be.

Now, when you post mp3s on the web how many downloads are made? If you have access to server logs you can record this and, for example, shut down the server once it has distributed a set number of downloads. But when you post an mp3 to a p2p network you cannot do this - it's out of your control. Because you cannot assure the FI you are abiding their terms of use you could be sued by Fraunhoffer itself. In theory Fraunhoffer could step in where the RIAA has failed and completely squash the problem simply by asserting **their rights** and sending c&d orders to every usenet provider that has not paid them licensing fees - because, technically, every mp3 posted to every newsgroup is a violation of Fraunhoffer's limited distribution license. 

But they don't do that. Why? Because those "illegal downloads" are what has fueled the entire "ipod industry." If they squash that "illegal content" the public will just move to another technology that *isn't* regulated, the sound appliance manufacturers will be forced to support that new, "free-er" format, and the FI will be out all those licensing fees being collected from Apple and Creative. 

So, they choose to assert their rights only where it is in their best interest - they are a "good player" because it suits them economically.

---

### Post by asimon on 2005-12-24
> **&#1055 said:**
> There's nothing in the gpl saying you cannot charge for software.
In the quoted context I meant of course not charging for software, but charging royalities for patents. The GPL-2 speaks very clearly about this. Again, don't mix patents and copyright.

And what the Fraunhofer Gesellschaft did was not the same what IBM did. You already mentioned the big difference above in your own postings.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-24
> In the quoted context I meant of course not charging for software, but charging royalities for patents. The GPL-2 speaks very clearly about this.

Doesn't matter. LAME is lgpl - one is allowed to make "non free" versions. and the gpl (or any license) can only be prosecuted by the license holder  in this case that means the fellow who makes LAME and those who agree to contribute to his project. Anyone who contributes to LAME most certainly will become (if they're not already) of the potentials for "non free" status of the software.

The GPL is not a self sustaining entity - it only means something to the people who actually wrote the licensed code. The person behind LAME *definitely* is aware of the legal issues because FI made their feelings very clear to him some time ago. LAME is only released in source form as an educational endeavour and if others compile it and offer it for download under terms not meeting with FI's approval it is up to the FI to prosecute their rights against those who are *publishing* it. You cannot say a given piece of software is "illegal" simply because the lgpl code makes use of patented technology - there are plenty of lgpl projects that make use of patented technolgy - and, in this case, none of the limitations outlined by the FI stipulate where or how one might initially obtain their technology.

> ...don't mix patents and copyright.

Rather impossible as your argument is based on terms of the gpl and the gpl itself addresses both these issues.

---

### Post by asimon on 2005-12-25
> **&#1055 said:**
> Doesn't matter. LAME is lgpl - one is allowed to make "non free" versions.
Right, I thought it was GPL, thus a bad example. But there are mp3 implementations under GPL, too, aren't there? At least the blog of a Fluendo developer says so.

> **&#1055 said:**
> 
The GPL is not a self sustaining entity - it only means something to the people who actually wrote the licensed code.
I don't know what you mean. Of course the lisence means something to the user of the software too! It defines what rights he has. What he can do with the software, if and how he can redistribute it, etc.

> **&#1055 said:**
> 
The person behind LAME *definitely* is aware of the legal issues because FI made their feelings very clear to him some time ago. LAME is only released in source form as an educational endeavour and if others compile it and offer it for download under terms not meeting with FI's approval it is up to the FI to prosecute their rights against those who are *publishing* it. 

Yep.

> **&#1055 said:**
> 
You cannot say a given piece of software is "illegal" simply because the lgpl code makes use of patented technology - there are plenty of lgpl projects that make use of patented technolgy - and, in this case, none of the limitations outlined by the FI stipulate where or how one might initially obtain their technology.
No no, lame was a bad example because I thought it was GPL. I was always speaking of GPL! My point was that patents (if you don't have a unlimited royality-free usage right) and the GPL can conflict in such a way that the GPL doesn't give you any rights to redistribute the software at all. And somewhere above I wondered that if the distribution is illegal, is then a download illegal too, just like it is for example in Germany with music. That was all.

> **&#1055 said:**
> 
Rather impossible as your argument is based on terms of the gpl and the gpl itself addresses both these issues.
Yes.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-25
> And somewhere above I wondered that if the distribution is illegal, is then a download illegal too, just like it is for example in Germany with music.

We've spent two pages on this now, is my example still not clear?

LAME may be distributed in binary form against the wishes of the patent owner, yet the FI has explicitly allowed use of their technology by individuals or even profit making entities so long as that use is within certain guidelines. Since it is up to the owner of the technology to deem "legality," any individual using a binary LAME - even when it was downloaded from an illicit source - may still do so while abiding the terms of the rights holders.

The creator of LAME obviously has other interests at heart; LAME is a poltical statement and a technological exercise. It is, in many ways, "better" than the FI implimentation. Because LAME is lgpl someone could, theoretically, use it in a FI licensed product (although the FI might not approve because of those previously mentioned political reasons). 

Copyrights and patents afford the owners certain exclusive and limited rights, but it is up to those rights owners to assert them when and where they see fit. Because LAME is not licensed but employs patented technology, corporations (like Canonical) cannot *distribute it* in binary form without risking prosecution from the patent owner (who has forbidden such use).  This does not make LAME itself "illegal" nor does personal use of LAME *necessarily*  violate the terms outlined by the FI.

---

### Post by asimon on 2005-12-25
> **&#1055 said:**
> We've spent two pages on this now, is my example still not clear?
It is clear, no need to tell again. :-) And your example isn't even in opposition with the conflict I pointed out between GPL and the mp3 patents. So where is the problem? I think everything should be clear by now and we can rest this.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-25
What "conflict?" If you write a contract ascribing rights to someone tha you do not have it is not a valid contract. The GPL is not a thing unto itself - it can only be prosecuted by the rights owner, and if you do not own those rights then your contract is unenforceable. If you tack the GPL on a piece of patented tchnology then **your** contract is unenforceable - but that doesn't make your software inherently "illegal." That is still up to the patent holder (and the courts) to decide.

---

### Post by asimon on 2005-12-25
*deleted*

---

### Post by Bandit on 2005-12-25
I think everyone has totally missed the reason MP3 codecs are what you call fishy..
The reason they are no longer shipped via the CD anymore is due to pantent infrindgement. It doesnt matter if someone wrights a whole new codec today that can encode or decode MP3 format. The fact is if they do then they have wrote a piece of software that infridges about a dozen or more US patents.
A patent doesnt have to based on writen software, it can be a idea or concept behind a software (algorythm). Thus anything that decodes a MP3 algorythm then infrindges a patent.
This is why, it has nothing to do with LAME, MAD, MP321, MP123 or anything else..
It just has to do with stupid US patent laws. 
Now if I wrote a software (algorythm) that even tho was almost perfectly the same, but named the format MPZ and used *.mpz extentions to all my files.. You could get away with it. As it no longer would be directed at mp3 but at mpz a **NEW** file format. ;)
Cheers,
Joey

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-25
> The reason they are no longer shipped via the CD anymore is due to pantent infrindgement. It doesnt matter if someone wrights a whole new codec today that can encode or decode MP3 format. The fact is if they do then they have wrote a piece of software that infridges about a dozen or more US patents.

ROTFL. I think the someone who is telling us we have forgotten something has  "forgotten" to actually read the thread...

---

### Post by Bandit on 2005-12-25
> **&#1055 said:**
> ROTFL. I think the someone who is telling us we have forgotten something has  "forgotten" to actually read the thread...
I read the thread until I got bored of it.
I am not here to argue with you or anyone else. I only wanted to help.
I explained to you the reason most distro's dont offer MP3 support out-of-the-box anymore.
So you are welcome to take my answer or just ignore it, becuase I dont give a shit..
Cheers,
Joey

---

### Post by asimon on 2005-12-30
Update: Jeff Waugh just mailed today on the Ubuntu development mailing list: "It won't be in main, so it won't be on the default CD.".

No big surprise.

---

### Post by Bandit on 2005-12-30
[QUOTE=asimon]Update: Jeff Waugh just mailed today on the Ubuntu development mailing list: "It won't be in main, so it won't be on the default CD.".

No big surprise.[/QUOTE]
Exactly :)

---

### Post by stoffe on 2005-12-31
I think it is a bad thing. Ok, so MP3 is still more or less omnipresent, and support is very wanted - hey I want it too, still have a few MP3s from the dark ages.

But paying this [extortion]("http://mp3licensing.com/") money is legitimising software patents, and I really, really don't like that. Shipping and using it also amounts to the same, at the very least indirect support of something really wrong and bad.

[No software patents!]("http://www.nosoftwarepatents.com/")

---

### Post by parminides on 2010-02-11
> **&#1055 said:**
> Actually, no. because Fraunhoffer owns the licensing rights to MP3 and they have said expelicitly that mp3 is completely legal for **individuals**. They even have made it legal for *limited distribution* if you have a small company and little net worth. What is not legal is large scale distribution of mp3 technology without a license. There is nothing at all illegal about me or you using LAME even if we got it from an offshore repository. That doesn't make it legal for Canonical to *distribute* LAME in binary form without paying a fee to Fraunhoffer.


Could someone point me to a reliable link where Fraunhoffer expresses such an attitude.

---

