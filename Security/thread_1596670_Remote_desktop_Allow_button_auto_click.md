---
title: "Remote desktop Allow button auto click???"
date: 2010-10-14
forum: Security
---

### Post by christoff123 on 2010-10-14
Hey there, guys.
That's my first post in this very helpful and useful forum ;).
I have a home LAN server with Ubuntu Desktop edition 10.10 and I'm having a problem with remote desktop application. For now I have a monitor on that machine, but in the future it's gonna be only the box, without any periferal devices. When I try to log in via UltraVNC from Windows XP, on Ubuntu server a little window pops up, asking me to allow or refuse this "invader", so I click Allow and I really have full control on that machine. However, when I dont have any devices I wouldnt be able to click this Allow button, but will have to have full control. So, my question is how to autoclick this Allow button? Or when I try to log in the ubuntu machine, it would automatically give me full control?
Thanks in advance!

---

### Post by OpSecShellshock on 2010-10-14
Hmmm. Even if there were a way to do that, it would almost certainly violate the forum rules if someone were to say how.

---

### Post by christoff123 on 2010-10-14
Yes, I think u r right, bot according to your post i understand that there's no way to do this. Do I understand u right?

---

### Post by OpSecShellshock on 2010-10-14
Not sure. I mean, it looks like in the Remote Desktop preferences on the Ubuntu desktop there is an option, checked by default, that says something about confirming before letting an external machine connect. It's possible that you could just un-check that and it would work without even prompting in the first place.

---

### Post by cariboo on 2010-10-14
If you set vinagre-preferences (the remote desktop server) the way it is in the screen shot, you shouldn't need to confirm a connection on the remote system.

The other thing you'll have to do is setup automatic login, as you won't be able to do anything if it is sitting at the login window.

Make sure you use a strong password.

The other thing I would suggest, is don't even think about accessing the system from anywhere but your local network with the default remote desktop applet.

---

### Post by christoff123 on 2010-10-15
Still got the same problem

---

