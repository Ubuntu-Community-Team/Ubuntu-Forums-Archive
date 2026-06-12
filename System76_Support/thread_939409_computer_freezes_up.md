---
title: "computer freezes up"
date: 2008-10-05
forum: System76 Support
---

### Post by johnmata on 2008-10-05
Hi,

I have a System76 system that I recently upgraded to the latest Ubuntu, 8.04.  Ever since the system will freeze up on me at least once per day.

BTW; just after I received the computer I replaced the GeForce video card with a NVidia card to accommodate two monitors. In Ubuntu 7.xxx i never had problems with the NVidia.

Any help is greatly appreciated.  Here is the system spec. [ except for the video card ]

- Operating System: Ubuntu 7.10 (Gutsy Gibbon) Linux
  - Processor: Celeron D 331 2.66 Ghz FSB 533 M
  - Memory: 2 GB - 2 x 1 GB DDR2 667 MHZ
  - Graphics: 128 MB nVidia GeForce 6200LE PCI
  - Hard Drive: 160 GB SATA II 300 Mbps - 7200 R
  - Optical Drive: CD-RW / DVD
  - Second Optical Drive: no second optical drive
  - Wireless: no wireless
  - LCD Monitor: no monitor
  - Speakers: no speakers
  - Floppy Drive: no floppy drive
  - Keyboard and Mouse: no keyboard and mouse
  - Portable Flash Drive: no flash drive
  - Hardware Warranty: 1 Yr. Ltd. Warranty and Technica

---

### Post by darkknight045 on 2008-10-06
Can you tell us the video card you are currently using?

Also, did you **upgrade** or do a **fresh install** of Hardy??  I tried to upgrade my GazP5 to Hardy and everything crashed catastrophically and nothing worked.  I did a fresh install and everything went as smooth as can be.

If it is a fresh install have you tried EnvyNG-gtk?  If not, then I would recommend using that to install the Nvidia drivers.  Let me know if any of this helps.

---

### Post by johnmata on 2008-10-06
I am using:

VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

Also, I did a fresh install, not an upgrade, to Ubuntu 8.04.

I have installed: EnvyNG-gtk.  I ran the tool using, "Install the NVIDIA driver(Automatic Hardware Detection).  Hopefully that will address the problem.

Thanks for the help.

John

---

### Post by thomasaaron on 2008-10-06
> Processor: Celeron D 331 2.66 Ghz FSB 533 M

Exactly which System76 computer do you have?

---

### Post by johnmata on 2008-10-08
Hi,

After trying what is mentioned in the previous post, the problem still persists.  Here is the run down on the System76 I have:

- Operating System: Ubuntu 8.04 (Hardy Heron) Linux
- Processor: Celeron D 331 2.66 Ghz FSB 533 M
- Memory: 2 GB - 2 x 1 GB DDR2 667 MHZ
- Graphics:  nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

What I mean by freezing up is that the mouse pointer will become suspended with everything else on the screen.  I friend suggested the other day that I keep "Top" open so we can get a snapshot at the system resources at the time it freezes up.  I successfully acquired the snapshot and we both agreed that there is nothing abnormal going on there.

Any advice appreciated.

John

---

### Post by thomasaaron on 2008-10-08
According to my records, you have a Ratel Value.

You have a pretty base-level processor in it, so it is possible that it is freezing because it is being overworked.

What programs (and how many programs) are being run when it freezes?

Also, please post your snapshot of top so that I can have a look. If CPU time or memory is running out, top should tell us that.

Finally, take not of the time next time it freezes. When it recovers, run this command...

cat /var/log/messages > ~/Desktop/messages.txt

It will create a file on your desktop that you can email to support(at)system76(dot)com. It is going to be way too long to post on the forum, although you might be able to attach it to the thread.

---

### Post by johnmata on 2008-10-08
I will do what you have suggested and get back with results.  When it freezes I usually only have one or two applications open; like Firefox and Open Office.  Here is a snapshot of the screen image on freeze-up.

[IMG]http://accessdreamland.com/temp/top.JPG[/IMG]

---

### Post by thomasaaron on 2008-10-08
You're right, that top snapshot isn't very useful.

What are you running on Firefox when it freezes? Something with Flash? Gmail? Something with Java Applets?

---

### Post by johnmata on 2008-10-08
i'll try to pay closer attention to what I am using in Firefox when it freezes.  i'll also run the script in the terminal as you requested earlier on boot up.  i'll provide feedback once i have some information.  thanks a lot for your help.  

cheers,
john

---

### Post by johnmata on 2008-10-08
After a freeze up and reboot I ran the requested command in the terminal.  [Click here to download the messages.txt file]("http://accessdreamland.com/temp/messages.txt")

---

### Post by thomasaaron on 2008-10-09
Nothing in there jumps out at me.

It would probably help to know what time it froze (on your system clock) and how long the freeze lasted. Otherwise, it is pretty difficult to isolate it.

Also, what were you doing when it froze that time. Were you on a particluar website or anything?

---

### Post by johnmata on 2008-10-09
Tonight it froze up at, or slightly before, 6:41PM.  Here is a link to the generated message on reboot:  [http://accessdreamland.com/temp/messages.6:41PM.txt]("http://accessdreamland.com/temp/messages.6:41PM.txt")

---

### Post by thomasaaron on 2008-10-10
There's nothing at all in that time frame that would indicate a problem. So, I'm almost certain it is a process gone awry and is basically hogging your cpu. I'm not sure why it is not showing up on top, unless top is basically just freezing too and not accurately revealing the problem.

You have a fairly low-end CPU, so it wouldn't take a whole lot to clog it up.

What were you doing at the time?

Try disabling desktop effects (System > Prefs > Appearance > Visual Effects > None) and see if the freeze happens again.

---

### Post by johnmata on 2008-10-10
Perhaps I should look into upgrading the CPU then.  I am not sure if the mother board can take a faster one.  

I the only thing that I ever have open when it freezes is Firefox.  As an experiment, I left the computer on with no applications running this morning.

I'll check the settings as you mentioned too.

Thanks,
John

---

### Post by thomasaaron on 2008-10-10
Well, just firefox shouldn't freeze up any cpu. Unless there is some content on that page that is causing problems. Flash? Java Applet?

So, it is probably some background process running. Right now, I'm betting compiz. Disabling desktop effects will take that out of play.

---

### Post by johnmata on 2008-10-13
Yesterday morning I reinstalled Ubuntu 8.10.  Since the reinstall the computer has not frozen.  Weird.

Thanks for all the support on this!

Cheers,
John

---

