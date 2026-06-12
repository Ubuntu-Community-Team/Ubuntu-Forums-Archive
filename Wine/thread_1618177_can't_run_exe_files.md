---
title: "can't run exe files"
date: 2010-11-10
forum: Wine
---

### Post by abhinavsinghkhanduja on 2010-11-10
i am quite new to ubuntu. i installed wine 1.2.1 and tried to run an exe file by right clicking and selecting open with wine. however the system just seemed busy for a while and then nothing happened. this file is a self executable zip file created in windows. how do i run it??plz help..

---

### Post by aromo on 2010-11-10
You got to run wineconf to configure your wine environment.  Once you do that (only once), then you can run any executable.

Hope this helps.

---

### Post by abhinavsinghkhanduja on 2010-11-11
well, what configuration should I set it to?

---

### Post by aromo on 2010-11-18
Just run it, accept defaults and exit.  It will create a .wine folder on your home folder that will contain the Wine configuration and therefore allow you to run executable files.

I hope this helps.

---

### Post by cainram on 2011-01-04
Most .exe files that are self extracting executable zip files can be opened without Wine. Just open the file with the Ubuntu Archive Manager.

---

