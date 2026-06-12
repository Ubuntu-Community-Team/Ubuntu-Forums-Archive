---
title: "A question of importance."
date: 2008-05-15
forum: The Cafe
---

### Post by Swarms on 2008-05-15
In another thread, a person is advertising for his new media center operating system. The problem is that he has taken open source code applied some of his own and closed it to the public, that have to pay for it. For what I understand that is illegal, and would like you to give me input on what to do about since he fails to understand what he is doing wrong.

[http://ubuntuforums.org/showthread.php?t=782024](http://ubuntuforums.org/showthread.php?t=782024)

---

### Post by Dr Small on 2008-05-15
Under the GPL, you are allowed to sell your product, as long as you still provide the source code for the binaries. As long as he is giving the source code, he is free to sell it.

---

### Post by Mr A Mouse on 2008-05-15
> **Swarms said:**
> In another thread, a person is advertising for his new media center operating system. The problem is that he has taken open source code applied some of his own and closed it to the public, that have to pay for it. For what I understand that is illegal, and would like you to give me input on what to do about since he fails to understand what he is doing wrong.

[http://ubuntuforums.org/showthread.php?t=782024](http://ubuntuforums.org/showthread.php?t=782024)

As long as he makes the FOSS source code available, and has used no GPL (or other FOSS licensed) code in his closed-source modules, he's abided by the license terms and should be good to go. 

Now, by the same token, I despise the thought of advertising on a webforum ... but at least his advertisement is on-topic.

---

### Post by Barrucadu on 2008-05-15
If the source code to the free version is not available without buying the full version, that *is* a GPL violation, since the GPL specifies that you *can* charge for the source code, but only what is required to send it to the user (such as FTP server maintenence, or DVD shipping, or something).

---

### Post by Swarms on 2008-05-15
The only way of getting the sourcecode for the enterprise version is by buying the dvd for 49 euros, is it still legal?

---

### Post by Mr A Mouse on 2008-05-15
If I understand correctly, the only way to get the enterprise version at all is to buy the DVD. Therefore, they're selling the enterprise version, and just throwing the source code on the same disk. Nothing wrong with that in the GPL.

---

### Post by Swarms on 2008-05-15
Ok, I just thought it was illegal to sell something other have coded under the GPL license, without offering the source for free?

Sorry for the troubles then.

---

### Post by eragon100 on 2008-05-15
Thanx for the link, the free edition looks like a nice distro.

Might install it :)

---

### Post by Ub1476 on 2008-05-15
> **Mr A Mouse said:**
> If I understand correctly, the only way to get the enterprise version at all is to buy the DVD. Therefore, they're selling the enterprise version, and just throwing the source code on the same disk. Nothing wrong with that in the GPL.

But that's not showing the source code for **free**.

EDIT: I looked a the web page and noticed it's a free version there too, which is okay (Like Linspire/Freespire, Redhat/Fedora etc). If the features in the Enterprise version is written by him (and not under the GPL), he can sell that without showing the source code.

---

### Post by Swarms on 2008-05-15
> **Ub1476 said:**
> But that's not showing the source code for **free**.

That is what worries me.

---

### Post by Mr A Mouse on 2008-05-15
> **Ub1476 said:**
> But that's not showing the source code for **free**.

The GPL does not require you to make the source code universally available for commercial products. In such a case, the source code is being released to customers who purchase the product, but not to those who don't. Such behavior is perfectly permissible under the GPL.

---

### Post by Swarms on 2008-05-15
> **Mr A Mouse said:**
> The GPL does not require you to make the source code universally available for commercial products. In such a case, the source code is being released to customers who purchase the product, but not to those who don't. Such behavior is perfectly permissible under the GPL.
Thanks for clearing that up. :)

---

### Post by Mr A Mouse on 2008-05-15
No problems. :)

---

### Post by koenn on 2008-05-15
> **Mr A Mouse said:**
> The GPL does not require you to make the source code universally available for commercial products. In such a case, the source code is being released to customers who purchase the product, but not to those who don't. Such behavior is perfectly permissible under the GPL.
True. 
Besides that, you can look at that eAR Media Center thing as an experimental business model for free software / open source, different from the "give away products, charge for support" model. It's interesting.

---

### Post by saulgoode on 2008-05-15
> **Mr A Mouse said:**
> The GPL does not require you to make the source code universally available for commercial products. In such a case, the source code is being released to customers who purchase the product, but not to those who don't. Such behavior is perfectly permissible under the GPL.
I am a little unclear as to what you are suggesting. To be clear, if you distribute GPLed binaries commercially, you must offer the source of those binaries to anyone requesting it ("any third party") -- NOT just people who purchase the binaries.

The packager may include his own non-GPLed binaries with the GPLed binaries, and thereby not be required to provide source for his own work; but that does not lift the requirement to provide source code to the GPLed work. 

One final note, pointing to upstream (e.g., Ubuntu or Debian) source code repositories is not sufficient to meet the demands of the GPL with regard to providing source code. For commercial distribution of GPLed code, you must provide the source code *yourself*.

---

### Post by Swarms on 2008-05-15
Ok now I am confused again.

---

### Post by koenn on 2008-05-15
> **saulgoode said:**
> I am a little unclear as to what you are suggesting. To be clear, if you distribute GPLed binaries commercially, you must offer the source of those binaries to anyone requesting it ("any third party") -- NOT just people who purchase the binaries.

I don't remember reading that. The GPL goes something like "if you distribute a covered work in the form of object code, you need to distribute source code with it" - meaning you only need to provide source code to those that you're giving (or selling) object code to. 

> **saulgoode said:**
> 
One final note, pointing to upstream (e.g., Ubuntu or Debian) source code repositories is not sufficient to meet the demands of the GPL with regard to providing source code. For commercial distribution of GPLed code, you must provide the source code *yourself*.
"Pointing upstream" is, if I recall correctly, acceptible : "the Corresponding Source may be on a different server (operated by you or a third party)"

---

### Post by Mr A Mouse on 2008-05-15
> **saulgoode said:**
> To be clear, if you distribute GPLed binaries commercially, you must offer the source of those binaries to anyone requesting it ("any third party") -- NOT just people who purchase the binaries.

This is correct, and applies to the original binaries and to derivatives. It does not, however, apply to original work that interacts with GPLed binaries.

Case in point: SameGnome is a GPLed game available on almost any Linux distro with Gnome. If I write a separate program (using my own libraries) that analyzes and automatically plays a game of SameGnome, I am under absolutely no obligation to provide the source code for my program or libraries. 

To the best of my understanding, eAR is not offering GPLed binaries at all: GPLed binaries are downloaded and installed from  Debian/Ubuntu repositories, and all the DVD contains is their proprietary software and an installation script for the base OS.

---

### Post by eragon100 on 2008-05-15
And since I couldn't care less it's propietary, I have just finished burning the free version to disk and am going to check it out right now :)

Wish me luck :)

---

### Post by p_quarles on 2008-05-15
> **koenn said:**
> I don't remember reading that. The GPL goes something like "if you distribute a covered work in the form of object code, you need to distribute source code with it" - meaning you only need to provide source code to those that you're giving (or selling) object code to. 
What it says is this (section 2.b):
[quote=GPL v2]You must cause any work that you distribute or publish, that in whole or in part contains or is derived from the Program or any part thereof, to be licensed as a whole at no charge to all third parties under the terms of this License.[/quote]
As I understand it, this means that any linked libraries must be made available to anyone else who has a stake in GPL'd software. Which basically means anyone who asks for it.

---

### Post by Swarms on 2008-05-15
Ok, he has finally answered, nevermind him acting like a jerk in the topic, but all the same programs are on the free cd (with source) according to him, so there are no problems then.

---

### Post by Mr A Mouse on 2008-05-15
Good deal!

And ... perhaps what we are interpreting as "acting like a jerk" is simply having a bad day? I know I get pretty snappish when I'm not at my best.

---

### Post by Swarms on 2008-05-15
No its his usual etiquette, I have encountered him in a couple of danish hifi foras, when you try to ask questions about his OS, he goes all cocky, swearing and then leaves to never return. Consistently bad days is the case I guess. :P

---

### Post by koenn on 2008-05-15
> **p_quarles said:**
> What it says is this (section 2.b):

As I understand it, this means that any linked libraries must be made available to anyone else who has a stake in GPL'd software. Which basically means anyone who asks for it.
Section 2b is about modified source code of GPL'd programs, or re-useing gpl'd source code in other programs. I base that assumption on the fact that re-using binaries would be an "aggregate" or "bundle", and object code is dealt with  explicitely in the next session, section 3, by imposing additional requirements in top of those mentioned in the previous sessions. 
> 3.  You may copy and distribute the Program (or a work based on it, under Section 2) in object code or executable form under the terms of Sections 1 and 2 above provided that you also do _one of the following_:
     a)Accompany it with the complete corresponding machine-readable source code, ... on a medium customarily used for software interchange;

GPL v3 has a similar clause. 
To me, that means : you can take gpl'd source code, re-use it, and sell the resultig program on a cd or dvd, with the corresponding  source code on that same CD. Correct me if I'm wrong.

---

