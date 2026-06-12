---
title: "Empathy Rant"
date: 2010-05-19
forum: The Cafe
---

### Post by Docaltmed on 2010-05-19
With my recent upgrade to Lucid, I began using Empathy. Much to my surprise, I found that I cannot turn off logging in Empathy; even more to my surprise was that this critical issue was brought to the developers' attention over a year ago, and nothing has been done. 

From the devs point of view, this is a apparently a wishlist kind of thing -- nice to have, but not critical. 

However, for anyone in journalism, legal, or medical fields, the inability to turn off logging in Empathy makes it not only unusable but quite possibly illegal, and quite certainly could open up any one of these professionals to malpractice claims.

I am a doctor. I have confidential discussions with patients and patients' attorneys. Sometimes, such discussions will be by necessity confidential and off the record. Chat is an increasingly frequent way that I keep touch with my patients and others, and I had been using Pidgin to this end.

The fact that this bug has been brushed off for over a year is, to my mind, unfathomable. I could understand it better if Empathy had not been incorporated as one of the core applications in the Ubuntu desktop. 

While Ubuntu's historical user base may have once been computer geeks and x-gens chatting with their peeps, increasingly these days, Ubuntu is the standard operating system for corporations such as mine. Core Ubuntu applications need to grow up as well and recognize that fact. Canonical is not going to get much penetration into business such as mine by positing such utterly flawed software as standard -- and then refusing to recognize the magnitude of such an error.

It's no big problem to move back to Pidgin. I'm just astounded by the blindness.

---

### Post by Paqman on 2010-05-19
> **Docaltmed said:**
> 
I am a doctor. I have confidential discussions with patients and patients' attorneys. Sometimes, such discussions will be by necessity confidential and off the record.

Have you contacted the devs to point this out? This seems like a very sound reason to disable logging. I'm not saying they'd change their mind, but it might add weight to the case.

> **Docaltmed said:**
> Canonical is not going to get much penetration into business such as mine by positing such utterly flawed software as standard -- and then refusing to recognize the magnitude of such an error.


Like most of the software in Ubuntu, Empathy isn't actually developed by Canonical. Creating a fork to introduce a new feature just for Ubuntu would be rife with difficulties in itself.

---

### Post by Docaltmed on 2010-05-19
> **Paqman said:**
> Have you contacted the devs to point this out? This seems like a very sound reason to disable logging. I'm not saying they'd change their mind, but it might add weight to the case.

Yeah, that's the thing of it. The first person to report this bug was a journalist, who made a very cogent argument for a fix. Nothing really happened, though.

---

### Post by Paqman on 2010-05-19
> **Docaltmed said:**
> Yeah, that's the thing of it. The first person to report this bug was a journalist, who made a very cogent argument for a fix. Nothing really happened, though.

Hmm. That sucks. I'd still chuck your hat into the ring though.

---

### Post by philinux on 2010-05-19
[http://osdir.com/ml/ubuntu-devel/2010-03/msg00317.html](http://osdir.com/ml/ubuntu-devel/2010-03/msg00317.html)

Delete them here. .local/share/Empathy/logs

---

### Post by madjr on 2010-05-19
i was surprise to hear that corporations would use empathy

i've only seen casual use of it

i didn't mind the logging i found it useful, i would just hit **clear log** if too long

anyway i see your point and the devs should implement the feature, **very easy to do**

i think it could be marked as a **papercut** (easy fix usability issues)

check here:
[http://ubuntuforums.org/showpost.php?p=9150240&postcount=12](http://ubuntuforums.org/showpost.php?p=9150240&postcount=12)

they should fix this pretty quick once it hits the queue and then send the patch upstream.

hopefully should be on time before the next ubuntu version ships, so this can be default (or as an option) for everyone to benefit from

---

### Post by Grenage on 2010-05-19
I'd let the devs know, then change messenger app.

---

### Post by RiceMonster on 2010-05-19
> **philinux said:**
> [http://osdir.com/ml/ubuntu-devel/2010-03/msg00317.html](http://osdir.com/ml/ubuntu-devel/2010-03/msg00317.html)

Delete them here. .local/share/Empathy/logs

That's really a bandaid solution though, because if you wanted to make sure you never stored the conversations, you would have to set up a cron job or something that emptied that directory. As the OP said, there's legal issues involved, so even if they're being deleted it can likely still be an issue that they're still being recorded at all.

I would personally just stick to pidgin.

---

### Post by Linuxforall on 2010-05-19
Gave Empathy a spin again, used it for few days before reverting back to tried and tested Pidgin, Empathy still isn't ready for big league.

---

### Post by philinux on 2010-05-19
> **RiceMonster said:**
> 
I would personally just stick to pidgin.

So would I.

---

