---
title: "Russian Government Computers to Get Linux-Based Operating System"
date: 2010-07-23
forum: The Cafe
---

### Post by BigCityCat on 2010-07-23
> The operating system, for use on the computer systems of government agencies and state-run companies, will be 90 percent based on the open-source Linux operating system, Deputy Communications and Press Minister Ilya Massukh said.


[http://www.themoscowtimes.com/business/article/government-computers-to-get-linux-based-operating-system/410915.html](http://www.themoscowtimes.com/business/article/government-computers-to-get-linux-based-operating-system/410915.html)

---

### Post by kellemes on 2010-07-23
I wonder what os the remaining 10 percent will be based on.

---

### Post by Keith_K on 2010-07-23
Didn't Microsoft just share their source code with the Russians?
I guess they didn't like what they saw ;)

---

### Post by chiliman on 2010-07-23
> **Keith_K said:**
> Didn't Microsoft just share their source code with the Russians?
I guess they didn't like what they saw ;)
 lol i was going to mention something along those lines.

---

### Post by prodigy_ on 2010-07-23
Oh, trust me, it's not good news for the community. I'm from Russia myself and I know how things are done in this country. For example, there's already a proprietary and closed source (I'm not joking!) distro of Linux used by Russian army - so called Mobile System of Armed Forces.

The maintainers of this abomination broken all rules possible. Suffice it to say that the default user is root. They also removed all traces of GPL and were impudent enough to actually call themselves the authors (again, I'm joking!) of everything, including the kernel.

And that's typical Russia for you.

---

### Post by Trinexx on 2010-07-23
The article states that use of the distro will be optional by the various agencies.

In other words, nobody will use it.

---

### Post by Dr Belka on 2010-07-23
> **prodigy_ said:**
> Oh, trust me, it's not good news for the community. I'm from Russia myself and I know how things are done in this country. For example, there's already a proprietary (I'm not joking!) disto of Linux used by Russian army - so called Mobile System of Armed Forces.

The maintainers of this distro broken all rules possible. Suffice it to say that the default user is root. They also removed all traces of GPL and were impudent enough to actually call themselves the authors (again, I'm joking!) of everything, including the kernel.

And that's typical Russia for you.

Do you mean that you aren't joking?

---

### Post by prodigy_ on 2010-07-23
> **Dr Belka said:**
> Do you mean that you aren't joking?
I mean that if somebody expects upstream contributions or at least a "thank you" from those guys, he doesn't have a clue. :-)

---

### Post by BigCityCat on 2010-07-23
Interesting comments from our Russian friend.

---

### Post by earthpigg on 2010-07-23
> Oh, trust me, it's not good news for the community. I'm from Russia myself and I know how things are done in this country. For example, there's already a proprietary and closed source (I'm not joking!) distro of Linux used by Russian army - so called Mobile System of Armed Forces.

if you do not distribute it outside of your own organization, you are not obliged by the GPL to open up the source code. 

> Suffice it to say that the default user is root. 

That makes sense, if the computer is to be regarded as a weapon and *not internet-facing*. 

Who has 'root' access to a rifle? The person holding the rifle.

Who has 'root' access to a military truck? The person sitting in the driver's seat. I don't know if Russia's Army is like this, but American military [hmmwv]("http://en.wikipedia.org/wiki/HMMWV")'s don't even have ignition keys. Literally *anyone* that walks up to an American hmmwv and sits in the driver's seat can immediately drive it off. The doors don't have locks, and no key is required to start it, pop the hood, or open the gas tank.

Who has 'root' access to a ship at sea? The crew, and the Captain who commands her.

Who can arm, disarm, or explode a hand grenade? Whoever picks it up.

Set 'root' to autologin without a password, remove *all* networking hardware & software, and suddenly you have a computer that adheres to standard weapons conventions. You can't SSH into a Warship at Sea and take control of it (what Captain would allow that?), so why should any other weapons system be different?

Let's say we have a truck-sized **_S_**urface to **_A_**ir **_m_**issile system running a Linux distribution that is completely secure by standard Linux conventions. Call it ***SAMLinux***. All of the "best practices" for computer security are being adhered to. No passwords written down, only one person knows the root password, and one additional person is on the sudoers list.

Now let's say that both password holders get killed while away from their machine (these are weapons of war we are talking about, after all), and we need to get that missile system up and running ASAP.... 

"uuuh, anyone have a *SAMLinux* LiveCD sitting around? ***Quick, fire up the CD burner***!"

You either ***do*** or ***do not*** trust that Russian Soldier with that non-nuclear weapon system. If you do not trust him, then you shouldn't be giving him physical access to the weapon. If you do trust him, and place him on the sudoers list... then he is just going to 'sudo su' as soon as he sits down anyways, so let's just skip that step. (i'm assuming these soldiers are actually trained to use their weapons prior to being left alone with them.)

I was in the Marines when I first discovered Ubuntu. As soon as I started messing around with the command line, one of the first things I learned was how to 'sudo su' so i could type subsequent commands more efficiently.

I'd be pretty pissed I where issued a rifle that was locked shut so I couldn't take it apart, and I'd also be pissed if it had complex safety mechanisms on it (like sudo) that I couldn't simply leave disabled 24/7.

One safety is all any troop needs or wants.

A Linux computer's safety is that the troop can read what he is typing or clicking on before he clicks on it or presses enter. Turning the weapon/computer on (inserting a magazine into the rifle) would be another safety.

trimming 5 seconds from the poweron-to-firing timeline could be lifesaving.


> They also removed all traces of GPL and were impudent enough to actually call themselves the authors (again, I'm joking!) of everything, including the kernel.

You are surprised that "Made in the USA" was removed from an imported weapon used by the Russian Armed Forces? 

(It isn't EU Law or Russian Law that the GPL was designed to function within... It's an American legal document, written in American English by an American, vetted by American lawyers, designed to function within the framework of American Copyright Law... So, Yeah. "Made in the USA." )

And the word "Linux"? Named after a Finn? One of [these]("http://en.wikipedia.org/wiki/Siege_of_leningrad") guys? It would have been nice to be a fly on the wall when some young & very smart Russian engineer tried telling a Russian General that the new weapons system ought to be named after a Finnish man. Leninux would be more likely :P

---

### Post by Dr. C on 2010-07-23
> **earthpigg said:**
> if you do not distribute it outside of your own organization, you are not obliged by the GPL to open up the source code. 



That makes sense, if the computer is to be regarded as a weapon and *not internet-facing*. 

Who has 'root' access to a rifle? The person holding the rifle.

Who has 'root' access to a military truck? The person sitting in the driver's seat. I don't know if Russia's Army is like this, but American military [hmmwv]("http://en.wikipedia.org/wiki/HMMWV")'s don't even have ignition keys. Literally *anyone* that walks up to an American hmmwv and sits in the driver's seat can immediately drive it off. The doors don't have locks, and no key is required to start it, pop the hood, or open the gas tank.

Who has 'root' access to a ship at sea? The crew, and the Captain who commands her.

Who can arm, disarm, or explode a hand grenade? Whoever picks it up.

Set 'root' to autologin without a password, remove *all* networking hardware & software, and suddenly you have a computer that adheres to standard weapons conventions. You can't SSH into a Warship at Sea and take control of it (what Captain would allow that?), so why should any other weapons system be different?

Let's say we have a truck-sized **_S_**urface to **_A_**ir **_m_**issile system running a Linux distribution that is completely secure by standard Linux conventions. Call it ***SAMLinux***. All of the "best practices" for computer security are being adhered to. No passwords written down, only one person knows the root password, and one additional person is on the sudoers list.

Now let's say that both password holders get killed while away from their machine (these are weapons of war we are talking about, after all), and we need to get that missile system up and running ASAP.... 

"uuuh, anyone have a *SAMLinux* LiveCD sitting around? ***Quick, fire up the CD burner***!"

You either ***do*** or ***do not*** trust that Russian Soldier with that non-nuclear weapon system. If you do not trust him, then you shouldn't be giving him physical access to the weapon. If you do trust him, and place him on the sudoers list... then he is just going to 'sudo su' as soon as he sits down anyways, so let's just skip that step. (i'm assuming these soldiers are actually trained to use their weapons prior to being left alone with them.)

I was in the Marines when I first discovered Ubuntu. As soon as I started messing around with the command line, one of the first things I learned was how to 'sudo su' so i could type subsequent commands more efficiently.

I'd be pretty pissed I where issued a rifle that was locked shut so I couldn't take it apart, and I'd also be pissed if it had complex safety mechanisms on it (like sudo) that I couldn't simply leave disabled 24/7.

One safety is all any troop needs or wants.

A Linux computer's safety is that the troop can read what he is typing or clicking on before he clicks on it or presses enter. Turning the weapon/computer on (inserting a magazine into the rifle) would be another safety.

trimming 5 seconds from the poweron-to-firing timeline could be lifesaving.




You are surprised that "Made in the USA" was removed from an imported weapon used by the Russian Armed Forces? 

(It isn't EU Law or Russian Law that the GPL was designed to function within... It's an American legal document, written in American English by an American, vetted by American lawyers, designed to function within the framework of American Copyright Law... So, Yeah. "Made in the USA." )

And the word "Linux"? Named after a Finn? One of [these]("http://en.wikipedia.org/wiki/Siege_of_leningrad") guys? It would have been nice to be a fly on the wall when some young & very smart Russian engineer tried telling a Russian General that the new weapons system ought to be named after a Finnish man. Leninux would be more likely :P

Actually the GPL is enforceable in Russia, but that is not the point. If the Russian Armed forces do not distribute or convey (depending of the version of the GPL) their modified software they have no obligation to provide anyone with the source code under the GPL, as was quite correctly pointed out. In fact they are not even bound by the GPL and can use the software internally with any modifications they wish. It is right in the GPL > 2. Basic Permissions.

All rights granted under this License are granted for the term of copyright on the Program, and are irrevocable provided the stated conditions are met. This License explicitly affirms your unlimited permission to run the unmodified Program. The output from running a covered work is covered by this License only if the output, given its content, constitutes a covered work. This License acknowledges your rights of fair use or other equivalent, as provided by copyright law.

You may make, run and propagate covered works that you do not convey, without conditions so long as your license otherwise remains in force. You may convey covered works to others for the sole purpose of having them make modifications exclusively for you, or provide you with facilities for running those works, provided that you comply with the terms of this License in conveying all material for which you do not control copyright. Those thus making or running the covered works for you must do so exclusively on your behalf, under your direction and control, on terms that prohibit them from making any copies of your copyrighted material outside their relationship with you.

Conveying under any other circumstances is permitted solely under the conditions stated below. Sublicensing is not allowed; section 10 makes it unnecessary. from: [http://www.gnu.org/licenses/gpl.html]("http://www.gnu.org/licenses/gpl.html")

---

### Post by earthpigg on 2010-07-23
> **FineE said:**
> Actually the GPL is enforceable in Russia, but that is not the point.

I never said it wasn't enforceable, I only inferred that things going on in Russia in 1989 weren't RMS's concern when he was working on the GPLv1.


"Well, General, we don't legally ***have*** to keep the American copyright notice or the Finnish name, but it would be kinda cool if we did..."

What sort of response to that do you picture, from a General that probably spent the first 10 years of his career as a loyal officer of the Red Army?

We should try to avoid making this to political, my only point was that when the guy above said that Linux, when implemented by the Russian Army, does not carry the name "Linux" or the American English text of the GPL... I saw no reason at all to be surprised.

Are there any AK-47 or M-16 rifles with "[Designed in Nazi Germany]("http://en.wikipedia.org/wiki/Sturmgewehr_44")" stamped on the side?

***Of course*** the GPL and name Linux will be removed from any Linux distribution used internally by the Russian Armed Forces.

---

### Post by MisterIcky on 2010-07-23
Ultimate irony would require that they run a Microsoft OS.... 

Alex ... very Russian name

Alexander Graham Bell -> Bell Telephone -> Bell Labs -> Unix -> Linux.

Sentimental issues aside, they should choose whatever OS works best for them. 'course if did their own homebrew OS our Military hackers would have a lot harder time getting inside!

---

### Post by prodigy_ on 2010-07-23
> **earthpigg said:**
> if you do not distribute it outside of your own organization, you are not obliged by the GPL to open up the source code. 
Yes, I know. I never wrote they were obliged to do anything. I only told you what they chose to do. 

> **earthpigg said:**
> That makes sense, if the computer is to be regarded as a weapon and *not internet-facing*. 

Root access by default never makes sense from security point of view and security was the main goal. By the way, the distro I'm talking about is based on RHEL. RHEL itself does things quite right. But our local "developers" managed to break it.

---

### Post by witeshark17 on 2010-07-24
Well it's not a surprising choice, is it then! :popcorn: :KS

---

### Post by earthpigg on 2010-07-24
> **prodigy_ said:**
> > That makes sense, if the computer is to be regarded as a weapon and not internet-facing.
 
Root access by default never makes sense from security point of view and security was the main goal. By the way, the distro I'm talking about is based on RHEL. RHEL itself does things quite right. But our local "developers" managed to break it.

Security is secondary to lethality, when it comes to non-nuclear weapons.

The vast majority of the Ubuntu community will disagree with me on that.

The vast majority of the Ubuntu community has also never received military training.

@passwords-on-weapons-of-warfare lovers:

Have fun with your password-protected spear if you want. The warriors will be stomping guts, shooting down aircraft, and generally causing chaos & mayhem while you are still checking to see if caps lock is turned on before entering your password for a third time. :P

And yes, it is possible that a mistake caused by always running as root could cause the 'spear' to fail. Fortunately, redundancy is always a priority. The "ah crap i broke my weapon" shell script will be present to restore things to the way they where a week ago.



I mean this all in good fun, by the way. I hope no one is offended or surprised at the notion that various armed forces of the world exist to eradicate human life with efficiency.

---

### Post by McRat on 2010-07-24
> **earthpigg said:**
> ...
Are there any AK-47 or **M-16** rifles with "[Designed in Nazi Germany]("http://en.wikipedia.org/wiki/Sturmgewehr_44")" stamped on the side?

...

I think you're thinking of the **M-60**(a MG-42 clone), not the M-16 (Designed by Eugene Stoner, was a truly unique rifle design).

---

### Post by earthpigg on 2010-07-24
> **McRat said:**
> I think you're thinking of the **M-60**(a MG-42 clone), not the M-16 (Designed by Eugene Stoner, was a truly unique rifle design).

if you say so. i haven't verified [wikipedia's]("http://en.wikipedia.org/wiki/Sturmgewehr_44#Post-war") sources for myself.

---

### Post by McRat on 2010-07-24
> **earthpigg said:**
> if you say so. i haven't verified [wikipedia's]("http://en.wikipedia.org/wiki/Sturmgewehr_44#Post-war") sources for myself.

Eh, don't believe everything in Wiki.  The M-16 uses a high velocity rifle (.223 Remington Varmint) cartridge, and had a 20" bbl, made of composites, with a machined receiver and a combo of aluminum and steel parts.  It's accurate out to about 300 yard (man sized target) through iron sights while standing.

The Sturmgewehr uses stamped steel parts and wood, fired an "intermediate" cartridge designed for just for the rifle.  Half way between a pistol and a rifle cartridge, with a 16" bbl.  It is heavy, shorter, and lower powered, with a shorter range than the M-16, about 150 yards, due to the low velocity, big bullet design.   It weighed more than a M1 Garand and almost twice as much as an M16.

What the US used tactically in place of the Sturmgewehr was the Thompson submachine gun. 

I'll agree that the AK-47 was inspired by the SG44, but the AK-74 is inspired by the M-16.  The M-16 was a new way of looking at combat rifles.

To be honest, the SG 44 was a POS made out of desperation.  It was no wonder weapon as is hyped today.

---

### Post by earthpigg on 2010-07-24
OK, you caught me. The claim was a stretch. Was trying to throw something American in there so it didn't look like I was picking on the Russian Armed Forces when it comes to certain traits that are nearly universal.

Would have been better to do my homework first, but the claim served it's purpose of demonstrating that I wasn't trying to pick on Russia.

> It's accurate out to about 300 yard (man sized target) through iron sights.

300?

The rifle itself is capable of grouping reliably within the chest of a man-sized target at 500 using iron sights, though it is true that most people cannot accomplish this. 

I'd have to dig up my boot camp range book from 9 years ago to be certain, but I'm pretty sure I scored 8 or 9 hits out of 10 from the 500 yard line prone slow fire. Plain-Jane M-16A2, Iron Sights. I never matched that accomplishment again, but I was never as focused again either. I've seen many Marines get 10/10 from the 500 - and we're not talking about snipers here, either.

And these weren't match grade rifles with special ammunition or anything, either. Beat up, had been issued back-to-back to recruits for a decade or more in 3 month cycles, bluing worn off many of the components due to excessive cleaning. Ball ammo, made by lowest bidder.

It certainly isn't practical to expect 500 yard shots with the m-16 to happen on a regular basis in combat, but it is essential to know what the *rifle itself* is capable of. It is unfortunate that the US Army has elected to completely abandon teaching the *art* of marksmanship, but that whack-a-mole video-game-inspired range qualification thing they have going on may have something to do with the 300 claim that I've seen tossed around before.

300 yards is indeed the maximum range an American *soldier* is typically aware that the rifle can hit targets at, yes. That's a frequent human limitation, not a limitation of the rifle.

---

### Post by neu5eeCh on 2010-07-24
I confess, I've always been perplexed that the purported "enemies" and "rivals" of the US would all be writing their diatribes on Windows. As far as  I know, even the Iranians and AQ are spewing their rubbish on Windows. You would think, as paranoid as these regimes can be, that they would all suspect Windows and Mac software. They would worry about Trojan Horses - (collusion between the US, Microsoft and Apple. In fact, I would be supremely disappointed if the United States government  **didn't** try something like that.

---

### Post by McRat on 2010-07-24
> **earthpigg said:**
> OK, you caught me. The claim was a stretch. Was trying to throw something American in there so it didn't look like I was picking on the Russian Armed Forces when it comes to certain traits that are nearly universal.

Would have been better to do my homework first, but the claim served it's purpose of demonstrating that I wasn't trying to pick on Russia.



300?

The rifle itself is capable of grouping reliably within the chest of a man-sized target at 500 using iron sights, though it is true that most people cannot accomplish this. 

I'd have to dig up my boot camp range book from 9 years ago to be certain, but I'm pretty sure I scored 8 or 9 hits out of 10 from the 500 yard line prone slow fire. Plain-Jane M-16A2, Iron Sights. I never matched that accomplishment again, but I was never as focused again either. I've seen many Marines get 10/10 from the 500 - and we're not talking about snipers here, either.

And these weren't match grade rifles with special ammunition or anything, either. Beat up, had been issued back-to-back to recruits for a decade or more in 3 month cycles, bluing worn off many of the components due to excessive cleaning. Ball ammo, made by lowest bidder.

It certainly isn't practical to expect 500 yard shots with the m-16 to happen on a regular basis in combat, but it is essential to know what the *rifle itself* is capable of. It is unfortunate that the US Army has elected to completely abandon teaching the *art* of marksmanship, but that whack-a-mole video-game-inspired range qualification thing they have going on may have something to do with the 300 claim that I've seen tossed around before.

300 yards is indeed the maximum range an American *soldier* is typically aware that the rifle can hit targets at, yes. That's a frequent human limitation, not a limitation of the rifle.

You put a scope on it, get prone or support, and it certainly can hit things past 500 reliably no doubt.  It just wouldn't be the best choice out of the NATO calibers.  Not much punch left.

I heard they are breaking out the old M-14's again for this reason.

---

### Post by chriswyatt on 2010-07-24
In Soviet Russia, Linux-based operating systems get you!

---

### Post by earthpigg on 2010-07-24
> **McRat said:**
> I heard they are breaking out the old M-14's again for this reason.

As 'designated marksman' rifles, one per Army rifle squad in certain units. My understanding is that more-or-less whoever the best shot is that isn't in a leadership position... gets a scoped M-14.

---

### Post by McRat on 2010-07-24
> **earthpigg said:**
> As 'designated marksman' rifles, one per Army rifle squad in certain units. My understanding is that more-or-less whoever the best shot is that isn't in a leadership position... gets a scoped M-14.

The .308 is still really good rifle cartridge, and the M-14 is one of the best rifle designs of all time, IMO.

PS - Thank you for your service.  :KS  I enlisted back in 79, but something went wrong, so I never served a day.

---

