---
title: "Print jobs automatically cancelled (CUPS)"
date: 2006-01-14
forum: Server Platforms
---

### Post by karih on 2006-01-14
Hello,

I have been struggling for a while to get a printer to work with my server.  I installed cupsys and modified the config file to gain access to the web interface from other computer.  After finding a driver for my printer in the cupsys-driver-gimpprint package (Printer is Canon i965; used driver BJC-8200) i tried printing some files but nothing happened and the "show completed jobs" just showed:
```
 	Canon-21   	Test Page   	   	15k   	 cancelled at
Sat 14 Jan 2006 06:04:47 PM GMT 
```
So it seems that all jobs are automatically cancelled.  I have tried reinstalling a few times and nothing works and I don't have a clue what to do.  I have got this printer working with my other Ubuntu computer which had Gnome and it's printing interface.

Any help is very much appreciated!

---

### Post by ari.maidana on 2006-05-16
I have exactly the same problem with an EPSON Stylus C43 UX. Every job I send is automatically and immediately shown as cancelled in the CUPS web interphase. I'm using Kubuntu 5.10, with KDE 3.5.2.
I will appreciate a lot any help with this issue!

---

### Post by ari.maidana on 2006-05-19
Problem solved!
I looked in [FONT="System"]/var/log/cups/error_log[/FONT] after trying to print and got this messages:

```
I [19/May/2006:01:03:36 -0300] Job 19 queued on 'C43UX' by 'ariel'.
E [19/May/2006:01:03:36 -0300] Unable to convert file 0 to printable format for job 19!
I [19/May/2006:01:03:36 -0300] Hint: Do you have ESP Ghostscript installed?
I [19/May/2006:01:03:36 -0300] Hint: Try setting the LogLevel to "debug".
```

So I installed ESP Ghostcript ([FONT="System"]sudo apt-get install gs-esp[/FONT]), restarted my cups server ([FONT="System"]sudo /etc/init.d cups restart[/FONT])

Then I sent a test page (from the Printers Kcontrol module) and bingo! it worked. :-D

---

