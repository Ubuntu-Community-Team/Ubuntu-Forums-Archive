---
title: "Anti-virus just became useless (for a while at least)"
date: 2010-05-09
forum: The Cafe
---

### Post by 3rdalbum on 2010-05-09
[http://www.theregister.co.uk/2010/05/07/argument_switch_av_bypass/](http://www.theregister.co.uk/2010/05/07/argument_switch_av_bypass/)

[I]Researchers say they've devised a way to bypass protections built in to dozens of the most popular desktop anti-virus products, including those offered by McAfee, Trend Micro, AVG, and BitDefender.

The method, developed by software security researchers at matousec.com, works by exploiting the driver hooks the anti-virus programs bury deep inside the Windows operating system. In essence, it works by sending them a sample of benign code that passes their security checks and then, before it's executed, swaps it out with a malicious payload.

[...]

"Realistic scenario: someone uses McAfee or another affected product to secure their desktops," H D Moore, CSO and Chief Architect of the Metasploit project, told The Register in an instant message. "A malware developer abuses this race condition to bypass the system call hooks, allowing the malware to install itself and remove McAfee. In that case, all of the 'protection' offered by the product is basically moot."[/I]

And in the comments of this article:

"I bet it can't remove Norton.

NOTHING can remove Norton."

---

### Post by Windows Nerd on 2010-05-09
Sounds interesting...which is why I don't even bother to install and antivirus on my windows box.

---

### Post by murderslastcrow on 2010-05-09
They have sudo for Windows, but it doesn't really... work the way it's supposed to. The most secure way to run Windows is without an internet connection. That's why VirtualBox is so convenient. XD

---

### Post by Lightstar on 2010-05-09
Thanks to them for explaining how to do it.
Now we can move on and hack people and destroy their data.

---

### Post by gnupipe on 2010-05-09
funny story

---

### Post by Khakilang on 2010-05-09
World domination through computer!
:mad::mad::mad:

---

### Post by goldshirt9 on 2010-05-09
> **murderslastcrow said:**
> They have sudo for Windows, but it doesn't really... work the way it's supposed to. The most secure way to run Windows is without an internet connection. That's why VirtualBox is so convenient. XD

what so i dont have to run a  AV on virtual box with xp installed.

i am looking at installing a AV.
why dont i need one :confused:

---

### Post by madjr on 2010-05-09
80% of viruses are sponsored by AV companies, so i guess this scheme too..

---

### Post by lisati on 2010-05-09
> **madjr said:**
> 80% of viruses are sponsored by AV companies, so who cares..

Citation needed..... :)

Your best first line of defense against malware begins with being smart with what you open.

---

### Post by lancest on 2010-05-09
Lets not forget normal usage. 

Lets see your neighbor comes over with any type of usb enabled device and plugs into your Windows computer to share something fun.
 Your anti virus definitions aren't up to date and/or ineffective. 
(happens alot for many possible reasons)

After that your Windows pc wont' boot, exhibiting strange behavior and/or secretly key logging your financial transactions. 

IMHO This is a normal usage case and just shows how utterly unsafe Windows is.

---

### Post by Swagman on 2010-05-09
Hilarious

---

### Post by Giant Speck on 2010-05-09
What about "behavioral antiviruses" such as Threatfire that don't just look for viruses, but detect malicious behavior?

---

### Post by Diluted on 2010-05-09
> **lancest said:**
> Lets not forget normal usage. 

Lets see your neighbor comes over with any type of usb enabled device and plugs into your Windows computer to share something fun.
 Your anti virus definitions aren't up to date and/or ineffective. 
(happens alot for many possible reasons)

After that your Windows pc wont' boot, exhibiting strange behavior and/or secretly key logging your financial transactions. 

IMHO This is a normal usage case and just shows how utterly unsafe Windows is.
Any platform which does not distinguish malicious binaries from benevolent ones is susceptible to your example.

---

### Post by Shpongle on 2010-05-09
they already were useless , :popcorn:

---

### Post by chappajar on 2010-05-09
> **Lightstar said:**
> Thanks to them for explaining how to do it.
Now we can move on and hack people and destroy their data.

Security through obscurity is never a good idea.

---

### Post by lisati on 2010-05-09
> **Shpongle said:**
> they already were useless , :popcorn:

Sorry to disagree with you, but I've had AV software alert me when I've plugged in USB devices which had infected files on them which were "caught" from other machines, one of which was in such a bad way that it needed a reinstallation of Windows.

---

### Post by prodigy_ on 2010-05-09
> **Diluted said:**
> Any platform which does not distinguish malicious binaries from benevolent ones is susceptible to your example.

First, what's a malicious binary? No examples, please, just a definition that can be algorithmized. (Ahh, and keep in mind that false positives are unacceptable.)

Second, your "any platform" means that you don't know how permissions work in Linux (and in other Unices).

---

### Post by Ugluk on 2010-05-09
I don't use antivirus. I just not run strange binaries.

If a computer user can install arbitrary driver in system, the system security is flawed completely and antivirus would not be effective.

---

### Post by Ugluk on 2010-05-09
> **prodigy_ said:**
> Second, your "any platform" means that you don't know how permissions work in Linux (and in other Unices).Prodigy, would you come with revelation about primitive and outdated *nix permission system that we don't know of? Because they are kinda useless now and being replaced actively.

---

### Post by Npl on 2010-05-09
> It can also be carried out only when an attacker already has the ability to run a binary on the targeted PC.
Some pretty strong limitation dont you think?

---

### Post by Diluted on 2010-05-09
> **prodigy_ said:**
> First, what's a malicious binary? No examples, please, just a definition that can be algorithmized. (Ahh, and keep in mind that false positives are unacceptable.)
Whatever they use for malware definitions.

> **prodigy_ said:**
> Second, your "any platform" means that you don't know how permissions work in Linux (and in other Unices).
Well, assuming some sort of malware has infected a computer to a point where it can spread things to a USB drive, surely it can set whatever it wants to be executable?

---

### Post by madjr on 2010-05-09
> **lisati said:**
> Citation needed..... :)

Your best first line of defense against malware begins with being smart with what you open.

hehe the virus/malware is billion dollar industry where they create the sickness and then sell you the cure

is like cyber-terrorism

i would never use an antivirus that has a "premium" version, specially from the biggest sponsors of this scheme: norton / symantec

is so easy to move some ca$h off$hore

even the government and military have gotten infected and big bucks go into cleaning this up by 2 face AV companies

i would also go further saying that MS is benefiting in some way too as they are not interested in creating a fully secure OS and also sell these extra 2nd grade security products and support

yea a big cashcow for them

---

### Post by Merk42 on 2010-05-09
> **madjr said:**
> hehe the virus/malware is billion dollar industry where they create the sickness and then sell you the cure

is like cyber-terrorism

i would never use an antivirus that has a "premium" version, specially from the biggest sponsors of this scheme: norton / symantec

is so easy to move some ca$h off$hore

even the government and military have gotten infected and big bucks go into cleaning this up by 2 face AV companies

i would also go further saying that MS is benefiting in some way too as they are not interested in creating a fully secure OS and also sell these extra 2nd grade security products and support

yea a big cashcow for them

again, [citation needed]

and doctors just make people sick to stay in business
and IT people deliberately break customers' computers to stay in business
and home security systems employ cat burglars to stay in business

see I can make wild conspiracy accusations with no evidence too!

---

### Post by earthpigg on 2010-05-09
> and doctors just make people sick to stay in business

psychiatrists certainly do, and they are 'doctors'. drugging our children, claiming the kids all have ADD. im sure some small number of children actually do have ADD, but the vast vast majority that are currently in a permanent state of drugged stupor on the doctors orders... are just regular rambunctious kids.

of course they have trouble paying attention in 3rd grade math class... its a beautiful day outside, and they want to go outside and play! this is a good thing, not something we need drugs to fix. parenting is the solution.

[more about "doctors" earning a living by making people sick.]("http://www.naturalnews.com/019189.html")


> and IT people deliberately break customers' computers to stay in business

BestBuy. nuff said. also: selling computers with windows preinstalled.

[more about computers being sold as defective and broken machines.]("http://www.defectivebydesign.org/")

> and home security systems employ cat burglars to stay in business

probably not, on this one.

> see I can make wild conspiracy accusations with no evidence too!

it would appear that 2 of 3 of your satirical accusations were absolutely correct. thanks for driving home the absolute plausibility of madjr's post. 

creating/releasing a problem that only one group/person/entity has the solution for isn't something new. are you well versed in history, sir?

**_*Homework Questions! :D*_**

How did the Mexican-American war start? Who provoked it, and did that entity also have a solution readily available?

How did Stalin's purges start? Who created/encouraged the notion that large numbers of the population were traitors, and did that entity also have a solution readily available? 

more on topic:

Who frequently hires the authors of malicious software, thus making it's creation (even if not for direct & immediate financial gain) a viable resume builder? Do those entities also have a solution to the problem of malicious software?

---

### Post by kevin11951 on 2010-05-09
> **earthpigg said:**
> psychiatrists certainly do, and they are 'doctors'. drugging our children, claiming the kids all have ADD. im sure some small number of children actually do have ADD, but the vast vast majority that are currently in a permanent state of drugged stupor on the doctors orders... are just regular rambunctious kids.

of course they have trouble paying attention in 3rd grade math class... its a beautiful day outside, and they want to go outside and play! this is a good thing, not something we need drugs to fix. parenting is the solution.

[more about "doctors" earning a living by making people sick.]("http://www.naturalnews.com/019189.html")




BestBuy. nuff said. also: selling computers with windows preinstalled.

[more about computers being sold as defective and broken machines.]("http://www.defectivebydesign.org/")



probably not, on this one.



it would appear that 2 of 3 of your satirical accusations were absolutely correct. thanks for driving home the absolute plausibility of madjr's post. 

creating/releasing a problem that only one group/person/entity has the solution for isn't something new. are you well versed in history, sir?

**_*Homework Questions! :D*_**

How did the Mexican-American war start? Who provoked it, and did that entity also have a solution readily available?

How did Stalin's purges start? Who created/encouraged the notion that large numbers of the population were traitors, and did that entity also have a solution readily available? 

more on topic:

Who frequently hires the authors of malicious software, thus making it's creation (even if not for direct & immediate financial gain) a viable resume builder? Do those entities also have a solution to the problem of malicious software?

You may just be my new hero...

---

### Post by sydbat on 2010-05-09
> **kevin11951 said:**
> You may just be my new hero...Oh, earthy has been one of my hero's for quite some time...

---

### Post by lisati on 2010-05-09
> **Merk42 said:**
> and doctors just make people sick to stay in business
<snip>
see I can make wild conspiracy accusations with no evidence too!

> **earthpigg said:**
> psychiatrists certainly do, and they are 'doctors'. drugging our children, claiming the kids all have ADD. im sure some small number of children actually do have ADD, but the vast vast majority that are currently in a permanent state of drugged stupor on the doctors orders... are just regular rambunctious kids.


I've seen similar observations elsewhere about psychiatrists supposedly keeping patients unwell, over medicated, and other such problems. I'm usually left with a sneaking suspicion that although it is possible that there are crooks in "the system", some of the time people are still hurting from the difficult circumstances that led them to seeing the mental health professionals in the first place.

---

### Post by lancest on 2010-05-09
> **Merk42 said:**
> again, [citation needed]
and doctors just make people sick to stay in business

Not enough doctors focused on preventing illness, and drug companies thriving. Yes they have their motives.

Cops have some $ reasons to write more tickets too.

---

### Post by Sef on 2010-05-09
This has gotten off-topic, so locked.

---

