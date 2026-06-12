---
title: "Howto for remote desktop??"
date: 2008-08-29
forum: Server Platforms
---

### Post by tmcmulli on 2008-08-29
Looking for a way to resume sessions on my Ubuntu 8.04 Server.  I have some processes that need to run for a few hours, and I want to start them and close the session, but not the job.  Usually use VNC, but this is my first foray into a no-GUI environment...

If someone could point the way, I'd appreciate it!

Thanks!

---

### Post by Vegan on 2008-08-29
I'm only familiar with old mainframes using MTS and JCL being able to run long running processes. With Linux et al, you need to maintain your terminal window open. It will shut down processes if you close it.

On MTS, running a program name with the $ after it will make it run til it is done. No good on Linux.

One idea is to log in on the server console and run it there where the machine is secure.

Putting the job is a shell script with a logout command would be achieve a nominal solution.

---

### Post by Mister.Vash on 2008-08-29
You'll probably want to use the program called screen

This is the first one I found searching for a how to on the forums
[http://ubuntuforums.org/showthread.php?t=492832](http://ubuntuforums.org/showthread.php?t=492832)

You can also find other tutorials  on it if you search google for 'unix screen' or 'linux screen'

---

### Post by inteluser on 2008-08-29
I second the mention of screen, although **nohup** and **disown** are also options.

---

