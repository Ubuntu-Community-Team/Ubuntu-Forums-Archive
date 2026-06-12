---
title: "Newbie (me) discovers flaw in school system."
date: 2010-01-04
forum: The Cafe
---

### Post by BT1 on 2010-01-04
Well, I am pretty much a Linux newbie, having only been serious about Linux this past year. I'm confident when it comes to installs and a few other things like debugging my most used programs.
 
My school has community computers which have administrator rights assigned them, which is a good thing. Bad thing is they do not allow installation of freeware stuff like firefox updates (flash download and install not allowed), they run slow on XP because of the antivirus slurping up resources, and a few other annoying things - like I can't format my own thumb drives, which is understandable because people might format the HD instead on accident if they don't know what they're doing.
 
I'm tired of this but I am a good boy and don't want to do anything bad.
 
I have experience with putting full linux installs on thumbdrives, meaning I have "/boot" , "/" , "/home" installed on the thumb drive as if it is a hard drive which allows me to boot into linux on any computer system that allows bios to boot USB drives. Well, I was messing around and brought a drive to school with xubuntu on it and restarted the computer. I was excited when I booted into my very fast Xubuntu desktop, but a pang of righteous fear came into my blood when I discovered I had complete control over the HD that was inside the computer. I didn't try to access the files, but I was shocked to find that I could delete, create, or resize partitions through linux even though the HD had a admin password on it.
 
I wanted to know how... open this system was, so I went into the native XP install and copied the network info (gateway, IP, etc.) and after putting it into the network connection configuration in Linux (the XP install has custom network settings), I was able to browse websites that I wasn't able to before. Even able to download content that could reduce the security of the system.
 
Now this is not a bragging post, I have an ethical dilhemma on my hands. On one hand, I want to alert the network admins/tech guys and point out this very dangerous flaw in the system, but I don't want to be locked out from using Linux on my thumb drive lol. Do I alert them and lose my ability to run my virus free, very quick xubuntu linux, or do I keep quiet and give evil a chance to wreak havoc? My better half says to speak up and do something, but my stingy inner child says "Noooo! No linux for you! Noooo!"
 
Mods if some of that info comes off as "showing people how to do illegal stuff" just edit it out please, I mean no harm.
 
So what should I do?

---

### Post by Skripka on 2010-01-04
I wouldn't lose much sleep...of how many 100 or 1000 students in your school system use *nix or know how to put a bootable OS on a thumb drive?  The number probably does not exceed the number of fingers you have.

---

### Post by RiceMonster on 2010-01-04
They're not your computers, so you really shouldn't be booting from a usb stick, especially since it gives you full access to the hard drive, which you are not supposed to have access to.

Perhaps if you're really concerned you should talk to them and recommend they disable booting from optical media and usb devices.

---

### Post by blur xc on 2010-01-04
#1- no computer is safe if someone has physical access to it

#2- Linux or any other Free Open Source Software (FOSS) is NOT freeware- (or share ware)

BM

---

### Post by Eisenwinter on 2010-01-04
Aren't they going to be really pissed off that you used your USB drive to boot into a different OS in the first place?

---

### Post by doas777 on 2010-01-04
sounds like the admins are using policies to block certain actions. that is why you are unencumbered when running outside of it. if they were blocking web requests by url at the gateway, you would not have noticed a difference.

you have hit upon a fundamental security truth: physical access == root access.

---

### Post by Skripka on 2010-01-04
> **Eisenwinter said:**
> Aren't they going to be really pissed off that you used your USB drive to boot into a different OS in the first place?

You'd be surprised how many non-*nix users don't even know you can boot from a thumb-drive.  I'd hazard a guess the reason why the hole is there, is because no one has though of the possibility.

---

### Post by Duhnali on 2010-01-04
If it were me, I wouldn't alert them. In most cases where a school gives students access to a computer, the student(s) have to sign a usage agreement form of some sort, which more than likely has a bit about loading foreign things, which I'm sure as hell is what they'd call an OS on a thumb drive.

Just keep it secret, or it'll probably get you in some trouble.

---

### Post by phawnex on 2010-01-04
^what he said. 

i cracked open my networks (not even through linux, i am a linux nooob) a while back and had to sign an agreement as he stated.  dont share your ability. use the linux to benefit yourself but i would also recommend on not unleashing havoc on their computers either.

---

### Post by Tristam Green on 2010-01-04
> **Duhnali said:**
> If it were me, I wouldn't alert them. In most cases where a school gives students access to a computer, the student(s) have to sign a usage agreement form of some sort, which more than likely has a bit about loading foreign things, which I'm sure as hell is what they'd call an OS on a thumb drive.

Just keep it secret, or it'll probably get you in some trouble.

Ding ding ding ding we have a winner.

---

### Post by Techsnap on 2010-01-04
It's not your computer and not your network. If you want to do this then you should ask permissions from the administrator. If the answer is no then it's fair enough.

---

### Post by underquark on 2010-01-04
Ah, so you thought this one up over the Christmas Vacation and tried it out today, the first day of Second Semester.  You do realise that if even just one IT person at your place reads this post that they will have looked up your profile, your Yahoo mailing details etc. and already have narrowed down where you live/study etc.  Don't be surprised if there's a message waiting for you tomorrow.

---

### Post by NoaHall on 2010-01-04
I've found many flaws in the school system, I reported them for a while, but as they weren't then fixed(and it was a REALLY easy fix), I stopped reporting. The password set up is so simple too, I can work out every users password.

---

### Post by Skripka on 2010-01-04
> **underquark said:**
> Ah, so you thought this one up over the Christmas Vacation and tried it out today, the first day of Second Semester.  You do realise that if even just one IT person at your place reads this post that they will have looked up your profile, your Yahoo mailing details etc. and already have narrowed down where you live/study etc.  Don't be surprised if there's a message waiting for you tomorrow.

After all, you're not really paranoid if the Black Helicopters really ARE out to get you.

---

### Post by RabbitWho on 2010-01-04
That's not a flaw in the system. There's no way for them to avoid that. 

What is that I read here before.. Physical access = root access. They could put a password on the hard drive.. but they'd have to let you guys know what it was so you could use the computers!

---

### Post by FuturePilot on 2010-01-04
> **Skripka said:**
> After all, you're not really paranoid if the Black Helicopters really ARE out to get you.

I hear somethi

---

### Post by adam814 on 2010-01-04
You do point out something important: You can't have information security without physical security.  If you can sit at the keyboard and carry a LiveCD/USB you can do more or less what you want with a machine.

In a situation like that it would be advisable for USB boot to be disabled in the BIOS and the BIOS protected with a password (although even that's not perfect it would make it impractical).

Even assuming you did have enough students to get one rogue with a thumb drive and a vendetta It's only likely to cause inconvenience.  In an install of that magnitude I'll bet they have a standardized disk image (probably with Norton Ghost) that they just blindly restore to any machine that succumbs to Windows errors or user errors.  WIthin 24 hours any of those machines could be back to where they were.

Unfortunately it's been my experience that pointing out the cracks in the armor tends to get one accused of cracking the armor.  I'd personally keep it to myself and let the admin(s) handle their network, that way if they ignore good policies and someone else does what you're worried about you won't be the first one suspended.

---

### Post by BT1 on 2010-01-04
> **Skripka said:**
> I wouldn't lose much sleep...of how many 100 or 1000 students in your school system use *nix or know how to put a bootable OS on a thumb drive? The number probably does not exceed the number of fingers you have.
 
Yeah, I don't see too many people talking about Unix/Linux outside of Apple vs. PC arguments, or talking about networking. I have converted 3 people to Ubuntu that used to go to this school, but they left for Grad School last semester.
 
[quote=Duhnali]If it were me, I wouldn't alert them. In most cases where a school gives students access to a computer, the student(s) have to sign a usage agreement form of some sort, which more than likely has a bit about loading foreign things, which I'm sure as hell is what they'd call an OS on a thumb drive.
 
Just keep it secret, or it'll probably get you in some trouble. [/quote]
 
When you turn on the computer and it loads into Windows XP, it makes you sign in but only has a warning that says "innappropriate use is prohibited". That's not a definition argument I want to get into with the Network Admins since I'm the "linux guy" that keeps hounding them about support for linux every time they update their windows friendly security settings (Yes! Fight the good fight!). It's odd because I'm such a newbie at linux and they refer to me with that name lol. I already annoy them with constant requests that they approve my MAC addresses (I like to install and reinstall custom configurations to see what I like, and each time they have to re-approve my MAC address for some reason even though its the same each time).
 
[quote=Eisenwinter]Aren't they going to be really pissed off that you used your USB drive to boot into a different OS in the first place? [/quote]
 
:( IF they're mature, they'll be thankful I hope and excuse my actions lol. If not, I could be banned from the school's computer system :O
 
[quote=blur xc]#2- Linux or any other Free Open Source Software (FOSS) is NOT freeware- (or share ware)[/quote]
 
Yeah, I shouldn't have grouped them like that. Dunno what I was thinking.
 
[quote=RiceMonster]
1.) They're not your computers, so you really should be booting from a usb stick, especially since it gives you full access to the hard drive, which you are not supposed to have access to.
 
2.) Perhaps if you're really concerned you should talk to them and recommend they disable booting from optical media and usb devices. [/quote]
 
1.) Should? Typo? Lol
 
2.) That's scary though. The bios is wide open. You can even set a bios password, mess with various other settings... I don't know why they would leave it so open other than not wanting to keep up with Admin bios passwords or something.
 
[quote=underquark]Ah, so you thought this one up over the Christmas Vacation and tried it out today, the first day of Second Semester. You do realise that if even just one IT person at your place reads this post that they will have looked up your profile, your Yahoo mailing details etc. and already have narrowed down where you live/study etc. Don't be surprised if there's a message waiting for you tomorrow. [/quote]
 
Its funny you should bring that up. Their network website says "We do not support linux on this network", and when I asked them why, they said because no one on the IT staff is familiar with Linux. That blew my mind. I'd always heard about Linux networking and how its so grand and stuff, but these guys don't even know how to use it?! With that in mind, I don't know why they would be visiting this site lol.
 
Thanks for your thoughts one and all.

---

### Post by Skripka on 2010-01-04
> **RabbitWho said:**
> That's not a flaw in the system. There's no way for them to avoid that. 

What is that I read here before.. Physical access = root access. They could put a password on the hard drive.. but they'd have to let you guys know what it was so you could use the computers!

Umm...I know the BIOSes I've seen let you password them...and many I've seen let your restrict the boot order.

---

### Post by NoaHall on 2010-01-04
> **Skripka said:**
> Umm...I know the BIOSes I've seen let you password them...and many I've seen let your restrict the boot order.

Remove the battery, put it back in, viola. Or use a Jumper.

---

### Post by Skripka on 2010-01-04
> **NoaHall said:**
> Remove the battery, put it back in, viola. Or use a Jumper.

I think most lab admins would NOTICE you and your screwdriver pulling apart a computer tower, to get at the BIOS jumper or battery :)

---

### Post by whiskeylover on 2010-01-04
> **Skripka said:**
> I think most lab admins would NOTICE you and your screwdriver pulling apart a computer tower, to get at the BIOS jumper or battery :)

Most towers don't need a screwdriver. Just push a button on the side, and the panel slides away, exposing the insides :)

---

### Post by gmjs on 2010-01-04
All good IT support departments should password protect the BIOS, set boot device priorities to include first HDD only and lock the machine cases (especially in schools)!

---

### Post by Eisenwinter on 2010-01-04
> **Skripka said:**
> I think most lab admins would NOTICE you and your screwdriver pulling apart a computer tower, to get at the BIOS jumper or battery :)
Unless you're Chuck Norris. He can unscrew everything while remaining undetected.

---

### Post by NoaHall on 2010-01-04
> **Skripka said:**
> I think most lab admins would NOTICE you and your screwdriver pulling apart a computer tower, to get at the BIOS jumper or battery :)

Not if they aren't in the room ;)
And there are always ways.

---

### Post by BT1 on 2010-01-04
> **Skripka said:**
> I think most lab admins would NOTICE you and your screwdriver pulling apart a computer tower, to get at the BIOS jumper or battery :)
 
Lol yeah. The admins aren't even on campus though, they're like 5 miles away in a remote location. The only thing in this room is a security camera that makes sure people don't steal the things, and I've seen people do some crazy stuff like steal keyboards and stuff which leads me to believe the camera is either fake or is just on record in case something *does* happen...like a shooting or bombing. Nevermind the fact that people steal keyboards and mice...

---

### Post by Skripka on 2010-01-04
> **Eisenwinter said:**
> Unless you're Chuck Norris. He can unscrew everything while remaining undetected.

[IMG]http://api.ning.com/files/NShDyS7CREO3aOBNBZZB1Af6-qx70VP5Eglc66La4Fub5k2z2wzGKoReDxeb1M2skE4vHR2KROcO0ASmLYqtmvjh5MkxuxVR/633508100345116838ninjaconvention.jpg[/IMG]

---

### Post by Skripka on 2010-01-04
> **NoaHall said:**
> Not if they aren't in the room ;)
And there are always ways.

True, but the further you get from the usual suspects the likelihood of needing countermeasures drops significantly.  As I said earlier, the number of folks who even know that you can make thumb-drives with bootable OSes on them is tiny.

---

### Post by NoaHall on 2010-01-04
> **Skripka said:**
> True, but the further you get from the usual suspects the likelihood of needing countermeasures drops significantly.  As I said earlier, the number of folks who even know that you can make thumb-drives with bootable OSes on them is tiny.

And I wish to keep it that way, but it seems the number is rising.

---

### Post by SuperSonic4 on 2010-01-04
I'd say nothing but stop exploiting the loophole immediately

---

### Post by Eisenwinter on 2010-01-04
> **SuperSonic4 said:**
> I'd say nothing but stop exploiting the loophole immediately
What a very politically-correct response.

---

### Post by Skripka on 2010-01-04
> **whiskeylover said:**
> Most towers don't need a screwdriver. Just push a button on the side, and the panel slides away, exposing the insides :)

Quality cases such as Lian-Li build the cable lock hardware through the door rail, in addition to thumbscrews...if an IT dept gets cheap crappy cases that don't have a lock of some sort built into the door-they're asking for it.

---

### Post by chriswyatt on 2010-01-04
They should really disable booting from removable media and password protect the BIOS.  They did at our school.

We found loads of ways to get round security at our school, I got in trouble once for taking over peoples' computers.  I'm by no means an expert at hacking, it's just the security at our school was rubbish :P.  There was this program you could use to control people's PCs, after everyone started going on it of course they blocked it, then we found another way:

They used to have some test accounts on the computers which allowed you staff privileges, one was:

Username: staffuser
Password: staffuser

another one we found after they got rid of staffuser:

Username: stafftest
Password: stafftest

In primary school the usernames / passwords were even simpler: user, manager, teacher :)

WinPopup was fun as you could propogate messages throughout the whole server, and all the staff used it :)

Someone told me they managed to get everyone in the school's passwords once by using a Linux computer to 'hack' into the network.  They could've been lying or showing off though.

And another little trick I used to enjoy doing was sending test pages to random printers in the school, pretty sad really but there wasn't a lot else to do at lunchtimes :).

Never did anything destructive but I think I pushed my luck a few times.

---

### Post by koleoptero on 2010-01-04
I'd install a win xp look-alike linux distro on the thumb drive and then to the hard drive and waited to see if anyone notices the difference.

Or at least use it from the thumb drive so that noone that sees you using linux and tells the admins.

And you're doing that computer a favor by using xubuntu on it instead of xp.

---

### Post by The Toxic Mite on 2010-01-04
> **Eisenwinter said:**
> What a very ***snide*** response.

Fixed it for you ;)

---

### Post by betrunkenaffe on 2010-01-04
You don't need to admit that you booted up from the USB in order to report there is a security hole. You could always mention that you discovered there is no passwords on the bios (seriously, what kind of admins run this system?!) and explain possibly security flaws that may arise due to it.

On the whole pulling the battery/resetting CMOS thing, it's one thing to accidentally get into a password unprotected bios (I hit the delete key cause I was curious/concerned/by accident) and quite another to be "accidentally opening" cases and doing a very specific set of actions which are clearly outside of normal usage and TOS.

I would definitely not be mentioning that you were able to successfully boot from your USB however you can always mention that you have a bootable USB they can borrow if they wish to test (say you have for showing off your pimp Linux distro to everyone you know) and that you can bring in for them if they  want.

School administrators will be unimpressed but a decent/competent (this is questionable at this point) computer administrator should be happy that you brought very real concerns to him for corrective actions.

---

### Post by gletob on 2010-01-04
Trust me, had an experience with reporting flaws back in middle school.

TELL THEM NOTHING!!!

You alert them to one little problem and they'll throw some crap at you about how you compromised their system, and how close you were to breaking the entire network and causing thousands of dollars worth of damage.  Most of the IT people that work for schools, are complete idiots (Not all, but most)

Before you know it you'll end up with 4 day's of ISD and suspended Computer Privlages.  Say nothing, securing their network is their problem.  Not yours.

---

### Post by staf0048 on 2010-01-04
I would say something so it alerts the school to the loophole.  Think of what could happen to the school's computers if someone not so honest as yourself does do the same thing, but with malicious intentions.  

Will you get in trouble?  Probably.  But you're helping to keep the school secure from other attacks.  Keeping quiet will not be much solice if something bad happens that you know you could have prevented.

---

### Post by staf0048 on 2010-01-04
Just a thought... could you do it anonomously?

---

### Post by Gizenshya on 2010-01-04
I've seen university networks so open that it was actually scary.  On one, they had folders for your documents.  Everyone had one, it's a good idea... But all you had to do was type in the above directory manually (change /folder/folder/username to /folder/folder/) and you had access to all active and archived usernames, including admins.  Very little guesswork later, access to all accounts and folders.  It isn't like that there anymore, though.

There were no boot passwords, and it was very easy to get into where they stored the images on network and copy away with r/w access.  Then have fun modding till you were blue in the face, if you were so inclined.

Whatever you do, **do not report it!!!**  I know it sucks, but you will probably get in just as much trouble as if you exploited the 'oversight' (... that word gives the admins too much credit...).  Check and see if it is against the rules.  If it is or might be, don't do it.  If it is unclear, call them up and ask if it is against the rules, and be sure to mention that it isn't in the rule book, you were just wondering.  At pretty much any university, it doesn't matter what is in the rule book.  If they don't want you to do something, even if they decide that after the fact, they WILL punish you for it, rule book be damned.  Unless your pockets are deep and you want to fight it in court (which you would have to do), then avoid the issue like the plague.  Again, I know it sucks, but such is the system.  Don't say you weren't warned.

Only if you call and ask, and get clear permission, would it be OK for you to do it.  Just say something like "I heard about this, and I would like to use x program that isn't on the school's computers for my project, but I heard on forums that I should ask first."  Never say that you've tried it, of course.  But yeah, then, and only then, is it ok to do, no matter what the rulebook says.  And even then, don't go screwing with other people's stuff.  Just because they give you permission to use x software, doesn't mean you can go around breaking other rules.

> **staf0048 said:**
> Just a thought... could you do it anonomously?

I wouldn't do it.  He is already known, so it would really narrow it down.  They would almost certainly go on a manhunt and end up making his life a living hell.  It isn't worth the risk.

---

### Post by squilookle on 2010-01-04
I wouldn't say anything if I were you. 

So long as you don't wreak the havok, it's not your problem, but we always used to try (and often succeeded) to get into things on the computers at school that we weren't supposed to.

---

### Post by Gizenshya on 2010-01-04
ok, how about this...

You say you've heard about many common security flaws in school networks, and that you would like permission to work with them to do a security audit that would make the network more secure for all.  (use some excuse, a love of programming, fear about the security of your account or data on the system, etc.).  Anyone can get on there and install keyloggers and the like at their whim, the way things are now.  They can't really refuse it (though they might not want to involve you, but ohh, well.  If they do complain or refuse, just go to the dean, and say that you fear the network may be at risk, and the network admin is apparently negligent.

Of course, include that test in the audit.

Work with them and say that the results will only be released when all threats have been fixed-- but that all threats must be released, because it will help other universities.

You might end up being a hero in this scenario :)

---

### Post by dragos240 on 2010-01-04
Alright. Have someone ask for you if you want to ask. Have them give you the answer. Since the IT people at the school are aware of linux and it's awesomeness, they have linux computers, XP computers, and 2 macs. They have firefox on almost all of them. And they let me boot off of my usb stick, yipee!

---

### Post by aaronchall on 2010-01-04
I wouldn't say anything about it to anyone, even if you consider yourself an ethical hacker.  [http://www.iprotect.com/Community_Forum/statutes-states-ctr-2.php](http://www.iprotect.com/Community_Forum/statutes-states-ctr-2.php)

It's not your computer, and the owners definitely don't want you to get into it.  If the computer admins are in a bad mood when you tell them (or even if they're not) they might decide to throw the book at you to cover up for their own inadequate security measures.  Some states' laws prohibit merely accessing material you're not supposed to access.

So then you might even find yourself in front of a judge who thinks kids who screw around on computers all day are up to no good, and then he might decide to make an example of you.  

All of the above a worst case scenario?  Yeah.  Sounds unreasonable?  Yeah.  Still could happen and ruin your life?  Yeah.  

So DON'T tell them you did it.  If you really want them to tighten security, make a project out of asking them about security and how they could better improve security.  Do it right, and the same people who would have destroyed your life might make you an admin.

---

### Post by oceania68 on 2010-01-04
> **Skripka said:**
> [IMG]http://api.ning.com/files/NShDyS7CREO3aOBNBZZB1Af6-qx70VP5Eglc66La4Fub5k2z2wzGKoReDxeb1M2skE4vHR2KROcO0ASmLYqtmvjh5MkxuxVR/633508100345116838ninjaconvention.jpg[/IMG]

:lolflag:

Funny bugga.... keep it coming, I like good humour...


And Mr Newbie.... Good onya.... And as far as schools computers not being yours, well they are the schools for the sole purpose of education... And every student has a right to use them or there own computer at school (hence wifi) but using ur usb stick on the "schools computer" does not rule out legit use... 

Now Was there and where was it any policy that says you "cannot" use a usb stick to boot to your own OS and use it.... regardless of it bypassing... it is seemingly obvious that they are NOT IT experts but a bunch of admins otherwise they would know about linux and would know that you can boot to an USB stick and indeed a live cd and hence bypass.... 

I suggest just keeping that information for yourself and do the work you need to do and DO NOT mess up THEIR computers... And at the end of your schooling..... when u get ur pieces of paper... Then tell em... and tell em how experienced they are.... hehehe .... The educational institution I attended last year had similar debates... In the end, WiFi came and we used out own... and they had set up printing and other services to use without touching their servers... (I then posed the question.. what good are ur servers if no is using them? lol... I can safely assume they didnt like me much... ) simply coz they were not IT pros... they were admins...

So it was new policies and procedures posted around and all users notified. Thats a little story to pass the time away with... :P  :popcorn:

---

### Post by Exodist on 2010-01-04
> **RiceMonster said:**
> They're not your computers, so you really shouldn't be booting from a usb stick, especially since it gives you full access to the hard drive, which you are not supposed to have access to.

Perhaps if you're really concerned you should talk to them and recommend they disable booting from optical media and usb devices.
This :)

---

### Post by Nerd King on 2010-01-04
Odds are the techs know nothing about linux. Windows specialists generally don't have a clue (linux specialists are unusual as they generally tend to have very strong windows skills but win and mac people tend to stick to their own). I would also point out that schools don't exactly hire the best usually, as the wider IT industry pays more, so you might get the odd teacher who's a real IT guru but is doing it cos s/he likes the kids (certainly not for the money!) but the tech staff are just whatever the school can get.
When I was at school I managed to hack the network very easily as basically it was put together by idiots. This was about 13 years ago, I was able to search for an off-the-shelf hack and use it there locally. I got everyone's passwords nice and easy and was able to remove the files of people I didn't like. I got away with it of course. However, if you've got anything between your ears you'll not follow my example!
The lesson here is physical access is root access. Linux is very good for repairing windows systems because of its ability to do stuff like this, it's a wonderful tool. Keep it to yourself as the admins will probably just blame you if anything goes wrong, don't make yourself a target.

---

### Post by MasterNetra on 2010-01-04
> **RiceMonster said:**
> They're not your computers, so you really shouldn't be booting from a usb stick, especially since it gives you full access to the hard drive, which you are not supposed to have access to.

Perhaps if you're really concerned you should talk to them and recommend they disable booting from optical media and usb devices.

A good point.

But yea, if you don't want to get into trouble and want them to know. Simply ask if booting in such a matter is ok. Don't tell them you did it and if they claim its not doable you could say that you've tried putting a password on your hard drive at home and was still able to access your windows drive with a linux CD/DVD. And suggest that if they haven't disabled booting from the USB as well as the CD/DVD from BIOS to do so. (Just don't make it sound like you actually know that its enabled. Otherwise they will probably gathered you've tried it already.) Of course it be best not to boot from your USB or CD/DVD as they might watch you a little more closely for a bit. ^.^

---

### Post by Frak on 2010-01-04
> **Nerd King said:**
> When I was at school I managed to hack the network very easily as basically it was put together by idiots.

Explain to me what this *hack* did. I'm curious.

As for the OP, the Sys. Admins are betting that you know nothing about computers. Trust me, students, while the instructors think they know everything under the sun about computers, are very limited in their knowledge of computers (past using proxies to view their Facebook wall, OH, IT UPDATED). It's not that the admins are dumb, it's because this method took less time, less effort, and can be enforced by a contract. Besides that, the parts are easily replaceable. If you pose a threat to the network, you are blocked from having access. Continue, you are suspended or expelled from the institution. It's that simple.

---

### Post by lisati on 2010-01-04
When I was at university I had a small share of being accused of stuff, pity Linux wasn't around in those days. Example: I'm waiting in the computer lab for their (then) shiny new IBM Series/1 to boot up so could log in as myself. I'm idly tapping my fingers, twiddling my thumbs and similar activities while at the terminal. At some point I press "Enter" to see if there's a response. The next thing I know, the terminal has been logged in as someone else, and the operator (who has noticed some kind of warning on the main console about an off-campus student) wanders through to find out why I'm using someone else's account.... This happened more than once. Awkward.

---

### Post by Warpnow on 2010-01-04
Even if they changed the boot order to stop you from booting from a thumb drive, and passworded the bios, all you'd have to do is wait until no one's around and pop the cmos battery out of the computer, which can be done in under a minute, and the bios would reset the next time the computer was turned off for any decent amount of time.

---

### Post by NoaHall on 2010-01-04
> **Warpnow said:**
> Even if they changed the boot order to stop you from booting from a thumb drive, and passworded the bios, all you'd have to do is wait until no one's around and pop the cmos battery out of the computer, which can be done in under a minute, and the bios would reset the next time the computer was turned off for any decent amount of time.

I've already said this :)

---

### Post by Nerd King on 2010-01-04
> **Frak said:**
> Explain to me what this *hack* did. I'm curious.

As for the OP, the Sys. Admins are betting that you know nothing about computers. Trust me, students, while the instructors think they know everything under the sun about computers, are very limited in their knowledge of computers (past using proxies to view their Facebook wall, OH, IT UPDATED). It's not that the admins are dumb, it's because this method took less time, less effort, and can be enforced by a contract. Besides that, the parts are easily replaceable. If you pose a threat to the network, you are blocked from having access. Continue, you are suspended or expelled from the institution. It's that simple.
Basically it gave me sysadmin access. This was years ago (I'm old) so I'm a little fuzzy on the details and I was fairly new to PCs at the time having been previously an avid Atari ST user. This was 1996 dude! As I recall the network had some Novell crap running on it that was a little lacking in security.

---

### Post by Crunchy the Headcrab on 2010-01-04
@ OP: You can do the same thing with MOST linux installs.  Point being, unless your drive is encrypted, you are not safe when somebody is in physical reach of it.  :)

---

### Post by CharlesA on 2010-01-04
It's pretty much the whole deal of physical access == all access.

That's already been said a few times.

The couple schools I went to had a proxy on the gateway to do content filtering and intrusion detection. Had one time when someone got on myspace by using a web proxy, sys admins got an email and the instructor was forwarded the IP, MAC and hostname of the machine.

That was a good job with network security. Too bad not all schools have the resources (monatary of skill-wise) to configure the network as such.

---

### Post by Dark Aspect on 2010-01-05
Are we talking about High school or College? I've hack the hell out the computers at my college directly in front of staff members and no one ever says anything. I figured the worst thing that can happen is that they ask me to leave, I doubt anyone is going to get into trouble for booting off of a thumb drive.

---

### Post by nanotube on 2010-01-05
a word of sage advice:

say nothing to anybody, and keep it secret.

school administrators are /usually/ semi-incompetent buffoons, and are just out to keep their job. (think about it - if /you/ were any good at computers, would /you/ be stuck administering some school computer lab? i didn't think so.) they are thus likely to blame you for all sorts of crap, just to avoid looking bad.

use your usb boot trick to your advantage, but do /not/ break anything or touch anything on the HD, and do /not/ tell anyone about it. ideally, 'anyone' also includes your friends, but realistically i know it's hard to avoid bragging :). but certainly do /not/ go and 'report' anything.

if the word of a random guy on ubuntu forums isn't enough, see this article on bruce schneier's blog:
[http://www.schneier.com/blog/archives/2006/05/dangers_of_repo.html](http://www.schneier.com/blog/archives/2006/05/dangers_of_repo.html)

---

### Post by Duhnali on 2010-01-05
now i'm interested in attempting that on my school's computers. :lolflag:

---

### Post by jayze on 2010-01-05
My advice would be to decide to be grown up about it and use the facilities that are there for your use..BUT swear yourself a solemn oath that you will use them responsibly and carefully..and carry on...if it comes up in conversation or you are asked about it you can just tell them the truth in a grown up manner. Remember that society (in this case school) exists for the people (not the people for the school) but also that you have to pay back by behaving responsibly. Not all rules and regulations are sensible or for our own good. Each of us has to decide (as adults) how to deal with that. enjoy! hope this helps you a bit:popcorn:

---

### Post by sdowney717 on 2010-01-05
since you said you can access sites and download things the school has deliberately blocked, they will consider you a lawbreaker if they find out.
At my wife's school, they are extremely paranoid about any attempts to get around school computer policies. One of their major fears is someone changing GRADES. Ignorance is blissfully ignorant. Using linux on a thumbdrive to get around computer security policies will reinforce unenlightened people into thinking linux is for hackers.

---

### Post by pwnst*r on 2010-01-05
> **RiceMonster said:**
> They're not your computers, so you really shouldn't be booting from a usb stick, especially since it gives you full access to the hard drive, which you are not supposed to have access to.

Perhaps if you're really concerned you should talk to them and recommend they disable booting from optical media and usb devices.

^^ This.  Please mark thread as solved. Thanks.

---

### Post by pwnst*r on 2010-01-05
> **Dark Aspect said:**
> I've hack the hell out the computers at my college directly in front of staff members and no one ever says anything. 

I believe you.

---

### Post by nanotube on 2010-01-05
> **pwnst*r said:**
> 
> 
They're not your computers, so you really shouldn't be booting from a usb stick, especially since it gives you full access to the hard drive, which you are not supposed to have access to.

Perhaps if you're really concerned you should talk to them and recommend they disable booting from optical media and usb devices.

^^ This.  Please mark thread as solved. Thanks.

says one nicknamed 'pwnst*r'. *grin*

---

### Post by pwnst*r on 2010-01-05
> **nanotube said:**
> says one nicknamed 'pwnst*r'. *grin*

Yes, because the word "pwn" has everything to do with hacking and nothing to do with gaming or otherwise.

Thanks for playing.

---

### Post by Frak on 2010-01-05
> **pwnst*r said:**
> Yes, because the word "pwn" has everything to do with hacking and nothing to do with gaming or otherwise.

Thanks for playing.
What'd I win?

---

### Post by pwnst*r on 2010-01-05
I just shredded some confidential docs.  Want a bag of that?

---

### Post by Frak on 2010-01-05
> **pwnst*r said:**
> I just shredded some confidential docs.  Want a bag of that?
Ummm... yes.

---

### Post by scottuss on 2010-01-05
I booted from an Ubuntu stick whilst at Uni. I don't mind openly admitting it. They expected things to be word processed, internet researched etc and if they honestly expected me to use their steaming piles of sad excuses for Lab computers, they would have needed to pay me instead of the other way around.

Windows took around 7 to 8 minutes to get from login to a usable desktop, and then, when "usable" it was so slow and restricted it was almost funny.

My Ubuntu stick took around 2 to 3 minutes to boot and then was speedy as anything. Content restriction etc was still in place because everyone knows you should do that at the gateway, not on the client machine (this is one of the few things the uni admins got right!)

I don't want to sound like an a** but I refused to use Windows. I told them about the millions of problems their computers had but they never listened, so I took it into my own hands. They allowed USB booting in the BIOS, so why wouldn't I? (P.S: I told them I was doing it and they never said not to)

I never did / accessed anything I shouldn't and I got my work done, so who did I hurt?

Inform them of their computer's issues and then if they don't listen, let them know you intend to boot from USB, then just do it.

---

### Post by nanotube on 2010-01-05
> **pwnst*r said:**
> ^^ This.  Please mark thread as solved. Thanks.

> **pwnst*r said:**
> Yes, because the word "pwn" has everything to do with hacking and nothing to do with gaming or otherwise.

Thanks for playing.

yes, because in the context of making a joke, i get to ignore alternative meanings of words that do not help me make the joke. 

you, panties, untwist, etc. :P

---

### Post by whiskeylover on 2010-01-05
> **scottuss said:**
> I booted from an Ubuntu stick whilst at Uni. I don't mind openly admitting it. They expected things to be word processed, internet researched etc and if they honestly expected me to use their steaming piles of sad excuses for Lab computers, they would have needed to pay me instead of the other way around.

Windows took around 7 to 8 minutes to get from login to a usable desktop, and then, when "usable" it was so slow and restricted it was almost funny.

My Ubuntu stick took around 2 to 3 minutes to boot and then was speedy as anything. Content restriction etc was still in place because everyone knows you should do that at the gateway, not on the client machine (this is one of the few things the uni admins got right!)

I don't want to sound like an a** but I refused to use Windows. I told them about the millions of problems their computers had but they never listened, so I took it into my own hands. They allowed USB booting in the BIOS, so why wouldn't I? (P.S: I told them I was doing it and they never said not to)

I never did / accessed anything I shouldn't and I got my work done, so who did I hurt?

Inform them of their computer's issues and then if they don't listen, let them know you intend to boot from USB, then just do it.

Thats not really the point. The computers belong to them, and you have to agree to their TOS to use them.

Its like me borrowing your car keys. You only give me permission to take it to Walmart, get groceries, and drive back. I, instead, bang hookers in it. I do make sure there were no stains. Nobody got hurt, right?

---

### Post by Exodist on 2010-01-05
> **whiskeylover said:**
> Thats not really the point. The computers belong to them, and you have to agree to their TOS to use them.

Its like me borrowing your car keys. You only give me permission to take it to Walmart, get groceries, and drive back. I, instead, bang hookers in it. I do make sure there were no stains. Nobody got hurt, right?
LOL very well said..

---

### Post by scottuss on 2010-01-05
> **whiskeylover said:**
> Thats not really the point. The computers belong to them, and you have to agree to their TOS to use them.

Its like me borrowing your car keys. You only give me permission to take it to Walmart, get groceries, and drive back. I, instead, bang hookers in it. I do make sure there were no stains. Nobody got hurt, right?

Firstly, I didn't agree to anything.

Secondly, yeah as long as I don't know you did whatever you did with the hookers, it hasn't hurt me. I don't mean this to sound arrogant, but it's not quite the same. The analogy doesn't work. Uni knew what I was doing, they never said I couldn't do it. If they told me not to, I would have respected this.

---

### Post by nanotube on 2010-01-05
> **whiskeylover said:**
> Thats not really the point. The computers belong to them, and you have to agree to their TOS to use them.


if the tos said "you are not allowed to boot from your own boot disk", ok. but the tos probably just says "do not do anything illegal, acceptable use policy, bla bla, bla bla". as long as booting your own os is not prohibited (including that you are not indirectly explicitly violating any of it), and as long as computers are provided for you to use productively, what's wrong with it, then?

> 
Its like me borrowing your car keys. You only give me permission to take it to Walmart, get groceries, and drive back. I, instead, bang hookers in it.

no, it's /not/ like that. in your analogy, the permitted use gave a specific whitelist of activities, which you explicitly violated. in the computer lab tos, the permitted use uses a /blacklist/ of activities, which, as long as it doesn't include booting your own os, you are not violating.

if you want to make a good analogy out of this, it would be this: you borrow my car for the day. i tell you, as long as nobody gets hurt and my car is returned without any damage, it's yours for the day. have fun. you, in turn, do whatever it is you decide to do in it, without violating my blacklist. and then i say:

> 
I ... bang hookers in it. I do make sure there were no stains. Nobody got hurt, right?

right!

---

### Post by doas777 on 2010-01-05
> **whiskeylover said:**
> Thats not really the point. The computers belong to them, and you have to agree to their TOS to use them.

Its like me borrowing your car keys. You only give me permission to take it to Walmart, get groceries, and drive back. I, instead, bang hookers in it. I do make sure there were no stains. Nobody got hurt, right?

but remember, if that car was OSS, then picking up some denizens of the night would be allowed by freedom 0: "The freedom to run the <car>, for any purpose". this obsession with TOS is directly antagonistic to the concept of open source.

but op, just keep your mouth shut. they already know that the hole is there.

---

### Post by Shpongle on 2010-01-05
> **Skripka said:**
> I think most lab admins would NOTICE you and your screwdriver pulling apart a computer tower, to get at the BIOS jumper or battery :)
also some machienes can be locked physically , so youd have to pick the lock first ;)

---

### Post by 00ber n00b on 2010-01-05
Exploit the system to the fullest!

---

### Post by t0p on 2010-01-05
I agree with those who say don't tell.  There are 2 reasons.  You may very well get into trouble for practicing black arts. Schools are very sensitive about their networks.  Even if you're not burned at a witch, you will lose the ability to boot Linux.  I'm sure that once an admin learns of the problem, he will do something about it.  Password-protect the BIOS or something.  So stay quiet.  It's pretty unlikely anyone will use a live usb to do evil at your school anyway.

---

### Post by Linux Army on 2010-01-05
My partner works as a teacher and one of her collegues wanted to boot of a live cd and she got a written warning as. A company blamed her for a virus intrusion.

---

### Post by koleoptero on 2010-01-05
> **whiskeylover said:**
> Thats not really the point. The computers belong to them, and you have to agree to their TOS to use them.

Its like me borrowing your car keys. You only give me permission to take it to Walmart, get groceries, and drive back. I, instead, bang hookers in it. I do make sure there were no stains. Nobody got hurt, right?

What a colourful example.

---

### Post by pwnst*r on 2010-01-05
I liked it.

---

### Post by Old_Grey_Wolf on 2010-01-05
> **BT1 said:**
> ...Bad thing is they do not allow installation of freeware stuff like firefox updates (flash download and install not allowed)...

Based on what you wrote, I think you know that you shouldn't be doing what you have done.

Based on your profile, I think you probably go to some university like UTA, UTD, UNT, or similar. 

They can see audits of network access, and access to servers. You leave a trail of your activities even if the computer you are using isn't booted in their preferred OS. 

Don't do it anymore and just move on.

---

### Post by sdowney717 on 2010-01-07
> collegues wanted to boot of a live cd and she got a written warning as. A company blamed her for a virus intrusion.

typical expected reaction, put the blame for a virus on an unknown OS, regardless of the truth. IT people look at this as infringing on their space. They are responsible for the systems and dont want it mucked up.
It is a control issue for sure, the way to deal with this is develop a good relationship with them and show them how it can work properly installed. You know that booting a live usb/cd gives you access to the hard drive and bypasses security for the drive in that system.

---

### Post by pwnst*r on 2010-01-07
> **Linux Army said:**
> My partner works as a teacher and one of her collegues wanted to boot of a live cd and she got a written warning as. A company blamed her for a virus intrusion.

Well, blaming is over the top, but inquiring and being suspect is right on target if it happened within the same time frame.

---

### Post by lisati on 2010-01-07
> **Dark Aspect said:**
>  I've hack the hell out the computers at my college directly in front of staff members and no one ever says anything. 

Although it's possible that they don't care, it's also possible that they trust you. Don't, however, immediately expect the same level of trust elsewhere...... As others have said, it's *their* computers, and it's up to them to set boundaries.

---

### Post by chriswyatt on 2010-01-09
> **staf0048 said:**
> Just a thought... could you do it anonomously?

set up an email address (e.g. [email]internet-batman@hotmail.com[/email]) at an internet cafe and post from there. :)

---

### Post by BT1 on 2010-02-15
Well here's an update.

The store that I work for is the university bookstore, and there's been over a dozen issues with printers/scanners/fax machines/ and general windows buggery that I've repaired since I've worked there. I got smart after the second time I saw the troubleshooting guy walk in (who happens to run most of the school network as the sub-systems administrator). I've been wanting to work in the student support center for some time, which is a bunch of students that help fix people's computers when students walk in and drop them off. They only require a certain level of familiarity with Windows in order to be there. That troubleshooting guy happens to be good friends with both the systems admin and the admins at that support center, so I decided I'd try to display my ability since it's mostly a recruitment type of hiring system. Applications are taken, but you're more sure to get a job there if you can show you know what you're doing.

So I started fixing the computer issues right after my manager calls the guy to come fix stuff, and when he gets there I've got it fixed with a smile on my face. After a while the guy started telling my manager to get me to work on stuff. Well I'm friends with that guy and I e-mailed him about the issue that started this thread and he laughed and said I'd have to ask the systems admin for the whole campus and that I shouldn't worry because he's a nice fellow that plays poker with him on the weekends.

I found that guy's e-mail and sent him an e-mail about it and he said that it wasn't something that they were going to change due to some stuff with the student workers who work on the computers. Two days later the troubleshooting guy walks in and offers me a job with his student staff if there's a position open, so I said yes enthusiastically. Well it fell through and he immediately went to the student support center and talked with the big wigs there, and they offered me a position there. My student worker aid fell through this semester but I'm promised a position there for the rest of my school career lol. 

When I get there, I'm going to work hard on them to get them officially supporting Linux. They're mostly ignorant about it right now which is why they're not supporting it, but once I show that all they need to do to support Linux systems on the network is manually add Linux user MAC addresses to the list of allowed MAC IDs, they should be more supportive[SIZE=4][COLOR=Red]*[/COLOR][/SIZE].

I think the only reason why this turned out good is because I was cautious and made sure I was on good terms with the people who ran the system.

Thanks for the support and advice in making my decision :D

[SIZE=4][COLOR=Red]*[/COLOR][/SIZE]*currently Linux distros are blocked because the university makes you download a file that checks your network settings and devices and reports back to a server that your system is acceptable. This file only runs on Windows and Mac, Linux is left in the cold. (and no it won't run on WINE) In summary it checks to make sure your system is compatible, and then adds your MAC address to the approved list.*

---

### Post by Sef on 2010-02-15
Thank you for the update.

---

### Post by markbuntu on 2010-02-15
Bug the library to get a subscription to linux pro magazine.

---

