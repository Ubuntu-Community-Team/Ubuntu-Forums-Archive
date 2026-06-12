---
title: "mainframe emulator in Ubuntu"
date: 2013-09-10
forum: Server Platforms
---

### Post by squakie on 2013-09-10
I've got no clue where to post this:

I've been thinking of trying one of the mainframe emulators to see how things from back then actually run in emulation within Linux.  One I've noticed in particular, because of the IBM images it can run, is Hercules, and a derivative that looks like the 380.

Anyone have any experience installing this in Ubuntu and using it in Ubuntu?

---

### Post by squakie on 2013-09-16
No one?  I guess I'll have to try this on my own and hope I don't screw up my ubuntu installation.

---

### Post by mikechant on 2013-09-19
I got this working a few years back, got MVS 3.8 up and running, it wasn't too difficult. Don't think there's any real risk of messing up your install, it's just another application as far as Ubuntu's concerned.
I referred to this site: [http://www.bsp-gmbh.com/turnkey/](http://www.bsp-gmbh.com/turnkey/)

Note that MVS 3.8 is the most recent version which is free to use without an IBM license. Anything more up to date you have to have a suitable license.

---

### Post by mikechant on 2013-09-19
Deleted.

---

### Post by squakie on 2013-09-19
Thanks mikechant.  I assume it's just the bare OS - that things like CICS, language compilers, certain file systems support are still add-ons (and probably still pay to use), correct?

---

### Post by mikechant on 2013-09-20
>  I assume it's just the bare OS

It's more than the bare OS. You get TSO, JES2, all dataset types (of that era) supported including VSAM**, 3270 terminal support (via BTAM/TCAM) and you get the Assembler and the MVT COBOL compiler (i.e. very old COBOL, maybe 1968 standard). I managed to log on to TSO from a 3270 emulator, and compile and run a Batch COBOL program.

You don't get RACF, ISPF, CICS, Databases etc.

I also forgot to mention that the 'turnkey' system at the above link includes the Hercules emulator and a 3270 terminal emulator so you don't need to install these separately.

**The system supports VSAM (e.g. in ASM progs) but COBOL does not support it direclty, there's a workaround.

Anyhow, this is all documented on the 'turnkey' website.

---

### Post by squakie on 2013-09-20
thanks!

---

