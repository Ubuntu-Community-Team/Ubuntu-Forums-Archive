---
title: "Booting from CD at school"
date: 2008-01-08
forum: The Cafe
---

### Post by Fleece Flamingo on 2008-01-08
Is it possible to boot from cd or usb flash drive at school and use Ubuntu ( or Kubuntu if school computer has less ram) to use as a web browser?

---

### Post by Pevichaey5 on 2008-01-08
it depends what their boot options are, but i wouldn't recommend trying to find out, as it could been seen as a hacking attempt if you don't have authentication,

---

### Post by bodhi.zazen on 2008-01-08
I don't see why not. It is best to ask permission before booting someone else's computer or booting a "foreign" OS on their network.

---

### Post by bodhi.zazen on 2008-01-08
> **thexero said:**
> it depends what their boot options are, but i wouldn't recommend trying to find out, as it could been seen as a hacking attempt if you don't have authentication,

hacker = white hat

cracker = black hat

---

### Post by Fleece Flamingo on 2008-01-08
Bwuahaha imagine if I did sudo rm -rf /* that would be BAD (most likely wont work on a live cd anyway)! Well it's only middle school, do you think they would see it as hacking? Its only a live CD running on ram

---

### Post by PetePete on 2008-01-08
depends is they want to cause trouble for you or not... what kinda mood the sys admin is in that day!

you may have trouble connecting it to the internet though, your school could have weird proxy settings and such.

---

### Post by Fleece Flamingo on 2008-01-08
LOL well I may have pissed him off a little bit but thats his own FAULT!
I dont have a username at my school so I cant do ****! And have asked to have one made for me, and they take FOREVER!
So they have this limited account setup that can't save anything so I did ctrl alt del and changed the password. He doesnt know its me tho.

---

### Post by lamalex on 2008-01-08
I got an in-school suspension for this when I was in middle school. Don't do it without asking. School computer policies tend to be very strict. Will you get caught? Probably not, but maybe.

Does your school not have firefox? Maybe you should start a F/OSS club and get kids in your school into freedom. Our elementary schools now uses OpenOffice, all the pcs have firefox, and my old high school is getting ready to roll out moodle because I went to meetings and showed why FOSS is better.

Oh, and yes, rm -rf /* will just ruin your live session, you need to mount the machines drive first, then you can do it. And yes, it works, and yes, you get suspended and often your technology privileges taken away for the year.

> **Fleece Flamingo said:**
> LOL well I may have pissed him off a little bit but thats his own FAULT!
I dont have a username at my school so I cant do ****! And have asked to have one made for me, and they take FOREVER!
So they have this limited account setup that can't save anything so I did ctrl alt del and changed the password. He doesnt know its me tho.

Don't piss off your school syadmins.  Dealing with little kids like you (and like I was) grates on your nerves.

---

### Post by Pevichaey5 on 2008-01-08
believe me when i say its not worth it

only do things like that if you have written permission from the System Administrator, i was have always been the person who likes to know and find out what your not suppost to know, and have got into a fair bit of trouble using that knowledge, so i was basically looking for trouble, and its not worth it, but if you like me, you going to take no notice of what i have just said lol
good luck

---

### Post by Fleece Flamingo on 2008-01-08
I should actually go to the sys admin and ask him if he has ever thought of using linux for schools. It would save the school a whole lot of money and keep greedy gates from earning more.

---

### Post by PetePete on 2008-01-08
i agree with previous posters... when i was in school, i messed around etc.. but you get to a certain age when you realise that buggering around with the school computers is so trival its just not worth the hassle if you get caught.

---

### Post by Hospadar on 2008-01-08
I would personally see nothing wrong with booting off a livecd, but as a tech support person myself, it would irk me to think about all the employees working at my place booting off livecd's.  It'd be only a matter of time before somebody accidentally (or maybe not accidentally) deleted crucial things off a hard drive.

So assuming you have good intentions I would advise just not telling your technical people about it, and don't ever even mount a hard drive (by default drives are unmounted in the livecd until you double-click em).  cd's and flash drives might not be on the boot list by defualt, so if they arn't, you'll have to use the bios options to boot off your chosen media.  many bioses have boot menu's aside from the actual boot order in the bios settings that allow you to boot off a chosen media without changing the standard boot order.  It would be nice for your tech people if you used that instead of changing the boot order.

Also as for net connections, a lot of places use MAC filters to control network access, but if you are booting off a machine already on the network you don't have to worry about that.  They may also use a network proxy (especially in a school, to keep out the porn sites and such) so you'll have to set yourself up with that.  if you're smart you can probably get the settings off a machine already running, or they may be freely distributed as to allow kids with laptops to connect, you might check with your tech people. A proxy would be set inside firefox (Edit->Preferences).

---

### Post by Fleece Flamingo on 2008-01-08
So you think that booting would from a live CD wouldn't change them from filtering out sites. No I have no desires to go on a porn site at school. But for christ sakes they won't even let us go on wikipedia!

---

### Post by wasing on 2008-01-08
chances are if its a school like mine they have changed the bios on the computer so the only boot device is to the network harddrive and you cannot boot from another device unless you find a way to access the bios i doubt it will work. and even then you have to have a password to access the schools network. like mine i know for sure it will not let me use my username/password on an unsecure computer so you have to have a super-root user account and password to access the schools servers. 

so chances of hacking are like zero to none and im not even talkin about failsafe's they have in place to prevent a security breach. which is why i havent tried it at my school and i would not want you to try and get and trouble at your school. if i was ever caught according to the rules i would have to be expelled for violating a contract i signed with the school for computer use.

if you really want to though is suppose you could technecly flash the bios and change boot device and boot a live cd but im not sure what thats gonna do for you cause its gonna be a live CD without access to anything networked so basicly i guess you could... um.. idk do whatevers preloaded on the live CD without access to a network.

now i mean when im bored in class and dont feel like paying attention to one of my teachers i sometimes do think about how i could possibly access the schools servers and i have had some really good ideas how to but again i would have absolutely no reason to what soever

if you want to go ahead

1. flash bios on computer
2. load a backtrack 2 live cd
3. my school uses novell suse linux.
so im sure if you are linux savey enough (not me... yet! but someday i hope so) you can obtain the super root user name and password.
4. congrates you have a key to the schools network until they find something mysteryious in the logs and the feds step in.

again just spewings from my mind. and i would never ever attempt this on any network unless i had absolute permission to. 

btw im a linux newb so far and only now how to make my way around windows...
im still havin trouble setting up my Geforce 8600GT and compiz.

anyway yeah i tried to run live off a usb stick at my school cause my tech teacher wanted to see what would happen but according to him a successful breach in the past lead to a step up in preventing another breach from happening again.

---

### Post by stump138 on 2008-01-08
they have to do that by law..The child internet protection act in the US is very abstract and anything that can be possibly construe as bad will get the block..don't blame the sys admins...blame your politicians :(

And as a sys admin at a school, I'll tell you that most of us (myself included) turn a blind eye to it, and only do something when you get caught by someone who complains to us :P

short lesson..I would ask, get told no...do it anyway...be smart enough not to get caught :P

---

### Post by Pevichaey5 on 2008-01-08
seems you go off easy lol

i would jus take out the cmos battery for a few minutes to clear the password, then replace and change the boot order.

i have been caught many times, but i'm still there because what i have turned into, i still go and do what i did before, but i report all my findings to the system admins now hoping i'll get a job there hehe

---

### Post by stump138 on 2008-01-08
Generally, if I have to sit down in a conversation about someone doing something "bad" on the network, i'm aggravated only at the fact that they got caught and now I have to listen some administrative type cry about it:P 

My philosphy is about being open to promote learning..who can learn anything in a completely locked down environment? I encourage people to break stuff so they can learn from it..but that of course isn't a discussion for here :)

---

### Post by theRightNee on 2008-01-08
hey if you just want more internet accesibility, no need to boot off of live CD

use torpark (google it, and download from download.com). slower-a little bit-but it gets the job done...and its a lot easier to hide than ubuntu =]

---

### Post by bodhi.zazen on 2008-01-08
Moved to the Cafe as this is not really a support thread :)

---

### Post by barbedsaber on 2008-01-08
I once ripped out the network cable from one of my school computers, and plugged it into my laptop, then picked connect to network. I guess they only made a very basic security syststem, because I could accses everyones files, print things, surf the net without using my account, print, and access the backup server files (but not the normall server) without any passwords. I had to run up to the sysadmin persons office, and appoligise before he suspened me, and he was glad that I told him, so I got off scot free, freaking funny tho. :):lolflag::)

---

### Post by stalker145 on 2008-01-09
> **Fleece Flamingo said:**
> Is it possible to boot from cd or usb flash drive at school and use Ubuntu ( or Kubuntu if school computer has less ram) to use as a web browser?

If all you're wanting to use is a different web browser, why not grab the Firefox application from [PortableApps]("http://www.portableapps.com")?

---

### Post by rowanparker on 2008-01-09
I once managed to boot DSL (Ubuntu was too slow) from USB stick (all the bios passwords are the same and really obvious). My ICT teacher gave me some IP address to help me try get on the internet through the school proxy. I couldn't get on anything. Mounted the drive but couldn't get write access to it.

I would advise asking before doing things (learning from experince here). I recently got told off and a final warning (and internet ban for a week, big wow). I was doing some VBA in word (only thing you can do) and I had put in some thing (that my mate made but I took the fall) that could view the servers (3 of them, couldn't really access much). It was a very simple exploit (execing `explorer [i]server_ip[/ip]`) but I had passworded my code so he couldn't view it. I get a really long lecture about crap and he said if you do anything again then thats it: "he's going to court". The stupid thing I did was name the program after myself :(

I'm going to ask him if he will open up port 22 for me and install putty on my login but I don't think he likes me. Although he did say if you ever want to try something just ask before you do it. I might tell him about some other exploits as a bribe (there is one in an ftp program which allows you to exec any file, even on a memory stick).

---

### Post by Lord DarkPat on 2008-01-09
I;m like the computer genius in around the school(not the only, the best[enjoying flattery[), so the sysadmin lets me toy around with the comps as much as Iike. she asked me to install ubuntu on her comp and she's loving it!
Try fiddling with the BIOS, you may be lucky if there's no password

---

### Post by fedex1993 on 2008-01-09
Well let me tell you my story of live cds at my high school and my middle school lets say it didnt end good. 

Okay about 2 years ago i started using ubuntu which i still use today but i am switching to red hat sadly but i asked the it depearment at our middle school well actually the technology depearment and they said oh yes you can boot a live cd and what not. about a week later whe i was in the computer labs and booted to the cd. Well after 20 mins of being on it my teacher walked buy and siad "no that is hacking into the system your a hacker" she didnt know what she was talking about. Well i got a refural for it and banned for using the computers for my 8th grade year which sort of pissed me off. Well this year the same thing happened at my highschool but i only got banned from the comps for about 1 semester. Well i decided to get back at them buy formatting the hardrive on about 22 computers which made them even more mad. That is my story i would not recommend it but back your self up and get it in writing thats all i half to say. :)

---

### Post by bodhi.zazen on 2008-01-09
I am going to close this thread now as it is starting to get a little repetitive.

There has been some discussion with the staff and I think the proper thing to do is to ask permission. Obviously rules and regulations vary widely from school to school. While we may not agree with them, these rules are to be followed. Think of as part of becoming an adult, there are lots of rules to follow and the consequences get greater as you get older.

Circumventing, cracking, or blatantly ignoring such rules is ill advised and NOT condoned on the Ubuntu Forums.

---

