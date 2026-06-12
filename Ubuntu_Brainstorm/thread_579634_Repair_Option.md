---
title: "Repair Option"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by SteveHillier on 2007-10-18
Don't get me wrong, of all the Linux distributions I have used Ubuntu is by far the best, but.....
Today I had a graphics card pack up.  So off with the side of the box, drop in a new graphics card and reboot.
Sorry, cannot load graphical interface - text logon only allowed.  Message pops up to look at /var/log/xorg.0/log to see what went wrong and go to /etc/X11/xorg.conf to fix.
Great, I find nothing of use in the log and the config file - well which bits can I change.  I don't know because I have never had to do it.  There is a bit about a device that lists my old graphics so try to use vi to edit file - even if just to comment out that section and see what happens.
Nothing - still getting text interface. 
OK, so lets get the boot disk and see what options there are for repairing the graphics card stuff.  None.  Ok lets look at the xorg.conf on the 'live' version and cut and paste the graphics card stuff into the old conf file.  Reboot - text interface.
OK, lets go round the loop again but this time carry the whole conf file across and see what happens.  Reboot - text interface.
Right, lets try running install and see if we can reinstall the bits we are interested in and leave the rest of the disk and user data intact.  Oh no!  Cannot do that.  There is no repair option in the list, no partial install, no check to see what is missing and fix it.  Only a complete new install.  The problem with this is I now loose all my user data, all my links and everything else I have spent 2 months setting up.

Now, that other operating system that so many people on this forum berate does actually have a repair function (no two repair functions) in it's install procedure.  I have used both on many occcasions.  The second one is a bit of pain because it goes through the 39 minute install process and simply rips of all the system file and replaces them (which is not 100% effective in all situations).
On that other well known OS if I change a graphics card it will rise from its ashes and allow me to install new drivers should I wish.  So why can't I do that on Ubuntu?
Neither of my graphics cards were cutting edge.  the old one was an MX400 the replacement a Radeon 9250.  I don't expect to have to understand the parameters needed to make either of these run nor where to configure them.  If this were a cutting edge card where I might reasonably expect that the card had not been incorporated into the standard release I might expect to have to learn how to install it but that would be my problem to sort out.  Both the cards I have are known to the system otherwise they would not install in the normal setup.

So my request would be is it possible for a (graphical) repair function to be added to the setup process which would allow me (us) to rebuild a system without destroying users and their data.  Luckily for me whis was my machine not one I had sold to someone else with a recommendation to use Ubuntu.

The version I have on this machine is 7.04, x86 desktop.  Celeron 2.80 with 1Gb RAM and 80Gb HDD.

I don't expect an answer to the problem, however I expect I will get a number of replies!!

I'm off to play some loud music!!!

---

### Post by Lord Illidan on 2007-10-18
If you were using 7.10, replacing a Graphics card would put X in failsafe mode so you can switch drivers and still be in a GUI.

---

### Post by SteveHillier on 2007-10-18
Thanks for that but what does X look like in failsafe mode?  and is that what I saw when I was given a text only logon prompt?

---

### Post by gaspard.leon on 2007-10-18
The new Failsafe X (in 7.10) is pretty easy, it defaults to using the vesa driver (which works with almost any video card) and lets you pick a video driver.

Pretty much when you re-started and were dropped to a text-prompt, instead you are prompted (using a gui) to install a different graphics driver, or continue with the vesa driver... from there you can upgrade/download new driver from the normal ubuntu interface...

It's pretty slick, I've tested it on the live CD...

don't know what would happen if your hard-drive or other important hardware was changed, so a "Repair" or "Safe mode" function would still be useful in my opinion... however the usual problem with X not starting cause it can't load the graphics card is fixed in 7.10..

Cheers,

Gaspard

---

### Post by Zdravko on 2007-10-19
Hmmm, nice idea. Never thought of it before, though.

---

### Post by JBAlaska on 2007-10-19
When I first upgraded to the RC, My video did a little hiccup and I rebooted, It was graphical..but just not quite right, so I opened xorg.conf...and was like..what manner of maddness is...oh yea this must be bulletproof x...cool.

I renamed my old xorg, restarted x and all was well...VERY COOL!

---

### Post by Zdravko on 2007-10-19
Hmm. I don't want to open that damn file...

---

