---
title: "hard drive spy ware"
date: 2015-02-25
forum: Ubuntu, Linux and OS Chat
---

### Post by ronbrooks on 2015-02-25
[http://www.businessinsider.com/r-russian-researchers-expose-breakthrough-us-spying-program-2015-2](http://www.businessinsider.com/r-russian-researchers-expose-breakthrough-us-spying-program-2015-2)

Found thid artical on line today and was woundering if this would effect Ubuntu systems. If so how would we be able to detect it on our hard drive.

---

### Post by QIII on 2015-02-25
As people respond to this, please everyone remember that if it becomes political the thread will be closed.

Thanks.

---

### Post by lukeiamyourfather on 2015-02-25
Likely the only people who could detect such modifications to drive firmware are the developers of the original firmware for the drives in question. Beyond that something like a utility from drive manufacturers could detect if the firmware is original or not but it might be a while before that happens (if ever). Unless you've been looking at jihadist websites or doing other nefarious things you probably don't have anything to worry about because the article is saying the firmware is modified by malware the NSA developed and distributed through very specific channels, it's not like the drives come from the factory this way. Or at least that's I how read it.

---

### Post by Bucky Ball on 2015-02-25
*Thread moved to **Ubuntu, Linux and OS Chat**.*

And seconding QIII.

---

### Post by ronbrooks on 2015-02-25
I was just worndering about it since I got some new hard drives and didn't know what this was all about.  Thanks for clearing it up.

---

### Post by grahammechanical on 2015-02-25
Getting a copy of the firmware code is one thing but how do you get a modified firmware code onto, or is that into, a particular hard drive on a particular computer? Perhaps they brought a batch of hard drives, modified the firmware and then sent the hard drives as a free gift to their intended victims.

If these people are so smart, then why did they not have these hard drives in the machines of Bradly Whatsit and Edward Thingy? Could have saved themselves a lot of bad publicity.

---

### Post by cmsideas2 on 2015-02-26
> **grahammechanical said:**
> Getting a copy of the firmware code is one thing but how do you get a modified firmware code onto, or is that into, a particular hard drive on a particular computer? Perhaps they brought a batch of hard drives, modified the firmware and then sent the hard drives as a free gift to their intended victims.

If these people are so smart, then why did they not have these hard drives in the machines of Bradly Whatsit and Edward Thingy? Could have saved themselves a lot of bad publicity.
I agree with you

---

### Post by PondPuppy on 2015-02-26
Probably the best general-audience article I've seen on the subject is the one on Wired: [http://www.wired.com/2015/02/nsa-firmware-hacking/](http://www.wired.com/2015/02/nsa-firmware-hacking/)

It appears that the firmware which operates the target hard drive can be flashed by another trojan (EquationDrug or Grayfish). I think that's right. So if the perpetrators can get a trojan onto the target system, then it installs the drive firmware modifications. That can't be dislodged even by reformatting the drive.

But the module of EquationDrug and Grayfish which flashed the hard drive is named "[COLOR=#333333][FONT=Exchange SSm 4r]nls_933w.dll" -- [/FONT][/COLOR]a Windows dynamic link library. I think that may mean that it would not work on a Linux system. (But if a pre-infected drive were used on a Linux system, I think the modified firmware may still run.)

Once the modified firmware is in place it uses the hard drive's controller as a mini-OS, independent of the main OS. The hard drive controller boots before the rest of the main operating system, so it can 'watch-and-record' as the user enters things like disk encryption passwords. And it can talk to its command server, if the computer has an Internet connection.

According to the article, those who discovered the hack found very, VERY few machines with the hacked drive firmware. I suspect a Linux machine used by an anonymous westerner would be more likely to be hit by a meteorite than to host this particular virus. 

I could be quite wrong.

---

### Post by sffvba[e0rt on 2015-02-27
If hacking starts to happen on the "hardware" level then software solutions become moot.

---

