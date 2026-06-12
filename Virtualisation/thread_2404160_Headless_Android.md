---
title: "Headless Android"
date: 2018-10-20
forum: Virtualisation
---

### Post by nobitakun on 2018-10-20
I have maybe a quite uncommon problem: I need a way to run many headless android emulators on a computer at once. As many I mean 70-80 at least.

I will explain what I want to accomplish. The company I work for uses Whatsapp for chatting with customers, but every worker is currently using an emulator on the computer because we use virtual numbers, and we want to remove the necessity of having them in favour of a centralized solution. So, what I want is to have a solely powerful computer running all of them at once, in a headless way without any other purpose that keeping the whatsapp on, to tell the service that actually there is a phone running it, unless there is a software that emulates whatsapp service only.

The plan I came with is to install first whatsapp, activate it with a number then use a virtual camera software to activate each whatsapp web in every computer browser, so they can use whatsapp only by opening the browser without caring at all about the emulator running in the said computer. Of course, I would be making a backup of their browser profile in case someone clears the cache and whatsapp web asks for validation again, I've tried that before and works without issues.

Whatsapp is a huge piece of crap as for business tasks, and they don't seem to be working in a solution other than a ****** business app that does not solve one of the most annoying things: having a phone to use it. They should make a way to random generate a virtual number that never is going to exist per se, only for this purpose, and link a email address to it for validating purposes. In other words, making it a complete non-phone dependent.

Thanks for your help! :)

---

### Post by ramennoodles20 on 2019-05-01
Hey nobitakun, 

I'm not sure that what you want to do is perfectly legal (at least according to whatsapp) but have you taken a look at yowsup it's a great open source projecct that let's you connect to whatsapp's api with out needing to run any emulators. I you do need to use emulated phones for whatever reason I don't see why you couldn't use some sort of docker solution to run multiple instances of android and install whatsapp on them, but these emulators typically take up about 256 - 512 mb of RAM so at the very best you would probably need to have a computer equiped with over 160GB of RAM which definitely won't come cheap. 

Cheers and I hope to hear about your solution!

---

