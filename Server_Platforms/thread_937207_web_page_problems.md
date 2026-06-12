---
title: "web page problems"
date: 2008-10-03
forum: Server Platforms
---

### Post by metaranha on 2008-10-03
Hi everyone, I'm a new Ubuntu server admin (running HH) and i'm having a little trouble getting a simple webpage I wrote in PHP to display to a browser. I forwarded port 80 on my router and put the PHP into the /var/www directory but it still won't display. 
One of my friends suggested that the page may not be displaying because the listening port (may not be open?) 
Does anyone have some suggestions to get this to work right?

---

### Post by elvinatom on 2008-10-03
Do you have a commercial connection?  I'm asking because it's possible that the port is blocked via your ISP.

---

### Post by Rich78 on 2008-10-03
Best way to find out is to telnet the box on port 80.

telnet <serverip> 80

If you don't connect, something is blocking port 80.

---

### Post by lykwydchykyn on 2008-10-03
Does it work fine on your local network?

---

### Post by metaranha on 2008-10-03
it doesn't work on my local network either. It looks like i can't telnet through 80 either.

---

