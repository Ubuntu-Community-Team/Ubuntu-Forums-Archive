---
title: "New Hardy install with full encryption?"
date: 2009-11-15
forum: Security
---

### Post by phryangle on 2009-11-15
Hi Everybody,

I've been reading non stop the last few days searching everywhere for answers and what I'm trying to do is to make a clean encrypted install of Hardy from the alternative cd. I want everything to be encrypted as much as possible, and I do realize there are sacrifices of convenience/performance in the name of paranoia/security. Anyway, from the links below I have created a list of steps that can be taken to encrypt a freshly installed ubuntu OS (to the best of my knowledge). Can anybody verify/add to the list and suggest improvements? 

Context: I am a total n00b and I am doing this on a laptop.

1. Use DBAN and securely wipe the HDD. [COLOR=Blue][Here]("http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html")[/COLOR] and [COLOR=Blue][Here]("http://www.dban.org/")[/COLOR].
2. Get the alternative install disc for Hardy and set up. [COLOR=Blue][Here]("http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml")[/COLOR]. 
3. Install TrueCrypt and set up for the full system once logged into Hardy. [COLOR=Blue][Here]("http://www.truecrypt.org/docs/")[/COLOR].
4. Set up BIOS passwords. Apparently not that strong, but better than nothing. Thoughts?

I know it seems overly simplified, but I need to boil it down so it makes sense in terms of action steps so I can do something. Thanks for any input.

---

### Post by cariboo on 2009-11-16
If someone has physcal access to your computer, the only thing you can do is encrypt your data, which you have done. The only thing I can suggest is to use a good strong pass-phrase, one that is not easily guessed.

---

### Post by FuturePilot on 2009-11-16
You shouldn't need TrueCrypt if you're setting up the system with the Encrypted LVM option in the alternate installer. Everything else seems OK though.

---

### Post by phryangle on 2009-11-16
Thanks for the quick replies!:p

---

