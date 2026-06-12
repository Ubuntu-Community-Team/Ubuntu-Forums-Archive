---
title: "Need to force specific resolution for GUI when I add it to server"
date: 2013-10-10
forum: Server Platforms
---

### Post by K7AAY on 2013-10-10
Got a Ubuntu 13.04 server set up. Now I need to add a GUI so I can occasionally, at will (not every time) load a web browser to control a device. Problem is, it's in a rack in a lights-out server room and I must use a KVM-over-LAN device (Raritan Command Center) to control it. 

Would strongly like to avoid the reinstall of the server, just want to add LXDE or XFCE (don't want overhead of GNOME or KDE) and a browser (FF or Chromium). Tried it once, LXDE came up in 1368-by-somethingoroher mode. Could not see the panel or launch any app because I could not scroll around in the Raritan to see that part of the screen, hadda do Ctrl-Shift-F1 to get to tty1 and uninstall the LXDE so I could get my server back.

So, here's the questions.

1) If I add a GUI, can I call for it only when I want it, for LXDE came back up even if I rebooted. I want CLI all the time and GUI just on demand.
2) How can I make that GUI launch in 800x600 every time without fail, avoiding the higher-res modes which keep me from using it?

Thank you kindly, all.

---

### Post by papibe on 2013-10-10
Hi K7AAY.

I would reconsider the idea of installing a full desktop, as you only need either xauth, or at best xorg and a window manager (openbox for instance).

[Here]("https://help.ubuntu.com/community/ServerGUI#Server_configuration_management") is an example on how to do that.

As for overriding, the now default graphic environment, you need to change a parameter on grub (read [here]("http://askubuntu.com/questions/174312/how-can-i-set-my-ubuntu-12-04-lts-to-boot-to-console-without-gui")).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by K7AAY on 2013-10-10
So, I can install 
a) xauth and Firefox, or
b) xorg, openbox and Firefox
and not need a full GUI to use Firefox?

And, when I launch that, everything remains in 800x600 mode?

If so, perfect solution, thank you kindly, *papibe*.

---

### Post by Lars Noodén on 2013-10-10
Another way might be to connect with ssh and have it forward X11 so you can see the browser on your local machine.

```

ssh -X k7aay@server.example.org firefox

```

That way you wouldn't even need a window manager, though Openbox is popular.  Network latency can be a problem with that, however.

---

### Post by papibe on 2013-10-10
> **K7AAY said:**
> So, I can install 
a) xauth and Firefox, or
b) xorg, openbox and Firefox
and not need a full GUI to use Firefox?
Yes. Note that you would access it as Lars Noodén describes (ssh X11 forwarding).
> **K7AAY said:**
> And, when I launch that, everything remains in 800x600 mode?
As you most likely would be forwarding a window, you could resize it as you want on the client size.

Let us know how it goes.
Regards

---

### Post by Lars Noodén on 2013-10-10
With X11 forwarding it gets even simpler, no GUI components are needed on the remote server.  It is enough with just the graphical applications, such as Firefox.  Since the actual display is on the local computer, it is forwarded to from the server to the local machine and makes use of the X server, window manager and desktop environment there.  The X server is where the display actually takes place.  But, again, if there is a lot of latency on your network, it won't be so pleasant to use and you'll want pabibe's suggestion of a lean window manager on the server and let the "KVM" take care of the connection.

---

### Post by K7AAY on 2013-10-10
And, SSH connections to the server ain't *permiso* for this test case, _has_ to go through the Raritan, so back to **papibe**'s suggestion.

---

