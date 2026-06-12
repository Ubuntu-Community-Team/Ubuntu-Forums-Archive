---
title: "What is the risk of adding a bad ppa?"
date: 2021-07-10
forum: Security
---

### Post by kaky951357 on 2021-07-10
[COLOR=#D7DADC][COLOR=#000000]Hello folks,
[/COLOR]
[COLOR=#000000]After  installing ubuntu, i was searching for a way to control my external  monitor brightness over DCI/CI. I found this github page [/COLOR][[COLOR=#000000]https://github.com/LordAmit/Brightness[/COLOR]]("https://github.com/LordAmit/Brightness")[COLOR=#000000]  offering a solution for my problem. i added the ppa without thinking about the risks ... i'm a noob and i don't know what is the repercussion of adding a  "bad" ppa. my questions are :
[/COLOR]
[COLOR=#000000]Is  there security risks when adding a ppa and update without  installing a software from it ? (i didn't install any software from that  ppa)
[/COLOR]
[COLOR=#000000]Does the ppa that i added look suspicious?[/COLOR]
[COLOR=#000000]What is a "bad" ppa and what are the risks of adding a bad ppa (security and stability-wise)?[/COLOR]
[COLOR=#000000]Thank you for your answers.
[/COLOR]
[COLOR=#000000]Have a great day.[/COLOR]

[/COLOR]

---

### Post by scorp123 on 2021-07-11
> **kaky951357 said:**
>  Is  there security risks when adding a ppa and update without  installing a software from it ?

Short answer: Yes. At least in theory. A malicious PPA maintainer or an intruder who hacked the PPA and now has it under his control could introduce a package that has the same name as a real package that exists elsewhere and give it an artificially high version number. Your OS would now see that manipulated package as "Update" and install that malicious package over the real package....

Example:

In Ubuntu 20.04 the official Firefox browser is at version 89.0.2 ...
```

 > apt show -a firefox
Package: firefox
Version: 89.0.2+build1-0ubuntu0.20.04.1
Priority: optional
Section: web
Origin: Ubuntu
... (rest of output removed) ...

```

A malicious PPA maintainer could now create a Firefox package (one that contains a Trojan horse and thus creates a backdoor into my system ...) with the version "99.99" ... and if I don't pay attention my OS might pull this from that repository thinking it's an "Update".  And taddaaaa, I unwittingly installed a backdoor into my system thinking it's "just the web browser".


> **kaky951357 said:**
>  Does the ppa that i added look suspicious? 
I'm rather paranoid so to me everything is usually suspicious. But that's just me...


> **kaky951357 said:**
>  What is a "bad" ppa and what are the risks of adding a bad ppa (security and stability-wise)?

Regarding security: See above. Stability is the other issue: Depending on what updated packages you wanted from a certain PPA it could be that the packages you pulled from there are replacing older but stable packages in your OS with brand-new but not so well-tested ones. 

For argument's sake, let's say you you experimented with a PPA and replaced some packages that came with your OS installation with stuff from the PPA ... and you're not liking the results because now things start breaking, crashes happen, you get core dumps, sudden reboots. In short: Stability is no longer what it used to be.

These are the commands to get rid of the PPA and everything it ever installed:
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:*NameOfPPAhere*

```

This will wipe the PPA and all the stuff it installed from your system. You could then get the packages from the official Ubuntu repositories again and thus reinstall the good versions of whatever package the PPA messed up.

---

### Post by kaky951357 on 2021-07-11
Hello, thank you for your reply.
I executed the command to purge the ppa :
```

sudo ppa-purge ppa:*NameOfPPAhere*

```
```
Updating packages lists
PPA to be removed: apandada1 brightness-controller
Warning:  Could not find package list for PPA: apandada1 brightness-controller

```
I had already removed the ppa with the gui interface.
Lets say this ppa installed some malicious software on my system. after purging the ppa will the system remove all the malicious software after an upgrade? 
thanks again.
Have a great day.

---

### Post by ajgreeny on 2021-07-11
Running ppa-purge will remove the version of a package from the ppa and, assuming such a package exists in the standard repos for your version of Ubuntu, that standard version will be installed, replacing the ppa version.
If the ppa installed a package that is not available in the repos, the ppa version will be removed but not replaced with anything else.

For your information, I have several ppa versions of packages installed and have never had any problems; I use Chromium from a development ppa which is very successful, avoiding the snap version completely, and also use LibreOfice from the ppa currently offering version 7.1.4.2 in place of 6.4.7.  I also have one or two that offer packages that are otherwise not available in the repos, eg mkusb.

---

### Post by scorp123 on 2021-07-12
> **kaky951357 said:**
>  I had already removed the ppa with the gui interface.

In that case "ppa-purge" hasn't done anything. All the potentially bad packages are still there.
Re-add the PPA and then use "ppa-purge" so it can do its job.

---

### Post by TheFu on 2021-07-12
A PPA can replace the kernel, so they are extremely dangerous. You could pwn yourself unknowingly.  Application installs are just the tip of the iceberg with PPA risks.

There are many different ways to calculate the risks, but most are an exercise in guesswork, since we'll never know how many PPAs there are or how many bad PPAs there are. Those two numbers would be required to calculate risk, right?

As for mitigation, I have a few rules for which PPAs I'll add to a system.  Are they reputable?  Have multiple, other, people, recommended the specific PPA?  Do I know the person's reputation?  For example, mkusb is created by a long-time forum contributor here. We've never met, but I trust him to try hard to do good stuff.  I would trust the Intel PPA for ethernet drivers too.  

I would not trust the AMD or nvidia PPAs (if they had any) to provide working GPU drivers.  That's because I've been burned by unstable code from both.  I can wait until Canonical puts any new GPU drivers into their additional drivers list and I get updates automatically.

I have the x2go PPA from that team and I have mc3man's mpv PPA. He's active here and mpv is freakin' amazing!  And I have the firejail PPA from that team - mainly out of necessity.  

Canonical can't keep up with the necessary changes for some reputable programs to keep working.  Firejail is one.

I avoid snap packages. They don't work on most of my systems anyways, so that isn't hard.
I avoid installing from source for almost all software, except 1 that comes to mind.  youtube-dl.  That software is constantly being tweaked, so it changes almost weekly. Because it is python, they don't bother with a PPA, but they build an "update" capability into the code itself. I have my weekly patch process perform an update for me on the systems where I run that script.  It does a few other things, like removing old kernels, removing old snap versions (snap wants to keep 2-3 versions).

I've never bothered with ppa-purge.  Why have an tool to delete a file?  PPAs are just text files put into /etc/apt/sources.list.d/ with a specific filename pattern.  Just change the .list from the end to anything else and that PPA will be disabled.  Deleting the file works too.  Most PPAs have descriptive names to help us know their purpose. *x2go-ubuntu-stable-focal.list*   Gee, I wonder what that PPA file is for? Not really.  Adding a PPA is a little harder because cryptographic signatures are part of the process.  
After deleting or changing the filename of a PPA, run **sudo apt update** to update the internal "where's that software" information in APT.

---

### Post by scorp123 on 2021-07-12
> **TheFu said:**
>  I've never bothered with ppa-purge. 

And what did you use instead to hunt down rogue packages that might have gotten installed by a PPA?

> **TheFu said:**
>   Why have an tool to delete a file?  

It does more than that. It also hunts down whatever was installed from that PPA and removes that too. Because just removing the PPA file does not automagically remove whatever it was you happen to have installed from there...

> **TheFu said:**
>  After deleting or changing the filename of a PPA, run **sudo apt update** to update the internal "where's that software" information in APT.

Yes, and how do you want to get rid of anything that you maybe already installed if not by using "ppa-purge" ...?

---

### Post by TheFu on 2021-07-12
So, the forum problems aren't all solved.  I'm getting the posting error again.  My workaround is to put that content into a pastebin and link it here.
http:// s p r u n g e . u s /0o83kX

Have to break up the URL, so it doesn't get censored. Sorry.  Hopefully, my 10 or so exact posts that weren't accepted by the forum software are helpful to Canonical to correct whatever the posting issue might be.  I don't see any clear pattern, though I though I had a few times.

---

### Post by ajgreeny on 2021-07-12
> **scorp123 said:**
> And what did you use instead to hunt down rogue packages that might have gotten installed by a PPA?



It does more than that. It also hunts down whatever was installed from that PPA and removes that too. Because just removing the PPA file does not automagically remove whatever it was you happen to have installed from there...



Yes, and how do you want to get rid of anything that you maybe already installed if not by using "ppa-purge" ...?
You can do it with synaptic if you have it installed, and I think it is well worth having available.
Using synaptic go to Origin in the left hand pane and click on the line for the PPA concerned.  That will list all packages that are contained in the PPA and you can see form the list which are installed and remove them, then disable the ppa and finally refresh the repos and reinstall all packages that you just removed.

Much easier, however, to simply run ppa-purge.

---

