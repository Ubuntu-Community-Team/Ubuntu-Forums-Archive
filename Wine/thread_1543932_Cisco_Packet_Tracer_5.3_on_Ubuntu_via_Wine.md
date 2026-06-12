---
title: "Cisco Packet Tracer 5.3 on Ubuntu via Wine"
date: 2010-08-01
forum: Wine
---

### Post by DeadlyOats on 2010-08-01
I installed Wine [COLOR="Red"]version 1.0.1-0ubuntu8[/COLOR] on my Ubuntu [COLOR="Red"]version 9.10[/COLOR].  Then I installed Cisco Packet Tracer [COLOR="Red"]5.3[/COLOR] from my usb flash drive.

When I start Packet Tracer, it goes through its start up routine, displaying the start up splash screen normally, but as soon as I get the application window, it immediately shuts down.  An error message dialogue box opens at the same instance as the application window does, and then the dialogue box and the application window both close.

This happens *SO FAST* , that I can't even try to read what it says in the dialogue box.

I haven't seen anyone express this problem here.  Does anyone know what's happening and how I might be able to fix this problem?

Thanks for reading my request for help.

Update:

I tried doing a print screen to see what the dialogue box says.  It didn't come out clearly, but what it seemed to say was to this effect: "Cisco Packet Tracer 5.3 stopped working unexpectedly."  Then, even harder to read... something about attaching a log of some kind and sending it to some bug report somewhere.

If more details are needed, what details do you need?

---

### Post by asdfoo on 2010-08-02
> **DeadlyOats said:**
> I installed Wine [COLOR="Red"]version 1.0.1-0ubuntu8[/COLOR] on my Ubuntu [COLOR="Red"]version 9.10[/COLOR].  Then I installed Cisco Packet Tracer [COLOR="Red"]5.3[/COLOR] from my usb flash drive.

When I start Packet Tracer, it goes through its start up routine, displaying the start up splash screen normally, but as soon as I get the application window, it immediately shuts down.  An error message dialogue box opens at the same instance as the application window does, and then the dialogue box and the application window both close.

This happens *SO FAST* , that I can't even try to read what it says in the dialogue box.

I haven't seen anyone express this problem here.  Does anyone know what's happening and how I might be able to fix this problem?

Thanks for reading my request for help.

Update:

I tried doing a print screen to see what the dialogue box says.  It didn't come out clearly, but what it seemed to say was to this effect: "Cisco Packet Tracer 5.3 stopped working unexpectedly."  Then, even harder to read... something about attaching a log of some kind and sending it to some bug report somewhere.

If more details are needed, what details do you need?

goto winehq.org and install wine 1.3.0, the version you have is 2+ years old.

ps. any reason you're not using wireshark?

---

### Post by DeadlyOats on 2010-08-02
Cisco Packet Tracer 5.3 is a router and switch simulator.  It is used to practice setting up cisco routers and switches using cisco's proprietary IOS.

Can Wireshark do that?

I wonder why Ubuntu doesn't offer the latest version of Wine in its repositories.  That could be looked upon as a failure to keep up to date packages for their repositories...  In fact, that is a failure.

Am I wrong?

UPDATE:

DeadlyOats - FAIL!!

There *_is_* a Wine 1.2 in the repositories after all.

Final score: Ubuntu - 1 / DeadlyOats - 0.

I uninstalled the older version of Wine, and then deleted the .wine folder from my home folder - to be safe.

Then with synaptic package manager, installed wine 1.2.

Instead of double clicking on the .exe file, in my flash drive, to install packet tracer 5.3, I right clicked it and chose to "open with Wine...." from the context menu.  I read somewhere that there was a bug related to double clicking .exe files.  I didn't know if that applied to wine 1.2, so I just played it safe...

Packet Tracer 5.3 works great!

Thanks for your help.

---

