---
title: "Ubuntu One being forced on us through Update Manager"
date: 2014-05-28
forum: Ubuntu, Linux and OS Chat
---

### Post by DigitalGrinch on 2014-05-28
I Do Not use *Ubuntu One*. I had uninstalled it and the associated *Ubuntu One Music Store* through the Ubuntu Software Center YEARS AGO. I just checked, it is still uninstalled.

Why then is Update Manager wanting to install *Ubuntu One client*, *Ubuntu One client Python libraries* and *Ubuntu One synchronization daemon library*?

I feel it is being forced on me when I choose not to use it. I do not know how to remove it from showing up in Update Manager(I could only find posts with older Ubuntu versions that use Synaptics PM and do not apply to 12.04), and frankly should not have to if I uninstalled the applications, so I will have to uncheck it each time I update something. This is not acceptable.

This is the kind of BS that Apple or Google would pull. The reason many of us choose to deal with Canonical/Ubuntu, is because they are not a greedy publicly traded company that tries to force products down their customers throats.

I realize I may not get an answer from someone at Canonical, but I need to demonstrate my frustration with this decision by them.

---

### Post by QIII on 2014-05-28
Hello!

In a few days *nobody *will be using Ubuntu One, since it is being [shut down]("https://one.ubuntu.com/services/shutdown/").  I doubt that Canonical has any intent to force it on you.

Odd, then, that updates are being offered.

What version of Ubuntu are you using?

---

### Post by ian-weisser on 2014-05-28
> **DigitalGrinch said:**
> I feel it is being forced on me when I choose not to use it. I do not know how to remove it from showing up in Update Manager(I could only find posts with older Ubuntu versions that use Synaptics PM and do not apply to 12.04), and frankly should not have to if I uninstalled the applications, so I will have to uncheck it each time I update something. This is not acceptable.

This is the kind of BS that Apple or Google would pull. The reason many of us choose to deal with Canonical/Ubuntu, is because they are not a greedy publicly traded company that tries to force products down their customers throats.

I realize I may not get an answer from someone at Canonical, but I need to demonstrate my frustration with this decision by them.

Whoa, slow down there, buddy.
Let's not leap to tinfoil-hat conclusions just yet.
There's a chance that Major League Baseball and it's nefarious allies had nothing to do with it.

The usual answer is that you reinstalled, upgraded-to, or otherwise installed an application that depends upon ubuntuone-client.

The package manager will happily tell you:
```
sudo apt-get autoremove --simulate ubuntuone-client
```

---

### Post by DigitalGrinch on 2014-05-28
> **QIII said:**
> Hello!

In a few days *nobody *will be using Ubuntu One, since it is being [shut down]("https://one.ubuntu.com/services/shutdown/"). I doubt that Canonical has any intent to force it on you.

Odd, then, that updates are being offered.

What version of Ubuntu are you using?

UbuntuOne is going away? Great news.

12.04 LTS x64


> **ian-weisser said:**
> Whoa, slow down there, buddy.
Let's not leap to tinfoil-hat conclusions just yet.
There's a chance that Major League Baseball and it's nefarious allies had nothing to do with it.


what? is this an inside joke or a joke from a movie I have not seen?

> **ian-weisser said:**
> 
The usual answer is that you reinstalled, upgraded-to, or otherwise installed an application that depends upon ubuntuone-client.

The package manager will happily tell you:
```
sudo apt-get autoremove --simulate ubuntuone-client
```

Thanks for that command, although it raises more questions.
I did not have the client installed according to Software Center, so something else installed it, and prevented it from showing up there. What would be so sneaky?
 
This is what I just removed by taking out the --simulate of that command(after testing with it in)
Remv gir1.2-ubuntuoneui-3.0 [3.0.1-0ubuntu1]
Remv ubuntuone-client-gnome [3.0.1-0ubuntu1]
Remv libubuntuoneui-3.0-1 [3.0.1-0ubuntu1]
Remv libsyncdaemon-1.0-1 [3.0.2-0ubuntu2]
Remv ubuntuone-control-panel [3.0.1-0ubuntu1]
Remv ubuntuone-client [3.0.2-0ubuntu2]

All are related to ubuntuone, so not sure how it was re-added to my system, as I never installed any of these packages. Nefarious? yes, I think so

FYI I also had to remove python libs as they did not get autoremoved

```
sudo apt-get autoremove python-ubuntuone-client
```

---

### Post by ian-weisser on 2014-05-28
> **DigitalGrinch said:**
> what? is this an inside joke or a joke from a movie I have not seen?
Well, I suppose so.

> **DigitalGrinch said:**
> 
Thanks for that command, although it raises more questions.
I did not have the client installed according to Software Center, so something else installed it, and prevented it from showing up there. What would be so sneaky?



Ubuntu's packaging system is _completely_ transparent and trustable. I've mucked about deeply in it for years.
Canonical has _NO_ backdoor to install software without your consent. None.

Occam's razor suggests that you, not Canonical, not malware, not aliens, not Major League Baseball, not the Rotfang Conspiracy, likely did it at some point in the past few years. There are lots of ways to unknowingly add or reinstall software, and to overlook the 'are you sure?' dialogs. I've done it, too.

User negligence is understandably frustrating (been there!), but it's NOT someone else's nefarious intent.


Autoremove doesn't work for packages installed during the original install of Ubuntu. So either you have never removed python-ubuntuone-client on that install, or you manually installed it in the past. There is a very good technical reason for Ubuntu preventing autoremove on new-install packages: Users were mistakenly uninstalling big chunks of their system when trying to make minor changes that affected the -desktop metapackage.

---

### Post by mastablasta on 2014-05-29
also Ubuntu one was actually a good cloud service. fast and reliable. but they couoldn't compete with others in pricing & capacity.

since they stopped it you can actually create your own service like that (if you have a server at home).

these kind of services have various uses, from simple backup, to sharing pcis with your closed circle of people, to sharing work and collaboration with remote offices.

---

### Post by ssam on 2014-05-29
Update manager's job is to make sure that updates go smoothly. Before it existed problems with problems with updating between versions were far more common than they are now. One of the things it does is makes sure that you have a reasonable set of default packages installed, as new ubuntu release can bring new packages, which an 'apt-get dist-upgrade' might miss. A side effect of this is that sometimes a package that you have chosen to un-install will get reinstalled.

---

### Post by mikewhatever on 2014-05-29
Want to know why the ubuntuone-client is updated? Run **apt-get changelog ubuntuone-client**.
> ubuntuone-client (3.0.2-0ubuntu2.2) precise-proposed; urgency=medium

  * debian/patches/00_farewell-u1.patch:
    - Pop up a notice when connecting the service will stop on June 1 2014.
    - Avoid trying to connect after June 1 2014. (LP: #1306225)

 -- Rodney Dawes <rodney.dawes@ubuntu.com>  Thu, 22 May 2014 21:26:57 -0400

Not so scary even for the really paranoid.

---

### Post by grahammechanical on 2014-05-29
There is another Ubuntu One that has/had nothing much to do with the UbuntuOne cloud storage offered by Canonical. I have just used this other Ubuntu One to log in to this forum. Ubuntu One is the the name of what used to be called Ubuntu Single Sign On.

[http://en.wikipedia.org/wiki/Ubuntu_One](http://en.wikipedia.org/wiki/Ubuntu_One)

---

### Post by Copper Bezel on 2014-05-29
> **mastablasta said:**
> also Ubuntu one was actually a good cloud service. fast and reliable. but they couoldn't compete with others in pricing & capacity.
It certainly wasn't as fast or dependable as Dropbox.

> **ian-weisser said:**
> Ubuntu's packaging system is _completely_ transparent and trustable. I've mucked about deeply in it for years.
Canonical has _NO_ backdoor to install software without your consent. None.
They did have the ability to shift from OpenOffice to LibreOffice at the repo level so that one "update" removed OpenOffice and replaced it with LibreOffice. That's technically a little bit non-transparent, though certainly not a backdoor, either. (And I'm not knocking the decision at all, which was a good one.)

---

### Post by ian-weisser on 2014-05-29
> **Copper Bezel said:**
> They did have the ability to shift from OpenOffice to LibreOffice at the repo level so that one "update" removed OpenOffice and replaced it with LibreOffice. That's technically a little bit non-transparent, though certainly not a backdoor, either. (And I'm not knocking the decision at all, which was a good one.)

Well, I'd say it's arguable. I saw an open and transparent process for that decision, with many  points of view considered, and great care to impact the fewest users  negatively.

Ubuntu was already packaging a variant instead of stock OpenOffice, the decision to change effort and support to LibreOffice was publicly debated and open, and the secondary decision to change the upgrade path to the supported fork was also publicly debated and open. Both decisions were announced on The Fridge, where such an announcement would be expected, and picked up by many of the common Linux press outletsimmediately.

---

### Post by Copper Bezel on 2014-05-29
That's not transparency *in the package manager*, which is what was under discussion.

Understand, I have zero objection to the decision, but it does make the claim that Canonical can't push something out and have someone install it by mistake a fair bit more tenuous. (Which, again, I am *not *objecting to. It was just a wrong statement in defense, and pretty unnecessary given the original objection was to something that didn't really happen.)

---

### Post by ian-weisser on 2014-05-30
> **Copper Bezel said:**
> That's not transparency *in the package manager*, which is what was under discussion.

I think you're reading too narrowly.

Apt certainly _can_ be misused to almost-secretly install software unwanted by users.
So I would say the discussion of that process that prevents misuse in Ubuntu Repository packages is relevant.

If you specifically want transparency in apt: The change from OpenOffice to LibreOffice was clearly made in the *-desktop metapackage dependencies.

---

### Post by DigitalGrinch on 2014-05-30
I understand now, I did not reinstall anything, this was Canonical's doing so users would get the note about Ubuntu One closing. I do not agree with this decision to push it on those of us who uninstalled the software.
My question has been answered, my minor frustration vented.

this thread has clearly gone off-topic

---

### Post by bapoumba on 2014-05-30
Agreed, and we better leave it there. Should you want it be reopened, please report it and someone on Staff will have a look. Thanks :)

---

