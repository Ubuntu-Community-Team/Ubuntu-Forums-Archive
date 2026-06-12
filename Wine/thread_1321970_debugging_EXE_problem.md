---
title: "debugging EXE problem"
date: 2009-11-10
forum: Wine
---

### Post by McWeirdo on 2009-11-10
Hello , I'm trying to debug an .exe , its not a program or anything just an .exe that demands password and etc, i think you know what i mean...
anyway , I really prefer working at linux, and i'm trying to overcome a problem:

I am using Kdbg(tried with xxgdb but it has another problem) and this is the error I get upon execution of the exe through Kdbg :
Warning: GDB failed to set controlling terminal:operation not permitted wine: '/hope/username' is not owned by you,refusing to create a configuration directory there .
I'm running kgdb from terminal with sudo.

I really need help on this one,
Thank You,

MCW.:p


more info:
wine version 1.0.1
ubuntu 9.10

---

### Post by beastrace91 on 2009-11-10
Run the file as your normal user (drop the sudo) - it should fix the issue. Also regarding issues you might have when running exes with Wine - always be sure to try updating to the latest release (as of typing this it is 1.1.32)

Cheers,
~Jeff

---

### Post by McWeirdo on 2009-11-10
Hi jeff,
Thank you for your reply.
First of all, I can't update Wine and I don;t know why, I installed it through synapyic package manager,and searched and google how to update, so far nothing has worked.

about the debugging, without running on sudo i get a different message:"operation not permitted ..............could not find dependent assembly L"microsoft.vc90.crt" and it says it didnt found another library that is needed

any idea what's wrong?

Thank You,
MCW

---

### Post by beastrace91 on 2009-11-10
Ahh my fault typically I link to [how to update Wine to the latest version](http://www.winehq.org/download/deb) but I was in a hurry when I responded to your above post. Be sure to update Wine!

Also regarding the file issue you list it giving you I did a few quick searches and it appears to be linked to M$ VC - try installing the package from [here](http://www.microsoft.com/downloads/details.aspx?familyid=9B2DA534-3E03-4391-8A4D-074B9F2BC1BF&displaylang=en) (with Wine) and see if that remedies the error.

Regards,
~Jeff

---

### Post by McWeirdo on 2009-11-11
Awesome!!
It worked!!!! updated and installed MS VC and now everything is fine.
I just have problems with the debugger,but that has nothing to do with wine, when i load an exe (using kdbg) it doesn't show me the code, just runs it, 2 bad I can't find a normal debugger like ollydbg XD

Thanks for your help Jeff!!
Helped me  a lot.

MCW

---

### Post by beastrace91 on 2009-11-11
Most excellent, glad you got it working.

~Jeff

---

