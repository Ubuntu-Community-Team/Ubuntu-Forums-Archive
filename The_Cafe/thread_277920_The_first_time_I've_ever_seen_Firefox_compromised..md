---
title: "The first time I've ever seen Firefox compromised... probably won't be the last"
date: 2006-10-15
forum: The Cafe
---

### Post by aysiu on 2006-10-15
**Some backstory** 
People in my office have been told repeatedly by IT that they're using Thunderbird instead of Outlook and Firefox instead of Internet Explorer because "it's more secure."

**The actual story**
Well, I happened to see Firefox get compromised on a co-worker's computer and sent this email to the IT department: > The other day, I helped (by editing about:config) [name of co-worker] get her homepage back from being hijacked after visiting a site. She's using an old version of Firefox.

In fact, most people's computers I've seen seem to have old versions of both Firefox and Thunderbird. For security reasons, wouldn't it make sense to give them at least version 1.5, which is self-updating?

Most of the new Firefox and Thunderbird version numbers (1.5.0.7, 1.5.0.6, etc.) have been security updates, not feature updates.

There's really no value in switching people off IE and Outlook to Mozilla products if the versions we use are still subject to old Javascript (and other) exploits.

Just an idea.  I got a rather enthusiastic response back from one person in IT who assured me that they were understaffed at the moment (which they are) but that he would help people upgrade their Mozilla applications if they were interested and either did or didn't have administrative access on their computers.

I then sent an email to my whole department letting them know about my email and the response I got. One person (out of about 16) responded back that he was interested in getting the latest versions of Firefox and Thunderbird. Since he had administrative access on his computer, I walked him through the launching the setup.exe files (and, to all those Windows power users who think "any moron" can do a setup.exe, that hasn't been my experience--people actually need you to say, "Then click *next*. Then click *next* again.").

One person, and he needed my help.

**My conclusion**
Further evidence that making an application secure is less than half the story. It should be done, but security ultimately lies with the user--updating applications, not visiting fishy (or phishy) websites, creating strong passwords (some of my co-workers use four numbers).

**Rant**
This is why I think Ubuntu won't be necessarily secure if we have a mass migration of ex-Windows users. Password stored as plain text? Oh, not a big deal, the next update fixes that.

Well, what if people don't install the next update?

Even my co-workers who have administrative privileges on their Windows PCs regularly view as an annoyance the balloon asking them for Windows updates... and they *don't* install them! They just ignore the balloon.

Convenience or apathy seems to be a much bigger draw than security.

---

### Post by Albi on 2006-10-15
What if we make major security updates do it in the background automatically?  They do this in Windows, but Ubuntu won't need to reboot after (unless it's a kernel upgrade).

---

### Post by Naralas on 2006-10-15
i ignore windows updates mostly because my windows machines are just there for compatibility and hold nothing of real value. Battlefield 1942 will still be on my CD's after a crash. Windows updates are famous for increasing system requirements.

I view them as annoyances because I know that even IF microsoft managed to patch even 40% of its weaknesses then it would probably do so by adding 100 megs of ram to the required amount just to boot.

Maybe e-mail that IT nut and advise him to move the office to ubuntu and just wine all your important applications.

Oh and Ubuntu upgrades usually are just bugfixes not really security holes arent they? Accept ofcourse browser patches which, like you said, happen automatically.

---

### Post by Lord Illidan on 2006-10-15
> **aysiu said:**
> Convenience or apathy seems to be a much bigger draw than security.

Whatever OS you use, the above will always apply.

---

### Post by aysiu on 2006-10-15
[quote=Naralas]Maybe e-mail that IT nut and advise him to move the office to ubuntu and just wine all your important applications.[/quote]Moving the office to Ubuntu? no way. There are only a couple of IT folk who like open source software, and the database program we use doesn't work in Wine, and there's a lot of stuff we do that requires MS Office (yes, MS Office, not OpenOffice).

There are many organizations that could switch to Ubuntu and be fine--mine is not one of them, unfortunately. Even it were, it would be hard to sell another migration after the nightmare that's been our database conversion the past two years.

By the way, the guy who responded wasn't a nut. I was impressed he was for the idea... at least in theory. Staffing--that's another issue.

[quote=Lord Illidan]Whatever OS you use, the above will always apply.[/quote] Yes, that's what I firmly believe. I believe Ubuntu is secure by design, but I also believe that design isn't worth a damn if you have users who don't care about security.

---

### Post by DoctorMO on 2006-10-15
You have to be able to have the resources to manage your computer. targeting those responsible for the computer maintenance will be the first step as there is just no way to educate basic users. the number of times I go to my mums machine (via ssh) and install the updates remotely or install the updates for my landladies machine. they just don't see maintenance as their job.

So all those IT Administration people for offices, all those computer shops and technical folk need to understand the importance of helping users keep on top of their charges security (for a fee or without *shrug*)

---

### Post by aysiu on 2006-10-15
I agree 100% DoctorMO. I don't work in IT officially, but I do try   as much as possible to educate my co-workers and support them.

Getting them to appreciate the education... that's another story.

---

### Post by skymt on 2006-10-15
> **Albi said:**
> What if we make major security updates do it in the background automatically?  They do this in Windows, but Ubuntu won't need to reboot after (unless it's a kernel upgrade).

There's a package called unattended-upgrades that should do this. It's installed by default. However, I haven't seen it work (I get security updates in my regular update sessions), and there doesn't seem to be any documentation for how to turn it on.

---

### Post by Polygon on 2006-10-15
when i use windows xp, sometimes after coming back to my computer i see an icon that says updates have been installed, please restart your computer. And i didnt click anything, so i know that windows updates download/install themselfs automatically in xp

and i think the same is for firefox as well, it checks daily/weekly for new updates and then if there is any it automatically downloads and installs it the next time you close/run the program. But this would most likely need administrative access to do though...

---

### Post by aysiu on 2006-10-15
> **Polygon said:**
> when i use windows xp, sometimes after coming back to my computer i see an icon that says updates have been installed, please restart your computer. And i didnt click anything, so i know that windows updates download/install themselfs automatically in xp That's a setting, actually, and Ubuntu has it as well and Firefox has it as well. I guess some people don't have that set, so they actually have to OK updates.

> 
and i think the same is for firefox as well, it checks daily/weekly for new updates and then if there is any it automatically downloads and installs it the next time you close/run the program. But this would most likely need administrative access to do though... It also needs at least Firefox 1.5 or above, and a lot of people in my office have 1.0 or 0.9.

---

### Post by RAV TUX on 2007-08-30
> **aysiu said:**
> **Some backstory** 
People in my office have been told repeatedly by IT that they're using Thunderbird instead of Outlook and Firefox instead of Internet Explorer because "it's more secure."

**The actual story**
Well, I happened to see Firefox get compromised on a co-worker's computer and sent this email to the IT department:  I got a rather enthusiastic response back from one person in IT who assured me that they were understaffed at the moment (which they are) but that he would help people upgrade their Mozilla applications if they were interested and either did or didn't have administrative access on their computers.

I then sent an email to my whole department letting them know about my email and the response I got. One person (out of about 16) responded back that he was interested in getting the latest versions of Firefox and Thunderbird. Since he had administrative access on his computer, I walked him through the launching the setup.exe files (and, to all those Windows power users who think "any moron" can do a setup.exe, that hasn't been my experience--people actually need you to say, "Then click *next*. Then click *next* again.").

One person, and he needed my help.

**My conclusion**
Further evidence that making an application secure is less than half the story. It should be done, but security ultimately lies with the user--updating applications, not visiting fishy (or phishy) websites, creating strong passwords (some of my co-workers use four numbers).

**Rant**
This is why I think Ubuntu won't be necessarily secure if we have a mass migration of ex-Windows users. Password stored as plain text? Oh, not a big deal, the next update fixes that.

Well, what if people don't install the next update?

Even my co-workers who have administrative privileges on their Windows PCs regularly view as an annoyance the balloon asking them for Windows updates... and they *don't* install them! They just ignore the balloon.

Convenience or apathy seems to be a much bigger draw than security.good points overall aysiu, this is why I like the rPath System manager, I can schedule updates to happen the same time each night and if need be roll back to a previous build.

---

### Post by karellen on 2007-08-30
people who work in an office and don't care about updating the applications they use shouldn't be there in the first place

---

### Post by Mr. Picklesworth on 2007-08-30
Particularly scary is the people that spend $100 on licenses for virus scanners but never actually let them update. They go on some weird idea that a virus scanner automatically means they'll get no viruses.

With installers and updates, I think Ubuntu does really well. Its notification popups just don't pour as much anger into me as Windows's, and it has a nice way of staying out of the way the first time I say "no," as opposed to Windows' updater, which has the memory of a goldfish and the behaviour of a Jack Russel terrier.
(Then again, maybe I'm just weird. Does anyone else get feelings of aggression at the sight of speech bubbles in computer software?)

That, and the installation of a package is of course completely consistent and easy here, with very few buttons that one needs to press or things to read. (Windows installers, on the other hand, come in all different shapes and sizes, some containing more buttons than a space ship).

---

### Post by jrusso2 on 2007-08-30
All the IT departments I worked for we tested and rolled out updates and patches from the server after testing.

We sure didn't have the users do it.

---

### Post by BoyOfDestiny on 2007-08-30
> **aysiu said:**
> 
**Rant**
This is why I think Ubuntu won't be necessarily secure if we have a mass migration of ex-Windows users. Password stored as plain text? Oh, not a big deal, the next update fixes that.

Well, what if people don't install the next update?

Even my co-workers who have administrative privileges on their Windows PCs regularly view as an annoyance the balloon asking them for Windows updates... and they *don't* install them! They just ignore the balloon.

Convenience or apathy seems to be a much bigger draw than security.

I think people (ok I'm going to say I "know", since I did this myself...)
most Windows Updates require either closing whatever app you might be using, or a restart. It feels like a nuisance (if anyone has a different take on it, please share...)

Ubuntu updates (barring kernel updates, or a restart for firefox) will update the app, even if I'm running it, and does not require a full system restart.

I have two users that I switched to Ubuntu, I did initially encourage they do the update, and emphasized it was for security and restarts are rare (which has proven true so far for ~2+ years.) 

So far they have been good about it, but there are ways to automate or make the updates automatic. Whether it should be a default setting or something in future, I don't know... 

Definitely a valid concern. People who don't update software after these flaws are made public, are in for it... Personally I prefer the repos since it covers applications as well as the core OS.

---

### Post by hanzomon4 on 2007-08-30
Yeah it's easier to stay current in Ubuntu then in windows.

---

