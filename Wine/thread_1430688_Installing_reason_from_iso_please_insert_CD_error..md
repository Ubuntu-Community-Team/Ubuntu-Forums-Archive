---
title: "Installing reason from iso: please insert CD error."
date: 2010-03-15
forum: Wine
---

### Post by Hamishfox on 2010-03-15
Hi there.

I´m trying to install a program called reason from a .iso in wine.

The installer works fine, but on the first startup the program expects to see the reason DVD in the drive so that it can copy some databases over to my HDD. What I gather I need to do is somehow mount the iso in the location the program is looking for it.

I´ve only installed Ubuntu this week, and had no experience with linux before. I really appreciate it if someone could take me, step by step, through a fix. Preferably explaining what I´m doing and why so I can take this opportunity to learn something.

Thanks in advance-
Hamish.

p.s. The iso is called ¨Reason 4.iso¨. I believe the program needs to see that exact name in order to work, although I´m no certain. Alternatively, the prog is supposed to run under os X too, so if there´s some easy way to make that work it might be a better option.

---

### Post by Hamishfox on 2010-03-15
Never mind! I found the DVD.

---

### Post by Peter7K on 2010-10-28
So it only works if you burn it to a DVD?  Thanks.

---

### Post by Serson_Person on 2011-04-06
Hey,

I thought I'd revive this old post instead of posting a new one, since I'm looking online for answers...

I've never used Wine, but I have a Reason 5.0 DVD and I'm trying to install it, but I don't have permission to as the .exe on the DVD is Read-Only.  I try to set it to Read and Write, but it won't allow me.  I cannot check the box to "allow as an executable" either.

Any help?

---

### Post by lisati on 2011-04-06
> **Serson_Person said:**
> Hey,

I thought I'd revive this old post instead of posting a new one, since I'm looking online for answers...

I've never used Wine, but I have a Reason 5.0 DVD and I'm trying to install it, but I don't have permission to as the .exe on the DVD is Read-Only.  I try to set it to Read and Write, but it won't allow me.  I cannot check the box to "allow as an executable" either.

Any help?

My experience of using Wine is rather limited, but I do recall seeing a similar question recently in another thread. If memory serves correctly, one way of running the setup program, assuming you have Wine installed, is with a terminal command similar to this:
```
wine /path/to/exe-file
```

---

### Post by Serson_Person on 2011-04-06
Here's a newb question... how do I know that path?  My username is sp98

so would it be:

sp98/media/Reason 5

?

---

### Post by Serson_Person on 2011-04-06
I just tried this:

sp98@SP98-Ubuntu:~$ sudo wine /media/Reason 5/Install Reason.exe
[sudo] password for sp98: 
wine: /home/sp98/.wine is not owned by you
sp98@SP98-Ubuntu:~$

---

### Post by lisati on 2011-04-06
> **Serson_Person said:**
> I just tried this:

sp98@SP98-Ubuntu:~$ sudo wine /media/Reason 5/Install Reason.exe
[sudo] password for sp98: 
wine: /home/sp98/.wine is not owned by you
sp98@SP98-Ubuntu:~$

Someone more experienced in using Wine than myself might be able to give a better answer to this, but I suspect you might not need the sudo portion of the command.

---

### Post by GWBouge on 2011-04-06
> **Serson_Person said:**
> I just tried this:

sp98@SP98-Ubuntu:~$ sudo wine /media/Reason 5/Install Reason.exe
[sudo] password for sp98: 
wine: /home/sp98/.wine is not owned by you
sp98@SP98-Ubuntu:~$

Yeah, sudo (root) doesn't own your home directory.  Also remember to either escape spaces in paths (put a backslash before it), or put quotes around it if there's spaces in it.  Try:

```
$ wine /media/Reason\ 5/Install\ Reason.exe
# OR ...
$ wine "/media/Reason 5/Install Reason.exe"
```

---

### Post by Serson_Person on 2011-04-06
Guys I could kiss you!

Unfortunately that would go against my sexuality, but let me just say I'm excited!  So far so good.  Yes, I figured the spaces were interrupting and the quotations helped.  Thanks a lot, I hope it completes itself.

That way I can end another day, saved from Windows.  :P

EDIT:  Just wanted to say it installed and works perfect.  Thanks again!

---

### Post by GWBouge on 2011-04-06
np  =o)

Also, if you didn't know, you can use the Tab button to autocomplete path and file names, and it will escape the spaces for you.  Just type the first couple letters of the path or file name, and push Tab.  Incredibly useful  =o)

---

