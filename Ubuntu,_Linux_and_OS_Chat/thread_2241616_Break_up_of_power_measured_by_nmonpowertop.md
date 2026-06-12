---
title: "Break up of power measured by nmon/powertop"
date: 2014-08-27
forum: Ubuntu, Linux and OS Chat
---

### Post by prashant6 on 2014-08-27
I have tried calculating the power usage by a process using powertop  tool. It works fine. Also, I have tried nmon tool. But I have a problem. For Example if I measure power usage by a process using "powertop"  and it comes out to be say 3 watts. Is there some tool by which I can  view the breakup of this 3 watts under different heads such as memory,  CPU, etc. Such as how much power was consumed in which component?

---

### Post by Mike_Walsh on 2014-08-28
Excuse me if I'm misunderstanding you, but.....do you have a specific reason for wanting to know?

Perhaps a systems designer, by any chance?

To the best of my knowledge, most hardware monitoring programs will measure things like temps, voltages (by major components, perhaps, but mostly your CPU) and stuff like fan speeds; but I don't think you're going to find anything that will give you a component by component breakdown of where every last milliwatt and milliamp is going to.

BTW, I may have played around with these things for 30-odd years, but by no means do I consider myself an 'expert'. I am MORE than willing to be proved wrong!

Wiser heads than mine can probably steer you in the direction you need.

Regards,

Mike.

---

### Post by prashant6 on 2014-09-01
thank you mike. no actually i m not a system designer. this is the demand of a research project. actually it can be very easily done using the multimeter but i was wondering can it be done through some software or not???

---

### Post by Mike_Walsh on 2014-09-02
Hello, prashant.

Um. As I said in my previous post, I don't know of any other sort of measuring software apart from the standard system stuff like PSensor, HWMonitor, Speccy.....that kind of thing. No doubt there IS something available that would do exactly what you want, but I rather doubt it'll be open-source software; I suspect you'll have to purchase proprietary stuff, and probably run it on Windows.

Sorry I can't be of any more help.

Perhaps re-posting it under 'General Help', or maybe 'Development & Programming' might help? I'll confess, that kind of thing is a little beyond my experience.

Regards,

Mike.

---

