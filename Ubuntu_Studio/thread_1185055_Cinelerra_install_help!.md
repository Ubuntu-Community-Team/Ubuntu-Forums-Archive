---
title: "Cinelerra install help!"
date: 2009-06-11
forum: Ubuntu Studio
---

### Post by samh785 on 2009-06-11
Ok, so here's what's happening. I really need a step-by-step walk through of installing cinelerra on Jaunty. I'm a huge noob, and the other threads on this subject don't seem to help me... :(

---

### Post by qamelian on 2009-06-11
The easiest way is to go here: [http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php) and scroll down until you find the instruction for adding the cinelerra repository for Ubuntu.

---

### Post by samh785 on 2009-06-11
> **qamelian said:**
> The easiest way is to go here: [http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php) and scroll down until you find the instruction for adding the cinelerra repository for Ubuntu.
ok, so I downloaded  [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb)
and I guess it put in the akirad repository, but cinelerra isn't showing up in the add remove applications thing. :[

---

### Post by qamelian on 2009-06-11
I never use Add/Remove as I prefer Synaptic Package Manager so I can't help you there, but if you load Synaptic from System > Administration >  Synaptic Package Manager and click the reload button on the tool bar, you should be able to find Cinelerra using the search feature in SPM after the reload finishes.

---

### Post by samh785 on 2009-06-11
nope, it's just not there. I don't understand this at all! haha :P

---

### Post by qamelian on 2009-06-11
> **samh785 said:**
> nope, it's just not there. I don't understand this at all! haha :P
Very weird. I installed it using the repo from the link I sent you without any problems. If you look under Settings > Repositories on the Third-Party tab, do you see an entry for this repo?

---

### Post by samh785 on 2009-06-11
here's a picture:
[IMG]http://img142.imageshack.us/img142/139/repo.png[/IMG]

---

### Post by samh785 on 2009-06-11
ok, now for some reason, the cinelerra packages started showing up. I installed and it works! thank you very much qamilian!__

---

### Post by qamelian on 2009-06-12
> **samh785 said:**
> ok, now for some reason, the cinelerra packages started showing up. I installed and it works! thank you very much qamilian!
No problem. Glad I could help! :)

---

### Post by Xander9791 on 2009-06-13
I have tried several times to get the appropriate repos in to be recognized and I could not get any results when I searched for cinelerra in add/remove or synaptic. I get some hits and some failures for different sites when I reload, so I know that I should get something.
   I resorted to just downloading the package from a link and double clicking and letting synaptic take over from there (don't understand why this isn't the standard procedure). I installed and cinelerra showed up in my list of apps, but will not start. I start it in terminal and get this:

bill@bill-desktop:~$ sudo cinelerra
[sudo] password for bill: 
cinelerra: error while loading shared libraries: libIlmImf.so.2: cannot open shared object file: No such file or directory

Any ideas on how to fix this or reinstall it correctly?

BTW I installed the file which is for 7.10 and I use 9.04.

---

### Post by cotcot on 2009-06-14
Sometimes it is easy. There is a binary [[COLOR="Blue"]here[/COLOR]]("http://www.heroinewarrior.com/cinelerra.php#download") that you only need to download, extract, go into the extracted folder and start with ./cinelerra.

---

### Post by Gannon8 on 2009-06-20
First, why are you trying to run it as root? You don't need to. Second, you should use the 9.04 version, seeing as Ubuntu 7.10 isn't supported anymore.

---

### Post by Bartender on 2009-07-11
I just wanted to update this - with a brand-new install of 9.04, I went to the Cinelerra website and followed the directions to add the cinelerra repository.  The rest of it must have seemed self-evident to the author but of course it's not for the less experienced operator.
Installing the package from the cinerella website does indeed do several things for you that could be confusing if trying to do them yourself.  But the package at the cinerella site doesn't INSTALL cinerella, it sets things up so that Synaptic will know what to do when you ask it to do a search for Cinerella.
So, install the correct package from the Cinerella website, then go to Synaptic and ask it to reload, then restart the PC, go back to Synaptic, and do a Search for cinerella.  It should show "cinerella cv".  Click on that, mark for installation, Synaptic will tell you that it needs several other items, and proceed.
As the OP mentioned, he didn't at first see cinerella in Synaptic.  Neither did I until restarting the PC.  I don't know why that is, but after a restart everything worked fine.

---

### Post by tommah04 on 2009-07-12
I got a different problem with cinelerra that I hope someone has an idea....

I start cinelerra and then it just freezes... I can switch between all the windows, but can't do anything

---

### Post by tommah04 on 2009-07-12
i get this error

---

### Post by thelastquincy on 2009-07-21
> **cotcot said:**
> Sometimes it is easy. There is a binary [[COLOR=Blue]here[/COLOR]]("http://www.heroinewarrior.com/cinelerra.php#download") that you only need to download, extract, go into the extracted folder and start with ./cinelerra.

Exactly how does this start ./cinelerra work...i have the file downloaded and extracted to my home folder I open folder and then what?? You make it sound so easy yet it isn't...

-Steve

---

