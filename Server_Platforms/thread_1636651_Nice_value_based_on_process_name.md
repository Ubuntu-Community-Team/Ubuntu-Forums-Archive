---
title: "Nice value based on process name?"
date: 2010-12-03
forum: Server Platforms
---

### Post by fela on 2010-12-03
Hi
I'm running a debian server but decided to ask in the more widely-read ubuntu forums.

My problem is that I'm running a web server as well as a game server on the same system. The game server likes to eat up CPU time. I give the web server more priority so I'd like to give all java processes (the game is java based and nothing else uses java on the system) a high nice value automatically when they run. Is this possible?

Thanks
Fela

---

### Post by SeijiSensei on 2010-12-03
Start the server process with nice:

nice server_process

adds ten (the default) to the nice level of server_process.

"man nice" for details.

---

### Post by fela on 2010-12-03
> **SeijiSensei said:**
> Start the server process with nice:

nice server_process

adds ten (the default) to the nice level of server_process.

"man nice" for details.

Sure I can do that...but is there any way to make it default to that for a certain process?

cheers

actually, I think that solution might work if I just put that in the sh launcher script actually...thanks ;)

---

### Post by SeijiSensei on 2010-12-04
> **fela said:**
> actually, I think that solution might work if I just put that in the sh launcher script actually...thanks ;)

That's what I was suggesting.

---

### Post by rubylaser on 2010-12-04
And add just a little more, you'll need to edit it's init script to get it to startup up at a higher level automatically.  The scripts on Debian are in /etc/init.d/<webserver_name>.

---

### Post by grrrb on 2011-05-19
You can also run the game server as a separate user, and then use /etc/security/limits.conf to set a default nice level for all this user's processes: (tail /etc/security/limits.conf)

gameserver   soft    priority        19
gameserver   hard    priority        19

---

### Post by fela on 2011-05-19
Cool, well the solution I've come up with is to just add nice to the shell script, as well as memory limits as Java command line options.

---

