---
title: "WTH is going on with the Software Center?"
date: 2011-04-28
forum: The Cafe
---

### Post by Shmantiv_Radio on 2011-04-28
I try to install Google Chrome, it takes forever to ask for the password, then shows the first part of the install progress bar which then disappears to show the install button again?! 20 minutes later it hasn't installed and USC crashes. This is repeatable and I had to use dpkg in Terminal.
I just tried to install the World of Goo demo and got this.
[IMG]http://i.imgur.com/UUTfm.png[/IMG]
So I pressed ignore and install and USC crashed AGAIN. So I had to use dpkg *again*. 

This is a clean install of 11.04, and everything else works fine. =/

---

### Post by leviathan8 on 2011-04-28
Don't you better install Chromium? :)

---

### Post by Throne777 on 2011-04-28
> **Shmantiv_Radio said:**
> I try to install Google Chrome, it takes forever to ask for the password, then shows the first part of the install progress bar which then disappears to show the install button again?! 20 minutes later it hasn't installed and USC crashes. This is repeatable and I had to use dpkg in Terminal.
I just tried to install the World of Goo demo and got this.
[IMG]http://i.imgur.com/UUTfm.png[/IMG]
So I pressed ignore and install and USC crashed AGAIN. So I had to use dpkg *again*. 

This is a clean install of 11.04, and everything else works fine. =/

Weird. I used the Software Centre about 10 hours ago to install Shotwell & Conky and that all went fine (OK, so it crashed the first time, but after that :p)

---

### Post by speedwell68 on 2011-04-28
I just use Synaptic Package Manager and Gdebi, much simpler in the long run.

---

### Post by Throne777 on 2011-04-28
> **speedwell68 said:**
> I just use Synaptic Package Manager and Gdebi, much simpler in the long run.

I must admit that I probably still do most of my 'program management' via Synaptic rather than the Software Centre.

---

### Post by Shmantiv_Radio on 2011-04-28
> **Throne777 said:**
> Weird. I used the Software Centre about 10 hours ago to install Shotwell & Conky and that all went fine (OK, so it crashed the first time, but after that :p)

But these are downloaded Deb files, not stuff from the repos.

---

### Post by dh04000 on 2011-04-28
1) Install Gdebi
2) In Properties of ANY .deb file, make Gdebi the default application.
3) Profit

---

### Post by Throne777 on 2011-04-28
> **Shmantiv_Radio said:**
> But these are downloaded Deb files, not stuff from the repos.

Oh, my bad.
I don't think I've ever used software centre to deal with .deb packages (come to think of it, I don't think it occurred to me that you could use it for that :p).

---

### Post by Shmantiv_Radio on 2011-04-28
> **dh04000 said:**
> 1) Install Gdebi
2) In Properties of ANY .deb file, make Gdebi the default application.
3) Profit

Oh GDebi is still available? Thanks :D

> **Throne777 said:**
> Oh, my bad.
I don't think I've ever used software centre to deal with .deb packages (come to think of it, I don't think it occurred to me that you could use it for that :p).

USC has taken the place of GDebi now.

---

