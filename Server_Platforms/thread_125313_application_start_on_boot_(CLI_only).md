---
title: "application start on boot? (CLI only)"
date: 2006-02-03
forum: Server Platforms
---

### Post by ned.b on 2006-02-03
Hi

How do I configure an application to start at boot time?  The only info I can find points towards GUI solutions and I am only running a console.  I  know it has something to do with symbolic links and run levels but I can't quite get my head around that - is there an easy way?

---

### Post by Stereotypical Rage on 2006-02-03
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

It deals with: sysv-rc-conf

I've been playing with this and BUM(GUI)

/etc/rcX.d (X==Runlevel), that's as far as I know.

---

### Post by Iowan on 2006-02-03
Maybe there's an easier way, but building a S##name script to start the application, and a corresponding K##name to shut it down stashed in the rc# area of init.d seems the most straightforward... this coming from someone who knows not of what they speak.  ;)

---

### Post by seakiwi on 2006-02-03
Check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=122529](http://www.ubuntuforums.org/showthread.php?t=122529)

The suggestion from adwait worked for me. Note that he has a typo in his first post - should read "rcconf" not "rccoonf".  Read both his posts first as you may need to start the rcconf service first, same as I did.

Works perfectly for getting Boinc to start at boot but I haven't tried it with anything else. 

Hope that helps  :)

---

### Post by ned.b on 2006-02-04
Thanks for the pointers :) 

I will have a play around and see which works best for me

---

### Post by ned.b on 2006-02-04
Hmm rcconf worked - kind of...  it started the application but then that application seemed to own the machine to such an extent that nothing would respond - I had to pull the power to get it to stop and when I restarted in recovery mode the application still took over - fortunately I managed to rcconf the app out of startup before it took over.  That puts me back at square one for the moment, I think I will bite the bullet and look into the S## K## scripts - anyone seen a good Ubuntu/Debian howto?

---

