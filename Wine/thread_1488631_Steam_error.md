---
title: "Steam error"
date: 2010-05-20
forum: Wine
---

### Post by overtone on 2010-05-20
I know im opening myself up to a world of hate mail here by asking whats wrong with steam. but ill try anyway since my problem seems different than everyone elses.

I installed steam in wine grand. it updated to a hundred percent. but then it doesnt run from there. When running in the terminal I got this 

Code:
    [email]overtone@Mountain:~/.wine[/email]/drive_c/Program Files/Steam$ 
    [email]overtone@Mountain:~/.wine[/email]/drive_c/Program Files/Steam$ wine Steam.exe
    fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
    fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
    CellID: Fetching server list from CSDS. . .
    X Error of failed request:  BadRequest (invalid request code or no such operation)
      Major opcode of failed request:  135 (GLX)
      Minor opcode of failed request:  19 (X_GLXQueryServerString)
      Serial number of failed request:  621
      Current serial number in output stream:  621
    [email]overtone@Mountain:~/.wine[/email]/drive_c/Program Files/Steam$

looks like something with the winecfg. any ideas on how to fix this?


using ubuntu 9.10 and wine 1.01

---

### Post by Bhamid on 2010-05-20
try updating to the latest Wine version with their PPA: *ppa:ubuntu-wine/ppa*

---

### Post by philinux on 2010-05-20
Moved to Wine forum.

---

### Post by overtone on 2010-05-21
any chance of a link

---

### Post by cogadh on 2010-05-21
Link to what, how to update Wine? There's a topic sticked at the top of the forum that tells you how to do that.

---

