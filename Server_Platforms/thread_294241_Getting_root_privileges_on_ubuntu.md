---
title: "Getting root privileges on ubuntu"
date: 2006-11-06
forum: Server Platforms
---

### Post by Godomega on 2006-11-06
Normally, during boot-time, It allways takes loads of 
time running dosfsck. 
One time I was inpatient an I decided to skip the 
test using the CTRL + C key combination.
I was expecting that It would give me a Failed mark 
on the "system test", and continue with booting. 
Or it would jump to console and ask for my username 
and password due to startup failure.
But I wasn't expecting that it would Jump into a shell 
while printing out "Filesystem check failed. 
Please repair manually" and give me [B][U]full root 
privileges[/U][/B].
I am shocked that it is that easy for 
other users to log into my computer with 
full root privileges that easy.:-|

---

### Post by Klaidas on 2006-11-06
Try booting in recovery mode... :-D
Ok, anyway, before you get those answers about your computer being insecure if anyone has access to it, I jhust suggest you setting a root password ;)

---

### Post by mvaniersel on 2006-11-06
Physical access to the machine == root access. This is impossible to prevent.

Any dude with a live CD or live USB stick can gain root access to any box if he has the chance of sitting behind it undisturbed for five minutes. Even if you set the BIOS not to boot from CD and protect it with a  password, it only takes a screwdriver and a quick look inside the machine to reset it.

What you need to worry about is root access by remote users, accross the internet.

---

### Post by Klaidas on 2006-11-06
I think it's pretty much like doors... They can be broken, but it doesn't mean there is no need of having them ;)
So again, my suggestion is to set up a root password

---

