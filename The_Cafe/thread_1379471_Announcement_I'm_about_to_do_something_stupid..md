---
title: "Announcement: I'm about to do something stupid."
date: 2010-01-12
forum: The Cafe
---

### Post by warfacegod on 2010-01-12
I'm going to resize my sda1 partition. I'm going to install 9.10 NBR as a dual with normal 9.10 on my laptop. Why you ask? Because I feel like it.
Can any one give me a decent partition size for NBR?


You see? This is what happens when you start computing with Windows. I start going:

"My Linux installs are perfect? There's nothing for me to fix? Sigh. Good grief, I am bored! Let me go screw up my laptop again so I can have something to do"

And that's after three years of being Windows free. Ubuntu: The Windows 12 Step Program

---

### Post by Puck7 on 2010-01-12
I totally feel you, I've messed up my laptop sooooo many times because I was bored.

Just for you I've booted my netbook to see how much space I've used since I installed UNR (May was the last date).

19G - That is 6 GB of movies, and some music documents and other stuff. So 10 GB is way enough for the cutie.

---

### Post by warfacegod on 2010-01-12
My laptop's internal is a mere 30 GB with 12 GB free. Can I get away with say, 6?

---

### Post by Puck7 on 2010-01-12
You could, my /home/ folder is 15,1 GB out of the 19.

---

### Post by J V on 2010-01-12
> **warfacegod said:**
> I'm going to resize my sda1 partition. I'm going to install 9.10 NBR as a dual with normal 9.10 on my laptop. Why you ask? Because I feel like it.
Can any one give me a decent partition size for NBR?


You see? This is what happens when you start computing with Windows. I start going:

"My Linux installs are perfect? There's nothing for me to fix? Sigh. Good grief, I am bored! Let me go screw up my laptop again so I can have something to do"

And that's after three years of being Windows free. Ubuntu: The Windows 12 Step ProgramI feel the same after only 6 months :(

---

### Post by warfacegod on 2010-01-12
> **J V said:**
> I feel the same after only 6 months :(

After three years I still catch myself saying: "Wait, *you can do that?* or "That's impossible in Windows." or my personal favorite "I'm getting really sick of fixing your Windows machine."

---

### Post by warfacegod on 2010-01-12
I stand before you utterly defeated. Perhaps... well, no, not humbled. It worked. Everything went exactly the way it was supposed to! Damn it! Now I'm sitting here bored again.

Resized sda1 creating unallocated space
Formatted unallocated space into 5 GB ext4 partition
Poked around in NBR Live environment
Installed NBR to new partition
Rebooted into new OS, poked around
Rebooted into old OS, poked around

Everything works perfectly!!!
I didn't even get to fix the stupid GRUB menu.
The install process didn't even complain about not creating a swap it just found my old one and used that.

Wait! I need to mess with GRUB to get normal 9.10 at the top of the list! Yeah!!! You cannot defeat me rock solid Linux operating system! Boowaahhaaahaaahaaaaa!!! (Runs off on tippy toes in maniacal glee)

---

### Post by warfacegod on 2010-01-12
Oh! The entire thing took just under an hour and 45 minutes. Resizing, installing, fooling around, etc.

I've set Windows to install and gone off to build a deck and it still wasn't done.

---

### Post by tom.swartz07 on 2010-01-12
I nominate this thread as my favorite of all time.

---

### Post by warfacegod on 2010-01-12
I second that nomination for your favorite of all time.

---

### Post by pizza-is-good on 2010-01-12
It's the beauty of linux, you can mess something up really bad, and then fix it.

I admit I like to have a smooth and bug free OS running, but my virtual box Ubuntu install is merely for playing around and messing things up just to fix them up again. Its so much fun...

---

### Post by warfacegod on 2010-01-12
> **pizza-is-good said:**
> It's the beauty of linux, you can mess something up really bad, and then fix it.

I admit I like to have a smooth and bug free OS running, but my virtual box Ubuntu install is merely for playing around and messing things up just to fix them up again. Its so much fun...

What's the world coming to when you can't break something just to fix it?

That's normally what my wife's computer is for but I figured I'd break my laptop for a change. Maybe I'll go put Windows on hers next to her Ubuntu. That should be worth a few days of fun!

---

### Post by Leppie on 2010-01-12
why don't you erase your mbr?
```
sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
```

then you can fix it ;)

---

### Post by tom.swartz07 on 2010-01-12
> **Leppie said:**
> why don't you erase your mbr?
```
sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
```

then you can fix it ;)

Or you could do a thread search for the fabled 'forbidden terminal commands'


unfortunately, most of them are related to just wiping your drive, but im sure there are some goodies there :D

---

### Post by warfacegod on 2010-01-12
> **Leppie said:**
> why don't you erase your mbr?
```
sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
```

then you can fix it ;)

Congrats on 1000+ beans.:popcorn::popcorn: Does that mean we can have a millennium party. Watch out for Y1K bug. :D

It's too late now. I'm gonna go the Grub route. See if I can screw it up in a righteous fashion. Now, where's my salt.

Ahh! Speak of the Devil. Update wants to know if I want to keep my current version of grub.

---

### Post by Leppie on 2010-01-12
thanks :)
how about LOTR marathon tomorrow nite? ;)

you could also try to resize the partition holding the /boot folder at the beginning of the partition.

---

### Post by warfacegod on 2010-01-12
> **tom.swartz07 said:**
> Or you could do a thread search for the fabled 'forbidden terminal commands'


unfortunately, most of them are related to just wiping your drive, but im sure there are some goodies there :D

I'm thinking of removing the hard drive while the computer is on.

---

### Post by warfacegod on 2010-01-12
> **Leppie said:**
> thanks :)
how about LOTR marathon tomorrow nite? ;)

you could also try to resize the partition holding the /boot folder at the beginning of the partition.

It did that already. When I resized sda1, it created 87 MB of unallocated at the beginning of the drive.

Your night and mine are like 6 hours apart, neither one of us would sleep for like 2 days. Cool sleep dep. LOTR.

---

### Post by Leppie on 2010-01-12
well, as the thread title says you really *are* about to do something stupid... :P

---

### Post by Leppie on 2010-01-12
> **warfacegod said:**
> It did that already. When I resized sda1, it created 87 MB of unallocated at the beginning of the drive.
did grub not complain about that?

> **warfacegod said:**
> Your night and mine are like 6 hours apart, neither one of us would sleep for like 2 days. Cool sleep dep. LOTR.
one of my favorites ;)
worth to stay awake for that long :D

---

### Post by Matt_Johnson on 2010-01-12
haha, I've screwed up my laptop soo many times doing stuff like this; but i get a kick out of it :P

---

### Post by warfacegod on 2010-01-12
> **Leppie said:**
> well, as the thread title says you really *are* about to do something stupid... :P

Assuming it doesn't frag my hardware, I think that might provide hours and hours of joy.

What happened to the good ol' days of screwing things up by simply turning on Windows?

---

### Post by Leppie on 2010-01-12
> **warfacegod said:**
> Assuming it doesn't frag my hardware, I think that might provide hours and hours of joy.

What happened to the good ol' days of screwing things up by simply turning on Windows?
though turning on windows is quite destructive, it's not that likely to nuke the electronics. does your laptop have the hotswap capability? if it doesn't i wouldn't try it, don't think the manufacturer will provide any assistance after that... :P

---

### Post by Matt_Johnson on 2010-01-12
> **warfacegod said:**
> Assuming it doesn't frag my hardware, I think that might provide hours and hours of joy.

What happened to the good ol' days of screwing things up by simply turning on Windows?
  If you pooch your hardware then you have more fun replacing computer components then repartition again!

---

### Post by Leppie on 2010-01-12
i'm about to swap my /boot partition, see if that comes up with anything interesting :)
i'll let you know ;)

---

### Post by warfacegod on 2010-01-12
> **Leppie said:**
> though turning on windows is quite destructive, it's not that likely to nuke the electronics. does your laptop have the hotswap capability? if it doesn't i wouldn't try it, don't think the manufacturer will provide any assistance after that... :P

My laptop is 5 or 6 years old. Hell, Toshiba told me to piss off about my crapped out DVD drive when I told them I put Linux on it.


That's 600. My not so secret plan for world domination is coming together nicely.

---

### Post by warfacegod on 2010-01-12
> **Matt_Johnson said:**
> If you pooch your hardware then you have more fun replacing computer components then repartition again!

I'm going to put an ATi card in my wife's computer that I never got the driver working well on. Then put 9.10 NBR on the 80 GB NTFS drive. It already has 8.04 and 9.04 on a 20 GB ext3 and 9.10 on an ext4. Then I'm going to try RAIDing them all together.

---

### Post by Leppie on 2010-01-12
i still don't get why manufacturers and retailers get so freaked out when you tell them you installed linux on one of their machines...

---

### Post by warfacegod on 2010-01-12
Contracts with Microsoft.

---

### Post by Leppie on 2010-01-12
how much can microsoft be paying them???
knowing how much profit the company makes, it can never be that much...
but obviously they pay only a very small amount for the rights as oem's.

---

### Post by Leppie on 2010-01-13
> **Leppie said:**
> i'm about to swap my /boot partition, see if that comes up with anything interesting :)
i'll let you know ;)
that wasn't very interesting... too smooth... blah...

---

### Post by warfacegod on 2010-01-19
Okay, I've had some time to sit with my 9.10 netbook install and things are starting to go badly. My netbook-launcher process is starting to argue with Compiz, hijacking my processor. Graphical artifacts. Pidgin is crashing. Somehow (I have *no* idea how) some of the settings and behaviors are leaching over to my other partition and into my normal 9.10 install. And myriad other instabilities too numerous to list. I'm getting twitches, glitches, and the damn thing needs stitches. 'Cause it's bleeding out. This is the computer equivalent of; explosive decompression of cardiac machinery.


So......in a nutshell......my nefarious plot has worked.


Of course it did......I'm a genius.


Bwaaahhooowaaaahaaaaahaaaaahaaaaahaaaaaa....gasp....bwaahhaahhaahaha..ha!

---

### Post by baddog144 on 2010-01-19
Woah. If screwing up installs is nefarious, then I'm some sort of damn evil genius. :D

---

### Post by Leppie on 2010-01-19
> **baddog144 said:**
> Woah. If screwing up installs is nefarious, then I'm some sort of damn evil genius. :D
it's easier to mess up an install unintentionally than when trying intentionally.

---

### Post by audiomick on 2010-01-19
> **Leppie said:**
> i still don't get why manufacturers and retailers get so freaked out when you tell them you installed linux on one of their machines...
I don't think it even goes as far as contracts, although that may well be a factor. I reckon it is just saving on support costs. If they only support one OS, then then people on the "help" line only have to pull up one set of "if you do this, then that, it will just work" instructions.

What I really can't understand is what a Yamaha product developement engineer once said to me. I had asked him why the programs for controlling their digital mixing desks and other digital audio devices only run on Windows, and why they don't make them for Linux. His answer: because windows is an open system....:confused:

---

### Post by warfacegod on 2010-01-19
I think I'm going to rip the guts out of my NBR. Invasive surgery, amputation, alien experimentation, .....you know, the usual.

But before I do, can someone explain to me the difference between *apt-get[I] and *aptitude.[/I]

More importantly the difference between *remove* and *purge*.

---

### Post by audiomick on 2010-01-19
I wouldn't  have thought I would have to suggest to you to look in a man page...:)

```
man apt-get
```
```
DESCRIPTION
       apt-get is the command-line tool for handling packages, and may be
       considered the user´s "back-end" to other tools using the APT library.
       Several "front-end" interfaces exist, such as dselect(8), aptitude(8),
       synaptic(8), gnome-apt(1) and wajig(1).
```

 ```
remove
           remove is identical to install except that packages are removed
           instead of installed. Note the removing a package leaves its
           configuration files in system. If a plus sign is appended to the
           package name (with no intervening space), the identified package
           will be installed instead of removed.

       purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).

```

---

### Post by warfacegod on 2010-01-19
Thanks. That is in essence what I had assumed.

---

### Post by tuddy666 on 2010-01-19
> **Leppie said:**
> i still don't get why manufacturers and retailers get so freaked out when you tell them you installed linux on one of their machines...

As mentioned before, OEM contracts. Some warranties have pretty silly terms for what you can do, but they never outright state that you cannot change the installed operating system. I mean, if they did, then you wouldn't be able to reinstall windows when the inevitable happens and it breaks itself.

Edit- if a manufacturer forbids installing a non-windows operating system in their warranty, it's usually through a technicality. It's never outright stated, so you have to do a -lot- of reading between the lines.

---

### Post by warfacegod on 2010-01-19
> **tuddy666 said:**
> As mentioned before, OEM contracts. Some warranties have pretty silly terms for what you can do, but they never outright state that you cannot change the installed operating system. I mean, if they did, then you wouldn't be able to reinstall windows when the inevitable happens and it breaks itself.

Try whispering the word Linux to Toshiba. Go ahead, I dare you.

---

### Post by tuddy666 on 2010-01-19
> **warfacegod said:**
> Try whispering the word Linux to Toshiba. Go ahead, I dare you.

oh, I know all too well. Thankfully, I don't own the Toshiba system in question. Admittedly, I look after my systems, so being unable to get a replacement because of the OS I run is the least of my concerns.

---

### Post by Leppie on 2010-01-19
> **audiomick said:**
> What I really can't understand is what a Yamaha product developement engineer once said to me. I had asked him why the programs for controlling their digital mixing desks and other digital audio devices only run on Windows, and why they don't make them for Linux. His answer: because windows is an open system....:confused:
maybe open in this case is equal to vulnerable? windows allows for lazy and "dirty" programming. this is why the system and it's services can be crashed so easily.

---

### Post by warfacegod on 2010-01-19
> **tuddy666 said:**
> oh, I know all too well. Thankfully, I don't own the Toshiba system in question. Admittedly, I look after my systems, so being unable to get a replacement because of the OS I run is the least of my concerns.

The new Satellites M505's are not the only ones in question. I'm running a Satellite P25-s607. The Panasonic/Matsushita? UJ-811 DVD burners they shipped died by the hundreds. Toshiba didn't want to make good on it saying it was Panasonic's fault. 

Eventually, Toshiba replaced the smoked ones and shipped the laptops with the Panasonic/Matsushita? UJ-811****** which did *the exact same thing!* That brings us back around to Linux. Toshiba refused to my UJ-811B because I installed Ubuntu on it. Said it was "Linux that did it to my drive". I responded with "I am probably 1 in 50,000 people this has happened to that installed Linux. So, by your very same logic, you are implying that Windows is not responsible for the remaining 49,999 drives burning out. Therefor, the only possibility left is that this is a hardware issue. They hung up.

You know you've had a good day when a major worldwide corporation feels the need to hang up on you.

---

### Post by Leppie on 2010-01-19
> **tuddy666 said:**
> Edit- if a manufacturer forbids installing a non-windows operating system in their warranty, it's usually through a technicality. It's never outright stated, so you have to do a -lot- of reading between the lines.
if it were only a technicality, they would have said something like "we don't provide assistance for the operating system". however installing another os isn't going to physically break the equipment. so why don't they want to provide hw warranty if another os has been installed?

---

### Post by audiomick on 2010-01-19
> **Leppie said:**
> windows allows for lazy and "dirty" programming.

That would explain their network to midi driver. It is not my friend...;)

---

### Post by Leppie on 2010-01-19
> **warfacegod said:**
> You know you've had a good day when a major worldwide corporation feels the need to habg up on you.
having worked for several multinationals i can tell you that support desks do not require a technical background. as a matter of fact, that's about at the bottom of the list _*if*_ on their list. they think that technical skills can be acquired more easily than cs skills... this is why most of the corporation nowadays are outsourcing to call centers in India/Malaysia/Philippines, then decide that because of the language gap (this is not because i want to be racist or something. hell, i'm an ethnic minority) pull the service back to their home country.

---

### Post by warfacegod on 2010-01-19
> **Leppie said:**
> having worked for several multinationals i can tell you that support desks do not require a technical background. as a matter of fact, that's about at the bottom of the list _*if*_ on their list. they think that technical skills can be acquired more easily than cs skills... this is why most of the corporation nowadays are outsourcing to call centers in India/Malaysia/Philippines, then decide that because of the language gap (this is not because i want to be racist or something. hell, i'm an ethnic minority) pull the service back to their home country.

Being an ethnic minority doesn't auto-magically make you not a racist. (Not implying that you are:D:D:D:D)

There are many black folk for instance, in my country that are convinced that they can't be a racist based soley on the fact that they're black. Jesse Jackson, Louis Farrakhan, Al Sharpton, and Barak Obama all come to mind.

---

### Post by Leppie on 2010-01-19
> **warfacegod said:**
> Being an ethnic minority doesn't auto-magically make you not a racist. (Not implying that you are:D:D:D:D)

There are many black folk for instance, in my country that are convinced that they can't be a racist based soley on the fact that they're black. Jesse Jackson, Louis Farrakhan, Al Sharpton, and Barak Obama all come to mind.
black folk aren't really an ethnic minority... what percentage of the us population is black? and then what percentage is white?

---

### Post by warfacegod on 2010-01-19
> **Leppie said:**
> black folk aren't really an ethnic minority... what percentage of the us population is black? and then what percentage is white?

I'm not sure at the moment. I used blacks as an example. The concept can and should be applied to anyone or any group no matter how they choose to define themselves.

---

### Post by warfacegod on 2010-01-19
> **Leppie said:**
> maybe open in this case is equal to vulnerable? windows allows for lazy and "dirty" programming. this is why the system and it's services can be crashed so easily.

Perhaps he just meant that the computer case was open.

I know I've posted this somewhere before but we are talking about doing evil things to computers.

Any body wanting to have fun on a Windows XP machine (read BSOD) need only to uninstall Notepad. I've done this. Twice.

---

### Post by tuddy666 on 2010-01-19
> **Leppie said:**
> if it were only a technicality, they would have said something like "we don't provide assistance for the operating system". however installing another os isn't going to physically break the equipment. so why don't they want to provide hw warranty if another os has been installed?
That's what confuses me. Software isn't going to physically break hardware, but a lot of companies will refuse hardware support under warranty if you've changed the OS. Then again, other companies have considerably better service and will fix physical hardware faults under warranty, regardless of software.

But, as you say, tech support workers usually don't have the kind of technical knowledge to actually know this, and are probably just reading their answers from a script.

---

### Post by Leppie on 2010-01-19
> **warfacegod said:**
> I'm not sure at the moment. I used blacks as an example. The concept can and should be applied to anyone or any group no matter how they choose to define themselves.
i have nothing against those peoples, it's merely an observation.
a lot of people mistake national pride for racism though...

also, the language gap is not necessarily related to the aforementioned countries.
i've spoken with a lot of people who claim to speak english very well, still they do not seem to understand irish people (the irish speak really fast).

---

### Post by Leppie on 2010-01-19
> **tuddy666 said:**
> But, as you say, tech support workers usually don't have the kind of technical knowledge to actually know this, and are probably just reading their answers from a script.
yes, exactly. because a "kind and helpful" person is more suitable than a someone with a technical background...

---

### Post by audiomick on 2010-01-19
> **Leppie said:**
> i've spoken with a lot of people who claim to speak english very well, still they do not seem to understand irish people (the irish speak really fast).

I have trouble with scotsmen myself. And I shared a flat with a bloke from Manchester for a while. Took me about 3 weeks to get my ears around his dialect.
On the other hand, a lot of people that I meet here in Germany think they can speak english well until they hear me speaking "normally"...;)

---

### Post by warfacegod on 2010-01-19
> **Leppie said:**
> i have nothing against those peoples, it's merely an observation.
a lot of people mistake national pride for racism though...

also, the language gap is not necessarily related to the aforementioned countries.
i've spoken with a lot of people who claim to speak english very well, still they do not seem to understand irish people (the irish speak really fast).

I'm human first (actually divine but that isn't the point) an American next but mostly Irish (bit of French, Scottish, and English) and I don't speak very fast but I do drink fast. Actually my landlord is Irish (American) and he does speak very quickly. I just say "okay" to him because I can only catch maybe 1 in 20 words he says. I could be agreeing to let him slit my wife's throat and wouldn't know.

---

### Post by Leppie on 2010-01-19
> **audiomick said:**
> And I shared a flat with a bloke from Manchester for a while. Took me about 3 weeks to get my ears around his dialect.
Manchunian is still ok, try the scouser (Liverpool + Wirral area) accent...

---

### Post by warfacegod on 2010-01-19
The English themselves don't think anybody speaks proper English, including the *English*.

It maybe slower but I've decided to speak exclusively in binary. 00010011101000101111000.

Now would someone please be kind enough to translate that for me because I hve no idea what I said.

---

### Post by audiomick on 2010-01-19
> **warfacegod said:**
> The English themselves don't think anybody speaks proper English, including the *English*.
actually, the only unadulterated english left in the world is Australian. I understand everyone there perfectly...:D
> It maybe slower but I've decided to speak exclusively in binary. 00010011101000101111000.

Now would someone please be kind enough to translate that for me because I hve no idea what I said.

643448
[http://www.binarymath.info/decimal-conversion.php](http://www.binarymath.info/decimal-conversion.php)

I geuss that is like 42, but more...:D

---

### Post by Leppie on 2010-01-19
> **audiomick said:**
> actually, the only unadulterated english left in the world is Australian. I understand everyone there perfectly...:D
you have a gift there mate. even though i speak more or less the same languages as my gf does, a lot of times i don't understand what she's talking about... #-o

---

### Post by warfacegod on 2010-01-19
> **audiomick said:**
> actually, the only unadulterated english left in the world is Australian. I understand everyone there perfectly...:D

643448
[http://www.binarymath.info/decimal-conversion.php](http://www.binarymath.info/decimal-conversion.php)

I geuss that is like 42, but more...:D

Yeah, but what does it mean in plain English?


Zaphod would disagree after getting lost on the way to 42.

---

### Post by audiomick on 2010-01-19
> **Leppie said:**
> you have a gift there mate. even though i speak more or less the same languages as my gf does, a lot of times i don't understand what she's talking about... #-o

Well there is that. I am lucky there;  with mine, one of us is always speaking a second language, so I have a good cop out.;)

---

### Post by warfacegod on 2010-01-19
> **Leppie said:**
> you have a gift there mate. even though i speak more or less the same languages as my gf does, a lot of times i don't understand what she's talking about... #-o

Nobody understands what women are talking about. Often they themselves don't. They aren't based on logic and reason. But I love them anyway.

---

### Post by audiomick on 2010-01-19
> **warfacegod said:**
> Yeah, but what does it mean in plain English?

Well, using the decimal via the phone keypad, I get "mid hit"...;)

---

### Post by warfacegod on 2010-01-19
Anybody come up with something sinister and Mephistophelian for me to do to my NBR install?

---

### Post by warfacegod on 2010-01-19
> **audiomick said:**
> Well, using the decimal via the phone keypad, I get "mid hit"...;)

I've decided to spend the rest of my life saying only "mid hit".

---

### Post by ibuclaw on 2010-01-19
Moved to the Community Cafe, as this thread has long since drifted from an actual support question into just general chatter.

On the side note though - I sometimes get the same bored streak. But I tend to fill that boredom with crazier things, such as ArchLinux, BtrFS **/** (root) installations (which I have two currently setup for production use) and Full disk encryption installations, where the disk is decrypted using a keyfile on an SD card .

Fun fun fun in the Sun.

---

### Post by audiomick on 2010-01-19
> **tinivole said:**
> Moved to the Community Cafe, as this thread has long since drifted from an actual support question into just general chatter.

was kind of wondering how long that might take...;)

---

### Post by warfacegod on 2010-01-19
> **tinivole said:**
> Moved to the Community Cafe, as this thread has long since drifted from an actual support question into just general chatter.

On the side note though - I sometimes get the same bored streak. But I tend to fill that boredom with crazier things, such as ArchLinux, BtrFS **/** (root) installations (which I have two currently setup for production use) and Full disk encryption installations, where the disk is decrypted using a keyfile on an SD card .

Fun fun fun in the Sun.

I don't think it ever was a support question by even the loosest definition.

Do I get to keep my beans though?#-o:-k

---

### Post by Leppie on 2010-01-19
> **warfacegod said:**
> I don't think it ever was a support question by even the loosest definition.

Do I get to keep my beans though?#-o:-k
they will be transferred to me... :P

---

### Post by warfacegod on 2010-01-19
> **Leppie said:**
> they will be transferred to me... :P

You're just concerned that I'm catching up. Have some :popcorn: for when you watch me fly past you.:twisted:

---

### Post by Leppie on 2010-01-19
> **warfacegod said:**
> You're just concerned that I'm catching up. Have some :popcorn: for when you watch me fly past you.:twisted:
youi're not there yet...
you may be deity, but remember: leprechauns are magical... :P

---

### Post by Gorgoth on 2010-01-19
> **warfacegod said:**
> 

You see? This is what happens when you start computing with Windows. I start going:

"My Linux installs are perfect? There's nothing for me to fix? Sigh. Good grief, I am bored! Let me go screw up my laptop again so I can have something to do"



THat is usually my exact line of reasoning for each new distro I try... "Hey, wonder how long it'll take me to mess something up significantly *this time*"

:D

---

### Post by audiomick on 2010-01-19
> **Leppie said:**
>  leprechauns are magical... :P

to be sure... And where do you keep your gold?

---

### Post by Leppie on 2010-01-19
> **audiomick said:**
> to be sure... And where do you keep your gold?
ain't gonna tell ya... have to catch me first :P

---

### Post by CharmyBee on 2010-01-19
I get bored and do dumb things with my old computers also, as I have Puppy Linux, Windows 95C and Windows 2000 SP3 booting from the same 1.9GB hard drive partition. Spare space is left at a grand total of 200mb. Why?

---

### Post by warfacegod on 2010-01-19
> **audiomick said:**
> to be sure... And where do you keep your gold?

Don't bother, those tiny freaks booby trapped the hell out of it. Nearly lost an arm and my left pinkie toe. Fortunately it went crying all the way home.

---

### Post by warfacegod on 2010-01-19
If I were to do to a human being, what I am planning on doing to my 9.10 UNR install, I would be charged with crimes against humanity. Mothers would shield their infants ears and run screaming at the mere mention of my name.  The elite class of killers such as Joseph Stalin and Jeffrey Dahmer would cower before me for I will have commit an atrocity so vile in its planning and foul in its execution that the very act would reverberate through Time and Space to eventually crumble the very Pillars of The Universe!

KNEEL! FEEBLE HUMANS! KNEEL BEFORE THE POWER THAT IS WARFACEGOD! I AM SUPREME!

---

### Post by audiomick on 2010-01-19
> **warfacegod said:**
> If I were to do to a human being, what I am planning on doing to my 9.10 UNR install, I would be charged with crimes against humanity. Mothers would shield their infants ears and run screaming at the mere mention of my name.  The elite class of killers such as Joseph Stalin and Jeffrey Dahmer would cower before me for I will have commit an atrocity so vile in its planning and foul in its execution that the very act would reverberate through Time and Space to eventually crumble the very Pillars of The Universe!

KNEEL! FEEBLE HUMANS! KNEEL BEFORE THE POWER THAT IS WARFACEGOD! I AM SUPREME!

do I applaud now, or is it time for the pitchforks and flaming torches??

---

### Post by warfacegod on 2010-01-19
> **audiomick said:**
> do I applaud now, or is it time for the pitchforks and flaming torches??

Both. Now kneel.

---

### Post by audiomick on 2010-01-19
I've thought of something: you could use the software centre to individually de-install and re-install all the major components of the system. And then clean up with the janitor...

---

### Post by warfacegod on 2010-01-19
> **audiomick said:**
> I've thought of something: you could use the software centre to individually de-install and re-install all the major components of the system. And then clean up with the janitor...

Now that I have Software Center working I used it to install Add/Remove and then used that to remove Computer Janitor.

---

### Post by warfacegod on 2010-01-19
I removed something like 30 packages or so with Synaptic, including netbook-remix without any apparent effect. None, zip, zero, zilch, nil, and nothing. Ergh!!!

So I happened across a package called apparmor. Mark for complete removal and damn near the whole screen goes red! Well this looks promising. So I do it. (Of course.)

Halfway through the removal all sorts of warning windows start popping up begging me "Do You *Really, Really* Want to Do This? Yup. Do it.

Almost done and nothings happening. Getting nervous. Gonna be pissed if this was a false alarm. There goes my network. Nothing. Nothing. Still nothing. Was that something?......no still nothing. Ok this was point... BAM!!

I've got black screen and* TEXT*!!!!

So I poke around for a bit getting nowhere and think; "Well, I only have wireless so there's no point to trying to fix [I]this!

[/I]reboot[I]

You must be root   [/I](I think: "Get the hell outta here. Okay....")sudo reboot    (This is stupid to have to do this.)

*password      *(Oh, Good Grief!)

noinotgoingtotypemypasswordforyouhooliganstosteal

It goes down like Newton's nonexistent apple. Boots back up and GRUB2 isn't even showing the install anymore!

---

### Post by baddog144 on 2010-01-19
Oh, snap. Victory is yours!
I think. I haven't been following this thread too closely.

---

### Post by warfacegod on 2010-01-19
Anybody think I can get this thread into Tips & Tutorials?

How To: Completely Frag Your System!

---

### Post by warfacegod on 2010-01-19
> **baddog144 said:**
> Oh, snap. Victory is yours!
I think. I haven't been following this thread too closely.

Neither have I.

---

### Post by chillicampari on 2010-01-19
> **warfacegod said:**
> Nobody understands what women are talking about. Often they themselves don't. They aren't based on logic and reason. But I love them anyway.

I know, right? It's just so darned cute when they talk, like they think they're people!

---

### Post by warfacegod on 2010-01-19
> **chillicampari said:**
> I know, right? It's just so darned cute when they talk, like they think they're people!

That made coffee shoot out of my nose.


Women are people. They just don't make any sense to me.

---

### Post by epicoder on 2010-01-19
*Deleted by sh228*

---

### Post by warfacegod on 2010-01-20
I just installed Mythbuntu into my UNR partition and didn't let it format the partition. It left all of my folders and files intact. I am very surprised.

Now I'm going to try to put the UNR interface into it.

---

### Post by Leppie on 2010-01-20
you could also try to downgrade from karmic to hardy, or something like that...

---

### Post by warfacegod on 2010-01-20
Is downgrading possible?

---

### Post by warfacegod on 2010-01-20
I just installed the nebook-launcher package. It's got all sorts of missing dependencies but it ran, barely. I've got the feeling this is going to turn into some kind of Frankenstein's Monster. Hail Linuxtein!

---

### Post by NCLI on 2010-01-20
> **warfacegod said:**
> Is downgrading possible?

According to official sources and guides: No.
Practically: YES.
Will it completely destroy your system: Most likely.

Just change all mentions of "karmic" in "/etc/apt/sources.lst" to the codename of whatever you want to downgrade to :popcorn:

---

### Post by DrMelon on 2010-01-20
Next, write a script that deletes every file with a randomly-chosen letter in it.

So once, you might run the script and it deletes files with 'z' in them. Not so bad, but all hell will break loose if the random generator hits 'u'... :D

---

### Post by warfacegod on 2010-01-20
Well, I've removed netbook-launcher and Compiz (sorry, forgot to mention I installed it). I think I'm going to see if I can get Mythbuntu to communicate properly with my Television. Not a simple task with a Go5200 64 MB graphics card with S-video. The closest I got was in Ubuntu 9.10 with a very low res B/W picture that filled a square in the middle of my screen. My TV is a Zenith. I'll post the model # later when I can get to it.


Oh, and before you clowns decide to razz me for having a Zenith, remember that LG owns Zenith now and LG makes some of the best TVs available.

---

### Post by warfacegod on 2010-01-21
I got it working! I am invincible! Another of warfacegod's enemies lays dead at his feet! Bwaaahaahaahaahaaaa!  Ahhmwaaahaaahaaa!

I didn't do this in Mythbuntu but in my normal 9.10 install. I'm not used to xfce yet so it'll be a bit harder there.

.01 I went into my nVidia X Server Settings.

.02 Lots of fiddling around.

.03 Went into X Server Display configuration, selected TV0, and clicked configure.

.04 Check Twinview and click OK. (Enabling Twinview must be done. I don't know why.)

.05 Click configure again and check Separate X Screen (Requires X restart) and clicked OK.

.06 Set resolution to 1024x768 and clicked Apply.

.07 Went through seizure of utter astonishment and shock that it worked.


The picture is barely passable, it doesn't quite fit the screen, a little bright, and it won't save the configuration when I reboot but at least it works.

This is all stuff I've done before (except the working part, that never happened) but the best I ever got was Twinview with half on my screen and half on the TV with the TV in black and white filling only a square in the middle. Here's the key:

I went to Edit Menus> hightlight nVidia X Server Settings> click properties> change Command from: /usr/bin/nvidia-settings to: gksu nvidia-settings

I found out immediately afterwards that you can get the same thing with:

> gksudo nvidia-settings

but it won't stick. You'll need to do that every time you reboot.

I'll post again with improvements like getting it to remember the settings so that I won't have to reenable the TV after every reboot.

With that kids, I leave you now to watch Captain Kirk blow up the ship...again.

---

### Post by nerdy_kid on 2010-01-22
this is my favorite thread of all time :D

---

### Post by warfacegod on 2010-01-22
Now I have to keep my standard of demented crap at it's apex. Since I consider dementia and insanity to have no limit, that's a very tall order. I'm going to look into computer repair with small, shaped charge explosives.

---

### Post by Tristam Green on 2010-01-22
> **warfacegod said:**
> Oh, and before you clowns decide to razz me for having a Zenith, remember that LG owns Zenith now and LG makes some of the best TVs available.

It's a shame they can't make a phone worth a ****.

---

### Post by nerdy_kid on 2010-01-22
> **warfacegod said:**
> Now I have to keep my standard of demented crap at it's apex. Since I consider dementia and insanity to have no limit, that's a very tall order. I'm going to look into computer repair with small, shaped charge explosives.

that would work, backup some very important data on an HD, paste an explosive to it then detonate it.  Then get the data back :D

---

### Post by warfacegod on 2010-01-22
> **nerdy_kid said:**
> that would work, backup some very important data on an HD, paste an explosive to it then detonate it.  Then get the data back :D

My interest is shaped charges. I don't want to recover the data, I want to blast it back into the laptop. With the proper shape and enough explosives, the binary code ought to fly through the air and land in my hard drive in the right order and exactly where it needs to be.

Forget Firewire or eSATA, this is the new data transfer technology. Bombs!

---

### Post by nerdy_kid on 2010-01-22
> **warfacegod said:**
> My interest is shaped charges. I don't want to recover the data, I want to blast it back into the laptop. With the proper shape and enough explosives, the binary code ought to fly through the air and land in my hard drive in the right order and exactly where it needs to be.

Forget Firewire or eSATA, this is the new data transfer technology. Bombs!

hmmm interesting idea :D  The internet would become VERY messy though.  Might drive web serving costs up a little too lol

---

### Post by 73ckn797 on 2010-01-22
This thread title led me to believe that I was going to encounter a red neck saying, "Hey, watch this". Then killing themselves over some dumb action when trying to show off. Shape charges would do this.

---

### Post by warfacegod on 2010-01-22
> **73ckn797 said:**
> This thread title led me to believe that I was going to encounter a red neck saying, "Hey, watch this". Then killing themselves over some dumb action when trying to show off. Shape charges would do this.

Great! So what's your verdict? After reading this, do I come off as a dumb actioned Redneck?

Gee! I do hope so. Although, I suppose the technical term would be "Dumb actioned *Yankee* redneck.

Seriously, if you don't like what's going on with this thread, then complain to the mods and ask them to close and/or remove it. I very rarely apologize for offending people and I'm not about to start now, in this thread. I don't tread lightly for people. As far as I'm concerned, peoples sensibilities can kick wind.

---

### Post by Leppie on 2010-01-22
> **warfacegod said:**
> As far as I'm concerned, peoples sensibilities can kick wind.
do they have sensibilities???

---

### Post by warfacegod on 2010-01-22
> **Leppie said:**
> do they have sensibilities???

They certainly don't have any *sense*, anyway!

---

### Post by Leppie on 2010-01-22
> **warfacegod said:**
> They certainly don't have any *sense*, anyway!
that's one thing we agree on then ;)

---

### Post by warfacegod on 2010-01-22
> **Leppie said:**
> that's one thing we agree on then ;)

Only *one*?:smile:

---

### Post by Leppie on 2010-01-22
> **warfacegod said:**
> Only *one*?:smile:
course not, but couldn't say that plain out in public... :P

---

### Post by 73ckn797 on 2010-01-22
> **warfacegod said:**
> Great! So what's your verdict? After reading this, do I come off as a dumb actioned Redneck?

Gee! I do hope so. Although, I suppose the technical term would be "Dumb actioned *Yankee* redneck.

Seriously, if you don't like what's going on with this thread, then complain to the mods and ask them to close and/or remove it. I very rarely apologize for offending people and I'm not about to start now, in this thread. I don't tread lightly for people. As far as I'm concerned, peoples sensibilities can kick wind.

Can't you take a joke? Where do you see that I am complaining? Oh, I see. I must have forgotten to put a smiley face on the end of my comments. I must have offended your sensibilities.   :D

---

### Post by Grifulkin on 2010-01-22
> **warfacegod said:**
> I'm going to resize my sda1 partition. I'm going to install 9.10 NBR as a dual with normal 9.10 on my laptop. Why you ask? Because I feel like it.
Can any one give me a decent partition size for NBR?


You see? This is what happens when you start computing with Windows. I start going:

"My Linux installs are perfect? There's nothing for me to fix? Sigh. Good grief, I am bored! Let me go screw up my laptop again so I can have something to do"

And that's after three years of being Windows free. Ubuntu: The Windows 12 Step Program

Screwing up my laptop to fix it is a hobby of mine.

---

### Post by warfacegod on 2010-01-22
> **73ckn797 said:**
> Can't you take a joke? Where do you see that I am complaining? Oh, I see. I must have forgotten to put a smiley face on the end of my comments. I must have offended your sensibilities.   :D

I can and have taken the joke. This entire thread is barely hovering above joke level. Unfortunately, sarcasm doesn't come through too well in print.

You still didn't answer the question though. Do I qualify for Redneckdom? (Yeah, I know it's not a word, Jeff Foxworthy would be *so* proud.)

---

### Post by 73ckn797 on 2010-01-22
> **warfacegod said:**
> I can and have taken the joke. This entire thread is barely hovering above joke level. Unfortunately, sarcasm doesn't come through too well in print.

You still didn't answer the question though. Do I qualify for Redneckdom? (Yeah, I know it's not a word, Jeff Foxworthy would be *so* proud.)


I do not know you to determine whether you would be the punchline of a Jeff Fozworthy "You might be a red neck if..." I was only playing off the thread title. I, however, might be considered a red neck because I have a trick-up puck. It is not a 4X4 and has no camo or gun rack. 

There are no decals of a deer that can be confused with the profile of a pregnant woman (if you have seen one of those you know what I am saying). I don't own any guns or have a Dale Earnhardt tag on the front or a Confederate flag in the back window. I do live in the land of certifiable rednecks, however, so I do know one when I see one. I have not seen you so I cannot know for sure.(GRIN)!! 

Redneckdom ... good word. That would be a good description for much of the south, away from the city that is. Urban rednecks drive newer pickup trucks and are in a class all their own.

---

### Post by warfacegod on 2010-01-22
> **73ckn797 said:**
> I do not know you to determine whether you would be the punchline of a Jeff Fozworthy "You might be a red neck if..." I was only playing off the thread title. I, however, might be considered a red neck because I have a trick-up pup. It is not a 4X4 and has no camo or gun rack. 

There are no decals of a deer that can be confused with the profile of a pregnant woman (if you have seen one of those you know what I am saying). I don't own any guns or have a Dale Earnhardt tag on the front or a Confederate flag in the back window. I do live in the land of certifiable rednecks, however, so I do know one when I see one. I have not seen you so I cannot know for sure.(GRIN)!! 

Redneckdom ... good word. That would be a good description for much of the south, away from the city that is. Urban rednecks drive newer pickup trucks and are in a class all their own.

Do combat boots, a beer, and a Slayer t-shirt qualify?

Actually, now that I think about, if you've ever typed the word sudo, that automatically disqualifies you for Redneckdom. *Curses!*

Nice laptop,by the way. I'm running a Toshiba Satellite P25-s607 with 2 GB Crucial RAM it's a bit long in the tooth (Yeah! Redneck phrase.) but still very capable of out performing allot of today's hardware.

---

### Post by 73ckn797 on 2010-01-22
> **warfacegod said:**
> Do combat boots, a beer, and a Slayer t-shirt qualify?

Actually, now that I think about, if you've ever typed the word sudo, that automatically disqualifies you for Redneckdom. *Curses!*

Nice laptop,by the way. I'm running a Toshiba Satellite P25-s607 with 2 GB Crucial RAM it's a bit long in the tooth (Yeah! Redneck phrase.) but still very capable of out performing allot of today's hardware.

The boots cannot be combat style but ACME or work boots. The beer would have to be Budweiser or PBR. The shirt would have to be a country singer. NAW, guess you ain't no redneck (my wording might qualify). I agree with sudo, most rednecks I know would think I am speaking or swearing at them in another language .

The Toshiba Laptop has been very reliable. It is over 3 years old and going strong. It has worked great with Ubuntu since 8.04

---

### Post by Leppie on 2010-01-22
> **73ckn797 said:**
> The Toshiba Laptop has been very reliable. It is over 3 years old and going strong. It has worked great with Ubuntu since 8.04
did you tell toshiba that you've installed ubuntu on one of their machines?

---

### Post by 73ckn797 on 2010-01-22
> **Leppie said:**
> did you tell toshiba that you've installed ubuntu on one of their machines?

UHH! was I sposed to?:D

I really could have cared less. I had the laptop for 8 months before I started using Ubuntu. It has held up very well. I use it daily as I travel around the area and it has taken its' share of bumps and knocks and keeps on ticking. The on-off button is loose but that is the only part starting to wear out that is obvious.

I thought the hard drive was failing last week. I dual boot with XP and the thing froze up while in Windows. Had to turn it off and after that Windows would not load. Ubuntu kept right on working. I wiped the drive using a live CD and partitioned it to reinstall Ubuntu and XP. I really cannot stand the Toshiba recovery disk. It puts so much other junk on the install that I spend several hours cleaning up the stuff. I try to keep a very light laptop as far as programs go. Windows is only using part of a 20GiB partition out of the 80GiB over-all size. I have only booted into Windows once this week to install the ext2fsd program.

Maybe I ought to get a #3 and #88 sticker to put on the laptop lid to show off my redneckdom? WOW, that word almost sounds like a lower part of the anatomy!!

---

### Post by warfacegod on 2010-01-22
Leppie's right. If you say Linux to Toshiba, the Costomer Service Rep will shriek like a banshee on PCP and curse you for the vile, Devil worshiping minion of hell you are. ...Or you'll get the response I got in post #43.

---

### Post by 73ckn797 on 2010-01-22
> **warfacegod said:**
> Leppie's right. If you say Linux to Toshiba, the Costomer Service Rep will shriek like a banshee on PCP and curse you for the vile, Devil worshiping minion of hell you are. ...Or you'll get the response I got in post #43.

A reaction out of fear or ignorance, likely both.

---

### Post by warfacegod on 2010-01-22
> **73ckn797 said:**
> A reaction out of fear or ignorance, likely both.

Both, because I was able to think circles around them without even trying.

---

### Post by 73ckn797 on 2010-01-22
I have never had to deal with tech support for any of my electronics.

Being in the auto business for 34 years I tend to open the hood and figure things out. Most of my desktop computers were put together by me. I have only bought one boxed computer and that was a Laser 286 back in 1990. One of the first things I did was remove the cover and look around. One time I fried the LPT port on it. That was my first time to figure out that a LPT card would fix the problem. AHH I remember the ISA expansion slot!! 1 megabyte of ram cost $100.

---

### Post by Leppie on 2010-01-23
> **73ckn797 said:**
> One time I fried the LPT port on it. That was my first time to figure out that a LPT card would fix the problem. AHH I remember the ISA expansion slot!! 1 megabyte of ram cost $100.
the first computer i fried was a ZX Spectrum... :P

---

### Post by 73ckn797 on 2010-01-23
> **Leppie said:**
> the first computer i fried was a ZX Spectrum... :P
My first computer was an Apple IIE that was given to me.The other person could not get it working. After several days and a couple of all nighters I got it working. I was hooked after that.

---

### Post by warfacegod on 2010-01-23
I've got a set of lenses that I salvaged out of an old Mitsubishi big screen projection TV (long story short, I have a fondness for taking things apart. That's how I discovered that removing notepad from XP will totally frag your install.) Anyway, I was thinking of putting them together and attaching a gigantic flashlight to it. I was thinking it might make a sort of focused light beam cannon.

---

### Post by audiomick on 2010-01-23
> **warfacegod said:**
> I've got a set of lenses that I salvaged ... I was thinking of putting them together and attaching a gigantic flashlight to it. I was thinking it might make a sort of focused light beam cannon.

might make a good bat signal (dada dada dada dada batman!)

---

### Post by warfacegod on 2010-01-23
> **audiomick said:**
> might make a good bat signal (dada dada dada dada batman!)

I was leaning more towards burning down my neighbor's tree.

---

### Post by 73ckn797 on 2010-01-23
> **warfacegod said:**
> I was leaning more towards burning down my neighbor's tree.

Let me know how that works out. I have 30 pine trees I'd like to take down.

---

### Post by audiomick on 2010-01-23
What have you guys got against trees? I try and hug one every day...

---

### Post by warfacegod on 2010-01-23
> **audiomick said:**
> What have you guys got against trees? I try and hug one every day...

Tree hugger.

---

### Post by warfacegod on 2010-01-23
73ckn797 has given me an excellent idea for my next post.

---

### Post by chillicampari on 2010-01-24
> **warfacegod said:**
> 73ckn797 has given me an excellent idea for my next post.

Hmm...(furrows brow in a concerned manner).

---

### Post by warfacegod on 2010-01-24
> **chillicampari said:**
> Hmm...(furrows brow in a concerned manner).

Considering the general theme of this thread, concern is a perfectly reasonable response.

---

### Post by s_ø on 2010-01-24
IF you want t do something stupid to your system. Boot another system and chown / on the 'stupid' system to a user on the one you just booted.

---

### Post by warfacegod on 2010-01-24
> **s_ø said:**
> IF you want t do something stupid to your system. Boot another system and chown / on the 'stupid' system to a user on the one you just booted.

I tried that a while ago, nothing happened. Thanks though. This thread has gone from idiocy I'm doing to my second OS to idiocy in general. Although I am looking for ideas on what I can remove from UNR and have it still function.

---

### Post by 73ckn797 on 2010-01-24
> **audiomick said:**
> What have you guys got against trees? I try and hug one every day...

Around these parts, if a tornado blows through and I am stuck outside, then that would be about the only time I would feel the need to hug a tree. I do not want to get blown away.:)

---

### Post by 73ckn797 on 2010-01-24
> **warfacegod said:**
> 73ckn797 has given me an excellent idea for my next post.
What in the world did I suggest this time? A new method of deforestation?

---

### Post by warfacegod on 2010-01-24
> **73ckn797 said:**
> What in the world did I suggest this time? A new method of deforestation?

Patience Grasshopper.

---

### Post by 73ckn797 on 2010-01-24
> **warfacegod said:**
> Patience Grasshopper.

Yes, the rice paper is tearing right now.

---

### Post by Leppie on 2010-01-24
> **73ckn797 said:**
> Let me know how that works out. I have 30 pine trees I'd like to take down.
sell them as xmas trees... ;)

---

### Post by warfacegod on 2010-01-24
Christmas is a taboo word in the U.S., at least it is in the north, in Yankee Land. You'd have to sell them as "Happy Holidays" trees.

---

### Post by audiomick on 2010-01-24
> **warfacegod said:**
> Christmas is a taboo word in the U.S., at least it is in the north, in Yankee Land. You'd have to sell them as "Happy Holidays" trees.
That's a new one for me. Why is that?

---

### Post by Leppie on 2010-01-24
> **warfacegod said:**
> Christmas is a taboo word in the U.S., at least it is in the north, in Yankee Land. You'd have to sell them as "Happy Holidays" trees.
how about a "hanukkah" tree?

---

### Post by warfacegod on 2010-01-24
> **audiomick said:**
> That's a new one for me. Why is that?

Not actually as "Happy Holidays" trees  but the concept is sound. The Liberals in my country have gotten everyone so paranoid about political correctness and offending people that every single "Civil Service" employee that I've spoken to in the last five years, has been mandated by the government or their department policies to say "Happy Holidays" not "Merry Christmas"

Read "Civil Service" as: Congressman, Secretary, Aide, Police Officer, Firefighter, and any others that I can't recall at the moment.

It's gotten so bad here that I had a Bestbuy computer department floor guy refer to me as an "Other Operating System Choice User". I tried to convince him to kill himself so that he could be an "Other Life State Choice Preference Decider". He tried to throw me out until I told his Manager that I didn't want to be an "Other Store Option Engager" nor did I like the prospect of being an "Interiorily Challenged Consumer Person". He agreed with me emphatically, so I said good because I wasn't looking forward to becoming a "Brick Wielding Window Specialist" and left.

---

### Post by 73ckn797 on 2010-01-24
> **Leppie said:**
> sell them as xmas trees... ;)

I am talking about 60 foot tall pine trees, the ones with pine cones, sap and squirrel nests.

---

### Post by warfacegod on 2010-01-24
> **73ckn797 said:**
> I am talking about 60 foot tall pine trees, the ones with pine cones, sap and squirrel nests.

Sell them to N.Y. city. They'll have a sixty year stock that way.

---

### Post by audiomick on 2010-01-24
> **73ckn797 said:**
> I am talking about 60 foot tall pine trees, the ones with pine cones, sap and squirrel nests.

Ah, the beauties of Nature!

@ warfacegod
> The Liberals in my country have gotten everyone so paranoid about political correctness and offending peoplenothing exceeds like excess eh? Sounds reminiscent of the "positive discrimination" phenomenum as practiced in Australia in the late 80's and early 90's.

---

### Post by 73ckn797 on 2010-01-24
> **audiomick said:**
> Ah, the beauties of Nature!
Not when they fall on the house. Today that could happen since we have had so much rain and a severe thunder storm warning for the area today.

---

### Post by audiomick on 2010-01-24
> **73ckn797 said:**
> Not when they fall on the house.
More beauties of nature:
My brother used to live in a house with a big loquat tree
[http://en.wikipedia.org/wiki/Loquat](http://en.wikipedia.org/wiki/Loquat)
over the carport. The fruit has 2 half inch big seeds in it. The possums would get up the tree and drop the seeds 20 feet onto the tin roof of the carport all night. Cute little fellas...

---

### Post by warfacegod on 2010-01-24
> **audiomick said:**
> More beauties of nature:
My brother used to live in a house with a big loquat tree
[http://en.wikipedia.org/wiki/Loquat](http://en.wikipedia.org/wiki/Loquat)
over the carport. The fruit has 2 half inch big seeds in it. The possums would get up the tree and drop the seeds 20 feet onto the tin roof of the carport all night. Cute little fellas...

Are they edible? The seeds, I mean, being a Redneck, I already know that you can eat possum.

---

### Post by audiomick on 2010-01-24
> **warfacegod said:**
> Are they edible? The seeds, I mean...

Not really, but they are good for throwing at possums...;)

---

### Post by warfacegod on 2010-01-24
> **audiomick said:**
> Not really, but they are good for throwing at possums...;)

So that you can eat the possums?

---

### Post by audiomick on 2010-01-24
> **warfacegod said:**
> So that you can eat the possums?

Kangaroo is better. More meat on them.

---

### Post by 73ckn797 on 2010-01-24
> **warfacegod said:**
> Are they edible? The seeds, I mean, being a Redneck, I already know that you can eat possum.


There are plenty of possums around here. There are also armadillo and we call them possum on the half shell. Both can be found along the road. If you are lucky one of them might be a fresh road kill, still warm. That is as long as the vultures and crows have not started feasting on them.

---

### Post by Leppie on 2010-01-24
i'd stick with the kangaroo, or maybe some gator...

---

### Post by warfacegod on 2010-01-24
> **73ckn797 said:**
> There are plenty of possums around here. There are also armadillo and we call them possum on the half shell. Both can be found along the road. If you are lucky one of them might be a fresh road kill, still warm. That is as long as the vultures and crows have not started feasting on them.

Why not eat the vultures and crows too?

---

### Post by llawwehttam on 2010-01-24
> **warfacegod said:**
> I'm going to resize my sda1 partition. I'm going to install 9.10 NBR as a dual with normal 9.10 on my laptop. Why you ask? Because I feel like it.
Can any one give me a decent partition size for NBR?


You see? This is what happens when you start computing with Windows. I start going:

"My Linux installs are perfect? There's nothing for me to fix? Sigh. Good grief, I am bored! Let me go screw up my laptop again so I can have something to do"

And that's after three years of being Windows free. Ubuntu: The Windows 12 Step Program

This described the object of my life lol.
Make a problem so I have something to fix to keep me from boredom.

---

### Post by warfacegod on 2010-01-24
> **Leppie said:**
> i'd stick with the kangaroo, or maybe some gator...

Kammodo dragon anyone?


(I just searched ixquick for "kammodo" and it asked me if I meant "jammed")

---

### Post by 73ckn797 on 2010-01-24
> **warfacegod said:**
> Why not eat the vultures and crows too?

They are harder to capture. I would need a shotgun but then would have to clean out all of the pellets.

---

### Post by warfacegod on 2010-01-24
> **73ckn797 said:**
> They are harder to capture. I would need a shotgun but then would have to clean out all of the pellets.

Use a taser.

---

### Post by 73ckn797 on 2010-01-24
> **warfacegod said:**
> Use a taser.
Can't get close enough, they fly off.

---

### Post by warfacegod on 2010-01-24
> **73ckn797 said:**
> Can't get close enough, they fly off.

Use the kind that shoot out the wires.

---

### Post by warfacegod on 2010-01-24
[CENTER][SIZE="5"]_Dumb Redneck Computer Stunts_
[/SIZE]
or

[SIZE="4"]_A List Of Things Not To Do To A Computer And Possibly Get Killed Doing Them_[/SIZE]
(Yankees Rednecks should pay attention too.)
[/CENTER]

.01 No matter how big your screen is, it will not double as a boogie board
.02 Sledding down an embankment on it, into your local pond is also not advised
.03 No matter how many laptops you strap to your arms, the lids will not act as airplane wing flaps
.04 Using your desktop case to make Moonshine in won't work and might give you lead    poisoning if it did
.05 Your mother board cannot be used to replace a broken plow furrow blade
.06 Computer tipping isn't nearly as much fun as cow tipping which, frankly, isn't very fun
.07 Stitching thousands of salvaged processors onto your overalls will not make you invisible like the Predator
.08 Using Paint to make a smiley face for your desktop does not make your computer a person, it will not be able to learn to drive your Camarro
.09 I'm not even going to mention thermal grease, you know what you shouldn't do with it
.10 Reshaping computer cases into armor will not make you bullet proof
.11 Bungee jumping with USB and mouse cables duct taped together is 100% fatal
.12 Hanging a Windows machine in effigy on a Mac or Linux users lawn is crass and immoral
.13 Putting your old slant six engine on desktop computers in your front yard is tacky, use cinder blocks
.14 Bringing your laptop to a Lynard Skynard concert, for the band to sign, will get you lynched
.15 Attaching legs to your laptop and eating possum stew on it while browsing  is not multitasking
.16 RAM chips are not meant for replacing missing teeth
.17 Catapulting computer parts at your neighbors livestock only will give him more ammunition for catapulting computer parts at yours
.18 Laptops bolted to the front of your truck will not work as a snowplow
.19 LCD screens strapped to your feet will not work as skis
.20 Using a computer case as the compression chamber for a potato cannon will always end in disaster

---

### Post by 73ckn797 on 2010-01-24
> **warfacegod said:**
> [CENTER][SIZE=5]_Dumb Redneck Computer Stunts_
[/SIZE]
or

[SIZE=4]_A List Of Things Not To Do To A Computer And Possibly Get Killed Doing Them_[/SIZE]
(Yankees Rednecks should pay attention too.)
[/CENTER]

.01 No matter how big your screen is, it will not double as a boogie board
.02 Sledding down an embankment on it, into your local pond is also not advised
.03 No matter how many laptops you strap to your arms, the lids will not act as airplane wing flaps
.04 Using your desktop case to make Moonshine in won't work and might give you lead    poisoning if it did
.05 Your mother board cannot be used to replace a broken plow furrow blade
.06 Computer tipping isn't nearly as much fun as cow tipping which, frankly, isn't very fun
.07 Stitching thousands of salvaged processors onto your overalls will not make you invisible like the Predator
.08 Using Paint to make a smiley face for your desktop does not make your computer a person, it will not be able to learn to drive your Camarro
.09 I'm not even going to mention thermal grease, you know what you shouldn't do with it
.10 Reshaping computer cases into armor will not make you bullet proof
.11 Bungee jumping with USB and mouse cables duct taped together is 100% fatal
.12 Hanging a Windows machine in effigy on a Mac or Linux users lawn is crass and immoral
.13 Putting your old slant six engine on desktop computers in your front yard is tacky, use cinder blocks
.14 Bringing your laptop to a Lynard Skynard concert, for the band to sign, will get you lynched
.15 Attaching legs to your laptop and eating possum stew on it while browsing  is not multitasking
.16 RAM chips are not meant for replacing missing teeth
.17 Catapulting computer parts at your neighbors livestock only will give him more ammunition for catapulting computer parts at yours
.18 Laptops bolted to the front of your truck will not work as a snowplow
.19 LCD screens strapped to your feet will not work as skis
.20 Using a computer case as the compression chamber for a potato cannon will always end in disaster

HA! Too much to comment on here but very funny.

---

### Post by warfacegod on 2010-01-24
So I managed to totally frag my system and I have no idea how, primarily because I wasn't trying to break it at the moment. And it happened to the install I wasn't trying to break. I got a grub prompt. I tried every command in step #15 here: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275") and got either "unknown command" or "file not found".

I think this may be related to what's going on in this thread: [http://ubuntuforums.org/showthread.php?t=1385774]("http://ubuntuforums.org/showthread.php?t=1385774") but at the moment, I'm just not sure.

---

### Post by audiomick on 2010-01-25
Ooops...
Have you run that boot info script on it? What does it tell you?
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by warfacegod on 2010-01-25
> **audiomick said:**
> Ooops...
Have you run that boot info script on it? What does it tell you?
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Unfortunately, I have no way of getting it to my laptop. My internal disc drive is fragged, my laptop won't boot from my external, I just erased my USB install disc and my wife broke the USB ports on her computer so I can't make another one.

---

### Post by audiomick on 2010-01-25
having a good day then...

---

### Post by warfacegod on 2010-01-25
> **audiomick said:**
> having a good day then...

I must grok further upon your words.

---

### Post by 73ckn797 on 2010-01-25
> **warfacegod said:**
> I must grok further upon your words.

Grok?
```

Main Entry: grok Pronunciation: \&#712;gräk\
Function:  transitive verb 
Inflected Form(s): grokked; grok·king
Etymology: coined by Robert A. Heinlein †1988 American author
Date: 1961
 : to understand profoundly and intuitively


```
Now it makes sense!

---

### Post by warfacegod on 2010-01-25
> **73ckn797 said:**
> Grok?
```

Main Entry: grok Pronunciation: \&#712;gräk\
Function:  transitive verb 
Inflected Form(s): grokked; grok·king
Etymology: coined by Robert A. Heinlein †1988 American author
Date: 1961
 : to understand profoundly and intuitively


```
Now it makes sense!

A very shallow and superficial definition of the word as Heinlein envisioned it. Perhaps cherishing, embracing, loving, learning, encompassing, and studying should be adding to that definition. Yet, it still would be shallow and superficial just slightly less so.

---

### Post by warfacegod on 2010-01-25
73ckn797

Almost didn't recognize you with that newfangled hairdo.

---

### Post by warfacegod on 2010-01-25
I'm going to borrow my neighbors' laptop so that I can use unetbootin to make a new LiveUSB.



I'm still gonna burn his tree down though.

---

### Post by Leppie on 2010-01-25
> **warfacegod said:**
> 73ckn797

Almost didn't recognize you with that newfangled hairdo.
maybe he went by edward's...

---

### Post by warfacegod on 2010-01-25
> **Leppie said:**
> maybe he went by edward's...

I was thinking somewhere with a guy playing banjo on the front porch and no shoes on.

---

### Post by nothingspecial on 2010-01-25
Hey, Warface, 

If you want to do some thing really stupid, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1387822").

I`ll race you to fix it.........say go!

---

### Post by warfacegod on 2010-01-25
> **nothingspecial said:**
> Hey, Warface, 

If you want to do some thing really stupid, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1387822").

I`ll race you to fix it.........say go!

You win. My laptop stalled before even getting to the starting line.

---

### Post by nothingspecial on 2010-01-25
Haha, the easiest way to fix "that" is a reinstall.

But I have to big up the stupidness of it.

---

### Post by warfacegod on 2010-01-25
> **nothingspecial said:**
> Haha, the easiest way to fix "that" is a reinstall.

But I have to big up the stupidness of it.

Can't. See post #166.

---

### Post by nothingspecial on 2010-01-25
Huh, wives.

I bet she`s worth it though, just like mine.

Frustrating - yes.

But we forgive them.

And toasted hard drives, bah, We get new ones and copy our backups across.

---

### Post by audiomick on 2010-01-25
From the Wikipedia> 
In Heinlein's view, grokking is the intermingling of intelligence that necessarily affects both the observer and the observed.
[http://en.wikipedia.org/wiki/Grok](http://en.wikipedia.org/wiki/Grok)

---

### Post by nothingspecial on 2010-01-25
Oh Grok!!!

I`m Grokked!!!!!

I have Grokked!

I`m Grokking up ?!?!

---

### Post by nothingspecial on 2010-01-25
> **audiomick said:**
> From the Wikipedia
[http://en.wikipedia.org/wiki/Grok](http://en.wikipedia.org/wiki/Grok)

Thank you for responding to this thread.

A response of such insight and understanding can only help a thread as serious as this ;)

Honestly, we value your insight and contribution.

Night, night :D

---

### Post by warfacegod on 2010-01-25
Just when I thought all hope was lost for this thread, dignity is restored.

---

### Post by warfacegod on 2010-01-25
I need to grok on ways to ruin it again. ....where's the nearest pool?....

---

### Post by 73ckn797 on 2010-01-25
> **warfacegod said:**
> I was thinking somewhere with a guy playing banjo on the front porch and no shoes on.
You talking about me?

I do play occasionally with a guy who has a banjo. He also has several Stratocasters, an electric bass, several acoustics, a mandolin, a fiddle and an upright bass but I keep my shoes on.

---

### Post by 73ckn797 on 2010-01-25
> **warfacegod said:**
> A very shallow and superficial definition of the word as Heinlein envisioned it. Perhaps cherishing, embracing, loving, learning, encompassing, and studying should be adding to that definition. Yet, it still would be shallow and superficial just slightly less so.

Ain't my definition.

---

### Post by warfacegod on 2010-01-25
> **73ckn797 said:**
> You talking about me?

I do play occasionally with a guy who has a banjo. He also has several Stratocasters, an electric bass, several acoustics, a mandolin, a fiddle and an upright bass but I keep my shoes on.

I have a Jackson King V.

---

### Post by warfacegod on 2010-01-25
> **nothingspecial said:**
> Oh Grok!!!

I`m Grokked!!!!!

I have Grokked!

I`m Grokking up ?!?!

Linux does not, however, assume you grok what you are doing.

---

### Post by Leppie on 2010-01-25
> **warfacegod said:**
> Linux does not, however, assume you grok what you are doing.
what does linux assume you grok?

---

### Post by warfacegod on 2010-01-26
> **Leppie said:**
> what does linux assume you grok?

Linux groks that we grok nothing, including Linux.

---

### Post by audiomick on 2010-01-26
Have you grokked your laptop yet?

---

### Post by warfacegod on 2010-01-26
> **audiomick said:**
> Have you grokked your laptop yet?

Oh, I grokked it long since. I grok that I'm about to grok it out the damn window.



Actually, all will be well when I can get my hands on a machine with a working USB port. Leppie assisted me with GRUB Rescue, last evening, and we confirmed what I had suspected through my own work on it ealier. That GRUB grokked itself out of partial existence.

---

### Post by audiomick on 2010-01-26
> **warfacegod said:**
> Actually, all will be well when I can get my hands on a machine with a working USB port. Leppie assisted me with GRUB Rescue, last evening, and we confirmed what I had suspected through my own work on it ealier. That GRUB grokked itself out of partial existence.

That's good to hear. Any idea what happened, or is it one of those little mysteries that life presents us to keep us on our toes?

---

### Post by warfacegod on 2010-01-26
> **audiomick said:**
> That's good to hear. Any idea what happened, or is it one of those little mysteries that life presents us to keep us on our toes?

Best guess? Ghost in the machine.

---

### Post by audiomick on 2010-01-26
> **warfacegod said:**
> Best guess? Ghost in the machine.

I hate it when that happens...

---

### Post by 73ckn797 on 2010-01-26
Isn't grok also the sound of a frog with a sore throat?

---

### Post by audiomick on 2010-01-26
> **73ckn797 said:**
> Isn't grok also the sound of a frog with a sore throat?

no, I think it is the sound when you step on one...

---

### Post by nothingspecial on 2010-01-26
> **73ckn797 said:**
> Isn't grok also the sound of a frog with a sore throat?

Groak,

---

### Post by warfacegod on 2010-01-26
> **nothingspecial said:**
> Groak,

When frogs croak, they go groak.

---

### Post by nothingspecial on 2010-01-26
groak, groak

---

### Post by 73ckn797 on 2010-01-26
> **audiomick said:**
> no, I think it is the sound when you step on one...
No that is more of a squish noise.

---

### Post by warfacegod on 2010-01-26
Anybody know how to fix a broken USB port?

[http://ubuntuforums.org/showthread.php?p=8729353#post8729353]("http://ubuntuforums.org/showthread.php?p=8729353#post8729353")

---

### Post by Leppie on 2010-01-27
> **warfacegod said:**
> Anybody know how to fix a broken USB port?

[http://ubuntuforums.org/showthread.php?p=8729353#post8729353](http://ubuntuforums.org/showthread.php?p=8729353#post8729353)
take a war hammer and give it some good'ol bashin?

---

### Post by warfacegod on 2010-01-27
> **Leppie said:**
> take a war hammer and give it some good'ol bashin?

Mjollnir's on vacation in Bermuda. It won't be back until spring. The day after I get my newlaptop.

---

### Post by Leppie on 2010-01-28
> **warfacegod said:**
> Mjollnir's on vacation in Bermuda. It won't be back until spring. The day after I get my newlaptop.
you can never rely on anybody when you need them...

---

### Post by warfacegod on 2010-01-28
> **Leppie said:**
> you can never rely on anybody when you need them...

You know the world has become too self-centered when even divine weapons don't want to help you out of a jam.

---

### Post by Leppie on 2010-01-28
> **warfacegod said:**
> You know the world has become too self-centered when even divine weapons don't want to help you out of a jam.
always better to never rely on anybody or anything...

---

### Post by audiomick on 2010-01-28
> **Leppie said:**
> always better to never rely on anybody or anything...

except Murphy. He is always right.

---

### Post by Leppie on 2010-01-28
> **audiomick said:**
> except Murphy. He is always right.
except when you rely on him to be right... otherwise his law wouldn't be universal...

---

### Post by warfacegod on 2010-01-28
Murphy was a grunt.

---

### Post by Leppie on 2010-01-28
> **warfacegod said:**
> Murphy was a grunt.
but a famous grunt...

---

### Post by warfacegod on 2010-01-28
> **Leppie said:**
> but a famous grunt...

Did Murphy use a 32 or 64 Bit? Did he even know?

Okay, I promise, last time!

---

### Post by Leppie on 2010-01-28
> **warfacegod said:**
> Did Murphy use a 32 or 64 Bit? Did he even know?

Okay, I promise, last time!
i think he used a 1 bitter... :P

---

### Post by warfacegod on 2010-01-29
> **Leppie said:**
> i think he used a 1 bitter... :P

So he was the guy that invented, what amounted to a pocket calculator, for the Apollo guys to fly to the Moon with.

---

### Post by audiomick on 2010-01-29
> **warfacegod said:**
> So he was the guy that invented, what amounted to a pocket calculator, for the Apollo guys to fly to the Moon with.

You'd need a big pocket for one of those rockets...

---

### Post by warfacegod on 2010-01-29
> **audiomick said:**
> You'd need a big pocket for one of those rockets...

Yeah, I stuck my neck out on that one. Seriously though, the computer on those rockets had the computing power of a modern pocket calculator. I think the NASA clowns are using Windows based computers in the stuff they launch now. If give a choice, I'll take the Saturn V computer any day.

---

### Post by audiomick on 2010-01-29
> **warfacegod said:**
> Yeah, I stuck my neck out on that one. Seriously though, the computer on those rockets had the computing power of a modern pocket calculator. I think the NASA clowns are using Windows based computers in the stuff they launch now. If give a choice, I'll take the Saturn V computer any day.

I used a thing at Uni called a PDP 11/10
6 feet high, 19 inch rack. It had a row of 16 switches on the front, and an enter switch. You programmed it in machine code by setting the switches bit for bit and pressing enter, line for line. It took about 15 minutes to program a one cycle sine wave look up table. But it didn't crash...

I saw a memory card out of one that a mate had a few years later: A grid of wires with a little lump of ferro-magnetic stuff at each crossing. 19" square and 1k of memory.

---

### Post by warfacegod on 2010-01-29
> **audiomick said:**
> I used a thing at Uni called a PDP 11/10
6 feet high, 19 inch rack. It had a row of 16 switches on the front, and an enter switch. You programmed it in machine code by setting the switches bit for bit and pressing enter, line for line. It took about 15 minutes to program a one cycle sine wave look up table. But it didn't crash...

I saw a memory card out of one that a mate had a few years later: A grid of wires with a little lump of ferro-magnetic stuff at each crossing. 19" square and 1k of memory.

You watching Frankenstien again?

---

### Post by audiomick on 2010-01-29
> **warfacegod said:**
> You watching Frankenstien again?

Waiting for that lightning strike. MWAAHAHAHAHAHA....

---

### Post by warfacegod on 2010-01-29
> **audiomick said:**
> Waiting for that lightning strike. MWAAHAHAHAHAHA....

That was an excellent evil scientist guffaw! I see your catching up in beans. You'll pass Leppie and me in no time.


(Now where's my sinister bean amplifying machine...?)

---

### Post by warfacegod on 2010-01-30
[size="7"]i fixed my laptop![/size]:P:P:P=D>=D>=D>=D>=D>

---

### Post by audiomick on 2010-01-31
> **warfacegod said:**
> [size="7"]i fixed my laptop![/size]:P:P:P=D>=D>=D>=D>=D

:popcorn:

---

### Post by Kai69 on 2010-01-31
Good work now install ************* linux:lolflag::KS:KS:KS:KS:KS

---

### Post by nothingspecial on 2010-01-31
[SIZE="5"]So[/SIZE].............


.........[COLOR="Magenta"][SIZE="5"]Break it again[/SIZE][/COLOR]

---

### Post by warfacegod on 2010-01-31
> **nothingspecial said:**
> [SIZE="5"]So[/SIZE].............


.........[COLOR="Magenta"][SIZE="5"]Break it again[/SIZE][/COLOR]

Why does *no one* believe me that I didn't do it!?

I'm trying to make a list of things to delete out of UNR to turn it into almost a minimal install.

---

### Post by nothingspecial on 2010-01-31
Break your system once a week .... minimum.

If you don`t do that you`re not doing it properly.

---

### Post by Kai69 on 2010-01-31
You could delete grub that might give you a very minimal install.:p

---

### Post by Leppie on 2010-01-31
remove all apt apps...

---

### Post by warfacegod on 2010-01-31
> **Kai69 said:**
> You could delete grub that might give you a very minimal install.:p

I just fix GRUB and you tell me to break it again.:tongue: Nope, not gonna happen!

I'll do you one better:

```
sudo apt-get purge mybrain0.00
```

---

### Post by Kai69 on 2010-01-31
I did that last week I now sudo apt-get Install marbles0.01  :tongue:

---

### Post by lisati on 2010-01-31
> **Kai69 said:**
> I did that last week I now sudo apt-get Install marbles0.01  :tongue:

I think I've lost mine:
> Package marbles is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lmarbles
E: Package marbles has no installation candidate


---

### Post by Kai69 on 2010-01-31
OK try sudo apt-get Install nuts0.2 ;)

---

### Post by warfacegod on 2010-01-31
See! I knew it wouldn't take too long for us to fall back into the abyss of ... whatever this thread has become.

---

### Post by lisati on 2010-01-31
> **Kai69 said:**
> OK try sudo apt-get Install nuts0.2 ;)
I could go somewhere with this one but choose not to! 
> **warfacegod said:**
> See! I knew it wouldn't take too long for us to fall back into the abyss of ... whatever this thread has become.

:D 

On a slightly more serious note: there *is* a certain satisfaction in getting things working how you like.

---

### Post by Kai69 on 2010-01-31
Oh go on you know you want to ;)

---

### Post by Kai69 on 2010-01-31
Hi warface have you made your minimal list yet for UNR ..

---

### Post by warfacegod on 2010-01-31
> **lisati said:**
> I could go somewhere with this one but choose not to! 


:D 

On a slightly more serious note: there *is* a certain satisfaction in getting things working how you like.

Basically, I'm looking to tear the guts out of UNR and have it still work. GUI, Internet, etc.

---

### Post by Leppie on 2010-01-31
why don't you try removing upstart?
```
sudo apt-get purge upstart
```

---

### Post by audiomick on 2010-01-31
> **Leppie said:**
> why don't you try removing upstart?
```
sudo apt-get purge upstart
```

I hate upstarts. They should all be removed...

---

### Post by Leppie on 2010-01-31
> **audiomick said:**
> I hate upstarts. They should all be removed...
i actually quite like them, they're not so hard to configure.
at the moment the difficulty lies more in the fact that we've got a hybrid system.
hopefully they really do complete the whole upstart transition for the launch of lucid.

---

### Post by audiomick on 2010-01-31
> **Leppie said:**
> i actually quite like them, they're not so hard to configure.
at the moment the difficulty lies more in the fact that we've got a hybrid system.
hopefully they really do complete the whole upstart transition for the launch of lucid.

sorry leppie, it was a (bad, i.e. the best sort) pun.;)

---

### Post by 73ckn797 on 2010-01-31
> **warfacegod said:**
> [SIZE=7]i fixed my laptop![/SIZE]:P:P:P=D>=D>=D>=D>=D>

What did you do to fix it? Drink a redneck beer and grok over it a while?

---

### Post by Kai69 on 2010-01-31
Hes broken it again hasnt he its gone very quiet :lolflag:

---

### Post by Leppie on 2010-01-31
> **73ckn797 said:**
> What did you do to fix it? Drink a redneck beer and grok over it a while?
i think he got some bits and pieces from the scrapyards, then poured a beer over it and used 10,000 volts to re-animate it... ;)

---

### Post by Leppie on 2010-01-31
> **Kai69 said:**
> Hes broken it again hasnt he its gone very quiet :lolflag:
most probably... lol

---

### Post by Kai69 on 2010-01-31
Maybe hes making Frankinstein out of it , try using 20.000v see if that helps...;)

---

### Post by warfacegod on 2010-01-31
> **73ckn797 said:**
> What did you do to fix it? Drink a redneck beer and grok over it a while?

When you bring it all down to basic facts, all beer is Redneck beer.

Actually I put my speakers in front of it a played, at full volume, Garth Brooks "Friends In Low Places".

---

### Post by warfacegod on 2010-01-31
> **Kai69 said:**
> Hes broken it again hasnt he its gone very quiet :lolflag:

I didn't go anywhere. It just took me this long to read through all the comments you clowns posted since I lasted looked.

---

### Post by audiomick on 2010-01-31
> **warfacegod said:**
> When you bring it all down to basic facts, all beer is Redneck beer.

Actually I put my speakers in front of it a played, at full volume, Garth Brooks "Friends In Low Places".

You evil evil man. How could you do that to a poor innocent computer?

---

### Post by Kai69 on 2010-01-31
Hes trying to kill it now cant you use that cd as a beer mat :p

---

### Post by 73ckn797 on 2010-01-31
> **warfacegod said:**
> When you bring it all down to basic facts, all beer is Redneck beer.

Actually I put my speakers in front of it a played, at full volume, Garth Brooks "Friends In Low Places".
That song is a redneck song!

---

### Post by audiomick on 2010-01-31
> **73ckn797 said:**
> That song is a redneck song!

That's why our favourite deity chose it. He wrote something the other day about a "Slayer" t-shirt, but I don't believe a word of it!

---

### Post by Kai69 on 2010-01-31
Its dead.

---

### Post by warfacegod on 2010-01-31
[QUOTE=73ckn797]That song is a redneck song![/QUOTE]

Yes. That is indeed a Redneck song. It's probably in the top 5 of Redneckiest of Redneck songs ever. This did not escape me.

[QUOTE=audiomick]You evil evil man. How could you do that to a poor innocent computer? [/QUOTE]

It was either Garth Brooks or Manowar. Either way it would have been evil...pure Eevviillll!

Speaking of Manowar, "The Dawn of Battle" just came on, let me put my laptop back between the speakers.

---

### Post by warfacegod on 2010-01-31
> **audiomick said:**
> That's why our favourite deity chose it. He wrote something the other day about a "Slayer" t-shirt, but I don't believe a word of it!

Oh! Ye naysayers and cynics. Heed me, thee of little faith for I am The warfacegod. (<<<See? *Capital* T)

---

### Post by audiomick on 2010-01-31
> **warfacegod said:**
> Oh! Ye naysayers and cynics. Heed me, thee of little faith for I am The warfacegod. (<<<See? *Capital* T)

But no capital W, I notice...

---

### Post by warfacegod on 2010-01-31
> **audiomick said:**
> But no capital W, I notice...

Easier to type with no capital for logging in. I never claimed I wasn't a *lazy* The warfacegod.:tongue:

---

### Post by Kai69 on 2010-01-31
If your that lazy why didnt you just use wfg  :tongue:

---

### Post by warfacegod on 2010-01-31
> **Kai69 said:**
> If your that lazy why didnt you just use wfg  :tongue:

Didn't want you guys deciding J-Lo wanted to be like me. Besides, people wouldn't be as offended by wfg.

---

### Post by Kai69 on 2010-01-31
At least didnt use H Lo  :lolflag:

---

### Post by warfacegod on 2010-01-31
Wasn't "thou shalt not try my patience" one of the ten commandments?

---

### Post by Kai69 on 2010-01-31
[http://www.youtube.com/watch?v=oZoxdiDdlyY](http://www.youtube.com/watch?v=oZoxdiDdlyY) :lolflag:

---

### Post by Leppie on 2010-01-31
> **warfacegod said:**
> Wasn't "thou shalt not try my patience" one of the ten commandments?
wasn't that from some book of a religion that did not include any warfacegod? :P

---

### Post by Kai69 on 2010-01-31
Sorry about that he takes the **** out of my favorite band as well 2nd part :lolflag:[http://www.youtube.com/watch?v=WeNLlC64HCY&feature=related](http://www.youtube.com/watch?v=WeNLlC64HCY&feature=related)

---

### Post by 73ckn797 on 2010-01-31
> **leppie said:**
> wasn't that from some book of a religion that did not include any warfacegod? :p
yep!

---

### Post by audiomick on 2010-01-31
@ kai69
I learn't "do the hokey pokey" 41 years ago in kindergarten, and I never realised that it was a Kraftwerk song!!!

---

### Post by audiomick on 2010-01-31
> **warfacegod said:**
> Wasn't "thou shalt not try my patience" one of the ten commandments?

Number 11, I think...

---

### Post by 73ckn797 on 2010-01-31
> **warfacegod said:**
> Oh! Ye naysayers and cynics. Heed me, thee of little faith for I am The warfacegod. (<<<See? *Capital* T)
And one (a god, little g) who doesn't seem to have any sovereignty over a measly little laptop computer but has to rely on other external resources. :guitar:

---

### Post by Kai69 on 2010-01-31
Audiomick What are you in Germany for ( sag hallo zu Hameln bitte ):p

---

### Post by audiomick on 2010-01-31
> **Kai69 said:**
> Audiomick What are you in Germany for ( sag hallo zu Hameln bitte ):p

Hallo Kai.
Was soll ich sagen:  Abenteur, was Neues erleben, Arbeit, die Welt sehen, na gut... da gibt's ja auch so'ne Frau....
Hameln ist ein Bißchen weiter weg. Ich bin zur Zeit in Heilbronn, unter den (Schauder...) Schwaben.

---

### Post by Leppie on 2010-01-31
how come there's always a woman involved??? :P

---

### Post by audiomick on 2010-01-31
> **Leppie said:**
> how come there's always a woman involved??? :P

What can I say? I'm actually on the second attempt here... But this time it looks good. :)

---

### Post by Kai69 on 2010-01-31
Hallo Micheal
Wie lange leben sie jetz im Deutchland. Das letstes mal das ich im Deutchland gewohnt habe war 82 aber ich bin da geboren in Hameln..

Sorry if my spelling isnt so good i havent been there for so long ( how do you get the keyboard to change ) 

SORRY ALL please continue thread;)

---

### Post by lisati on 2010-01-31
> **audiomick said:**
> @ kai69
I learn't "do the hokey pokey" 41 years ago in kindergarten, and I never realised that it was a Kraftwerk song!!!

I think the dances is actually the "hokey cokey." I sometimes eat hokey pokey ice cream. For the uninitiated it's vanilla ice cream with small lumps of toffee mixed in. See [here]("http://en.wikipedia.org/wiki/Hokey_pokey_(ice_cream)") for more information.

---

### Post by warfacegod on 2010-01-31
Here's German, Metal, and Redneck are thrown together:

Die Apokalyptischen Reiter doing a cover song of Johnny Cash "Ghost Riders In The Sky".

---

### Post by Kai69 on 2010-01-31
could you upload for us :p

---

### Post by warfacegod on 2010-01-31
> **Leppie said:**
> wasn't that from some book of a religion that did not include any warfacegod? :P

Wrath of god, brimstone, vengeance is mine, pillars of salt, seven plagues of Egypt, floods, curses from god, killing heathens. Old Testament's got me all through it.

---

### Post by warfacegod on 2010-01-31
> **Kai69 said:**
> could you upload for us :p

[http://www.youtube.com/watch?v=thjCnWf-kEI]("http://www.youtube.com/watch?v=thjCnWf-kEI")

---

### Post by 73ckn797 on 2010-01-31
> **warfacegod said:**
> Wrath of god, brimstone, vengeance is mine, pillars of salt, seven plagues of Egypt, floods, curses from god, killing heathens. Old Testament's got me all through it.
Does that make you an "ancient of daze"? (little a)

---

### Post by Kai69 on 2010-01-31
GERMAN Rednecks what next  :lolflag:

---

### Post by 73ckn797 on 2010-01-31
> **Kai69 said:**
> GERMAN Rednecks what next  :lolflag:
Do they also drive a trick-up puck?

---

### Post by audiomick on 2010-01-31
> **warfacegod said:**
> Here's German, Metal, and Redneck are thrown together:

Die Apokalyptischen Reiter doing a cover song of Johnny Cash "Ghost Riders In The Sky".

"My grandmother drowned in the Grotto at Lourdes when a Dwarf in a wheelchair pushed her in." (Yodel a-hi-a-hi-a-hi-uhuwoo) - Billy Connolly

@ Kai
Been here 14 years.
Keyboard change? Easy: German keyboard and German installation so my girlfriend can understand it... ;)

---

### Post by Kai69 on 2010-01-31
Nah BMW is chopping the roof of an X5 :D

---

### Post by Kai69 on 2010-01-31
Audiomick can I do english install but able to switch to german keyboard and back again  ?:D

---

### Post by audiomick on 2010-01-31
> **Kai69 said:**
> Audiomick can I do english install but able to switch to german keyboard and back again  ?:D

You can; I have read several threads on the subject, but I have no idea how to do it.:redface:
I don't need to, so I didn't take note of it.

---

### Post by 73ckn797 on 2010-01-31
> **audiomick said:**
> You can; I have read several threads on the subject, but I have no idea how to do it.:redface:
I don't need to, so I didn't take note of it.
Use this search tool and you can find valuable info.
[http://www.uboontu.com](http://www.uboontu.com)

---

### Post by Kai69 on 2010-01-31
It just looks so wrong ( SS " )  missus is doing a german degree I keep well out of it unless she asks for help :D But she uses vista because its with the OU .

---

### Post by warfacegod on 2010-01-31
> **73ckn797 said:**
> Do they also drive a trick-up puck?


Camouflage trick-up pucks so the SS won't catch 'em running moonshine across the wall.

---

### Post by Kai69 on 2010-01-31
Wall came down Vodka came through :p

---

### Post by audiomick on 2010-01-31
> **Kai69 said:**
> ... I keep well out of it unless she asks for help :D

wise man...;)

---

### Post by Kai69 on 2010-01-31
She is fasinated that I can talk in english switch to german in a conversation.:p

---

### Post by lisati on 2010-01-31
> **Kai69 said:**
> She is fasinated that I can talk in english switch to german in a conversation.:p

The conversation in our house is a mixture of English and Samoan, with a little bit of Maori thrown in for good luck.

---

### Post by warfacegod on 2010-01-31
I speak English and enough of the romance languages to get a beer in half of Europe. My wife speaks fluent Gibberish exclusively.

---

### Post by audiomick on 2010-01-31
> **Kai69 said:**
> She is fasinated that I can talk in english switch to german in a conversation.:p

One time I was at my mum's place (in Australia) with my girlfriend, and said something to her in German. My little brother looked at me and said "oh, I forgot you can do that".

Another time I had a job for an English sound company on a German production. As the only bi-lingual, I was the designated "talking to foreigners" guy. Also in Finland and Portugal.  At one point I was walking around with two walkie-talkies; German in one ear, English in the other, and people talking to me directly at the same time. Does your head in....

---

### Post by Kai69 on 2010-01-31
Your right there I sometimes have to translate at work to euro truckers and the looks I get afterwards :lolflag:

---

### Post by warfacegod on 2010-01-31
I'm usually designated "talking to rednecks" guy.

---

### Post by Kai69 on 2010-01-31
Ive just done something stupid [http://ubuntuforums.org/showthread.php?p=8756387#post8756387:lolflag:](http://ubuntuforums.org/showthread.php?p=8756387#post8756387:lolflag:)
I couldnt help it

---

### Post by Kai69 on 2010-01-31
It said Challenge :lolflag:

---

### Post by lisati on 2010-01-31
> **audiomick said:**
> One time I was at my mum's place (in Australia) with my girlfriend, and said something to her in German. My little brother looked at me and said "oh, I forgot you can do that".

Another time I had a job for an English sound company on a German production. As the only bi-lingual, I was the designated "talking to foreigners" guy. Also in Finland and Portugal.  At one point I was walking around with two walkie-talkies; German in one ear, English in the other, and people talking to me directly at the same time. Does your head in....

I remember my Dad telling one time about a business trip he made to Germany. Seeing that he was from New Zealand the people spoke to him in English, and he didn't let on that having grown up in the Netherlands he could speak some German. I think his hosts figured it out not long after he saw a sign (in German) telling people to put on safety glasses or something of that nature, and he did so automatically.

---

### Post by audiomick on 2010-01-31
> **warfacegod said:**
> I'm usually designated "talking to rednecks" guy.

Redneck: Where's ma beer
Talking to Rednecks guy: You drank it already. Here's a new one.

A German guy once told me a story about being in  a Sauna in England. Two German girls came in and had a long involved conversation about men and who was interesting and what they thought about them, assuming the German guy was English and wouldn't understand them. Until he got up to go and wished them a nice day in German...

---

### Post by warfacegod on 2010-01-31
Announcement: I'm about to do something stupid...in German.

---

### Post by audiomick on 2010-01-31
> **warfacegod said:**
> Announcement: I'm about to do something stupid...in German.

Personally, I have absolute faith in your ability...;)

---

### Post by warfacegod on 2010-01-31
> **audiomick said:**
> Personally, I have absolute faith in your ability...;)

Then teach me some German so I can get it done.

---

### Post by lisati on 2010-01-31
> **warfacegod said:**
> Announcement: I'm about to do something stupid...in German.

[Ankündigung: Ich bin kurz davor, etwas dumm zu machen. ..in Deutsch. ]("http://www.freetranslation.com")

---

### Post by audiomick on 2010-01-31
> **warfacegod said:**
> Then teach me some German so I can get it done.

Find the biggest German you can, preferably a policeman, and say to him

> Du bist wohl das erbärmlichste, das ich je gesehen habe. Ich würde nicht mal auf dich pissen, wenn du brennen würdest.


(see link from lisati)

---

### Post by warfacegod on 2010-02-01
Announcement: I'm about to do something stupid...in Sumerian.

---

### Post by Kai69 on 2010-02-01
Audiomick Dont the german police carry guns anymore, Ill let you tell him first ;)

---

### Post by warfacegod on 2010-02-01
Do Sumerian cops carry guns?

---

### Post by audiomick on 2010-02-01
> **warfacegod said:**
> Do Sumerian cops carry guns?

I think they have those long spear things where the end opens up and an energy beam shoots out. Like the bad guys have on Stargate.

---

### Post by Kai69 on 2010-02-01
Who says germans havent got a sense of humor [http://ubuntuforums.org/showthread.php?p=8757698#post8757698:p](http://ubuntuforums.org/showthread.php?p=8757698#post8757698:p)

---

### Post by Leppie on 2010-02-01
> **warfacegod said:**
> Do Sumerian cops carry guns?
did you find a way to offend them?

---

### Post by warfacegod on 2010-02-01
> **Leppie said:**
> did you find a way to offend them?

Do you doubt my ability to offend *anyone*? Possible all anyones at the same time?

---

### Post by Leppie on 2010-02-01
> **warfacegod said:**
> Do you doubt my ability to offend *anyone*? Possible all anyones at the same time?
no, not really. just was curious what technique you'd use...

---

### Post by Kai69 on 2010-02-01
Im doing something stupid 
Ive just tried to put edubuntu on a usb 4gb , The iso is 3.3gb im useing USB startup disk creator but it wont install gets to 40 odd % error. Ive formatted usb stick FAT <>  HELP 
OR im I being really stupid and should just burn to DVD

---

### Post by warfacegod on 2010-02-02
Redneck multitasking:

Compiling software and cleaning your piled up dishes at the same time.

---

### Post by nothingspecial on 2010-02-02
> **warfacegod said:**
> 

It was either Garth Brooks or Manowar. Either way it would have been evil...pure Eevviillll!

Speaking of Manowar, "The Dawn of Battle" just came on, let me put my laptop back between the speakers.

Some people believe that Manowar are true metal. This is incorrect. Behold the **[COLOR="Red"]TRUEST METAL of STEEL[/COLOR]**


            [[COLOR="Blue"][SIZE="4"]N[/SIZE]ANOWA[SIZE="4"]R[/SIZE][/COLOR]]("http://www.nanowar.it/")

Only true metal of steel would be available for free under the Creative Commons.

---

### Post by nothingspecial on 2010-02-02
> **warfacegod said:**
> Redneck multitasking:

Compiling software and cleaning your piled up dishes at the same time.

That`s what I`m doing, and drinking beer.

---

### Post by Stan_1936 on 2010-02-02
> **warfacegod said:**
> I'm going to resize my sda1 partition. I'm going to install 9.10 NBR as a dual with normal 9.10 on my laptop. Why you ask? Because I feel like it.......

**[COLOR="Red"]"My Linux installs are perfect? There's nothing for me to fix? Sigh. Good grief, I am bored! Let me go screw up my laptop again so I can have something to do"[/COLOR]**.....

**[COLOR="Red"]If only I hadn't done the same thing probably 50+ times since I first learned how to install Ubuntu.  IF ONLY.[/COLOR]**

---

### Post by warfacegod on 2010-02-02
> **Stan_1936 said:**
> **[COLOR="Red"]If only I hadn't done the same thing probably 50+ times since I first learned how to install Ubuntu.  IF ONLY.[/COLOR]**

I like black.

---

### Post by warfacegod on 2010-02-02
> **nothingspecial said:**
> Some people believe that Manowar are true metal. This is incorrect. Behold the **[COLOR="Red"]TRUEST METAL of STEEL[/COLOR]**


            [[COLOR="Blue"][SIZE="4"]N[/SIZE]ANOWA[SIZE="4"]R[/SIZE][/COLOR]]("http://www.nanowar.it/")

Only true metal of steel would be available for free under the Creative Commons.

There must be something wrong with you.

---

### Post by Leppie on 2010-02-02
> **warfacegod said:**
> I like black.
of course you do. red supposedly stands for love, not war...
make war not love!!! :lolflag:

---

### Post by warfacegod on 2010-02-02
> **Leppie said:**
> of course you do. red supposedly stands for love, not war...
make war not love!!! :lolflag:

Then why is the planet Mars red?

---

### Post by Leppie on 2010-02-02
> **warfacegod said:**
> Then why is the planet Mars red?
love overkill?

---

### Post by audiomick on 2010-02-02
> **warfacegod said:**
> Redneck multitasking:

Compiling software and cleaning your piled up dishes at the same time.

I made the mistake of allowing my girlfriend to see that. Now she reckons I could probably manage that too. Damn...

---

### Post by Leppie on 2010-02-02
> **audiomick said:**
> I made the mistake of allowing my girlfriend to see that. Now she reckons I could probably manage that too. Damn...
good thing she didn't read post #417... ;)

---

### Post by warfacegod on 2010-02-02
> **audiomick said:**
> I made the mistake of allowing my girlfriend to see that. Now she reckons I could probably manage that too. Damn...

My evil Redneck plot strikes again! Mwaawuhahhahahahhhahhaaaa!!!!!!



(warfacegod twists the end of his sinister mustache in an insidious fashion)

---

### Post by Kai69 on 2010-02-02
Did something stupid today, Went back to work:lolflag:

---

### Post by warfacegod on 2010-02-02
> **Kai69 said:**
> Did something stupid today, Went back to work:lolflag:

I just wish I had work *to* go back to.

---

### Post by nothingspecial on 2010-02-02
> **warfacegod said:**
> There must be something wrong with you.

Not with me.

You have false metal on your harddrive.

I have true metal of steel,

---

### Post by Kai69 on 2010-02-02
Sorry warfacegod something will come through, Nah did somethinng even more stupid .I had to change a cambelt on an ISUZU truck everything was going well put everything back on all i had left to do was tighten the alternator belts dropped a bolt looked under truck for the bolt found a metal plate,Looked at engine S*** the plate went on the end of the camshaft to stop the belt sliding off the sprocket ](*,).Had to take everything off again to put the plate on .

---

### Post by warfacegod on 2010-02-02
> **Kai69 said:**
> Sorry warfacegod something will come through, Nah did somethinng even more stupid .I had to change a cambelt on an ISUZU truck everything was going well put everything back on all i had left to do was tighten the alternator belts dropped a bolt looked under truck for the bolt found a metal plate,Looked at engine S*** the plate went on the end of the camshaft to stop the belt sliding off the sprocket ](*,).Had to take everything off again to put the plate on .

That makes you a Redneck. I do that all the time. Put everything back together then go: "What's this part?". Toys, vacuums, cars, computers, doesn't matter.

---

### Post by warfacegod on 2010-02-02
> **nothingspecial said:**
> Not with me.

You have false metal on your harddrive.

I have true metal of steel,

Chuck Norris listens to Manowar.



From Merriam-Webster:

Main Entry: heavy metal
Function: noun
Date: 1973

: energetic and highly amplified electronic rock music having a hard beat


Main Entry: false metal
Function: noun
Date: 1973

: lathargic and highly gay amplified electronic rock music having a limp or lame beat, chief useage: Krokus

---

### Post by nothingspecial on 2010-02-02
Vacuums are easy;)

---

### Post by Kai69 on 2010-02-02
Redneck hmmm sounds good do I need to change my wordrobe or habits LOL .This was payback for taking time of work 1st time ive done something like this in ages just felt a bit stupid standing there with an engine back together holding this plate :p
BTW Hows your lappy

---

### Post by nothingspecial on 2010-02-02
And I quote, for non-believers of True Metal Steel

```

NanowaR is the TRUEST metal band in the known universe.
 No heavy true metal band can be as heavy
 true and metal as Nanowar is.
 Even though propaganda states that Nanowar started their activity in 2003,
 many archeologists claim
 to have found undeniable proofs of Nanowar's existence dating back to 2003 B.C.,
 when Ozzy was only three years old.
 Nanowar is the only EPIC - POWER - TRUE METAL 
band who actually killed a dragon.
 That's for real ! 
It happened in the Gargalord Ancient Valley a couple of weeks ago.
 Nanowar had to change their name 
to Nanowar Of Steel - 
obviously not in order to spoof Rhapsody Of Fire, but for REAL and TRUE copyright issues.....................................We're serious !!
```

---

### Post by warfacegod on 2010-02-02
> **nothingspecial said:**
> And I quote, for non-believers of True Metal Steel

```

NanowaR is the TRUEST metal band in the known universe.
 No heavy true metal band can be as heavy
 true and metal as Nanowar is.
 Even though propaganda states that Nanowar started their activity in 2003,
 many archeologists claim
 to have found undeniable proofs of Nanowar's existence dating back to 2003 B.C.,
 when Ozzy was only three years old.
 Nanowar is the only EPIC - POWER - TRUE METAL 
band who actually killed a dragon.
 That's for real ! 
It happened in the Gargalord Ancient Valley a couple of weeks ago.
 Nanowar had to change their name 
to Nanowar Of Steel - 
obviously not in order to spoof Rhapsody Of Fire, but for REAL and TRUE copyright issues.....................................We're serious !!
```

I am of the unknown universe. My word is absolute. So is Chuck Norris'.

---

### Post by audiomick on 2010-02-02
> **Kai69 said:**
> 
I had to change a cambelt on an ISUZU truck everything was going well put everything back on all i had left to do was tighten the alternator belts dropped a bolt looked under truck for the bolt found a metal plate,Looked at engine S*** the plate went on the end of the camshaft to stop the belt sliding off the sprocket ](*,).Had to take everything off again to put the plate on .

Gee, I've _NEVER_ done _ANYTHING_ like that.

The last time I didn't do it was about 2 weeks ago when I took my old Laptop apart to look for why it wasn't starting properly.

At the end, I had three empty screw holes in the bottom of the case, and 3 screws that didn't fit the holes. The laptop works again, though...

---

### Post by warfacegod on 2010-02-02
We need a new theme of degeneracy and idiocy.

---

### Post by Kai69 on 2010-02-02
You start first. LOL

---

### Post by lisati on 2010-02-02
> **nothingspecial said:**
> Vacuums are easy;)

There's nothing of substance to them.

---

### Post by Stan_1936 on 2010-02-02
> **warfacegod said:**
> I like black.

I was sexually aroused at the time when I posted that, which is why I wanted to do something loud.

---

### Post by warfacegod on 2010-02-02
> **lisati said:**
> There's nothing of substance to them.

warfacegod abhors a vacuum.

---

### Post by warfacegod on 2010-02-02
> **Stan_1936 said:**
> I was sexually aroused at the time when I posted that, which is why I wanted to do something loud.

I'm guessing that Ron Jeremy doesn't use Linux. Probably Kleenex though.

---

### Post by Leppie on 2010-02-02
> **warfacegod said:**
> I'm guessing that Ron Jeremy doesn't use Linux. Probably Kleenex though.
what does kleenex have that linux doesn't?

---

### Post by Stan_1936 on 2010-02-02
> **Leppie said:**
> what does kleenex have that linux doesn't?

Guaranteed compatibility with ALL "hardware" that is "thrown" at it.

---

### Post by Leppie on 2010-02-02
> **Stan_1936 said:**
> Guaranteed compatibility with ALL "hardware" that is "thrown" at it.
wow, even better than windows...

---

### Post by warfacegod on 2010-02-02
> **Leppie said:**
> what does kleenex have that linux doesn't?

Absorbency.

---

### Post by Leppie on 2010-02-02
> **warfacegod said:**
> Absorbency.
absorbency? my system absorbs a lot... no liquids though...

---

### Post by audiomick on 2010-02-02
> **Leppie said:**
> what does kleenex have that linux doesn't?

that additive that stops your nose from going red when you have to use them too often.

---

### Post by Leppie on 2010-02-02
> **audiomick said:**
> that additive that stops your nose from going red when you have to use them too often.
i never try to wipe my nose with my linux box... you're a funny guy... :P

---

### Post by warfacegod on 2010-02-02
> **Leppie said:**
> absorbency? my system absorbs a lot... no liquids though...

My laptop has survived a glass of milk from my kids and a cup of hot coffee from me. I guess it's pretty absorbent after all.

---

### Post by audiomick on 2010-02-02
> **warfacegod said:**
> My laptop has survived a glass of milk from my kids and a cup of hot coffee from me. I guess it's pretty absorbent after all.

Is that the one that broke down recently?

---

### Post by warfacegod on 2010-02-02
> **audiomick said:**
> Is that the one that broke down recently?

One and the same.

---

### Post by Leppie on 2010-02-03
> **warfacegod said:**
> One and the same.
no wonder cdrom drive broke down...

---

### Post by 73ckn797 on 2010-02-03
> **Leppie said:**
> what does kleenex have that linux doesn't?
It may be only tissue but its snot.

---

### Post by Leppie on 2010-02-03
> **73ckn797 said:**
> It may be only tissue but its snot.
no hard bits??? :(

---

### Post by theDaveTheRave on 2010-02-03
> **Leppie said:**
> how much can microsoft be paying them???

In fact it is the opposite.

Each manufacturer / OEM is pre-paid for each machine produced.

They don't "have" to install windows onto any of their systems, but as they are paying microsoft for the OS in bulk, and MS then says - "you have to install this on the machine before it is sold" they are a bit cought.

Seems like its is the wrong way around to me.

But try explaining it to people.... ](*,)


David

---

### Post by warfacegod on 2010-02-03
> **theDaveTheRave said:**
> In fact it is the opposite.

Each manufacturer / OEM is pre-paid for each machine produced.

They don't "have" to install windows onto any of their systems, but as they are paying microsoft for the OS in bulk, and MS then says - "you have to install this on the machine before it is sold" they are a bit cought.

Seems like its is the wrong way around to me.

But try explaining it to people.... ](*,)


David

I'm pretty sure that is only one of hundreds of business practices that got them sued and brought before Congress in the U.S. As far as I can tell, in spite of Congressional order, thay have not altered their agenda one bit.

---

### Post by Leppie on 2010-02-03
> **theDaveTheRave said:**
> In fact it is the opposite.

Each manufacturer / OEM is pre-paid for each machine produced.

They don't "have" to install windows onto any of their systems, but as they are paying microsoft for the OS in bulk, and MS then says - "you have to install this on the machine before it is sold" they are a bit cought.
what you're saying here is a bit contradictive...

---

### Post by audiomick on 2010-02-03
> **Leppie said:**
> what you're saying here is a bit contradictive...

I think this
> Each manufacturer / OEM is pre-paid for each machine produced.
should read "each manufacturer **has** pre-paid..."
Then it would make sense.

---

### Post by Leppie on 2010-02-03
> **audiomick said:**
> I think this

should read "each manufacturer **has** pre-paid..."
Then it would make sense.
yeah, makes more sense like that...

you imitating wfg?

---

### Post by warfacegod on 2010-02-03
It was my suggestion.

---

### Post by warfacegod on 2010-02-03
My new evil experiment:

---

### Post by texaswriter on 2010-02-03
> **warfacegod said:**
> I'm going to resize my sda1 partition. I'm going to install 9.10 NBR as a dual with normal 9.10 on my laptop. Why you ask? Because I feel like it.
Can any one give me a decent partition size for NBR?


You see? This is what happens when you start computing with Windows. I start going:

"My Linux installs are perfect? There's nothing for me to fix? Sigh. Good grief, I am bored! Let me go screw up my laptop again so I can have something to do"

And that's after three years of being Windows free. Ubuntu: The Windows 12 Step Program


ROFLMAO, what ever happened to: if it works, dont' fix it... 

oh well, have fun!

IGNORE THIS: didnt realize there were 13 pages already when i posted: > BTW, dual booting, starting from a clean hard drive, I created 2 partitions with Window, installed WIndows on one, and then windows made another 1 or 2 tiny partitions [don't wrry about those]. Then with Ubuntu CD, manually configured partitions to have root boot up in the blank partition. 

Manuallyl setting the partitions is the only way I know of ensuring the automatic settings don't overwrite your Windows partition [which I have done before .... automatic settings with Debian livecd].

---

### Post by warfacegod on 2010-02-03
13? There's already 37! pages of idiocy here. I don't see the madness stopping any time soon.

---

### Post by texaswriter on 2010-02-03
rofl, yeah I forgot i have more threads per page... 13 of my pages = 37 of ur pages... ;)

---

### Post by warfacegod on 2010-02-03
> **texaswriter said:**
> rofl, yeah I forgot i have more threads per page... 13 of my pages = 37 of ur pages... ;)

I'd forgotten about changing the number of posts per page.

---

### Post by warfacegod on 2010-02-03
Okay, new idea.

I hereby decree, through my divine right to decree stuff, that all people on Earth, with failing or broken Windows installs (which means anybody that ever turned Windows on), shall mail their computers to Microsoft and demand a replacement.

---

### Post by audiomick on 2010-02-03
> **warfacegod said:**
> ...shall mail their computers to Microsoft and demand a replacement.
C.O.D., of course....

---

### Post by warfacegod on 2010-02-03
> **audiomick said:**
> C.O.D., of course....

And give my government an excuse to spend billions on more bailout money. For Microsoft this time. That would make Obama defacto C.E.O. of Microsoft, just like GM.

---

### Post by Leppie on 2010-02-04
> **warfacegod said:**
> It was my suggestion.
haha, ok... it's a nice drawing anyways :)

---

### Post by Leppie on 2010-02-04
> **warfacegod said:**
> My new evil experiment:
so what is it?
bombard everyone with gibberish on milk cartons? i believe they're already doing that... :P

---

### Post by audiomick on 2010-02-04
> **Leppie said:**
> ... gibberish on milk cartons? i believe they're already doing that... :P
I always thought that was "valuable consumer information". That's what they claim, anyway....;)

---

### Post by Leppie on 2010-02-04
> **audiomick said:**
> I always thought that was "valuable consumer information". That's what they claim, anyway....;)
well, microsoft also says to "obtain" a legal copy of windows or any other ms product. but when you read their eula, you're soon to discover that you did not buy a copy but the right to use a copy...

---

### Post by warfacegod on 2010-02-04
> **Leppie said:**
> well, microsoft also says to "obtain" a legal copy of windows or any other ms product. but when you read their eula, you're soon to discover that you did not buy a copy but the right to use a copy...

You actually read one?  I just automatically assumed that it places all responsibility on the user and places all the rights aand ownship on MS.

---

### Post by forrestcupp on 2010-02-04
> **warfacegod said:**
> You actually read one?  I just automatically assumed that it places all responsibility on the user and places all the rights aand ownship on MS.
"We have the right to repeatedly bludgeon you with a spiked club, and if you choose to use our software, you automatically waive your right to do anything about it.  You promise to lie there and take it in exchange for the right to happily use *our* software."
:)

---

### Post by audiomick on 2010-02-04
> **forrestcupp said:**
> "....the right to happily use *our* software."
:)
So I have the right to be happy about using their software, but no-one is claiming I will be happy about it? That explains that then! And here was me thinking I was getting depressive or something....

---

### Post by Leppie on 2010-02-04
> **warfacegod said:**
> You actually read one?  I just automatically assumed that it places all responsibility on the user and places all the rights aand ownship on MS.
well, that is a well known fact now... was a bit different in the early days...

---

### Post by Leppie on 2010-02-04
> **audiomick said:**
> So I have the right to be happy about using their software, but no-one is claiming I will be happy about it? That explains that then! And here was me thinking I was getting depressive or something....
they do claim that... but only ***before*** the sale...

---

### Post by warfacegod on 2010-02-04
The only thing that makes me happy about using Windows is breaking it. I think I mentioned it before but I'll say it again; I've grown a fondness for going into the store and "trying out" the demo computers and breaking the Windows installs on them.

---

### Post by Stan_1936 on 2010-02-04
> **warfacegod said:**
> ...**I've grown a fondness for** going into the store and "trying out" the demo computers and **breaking the Windows installs on them**.

**How exactly do you do this?**

---

### Post by warfacegod on 2010-02-04
> **Stan_1936 said:**
> **How exactly do you do this?**

Depends on if there's clerk around.

---

### Post by Stan_1936 on 2010-02-04
^^Hehe, nice way to sidestep the question which was really asking for details/steps involved in the process....almost a step-by-step Windows breakage instruction manual, if you will.

---

### Post by warfacegod on 2010-02-04
> **Stan_1936 said:**
> ^^Hehe, nice way to sidestep the question which was really asking for details/steps involved in the process....almost a step-by-step Windows breakage instruction manual, if you will.

I'm most familiar with XP so I'll start there. Remove notepad that's pretty much all it takes.

The brute force technique always works best. Go into any of the OS folders and just get trigger happy. That applies to any OS really. Some times just giving it a stern look works too.

---

### Post by Leppie on 2010-02-04
> **warfacegod said:**
> I'm most familiar with XP so I'll start there. Remove notepad that's pretty much all it takes.

The brute force technique always works best. Go into any of the OS folders and just get trigger happy. That applies to any OS really. Some times just giving it a stern look works too.
they don't password protect the machines on display?

---

### Post by warfacegod on 2010-02-04
> **Leppie said:**
> they don't password protect the machines on display?

Most do but not all. Sometimes the password is just the name of the store.

---

### Post by Leppie on 2010-02-04
> **warfacegod said:**
> Most do but not all. Sometimes the password is just the name of the store.
oh yeah, like using 123456, or abcdef, etc.

---

### Post by lisati on 2010-02-04
Darn! My laptop came with a screen saver installed by the shop (it was a demo machine, the screen saver was of the kind that advertises the shops services). Perhaps I was too hasty reinstalling Vista from the recovery partition when I got it home.

---

### Post by Leppie on 2010-02-04
why? did you want to hack your own pc?:lolflag:

---

### Post by warfacegod on 2010-02-04
> **Leppie said:**
> why? did you want to hack your own pc?:lolflag:

If so, I recommend a medium sized hatchet.

---

### Post by Leppie on 2010-02-04
a large chopping knife will do nicely as well ;)

---

### Post by warfacegod on 2010-02-04
Go for the gusto, get out the Sawzall!

---

### Post by audiomick on 2010-02-04
> **warfacegod said:**
> Go for the gusto, get out the Sawzall!
I'm fond of a gas welding torch myself...

---

### Post by Leppie on 2010-02-04
> **audiomick said:**
> I'm fond of a gas welding torch myself...
thermite is still my favorite ;)

---

### Post by warfacegod on 2010-02-04
Take the magnet off of a 12" speaker cone and...well, need I say more?

---

### Post by Leppie on 2010-02-04
> **warfacegod said:**
> Take the magnet off of a 12" speaker cone and...well, need I say more?
just place it on you subwoofer... :P

---

### Post by audiomick on 2010-02-04
There was a warning in the papers here about 10 years ago. A particular type of train had a handy little fold down tablet built in to the back of the seat in front, like in planes. Except the one on the trains was held in place with a magnet in the fold down bit. Guess what was happening...

---

### Post by Leppie on 2010-02-04
they received some nice claims?

---

### Post by audiomick on 2010-02-04
> **Leppie said:**
> they received some nice claims?
Don't know, but all of a sudden there where warning stickers all over the place.

---

### Post by Leppie on 2010-02-04
> **audiomick said:**
> Don't know, but all of a sudden there where warning stickers all over the place.
hehehe... they should've left the surprise for the travellers... :P

---

### Post by warfacegod on 2010-02-04
Planes, Trains, and Automobiles. All excellent forms of computer genocide.

---

### Post by warfacegod on 2010-02-04
Oh, and Windows too.

---

### Post by Leppie on 2010-02-04
> **warfacegod said:**
> Oh, and Windows too.
especially windoze...

---

### Post by warfacegod on 2010-02-04
Saw you guys over in the lostthewilltolivethread.

I almost posted: I suggest 1-800-SUICIDE


But I didn't have the heart.

---

### Post by audiomick on 2010-02-04
> **warfacegod said:**
> Saw you guys over in the lostthewilltolivethread.

I almost posted: I suggest 1-800-SUICIDE


But I didn't have the heart.
Yes, I think the guy is feeling bad enough already...;)

---

### Post by warfacegod on 2010-02-04
If it were mine, I would just go for fresh installs. (It would never happen on my system though.)

---

### Post by Leppie on 2010-02-04
the problem is that a lot of people try too many things first before asking help...
maybe they're too confident? or maybe they feel to stupid?

---

### Post by warfacegod on 2010-02-04
I usually think of stupidity (in part) as not knowing or caring when you can't do something without help.

---

### Post by Leppie on 2010-02-04
> **warfacegod said:**
> I usually think of stupidity (in part) as not knowing or caring when you can't do something without help.
so, over-confidence really comes down to plain stupidity? sounds quite right actually...

---

### Post by warfacegod on 2010-02-04
Indeed. I suggest we send them packages of explosive cheese.

---

### Post by Leppie on 2010-02-04
that'll teach em... put some thermite in as well... ;)

---

### Post by warfacegod on 2010-02-04
And we'd be forwarding the goal of Global Elimination Of Room Temperature IQ.

---

### Post by warfacegod on 2010-02-04
Curses! I have inadvertently revealed part of my not so secret plan for world domination! Drat the luck!

---

### Post by Leppie on 2010-02-04
> **warfacegod said:**
> And we'd be forwarding the goal of Global Elimination Of Room Temperature IQ.
but still a long way to go... :(

---

### Post by warfacegod on 2010-02-04
If we set off a Hydrgen Bomb that would raise the room temperature....

---

### Post by witeshark17 on 2010-02-04
> **warfacegod said:**
> Curses! I have inadvertently revealed part of my not so secret plan for world domination! Drat the luck! Quick! Maybe you can make it a diversion for a new plan! ;)

---

### Post by Thomas Garman on 2010-02-04
I have installed uninstalled reinstalled so many times just to try out different ideas, which is not something you can really do with Windows.
 
If you want a real adventure...  I would suggest buying a tv usb stick, like for example the Pinnacle PCTV HD Pro stick or something, and try to get ANY version of Linux to actually work to show television on your computer with it.
 
Anyway, that's what I am doing for fun.  I have also started learning to program with Ruby just so I have something more substantial to do with the terminal than sudo apt-get...
 
Another fun project is getting a second monitor and then trying to get two independently working cubes to spin in each monitor.

---

### Post by warfacegod on 2010-02-05
> **Thomas Garman said:**
> I have installed uninstalled reinstalled so many times just to try out different ideas, which is not something you can really do with Windows.
 
If you want a real adventure...  I would suggest buying a tv usb stick, like for example the Pinnacle PCTV HD Pro stick or something, and try to get ANY version of Linux to actually work to show television on your computer with it.
 
Anyway, that's what I am doing for fun.  I have also started learning to program with Ruby just so I have something more substantial to do with the terminal than sudo apt-get...
 
Another fun project is getting a second monitor and then trying to get two independently working cubes to spin in each monitor.

My TV doesn't like my laptop as it is. It works but only just so.

There is no way my graphics card will handle two cubes. nVidia Geforce Go5200 64 MB. Thanks for the idea though, I'm going to try that on my next system.

---

### Post by warfacegod on 2010-02-05
> **witeshark17 said:**
> Quick! Maybe you can make it a diversion for a new plan! ;)

Yes! Plots within schemes within plans.....

....Step #256, brainwash whiteshark.....

---

### Post by Leppie on 2010-02-05
> **warfacegod said:**
> If we set off a Hydrgen Bomb that would raise the room temperature....
thermite would raise the room temperature as welll :P

---

### Post by audiomick on 2010-02-05
> **warfacegod said:**
> I usually think of stupidity (in part) as not knowing or caring when you can't do something without help.
I read somewhere of the type of confidence that is caused by being too stupid to realize you might fail.
That would explain the apparent IQ of some of the world's "successful" people...

---

### Post by Leppie on 2010-02-05
> **audiomick said:**
> I read somewhere of the type of confidence that is caused by being too stupid to realize you might fail.
That would explain the apparent IQ of some of the world's "successful" people...
some of them??? i'd go with most of them...
some of them are different, they actually are intelligent. but that's only few fo them...

---

### Post by warfacegod on 2010-02-05
They are successfully stupid.

---

### Post by audiomick on 2010-02-05
> **warfacegod said:**
> They are successfully stupid.
very good...:p

---

### Post by Leppie on 2010-02-05
> **audiomick said:**
> very good...:p
it's really very bad and sad...

---

### Post by audiomick on 2010-02-05
> **Leppie said:**
> it's really very bad and sad...
well yes, given that there is an amount of truth in it.

---

### Post by warfacegod on 2010-02-05
Playing Devil's Advocate here. If there were no stupid people, wouldn't that just make the rest of us average, therefor stupid?

---

### Post by Leppie on 2010-02-05
> **warfacegod said:**
> Playing Devil's Advocate here. If there were no stupid people, wouldn't that just make the rest of us average, therefor stupid?
if there were no stupid people, we would all be stupid and intelligent at the same time... so yes, average... but that might still be a better solution...

---

### Post by willowave on 2010-02-05
so this is where the party is at huh?

---

### Post by willowave on 2010-02-05
I'm sure you will be elated to know my wireless quit working again on ubuntu. Tho all I had to do was restart to get it going again I see issues in my future...

---

### Post by warfacegod on 2010-02-05
> **willowave said:**
> so this is where the party is at huh?

Yeah! You like my thread?

---

### Post by warfacegod on 2010-02-05
MURPHY'S LAWS OF COMBAT




1.You are not a superman.
2.If it's stupid but works, it isn't stupid.
3.Don't look conspicuous - it draws fire.
4.When in doubt, empty your magazine.
5.Never share a foxhole with anyone braver than you are.
6.Never forget that your weapon was made by the lowest bidder.
7.If your attack is going well, it's an ambush.
8.No plan survives the first contact intact.
9.All five-second grenade fuses are three-seconds long.
10.Try to look unimportant because the enemy may be low on ammo.
11.If you are forward of your position, artillery will fall short.
12.The enemy diversion you are ignoring is the main attack.
13.The important things are always simple.
14.The simple things are always hard.
15.The easy way is always mined.
16.If you are short of everything except enemy, you are in combat.
17.When you have secured an area,  don't forget to tell the enemy.
18.Incoming fire has the right of way.
19.Friendly fire--isn't.
20.If the enemy is in range, "SO ARE YOU"!!!!!
21.No combat ready unit ever passed inspection.
22.Beer count math is: two beers times 37 men =49 cases.
23.Body count math is: two guerrillas plus three chickens plus two pigs= 37 enemy killed.
24.Things that must be together to work, usually can't be shipped together.
25.Radio's will fail as soon as you need fire support desperately.
26.Anything you do can get you shot-- including doing nothing.
27.Tracers work both ways.
28.The only thing more accurate than incoming enemy fire is incoming friendly fire.
29.Make it tough for the enemy to get in and you can't get out.
30.If you take more than your fair share of objectives you will have more than your fair share of objectives to take.
31.When both sides are convinced that they are about to lose, they are both right.
32.Professional soldiers are predictable but the world is full of amateurs.
33.Murphy was a grunt.

---

### Post by willowave on 2010-02-05
lol interesting. and useful!!
Yeah actually before I replied to your other thread...you know the one I hijacked...
I read this. Thats why I figured you might be up for helping me out. lol

---

### Post by warfacegod on 2010-02-05
MURPHY'S REVISED LAWS OF LINUX COMBAT




1.You are not Linus. Linus isn't Linus
2.If it's stupid but works, it's still stupid but at least it worked.
3.Don't look conspicuous &#8211; Microsoft will shoot you.
4.When in doubt, wipe your hard drive.
5.Never share a computer with your wife.
6.Never forget that your components were made by the lowest bidder. Unless you made them. In that case, you have spent way too much time in your parents basement.
7.If your operation is going well, it will crash.
8.No OS survives the first user intact.
9.All five-second USB transfers are thirty minutes long.
10.Try to look unimportant because Microsoft may be low on ammo.
11.If you are forward of your cd / position, tarballs will fall short.
12.The error message you are ignoring is the main attack.
13.The important things are always simple. Which means really, really hard.
14.The simple things are always hard. Which means really, really impossible.
15.The easy way is always some guru jerk off telling you it's easy and posting 30 obscure and mystical commands in geekspeak that make you wish you'd stepped on a mine.
16.If you are short of everything especially patience, you are in Linux.
17.When you have installed Linux,  don't forget to not tell the computer manufacturer. They'll behave as though you've had their only begotten child beheaded.
18.Incoming infractions have the right of way.
19.Friendly users--aren't.
20.If Microsoft is in range, "SO ARE YOU"!!!!!
21.No boot ready machine ever got past GRUB.
22.Beer count math is: two beers times 37 men =49 cases. Beer math needs no revision.
23.Body count math is: two unistalled apps plus three updates plus two zombies= 37 broken packages.
24.Things that must be together to work, usually can't be .debed together.
25.Wifi will fail as soon as you need Linux support desperately.
26.Anything you do can crash your system-- including doing nothing.
27.Flames work both ways.
28.The only thing more accurate than incoming bad commands is incoming friendly commands.
29.Make it tough to get into an app or file then hitting escape won't always get you out.
30.If you take more than your fair share of operations your CPU will have more than its fair share of operations to do. Then your system will crash.
31.When both OS and application are convinced that they are about to crash, they are both right.
32.Professional hackers are predictable but the world is full of amateurs.
33.Murphy was a noob.

---

### Post by Kai69 on 2010-02-05
Hi warface I was actually thinking about putting W7 on lappy again ](*,)I dont know why, Help

---

### Post by warfacegod on 2010-02-05
Call 1-800-SUICIDE

---

### Post by willowave on 2010-02-05
You have a typo in #29. Otherwise I agree completely. :D

---

### Post by Kai69 on 2010-02-05
Nah Im not that desperate, went to a computer store yesterday saw all the lappys (broke one deleted i386 folder) Brought a grafics tablet and then installed it on kids lappy,still had to go to wacoms website to get the drivers so more work,installed tablet on my lappy it sort of works, Its just that to only people I know that uses linux is on this forum everywhere I look its all windows???

---

### Post by Leppie on 2010-02-05
you would think that with all those windows there would be some transparency... but alas...

---

### Post by Kai69 on 2010-02-05
I know no one understands linux ive even tried to get a friend to use Gimp instead he just got a pirate copy of photoshop go figure :roll:

---

### Post by Leppie on 2010-02-05
well, to be honest gimp doesn't do everything photoshop does... but that's why we've got virtual windows ;)

---

### Post by Kai69 on 2010-02-05
But why use a pirate copy instead of looking for an oss version

---

### Post by warfacegod on 2010-02-05
> **willowave said:**
> You have a typo in #29. Otherwise I agree completely. :D

Leave it to a woman to correct my spelling.

---

### Post by warfacegod on 2010-02-05
> **Leppie said:**
> you would think that with all those windows there would be some transparency... but alas...

Vista has the Aero interface...at the cost of 1.5 GB RAM.

---

### Post by warfacegod on 2010-02-05
> **Leppie said:**
> well, to be honest gimp doesn't do everything photoshop does... but that's why we've got virtual windows ;)

I believe Spiderman 1, 2, & 3, LOTR 1, 2, & 3 and many others were done with GIMP not PS.

---

### Post by Kai69 on 2010-02-05
How much Ram does compiz use ?

---

### Post by warfacegod on 2010-02-05
> **Kai69 said:**
> How much Ram does compiz use ?

I'm at the moment I'm using about 360 MB total and Compiz gets about 140 MB of it.

---

### Post by audiomick on 2010-02-05
> **Kai69 said:**
> ...everywhere I look its all windows???
Start throwing stones??

---

### Post by Kai69 on 2010-02-05
You could run another os with the ram left over from 1.5GB
Im thinking about throwing Bricks

---

### Post by audiomick on 2010-02-05
> **Kai69 said:**
> How much Ram does compiz use ?
My Compiz is using about 140kiB, that would be kiloBytes I imagine, according to the system resources thing. There is also something called compiz.real that is using 37.2MiB.

---

### Post by warfacegod on 2010-02-05
> **audiomick said:**
> My Compiz is using about 140kiB, that would be kiloBytes I imagine, according to the system resources thing. There is also something called compiz.real that is using 37.2MiB.

If Compiz is at 140 K then I'm betting that you are using normal effect at most, almost certainly none.

---

### Post by audiomick on 2010-02-05
I have selected the "extra" button on the "visual effects" tab in the appearance thing.
It does the wobbly windows thing when I move a window, but to be quite honest I don't know how much is really working, and how much not.

---

### Post by Leppie on 2010-02-05
> **audiomick said:**
> My Compiz is using about 140kiB, that would be kiloBytes I imagine, according to the system resources thing. There is also something called compiz.real that is using 37.2MiB.
Compiz i think refers to a launcher, compiz itself is the compiz.real process.

---

### Post by warfacegod on 2010-02-05
> **Leppie said:**
> Compiz i think refers to a launcher, compiz itself is the compiz.real process.

You're right. My System Mon. says 97 K not M. So that means my Compiz really only uses about 45 or 50 MB.

Actually 1.5 GB is an over statement. My uncles desktop idles at about 1.5 GB RAM. I watched him turn off the Aero interface and him RAM dropped to about 450 MB. Last week, he did an upgrade install to 7 without backups of any kind. I'll ask him about his RAM use tomorrow.

---

### Post by Leppie on 2010-02-05
> **warfacegod said:**
> Last week, he did an upgrade install to 7 without backups of any kind.
how is switching to 7 an upgrade?

---

### Post by Kai69 on 2010-02-05
Why not use linux

---

### Post by Leppie on 2010-02-05
i thought his whole family was using linux...

---

### Post by Kai69 on 2010-02-05
Desserter in the ranks??;)

---

### Post by Leppie on 2010-02-05
looks like it...

---

### Post by warfacegod on 2010-02-05
> **Leppie said:**
> how is switching to 7 an upgrade?

Windows upgrade installs are possible just like Ubuntu.

---

### Post by warfacegod on 2010-02-05
> **Leppie said:**
> i thought his whole family was using linux...

My immediate family. My mother. My uncle dabbles with a 9.04 disc I gave him last spring.

---

### Post by Leppie on 2010-02-06
just installed it when he's not looking :P

---

### Post by warfacegod on 2010-02-06
> **Leppie said:**
> just installed it when he's not looking :P

Actually, the ethernet and wireless just broke on his XP netbook. I'm going to try to talk him into taking a look at UNR.

---

### Post by Leppie on 2010-02-06
> **warfacegod said:**
> Actually, the ethernet and wireless just broke on his XP netbook. I'm going to try to talk him into taking a look at UNR.
just tell him the fix is called ubuntu ;)

---

### Post by warfacegod on 2010-02-06
I must be losing my touch. I post what I thought was, at least, mildly amusing and all I get is a post correcting my spelling.

---

### Post by 73ckn797 on 2010-02-06
> **warfacegod said:**
> I must be losing my touch. I post what I thought was, at least, mildly amusing and all I get is a post correcting my spelling.
Insert dictionary and reboot.

OR

Computer does not recognize redneck.

---

### Post by warfacegod on 2010-02-06
> **73ckn797 said:**
> Insert dictionary and reboot.

OR

Computer does not recognize redneck.

What does that have to do with post #432/434?:confused:

How you been by the way? How's the Les Paul Electric Banjo doing?

---

### Post by 73ckn797 on 2010-02-06
> **warfacegod said:**
> What does that have to do with post #432/434?:confused:

How you been by the way? How's the Les Paul Electric Banjo doing?
It was a comment on being corrected in your spelling:p

There is a Les Paul Banjo? I have the latest Musicians Friend catalog in front of me but do not see one.

I have the Gibson Blues Hawk. (see avatar)

Been doing fine.

---

### Post by Kai69 on 2010-02-06
> Actually, the ethernet and wireless just broke on his XP netbook. I'm going to try to talk him into taking a look at UNR.


How long does it take for a windows install to break?

---

### Post by Leppie on 2010-02-06
> **Kai69 said:**
> How long does it take for a windows install to break?
they come broken by default... :P

---

### Post by 73ckn797 on 2010-02-06
> **Kai69 said:**
> How long does it take for a windows install to break?
Depends upon how much it gets used when it is new.:)

---

### Post by warfacegod on 2010-02-06
I can break a Windows XP in under one minute, after boot.

---

### Post by Kai69 on 2010-02-06
I suppose what im asking is if everything is installed and running ok then what makes it break, Is it fragmented files ,MS updates or something else Im asking because Vista has started to play up again. I had to do a full install after sp2 came out because it broke my internet ,so since install everything has been running ok but I wont install sp2 update, over the last few days weve been loseing internet again,, I havent used Vista since august last year my lappy had XP on it that only lasted until November when XP broke and not through viruses either but taking 15 mins to boot or shut down W7 so far on kids lappy had 1 virus, soon sorted but so far seems stable even with updates.

---

### Post by warfacegod on 2010-02-06
Over time, HDD fragmenting, Registry fragmenting, ever growing temp folder (which happens regardless of actually using I.E.), growing list of startup programs, and simply *turning it on* can lead to a broken system. Among many other factors.

---

### Post by Woolio1 on 2010-02-06
Heh, I've been bored so many times, I've come up for an excellent way to screw up a system.

Partition 1gb of hard drive space, and install Windows on it.

Erase the Ubuntu partition(Not uninstall, simply erase the partition), and allocate it to Windows. 

This kills GRUB, because you're missing one of it's partitions. And then you have to take an Ubuntu boot disk and reinstall the entire operating system.

Have fun!:)

(I've dabbled in Ubuntu for quite some time... I put it on my desktop, and tried to remove it... Discovered the method above. I mainly use Windows 7 (Laugh if you will) at home, because I'm a gamer. Recently purchased a machine just for Ubuntu, a netbook. And so far, I've not been bored at all. The filesystem tends to break pretty often, though. -.-)

---

### Post by warfacegod on 2010-02-06
> **Woolio1 said:**
> Heh, I've been bored so many times, I've come up for an excellent way to screw up a system.

Partition 1gb of hard drive space, and install Windows on it.

Erase the Ubuntu partition(Not uninstall, simply erase the partition), and allocate it to Windows. 

This kills GRUB, because you're missing one of it's partitions. And then you have to take an Ubuntu boot disk and reinstall the entire operating system.

Have fun!:)

(I've dabbled in Ubuntu for quite some time... I put it on my desktop, and tried to remove it... Discovered the method above. I mainly use Windows 7 (Laugh if you will) at home, because I'm a gamer. Recently purchased a machine just for Ubuntu, a netbook. And so far, I've not been bored at all. The filesystem tends to break pretty often, though. -.-)

What filesystem are you using? The ext's tend to be pretty stable.

---

### Post by Leppie on 2010-02-06
> **Woolio1 said:**
> Partition 1gb of hard drive space, and install Windows on it.

Erase the Ubuntu partition(Not uninstall, simply erase the partition), and allocate it to Windows. 

This kills GRUB, because you're missing one of it's partitions. And then you have to take an Ubuntu boot disk and reinstall the entire operating system.
you can have windows booting off a system like this in less than half an hour and that's only if you have to download and burn some image to restore the mbr. if you already have an image, restoring the mbr can be done in less than 5 minutes (time for booting off a cd included).

---

### Post by Kai69 on 2010-02-06
> **warfacegod said:**
> Over time, HDD fragmenting, Registry fragmenting, ever growing temp folder (which happens regardless of actually using I.E.), growing list of startup programs, and simply *turning it on* can lead to a broken system. Among many other factors.

I suppose the best thing to do is reinstall the whole os:frown:

---

### Post by warfacegod on 2010-02-06
> **Kai69 said:**
> I suppose the best thing to do is reinstall the whole os:frown:

I'll give you a list of things to use to help fix it up good as new. After I watch Stargate SG1.

---

### Post by Kai69 on 2010-02-06
> **warfacegod said:**
> I'll give you a list of things to use to help fix it up good as new. After I watch Stargate SG1.

Thanks I really dont want to do a reinstall :p

---

### Post by Woolio1 on 2010-02-06
> **warfacegod said:**
> What filesystem are you using? The ext's tend to be pretty stable.

Honestly, I have no idea what filesystem I'm using. And what's an ext? 

Like I said, I've screwed over more Linux installations because I have no idea what I'm doing. Compared to Ubuntu, my Windows 7 64-bit ultimate is stable as a rock. 

Maybe I should take some time to learn why things keep breaking.

---

### Post by Leppie on 2010-02-06
> **Kai69 said:**
> I suppose what im asking is if everything is installed and running ok then what makes it break, Is it fragmented files ,MS updates or something else Im asking because Vista has started to play up again. I had to do a full install after sp2 came out because it broke my internet ,so since install everything has been running ok but I wont install sp2 update, over the last few days weve been loseing internet again,, I havent used Vista since august last year my lappy had XP on it that only lasted until November when XP broke and not through viruses either but taking 15 mins to boot or shut down W7 so far on kids lappy had 1 virus, soon sorted but so far seems stable even with updates.
i still prefer xp to vista and 7...
you can use apps like Glary Utilities to clean up your registry. it can remove empty keys etc.but it would be best to export your registry every now and then.

---

### Post by Leppie on 2010-02-06
> **Woolio1 said:**
> Like I said, I've screwed over more Linux installations because I have no idea what I'm doing. Compared to Ubuntu, my Windows 7 64-bit ultimate is stable as a rock.
it's easy to say that a system is stable as a rock if you know exactly what you should not do (or know more or less what you should do). it's a bit strange to say that ubuntu isn't stable. it's like giving a little kid a machine gun and then say that the kid has psychological issues if he guns people down.

> **Woolio1 said:**
> Maybe I should take some time to learn why things keep breaking.
yes, that would be a good start. i think that you didn't learn how to use windows in a couple of minutes and without reading anything either...

---

### Post by Woolio1 on 2010-02-06
> **Leppie said:**
> it's easy to say that a system is stable as a rock if you know exactly what you should not do (or know more or less what you should do). it's a bit strange to say that ubuntu isn't stable. it's like giving a little kid a machine gun and then say that the kid has psychological issues if he guns people down. 

That's... A very funny comparison. However, I've had clean installs fail on me, and fail to mount the filesystem even before I installed anything. Any ideas what's going on there?


> **Leppie said:**
> yes, that would be a good start. i think that you didn't learn how to use windows in a couple of minutes and without reading anything either... 

I've used Windows all my life. I know it like the back of my hand, and I've been able to know just what to do when a problem comes up. It seems that my Ubuntu installations follow the law of "It doesn't break often, but when it does, it fails catastrophically."

---

### Post by Kai69 on 2010-02-06
> **Leppie said:**
> i still prefer xp to vista and 7...
you can use apps like Glary Utilities to clean up your registry. it can remove empty keys etc.but it would be best to export your registry every now and then.

I know what you mean I was stupid not to find out how to make system restore disks when I got the lappy Dell xps m1330 it should have had Vista on but I asked my dad if the shop can put on XP They put on XP pro sp3 which worked ok until it broke so ive used vista on this hated it then tried W7 what a differance Hi Def movies and sound only problem pirate copy so I went with ubuntu

---

### Post by Leppie on 2010-02-06
> **Woolio1 said:**
> That's... A very funny comparison. However, I've had clean installs fail on me, and fail to mount the filesystem even before I installed anything. Any ideas what's going on there?
did you check for errors after downloading and burning? it's always best to check before installing.
anyways, start your thread and give us the link so we can have a look.

> **Woolio1 said:**
> It seems that my Ubuntu installations follow the law of "It doesn't break often, but when it does, it fails catastrophically."
ubuntu gives you the power to control most of the system (instead of the system controlling what you can do with it). so if something goes wrong, it may seem difficult to repair at start, but most things actually can be repaired. most first time users do not have enough knowledge to break the system badly enough to have to re-install it. it's different if some experienced user provides some nasty code which breaks the system.
i would say that in general windows systems are more difficult to repair.

---

### Post by Leppie on 2010-02-06
> **Kai69 said:**
> I know what you mean I was stupid not to find out how to make system restore disks when I got the lappy Dell xps m1330 it should have had Vista on but I asked my dad if the shop can put on XP They put on XP pro sp3 which worked ok until it broke so ive used vista on this hated it then tried W7 what a differance Hi Def movies and sound only problem pirate copy so I went with ubuntu
i'm not sure which one was worse, millenium or vista...

---

### Post by warfacegod on 2010-02-06
> anyways, start your thread and give us the link so we can have a look.

Agreed. This thread is for the promotion of congenital psychosis not therapy for it.

PM the link.

---

### Post by Kai69 on 2010-02-06
Warfacegod have you been reading the dictionary ?;)

---

### Post by warfacegod on 2010-02-06
> **Kai69 said:**
> Warfacegod have you been reading the dictionary ?;)

No.


(And that's a lower case w, even at the beginning of a sentence, look it up in the dictionary.)

---

### Post by Leppie on 2010-02-06
> **warfacegod said:**
> No.


(And that's a lower case w, even at the beginning of a sentence, look it up in the dictionary.)
:lolflag:

---

### Post by Kai69 on 2010-02-06
> **Leppie said:**
> i'm not sure which one was worse, millenium or vista...

Never used millenium what was that?

---

### Post by warfacegod on 2010-02-06
> **Kai69 said:**
> Never used millenium what was that?

That was Satan's rule of 1000 years.

---

### Post by Leppie on 2010-02-06
> **Kai69 said:**
> Never used millenium what was that?
[http://en.wikipedia.org/wiki/Windows_Me](http://en.wikipedia.org/wiki/Windows_Me)

i've never seen a pc that came with millenium pre-installed. at least vista was, even though a lot of people have requested a downgrade to xp...

---

### Post by Kai69 on 2010-02-06
> **leppie said:**
> [http://en.wikipedia.org/wiki/windows_me](http://en.wikipedia.org/wiki/windows_me)

i've never seen a pc that came with millenium pre-installed. At least vista was, even though a lot of people have requested a downgrade to xp...

yuck!!

---

### Post by Leppie on 2010-02-06
> **Kai69 said:**
> yuck!!
exactly...

---

### Post by Kai69 on 2010-02-06
looks like 98 with colour :p

---

### Post by Leppie on 2010-02-06
> **Kai69 said:**
> looks like 98 with colour :p
looks like something unusable...

---

### Post by Kai69 on 2010-02-06
> **Leppie said:**
> looks like something unusable...

I think our 1st pc had win98 in 2000 brought a new pc with XP never saw any others.

---

### Post by Leppie on 2010-02-06
> **Kai69 said:**
> I think our 1st pc had win98 in 2000 brought a new pc with XP never saw any others.
first pc i used was a mac...
second had msdos... was an xt... :lolflag:

---

### Post by Kai69 on 2010-02-06
> **Leppie said:**
> first pc i used was a mac...
second had msdos... was an xt... :lolflag:
Never used a mac or ms doss :p
Just figured out why i need windows on my lappy,  for work for ISUZU manuals tried wine didnt want to know NUTS

---

### Post by Woolio1 on 2010-02-06
> **Leppie said:**
> did you check for errors after downloading and burning? it's always best to check before installing.
anyways, start your thread and give us the link so we can have a look.


ubuntu gives you the power to control most of the system (instead of the system controlling what you can do with it). so if something goes wrong, it may seem difficult to repair at start, but most things actually can be repaired. most first time users do not have enough knowledge to break the system badly enough to have to re-install it. it's different if some experienced user provides some nasty code which breaks the system.
i would say that in general windows systems are more difficult to repair.


I'm not having trouble right now, but if I encounter anything, I'll make sure to come here and get help. Any tips for a beginner? 

And now, to prevent this from derailing the entire thread... I say we halt the conversation post-haste. 

-Ericson

---

### Post by Kai69 on 2010-02-06
Has anyone tried using the recovery disk from another pc I wonder what would happen ?:lolflag:

---

### Post by warfacegod on 2010-02-06
> **Kai69 said:**
> Has anyone tried using the recovery disk from another pc I wonder what would happen ?:lolflag:

I've done that with XP manufacturer recovery discs. Compaqs work on anything. HPs don't work at all. I'd rather shoot myself than argue with another Dell disc or machine. Gateways are iffy. IBM discs work fairly well.

---

### Post by Leppie on 2010-02-06
> **Kai69 said:**
> Never used a mac or ms doss :p
Just figured out why i need windows on my lappy,  for work for ISUZU manuals tried wine didnt want to know NUTS
virtualisation is the word...
install xp in virtual box. after the clean install in virual box, make a copy of the image so you can restore it when needed ;)

---

### Post by Leppie on 2010-02-06
> **warfacegod said:**
> I've done that with XP manufacturer recovery discs. Compaqs work on anything. HPs don't work at all. I'd rather shoot myself than argue with another Dell disc or machine. Gateways are iffy. IBM discs work fairly well.
i've never really had issues with the hp and dell recovery discs. not sure what you guys mean by recovery disc... hp calls the hp xp disc "recovery disc", installs fine on non-hp machines. it just asks for a valid product key.

---

### Post by warfacegod on 2010-02-06
> I'd rather shoot myself than argue with another Dell disc or machine.

I just felt that I needed to reiterate this: *I'd rather shoot myself than argue with another Dell disc or machine.*

I just remembered. I've already shot myself. DAMN IT!!!!:-x:evil:

---

### Post by Kai69 on 2010-02-06
> **warfacegod said:**
> I just felt that I needed to reiterate this: *I'd rather shoot myself than argue with another Dell disc or machine.*

I just remembered. I've already shot myself. DAMN IT!!!!:-x:evil:

So whats wrong with DELLS ?

---

### Post by warfacegod on 2010-02-06
> i've never really had issues with the hp and dell recovery discs. not sure what you guys mean by recovery disc... hp calls the hp xp disc "recovery disc", installs fine on non-hp machines. it just asks for a valid product key.

I've *never* had an HP disc work in anything but an HP machine. Aside from that good company.

> So whats wrong with DELLS ? 

I could go through the loooonnnngggg list but I'll just ask you this; Have you ever wondered why they are only one of three computer companies with their own support sub-forums here?

---

### Post by Kai69 on 2010-02-06
I thought it was because of the number of people owning said pcs

---

### Post by warfacegod on 2010-02-06
> **Kai69 said:**
> I thought it was because of the number of people owning said pcs

Dells are pieces of crap. They tend to put substandard parts into their computers. I here even Alienware systems have dropped in quality since Dell bought the company. Next time you are in a computer store, compare the Touchpads of a Dell laptop and a Toshiba or IBM.

---

### Post by Woolio1 on 2010-02-06
> **warfacegod said:**
> Dells are pieces of crap. They tend to put substandard parts into their computers. I here even Alienware systems have dropped in quality since Dell bought the company. Next time you are in a computer store, compare the Touchpads of a Dell laptop and a Toshiba or IBM.

I've been using a Dell Box (inspiron 530) and a Dell Mini 10. Both work excellently. Have had no problems with hardware. Ever.

---

### Post by warfacegod on 2010-02-06
> **Woolio1 said:**
> I've been using a Dell Box (inspiron 530) and a Dell Mini 10. Both work excellently. Have had no problems with hardware. Ever.

Roughly 9 out of 10 desktops people bring to me to fix are Dells. There is no way 90% of computers out there are Dell.

---

### Post by Woolio1 on 2010-02-07
Never said they were. I was just saying... I must've bought some pretty terrific Dells.

---

### Post by Leppie on 2010-02-07
> **warfacegod said:**
> Next time you are in a computer store, compare the Touchpads of a Dell laptop and a Toshiba or IBM.
i like the compaq touchpads :)

---

### Post by warfacegod on 2010-02-07
Dell touchpads are flat out cheap and flimsy. Especially the buttons. I feel like I'm going to break it, ever time I use one. The touchpad on my Toshiba is just starting to get a little shaky and it's many years old and yet it's still much better than a brand new Dell.

---

### Post by Leppie on 2010-02-07
> **warfacegod said:**
> Dell touchpads are flat out cheap and flimsy. Especially the buttons. I feel like I'm going to break it, ever time I use one. The touchpad on my Toshiba is just starting to get a little shaky and it's many years old and yet it's still much better than a brand new Dell.
what Dell series have you seen?

---

### Post by warfacegod on 2010-02-07
> **Leppie said:**
> what Dell series have you seen?

Don't recall. My wife's aunt bought a Dell XPS for around $1400 US and the touchpad was just as bad as the cheapy models I've seen.

---

### Post by Leppie on 2010-02-07
> **warfacegod said:**
> Don't recall. My wife's aunt bought a Dell XPS for around $1400 US and the touchpad was just as bad as the cheapy models I've seen.
i was said to a Dell reseller that the Lattitude series (business machines) looks flimsy... he wasn't very pleased i believe...

---

### Post by warfacegod on 2010-02-07
> **Leppie said:**
> i was said to a Dell reseller that the Lattitude series (business machines) looks flimsy... he wasn't very pleased i believe...

Folks don't like it when you tell them their livelihood is a piece of garbage.

---

### Post by Leppie on 2010-02-07
> **warfacegod said:**
> Folks don't like it when you tell them their livelihood is a piece of garbage.
how can a piece of garbage be your livelihood???

---

### Post by warfacegod on 2010-02-07
> **Leppie said:**
> how can a piece of garbage be your livelihood???

When your the garbage man or ...you sell Dells. Same thing.

---

### Post by Kai69 on 2010-02-07
The only thing ive had a problem with on my Dell is the O/S every thing else works :lolflag:

---

### Post by willowave on 2010-02-07
Whats better than a Dell?

---

### Post by lisati on 2010-02-07
The only Dell that has come my way was beyond my skills and patience to get working (wouldn't power up, I think there was a power supply problem and the battery was dead) so I'm not in a position to comment on the touch pad. 

I've had two Toshiba laptops, and haven't noticed any problems with the keypad, other than the occasional jumping of the cursor if I'm a bit careless where I have my hands while typing. Mind you, I generally use a USB mouse..... :)

---

### Post by nothingspecial on 2010-02-07
uugghh!?!

Mice ..... EEEEEEKK

---

### Post by warfacegod on 2010-02-07
Quick! Get Jinx the Cat!

---

### Post by willowave on 2010-02-07
you can borrow my cat. he's got some sharp claws.

---

### Post by willowave on 2010-02-07
you know...I just realized my beans went from like...70 to 8.

---

### Post by warfacegod on 2010-02-07
> **willowave said:**
> you can borrow my cat. he's got some sharp claws.

Is his name Hobbs?

---

### Post by willowave on 2010-02-07
> **warfacegod said:**
> Is his name Hobbs?
lol nope. Paco.

---

### Post by audiomick on 2010-02-07
> **willowave said:**
> you know...I just realized my beans went from like...70 to 8.
hmmm.... and wfg now has over 2000....
but I am sure there is no connection...

---

### Post by willowave on 2010-02-07
> **audiomick said:**
> hmmm.... and wfg now has over 2000....
but I am sure there is no connection...
 hmm...can he hack?

---

### Post by warfacegod on 2010-02-07
> **audiomick said:**
> hmmm.... and wfg now has over 2000....
but I am sure there is no connection...

Actually, Leppies and mine just dropped about 100 each. We were both very close to 2100 beanses.

---

### Post by audiomick on 2010-02-07
> **willowave said:**
> hmm...can he hack?
only with a cleaver.

@ wfg: that's a bit odd. I think my count is ok. It looks about right...

---

### Post by nothingspecial on 2010-02-07
slippery beans

---

### Post by Kai69 on 2010-02-07
Try using a spoon beans wont slip:lolflag:

---

### Post by warfacegod on 2010-02-07
> **willowave said:**
> you know...I just realized my beans went from like...70 to 8.

I'm going to guess that most of your beanses came from my thread that you so gracefully hijacked. That would explain why your down to 8.

---

### Post by warfacegod on 2010-02-07
Spoons don't work for Mexican jumping beanses. Use a hammer instead.

---

### Post by nothingspecial on 2010-02-07
> **Kai69 said:**
> Try using a spoon beans wont slip:lolflag:

I`m going to try that next friday night ;)

---

### Post by Kai69 on 2010-02-07
> **warfacegod said:**
> Spoons don't work for Mexican jumping beanses. Use a hammer instead.

Why not just cut their legs off ;)

---

### Post by nothingspecial on 2010-02-07
> **Kai69 said:**
> Why not just cut their legs off ;)

It wouldn`t be as much fun

---

### Post by warfacegod on 2010-02-07
Because we'd have to set up a bean amputee ward.

---

### Post by nothingspecial on 2010-02-07
Because we'd have to set up a bean amputee world.

---

### Post by Kai69 on 2010-02-07
Try mashing them up instead in the UK we have Mushy Peas normally put on chips YUCK:-&

---

### Post by willowave on 2010-02-07
> **warfacegod said:**
> I'm going to guess that most of your beanses came from my thread that you so gracefully hijacked. That would explain why your down to 8.
 I kind of figured that. Thats kind of mean of them. lol
I had good intentions when I hijacked your thread.

---

### Post by willowave on 2010-02-07
> **Kai69 said:**
> Try mashing them up instead in the UK we have Mushy Peas normally put on chips YUCK:-&
 Seriously? Peas? Like the green kind?
Or is this a case of we call them peas and you guys call them beans. lol

---

### Post by willowave on 2010-02-07
> **Kai69 said:**
> Why not just cut their legs off ;)
You silly silly people.
 
Jumping beans don't have legs.
They have hats but they don't have legs.

---

### Post by nothingspecial on 2010-02-07
How do you jump with a hat?..........but no legs?

---

### Post by warfacegod on 2010-02-07
> **willowave said:**
> Seriously? Peas? Like the green kind?
Or is this a case of we call them peas and you guys call them beans. lol

It's case of they call them lunar rockets but they're really peas.

---

### Post by warfacegod on 2010-02-07
> **nothingspecial said:**
> How do you jump with a hat?..........but no legs?

It's allot like falling and missing the ground.

---

### Post by nothingspecial on 2010-02-07
> **warfacegod said:**
> It's case of they call them lunar rockets but they're really peas.

No

---

### Post by Kai69 on 2010-02-07
[attach]146377[/attach]

---

### Post by audiomick on 2010-02-07
> **Kai69 said:**
> Try mashing them up instead in the UK we have Mushy Peas normally put on chips YUCK:-&
In Adelaide they do a thing called a "Pie Floater". That's a meat pie floating in a bowl of pea soup.
No one  in Australia outside of Adelaide understands the attraction.

As far as chips go, I thought the Germans were bad with their tomato sauce and mayonnaise on chips (which you can buy ready mixed in a tube, like stripy toothpaste...)
Everyone knows the only thing you can put on chips is white vinegar!

---

### Post by nothingspecial on 2010-02-07
You`ve never been to Mario`s

---

### Post by Kai69 on 2010-02-07
Chips and mayo hmmmmmmm nice=P~

---

### Post by willowave on 2010-02-07
> **Kai69 said:**
> [attach]146377[/attach]
Holy crap...thats nasty lookin.

---

### Post by nothingspecial on 2010-02-07
[attach]146378[/attach].

---

### Post by willowave on 2010-02-07
> **Kai69 said:**
> Chips and mayo hmmmmmmm nice=P~
 Do you mean chips as in fries or chips as in american potato "crisps"? lol
(I could go on and on with this...)

---

### Post by audiomick on 2010-02-07
> **nothingspecial said:**
> You`ve never been to Mario`s
In Brunswick St.? Go there every time I get back to Melbourne... ;)

---

### Post by willowave on 2010-02-07
> **nothingspecial said:**
> [attach]146378[/attach].
LOL do they have a Dr standing by for the heart attack thats coming after you eat that?

---

### Post by Kai69 on 2010-02-07
> **willowave said:**
> Do you mean chips as in fries or chips as in american potato "crisps"? lol
(I could go on and on with this...)

Sorry chips as in fries :p
Audiomick youve got to have chips with mayo and Bratwurst with currysause

---

### Post by audiomick on 2010-02-07
> **nothingspecial said:**
> [attach]146378[/attach].
Please tell me that is a platter for 10 people....

---

### Post by Kai69 on 2010-02-07
> **audiomick said:**
> Please tell me that is a platter for 10 people....

Look at the amount of toast he has Bet he didnt eat all of it :lolflag:

---

### Post by warfacegod on 2010-02-07
> **nothingspecial said:**
> [attach]146378[/attach].

I once ate a pancake about the size of that platter.

---

### Post by nothingspecial on 2010-02-07
[[COLOR="Magenta"]It`s Free[/COLOR]]("http://www.theboltonnews.co.uk/leisure/foodanddrink/eatingout/3943812.Bolton_s_amazing_10_egg__big_breakfast_challenge/")..........if you can eat it.

---

### Post by Kai69 on 2010-02-07
How much if you cant :lolflag:

---

### Post by willowave on 2010-02-07
> **Kai69 said:**
> Sorry chips as in fries :p
Audiomick youve got to have chips with mayo and Bratwurst with currysause
No need to be sorry. I'm just giving you a little crap. I dated someone from England. I used to harrass him all the time abotu the food thing. My favorite one was "biscuits"...and cookies? I think

---

### Post by warfacegod on 2010-02-07
I like French fries and mayo. I'm one of the few Americans not addicted to that ketchup idiocy.

---

### Post by nothingspecial on 2010-02-07
> **kai69 said:**
> how much if you cant :lolflag:

£10.95

---

### Post by warfacegod on 2010-02-07
> **nothingspecial said:**
> £10.95

Does throwing some of it at people at other tables count?

---

### Post by nothingspecial on 2010-02-07
> **warfacegod said:**
> Does throwing some of it at people at other tables count?

Not if you get caught

---

### Post by Kai69 on 2010-02-07
Where from last time I saw a plate that full was when I was working for British Rail, We used to go to the London Underground canteens £5.00 Full English :p

---

### Post by audiomick on 2010-02-07
> **nothingspecial said:**
> [[COLOR=Magenta]It`s Free[/COLOR]]("http://www.theboltonnews.co.uk/leisure/foodanddrink/eatingout/3943812.Bolton_s_amazing_10_egg__big_breakfast_challenge/")..........if you can eat it.

> A spokesman for the British Heart Foundation said: “Eating this amount in one sitting is not a good idea.” 

That'd be your classic English  Understatement then...

@Kai: I didn't mention Currywurst because I try not to think about that if I can possibly manage it....;)

---

### Post by Kai69 on 2010-02-07
I miss German food :sad: Aldi only has a few items of german food .

---

### Post by warfacegod on 2010-02-07
I've tried very hard to not post anything political here because I didn't want the mods to shut us down. However, the level of moronitude that the Nobel Peace prize has achieved is staggering.

A couple among many foolish winners:

Yasser Arafat: Inventor of modern day suicide bombing.

Barrack Obama: for his *intentions*, not actually having done *anything!* I shall refrain from further comment on this particular laureate, as much as I would like to let the flood gates open.

And now possibly joining such a heady crowd:

[http://mashable.com/2010/02/06/internet-nobel/]("http://mashable.com/2010/02/06/internet-nobel/")

---

### Post by lisati on 2010-02-07
> **audiomick said:**
> Everyone knows the only thing you can put on chips is white vinegar!
Vinegar on chips/fries? Using wine that has gone bad as a condiment is FOUL, and insisting that it should be white.....well! Must be time to get the AV software out.......

---

### Post by Kai69 on 2010-02-07
> **warfacegod said:**
> I've tried very hard to not post anything political here because I didn't want the mods to shut us down. However, the level of moronitude that the Nobel Peace prize has achieved is staggering.

A couple among many foolish winners:

Yasser Arafat: Inventor of modern day suicide bombing.

Barrack Obama: for his *intentions*, not actually having done *anything!* I shall refrain from further comment on this particular laureate, as much as I would like to let the flood gates open.

And now possibly joining such a heady crowd:

[http://mashable.com/2010/02/06/internet-nobel/](http://mashable.com/2010/02/06/internet-nobel/)

So which search engine are they going to give it to:lolflag:

---

### Post by audiomick on 2010-02-07
> **warfacegod said:**
> 
And now possibly joining such a heady crowd:

[http://mashable.com/2010/02/06/internet-nobel/](http://mashable.com/2010/02/06/internet-nobel/)
I am speechless...

In the event of a win, would the prize money then be divided up among all the people who are using the internet at the time of the award?

---

### Post by Leppie on 2010-02-07
> **audiomick said:**
> I am speechless...

In the event of a win, would the prize money then be divided up among all the people who are using the internet at the time of the award?
are you from this planet??? if those few people try to control all the money in the world, hence the world population...

---

### Post by audiomick on 2010-02-07
> **Leppie said:**
> are you from this planet??? 
As far as I know...;)
What I meant to convey was that I find the concept of awarding "the Internet" a Nobel Prize utterly ridiculous.

---

### Post by Kai69 on 2010-02-07
Wasnt the internet originally developed for the military ?

---

### Post by warfacegod on 2010-02-07
> **audiomick said:**
> I am speechless...

In the event of a win, would the prize money then be divided up among all the people who are using the internet at the time of the award?

If it was, we'd end up owing money. Not that we don't anyway.

---

### Post by warfacegod on 2010-02-07
> **Kai69 said:**
> Wasnt the internet originally developed for the military ?

Many of the first internet protocols were originally from CERN so that particle physicists could more easily communicate and share data.

---

### Post by Leppie on 2010-02-07
> **Kai69 said:**
> Wasnt the internet originally developed for the military ?
yes, if i'm not mistaken it started with the arpa net. the military thought it wouldn't be that useful...

---

### Post by audiomick on 2010-02-07
as I thought

from Wikipedia
According to Nobel's will, the Peace Prize should be awarded to the [COLOR=Red]**person**[/COLOR] who:
   [SIZE=1]&#8220;[/SIZE] [SIZE=1]...shall have done the most or the best work for fraternity between nations, for the abolition or reduction of standing armies and for the holding and promotion of peace congresses.*[[1]]("http://en.wikipedia.org/wiki/Nobel_Peace_Prize#cite_note-0")*[/SIZE]
"Good evening Mr. Internet, how are you feeling today?"

@Kai: Yes, it was, as far as I know.

---

### Post by warfacegod on 2010-02-07
> According to Nobel's will, the Peace Prize should be awarded to the person who:
“ ...shall have done the most or the best work for fraternity between nations, for the abolition or reduction of standing armies and for the holding and promotion of peace congresses.[1]

Which means Obama needs to give his back. WE could put that on protest signs.


GIVE IT BACK BARRACK!

---

### Post by willowave on 2010-02-07
> **Leppie said:**
> yes, if i'm not mistaken it started with the arpa net. the military thought it wouldn't be that useful...
You are correct. I remember it from all my networking classes.

---

### Post by sudoer541 on 2010-02-07
I waz kinda zcared cuz I though thiz guy would do zomething really ztupid zeriosuly! 
no I waz zcared!!!! I waz like OMG!!! iz he gonna do zomething embarazing?

---

### Post by ubuchignome on 2010-02-07
LOL. I can sure relate to this post! Thanks I needed that .  Oh, and I love the "12 step for windows program" quote, nice!

TC
:p

---

### Post by willowave on 2010-02-07
> **sudoer541 said:**
> I waz kinda zcared cuz I though thiz guy would do zomething really ztupid zeriosuly! 
no I waz zcared!!!! I waz like OMG!!! iz he gonna do zomething embarazing?
 Dude, I think you need a new keyboard. Your S is mezzed up. ...I mean messed up.
Or maybe just spell check?

---

### Post by warfacegod on 2010-02-07
> **ubuchignome said:**
> LOL. I can sure relate to this post! Thanks I needed that .  Oh, and I love the "12 step for windows program" quote, nice!

TC
:p

We're here to please.

---

### Post by sudoer541 on 2010-02-07
> **willowave said:**
> Dude, I think you need a new keyboard. Your S is mezzed up. ...I mean messed up.
Or maybe just spell check?

or maybe is a new way of communicating lol
btw I bough my keyboard for $3 and never had a problem with it. but I might buy a new one cuz this one is very basic.

---

### Post by warfacegod on 2010-02-07
So! Back to something stupid. Anybody know how to reduce an install down to nothing? As though it were a fresh minimal install. No anything. Black screen and text.

I think it was posted in here before but, to be honest, I am f*aaarrrrr* too lazy to go hunting through nearly 600 posts.

I'm going to try and build an OS from the ground up with a wireless connection.

---

### Post by audiomick on 2010-02-08
Obviously, the easiest way would be to install a minimal system and start from there, but I can't see you doing that....

If you can find a package list for the minimal install, you could try removing everything that is not on it from a standard install.

---

### Post by Leppie on 2010-02-08
> **willowave said:**
> Dude, I think you need a new keyboard. Your S is mezzed up. ...I mean messed up.
Or maybe just spell check?
lolzerz...

---

### Post by Leppie on 2010-02-08
> **warfacegod said:**
> So! Back to something stupid. Anybody know how to reduce an install down to nothing? As though it were a fresh minimal install. No anything. Black screen and text.

I think it was posted in here before but, to be honest, I am f*aaarrrrr* too lazy to go hunting through nearly 600 posts.

I'm going to try and build an OS from the ground up with a wireless connection.
maybe you've got some desktop package installe?
```
dpkg -l | grep desktop
```
after removing that one, i'm sure you're pretty much back at a minimal install.

---

### Post by audiomick on 2010-02-08
> **warfacegod said:**
> 
I think it was posted in here before but, to be honest, I am f*aaarrrrr* too lazy to go hunting through nearly 600 posts.
I'm a bit bored, so I had a look. Nothing there.

---

### Post by audiomick on 2010-02-08
> **Leppie said:**
> maybe you've got some desktop package installe?
```
dpkg -l | grep desktop
```after removing that one, i'm sure you're pretty much back at a minimal install.
Will that pull out anything that has the desktop as a dependency? By that, I mean effectively all GUI applications?

---

### Post by warfacegod on 2010-02-08
> Obviously, the easiest way would be to install a minimal system and start from there, but I can't see you doing that....

That is exactly what I would prefer doing but I can't. No working internal disc drive and minimal .iso's won't install to a jump drive.

---

### Post by warfacegod on 2010-02-08
> **willowave said:**
> Dude, I think you need a new keyboard. Your S is mezzed up. ...I mean messed up.
Or maybe just spell check?

That's how the aliens speak before they've learned our language fully.


Ve 'ave vayz to mek you taulk!

---

### Post by audiomick on 2010-02-08
> **warfacegod said:**
> That is exactly what I would prefer doing but I can't. No working internal disc drive and minimal .iso's won't install to a jump drive.
maybe you can find a way to do that here
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

---

### Post by willowave on 2010-02-08
Whats the difference between what you want to do and a Gentoo installation?
And I'm not being a smart ***. lol I have installed Gentoo once, but not without help. It's very basic and you have to add everything you want.

---

### Post by willowave on 2010-02-08
> **audiomick said:**
> maybe you can find a way to do that here
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
Thanks for that post mick. I was just trying to find a way to get chakra to a usb and it wont go with Unetbootin. I'm going to try one of those other ones.

---

### Post by audiomick on 2010-02-08
> **willowave said:**
> Thanks for that post mick. I was just trying to find a way to get chakra to a usb and it wont go with Unetbootin. I'm going to try one of those other ones.
good luck then!

---

### Post by Leppie on 2010-02-08
> **willowave said:**
> Whats the difference between what you want to do and a Gentoo installation?
And I'm not being a smart ***. lol I have installed Gentoo once, but not without help. It's very basic and you have to add everything you want.
gentoo and arch are more for people who like to compile and setup everything from scratch all the time, rather than installing and actually using their system ;)

---

### Post by warfacegod on 2010-02-08
> **Leppie said:**
> gentoo and arch are more for people who like to compile and setup everything from scratch all the time, rather than installing and actually using their system ;)

As opposed to people that set it up to use it to break it.

---

### Post by texaswriter on 2010-02-08
> **Leppie said:**
> gentoo and arch are more for people who like to compile and setup everything from scratch all the time, rather than installing and actually using their system ;)

I thought custom compiles were the **most **optimized for a particular system. Whenever I have to update something that's broken in the repositories [aka Pidgin on Debian Lenny], I custom compile it. Unless it's just a pain, [haha, when is it not a pain lol], ok, even when it's a pain I custom compile. Did that for VLC, PIDGIN, even have a version of FF 3.5 on Debian Lenny. Too bad I couldn't custom compile WoW, ES IV, and Total war games, then life would be **perfect.** :popcorn::KS

---

### Post by Leppie on 2010-02-08
> **willowave said:**
> Thanks for that post mick. I was just trying to find a way to get chakra to a usb and it wont go with Unetbootin. I'm going to try one of those other ones.
you could have a look at this page: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

you could also try usb-creator-gtk or usb-imagewriter ;)
i've tried usb-imagewriter myself with a dsl .iso, so i know it works.

---

### Post by Leppie on 2010-02-08
> **texaswriter said:**
> I thought custom compiles were the **most **optimized for a particular system. Whenever I have to update something that's broken in the repositories [aka Pidgin on Debian Lenny], I custom compile it. Unless it's just a pain, [haha, when is it not a pain lol], ok, even when it's a pain I custom compile. Did that for VLC, PIDGIN, even have a version of FF 3.5 on Debian Lenny. Too bad I couldn't custom compile WoW, ES IV, and Total war games, then life would be **perfect.** :popcorn::KS
what's the fun of custom compiling? i've compiled e17 a couple of times... but i can tell you that there's no excitement in seeing comile messages flashing by for hours... and e17 isn't even such a huge package to compile...

---

### Post by Leppie on 2010-02-08
> **warfacegod said:**
> As opposed to people that set it up to use it to break it.
breaking is using to me ;)

---

### Post by texaswriter on 2010-02-08
> **Leppie said:**
> what's the fun of custom compiling? i've compiled e17 a couple of times... but i can tell you that there's no excitement in seeing comile messages flashing by for hours... and e17 isn't even such a huge package to compile...

Hey, not that hardcore that I will compile something basic like a windowing manager [whatever E17 is]... Just stuff that is necessary. That's why i use Gnome... can be basic, fast, and robust with metacity or nice, still fast [on my laptop], and mostly stable with compiz... 

Now apps that I can't get or need... like pidgin.. or vlc, Debian especially, has old versions in the repository. I'm basically using apps that were frozen prolly early last year on Debian Lenny. Apps in Ubuntu are much newer... all of them.

---

### Post by Leppie on 2010-02-08
> **texaswriter said:**
> Now apps that I can't get or need... like pidgin.. or vlc, Debian especially, has old versions in the repository. I'm basically using apps that were frozen prolly early last year on Debian Lenny. Apps in Ubuntu are much newer... all of them.
well, you could try an ubuntu minimal install and then add everything you want to that. it's like a very new debian install like that (just make sure you don't install things like ubuntu-desktop, etc.)

---

### Post by warfacegod on 2010-02-08
How's this for stupid? I just wiped my normal install and, until I get a minimal working, I'll be running on my experimental install.:shock:

---

### Post by Leppie on 2010-02-08
> **warfacegod said:**
> How's this for stupid? I just wiped my normal install and, until I get a minimal working, I'll be running on my experimental install.:shock:
haha, at least you still have your minimal... ;)

---

### Post by texaswriter on 2010-02-08
> **Leppie said:**
> well, you could try an ubuntu minimal install and then add everything you want to that. it's like a very new debian install like that (just make sure you don't install things like ubuntu-desktop, etc.)

Actually, I will be getting a chance to setup **another** server. Since it's a bit newer than Pentium III, I'll actually stick Debian Lenny [server] or Ubuntu Server on it. Not sure about minimal, but I'll look into that if I have problems installing. Shouldnt' though.. had problems instaling Debian on the P3, but I found out it was because of a bad stick of RAM. I tried so many different OS installs, till finally a Ubuntu Hardy install stuck... then had the box crash on the memory problem [like months later]... That's when I found out it was a bad stick.

---

### Post by audiomick on 2010-02-08
> **warfacegod said:**
> How's this for stupid? I just wiped my normal install and, until I get a minimal working, I'll be running on my experimental install.:shock:
Champion effort! :p

---

### Post by nothingspecial on 2010-02-08
> **Leppie said:**
> haha, at least you still have your minimal... ;)

My first steps are always 

```
sudo apt-get install wicd ncurses-base ncurses-bin ncurses-term
```

Then ```
wicd-curses
```

to set up my wireless.

---

### Post by warfacegod on 2010-02-08
> **Leppie said:**
> haha, at least you still have your minimal... ;)

Not so much. CLI is refusing to let me use wireless.

> **audiomick said:**
> Champion effort! :p

Aside from firing it into the sun, it doesn't get much better than that.

---

### Post by warfacegod on 2010-02-08
Okay...plan B. Ignoring the fact that plan B was actually plan A because having priorities for plans or even plans at all it counter-productive and frankly utterly beside the point.

I'm going to do a full install of 9.10 and lobotomise it leaving wireless connectivity intact. ....Anybody know how to do that?

---

### Post by nothingspecial on 2010-02-08
> **warfacegod said:**
> Not so much. CLI is refusing to let me use wireless.


Does wicd-curses not work?

---

### Post by audiomick on 2010-02-08
> **warfacegod said:**
> Okay...plan B. Ignoring the fact that plan B was actually plan A because having priorities for plans or even plans at all it counter-productive and frankly utterly beside the point.
 
"Making plans is what people do instead of thinking"   - Terry Pratchett
Don't ask me which book, I've got about 40 from him.

---

### Post by audiomick on 2010-02-08
> **warfacegod said:**
> 
I'm going to do a full install of 9.10 and lobotomise it leaving wireless connectivity intact. ....Anybody know how to do that?

I reckon the biggest trick will be sorting out which packages you can pull out together in one go and still leave a bootable system on which you can proceed to pull out the next block.

---

### Post by warfacegod on 2010-02-08
> **nothingspecial said:**
> Does wicd-curses not work?

Don't have a wired connection to get it.

---

### Post by warfacegod on 2010-02-08
> **audiomick said:**
> I reckon the biggest trick will be sorting out which packages you can pull out together in one go and still leave a bootable system on which you can proceed to pull out the next block.

And I was so hoping to open Synaptic, select all, mark for Complete removal and apply.

---

### Post by Leppie on 2010-02-08
> **nothingspecial said:**
> Does wicd-curses not work?
wicked curses? not sure they would work on your wifi... dogs maybe, but wifi doubtful... :P

---

### Post by warfacegod on 2010-02-08
> **Leppie said:**
> wicked curses? not sure they would work on your wifi... dogs maybe, but wifi doubtful... :P

I like my dog, I'll try it on my wife.

---

### Post by nothingspecial on 2010-02-08
How have you managed to do a minimal install without a wired connection?

If you can`t get wireless to work?

I wouldn`t try wicked curses on your wife if she`s anything like mine.....


.....I always loose.

---

### Post by Leppie on 2010-02-08
> **nothingspecial said:**
> .....I always loose.
don't we always? even if we win, we loose... #-o

---

### Post by Kai69 on 2010-02-08
Hi warfacegod why not try this 10mb very small [http://distrowatch.com/table.php?distribution=tinycore](http://distrowatch.com/table.php?distribution=tinycore)
Or for use in ram [http://distrowatch.com/table.php?distribution=puppy](http://distrowatch.com/table.php?distribution=puppy)

---

### Post by warfacegod on 2010-02-08
> **Leppie said:**
> don't we always? even if we win, we loose... #-o

Because I had to ask why it was my fault made it my fault.

---

### Post by nothingspecial on 2010-02-08
There`s no reason......it just is......like........

the baddie from the silver surfer.....

Galactus?

---

### Post by willowave on 2010-02-08
> **Leppie said:**
> don't we always? even if we win, we loose... #-o
Thats cuz we make the rules :D heh

---

### Post by warfacegod on 2010-02-08
> **willowave said:**
> Thats cuz we make the rules :D heh

That's because you have something we want.

---

### Post by Leppie on 2010-02-09
> **warfacegod said:**
> That's because you have something we want.
true... :lolflag:

---

### Post by warfacegod on 2010-02-09
Thought I'd go incognito for a bit.

---

### Post by audiomick on 2010-02-09
What's his name? Killer?

---

### Post by willowave on 2010-02-09
> **warfacegod said:**
> That's because you have something we want.
You know, I really wish that was something my mother would have told me about when I was younger. I'm going to make sure my daughter knows, I can tell you that much. 
Thats the only reason you guys do ANYTHING is cuz you want "something" :P

---

### Post by warfacegod on 2010-02-09
*Her* name is Retarded And Remarkably Deformed Furry Yoda. Dog for short.

---

### Post by warfacegod on 2010-02-09
Actually I made that up. I have no idea who's dog that is.

---

### Post by warfacegod on 2010-02-09
What's that thing about dogs and their masters looking alike?

---

### Post by audiomick on 2010-02-09
> **warfacegod said:**
> What's that thing about dogs and their masters looking alike?
It's true. Not always, but amazingly often...

---

### Post by willowave on 2010-02-09
I'm glad you changed the subject. :D I'm about to install everything pretty there is to install from the "Great Desktop Effects FAQ" any advice?

---

### Post by audiomick on 2010-02-09
> **willowave said:**
> I'm glad you changed the subject. :D I'm about to install everything pretty there is to install from the "Great Desktop Effects FAQ" any advice?
Don't do anything that will shoot down your system....;)

---

### Post by nothingspecial on 2010-02-09
> **willowave said:**
> any advice?

Don`t put your kids in the bath after they`ve covered themselves in an entire sack of plaster.

I mean it - just dont.

---

### Post by warfacegod on 2010-02-09
When your kid pours a gallon of blue oil-based paint on his head, give up all hope of him not looking like a Smurf for the next month.

---

### Post by warfacegod on 2010-02-09
> **willowave said:**
> I'm glad you changed the subject. :D I'm about to install everything pretty there is to install from the "Great Desktop Effects FAQ" any advice?

Turn everything on at the same time.

---

### Post by willowave on 2010-02-09
Smartyarses.
See if I got around the stars this time. Unfortunately for you even if I hose my system I can come back and bug you because I am talking to you from WINDOWS. :P
HA!! I swore!!

---

### Post by Leppie on 2010-02-09
> **willowave said:**
> Smartyarses.
See if I got around the stars this time. Unfortunately for you even if I hose my system I can come back and bug you because I am talking to you from WINDOWS. :P
HA!! I swore!!
some advice...
don't swear in front of your kids ;)
(it will backfire on you sooner than you imagine)

---

### Post by warfacegod on 2010-02-09
> **Leppie said:**
> some advice...
don't swear in front of your kids ;)
(it will backfire on you sooner than you imagine)

Yup, they'll start swearing at you from a Mac! Gasp!!!!

---

### Post by warfacegod on 2010-02-09
Look! It was me all along. Ha Ha. Fooled you guys.:tongue:

---

### Post by willowave on 2010-02-09
> **warfacegod said:**
> Look! It was me all along. Ha Ha. Fooled you guys.:tongue:
 lol bored huh?

---

### Post by warfacegod on 2010-02-09
> **willowave said:**
> lol bored huh?

Why do you think I started this thread in the first place?

---

### Post by willowave on 2010-02-09
good point. hows the laptop project coming along? You never did mention what happened to it last time.

---

### Post by warfacegod on 2010-02-09
> **willowave said:**
> good point. hows the laptop project coming along? You never did mention what happened to it last time.

Dead in it's tracks. It refuses to connect wirelessly from the command line install so I can't built my itty bitty OS. (warfacegod whips around and stalks off to pout and sulk in the corner because his nefarious schemes have been foiled again.)

---

### Post by warfacegod on 2010-02-09
Why does everyone in the forum take me seriously?


Not giving you guys the chance on that one. More specifically, why do they take me seriously when I'm being sarcastic? Even when I state that I'm being sarcastic! (But often refuse to listen to my advice when everyone else in the thread is clearly insane!)

---

### Post by audiomick on 2010-02-10
> **warfacegod said:**
> Why does everyone in the forum take me seriously?


Not giving you guys the chance on that one. More specifically, why do they take me seriously when I'm being sarcastic? Even when I state that I'm being sarcastic! (But often refuse to listen to my advice when everyone else in the thread is clearly insane!)
I know that feeling well...;)

---

### Post by nothingspecial on 2010-02-10
Some more advice -

Don`t take your iPod into the sauna.

---

### Post by warfacegod on 2010-02-10
You'd think with a Titanium case those things would be goddamned bulletproof but *nnnoooo!* It's amazing how easy it is to break those fragging things.

---

### Post by willowave on 2010-02-10
> **nothingspecial said:**
> Some more advice -
 
Don`t take your iPod into the sauna.
Yeah I learned not to take my phone into the bathroom when I shower too. I'm pretty sure that most of those small electronics are not fit to be in damp/wet environments. 
However, I tried the "phone in rice" thing to dry it out and it worked (mind you this is after my daughter submersed it in a cup of water for 2 minutes)
I bet that would dry out your iPod. Just don't use sticky jasmine rice. 
If you need a tough phone btw, my LG8300 has been through a cup of water, a snow bank for 3 hours. Not counting the various times its been flung dropped and mishandled by children. It's still working perfectly.

---

### Post by warfacegod on 2010-02-10
LG also makes the best TV's at the moment.

---

### Post by nothingspecial on 2010-02-10
There is a tv in the sauna. Not sure weather its lg or not.

Anyway, it`s behind a protective screen......the ipod, however, was not.

---

### Post by warfacegod on 2010-02-10
> **nothingspecial said:**
> There is a tv in the sauna. Not sure weather its lg or not.

Anyway, it`s behind a protective screen......the ipod, however, was not.

Isn't that what the touch screen is for?:rolleyes:

---

### Post by willowave on 2010-02-10
> **warfacegod said:**
> Isn't that what the touch screen is for?:rolleyes:
 lol nope I'm pretty sure its not :P

---

### Post by willowave on 2010-02-10
I'm bored. 
Quick, do something to entertain me!!
I know, I'll install windows inside virtualbox on my linux. 
Anything else fun I should install in Linux?

---

### Post by audiomick on 2010-02-10
> **willowave said:**
> I'm bored. 
Quick, do something to entertain me!!
I know, I'll install windows inside virtualbox on my linux. 
Anything else fun I should install in Linux?
Install my book keeping program,
[http://mcrichter.macbay.de/Seiten/Deutsch/Linux/Lin-HaBu/LinHaBu.htm](http://mcrichter.macbay.de/Seiten/Deutsch/Linux/Lin-HaBu/LinHaBu.htm)
 learn how to use it and then tell me how it works!;)

---

### Post by nothingspecial on 2010-02-10
I like having two linuxes and breaking one of them.

---

### Post by warfacegod on 2010-02-10
> **willowave said:**
> I'm bored. 
Quick, do something to entertain me!!
I know, I'll install windows inside virtualbox on my linux. 
Anything else fun I should install in Linux?

How's this:

---

### Post by Leppie on 2010-02-10
> **warfacegod said:**
> How's this:
that's nasty... not entertaining...

---

### Post by warfacegod on 2010-02-10
It's a talent. An attribute if you will.

---

### Post by audiomick on 2010-02-10
> **warfacegod said:**
> How's this:
looks like one of those synthesizer pop bands from the 1980's. Urrgh!

---

### Post by Leppie on 2010-02-10
> **willowave said:**
> I'm bored. 
Quick, do something to entertain me!!
I know, I'll install windows inside virtualbox on my linux. 
Anything else fun I should install in Linux?
install some lexmark printer drivers ;)

---

### Post by warfacegod on 2010-02-10
This then:

---

### Post by audiomick on 2010-02-10
> **warfacegod said:**
> This then:
is that a target on that bloke's head?

---

### Post by warfacegod on 2010-02-10
And we wonder why the other camps think we're crazy:

---

### Post by willowave on 2010-02-10
> **audiomick said:**
> is that a target on that bloke's head?
 LMAO...
no 
.the 
.i.3Pod play grrr...
naughty child
thats the iPod play/menu button

---

### Post by willowave on 2010-02-10
> **warfacegod said:**
> And we wonder why the other camps think we're crazy:
 thats just plain ugly and crazy. at least when you see people who go to football game with haircuts like that, you can at least assume they hopefylly were either already drunk...or planning on getting drunk. Both which make those haircuts much more understandable.

---

### Post by willowave on 2010-02-10
> **Leppie said:**
> install some lexmark printer drivers ;)
 _[COLOR=#0000ff]ewwwww at printer[/COLOR]_ drivers. no thank you.

---

### Post by willowave on 2010-02-10
> **audiomick said:**
> Install my book keeping program,
[http://mcrichter.macbay.de/Seiten/Deutsch/Linux/Lin-HaBu/LinHaBu.htm](http://mcrichter.macbay.de/Seiten/Deutsch/Linux/Lin-HaBu/LinHaBu.htm)
learn how to use it and then tell me how it works!;)
 ick at anything that involves numbers. bleah.

---

### Post by nothingspecial on 2010-02-10
[attach]146655[/attach]

---

### Post by warfacegod on 2010-02-10
Donald Trump's dog and the ultimate:

---

### Post by willowave on 2010-02-10
> **warfacegod said:**
> Donald Trump's dog and the ultimate:
 LOL, I've never seen that. Thats funny.

---

### Post by willowave on 2010-02-10
Is it safe to rename a ISO? I mean is there any reason why you shouldn't? I'm guessing no.

---

### Post by Leppie on 2010-02-10
> **willowave said:**
> Is it safe to rename a ISO? I mean is there any reason why you shouldn't? I'm guessing no.
what do you mean, change the name of an iso? like my_iso.iso to your_iso.iso?
or more like my_iso.iso to my_iso.img?
both are possible and shouldn't cause you any (major) issues ;)

---

### Post by neu5eeCh on 2010-02-10
> **warfacegod said:**
> I'm going to resize my sda1 partition. I'm going to install 9.10 NBR as a dual with normal 9.10 on my laptop. Why you ask? Because I feel like it.
Can any one give me a decent partition size for NBR?


You see? This is what happens when you start computing with Windows. I start going:

"My Linux installs are perfect? There's nothing for me to fix? Sigh. Good grief, I am bored! Let me go screw up my laptop again so I can have something to do"

And that's after three years of being Windows free. Ubuntu: The Windows 12 Step Program

Once you pull that off, try a dual boot system: Linux and OSOL. I've read that this can get quite ugly. Or better yet Linux, OSOL and FreeBSD. Send us a postcard.

---

### Post by Leppie on 2010-02-10
> **VTPoet said:**
> Once you pull that off, try a dual boot system: Linux and OSOL. I've read that this can get quite ugly. Or better yet Linux, OSOL and FreeBSD. Send us a postcard.
i'm going to go for linux+osol soon... will let you know ;)

---

### Post by warfacegod on 2010-02-10
I'm thinking of jumping ship.

---

### Post by Leppie on 2010-02-10
> **warfacegod said:**
> I'm thinking of jumping ship.
same here ;)

---

### Post by willowave on 2010-02-12
Hellloooooo.....ello ello ello
Echooooooooo echo echo echo

---

### Post by nothingspecial on 2010-02-12
Delta Alpha Mike November

---

### Post by willowave on 2010-02-12
Nice! lol

---

### Post by willowave on 2010-02-12
I was just trying to add another page to the thread. lol

---

### Post by audiomick on 2010-02-12
I'm still here...

---

### Post by warfacegod on 2010-02-12
> **audiomick said:**
> I'm still here...

I'm not. You guys can't see me. I'm hiding under the blankets.

---

### Post by nothingspecial on 2010-02-12
I`ve not bounced on the bed for years  :-\"

---

### Post by Leppie on 2010-02-12
> **nothingspecial said:**
> Delta Alpha Mike November
Hotel Oscar Lima Yankee Kilo Alpha Whiskey... ;)

---

### Post by Leppie on 2010-02-12
> **warfacegod said:**
> I'm not. You guys can't see me. I'm hiding under the blankets.
i'm behind the lamp... but don't tell anyone ;)

---

### Post by texaswriter on 2010-02-12
Did this turn into a bump forum sometime back?

---

### Post by nothingspecial on 2010-02-12
No, it`s an intelligent, focused, adult discussion.


Maybe you wouldn`t recognize one ;):D

:p

---

### Post by nothingspecial on 2010-02-12
> **texaswriter said:**
> Did this turn into a bump forum sometime back?

Sorry, I see what you mean now.

You need [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=520091")

---

### Post by texaswriter on 2010-02-12
> **nothingspecial said:**
> Sorry, I see what you mean now.

You need [[COLOR=Magenta]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=520091")

KEK, I know wut i'm talking about... 

This forum has scrolled fast... but not anywhere near as fast as the bump forum.

---

### Post by nothingspecial on 2010-02-12
So where are you hiding.....


....I can`t find anyone.

I`ve looked behind the wardrobe, under the table, behind the door....

...I`ve not checked the sheets yet or behind the lamp??

---

### Post by Kai69 on 2010-02-12
Ive been hiding behind my toolbox so management cant see me :p

---

### Post by audiomick on 2010-02-12
I tried to hide behind the cat, but he keeps looking at me funny and moving.

---

### Post by Kai69 on 2010-02-12
:lolflag:

---

### Post by willowave on 2010-02-12
> **audiomick said:**
> I tried to hide behind the cat, but he keeps looking at me funny and moving.
 Just don't grab his tail when he moves. they get real irritated at that. Ask my 2 yr old. (almost 2 anyways)

---

### Post by willowave on 2010-02-12
I'm going to try a dual boot of linux and xp, but with linux installed first. 
Thanks to Netflix. Jerks don't support linux.

---

### Post by warfacegod on 2010-02-12
> **willowave said:**
> I'm going to try a dual boot of linux and xp, but with linux installed first. 
Thanks to Netflix. Jerks don't support linux.

Don't be surprised if you break GRUB doing it.

---

### Post by willowave on 2010-02-13
> **warfacegod said:**
> Don't be surprised if you break GRUB doing it.
well I have a how-to here that says if you back up grub, and then using one of the usb live thingys, rewrite the mbr back to grub, it will work. 
I installed windows inside virtualbox but netflix skips inside there. so thats pointless. 
so...figuring I really have nothing to lose really.

---

### Post by mhgsys on 2010-02-13
> **willowave said:**
> well I have a how-to here that says if you back up grub, and then using one of the usb live thingys, rewrite the mbr back to grub, it will work. 
I installed windows inside virtualbox but netflix skips inside there. so thats pointless. 
so...figuring I really have nothing to lose really.

So that and some mapping, and your back to boredom with your dual boot

---

### Post by willowave on 2010-02-13
Yep. Thanks to Netflix. I could do without windows, but of course they won't let me. I wish there was another way around it.
I have a sneaking suspicion that I'm going to botch up grub. At least enough that I can't get to my XP.
If I want to get rid of some of the items on grub...do I just # them out?

---

### Post by nothingspecial on 2010-02-13
Do without netflix.

---

### Post by willowave on 2010-02-13
> **nothingspecial said:**
> Do without netflix.
thats just a silly suggestion.

---

### Post by nothingspecial on 2010-02-13
Well I do without toohpicks.

I don`t actually know what netflix is.

Is it a subuteo derivative?

---

### Post by willowave on 2010-02-13
> **nothingspecial said:**
> Well I do without toohpicks.
 
I don`t actually know what netflix is.
 
Is it a subuteo derivative?
lol no, it's a movie web site I subscribe to where you can watch movies online or also have them sent to you in the mail. 
[www.netflix.com]("http://www.netflix.com")
and if you do without toothpicks I hope you have dental floss.lol

---

### Post by warfacegod on 2010-02-13
Hi, kids, I'm here.

---

### Post by Kai69 on 2010-02-13
Hows the minimal install going?

---

### Post by willowave on 2010-02-14
*grumblegrumblegrumblegrumble*
grub 2. no menu.lst
not meant to be edited???
pffft.

---

### Post by willowave on 2010-02-14
maybe I'll just uninstall grub 2, install windows....then...reinstall grub 2 again. 
or old grub.
grub grub grub.
woo hoo!! I think I'm losing it.

---

### Post by willowave on 2010-02-14
I'm going to keep posting til I get a new page. I'm tired of looking at all of my own posts.

---

### Post by willowave on 2010-02-14
uninstalled grub2, reinstalled old grub. and I've got nearly nothing in my boot menu. which is ok I guess.

---

### Post by cariboo on 2010-02-14
I could make this thread go away. :)

---

### Post by audiomick on 2010-02-14
> **willowave said:**
> uninstalled grub2, reinstalled old grub. and I've got nearly nothing in my boot menu. which is ok I guess.
Have you got it the way you want it now?

---

### Post by willowave on 2010-02-14
> **audiomick said:**
> Have you got it the way you want it now?
Well so far sogood. I've uninstalled grub2, reinstalled grub, and backed it up. Got my XP to my usb drive and now I'm installing XP. So it will just be a matter of ....oh hell. Maybe not. 
The usb key doesnt see any partitions except for it's own. 
Hmmm...

---

### Post by willowave on 2010-02-14
> **cariboo907 said:**
> I could make this thread go away. :)
 lol good point.

---

### Post by Satoru-san on 2010-02-14
I am surprised this thread has so many posts.

---

### Post by audiomick on 2010-02-14
Hi.
Is there a partition there that XP is capable of reading?
I should add that I have no experience with installing via USB, so I could be barking up the wrong tree...
However, I think that windows / the windows installer needs to have disk space that it is allowed to be able to recognise, i.e. empty or NTFS or something else out of the windows world.

---

### Post by willowave on 2010-02-14
> **audiomick said:**
> Hi.
Is there a partition there that XP is capable of reading?
I should add that I have no experience with installing via USB, so I could be barking up the wrong tree...
However, I think that windows / the windows installer needs to have disk space that it is allowed to be able to recognise, i.e. empty or NTFS or something else out of the windows world.
 You are right. I did have a 20 gig made into NTFS (which actually most times it will see the linux partitions it just can't read what they are) but for some reason...it's only seeing the flash drive. I even went back and deleted the partition thinking maybe it would pick it up if it was unallocated. But nope. 
SO I gave up the usb idea with XP. I just plugged in an old cranky ide dvd-r to my Eee pc. I'd still like to have a bootable xp flash drive. But I'll tackle one issue at a time.
Huh...XP can't see my Eee HD. Thats what it is. It's not the flash drive.
OK...thats weird.

---

### Post by audiomick on 2010-02-14
Weird indeed...
I don't think I am going to be much use to you. I haven't done a windows install for about 8 years....

Have you got an Ubuntu CD that you can boot into and see if that sees that drive ok?

---

### Post by willowave on 2010-02-14
wow...I dont think there is a way to get XP on here without killing linux off first. Unless I slipstream sata drivers (which I think might be why XP isn't seeing the HD) into an ISO...I try to install from my restore disk and it wants to wipe out linux not just install XP where I want it. 
I'm not sure which would be more work...slipstreaming the drivers in...burning the disk...ect...
Or just reinstalling everything.

---

### Post by willowave on 2010-02-14
> **audiomick said:**
> Weird indeed...
I don't think I am going to be much use to you. I haven't done a windows install for about 8 years....
 
Have you got an Ubuntu CD that you can boot into and see if that sees that drive ok?
 Oh yeah. Ubuntu sees everything fine. I'm pretty sure XP doesn't have the sata drivers from what I am reading.

---

### Post by audiomick on 2010-02-14
> **willowave said:**
> Oh yeah. Ubuntu sees everything fine. I'm pretty sure XP doesn't have the sata drivers from what I am reading.
That could well be, I suppose. Sata turned up well after XP, didn't it?

---

### Post by willowave on 2010-02-14
ok I need to just type this out and see if anyone can come up with a solution or at least say something that will help me figure this out.
I have a 160 gig hard drive on my Eee PC. It has a SATA drive on it so apparently I can only use the disk that came with it to install XP. I want to dual boot so I can watch netflix on it. The restore disk obviously sets up the partitions...and they look like this...
 
1)XP
2)Storage
3)PE/ghost type of thing (which I would like to keep) which also says hidden...does that mean if I wipe the disk it will stay?
 
I have tried to resize the XP partition and then install ubuntu but it tells me it cant have more than a certian amount of primary partitons. I'm not setting the drives the restore disk is.
I can't change it to logical with gparted as far as I know...without destroying the XP. Which the restore disk will just go back and rewrite it as soon as I reinstall it. If I use another XP disk it doesnt work because it doesnt have the SATA drivers. 
I was looking at slipstreaming the drivers into an iso...but not sure which ones to use. 
Is slip streaming the only way to do this if I want to get out of the restore disks way of doing things?

---

### Post by Kai69 on 2010-02-14
[http://ubuntuforums.org/archive/index.php/t-942437.html](http://ubuntuforums.org/archive/index.php/t-942437.html) This may help as for section 3, I think that may be a recovery partition you will lose it if you format the drive.

---

### Post by willowave on 2010-02-14
> **Kai69 said:**
> [http://ubuntuforums.org/archive/index.php/t-942437.html](http://ubuntuforums.org/archive/index.php/t-942437.html) This may help as for section 3, I think that may be a recovery partition you will lose it if you format the drive.
Hmm, thanks Kai. That was a good thread for me to read. I think I must just suck at searching. Everyone else always finds the good stuff.

---

### Post by audiomick on 2010-02-14
Hallo.
As far as your partitions go: According to what you have written, the XP installer has created 3. The Ubuntu installer wants to create 2, which is why your are getting messages about more than 4 primary partitions.
What you need to do is shrink whichever one you want to shrink, create an extended partition in the free space and create your Ubuntu partitions as logical partitions in the extended partition.

It is often recommended to clean out and defrag the windows partition before you start, shrink it and then start windows a couple of times to give it a chance to do any file system checks it might want to do. Having done that, you can go ahead with the Ubuntu install. In your position, I would choose the manual partitioning option during the Ubuntu install. I think you might have to anyway to make it install where you want it to in your case.

---

### Post by Kai69 on 2010-02-14
Your welcome :p Has it sorted your problem ?

---

### Post by willowave on 2010-02-14
> **Kai69 said:**
> Your welcome :p Has it sorted your problem ?
 It gave me some options to look at. I'm more curious about the partitioning issue tho.

---

### Post by willowave on 2010-02-14
> **audiomick said:**
> Hallo.
As far as your partitions go: According to what you have written, the XP installer has created 3. The Ubuntu installer wants to create 2, which is why your are getting messages about more than 4 primary partitions.
What you need to do is shrink whichever one you want to shrink, create an extended partition in the free space and create your Ubuntu partitions as logical partitions in the extended partition.
 
It is often recommended to clean out and defrag the windows partition before you start, shrink it and then start windows a couple of times to give it a chance to do any file system checks it might want to do. Having done that, you can go ahead with the Ubuntu install. In your position, I would choose the manual partitioning option during the Ubuntu install. I think you might have to anyway to make it install where you want it to in your case.
Right...but as soon as I resize the windows partition, and try to make the partition for linux in the unallocated space, it says I can't have more than 4 primary partitions. But I have no other option to make anything else but a "new" partition from it. When I click to make a "new" partition, it immediatly tells me to make an extended ect ect...but how do I do that...if its not letting me. 
It also tells me to unmark the others as primary...but I'm not real sure how to do that. I unmarked the "boot partition. Still no help.
And yes also when I tried to install Ubuntu...I tried to manually partition...gave me pretty much the same warning...too many primarys and to make an extended.

---

### Post by audiomick on 2010-02-14
Hi.
You are actually on the right track; you need to make an extended partition.
Maybe it would help to have a look here
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
particularly the section on extended partitions (link a bit lower down).

Once you have an extended partition, you can then create a large number of logical partitions inside that, I think the number is 64.

There is also a general explanation here
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by nothingspecial on 2010-02-14
Yeah, you need to make one of your primary partitions into an extended partition.

If you want  new partition.

---

### Post by audiomick on 2010-02-14
> **nothingspecial said:**
> Yeah, you need to make one of your primary partitions into an extended partition.

If you want  new partition.
I don't think so, I think there are only 3 to date, which means one primary or extended can be added. If there are already 4, then that is true.

---

### Post by willowave on 2010-02-14
See this is where I am running into ttroubles...if you look at the how-to you gave me Mick, going down to making an extended partition ( and I have not read thru the whole thing, I'll do that here but I've partitioned before...it's just been awhile)
If you look here...[https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition](https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition)
it shows where you can change it to extended or logical or primary all that...I don't have that menu, I don't get that option. when I go to (and this is in Gparted that I am using) resize the partition, I don't get the option of doing that. It gives me the option to resize...but not to change those things.
EDIT: I know I have had that option before...I'm starting to wonder if I have to start all over? and make the logicals before windows is even on there? But then that goes back to, my restore disk sets the partition tabel, I'm not getting to. So then I'm going to have to slipstream the drives cuz I can't use my restore disk?

---

### Post by warfacegod on 2010-02-14
You could skip all the hassle and have Ubuntu install without a swap partition. If you aren't going to be doing heavy video encoding, or something that is hardware intensive, you'll probably never need swap at all.

---

### Post by Woolio1 on 2010-02-14
Has this just become a general chat thread? Speaking of which, we really need a General Chat Thread here... You know, just for chatting, and not delving into other matters discussed here. 

I'll see if I can't get one of the mods to make one...

---

### Post by willowave on 2010-02-15
> **warfacegod said:**
> You could skip all the hassle and have Ubuntu install without a swap partition. If you aren't going to be doing heavy video encoding, or something that is hardware intensive, you'll probably never need swap at all.
I'd be fine with that but I can't seem to get that far. which the partitions I have from the rstore cd, even trying to make one more partiton manually in gparted (actually using parted magic) it won't let me make one more. I just wish I could go in and change some of the partitions from primary. But I'm begining to get that I can't. Once it's done it's done? I did find out that I can get rid of the other partitions, and the restore disk will restore those a well. Which is a good thing, but a bad thing because then it looks like I am back to slipstreaming those drivers to make XP work, of using the ideas in that thread that Kai posted. Changing the BIOS to read as IDE and then installing XP....drivers installled, then changing it back to ACHI to install  linux. Thanks Kai : ) It helped even more than I realized. 
So I think I have a solution to my problem, it's just picking which one I want to use. 
I like the idea of using nlite to get the setup I need for the Eee so I can have that handy in case XP does its usual thing. I just need to figure out exactly which drivers I need. Which isn't small task there. 
This is alot of work just to watch movies. lol

---

### Post by willowave on 2010-02-15
> **Woolio1 said:**
> Has this just become a general chat thread? Speaking of which, we really need a General Chat Thread here... You know, just for chatting, and not delving into other matters discussed here. 
 
I'll see if I can't get one of the mods to make one...
I think this has become the "Help Angie with whatever mess she gets herself into that day" thread. Do they have one of those? Cuz they should.
Hey warface, look. I hijacked your thread again. lol

---

### Post by audiomick on 2010-02-15
Hi.
Once more from the top to get it clear for me...;) The last lot of partitioning I did was about 4 weeks ago, but the time before was 2 years previously,  so I don't actually have it all that fresh in my mind.

Firstly, you know you can't operate on a partition that is mounted, don't you? For this reason, I like to use the Ubuntu live CD or a gparted live CD. How are you going about it? You have mentioned gparted, but also parted magic, which I am not familiar with. Which one are you using, and are you working from some sort of live environment, or booted into an install? Is it possible that the partition you are trying to work on is mounted?

From what you have written, I gather you can see the option to resize, but not to create new. Is this right?
Gparted is not all that smart; you have to do things one step at a time. In this case, if I have understood you right, Resize then apply. This should give you unallocated space. In this space, create an extended, apply. Inside the extended, create the Ubuntu partitions, apply.

As far as the advice from Kai about those drivers goes, I can't advise you there; it is outside my experience.

In answer to your question
 > But I'm begining to get that I can't. Once it's done it's done?
no, this is not the case. All things being equal, you can always alter your partitioning. Whatever is stopping you is not any kind of fundamental limitation, as far as I know.

---

### Post by willowave on 2010-02-15
> **audiomick said:**
> Hi.
Once more from the top to get it clear for me...;) The last lot of partitioning I did was about 4 weeks ago, but the time before was 2 years previously, so I don't actually have it all that fresh in my mind.
 
Firstly, you know you can't operate on a partition that is mounted, don't you? For this reason, I like to use the Ubuntu live CD or a gparted live CD. How are you going about it? You have mentioned gparted, but also parted magic, which I am not familiar with. Which one are you using, and are you working from some sort of live environment, or booted into an install? Is it possible that the partition you are trying to work on is mounted?
 
From what you have written, I gather you can see the option to resize, but not to create new. Is this right?
Gparted is not all that smart; you have to do things one step at a time. In this case, if I have understood you right, Resize then apply. This should give you unallocated space. In this space, create an extended, apply. Inside the extended, create the Ubuntu partitions, apply.
 
As far as the advice from Kai about those drivers goes, I can't advise you there; it is outside my experience.
 
In answer to your question
 
no, this is not the case. All things being equal, you can always alter your partitioning. Whatever is stopping you is not any kind of fundamental limitation, as far as I know.
 ok...well thats good to know (that last part). I am using a live cd, I've used both ubuntu live and this parted magic which is pretty much gparted and a bunch of other partitioning /disk tools. I like it. 
so I am going to try what you said..making the resize and then applying...maybe I'll restart just to be safe too. I think I have done this once already. But I'll do it again just so we can rule it out if it doesn't work. 
My poor little hard drive.

---

### Post by nothingspecial on 2010-02-15
Your hard drive maybe glad of the attention?

---

### Post by warfacegod on 2010-02-15
> I think this has become the "Help Angie with whatever mess she gets herself into that day" thread. Do they have one of those? Cuz they should.
Hey warface, look. I hijacked your thread again. lol

So I'd noticed.

---

### Post by willowave on 2010-02-15
Do you think they'd get rid of my thread if I named it that? lol

---

### Post by warfacegod on 2010-02-15
> **willowave said:**
> Do you think they'd get rid of my thread if I named it that? lol

Not if it's in the cafe.

---

### Post by willowave on 2010-02-15
Well I got my issue sorted. I just deleted all the other partions, because I found that the restore disk will restore even the PE partition (that I was concerned I needed to keep)
So I've just deleted everything but the XP I installed, and then moved that to the back of the HD and making an extended partition to the front.
I thought you guys were "jumping ship" so I didn't think you'd mind if i borrowed your thread. lol

---

### Post by nothingspecial on 2010-02-15
Remember the iPod?

---

### Post by willowave on 2010-02-15
> **nothingspecial said:**
> Remember the iPod?
 LOL yep, did you put it in rice???

---

### Post by nothingspecial on 2010-02-15
No, I only had sticky rice, but I dried it out.

It doesn`t work as an Ipod but does work as a removable hard drive, so I`ve got a spare 80 gig hard drive....

should I try and put an operating system on it?

Or should I just chuck it?

---

### Post by willowave on 2010-02-15
> **nothingspecial said:**
> No, I only had sticky rice, but I dried it out.
 
It doesn`t work as an Ipod but does work as a removable hard drive, so I`ve got a spare 80 gig hard drive....
 
should I try and put an operating system on it?
 
Or should I just chuck it?
 I'd put an OS on it...you might still be able to use it as a mp3 player if you can get a OS on it.

---

### Post by nothingspecial on 2010-02-15
Good point :D

I`m going to the butchers to get a couple of rib eye steaks for dinner.

yum yum

Catch you later ;)

---

### Post by audiomick on 2010-02-15
@nothingspecial
you could have a go at this
[http://www.rockbox.org/](http://www.rockbox.org/)
although I suspect that if it doesn't work now, that wont bring much either.
Can you pull those things apart? Might be worth looking inside to see if there is any residue anywhere that might be giving it a problem. Or suspicious scorch marks...

---

### Post by willowave on 2010-02-15
You know the sticky rice will work. Thats what I put my phone in. It's a little more annoying cuz it kind of sticks to where the water was at. But it still works. I had to leave my phone in it for a few days before it worked completely. I'm surprised the iPod would die that badly after just being in the sauna. Tho I suppose it depends on how long it was in there.

---

### Post by audiomick on 2010-02-15
> **willowave said:**
>  after just being in the sauna. Tho I suppose it depends on how long it was in there.
Might have been the heat that killed it too. Particularly if he put it down on the hot stones...;)

---

### Post by willowave on 2010-02-15
lol I would hope he didnt put it on the hot stones. 
Well warface can have his thread back. I've got my Eee PC set up just perfect. Now I think I am going to clone the whole disk....er....I need to figure out how clonezilla works.

---

### Post by nothingspecial on 2010-02-15
The iPod was in there for about 40 mins

I hit the cold plunge a few times during the process.

Thing is it worked throughout the sauna, just the next time I tried to use it, no no.

---

### Post by audiomick on 2010-02-15
> **nothingspecial said:**
> The iPod was in there for about 40 mins

I hit the cold plunge a few times during the process.

Thing is it worked throughout the sauna, just the next time I tried to use it, no no.
Ah ha! What happens  is that the damp inside condenses as the device cools and leaves water inside. We tend to leave PA systems on overnight on outdoor jobs for that reason.
It still might dry out if you leave it long enough or open it.

---

### Post by themarker0 on 2010-02-15
Dellls are crap. On my craptop (A laptop consisting of like 3 different ones...) I have a dell screen. Breaks weekly, No aparrent reason. I don't understand how they are the only company that sells Ubuntu.

---

### Post by willowave on 2010-02-15
> **themarker0 said:**
> Dellls are crap. On my craptop (A laptop consisting of like 3 different ones...) I have a dell screen. Breaks weekly, No aparrent reason. I don't understand how they are the only company that sells Ubuntu.
 well thats good to know.

---

### Post by Woolio1 on 2010-02-15
> **themarker0 said:**
> Dellls are crap. On my craptop (A laptop consisting of like 3 different ones...) I have a dell screen. Breaks weekly, No aparrent reason. I don't understand how they are the only company that sells Ubuntu.

I've used only dells for the past five years.. Never had a hardware failure... Right now, I'm using one of their 1080p screens, not broken. Before, I used a 720p LCD screen, never failed. I've had two Dell boxes, never broke. 

Dells are pretty reliable here. Not sure if it's the same everywhere, though.

---

### Post by audiomick on 2010-02-15
glad I didn't buy one then. I thought about it, then bought an MSI instead. 300 Euros less for similar specs, and it's got hotrod flames on it!
[ATTACH]147181[/ATTACH][ATTACH]147180[/ATTACH]

---

### Post by Kai69 on 2010-02-15
> **audiomick said:**
> glad I didn't buy one then. I thought about it, then bought an MSI instead. 300 Euros less for similar specs, and it's got hotrod flames on it!
[ATTACH]147181[/ATTACH][ATTACH]147180[/ATTACH]

Whats it like missus is looking at getting a new lappy this year and saw an MSI and likes the look of them but didnt know the make,
Im looking at getting a netbook either a eee pc or MSI for work Im going to use it for Diagnostics.

---

### Post by audiomick on 2010-02-15
Hallo Kai.
the company is in Frankfurt am Main. Site is here
[http://www.msi-computer.de/index.php](http://www.msi-computer.de/index.php)

The laptop was sold as a gamer's laptop. It is, as I mentioned, fast for the price. It doesn't appear to be as sturdily built as the Toshiba I had before it, but the price has to come from somewhere, doesn't it? I am pretty happy with it so far. I got a mouse with it that is great, except that it is right handed and I have gotten into the habit of using the mouse left handed because I use the number block a lot. About the most annoying thing about it is that the button to open the CD drive is right where you grab it to pick it up, so when I move it, about half the time I end up with the CD drawer open.
The keyboard feels ok, but if you press hard it gives a bit. I think I need to treat it well, but that it will last ok.
Their netbooks, wind I think they are called, aren't they, have been getting reasonable reviews here, I think.

The main board in my desktop is also from MSI.

---

### Post by Kai69 on 2010-02-15
Hi Audiomick  It still looks like a nice lappy as for sturdyness the lappy we brought for the kids is also a little flimsy in feel but so far has held up well Advent Roma 3000. Im just waiting for the new prossesors to come out for the netbooks later this year before I get a netbook [http://news.cnet.com/8301-17938_105-10347141-1.html](http://news.cnet.com/8301-17938_105-10347141-1.html) .

---

### Post by audiomick on 2010-02-15
> **Kai69 said:**
>  Im just waiting for the new processors to come out for the netbooks later this year before I get a netbook [http://news.cnet.com/8301-17938_105-10347141-1.html](http://news.cnet.com/8301-17938_105-10347141-1.html) .
That looks interesting. But at some point you have to stop reading the news and just buy something, or you will be waiting for the development that is "just around the corner" for ever. And when you have bought something, you don't dare look at new product news for at least 2 years, or you will only get depressed.;)

---

### Post by Kai69 on 2010-02-15
> **audiomick said:**
> That looks interesting. But at some point you have to stop reading the news and just buy something, or you will be waiting for the development that is "just around the corner" for ever. And when you have bought something, you don't dare look at new product news for at least 2 years, or you will only get depressed.;)
  
LOL Nah I was thinking at Xmas about getting a netbook thats when I found out about the new cpu so I thought Id wait most of the shops are still selling netbooks with the old cpu but try and get a discount haha Im also still trying to sort out my diagnostic cable and software most companys want to sell the laptop as well no thanks. We use Snap-on Modis at work but as the unit is about £6000 they wont let me take it home which is understandable. 
Not only that I found ubuntu has a digital osiliscope in software center so im going to have a look at that as well , Its amazing what is in OSS .

---

### Post by Zoot7 on 2010-02-15
Talking of stupid things to do, one thing to do is to add absolutely every obscure repository you can find on the internet housing deb packages to your sources.list and have apt pull down packages from each and every one. You'll be in dependency hell in no time at all. :)

Or why not try maybe fetching the source for a totally different package manager like yum or zypper and seeing if you can have either work side by side with apt.

---

### Post by audiomick on 2010-02-15
> **Kai69 said:**
> 
Not only that I found ubuntu has a digital oscilloscope in software center so im going to have a look at that as well , Its amazing what is in OSS .
I don't really have a use for that, but I think I need to look at it anyway....;)

---

### Post by Kai69 on 2010-02-15
Zoot7 I was wondering what would happen if I installed everything from synaptic package manager :lolflag:
Audiomick We use scopes for a lot of testing on cars these days things like ABS sensors Lambda probes , Can bus etc I have a small fault code reader that I use at home, the amount of times i have someone ask about why the engine management light is on I can check and clear faults in less than 5 mins LOL  But with a scope I can see the signal that the ecu is seeing. :p

---

### Post by audiomick on 2010-02-15
> **Kai69 said:**
> Can bus etc 
You will like this.
This
[http://www.dbaudio.com/de/systems/remote/](http://www.dbaudio.com/de/systems/remote/)
runs on Can bus.:p
Slow, but solid as a rock...

---

### Post by willowave on 2010-02-15
> **Kai69 said:**
> LOL Nah I was thinking at Xmas about getting a netbook thats when I found out about the new cpu so I thought Id wait most of the shops are still selling netbooks with the old cpu but try and get a discount haha Im also still trying to sort out my diagnostic cable and software most companys want to sell the laptop as well no thanks. We use Snap-on Modis at work but as the unit is about £6000 they wont let me take it home which is understandable. 
Not only that I found ubuntu has a digital osiliscope in software center so im going to have a look at that as well , Its amazing what is in OSS .
 
I have an Eee PC. the 1005HA. I like it quite a bit, altho if I used it more I would wish I had the 12 inch screen instead of the 10 inch. If your wife will use it alot, not just as an email checker, I'd get the bigger screen.

---

### Post by Zoot7 on 2010-02-15
> **Kai69 said:**
> Zoot7 I was wondering what would happen if I installed everything from synaptic package manager :lolflag:
How about uninstalling apt and everything to do with it? ;)

---

### Post by Kai69 on 2010-02-15
NICE But try finding a fault in 1 of 52 ecu's in a modern car lol bit of head scratching The last I heard Mercedes had one with 250 ecu's in it :p

---

### Post by audiomick on 2010-02-15
> **Zoot7 said:**
> How about uninstalling apt and everything to do with it? ;)
A genius in our midst....:p

@Kai
don't talk to me about Daimler. I did their Aktionaires Hauptversammlung for about 9 years in a row, and various other events. Result: I will never buy a Mercedes. Ever.;)

---

### Post by Kai69 on 2010-02-15
Same here ive seen the rust on these cars ill stick with VW :p

---

### Post by willowave on 2010-02-15
Whats the best music player for ubuntu?

---

### Post by audiomick on 2010-02-15
> **willowave said:**
> Whats the best music player for ubuntu?
You've got questions! There's only about 17 squillion to chose from....;)
I don't know really, but I see a lot of references to Rhythmbox, and I think Mplayer is ok, although it is really a movie player.

---

### Post by Kai69 on 2010-02-15
Im using Rythumbox but I hate the way it moves some of my tracks around thats the only thing I miss from windows their player I could see my album covers click on it and see all the tracks from that album in rythumbox it may be in differant places very annoying.

---

### Post by willowave on 2010-02-15
> **audiomick said:**
> You've got questions! There's only about 17 squillion to chose from....;)
I don't know really, but I see a lot of references to Rhythmbox, and I think Mplayer is ok, although it is really a movie player.
 I know! Isn't that how a person learns? :D

---

### Post by warfacegod on 2010-02-15
> **willowave said:**
> Whats the best music player for ubuntu?

Amarok 1.4

---

### Post by warfacegod on 2010-02-15
I got this from a script from another thread. I never got the script to work properly so I do each step manually and I took out the packages that don't exist anymore.



```
Step .01   Installing dependencies

sudo apt-get install kdelibs4-dev libxine-dev libdbus-qt-1-dev libtag1-dev libsqlite3-dev libtunepimp-dev libmysqlclient15-dev libpq-dev libvisual-0.4-dev libsdl1.2-dev libifp-dev libusb-dev  libnjb-dev ruby ruby1.8-dev  x11proto-core-dev automake libtool libxine1 libxine1-ffmpeg build-essential

Step .02

sudo apt-get install ruby-dev libtag1-dev qt4-dev-tools qt3-dev-tools kdelibs4-dev x-dev libxine1

Step .03   Installing iPod Support dependencies (Optional)

sudo apt-get install libgpod-common libgpod4 libgpod-dev gtkpod
cd ~/Downloads

Step .04

wget http://bugs.kde.org/attachment.cgi?id=32838 -O amarok-1.4.10-gcc44.patch
patch -p1 < amarok-1.4.10-gcc44.patch

Step .05

http://mail.kde.org/pipermail/amarok/attachments/20090822/52116f4a/attachment-0001.dll -O covermanager-fix.patch
patch -p1 < covermanager-fix.patch

Step .06

wget http://launchpadlibrarian.net/34885946/99_fix_wikipedia_lookup.patch -O wikipedia-lookup.patch
patch -p1 < wikipedia-lookup.patch

Step .07

sed 's/return " (band)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
sed 's/return " (Band)";/return "";/g' amarok/src/contextbrowser.cpp.tmp > amarok/src/contextbrowser.cpp

sed 's/return " (album)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
mv amarok/src/contextbrowser.cpp.tmp amarok/src/contextbrowser.cpp

sed 's/return " (song)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
mv amarok/src/contextbrowser.cpp.tmp amarok/src/contextbrowser.cpp

Step .08

./configure --without-arts

Step .09

make

Step .10

sudo make install

Step .11

rm -r ~/Downloads/amarok*
```

---

### Post by willowave on 2010-02-15
holy crap...what does that all do?

---

### Post by warfacegod on 2010-02-16
It will compile Amarok 1.4 which is necessary because it is no longer supported. The Amarok 2 series is absolute garbage so I use the older version. It installs iPod support, a patch for album art, and some lookups for band info on Wikipedia.

---

### Post by Zoot7 on 2010-02-16
> **audiomick said:**
> A genius in our midst....:p
:lolflag:

---

### Post by nothingspecial on 2010-02-16
Try the music player in my sig.

It`s a work in progress and being heavily developed as we speak. You can comment, make feature requests, report problems and the developer _will_ respond.

If you ever wanted to get involved in open source software, this is your perfect opportunity.

.....uninstall apt....you`re tempting me.:P

[SIZE="5"][COLOR="Red"]WARNING !!!!!

THE NEXT FEW POSTS IN THIS THREAD CONTAIN CODE THAT WILL COMPLETELY DESTROY YOUR SYSTEM[/COLOR][/SIZE]

Do not copy and paste random bits of code into your terminal from the internet unless you understand what they do. Thankyou.

---

### Post by Zoot7 on 2010-02-16
Come to think of it another really stupid thing to do would be to remove python entirely when I gather most of the desktop apps depend on it. :)

EDIT:
> **nothingspecial said:**
> .....uninstall apt....you`re tempting me.:P
```
aptitude purge $( dpkg -l | grep apt | awk '{print $2}' | xargs )
```

;)

---

### Post by warfacegod on 2010-02-16
> **Zoot7 said:**
> Come to think of it another really stupid thing to do would be to remove python entirely when I gather most of the desktop apps depend on it. :)

EDIT:

```
aptitude purge $( dpkg -l | grep apt | awk '{print $2}' | xargs )
```

;)

I'd venture a guess to say you'd need to sudo this command.

---

### Post by audiomick on 2010-02-16
> **warfacegod said:**
> I'd venture a guess to say you'd need to sudo this command.
Well, try it and find out...;)
(better your box than mine :) )

---

### Post by nothingspecial on 2010-02-16
Here goes my testing partition.....

.....again!

---

### Post by nothingspecial on 2010-02-16
Actually I`m don`t think I`m going to bother
```

$ sudo aptitude purge $( dpkg -l | grep apt | awk '{print $2}' | xargs )
[sudo] password for rob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  command-not-found gstreamer0.10-plugins-bad-multiverse libept0 librasqal1 librdf0 ppp python-software-properties 
  software-properties-gtk tasksel tcpdump ubufox ubuntu-minimal ubuntu-standard unattended-upgrades update-manager-core 
  update-notifier-common xserver-xorg-input-all 
The following packages will be REMOVED:
  apt{p} apt-transport-https{p} apt-utils{p} apt-xapian-index{p} aptitude{p} apturl{p} apturl-common{p} laptop-detect{p} 
  libmjpegtools-1.9{p} libpcap0.8{p} libraptor1{p} python-apt{p} synaptic{p} xserver-xorg-input-synaptics{p} 
0 packages upgraded, 0 newly installed, 14 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 27.2MB will be freed.
The following packages have unmet dependencies:
  librdf0: Depends: libraptor1 (>= 1.4.19) but it is not installable
  python-software-properties: Depends: python-apt (>= 0.6.20ubuntu16) but it is not installable
  ubuntu-standard: Depends: aptitude but it is not installable
  ubufox: Depends: apturl (>= 0.1.2ubuntu1) but it is not installable or
                   apturl-kde but it is not installable
  command-not-found: Depends: python-apt but it is not installable
  update-manager-core: Depends: python-apt (>= 0.7.5) but it is not installable
  update-notifier-common: Depends: python-apt (>= 0.6.12) but it is not installable
  gstreamer0.10-plugins-bad-multiverse: Depends: libmjpegtools-1.9 (>= 1:1.9.0) but it is not installable
  librasqal1: Depends: libraptor1 (>= 1.4.16) but it is not installable
  tcpdump: Depends: libpcap0.8 (>= 1.0.0-1) but it is not installable
  xserver-xorg-input-all: Depends: xserver-xorg-input-synaptics but it is not installable
  libept0: Depends: libapt-pkg-libc6.10-6-4.8 which is a virtual package.
  unattended-upgrades: Depends: python-apt (>= 0.7.9) but it is not installable
                       Depends: apt-utils (>= 0.7) but it is not installable
                       Depends: apt (>= 0.7) but it is not installable
  ubuntu-minimal: Depends: apt but it is not installable
                  Depends: apt-utils but it is not installable
  ppp: Depends: libpcap0.8 (>= 1.0.0-1~exp1) but it is not installable
  tasksel: Depends: apt (>= 0.6.45ubuntu14) but it is not installable
           Depends: aptitude (>= 0.2.15-1) but it is not installable
  software-properties-gtk: Depends: synaptic (>= 0.57.8) but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
command-not-found
gstreamer0.10-plugins-bad-multiverse
language-support-en
language-support-writing-en
librasqal1
librdf0
openoffice.org
openoffice.org-base
openoffice.org-base-core
openoffice.org-calc
openoffice.org-core
openoffice.org-draw
openoffice.org-hyphenation-en-us
openoffice.org-impress
openoffice.org-math
openoffice.org-officebean
openoffice.org-report-builder-bin
openoffice.org-thesaurus-en-us
openoffice.org-writer
ppp
pppconfig
pppoeconf
python-software-properties
software-properties-gtk
tasksel
tasksel-data
tcpdump
ubufox
ubuntu-minimal
ubuntu-standard
unattended-upgrades
update-manager-core
update-notifier-common
xserver-xorg-input-all

Keep the following packages at their current version:
apt [0.7.23.1ubuntu2 (karmic, now)]

Leave the following dependencies unresolved:
byobu recommends update-notifier-common
debconf recommends apt-utils (>= 0.5.1)
friendly-recovery recommends update-manager-core (>= 0.90.0)
python-debian recommends python-apt
ubuntu-restricted-extras recommends gstreamer0.10-plugins-bad-multiverse
firefox-3.5 recommends ubufox
Score is 83265

Accept this solution? [Y/n/q/?]
```

---

### Post by warfacegod on 2010-02-16
> **audiomick said:**
> Well, try it and find out...;)
(better your box than mine :) )

Nope.

My experiment drive is now my main OS for the moment. I've been playing with Linux Mint, Linux Mint Fluxbox, and Dream Linux. Of the three, Fluxbox was the most visually pleasing and seemed to be the lightest on my hardware. Unfortunately, it does not install to a hard drive with the same visual appeal as it has running from a LiveUSB. Installed, it has a very Windows 2000ish look to it. Nor does it even behave the same way.

Linux Mint installed just fine but then refused to start properly. It won't get past some flickering text for splash right after GRUB.

Dream Linux refuses to install in any other way besides wiping my entire hard drive.

---

### Post by audiomick on 2010-02-16
hmmm, frustrating! A pity really, that stuff all looks interesting.

---

### Post by nothingspecial on 2010-02-16
> **warfacegod said:**
> Nope.


I did in the end.

Just a matter of building apt from source to recover. 

No problems yet.

---

### Post by Zoot7 on 2010-02-16
> **warfacegod said:**
> I'd venture a guess to say you'd need to sudo this command.
Indeed! I hardly ever use sudo myself though. :p

> **nothingspecial said:**
> Actually I`m don`t think I`m going to bother
<snip>
Try using apt-get instead of aptitude. ;)

---

### Post by nothingspecial on 2010-02-16
I already did it and rebuilt apt from source. Much easier than trying to recover from

```
find ./ -type f -exec mv '{}' ./ \;
```

issued from / ;)

---

### Post by Zoot7 on 2010-02-16
> **nothingspecial said:**
> I already did it and rebuilt apt from source. Much easier than trying to recover from

```
find ./ -type f -exec mv '{}' ./ \;
```

issued from / ;)
Haha, so it's actually possible to recover from uinstalling the package manager. And yeah executing that has got to be one of the most stupid things possible to do in Linux. :)

EDIT:
Another thing I tried recently was this:
```
mkfs.ext3 -L "OH_NO" $(df -h | awk '{print $1}' | xargs | awk '{print $2}')
```
But sadly there's a lock on formating a partition while it's mounted, I wonder would dd work? :lol:

---

### Post by nothingspecial on 2010-02-16
Not just possible but quite easy really

```
454  sudo aptitude purge $( dpkg -l | grep apt | awk '{print $2}' | xargs )
  455  cd /var
  456  ls
  457  cd cache/
  458  ls
  459  cd apt
  460  ls
  461  cd archives/
  462  ls
  463  sudo dpkg -i apturl-common_0.4.1ubuntu2_all.deb 
  464  ls | grep python-apt
  465  bzr branch http://bzr.debian.org/apt/debian-sid apt-debian-sid
  466  cd
  467  tar -xvf apt_0.7.25.3.tar.gz 
  468  cd apt-0.7.25.3/
  469  ls
  470  ./configure 
  471  make
  472  sudo make install
  473  ls
  474  cat COMPILING 
  475  ls
  476  cat README.make 
  477  ls
  478  sudo apt-get install -f
  479  sudo apt-get install aptitude
  480  sudo apt-get install   command-not-found gstreamer0.10-plugins-bad-multiverse libept0 librasqal1 librdf0 ppp python-software-properties 
  481  sudo apt-get install -f
  

```

---

### Post by nothingspecial on 2010-02-16
> **Zoot7 said:**
>  I wonder would dd work? :lol:

You can try that one :D

I`ve done all my doing something stupid experimentation for the day.

---

### Post by Zoot7 on 2010-02-16
> **nothingspecial said:**
> Not just possible but quite easy really

Ah that's a shame, you'd right to have removed dpkg and everthing to do with it too! :D

> **nothingspecial said:**
> You can try that one :D

I`ve done all my doing something stupid experimentation for the day.
Indeed I will. :p

Actually for the record **rm -rf /** run as root doesn't work in Ubuntu, there's a lock on it, but **rm -rf /*** does.

---

### Post by nothingspecial on 2010-02-16
Make sure you use the -v flag so you can _see_ it disappear before your eyes.

---

### Post by Zoot7 on 2010-02-16
Okay I ran
```
dd if=/dev/zero of=/dev/sda
```

The result was sort of similar to what I got when I pulled the hard drive out while the OS was running a while back.
The images and icons all disappear.
I get a weird error message consisting of null characters.
Command after command stops working in the terminal.
The panel disappears, and after a while so does the terminal. 
I was eventually left with a brown desktop and a frozen mouse pointer.

I don't think one can come back from this. :)

---

### Post by nothingspecial on 2010-02-16
> **Zoot7 said:**
> Okay I ran
```
dd if=/dev/zero of=/dev/sda
```

The result was sort of similar to what I got when I pulled the hard drive out while the OS was running a while back.
The images and icons all disappear.
I get a weird error message consisting of null characters.
Command after command stops working in the terminal.
The panel disappears, and after a while so does the terminal. 
I was eventually left with a brown desktop and a frozen mouse pointer.

I don't think one can come back from this. :)

Nope...... reinstall.

---

### Post by Zoot7 on 2010-02-16
Writing zeros to the hard drive destroying the MBR, the partition table, and filesystem and everything else while the OS itself is running is a feat in itself. Breakage doesn't get any more extreme. :)

---

### Post by nothingspecial on 2010-02-16
> **Zoot7 said:**
> Writing zeros to the hard drive destroying the MBR, the partition table, and filesystem and everything else while the OS itself is running is a feat in itself. Breakage doesn't get any more extreme. :)

I salute you.  :p

---

### Post by nothingspecial on 2010-02-16
I can`t remember alot of what happened when I ran that find command, but I do remember something like

```
help -- you have no username!
```

or words to that effect. I`d say try it but I don`t suppose you can at the moment. And I`m hoping, like me, you have a testing partition, or machine and didn`t nuke your main system.

---

### Post by Kai69 on 2010-02-16
You lot are NUTS :lolflag: Can I ask what does happen when you use one of the dangerous code like rm-f/ or whatever it is ?

---

### Post by nothingspecial on 2010-02-16
```
dd if=/dev/zero of=/dev/sda
```

Will completely destroy any data on your main partition. Everything gone.```


rm -rf /*
```

rm is the remove/delete command. -r means go down through all directories contained in the directory you specify.

f means don`t ask questions just do it.

/ means the root directory, as in the parent directory of everything ( so the -r means everything)

* means everything

```
find ./ -type f -exec mv '{}' ./ \;
```

find is pretty obvious

./ means in this directory (find defaults to going down through all the child directories)

-type f (file - so find any file contained within / and all it`s child directories)

- exec means execute the following command

mv means move

'{}' do it to everything find found

./ means here (or the directory you are in)

So that command will move every file contained within any/every folder in the root directory and dump them in the root directory.

For example, if you have a Photos directory with folders 2010, 2009 & 2008 in it. And they are all full of .jpgs - if you issued that command from Photos then 2010, 2009 & 2008 would be empty and all the .jpgs would be in Photos.

---

### Post by Kai69 on 2010-02-16
Thanks I managed to get hold of a copy of Linux Bible 2008 ed 891 pages its heavy going and it bores me to tears but im trying my best to understand it.:D

---

### Post by nothingspecial on 2010-02-16
> **Kai69 said:**
> Thanks I managed to get hold of a copy of Linux Bible 2008 ed 891 pages its heavy going and it bores me to tears but im trying my best to understand it.:D

I`m not suggesting this is a good way of doing things---------but

I have a seperate partition with another install on it that I use to test stuff.

Don`t get me wrong 99% of the time I do low risk stuff, but occasionaly a command that will completely hose your system interests me and I like to see if I can recover from it.

The dd and find one afaik are unrecoverable from.

---

### Post by Kai69 on 2010-02-16
See this is the thing in windows you dont do stuff like this. Ive been using linux now since Nov 09 never used it before and the amount of times Ive broken linux and fixed it amazes me its just so easy and quick to reinstall and adjust partitions Never did anything like this with windows because it takes so long to install messing with drivers and such. Im enjoying the freedom and expirence to do all this so far ive tried 9.04 ubuntu, Kubuntu, NBR, Mint, at the moment ive got 9.10 and edubuntu on here next Im thinking of Slackware LOL :p

---

### Post by SteveHillier on 2010-02-16
I have enjoyed this thread so far but I am not sure if I have the time to read all 83 pages of it, however.....

> **warfacegod said:**
> You know you've had a good day when a major worldwide corporation feels the need to hang up on you.

I do like the sentiment in this quote.  I recently had a run in with Dell.  I had a customer machine in that looked quite new so armed with the service tag I phoned Dell to see if they could tell me if it was in warranty.  At the end of an hour, when they constantly refused to give me the information because I could not tell them where the machine was bought, I was told that I could look it up online.
I invoiced them for wasted time.  On the second similar event (and invoice) they phoned me up asking me to explain what the problem was.  They got it.  Both barrels.  Point blank range.  No holds barred.  and as many other mixed metaphors that I can stick together.
OK, they won't pay the invoice but at least the b....rs had to speak to me.
and one better than you warfacegod.  They didn't hang up on me, THEY PHONED me!!!

---

### Post by Kai69 on 2010-02-16
I tried to phone DELL and ask about buying the setup disks for my lappy they didnt want to know because im not the original owner I told them that I would pay £200 for the OS and driver disks they still didnt want to know just told me to download the drivers from the website ](*,)
Stevehiller  I used to live in Southend small world ESSEX BOYS LOL

---

### Post by warfacegod on 2010-02-16
> and one better than you warfacegod. They didn't hang up on me, THEY PHONED me!!!

You got me there hoss.

---

### Post by nothingspecial on 2010-02-17
Careful guys.

I wanted this to get to 1000

---

### Post by lisati on 2010-02-17
> **warfacegod said:**
> You know you've had a good day when a major worldwide corporation feels the need to hang up on you.

Or something like [this]("http://www.3news.co.nz/Telecom-SMS-abuse-hacker-or-disgruntled-employee/tabid/817/articleID/142310/Default.aspx") happens.

---

### Post by Kai69 on 2010-02-17
[willowave]("http://ubuntuforums.org/member.php?u=1004756") Did you get your HDD sorted?;)

I hung up on my boss today what a <snip>..

---

### Post by nothingspecial on 2010-02-17
> **lisati said:**
> Or something like [this]("http://www.3news.co.nz/Telecom-SMS-abuse-hacker-or-disgruntled-employee/tabid/817/articleID/142310/Default.aspx") happens.

You`re late!

---

### Post by lisati on 2010-02-17
> **nothingspecial said:**
> You`re late!

Oh? I was momentarily distracted by the disposal of a furry guest that got trapped.

---

### Post by Kai69 on 2010-02-17
> **nothingspecial said:**
> careful guys.

I wanted this to get to 1000

832

---

### Post by nothingspecial on 2010-02-17
> **lisati said:**
> Oh? I was momentarily distracted by the disposal of a furry guest that got trapped.

In that case you are excused.

:P

---

### Post by audiomick on 2010-02-17
> **lisati said:**
> Oh? I was momentarily distracted by the disposal of a furry guest that got trapped.
What sort of guests do you have? I thought there was only flightless birds there...

---

### Post by willowave on 2010-02-17
> **Kai69 said:**
> [willowave]("http://ubuntuforums.org/member.php?u=1004756") Did you get your HDD sorted?;)
 
I hung up on my boss today what a dick..
LMAO..you hung up on your boss? Thats funny. 
Yes I certianly did. I found out that it was ok to get rid of the small PE partition that the restore disk puts on it. I was concerned I wouldn't be able to restore to original if I didn't have that partition. So I removed everything and made it nice and pretty. 
Storage partition both linux and windows can see, linux, then windows for my netflix. 
So now it's perfect and I am bored as hell.

---

### Post by nothingspecial on 2010-02-17
I (and others) have given you plenty of ideas ;)

---

### Post by audiomick on 2010-02-17
> **willowave said:**
> 
So now it's perfect and I am bored as hell.
Set yourself up an experiment install before you start breaking things...;)

---

### Post by BbUiDgZ on 2010-02-17
> **nothingspecial said:**
> 

```
find ./ -type f -exec mv '{}' ./ \;
```

find is pretty obvious

./ means in this directory (find defaults to going down through all the child directories)

-type f (file - so find any file contained within / and all it`s child directories)

- exec means execute the following command

mv means move

'{}' do it to everything find found

./ means here (or the directory you are in)

So that command will move every file contained within any/every folder in the root directory and dump them in the root directory.

For example, if you have a Photos directory with folders 2010, 2009 & 2008 in it. And they are all full of .jpgs - if you issued that command from Photos then 2010, 2009 & 2008 would be empty and all the .jpgs would be in Photos.

could be pretty handy cmd with a little edit - cheers :D

---

### Post by lisati on 2010-02-17
> **nothingspecial said:**
> In that case you are excused.

:P
Thank you.
> **audiomick said:**
> What sort of guests do you have? I thought there was only flightless birds there...
I discovered a field mouse caught in a trap in one of our cupboards, and wanted to deal with it before Mrs Lisati got back from visiting one of her cousins in hospital (dialysis or something of that nature). It could have been worse. One time I'm out doing some errands, and Mrs Lisati gave me a call saying that there was a mouse in the cupboard. When I got home, I discovered that there was a mouse, still alive, with its rear end successfully trapped. Feisty little so-and-so!

---

### Post by Kai69 on 2010-02-17
[QUOTE=willowave;8842257]LMAO..you hung up on your boss? Thats funny. 

ARGH He just winds me up hasnt a clue at what hes doing I was sent out to pick up another mechanic I got there 5mins before the other mechanic so i called the boss and i just hung up Im waiting for 4pm tomorrow YIPPEE Weekend

---

### Post by nothingspecial on 2010-02-17
> **lisati said:**
> Thank you.

I discovered a field mouse caught in a trap in one of our cupboards, and wanted to deal with it before Mrs Lisati got back from visiting one of her cousins in hospital (dialysis or something of that nature).

I hope Mrs lisatis` cousin pulls through.

Sincerely

---

### Post by nothingspecial on 2010-02-17
> **BbUiDgZ said:**
> could be pretty handy cmd with a little edit - cheers :D

You don`t need to edit it.

Just do it from the appropriate directory.

---

### Post by willowave on 2010-02-17
> **audiomick said:**
> Set yourself up an experiment install before you start breaking things...;)
lol good idea. I suppose I could split my storage drive in half. I'm content to just try new distros from a usb drive tho. For now anyways. I never did get Chakra to run on usb.

---

### Post by Kai69 on 2010-02-17
> **audiomick said:**
> Set yourself up an experiment install before you start breaking things...;)

Ive got a better plan brought a new usb stick SANDISK it has U3 on it [http://en.wikipedia.org/wiki/U3](http://en.wikipedia.org/wiki/U3) It thinks it only works in windows any sugestions to getting it to work in linux ;)

---

### Post by nothingspecial on 2010-02-17
> **audiomick said:**
> Set yourself up an experiment install before you start breaking things...;)

Excellent advice.

The trouble is, once you have "an experiment install" ......you can`t help yourself.

---

### Post by nothingspecial on 2010-02-17
> **Kai69 said:**
> Ive got a better plan brought a new usb stick SANDISK it has U3 on it [http://en.wikipedia.org/wiki/U3](http://en.wikipedia.org/wiki/U3) It thinks it only works in windows any sugestions to getting it to work in linux ;)

What does ---after you`ve just plugged it in ----

```
sudo fdisk -l
```

and ```


dmesg | tail 
```

say?

---

### Post by Kai69 on 2010-02-17
Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         488     3919841    b  W95 FAT32
kai@kai-laptop:~$ dmesg | tail
[10092.285303] sd 6:0:0:0: [sdb] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[10092.288318] sd 6:0:0:0: [sdb] Write Protect is off
[10092.288327] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[10092.288333] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[10092.291036] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[10092.291040]  sdb: sdb1
[10092.294032] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[10092.294036] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[10092.998410] ISO 9660 Extensions: Microsoft Joliet Level 3
[10093.053727] ISOFS: changing to secondary root


Its a DOS program

---

### Post by nothingspecial on 2010-02-17
> **Kai69 said:**
> Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         488     3919841    b  W95 FAT32
kai@kai-laptop:~$ dmesg | tail
[10092.285303] sd 6:0:0:0: [sdb] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[10092.288318] sd 6:0:0:0: [sdb] Write Protect is off
[10092.288327] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[10092.288333] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[10092.291036] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[10092.291040]  sdb: sdb1
[10092.294032] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[10092.294036] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[10092.998410] ISO 9660 Extensions: Microsoft Joliet Level 3
[10093.053727] ISOFS: changing to secondary root

What I would try first (and bear in mind that I don`t mind breaking stuff)

is

```
sudo umount /dev/sdb1
```

```
sudo mkfs -t ext3 /dev/sdb1
```

This will, hopefully, destroy any data on that drive and make it linux compatible.

Have a look at my sig........

---

### Post by Kai69 on 2010-02-17
[attach]147391[/attach]

---

### Post by audiomick on 2010-02-17
I've no idea how to do it, but I'll bet it can be made to work. It is showing up, so there must be a good chance.

Did you follow the link on the U3 wikipedia page to this?
[http://u3-tool.sourceforge.net/](http://u3-tool.sourceforge.net/)

---

### Post by Kai69 on 2010-02-17
[http://www.everythingusb.com/u3.html](http://www.everythingusb.com/u3.html) 
If I get rid of it is there a linux version that works in windows if you got to [http://software.u3.com/SoftwareCentral.aspx?skip=1](http://software.u3.com/SoftwareCentral.aspx?skip=1) there are a lot of OSS on there .:lolflag:

---

### Post by nothingspecial on 2010-02-17
> **audiomick said:**
> I've no idea how to do it, but I'll bet it can be made to work. It is showing up, so there must be a good chance.

Did you follow the link on the U3 wikipedia page to this?
[http://u3-tool.sourceforge.net/](http://u3-tool.sourceforge.net/)

Wow, is it that bad?

Can you not just....reformat a file system anymore?

Not good.

---

### Post by nothingspecial on 2010-02-17
[http://www.everythingusb.com/u3.html](http://www.everythingusb.com/u3.html) 

Ouch!!!

As a linux only user that hurts.

Well, it doesn`t hurt, it just reinforces my prejudice to commercial computing platforms.

If you`ve ever had a job in sales you would laugh ............

---

### Post by Zoot7 on 2010-02-17
Next project, try to install a totally different package manager on a debian based distro. :)

---

### Post by Kai69 on 2010-02-17
You can use it as a normal usb stick or if you put it in a windows pc it acts as a live cd with persistance . What gets me is this is what linux has been doing for a long time put UNR on a 4gb usb with persistance  same sort of idea but U3 dosnt work in linux but UNR works in windows go figure,, So im thinking of getting this to work in linux or blast it and put linux on it and use it in windows :lolflag:

---

### Post by nothingspecial on 2010-02-17
> **Zoot7 said:**
> Next project, try to install a totally different package manager on a debian based distro. :)

Stop it.


 So yum or pkgtool or pacman etc  on ubuntu. I don`t think I can get that to work.

I might have a go though.

pacman is by far the best name though.

---

### Post by Zoot7 on 2010-02-17
> **nothingspecial said:**
> Stop it.


 So yum or pkgtool or pacman etc  on ubuntu. I don`t think I can get that to work.

I might have a go though.

pacman is by far the best name though.

I rather pkgtool the best. It'd be great if one could get pkgtool working with Debian's repositories, although that's a pipe dream methinks.

---

### Post by audiomick on 2010-02-18
> **Zoot7 said:**
> I rather pkgtool the best. It'd be great if one could get pkgtool working with Debian's repositories, although that's a pipe dream methinks.
I had a quick look in Wikipedia. It seems that pacman tracks dependencies and pkgtool doesn't.

Now what would be really interesting would be to have synaptic, pacman and something that administers .rpm all running at once and keeping each other up to date....
I am not even going to attempt that though.:p

---

### Post by willowave on 2010-02-18
And I thought I was bored.

---

### Post by bapoumba on 2010-02-18
Several posts were removed from this thread.

---

### Post by nothingspecial on 2010-02-18
Thought they might be.

---

### Post by Zoot7 on 2010-02-18
> **audiomick said:**
> I had a quick look in Wikipedia. It seems that pacman tracks dependencies and pkgtool doesn't.
Indeed it doesn't. It's both good and bad IMO, good in the sense you can forego uneeded dependencies that certain package managers pull in for certain apps that don't need them and bad in the sense when you install an app with a load of dependencies, you'll have to route all them out yourself.
Because of that I rather compile most stuff from source on Slackware, but then again I do the same on Debian.

---

### Post by Leppie on 2010-02-20
> **bapoumba said:**
> Several posts were removed from this thread.
could you also enlighten us with as to why these posts have been removed? or are we back in kinder garten?

---

### Post by Leppie on 2010-02-20
> **Zoot7 said:**
> Next project, try to install a totally different package manager on a debian based distro. :)
a long time ago i tried to install rpm, now yum (rpm front end) is in the repos...

---

### Post by warfacegod on 2010-02-20
Indeed, I wish to grok why posts were removed as well. "Off Topic" doesn't cut it, 75% of this thread is off topic.

---

### Post by bapoumba on 2010-02-20
> **Leppie said:**
> could you also enlighten us with as to why these posts have been removed? or are we back in kinder garten?
Would you prefer we silently wipe stuff out?

> **warfacegod said:**
> Indeed, I wish to grok why posts were removed as well. "Off Topic" doesn't cut it, 75% of this thread is off topic.
I'll have to manually search the Jail to find them back and remember why I moved 2 out and someone else a couple more. The ones I removed were cited in the RC thread.

To both: RC is the appropriate place for such questions, BTW.

Edit: posts were comparing the forums to some real places where real people have no freedom.

---

### Post by matthew on 2010-02-20
Stuff was moved because this, according to the Forum CoC, is a moderated forum where we have the explicit permission to move or edit posts as needed to make sure content conforms to the site rules.

[QUOTE=Forum CoC]While the administrators and moderators of this forum will attempt to remove or edit any generally objectionable material as quickly as possible where acceptable, it is impossible to review every message. Therefore you acknowledge that all posts made to these forums express the views and opinions of the author and not the administrators, moderators or web-master (except for posts by these people) and they will not be held liable.

You agree not to post any abusive, obscene, vulgar, slanderous, hateful, threatening, sexually-orientated material or any other material that may violate any applicable laws. Doing any of these may lead to you being temporarily or permanently banned from these forums (and your service provider may also be informed). 

Posts which violate any part of this Code of Conduct may be edited or moved to a special holding area called "The Jail." Posts in The Jail are only visible to staff members and the original poster. [/QUOTE]
If you have a specific question or issue with regards to *your personal post(s)*, feel free to start a discussion in the Resolution Center.

As this thread has drifted far off course, I'm going to close it now.

---

