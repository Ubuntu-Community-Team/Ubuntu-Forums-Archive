---
title: "Ubuntu Server Console overview"
date: 2011-12-10
forum: Server Platforms
---

### Post by marcbea on 2011-12-10
Ok been looking for this everywhere thought it was time to post something.

Does anyone know where i can get the Server overview script that pops up i the console when you login.

Gives you stuff like uptime and ip address binds really is nice to have.

---

### Post by volkswagner on 2011-12-10
This may help:

MOTD = "Message of the Day"

```
 ls /etc/update-motd.d/

```

```
man update-motd
```

This[ link]("http://www.ubuntugeek.com/how-to-change-message-of-the-day-motd-in-ubuntu-server.html") has some info.

Hope this helps.

---

### Post by Lars Noodén on 2011-12-11
You could put something like the following into [font=Courier New].profile[/font] or [update-motd.d](http://manpages.ubuntu.com/manpages/oneiric/man1/update-motd.1.html) so that it runs when you log in.

```

(
ifconfig | awk 'BEGIN{RS="";FS="\n"}{print $1;print $2;print""}'
uptime;
) | more

```

Edit: here's a more concise output from [ifconfig](http://manpages.ubuntu.com/manpages/oneiric/en/man8/ifconfig.8.html)

```

(
ifconfig | awk '/^[^ ]/{name=$1} $1 == "inet" {sub(/addr:/,"",$2);print name,"\t",$2}'; 
uptime; 
) | more


```

---

### Post by CharlesA on 2011-12-11
> **marcbea said:**
> Ok been looking for this everywhere thought it was time to post something.

Does anyone know where i can get the Server overview script that pops up i the console when you login.

Gives you stuff like uptime and ip address binds really is nice to have.

It is a python script that Ubuntu Server runs.

The command to display it is: ```
landscape-sysinfo
```

---

