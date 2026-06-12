---
title: "somebody hacked my Ubuntu ??"
date: 2008-05-17
forum: Security
---

### Post by hangnguyen on 2008-05-17
Hello

Sometime my firefox browser suddenly turned off, sometime I can not click on any buttons, can not Shut down the Ubuntu ...ect 

I worry that my ubuntu was hacked ???

How can I check ?

thanks

HN

---

### Post by Cew27 on 2008-05-17
it wasnt hacked it is an instability with flash player i think

---

### Post by the8thstar on 2008-05-17
I've had this issue happen several times too. I'm interested to know what causes it. I use FF3 Beta in HH.

---

### Post by hangnguyen on 2008-05-17
thanks for replys 

I scan my Ubuntu with rkhunter yesterday and got two warnings :

Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

what does it mean ???

Thanks

HN

---

### Post by Thirtysixway on 2008-05-17
This has happened to me before, perhaps it's flash causing it.  It's not a hacker or virus, don't worry.

---

### Post by the8thstar on 2008-05-18
> **hangnguyen said:**
> thanks for replys 

I scan my Ubuntu with rkhunter yesterday and got two warnings :

Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

what does it mean ???

Thanks

HN

There can be false positives. AFAIK, finding trojans, worms and all these nasty beasts is not exact science.

A word of advice though: rkhunter needs to be updated with the latest definitions in order to do a good job. This takes care of a good amount of false positives. In the terminal, enter the command:

> rkhunter --help

In the option list, there is an option for updating definitions. Run it first, then run rkhunter again by itself to scan the system.

---

