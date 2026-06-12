---
title: "Looking for a bare bones linux distro"
date: 2007-05-13
forum: The Cafe
---

### Post by GTyron on 2007-05-13
I;m looking for a bare bones distribution that has no GUI, and no user accounts. It doesn't necessarily have to have extremely low system requirements, i just don't need those things getting in my way in this project. Does anyone know of something that fits that description? If so thanks.

---

### Post by heimo on 2007-05-13
> **GTyron said:**
> I;m looking for a bare bones distribution that has no GUI, and no user accounts. It doesn't necessarily have to have extremely low system requirements, i just don't need those things getting in my way in this project. Does anyone know of something that fits that description? If so thanks.

It's possible that if you can describe your need more specifically, someone can recommend a distribution. But with this information, my suggestion is LFS:
[http://www.linuxfromscratch.org/lfs/](http://www.linuxfromscratch.org/lfs/)

---

### Post by aysiu on 2007-05-13
Is it possible for a Linux distro not to have user accounts? Surely there must at least be a root user, right?

---

### Post by heimo on 2007-05-13
> **aysiu said:**
> Is it possible for a Linux distro not to have user accounts? Surely there must at least be a root user, right?

I could imagine that embedded operating system could have no actual user accounts. But I'm not an expert.

---

### Post by slimdog360 on 2007-05-13
arch is great, but if you were looking for something easy download the ubuntu server cd. It Ubuntu minus everything.

---

### Post by bonzodog on 2007-05-13
Yeah, Arch base install will give you *just* a CLI and enough libs and the base bin files for an operative system. 

Also Zenwalk Core does this.

Ubuntu server is also a fairly minimal install, no X, but it comes with a few other items that they think might be useful.

---

### Post by GTyron on 2007-05-13
thanks, i'll look into all of your recommendations

---

### Post by happy-and-lost on 2007-05-13
Debian minimal/netinstall?

---

### Post by ArtificialSynapse on 2007-05-13
Just out of curiosity, what's the project??

---

### Post by Rhox on 2007-05-13
> **heimo said:**
> I could imagine that embedded operating system could have no actual user accounts.

That's correct. You technically don't need to have user accounts.

---

### Post by GTyron on 2007-05-13
> **ArtificialSynapse said:**
> Just out of curiosity, what's the project??

It's mostly just out of me wanting to do it rather than anything useful. I'm wanting to basically make an old computer into a big remote controlled mp3 player. it would be a hassle to have to login every time i turned it on seeing as it will have no i/o devices. I'm planning on it communicating with a hand held device such as a pda or something through bluetooth using that as a remote control and song display for it. Things are looking promising as far as the media player itself goes, but the control scheme may not work out, i don't know i've never designed anything for portable devices before.

---

### Post by ArtificialSynapse on 2007-05-13
That's neat, this thread made me decide that I'm going to start working on my home automation project with a scratch install. 

It will use voice recognition, motion sensors, temperature sensors, and much more.

It will provide dim lighting and soft ambient music for the night time, it'll know where you are, and change climate for you, play music and movies, provide news and weather information, all at the sound of your voice / your very existence.

---

### Post by macogw on 2007-05-13
Slackware?

---

### Post by Rhox on 2007-05-13
> **ArtificialSynapse said:**
> That's neat, this thread made me decide that I'm going to start working on my home automation project with a scratch install. 

It will use voice recognition, motion sensors, temperature sensors, and much more.

It will provide dim lighting and soft ambient music for the night time, it'll know where you are, and change climate for you, play music and movies, provide news and weather information, all at the sound of your voice / your very existence.

That sounds pretty expensive.

---

### Post by ArtificialSynapse on 2007-05-14
nah, I don't think so, I just need to buy X10 modules, although I've heard bad things about that. 

but x10 basically uses electrical lines in your house as a data line for sending signals to electrical devices that are plugged into them.

---

### Post by sedition on 2007-06-11
Roger that. Sounds like the project I'm working on now. I highly recommend the Firecracker interface  (as long as you have a working serial port) and the BottleRocket package via the Ubuntu server (text only) install. You can buy additional X10 units and scatter them throughout your home. I just turn on and log in via SSH (you can also setup automatic login for users as well). Still working on the voice recognition issue, had a little bit o' luck via Perlbox on FreeBSD a while back, but it's giving me issues on Ubuntu.

---

### Post by LaRoza on 2007-06-11
uL
Puppy-barebone
slax-frodo

---

### Post by PhatStreet on 2007-06-11
Arch is great, very stable too.

---

