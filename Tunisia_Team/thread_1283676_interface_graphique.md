---
title: "interface graphique"
date: 2009-10-05
forum: Tunisia Team
---

### Post by Radskin on 2009-10-05
Bonjour,
je na'arrive plus a demarrer l'interface graphique d'ubuntu: j'arrive à voir le logo du demarrage, mais je n'ai pas la fenetre dans laquelle on met le login et le mot de passe
Pouvez vous m'aider à régler ce problème?
Merci d'avance

---

### Post by Neo31 on 2009-10-06
Hello Radskin,
Did you updated your system before this problem happens?
it's may be because of /etc/X11/xorg.conf file. Try to reconfigure it, for sure make a backup of it before you modify it.
I recommend you for now to just move it (rename it)
sudo mv /etc/X11/xorg.conf /etc/X11/bkp.xorg.conf
please report back if that solution worked for you. answer the questions and provide more details if possible.
Good luck.

Regards, Ahmed Sghaier.

---

### Post by Radskin on 2009-10-07
Hi,
I finally could access to the desktop: I just deleted all the packages including "fglrx". I think this is related to my graphhical card. Now, I have to setup new drivers ...
Thank you Neo31 for your help even though I didn't try your solution. The problem is not related to an update.

---

### Post by Neo31 on 2009-10-07
Great, I am happy for ya Radskin,
Good luck with setting up graphics on ur Linux.

---

