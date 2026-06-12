---
title: "Hacking through public folder!?"
date: 2011-05-30
forum: Security
---

### Post by CoffeeRain on 2011-05-30
So, I have a public folder that I use for transferring files from machine to machine, and I was wondering if I was at a coffee shop, could someone run a script on my computer even though I do not have SSH enabled? Is there something a person could do through my public folder even though they do not have access to my other files? What could I do to stop this from happening? Or am I just completely paranoid and there is absolutely nothing that someone could do. I don't want to chmod it, because I need my friends to be able to get in there and be able to read and place files. Thanks.

---

### Post by tgm4883 on 2011-05-30
> **CoffeeRain said:**
> So, I have a public folder that I use for transferring files from machine to machine, and I was wondering if I was at a coffee shop, could someone run a script on my computer even though I do not have SSH enabled? Is there something a person could do through my public folder even though they do not have access to my other files? What could I do to stop this from happening? Or am I just completely paranoid and there is absolutely nothing that someone could do. I don't want to chmod it, because I need my friends to be able to get in there and be able to read and place files. Thanks.

I don't see how they could run files. If you allow writing access that is one thing, but executing access is completely different.

---

### Post by Lars Noodén on 2011-05-31
How are you connecting to the public folder, if not through SSH?
The method will tell you whether it is secure or not.

---

### Post by CoffeeRain on 2011-05-31
I have a mac, so it shows up on other people's computers and if they had my username and password, they could see all my files, but anyone can see and write to this folder.

---

### Post by Lars Noodén on 2011-05-31
> **CoffeeRain said:**
> ... but anyone can see and write to this folder.

Even without having to log in?  You should at least require a login name and password to write to the folder.

---

