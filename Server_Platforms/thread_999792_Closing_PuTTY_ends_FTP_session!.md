---
title: "Closing PuTTY ends FTP session!"
date: 2008-12-02
forum: Server Platforms
---

### Post by AvWijk on 2008-12-02
I'm controlling my Ubuntu 6.06 box with PuTTY 0.56 on Windows XP, since my Ubuntu box is physically 20 KM away from my desk.

While transferrring some files overnight, I noticed my session just quits if I close my PuTTY window? This doesn't happen when I use wget (just tested)

Any reason for this? It occurs with *ftp* and *lukemftp*.

---

### Post by Masuran on 2008-12-02
Hmm, pretty strange. Normally any program should quit when you close your putty session (closes the SSH connection). 
Anyway, what you need is a program called **screen**, this is sort of a window manager for text terminals. 
*screen <command here>*
starts a command using screen. You can then press CTRL+A D to detach the program. If you restart your session on a later time you can *screen -r* to reattach to your previous session. 
Just google for screen to find more information about it.

Still curious about wget not shutting down when you close your session though :)

---

### Post by AvWijk on 2008-12-02
Thanks, but that means I can just do 

#screen lukemftp -i X.X.X.X

And later 'save' my session by pressing the keys?

---

### Post by koenn on 2008-12-02
yes

---

### Post by koenn on 2008-12-02
> **Masuran said:**
> 

Still curious about wget not shutting down when you close your session though :)
... unless it's run with

  -b,  --background        go to background after startup.

?

---

### Post by AvWijk on 2008-12-02
Thanks Masuran, excellent tip!

---

