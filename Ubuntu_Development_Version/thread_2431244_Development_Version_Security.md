---
title: "Development Version Security?"
date: 2019-11-13
forum: Ubuntu Development Version
---

### Post by Ice-Tea on 2019-11-13
Is there any difference in the level of security between the development version and the point release for patches and updates?

thanks

---

### Post by Frogs Hair on 2019-11-13
AFIK ,kernel related security  would be the same and there are no open ports by default. Using a development release as a daily driver is not a good idea. There are many issues that could be cause to reinstall during the development cycle. 3rd party and PPA software may not work or be incompatible and even native packages can break after updates.

---

### Post by Ice-Tea on 2019-11-13
Thanks Frog 

Broken packages is ok , i was more concerned if development of the software was more important than the security.

---

### Post by TheFu on 2019-11-13
It is called the *bleeding edge* for a reason.

---

### Post by Ice-Tea on 2019-11-14
> **TheFu said:**
> It is called the *bleeding edge* for a reason.

:confused:

I've read your post a couple of times and i don't understand how that explains if the Canonical developers release the Devel version with the same level of effort of security as the point release or if they leave it with standard default upstream settings for the testers?

---

### Post by guiverc on 2019-11-14
I too don't believe there is a difference between focal (development) and stable (eoan or older) with regards security. Development still has -proposed, which from my observations is the same (testing & procedure wise before it makes it into release repos), though making changes into the stable (released) release repositories does require the SRU which I gather is a load more work that is avoided if possible (ie. unless necessary).

This box was switched to 'development' (now 20.04) late in the 17.10 cycle (ie. before 17.10's release), and any '*problems*' have been extremely minor (I can't recall any anyway; even with -proposed packages though I don't usually use them unless asked to test for something specific).

Note:  I'm not a developer & thus this is my opinion from observation.

---

### Post by Ice-Tea on 2019-11-14
Thanks , i had a good search at google but i couldn't find anything on the subject.

---

### Post by TheFu on 2019-11-14
New is the enemy of stable and secure.

---

### Post by Ice-Tea on 2019-11-15
I still don't understand what that has to do with Ubuntu's security configuration policy on the development branch before it goes public for testing but thanks for sharing.:p

---

### Post by TheFu on 2019-11-15
> **lucap2 said:**
> I still don't understand what that has to do with Ubuntu's security configuration policy on the development branch before it goes public for testing but thanks for sharing.:p

I read it as a question about real-world security in using software that hasn't been tested together in a complete system but is used as production software.  Often, there are huge issues in pre-production software. Sorry.

---

### Post by Ice-Tea on 2019-11-16
I get you now. :P

Doesn't seem to matter these days if something is old or new when you consider all the grief OpenSSL has caused with ancient bugs and at a hardware level you now have side channel exploits like Spectre and Meltdown regardless what you are running.

Ubuntu prides itself on secure default settings with the latest patches when possible so i just wondered if the development version was the same or left to the testers to configure.

---

