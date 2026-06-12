---
title: "Execute Command When Server is Shut Down or Started?"
date: 2012-08-29
forum: Server Platforms
---

### Post by jlacroix on 2012-08-29
I tried searching for this but maybe my Google skills suck today. 

Anyway, I want the server to email me when it is going down for a graceful shutdown. I also want it to email me when it is started. 

I can handle writing the actual email scripts for both events, I don't need help with that. I just need to know where to tell Ubuntu to execute such a script on shut down and start up.

---

### Post by CharlesA on 2012-08-29
You can always write a startup script to notify you and set it to run before networking goes down.

[http://wiki.debian.org/LSBInitScripts/](http://wiki.debian.org/LSBInitScripts/)

---

### Post by Lars Noodén on 2012-08-29
You could make an upstart script or system v script and set it to run after the network is brought up or before it is shutdown.  For the upstart scripts see [font=Courier New]/etc/init/[/font].  For the System V scripts see [update-rc.d](http://manpages.ubuntu.com/manpages/precise/en/man8/update-rc.d.8.html).  I think System V is deprecated but for me it is more clear.

Alternately, you can put a pair of scripts in [font=Courier New]/etc/network/if-up.d/[/font] and [font=Courier New]/etc/network/if-down.d/[/font].

---

### Post by CharlesA on 2012-08-29
> **Lars Noodén said:**
> You could make an upstart script or system v script and set it to run after the network is brought up or before it is shutdown.  For the upstart scripts see [font=Courier New]/etc/init/[/font].  For the System V scripts see [update-rc.d](http://manpages.ubuntu.com/manpages/precise/en/man8/update-rc.d.8.html).  I think System V is deprecated but for me it is more clear.

Not to be totally offtopic, but I wrote the startup script I use with VirtualBox in System V, because I had a hell of a time wrapping my head around upstart. System-V seems more intuitive to me.

---

### Post by jlacroix on 2012-08-29
Wow, it looks like those solutions may be a bit over my head. I know how to write BASH scripts fairly well. I was hoping to write a script for shutdown and one for startup and put them somewhere and have them run accordingly. I'm not sure I want to tie such scripts to the network, just in case my network goes down I don't mistakenly think my server has shut down.

---

### Post by Lars Noodén on 2012-08-29
Well, the new way, Upstart, seems harder and less straight forward.  I have to practice with them still.

The old way, System V, still works and is just a matter of writing a plain shell script and then running a program (update-rc.d) to install it.  You can look at several of the scripts in [font=Courier New]/etc/init.d/[/font] to get an idea of how it's done.  I'd say look at several to find a simple one.  It's not hard if you already have the script.  Here's a template:

[http://www.cyberciti.biz/tips/linux-write-sys-v-init-script-to-start-stop-service.html](http://www.cyberciti.biz/tips/linux-write-sys-v-init-script-to-start-stop-service.html)

---

### Post by thnewguy on 2012-08-29
For start up, you could simply copy/paste your script into /etc/rc.local Commands in this file get run after everything else is brought up. It will be the last set of commands executed during start-up.

As for shutdown, if you aren't comfortable working with Upstart you could probably do something like alias the poweroff command to run your script and then shutdown the system.

---

### Post by jlacroix on 2012-08-29
I have an APC UPS with a working apcupsd configuration, is there a way to use that? I Googled around for a way to do it, but I don't see how. I have it emailing me when the power goes down, but I don't see an option in the config to make it email when the server shuts down, unless I missed it. Perhaps that's a possibility?

---

### Post by CharlesA on 2012-08-29
That wouldn't work for normal shutdowns.

---

### Post by Bachstelze on 2012-08-29
IIRC putting a script in /etc/rc0.d/ will make it execute at shutdown (when entering runlevel 0). Another option for running it at boot is to have a @reboot crontab line for it (see crontab(5)).

*EDIT:* I just tried, seems to do the trick.

---

