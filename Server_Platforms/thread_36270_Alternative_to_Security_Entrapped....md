---
title: "Alternative to Security Entrapped..."
date: 2005-05-22
forum: Server Platforms
---

### Post by redboar on 2005-05-22
Is there any other security alternative, whether or not kernel based, for the government sponsored and/or promoted one bulit into Ubuntu which is enabled by default?  I cannot seem to uninstall its libraries without crippling the gdm package.  I don't mean to insult anyone or start a troll, but being a linux newbie I was quite disturbed when I found out who and what is involved with Linux (and apparently some BSDs) security without any disclaimers or choices.

---

### Post by LordHunter317 on 2005-05-22
[QUOTE=redboar]Is there any other security alternative, whether or not kernel based, for the government sponsored[/quote]What government sponsored security system?  Are you talking about SELinux?  That's not enabled OOB AFAIK on any current Ubuntu release.

>  I cannot seem to uninstall its libraries without crippling the gdm package.What libraries?  Not being specific doesn't help anyone.

>  I don't mean to insult anyone or start a troll, but being a linux newbie I was quite disturbed when I found out who and what is involved with Linux (and apparently some BSDs) security without any disclaimers or choices.What about it?  I honestly have no clue what you're talking about here, so you need to be more specific.

---

### Post by redboar on 2005-05-23
I don't know what OOB AFAIK stands for, and yes it is most definitely enabled by default.  How do I know this?  Here are some specifics:

1) I discovered a file named libselinux1 on my newly installed Ubuntu Hoary partition.  When I tried to "sudo apt-get remove libselinux1", it wanted to remove gdm, among other files.

2) I was brave enough to let it remove and chose xdm as an alternative.  Then if I tried running any administrative program like Synaptic, I got some X.authority error and it never opened.  I tried living with running everything I could from the console, but because I cannot seem to view any icon properties in Gnome's menus, I gave up this approach.

Since then I reinstalled Ubuntu once or twice on my system.  It seemed to really not like an extended partition I USED to have on my hard drive LOL, but that's another story.  This transition from the M$ world has been no walk in the park and I am truly amazed that a federally funded program is included in an OS meant for geek rebels.

I know I seem a little advanced for a noob, I got my start in computers back in the Windows 3.x days when you had to edit .ini files every now and then.

---

### Post by LordHunter317 on 2005-05-23
[QUOTE=redboar]I don't know what OOB AFAIK stands for, and yes it is most definitely enabled by default. How do I know this? Here are some specifics:[/quote]OOB = Out Of Box
AFAIK = As Far As I Know.

> 1) I discovered a file named libselinux1 on my newly installed Ubuntu Hoary partition. When I tried to "sudo apt-get remove libselinux1", it wanted to remove gdm, among other files.Right, because it depend on that library.  But the presence of libselinux1 doesn't mean that SELinux is actually being used.

The important bits of SELinux are in the kernel.  Ubuntu likely compliles SELinux support into the kernel using the mainline version (which is generally slightly out-of-date), but leaves it disabled on boot.  They also don't provide any policies of note, so even if it were enabled, it wouldn't do anything useful (besides maybe completely lock you out of your system).

Unless you can show me output from the kernel showing SELinux on, I'm not going to believe you.  You're being paranoid with no good reason, and it's clear you don't understand the components your'e dealing with.

> I know I seem a little advanced for a noobNo, you don't.  You'd do well to go read about these things you seem so worried about instead of tooting your own horn.

>  I got my start in computers back in the Windows 3.x days when you had to edit .ini files every now and then.Wow.  So did a lot of us.  That could make you as young as about 17 or as old about about 97.

---

### Post by nocturn on 2005-05-23
As long as a system is provided as Free Software, I do not see the problem...

---

### Post by teevee on 2005-05-23
[QUOTE=nocturn]As long as a system is provided as Free Software, I do not see the problem...[/QUOTE]
Yup. If you suspect Big Brother is watching you, check the source. It's openly available under the terms of the GNU GPL:
[http://www.nsa.gov/selinux/](http://www.nsa.gov/selinux/)

But you can be sure thousands others did check it as well before. ;-)

---

### Post by LordHunter317 on 2005-05-23
Anyone with even the slighest understanding of what SELinux is and what it does would understand why it'd be somewhat silly for the NSA to try to insert a backdoor or any sort of monitoring or phone-home utilities in it.

Ignoring the fact it's open-source and it'd be easy to find out, it'd just lower the security provided too far to be extremely useful.

---

### Post by redboar on 2005-05-23
[QUOTE=LordHunter317]
Unless you can show me output from the kernel showing SELinux on, I'm not going to believe you.  You're being paranoid with no good reason, and it's clear you don't understand the components your'e dealing with.

No, you don't.  You'd do well to go read about these things you seem so worried about instead of tooting your own horn.

Wow.  So did a lot of us.  That could make you as young as about 17 or as old about about 97.[/QUOTE]

Perhaps the last line was tooting my own horn a bit, from this perspective I'm not comparing myself to computer science majors and people who grew up with computers since elementary school.  More often do I meet a person who can't understand the difference between a file and a folder, and by no means would they understand the steps I took above to remove libselinux1, let alone recognize it's there.

In the Windows world, which I'm familiar with to a degree most Linux advocates I've met are not, and perhaps hate this world more than they do and also respect it much more, the presence of a library or dll file is a sure sign it's being used.  Now I can assume it's being used to a limited sense or that as another poster put it, "thousands of others" have desected its sources and found nothing of harm.  If I was the one who compiled it or enabled any of its functionality then I'd be rest assured of that.

I suppose I said some insulting comments in my post above for those who come onto this forum on a regular basis and attempt to be helpful.  At this point I've gotten the answers to my questions that I needed.  I've decided to erase Ubuntu from my hard drive.

I've already lost gigs of data and hundreds of hours and when I post a simple question regarding another government intrusion during the Shrub era LOL, I'm getting the same pat answers and once again the "investigate it yourself" attitude so prevalent from the Linux crowd.  Let's put aside the politics for a second, so I can tell you I've had more trouble finding a distro that supports an Nvidia graphics card, integrated sound, and yes even handling an extended partition that somehow got set up wrong since I used an M$ product to create it, than it has been proven worth doing in the first place.  I would think that if part of the creation of this forum were about advocacy and helpfulness, it would at least show more understanding than this "red pill vs. blue pill" childish mentality that I've encountered.  And this is not the only place I experience it in relation to Linux.  It's a shame that an OS with tremendous potential is continually being pulled down by the lack of social skills and the callousness of the community behind it.

Take care.

---

### Post by LordHunter317 on 2005-05-23
> **redboar]let alone recognize it's there.[/quote]**But you don't, and that's the problem**.

> In the Windows world, which I'm familiar with to a degree most Linux advocates I've met are not,You need to drop the presumptions, as they're simply doing nothing more than proving you to be an ignorant, arrogant paranoid said:**
>  the presence of a library or dll file is a sure sign it's being used.Utter nonsense. You clearly don't understand how shared libraries are used. I'd recommend taking several courses in computer science and software engineering, or system administration so you can understand how shared libraries work and how the presence of a piece of code on your harddrive doesn't mean it's being used.

By your logic, every application I've installed must be running all the time, and every library I have installed must be running all the time. Yet OpenOffice current isn't running, but I have it installed, so your reasoning must be false.

>  Now I can assume it's being used to a limited senseYou can safely assume it's not being used at all as **SELinux is *disabled* on your system**.  The only way it can be enabled is if ***you*** turned it on.

>  At this point I've gotten the answers to my questions that I needed. I've decided to erase Ubuntu from my hard drive.And if you understood the answers you had gotten, you wouldn't have done something so stupid and drastic. ](*,)

> Let's put aside the politics for a second, so I can tell you I've had more trouble finding a distro that supports an Nvidia graphics card,I can think of about 10.

>  integrated sound,I can think of about 6. Though some of the newest integrated chips aren't very well supported yet, since support is still be written for them.

> I would think that if part of the creation of this forum were about advocacy and helpfulness, it would at least show more understanding than this "red pill vs. blue pill" childish mentality that I've encountered.There was none of that in this thread, mearly a childish paranoid worrying about things he doesn't understand and comprehend.

> It's a shame that an OS with tremendous potential is continually being pulled down by the lack of social skills and the callousness of the community behind it.It's difficult to help people who are unwilling to help themselves and turn on anyone who tries to help them. The dog who bares his teeth at anyone who walks by tends to get beaten, not petted.

> Take care.No, you do.  Hope you don't see any black helicopters.

---

### Post by redboar on 2005-05-23
[QUOTE=LordHunter317]**But you don't, and that's the problem**.

You need to drop the presumptions, as they're simply doing nothing more than proving you to be an ignorant, arrogant paranoid; and they're also quote wrong.

Utter nonsense. You clearly don't understand how shared libraries are used. I'd recommend taking several courses in computer science and software engineering, or system administration so you can understand how shared libraries work and how the presence of a piece of code on your harddrive doesn't mean it's being used.

It's difficult to help people who are unwilling to help themselves and turn on anyone who tries to help them. The dog who bares his teeth at anyone who walks by tends to get beaten, not petted.

No, you do.  Hope you don't see any black helicopters.[/QUOTE]


You jackass, I didn't accept the help you offered so you get your panties in a bunch?  The help I wanted was to REMOVE ANY TRACE OF SELinux ON MY INSTALLATION AND INSTALL AN ALTERNATIVE.  Anything short of this is excuses and lecturing.  Please scan what you and your buddies wrote above, I was told I was paranoid, simple minded, arrogant and childish.  I don't care to leave my PC open to any parties, public or private, and that turns me into a guy looking for black helicopters?  By the way, what are they and why should I watch for them?!?

I'm looking for an alternate OS as you cook up another clever reply!  Maybe the one I find will consist of users and developers who don't live in front of their PCs and live to tweak text files all day rather than seek a sex life.

Help myself?  I do that by staying away from my computer as much as possible while it does work for me, you know, what a friggin computer was invented for in the first place!!!  I'm not taking any computer science courses.  They are nerdy.  LOL

If we ever meet it's you who may get the beating of your life, not I.

---

### Post by teevee on 2005-05-23
Oh, wasted time trying to help someone who apparently just searched for an excuse to flame around, silly me.

---

### Post by LordHunter317 on 2005-05-23
[QUOTE=redboar]You jackass, I didn't accept the help you offered so you get your panties in a bunch? [/quote]No, you tried to bait me and debate about things you don't understand.

>  The help I wanted was to REMOVE ANY TRACE OF SELinux ON MY INSTALLATION AND INSTALL AN ALTERNATIVE.And I calmly pointed out that what portion of SELinux was compiled on your system wasn't capable of doing anything, as the kernel portion of SELinux has been disabled.  

You're worrying about the razor handle when the blade isn't anywhere to be found.  You're going to be hard pressed to cut yourself on the handle, or have anyone else do it.

> I was told I was paranoid, simple minded, arrogant and childish.You are be.  You've been told in no uncertain terms that you're worrying about nothing.  Had you come back and simply said, "I understand that, and I still want to remove it," I would have gladly outlined what you need to do.

But that's not you did.  You came back tooting your own horn and suggesting incorrect reasoning for why your concerns were valid.  Which I then proceeded to refute.  

Your inability to accept the truth in this situation merely reinforcement the above claims about your person.

>  I don't care to leave my PC open to any parties, public or private, and that turns me into a guy looking for black helicopters? That's just the thing.  You haven't shown how having SELinux installed leaves your computer open to parties, public or private.  And worrying about somethign with no justification is the definition of the paranoia, I might add.  

You're acting like every other tinfoil-hat wearing computer security paranoid out there.  You want to do things without understanding the implications or reasoning.  You probably don't even know what SELinux does or how it's implemented, and you're  hellbent on removing it mearly due to some of its authors.

Nevermind the fact that it's open source.  Nevermind the fact if you understand what it was meant to do, you'd understand why suggesting it would have a backdoor is somewhat silly.  

>  and live to tweak text files all day rather than seek a sex life.I have a perfectly normal and healthy sex life, thank you very much.

> Help myself?Yes.  You're the one who has an issue, and you refuse to get off your high-horse for even 30 seconds to learn what you're so desperating seeking.  

> I'm not taking any computer science courses. They are nerdy. LOLWell, then you may never understand these things you worry about so much.

> If we ever meet it's you who may get the beating of your life, not I.OMG I've been threatened by someone on the Internet.  OH NOES WHATEVER WILL I DO!!!!11111oneone.
Grow up, seriously.  And you wonder why I called your behavior childish.  I can tell you that you're wrong without resorting to threating ones life.

---

### Post by jdodson on 2005-05-23
it is unfortunate members of the ubuntu community resort to name calling and user bashing and threats of violence when someone does not understand something well.

it is unfortunate that we must sling rocks at each other to save face.  

i am unimpressed with this thread.

this thread is now locked.

please read up on the ubuntu philosophy of community(code of conduct) please, it will do you well to know it for future dealings on this forum.   [http://www.ubuntulinux.org/community](http://www.ubuntulinux.org/community)

to the originator of this post: i would recommend you stick with ubuntu a bit longer.  ubuntu completley rocks for nvidia 3D support, check my post here in regards to that:  [http://ubuntuforums.org/showthread.php?t=25723](http://ubuntuforums.org/showthread.php?t=25723)

most people have found the community to be quite pleasant.  i think that if all parties remember what ubuntu actually means and attempt to do that on the forums, they will be free from this form of abuse(both parties are culprits of this).  

as far as selinux, it is not enabled by default.  i am not totally sure why that file is included.  however, i know it is not setup by default.  in the future this might change, however now, the only distro i know to do this be default is fedora.

if you have any other questions or comments, please post or PM me directly if you wish.

and btw, i graduated with a computer information science degree, program, edit text files and have sex(though rarely at the same time).  i think it would serve you well to realize that rampant generalizations originate from a weak arguement.

threats of physical violence are not tolerated on these forums FOR ANY REASON! see you made me use caps.  do NOT repeat that mistake again.

---

