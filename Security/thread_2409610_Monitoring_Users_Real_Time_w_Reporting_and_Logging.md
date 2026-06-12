---
title: "Monitoring Users Real Time w/ Reporting and Logging"
date: 2019-01-04
forum: Security
---

### Post by humblesage2 on 2019-01-04
Hello!

I'm relatively new to Linux in general so be gentle. I have a situation where I have to implement a small Ubuntu 18.04.1 LTS box for some Analytics and it has to allow an outside company to access it to develop on it. They are requiring root access so I need a way to monitor their activity in real time, with logging and email notifications so that I may act accordingly if they step out of line. I'm looking for a thorough explanation here as I am new to Linux (not IT). I don't want to debate the politics of procedure, proper accountability with action is enough for my situation. I simply need this type of solution. I have researched Sysdig, whowatch, and a few other various tools but am finding configuration of these to be a bit difficult.

Specifically, I'd like to achieve a setup where I can monitor and log ALL the activities (down to the command line). I'm aware that a user having root access will be able to cover their tracks but the premise here is if I am also sudo root and getting real-time notifications I can account for the sudo user causing the mischief. ie, they stop the services notifying me etc.. act accordingly etc..

Appreciate your insights and direction in advance. :)

---

### Post by Frogs Hair on 2019-01-04
Edit: sysdig included in original post.

---

### Post by oldos2er on 2019-01-04
Why isn't your company's IT handling this?

---

### Post by humblesage2 on 2019-01-04
@Frogs Hair: I was looking into this but it has errors right out of the box. I am troubleshooting that separately.

@oldos2er: I am the IT company. Looking to dive deeper into ubuntu and see how I can leverage it in some existing networks I manage. Needs to be ubuntu for this particular applications needs and comfort level of the developers (though I suspect this could be done on a different distro). BTW, nice throwback to OS2 in your name. :)

---

### Post by oldos2er on 2019-01-05
You specifically said "I am new to Linux (not IT)" in your OP?

May I suggest you look into [Canonical paid support]("https://www.ubuntu.com/support/plans-and-pricing") for your software requirements? Discussions of monitoring software like you describe can be a problem here, due to potential legal fallout.

---

### Post by SeijiSensei on 2019-01-06
If you're using an outside contractor that you think is so untrustworthy, you need a different contractor.

---

### Post by humblesage2 on 2019-01-06
@oldos2er: I don't see how anything I'm discussing could bring about any "legal fallout". There's nothing wrong with monitoring Administrator's of a network, I even do this myself. I'm simply looking for a way to do it with Ubuntu.

@SeijiSensei: Your statement is a bit trollish. Please limit input to productive responses, not stating the not so indirect yet not so obvious. Clearly I trust the company but EVERY responsible System Administrator should maintain their network with monitoring of all aspects. I won't digress any further or debate a "trust" topic with anyone here.

Kind of expected more from a tech forum that's built on a "free" operating system. Guess nothing stays free for long. I'll figure it out.

---

### Post by oldos2er on 2019-01-06
Freely available online information isn't always used in a benign manner, that's why we tend to frown on discussions of monitoring software.

---

### Post by humblesage2 on 2019-01-06
> **oldos2er said:**
> Freely available online information isn't always used in a benign manner, that's why we tend to frown on discussions of monitoring software.

Fair enough.

---

