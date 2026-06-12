---
title: "Only boots into terminal after 11.10 install"
date: 2011-12-27
forum: Server Platforms
---

### Post by bryan.sailer on 2011-12-27
I am building a home server to store my family pictures and documents. I installed Ubuntu 11.10 and now when I restarted the machine it only boots in terminal. What did I do wrong?

---

### Post by spiky001 on 2011-12-27
Hi  Did you install the server edition or desktop edition of ubuntu?

---

### Post by bryan.sailer on 2011-12-27
I installed the server edition. I am able to get around using the terminal but the gui would be nice.

---

### Post by croxio5 on 2011-12-28
If you want to install the desktop system used by the Desktop edition of Ubuntu, do the following at the terminal:
> sudo apt-get install ubuntu-desktop

It's quite a hefty package, but it'll install the full Ubuntu desktop. With Oneiric, not sure if it installs GNOME or the Unity-based system.

---

### Post by spynappels on 2011-12-28
> **bryan.sailer said:**
> I installed the server edition. I am able to get around using the terminal but the gui would be nice.

By default, the Server Edition is CLI only. A full Desktop Environment install might be overkill for just administering the server, you could look at web-based GUI options like Webmin.

Getting more proficient at using the CLI is also worth spending time on though....

---

### Post by rubylaser on 2011-12-28
If you want a GUI, you should just install the Desktop Edition.  A server install really should only be running with the CLI.  As stated above, learning to properly use the CLI is really worth your time.

---

### Post by bryan.sailer on 2011-12-29
Thank you all for your input. I was more worried that I had done something wrong more then needing a gui. The CLI is all I need. I am also running Webmin which works well.

---

