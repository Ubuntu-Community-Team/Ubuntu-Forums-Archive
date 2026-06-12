---
title: "Innocent website tries to &quot;scan&quot; computer - should I get protection?"
date: 2010-05-06
forum: Security
---

### Post by racie on 2010-05-06
So I forgot how to do something in Compiz and I quickly Googled it to find the answer.  On the first or second link I clicked, a pop-up box opened from Firefox saying that I should scan my computer.  Immediately, I pressed the X button, but a page started to load that tried to "scan" my computer.  I closed out Firefox and re-opened it.  I did the exact same search again on Google, but I clicked on the cached view of the site.  It was harmless enough--a blog with some ads on the side of the page.  I'm assuming that it was one of the ads that somehow must have taken over the page.

Anyway, I know that the discussion of anti-virus programs is not anything new, but I would like to know if this virus may have affected Ubuntu.  What would you guys recommend in this case?

Also, after running the update manager, I received a pop-up box asking if I would like to **update Grub**.  Is this a normal part of the update, or could it be a virus?  I'm a bit paranoid, being from the land of Windows.  :/

Thanks!

---

### Post by mathspeedy on 2010-05-06
I'm not completely sure but, when a "website" tries to scan a computer, it's because of a malicious add trying to make people buy a fake A-V,which will in fact, give you viruses.
But like most viruses, they are made for Windows only. So it's not supposed to harm the computer.
I hope it helps.;)

---

### Post by mkvnmtr on 2010-05-06
You might should use the no-script and add blocker extentions in Firefox. It will stop that.

---

### Post by sgosnell on 2010-05-06
Updating grub is normal for some updates, it depends on the packages that were updated.  If a newer kernel was installed, you'll have to update grub before you can boot to it.

It's common for websites to pop up scary warning messages, in order to try to get you to buy their guaranteed gee-whiz malware remover.  They're all for Windows, and don't even bother to scan your computer to see what the OS is, they just assume everyone runs Windows and is terrified of viruses, etc.  Just ignore it.

---

### Post by noway2 on 2010-05-06
If you recently ran the update manager it is probably that.  I recall seeing an update to grub a few days ago.

---

### Post by Letrazzrot on 2010-05-06
The ones I have seen do a fake "scan" of your computer - they actually don't do anything.  Then they supposedly determine that you are infected with some virus, and give you a download link to an anti-virus program as a solution.  Of course, the anti-virus program is just a trojan with some malware payload.

If this is the same type of scam as these, then you would have to download the program and execute it on Windows to actually get infected.

I suppose that theoretically,  there could be some security hole in the web browser where malicious code could install without you actually downloading it and manually installing it.  But in such an unlikely case, you probably wouldn't even notice it - the malicious page would not need to use social engineering tactics.

Unless you are a highly profitable target for criminals or involved in corporate espionage, I doubt you have much to worry about.

Also, the "NoScript" mentioned above is great for Firefox to block this kind of crap out.

---

### Post by racie on 2010-05-06
Thanks everyone for clarifying.  I feel much safer now.  No Avast! for me yet and I will also try that Firefox plugin. :)

---

