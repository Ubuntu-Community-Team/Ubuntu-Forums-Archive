---
title: "Should we change the default behavior of updates?"
date: 2016-11-22
forum: Ubuntu, Linux and OS Chat
---

### Post by ian-weisser on 2016-11-22
I think we should enable-by-default unattended upgrades for the -security and -updates repositories.
Currently neither is enabled by default, though users can easily enable -security using the GUI.

The current default setting made a lot of sense 15 years ago, when apt was new, testing was much looser, the build infrastructure and CI silos were a futuristic dream, and Ubuntu didn't exist.
It made sense 10 years ago.
It stopped making sense five years ago, as the Debian and Ubuntu build and testing infrastructures came on-line and eliminated whole classes of fail-to-build and regression and other formerly-common bugs that required downgrading.
Today we have a proven, reliable apt. We have strong testing and QA/QC and infrastructure. I have not had to downgrade a distro package in over a decade.

We now have throngs of users today who missed those years of growth and development. They get their daily/weekly apt notice, and click 'install' without reviewing or researching. Why are we pestering them with the notice at all anymore?

We have all see threads where the user wondered "why didn't the package manager take care of this for me?" I think that user is right - apt has included this capability for years. I have tested it for years - flawlessly.

I want to propose this change tot he Desktop Team...but I want your input first!

---

### Post by wildmanne39 on 2016-11-22
For security I do agree but not so sure we should take control of normal updates out of the hands of the user, ubuntu is about choice and control by the user so I am not sure how people would perceive updates being automatic, I personally do not like it when I boot an OS that installs updates without asking me first.

---

### Post by Bashing-om on 2016-11-22
@ian-weisser; +1 from me.

> 
I think we should enable-by-default unattended upgrades for the -security and -updates repositories.
Currently neither is enabled by default, though users can easily enable -security using the GUI.


After all is this not the function of the update-manager ? Else why run it ? 
In the GUI how many users do look to observe what is going to be updated ? Those of us that want to be aware do not run with the update-manager, and handle updates manually on  regular basis.

As responders for aid and assistance, the 1st order of operations is always to insure the system is fully updated. How many times has updating a system resolved the problem ?

We tout ubuntu as "user friendly"; As such we do all we can to make it the more so.

[INDENT][INDENT][INDENT]every little bit helps
[/INDENT][/INDENT][/INDENT]

---

### Post by sudodus on 2016-11-22
> **wildmanne39 said:**
> For security I do agree but not so sure we should take control of normal updates out of the hands of the user, ubuntu is about choice and control by the user so I am not sure how people would perceive updates being automatic, I personally do not like it when I boot an OS that installs updates without asking me first.

+1

Starting with Xenial, security upgrades ***are*** automatic by default, which I think is good (but causes problems in live and persistent live systems, that are left running overnight - this is fixed (turned off by casper, so only for live and persistent live systems) in Yakkety and should be fixed in 16.04.2 LTS).

---

### Post by deadflowr on 2016-11-22
Some sort of message indicating that the unattended upgrades are enabled would be nice.
(And a quick instruction on how to turn off)
Otherwise I'm fine with it set as the default.

A message would be helpful for those who have legacy updating behavior and get frustrated when they run apt-get or open the software updater and see either the *waiting to exit* message(software updater) or the *could not open /var/lib/dpkg/lock* (apt-get), because the unattended upgrade is already running.

Where to put a message, though...

---

### Post by ajgreeny on 2016-11-22
> **wildmanne39 said:**
> For security I do agree but not so sure we should take control of normal updates out of the hands of the user, ubuntu is about choice and control by the user so I am not sure how people would perceive updates being automatic, I personally do not like it when I boot an OS that installs updates without asking me first.
^^^^+1
I always turn off automatic updates and do not even allow the software-update application to run automatically on my machine, as I like to update packages when I want not when the OS decides the time is right.

I can however see a very good reason for security updates to be carried out unattended by default for most users who may not realise how critical it is to keep software updated, but I am like Bashing-om from post #3, I like to control things myself.

---

### Post by ian-weisser on 2016-11-22
I certainly understand wanting to control things myself.
Me, too...and I suggested this change!

The change isn't intended for us. As proposed it's super-easy for us power-users to change one setting and get our desired behavior back.

The change is intended for all those people we help, who are not power users, who expect update notifications to be important (they usually are not), who do not understand apt commands or policies (why should they?), and who can soon get background auto-updates from their kernel and their snaps.

---

### Post by oldos2er on 2016-11-23
I miss the "fix 100 bugs" thing Canonical used to do, which could've easily taken care of the security updates, if nothing more. Sure hope you can get the Desktop team's attention with this, ian-weisser.

---

### Post by Irihapeti on 2016-11-23
As you put it, ian-weisser, it makes sense. We can change it to behave the way we wish, and those who otherwise are not likely to update if left to their own devices are taken care of.

I suppose the only concern might be those occasions when there are a few kernel updates in fairly close succession. But then, how many people leave their machines running all the time? (And, no, I don't know the answer to that question.)

---

### Post by mastablasta on 2016-11-24
-1 on both updates.

 a better way would be to explain the logic to users and offer a nice gui (maybe during or immediatelly after) install with these 2 update types enabled by default (others as option) as well as an option to disable it all.

reason - you travel say to venice airport with their expencive wi.fi. you surely do not want to update the kernel and pay for it at that time. similary if you need to use limited mobile connection. an option would also be to tunr it on or off or to enable it only if you have wire connections. kind of like andoid does which would update or an app download only when there is wi-fi connection for exmaple (well depending on setting).

anyway this is the reason why one of the first things i did on Windows was to disable auto updates and replace it with "notify me". so i can choose when i want my system resoruces to be used for update. similary this is the setting i have now at work on win10 (i can postpone the update until in AD or on cable). what could (theoretically) happen is that i would use my mobile phone to connect to internet abroad for osme other reason and it the update would eat up my data plan.

i agree that these are safe and stable and i have them enabled on server, but not on desktop. again for similar reason - i do not want the updates to run during work and we do not leave the Linux deskotp PC on all the time (issues with suspend/hybernate...). if it all worked and PC was on all the time i would definitelly use the unnatended updates and enabel these two repos (scheduled to run during nigh ofcourse)

---

