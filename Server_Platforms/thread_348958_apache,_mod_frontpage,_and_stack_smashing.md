---
title: "apache, mod_frontpage, and stack smashing"
date: 2007-01-29
forum: Server Platforms
---

### Post by Staceman on 2007-01-29
I've run into a problem on an Ubuntu Edgy server install. I'm in the process of replacing an aging domain hosting server. The old machine is RedHat 9, with Apache 2.0.x, PHP, mod_perl, and the Microsoft FrontPage Server Extensions for Linux. It ran fine for quite some time.

I opted to go with Ubuntu on the new machine. Everything went fine, except for the FPSE module. Anytime a FrontPage-enabled site is accessed either from a web browser, or from FrontPage 2003, a "*** stack smashing detected ***" error appears in the apache error log, indicating that it's terminating the offending process. The site displays fine in a browser, but gives an error in the FP client.

I removed all Ubuntu default apache packages, and thought compiling from source would do the trick. Same error. I did some more research, and discovered that the stack smashing protection can be shut off at compile time. I tried adding "-fno-stack-protector" to many different places in my configure line, and in the make line, using CC, CFLAGS, CPPFLAGS, etc, all to no avail. Regardless of how I manage to get that option passed to gcc, the option indeed does appear in the output of make, but it doesn't seem to make any difference whatsoever, as I still get the same errors/crashes in my logs when accessing the site. Another option, "-fno-stack-protector-all", would logically seem to be a better choice, but alas, the version of gcc that Edgy has, doesn't recognize that particular option.

I realize that M$ EOL'd the FPSE module for apache last year. However, I *must* have the FPSE enabled on this new server. I'm about to wipe it out and try it with Fedora Core 6. I just figured I'd post my problem here, in case anyone else has seen the same thing, and perhaps has some advice.

Thanks!

---

