---
title: "virtualbox problem with 8.10"
date: 2008-10-30
forum: Virtualisation
---

### Post by Tucatts on 2008-10-30
I upgraded today to 8.10 and it all went fine except now virtualbox has stopped working. The error I get is " failed to create the virtualbox com object". Anyone else had this situation? Any ideas?
Thanks! Overall 8.10 is fine so I am happy but do want to get Vb working, as it has my XP installed on it.
Thanks again for any help.

---

### Post by stinger30au on 2008-10-30
did you use the free version or the closed source from the virtual box web site?

---

### Post by Tucatts on 2008-10-30
you know , embarrassed to admit but I can't remember. I usually use synaptic for everything and then when things go bad, lol I find something in the forums to get me back on track.I am not a linux power user for sure but I have been able to fix almost every problem I have encounted with all the help found her. In short I can follow instructions, ha ha.

---

### Post by jack frost on 2008-10-30
> **Tucatts said:**
> I upgraded today to 8.10 and it all went fine except now virtualbox has stopped working. The error I get is " failed to create the virtualbox com object". Anyone else had this situation? Any ideas?
Thanks! Overall 8.10 is fine so I am happy but do want to get Vb working, as it has my XP installed on it.
Thanks again for any help.
you  may have to recompile the virtualbox kernel with this command
 
sudo /etc/init.d/vboxdrv setup
 
I googled and found that in forums that someone found on the virtualbox website forums.. I had to do it once my kernel updated and it let my xp vm boot after that.

---

