---
title: "Screen lock question"
date: 2013-12-31
forum: Ubuntu Development Version
---

### Post by d-cosner on 2013-12-31
I have been looking over 14.04 and Unity pretty carefully, looking for bugs and things that might need attention. I noticed the dialogue box to enter my password for the screen lock did not really go along with the look of Unity. I realize that this may be the last we see of Unity 7 and that Unity 8 is being developed. The restart, shut down dialogues in the panel menu and the Unity greeter have been changed to have the Unity look to them. Should the lock screen dialogue to enter the password also have the same look to it?

Unity has seen many refinements over the last few releases and I wonder if anyone has thought about changing the appearance of the lock screen? The user interface freeze is still a ways off and I am thinking about mentioning this. Anyone have an opinion about this?

Edit: I had a hard time figuring out how to submit this and accidentally generated a bunch of stuff about compiz.... Oh well, at least I got it out there.

 [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1265251](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1265251)

---

### Post by grahammechanical on 2014-01-01
I am not sure that the look of the screen lock dialog has much to do with Unity. I agree that it does not match the design of the notification dialogs in 13.10 and 14.04. I am guessing that this design has more to do with LightDM. The other month I learnt something about LightDM that I did not know. It does more than handle the login screen. It is a Display Manager. So, I guess that the screen lock login dialog is also coming from LightDM.

MIr will replace not only the Xserver but also LightDM and Compiz. So, this may not be "fixed" until we get full convergence of the Ubuntu mobile platform with the Ubuntu desktop platform. In oher words, sometime between spring 2014 and spring 2015.

Regards.

---

### Post by d-cosner on 2014-01-01
Thanks for the reply grahammechanical. I am sure you are right. I was just thinking that 14.04 is going to be supported for 5 years and the developers have been aiming for a consistent look for Unity in the last few releases. The look of the screen lock is a pretty trivial thing but the LTS is aimed at businesses and altering the look of the screen lock might help Canonical make an even better impression. I really doubt anyone will consider the bug report I created but I just wanted to put the idea out there just in case they might be interested.

I did see a lot going on in the bug tracking system about Unity 8 and MIR, so I realize Canonical is very serious about Ubuntu running on phones and tablets.

---

### Post by Mateusz Stachowski on 2014-01-01
I think that there is quite a big possibility that 14.04 will have Unity style locksreen because recently Andrea Azzarone started a new branch titled lockscreen.

[https://code.launchpad.net/~andyrock/unity/lockscreen](https://code.launchpad.net/~andyrock/unity/lockscreen)

This is only a beginning of the work.

> [COLOR=#333333][FONT=Ubuntu]Initial commit for the unity lockscreen. UserAuthenticator added with tests too.[/FONT][/COLOR]

---

### Post by d-cosner on 2014-01-01
Wow! That is awesome! Thanks!

---

