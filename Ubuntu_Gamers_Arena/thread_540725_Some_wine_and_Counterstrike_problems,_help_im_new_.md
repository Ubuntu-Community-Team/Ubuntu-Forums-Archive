---
title: "Some wine and Counterstrike problems, help im new &gt;&lt;"
date: 2007-09-01
forum: Ubuntu Gamers Arena
---

### Post by VietxHieu on 2007-09-01
hello im kinda new at linux,ubuntu and... well i looked around on ubuntu forums and couldnt find an answer to my question, it is..

Well i have counter strike and steam running on latest wine, so when i downloaded the Counter strike Source, and tried to run it, i kept on getting this error...

"Steam.exe(main exception): Win32 StructuredException at 0EEB4546 : 
UNKNOWN"

i cant seem whats wrong and even if i try to start steam it says the same error... So i dunno whats wrong i tried uninstalling and reinstalling steam but get the same thing over and over =\ thanks for reading much appreciated~

~Hieu

---

### Post by VietxHieu on 2007-09-01
anyone?

---

### Post by cogadh on 2007-09-02
Three questions:

What version of Wine are you using?
Have you installed the Gecko engine in Wine?

Actually, I only have those two questions. There might be a third depending on the answers to one and two. :-k

---

### Post by VietxHieu on 2007-09-02
hieu@hieu-desktop:~$ wine --version
wine-0.9.44

and yes i have wine gecko installed on it =\ whats your third question? lol

---

### Post by cogadh on 2007-09-02
Have you tried deleting the "ClientRegistry.blob" file from the Steam install directory, then starting Steam and letting it rebuild?

---

### Post by VietxHieu on 2007-09-02
> **cogadh said:**
> Have you tried deleting the "ClientRegistry.blob" file from the Steam install directory, then starting Steam and letting it rebuild?

yeah tried that... and im still getting the error, and i cant "open steam" unless i uninstall it and then create a new account, but then i dont have my counter strike =\

---

### Post by VietxHieu on 2007-09-05
no one can help? =\

---

### Post by Corpus_CT on 2007-10-26
Try re-installing wine and then re-installing Counter-Strike, Steam and whatever other programs you want to use under it.

To uninstall wine:
[LIST]
[*]Remove the package
        [FONT="Courier New"]sudo apt-get remove wine[/FONT]

[*]Delete the .wine folder in your home directory
        [FONT="Courier New"]sudo rm -Rf ~/.wine[/FONT]
[/LIST]
And I'm guessing you know how to install it again after that.

Hope that helps.

---

### Post by VietxHieu on 2007-10-27
thanks that did help ^^-b

---

