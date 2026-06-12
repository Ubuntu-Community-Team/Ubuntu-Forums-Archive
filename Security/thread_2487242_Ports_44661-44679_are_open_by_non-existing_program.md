---
title: "Ports: 44661-44679 are open by non-existing program?"
date: 2023-05-28
forum: Security
---

### Post by kanatbek-aka on 2023-05-28
Hi everyone,

Can someone please explain to me what reason the ports 44661 & 44679 are open on localhost pid 5388 by program code standard on my machine? It appeared two days ago and could not figure out which local program is running it. The screenshot is available below. [IMG]https://drive.google.com/drive/folders/17dHb5oKXtgqSBh9xc4K7eV6YqKQPWJYz?usp=share_link[/IMG]

Thanks in advance.

Kanatbek

---

### Post by kanatbek-aka on 2023-05-28
Thanks for the assissting me here to explain what to look for. 

Kind regards,
Kanatbek

---

### Post by Rubi1200 on 2023-05-28
Hi and welcome to the forums :-)

Please keep in mind we are all volunteers here with different time zones and different priorities in our lives.

You are asking a very specific question and not everyone will be able to come along and answer immediately.

Please provide the output (in code tags) for the following commands:

```
sudo netstat -ano -p tcp
```

And for more information on the process in your screenshot use this:

```
ps -ef | grep <PID number>
```

Thanks.

---

### Post by The Cog on 2023-05-29
I would ask for the output of **[FONT=Courier New]sudo ss -lntp[/FONT]**. But in the meantime, the program doing the listening seems to have the name **Code**. I'm not familiar with that. Visual studio vscode installs an executable called **code**, but that's in lower case.
Anyway, the program you are wondering about is listening on the loopback address 127.0.0.1, which means it cannot communicate outside of the machine - it is only there for talking to itself, or to client programs on the same box.

---

