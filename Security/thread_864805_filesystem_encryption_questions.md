---
title: "filesystem encryption questions"
date: 2008-07-20
forum: Security
---

### Post by addison3 on 2008-07-20
Hi, I'll be doing an installation of ubuntu soon (dual-boot with xp), and I have a few questions about filesystem encryption.

1. Would you recommend using Ubuntu's filesystem encryption options or using some other program for this? Is Ubuntu's built in filesystem encryption considered fairly secure, or would using another program be more secure? What options does Ubuntu's filesystem encryption have?

2. Which installation methods for Ubuntu allow me to do filesystem encryption (CD, internet, etc.)

3. Which encryption engines does Ubuntu's filesystem encryption allow? (Twofish, AES, etc.)

4. Can I do cascading encryption engines? (encrypting with a chain of encryption engines)

5. How much does filesystem encryption affect the speed of the operating system?

Thanks for the help!

---

### Post by hyper_ch on 2008-07-20
> **addison3 said:**
> 1. Would you recommend using Ubuntu's filesystem encryption options or using some other program for this? Is Ubuntu's built in filesystem encryption considered fairly secure, or would using another program be more secure? What options does Ubuntu's filesystem encryption have?
I'd use LUKS/dm_crypt as proivded by ubuntu... and IMHO it is secure... what do you mean by "what options does it have?"

> **addison3 said:**
> 2. Which installation methods for Ubuntu allow me to do filesystem encryption (CD, internet, etc.)
Alternate or server install

> **addison3 said:**
> 3. Which encryption engines does Ubuntu's filesystem encryption allow? (Twofish, AES, etc.)
It has AES and.... don't remember the rest

> **addison3 said:**
> 4. Can I do cascading encryption engines? (encrypting with a chain of encryption engines)
I don't think so

> **addison3 said:**
> 5. How much does filesystem encryption affect the speed of the operating system?
Normal operation you won't notice much but there is a slowdown for large read/write amounts.

---

### Post by addison3 on 2008-07-20
> **hyper_ch said:**
> I'd use LUKS/dm_crypt as proivded by ubuntu... and IMHO it is secure... what do you mean by "what options does it have?"

I was just wondering if there would be any good reason to use another program for linux filesystem encryption other than the one that comes with ubuntu, maybe something more customizable or more flexible or something. But ease of use is important, and if enabling the built in encryption in ubuntu during installation is the easiest option, that's probably what i'll do.

> Alternate or server install

Where do i find the "alternate" install? Is the server install the one that starts installing while downloading from ubuntu's site? Where do I find that?

---

### Post by hyper_ch on 2008-07-20
all downloadable from the ubuntu site.

---

### Post by kevdog on 2008-07-20
What cipher does dm_crypt actually employ?  Do you get a choice?

---

### Post by hyper_ch on 2008-07-20
you do

---

