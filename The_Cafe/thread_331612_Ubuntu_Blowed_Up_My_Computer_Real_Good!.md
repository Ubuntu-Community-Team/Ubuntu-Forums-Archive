---
title: "Ubuntu Blowed Up My Computer Real Good!"
date: 2007-01-04
forum: The Cafe
---

### Post by Babak on 2007-01-04
Ahem, now that I have your attention with that subtle (as a charging rhinocerous) thread title let me tell you of a tale...

... it was a dark and stormy night, and not a creature was stirring, not even a mouse... except for Babak (ah, that would be moi) who happened onto a youtube vid of a desktop with Sun's brand spanking new release of Looking Glass running on Ubuntu.

The keyboard was thoroughly soaked before I realized that I was drooling. I grabbed the mop with one hand and with the other I went to ubuntu.org and downloaded the ISO file to burn on a CD.

I ran Ubuntu from the CD and thought, hmm, the GUI is a bit clunky - or is that chunky? - but otherwise it is rather interesting. I wonder if I can use my vestigial 20 Gig HD. Sure it still had Windows 2000 Pro like the 80 Gig HD that I used everyday but it was for all practical purposes just lying there... So why not put it to good use, I bravely thought? why not install ubuntu on it and jump back and forth between it and Windows 2000?

Sure, Win2k was a lifelong friend but I was sure it wouldn't mind a bit of promiscuity on my part. After all, I would be running back into its arms... right? And didn't Windows 2000 already give me the choice, at boot up time, which HD I could jump into?

Surely it would do the same, or I could somehow get it to do the same once I installed Ubuntu on my 20 Gig HD, right? After all, I wasn't installing Ubuntu as a partition of my 80 Gig HD, it would be on a *completely separate* HD!

Feeling overwhelmed with warm and fuzzy feelings like only a good plan can give you I dived in... install from the live CD... why sure!

And look!!! As it is installing itself.. I   can   actually use it  --- woaaaah!! Sick man... This Ubuntu thing rocks... [kick] why didn't I do this before?

Alright, so Ubuntu installed itself snuggly in my 20 Gig HD and I'm sure it felt good for the old HD to know that it was actually useful after many years of sitting there bare, and watching in a caged jealous rage as its 80 Gig cousin took all the glory.

Everything up to that point was delightful... 

... then I restarted and thought, Hee-Hee--Heeeee [rubbing of hands] lets see the start up screen where I can choose which drive/OS to dive into...

Uh.......oh

What?

whaaa....?!?!?!

You've got to be kidding me?!?!

Where is my 80 Gig drive? Where is Windows 2000?

What's this GRUB thing?!!?

GRUB??!? get the f out of here, I want Windows 2000 !!! My lovely Windows 2000 !

I got into the forums and asked for help:
[http://ubuntuforums.org/showthread.php?t=323381](http://ubuntuforums.org/showthread.php?t=323381)


If you don't want to read through the whole painful ordeal, I'll summarize what had happened (in case you hadn't already guessed)

Ubuntu had installed on my 20 Gig HD but it had messed with my MBR on the 80 Gig HD !!

It had no reason to, but it did. Was I stupid and at fault? or was Ubuntu/GRUB? 

Well, lets look at this situation through the perspective of *USABILITY*...

In usability they have two elements: the user's mental model and the 'machine' model. When these two are different, all sorts of antics ensue.

My mental model was that since ubuntu was being installed on a separate HD my other drive would not be effected. After all, a complete HD is an entity onto itself, right? And I was giving Ubuntu free rein of the whole HD, right? What else does it want?

But, the machine model, as I've learned, was quite different! For some reason GRUB needs to or wants to, by default do something to the other HD (when you have 2 HDs as in my case).. now I know there is a way you can force GRUB to install itself on only drive containing Ubuntu but puh-lease for the love of all that is cute and pink... do you really expect people to 1)suspect this 2)find the correct solution 3)implement the solution flawlessly when it involves things like 'sudo this' 'sudo that'?

Getting back to the usability thing...in situations like this usability faults the designer of the machine (software) since it is their job to anticipate the user's mental model and work to closely match it with the machine model (something I'm told LILO does).

Now, before you think I'm here to bash Ubuntu or linux or GRUB or whatever... take a deep breath and read the following:

I have tremendous respect not only for the thousands of bright minds behind unix/linux but also for Mark Shuttleworth and the team that is working hard to make Ubuntu the best OS. This is why I'm spending my time telling my tale (I'm sure 100% this has happened to many, many others btw). 

It is my hope that after reading this feedback, the designers of the 'machine' will understand that their 'machine model' is inadequate and must be brought to closer alignment with the 'human model'. I have no clue what that means on their end. I have no idea what they need to do, how many lines of code they have to change/edit/create... and frankly as a user, it isn't my place to even think about that.

Just like it isn't your place to ponder and spend your time thinking about the intricacies of your transmission. You just hit the clutch and change gears... the fantastic engineers at BMW have taken care of the grunt work so you can just sit back and enjoy the kick of the engine... that's your right as a user. And similarly, your right and privelege as the user of any other 'thing'.

My suggestion is for Ubuntu (the organization/project) hire usability specialists and have them dissect the Ubuntu experience, from install all the way to advanced GUI usage and to iteratively improve Ubuntu's usability.

Without a doubt, ubuntu has warped linux onto the desktop like no other distro and I'm sure it will continue to make advancements in this direction. I also believe with the same conviction that without the implementation of usability as a fundamental principle of the project it will fail to make major inroads in becoming the OS of choice for normal, average people around the world. Unless I'm mistaken, this is one of Ubuntu's goals.

The normal, average person around the world using an OS is, for lack of a better word... dumb! And I categorically place myself along side them. When it comes to any OS the avg person is dummer than dumb! Just like the avg person (including those who compile their kernal weekly) is dumb when it comes to thoracic surgery. Or the same way that a thoracic surgeon is 'dumb' when it comes to cooking fine French cuisine.

It is the job of the designer (usability expert) to create the 'thing' in such a way that is almost impossible to do the wrong action and very, very easy to do the right action. That, unfortunately, wasn't my experience.

So please, hire the best in usability (is Norman available?) and if you have already hired people please take a good look at whether they are really doing the job they were hired to do.

Thank you for reading this and for all of your effort in creating/improving ubuntu.

Peace

---

### Post by teaker1s on 2007-01-04
thing with ubuntu it works great if your prepared to invest time customising it for your needs and hardware. I set up a wireless ubuntu box for my grandparents on old hardware, it's miles better than win ME they had and all they want is internet browsing/email and to write letters:mrgreen: sorted

if you wanted your mbr on windows you could of either windows xp fixmbr or other windows versions fdisk fix mbr feature. or you could have edited grub so it either booted windows or ubuntu-maybe two disks in your case wasn't straight forward as it could be

---

### Post by 3rdalbum on 2007-01-04
I'm sorry that happened to you, but I don't think there's ever going to be a satisfactory solution to these kinds of problems. The BIOS is technology that should have been obseleted 10 years ago, simply because it can't easily handle the kinds of flexible booting options that today's users require. Long live EFI and LinuxBIOS!

And, as I'm sure you're already aware, installing Windows would have also changed your MBR.

I once tried to install SUSE onto an external hard drive. It installed GRUB onto my internal drive, but unfortunately Stage 2 of GRUB was installed onto the external, and apparantly my stupid 1980s-technology BIOS can't access the USB, so I lost the ability to boot any operating system.

I found that the Recovery Is Possible Live CD has a version of GRUB on it which, although it couldn't repair my existing GRUB, it *could* boot into the operating systems on my internal drive. You might want to consider downloading that, for emergencies.

---

### Post by seijuro on 2007-01-04
It seems to me you **may** have been told your install was toasted inaccurately, I have a usb jump drive and when I have it plugged in and list my mounts it actually shows up as fat16 as well for some unknown reason yet it is NOT fat16 and works just fine. In theory GURB and LILO assume you do not have a boot loader so they take over the MBR of the master drive to give you the option to boot multiple OS. In most instances this works just fine, but I am guessing(never used win2k) the boot loader for win2k was needed to boot your particular win so when GRUB wrote over the MBR you lost your access to it. My guess though is you could probably popped in your win2k disk and patched the MBR from some sort of recover mode like you can with winxp and the worked out what exactly was needed to allow your windows to boot with GRUB and configured it as such. Never forget failure is always a possibility no matter how "fool proof" something is and take the appropriate precautions.

---

### Post by Dies on 2007-01-04
It's been said that:

It's hard to make things "idiot proof" if we keep coming up with better idiots.

Not that I'm calling you an idiot, although I have to admit I did think so when I had just read the title :mrgreen: , but not after reading your entire post.

Let's take that BMW as an example, let's say you heard about this nitrous thing and the performance you could gain from it, now you could go a few different routes, professional instalation for example or maybe getting a friend in the know to help out. But instead you said screw that and just got a kit and installed it yourself without even doing any research, so you start up your BMW and it screams for a little bit then it dies, are the engineers at fault here?
Maybe they should have foreseen this and found a way to make it easy for you or prevent this disaster.

I agree that things can always be done to make it a little easier, but up to what point, how stupid do designers have to anticipate the user will be, and what impact will dumbing the process down that far have on users that know what they're doing?

Point is take responsibility for what you do and always try to understand what it is you are doing before you do it.


Oh and by the way fixing your particular problem really doesn't get any easier, and you can find the solution at any Linux forum.

---

### Post by mykalreborn on 2007-01-05
really nice story! i mean, the words you used. A+ in my book :D

but it's not ubuntu's fault. ubuntu comes from a great distro called debian which was designed - so i think, correct me if i'm wrong, for linux people who knew what they were doing. so ubuntu has came a long way from that and is still doing that.
then you have the problem with windows that it refuses to recognize other systems, like linux distros do. i once wanted to install windows after i've installed ubuntu. so i entered the cd - which btw, with it's "stunning" graphics took longer to start than ubuntu's live cd - and when i wanted to install it it said that the it cannot use the mbr bla bla bla (translation:we do not want to recognize the power of linux systems therefore when you have one on a computer we will not admit it). anyways. so i ejected teh win cd and even though i didn't install anything it messed up my grub. i had ti use the live cd etc. 
so you see. windows *"Blowed Up My Computer Real Good!"* without even installing it ;). that's even worse than your story :p

---

### Post by diepruis on 2007-01-05
Mmmm... I think he has a point. Perhaps we should have a screen for grub setup on the alternate CD?

---

### Post by ssavelan on 2007-01-05
I have had some serious problems with GRUB... almost lost a few machines... got real scared messing with other people's hardware.. trying to preserve their Windows partitions and finding GRUB setting up things wrong..... never actually had any residual problems in the long run.

I think a "REMOVE GRUB AND RESTORE SYSTEM" option would be good as a failsafe.  A kind of.. "your install didn't work so you can get your system back.


But... omg, if I had given up on ubuntu.... 

I was actually looking for a thread about proaudio ubuntu and how JACK and ALSA with the suite of MIDI and audio software destroy Winslows and whatever you can buy at any price.  I feel like my software set-up is worth thousands of dollars but is better than anything that can be bought.

I have had some trouble with GRUB and think that it could be improved a bit.  I've set up four complete newbs as someone who has only been messing with linux for a couple of months.  In and of itself I think that it is impressive.  I got scared because I had problems and an not at all an expert.

Reformat... reinstall... try a guided partition method.:cool:

---

### Post by raul_ on 2007-01-05
I didn't get it...did it erase your data or not? Why don't add an entry to /boot/grub/menu.lst that points to your other drive? Sorry if I'm missing something here

---

### Post by ssavelan on 2007-01-05
Ps, I don't believe that ubuntu/GRUB actually messed with your windows partition unless you did something seriously wrong in the partition phase.

---

### Post by Rhubarb on 2007-01-05
IMO if someone knows how to install extra hard disks, configure the BIOS, and install operating systems (win2k / ubuntu for example), then they've usually got a fair bit of technical experience under their belt.

From my own personal experience when I was just dabbling around with installing win ME / XP / Linux, I always backed up my data and / or disconnected the main hard drive (in your case the 80GB).

Though I'm sure the whole ideal would've been quite awful for you to experience, at least you've learnt a bit more of what goes on under the hood.
And I hope you (and everyone else here) practices good data backup habits.

---

### Post by diepruis on 2007-01-06
> **ssavelan said:**
> I think a "REMOVE GRUB AND RESTORE SYSTEM" option would be good as a failsafe.  A kind of.. "your install didn't work so you can get your system back.

Perhaps partimage should be added to the LiveCD, along with a warning and instructions. What do you guys think?

---

### Post by Babak on 2007-01-07
Thanks for reading and replying to my story.

I wanted to make something clear, my intentions were not to simply point out a discrepancy between 'machine' model and human model in GRUB for a dual boot install. This was what happened to me and it should be fixed. 

However, my true intention in going through with the posting was to use this as a mere example to illustrate that Ubuntu needs to take a leaf from Apple's playbook and put usability much higher on its priority list. Otherwise, all that wonderful effort will be for naught.

Who cares if you have the most stable, fastest, bestest, OS if the average human being (so full of 'idiocy') can not use it out of the box?

Rather than requiring each and every user to climb a steep learning curve... a design team of usability experts need only traverse the curve *once* and then redesign it so that it is much, much flatter.

That was my point. Hope it is clearer now.

ps to answer a raul_'s Q: no I did not lose any data/files. GRUB nuked my MBR. Once Winternals restored it, it was back to the rock solid OS that is Win2k.

Cheers

---

### Post by quartzy on 2007-01-07
Lol. Is all I can do,

The funny thing for me is that if ubuntu hadn't done what it tried to do you would NEVER to able to access it without the live CD, since windows bootloader couldn't care less about anything but itself.  it's not a ubuntu problem but a problem with how unflexable the BIOS is. Prehaps ubuntu should be more like your 'solid' windows and takeover the MBR then proceed to not care about any other OS's on the system?

Although I do admit grub needs some work, it's a big task when there are so many variables involved.  A quote I saw somewhere that said "the problem is every desktop system can almost be considered unique" couldn't be more true in this instance.  Trying to design a bootloader than will work 100% on 1000's of unique systems?

---

### Post by livingtarget on 2007-01-07
In fact you can let the windows bootloader manage linux as well rather than installing grub to the MBR. The trick is to know what you are actually doing, in the install procedure it will actually tell you where it is going to install GRUB. Grub goes into hd0 by default. That would be the first disk, you can install grub into hd1 and then set up (read: this is difficult) the windows bootloader to take care of it. Of course that's not easy, but I'm saying it's all possible.

---

### Post by Babak on 2007-01-07
"The funny thing for me is that if ubuntu hadn't done what it tried to do you would NEVER to able to access it without the live CD, since windows bootloader couldn't care less about anything but itself."


"Grub goes into hd0 by default. That would be the first disk, you can install grub into hd1"

ok, now don't take this the wrong way but my eyes start to glaze over when I read things like the above. It reminds me of going to my mechanic or Star Trek 'tech' talk...

As a user, I don't *care* what needs to happen under the hood !! That is not my job! That is the designers job! Why should I do their work for them?

Do you need a degree in mechanical engineering to drive a car? No! You just get in and drive!

Why is that? Because it is easy!

Why is it easy? Because thousands, no, millions of hours and $$$ have been spent on tweaking every conceivable part and form of the car to make *it fit the user and his/her mental model*.

That's why.

Any more rhetorical Q? No, I'm talking to myself here 




So let me say it again, and hope in the clearest way possible:

When something goes wrong with a complicated 'thing' it is NOT the user's fault !!

I know that sounds really stupid to an engineer, or a programmer who knows things inside out and likes to look down on others who don't have the same specialized knowledge... but it is a principle of usability.

Unless Ubuntu takes the guiding view that it is NOT the user's fault for [insert: not knowing sudo and other command line code, not knowing that GRUB needs to be configured with the fsdke::a command to confabulate the flux capacitor, etc .....] then from the user's perspective (that's the only one that counts btw!) it is not easy to use. And if it is not easy to use, they will simply not use it.

Have you ever noticed that in your own life? That you use things more and with relish when they are easy to use? it is actually, you know, *fun*? And the stuff that is tempermental and frustrating, you chuck across the room, right? you find a substitute for it, right?


Ubuntu needs to put the user FIRST and the technology SECOND (to serve the user)

Anything (repeat, anything!) that is marvelous to use only becomes so by following those two simple principles. Don't believe me? Look around you and find what you love to use... a teddy bear, a shoe, your ipod, etc...

They were all designed by someone who put you (the user) first and made the material, technology, software, etc. all of it subservient to you and your enjoyment... the designer worked hard to make it all a means to an end. 

For those that like formulas:

Ubuntu + usability = kick donkey OS (i can hear Bill whimpering in a fetal position already)

Ubuntu - usability = joins the rank of things which coulda been great but weren't

All the best to Ubuntu

(hire these guys: [http://www.nngroup.com/](http://www.nngroup.com/))
I have no affiliation with them btw (well, I lied, actually they give me a strawberry lollipop everytime they get a $1M+ account.. but only on leap years which coincide with a lunar eclipse)

---

### Post by 3rdalbum on 2007-01-07
Do PPC Linux users have to care about MBRs and non-Linux bootloaders and where the bootloader gets installed? Nope. Ubuntu installs Yaboot at some point on the disk, changes the NVRAM settings to automatically boot into Yaboot, and Yaboot is set up to run either Mac OS or Linux depending on the user's input.

Reason? Macs don't have a BIOS, they have a more advanced, trouble-free booting technology.

This thread is less about Ubuntu being "desktop-ready" and more about the ancient, unfriendly, trouble-prone part of "modern" PCs.

---

### Post by teaker1s on 2007-01-07
personally I'm not keen on live install cd as alternate.iso text install has always worked better for me

---

### Post by raul_ on 2007-01-07
Just to say that I couldn't disagree more with Babak :mrgreen: but it's ok

---

### Post by Dies on 2007-01-07
> **raul_ said:**
> Just to say that I couldn't disagree more with Babak :mrgreen: but it's ok

Man, can you imagine if he had actually PAID for this OS. :-k

---

### Post by gozzerd on 2007-01-08
I think Babak has an excellent point. By making the live cd so hugely easy to use, it establishes a context of ease of use in the mind of the user. Which, I think, is what we want, right? Those of us who have already hosed our systems six times know that his win2k partition is safe and sound and restoring the mbr is trivial. But Babak received a result he didn't expect. Nothing warned him. All that was needed was a little bit of educational material in the set-up, some more context,  so that he wouldn't have suddenly felt like he stepped into an empty elevator shaft. It  could be  giving how-to type instructions to manually do the steps needed to use the ntloader before  grub. The concepts involved in the decision grub -  yes or no? -  are not hard to understand, and it would be easy to give the user enough context to decide how he wants to proceed.  Install scripts usually offer some sorts of choices in this area, and knowing how wonderful Ubuntu is, something especially clear and gracious might be appropriate here.

---

### Post by raul_ on 2007-01-08
Does Windows installer offer that choice? It's an honest question because i really don't know...
What about OS X?

---

### Post by MrDigital1 on 2007-01-08
I guess I don't see the problem either.  I've had other people install Ubuntu who are relatively unsure about their own computer skills and there hasn't been an issue yet with them.  They see on reboot that they have this little menu that has Ubuntu, and their original OS as options on it.  I'm sure the OP had the same thing.  Ubuntu and Windows 2000 would both be on the GRUB menu.

I'm not sure what good a freshly installed Ubuntu OS would be if it left the Windows boot loader alone because it would completely inaccessible from a "newbie" point of view.  They'd boot up, get Windows menu (if they got it at all) and go "Oh no, where is my new Ubuntu installation??"

I guess they could change the install routine to say something like "This is going to install a new bootloader for when you boot your system you'll get a new menu" type message.  Maybe that's all the OP is asking for.

Hell, I've been a Windows and computer user now for more than 15 years and even I'd have to go look up how to edit Windows dumb boot menu.  ](*,)

---

### Post by gozzerd on 2007-01-08
I am not sure from Babak's post, but I think his grub install failed and he didn't get a menu, just a grub prompt. And, of course, even with just that, he could find instructions online on how to boot his win2k partition, assuming he could still get online. 

Microsoft still pretends that it is unimaginable that you would want to install anything but a Microsoft OS anywhere on your machine. Maybe Vista will be different. I will probably never know. But NT type windows do have a bootloader that grub can take advantage of. Grub can generate a small binary that you put on your windows boot partition, for instance, name it ubuntu.bin and copy it to c:\ubuntu.bin. You add one line to your boot.ini that points a menu listing to that binary,  i.e UBUNTU=ubuntu.bin, and there you go. The binary starts up grub. So you get an NT boot menu, then you get a grub menu, then you boot ubuntu.  

When writing to an NTFS partition is considered safe (some distributions are already doing it) this could be done in a script during install, and the MBR would never have to be altered for someone to try dual booting ubuntu and windows. You could try it, then if it wasn't for you, erase it, and Windows precious MBR would be none the wiser.  Many XP partitions still are fat32, so this could be done for them right now.  

Some years back, an earlier version of grub would change the chs numbers for your drive to something sensible, and make your windows partition unbootable, because windows always expects certain other fictitious values. Maybe something like that happened here. I think if Babak had gotten the intended grub boot menu, with a windows listing and an ubuntu listing, he wouldn't have been disappointed and written his nicely worded messages to this forum. He would have booted his winnt partition whenever he felt a need to, and the rest of the time experienced ubntu and seen how good it really is.

---

### Post by mikewhatever on 2007-01-10
Hey Babak,

while Ubuntu installer may not be perfect, you seem to have contributed to the problem. According to your first post you were overexcited, over expecting, and had wrong illogical assumptions. There is no way you can use anything without learning first, BMW included. You may not remember, or choose not to, but you must have taken driving classes, haven't you.

Now, from a different perspective, perhaps Ubuntu does not suit you. Just try and use something else.

---

### Post by cameron_1st on 2007-01-11
Uhm... if GRUB indeed messed up your MBR you can easily fix that by booting a Windows CD and going to console more. More details on Google as I don't want to get into details about how to fix Windowses ;-)

Big story for nothing. It's always like this. Windows NT crashes on a military vessel and nothing happens, life goes on, GRUB messes up 1 MBR out of 10 million out there and let's make a new novel about how bad Ubuntu/GRUB are...

](*,)

---

### Post by cameron_1st on 2007-01-11
Alright I read some more of this thread, and it seems that it wasn't the MBR it was an user error which perhaps formatted the drive. Even worse...

---

### Post by mykalreborn on 2007-01-11
> **cameron_1st said:**
> Uhm... if GRUB indeed messed up your MBR you can easily fix that by booting a Windows CD and going to console more. More details on Google as I don't want to get into details about how to fix Windowses ;-)

Big story for nothing. It's always like this. Windows NT crashes on a military vessel and nothing happens, life goes on, GRUB messes up 1 MBR out of 10 million out there and let's make a new novel about how bad Ubuntu/GRUB are...

](*,)

on this forum it's exactly the opposite. every little mistake in windows is folowed by things like "that's why bill gates is a *****" or waht-ever. you don't really see people beeing bummed up about ubuntu. don't get me wrong. i'm not a windows supporter (that's just so people won't throw stuff at me :p), but yo have to admit people often forget that even windows has a lot of advantages.

---

### Post by Babak on 2007-01-15
Here's an interesting post which is close to what I'm trying to say:

[http://kerneltrap.org/node/5610?page=5](http://kerneltrap.org/node/5610?page=5)

"Usability /should be king/."

Preach it, brother!

---

### Post by macogw on 2007-01-15
Uh, actually it DID have reason to install there.  See, that hard drive is "primary" in your BIOS, so it installs on the MBR of the "primary" hard drive.  If it installed on the other one, GRUB would never load and you could only boot into Windows.  You need both boot loaders.  You either need GRUB to chainload the ntldr to load Windows or the other way around.  Since the Windows drive is primary/master/whatever, it needs to be the other way around with Windows chainloading GRUB to load Ubuntu.

At least, that's my understanding of how it works.

---

### Post by diogenes_3 on 2007-01-15
OK, let's look back at what was said here by Babak:
a) He ran into a problem when installing Ubuntu, but b) that is not what he was posting about, rather he was posting about usability, and, well, c) along with impressively good wording he used some real stupid examples to bring his point across. Acceptable, given that Babak reserves for himself the right to be a computer illiterate. Sadly, it made for lots of discussions running around in circles.

Babak's post was not *meant to be* about Grub, yet there were all sorts of reasons to talk about Grub: He was wrong claiming that his was a standard install, and he was badly wrong claiming that a clutch is an example of good usability. Two hard disks is is not a standard install, and a clutch is *on the opposite* a typical example of how user were conditioned (yes, over more than a century in this case) to accept a clumsy device that needs the synchronous operation of three actuators - the clutch, the gear shift and the accelerator pedal (like a monkey, *with hands and feet!*) - to perform one function - shifting gears -, a process that takes many driving lessons to learn and half a life to perform smoothly, *not* because of usability considerations, but because Gottlieb Daimler and Adam Opel *could think of no better way to do it, and no one has since*.

Babak is, thirdly, gravely wrong in assuming that any usability expert can, and should, make installing an operating system, the equivalent not to plain driving, but to changing a motor, a foolproof task. Rather, all that is present in the market are vain attempts (pioneered by Windows as well as followed by Ubuntu) to pretend that usability could eventually succeed in making it foolproof. Car usability is all about the brake pedal being always in the center, and not at all about making even seemingly simple tasks (like changing a braking light bulb) easy, or comparative between a Chrysler, a Honda, and a Renault.

So, finally, to add my two cents to the matter: Changing an operating system should be done by people with at least basic knowledge of what they're doing. To them, it has already been made real easy. All others (like, my Mom) should be denied root privileges on *any* machine. As concerns other tasks, yes, there *are* points where Ubuntu's usability *could* use improvement (so could Windows', but it's still ahead).

---

### Post by Steveire on 2007-01-15
Good posts Babak. You really make a good point about bootloders and usability. KDE and GNOME have usability people working on the team, but they are major desktop environments. I'm not sure grub gets so much attention. [OpenUsability](http://openusability.org/index.php) is a site dedicated to bringing open source together with usability experts. I didn't find anything on there about grub.

It looks like this issue may be resolved during the ubuntu install. Fill out a spec [here](https://blueprints.launchpad.net/ubiquity/), noting what the installer should have done in your case, and link to this thread etc.

All the best.

---

### Post by mips on 2007-01-15
Stop using Grub and start using **[GAG]("http://gag.sourceforge.net/")** !!!

---

### Post by xpod on 2007-01-15
> Stop using Grub and start using GAG !!!

Thats right......GAG him:twisted: 

Is this like the "ubuntu ate my hardrive" thread...or the "Ubuntu wiped my Windows" one,mmm:-k 

Well if thats the case it must have been Windows that runied my sex life for 4 months too..[-( 

Just joking,keep at it Babak....it is worth it in the end
Dont let a box of wires n stuff get the better of you mate;)

---

### Post by Babak on 2008-04-14
Hello guys, I'm back. 

I just wanted to give a heartfelt THANK YOU to the ubuntu team for integrating WUBI into the distro - I don't doubt that the situation I describe in this thread would have been totally side stepped had it been integrated back when I tried my install.

I'm counting the days for the final release of 8.04 so I can attempt another run at linux/ubuntu as an OS

the point of the thread was usability and with wubi ubuntu has made great strides!

wonderful, wonderful !!

way to go guys

oh and especially warm thank yous to the smart folks behind wubi! I tip my hat to you sirs.

---

