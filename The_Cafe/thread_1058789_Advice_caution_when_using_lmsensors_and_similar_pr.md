---
title: "Advice caution when using lmsensors and similar *probing* software or modules ."
date: 2009-02-03
forum: The Cafe
---

### Post by rajeev1204 on 2009-02-03
hi.

A long while ago i had posted a thread asking if software can damage hardware beyond repair.Most replied in the negative.

Well,especially when using software which *probes* for temperature and similar.it gives me the creeps.

I would say users exercise caution when recommending installation of such software to users on these forums,I was about to install lmsensors but now have permanently decided against it.

Look what lmsensors did to a phenom cpu .(fixed later with a patch)

[http://www.lm-sensors.org/wiki/Configurations/Sapphire/AM2RD790](http://www.lm-sensors.org/wiki/Configurations/Sapphire/AM2RD790)




Pretty scary.



regards

rajeev.

---

### Post by JillSwift on 2009-02-03
Kind of a FUDish way of putting it, isnt' that?

***One*** dead CPU out of thousands of installations, and the problem's been identified and handled. Kudos to the lm-sensors team for hopping on it like that.

---

### Post by Polygon on 2009-02-03
yeah really. ive ran it countless times on my old computer, and ran it again when i got my new computer. Nothing has been 'bricked' yet. It sucks that that guys cpu got destroyed but it was not entirely lm sensors's fault, it was also a kernel problem which most likely should of stopped them from doing anything that could damage the hardware. 

now it is fixed, and we can all rejoice =)

---

### Post by rajeev1204 on 2009-02-03
> **JillSwift said:**
> Kind of a FUDish way of putting it, isnt' that?

***One*** dead CPU out of thousands of installations, and the problem's been identified and handled. Kudos to the lm-sensors team for hopping on it like that.


Ya but if the user wasnt smart enough to report it, it wouldnt have been isolated.You think any user would have wildly guessed that lm sensors could be reason for the CPU going dead? Not me.Call me ignorant ,but i would have contacted AMD thinking it was a faulty CPU.That one CPU could have been yours,And its damn expensive too.

Anyways, good that it has been fixed.And yes,kudos  the lm-sensors team looked into it.

---

### Post by JillSwift on 2009-02-03
> **rajeev1204 said:**
> That one CPU could have been yours,And its damn expensive too.Well, by that logic...

[LIST]
[*]Shouldn't own anything valuable, there have been burglaries.
[*]Shouldn't drive a car, there have been mechanical failures.
[*]Shouldn't eat at restaurants, there have been incidents of tainted food.
[/LIST]
Life gets awfully boring - if rather stressful - if all you do is avoid even the tiniest risk. :)

---

### Post by Trail on 2009-02-03
I call it a hardware bug, if hardware of any sort can potentially be damaged by software operations.

---

### Post by binbash on 2009-02-03
There was a bug at UBUNTU which destroys some wifi cards.Then you should not recommend UBUNTU also.I dont agree with you

---

### Post by p_quarles on 2009-02-03
I'm not sure why lm-sensors would be any worse than, say, a web browser. I mean, it is indeed probing software, but it's not like it puts a thermometer on top of your motherboard. It's just querying information that is already on your system, but in some cases isn't readily accessible.

---

### Post by Polygon on 2009-02-03
> **p_quarles said:**
> I'm not sure why lm-sensors would be any worse than, say, a web browser. I mean, it is indeed probing software, but it's not like it puts a thermometer on top of your motherboard. It's just querying information that is already on your system, but in some cases isn't readily accessible.

lm-sensors does do some scary stuff, as in it probes the varios parts of your hardware that usually doesnt read by normal programs,and in this case it probed the wrong part of the CPU and the cpu freaked out (most likely was a cpu bug as well, but yeah)

---

