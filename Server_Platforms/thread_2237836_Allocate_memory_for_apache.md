---
title: "Allocate memory for apache"
date: 2014-08-04
forum: Server Platforms
---

### Post by anndrey on 2014-08-04
Hi everyone!
I have a server that I use for many things. One of the most important is a apache web server. Sometimes other applications use a major part of the memory and the apache server don't work fine.
There is a method to allocate a minimum amount of memory for apache? For example if I have 8GB RAM and I want apache always have 5 GB allocated and the system and the others applications cannot use more than 3 GB.
Is this possible?
Thank you very much!

---

### Post by SeijiSensei on 2014-08-04
I've run Apache on machines with much smaller amounts of memory than that and have never seen it run out of memory.  How many listeners are you running?  How much traffic?  How much swap?  Are you using a GUI or just running from the command prompt?

---

### Post by anndrey on 2014-08-05
There was just an example. I have a much smallar server. I use a server version without GUI.
Thanks

---

### Post by Gyokuro on 2014-08-07
Hi

You can achieve the memory limitation with the setup of apache in cgroups (Control groups) and there a plenty of guides how it's done. Another possibility is to limit the memory via an ulimit -v 5242880 in /etc/apache2.conf. However I would suggest you that you go with cgroups. 

- HTH

---

