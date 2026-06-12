---
title: "A Virus Has Been Found... Now What?"
date: 2009-09-07
forum: The Cafe
---

### Post by shinkaide on 2009-09-07
Though well aware that Linux is quite virus-proof, I still run scans every now and then with Avast to avoid inadvertently spreading it to other people who use Windows.

On my recent scan, Avast detected the file from ClamAV ```
/var/lib/clamav/daily.cld
``` as a virus (or trojan, rather). I would imagine that's got something to do with ClamAV's own files.

My questions are: 

[LIST=1]
[*]Is it really a virus/trojan?
[*]Avast can't do anything with the file. Would it be dangerous to "sudo rm" the file?
[*]I have WINE installed. Should this concern me, with regard to virus susceptibility?
[/LIST]

I'm reasonably adept at using Linux systems, though sometimes I don't have a complete grasp of how exactly the stuff under the hood works.

---

### Post by dragos240 on 2009-09-07
This post doesn't exist.

---

### Post by XDevHald on 2009-09-07
Modified: See above post

---

### Post by .Maleficus. on 2009-09-07
From what Google tells me, that's Clam's definitions file.  It's not a virus and you shouldn't remove it if you still use Clam.  What you should remove are both of those scanners though - they do you no good under Linux.  Any vulnerability under Linux will patched before virus definitions are out.  You're wasting resources by using those.

---

### Post by shinkaide on 2009-09-07
> **dragos240 said:**
> [Interesting. Let me google that for you.]("http://lmgtfy.com/?q=%2Fvar%2Flib%2Fclamav%2Fdaily.cld")

I have previously tried that and the results weren't of too much help for my specific case (it was clamAV's file). That's why I wanted to ask people who know more than I do, sir.

---

### Post by lswb on 2009-09-07
> **.Maleficus. said:**
> From what Google tells me, that's Clam's definitions file.  It's not a virus and you shouldn't remove it if you still use Clam.  What you should remove are both of those scanners though - they do you no good under Linux.  Any vulnerability under Linux will patched before virus definitions are out.  You're wasting resources by using those.

Using a virus scanner where the linux system is serving files to windows systems is a valid use case.

---

### Post by shinkaide on 2009-09-07
> **.Maleficus. said:**
> From what Google tells me, that's Clam's definitions file.  It's not a virus and you shouldn't remove it if you still use Clam.  What you should remove are both of those scanners though - they do you no good under Linux.  Any vulnerability under Linux will patched before virus definitions are out.  You're wasting resources by using those.

Thanks!

---

### Post by misfitpierce on 2009-09-07
> **lswb said:**
> Using a virus scanner where the linux system is serving files to windows systems is a valid use case.

Indeed but thats about it.

---

### Post by cariboo on 2009-09-07
> **lswb said:**
> Using a virus scanner where the linux system is serving files to windows systems is a valid use case.

Why are you serving files to Windows systems without an av scanner?

---

### Post by calrogman on 2009-09-07
> **lswb said:**
> Using a virus scanner where the linux system is serving files to windows systems is a valid use case.

Also, mail servers.  You should always scan mail servers you know are (or don't know aren't) going to be used by Windows users (and increasingly so, Mac OS users).

---

### Post by thisllub on 2009-09-07
It is also essential on a dual boot system.
When the inevitable virus attack hits the Windows partition at least the virus can be identified and possibly repaired.

I have removed viruses from a few crippled Windows machines this way.

---

