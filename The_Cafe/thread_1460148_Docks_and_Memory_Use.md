---
title: "Docks and Memory Use"
date: 2010-04-22
forum: The Cafe
---

### Post by Frogs Hair on 2010-04-22
Hi,
My to biggest memory hogs besides Xorg, are Pulse Audio and Cairo Dock . From what I've
read so far, AWN is a bigger memory hog than Cairo Dock. Does anyone have any data on  Docky and its memory use ? 
 
The Cairo Dock system monitor lists the top three memory users , but I don't know if Docky
does the same.

---

### Post by Simian Man on 2010-04-22
Are you actually running out of memory?

---

### Post by Frogs Hair on 2010-04-22
> **Simian Man said:**
> Are you actually running out of memory?

No, Cairo is a 16mb program but it's using about 40mb while running a dock with 10 launchers .

---

### Post by tkblackbelt on 2010-04-22
40 mb isn't that big of a deal

---

### Post by Simian Man on 2010-04-22
> **chuckbenger said:**
> 40 mb isn't that big of a deal

Exactly.

If you like Cairo-dock, why would you consider getting rid of it just because it's using a few megabytes that would otherwise go unused?

---

### Post by Frogs Hair on 2010-04-22
> **Simian Man said:**
> Exactly.

If you like Cairo-dock, why would you consider getting rid of it just because it's using a few megabytes that would otherwise go unused?

Good question ,   Cairo works well for me , but Docky is newer and I was wondering about its resource use in comparison to Cairo.

---

### Post by RaZe42 on 2010-04-22
> **Simian Man said:**
> Exactly.

If you like Cairo-dock, why would you consider getting rid of it just because it's using a few megabytes that would otherwise go unused?

That mentality is the reason why software becomes bloated.

---

### Post by chriskin on 2010-04-22
> **RaZe42 said:**
> That mentality is the reason why software becomes bloated.

40 megabytes of ram doesn't show a bloated application

the mentality to make everything ubersuperduperlightweight by removing features, that's what makes software useless

---

### Post by BrokenKingpin on 2010-04-22
> **RaZe42 said:**
> That mentality is the reason why software becomes bloated.
Agreed. I have always hated how some people think just because you have 4GB of ram that software can be poorly written and use more RAM than it really needs to. You ever notice that computer hardware gets faster, but software gets slower... so as time goes on your overall computer experience performs the same as it did 10 years ago on crap hardware.

> **chriskin said:**
> 40 megabytes of ram doesn't show a bloated application

the mentality to make everything ubersuperduperlightweight by removing features, that's what makes software useless
Just because it is lightweight doesn't mean it doesn't have features. 

This all being said I haven't used the dock in question... so 40MB of RAM could be completely reasonable for what it does.

---

### Post by chriskin on 2010-04-22
i didn't say that, read what i said once more :)


if they had to make the dock even more lightweight, they would have to remove something , no?

---

### Post by zekopeko on 2010-04-22
> **Frogs Hair said:**
> Hi,
My to biggest memory hogs besides Xorg, are Pulse Audio and Cairo Dock . From what I've
read so far, AWN is a bigger memory hog than Cairo Dock. Does anyone have any data on  Docky and its memory use ? 
 
The Cairo Dock system monitor lists the top three memory users , but I don't know if Docky
does the same.

Docky is sitting now at 45.7 MB of ram. 12 launchers and 6 docklets + 4 helper scripts.

EDIT: Forgot to add that I have another Docky with 12 launchers on the side of the screen.

---

### Post by BrokenKingpin on 2010-04-22
> **chriskin said:**
> 
if they had to make the dock even more lightweight, they would have to remove something , no?
Yeah, but not features necessarily. They could write the same features, with more efficient code... resulting in a lighter application.

It is true that more features probably results in an application using more memory, which is fine. The problem is developers writing applications with inefficient code due to sloppiness, and the attitude that it doesn't matter because everyone has 4GB of RAM these days.

---

### Post by chriskin on 2010-04-22
> **BrokenKingpin said:**
> Yeah, but not features necessarily. They could write the same features, with more efficient code... resulting in a lighter application.

it seems that my point fails to reach you, probably something i said wrong 

what i said was that there is a limit of how lightweight something can be without sacrifices. 
better code can make it lighter but not THAT much lighter. better code can make it use 35 instead of 40 mbs of ram, there is no way one can make a real dock with all the effects this one has with 1mb ram usage.
------------

what i said above is that there is a tendency to make software too lightweight these days , sometimes so lightweight that "non-essential" features are sacrificed in the name of simplicity.

---

### Post by BrokenKingpin on 2010-04-22
> **chriskin said:**
> it seems that my point fails to reach you, probably something i said wrong 

what i said was that there is a limit of how lightweight something can be without sacrifices. 
better code can make it lighter but not THAT much lighter. better code can make it use 35 instead of 40 mbs of ram, there is no way one can make a real dock with all the effects this one has with 1mb ram usage.

My comments were directed towards applications in general. I wasn't saying you can get the dock down to 1MB, in fact I said in my early post that this probably wasn't even the case for this dock.
In terms in decreasing RAM usage on applications, it really depends on the application. I work at a company that makes software that uses about 150MB when running, and we have done fixes in code that have dropped the usage by 10s of MB.



> **chriskin said:**
> 
what i said above is that there is a tendency to make software too lightweight these days , sometimes so lightweight that "non-essential" features are sacrificed in the name of simplicity.
I would disagree, a lot of software these days is bloated and is not trying to be lightweight at all. There are developers out there that do focus on making lightweight software though (XFCE, LXDE, etc.).

---

### Post by Simian Man on 2010-04-22
Of course it's true that, in general, programmers should be concerned with the memory usage of their applications.  In practice, however, you always have a choice between working on new features, fixing bugs, or optimizing what's already there.  For the vast majority of projects making it work, and work well is going to be way more important most of the time.

For most applications adding new features and fixing bugs is more important than spending hours and hours of work to reduce the memory consumption of a program by a few megabytes.  If that means that you can't use a given application (or just want to impress people with your *free -m* output), then you can either work on improving performance yourself orfind an alternative that uses less memory.  And no matter what you say, in practice I can bet you that that alternative will also have fewer features more often than not.

This attitude of thinking that developers are being lazy by not focusing as much on optimization is bull.

---

### Post by Frogs Hair on 2010-05-02
> **zekopeko said:**
> Docky is sitting now at 45.7 MB of ram. 12 launchers and 6 docklets + 4 helper scripts.

EDIT: Forgot to add that I have another Docky with 12 launchers on the side of the screen.

Thanks, thats what i was looking for, some data !

---

