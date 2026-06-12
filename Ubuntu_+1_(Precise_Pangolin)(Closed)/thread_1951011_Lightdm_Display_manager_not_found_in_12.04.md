---
title: "Lightdm Display manager not found in 12.04 ?"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rigel4 on 2012-04-01
I have been on line looking to find an answer to this problem for the last couple of hours and haven't had any luck.

I can t find any way to launch the Simple display manager in Ubuntu 12.04 beta2.
Ubuntu software center says it is installed but i simply cant find the application anywhere to change the back ground of the login screen.

If i use dash it says "nothing found".

Any help appreciated.

Thank you

---

### Post by grahammechanical on 2012-04-01
You are talking about the Simple LightDm Manager. You most certainly do have the LightDM display manager installed but may be you do not have the Simple LightDM Manager installed. They are two different things.

Simple LightDM Manager is installed through a PPA. So, although the Software Centre will confirm that LightDM is installed It will not show any result if you search for Simple LightDM Manager unless you added the PPA to your software sources and then run Update Manager to install it.

Can you confirm that you installed Simple LightDM Manager?

[https://launchpad.net/~claudiocn/+archive/slm]("https://launchpad.net/%7Eclaudiocn/+archive/slm")

Regards.

---

### Post by mc4man on 2012-04-01
That ppa is for oneiric only & would have to be added to sources as such, not as precise

In any event probably doesn't matter, I'd be very surprised if the app worked with the current lightdm in 12.04

---

### Post by rigel4 on 2012-04-02
No , i cant confirm it. I was under the impression it was there by default in this release.
I'm sorry. i really thought it was installed.

Thank you

---

### Post by grahammechanical on 2012-04-02
I had simple LightDM manager installed on 12.04 Alpha 1 and it worked. I took it out when the change-over from LightDM to the desktop got messed up. But Simple LightDM Manager was not the cause. It was Unity-greeter. Which was fixed by an update a couple of weeks later.

Mind you, my 12.04 alpha 1 was built on a 11.10 install. So, it was more 11.10 than 12.04 at that stage.

@rigel4

It is an easy mistake to make, especially as LightDM is described as a Display manager. which it is. Someone else also thought as you did.

Regards.

---

