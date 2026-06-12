---
title: "ClamAv says I have nearly 500 threats."
date: 2012-08-25
forum: Security
---

### Post by Lemuel111 on 2012-08-25
I recently had some sort of problem with the computer; in text boxes, keys would be pressed in excess which I was not pressing e.g. loads of full stops. I concluded that I had some sort of virus and it was affecting both Ubuntu and Windows (both are on the computer). Consequently I wiped the computer and reloaded everything but the same problem occurred.
I then read that I also needed to format the disks to ensure that everything was clean. I did this and reloaded Windows and Ubuntu again. I also did a full Norton virus check in Windows with no threats. I also did a Hitman Pro 3 Malware check and Emsisoft Malware check both with nothing. I then did a Clam AV check in Ubuntu and for the Windows partition  & it came up with nearly 500 threats! Can this be that my computer is still infected with a virus/trojan that I cannot get rid off (though I am not yet experiencing the same keyboard/text box problems)? The majority of threats are in the Win32 directory. Any help or advice appreciated. Thanks.

---

### Post by critin on 2012-08-25
The threats are still in the Win32 directory AFTER wiping and reinstalling?  Odd.  Was the reinstall done by the original CD or copied some other way?  For instance, a copy that may have virus's stored.  Did you wipe the email too?  It could be something in there.

And again, it could be harmless threats that appear in almost anything downloaded--tracking, etc.  
But the pressing keys are not harmless are they?  If your virus/malware programs don't find anything, I'd say there is nothing to worry about now.  Did you run the virus checks before wiping the OS's?  It could be a keyboard issue.

The malware alert notice should link to the file showing malware so you can click on it to find out which file it is.  It should also be able to take you to a site that explains the malware.

---

### Post by cariboo on 2012-08-25
How up-to-date are the ClamAV virus signatures, depending on what version you are using they could be fairly old.

---

### Post by Lemuel111 on 2012-08-30
Clam Av is the latest version. What do you mean by the signatures? 

I have started to look through some of the quarantined files and check them and they are not viruses according to the net. However, when I try to restore them Clam AV just says " couldn't move file ........no such file or directory. " 
Until I restore some of these files I cannot open Windows.

---

### Post by WhiteHatGuy on 2012-08-30
> **Lemuel111 said:**
> I recently had some sort of problem with the computer; in text boxes, keys would be pressed in excess which I was not pressing e.g. loads of full stops. I concluded that I had some sort of virus and it was affecting both Ubuntu and Windows (both are on the computer). Consequently I wiped the computer and reloaded everything but the same problem occurred.
I then read that I also needed to format the disks to ensure that everything was clean. I did this and reloaded Windows and Ubuntu again. I also did a full Norton virus check in Windows with no threats. I also did a Hitman Pro 3 Malware check and Emsisoft Malware check both with nothing. I then did a Clam AV check in Ubuntu and for the Windows partition  & it came up with nearly 500 threats! Can this be that my computer is still infected with a virus/trojan that I cannot get rid off (though I am not yet experiencing the same keyboard/text box problems)? The majority of threats are in the Win32 directory. Any help or advice appreciated. Thanks.






In ClamTk (clamav) go to preferences, scanning preferences, look if there is a checkmark in ENABLE EXTRA SCAN SETTINGS, this are not necesarly harmfull to your computer. But they have potential to do harm. Try scanning without that option and see how it goes.

---

### Post by Lemuel111 on 2012-08-30
> **WhiteHatGuy said:**
> In ClamTk (clamav) go to preferences, scanning preferences, look if there is a checkmark in ENABLE EXTRA SCAN SETTINGS, this are not necesarly harmfull to your computer. But they have potential to do harm. Try scanning without that option and see how it goes.


Do I do another scan now?

---

### Post by WhiteHatGuy on 2012-08-30
> **Lemuel111 said:**
> Do I do another scan now?



Well, that depends on you, when you have free time. Or start the scan with option on and see how long it takes to catch the first viruses alerts, and then do the same but with option off, and watch if it catch the same viruses again.

---

