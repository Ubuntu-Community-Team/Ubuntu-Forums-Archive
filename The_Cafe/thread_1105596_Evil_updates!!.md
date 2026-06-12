---
title: "Evil updates!!"
date: 2009-03-24
forum: The Cafe
---

### Post by t0p on 2009-03-24
What is there to prevent a software developer releasing a malicious update to Ubuntu users?

---

### Post by Skripka on 2009-03-24
> **t0p said:**
> What is there to prevent a software developer releasing a malicious update to Ubuntu users?

Nada.  Sleep tight.

---

### Post by MaxIBoy on 2009-03-24
This is the official rationale for why Hardy will be stuck with a release-candidate version of Mesa3D for all eternity, even though there have been three stable releases since then.

The policy is detailed here: 
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
[https://wiki.ubuntu.com/FreezeExceptionProcess](https://wiki.ubuntu.com/FreezeExceptionProcess)
[https://wiki.ubuntu.com/SyncRequestProcess](https://wiki.ubuntu.com/SyncRequestProcess)

---

### Post by Moustacha on 2009-03-24
Peer review

---

### Post by cariboo on 2009-03-25
Each package submission by someone who is not a member of the development team must be sponsored by a developer.

Jim

---

### Post by Rokurosv on 2009-03-25
Hmmm, how about a rogue PPA?

---

### Post by Polygon on 2009-03-25
> **t0p said:**
> What is there to prevent a software developer releasing a malicious update to Ubuntu users?

these.

[img]http://img242.imageshack.us/img242/9017/screenshot016.png[/img]

each package that comes through the main ubuntu repos are signed by a key, and the way pgp works is that only the ubuntu developers have access to the private key, so only they can sign it.

also, ppa's use pgp keys on launchpad now, but they arn't enforced...it just yells at you that they are not authenticated

---

### Post by namegame on 2009-03-25
> **Polygon said:**
> these.

each package that comes through the main ubuntu repos are signed by a key, and the way pgp works is that only the ubuntu developers have access to the private key, so only they can sign it.

also, ppa's use pgp keys on launchpad now, but they arn't enforced...it just yells at you that they are not authenticated

Exactly, in the end security is the responsibility of the end user. If you don't know what you are installing, don't do it. If you don't know where your package came from, don't install it.

Then there are those of us who install extremely bleeding edge software because we want to. If we get something malicious/bad we usually are prepared to deal with it, but that's another story.

---

### Post by t0p on 2009-03-25
> **namegame said:**
> Exactly, in the end security is the responsibility of the end user. If you don't know what you are installing, don't do it. If you don't know where your package came from, don't install it.

Then there are those of us who install extremely bleeding edge software because we want to. If we get something malicious/bad we usually are prepared to deal with it, but that's another story.

I agree the user must be aware of what he's installing.  But when a big bunch of updates comes along, not everyone meticulously examines each one.

I don't think our updates are going to turn against us.  I'm just curious what kind of safeguards exist to protect us from a malicious update.

---

### Post by 3rdalbum on 2009-03-25
If you have a third-party repository in your software sources, then the same security feature will protect you as the one that prevents Windows users from downloading and running "MEGAN_FOX_NUDE!!!.jpg.exe".

---

### Post by 23meg on 2009-03-29
> **MaxIBoy said:**
> This is the official rationale for why Hardy will be stuck with a release-candidate version of Mesa3D for all eternity, even though there have been three stable releases since then.

The policy is detailed here: 
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
[https://wiki.ubuntu.com/FreezeExceptionProcess](https://wiki.ubuntu.com/FreezeExceptionProcess)
[https://wiki.ubuntu.com/SyncRequestProcess](https://wiki.ubuntu.com/SyncRequestProcess)

Malicious software ending up on official Ubuntu updates would be an extremely unlikely happening, and none of the policy documents you've cited point to that as the official rationale for not updating a certain package in a stable release.

---

### Post by cmay on 2009-03-29
i read that there has been few incidents where security could have been compromised in the past. 

once a cracker had been able to implant a one line kernel patch that would have been able to give him access to all of the debian computers taking this kernel from the kernel.org. that was discovered same day and the security hole was closed and people was informed that it had happen.

 the other incident i read about is a program where two developers one of them being the author of a progam where argueing about personal things mixed wiht the maintenance of the package. the author in the end decided to make a obfuscated piece of code that would prevent the program from been run on debian systems and call the ohter developer names if tried to run on a debian system. that too was discoved within few hours and the package was removed from the respotories after that. 

it is not that no one tries to use the packages to do malicius things out of different reasons but i think from what i read that the peer review system works and i never fear any packages from the official debian or ubuntu respotories. i do not like to use the restricted drivers and so on exactly because the sources are closed so i only use them if i really have to.

---

### Post by myusername on 2009-03-29
Oh ye of little faith. everyone knows that we are protected by the scottish mofia. never heard of them? its cause they're THAT good.

---

