---
title: "[SOLVED] What really is this?"
date: 2009-01-06
forum: Security
---

### Post by BSG Fan on 2009-01-06
Hello
I don't know if this is the place to post this thread.

Well, I use Ubuntu, and I can not login in Myspace

This is the certificate error I am receiving.

Can u tell me what specifically it is?

Plz, see the attachment

Thanks u

BSG Fan
;)

---

### Post by cariboo on 2009-01-06
I beleive it may be a bug in Firefoax as I get that on occasion, If it is from a site I trust (I had this once on a Government of Canada web site using FireFox 3.02 in VIsta) I just click on the link to create an execption.

Jim

---

### Post by ToasterThief on 2009-01-06
> **cariboo907 said:**
> I beleive it may be a bug in Firefoax as I get that on occasion, If it is from a site I trust (I had this once on a Government of Canada web site using FireFox 3.02 in VIsta) I just click on the link to create an execption.

Jim

Rubbish. It has nothing to do with Firefox or Ubuntu. It's Myspace messing up their certificates. Just add the exception as Firefox suggest. ...Christ.

---

### Post by pdtpatrick on 2009-01-06
Coulda said that a bit less harsh .. people mistakes sometimes.

---

### Post by hyper_ch on 2009-01-07
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by amac777 on 2009-01-07
The date on your computer is wrong. Look in the upper right hand corner - it says Nov 6th. I suspect the year is probably wrong too and is probably before the effective date of the certificate.

If this is the problem, changing the date on your computer to be correct will fix the problem.

---

### Post by cariboo on 2009-01-07
ToasterThief: I sorry if I hurt your feelings by saying the Firefox 3.0.2 may have had a bug, but I'm sticking by my guns, I even had a invalid security certificate error at this site:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

as well as several other sites.

amac777 is right, I didn't look close enough at the OP's screenshot, it is a problem with the date on his computer.

Jim

---

### Post by BSG Fan on 2009-01-09
> **amac777 said:**
> The date on your computer is wrong. Look in the upper right hand corner - it says Nov 6th. I suspect the year is probably wrong too and is probably before the effective date of the certificate.

If this is the problem, changing the date on your computer to be correct will fix the problem.

AMAC77 has the reason!
The problem was in my clock pc.
I changed to the correct time and the problem disappeared.
I thought was a hacker or something.

Thanks to everybody for share your opinion and help me.
U rock

BSG fan
:)

---

### Post by argie on 2009-01-11
> **cariboo907 said:**
> ToasterThief: I sorry if I hurt your feelings by saying the Firefox 3.0.2 may have had a bug, but I'm sticking by my guns, I even had a invalid security certificate error at this site:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

as well as several other sites.

amac777 is right, I didn't look close enough at the OP's screenshot, it is a problem with the date on his computer.

Jim

That is very interesting. Were you using untrusted wireless? Can you be certain it wasn't a man-in-the-middle attack? See [this bug report]("https://bugzilla.mozilla.org/show_bug.cgi?id=460374"), for example.

---

### Post by cariboo on 2009-01-11
I haven't had the problem since upgrading to 3.0.5, and I am currently using 3.1b2, I haven't run into the problem agian.

I'm using a wired network, although my wireless is open. I live far enough from any one else, that they would have to be sitting in my yard to access it.

Jim

---

