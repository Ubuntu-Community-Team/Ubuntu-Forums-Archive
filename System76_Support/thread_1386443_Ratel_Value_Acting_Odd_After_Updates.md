---
title: "Ratel Value Acting Odd After Updates"
date: 2010-01-20
forum: System76 Support
---

### Post by Teasdale on 2010-01-20
I installed the updates and now the monitor display is shaky and looks like it's vibrating. Also, the mouse isn't as reliable. It doesn't always highlight where I expect, it doesn't always resize windows, and using the sidebar on the window border to go up and down pages isn't very predictable. When I click to open a new window (for any program), I sometimes get two windows, as if I had double clicked. And the right click button sometimes doesn't do anything. This all started this morning when I installed the updates. I've restarted three times, but it's doing the same thing.

I have a Ratel Value and it's running Ubuntu 9.04 (Jaunty Jackalope) 64 Bit Linux.

---

### Post by thomasaaron on 2010-01-21
What kind of graphics card do you have in your Ratel?
And have you enabled the driver for it in Hardware Drivers?

---

### Post by Teasdale on 2010-01-21
I think this is the graphics card:
VGA compatible controller 82G33/G31 Express Integrated Graphics Controller

It's the card that was originally installed; I haven't changed anything since I received the computer.

I have not enabled it; I restarted the PC in recovery mode last night and then let it start up normally and it seems to be fine at the moment. It must be that it's not picking up something sometimes at start-up. I remember it being wavy/shaky once before, months ago, so I restarted it and it was fine, so I didn't think anything of it. This is the computer that will freeze up once in a while, and you once mentioned something with the graphics card.

---

### Post by thomasaaron on 2010-01-21
Hi,

That line about the integrated graphics controller will show up regardless of whether or not a discreet graphics card is installed. So, I'm wondering if you ordered the machine with an nVidia or ATI card.

Can you please send an email to [email]support@system76.com[/email] with either your order number or name so that I can look up your account?

Also, reference the URL for this post in the email, and I'll respond back here with the card type (if there is one) so that we can figure this one out.

---

### Post by thomasaaron on 2010-02-01
OK, thanks. You have integrated Intel graphics. So, I doubt that has anything to do with your problem. 

It kind of sounds, though, like Ubuntu isn't syncing correctly with your monitor.  Does your *monitor* have a menu item for *auto-adjust*?

And what kind of monitor do you have (brand and model)?

Finally, if you go to System > Preferences > Display, what resolution is it showing, and what refresh rates is it using?

---

### Post by Teasdale on 2010-02-01
My monitor is a ProView 700P
There is an auto button, so I clicked it just now and it made everything a bit grayer.

Refresh rate is 75 Hz
Resolution is 1280 x 1024 (5:4)

I tried changing them a week ago when I posted this, and every change was worse, not better. 

At the moment, the display is stable and not vibrating. The last restart a week ago made it stop shaking, although the top and bottom toolbars on the desktop are "off." The display seems to think they're shorter than they really are, so almost everything is squeezed to the left. But I haven't wanted to restart it again -- squished toolbars is an acceptable trade-off to headaches from a shaky display. ;)

I don't know if this helps, but when I click the "Menu/Enter" button at the bottom of the monitor, the little box that pops up says;

1280 x 1024
H: 79.5KHZ  V: 74.6HZ

---

### Post by thomasaaron on 2010-02-02
Well, that looks like Ubuntu is reading the monitors specs correctly anyway. So, that's good.

Have you checked to make sure your monitor's cables are connected tightly, both at the monitor and at the computer?

Have you tried using a different monitor to see if you have issues with it?

Another good thing to try would be booting from a 9.10 64-bit live CD to see if you get the same problem. If you do, then the issue probably is either with Ubuntu or your graphics card. If not, it's most likely a monitor issue.

---

