---
title: "You're Fired"
date: 2011-04-30
forum: Server Platforms
---

### Post by Vegan on 2011-04-30
Given my server has crapped out again with a total file system error. I refuse to endure repeated problems resulting in catastrophic data loss.

I have Window Server licenses, so Linux, you're fired.

---

### Post by crispy_420 on 2011-04-30
Bye I guess.

---

### Post by hansdown on 2011-04-30
> **Vegan said:**
> Given my server has crapped out again with a total file system error. I refuse to endure repeated problems resulting in catastrophic data loss.

I have Window Server licenses, so Linux, you're fired.

Ummmmm..., sorry?

---

### Post by elico on 2011-04-30
tell me you used ext4 and i would ask? did you tried to recover the files using UFS EXPLORER?

by the way..
if you do feel safe with windows...
now it's the time to learn a lesson in computers.. backup backup backup...

i will not try to convince you to use linux cause you might not need it.

---

### Post by wojox on 2011-04-30
> **Vegan said:**
>  catastrophic data loss.

No such thing when you back up.

---

### Post by tgalati4 on 2011-04-30
What was the hardware and what was the failure?

I have found Ubuntu server to be pretty good (uptime of several YEARS).  Runs well on my Dell poweredge rack servers.

---

### Post by CharlesA on 2011-05-01
> **tgalati4 said:**
> What was the hardware and what was the failure?

I have found Ubuntu server to be pretty good (uptime of several YEARS).  Runs well on my Dell poweredge rack servers.

I'm curious as well. I haven't run it on "server grade" equipment, or in an enterprise environment, but I haven't had any problems with file system corruption at all. *knocks on wood*

In any case - use what works best for you. :)

---

### Post by |{urse on 2011-05-01
> **Vegan said:**
> Given my server has crapped out again with a total file system error. I refuse to endure repeated problems resulting in catastrophic data loss.

I have Window Server licenses, so Linux, you're fired.

NOOOOO! Linux has kids to feed! Wait.. How much were you paying Linux again?

---

### Post by terrapin893 on 2011-05-01
A server administrator is only as good as his last backup.  No matter what operating system you may be running.

---

### Post by elico on 2011-05-01
i'm running a nice server on an intel atom 410D and without any problem for the last unknown time since i have installed the os.
i'm running on a MSI laptop (with acpi=off) for the last couple of month without any problem.
on the same laptop also installed Gentoo works ok no problem.
on a production server using desktop HW CORE2QUAD + lots of space + lots of ram + crappy lan + intel expensive dual lan
no problem since 3 month ago.

the only problem was when i did a migration from small disk to larger disk.
i made a backup booted the OS from the backup and after 5 hours the backup drive FS got corrupted by an unknown reason so i had to find a way to get some very very long scripts i wrote.(i did had a backup and was using it...)
so the only Recovery software i have found for ext4 was UFS EXPLORER that really could get me a result
(as long as i didnt write any data to the drive)
i got 155GB out of 160GB restored.

after this incident i found out that the problem was a bad sector on the BACKUP HD.
(go to hell WD crappy old drive. and fool me to use a 2 years old WD HardDrive for backup without checking the drive surface).

---

### Post by rubylaser on 2011-05-01
Sounds like a hardware failure (hard disk), and a good situation for backups.  Anyways, enjoy Windows, and all the fun / reliability / uptime that brings ;)

---

### Post by bdaman80 on 2011-05-01
No Body made you be here, thats the great thing about FOSS is choice.

Dont let the door hit ya.............

---

### Post by Vegan on 2011-05-01
The machine is not at fault, I put XP back on the machine and turned it off.


I am very annoyed with the problem of the root system disappearing and totally trashed. That is unacceptable.

Windows never crashed like Unbuntu has. It has crashed 4 times on me, Windows on the same machine is fine.

This suggests the OS is at fault.

Dodgy system need not apply.

---

### Post by elico on 2011-05-01
i know this guy that maintaining servers and he is like:
"linux linux linux"
but he doesnt have any real touch into it.
every time he gets into trouble you dont want to know what happens.
so dont get into your head "linux"
or 
"OS"
the dancer dosnt know how to dance so he is saying that the flood was slippery.

i'm not a "linux linux linux" guy.
you need to be smart and to know and understand what you are doing.
the main problem is that it happen to you 4 times and instead of understanding and asking after the first time
you got wasted 4 times more then you needed to.

it's an opportunity to learn without any connection to linux:
before you run a system make a big assessments of the system in money loss.
then in a case you have impotent data.. spend time and resources on making it (not OS related) redundant.
the only reason that one OS will be better then the other is the user and maintainer!!
you dont have the knowledge consult with anyone you can effort and take in mind that it's money you are talking about.
you might not understand or do understand but external HD cost 20-30$ and it worth any peny.
you want to test a system? test if for weeks or months.
instead of replacing the existing system think about migration..

you had problems with the root FS post here and meanwhile use another HD to operate the server.
the data is impotent to you? dont make sure that will never be able to recover some of it.

so the sum of all is:we are here to help you if you need it. :)

---

### Post by rubylaser on 2011-05-01
> Dodgy system need not apply.
As was said earlier, that's the great benefit of FOSS, take it or leave it.  Bashing it as "dodgy" seems like trolling.  If you don't know how to configure it or want to bother troubleshooting, just move along.  That's like bashing Windows for not working when you haven't installed the drivers...ridiculous.

This thread is a waste. You didn't post logs, you didn't provide any useful information for anyone to help you.  My filesystem is "thrashed"  and that it "crashed" don't count. That's something one of my clients would say, and it would require further questions and testing to find the problem, i.e: Is this a system that's been running for a while and suddenly started exhibiting this behavior, or is it a fresh install each time?  If it was an existing install, what was changed that caused the problem.  If it was a fresh install, what version of Ubuntu did you install? Questions like this would need to be answered to perform basic troubleshooting.  But, since you're obviously a Windows guy, that's fine, just move along, and stop trolling.

---

### Post by elico on 2011-05-01
im saying yes for trolling!!!!
why not?
it's good for everyone :)
and funny ;)

---

### Post by tgm4883 on 2011-05-01
No specifics, wide generalizations, no logs. Sounds like trolling.

---

### Post by Rasa1111 on 2011-05-01
My friend at the observatory has had an Ubuntu server running for 4+ years non stop. lol 
But he also keeps backups, just in case. :rolleyes:

---

### Post by koenn on 2011-05-01
> **tgm4883 said:**
> No specifics, wide generalizations, no logs. Sounds like trolling.

well, his filesystem blew up and he apperently doesn't have backups, so that's why no logs, maybe.

Probably a case of incompetent craftsman blaming the tools, rather than trolling. But still ...

---

### Post by akand074 on 2011-05-01
> **tgm4883 said:**
> No specifics, wide generalizations, no logs. Sounds like trolling.

Good catch. I think this is definitely trolling. His name is Vegan (meat trolling already, and meat is the worst thing to troll!) and his avatar is about positive reinforcement of Microsoft. There are plenty of other Linux-based distributions for servers, and anybody with a server knows well enough to have backups. So probably trolling, good one.

---

### Post by rubylaser on 2011-05-01
> Probably a case of incompetent craftsman blaming the tools, rather than trolling. But still ...
That's probably the best way to put it.

---

### Post by JohnWillyam on 2011-05-01
here's my bean.
 
for me, I find that most of the problem is between the keyboard and the chair...
 
:D
 
love, John

---

### Post by Rasa1111 on 2011-05-01
> **JohnWillyam said:**
> here's my bean.
 
for me, I find that most of the problem is between the keyboard and the chair...
 
:D
 
love, John

Yeah, my dad always told me that..
and I never believed or understood him until about 5-6 years ago. 
But it is a Truth I have come to learn, for sure. lol

 what's funny is when you say that to someone,
and they can't quite figure out what you mean...
*"hmm, between keyboard and chair... i cant think of any computer parts there..hmmm" * Lol!

Yet they expect to be able to work a computer properly. :lol:

---

### Post by akand074 on 2011-05-01
I remember a rather good quote:

"For every error blamed on the computer there is at least two human errors. One of which is blaming the error on the computer"

---

### Post by Rasa1111 on 2011-05-01
> **akand074 said:**
> I remember a rather good quote:

"For every error blamed on the computer there is at least two human errors. One of which is blaming the error on the computer"

haha! Good one, Im keeping it! lol :)

---

### Post by walt.smith1960 on 2011-05-01
"This suggests the OS is at fault.

Dodgy system need not apply."

My thought when reading the O.P.  was "Huh, it makes me wonder how Google and Amazon et. al. got where they are running dodgy systems"  I guess they couldn't find enough Microsoft Most Valuable Professionals









:P

---

### Post by howefield on 2011-05-01
Thread closed.

No support appears to be being sought. If wrong, the OP can let me know.

---

