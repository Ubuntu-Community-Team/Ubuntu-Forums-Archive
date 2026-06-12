---
title: "Any distribution that includes a pile of the non-free software?"
date: 2005-03-01
forum: The Cafe
---

### Post by brewsterkahle on 2005-03-01
I was hoping that this distribution would work for my home use (kids, spouse, me).   But it does not have mp3 or flash support, and I am now imagining that it does not have lots of other useful things.   

I respect the "dont want to have anything non-free" in the distribution, but the directions on how to get non-free stuff was obscure and trying to follow them is klunky.    Lindows click-and-run, while buggy, seems to be going in a useful direction.

I was wondering if anyone has made a distribution CD of a full set of software to make a desktop computer for home use.

-brewster
[email]brewster@archive.org[/email]

---

### Post by jdodson on 2005-03-01
[QUOTE=brewsterkahle]I was hoping that this distribution would work for my home use (kids, spouse, me).   But it does not have mp3 or flash support, and I am now imagining that it does not have lots of other useful things.   

I respect the "dont want to have anything non-free" in the distribution, but the directions on how to get non-free stuff was obscure and trying to follow them is klunky.    Lindows click-and-run, while buggy, seems to be going in a useful direction.

I was wondering if anyone has made a distribution CD of a full set of software to make a desktop computer for home use.

-brewster
[email]brewster@archive.org[/email][/QUOTE]

read this guide, it will help you solve your problem(s): [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

ubuntu does not put mp3 or flash on the main cd.  they have both of those in the repositories you can easily download.  i would recommend using ogg as a music file format, it is better quality than a mp3 and works with all gnu/linux distros that have a music player.

ubuntu has support for many useful things.  just because it does not have mp3 or flash on the main cd does not mean it does not have support for "lots of other useful things," that does not logically follow anyway.  if you respected the "non-free" stance then you know what you sign up for.  where as it might be a slight bit terse at times to install the software, that is what we are left with.  i am not trying to be an ass or anything, but if adding a line of a repository is tough then ubuntu might not be for you.

---

### Post by DarkSilver on 2005-03-01
The fact is ubuntu say "distribution that just work"
it's wrong !!!

because of license , etc.. mp3, flash are not playable by default

I think it can be great if at the first launching there is screen : " Do you want to install non-free software until there is a free alternative to use your desktop computer at 100% ?"
and it install flash, mp3 player, and all the non-free stuff we all install !!!

It's really stupid : 99% of all users install these softwares..
at every instalation, you have to install them manually each time !

so, ok, don't put them in the default installation to stay a free distro, but let user to install them very easily (i mean : one click, and that's it)


EDIT : 
I can add : Java, NVidia Driver too...
if the java license is shown and accepted by the user, where is the problem ??
it is non-free, ok, but if users want it.. he can
if he accepts the license, he can use java legally...

---

### Post by nikopol on 2005-03-01
[QUOTE=DarkSilver]The fact is ubuntu say "distribution that just work"
it's wrong !!!

because of license , etc.. mp3, flash are not playable by default[/QUOTE]

To a large extent no OS  "just works" - Windows doesn't come with Enemy Territory pre-installed so to me it doesn't work! More seriously, it's only recently that mp3 support is part of  windows  and don't you have to download java, flash and realplayer for XP (I haven't used Windows in ages so I honestly am not sure)? How about the drivers for a lot of peripherals?

That said I think it would be cool to have a simple script that could or coult not be run to download and install RealPlayer, Skype, Flash and other proprietary software. But I fully accept that a lot of Linux users do no want to support proprietary software in any way,..

---

### Post by poofyhairguy on 2005-03-01
[QUOTE=DarkSilver]
so, ok, don't put them in the default installation to stay a free distro, but let user to install them very easily (i mean : one click, and that's it)
[/QUOTE]



Um...to me apt-get is miles easier than years of Windows installs (next, next, next, I agree, next, next, next, next, next, etc.) And unlike every OS I've tried that incorporates such things out of the box, on Ubuntu whenever I do it everything "just works." Mepis, Mandrake, and Knoppix are set up to play unfree files, but in every case when I used each OS there was some file that they wouldn't play perfectly. Something like quicktime or a rare Microsoft codec would mess it up, and I didn't know how to fix it (since I never installed the codecs in the first place).

My Gxine in Ubuntu plays every media file under the sun perfectly once its set-up. No OS I've ever used can claim that (not even XP). Sure...its a little pain to install those things but I like playing on my computer so I call that pain "fun."

There are hundreds of distros out there. If someone wants unfree media player support out of the box let them use an distro that includes it such as Mepis, Kanotix, etc. I'd rather the Ubuntu devs work on making a stable, useful Gnome distro than make it a little easier to install unfree stuff. Ubuntu is not going to be everything to everyone, especially someone that doesn't want to touch apt-get.

---

### Post by DarkSilver on 2005-03-01
I never say Windows "works" out of the box, i didn't talk about windows..
windows doesn't work at all out of the box (you have to install ALL the software, codec, etc..)
that's not the problem, i'm talking just about ubuntu

Did you count how many posts there was about codec, softs like skype etc... ?
they all refer to ubuntuguide

tell me what is the difference between:
1/ don't mention non-free software, lost a lot of time for answering all the same questions about these packages in forum, wiki, mailing-list, and refer to ubuntuguide

2/ put a script that the ones who wants can launch in one click and install everything with the good parameters ?

At the end, 1/ and 2/, the 99% of users will have Java, skype, flash, etc....
but the 1/ is longer, take many times to ubuntu addict to learn to newbies, etc...
Is there one of you who have no non-free packages ? java, nvidia, skype, w32codecs, etc... ?

another point is :
I always find totally stupid to make something by default if everyone change it just after install
there are some software, EVERYONE change one option by example. Even the official website of the soft tells to change this option in some case.... but why not put it by default 
??
well, it is another  discussion....

---

### Post by jdong on 2005-03-01
Umm, laws prohibit distributors like Canonical from packaging certain stuff, like Java or codecs.


Third party repositories, like Marillat, can cause problems with APT -- failed dependencies, whole system breakage, etc. Canonical won't put something in the distro by default that can harm the quality of its distribution...


As far as a script, that'd show that Canonical *endorses* illegal activities. If you were a medication maker, would you put in a label showing how to kill people through overdosing? Probably not.

---

### Post by Jad on 2005-03-01
apt is just great, but it would be great if it can work like 
apt-get transfer $1000000 :-)

> 
jdong
As far as a script, that'd show that Canonical endorses illegal activities. If you were a medication maker, would you put in a label showing how to kill people through overdosing? Probably not.
agreed

---

### Post by Dylanby on 2005-03-01
Canonical is aiming for the corporate desktop as well as the "free" desktop, which is why you'll never find legally questionable stuff in the main repos.

And you can't expect them to officially support all of Debian's packages either.

People who complain about spending five minutes adding mp3, Flash, Java, etc., should spend an extra fifteen minutes learning about GNU/Linux.

---

### Post by TravisNewman on 2005-03-01
No OS "just works" in all cases. However, you can't say that this is false because MP3 support, etc, doesn't come installed. Those are features you may want, but the OS DOES work without them. I wouldn't return a bike to the sporting goods store and say it doesn't work because it didn't come with a bookshelf. Maybe I am an avid reader and want a place to put my books when I ride my bike, and maybe I don't want to ride the bike until I install a bookshelf on it, but that doesn't mean the bike doesn't work.

Strange example I know.

The question I've always had is this: 
You can legally download java, flash, and mp3 support. Therefore, would it be legal if there was an install script that pulled the official binaries from the developers' websites, showed their licenses, and required you to agree with them before installing them? Because that would be handy.

---

### Post by bored2k on 2005-03-01
[QUOTE=Jad]apt is just great, but it would be great if it can work like 
apt-get transfer $1000000 :-)
[/QUOTE]

rofl lmao

---

### Post by nikopol on 2005-03-01
> **DarkSilver]I never say Windows "works" out of the box, i didn't talk about windows..
windows doesn't work at all out of the box (you have to install ALL the software, codec, etc..)
that's not the problem, i'm talking just about ubuntu[/quote]
Windows was just an example to aruge that the concept of "just works" is beyond vague. Nothing will ever just work for any requirement but as things go, Ubuntu comes as close to Just Working as any OS I've had to use (well Hoary does, I'm less sure about Warty  said:**
> Did you count how many posts there was about codec, softs like skype etc... ?
they all refer to ubuntuguide

tell me what is the difference between:
1/ don't mention non-free software, lost a lot of time for answering all the same questions about these packages in forum, wiki, mailing-list, and refer to ubuntuguide

2/ put a script that the ones who wants can launch in one click and install everything with the good parameters ?

At the end, 1/ and 2/, the 99% of users will have Java, skype, flash, etc....
but the 1/ is longer, take many times to ubuntu addict to learn to newbies, etc...
Is there one of you who have no non-free packages ? java, nvidia, skype, w32codecs, etc... ?
 hey I don't disagree with you there - see the last paragraph of my post.


> another point is :
I always find totally stupid to make something by default if everyone change it just after install
there are some software, EVERYONE change one option by example. Even the official website of the soft tells to change this option in some case.... but why not put it by default 
??
well, it is another  discussion....

What software are you referring to? The IPV6 problem? I think that's been resolved in Hoary...

---

### Post by KiwiNZ on 2005-03-01
This arguement about "non free" software, codecs, mp3 , flash blah blah blah comes up all the time. And becoming more so as new adventurers into the World of Linux make their first clumsy steps and leave the ever cuddling Windows behind them.

And I do not believe we do a very good job explaing why these things are not there. Remember in the windows world there is not the restrictions and free only has one meaning , that is zip , nada gratis .

We need to find a better way of explaining this situation other  than getting terse with these innocent Windows refugees.

---

### Post by nikopol on 2005-03-01
[QUOTE=jdong]As far as a script, that'd show that Canonical *endorses* illegal activities. If you were a medication maker, would you put in a label showing how to kill people through overdosing? Probably not.[/QUOTE]

Not so in all cases - you are legally allowed to download Java, Flash, Skype, RealPlayer and co. and install them. Surely it's not illegal to include a script that when run would allow the user to do that?

Some codecs, mp3 support, dvdCSS is an issue and I agree that Canonical can't be seen to be encouraging such activity but a script for the rest would be nice.

Oh and I'm not a windows refugee! I've been unders linux for over 6 years now. I just think Ubuntu is the most user friendly distro and thinking of how to get the resilient Windows users to give Linux a try...

---

### Post by poofyhairguy on 2005-03-01
[QUOTE=nikopol] I just think Ubuntu is the most user friendly distro and thinking of how to get the resilient Windows users to give Linux a try...[/QUOTE]

Set it up for them. That is what I do. For the interested I show them what I'm doing. Everything works that way.

---

### Post by nikopol on 2005-03-01
[QUOTE=poofyhairguy]Set it up for them. That is what I do. For the interested I show them what I'm doing. Everything works that way.[/QUOTE]

Well that's the option I usually take but consider it this way. My extended family lives a minimum of 2 hours drive away, my parents live 800 km away and most of my family live a ferry trip away. Not so easy to just check they've symbolically linked /dev/cdrom to /dev/hdc ;)

I think for Linux to make headways into the AverageUserGroup, it will have to be independent of the good will of Linuxer... Hence why I think the easier a non-guru can use it, the better. I mean there's lots to be said in favour of Linux in terms of usability (it's pretty cool telling them "from now on, you won't have to buy a single CD for any future program you want. Just search for it synaptic and install it from there.") and Project Utopia is splifftastic but I think that these can be moderate barriers that could frustrate the Mr(s). AverageUser. 

Now whether this is something we should be looking at now in Linux development or rather later is another issue and hopefully with a growing user base, these software manufacturers will start to see the light... After all, it's still being rumoured Java is going to be open-sourced soon so maybe that'll be one irritating obstacle out of the way :)

---

### Post by rapala61 on 2005-03-01
so far my experience with ubuntu is the best.  I struggled for a while at first, and sometimes i still do when i want some things to work the way i want them. The fact is that media support out of the box not even windows has it.  The problem is that people are so used to do things the windows way that they feel like in another planet when they try linux ( which actually is... just a better planet  :)  ) .. 

In windows is  Download the app-> Install-> use  
Linux way ( Ubuntu )  apt-get->configure-> use ( and that is just sometimes)

Its really the same thing, the difference is that Linux is really into letting you know what its doing , and what u want.. thats why u spend more time configuring stuff...

I admit that out of the box  media support could be really easy to inplement if the devs wanted it...   

for example: I have this idea.. and this came right after i embarrased myself posting in the ubuntu hoary dev forum about how to setup mozplugger. We have almost everything we need to have full media support when we first install ubuntu...  we are just missing 2 things:

1) downloading the w32codecs deb.
2) a script that would download/configure mozplugger to work with totem-xine , java , nvidia (depends on hardware ) ,etc.  

I dont believe w32codecs are illegal to install once the Ubuntu cd doesn't include it itself. and having this package is equal to support even more media than the average  windows user would need.

what u think about this???

---

### Post by Jesus Franco on 2005-03-01
Yes and add free pc upgrades aswell!  :D 

Comeon' people. Why dont you simply make a custom install cd. It isnt very hard. I am planning to do so once the final version of horay is out. Or even better make a disc image. And install from that instead of from the cd  #-o

---

### Post by rapala61 on 2005-03-01
[QUOTE=Jesus Franco]Yes and add free pc upgrades aswell!  :D 

Comeon' people. Why dont you simply make a custom install cd. It isnt very hard. I am planning to do so once the final version of horay is out. Or even better make a disc image. And install from that instead of from the cd  #-o[/QUOTE]

Well.. because the point is helping people that dont have a clue how to get mp3 files or quicktime movies to play under ubuntu... not sending them to build their own cd.

---

### Post by TravisNewman on 2005-03-02
I could go for something to make mozplugger work with xine/mplayer, etc. I have installed a basic LFS system, completely installed a gentoo system, taken a class on shell scripts, frequently compile software including dependency resolving, and other technically difficult things, but I just can't figure out mozplugger *L* And yes, I've read the docs on it.

---

### Post by rapala61 on 2005-03-02
i know enough to make my movies to play in totem embedded in mozilla.. but if u look at a post i made in the hoary dev forums... i learned all that today lol..  desperation can make u do things u never knew u were able to....

---

### Post by jdodson on 2005-03-02
ubuntu wants to encourage the use of free codecs and programs.  if ubuntu included a script to install non-free stuff, that is not really encouraging people.  they provide an adequate wiki and some community member provided an very ample ubuntu guide.   

if users are looking for something that barks, walks and works like windows, why switch?  just use windows.  gnu/linux is not a clone of windows people, it is a clone of unix.  not to say gnu/linux is not a nice operating system, i think it is a gift of art to mankind.  but ubuntu will NEVER, and i say never in caps because i have read much from the developers on this issue(check the ubuntu email list history) to include non-free software with the ubuntu main cd.  they do add the mad, flash, nvidia and ati proprietary software to the ubuntu repositiries already.  for that we should all be thankful, or not depending of if you are a free software purist or not.  the reason they can do that is because the license of the software in question allows them to.  now if the laws change or a particular codec becomes free, then they will.   as far as a script goes, personally i think pasting a few lines into apt-get is fine enough.  i don't think adding a script to the main cd is useful in the slightest.

like many have suggested on the forums.  people who don't know anything about computers should have a friend install gnu/linux for them.  it makes the transition easier until they learn howto do it on thier own.

and like i have stated a gazillion other times and i will stand by that statement, like many other in this thread:  ubuntu default install is WAY more functional than a windows xp default install.  just think about what ubuntu includes and what xp includes and i think you will realize that ubuntu kicks windows xps ass.  then when you enable universe you have GAZILLIONS of programs that are very functional and useful.  when you get on the windows site, what do you have to get that makes you more productive?  well media player, which is good.  movie maker, which is good.  updates to windows software, ok thats good.  any word processor?  nope.  how bout a image editing program to do cool stuff?  nope.  how bout some fun games?  nope.  how bout a spreadsheet program?  nope.  how bout a multi-functional-protocol instant messenger?  nope.  how bout multi-themes for desktop?  nope.  the list is endless my friends.

---

### Post by rapala61 on 2005-03-02
yep... we keep going in circles...  J my man, everything u said is 150% correct and i completely agree with that... but i have always though  that the " u dont want the linux way, stick with windows "  its not  usefull at all because thats really coming back to us u see. not that Linux is or is intented to be a windows clon ( Thanks God ) but we need to acknowledge that most new linux users are coming from windows... and to evade getting the forums crowded with questions like .. " hey , i cant listen to my mp3 cd, some1 help!!" , or " why cant i see my quicktime movies"  we need to make it simple and practical. For me.. the script idea is more to give people a choice to whether they want to do it themselves or just run a script.. not a big deal.. what u think. 

Newbies will eventually learn as they get more deep into Linux , but they dont need to be faced with these "problems" the first day they try playing around with Linux.

---

### Post by defkewl on 2005-03-02
Try Debian

---

### Post by jdodson on 2005-03-02
[QUOTE=rapala61]yep... we keep going in circles...  J my man, everything u said is 150% correct and i completely agree with that... but i have always though  that the " u dont want the linux way, stick with windows "  its not  usefull at all because thats really coming back to us u see. not that Linux is or is intented to be a windows clon ( Thanks God ) but we need to acknowledge that most new linux users are coming from windows... and to evade getting the forums crowded with questions like .. " hey , i cant listen to my mp3 cd, some1 help!!" , or " why cant i see my quicktime movies"  we need to make it simple and practical. For me.. the script idea is more to give people a choice to whether they want to do it themselves or just run a script.. not a big deal.. what u think. 

Newbies will eventually learn as they get more deep into Linux , but they dont need to be faced with these "problems" the first day they try playing around with Linux.[/QUOTE]


perhaps if there was something in the menu like "find outmore about ubuntu"  or some kind of readme file with some kind of visibility that is a html file or whatever that explains some things, that might help.  also i have heard, and it seems you mention some kinds of error messages if you tried to play a certain media file that told you why you could not play it.  that might be helpful too.

sorry about the circles thing, i do want ubuntu to be useful to people.  but it does seem like at times people are trying to clone windows.  perhaps this is not one of those times.  my goal is not to convert people, if windows suits certain users better then use windows.  

as far as the script idea, i think it has been suggested, however you can do more formally via the ubuntu mailing list.  you might want to check to see if it has already been nixed or oked by the devels.

---

### Post by neighborlee on 2005-03-02
[QUOTE=jdodson]
sorry about the circles thing, i do want ubuntu to be useful to people.  but it does seem like at times people are trying to clone windows.  perhaps this is not one of those times.  my goal is not to convert people, if windows suits certain users better then use windows.  

[/QUOTE]
===============
Im' glad we're having this discussion but want I"d like to suggest is a different 'mindset'.  Who said anything about converting anyone ? ;-)..

We all use linux because it IS everything we want including having a philosophy that doesn't leave anyone OUT of the loop, not to mention being stable and free of infectious critters.  I presonally find that if we BUILD an easy to use system ( there is nothing wrong with making linux 'easier' than windows just look at Linspires and say xandros goals/current systems ) and make the linux community  'larger' than it is today, for  THEN we can all benefit from increased community involvement from all sectors.

I Just felt it important to make that distinction and I shall now be quiet and go checkout the ML and hope to see progress on the script horizon. ( my hats off to those nimble able programmer types making ALL this possible ).

cheers
nl
------

---

### Post by jdodson on 2005-03-02
[QUOTE=neighborlee]I presonally find that if we BUILD an easy to use system ( there is nothing wrong with making linux 'easier' than windows just look at Linspires and say xandros goals/current systems ) and make the linux community  'larger' than it is today, for  THEN we can all benefit from increased community involvement from all sectors.[/QUOTE]

to make the community larger you need conversions.  conversions require people to convert and be converted.  so when you talk about increasing the community you are talking conversion.  

i have no problem discussing gnu/linux and my experiences with people.  i have no problems showing people what it is.  but i absolutely will not attempt to change anyones mind about using gnu/linux in a personal setting.  i have had much more "success" as it were with "increasing the community" that way.  btw, i love talking about gnu/linux and free software, so any chance i get i enjoy.  but will NOT say to anyone "you should use gnu/linux" anymore, i used to but got into too many arguements by scared or frustrated windows users.  but i will say "hey you know, this is why i use gnu/linux and this is what i have found it to be and not be."  i also like a nice debate about the merits of the FOSS model as opposed to proprietary models for software development and use.  however when the names start flying, i exit, there is no point in arguing or taking part in a zealot bash on either side.... not really sure why i decided to comment on that, guess i am bored :D 

anyways, a more functional user experience is good.  good bless the gnome and ubuntu foundations for that. :D

---

### Post by jdodson on 2005-03-02
[QUOTE=neighborlee]not to mention being stable and free of infectious critters.[/QUOTE]

some people consider proprietary software to be an infectious critter. :D

---

### Post by nikopol on 2005-03-02
Good thread this one. It's good to thrash these things out and at least discuss possible improvments even if we don't all agree how or whether it should be integrated into the distro. 

to a large extent, I full agree with you J - encouraging open standards is very important and to that extent, encouraging people to not use them is useful. For example, having grip default to encode to oggs and other configuration issues. I guess it's an issue of finding a balance between not encouraging and pragmatically accepting that most people's music collection will most likely be in mp3 (or even wma :shudder: ). I mean one way to make sure we're encouraging open standards is to lock-out the likes of mp3 playback, ram streams etc :D but that would freak some people out!

---

### Post by jdodson on 2005-03-02
[QUOTE=nikopol]Good thread this one. It's good to thrash these things out and at least discuss possible improvments even if we don't all agree how or whether it should be integrated into the distro. 

to a large extent, I full agree with you J - encouraging open standards is very important and to that extent, encouraging people to not use them is useful. For example, having grip default to encode to oggs and other configuration issues. I guess it's an issue of finding a balance between not encouraging and pragmatically accepting that most people's music collection will most likely be in mp3 (or even wma :shudder: ). I mean one way to make sure we're encouraging open standards is to lock-out the likes of mp3 playback, ram streams etc :D but that would freak some people out![/QUOTE]

right i am tracking with you.  balancing free software and pragmatism is something i have been thinking about for sometime.  there seems to be the RMS free software and everything else is unethical approach or the, mixed bag of propreity.

---

### Post by amoser on 2005-03-02
I don't think that closed source software is really a *bad* thing.  But I do think that we should push for open source, but sometimes that is not possable.  For example look at Flash and the Nvidia drivers, I don't think that there will ever be an open source project (unless the companys open them up) that can compeate with the closed source versions.  Yeah there are projects that are out there to make open source versions, but I don't think that is going to happen any time soon, but I will still push for them.  Basiclly what I am tring to say is that if the open source version of software X can do just as good (or better) then the closed source version of software X then we should use it, but if it is the other case around, then the closed source version should be the default.  That is just my US$.02 worth

~Alan

---

### Post by TravisNewman on 2005-03-02
There's a decent GPL flash player. It doesn't do much of the advanced stuff, but considering the complexity and the lack of cooperation from Macromedia, I think they did a good job.

No, I don't use it on a normal basis, because it's not there yet ;)

Anyway, I think that in all possible cases, GPL software should be pushed. Then other open source, then if no open alternatives exist, a script for downloading things would be handy. nvidia drivers come to mind.

---

### Post by gylf on 2005-03-03
I think the real trick to creating some sort of assisted-install script is to take each program you want to install and go through the licensing agreement real carefully.  I'm not aware of any laws in the US that make the distribution of free software *illegal*, but I know the distributions may be a breach of the licensing agreement you accept when you download the software.  Take java for instance.  The 5.0 agreement really only states this about distros:
> 
# License to Distribute Software. Subject to the terms and conditions of this Agreement and restrictions and exceptions set forth in the Software README file, including, but not limited to the Java Technology Restrictions of these Supplemental Terms, Sun grants you a non-exclusive, non-transferable, limited license without fees to reproduce and distribute the Software, provided that (i) you distribute the Software complete and unmodified and only bundled as part of, and for the sole purpose of running, your Programs, (ii) the Programs add significant and primary functionality to the Software, (iii)** you do not distribute additional software intended to replace any component(s) of the Software, **(iv) you do not remove or alter any proprietary legends or notices contained in the Software, (v) you only distribute the Software subject to a license agreement that protects Sun's interests consistent with the terms contained in this Agreement, and (vi) you agree to defend and indemnify Sun and its licensors from and against any damages, costs, liabilities, settlement amounts and/or expenses (including attorneys' fees) incurred in connection with any claim, lawsuit or action by any third party that arises or results from the use or distribution of any and all Programs and/or Software.


From what I understand, the bolded part above is the problem for most linux distos, as some of them bundle necessary code that could "replace components" in java.  But if your script is doing nothing but distributing java alone, it wouldn't violate that agreement so long as you present that agreement and have the user accept it.  

I would definatly do more research, that's just an example to get anyone who's interested started :)  I would start with the README file (which I haven't looked through).  I'd also contact the source (Sun, in this example) and just ask.

EDIT: Another look shows (i) might be a problem, as linux can't bundle java for the "sole purpose of running its programs"...but a install-script might be OK since its not really "bundling" it with anything.

---

### Post by Slapdash on 2005-03-03
This is getting really interesting.
I didnt see this thread and started another one on this subject. The Mod closed it.

I posted on a Mepis forum this question and am still awaiting feedback.

---

### Post by nocturn on 2005-03-03
[QUOTE=DarkSilver]The fact is ubuntu say "distribution that just work"
it's wrong !!!
[/QUOTE]

Well, I got my laptop with WinXP at work.  It doesn't 'just work' either.
It did not even have basic stuff like perl, bash and vi.

(seriously), I had to tweak my XP install with GNU tools and the likes for hours before getting it to do anything usefull at all.  In contrast, I apt-got xmms and flash on Ubuntu in minutes.

---

### Post by Mike Douglas on 2005-03-03
As jdodson stated, GNU/Linux was never about converting users, it was about providing a free and open operating system. Ubuntu follows these same guidelines and for good reason. Patents are not only a legal nightmere, but by using patented software, you're just legitimizing it. If some users can't handle that, so be it...

---

### Post by nikopol on 2005-03-03
[QUOTE=Mike Douglas]As jdodson stated, GNU/Linux was never about converting users, it was about providing a free and open operating system. Ubuntu follows these same guidelines and for good reason. Patents are not only a legal nightmere, but by using patented software, you're just legitimizing it. If some users can't handle that, so be it...[/QUOTE]

That's an interesting perspective - maybe the role of worldbeater that Linux has been given has in large part been foistered upon us whereas that's not really what we should be about. After Linus himself isn't really interested in other OS as his sole focus is making Linux work in and of itself not play catchup with Windows or Mac. 

But maybe the evangelists amongst us (myself included) have done ourselve a disservice by telling people how Linux is better than Windows and encouraging Windows users to switch. If they don't understand (or agree with) the philosophical aspect of Linux, will they actually make the effort of staying? Maybe not... From my own perspective, I chose Linux a long time back despite being a complete computer neophyte (to this day my programming skills are virtually non-existent). What made me stick with Linux when I could have used Windows? My belief in sharing with others  and the need to be involved to make things progress beyond the windows domination. It wasn't easy - the learning curve back then was pretty steep and I learnt a lot of stuff I wouldn't need to nowadays - but it was worth it.

---

### Post by rapala61 on 2005-03-03
[QUOTE=nikopol]That's an interesting perspective - maybe the role of worldbeater that Linux has been given has in large part been foistered upon us whereas that's not really what we should be about. After Linus himself isn't really interested in other OS as his sole focus is making Linux work in and of itself not play catchup with Windows or Mac. 

But maybe the evangelists amongst us (myself included) have done ourselve a disservice by telling people how Linux is better than Windows and encouraging Windows users to switch. If they don't understand (or agree with) the philosophical aspect of Linux, will they actually make the effort of staying? Maybe not... From my own perspective, I chose Linux a long time back despite being a complete computer neophyte (to this day my programming skills are virtually non-existent). What made me stick with Linux when I could have used Windows? My belief in sharing with others  and the need to be involved to make things progress beyond the windows domination. It wasn't easy - the learning curve back then was pretty steep and I learnt a lot of stuff I wouldn't need to nowadays - but it was worth it.[/QUOTE]

It is.. really interesting.. of course GNU/Linux was never about converting users...
thats linspire work. 

nocturne said something really interesting... that he spent hours configuring his laptop with all those programs.. now.. on average how many windows users would need to do such a config???. not a lot.. its not fair comparing this way since winxp its in no way meant to be a developer desktop, whereareas Linux was borned to do that.

Now.. talking about the real topic.. why is such a problem supporting a script to download a few packages and install/configure it??. As far as i know that would no require any kernel level hack , or something similar. Its not about making Linux looks like windows , but to HELP those who want to make the switch and not converting Linux  in the avobe-average IQ people OS. Most of us new Linux users come from Windows , we switched because the usuall.. viruses, lack of securitym spyware, bugs everywhere, curiosity to see what is this all about, etc. So... seeing that we get a lot of them , and that we can do this part of Linux shines really easy.. then.. why not to do it...??

---

### Post by Slapdash on 2005-03-04
I tried to get some answers from the Mepis community without much luck.
If there is truely something I dislike about that distro is the Community.

ANyway I asked how they could Distribute Java, Flash Player and nVidia Drivers so it works "out of the box" and asked if that isnt Illegal to do so.

This is so far the only response I recieved.... yeah I know ;)

"I doubt it, my Mac Mini showed up with the exact same capabilities."

Now I though that this guys response cant be a true reflection of the MEPIS community and then I posted my question in the Dev mailing list. It got accepted in the list and I got the next mailing list back.... No one replied.

So.... still a unresolved issue, anybody else had any luck so far as to get to the bottom of this?

---

### Post by Slapdash on 2005-03-04
There is some strange answers on the Mepis forums.
Relating to Java, As far as I can tell if UBUNTU includes Black Down Java it is legal to include & distribute it. THe other apps is still up in the air though.

Would anyone mind if I posted the Direct link there so you guys can see what is happening?

[Forum thread](http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=4844&forum=8)

---

### Post by nikopol on 2005-03-04
Mmm that GuitarDood is a bit of plank... not a clue then gets all sarcastic.

---

### Post by mike998 on 2005-03-04
[QUOTE=nocturn]Well, I got my laptop with WinXP at work.  It doesn't 'just work' either.
It did not even have basic stuff like perl, bash and vi.

(seriously), I had to tweak my XP install with GNU tools and the likes for hours before getting it to do anything usefull at all.  In contrast, I apt-got xmms and flash on Ubuntu in minutes.[/QUOTE]

I tried to install XP back onto my laptop for giggles.  Sound didn't work out of the box, resolution was 640 x 480 with 8 bit colour, modem and wireless didn't work, network card didn't work.  I didn't feel like messing with an install that had already taken an hour JUST to get it to the point where I could start customizing.  Ubuntu was installed onto my laptop 10 minuites after I had taken it out of the shipping box.  It works, it works for me, even if I had to do some tweaking to get .mp3, flash and all the other pieces of software to run and become usable.

I'm stuck with windows at work and even though windows can do some of the tasks that I want it to do out of the box (play mp3s), it uses programs I don't like to do so (windows media player), and I have to spend time downloading tools to make my life easier.

Linux is not Windows.  A typical windows install tends to hand-hold users through their steps.  One way of looking at it is that to do simple tasks (listen to an mp3, watch a movie) windows makes it fairly easy to complete these tasks, but other tasks are harder to the point where you have to be approaching an expert to do so (for example, I can remove all the spaces in my mp3s and replace them with underscores with a one line bash script under linux - I STILL haven't discovered how to do this easily under windows, unless I install Cygwin (which is cheating!)

What it boils down to in the arguments of windows vs linux is what does the user want?  Some users are happy using windows, some are happier using linux.  It would appear that for people who want to have a distrobutin that includes a pile of non-free software and is fairly easy to use - go with windows and good luck to you.

I'm going to stick with Ubuntu Linux, have to install some non-free software and have a box I love using and does what I want it to do.

 8-[  Oh my... where did that rant come from?  Better stay away from the Gnome / KDE forums !  :lol:

---

