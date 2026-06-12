---
title: "AVG for Linux - need simple instructions"
date: 2009-08-15
forum: Security
---

### Post by ed-koala on 2009-08-15
Hello.  I'm trying to find out if my Wine directory (or anywhere else for that matter) has picked up a keylogger/trojan/whatever.  I downloaded AVG for Linux, but I can't find a simple explanation anywhere of how to scan for a virus.

I am guessing you use the avgscan command in terminal, that much I have found.  Can anyone please give me a simple explanation of what to type to make sure I'm actually scanning everything?  Typing just avgscan seems to do something .. there is a pause, and then I get the command prompt ... no explanation of what, if anything, got done, or found/not found.

You'd think somewhere there would be a step by step guide, but there isn't.

---

### Post by ajgreeny on 2009-08-15
I've never used avg on linux, but it was my prefered choice in WinXP when I used that.  However, as a general rule, if you issue a command in terminal, and the terminal returns to the command prompt with no errors showing, then it has been carried out and there is nothing to report, ie, in your case, no viruses or malware found.

There may be a switch to show you output as the comand is happening, often -v (verbose), so have a look at man avgscan in terminal for more info.  This will also give a lot more info on how to use avgscan and the options available.

---

### Post by ed-koala on 2009-08-15
I've looked at the manual, and it is a bit simpler so helps ... some.  I'm still confused as to what the program is doing though. It does not seem to be taking enough time to do a scan of all files, and no matter what verbose setting, no result code appears.

I've tried the -o (report clean files also), -r (save report to file, which only gives some error or gives an empty file), and -d (verbose, does nothing noticable).

Can anyone help me?  All I want is to know a scan has been done, all files have been scanned, and no virus/problem has been found.  Tell me what to type in to get this please.

Barring help with AVG, can anyone recommend a program that WILL work and do what I want?

---

### Post by malachi1990 on 2009-08-15
The reason why you haven't see any results is probly bc there have not been any infections.  As I recall, AVG only displays code if it finds anything.  Though I may be wrong on this point.

The reason why it's not taking a long time can be traced to two possibilities: 

1: linux is faster than windows (most of the time)

2: AVG is only scanning your home directory, and not your system files.    

The AVG for linux isn't the best one to use, as it requires kernel modules that dont always behave, and if those modules don't properly load, you have no antivirus.  

If you really want AV software for linux, try ClamAV. It has a "scan directory" button, and it's pretty good overall.  The only catch is that you have to tell it to auto-delete infected files in the settings.  The only real problem is that (at least in intrepid ibex, I haven't used a more recent linux version) it sometimes appears to freeze when it scans.

---

### Post by ajgreeny on 2009-08-16
Yes, as malachi1990 says, install and try try clamav, or if you must have a gui clamtk.  Run the command ```
clamscan -ri
``` or ```
clamscan -vri
```for a full verbose output, though the latter may well mean that the output is far too long for all to appear in the terminal buffer, so -ri is probably best.  That will recursively scan your /home folder by default, and just show infected files, if any.  If none it will simply drop back to your command prompt.

---

### Post by HermanAB on 2009-08-16
Howdy,

I sincerely doubt that you have a WINE virus.  As mentioned above, your best bet is ClamAV, but it is extremely unlikely that it will find anything.  If you have a problem with your system then it is most likely something rather more mundane than a virus.

---

