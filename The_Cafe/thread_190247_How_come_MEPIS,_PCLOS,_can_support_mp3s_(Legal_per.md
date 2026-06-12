---
title: "How come MEPIS, PCLOS, can support mp3s? (Legal perspecitive)"
date: 2006-06-06
forum: The Cafe
---

### Post by Jucato on 2006-06-06
Let me state the question in full:
How come MEPIS, PCLinuxOS, KNOPPIX, and other "free" distros can support MP3 playback out of the box, while Ubuntu, for legal reasons, can't?

I'm just perplexed by it. It's more of a question about the legal issues concerned, rather than Ubuntu's commitment to free software.

Is it because MEPIS et al are just playing hooky, trying to get away with what they can? Surely there must be a reason.

---

### Post by GarethMB on 2006-06-06
Canonical won't pay for the license to include mp3 support because they support open software.

---

### Post by Jucato on 2006-06-06
So would that mean that distros like MEPIS and KNOPPIX paid for the license? I guess I could understand that if we were talking about big distros like Red Hat and SUSE. But these ones are completely free distros. But I guess it's possible...

---

### Post by zugu on 2006-06-06
[QUOTE=GarethMB]Canonical won't pay for the license to include mp3 support because they support open software.[/QUOTE]

So are we to understand that MEPIS and PCLINUXOS don't support free software? Is Knoppix a hybrid FOS/proprietary software mutant anomaly?

---

### Post by curuxz on 2006-06-06
No there is some confusion here because of your choice of distro's. Mepis duno about, pclinuxos have paid and knoppix is made outside the US so they dont have to pay, but technicaly that makes use of knoppix mp3's inside of america illegal

---

### Post by awakatanka on 2006-06-06
If the dev people of that distro make it outside the US they don't have to follow US law's, Almost every other country has no problem with it. Those distro's leave US people decide if they install it illegal our not. They think those people can think for them self and know what is illegal our not in there country's.

They don't nurse there userbase.

---

### Post by frodon on 2006-06-06
Mp3 support is free but not open source and ubuntu choose to not include any non open-source software by default (with some exeptions however) but Mp3 support and other codecs are easy to install and there are nice guides on the wiki for that.
As for MEPIS and KNOPPIX they just make another choice, they prefer to provide a default install which allow the users to read most of popular audio/video formats.

It's the explanation in my opinion.

---

### Post by helpme on 2006-06-06
[QUOTE=frodon]Mp3 support is free but not open source and ubuntu choose to not include any non open-source software by default (with some exeptions however) but Mp3 support and other codecs are easy to install and there are nice guides on the wiki for that.
As for MEPIS and KNOPPIX they just make another choice, they prefer to provide a default install which allow the users to read most of popular audio/video formats.

It's the explanation in my opinion.[/QUOTE]
No, mp3 support is opensource, that is, you can get the source code of mad, lame, the gstreamer stuff from fluendo.
The problem is entirely a legal one as there a patents on mp3 that also are actively enforced, though not against individuals using free mp3 decoders.
[http://en.wikipedia.org/wiki/Mp3#Licensing_and_patent_issues](http://en.wikipedia.org/wiki/Mp3#Licensing_and_patent_issues)

---

### Post by frodon on 2006-06-06
helpme, i'm sure you understood what i mean, MP3 algorythm is proprietary (it's written in the link you gave).

---

### Post by helpme on 2006-06-06
[QUOTE=frodon]helpme, i'm sure you understood what i mean, MP3 algorythm is proprietary (it's written in the link you gave).[/QUOTE]
It's patent encumbered, exactly, but the actual decoders are still open source.

And no, I did not know what you meant. I simply did understand what you wrote differently from what you seem to have meant.

P.S.: I don't know what the hell I did to you that you expect me to somehow intentionally misunderstand you just to disagree with you, however, I find the accusation childish and insulting.

---

### Post by Jucato on 2006-06-06
(EDITED POST) Hmm... So let me get this straight. the MP3 algorithm is propriety, that's why you need to buy a license in order to distribute and/or sell encoders/decoders in countries that acknowledge/support software patents? But:

PCLinuxOS, and probably all the other big distros like Red Hat/Fedora, SuSE, etc., have paid for the license?
KNOPPIX (and probably Kanotix as well) is German based, so is not affected by the licensing issues?
MEPIS, we actually don't really know how they do it? :D

Also that, according to the wiki link, the license holders rarely enforce the patents on open source projects?

I guess Ubuntu could support MP3's out of the box as well, if they wanted to, since the main office is located on the Isle of Man, right? But then of course it would go against their commitment to Free/Open Source Software.

I wonder if other distros that have MP3 support out of the box also bought the license and/or just make the distro outside of the U.S. But then what about U.S. based mirrors of the repositories, where you could download MP3 encoders/decoders? Wouldn't that be considered a form of distribution, putting them in trouble with the law?

---

### Post by egon spengler on 2006-06-06
[QUOTE=awakatanka]Those distro's leave US people decide if they install it illegal our not. They think those people can think for them self and know what is illegal our not in there country's.

They don't nurse there userbase.[/QUOTE]

ubuntu also leave the people to think for themselves and decide whether or not they install software that could be illegal in their country, so what's yor point?

Isn't it more nursing to do everything for someone?

---

### Post by frodon on 2006-06-06
[QUOTE=Fenyx]
PCLinuxOS, and probably all the other big distros like Red Hat/Fedora, SuSE, etc., have paid for the license.
KNOPPIX (and probably Kanotix as well) is German based, so is not affected by the licensing issues.[/QUOTE]Didn't know that, thanks for sharing, the KNOPPIX live CD is so useful i wouldn't live without now :mrgreen:

---

### Post by Jucato on 2006-06-06
EDIT: Sorry for the double posting... my connection messed up :(

@frodon: Maybe I should have reworded my statements. I wasn't stating facts. Those were statements that needed clarfications. Sorry about that... :(

---

### Post by helpme on 2006-06-06
[QUOTE=Fenyx]
PCLinuxOS, and probably all the other big distros like Red Hat/Fedora, SuSE, etc., have paid for the license.
KNOPPIX (and probably Kanotix as well) is German based, so is not affected by the licensing issues.
MEPIS, we actually don't really know how they do it? :D
...
I wonder if other distros that have MP3 support out of the box also bought the license and/or just make the distro outside of the U.S. But then what about U.S. based mirrors of the repositories, where you could download MP3 encoders/decoders? Wouldn't that be considered a form of distribution, putting them in trouble with the law?[/QUOTE]
AFAIK both Suse and Fedora don't come with mp3 playback.
Also, I think the main problem is that it's a legal grey area, so many distros choose the safe route of not including mp3 playback by default.

P.S.:
One interesting development is fluendo recently licensing mp3 and making it available free of charge and that's also allowing distros to redistribute it free of charge (though this of course still does not make it free software in the freedom kind of sense):
> The redistribution contract
 Any distribution or Unix maker out there who want to include the Fluendo MP3 plug-in with their distribution can do so by just signing a contract with Fluendo to become an official redistributor. This contract includes no monetary compensation to Fluendo for getting the right to redistribute the Fluendo MP3 plug-in and no demands of additional purchases from Fluendo. The main purpose of the contract is to satisfy our upstream contractual requirements. By signing this contract any distribution can support mp3 out of the box without any additional license fee. Take a look at the example contract and contact us at  [email]info@fluendo.com[/email] for details.
[http://www.fluendo.com/resources/fluendo_mp3.php](http://www.fluendo.com/resources/fluendo_mp3.php)

---

### Post by nocturn on 2006-06-06
[QUOTE=Fenyx]Let me state the question in full:
How come MEPIS, PCLinuxOS, KNOPPIX, and other "free" distros can support MP3 playback out of the box, while Ubuntu, for legal reasons, can't?

I'm just perplexed by it. It's more of a question about the legal issues concerned, rather than Ubuntu's commitment to free software.

Is it because MEPIS et al are just playing hooky, trying to get away with what they can? Surely there must be a reason.[/QUOTE]

They can't, but most of them are guessing that they are small enough not to get sued.  
Given the DMCA, it is a big risk to take, even for the devs personally.

---

### Post by nocturn on 2006-06-06
Just a quick point to make.  The MP3 format is only encumbered by one or more patents, which are currently only valid in the US AFAIK. Users in countries that do not (yet) allow software patents (like the EU member states) are in the clear.

It's not a copyright issue.

---

### Post by bruce89 on 2006-06-06
Linux distros shouldn't support MP3, as it means that open formats won't go anywhere.  If Ubuntu supported MP3 out the box, people would use that instead of Vorbis (which is much better quality anyway).

---

### Post by nocturn on 2006-06-06
[QUOTE=bruce89]Linux distros shouldn't support MP3, as it means that open formats won't go anywhere.  If Ubuntu supported MP3 out the box, people would use that instead of Vorbis (which is much better quality anyway).[/QUOTE]


That's partly true, but in my country, MP3 is a free format though.

---

### Post by bruce89 on 2006-06-06
[QUOTE=nocturn]That's partly true, but in my country, MP3 is a free format though.[/QUOTE]
Same here, (I think) although I don't really need to (except podcasts).  I wish podcasts were in Vorbis.

---

### Post by curuxz on 2006-06-06
[QUOTE=bruce89]Linux distros shouldn't support MP3, as it means that open formats won't go anywhere.  If Ubuntu supported MP3 out the box, people would use that instead of Vorbis (which is much better quality anyway).[/QUOTE]

I agree, Im currently doing a long and mass process of converting around 30 gig of my muisc to OGG, to phase out all mp3 music. 

Mp3 is not a good format its old and stale. we want OGG and open source and I really wish there was not such a backlash from the new uers asking for mp3's all the time or complaining about. Not saying anyone is this thread IS but that it does happen alot and is like complaining that we dont run exe's in linux its not our format and its not our fault! lol

---

### Post by Jucato on 2006-06-06
MP3 is also a free format, too, AFAIK.
Though I would like to really use open formats 100%, it's not really 100% possible because the MP3 is too famous, to the point that some people don't want to use anything else. While I have no problem with playing OGG on my PC and mobile device, I can't force other people to do the same, especially if their device does not support it (talking about some MP3/MP4 players).

Btw, I think most Linux/Open Source oriented podcasts usually have OGG alternatives available for download, too.

EDIT: I'm also in the process of converting my MP3 collection into OGG. I'm not picky about some quality loss anyway, so straight MP3-OGG conversion is fine by me.

---

### Post by curuxz on 2006-06-06
[QUOTE=Fenyx]EDIT: I'm also in the process of converting my MP3 collection into OGG. I'm not picky about some quality loss anyway, so straight MP3-OGG conversion is fine by me.[/QUOTE]

Quality loss WTF? Should that not be the other way around as ogg tends to get better encoding rates, certainly sounds better on my sound system.

I think in the same way others offer mp3 only we should offer ogg only not give people a choice, because if we do there is no reason to use ogg for alot of people. Any content made by the open source community should be made for the open source community and IMHO that means pure OGG no mp3 versions since its easyer for them to use ogg than us to use mp3

---

### Post by Michael_aust on 2006-06-06
To change th whole issue of mp3 and openformats people need to stop buying Ipods and other audio players that do not include support for OGG.  So this means rather then going out and buying a 20gb creative zen for £150 you should go out and buy a 1gb iaudio for £150.  By not purchasing auido players who only support aac, mp3 and wma you are making a difference.  Saying that distros should not support mp3 at all wont do a thing.  Firstly it will just make people less likely to use it and secondly hardware manufacturers dont care about Linux.  Come on they barly care about Apple macs.  Look at the hoops you have to run through to get a creative zen to work on Linux or an Ipod.

The hardware manufacturrs are the ones who need to be pressured into supporting other formats.  You may have to spend alot more for a product that support ogg yet does not offer the storage capacity of one that does not support ogg.  However you are making s stand.

---

### Post by matthew on 2006-06-06
[quote=helpme]P.S.: I don't know what the hell I did to you that you expect me to somehow intentionally misunderstand you just to disagree with you, however, I find the accusation childish and insulting.[/quote]Somehow I don't find posting in a rude and insulting manner any less childish and insulting than you are accusing Frodon of being. Seriously, use private messaging or post in the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123") if you have a problem with a staff member. I'm posting this publicly to send this same message to everyone who is reading the posts in this thread, not just you.

Now, back to the topic at hand.

---

### Post by curuxz on 2006-06-06
Im not saying distro's should not support MP3 i am saying content providers that are pro-opensource should not support mp3 and stop releasing content in mp3 format, if they change then you will get people needing ogg more.

---

### Post by helpme on 2006-06-06
[QUOTE=matthew]Somehow I don't find posting in a rude and insulting manner any less childish and insulting than you are accusing Frodon of being. 
[/QUOTE]
Ah, of course it was me who was rude and insulting, not the moderator. As we all know, on this forum mods never make mistakes and by definition they don't insult others. So, where exactly was I rude and insulting? Was it calling accusing someone of intentionally misunderanding something insulting and childish, or was it the misconception I operated under that disagreeing with a post by a member of the forum staff somehow was within the rules and pointing out that mp3decoders are indeed open source?

[QUOTE=matthew]
Seriously, use private messaging or post in the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123") if you have a problem with a staff member. 
[/QUOTE]
Seriously, if you have a problem with me, send me a private message, but don't publicly slam me. 

[QUOTE=matthew]
I'm posting this publicly to send this same message to everyone who is reading the posts in this thread, not just you.
[/QUOTE]
I'm posting this publicly because you chose to publicly slam me, instead of sending me a pm and I certainly won't let this behaviour go unanswered publicly.

[QUOTE=matthew]
Now, back to the topic at hand.[/QUOTE]
Agreed.

---

### Post by RAV TUX on 2006-06-06
[quote=Fenyx](EDITED POST)
KNOPPIX (and probably Kanotix as well) is German based, so is not affected by the licensing issues?
MEPIS, we actually don't really know how they do it? :D

[/quote] 
Mepis was based atleast partially on Knoppix.

If you want a refined version of Mepis go with Knoppix or Morphix([B]Morphix is derived from [Debian]("http://www.morphix.org/wiki/index.php/Debian") Linux and [Knoppix]("http://www.morphix.org/wiki/index.php/Knoppix")!).
[http://www.knoppix.org/](http://www.knoppix.org/)
[http://www.morphix.org/](http://www.morphix.org/)

A even more refined Distro would be Dreamlinux.
[/B][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]"Dreamlinux is based on Debian and Morphix, which means it takes advantages of their best features and adds its own modern development tools"
[http://www.dreamlinux.com.br/english/index.html](http://www.dreamlinux.com.br/english/index.html)
[/SIZE][/FONT]

---

### Post by matthew on 2006-06-06
[quote=yozef]Mepis was based atleast partially on Knoppix.[/quote]Formerly, it's now based on Ubuntu. From [Wikipedia]("http://en.wikipedia.org/wiki/Mepis"):
> As of June 2006, MEPIS has shifted from being Debian-based to [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_Linux")-based (which is also based on Debian).

---

### Post by RAV TUX on 2006-06-06
[quote=matthew]Formerly, it's now based on Ubuntu. From [Wikipedia]("http://en.wikipedia.org/wiki/Mepis"):[/quote] 
yes, this is why I stated "was based".

[quote=yozef]Mepis [COLOR=Red]**was based**[/COLOR] atleast partially on Knoppix.

If you want a refined version of Mepis go with Knoppix or Morphix([B]Morphix is derived from [Debian]("http://www.morphix.org/wiki/index.php/Debian") Linux and [Knoppix]("http://www.morphix.org/wiki/index.php/Knoppix")!).
[http://www.knoppix.org/]("http://www.knoppix.org/")
[http://www.morphix.org/]("http://www.morphix.org/")

A even more refined Distro would be Dreamlinux.
[/B][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]"Dreamlinux is based on Debian and Morphix, which means it takes advantages of their best features and adds its own modern development tools"
[http://www.dreamlinux.com.br/english/index.html]("http://www.dreamlinux.com.br/english/index.html")
[/SIZE][/FONT][/quote] 
[B]...of course this goes without saying that Ubuntu is still the very best in FREEDOM of CHOICE, I personally prefer not to have a out-the-box prebundled Linux Distro and enjoy my freedom to enable what I choose from multiverse, Universe or other.

This is why I choose Ubuntu over SUSE last year.
[/B]

---

### Post by aysiu on 2006-06-06
[QUOTE=curuxz]I agree, Im currently doing a long and mass process of converting around 30 gig of my muisc to OGG, to phase out all mp3 music.[/QUOTE] Why is it long? Isn't there some command-line utility in the repositories that can mass-convert them all with a single command? Poke around in Synaptic and see.

**Edit** Try [making sure you have extra repositories enabled](http://www.psychocats.net/ubuntu/sources) and then ```
sudo aptitude update
sudo aptitude install mp32ogg
``` Here's the *man* file: ```
MP32OGG(1)                                                          MP32OGG(1)

NAME
       mp32ogg - Convert MP3 to Ogg Vorbis

SYNOPSIS
       mp32ogg [options] files directories...

DESCRIPTION
       This  manual  page  documents briefly the mp32ogg command.  This manual
       page was written for the Debian distribution because the original  pro&#8208;
       gram does not have a manual page.

       mp32ogg  is  a  program  that converts MP3 files and directories to Ogg
       Vorbis.

OPTIONS
       These programs follow the usual GNU  command  line  syntax,  with  long
       options  starting  with  two  dashes  (&#8216;-&#8217;).   A  summary of options is
       included below.

       -h, --help
              Show summary of options.
       --delete
              Delete files after converting

       --rename=format
              Instead of simply replacing the .mp3 with .ogg  for  the  output
              file,  produce output filenames in this format, replacing %a, %t
              and %l with artist, title, and album name for the track

       --lowercase
              Force lowercase filenames when using --rename

       --verbose
              Verbose output

       --preserve-timestamp
              Preserve file timestamp

SEE ALSO
       oggenc(1),

AUTHOR
       This manual page was written by Julien  Danjou  <acid@debian.org>,  for
       the Debian GNU/Linux system (but may be used by others).

                                August 28, 2002                     MP32OGG(1)
```

---

### Post by matthew on 2006-06-06
[quote=yozef]yes, this is why I stated "was based".[/quote]Sorry if you felt threatened/insulted. I was just trying to be informative, nothing else. :)

---

### Post by curuxz on 2006-06-06
[QUOTE=aysiu]Why is it long? Isn't there some command-line utility in the repositories that can mass-convert them all with a single command? Poke around in Synaptic and see.[/QUOTE]

Im sure there is but Im doing it kinda ad-hoc, all my music is spread across my computers I keep meaning to do a massive file clean up and sort through, maybe ill get around to it tonight.](*,)

---

### Post by aysiu on 2006-06-06
[QUOTE=curuxz]Im sure there is but Im doing it kinda ad-hoc, all my music is spread across my computers I keep meaning to do a massive file clean up and sort through, maybe ill get around to it tonight.](*,)[/QUOTE] Take a look at my last post--I edited it with more details.

---

### Post by RAV TUX on 2006-06-06
[quote=matthew]Sorry if you felt threatened/insulted. I was just trying to be informative, nothing else. :)[/quote]

No worries Matthew. I neither felt threatened or insulted. I was just clarifying my post and stance.:p

Thanks for the follow-up post.

---

### Post by curuxz on 2006-06-06
[QUOTE=aysiu]Take a look at my last post--I edited it with more details.[/QUOTE]

Thanks aysiu for taking the time to post detailed information, ill probs do my big clean out later, see if i can get an mp3 free system ;)

---

### Post by RAV TUX on 2006-06-06
[quote=curuxz]Thanks aysiu for taking the time to post detailed information, ill probs do my big clean out later, see if i can get an mp3 free system ;)[/quote]

Gmusicbrowser would be a great utility to use.

---

### Post by Lord Illidan on 2006-06-06
It's all very well to say that we should all use OGG instead of mp3, but what happens if you have a portable media player that can't play them, as in my case? I don't want to dump my Zen Micro just because it can't play ogg files.

Otherwise, yes, I would use ogg files. But until they become more supported, I am stuck to using mp3.

Still, it is nice to see that many commerial games are also using ogg, like UT 2004, Praetorians and Battle Engine Aquila. A step forward, imho.

About Mepis, PCLOS... I think it is a bold move on their path. Consumers should be given a **choice** not limited to just ogg. Especially when the consumers don't know how to stay installing the extra codecs etc.

Ubuntu's stance is not bad, though. One can install the gstreamer-ugly codecs. However, in SUSE's case, the entire applications are crippled, which I hate. And Fedora is also heavy handed about mp3 support.

---

### Post by prizrak on 2006-06-06
Converting one compressed format into another is definetly going to result in quality loss. OGG support isn't nearly as great as MP3 support. For instance I have an iRiver that can do both, however alot of times when I use an ogg I get the "Not supported ogg format" message (normally happens when it's a VBR) and then I have to find out which file it is and go and recode it and all that fun stuff. No such thing with MP3 files. 

There is also an issue of DRM, Ogg cannot be DRM'ed but MP3 can, which means that content providers will not want to use OGG's. You can refuse to buy devices that don't support OGG's all you want but if no one sells OGG's it will make no difference.

---

### Post by Brunellus on 2006-06-06
@Lord Illidian:  In that case, what you do is vote with your wallet and buy ogg-supporting hardware.  I do.

---

### Post by Jucato on 2006-06-06
@yozef: thanks for the suggestions. But I wasn't really looking for a replacement to Ubuntu/Kubuntu. (I have to disagree a bit on KNOPPIX being more refined that MEPIS, though :D)

I was just really puzzled how smaller distros (at least smaller in financial status as compared to RH/Fedora, SUSE, Linspire) are able to ship with built in MP3 support, without getting into any legal troubles.

Still, I like that fact that in Ubuntu, I have the choice/power to install mp3 support if and when I want to. It gives me a chance to make an informed decision, or in the very least it informs me about the issues surrounding mp3s.

@aysiu: thanks for that info! I though I would have to do multiple OGG exports in Audacity till the day I die. :D

@prizrak: that's was the "quality loss" I was talking about, although the loss is not really that noticeable to the untrained (meaning, my) ear. Unfortunately, I have no other choice but to really convert (Don't have the raw formats/source with me). OGG is really a good alternative to MP3. Too bad, though, that DRM, one of the banes of FLOSS, is again responsible for stunting the growth of open formats.

@Brunellus: ideally that would be the best thing to do. I'm glad my mobile device is capable of playing open formats. Unfortunately, if you are one of those people who have no issues with sharing music with acquaintances who might not have OGG-capable devices, having OGG-only media will be a bit of a problem.

---

### Post by aysiu on 2006-06-06
[QUOTE=Fenyx]
@aysiu: thanks for that info! I though I would have to do multiple OGG exports in Audacity till the day I die. :D[/QUOTE] I did a test run to make sure it works, and to show you how to do it: ```
username@ubuntu:~$ **sudo aptitude update && sudo aptitude install mp32ogg**
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:4 http://security.ubuntu.com dapper-security Release [19.6kB]
Get:5 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Get:6 http://archive.ubuntu.com dapper-updates Release [27.0kB]
Get:7 http://security.ubuntu.com dapper-security/main Packages [14B]
Get:8 http://archive.ubuntu.com dapper-backports Release [19.6kB]
Get:9 http://security.ubuntu.com dapper-security/restricted Packages [14B]
Get:10 http://security.ubuntu.com dapper-security/main Sources [14B]
Get:11 http://security.ubuntu.com dapper-security/restricted Sources [14B]
Get:12 http://security.ubuntu.com dapper-security/universe Packages [14B]
Get:13 http://security.ubuntu.com dapper-security/universe Sources [14B]
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Get:14 http://archive.ubuntu.com dapper-updates/main Packages [10.2kB]
Get:15 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:16 http://archive.ubuntu.com dapper-updates/main Sources [4268B]
Get:17 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:18 http://archive.ubuntu.com dapper-backports/main Packages [14B]
Get:19 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:20 http://archive.ubuntu.com dapper-backports/universe Packages [14B]
Get:21 http://archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Fetched 81.5kB in 2s (40.2kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  libmp3-info-perl libstring-shellquote-perl mpg321
The following NEW packages will be installed:
  libmp3-info-perl libstring-shellquote-perl mp32ogg mpg321
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 93.3kB of archives. After unpacking 422kB will be used.
Do you want to continue? [Y/n/?] **y**
Writing extended state information... Done
Get:1 http://archive.ubuntu.com dapper/universe libmp3-info-perl 1.13-1 [37.3kB]
Get:2 http://archive.ubuntu.com dapper/universe libstring-shellquote-perl 1.03-1  [14.0kB]
Get:3 http://archive.ubuntu.com dapper/universe mpg321 0.2.10.3 [34.5kB]
Get:4 http://archive.ubuntu.com dapper/universe mp32ogg 0.11-6 [7462B]
Fetched 93.3kB in 1s (72.9kB/s)
Selecting previously deselected package libmp3-info-perl.
(Reading database ... 110384 files and directories currently installed.)
Unpacking libmp3-info-perl (from .../libmp3-info-perl_1.13-1_all.deb) ...
Selecting previously deselected package libstring-shellquote-perl.
Unpacking libstring-shellquote-perl (from .../libstring-shellquote-perl_1.03-1_a ll.deb) ...
Selecting previously deselected package mpg321.
Unpacking mpg321 (from .../mpg321_0.2.10.3_i386.deb) ...
Selecting previously deselected package mp32ogg.
Unpacking mp32ogg (from .../mp32ogg_0.11-6_all.deb) ...
Setting up libmp3-info-perl (1.13-1) ...
Setting up libstring-shellquote-perl (1.03-1) ...
Setting up mpg321 (0.2.10.3) ...

Setting up mp32ogg (0.11-6) ...
username@ubuntu:~$ **cd Desktop/mp3s/**
username@ubuntu:~/Desktop/mp3s$ **mp32ogg --verbose *.mp3**
mp32ogg v0.11
(c) 2000-2002 Nathan Walp
Released without warranty under the terms of the Artistic License

Converting 10,000 Maniacs - Can't Ignore The Train (Demo).mp3 to OGG...
Length: 02:52           Freq: 44.1 kHz
MP3 Bitrate: 128        OGG Quality Level: 5
 Artist: 10,000 Maniacs
  Album:
  Title: Can't Ignore The Train (Demo)
   Year: 2004
  Genre: Rock/Pop
Track #:
Comment: 000011B4 00000626 0000A94B 00005158 00020249 0000682F 00007874 000077F3  00018514 00021F0F
10,000 Maniacs - Can't Ignore The Train (Demo).ogg done!
Converting 3 Doors Down - The Road I'm On.mp3 to OGG...
Length: 03:58           Freq: 44.1 kHz
MP3 Bitrate: 128        OGG Quality Level: 5
 Artist: 3 Doors Down
  Album:
  Title: The Road I'm On
   Year: 2003
  Genre: Rock/Pop
Track #:
Comment: 000020FC 00000F60 00013CB2 00006094 0000CF8D 00022B00 00008AE5 00008D14 0000D043 0000D043
3 Doors Down - The Road I'm On.ogg done!
Converting 5ive-0 - Out for Just Us.mp3 to OGG...
Length: 03:10           Freq: 44.1 kHz
MP3 Bitrate: 96 OGG Quality Level: 5
 Artist: 5ive-0
  Album:
  Title: Out for Just Us
   Year:
  Genre: Rap
Track #:
Comment: 00000883 000005B4 0000209B 00000EF4 0002BF37 000186A0 00008000 00008000 0001FBD0 0001FBD0
5ive-0 - Out for Just Us.ogg done!
username@ubuntu:~/Desktop/mp3s$
``` The first time you do it, you might want to run the *--verbose* option as I did in this example. Once you're content with the results, you can substitute in the *--delete* option, which will delete the MP3 after the conversion.

---

### Post by Jucato on 2006-06-06
Thanks! That was very, very kind of you to test it out for us to see. You are by far my favorite Ubunter (if there's such a word :D)! :D

This sure beats the hell out of any GUI. In Audacity, you'd have to import different MP3s as separate tracks, then export multiple each track into OGG. Both importing and exporting takes a whole lot of time, specially if you process lots of MP3s.

Btw, off-topic: I see you're using aptitude. Is it really a whole lot better than apt?

---

### Post by Iandefor on 2006-06-06
[quote=Fenyx]Thanks! That was very, very kind of you to test it out for us to see. You are by far my favorite Ubunter (if there's such a word :D)![/quote] I prefer the term Ubuntista.

---

### Post by John.Michael.Kane on 2006-06-06
:rolleyes:

---

### Post by aysiu on 2006-06-06
[QUOTE=Fenyx]
Btw, off-topic: I see you're using aptitude. Is it really a whole lot better than apt?[/QUOTE] I'll show you the difference. Here's installing and removing *mp32ogg* with *aptitude* ```
username@ubuntu:~$ **sudo aptitude update && sudo aptitude install mp32ogg**
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Get:4 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Fetched 4B in 1s (2B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  libmp3-info-perl libstring-shellquote-perl mpg321
The following NEW packages will be installed:
  libmp3-info-perl libstring-shellquote-perl mp32ogg mpg321
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/93.3kB of archives. After unpacking 422kB will be used.
Do you want to continue? [Y/n/?] **y**
Writing extended state information... Done
Selecting previously deselected package libmp3-info-perl.
(Reading database ... 110384 files and directories currently installed.)
Unpacking libmp3-info-perl (from .../libmp3-info-perl_1.13-1_all.deb) ...
Selecting previously deselected package libstring-shellquote-perl.
Unpacking libstring-shellquote-perl (from .../libstring-shellquote-perl_1.03-1_all.deb) ...
Selecting previously deselected package mpg321.
Unpacking mpg321 (from .../mpg321_0.2.10.3_i386.deb) ...
Selecting previously deselected package mp32ogg.
Unpacking mp32ogg (from .../mp32ogg_0.11-6_all.deb) ...
Setting up libmp3-info-perl (1.13-1) ...
Setting up libstring-shellquote-perl (1.03-1) ...
Setting up mpg321 (0.2.10.3) ...

Setting up mp32ogg (0.11-6) ...
username@ubuntu:~$ **sudo aptitude remove mp32ogg**
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  libmp3-info-perl libstring-shellquote-perl mpg321
The following packages will be REMOVED:
  mp32ogg
0 packages upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 422kB will be freed.
Do you want to continue? [Y/n/?] **y**
Writing extended state information... Done
(Reading database ... 110426 files and directories currently installed.)
Removing mp32ogg ...
Removing libmp3-info-perl ...
Removing libstring-shellquote-perl ...
Removing mpg321 ...
username@ubuntu:~$
``` Here's installing and removing *mp32ogg* with *apt-get*: ```
username@ubuntu:~$ **sudo apt-get update && sudo apt-get install mp32ogg**
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Get:4 http://security.ubuntu.com dapper-security Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Fetched 4B in 3s (1B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libmp3-info-perl libstring-shellquote-perl mpg321
The following NEW packages will be installed:
  libmp3-info-perl libstring-shellquote-perl mp32ogg mpg321
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/93.3kB of archives.
After unpacking 422kB of additional disk space will be used.
Do you want to continue [Y/n]? **y**
Selecting previously deselected package libmp3-info-perl.
(Reading database ... 110384 files and directories currently installed.)
Unpacking libmp3-info-perl (from .../libmp3-info-perl_1.13-1_all.deb) ...
Selecting previously deselected package libstring-shellquote-perl.
Unpacking libstring-shellquote-perl (from .../libstring-shellquote-perl_1.03-1_all.deb) ...
Selecting previously deselected package mpg321.
Unpacking mpg321 (from .../mpg321_0.2.10.3_i386.deb) ...
Selecting previously deselected package mp32ogg.
Unpacking mp32ogg (from .../mp32ogg_0.11-6_all.deb) ...
Setting up libmp3-info-perl (1.13-1) ...
Setting up libstring-shellquote-perl (1.03-1) ...
Setting up mpg321 (0.2.10.3) ...

Setting up mp32ogg (0.11-6) ...
username@ubuntu:~$ **sudo apt-get remove mp32ogg**
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  mp32ogg
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 65.5kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 110426 files and directories currently installed.)
Removing mp32ogg ...
username@ubuntu:~$  
``` Notice how *aptitude* got all the crud out there when it removes mp32ogg and how *apt-get* left all the crud in there?

---

### Post by Jucato on 2006-06-06
Yes. That's very nice. Now if only we used aptitude more than apt-get. Oh well, a new set of CLI commands to learn! :D

---

### Post by aysiu on 2006-06-06
[QUOTE=Fenyx]Yes. That's very nice. Now if only we used aptitude more than apt-get. Oh well, a new set of CLI commands to learn! :D[/QUOTE] I'm trying to get people to do so.

After all we do get two very popular questions that wouldn't exist if people used *aptitude* all the time:

1. How do I get rid of all the dependencies that came with applications I've uninstalled? *gtkorphan* is an annoying last resort... or it should be.

2. How do I remove Gnome or KDE after I've used *apt-get* or Synaptic to install it?

---

