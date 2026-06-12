---
title: "Screen timeout interrupted after boot"
date: 2023-03-08
forum: Server Platforms
---

### Post by Anquietas on 2023-03-08
Hello,

I was wondering if someone could help me out with a wierd Console lock / login screen / monitor problem....

I have a home server linux box running Ubuntu Server 22.04.1 LTS.
Being a Server, it runs 24/7 and is connected to my VGA Monitor.
That being said, I need the server to run only as a Linux Box, no Monitor Output, unless I am actively working on it. That monitor is being used for something else, too.

So I configured the following in **/etc/default/grub**:
```

GRUB_CMDLINE_LINUX_DEFAULT="consoleblank=60"

```

As I start the server and it begins the boot process, it reaches 60 seconds somewhere at the middle of the boot sequence (when Starting the Services), and my monitor turns off ! That's very OK ! I see that the above setting is respected.

BUT, near the Login Prompt, something happens that triggers the monitor to go into Active State again, and the monitor remains in this active state (however, it closes after a period, but it still doesn't enter sleep mode).
I have to physically hit Enter in order to display the Login Prompt.
Only after that, the monitor turns off after 60 seconds and enters sleep mode.

I am assuming something is Hanging in the Console which keeps my monitor busy somehow and it doesn't let it shut down:
The text looks similar to this:
```

Welcome to Ubuntu .....

```
and no login prompt.

Only if I hit Enter to display the Login Prompt, something "releases" the hold on the Monitor, and the Monitor effectively goes to sleep as it should be.

First, I assumed that it is cloud-init. I disabled cloud-init. Now, my system is running without it. (I hope I don't need it ! Or,...do I ? I only have a few services like webserver, email server, vpn server, and so on...) 

Can anyone guess what is going on,... or is there a more direct or efficient method of effectively shutting down the monitor after the server booted ?
(of course, if I have to work on the TTY console, physically, I need that monitor, so it should come back to life when I hit a key on the keyboard... But I want it to timeout after 60 seconds to save energy consumption and the monitor itself).

Thank you !

---

