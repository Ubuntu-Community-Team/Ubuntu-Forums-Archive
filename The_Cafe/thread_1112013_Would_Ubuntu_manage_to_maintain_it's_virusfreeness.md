---
title: "Would Ubuntu manage to maintain it's virusfreeness (just made that up) if..."
date: 2009-03-31
forum: The Cafe
---

### Post by Peter_G on 2009-03-31
it got the same market share as Microsoft? Just wondering about peoples opinions on this...

---

### Post by Izek on 2009-03-31
> **Peter_G said:**
> it got the same market share as Microsoft? Just wondering about peoples opinions on this...

Linux won't have the same market share as Microsoft Windows.

And no, it would likely wouldn't if that happened, as people would scramble to make viruses for Linux.

---

### Post by Peter_G on 2009-03-31
Thought as much.

---

### Post by LowSky on 2009-03-31
there would be viruses, but because of linux's file structure, many flavors, and the need for root access, viruses would have a hard time running.

Linux versions like Ubuntu with its Sudo access might be easier to crack as some people might just enter passwords.

---

### Post by albandy on 2009-03-31
only if users install the virus, a virus could not be autoinstalled in linux.
To install a virus you need to be super user and execute it. 

Of course, if you only use the ubuntu repositories to install software it could be very very very very difficult to install a virus.

---

### Post by forrestcupp on 2009-03-31
Linux is way more secure than Windows.  But if it got to the point where people actually cared about it, I'm sure plenty of exploits would be found quickly.

Anyway, all you have to do is play on people's ignorance and offer a "beneficial" script that everyone will love but most people won't check into.  How many people actually sift through all the code of everything they install?  Even expert developers can't possibly do that.  You can cause a lot of damage without trashing the whole system.  If you've spent a lot of high priced, valuable hours working on an important project that is saved to your /home folder, you don't even need super user privileges to cause *a lot* of trouble.

Virus creators know that their viruses won't last forever before being stopped.  Their goal is just to exploit as many computers as possible before that happens.

---

### Post by Simian Man on 2009-03-31
Keep in mind that most of the worlds web servers are running Linux, so there is *certainly* a market for Linux viruses.  The reasons there are few to none are more about the fact that most Linux users (especially for servers) know what the hell they're doing while Windows users don't.

If Linux was more popular on the desktop, there would be more cluless people using it and hence be easier to distribute viruses for.  The biggest security flaw is always the user.

---

### Post by lykwydchykyn on 2009-03-31
This question is asked a lot, and almost universally I think it's asked in the wrong frame of mind.  A "virus" is one type of security exploit, one type out of many.  Whether or not Linux would be (or is) immune to "viruses" is not the issue; it's immunity to exploits in general that matters.  Do you really care whether your computer got hacked with a virus, malware, trojan, or rootkit?  These are just tools, the bottom line is you got hacked.

With that in mind, consider this from an economic standpoint:  within the criminal world, there is a DEMAND for compromised computers -- botnets for DDOS attacks, entry points into secure networks, sources of identity theft data, etc.  As long as there is a demand, there will be people working to create a SUPPLY.  The people doing this are not going to suddenly say "Oh, everyone switched to Linux, I guess we'll stop cracking computers".  They will just formulate new vectors of attack and new ways to provide a SUPPLY for the DEMAND.  

On the flipside, there are several nice things about Linux that will make this a bit harder for them to accomplish this.  One of the biggest assets in my opinion is the inbuilt diversity.  You and I may both be running "Linux" on our machines, but we may have very different selections of libraries, installed programs, kernel versions, etc.  This makes it harder to have epidemic exploits.  Consider: the biggest security blunder in Debian history happened last year.  SSH/SSL keys were screwed up, and created a huge flaw not only in Debian but in all distros derived from Debian (including Ubuntu).  But even with that huge deal, a big chunk of the Linux world was unaffected: RedHat, Suse, Mandriva, Slackware, etc.  If such a flaw had happened in the Windows world, every single Windows machine would have been affected.  

Now, if Ubuntu (or any other single distro) becomes 90% of the world's desktops, then we potentially have a problem.  But as long as we avoid a monoculture and keep a diversity, I think the days of epidemic computer exploits would dwindle.

---

### Post by sydbat on 2009-03-31
The user is always the weakest link. 

However, the recent 'conficker' worm attacking Windows boxes supposedly can exploit "*a **previously patched** vulnerability in the Windows Server service used by Windows 2000, Windows XP, Windows Vista, Windows Server 2003, Windows Server 2008, Windows 7 Beta, and Windows Server 2008 R2 Beta*"...at least according to [Wikipedia]("http://en.wikipedia.org/wiki/Conficker").

So the question now becomes, can malware written for GNU/Linux take a similar path. (of course, this would be outside of safe Internet practises and only using reliable repositories to install applications)

---

### Post by Kareeser on 2009-03-31
> **forrestcupp said:**
> If you've spent a lot of high priced, valuable hours working on an important project that is saved to your /home folder, you don't even need super user privileges to cause *a lot* of trouble

Viruses don't have proper ownership of the home folder in question, unless chown is run. In that case, you'd need sudo.

Therefore, the virus still won't be able to do any damage UNLESS the user inputs the password during a gksudo prompt.

Caveat: Unless, of course, you have o+wx permissions on the critical files. But by default, that isn't set...

---

### Post by MaxIBoy on 2009-03-31
Linux is inherently more secure, due to its Unix-inspired design and its development model. 

Remember that, early in its development, Unix was used on timesharing computers, where many different users had to log in remotely, and any one of those users was a potential security threat (jokester genius university student with too much time.) It *had* to be secure. It's got an excellent system of users, groups, and fine-grained segmented permissions; no user has any more permissions than it absolutely needs. An executable program doesn't even have permission to run at *any* privelege level unless you chmod +x it. 

If you want an example of why Linux's development model makes it secure, take a look at this page here:
[http://insecure.org/sploits/ping-o-death.html](http://insecure.org/sploits/ping-o-death.html)
Linux had this fixed in just over two hours and a half. Because the source is open, someone was working on the problem probably befor Linus Torvalds had even heard of it. This is why, while there have been Linux viruses before, most of them take advantage of exploits that have since been fixed. In fact, most of them were created specifically to demonstrate where the exploit is, and were never released into the wild.


Remember though, no OS will protect you from your own stupidity. Don't install stuff you don't trust!

---

### Post by insane_alien on 2009-03-31
seeing as linux already has a higher market share than windows in high-value targets i think we can safely say that:

yes linux would remain virus-free even if its desktop adoption was near monopoly.

however, viruses would be able to appear now and then but would be fixed by a patch within days, only certain distributions would be vulnerable and infection would be stopped before becoming widespread. 

Due to the variation in linux, it has herd immunity. This is where a population(of computers in this case) are diverse enough so that most individuals will be immune to a particular virus which makes transmition of the virus so unlikely that even those without the immunity are unlikely to contract the virus.

also, once the virus is found, patches will cut off the exploit the virus was using. it won't cure existing infections but will prevent ANY virus that uses that exploit from being viable.

linux tends to treat the cause rather than the symptoms. on windows the symptoms are treated but the underlying cause may be around for years(i'm unfortunately serious here)) even if the cause is known.

---

### Post by lykwydchykyn on 2009-03-31
Something else people never really consider in these discussions is what a singularity it would be for a free, open-source operating system to take over as the dominant OS.  Nobody can really predict what would happen beyond that point, or what Linux would look like at that point.

I mean, so much of the argument revolves around what Linux *is*.  But can you really believe that -- given its open development model, its modularity, its open source code -- Linux would be the same with *the full force* of the entire technology industry behind it?  Every hardware maker, every software vendor, every user community, the IT departments of every fortune 500 company, all of academia, governments, etc. etc. -- all contributing to make Linux more secure and more user-friendly.  Today's distros would hardly compare to what we'd have on our hands at that point.

---

### Post by FraggedLocust on 2009-03-31
> **lykwydchykyn said:**
> Today's distros would hardly compare to what we'd have on our hands at that point.

That seems like a utopia that can't be realized. People will always pay for stuff they want because they think their money is going somewhere and paying for superior software. 

Of course, if the open source community can show people that you can donate a small percentage of your $40 or $100 to have equal or superior value to commercial products, then Linux might be able to get the general public interested.

---

### Post by insane_alien on 2009-03-31
true, there is insufficient data for an accurate prediction but we do what we can with simple extrapolation. it's very likely to be wrong but is a whole lot closer than 'dunno'.

---

### Post by lykwydchykyn on 2009-03-31
> **insane_alien said:**
> true, there is insufficient data for an accurate prediction but we do what we can with simple extrapolation. it's very likely to be wrong but is a whole lot closer than 'dunno'.

I'm not saying people shouldn't talk or think about it, I'm just trying to get people to think about how there'll be a lot more to the story than just Ubuntu in its current state suddenly on billions of computers.  People (particularly the "Linux will be just as insecure as Windows" crowd) tend to argue from that point of view without giving credit to the fact that we'd have a lot more well-equipped organizations contributing to FOSS/Linux development.

Maybe it's not quite a singularity, but clearly the system itself would change significantly if it had that kind of market share.  Arguing over the minutiae of its current security model seems a little pointless in that respect.

---

### Post by albandy on 2009-03-31
As you should now, 90% of adsl home routers works under Linux, and are exposed directly to internet.

Except for a bad login/password configuration (short and easy passwords) these systems are very secure.

---

### Post by aysiu on 2009-03-31
I may be repeating a few points already mentioned, but this is my take on things: [list][*]There will certainly be a huge malware problem, but most of the malware will rely on social engineering (tricking the user) instead of the exploitation of software flaws.[*]On a similar note, even if software flaws are quickly patched, it's still up to the user to patch them. The Conficker worm has managed to infect 10 million Windows computers since November despite Microsoft having released a patch for it back in October.[*]Linux is not inherently more secure by design, but it is easy to secure by design and it is often secure by design. As Linspire and the Eee Xandros have shown, you can just as easily distribute a version of Linux that is completely insecure (essentially run as root). Even if Ubuntu were to become as popular as Windows, due to Ubuntu's open source nature, it may not be Ubuntu itself but a less secure variant of Ubuntu that becomes popular and so might be just as insecure as Windows.[*]I don't believe Windows will *always* be the dominant consumer OS, but I also don't think a change will happen overnight. Windows is deeply entrenched in people's psyches right now. So by the time Ubuntu became as popular as Windows (if that ever happens), the very nature of the internet and security may have changed significantly so all this talk about "viruses" might seem old-fashioned by that point.[/list]

---

### Post by forrestcupp on 2009-03-31
> **Kareeser said:**
> Viruses don't have proper ownership of the home folder in question, unless chown is run. In that case, you'd need sudo.

Therefore, the virus still won't be able to do any damage UNLESS the user inputs the password during a gksudo prompt.

Caveat: Unless, of course, you have o+wx permissions on the critical files. But by default, that isn't set...

That's true, but I was talking about user-run scripts.  A user can run a seemingly beneficial but actually malicious script from the home folder, and it could trash your home folder without the user ever entering a sudo password.

---

