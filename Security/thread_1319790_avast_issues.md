---
title: "avast issues"
date: 2009-11-08
forum: Security
---

### Post by mattsegstro on 2009-11-08
I know a lot of people on here are going to say that you don't need virus protection for Linux and I agree but I use it because I am in contact with a lot of Windows users and sharing files whether via email, flash drives, or networks with them, and I don't want to be infected so I don't infect them.

I downloaded Avast for Linux today, the free home edition one, and it creates an icon in my Applications-Accessories menu.  When I click on it, it updates just fine, I can change all the preferences, put in my free license code, everything.  The problem starts when I scan.  Any kind of scan, from Thorough including scanning in archives, to Quick excluding archives, generates a long list of errors at the end that say permission denied or something for scanning certain files.

How can I get rid of those errors?  I would assume the answer has something to do with running the program as root rather than my standard user account.  I guess I could probably do that in Terminal and simply use CL to start the program as sudo root or something like that, but is there a way that I could maybe edit the menu item and set it to always run as root or always give permissions so I can always scan, not have those errors, and not have to manually start the program via CL or something and just be able to use the menu item all the time?

I hope I'm being clear enough here with what I'm asking, and I hope there's a quick and easy way to do this.  I'm not afraid of using CL solutions so long as the instructions on how to do them are extremely clear, like step by step instructions.  I'm not all that bad with computers or Linux in general but unless I'm told explicitly, I can't do CL.

Thanks in advance for any answers!

---

### Post by cariboo on 2009-11-08
You really don't have to scan any directories other that the directories where the files you share/email files are located. As you know you need to be root to do anything in any other directory besides your own home directory, so the chances of a virus be in any other directory are pretty slim in a default installation.

---

### Post by mattsegstro on 2009-11-08
So I should just scan my Home rather than trying to run the program itself as root?

---

### Post by cariboo on 2009-11-09
Yes, as that is more than likely where the viruses would be. unless you purposely moved the files to somewhere outside your home directory.

---

### Post by mattsegstro on 2009-11-09
Well I never touch other folders other than my home directory, or when I do I'm just looking for something, certainly not moving files around, so I'll just scan my Home from now on... thanks!

---

### Post by cariboo on 2009-11-09
Your welcome.

---

