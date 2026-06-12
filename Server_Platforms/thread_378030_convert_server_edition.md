---
title: "convert server edition"
date: 2007-03-06
forum: Server Platforms
---

### Post by jrock2004 on 2007-03-06
Is there a way to install ubuntu server and not use it as a server? See I have regular version of ubuntu but it does not detect NIC. The server edition does. So is it possible and would it be tuff?

---

### Post by magicfab on 2007-03-06
I don't see why one version would detect your NIC and not the other, but yes. Install your server version and just install the desktop you want, eg. sudo apt-get install ubuntu-desktop

---

### Post by Mr. C. on 2007-03-07
> **jrock2004 said:**
> Is there a way to install ubuntu server and not use it as a server? See I have regular version of ubuntu but it does not detect NIC. The server edition does. So is it possible and would it be tuff?

Of course.  Just disable the services you do not want to use.

Would it be tough?  Thats like asking your friend if you should wear a sweater.  Depends on you and your skills.

---

### Post by Brazen on 2007-03-07
I also don't see how one version would detect your NIC and not the other considering the drivers are built into the kernel used by both.  Have you tried the desktop "alternate install" CD?

---

### Post by jrock2004 on 2007-03-07
I dont know either. It is weird. I boot to live CD and nothing. now the cd I have is 6.06. could this be why?

---

### Post by Mr. C. on 2007-03-07
We can play the guessing game from now until the cows come home... at this rate, a solution will never be found.

You asked if you could install the server addition.  Answer: Yes.

You asked if it would be tough.  Answer: we can't answer that for you.  Try it.

If you want to diagnose why your card isn't being detected, your going to have to show some info about the card itself.  What's the mfg, card ID, etc.

lshw -class network
lspci

Without data, this thread will go no where.
MrC

---

### Post by jrock2004 on 2007-03-07
It is a intel board. according to the server edition I have installed it says driver is e1000

so I believe that would be my driver

PC is dell dimension E520

---

### Post by Mr. C. on 2007-03-07
I gave you the commands to execute.  I need data instead of your interpretation and guesses.

Sorry,
MrC

---

