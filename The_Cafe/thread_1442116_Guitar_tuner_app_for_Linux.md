---
title: "Guitar tuner app for Linux?"
date: 2010-03-29
forum: The Cafe
---

### Post by swoll1980 on 2010-03-29
I use [this]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAgQFjAA&url=http%3A%2F%2Fwww.aptuner.com%2F&ei=8QWxS-aVGoaBlAf2ztWQAQ&usg=AFQjCNG7dKZhct2ABmw_0IM5QipztjmYOg") for Windows, but I can't seem to find anything in the repos that does this. You know of any?

---

### Post by castrojo on 2010-03-29
gtkguitune

---

### Post by swoll1980 on 2010-03-29
> **whiprush said:**
> gtkguitune

Thanks it's not working though. Might be mic settings I don't know.

---

### Post by swoll1980 on 2010-03-29
Would there be a reason my front mic jack wouldn't be working from a software perspective. I know the hardware works. 

edit: Switched to the rear jack logged out then in, and mic works. Still can't figure out how to work it. It's giving me a different reading on the same string every time. sometimes 3 notes away from each other.

---

### Post by steveneddy on 2010-03-30
Here's an online tuner that runs Flash.

[http://www.tunemybass.com/](http://www.tunemybass.com/)

---

### Post by sgosnell on 2010-03-30
[Let me Google that for you](http://lmgtfy.com/?q=guitar+tuner+linux).  The fifth hit down has a discussion of several tuner apps, but all of them might help you.

---

### Post by swoll1980 on 2010-03-30
> **sgosnell said:**
> [Let me Google that for you]("http://lmgtfy.com/?q=guitar+tuner+linux").  The fifth hit down has a discussion of several tuner apps, but all of them might help you.

If you read my op it says I was  looking for something in the repos. I would have to be really, really stupid to go installing random apps off the Internet. That's why I ask for recommendations, so I don't have to do something so insanely stupid.

---

### Post by swoll1980 on 2010-03-30
> **steveneddy said:**
> Here's an online tuner that runs Flash.

[http://www.tunemybass.com/](http://www.tunemybass.com/)

Thanks for some reason I have trouble doing it by ear though. I need one that uses the mic to tell me exactly when it's in tune.

---

### Post by Brandel Valico on 2010-03-30
TuxGuitar has a tuner in it that works fairly well. I still prefer just using the tuner I bought for my Electric Guitar. But just tested the tuner app in Tux Guitar and it was fairly accurate when compared to the tuner I have. The program also has alot of other fun features you may like. It's also in the Repo's which is a huge plus.

The tuner is in the tools tab

Tested gtkGuitune also. It's accurate also. 

Please note I am testing this with an Electric Guitar plugged into the Mic port on the front of my laptop.

Having messed with them. I would still suggest going and buying a decent tuner.

---

### Post by MIJ-VI on 2010-03-30
lingot

It's in the Ubuntu repositories.

---

### Post by swoll1980 on 2010-03-30
> **Brandel Valico said:**
> TuxGuitar has a tuner in it that works fairly well. I still prefer just using the tuner I bought for my Electric Guitar. But just tested the tuner app in Tux Guitar and it was fairly accurate when compared to the tuner I have. The program also has alot of other fun features you may like. It's also in the Repo's which is a huge plus.

The tuner is in the tools tab

Tested gtkGuitune also. It's accurate also. 

Please note I am testing this with an Electric Guitar plugged into the Mic port on the front of my laptop.

Having messed with them. I would still suggest going and buying a decent tuner.

> **MIJ-VI said:**
> lingot

It's in the Ubuntu repositories.

Thanks alot I will try these out.

---

### Post by sgosnell on 2010-03-30
Why are you so terrified of installing something not in the repositories?  Are you afraid your guitar will be out of tune?  There really isn't much danger in running programs not in the repositories, other than having no assurance that they will work perfectly in Ubuntu.

---

### Post by steveneddy on 2010-03-30
More stuff to look at:

[http://sound.condorow.net/guitar.html](http://sound.condorow.net/guitar.html)

---

### Post by swoll1980 on 2010-03-30
> **sgosnell said:**
> Why are you so terrified of installing something not in the repositories?  Are you afraid your guitar will be out of tune?  There really isn't much danger in running programs not in the repositories, other than having no assurance that they will work perfectly in Ubuntu.

Trojan Horses. If you go around the web installing random apps from random places you end up with random things on your machine.

---

### Post by Warpnow on 2010-03-30
> **swoll1980 said:**
> Trojan Horses. If you go around the web installing random apps from random places you end up with random things on your machine.

While theoretically plausible, any reason you consider this a huge threat? I've never heard anything about this ever happening in linux. A common problem in windows, obviously. Even if it did happen the program only runs as root if you run it as root. Can also just compile and run the app...if it does something you don't like kill the pid and rm -rf the folder.

---

### Post by swoll1980 on 2010-03-30
> **Warpnow said:**
> While theoretically plausible, any reason you consider this a huge threat? I've never heard anything about this ever happening in linux. A common problem in windows, obviously. Even if it did happen the program only runs as root if you run it as root. Can also just compile and run the app...if it does something you don't like kill the pid and rm -rf the folder.

If you install a .deb and put your password in, that program can do anything. Linux is no different than any other OS when it comes to the user being the biggest potential  security hole. Further more there is no detection or removal software which would make getting a trojan 10 times worse than it is in Windows.

---

### Post by sgosnell on 2010-03-30
I don't think you understand how package installation works.  When you enter your password to install a .deb file, you're giving it to gdebi, the package installer, not to the .deb file being installed.  The package being installed does not have the password, nor any way to get it until you run it as root.  If you never run it as root, it will never have the sudo password.

---

### Post by swoll1980 on 2010-03-31
> **sgosnell said:**
> I don't think you understand how package installation works.  When you enter your password to install a .deb file, you're giving it to gdebi, the package installer, not to the .deb file being installed.  The package being installed does not have the password, nor any way to get it until you run it as root.  If you never run it as root, it will never have the sudo password.

When you put that password in you're giving the package installer root privileges to unload the payload that's in the deb to wherever the deb specifies and run a installation/configuration script. The pay load could be a guitar tuner or it could be a guitar tuner/bash script that configures my computer to log my key strokes and mail them to some one. I don't think you understand how it works.

---

### Post by sgosnell on 2010-03-31
Well, I suggest you buy a separate guitar tuner and tune your guitar.

---

### Post by swoll1980 on 2010-03-31
> **sgosnell said:**
> Well, I suggest you buy a separate guitar tuner and tune your guitar.

No need Tux Guitar is awesome sauce. and it was in the repos.

---

### Post by swoll1980 on 2010-03-31
Thanks all.

---

### Post by Brandel Valico on 2010-03-31
Glad you found an app that does what you need it to do.

:guitar:

---

### Post by afrodeity on 2012-09-24
I had a tuner installed, that simply played a note for each string, and you tuned by ear. Can't remember what it was called, kguitar or something?

---

### Post by Elfy on 2012-09-24
Old thread closed.

---

