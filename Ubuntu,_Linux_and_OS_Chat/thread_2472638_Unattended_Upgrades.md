---
title: "Unattended Upgrades"
date: 2022-03-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2022-03-07
I have a friend of a friend whose laptop might (I have yet to see it) be too low spec to run win10 (is it a win7 machine upgraded?).  A number of people have suggested she needs to buy a new laptop. If when I get it, it turns out that it is just too low spec wise l,k,ubuntu might be an option.  However, unlike some other machines I look after, this machine/person would be remote and I'm nervous setting up completely non tech person with a linux based machine.   I think my decision has already been made  - not worth it - but I would like your views as well.  Does having unattended-upgrades completely look after the updating with no user interaction (as per windows)?   The biggest hurdle for me is the 5yr/end of life issue.  Sad as it seems - unlike Windows, and I guess Mac, ubuntu is not quite there for the majority of non-tech (in any sense) users.

---

### Post by TheFu on 2022-03-07
After my Mom's Windows PC was hacked via social networking, I offered to setup Linux on her system, but with a few caveats.

a) I needed remote ssh access once a week.
b) Local backups would be setup, and 
c) I'd pull the most critical data to my network 3 states away once a week.

I'd visit her just 1-2 times a year for physical access.

She started with a Pentium4, but when that failed a local relative in the same city gave her a Core i7 desktop. Both looked the same from the outside.  She was running Lubuntu.  After the Core i7 swap, I pressed and pressed go hear how much faster everything was.  Mom didn't notice the difference.  "It's fine, about the same." was her answer.

I've made the same offer to my family - I'd provide IT support for their computers, but only if they ran an Ubuntu flavor and had remote access setup.  To me, patching 1 or 20 or 50 computers weekly isn't any different.

I did 1 LTS -to- LTS upgrade for her. Just to see how well it would go, I did it the day before flying up for a visit. The upgrade process warned that it was a bad idea, but worked well.  After the reboot, I was able to ssh in and the OS was the new LTS.  I wouldn't do that if I didn't have a remote console or wasn't planning to be there within a day or two.

I'm extremely anti-auto-update, because I've been burned.  Heck, a few days ago, a regular patch session removed a package that I use probably 20x a week, so there are still some dependency failures in some packages. Beware.

Run **inxi -Fxxz** on the computer if you want better recommendations about which OS can and should work.

You will need to suggest a way to handle LTS-to-LTS upgrades every few years.  Don't leave that unstated. I'd actually put the suggesting in writing and have them put a calendar entry somewhere as a reminder.

If you are unwilling to help maintain it, I wouldn't accept the system. Best not to start anything you aren't willing to follow through on issues concerning.  How will a dead SSD be handled?

Most normal people are probably better getting a cheap chromebook. Then they can love/hate google and not us. Best of all, any problems aren't ours.

---

### Post by him610 on 2022-03-07
> ...laptop... too low spec to run win10
Sounds like a good candidate for Chrome OS Flex. [https://chromeenterprise.google/os/chromeosflex/]("https://chromeenterprise.google/os/chromeosflex/")

---

### Post by TheFu on 2022-03-08
> **him610 said:**
> Sounds like a good candidate for Chrome OS Flex. [https://chromeenterprise.google/os/chromeosflex/]("https://chromeenterprise.google/os/chromeosflex/")

There are other solutions based on ChromiumOS, as compared to ChromeOS if you prefer to avoid Google stuff, like me.
[https://www.electromaker.io/blog/article/flint-os-vs-chromium-os-vs-cloudready-which-chrome-os-is-best](https://www.electromaker.io/blog/article/flint-os-vs-chromium-os-vs-cloudready-which-chrome-os-is-best) shows some options.

---

### Post by grahammechanical on 2022-03-08
I am of the opinion that all computer operating systems do similar things but in slightly different ways and with different applications.

The first hurdle to jump over is the question: Can this friend of a friend adjust to a different user interface and different applications. If the answer is no, then go no further. Some people stubbornly refuse to try anything different. With them it is Windows XP or nothing. They cannot be helped.

If this person is willing to learn then think about providing written tutorials on how to do things. Such as, using the update manager; why we are required to authenticate and how to do it; setting up email; the default applications. What does this person use a laptop for?

Regards

---

### Post by Quarkrad on 2022-03-09
Thank you for all your replies/opinions/advice.   The ChromeOS has given me some thought.  Like many I 'look after' a number of machines and have limited experience of those who are willing to give something different a try and change the way they work to those who stubbornly/unable/incapable to change.  Some I've had to revert back to their previous OS (always Windows).  This laptop's use is quite basic so potentially an ideal candidate but having asked some questions  (e.g. do know if you use any spreadsheets that have macros?) I've judged the user to be quick basic and may needing a lot of hand-holding.  Although not an issue in it's self I get the feeling this could take up a lot of time I don't have.  I've had a brief look at the laptop and there are number of things that need sorting and contribute to its slowing down.  Massive bloatware and (subscribed) OneDrive that I do not believe they actually need.  They seem to be paying MS  @£80 for something they perhaps do not need - there are other options to do what OneDrive is doing for them.  A fresh install of Win10 without all the bloatware and OneDrive will certainly give them a more responsive machine and the familiarity (apart, potentially from LibreOffice) they are use to.  In my experience people moving from MS Office to Open/Libreoffice have never had a problem (apart from the macro issue) so I do not anticipate any issues here.

---

### Post by mastablasta on 2022-03-09
> **Quarkrad said:**
>  The biggest hurdle for me is the 5yr/end of life issue.  Sad as it seems - unlike Windows, and I guess Mac, ubuntu is not quite there for the majority of non-tech (in any sense) users.

actually this is the smallest hurdle. process is automatic and requires a confirmation or a single command line. you can choose not to upgrade and remain on unpatched and unsecure OS. even the forever & last final version of windows - the windows 10 will now end their life and be replaced with windows 11.

---

### Post by pantazi on 2022-03-12
> **mastablasta said:**
> actually this is the smallest hurdle. process is automatic and requires a confirmation or a single command line. you can choose not to upgrade and remain on unpatched and unsecure OS. even the forever & last final version of windows - the windows 10 will now end their life and be replaced with windows 11.

+1
I was a total newcomer to Ubuntu some 4/5 years ago and began with 16.04, auto upgrading through 18.4 to 20.04 with no problems at all. I have recently purchased a second hand HP Probook, removed Windows and Installed Ubuntu easily transferring data.
I have learned a lot via these forums and would go so far as to say that getting more into Linux kept me sane during lockdown!

Nothing would persuade me to return to Windows. (I'm in my mid 70's, so not a bright young thing.)

---

### Post by DuckHook on 2022-03-12
I've taken on the task of moving a number of users to Linux. Mine is not a statistically relevant sampling but, as far as anecdotal evidence goes, here are my experiences:

Such a move only works if the following conditions are met:

[list=1]
[*]While the user doesn't have to be technically savvy, s/he needs to at least be a technophile—someone who enjoys tech. Those who treat technology as just an unpleasant means to an end—a necessary evil—are not good candidates.
[*]The newbie cannot be using this as a production machine. If s/he relies on this for work or to make a living, then even small learning curves become anxiety or panic inducing when confronted with the pressure to grind out a result by deadline.
[*]S/he has to be willing to work with you remotely and will not wilt when confronted with the command line. It's simply a fact of Linux life that some troubleshooting cannot be done on anything other than the old terminal.
[*]Clear and realistic expectations. Support is informal: consisting of you and an eclectic community of online geeks. The ability to take his/her ire out on a support person paid to put up with abusive frustration doesn't exist.
[*]Closely related to expectations, maybe even a subset, is willingness to adapt. This I found to be the toughest one. Some people have no idea what they are really getting into when they try to jump to Linux. It's a whole different world with different apps, different norms and different philosophies. The dev is king; not the user. It's based on community and sharing; not on silos and payment. It focuses on power, flexibility, adaptability and security; not on ease of use.
[/list]
Having said all that, Mrs DH happily uses Ubuntu and she is about the most nontechnical person I know. But she has me to look after the few little things that occasionally need looking after.

---

### Post by Quarkrad on 2022-03-14
Thank you all - I agree with everything. One of my 'users' is a non-techie 80 year old and I really have no involvement. However, after talking to this friend of a friend the following was stated - "my brother-in-law thinks I should go for an AppleMac".  I might be wrong but I saw this as my 'exit path' as earlier in the conservation, when I pointed out that paying @£160 per year (yes, per year) for cloud service/backup and antivirus could be avoided, there seemed to be little interested.

---

### Post by DuckHook on 2022-03-14
> **Quarkrad said:**
> &#8230;when I pointed out that paying @£160 per year (yes, per year) for cloud service/backup and antivirus could be avoided, there seemed to be little interested.
I should add that "saving money" is usually&#8212;not always, but usually&#8212;a bad reason to switch to Linux. I've had an unsuccessful transplant tell me: "the amount of time and aggravation I've gone through dwarfs the savings that I'm theoretically getting from Linux." Again, anecdotal, but it's a telling comment. A reasonable one too.

I think grahammechanical nails this one in his [post #5]("https://ubuntuforums.org/showthread.php?t=2472638&p=14084759#post14084759"). We sometimes need to remind ourselves that we have no obligation to support Linux for general users. This ought to be the default position. If we take on the task, it needs to be done for the right reasons, and whether those reasons are right or not is in the user's hands, not in ours.

I agree with your assessment that this prospect is not a good candidate for Linux. In fact, I doubt that this friend of a friend should be on anything other than an "AppleMac". ;)

---

