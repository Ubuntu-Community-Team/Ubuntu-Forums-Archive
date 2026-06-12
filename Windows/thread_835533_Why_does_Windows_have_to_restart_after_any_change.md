---
title: "Why does Windows have to restart after any change"
date: 2008-06-20
forum: Windows
---

### Post by VChief on 2008-06-20
I was playing with Windows in Qemu and it had one of it's commonplace restarts. That reminded me of a question that I had back when I first started using Linux, but since I rarely touch Windows outside of work (where I do no admin-type stuff), I never think about it.

Why does Windows have to restart so much? Change a setting, Windows must restart. Install a program, Windows must restart. Remove a program, Windows must restart. This restart came after downloading something, before it even restarted (from MS's website). I'd just really like to know why Windows has to always restart. I must admit, I don't miss it in Linux. I love being able to do a thousand-some changes and only restart for a kernel update.

Another point, how did this become "ok" to people? I know I get really mad when I'm at work doing something important and get a message that Windows has to restart for whatever reason (which I never knew it was doing...but apparently the admins did). Just curiosity if anyone's got answers.

---

### Post by rickyjones on 2008-06-20
> **leeward said:**
> I was playing with Windows in Qemu and it had one of it's commonplace restarts. That reminded me of a question that I had back when I first started using Linux, but since I rarely touch Windows outside of work (where I do no admin-type stuff), I never think about it.

Why does Windows have to restart so much? Change a setting, Windows must restart. Install a program, Windows must restart. Remove a program, Windows must restart. This restart came after downloading something, before it even restarted (from MS's website). I'd just really like to know why Windows has to always restart. I must admit, I don't miss it in Linux. I love being able to do a thousand-some changes and only restart for a kernel update.

Another point, how did this become "ok" to people? I know I get really mad when I'm at work doing something important and get a message that Windows has to restart for whatever reason (which I never knew it was doing...but apparently the admins did). Just curiosity if anyone's got answers.

Windows XP and Vista, in my experience as an IT Consultant, only need to be restarted when you are installing or uninstalling software that affects system files or files that may be in use. You also must restart for certain system wide events (changing the size of the page file because the page file is currently in use is one example).

What changes are you making? What version of Windows are you running?

I remember a lot more reboots in Win9X because of the way the system was. People were not OK with this which is why they made this better in Windows 2000/XP/2003/Vista.

Sincerely,
Richard

---

### Post by tgrimley on 2008-06-20
In addition to what Richard says, Windows doesn't really have the ability to restart some services like you can in Linux, so it requires a full reboot (for instance you have to restart when you change your workgroup!).  Although I'm always annoyed that you have to log in and out to get group changes for the current user to stick (in Ubuntu).

---

### Post by ComputerGeek31618 on 2008-06-20
Yep.  That about sums it up.  However, there is also the registry, and although you can install most programs without requiring a restart, almost all programs write in the registry, and any system area changes in it need reboots.  

XP is good about what needs restarts and what doesn't.  If it isn't a function critical change, or a system method change, it doesn't bother.

---

### Post by LaRoza on 2008-06-20
Windows is poorly designed, or at least, designed in a way that makes it unwieldly for users.

I once had to restart for installing a browser (Opera 9.5 in Windows 98 SE)

---

### Post by LaRoza on 2008-06-20
> **leeward said:**
> 
Another point, how did this become "ok" to people? 

Because they don't know better.

---

### Post by karellen on 2008-06-21
it's because of its (poor) design.
but in XP and Vista you don't have to restart in a particular moment if you don't want to. there's an option to postpone it indefinetely

---

### Post by tgrimley on 2008-06-21
> **karellen said:**
> it's because of its (poor) design.
but in XP and Vista you don't have to restart in a particular moment if you don't want to. there's an option to postpone it indefinetely

as long as you don't mind clicking "do not restart" every 4 hours in vista or 15 minutes or whatever it is in xp...

---

### Post by karellen on 2008-06-21
> **tgrimley said:**
> as long as you don't mind clicking "do not restart" every 4 hours in vista or 15 minutes or whatever it is in xp...

:) something like that...

---

### Post by kerry_s on 2008-06-21
that's 1 of the things i found annoying, i just did a win2k setup for mom and waiting for reboots was the longest part. it took me 2 days to get everything installed, setup, and secured. now every things cake, she just wakes it up does her thing, then puts it back in standby. so far only 2 blue screens of death(permissions thing), but i think i fixed that for now.

---

### Post by jnw222 on 2008-06-21
because windows is a group of idiots

---

### Post by rickyjones on 2008-06-23
> **tgrimley said:**
> as long as you don't mind clicking "do not restart" every 4 hours in vista or 15 minutes or whatever it is in xp...

Your post is in regards to updates, right? Because I use Windows XP Professional and Windows Vista Business every day for personal and business use and I only see those dialog boxes after an update cycle. 

By the way you can stop that "annoying" reminder by disabling the Automatic Updates service using the Services control panel applet (available from the Administrative Tools menu). This will allow you to reboot manually when you feel like it.

Sincerely,
Richard

---

### Post by rickyjones on 2008-06-23
> **kerry_s said:**
> that's 1 of the things i found annoying, i just did a win2k setup for mom and waiting for reboots was the longest part. it took me 2 days to get everything installed, setup, and secured. now every things cake, she just wakes it up does her thing, then puts it back in standby. so far only 2 blue screens of death(permissions thing), but i think i fixed that for now.

It took you two days to get everything installed, setup, and secured? May I ask what programs and processes were being installed and set up that would take this long? Or is this two days because you spent a few minutes here and there but couldn't sit down and do it all at once because you were busy doing other things?

For the second part: BSOD related to permissions? I've never heard of that one. Hardware failure or software failure sure, but permissions? On a default installation? Just sounds very... odd.

If you have the STOP message available I'd be happy to help look into it for you.

Sincerely,
Richard

---

### Post by kerry_s on 2008-06-23
> **rickyjones said:**
> It took you two days to get everything installed, setup, and secured? May I ask what programs and processes were being installed and set up that would take this long? Or is this two days because you spent a few minutes here and there but couldn't sit down and do it all at once because you were busy doing other things?

For the second part: BSOD related to permissions? I've never heard of that one. Hardware failure or software failure sure, but permissions? On a default installation? Just sounds very... odd.

If you have the STOP message available I'd be happy to help look into it for you.

Sincerely,
Richard

i took my time with the setup, didn't want to rush as i wanted it perfect for mom.

BSOD was something to do with permissions and wireless. i started her out at restricted user, which caused the first blue screen, moved her to power user, which resulted in the second blue screen, now she's a administrator no more blue screens. win2k doesn't have wireless like xp, you use the drivers & utility that come with the device(blitz usb wireless) so i'm sure the problem is there. i'm planning on getting a wireless pc card, then i'll try again, for now it's working perfectly, so i'll leave it as it is.

thanks for the offer to help, but i'm a X ms employee, i can handle it. :lolflag:

---

### Post by Bungo Pony on 2008-06-23
There are two times when I hate the whole restart Windows thing:

1) When I'm doing a fresh install and need to install a pile of software. I want to do ONE restart for a bunch of new software, not one restart for each install. Some software doesn't even give you the option of "restart later".

2) Windows Updates. Windows tells me I can keep working while it downloads updates, so I do. Then when it's done, it NAGS me every 10 minutes to restart the damn computer. Hey, you told me to keep working and now I'm in the middle of something. I don't WANT to restart in the middle of a project!

---

### Post by rickyjones on 2008-06-23
> **Bungo Pony said:**
> There are two times when I hate the whole restart Windows thing:

1) When I'm doing a fresh install and need to install a pile of software. I want to do ONE restart for a bunch of new software, not one restart for each install. Some software doesn't even give you the option of "restart later".

Sounds to me like you need to invest in software designed for your version of Windows. The only recent time that I have had a software package prompt a restart would be an older game that I was installing. I think it may have had a hook that said "When on Windows, Install, then reboot to be safe." Not a Windows problem on your hands, but a third party software problem. May I ask what software packages are prompting these reboots? Thanks!

> **Bungo Pony said:**
> 
2) Windows Updates. Windows tells me I can keep working while it downloads updates, so I do. Then when it's done, it NAGS me every 10 minutes to restart the damn computer. Hey, you told me to keep working and now I'm in the middle of something. I don't WANT to restart in the middle of a project!
Well you can keep on working, but of course Windows is going to prompt for a reboot. It just changed some critical system files and you are still not fully patched until you reboot. Windows is doing it's best to ensure a secure configuration. 

You can also stop the Automatic Updates service when you see the prompt and it'll go away until you reboot.

Sincerely,
Richard

---

### Post by BlueSkyNIS on 2008-06-23
> **rickyjones said:**
> May I ask what software packages are prompting these reboots? Thanks!


I needed to restart because of:

*Adobe Acrobat Reader* V8.1.2 (not sure about version, but it was V8 definitively), but I can remember I was very curious why Acrobat needed restart, there was no previous adobe software installed... :-?

*Internet Explorer 7*

MultiSIM 10 (electronic simulation)
Protel 99SE (PCB design, ok it is a bit outdated :) )
Design Explorer DXP (PCB design and much more...)

---

### Post by nvteighen on 2008-06-24
> **BlueSkyNIS said:**
> I needed to restart because of:

(...)

*Internet Explorer 7*

Quite logical: Internet Explorer is that tightly integrated to Windows that nobody can't tell the difference where the system ends and the browser begins.

---

### Post by ComputerGeek31618 on 2008-06-24
No kidding.  I'll bet the people who built it in the first place know the dividing line, but why should they tell us?

---

### Post by kerry_s on 2008-06-24
> **ComputerGeek31618 said:**
> No kidding.  I'll bet the people who built it in the first place know the dividing line, but why should they tell us?

yeah, there's no need to know how it works, just that it works. 90% of people don't care, 10% of us want to see what we can do to improve it, so we want to look deep.
:lolflag:

---

### Post by nvteighen on 2008-06-25
> **ComputerGeek31618 said:**
> No kidding.  I'll bet the people who built it in the first place know the dividing line, but why should they tell us?
I think they've lost where the dividing line is... Or Microsoft developers are being forced by their Marketing Dept. to forget where it is. 

(Hey, I don't blame MS programmers... I believe they are willing to do their best, but they have to comply to the company's "politics" or they'll be fired)

---

