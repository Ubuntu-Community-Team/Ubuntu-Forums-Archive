---
title: "Spectre V2 mitigation: LFENCE not serializing. Switching to generic retpoline"
date: 2018-03-04
forum: Security
---

### Post by missmoondog on 2018-03-04
i get the message in subject line when booting my old amd atlon xp 3000+ lubuntu 16.04.01 machine. what does it mean and is there any way to fix it or at least make it so it doesn't show up?

doesn't have any effect on how machine runs but takes a few seconds longer to boot than normal. i know the machine is on it's last leg as the only browser i can use is palemoon without the sse instruction set.

i've done some searches and found some info about it, but it's so confusing i wouldn't know where to start and not sure what they're talking about is even something that can be done myself.

thank you

---

### Post by corradoventu on 2018-03-05
Lubuntu should be at level 16.04.4 [http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/) did not you update?

---

### Post by missmoondog on 2018-03-05
my install is from the first release. dumb question, but are you supposed to install all new releases like that? otherwise, been getting all the updates through synaptic as they get released.

---

### Post by deadflowr on 2018-03-17
> **missmoondog said:**
> my install is from the first release. dumb question, but are you supposed to install all new releases like that? otherwise, been getting all the updates through synaptic as they get released.

Just by updating you'll move up to 16.04.4.
No need to re-download and reinstall a fresh version.
Doing normal updates is suffice.
The 16.0.4 designation means you have all packages fully up-to-date.

For what it's worth:
Installing 16.04.1 will keep you with the original 4.4 kernel series.
Newer point releases use a moving hardware stack, so an update from, let's say, 16.04.3 will move you up from the 4.10 kernel to the 4.13 kernel.
Since the 4.4 kernel gets the same security support that 4.13 has been getting, there is really no need to update the stacks.
(the only real reason to update the hardware stack is if you find out that there is a fix within the

A basic rundown of what is what can be found here:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

---

### Post by missmoondog on 2018-03-19
thank you, deadflowr

does anyone think this error is simply due to it being an ancient machine that has an athlon xp processor? i also have another ancient machine with an amd sempron processor that does not get that error though.

---

### Post by milkymoo on 2018-03-21
> **missmoondog said:**
> thank you, deadflowr

does anyone think this error is simply due to it being an ancient machine that has an athlon xp processor? i also have another ancient machine with an amd sempron processor that does not get that error though.

I'm getting the same error on my virtualbox machine, but i can't get it to boot.
also running 17.10
[https://ubuntuforums.org/showthread.php?t=2387319](https://ubuntuforums.org/showthread.php?t=2387319)

---

### Post by harveyp2 on 2018-11-02
I have exactly the same messages in my kern.log. I have automatic updating for 18.04. What do I need to do different to get rid of these messages ?

    nov. 01 12:30:27 harvey-System kernel: Spectre V2 : Spectre mitigation: LFENCE not serializing, switching to generic retpoline
    nov. 01 12:30:27 harvey-System kernel: Spectre V2 : Mitigation: Full generic retpoline
    nov. 01 12:30:27 harvey-System kernel: Spectre V2 : Spectre v2 / SpectreRSB mitigation: Filling RSB on context switch

---

### Post by oldos2er on 2018-11-02
@harveyp2, please start your own thread, it's likely no one will look in an older "Solved" thread for new questions.

---

