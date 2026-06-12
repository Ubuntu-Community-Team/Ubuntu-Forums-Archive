---
title: "Application time."
date: 2009-06-25
forum: Server Platforms
---

### Post by Grenage on 2009-06-25
Greetings, and cheers for reading.

I'm having an issue with time on a certain application; the system time is correct (using 'date'), and the hardware clock seems to be fine too (bios and 'hwclock').

When running the application in debug mode it shows that the application is using GMT/UTC rather than BST (GMT/UTC+1).  Does anyone have any ideas on what else I can check, to see exactly where the app is getting it's time from?

For those curious, the application is called 'oreka', and there doesn't appear to be any setting for changing the time in it's config files.

Grenage.

---

### Post by grantemsley on 2009-06-25
Is your system's hardware clock (IE in the BIOS) set to local or GMT time?

You can tell ubuntu which it is by editing the UTC line in/etc/default/rcS if it is wrong.

I found that some programs look in the wrong place for timezone data, since it used to be in a different place on some linux distros.  Try this command: "sudo ln -s /usr/share/zoneinfo /usr/lib/zoneinfo" which will make a link from the old place to the new one.

---

### Post by Grenage on 2009-06-25
UTC was set to yes under that config, so that is very promising.  I've made the change and will reboot as soon as I can.

Thanks a lot for your help.

EDIT:

Alas, no dice.  Not sure what's going on with this program!

---

### Post by grantemsley on 2009-06-25
Did you try making that link with the command I posted?

Edit:

Also try from a console window:
"export TZ=America/Los_Angeles" (replace that with whatever timezone is listed in /etc/timezone)
then run your program from that window.

---

### Post by Grenage on 2009-06-25
Hey there, thank you again for your reply.

I did as you suggested (what exactly does exporting the TZ do?), but unfortunately to no avail.  I'm beginning to suspect it's the program alone that's refusing to use anything other than UTC.  Odd, because it ran ok on the old install.

---

### Post by grantemsley on 2009-06-25
export TZ sets an environment variable that some programs use for the current time zone.

I guess the simplest solution would be to set the hardware clock to UTC instead of local time, and set UTC=yes in the file I mentioned earlier.  Properly designed programs should still give you the time in local time that way.

(I don't exactly know if that is the proper way to tell ubuntu that your clock is in UTC...if you have a GUI I'd poke around the clock or time related settings for the proper way to do it).

---

### Post by Grenage on 2009-06-26
Thank you for your help, I will try a few changes here and there and see what happens.  Here's hoping it sorts itself out! :popcorn:

---

