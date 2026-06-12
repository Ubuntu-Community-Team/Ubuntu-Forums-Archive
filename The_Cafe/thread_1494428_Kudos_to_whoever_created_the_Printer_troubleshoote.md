---
title: "Kudos to whoever created the Printer troubleshooter"
date: 2010-05-26
forum: The Cafe
---

### Post by rarsa on 2010-05-26
While I was trying to install the drivers for a printer, and after I installed everything as I had done before; my printer icon had an ! (exclamation) mark and when I tried to print it would just give me an error. I decided to press the "diagnose" button not expecting too much out of it. After all, I've never found such a button useful under any MS Windows OS/application.

The wizard gave me some recommendations. It then asked me if I wanted to turn on debug mode. I accepted, tried to print the test page and after that it showed me the CUPS log! There I was able to find the error, Google it and solve my problem.

I was pleasantly surprised. Kudos to the people that figured out how to make a useful wizard.

It would have certainly taken me longer had I had to remember how to turn on debugging and where the log file were.

Cheers. Another thing to be grateful about to the people that contribute to FLOSS.

Have you had other pleasant surprises like this?

---

### Post by Queue29 on 2010-05-26
Yea, this one time, I was setting up Windows 7, and it probed my hardware, searched a repository for WHQL certified drivers, downloaded them, installed them, and all I had to do was.. nothing. Nothing actually, I didn't have to do anything. 

Not to poopoo open source software but c'mon, a dialog box that turns on debugging is pitiful compared to what else is out there. And I wouldn't call that progress either. Progress would be having things work without greping through debug logs, crossing your fingers in hopes of a solution on Google and applying said fix to incomprehensible config files.

I don't give Kudos to whoever created the Printer troubleshooter. It's a bandaid for a broken arm.

---

### Post by chessnerd on 2010-05-26
> **Queue29 said:**
> I don't give Kudos to whoever created the Printer troubleshooter. It's a bandaid for a broken arm.

Patience, my friend. The day will come when we see a truly powerful troubleshooter for hardware issues on Linux.

Well, "we" personally won't see that day, but our children just might!

I think Linux troubleshooting is going places, but you are absolutely right in thinking that it isn't "there" yet. I don't think this is a step in the wrong direction, but I do think that there should be something better by now. Shouldn't there be a way to analyze a device, compare it against some kind of online database, and then direct the user to the proper driver?

---

### Post by cguy on 2010-05-27
> **Queue29 said:**
> Yea, this one time, I was setting up Windows 7, and it probed my hardware, searched a repository for WHQL certified drivers, downloaded them, installed them, and all I had to do was.. nothing. Nothing actually, I didn't have to do anything. 

Not to poopoo open source software but c'mon, a dialog box that turns on debugging is pitiful compared to what else is out there. And I wouldn't call that progress either. Progress would be having things work without greping through debug logs, crossing your fingers in hopes of a solution on Google and applying said fix to incomprehensible config files.

I don't give Kudos to whoever created the Printer troubleshooter. It's a bandaid for a broken arm.
my sister's Windows 7 can't do a few things:
- install a driver for the bluetooth
- simulate mouse scrolling on the touchpad or enabling third button emulation
Can I read logs, modify some config files (whose structure and logic I could understand with a little effort) and make them work?
No!
I can fiddle with the Device Manager and scour the net for alternative drivers, both of which I did for 2 or more hours without succes.
Sometimes, but just sometimes, I can use some incomprehensible commands/registry tweaks and make things work.

With Ubuntu on that very same laptop, the only problem is that the bluetooth doesn't work*, but the fix is one very brief Google search+1 config file editing away.
* on Jaunty; I haven't yet tried running Lucid on it.

And here's how I installed the printer on both Ubuntu and W7: I plugged it in!


The complaints can go both ways, see? As can the good remarks.

---

