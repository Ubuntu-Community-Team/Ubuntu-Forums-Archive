---
title: "Unable to see login using Xvnc (when no screen connected)"
date: 2010-08-27
forum: Server Platforms
---

### Post by silentbuteo2 on 2010-08-27
I have a VNC connection running to my Ubuntu 10.04 server (configuration see [http://oapeon.blogspot.com/2010/05/ubuntu-1004-vnc-based-login-server.html]("http://oapeon.blogspot.com/2010/05/ubuntu-1004-vnc-based-login-server.html")). This was running fine for a day or 2 after that, sometimes it worked and sometimes not. When it didn't work, I could connect with VNC (i got a gray window with the cursor) but no login screen was shown.
After some testing I now know what the root cause is. When I disconnect the screen from my server, I don't get the login screen. When I connect the screen (even if it is not powered) after a reboot, I can see the login screen.

Next I was looking for some logging that could indicate some problems. I looked into "/var/log/Xorg.0.log" and there I see a difference when I connect/disconnect the screen. When the screen is disconnected, the log says:
```
(II) intel(0): Integrated Graphics Chipset: Intel(R) Pineview G
(--) intel(0): Chipset: "Pineview G"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): Output VGA1 disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA1 disconnected
(WW) intel(0): Unable to find initial modes
(==) intel(0): video overlay key set to 0x101fe
(EE) intel(0): No modes.
(II) UnloadModule: "intel"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

Can anyone help me with this awkward problem?

---

### Post by arrrghhh on 2010-08-27
So you have an X server installed I assume...?

Kinda odd for a server...

But, with that said, I think there's some way you can 'trick' x.org into thinking there's always a monitor connected.  I think it involves some hairy X11 conf file maddness...  I know there were some other people trying to do this with their htpc, but I'm not sure how much progress they made.

---

### Post by silentbuteo2 on 2010-09-02
For some programs i have to use a GUI. Most of the time it's for configuring the setup.

Later on I'll try to remove the X stuff again from default starting. Then only the command prompt will be available (ssh). And if i need the X for something, then i can manually do that.
For now, now idea how to do this, but that's for later.

Another thing i now saw, (i think the same root cause) was when i startup the server without a screen attached. When i connect later on the screen, no image is seen on the screen. After a new reboot everything is fine. Odd. When i do that with Windows, this doesn't matter. The resolution of the screen is not correct, but i can see at least something.

Ok, but for the X.org configuration. How can I set the fixed configuration. Is there some way to have a default setting only when there is no screen connected? That way, when a screen is attached, the correct config is used, instead of the default one.

---

### Post by silentbuteo2 on 2010-09-08
any thoughts?

---

