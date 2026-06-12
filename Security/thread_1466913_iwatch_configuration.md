---
title: "iwatch configuration"
date: 2010-04-30
forum: Security
---

### Post by jimf8 on 2010-04-30
I am looking for some help configuring iwatch.  Hope I have the right forum.  I am hoping someone has experience with iwatch or suggestions.
I want to monitor my key system folders for changes.  I discovered iwatch but am having trouble configuring it.

I want to monitor more than one folder and local alerts are fine.  I don't need email notification and frankly I was not able to figurre out how to configure the email server on my system.

So using the command line mode is fine and this code, for example, will alert me with a ring sound if there are any changes in the /etc folder tree. 

code:

iwatch -c "canberra-gtk-play --id="phone-incoming-call"" -r /etc

But how to monitor multiple folder trees without running a separate terminal for every folder tree monitored?

I cannot get iwatch to run in deamon mode (iwatch -d).  It simply returns the –help output.

Thank you for all the help that you provide!

BTW I am new to Ubuntu / Linux.  Ubuntu is AWESOME!  I am so glad that I switched away from winblows.  I feel like a political prisoner who has just been set free !!!

---

