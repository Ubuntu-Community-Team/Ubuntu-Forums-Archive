---
title: "Why are linux versions of apps sometimes bigger in filesize than other OS's?"
date: 2012-04-23
forum: The Cafe
---

### Post by user1397 on 2012-04-23
For example, looking at the [chromium web browser wikipedia page]("http://en.wikipedia.org/wiki/Chromium_(web_browser)"), you can see the the file sizes for linux 32-bit and 64-bit, mac os x, windows, and android.  The linux ones are clearly bigger.

I see this all the time, is there a simple answer?  Am I missing something?

---

### Post by Primefalcon on 2012-04-23
> **ubuntuman001 said:**
> For example, looking at the [chromium web browser wikipedia page]("http://en.wikipedia.org/wiki/Chromium_(web_browser)"), you can see the the file sizes for linux 32-bit and 64-bit, mac os x, windows, and android.  The linux ones are clearly bigger.

I see this all the time, is there a simple answer?  Am I missing something?
I'd say the companies not optimizing for Linux..... but that'd be a guess

---

### Post by zombifier25 on 2012-04-23
Actually, most apps I saw has the biggest filesize on the Mac version.

---

### Post by haqking on 2012-04-23
different code, different dependencies ad nauseum ad infinitum

---

### Post by forrestcupp on 2012-04-23
Windows versions use the winAPI, which doesn't have to be installed. Same idea for Mac. In Linux, you can't assume any GUI toolkit is already installed. Things you get from the repos don't have to include dependencies because APT works all of that out. But standalone things for Linux usually either include dependencies, or they work everything out from scratch in the code.

---

### Post by snowpine on 2012-04-23
Irrelevant unless you are running extremely low on disk space (but hard drives are cheap).

---

### Post by Eddie Wilson on 2012-04-23
> **forrestcupp said:**
> Windows versions use the winAPI, which doesn't have to be installed. Same idea for Mac. In Linux, you can't assume any GUI toolkit is already installed. Things you get from the repos don't have to include dependencies because APT works all of that out. But standalone things for Linux usually either include dependencies, or they work everything out from scratch in the code.

That's exactly correct. How digga know that? ;)

---

### Post by Majorix on 2012-04-23
> **forrestcupp said:**
> windows versions use the winapi, which doesn't have to be installed. Same idea for mac. In linux, you can't assume any gui toolkit is already installed. Things you get from the repos don't have to include dependencies because apt works all of that out. But standalone things for linux usually either include dependencies, or they work everything out from scratch in the code.

+1

---

