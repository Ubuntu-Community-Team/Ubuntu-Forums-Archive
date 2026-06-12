---
title: "Is there a way of overriding Wine when it blocks an .exe file that you trust?"
date: 2010-12-01
forum: Wine
---

### Post by Chrisy91 on 2010-12-01
Im trying to install some Windows programs that are from a reputable source, but I am unable to install it because Wine thinks its some kind of malicous program.. Is there a way to override it??

Thank you.:)

---

### Post by dtfinch on 2010-12-01
I'm not aware of anything in wine to block exes. How are you trying to run it and what errors are you getting?

---

### Post by chaanakya_chiraag on 2010-12-01
You need to mark the files as executable.  Right-click on the offending file and click Properties.  Click on the File Permissions tab and tick the checkbox for Owner Executable rights.

---

### Post by Chrisy91 on 2010-12-01
I have just simply downloaded the archive off Cnet and tried to run it through wine and it says > [COLOR="Blue"]The file .... installer.exe is not marked as exectuable. If this was downloaded or copied drom an untrusted source, it may be dangerous to run.[/COLOR]

---

### Post by chaanakya_chiraag on 2010-12-02
Right...and my post above will fix that :)

---

### Post by cogadh on 2010-12-02
> **Chrisy91 said:**
> I have just simply downloaded the archive off Cnet and tried to run it through wine and it says
That's not Wine doing that, that's Ubuntu. Google "Ubuntu no execute bit" and you'll get the full story.

---

