---
title: "Chrome OS"
date: 2010-07-18
forum: The Cafe
---

### Post by KdotJ on 2010-07-18
Not sure if this has been asked before (I'm sure it has many times) but I'm looking to try out Chrome OS (or Chromium OS as I believe it's current state is). 
I have looked on the google website and it talks of compilation and building form source. That's fine for me to do, but on the off chance, I was wondering if anyone knows of any ready-to-go images that are up for download?

Many thanks

---

### Post by tjwoosta on 2010-07-18
Never mind, thought I had a link but it was wrong.

---

### Post by TwoEars on 2010-07-18
> **tjwoosta said:**
> [http://getchrome.eu/index.php]("http://getchrome.eu/index.php")

That isn't Chrome OS. That's a replication, using SUSE Studio.

---

### Post by tjwoosta on 2010-07-18
> **TwoEars said:**
> That isn't Chrome OS. That's a replication, using SUSE Studio.

yea just noticed right before seeing your post

---

### Post by Penguin Guy on 2010-07-18
There's a slightly modified version that works [here]("http://chromeos.hexxeh.net/"), as far as I know there are no others. I had a go myself but it took forever to compile and once it did it didn't even boot. Please post back here if you have any success. I've attached some notes I made while compiling incase it'll help.

Good luck ;)

---

### Post by KdotJ on 2010-07-18
> **Penguin Guy said:**
> There's a slightly modified version that works [here]("http://chromeos.hexxeh.net/"), as far as I know there are no others. I had a go myself but it took forever to compile and once it did it didn't even boot. Please post back here if you have any success. I've attached some notes I made while compiling incase it'll help.

Good luck ;)

Thanks Penguin Guy,
I'll give it a shot. You know I'm surprised at google, I know that its still in development but I though they would have some ISO's floating around

---

### Post by lovinglinux on 2010-07-18
Edit: Nevermind, when I saw Chromium I immediately associated with the browser and didn't notice the title of the thread.

---

### Post by chriswyatt on 2010-07-18
You've misunderstood.  Chrome OS is Google's new operating system, hasn't been released yet.

Also, while we're on the subject, when Chrome OS is released will you be able to load it from GRUB?  I'm thinking about dual-booting when Chrome OS is finally released.

---

### Post by cascade9 on 2010-07-18
@ lovinglinux- that is Chrome(browser) not ChromeOS *Edit no problems, fixed ;) 

@ KdotJ- have you seen this page?-

[http://getchrome.eu/download.php](http://getchrome.eu/download.php)

I dont know if it works, is rootkitted, etc, but hopefully that helps.

---

### Post by Legendary_Bibo on 2010-07-18
I once found an iso of Chrome OS that someone made. I remember using it and it booted insanely fast, but I don't remember there being anything special about it. This was a year ago though.

---

### Post by lovinglinux on 2010-07-18
> **cascade9 said:**
> @ lovinglinux- that is Chrome(browser) not ChromeOS

@ KdotJ- have you seen this page?-

[http://getchrome.eu/download.php](http://getchrome.eu/download.php)

I dont know if it works, is rootkitted, etc, but hopefully that helps.

When I saw Chromium in the post I immediately associated with the browser and didn't notice the title of the thread. Already edited my previous message.

---

### Post by TwoEars on 2010-07-18
> **cascade9 said:**
> @ lovinglinux- that is Chrome(browser) not ChromeOS

@ KdotJ- have you seen this page?-

[http://getchrome.eu/download.php](http://getchrome.eu/download.php)

I dont know if it works, is rootkitted, etc, but hopefully that helps.

> **TwoEars said:**
> That isn't Chrome OS. That's a replication, using SUSE Studio.

Oh dear.

OP, to get the best results, you really need to build the whole thing from source.

---

### Post by nw2001 on 2010-07-18
[http://chromeos.hexxeh.net/](http://chromeos.hexxeh.net/) delivered.

---

### Post by Khakilang on 2010-07-19
If it comes out I just run it in Virtual box just to test it out before commit to a computer. Unless I got spare computer to do it. I think I just wait for the final version.

---

### Post by Paqman on 2010-07-19
> **KdotJ said:**
> You know I'm surprised at google, I know that its still in development but I though they would have some ISO's floating around

Presumably they'd prefer not to have generic images floating around that aren't optimised for any particular hardware. Running on a wide variety of machines is (I would imagine) not a design priority for ChromeOS. 

They'll be working with OEMs to target a pretty small subset of hardware. When you look at things like the announcements they've made about printing it seems like they've really chucked a lot of what is on a standard desktop OS out and gone right back to the drawing board.

---

### Post by Legendary_Bibo on 2010-07-19
> **Paqman said:**
> Presumably they'd prefer not to have generic images floating around that aren't optimised for any particular hardware. Running on a wide variety of machines is (I would imagine) not a design priority for ChromeOS. 

They'll be working with OEMs to target a pretty small subset of hardware. When you look at things like the announcements they've made about printing it seems like they've really chucked a lot of what is on a standard desktop OS out and gone right back to the drawing board.

Yeah, lots of web applications. Ooohhh wow so when you're not connected to the internet you can't do anything. Sound logical.

---

### Post by Paqman on 2010-07-19
> **Legendary_Bibo said:**
> Yeah, lots of web applications. Ooohhh wow so when you're not connected to the internet you can't do anything. Sound logical.

You know, I think they've thought of that. Between HTML5 and a built-in 3G connection I think it's a non-issue.

---

### Post by fatality_uk on 2010-07-19
> **Paqman said:**
> You know, I think they've thought of that. Between HTML5 and a built-in 3G connection I think it's a non-issue.

Plus a GoogleGears type thing for offline access to data

---

### Post by Legendary_Bibo on 2010-07-19
> **Paqman said:**
> You know, I think they've thought of that. Between HTML5 and a built-in 3G connection I think it's a non-issue.

Unless they provide the world with free wireless internet then it will be an issue.

---

### Post by Paqman on 2010-07-19
> **fatality_uk said:**
> Plus a GoogleGears type thing for offline access to data

Yep, although I believe Google have wound down development on Gears, as HTML5 apparently includes support for local storage.

> **Legendary_Bibo said:**
> Unless they provide the world with free wireless internet then it will be an issue.

Well, it remains to be seen whether it'll be free, or indeed what pricing model the ChromeOS netbooks will roll out with. I know where I live a lot of mobile operators will currently give you a free netbook with a 3G dongle if you sign up for a contract at a fixed monthly fee (ie: like a mobile phone). I think it's pretty likely the ChromeOS machines will have integrated 3G and be sold in a similar way. Google already has a close relationship with the mobile networks through Android.

Between 3G and wifi it should be pretty hard to find yourself without a connection. I seriously doubt that Google would release a web-based system to market without making absolutely sure you had constant access to viewing Google ads ;)

---

