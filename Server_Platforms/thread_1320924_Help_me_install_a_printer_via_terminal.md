---
title: "Help me install a printer via terminal"
date: 2009-11-09
forum: Server Platforms
---

### Post by mendo on 2009-11-09
i have a new ubuntu server that i'm trying to set up so that i can share a printer on a small home network.  i don't know how to install the printer on the server.

so far, i've obtained what i believe to be the proper driver package and copied it to a directory on the server.  it was originally an .rpm file and i used alien to convert it to a .deb file.  and there it sits.  i have no idea what to do next.  i'm not even convinced i did the .rpm to .deb conversion properly b/c it said that it didn't convert scripts.

what say you, linux masterminds?

if i've got the driver in the proper format, what next?  there's no double-clicking or install button to click, so i'm pretty much lost.

if it matters, the printer is a canon pixma mp160.

thanks in advance.

---

### Post by BQAggie2006 on 2009-11-09
To install the .deb file, you need to run the command:

```
sudo dpkg -i <filename>
```

---

### Post by Girya on 2009-11-09
> **mendo said:**
> i have a new ubuntu server that i'm trying to set up so that i can share a printer on a small home network.  i don't know how to install the printer on the server.

so far, i've obtained what i believe to be the proper driver package and copied it to a directory on the server.  it was originally an .rpm file and i used alien to convert it to a .deb file.  and there it sits.  i have no idea what to do next.  i'm not even convinced i did the .rpm to .deb conversion properly b/c it said that it didn't convert scripts.

what say you, linux masterminds?

if i've got the driver in the proper format, what next?  there's no double-clicking or install button to click, so i'm pretty much lost.

if it matters, the printer is a canon pixma mp160.

thanks in advance.

Look at installing CUPS then you can set the printer up through the CUPS web interface.

[http://ubuntuforums.org/showthread.php?p=1831119]("http://ubuntuforums.org/showthread.php?p=1831119")

---

### Post by mendo on 2009-11-10
i used alien again to recreate the .deb package, this time including scripts and installed it.

i don't know how to test the printer locally, let alone remotely through cups.

i followed the how-to on how to setup cups for remote administration, but can't get the web interface up on a remote machine.

is there a way to print something directly from the server just to test that the drivers are good?

if the drivers aren't working, there's no use to worrying about cups.

---

### Post by mendo on 2009-11-10
can anyone provide a checklist of things to check so that i might figure out where i'm wrong with this cups thing?

i'm totally lost and keep going over the same google results re: setting up cups/installing printers/sharing a printer/etc.

---

### Post by mendo on 2009-11-11
thanks to girya, i explored the cups web interface and was able to print something today!!!!

after using alien to re-convert the .rpm driver package for the canon pixma mp160, this time including scripts, i installed the resulting .deb package.

i had no idea if this worked b/c i didn't know how to test it.

then i got on to cups.  i could not get the web interface for cups to work from either of my winxp machines.  i booted my dual-boot winxp/ubuntu 9.10 desktop machine into ubuntu and was able to access the cups web interface, though i was not able to access any of the administration pages.

i read about managing operation policies for my version of cups (1.3) here:  [http://www.cups.org/documentation.php/doc-1.3/policies.html](http://www.cups.org/documentation.php/doc-1.3/policies.html)  and decided to try adding "Allow from all" to every section of the cupsd.conf file.  i restarted cups and it worked from my ubuntu and my winxp machines.  i was now able to strart my printer and allow jobs.  i tried to print and it worked.  that's as far as i got before i wanted to share this info.

now i will have to go back and try to secure this printer a little bit b/c i'm sure that by adding 'allow from all' to all the sections, i have created the world's most vulnerable printer.

this was a major pain in the *** and i know that this is not the most desired fix, but it is a fix and i hope it helps someone else.

thanks to those of you that took a minute to point me in the right direction.

---

### Post by mendo on 2009-11-11
well, f that.  it worked for a minute, then i managed to break it somehow.

i figured out what broke cups - for some reason, using the web interface to configure cups re-wrote the cupsd.conf to the point where i could no longer connect via browser.

---

### Post by mendo on 2009-11-11
not that anybody's reading this except me anymore, but here's what i did to get it operational again:

copied my backup cupsd.conf.original file to cupsd.conf to get a fresh start.  then i added "from allow all" to one section of the cupsd.conf file until i could access all the pages of the web interface for cups from my winxp machines.  after i figured out which ones were necessary to give me access to all the pages, i replace "allow from all" with " allow from 192.168.1.* to restrict access to these pages to machines on my network, but i'm not sure that makes it any more secure than "allow from all."

the bare minimum sections that must have this entry are:

Location /
Location /admin

I guess that makes sense.

coincidentally, the "print test page" button doesn't work from cups, but once i add the printer on my winxp machines, i can print test pages from there.  does that mean something's screwed up?

---

