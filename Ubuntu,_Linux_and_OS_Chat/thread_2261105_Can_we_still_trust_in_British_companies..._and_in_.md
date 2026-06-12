---
title: "Can we still trust in British companies... and in Ubuntu ? (relaxed version)"
date: 2015-01-16
forum: Ubuntu, Linux and OS Chat
---

### Post by Martin_Gerber on 2015-01-16
Now take all these facts plus the fact that Canonical is a British company and that Ubuntu is the most well-known Linux derivative.

I think it is no longer absurd that some programmers of Canonical might work for the GCHQ and that they already added some backdoors to Ubuntu that allow the GCHQ to remote-access every Ubuntu-PC and Ubuntu-server. In particular I think it is a doubtful quality assessment that the GCHQ itself awarded Ubuntu as the most secure OS [16].

I really hope for a clear statement of Canonical or of Mark Shuttleworth against total surveillance  - for example Canonical could move its head office away from the UK to some country that shows much less surveillance fanaticism.

What do you think about all this? Does the loss of trust in British companies also affect Ubuntu? Or is everything just fine and I am simply paranoid?

(Note: I am responsible for ~30 Ubuntu-desktop-PCs and 5 Ubuntu-internet/intranet-webservers, and I am really worrying whether I should stop using Ubuntu)

---

### Post by Martin_Gerber on 2015-01-16
(let me just copy&paste the answer of *mastablasta*, given in the other thread)

[I]the code is open. so what backdoors are you talking about? and what  kind of activities are you doing on desktops that would even attract  some government attention?

Cannonical doesn't create the OS from scratch, they repackage Debian,  add a few features, add some programs and you get Ubuntu in the end.  yes, you are paranoid.

if you feel you can't shake off the paranoia then use Tails, but you  will never know if anyone inserted anything into the OS unless you are  prepared to check all the code. another option would be to assemble your  own Linux from scratch.[/I]

---

### Post by Barsoom88 on 2015-01-16
Paranoia occurs when an event is NOT happening. Edward Snowden proved is was. Hence, no paranoia.

---

### Post by zombifier25 on 2015-01-16
> **Barsoom88 said:**
> Paranoia occurs when an event is NOT happening. Edward Snowden proved is was. Hence, no paranoia.

Elaborate? Because as far as we're concerned Ubuntu is a repackaged Debian, and its source code is completely open source. Any bug (as in tracking bug) inserted into the code would be discovered immediately by the maintainers.

---

### Post by howefield on 2015-01-16
Thread moved to the "Ubuntu, Linux and OS Chat" forum, and OP edited to comply with Code of Conduct.

---

### Post by grahammechanical on 2015-01-16
> [COLOR=#000000]I think it is no longer absurd[/COLOR]

It is the height of absurdity to make assumptions and then turn those assumptions into beliefs. It is even more absurd to then demand evidence that what you believe is false. And then to claim that as no one is providing evidence that the belief is false, then it must be surely be true and you were right all along.

Do you not realise that by using the internet to access this forum which is hosted on Canonical servers and by making such assertions you have exposed yourself to the very people that you wish to hide from? Now, if what you claim is not true, then we are safe talking about these matters.

I do not have to be a Vulcan to know that what you have done is illogical. The biggest security risk to those computers you are responsible for is the users of those machines themselves.

---

### Post by oldos2er on 2015-01-16
> **Martin_Gerber said:**
> (Note: I am responsible for ~30 Ubuntu-desktop-PCs and 5 Ubuntu-internet/intranet-webservers, and I am really worrying whether I should stop using Ubuntu)

And use which OS?

---

### Post by Martin_Gerber on 2015-01-17
@mastablasta, @zombifier25
The latest OpenSSL-Heartbleed and the Bash-Bug show that even open source does not protect us from dramatic bugs that stay open for years. New source may also contain subtle "bugs" intentionally. But probably even more important is that the binaries need not to match the source. Almost nobody compiles Ubuntu from scratch, but relies on the provided binaries - which might include some slightly modified "special versions" of typically used software (Firefox, System Services, ...). Technically, adding backdoors to binaries is a simple issue, so it's all about "trusting the distributor". I totally lost my trust in companies from the US, and I am loosing my trust in companies from the UK.

@grahammechanical
I do not see these forums as the lion's den. I am enthusiastically addicted to Ubuntu over many years now. But my enthusiasm is damped because of the reasons explained in my OP. So I am hoping for some new reasons that allow me to be enthusiastic again. For example, probably someone here knows some interview with CEOs from Canonical or with Mark Shuttleworth, where they regard Snowden with favour, or that they support the Wau Holland Foundation, etc., or that they do other proactive things that show that Ubuntu takes a firm stand against total surveillance.

@oldos2er
> And use which OS?
Many Linuxes belong to Red Hat or Novell. So probably the distributed community structure of Debian is much more trustworthy than any Five-Eyes-company. And there are some BSD variants, which might also fit my needs. I don't want to use something like Tails, which automatically routes everything via the Tor network. I just want to use some OS in which I can trust in as much as possible.

Some of you asked why I care about this at all if I am no terrorist? The examples in the OP show that NSA/GCHQ do not only spy out because of terrorism, but also for political and economical reasons (and I do state-of-the-art research on sensitive data). Further, not only terrorists have to fear reprisals, but also other people, like for example Ilija Trojanow, Saad Allami, Evo Morales, Justin Carter, Henry Smith, David Miranda, ... since I travel job-related to US and UK, it might also happen to me. Not because I am a terrorist, but because I publically criticize total surveillance - which is apparently the same according to Bush's logic of "who is not with us is against us", and Cameron's logic of "modern democracy".

---

### Post by ian-weisser on 2015-01-17
> **Martin_Gerber said:**
> But probably even more important is that the binaries need not to match the source. Almost nobody compiles Ubuntu from scratch, but relies on the provided binaries.

The source package input, build systems, and build logs for both Debian and Ubuntu are thoroughly transparent and duplicable, though quite dull and tedious. Setting up your own identical build system is not difficult.

You are welcome to randomly select and build anything you wish, and to look for hash mismaches that would indicate an unexpected difference. I mean it: You are totally welcome to verify any builds you like. 

You probably can't do them all, but you can do a sample. You can do a couple each day. You can work through a lot if you give yourself a little time.

We can't prove a negative, but the tools are already here for you to satisfy your concerns to your own satisfaction.

---

### Post by zombifier25 on 2015-01-17
> **Martin_Gerber said:**
> @mastablasta, @zombifier25
The latest OpenSSL-Heartbleed and the Bash-Bug show that even open source does not protect us from dramatic bugs that stay open for years.

I'm not talking about those types of bug though. Those are honest software bugs that can be overlooked by the developers (Launchpad and Bugzilla exist for a reason)

---

### Post by Martin_Gerber on 2015-01-18
@zombifier25
Yes, but a "bad" guy may add this kind of hard to find bugs *intentionally* as a strategy of adding a "deniable backdoor". Just as a wild hyptothesis: "0.1% of all hard to find bugs in open source are intentionally, 50% of those by script kiddies and 50% by secret services." So it *could* be that these deniable backdoors exist, and that the open source community does not find them for years, because almost nobody really checks the source carefully (in particular if the backdoor/bug does not lead to a malfunction).

@ian-weisser
So you mean that all Ubuntu packages provide deterministic/reproducible builds? I always thought that different builds will almost always give quite different binaries. I will try it out. Can you recommend any tool or further documentation on how to setup an identical build system?

---

### Post by mooreted on 2015-01-18
Being an open system the logistics of hiding such backdoors would be a nightmare. You would have to gag every Debian developer, every independent developer working from his home, every one of us geeks that spends way too much time monitoring our systems and poking around in things. It's not like Microsoft where they can tell all their employees to shut up or be fired and possibly arrested. How do you get millions of people all over the world to keep a secret like that?

---

### Post by leclerc65 on 2015-01-18
Is the Bash bug intentional ?:p

---

### Post by DuckHook on 2015-01-19
From a fellow paranoid (fwiw)...

Life is not an on/off switch. In the context of computer security, it is not a matter of being either totally secure or else totally insecure with nothing in between. In fact, most of life is about finding a bearable compromise in that hazy middle area where things are frustratingly impossible to make definitive. Trying to define the indefinable makes as much sense as pushing on a rope.

In matters of IT security, we take such measures as each of us feel reasonable to achieve a security level that is roughly acceptable in our own eyes. If you work for a company, the judgment as to what is acceptable may be your boss's or her boss's boss, but at some point, it boils down to a decision based on comfort level and someone's informed but ultimately subjective judgment.

So here's the bad news. It is not possible for anyone to reassure you that Ubuntu is absolutely secure. You can compile the entirety of Ubuntu from source, but you would have to use a compiler, and if this is compromised, then the resulting compilation will be tainted. If you first compile the compiler, you've just pushed the same problem one iteration backward. There is no end zone in the pursuit of security. Like life, it's about living with uncertainty. Deal with it.

For years, I told friends and family that we were nowhere nearly as free, or as private or as proof against spying as we had deluded ourselves into believing. I told them that not only our own government, but governments everywhere were actively spying on theirs and others' citizens, and sniffing up our very backsides. I was met with open derision and good natured scoffing. Then came Edward Snowden and the veritable cascade of revelations about how governments indeed capture every single conversation, e-mail, tweet and transaction that we do. No one scoffs these days. But has that turned me into a technological hermit who refuses to use a phone, a computer or a credit card? Who loses if I stop living?

Nothing has changed for me except the confirmation of my previous suspicions. Life goes on. I still take such measures as I deem sufficient to deal with the level of threat that I deem to be realistic. I harden my security to the point where I hope that a bad guy will go after easier pickings, but I'm not foolish enough to think that if the NSA were after me, that I would stand a Hail Mary's chance of hiding from them, backdoor or no backdoor.

This knowledge does not make me happy. I just have to deal with it. So do you.

---

### Post by Martin_Gerber on 2015-01-20
@mooreted
No, it just needs a single person X to hide the secret. Person X contributes some cool new feature to Software Y, including an intentional "bug" that is hard to find, and which could even happen to experienced programmers. Then it is not unlikely that this bug is overlooked by others over years, and that it will make its way to the public, and open a backdoor for person X. And even IF it is detected someday, then person X can still say "sorry, this was my fault, but you must agree that the bug was really tricky. Of course it was not intentionally."

@leclerc65
> Is the Bash bug intentional ?
Well, it *could* be, but I suppose that it's not, since it goes back to 1989. But it is not unlikely that the NSA found this bug several years earlier than 2014, and that they were happy to use it from time to time (in contrast to botnet-programmers, they will use such a wonderful bug carefully, not widely spreaded).

@DuckHook
I see this very similarly. You cannot be absolutely sure. However, I feel that it is important to actively fight things that I dislike, not just to come to terms with them, because things like that do always get worse until they finally reach a barrier of active resistance. Unfortunately, this mechanism holds true for total surveillance as well as for working conditions, the gap between the rich and the poor, environmental pollution, etc... On the "bad" side there are strong egotistic or fanatic forces that make the things worse, so we need strong activities on the "good" side to hold a passable balance somewhere. Here, for example, re-validate Ubuntu's binaries publically, organize code-reviews for critical open source software, raise the peoples' awareness of informational self-determination, make end-to-end-encryption easily available to everyone, badmouth spy-software (like Angry Birds, web-trackers, and hopefully not like Ubuntu), affect politics in order to let them pass a law that explicitly states that encrypted communication as such is *not* illegal, and so on... I don't want to leave my children in George Orwell's 1984.

Btw: I just read today, that Barack Obama sided with Cameron last Friday. Obama also pushes to forbid end-to-end encryption if it cannot be broken by the government. So, it's really time to take a firm stand against this idiocy.

---

### Post by coffeecat on 2015-01-20
Thread closed. 

A reminder of the forum [Code of Conduct](http://ubuntuforums.org/misc.php?do=showrules)...

> **Politics**: This topic has caused serious problems in the past, and as such is subject to tight control. Discussion of the politics of open source is permissible within the Ubuntu/Linux and Other OS forum, no other political posting is permitted in any form in any other area of the forum.

And the forum description for this section...

> Discussion of the politics of open source is permissible, but only the politics of open source. **Wider political discussion is disallowed in all areas of the forum**, as is discussion of religion.

---

