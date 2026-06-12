---
title: "[SOLVED] Miro dependancy unsupported in Gusty"
date: 2007-10-21
forum: Repositories &amp; Backports
---

### Post by onetb on 2007-10-21
After the Gusty update, I noticed that Miro had downgraded for some reason.  I had installed it by adding the miro repositories to synaptic before.
When I attempted to open it after the update, I was told that the database was made by a newer version (0.9.9.1) and that I would have to update.  I cannot update, however, because:
```
miro:
 Depends: libboost-python1.33.1  but it is not installable
```
I am guessing this was in the feisty repositories, but I am not sure what to add where.  My software sources seem to be pulling Edgy, not Gusty.  Any help?

---

### Post by Sahtor on 2007-10-21
[http://pculture.org/devblogs/wguaraldi/2007/10/19/gutsy-package-for-miro-status/](http://pculture.org/devblogs/wguaraldi/2007/10/19/gutsy-package-for-miro-status/)

I'm personally going to wait for next week until 0.9.9.9 is released

---

### Post by onetb on 2007-10-21
I'm not a big fan of the "wait 'til the next release" method.
Me want Miro now!  That being said, I'll probably have to wait

---

### Post by siena on 2007-10-22
deb file to download
[http://elmargol.wordpress.com/2007/10/16/miro-0991-for-ubuntu-gutsy-gibbon-710/](http://elmargol.wordpress.com/2007/10/16/miro-0991-for-ubuntu-gutsy-gibbon-710/)

---

### Post by Sahtor on 2007-10-24
3rd party repository with latest 0.9.9.9-rc0-1ubuntupcf
```
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/
```

I'm missing the apt-key for this thing. any help?

---

### Post by lintoon on 2007-11-25
I had exactly the same dependency issue.  The problem was my sources list.  All I had to do was change the word feisty to gutsy on my miro repository line.  See below for the new line in /etc/apt/sources.list

deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/

After I made the change I ran sudo apt-get update followed by sudo apt-get install miro.  It installed without issues and works fine.  

Hope this helps someone.

PS.  Has anyone seen VeohTV on Windows.  It's really good so much better than miro.  Hopefully this will get ported for us soon because It's one of those apps that prevents me from going fully linux.

---

### Post by onetb on 2007-11-25
When I began this thread, I don't believe there was a Gusty repository for Miro.  About a week later, there was.
Thanks tho
PS - thanks for the Veoh tip.  I have to check it out on my Windows box

---

