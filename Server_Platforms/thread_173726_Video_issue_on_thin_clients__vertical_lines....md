---
title: "Video issue on thin clients : vertical lines..."
date: 2006-05-10
forum: Server Platforms
---

### Post by AlexMorin on 2006-05-10
Hello all!

I am running Dapper Beta on a nice 3.2 Ghz HP Proliant server. Everything is working, the thin clients boot-up and login fine. All is rosy, except for a few glitches...

The thin clients are Compaq Deskpro EN PIII 866mhz, using the onboard Intel 815 graphics card. When running at the default resolution (1280 x 1024), they have ten thin bluish vertical lines running from the bottom to the top of the screen, whether at the login screen or when the session is open. They seem to be a couple of pixels wide, and these pixels are moving upwards.

My other test (PIII Ciara) machines do not exhibit this behavior, and changing the screen does not help.

If I use a lower resolution, all is fine, except for the login screen. What should I try to resolve this issue? Or how do I set the default resolution for the terminals, including the login screen?

---

### Post by AlexMorin on 2006-06-06
Anyone? This is really bugging me.

---

### Post by AlexMorin on 2006-06-13
I insist! Anyone?

---

### Post by Ignite_nz on 2006-06-13
I'm no expert on what you're doing here, but try and install Dapper 6.06, the proper release not the beta, that could help?

---

### Post by AlexMorin on 2006-06-13
[QUOTE=Ignite_nz]I'm no expert on what you're doing here, but try and install Dapper 6.06, the proper release not the beta, that could help?[/QUOTE]
Good point! Well, I installed the beta, but since I did 'aptitude upgrade' last week, I should be current with 6.06 LTS right?

Thanks for the reply!

---

### Post by kdw on 2006-06-13
[QUOTE=AlexMorin]

If I use a lower resolution, all is fine, except for the login screen. What should I try to resolve this issue? Or how do I set the default resolution for the terminals, including the login screen?[/QUOTE]

I had a bunch of workstations with the Intel 810 graphics chip that had that weird vertical line issue.  Lowering the color depth to 15/16 bit fixed it.

If you are running LTSP on the server, this link will help:
[http://wiki.ltsp.org/twiki/bin/view/Ltsp/LtsConf#X_COLOR_DEPTH](http://wiki.ltsp.org/twiki/bin/view/Ltsp/LtsConf#X_COLOR_DEPTH)

---

### Post by AlexMorin on 2006-06-13
I will set-up an LTS.conf file, thanks!

---

### Post by AlexMorin on 2006-09-18
It worked!! Thanks a lot!
It seems the default resolution and bit depth was the cause.

Specifying 16 bits in a brand new lts.conf file fixed the issue.

[Default]
        SERVER                  = 192.168.0.1
        X_COLOR_DEPTH           = 16

Of course, there are many more settings to be done in there. See : [http://wiki.ltsp.org/twiki/bin/view/Ltsp/LtsConf#X_COLOR_DEPTH](http://wiki.ltsp.org/twiki/bin/view/Ltsp/LtsConf#X_COLOR_DEPTH)

Wee!

---

