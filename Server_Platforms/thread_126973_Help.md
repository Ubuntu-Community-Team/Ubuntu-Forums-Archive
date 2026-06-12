---
title: "Help"
date: 2006-02-07
forum: Server Platforms
---

### Post by soon82 on 2006-02-07
Actually, i have setup xmailserver on my ubuntu 5.04.... the mail server was run properly... but i found that once i restart my server.. the xmailserver will not start automatic. and i need to open the root terminal and type a command to start the xmailserver software.. /etc/init.d/xmail start

everyone, tell me.. how to start my xmailserver automatically.. because i had try to install the bum by using this command apt-get install bum.. but unsuccessful...

---

### Post by Glut on 2006-02-08
Use the update-rc.d to propgate the script to the appropriate run levels. Do **man update-rc.d** for the full description of the tool.

---

### Post by soon82 on 2006-02-09
hi glut.. I had try man update-rc.d.... i read the manual a few time... and i also try...

but i can't get it ... may be i had misunderstand ..... do u have other method to solve my problem..

thank you.

---

### Post by Glut on 2006-02-12
Basically, type **update-rc.d ***xmail*** defaults**. You should be right.

---

### Post by soon82 on 2006-02-16
hi glut, i had done it... thank you for your help

bye bye

---

