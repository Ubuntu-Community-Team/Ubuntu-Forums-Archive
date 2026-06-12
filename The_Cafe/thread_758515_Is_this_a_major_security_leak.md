---
title: "Is this a major security leak??"
date: 2008-04-18
forum: The Cafe
---

### Post by itix on 2008-04-18
Right click on menus, go to system tools, enable root terminal, start root terminal, play god on the machine and not ONCE did MY computer ask for the root password.
I brought up a nautilus file browser and was able to create folders on my external HD (that for some strange reason is owned by root, same with my iPod and my usb-stick: [post]("http://ubuntuforums.org/showthread.php?t=758223")). I just wonder, had I a client system in, for example, the school, would the "curious" little pupils be able experiment with the machines via this?

---

### Post by wormser on 2008-04-18
I am running Gusty and it brought up a GUI password request.

Is this on Hardy?  It sounds like a BIG security flaw to me.  Have somebody else confirm it then write up a bug in [launchpad]("https://launchpad.net/ubuntu").  It needs to be fixed in the next 6 days.

BTW, nice find!

---

### Post by LightB on 2008-04-18
Uh, well it uses sudo to authenticate root permissions right? sudo gets timed in and maintains root permissions without password input for a limited time, right?

Other than that, make sure you're not actually logged in as root. (stranger things have happened)

---

### Post by itix on 2008-04-18
I am also running gutsy... Ran hardy until yesterday when I got tired of all the bugs. I should change my profile display.
I just tried again and it actually asked for my root password this time. It was from a fresh login last time, so It could not be that I had already typed it in for another application. Maybe it was just a one-time-only event??

---

### Post by Sukarn on 2008-04-18
The "root terminal" as you're calling it, is just a "gksudo gnome-terminal" call, so it brings up a graphical password box courtesy of gksudo.

If you already ran something with gksudo recently, then you wouldn't get the password box because of the way gksudo and sudo are set up by default to not ask for password again within a short time period.

---

### Post by itix on 2008-04-18
How would I make sure of that??
I have not enabled root login... and I still needed to type the root password the second time so I guess that I'm not.

---

### Post by chewearn on 2008-04-18
I tried it in Hardy, the password prompt came up.  No problem there.

---

### Post by itix on 2008-04-18
Probably just a one-time event...
Guess it's nothing then... Wierd as hell though.

---

### Post by Sukarn on 2008-04-18
> **itix said:**
> How would I make sure of that??
I have not enabled root login... and I still needed to type the root password the second time so I guess that I'm not.

Make sure of what?

Its just that if you used gksudo with any application recently (anything that gives the graphical password prompt like synaptic, update manager, etc. is calling gksudo) then you wouldn't be prompted for the password again.

I'm not sure about this, but I think that the default timeout is set to 15 minutes, and it seems to last into different sessions (at least for me). I mean that if I use gksudo synaptic, and then logout and login then I can use gksudo [anything] without being prompted for my password again unless the 15 minutes have passed, and as long as its treated as the same virtual console or X session, which happens if I do not log into multiple sessions at the same time (like being logged into two X sessions at the same time)

---

### Post by itix on 2008-04-18
> **LightB said:**
>  [...] make sure you're not actually logged in as root. (stranger things have happened)

What I mean is; are there any cool terminal command that you can use, like *am_I_root_loz?* or such?

The gksudo on different sesions theory seams like the mot plausable one. I did actually use certain root constricted applications before logging out...

---

### Post by LightB on 2008-04-18
Not sure, either way I just think it's a case of the sudo password timeout and you input the password previously.

---

### Post by tribaal on 2008-04-18
You can easily see who you are by using the "whoami" command.

Changing the timeout of your sudo cache might work for you if you don't mind inputing your password every time.

Cheers

- Trib'

---

### Post by itix on 2008-04-18
> **tribaal said:**
> You can easily see who you are by using the "whoami" command.[...] 

Cool! =)
Philosophical linux ftw x)

...and I already knew about the timout, but thanx anyways. I think we have solved the problem actually. It was just a timout that hadn't run out just yet. I **do** mind entering my password actually since I'm th only user of this computer so if I would change the timeout, I would lengthen it. I was just thinking of those who isn't the only user of their comuter.

---

### Post by Trail on 2008-04-18
If you really want to, you can change sude policy (through visudo) so that you don't have to type your password when using sudo/gksudo/kdesu/... Look it up on these forums.

---

### Post by macogw on 2008-04-18
> **itix said:**
> What I mean is; are there any cool terminal command that you can use, like *am_I_root_loz?* or such?

The gksudo on different sesions theory seams like the mot plausable one. I did actually use certain root constricted applications before logging out...

whoami

---

### Post by uknowho008 on 2008-04-18
i noticed another bug in 8.04 on xubuntu. i reported it on launchpad but dont really know what im doing and nobody seems to have addressed it.

if youre logged in then you switch user to another user. when you log out of that user it logs you right back into the previous user automatically without any password or anything. seems like a pretty big flaw to me.

---

### Post by shinythings on 2008-04-18
That is actually a setting you can change. Right click on the switcher app, select 'Preferences', and tick 'Lock the screen after switching users' under 'Options'.

---

### Post by Daveski on 2008-04-18
> **itix said:**
>  I **do** mind entering my password actually since I'm th only user of this computer so if I would change the timeout, I would lengthen it. I was just thinking of those who isn't the only user of their comuter.

Then you would set up the other users not to have the authority to run sudo - easy really.

---

### Post by HermanAB on 2008-04-18
$ who

---

### Post by orgy on 2008-04-18
maybe before you ran the root terminal you ran the update manager which is a gksudo call, that's why it didnt ask for your password.

my guess.

---

### Post by Polygon on 2008-04-18
yeah, you most likely entered your password for some other gksudo application within 5 minutes which is why it didnt ask for your pass.

---

### Post by itix on 2008-04-19
Read through the entire thread ;)
We have already established that that was what happened, only I logged out and in again (to make sure that the GDM-theme was correct) and Ubuntu thought of it as one session. I therefor felt a bit strange since it was a fresh login, but it's no security leak.

---

