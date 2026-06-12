---
title: "possible to keep plymouth splash running"
date: 2010-05-16
forum: Server Platforms
---

### Post by stormcel on 2010-05-16
Hi guys,
Is it possible to keep the plymouth splash screen running, requiring a key combination to bring up a login.
I am running this box headless and if any snooper comes along and plugs in a monitor I would like for them to see the logo and have to hit a key combo to get in.
I saw that this was actually a bug at one time and now I would like it as a feature.
:-)
TIA for any help!!!

---

### Post by lavinog on 2010-05-16
I think a problem would be that the monitor would have to be plugged in for plymouth to know what resolution to use...I think.

Is this just for looks?
Are you expecting it to be a deterrent?
What key combo would you be wanting?

---

### Post by stormcel on 2010-05-16
Yes, I would like this feature as a deterrent.  The box is running all of its services via http in an office and there should be no reason for a user to login at the console except myself for troubleshooting. I have already customized the splash, but it gives way to the login prompt.
This box should sit unmolested in a corner, but should the curious plug a monitor and keyboard in and boot, I would like them to see the animated logo on a loop, I would like to lockout the ESC key and other obvious devices.  Maybe a CTRL+ALT+SHIFT+F9 type of thing to get a prompt.
It's not going to slow down a tech, but a newb or just a curious citizen will probably give up quickly.
I mean a tech would probably SSH in anyway and get a prompt.  They still need the login info.
I think you get my point though.  This thing is going to be unprotected in the field and I would like to add as many layers as possible without affecting performance too greatly.

Thanks again for any help!

---

### Post by stormcel on 2010-05-24
Bump, 
Anybody?

---

### Post by arrrghhh on 2010-05-24
I guess this really isn't a issue for most, a secure password is all you need...

Sorry, I understand what you want but I have no idea how to do it.  Again, a secure password *should* be enough.

---

### Post by stormcel on 2010-05-25
Hey, at this point I'm just happy that anyone responded.
Thank you for your honesty....
 
 
OK, how about this....
Is there a way to activate the plymouth splash as a foreground process in tty1 on Lucid Server?
Kind of like a screensaver preview.
This seems to be possible, maybe?

---

### Post by lavinog on 2010-05-25
I think the issue is that plymouth uses xserver so it will be on tty7.
Basically you could setup the system to autologin a user with limited privileges that runs an app that does what you want at login.
The app can require a certain key combo that will logout the limited user and bring you to a login screen.

---

### Post by stormcel on 2010-05-26
Thanks lavinog!
That gives me a definite direction to try!

---

