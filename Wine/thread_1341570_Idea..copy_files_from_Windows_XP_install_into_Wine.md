---
title: "Idea..copy files from Windows XP install into Wine's folders?"
date: 2009-11-29
forum: Wine
---

### Post by TheOnlyMrK on 2009-11-29
It's something that I just randomly thought up, I'm not too sure it would work so I figured I'd ask to see what everyone says, though I probably will be testing this tomorrow.

What if I were to install Windows XP in a virtual machine on my computer then when it's finished I open up the virtual hard drive and copy it's files to the proper spots in Wine's folders (/home/USER/.wine/drive_c). In the end wouldn't Wine now have every file needed to run any Windows program, or at least a ton more of them?

---

### Post by PariahVayne on 2009-11-29
> **TheOnlyMrK said:**
> It's something that I just randomly thought up, I'm not too sure it would work so I figured I'd ask to see what everyone says, though I probably will be testing this tomorrow.

What if I were to install Windows XP in a virtual machine on my computer then when it's finished I open up the virtual hard drive and copy it's files to the proper spots in Wine's folders (/home/USER/.wine/drive_c). In the end wouldn't Wine now have every file needed to run any Windows program, or at least a ton more of them?

It has been thought of and done before many times. It will most likely cause problems if you do it.

---

### Post by TheOnlyMrK on 2009-11-29
> **PariahVayne said:**
> It has been thought of and done before many times. It will most likely cause problems if you do it.
Figured I wasn't the first one to think this up. Just couldn't find anything of someone else trying.

---

### Post by PariahVayne on 2009-11-29
> **TheOnlyMrK said:**
> Figured I wasn't the first one to think this up. Just couldn't find anything of someone else trying.

Just backup your entire WINE folder and try it if you truly desire.

---

### Post by jpaugh64 on 2009-11-29
I've seen this done, for a few files which WINE didn't have, but certain WIN programs needed. It works, at least as well as I can tell--and, of course, there's no warranty. But, although I haven't checked, I'm almost certain this violates the Windows EULA.

---

### Post by beastrace91 on 2009-11-30
I would NOT recommend copying the entire contents of your Windows system folder over... in many cases you are better off using the default Wine .dlls (if they exist and are completed enough for your program to use). On occasion you can use a native .dll file from Windows for certain programs (not always 100% going to work) and have success with it - but you should really do this on a case by case basis (and not just for every .dll file on a normal Windows install).

Lastly I'd like to mention if you do copy over a .dll file from a Windows install to your Wine before you open your WineCFG and set that particular .dll file to a native override.

Regards,
~Jeff

---

### Post by hikaricore on 2009-11-30
No.

---

### Post by beastrace91 on 2009-11-30
> **hikaricore said:**
> No.

Your description is elegant yet simple - I like it ;)

~Jeff

---

