---
title: "Vlc without screen"
date: 2010-09-13
forum: Server Platforms
---

### Post by Paretje on 2010-09-13
Well, I had today some big problems. I want to set up a little home server here, and everything is going well with this.

But, an important thing I would want to let my server do is recording and streaming TV. Well, that's all going well, until I do my screen away, and I restart my server, then I get this:
```
VLC media player 1.0.6 Goldeneye
[0x9e0bae0] inhibit interface error: Failed to connect to the D-Bus session daemon: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.

[0x9e0bae0] main interface error: no suitable interface module
[0x9d74148] main libvlc error: interface "inhibit,none" initialization failed
[0x9e11050] main interface error: no suitable interface module
[0x9d74148] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9e11040] dummy interface: using the dummy interface module...
[0x9e22910] dvb access error: FrontEndOpen: opening device failed (Permission denied)
[0xb7000a40] main input error: open of `dvb://frequency=482000000' failed: (null)
[0xb7000a40] main input error: Your input can't be opened
[0xb7000a40] main input error: VLC is unable to open the MRL 'dvb://frequency=482000000'. Check the log for details.

```

But, two minutes before, this was no problem:
```
VLC media player 1.0.6 Goldeneye
[0xb7000cc0] inhibit interface error: Failed to connect to the D-Bus session daemon: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.

[0xb7000cc0] main interface error: no suitable interface module
[0x8ca9148] main libvlc error: interface "inhibit,none" initialization failed
[0xb7000ef8] main interface error: no suitable interface module
[0x8ca9148] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x8d47408] dummy interface: using the dummy interface module...
libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 0) for PID 4112
libdvbpsi error (PSI decoder): TS discontinuity (received 3, expected 0) for PID 17

```

The only difference is my screen, but I can't just let my screen on my server all the time, and I think it should be possible to reboot, without connecting my screen. So I'm hoping now to find my solution here ...

---

### Post by gobbledigook on 2010-09-14
are you using cvlc? ie commandline-vlc :)

---

### Post by kimsmarkin on 2010-09-14
I am having problems getting VLC to play my second monitor (TV) while using the library. The first film in my play list goes to a second monitor as it should. But the second film, after all, return to the default setting and the movie playing on my laptop monitor.

---

### Post by Paretje on 2010-09-14
> **gobbledigook said:**
> are you using cvlc? ie commandline-vlc :)

Off course, I do this since a long time, only now I made a Atom server, and so I don't want to run my i7 all day long. But it seems like there is something that isn't done in combination with permissions etc. when I start my computer with screen, or without, and that's my problem.

---

### Post by Paretje on 2010-09-30
bump

---

### Post by linkyone on 2011-02-07
I've got the same error. It seems if I try the same thing with Ubuntu Desktop 10.04 I have no problems at all. I want to do the same as the original poster and run 'cvlc -I http' on a headless Ubuntu Server 10.04. What are we missing (besides the whole GUI thing) that is causing this error:

"Failed to connect to the D-Bus session daemon: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed."

---

### Post by HermanAB on 2011-02-07
How about installing Mythbuntu?

---

### Post by linkyone on 2011-02-09
> **HermanAB said:**
> How about installing Mythbuntu?

That would be perfect for the client machines but I'm trying to setup the server side.

---

