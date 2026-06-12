---
title: "hardy heron - i really wanted to like it but..."
date: 2008-05-27
forum: Testimonials &amp; Experiences
---

### Post by jinchoung on 2008-05-27
not a lot of important things work "out of the box"!

first i had a bitch of a time with installing or even getting the live disk to go AT ALL.

1.  i had to add the 'IRQ POLL' command on starting and wanna guess how long it took me to discover that?  WHY OH WHY OH WHY isn't this ON BY DEFAULT?  or made an option with a helpful message that says, "hey, if you're having problems, try this..." ?

seriously, this is inexcusable for a mainstream distro.

but it befalls fedora 9 as well... mandriva one is the only distro i've tried that "just worked".

2.  GRUB is trash!  i could boot xp.  i could load linux.  i can't load both!  wasted weeks on this!  GRUB4DOS should be the default method especially since it doesn't f with mbr.

3.  why doesn't "DESKTOP EFFECTS" work out of the box.  i don't have an uncommon vidcard - it's an nvidia 7600gt... why doesn't it tell me WHY IT DOESN'T WORK?  WHY isn't the driver activating to full effect?  why can't i turn on compiz?  WHY ISN'T THIS DOCUMENTED?  that is the most mind boggling thing...

did the distro makers just NOT KNOW?  does it work out of the box for ANYONE?  and if not... wtf... WHY NOT DOCUMENT IT?

again fedora 9 fails as well.  mandriva one is the only distro where compiz works out of the box.

4. wireless doesn't work for me.  tried for weeks to get it working, tried using ndiswrapper - got so far as to be able to see wireless access points but could never get online.  even disabled wireless for my xp for some reason!  had to reboot the router.

this didn't work on any distro.

------------------------------------------------------------------

i'm a sucker for hype.  i want to like ubuntu.  but why do you have to make it so hard for me to like it?!?!

so, my last 2 questions are:

1. will there be an updated version of the installer?  should i wait awhile and try again in a few months?

2. as i said, i get no net access in ubuntu - can i download all the update content in xp?

thanks.

jin

---

### Post by kpkeerthi on 2008-05-27
[https://help.ubuntu.com/8.04/](https://help.ubuntu.com/8.04/)

---

### Post by oedha on 2008-05-27
2. you can use wubi or vmware to run both....but what is that for ? since they are different anyway
3. your nvidia need the restricted drivers....or linux driver from nvidia website ( even your windows can not play 3d efect without installing the driver....right ? )
4. what type of wireless ? beside ndiswrapper....there's also madwifi

1. maybe you should post your computer specification.....and let's see if it can run on recent HH
2. yes...but useless i think.......from [http://packages.ubuntu.com](http://packages.ubuntu.com) and then make your own repo....later on your ubuntu can update from there

---

### Post by kpkeerthi on 2008-05-27
> 
2. GRUB is trash! **i could boot xp. i could load linux.** i can't load both! wasted weeks on this! GRUB4DOS should be the default method especially since it doesn't f with mbr.

You can boot XP and you can boot linux. But you can't boot both. That is not possible in the current GRUB implementation. It can only boot one OS at a time. 
And GRUB is not a crap. If does what you told it to do in the installer. If you mess it, your boot record will be messed.

Instead of wasting weeks to figure out problems for yourself, you could have asked for help here in a nice way. I bet there are some smart minds here to help you out. Good luck.

And spend some time reading the ubuntu documentation (link posted earlier). The Desktop Effects issue you faced is documented there if you look closely.

---

### Post by jinchoung on 2008-05-27
> **kpkeerthi said:**
> [https://help.ubuntu.com/8.04/](https://help.ubuntu.com/8.04/)

sigh...

what about my issues do those docs address?  wanna venture a guess?

jin

---

### Post by jinchoung on 2008-05-27
> **oedha said:**
> 2. you can use wubi or vmware to run both....but what is that for ? since they are different anyway
3. your nvidia need the restricted drivers....or linux driver from nvidia website ( even your windows can not play 3d efect without installing the driver....right ? )
4. what type of wireless ? beside ndiswrapper....there's also madwifi

1. maybe you should post your computer specification.....and let's see if it can run on recent HH
2. yes...but useless i think.......from [http://packages.ubuntu.com](http://packages.ubuntu.com) and then make your own repo....later on your ubuntu can update from there

thanks,

cool.  so now i have confirmation that i need restricted driver.

question then (and heat is directed not at all at you but on canonica) - WTF isn't the restricted drivers loaded as default?!  seriously, for a linux newb, i'm wondering - WHY DOESN'T IT JUST WORK?!  why make the user jump through hoops?  WHY WOULDN'T I WANT THE DRIVERS THAT ACTUALLY MAKE STUFF WORK?

or if i need restricted drivers, WHY DOESN'T IT TELL ME?

----------------------------------------

if my rig can't run hh (which i know is not the case), i want nothing to do with linux...

P4 e2180
abit p35
2gb pc3200 ddr2 ram
nvidia 7600gt
belkin wifi 802.11g usb2 dongle
3 sata hard drives
1 dvdrw 
--------------------------------------------------------------------

i'm a linux newb (though i've started and made some good progress on my eee) but i built my own rig from scratch and i'm far from a newb on xp.
--------------------------------------------------------------------

so, wifi does not work, i have not internet in ubuntu so i'm not going to run through that again.... so basically, if i can't get an updated system without net connection, then i'm out of luck?

jin

---

### Post by jinchoung on 2008-05-27
> **kpkeerthi said:**
> Instead of wasting weeks to figure out problems for yourself, you could have asked for help here in a nice way. I bet there are some smart minds here to help you out. Good luck.

And spend some time reading the ubuntu documentation (link posted earlier). The Desktop Effects issue you faced is documented there if you look closely.

ubuntu documentation is a joke.  the slimness of the documentation about installing alone perfectly captures how inept it is.  it deals with NONE of the problems i dealt with.

as for searching the web, trying doing a search on "GRUB wiped out my xp" and see how many hits you come up with.  THAT imo qualifies it as junk.

as i said earlier, i'm not a novice but i could NOT get xp to boot with grub... to get into xp, i had to fixmbr then i can't boot ubuntu or i install grub and can boot ubuntu but can't boot xp.... fing junk.

as i said, i finally solved the problem with grub4dos which is BRILLIANT!!!  IT DOES NOT TOUCH MBR!  this should be the default or newbie method on all linux distros with an option for other grubs for seasoned users.

fing with the mbr if you have a win os is just stupid.
-----------------------------------------------------------------------

wifi not working out of the box is a DEAL BREAKER but understandable.

compiz not working out of the box when they can make it work out of the box is STUPIDITY!  not giving the user a heads up on what the issue is when you try to activate compiz (when canonical knows damn  well ahead of time that it WON'T WORK OUT OF THE BOX) is just shy of CRIMINAL!

not booting the livecd or letting me install out of the box tells me there are idiots in the pipeline.

i know, that is harsh but try to understand the problem (needing to add 'irq poll') and what it took for them to miss it in alpha, beta release candidates and up to final release.

WHAT IS THE EXCUSE?

they didn't have access to modern machines?

seriously, as i said, i wanted to like ubuntu but stupid **** like this made me really hate it.  i'm hoping it's temporary.  we'll see.

jin

---

### Post by jinchoung on 2008-05-27
also,

"if you look closely"... seriously... the organization in that manual is a mess and your words show that you see it to.

just that manual alone is a big argument for why ubuntu is not ready for the masses.

jin

---

### Post by jinchoung on 2008-05-27
that's another thing-

if web access can be SUCH a huge problem for wifi users (and this is admitted by many)...

WHY NOT ANTICIPATE the problems of these people and create a way for them to update stuff by downloading in windows and burning on a cd or something.

why not have that as an FAQ since net is denied for so many (again, google, it afflicts a LOT of people).

it's stuff like this that makes me batshit with rage.  their inability to anticipate problems and either document it or address it somehow.

jin

---

### Post by oedha on 2008-05-27
i also dont know the reason about that
actually you can check on system - administration - hardware drivers
it will tell you about restricted drivers ( it also pop up on the panel bar )

....but your spec is OK except the wifi ( i have no experience in belkin ....sorry :()

what if you check here :==> [https://help.ubuntu.com/community/?action=fullsearch&context=180&value=belkin&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=belkin&titlesearch=Titles)

---

### Post by jinchoung on 2008-05-27
[https://help.ubuntu.com/8.04/desktop-effects/C/compiz-problems.html](https://help.ubuntu.com/8.04/desktop-effects/C/compiz-problems.html)

lol... and if you click on the restrictd driver link, you know what you get?

try it....

lol....

why does canonical try to make us hate them... so much....

jin

---

### Post by kpkeerthi on 2008-05-27
> **jinchoung said:**
> ubuntu documentation is a joke.  the slimness of the documentation about installing alone perfectly captures how inept it is.  it deals with NONE of the problems i dealt with.

as for searching the web, trying doing a search on "GRUB wiped out my xp" and see how many hits you come up with.  THAT imo qualifies it as junk.

as i said earlier, i'm not a novice but i could NOT get xp to boot with grub... to get into xp, i had to fixmbr then i can't boot ubuntu or i install grub and can boot ubuntu but can't boot xp.... fing junk.

as i said, i finally solved the problem with grub4dos which is BRILLIANT!!!  IT DOES NOT TOUCH MBR!  this should be the default or newbie method on all linux distros with an option for other grubs for seasoned users.

fing with the mbr if you have a win os is just stupid.
-----------------------------------------------------------------------

wifi not working out of the box is a DEAL BREAKER but understandable.

compiz not working out of the box when they can make it work out of the box is STUPIDITY!  not giving the user a heads up on what the issue is when you try to activate compiz (when canonical knows damn  well ahead of time that it WON'T WORK OUT OF THE BOX) is just shy of CRIMINAL!

not booting the livecd or letting me install out of the box tells me there are idiots in the pipeline.

i know, that is harsh but try to understand the problem (needing to add 'irq poll') and what it took for them to miss it in alpha, beta release candidates and up to final release.

WHAT IS THE EXCUSE?

they didn't have access to modern machines?

seriously, as i said, i wanted to like ubuntu but stupid **** like this made me really hate it.  i'm hoping it's temporary.  we'll see.

jin

I don't think this kind of attitude will draw people to offer you  help. Sorry.

Ubuntu ships with only free and open source software out-of-the box. If you have hardwares that require non-open sourced (binary) driver, they WILL NOT work out of the box in ubuntu.

[http://www.ubuntu.com/community/ubuntustory/licensing](http://www.ubuntu.com/community/ubuntustory/licensing).

---

### Post by AndrewTheArt on 2008-05-27
There are way too many points to be made here concerning your complete ignorance of Ubuntu and the tribulations and philosophies that are inherently a part of the Linux experience. I could go on for days concerning these issues. 

You appear to be the typical Windows user who expects everything to work out of the box. This is not necessarily your fault - you've probably just been exposed to an environment that conditioned you to believe that the Windows way was the way things worked all the time. In the world of Windows, things work because the hardware and software are intricately designed to cooperate flawlessly, generally unbeknown to the end user. It boils down to the relationship between the hardware manufacturers and Microsoft. In general terms, the hardware manufacturers make drivers for thier hardware that operate perfectly (98% of the time) with the predominant operating system on the market at that time (currently Windows, and XP in particular), because that's where the intrest and therefore money are at. The end result is that XP is shipped on computers loaded with the correct drivers and configured in such a way that the hardware appears to work without any special configuration at any point of the process using generic drivers. Windows seems perfect to the average person buying a computer simply because everything works out of the box.

Because of this relationship, people begin to expect that that's just the way all computers work.

Then comes in Linux. Some of the drivers that ship with Ubuntu were developed by hardware manufacturers, but just as many (and undoubtely more) were developed by unpaied programmers from around the world either reverse engineering binary drivers or simply hacking together a method to make a piece of hardware work to the best of thier ability. They get no support whatsoever from the manufacturers most of the time, especially with diverse and intricate new hardware. The ones that manufatuerers do provide out of necessity are often extremely crappy piles of dung that fail constantly or just provide a horrible end experience to the user. See the difference? You either need to accept the fact that Linux will be like this for some time, possibly for many years, or you can go back to XP, where in the right conditions everything will work great and flawlessly without any sort of effort. If you take the first approach, you will need to take the time to Google your problems and really dig around to get things working. The fact of the matter is that the problems you're experiencing are entirely typical. Ubuntu does a great job recognizing all the diverse hardware out there and offering you proprietary drivers whenever possible to enchance your experience. Try putting a generic copy of Windows XP on a machine that it didn't ship with, and see what happens. You'll go through a LOT more hell than what you're experiencing right now and you'll find close to not help on the Internet. This is an area where Linux simply shines.

Windows XP might be easier when it's in the perfect environment, but it's definitely not because it's inherently better. In fact, by itself and alone, it completely sucks next to Linux in the areas of hardware recognition, configuration, and the like. Windows XP is like an extremely wealthy but snobby kid given all the money in the world to succeed, but only possessing a superficial and fleeting knowledge of how things work and a bad attitude towards getting work done consistently. Linux is more like a poverty stricken genius using pure intuition and guesswork to make thing work. Take away the support of money, and who operates better most of the time? Linux, by a huge margin. But keep the crutch of money in the equation and the status quo we see today dominates - at a huge expense on multiple levels (that's a story for another time, though). I'll stick with the genius, personally. I know he'll figure things out eventually, operate more efficiently, and change the world someday. There's nothing wrong with the rich kid -  he gets things done, but I have more faith in the genuis.

---

### Post by kpkeerthi on 2008-05-27
> **jinchoung said:**
> [https://help.ubuntu.com/8.04/desktop-effects/C/compiz-problems.html](https://help.ubuntu.com/8.04/desktop-effects/C/compiz-problems.html)

lol... and if you click on the restrictd driver link, you know what you get?

try it....

lol....

why does canonical try to make us hate them... so much....

jin

LOL!.. thats how I got that working in ubuntu... LOL!

---

### Post by kpkeerthi on 2008-05-27
If you are looking for some help, please be nice and respectful. This is not a paid support. People here are volunteers.

[http://www.ubuntu.com/community/conduct](http://www.ubuntu.com/community/conduct)


If you need professional support see this website [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

---

### Post by CameO73 on 2008-05-27
First I wanted to take the time to answer your questions, but it seems you have already made up your mind about Ubuntu. Just a couple of tips then:

[LIST]
[*]One of the best ways to get help is just ask questions on forums (these forums are a good start). It would help to ask them nicely, but you don't have to (I've had my share of frustrations, so I know what it's like).
[*]The restricted drivers are not enabled by default, because they are restricted. This means there is no source (read: no way to check or extend the functionality). Ubuntu gives you this option, since it has added features (one of them is improved 3D support), but it can not support them. Btw, normally the restricted driver will be offered right after installation (which happened for me with my 7600GT (in Feisty) and 8800GT (in Hardy).
[*]I assume you have reported any bugs and feature requests in [Launchpad]("https://launchpad.net/ubuntu")? If you want things to change, you'll have to do your part. Ranting in a forum is not the way. Ubuntu (in fact any Linux distribution) exists solely because of the supporting community.
[/LIST]

---

### Post by akiratheoni on 2008-05-27
Dang, it looks like you're having too many problems, you should ask for a refund if I were you.

---

### Post by cheesypoof on 2008-05-27
> **akiratheoni said:**
> Dang, it looks like you're having too many problems, you should ask for a refund if I were you.
^^

Don't forget, ubuntu is free. I am sure if it had the type of money invested in it like Windows does, it would have much fewer bugs.

---

### Post by jinchoung on 2008-05-27
> **kpkeerthi said:**
> LOL!.. thats how I got that working in ubuntu... LOL!


lol... click the hyperlink that says "restricted drivers" when you get to that page.

TRY IT.

you get a 404 error.

jin

---

### Post by akiratheoni on 2008-05-27
I was going to help you, except I decided not to. Your loss.

---

### Post by jinchoung on 2008-05-27
> **kpkeerthi said:**
> If you are looking for some help, please be nice and respectful. This is not a paid support. People here are volunteers.

[http://www.ubuntu.com/community/conduct](http://www.ubuntu.com/community/conduct)


If you need professional support see this website [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

there should be a code of conduct for "helpers" who seem to think they're helping by posting a link to documentation that doesn't say anything at all about all the issues that a newby is having...

since such behavior is likely to cause a frustrated newb to go ballistic.

jin

---

### Post by jinchoung on 2008-05-27
> **akiratheoni said:**
> I was going to help you, except I decided not to. Your loss.

boo hoo.

besides, i doubt it.  as i said, the signal to noise on ubuntu wisdom is pretty nutty.

jin

---

### Post by AndrewTheArt on 2008-05-27
> **jinchoung said:**
> and yours is the typical linux attitude that makes "typical windows users" roll their eyes and punch a cute dog in the face.

listen, i get the whole philosophy thing.  why t f do you think i'm even investigating ubuntu?

i don't love m$.  why do you think i'm even investigating ubuntu?

as i said, i get the philosophy.

y'know what i don't get?

NOT MOTHERFING LABELING IN BIG RED FLASHING MOTHER FING LETTERS THIS WILL NOT WORK FOR YOU WITH THE DEFAULT DRIVERS - INSTALL THE MOTHERFING "REAL DRIVERS" THE RESTRICTED DRIVERS THAT ACTUALLY LET YOU DO ****!  WE KNOW THIS DOESN'T WORK OUT OF THE BOX... AND WE KNOW HOW TO MAKE IT WORK... SO WE'RE GIVING YOU A HEADS UP.

i get the philosophy.  i like the philosophy.

BUT I WANT MOTHERFING COMPIZ TO JUST MOTHERFING WORK.

if i'm beating my head against the desk because i can't even boot the fing cd because i have to type in irq poll for some reason, ya think i care about philosophy then?

as for googling - there's a real huge problem that seems very unique to linux... the amount of answers that crop up are surprisingly diverse and shockingly wrong... moreso than with other things you might google.

the signal to noise ratio on offered solutions is ludicrous on certain (mainly, newby mainstream issues!!!) issues.

jin
The Restricted Driver Manager should do exactly that - it should pop up after installation and prompt you to install restricted drivers if you so choose. I don't know what happened to you, but Ubuntu 8.04 and Ubuntu 7.10 both did that for me.

By the way, few operating systems if any do exactly what you describe. Just today, my friend was installing a generic copy of XP on his computer. The install went fine, but he coulden't access the Internet! XP didn't have drivers for his Ethernet card, but it took him hours to figure that out. Windows did not give ANY indication that this was the problem. Ubuntu does a hell of a lot better job than Windows in this area much of the time, and I think it should be commended for that.

By the way, people investigate Ubuntu and don't understand the philosophy all the time, so forgive me for that mistake. :roll:

---

### Post by ardvark71 on 2008-05-27
Hi all...

I can understand the OP's frustration, though. I felt a lot like he did when I was using Breezy Badger and learning the nuts and bolts of Ubuntu and Linux.

I would agree with Andrew that a large portion of the problem is that drivers and driver support and quality. This is one of the biggest hurdles Linux will have to overcome if it is to seriously compete with Microsoft. The one thing I disagree with is that installing drivers for any version of Windows is, for me, *much* easier and simplified. But I suppose it depends on what you're used to. ;)

The above combined with a completely different structure and method of operation, which is mostly Windows incompatible in terms of software, presents a pretty high hurdle for many folks who use computers (to consider using Linux.) 

Best Regards...

---

### Post by jinchoung on 2008-05-27
finally,

i realize my tone is hostile but it wasn't directed at any of you until some of you decided to start making it personal.  (or offering a single useless link that offered virtually no help)

i'm blowing off steam and i don't mean to run anyone over with it except maybe mark shuttleworth...

perhaps it might be worth noting that it's best to let an obviously frustrated individual just blow it off instead of trying to jump in their way and further the aggravation?  lol... this is the advice of the criminal to his victims... : )

anyway, any and all contention caused right now is due unequivocally to my rage and for that i do apologize.

but i HATE HATE HATE all the deficiencies in documentation and implemention in hardy heron right now.  i HATE HATE HATE ubuntu and it's stupid fing web page even... where's the community forum?  in community?  no?  in help>community?!  WTF?!?!?!

but that's not your fault.

i'll come back every so often to see if linux is up to my standards of usability and sanity yet....

jin

---

### Post by jinchoung on 2008-05-27
> **AndrewTheArt said:**
> The Restricted Driver Manager should do exactly that - it should pop up after installation and prompt you to install restricted drivers if you so choose. I don't know what happened to you, but Ubuntu 8.04 and Ubuntu 7.10 both did that for me.

By the way, few operating systems if any do exactly what you describe. Just today, my friend was installing a generic copy of XP on his computer. The install went fine, but he coulden't access the Internet! XP didn't have drivers for his Ethernet card, but it took him hours to figure that out. Windows did not give ANY indication that this was the problem. Ubuntu does a hell of a lot better job than Windows in this area much of the time, and I think it should be commended for that.

By the way, people investigate Ubuntu and don't understand the philosophy all the time, so forgive me for that mistake. :roll:

thanks for the helpful reply.  sincerely.

but if you read all of my (admittedly ridiculous, rambling, raging) post, you'd see that because i'm running wifi, i had no internet access.

it is a perfect storm that unfortunately because of hardware drivers for wifi befalls LOTS of folks.

lots of things don't work out of the box and without internet access, no POSSIBILITY of getting anything to work period.

that's why i was asking about downloading these updates in xp and burning them to get ubuntu up and running.

i know xp doesn't offer the kind of explicit directions that i'm asking about compiz or desktop effects.

but the issue is this:
1. they include desktop effects and compiz in the default distro
2. they know FULL WELL AHEAD OF TIME IT WON'T WORK WITH THE DRIVERS LOADED in the default install.

IF web access was never an issue, then sure, they could assume that the proper drivers will just get loaded... but because of wifi, this is NEVER THE CASE IN THIS PERIOD IN TIME.

and so i think having an explicit heads up makes sense.

(also, in your friends case, that's usually not a problem with most xp users because the hardware either works with xp built in drivers or if not, ALWAYS comes with a driver disk that contains windows drivers... usually with "autorun" enabled.... i know, this is a luxury that linux doesn't enjoy yet)
-----------------------------------------------------------

the heads up is more necessary because the signal to noise in linux answers as i said is so bad and can easily cause newbs to go and superwildgoosechases...

i've read lots of replies in my weeks of researching agony where people said "hey, it just worked for me.  maybe your graphics card is busted" !!!!  i literally shudder to think of things i might have tried based on google searches if i were not as computer literate as i am....

and as i said, the IRQ POLL thing is inexcusable.  whoever let that pass should be fired and/or flogged.

jin

---

### Post by cackles on 2008-05-27
OK, your blowing off steam but as said by someone maybe coming here and asking would have helped.

I dont mean to be smart but on the 15th of this month I asked in a forum 'Debian, Ubuntu, what?' Using the help on the net by the 18th I had written a tut on a fast install of a headless server using Ubuntu 8.04 that covered ftp, samba, remote torrents via azureus and webserver ... from knowing NADA.

3 days using outdated parts from other tutorials and ... ASKING QUESTIONS to turn the pile of rubbish computer parts that their last OS was WinME into a NAS, FTP, webserver, BT client.

You spent weeks?

You wanted to like it and I didnt know what to expect, last command line based OS I used was DOS and your talking about fedora 9 and stuff I know nothing about as well.

It's annoying chasing your tail but if you dont ask you dont get.

---

### Post by forestpixie on 2008-05-27
Now you've calmed down a bit - the next time you feel the need to blow off steam maybe do it in the Testimonial Experiences forum- where this should be, there are plenty of these in there.

I can understand that people get frustrated but there's not really any excuse for peppering with bad language. Young people go here as well - by that I mean young young - not the young who can teach the rest of us how to swear :)

From what I've read the next version is aiming at trying to sort the wireless thing out from install, at least that's how I read it anyway. If you have the time and space on the laptop/pc - maybe get involved from the beginning and help to get wireless connections bug free - or at least as much as it can be.

I hope that you get it sorted to your satisfaction and wish you luck.

---

### Post by ardvark71 on 2008-05-27
> **jinchoung said:**
> 
anyway, any and all contention caused right now is due unequivocally to my rage and for that i do apologize.


Not a problem. :)

I felt exactly as you do MANY times when I was using Ubuntu. ;)

Take Care and Best Regards...

---

### Post by robert shearer on 2008-05-27
> **akiratheoni said:**
> Dang, it looks like you're having too many problems, you should ask for a refund if I were you.

Thank you thank you thank you. Your levity and commonsense is sooo appreciated and refreshing. 
Now, what suggestion can you offer for bruising as I think I have a couple where I fell off my chair, I was laughing so hard.

---

### Post by jinchoung on 2008-05-27
> **CameO73 said:**
> First I wanted to take the time to answer your questions, but it seems you have already made up your mind about Ubuntu. Just a couple of tips then:

[LIST]
[*]One of the best ways to get help is just ask questions on forums (these forums are a good start). It would help to ask them nicely, but you don't have to (I've had my share of frustrations, so I know what it's like).
[*]The restricted drivers are not enabled by default, because they are restricted. This means there is no source (read: no way to check or extend the functionality). Ubuntu gives you this option, since it has added features (one of them is improved 3D support), but it can not support them. Btw, normally the restricted driver will be offered right after installation (which happened for me with my 7600GT (in Feisty) and 8800GT (in Hardy).
[*]I assume you have reported any bugs and feature requests in [Launchpad]("https://launchpad.net/ubuntu")? If you want things to change, you'll have to do your part. Ranting in a forum is not the way. Ubuntu (in fact any Linux distribution) exists solely because of the supporting community.
[/LIST]

thanks much,

yes, absolutely.  i was on a completely, HULK SMASH!!!, rampage.  again, my apologies and yep, if you've been frustrated with linux, i trust you understand (if not approve) of my behavior.

thanks again for confirming the restricted drivers thing.  this information is extremely hard to get from a google search even of these forums.  lots of diverse answers, most of them wrong.

which is why i waited this long to actually post and ask myself.

i do very much like getting involved in the things that i tinker with.  but for me, ubuntu is not even at a level where i can tinker with it because of the wifi net access thing.

so i hope my hate will dissipate and there will come a time where ubuntu or my hardware configuration will allow my participation.  but that time ain't now.

thanks for the help.

jin

---

### Post by oedha on 2008-05-27
sorry to interupt...what belkin is yours exactly....
( have you check the previous link that i gave you ? is taht fit or not ? )
maybe you can find out from terminal by typing :==> sudo lshw -short -C network
:)

---

### Post by Efros on 2008-05-27
Try [EnvyNG]("http://www.albertomilone.com/envyngfaq.html"), use it to uninstall your existing driver and then to install the new driver. You may have to completely remove all compiz stuff using synaptic and then reinstall it all. You will probably need Emerald too. Compiz is pretty but it shouldn't be your only reason for using Ubuntu.

---

### Post by jinchoung on 2008-05-27
thanks again everyone for your understanding and indulgence.

oedha,
Belkin 802.11g F5D7050... i spent forever tracking down the linux native drivers... it's something like rtsomethingsomething... forgot...  but it was a no go.  best results i got was ndiswrapper where i could see access points but encountered a common problem lots of people were having about "no dhcp offers"....

and again, there's the freaky thing that disables wifi when i switch back to xp and i have to reboot the router.

frankly, the thought of hobbling my net access on all computers just made me want to stop fiddling.

hey efros,
thanks for the tips. but i can't install any restricted drivers until i can actually download it.  but now that i know what the issue is, maybe i can download it in xp somehow... i should be able to google up a link to this pretty easy.  thanks.

as for compiz not being the only reason to use linux or ubuntu - you got that right.  my first linux was mandrake a few years back and now i've been re-introduced and re-motivated to explore and learn linux through my eee (a customized xandros distro).  making good enough progress that i wanted to add a dual boot to my xp desktop.

but dang it if compiz ain't sexy.  after seeing ubuntu with compiz on youtube, it just completely made any notion of upgrading to vista disappear.

yeah, it's eyecandy but the multidesktop views is a functional feature that i wish for everyday at work on xp.

so for me, compiz kinda fell into the "basic fundamentals" that i wanted for my initial linux install - especially since it's a huuuuuge pain to get it going on my eee....

jin

---

### Post by eldepeche on 2008-05-27
Several things:

1. The irqpoll boot option is not necessary nor helpful on many computers, so it is not enabled by default. Ubuntu was not designed for your computer, but for most computers.

2. Wireless network adapters and graphics are pretty much the worst area as far as Linux hardware support. There are wireless adapters from many manufacturers that work well with Linux, and there are some that don't work at all. It might be worth your time and money to find one that is fully supported. 

3. You said before that you understand the philosophy issue, but you just wanted your stuff to work. Fair enough, but there are plenty of other distributions that ship non-free software. You mentioned Mandriva. Why not use that if it works? 

4. Just because a bunch of people on the internet think Grub broke their computers, does not mean that it actually did. 

5. Next time, don't wait to post here until you're so upset. This is one of the few places you can go to ask Linux questions without having to catch hell for not doing weeks of homework.

---

### Post by jinchoung on 2008-05-27
> **eldepeche said:**
> Several things:

1. The irqpoll boot option is not necessary nor helpful on many computers, so it is not enabled by default. Ubuntu was not designed for your computer, but for most computers.

2. Wireless network adapters and graphics are pretty much the worst area as far as Linux hardware support. There are wireless adapters from many manufacturers that work well with Linux, and there are some that don't work at all. It might be worth your time and money to find one that is fully supported. 

3. You said before that you understand the philosophy issue, but you just wanted your stuff to work. Fair enough, but there are plenty of other distributions that ship non-free software. You mentioned Mandriva. Why not use that if it works? 

4. Just because a bunch of people on the internet think Grub broke their computers, does not mean that it actually did. 

5. Next time, don't wait to post here until you're so upset. This is one of the few places you can go to ask Linux questions without having to catch hell for not doing weeks of homework.

1. but does it do any harm in having it for ANYONE?  mine is not a nonstandard or even exotic computer setup.  i have my specs a few posts back.  i'm not sure if 'irq poll' needed to be added because of multiple hard drives or sata but both are probably more common than not.  and there are a lot of people who turn out to be RANK BEGINNERS having this problem.

their FIRST EXPERIENCE WITH UBUNTU IS COMPLETE FAILURE.

that being the case, if irqpoll inclusion does little or no harm to systems that don't need it and allow EVERYONE to boot, in my view it is a usability misjudgment NOT to include it.

2. this i understand and have said so.  wireless being crippled is probably the most critical failure (besides boot) but this is a "no fault" situation.  they're doing the best they can with proprietary hardware vendors.

BUT

re-read what i said about the graphics issue.  THEY KNOW FULL WELL COMPIZ IS NOT GOING TO WORK WITH THE DEFAULT INSTALL!

they should TELL YOU THIS right off the bat.  no excuse for this.

3. i might.  not merely because things don't work but because basic documentation issues are left in a bad place.

because ubuntu seems to not want to accommodate newbs with easily implementable documentation like "this will not work for you... just so there's no mystery, get the restricted drivers".

4. but it becomes a usability issue again.  pros can and know how to setup their grub no matter what the default boot installer is.  if they don't like it, they'll change it.

the ones who are held hostage to the default boot loader is the newb.  and they're the ones most apt to hobble their systems with futzing with the MBR.

grub is good.  grub is great.  but from a newb standpoint - especially in consideration of the vast amount of potential system configurations, it is hard and potentially lethal for a newb setting up a dual boot.

grub4dos is waaaaaaaaaaaaaaaaaaaaaaaaaaaaay better in this regard.  does not TOUCH mbr.  windows can always boot.  it uses the windows bootloader to load grub.  you can launch linux from there.

it may be an issue of pride and not wanting to acknowledge windows or be subordinate in THEIR bootloader but if the majority of linux converts will be coming from windows and will probably try dual booting before full on conversion, the linux community might just benefit from ceding here.

again, it's an issue of first impressions.  if the linux community does not care about first impressions though, we've got nothing to discuss i guess.

5. thanks, this is good advice.  but my instinct is to research before asking.... too many years of seeing "rtfm".  : )

jin

---

### Post by CameO73 on 2008-05-27
Maybe nice to know... if you want to know if certain hardware works with Ubuntu, check out [UbuntuHCL.org](http://www.ubuntuhcl.org/). Strange, though ... someone there mentions that his [Belkin F5D7050 wireless card](http://www.ubuntuhcl.org/browse/product+bBelkin_F5D7050b_v4000uk?id=749) work OK (in Hardy).

---

### Post by Joeb454 on 2008-05-27
All my hardware works out of the box with Ubuntu - you asked in the first post :)

---

### Post by civillian on 2008-05-27
I can appreciate your complaint, but rather than ranting, asking politely is what might have gotten you help rather than flames.

Your biggest bugbear seems to be that there is a lack of documentation which is simply not true. A quick google might have solved this or visiting the documentation area of the ubuntu website, or simply searching the forums, rather than just causing a bit of a flame war.

And if you preferred mandriva, why not just use that?

And next time ask for help in the questions area of the forum, or just take it to a generic discussion board.

---

### Post by lswest on 2008-05-27
> **jinchoung said:**
> not a lot of important things work "out of the box"!

first i had a bitch of a time with installing or even getting the live disk to go AT ALL.

1.  i had to add the 'IRQ POLL' command on starting and wanna guess how long it took me to discover that?  WHY OH WHY OH WHY isn't this ON BY DEFAULT?  or made an option with a helpful message that says, "hey, if you're having problems, try this..." ?

seriously, this is inexcusable for a mainstream distro.

but it befalls fedora 9 as well... mandriva one is the only distro i've tried that "just worked".

2.  GRUB is trash!  i could boot xp.  i could load linux.  i can't load both!  wasted weeks on this!  GRUB4DOS should be the default method especially since it doesn't f with mbr.

3.  why doesn't "DESKTOP EFFECTS" work out of the box.  i don't have an uncommon vidcard - it's an nvidia 7600gt... why doesn't it tell me WHY IT DOESN'T WORK?  WHY isn't the driver activating to full effect?  why can't i turn on compiz?  WHY ISN'T THIS DOCUMENTED?  that is the most mind boggling thing...

did the distro makers just NOT KNOW?  does it work out of the box for ANYONE?  and if not... wtf... WHY NOT DOCUMENT IT?

again fedora 9 fails as well.  mandriva one is the only distro where compiz works out of the box.

4. wireless doesn't work for me.  tried for weeks to get it working, tried using ndiswrapper - got so far as to be able to see wireless access points but could never get online.  even disabled wireless for my xp for some reason!  had to reboot the router.

this didn't work on any distro.

------------------------------------------------------------------

i'm a sucker for hype.  i want to like ubuntu.  but why do you have to make it so hard for me to like it?!?!

so, my last 2 questions are:

1. will there be an updated version of the installer?  should i wait awhile and try again in a few months?

2. as i said, i get no net access in ubuntu - can i download all the update content in xp?

thanks.

jin

1.  Chances are that command causes a problem for other people who do not have your hardware, so it's not enabled for default.  The error may not be fixed by adding that boot option to any kind of hardware, so a prompt suggesting it can lead to bigger problems, and would lead to larger complaints for supplying bad advice.  The boot options included inside the liveCD are fine for a mainstream distro.

2. GRUB is fine, again, it's not unheard of for it to cause trouble, but by no means generalize and claim something else should be the default.  Large teams of people decided what to make default and what not, they had their reasons, and i support them fully.  If you have an issue with it, replace it or test the configurations until you find the right one for yourself.

3.  Desktop effects are enabled out of the box, but have a failsafe that disables them if the card cannot support them (e.g. when it runs on the VESA driver).  Nvidia cards are not supported (past the series 6) by the open-source nv drivers, but by the nvidia drivers, which are propriety software, which will never be installed by default on an open-source OS that aims to reach as many people as possible.

4.  Ubuntu will not have affected your XP wireless-wise, and it is known that some wireless cards will not work with Ubuntu, either purchase a cheap wireless dongle that will work out of the box, or do extensive research on the problem.  if you got the card working enough to scan networks, then it may have been a configuration error preventing it to connect.
-----------------------------------------------------------------
1.  Updated version of the installer?  It will be updated when Intrepid Ibex is released.  Otherwise, I'm not sure what you mean?  An installer with all the newest packages?  Will probably occur when 8.04.1 is released in June or July.

2.  You can download the updates, but chances are you won't get them all and that they will need files that are not already on your computer.  best to plug in an ethernet cable for a few minutes while it updates.

Judging by your post count of 17, I'd say you didn't do as much as you could have to solve your problems, nor am i inclined to help you anymore, because these kinds of posts wear down my nerves, and I try hard to be polite when i reply to them.  I'm sure I'm not the only one whom this annoys.  Also, looking at the last post you made on this thread, it does not seem like your tone or attitude is improving.  We are **not** paid support, we do not do this for a living.  We do this **out of our own free will**.  So do the developers of Ubuntu (the vast majority at least).  

Define a "nonstandard" or "exotic" computer.  If you can code an OS (linux or otherwise) that supports more hardware out of the box than any distro in existance at the moment, and has enough stored(probably in the gigabytes) documentation to inform beginners of minor, not guaranteed, fixes, then i tip my hat to you.  But if you cannot, then you shouldn't complain about other people's work.  Did you ever even look at the documentation in the ubuntu wiki?

GRUB4DOS isn't way better at all.  This is what it does:  Installs GRUB to the partition where linux is installed (can be changed from MBR during install in any distro that I've tried, and I've tried many) and then adds an entry into the boot.ini files of windows which links to the grub in the linux partition.  That can be done manually.

Last point about posting here.  Yes, you should post here before you get frustrated, there are many many people here who are happy to help beginners with their problems, but not when they post threads like this.  I, for one, am no longer inclined to help you at all, and I will add you to my (very short) list of people whose issues I leave to others.  Why? because the first impression you made is, frankly, pretty crap.  Also, these forums hold a lot of answers, your first instinct should be to search this forum for answers to your problems, or use [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by eldepeche on 2008-05-27
A quick Google search indicates that on a desktop machine, there is a small performance hit if you use the irqpoll boot option, and it can be more pronounced on older hardware. 

I have an ATI Radeon X800, and Compiz works perfectly out of the box. For most graphics cards, the Restricted Drivers Manager will pop up and say  that proprietary drivers are available; I'm not sure why it didn't for you. That is indeed a usability problem, and you may want to file a bug if you can reproduce that behavior.

The developers have tried very hard to make a collection of software work well on a large number of machines. Most of the posts in this forum are about the same 10 common issues, and are answered pretty quickly. You are one of the unlucky ones, but if your issues are now fixed, maybe you'll stick around, and next time you'll buy a computer with Ubuntu pre-installed, or at least do some research and buy compatible hardware. It definitely takes some work to be a dedicated Linux user, but you're past the tough part now.

---

### Post by DMK62 on 2008-05-27
If linux is causing the level of frustration displayed in your posts then you may be better off not using it at this point in time. When you attack the OS and the developers you ARE also attacking many of those involved with the community so expect it to be taken personally. 

Linux is not a magical OS that will do everything automatically for you. It doesn't hold your hand like others do. Try doing an install of arch, debian, slackware, and many others and you will appreciate how user friendly Ubuntu is for the new user. 

There has been an increase in the amount of posts with the " if I yell and scream enough they will make sure my problems are solved " attitude. The community is here for those that seek assistance in a polite manner.

Dale

---

### Post by Ballistixx on 2008-05-27
Hello Guy's,

I thought would add my two cents to the mix as a week old Hardy Heron user. Fist time with any Linux distro.

First I am simply amazed that Ubuntu can work (mostly) with so many different makes of hardware with out specifically made drivers. The price of free.99 can't be beat either.

No on to the community and these forums...

I have asked a couple questions and never mind not being answered they weren't even read. I asked the questions politely and to the point.

It is very offensive to be recommended by somebody to post questions on these forums only to be smartly told to use google. Of coarse I agree one should do research on their own before asking here but, I see some "members of the community" seem to to get annoyed by questions they deem "stupid" and/or repeated questions. 

If you don't want to post and help people on the forums don't. The forums are here to answer peoples questions. Don't whine you don't get paid. Lets be realistic most "community members" are nothing more than Ubuntu users filled with self importance. Not computer techs or Linux programmers. The fella that asks a question last week calls the next person stupid when they ask a similar question a month later. I see the same attitudes on other forums I belong to as well. It's ugly and serves no one!

In fact I have helped another member with a problem when he couldn't get Firefox 2 extensions installed. I had the same problem the day before. I have a hard time imagining he and I were the first two people ever to run in to this problem, though you wouldn't know it by the answers that were posted. When a user that has been using Ubuntu for a few days is the only one answering another person's question there is a serious problem with "the community".

Add in the signal to noise ratio when you search on a particular topic leads me to believe there is a lot of people who think they are "in the know" tooting their own horns.

Remember, peoples attitudes can and are sometimes affected by the environment.

Let me end by saying this post is not aimed at anyone particular. It is not meant to be a complaint, but simply how I perceive and possibly others see things. It may even help the forums be a more welcoming place.

Thanks and Regards,
Jason

---

### Post by jinchoung on 2008-05-27
> **lswest said:**
> 1.  Chances are that command causes a problem for other people who do not have your hardware, so it's not enabled for default.

y'know, you try to sound authoritative in your post and all but you start with "Chances are..." ???

lol...

do you know or don't you or are you just talking out of your butt and therefore not contributing any useful information.

WHY IS IRQ POLL NOT IN THERE?

if you don't know, do you know how much you're helping by throwing in "CHANCES ARE"?

ugh, this is the kinda thing that makes the signal to noise ratio on linux topics so ludicrous.
--------------------------------------------------------------
as for my tone, after my apologies had been made, it was not directed at anything or anyone besides ubuntu.

why do YOU take that personally?  are you even a developer?  do you have any stake in ubuntu at all such that a frustrated barb at the software would in any way bother you?

at this point, this is your problem.  not mine.  good luck with that.

jin

---

### Post by jinchoung on 2008-05-27
> **DMK62 said:**
> If linux is causing the level of frustration displayed in your posts then you may be better off not using it at this point in time. 


yep.  i've said this in my previous posts myself.  alas, just when i thought linux was ready for prime time... maybe next time.

> **DMK62 said:**
> When you attack the OS and the developers you ARE also attacking many of those involved with the community so expect it to be taken personally.

why?  this is not at a NECESSARY effect and imo rather unhealthy for those who take personal offense when they are not actively involved in development... but alas, human nature i suppose.

i heard some lady got shot for wearing the wrong baseball team's cap at a bar a few weeks ago....  same thing i guess.

duly noted.

jin

---

### Post by issih on 2008-05-27
Actually, as the kind of person who uses "chances are" and other such caveats a lot of the time, he was giving you a perfectly sound, rational explanation as to why an option may not be turned on by default. With modern hardware, what makes one computer work can just as easily break another, these things are not all the same, they are made up of a random mess of hardware and firmware from a whole myriad of different manufacturers. Your computer is potentially as unique as you are, and can have issues all of its very own, especially if just one component on that motherboard is a bit out of tolerance.

The poster didn't know, and nor do I know the exact reason why that specific option amongst the thousands and thousands of possible ones that make up a specific distribution is disabled by default, and it is a shame that it made your experience of ubuntu more troublesome. But if it is something that would cause trouble for the majority of users then it is obvious why it would be turned off.

It is possible it could be turned on by default and no great harm would be done, but I don't know that, do you? You are ranting that it is off, with no proof it would be safe to turn it on for the majority of cases.

Calm down, and stop looking for a fight, I guarantee you there are plenty of people using Linux who are looking for a newbie bug to squish for being impertinent. This isn't windows, and it isn't perfect, sadly there are issues, some of them major, but mostly these arise because of the state of the industry, and the massive difference between a specially tweaked pre-installed version of an OS, and one that has to try and be able to run and installed from a cd thrown into any machine on the planet. Nowadays we think that internet access and working graphics are the bare essentials, but honestly windows as a bare install is not much better than what you have experienced here, its the configuration of the machine by the manufacturer that buys you the easy life. Getting wireless to work can be a PITA, I know, I am fighting it myself, and not getting very far, but sadly that is life. If you can't stand it, use windows, use a mac. People are disinclined to help if you attack something they like, and people with knowledge generally started where you are, and had to fight through all those same problems. In no way is  canonical trying to make you hate them, but in the end they didn't make ubuntu just for you either. Its got to cater for as many people as possible, and sadly that means almost everyone has problems if one form or another.

---

### Post by kk0sse54 on 2008-05-27
If the liveCD doesn't work for you then usually it's an indicator that you should try another distro instead of trying to fighting and just ending up fustrated. Even if Ubuntu doesn't seem to want to cooperate with you there are hundreds of other distros you can try.

---

### Post by jinchoung on 2008-05-27
> **eldepeche said:**
> A quick Google search indicates that on a desktop machine, there is a small performance hit if you use the irqpoll boot option, and it can be more pronounced on older hardware. 

I have an ATI Radeon X800, and Compiz works perfectly out of the box. For most graphics cards, the Restricted Drivers Manager will pop up and say  that proprietary drivers are available; I'm not sure why it didn't for you. That is indeed a usability problem, and you may want to file a bug if you can reproduce that behavior.

The developers have tried very hard to make a collection of software work well on a large number of machines. Most of the posts in this forum are about the same 10 common issues, and are answered pretty quickly. You are one of the unlucky ones, but if your issues are now fixed, maybe you'll stick around, and next time you'll buy a computer with Ubuntu pre-installed, or at least do some research and buy compatible hardware. It definitely takes some work to be a dedicated Linux user, but you're past the tough part now.

it might not have popped up a prompt or failed to carry out its mission because of my particular combination of problems - namely no net access due to wifi.

this imo is a big usability issue too... if your distro is heavily dependent on net access for full functionality - at this particular point in time with the proliferation of wifi devices, it might be an extremely bad dependency indeed.

would be nice if, since ubuntu won't allow restricted drivers on the default install disk, they pile them onto a separate iso that can be downloaded and burned so that people without the capability to get net access will have an easy way to still get a fully functional ubuntu.

anyhoo, thanks for the info and pep talk.

jin

---

### Post by aysiu on 2008-05-27
> **Ballistixx said:**
> 
I have asked a couple questions and never mind not being answered they weren't even read. I asked the questions politely and to the point. On the contrary, your three posts have been read an average of about 60 times each. One has one reply, one has six replies, and one has eight replies. The one with eight replies is marked [SOLVED]

---

### Post by inportb on 2008-05-27
What aysiu said makes sense. UF is a great resource; use it.

Now, you might want to follow this thread to find out why it's bad to specify irqpoll by default: [http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-11/msg00912.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-11/msg00912.html)

GRUB does not have to install itself into the MBR. GRUB is perfectly fine installed to a partition.

> **jinchoung said:**
> would be nice if, since ubuntu won't allow restricted drivers on the default install disk, they pile them onto a separate iso that can be downloaded and burned so that people without the capability to get net access will have an easy way to still get a fully functional ubuntu.

Remember, licensing issues prevent distribution of said software packages.

> **jinchoung said:**
> why?  this is not at a NECESSARY effect and imo rather unhealthy for those who take personal offense when they are not actively involved in development... but alas, human nature i suppose.

i heard some lady got shot for wearing the wrong baseball team's cap at a bar a few weeks ago....  same thing i guess.

One does not have to be a programmer to be actively involved in development. Not only do the forum members provide support, but they also test software and submit bug reports. If this is not direct involvement, I'm not sure what is.

BTW, did I hear you say you had an Eee? If so, take a look at this: [http://www.eeebuntu.org/](http://www.eeebuntu.org/)

---

### Post by jinchoung on 2008-05-27
> **issih said:**
> Actually, as the kind of person who uses "chances are" and other such caveats a lot of the time, he was giving you a perfectly sound, rational explanation as to why an option may not be turned on by default.

my point is, it's speculation.  i DON'T KNOW.  that's why i asked.

anyone can speculate.  i can speculate.  we can all speculate.  i speculated before i came here that it was a stupid omission that probably does greater harm by its absence than its inclusion.  now that we have all speculated, how much closer to the answer are we?

it just makes noise that makes the actual answer harder to see.

i don't really have a problem with speculation per se but in the context of someone trying to "put me in my place", it struck me as comedic.

jin

---

### Post by jinchoung on 2008-05-27
> **inportb said:**
> 
Now, you might want to follow this thread to find out why it's bad to specify irqpoll by default: [http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-11/msg00912.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-11/msg00912.html)


seriously?

the other option for the guy is that ubuntu does not install or boot up AT ALL.

so in that case, what the developers SHOULD HAVE MAYBE PONDERED is this:

- in one case, EVERYBODY takes a small performance hit but they can boot up and install.
- in another case, a pretty large subsection of users will not be able to boot up AT ALL.  possibly their VERY FIRST FORAY into linux is stopped stone cold dead at INSTALLATION.  ?!?!?!
-----------------------------------------------------------------

OR - they could have done the IDEAL THING and include prompts DURING INSTALL that say,

"hey, if you get dumped into busy box while trying to boot livecd or install, you're gonna have to reboot and come to this screen again, but when you do, add the words 'irq poll' - then you'll be golden."

seriously, it is the HEIGHT OF NEGLIGENCE to let a product get out the door with a non rare problem like this not being addressed.  this is a showstopper that stops the show before it even gets started for heaven's sake.
----------------------------------------------------------------

as for licensing issues for restricted drivers - WHAT LICENSING ISSUES?

mandriva includes them (though fedora 9 does not).

and in shuttleworth's blog, it sounds like the issue is one completely of canonical's own choice rather than any license restriction.

and even if it IS a license restriction, repos carry it right?  so just set up a non canonical official webspace that carries the iso with restricted drivers for the sake of no-internet wifi schlubs who'll have to download in windows and burn a disk.

at least then, they can have a fully functional ubuntu setup without net access.

seriously, the thing that offends me most is evidently NOBODY ELSE THOUGHT ABOUT THIS....

???
-----------------------------------------------------------------

as for my comments on grub - i realize completely that i am being extremely undiplomatic.

i'm sure it works fine for lots of folks and blah blah blah.

but it doesn't work for me.

i tried replacing the mbr.  i tried installing it on a non mbr partition.  pretty much everything i could try i tried.

but if it's NOT in mbr, it never booted grub.  just goes straight to winxp.  and if i got grub by putting it in the mbr, it would never let me boot win.  supposedly you should be able to, it wouldn't let me.

it's hard.  it's technical.  my mother would NEVER EVER EVER be able to do it.

THAT BEING THE CASE,

grub4dos seems like a FAAAAAAAAAAAAaaaaaaaaar better, IDIOT PROOF way for win folk to dual boot into linux.

don't we like idiot proof?

jin

p.s. re eeebuntu, thanks but no thanks.  i hear there are wireless issues there as well and i'm really really tired of wireless issues.

---

### Post by DMK62 on 2008-05-27
It's next to impossible to cover every base with installations. Try installing windows and not having drivers for controllers etc that are not included on the windows cd and see how far it gets. Nothing is foolproof. There is also alternate cd's for Ubuntu for systems with lower memory specs or for computers that will not work with the live-cd. 

[http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)

That link will explain how software is released under the GPL. Items such as video card drivers and drivers for wifi are more than likely going to be closed source / proprietary. Some distributions include them but that is their decision about how tightly they adhere to the GPl and Open Source. There has been countless hours spent by developers and volunteers to reverse engineer and develop drivers for hardware on linux. Ubuntu does offer the closed source drivers but they do not support the drivers and you are notified when installing of them not providing support. It's not easy to support something when the company will not release the full code for their drivers. When it involves codecs and other closed source packages then it is the decision of the user.

As to your reply to my previous post. Some people take their operating system very personally. Others contribute on the forums here day in and and day out and it can be frustrating when someone is openly negative about Ubuntu. The last month has not been the best here with the release of Hardy Heron. I have seen tempers flare and personal attacks increase dramatically during the last month. It's usually a much friendlier  forum.

Use whichever operating system that works the way you want. Take a couple days, weeks, months ... away from Ubuntu / Linux and give it another try if you are still interested. I know what it feels like to be frustrated with an operating system , application, or hardware. I have sworn at this computer more times than I probably want to know. I've given it names that would probably get me banned from the forums if I repeated them here. I have also learned that at that point it's best just to walk away and clear my head and when that urge to hard boot it out the window is gone I will return and work on the problem.

Dale

---

### Post by Enriquecaribe on 2008-05-27
yea, Dale is right.
If you go out and just buy a plain Vista or XP cd, no driver will work. I know so, I used to use Vista and nothing worked out the box.

Ubuntu, imo, is awesome. I just log into the forms, post what I need, and BAM someone is there to help. I got HD video editing in linux. Thats really hard to get unless your Dreamworks, Disney, or Pixar.

I just recently got my wireless working on my HP laptop, and Ubuntu detects better networks, imo, because with windows, It only read 3 networks, My laptop with ubuntu detects 20 local wireless netorks.

but I guess its a matter of opinion. I just love my open source desktop.

---

### Post by Ballistixx on 2008-05-27
> **aysiu said:**
> On the contrary, your three posts have been read an average of about 60 times each. One has one reply, one has six replies, and one has eight replies. The one with eight replies is marked [SOLVED]

Hello Aysiu,

I said a couple of questions. The third was answered actuall reconfirmed my own.
Have you read the replies from the other posts, and who they are from, mostly me. Others are try turning the "alsa volume up" quality answers or sorry I can't help. Were they sincere? Of that I have no doubt. There also very well may be some newer answers since I last checked, which I will read, and politely respond to. 

Certainly as time goes on I am sure more people will read the posts, if from nothing else boredom. More likely in hopes that it will some how help their own similar problems, perhaps from a search. 

Some issues are time sensitive. Immediate help is why most people post their questions here. Perhaps someone might have dealt with the same issue so they pass that knowledge on and it spreads. Then everyone can reminisce how tuff things used to be.  That is how you learned to speak,read and write. No one owes me anything,I owe no one, so everything is fine, meaning I don't expect anything.
 
Now on to the ever prevailing attitude that was meant to be the main theme of my post! You display this contempt so eloquently one could almost assume you invented the behavior. I don't dare ask of your status in this "community" I often hear people speak of. You totally changed my mind with your most welcoming post. Seriously though, and you can get mad, but it's how I see things. I doubt I am the only one. I read more posts than my own, and the writings on the wall so to speak...When you try to discredit my experiences by saying 80 people read a three day old post in a community of thousands that is sad. We both know 80 is a very generous and exaggerated number. Did you read the posts or just looking at the numbers? That is it for me on this.

Aysiu, I sincerely hope you have a wonderful day/evening and what ever deity you hold true bestows blessings upon you. (Or not if you are not into that kind of thing!)

Kind Regards,
Jason
Ballistixx

---

### Post by inportb on 2008-05-27
Dude, WHAT'S WITH THE CAPS? If your caps-lock is on, TURN IT OFF. If you haven't learned the proper manners when posting on forums, MAYBE YOU SHOULD. IT IS VERY ANNOYING WHEN YOU SHOUT LIKE THIS.

> **jinchoung said:**
> so in that case, what the developers SHOULD HAVE PONDERED is this:

- in one case, EVERYBODY takes a small performance hit but they can boot up and install.
- in another case, a pretty large subsection of users will not be able to boot up AT ALL.  possibly their VERY FIRST FORAY into linux is stopped stone cold dead at INSTALLATION.  ?!?!?!

Maybe, just maybe... what you should have pondered is this:

- in one case, we have the greatest good for the greatest number
- in the other case, everybody ends up with inefficient systems, just to satisfy the very small number of selfish individuals who are *also* not willing to ask questions

I've had my share of troubles when starting with Ubuntu, and I can understand how frustrating it is to have a system that does not boot or install. I've been there, and I still get annoyed at this ATi chipset from time to time. Many of us have been there. Therefore, we try my best to answer questions accurately. If you don't ask, you're just going to end up spending a lot more time. And if your attitude is that everyone must bend to your desires, it is no wonder that you don't seem very satisfied with your life.

> **jinchoung said:**
> "hey, if you get dumped into busy box while trying to boot livecd or install, you're gonna have to reboot and come to this screen again, but when you do, add the words 'irq poll' - then you'll be golden."

Seriously, if that were the only issue one can run into, I'm sure it would have been done. In reality, everyone has a different hardware setup that can behave differently and may require different techniques. This is why, instead of dumping screenfuls of alternatives at you, Ubuntu has a helpful forum that is full of knowledge about these things. Again, if you don't use these resources, you can't really blame anyone but yourself.

> **jinchoung said:**
> seriously, the thing that offends me most is evidently NOBODY ELSE THOUGHT ABOUT THIS....

I have a feeling you think you're the smartest person here, to have thought of this brilliant idea first. But really, you can't even substantiate your assumptions.

> **jinchoung said:**
> and if i got grub by putting it in the mbr, it would never let me boot win.  supposedly you should be able to, it wouldn't let me.

Have you raised a thread about it? Why not? You seem to have enough technical knowledge to describe your situation.

> **jinchoung said:**
> it's hard.  it's technical.  my mother would NEVER EVER EVER be able to do it.

Sorry, but when my mother runs into these issues, she calls me up and I fix them. What kind of son/daughter are you to not even consider helping your mother?

> **jinchoung said:**
> p.s. re eeebuntu, thanks but no thanks.  i hear there are wireless issues there as well and i'm really really tired of wireless issues.

Are you telling me that you've got everything figured out on your current system? If so, that's great. If not, why are you dismissing eeebuntu? It's just Ubuntu fixed to work better on Eee's. Wouldn't you like to have fewer problems?

---

### Post by nachomania on 2008-05-27
There are hundreds of developers taking their OWN time to work on this, along with tons of people testing. 
     It doesn't work for everyone. If Mandriva worked for you, use it, but don't aggravate others. I switched through different distros six times, and it doesn't help to blast one.
     If you installed the bloody restricted packages (mp3s, etc) you'd find out that they come with a disclaimer. Read it some time. 
     If hardware doesn't work on the LiveCd, chances are it won't on a hard install. IF there are any possible users reading this, take note. Research on the forums before you even insert the ubuntu disc.
     Linux in general has a bit of a learning curve, but most people can get into it. There are lots of people working hard to try and make it easier for new users, but there are still cracks. 
     People are honestly trying their best to solve problems on these forums. Don't blast them.

---

### Post by sink on 2008-05-28
I am glad my ubuntu work out of the box!! :)

(well, except my wacom tablet, but I installed it by following instructions on the forum)

:guitar:

---

### Post by pbpersson on 2008-05-28
Linux - even Ubuntu - is still a work in progress.

It works for most people most of the time.

Anyone who does not want to put some real effort into this should just walk away at the first sign of trouble.

Now.....as to some of the comments here - the entire concept of the computer displaying a message, "oh, if you are having this problem, try this solution..." - I think that is nonsense.

I have been developing software for 25 years and my point of view is if the computer gives me an error and the developer knows what the solution might be, the **COMPUTER** should try to fix it, not me.  The entire concept of the computer telling me what to type at the keyboard is silly - it should just try a list of possible solutions for the problem to see which one will work in this situation.

I am certain that is the goal for some future release many versions from now.  If it is not, it should be.

I am just thrilled with the progress Linux has made over the years - it is like a different world from what it was eight years ago.

---

### Post by mdsmedia on 2008-05-28
> **jinchoung said:**
> 
grub4dos seems like a FAAAAAAAAAAAAaaaaaaaaar better, IDIOT PROOF way for win folk to dual boot into linux.

don't we like idiot proof?


What if the person installing is not using Windows, and therefore no Windows MBR?

Is this only necessary for dual-booting? I thought GRUB was installed for all Ubuntu installations?

---

### Post by jinchoung on 2008-05-28
> **mdsmedia said:**
> What if the person installing is not using Windows, and therefore no Windows MBR?

Is this only necessary for dual-booting? I thought GRUB was installed for all Ubuntu installations?

grub IS installed for ubuntu installations and YES, i said that this would be for win users trying to dual boot.

if you're not doing dual boot, grub4dos offers no advantage.

going the grub4dos method is imo a very nice tip of the hat canonical (and all linux distro makers actually) can give to windows users that might want to check out what's on this side of the fence.

which i would imagine is not a negligible number.

jin

---

### Post by jinchoung on 2008-05-28
> **pbpersson said:**
> 
I have been developing software for 25 years and my point of view is if the computer gives me an error and the developer knows what the solution might be, the **COMPUTER** should try to fix it, not me.  The entire concept of the computer telling me what to type at the keyboard is silly - it should just try a list of possible solutions for the problem to see which one will work in this situation.

wow... i really could not agree with you more.

but if you'll look at the latest responses, the consensus seems to be that it's IMPOSSIBLE to accommodate all configurations of all systems.

which is a completely reasonable assertion.

SOOOoooooo... considering that so many people are encountering this particular issue (just google busybox and ubuntu and marvel at not only the number of problems but the spectacular array of misguided advice) i say, forgo the perfect for the good and drop in such friendly little notes.

jin

---

### Post by jinchoung on 2008-05-28
> **inportb said:**
> And if your attitude is that everyone must bend to your desires, it is no wonder that you don't seem very satisfied with your life.

lol.  oops, i mean LOL.

classy.  good one.  you really showed me.  ouch.

jin

---

### Post by 3rdalbum on 2008-05-28
1. It's rare that IRQPOLL needs to be put into your kernel arguments. There are good reasons to leave it out if you don't need it, so I think the Ubuntu team have the right idea. They should document IRQPOLL if they haven't already and put it into the "Other booting options" menu. I wouldn't be surprised if IRQPOLL causes your second problem of GRUB not automatically finding your other partitions...

2. I've never had any problems with GRUB finding and being able to boot Windows and Linux - I think this might be a case of user error. It's certainly a case of "Anything regarding bootloaders is a horrible kludge anyway because our computers use unfriendly technology from the 1980s".

3. Your proprietary graphics card drivers are not loaded. Go to Hardware Drivers in the System > Administration menu and enable them. Mandriva loads them at startup if needed, which can cause other problems, and it's actually a slightly grey area legally.

There are graphics cards with free software drivers, where Compiz works out-of-the-box.

4. Rather than try for weeks with an incompatible chipset, why not spend $30 and buy something that is known to be compatible?

---

### Post by jinchoung on 2008-05-28
> **Ballistixx said:**
> Hello Aysiu,

I said a couple of questions. The third was answered actuall reconfirmed my own.
Have you read the replies from the other posts, and who they are from, mostly me.

YIKES!  my condolences....

that's a real shame.  hope you can find your way through linux a bit better than i am....

jin

---

### Post by dnairb on 2008-05-28
Regarding the Belkin wireless thingy:

I have seen/tried 3 different versions (the version number should be on a sticker on the outer box):

Version 3 (or 3002 or similar): works-ish out-of-the-box but has no support for encryption (WEP or WPA/2)

Version 4 (or 4001, 4002, etc.): works out-of-the-box. Period.

Version 5 (or 5001, etc): requires ndiswrapper and Windows driver.

I hunted around at various stores, checking each box I found and managed to find version 4 adapters.

Hope this helps...

---

### Post by jinchoung on 2008-05-28
> **3rdalbum said:**
> 1. It's rare that IRQPOLL needs to be put into your kernel arguments. There are good reasons to leave it out if you don't need it, so I think the Ubuntu team have the right idea. They should document IRQPOLL if they haven't already and put it into the "Other booting options" menu. I wouldn't be surprised if IRQPOLL causes your second problem of GRUB not automatically finding your other partitions...

2. I've never had any problems with GRUB finding and being able to boot Windows and Linux - I think this might be a case of user error. It's certainly a case of "Anything regarding bootloaders is a horrible kludge anyway because our computers use unfriendly technology from the 1980s".

3. Your proprietary graphics card drivers are not loaded. Go to Hardware Drivers in the System > Administration menu and enable them. Mandriva loads them at startup if needed, which can cause other problems, and it's actually a slightly grey area legally.

There are graphics cards with free software drivers, where Compiz works out-of-the-box.

4. Rather than try for weeks with an incompatible chipset, why not spend $30 and buy something that is known to be compatible?

howdy,

argh... please read earlier in this thread about RESTRICTED DRIVERS.  there have been several people here go into the reasons why they are NOT included.

mandriva DOES include them in the default install.  it is NOT merely a matter of turning them on.  again, go back several messages and read the link to mark shuttleworth's blog about WHY they're not included... (ugh)....

re: your specific suggestion, i tried it.  with my nvidia card, it does NOT turn on.  i can't activate it.

i have a feeling that my setup of multiple hard drives and or SATA is necessitating the irq poll and i DO think that the grub issue is related to my hardware configuration... but i don't think it's the irq poll.

and in any case, it's irq poll or nothing so can't see anyway around this without any alternatives before me.

regarding 4) eh..... if that's what the linux community is waiting for get into "prime time", they're gonna be waiting a looooooooooong time.  sorry to say, that's just not how most people work (linux as priority) and it's certainly not how i work.

it's something that i just have fond wishes for and try out every now and again with what i have at hand.

if anything is gonna do the accommodating in this scenario, it would have to be linux to me not the other way around.

jin

---

### Post by jinchoung on 2008-05-28
> **dnairb said:**
> Regarding the Belkin wireless thingy:

I have seen/tried 3 different versions (the version number should be on a sticker on the outer box):

Version 3 (or 3002 or similar): works-ish out-of-the-box but has no support for encryption (WEP or WPA/2)

Version 4 (or 4001, 4002, etc.): works out-of-the-box. Period.

Version 5 (or 5001, etc): requires ndiswrapper and Windows driver.

I hunted around at various stores, checking each box I found and managed to find version 4 adapters.

Hope this helps...

thanks it does.  haha, i have version 5.

but as i said, ndiswrapper gets me to see access points and MY access point but run into "no dhcpoffers"... and if you google that + "problem" + "ubuntu", you get a looooooooooooooooong list... : )

jin

---

### Post by Artsaypunk on 2008-05-28
You know, I'm really hesitant to say anything in an angry thread like this one, especially as I'm relatively new to Ubuntu, and I really don't want to suggest something and get my head bitten off... but Jin, you seemed to indicate at one point that half your frustration was that you couldn't download and install restricted drivers etc, because of your wireless problems.  I can see how that would be frustrating, since an internet connection is essential to solving any Ubuntu problem.  However, maybe this is a really stupid question, but is there a way for you to temporarily plug in to a wired connection, allowing you to work on your issues without having to download things seperately within XP?  I feel like it's too simple to point out, but oh well.

I have an ATI video card, for which Ubuntu generally gives you a kind pat on the back and says, "Sorry, please try again later" when the next version of the driver comes out.  In fact, I'd almost guess that there are more ATI based threads on these forums than anything else.  So I understand the frustration.  That being said, I knew what I was getting into when I decided to make "the switch."  With a laptop, I knew I'd have to do some learning and do some troubleshooting.  I didn't expect everything to work "out of the box" like I would with a commercial OS, in fact, I was surprised at how much actually did "just work."   I don't even have everything working the way I'd like yet, but everything that is working is fantastic, so I have faith.

I would like to add however, that although I disagree with the tone and attitude of this thread, I do believe that one area in which Ubuntu is severely lacking is documentation.  As a relatively new user, I agree with you on that one.  From what I've seen, Ubuntu has come an amazing way in a short time, and I can understand why documentation might not be a priority over getting things up and running. Community support is great, but internal documentation is weak. Unfortunately, I have never seen documentation mentioned in improvements for upcoming versions, which worries me a bit.  Error messages DO need to be clearer, manuals DO need to be geared toward new users.  I don't know how many times I have searched the forums or the Interweb, only to find an extremely simple answer hidden in a menu somewhere.  

Perhaps the difference though, between you and I, is that I would love to be a part of making Ubuntu better.  I think what has been accomplished with this operating system is incredible, but there are many things to keep working on.  I'm no programmer, my skills lie in writing and editing, so my goal is to learn enough about Ubuntu, and Linux in general, to be able to contribute to help in writing clear and concise documentation some day.

By the way, does anyone know how I might go about pursuing something like that?

And Jin, don't be so angry man.  If you're beating your head against a wall on getting this working, then it'll feel amazing when you stop.  I think that if you've invested this much time into your troubles, and don't seem to be getting anywhere, maybe you should stick with what works for you and check back in with Ubuntu after the next release.  Good luck with everything.

---

### Post by mdsmedia on 2008-05-28
> **jinchoung said:**
> grub IS installed for ubuntu installations and YES, i said that this would be for win users trying to dual boot.

if you're not doing dual boot, grub4dos offers no advantage.

going the grub4dos method is imo a very nice tip of the hat canonical (and all linux distro makers actually) can give to windows users that might want to check out what's on this side of the fence.

which i would imagine is not a negligible number.

jinSo, what you're saying is, Ubuntu should make grub4dos default, so that Windows users will be less inconvenienced?

Ubuntu is Linux. Windows is Windows.

I'm a long time Windows user. I'm a short time Linux user. I had no problem installing dual-boot with XP on my HP laptop, or my no-name desktop.

I've seen very few cases of GRUB being a problem. I'm not an experienced user, but Ubuntu isn't here to cater for people wanting to dual-boot. It's a Linux distribution for people to use Linux. If GRUB doesn't suit your purposes, use grub4dos. It works for you, so use it. 

What you want Ubuntu to do is set a program as default that's aimed at dual-booters. That doesn't make any sense. As someone else said earlier, all it does is setup GRUB for Windows users by altering a Windows file. This ISN'T Windows. This is Linux.

---

### Post by mdsmedia on 2008-05-28
> **jinchoung said:**
> howdy,

argh... please read earlier in this thread about RESTRICTED DRIVERS.  there have been several people here go into the reasons why they are NOT included.

mandriva DOES include them in the default install.  it is NOT merely a matter of turning them on.  again, go back several messages and read the link to mark shuttleworth's blog about WHY they're not included... (ugh)....

re: your specific suggestion, i tried it.  with my nvidia card, it does NOT turn on.  i can't activate it.

i have a feeling that my setup of multiple hard drives and or SATA is necessitating the irq poll and i DO think that the grub issue is related to my hardware configuration... but i don't think it's the irq poll.

and in any case, it's irq poll or nothing so can't see anyway around this without any alternatives before me.

regarding 4) eh..... if that's what the linux community is waiting for get into "prime time", they're gonna be waiting a looooooooooong time.  sorry to say, that's just not how most people work (linux as priority) and it's certainly not how i work.

it's something that i just have fond wishes for and try out every now and again with what i have at hand.

if anything is gonna do the accommodating in this scenario, it would have to be linux to me not the other way around.

jinAll I see here is you wanting everything bent to suit your situation. Sorry, it doesn't work that way. If you're concerned about Linux gaining another user, don't be concerned. It's still the best OS out there bar none.

I've read this whole thread, and it seems to be all about YOU. Not about Linux. It's not about Linux being ready for the masses, it's about Linux bending to meet your needs.

If you're not happy with the Ubuntu philosophy, please feel free to use another distro which does. Don't expect Ubuntu, Canonical, Mark, anyone, to change, just because that's what you think should happen. You've expressed your distaste for the Ubuntu philosophy. So GO SOMEWHERE ELSE. There are hundreds of distros out there. Why pick on Ubuntu, just because it's not as unethical as you want it to be?

---

### Post by Samhain13 on 2008-05-28
> **It's not about Linux being ready for the masses, it's about Linux bending to meet your needs.**

+1

I was thinking about saying this a few pages back. Troll, I say. Let us not feed it. :)

---

### Post by inportb on 2008-05-28
It's okay to want a tool to work the way you work, and most people do. However, most recognize that it's not always possible and make compromises. If one can be just a little bit flexible, one would achieve a lot more than if one would rigidly clash with everything.

jinchoung is less newbie than selfish. I definitely detect the technical knowledge. Yet, here is a person who is not willing to interface with other individuals or with the community at large. This is not a problem with Ubuntu, Linux, or computing in general. This is a problem with being human on this planet. (Heh, troll's an appropriate title.)

---

### Post by stalkingwolf on 2008-05-28
> IF web access was never an issue, then sure, they could assume that the proper drivers will just get loaded... but because of wifi, this is NEVER THE CASE IN THIS PERIOD IN TIME.

I have installed every ubuntu distro from 6.06 on and never had an issue with wifi working. in all but 2 cases out of the box.  In those 2 cases 5 min. in configuration fixed the problem.

Now on to your problem.  after about 15 min. of google search
it appears that the problem is not Ubuntu, nor even Linux.
It would seem that the problem is with the chip set.  It would also appear that the driver problem is not limited to Ubuntu or Linux.
there are abundant references to problems in Leopard,Vista,XP, and even the venerable 98.

I did a google search for
rtl8187b driver linux( the chipset for your adapter which i found by googling Belkin F5D7050 v5) and found these 3 work arounds.

[http://danmarner.blogspot.com/2008/01/rtl8187b-linux-native-driver-works-on.html](http://danmarner.blogspot.com/2008/01/rtl8187b-linux-native-driver-works-on.html)

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek)

[http://ubuntuforums.org/showthread.php?t=571046&page=5](http://ubuntuforums.org/showthread.php?t=571046&page=5)

maybe my Google goes to adifferent place than yours does?:biggrin:    :-k

As to your poll command, in the 10 or so installs I have done on various systems in the last few weeks, many with multiple drives, 2 with mixed ata and sata drives I have never had to use that command.  Nor have I had any problem with Grub.  So once again I must conclude it is an issue with your hardware or your configuration.  Not an Issue with Ubuntu.

My remote diagnosis would be that " There is a terminal failure
in the primary input device caused by a short between the chair and the keyboard."

---

### Post by jinchoung on 2008-05-28
> **mdsmedia said:**
> What you want Ubuntu to do is set a program as default that's aimed at dual-booters. That doesn't make any sense. As someone else said earlier, all it does is setup GRUB for Windows users by altering a Windows file. This ISN'T Windows. This is Linux.

so why do they have wubi then?

*BONK*

pfffffft....

jin

---

### Post by jinchoung on 2008-05-28
> **mdsmedia said:**
> All I see here is you wanting everything bent to suit your situation. Sorry, it doesn't work that way. If you're concerned about Linux gaining another user, don't be concerned. It's still the best OS out there bar none.

I've read this whole thread, and it seems to be all about YOU. Not about Linux. It's not about Linux being ready for the masses, it's about Linux bending to meet your needs.

If you're not happy with the Ubuntu philosophy, please feel free to use another distro which does. Don't expect Ubuntu, Canonical, Mark, anyone, to change, just because that's what you think should happen. You've expressed your distaste for the Ubuntu philosophy. So GO SOMEWHERE ELSE. There are hundreds of distros out there. Why pick on Ubuntu, just because it's not as unethical as you want it to be?

lol... "unethical"... okay, so you're not a fundamentalist.... got it.

anyhoo, as for the selfish thing - it sounds that way doesn't it?

it really does.

but then you do a google search for terms relevant to the problems i've been having.

see how many hits you come up with.
-------------------------------------------------------------

it SOUNDS selfish because i am not prefacing the whole thing with why i think it is a wise thing to do and all that jazz... it's too boring to do that.  besides, this started as a mildly frustrated rant that got fueled by fanboy prodding and so here we are.

but what i propose is NOT purely so that an entire distro can accommodate ME.

i propose what i propose because i am a representative sampling of a NOT INSIGNIFICANT NUMBER OF USERS WHO SUFFER THE SAME PROBLEMS.

i'm not lyin'.  all i've been doing for the weeks when i was struggling with all this stuff is googling.  and i'm not the only one.

and as i say, it is truly TERRIFYING the kinds of answers that are being thrown out to folks who possibly may know less than i do.  everything from reformatting your hard drive to chucking it because it's probably broken....
---------------------------------------------------------------

so, as a distro, you can try to acknowledge a non-negligible problem and address it by providing more options or more blow by blow documentation.

or you can call me a troll and selfish and blah blah blah.

one route may endear the distro to more users and help get more folks into the linux movement.

the other results in "our way or the highway" vigorous high fiving each other as another newb walks away.

jin

---

### Post by jinchoung on 2008-05-28
> **stalkingwolf said:**
> 
As to your poll command, in the 10 or so installs I have done on various systems in the last few weeks, many with multiple drives, 2 with mixed ata and sata drives I have never had to use that command.  Nor have I had any problem with Grub.  So once again I must conclude it is an issue with your hardware or your configuration.  Not an Issue with Ubuntu.

My remote diagnosis would be that " There is a terminal failure
in the primary input device caused by a short between the chair and the keyboard."

nice.

great.  and so you're never having encountered the problem is just as valid as my having encountered it.

again, if we have the same google, google the irq poll thing.  am i the only name that comes up?

it's great that ubuntu works for so many people.  but that doesn't mean squat for the people for whom it doesn't.

you disagree?

jin

---

### Post by inportb on 2008-05-28
I agree. I also agree that it does not mean that you can start bashing Ubuntu because of it.

> **jinchoung said:**
> i propose what i propose because i am a representative sampling of a NOT INSIGNIFICANT NUMBER OF USERS WHO SUFFER THE SAME PROBLEMS.

A side note on significance: searching "irqpoll" on Google fetches 53200 results, whereas searching "linux" fetches 534000000. You do the math. I don't have enough statistics to comment on significance, and neither do you; but at least one can say that < 1/10000 is pretty small.

And for the < 1/10000 who have problems with this issue, most/many of them found answers either by asking or reading, but you're the only one who's getting riled up.

Another side note on significance: searching "+jinchoung +irqpoll" on Google fetches 4 results; recall that searching "irqpoll" fetched 53200. You do the math. Again, how can 1 represent > 10000? As they say, the sample size is way too small.

Feel free to substantiate your claims with numbers or statistics superior to my estimates.

> **jinchoung said:**
> i'm not lyin'.  all i've been doing for the weeks when i was struggling with all this stuff is googling.  and i'm not the only one.

We believe you. And this is why you haven't been getting answers. Post, dude, post.

> **jinchoung said:**
> the other results in "our way or the highway" vigorous high fiving each other as another newb walks away.

Well, you're not a newb. And we would not mind if you took the highway ;p

---

### Post by y6FgBn)~v on 2008-05-28
Good bye jinchoung, we wish you well, really we do :)

---

### Post by jinchoung on 2008-05-28
> **inportb said:**
> 53200 results, whereas searching "linux" fetches 534000000. You do the math.

wow, if you don't get why your little statistical comparison is ludicrously irrelevant, you're not smart enough to talk to me.

jin

---

### Post by ellalan on 2008-05-28
Hi Friends
I think most of you have misunderstood jinchoung, i do really sympathise with him. I am still hanging on with Gutsy because Hardy is not as refined as Gutsy on certain machines and it will take some time to do that. He is not bashing Ubuntu,he only cries out for help and venting out his anger.
Only person who really attempted to help him was Oedha the rest of you just having a go at him as if he is some sort of enemy of mankind. this kind of behaviour I have seen in some vista forums and I hate that. I would like to see this community grow in to a descent,tolerant and accommodating happy environment.
I know some of you might disagree with me,but what the heck! I always say what i believe is right.

---

### Post by jinchoung on 2008-05-28
> **ellalan said:**
> I know some of you might disagree with me,but what the heck! I always say what i believe is right.

ready for some predictable gratitude?

thanks!  appreciate it and pretty ballsy of you to step in front of a blood lusting forum lynch mob.  not a lot of folks would.

jin

---

### Post by inportb on 2008-05-28
> **ellalan said:**
> I would like to see this community grow in to a descent,tolerant and accommodating happy environment.
I know some of you might disagree with me,but what the heck! I always say what i believe is right.

Hey, I agree. Now about this decent, tolerant, and accommodating happy environment... I'm sure the OP could help with that.

> **jinchoung said:**
> wow, if you don't get why your little statistical comparison is ludicrously irrelevant, you're not smart enough to talk to me.

jin

And if you don't have anything to back your claims, you're not smart enough to post them.

Here, let me justify my data. Of the 534000000 pages about Linux, 53200 are about irqpoll. These numbers are not perfect because they represent not just posts seeking solutions, but general discussion as well. But since it's true for both sets, the quality of the comparison is improved.

Your claim is that the number of individuals experiencing irqpoll trouble is not an insignificant number; however, you fail to take the bigger picture into consideration. 53200 might seem a large number, but Google routinely returns resultsets comparable to these. At the same time, the number pales in comparison to the number of pages about Linux in general.

Why don't you substantiate your own claims instead of continuing to post empty statements? Or at least offer a valid objection against my data and an alternative set.

---

### Post by skeetwood-mac on 2008-05-28
Try linux mint. Its like ubuntu but it actually works. I switched to that after I figured out nothing works very well on ubuntu.

---

### Post by inportb on 2008-05-28
> **skeetwood-mac said:**
> Try linux mint. Its like ubuntu but it actually works. I switched to that after I figured out nothing works very well on ubuntu.

True; Mint is Ubuntu packaged with proprietary stuff. It looks like it might be good for you. And now that you know how to use the irqpoll option, don't hesitate to use it if anything ;p

I'll have to stop following this thread for a while, as I've better things to do. But I'll be back, my friend jin ;p

---

### Post by 23meg on 2008-05-28
[QUOTE=Artsaypunk]Perhaps the difference though, between you and I, is that I would love to be a part of making Ubuntu better. I think what has been accomplished with this operating system is incredible, but there are many things to keep working on. I'm no programmer, my skills lie in writing and editing, so my goal is to learn enough about Ubuntu, and Linux in general, to be able to contribute to help in writing clear and concise documentation some day.

By the way, does anyone know how I might go about pursuing something like that?
[/QUOTE]

[https://wiki.ubuntu.com/DocumentationTeam/GettingStarted](https://wiki.ubuntu.com/DocumentationTeam/GettingStarted)

---

### Post by jinchoung on 2008-05-29
> **inportb said:**
> Here, let me justify my data.

please.  don't.

again, if you don't understand why your procedure is flawed i really can't help you.

howabout going specific eh?

google ubuntu + boot + busybox   30,000 hits

google ubuntu + irqpoll + problem  110,000 hits

now the better thing to do than googling linux for f's sake is to find out how many people are using ubuntu.

don't know what the answer to that is.  but that would make MY google searches meaningful in comparison.

and then you can say - HEY, if 30,000 or less - to 110,000 or more problems are a negligible percentage - hey, go to it.  ignore.

jin

---

### Post by jinchoung on 2008-05-29
> **skeetwood-mac said:**
> Try linux mint. Its like ubuntu but it actually works. I switched to that after I figured out nothing works very well on ubuntu.

!!! THANKS!!!  i had no idea such a thing existed!  that's my next stop!  thank you very very much!

jin

---

### Post by mooha on 2008-05-29
jinchoung

Hey Man, you are the man ... really true ..

Over here people waste time defending Ubuntu instead of helping People, when I mean help, I mean a real fing help, they (not all of them) don't try to putt them selves in your disaster situation, they just reply by useless link, or READ DOCUMENTATION !! read it very well, it worked for me !!! bla bla bla

It's not important to any one of you (helpless replies), weer  are talking about Computers and software technology, for me ubuntu Forums is a big Mess.

the good example I experienced is with Grub + MBR, and the useless forums, for a long time I tried to understand you (useless helpers), I couldn't, maybe you better google first to learn how to help in Computer World !!! here you go try it  

jinchoung  you're the MAN,

---

### Post by jinchoung on 2008-05-29
thanks skeetwood-mac,

i downloaded linux mint last night and even though i still had to "irqpoll" to get it to boot...

<drum roll>

WIFI WORKS!!!  i had to resort to ndiswrapper again but after entering my wpa and set dhcp to auto boom!  i downloaded and upgraded packages, surfed the net, everything!  woooooo hoooooo!

so i guess the ubuntu distro for me is linux mint!

thanks much!

jin

---

### Post by CloudFX on 2008-05-29
Some news for you guys... Firefox Release Candidate is now available through Update Manager.  It fixes some major bugs.

---

### Post by 3rdalbum on 2008-05-30
> **jinchoung said:**
> or made an option with a helpful message that says, "hey, if you're having problems, try this..." ?

True, but there's already 3 screens worth of "If you're having problems, try this", and I believe the irqpoll thing is reasonably rare.

> 3.  why doesn't "DESKTOP EFFECTS" work out of the box.  i don't have an uncommon vidcard - it's an nvidia 7600gt... why doesn't it tell me WHY IT DOESN'T WORK?

I agree, there must be a description of why "Desktop Effects could not be enabled". I think it's actually an upstream problem, because I think Fedora does the same thing.

> does it work out of the box for ANYONE?

Yes, with integrated Intel graphics, and any other graphics chipset with open-source 3D drivers. With Intrepid Ibex this will include a bunch of ATI cards too.

I'm glad Linux Mint resolved your issues anyway. I've said it before and I'll say it again: Linux, like any operating system, is best used if it's been preinstalled on compatible hardware. I've built two different hardware configurations with no-worries Ubuntu, INCLUDING wireless out-of-the-box, so it's easy enough for OEMs to do. That's the real answer to things.

---

