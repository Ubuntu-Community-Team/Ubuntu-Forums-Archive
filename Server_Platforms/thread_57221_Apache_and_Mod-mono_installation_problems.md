---
title: "Apache and Mod-mono installation problems"
date: 2005-08-15
forum: Server Platforms
---

### Post by dmccarney on 2005-08-15
Hello, 

I'm not sure if this is the best place to be posting this but here we go anyway...
I've been following the instructions at [http://www.codeproject.com/cpnet/introtomono2.asp](http://www.codeproject.com/cpnet/introtomono2.asp) in hopes of running apache and mod-mono to server ASP.net pages. 

I've managed to get to the point where I'm compiling mod-mono but for some reason it seems to think I have Apache 1.3 installed when I really have Apache2 installed from Synaptic. 

This is the last output I get from running ./configure --prefix=/usr

---
Configuration summary for mod_mono

   * Installation prefix = /usr
   * Apache version = 1.3
   * Apache modules directory = /usr/lib/apache/1.3
   * apxs = /usr/bin/apxs
   * Verbose logging (debug) = no
   * mono prefix = /usr
   * Default MonoApplicationsConfigDir = /etc/apache/mod-mono-applications

---
 
Needless to say if I continue and compile it ends up not working because as near as I can tell it is putting files in the wrong place and aimed at the wrong version of Apache. 

If anyone could help I would greatly appreciate it. If I haven't provided enough information please let me know and I'll post more.

I already have Mono and XSP working great. 

Thanks

---

### Post by dmccarney on 2005-08-16
Nobody has any idea? Apache 2 is definately the only version of Apache I have installed and it came right from the Ubuntu repo's not from Backports or anything slightly wonky. I don't think I even have multiverse included in my repo's.

I can't quite figure out why it doesn't see Apache2... I've never ever installed Apache 1.3.

Can anyone tell me what the advantage of running V. 2 over V. 1.3 is?

---

### Post by retslig on 2007-04-26
You may fixed your problem by now, however here is a good tutorial that will help you.
[https://help.ubuntu.com/community/ModMono?highlight=%28mod%29%7C%28mono%29](https://help.ubuntu.com/community/ModMono?highlight=%28mod%29%7C%28mono%29)

---

