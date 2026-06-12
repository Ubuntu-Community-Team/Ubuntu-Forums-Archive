---
title: "ubuntu --&gt; windows"
date: 2010-09-04
forum: The Cafe
---

### Post by psihokiller4 on 2010-09-04
well it's I don't know where to ask this and here it seems most appropriate and I'll ask

is ubuntu going in way of windows as system does everything and we can't really control it or let say we don't really know what EXACTLY will system do before it does it


and if it does witch linux distro is mostly against that rule except:
LFS and arch linux -- as I tried on arch and I'm too little linux lvl to start at arch


what would you guys recommend?




sorry if I posted in wrong section

---

### Post by TheNessus on 2010-09-04
> **psihokiller4 said:**
> well it's I don't know where to ask this and here it seems most appropriate and I'll ask

is ubuntu going in way of windows as system does everything and we can't really control it or let say we don't really know what EXACTLY will system do before it does it


and if it does witch linux distro is mostly against that rule except:
LFS and arch linux -- as I tried on arch and I'm too little linux lvl to start at arch


what would you guys recommend?




sorry if I posted in wrong section

I honestly don't understand your question.

---

### Post by NCLI on 2010-09-04
I understand, but don't agree. Examples of Ubuntu not telling you what it's going to do?

---

### Post by psihokiller4 on 2010-09-04
ok when I say let say

I update the system

and after update the system becomes completely unstable from perfect stable system

---

### Post by psihokiller4 on 2010-09-04
or let say I need to install something

and it says we need to install 300 more applications and libraries to run that thing and 20 included in that install other app and lib makes the system unstable

and the system doesn't say those 2 programs interact each other in wrong way

---

### Post by psihokiller4 on 2010-09-04
all this apps and libs are unique names and you have to be a genius to know all of them
and how they interact with each other

so when I want to install 1 thing how can I know it won't interact with other system programs in wrong way (CPU working for nothing),(something in video doesn't work any more), ...

---

### Post by cpmman on 2010-09-04
Yes - I remember when tens of thousands of AVG users lost access to the internet and many had the whole system tied up for two months when Microsoft sent out a security update that prevented AVG from working.

Fortunately I have not had that problem with Ubuntu.

---

### Post by Legendary_Bibo on 2010-09-04
Okay first off you don't need a new post for every sentence. Second, what are you talking about? When you install anything it tells you what's going into it. lib files are like dll's. Metapackages are blank files that just link to all the dependencies needed, etc. It tells you what it's installing, or removing. It won't remove anything unless you let it.

---

### Post by psihokiller4 on 2010-09-04
yes but how should I know it won't destroy my system?

or it won't interact in wrong way?

---

### Post by Legendary_Bibo on 2010-09-04
> **psihokiller4 said:**
> yes but how should I know it won't destroy my system?

or it won't interact in wrong way?

Typically it won't. I've downloaded over a hundred application packages and other random things from it, and I have yet to have a conflict. If you're that worried then keep a backup.

---

### Post by NightwishFan on 2010-09-04
Packages go through all sorts of testing before being updated or released. Software under 'Main' in Ubuntu is the most tested. If you are using a development version of Ubuntu such as a Beta, it is designed only for early previews and bug testing.

If you are concerned about stability the current LTS (Long Term) version of Ubuntu, 10.04, is already on its first bug fix release and should be free of many issues.

---

### Post by jeight on 2010-09-04
Linux runs differently than Windows. In windows each application is a standalone program that uses all of it's own files to run. Linux software on the other hand will use libraries from other applications that is already installed. Because of this there is less chance that software will conflict. Linux normally already knows which lib files don't work together and will warn you if something might run funky. Windows on the other hand never knows. That is why windows computers tend to start running slower over time. There are too many independent programs trying to take charge.

Chances are you will never run into an issue using Linux and if you do you were probably warned on installation that something wasn't right.

---

### Post by Brunellus on 2010-09-04
There is a continuum between stability and progress.  If you install an LTS release of Ubuntu, it should be fairly "stable," since, after a certain point, only security fixes will be released for that software (no new features will be added).  Of course, if you ONLY install LTS versions, you'll have a three-year release cycle to reckon with.

On the other extreme would be debian-unstable, where the packages are new every day.  You'll get the newest, shiniest everything--but you won't be sure that a new update doesn't hose you completely.

Most things in Ubuntu are still configurable on the command-line, or by messing with the necessary text config files--so in terms of obscuring the system, Ubuntu is nowhere near as obscure as Windows.

Otherwise, I can identify a few other concerns:

"interact in the wrong way."  This is actually taken care of by the deb/apt package management system.  Synaptic (the GUI package manager) or aptitude or even apt-get (these two are command-line) will solve dependency problems like this automatically.  It is very easy to take this for granted--if you want a taste of how it used to be, install Slackware (that's another Linux distro--arguably the oldest currently-maintained one) without a package manager, and figure out your dependencies by hand.

"unique names"  I don't understand this.  Programs are named by their developers for a number of reasons.  But if you're looking for names that copy the names of analogous proprietary software (so, "Excel" in Linux, for instance) you're out of luck because that name is trademarked.  The devs couldnt use it even if they wanted to, since the trademark owner would sue them for trademark infringement.  

Indeed, software naming in general is far from logical.  It's not obvious that "firefox" is a web browser, that "thunderbird" handles e-mail, or that "Excel" (to use that example, again) is a spreadsheet program that allows me to do mathematics;  nor is it obvious that "outlook" is an e-mail/calendar/scheduling/behemoth, nor that "Quarx" is a desktop-publishing suite, nor that "Avast" has anything to do with malware.

---

### Post by cariboo on 2010-09-04
Looking at the op's posting history, most of his problems are of his own making, and as he stated in [this]("http://ubuntuforums.org/showpost.php?p=9690415&postcount=15") post that he no longer uses Ubuntu, there is no use in continuing this discussion. Thread closed.

---

