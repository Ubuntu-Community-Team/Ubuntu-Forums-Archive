---
title: "Tips to troubleshoot a server please!"
date: 2006-06-23
forum: Server Platforms
---

### Post by fizgig on 2006-06-23
I've got Ubuntu server running
[LIST]
[*]Samba (as a PDC)
[*]ldap
[*]apache2
[*]openvpn[/LIST]And probably more services that I forget.  It's a low-demand atmosphere so it runs fine..... except every 3-6 days or so it just dies.  None of the services work (can't browse to its web page, can't search the ldap dir, can't ssh into it and so forth).  I am able to ping it however.

I am able to log in locally to it and move around.  Trouble is, I don't know what to look for.   **ps -A **shows me services like apache2 are indeed running.

Can anyone give me some tips to help my troubleshoot this guy?

---

### Post by fizgig on 2006-06-23
I noticed that when the problem occurs, if I stop slapd and samba, apache and ssh start working again.

Anyone know what this means?

---

### Post by robert_pectol on 2006-06-23
[QUOTE=fizgig]I noticed that when the problem occurs, if I stop slapd and samba, apache and ssh start working again.

Anyone know what this means?[/QUOTE]

I'd take a look in your /var/log directory and start going through your system and server logfiles.  There are usually clues in them that can significantly help when diagnosing strange problems like this.  Specifically look for problems in the logs related to the two processes you mentioned above.

---

### Post by lamego on 2006-06-24
Did you checked the processes "top" ?

---

