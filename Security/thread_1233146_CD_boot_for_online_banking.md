---
title: "CD boot for online banking"
date: 2009-08-06
forum: Security
---

### Post by Ender.Wiggin on 2009-08-06
I am thinking of using the boot-able version of Ubuntu just for accessing and performing occasional online banking, which only involves paying bills and printing PDFs of the transactions. How safe is this method compared to my current method of booting to a separate hard drive with only Windows and Norton Internet Security installed to access the bank web site? I use that drive just to access the site and then power down, and use swap connectors for another hard drive with Windows for daily less secure stuff...

---

### Post by DiscoKiller on 2009-08-06
Hi Ender, as no cache data is held once you terminate a livecd session then this would be a very secure method for your needs. The security in Linux on the whole is fr greater than Windows so this could be a good option for you. 
 
Hope this helps, 
 
Peace, 
 
DK

---

### Post by megamania on 2009-08-06
> **Ender.Wiggin said:**
> I am thinking of using the boot-able version of Ubuntu just for accessing and performing occasional online banking, which only involves paying bills and printing PDFs of the transactions. How safe is this method compared to my current method of booting to a separate hard drive with only Windows and Norton Internet Security installed to access the bank web site? I use that drive just to access the site and then power down, and use swap connectors for another hard drive with Windows for daily less secure stuff...
Using the live CD is safer not only because linux is safer in general, but also because even if the system is corrupted, the next time you boot the live CD the system will be clean again.

But I'm really surprised by your attention to security. I've been doing online banking from my main computer (running Ubuntu) for years with no particular extra-care...

---

### Post by Ender.Wiggin on 2009-08-06
Thanks, I am still primarily a Windows user so have not given up on feeling insecure even though I am being told by the bank that my accounts are protected against fraud. Perhaps I am a bit overly paranoid but I would rather be too much than not enough. :D

---

### Post by Cyked on 2009-08-06
You can do things to further secure your browsing, hence you posting here.  However, YOU can do NOTHING to prevent the BANK itself in having a security breach. :D

"Just because you are paranoid doesn't mean they are not out to get you"

---

### Post by XanTrax on 2009-08-06
Are you using Windows as your standard operating system now?  If so, you can just use Wubi and run the liveCD through Windows and do your banking and other things through it.  This way, you wouldnt have to shut down every time or move to another computer to do your banking stuff.

If you're using Ubuntu and want to use the LiveCD to do your banking for security purposes (but why?  Ubuntu is secure anyway...), you can install VirtualBox, download the latest ISO, set your Virtual Machine to use the ISO image to boot from, start the VM, and voila...you can boot the liveCD each time through a Virtual Machine rather than having to shut down.

---

