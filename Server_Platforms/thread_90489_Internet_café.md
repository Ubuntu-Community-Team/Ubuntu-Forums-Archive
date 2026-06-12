---
title: "Internet café"
date: 2005-11-15
forum: Server Platforms
---

### Post by khaledagha on 2005-11-15
Hello all 

Is there is any program on Linux to manage a internet café? (user account management  , shutdown all computer from the server ….  )

---

### Post by lafnlab on 2005-11-15
I don't know if there is an all-in-one solution. My guess is that you would need to have several different pieces of software, and you might have to come up with some yourself. 

For the part about shutting all computers down from the server, you might need to look into a clustering app (?), or maybe some software used on clusters can be used to shut them all down. If you need to shut them off at a certain time, you might be able to set it up in cron. If you want to shut them down on demand, regardless of time, you would have to send each machine a message to shutdown. You might have to come up with a shell script that can automate this. 

As far as billing goes, I think I read somewhere in these forums about software used by hosting services. Maybe take a look at that. :???:

---

### Post by ejms07 on 2005-11-15
Check [http://openkiosk.sourceforge.net](http://openkiosk.sourceforge.net) (Requires KDE) and [http://cyborg.sourceforge.net](http://cyborg.sourceforge.net) (for a complete solution)

---

### Post by odzk on 2007-10-17
> **ejms07 said:**
> Check [http://openkiosk.sourceforge.net](http://openkiosk.sourceforge.net) (Requires KDE) and [http://cyborg.sourceforge.net](http://cyborg.sourceforge.net) (for a complete solution)

thanks for the info, ill give this a try ^_^

---

