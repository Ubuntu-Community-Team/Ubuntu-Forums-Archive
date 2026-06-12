---
title: "wine and security"
date: 2010-02-24
forum: Wine
---

### Post by Joe Ker1086 on 2010-02-24
ok, this might be a dumb question but im going to ask it anyway b/c im curious. It looks to me like wine creates a little clone registry for windows....so does that technically open it up to the same viruses as windows?

---

### Post by gsmanners on 2010-02-24
That is one of the risks of using Wine, however you can protect yourself:

1) Never run Wine as root.
2) Never run applications you are unsure about.
3) Do not trust suspicious URLs in web sites or emails.
4) Consider using [ClamAV]("https://help.ubuntu.com/community/ClamAV")
5) Keep your drives in winecfg limited to small areas (and remove the Z drive).
6) If you must run suspicious software, do so in a VM.

---

### Post by Joe Ker1086 on 2010-02-24
im actually kind of glad i didnt ask a dumb queston lol.....but if a virus got into the "windows registry" wouldnt it only affect the windows stuff? i mean a virus written for windows couldnt really attack my /home folder could it?

---

### Post by gsmanners on 2010-02-24
A "virus" is just another type of application. You should be aware that an application can do whatever it's programmed to do within its environment. If you permit it, it can modify your vital data.

---

### Post by d3v1150m471c on 2010-02-24
```

#!/usr/bin/env python
import os
os.system('echo "hello world"')

```That is python language, multiplatform as well. C++ also multiplatform. The above script will tell your native shell to print hello world on the screen. So, as you can imagine a similar string of code could be compiled into a seemingly legitimate .exe file executed by wine and tear a hole right through your system. Linux can get viruses and the like, including through wine. The reason it doesn't? Security is a bit tighter and people typically make them for windows. I wrote a script yesterday to see if I could steal the root password and voila...got it. I'm not going to post it here because it's against the forum rules but linux is as only secure as the user's practice.

---

### Post by Joe Ker1086 on 2010-02-25
> **d3v1150m471c said:**
> ```

#!/usr/bin/env python
import os
os.system('echo "hello world"')

```That is python language, multiplatform as well. C++ also multiplatform. The above script will tell your native shell to print hello world on the screen. So, as you can imagine a similar string of code could be compiled into a seemingly legitimate .exe file executed by wine and tear a hole right through your system. Linux can get viruses and the like, including through wine. The reason it doesn't? Security is a bit tighter and people typically make them for windows. I wrote a script yesterday to see if I could steal the root password and voila...got it. I'm not going to post it here because it's against the forum rules but linux is as only secure as the user's practice.

thank you, deffinately something to tink about.

---

### Post by forcecore on 2010-02-25
as long as you do not run wine in root it is quite safe, i have tested lot of viruses and trojans on wine. Never enter your root password when suddenly something asks out of nowhere. Files still can be deleted (home folder or drives if mounted) or downloaded (trojans).

To d3v1150m471c: can it steal root password without you actually enter it???

---

### Post by ubunterooster on 2010-02-25
1 it can't get your password unless it is given by you
2 there is some danger w/o running as root
3 install the "virus scanner" gui to clamav; this usually is default for opening .exe files. meaning a double-clicked (or autostarted) file should open clam not the program.

---

