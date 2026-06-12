---
title: "pour les expert de ubuntu"
date: 2010-04-10
forum: Tunisia Team
---

### Post by haha100 on 2010-04-10
ce probleme concerne les mise a jour quant je veut faire des mise à jour une fenetre signe une erreur regader
voici le message
W: Erreur GPG*: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible*: NO_PUBKEY A445E8CCD1A0D2FB
aider moi svp

---

### Post by l.billon on 2010-04-10
Bonjour,

Ce message provient d'une source qui a été mal installée, peux-tu donner le résultat des commandes suivantes:

```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

**Oublies ce que j'ai dit, la solution de stilling est meilleure**

---

### Post by stilling on 2010-04-10
@haha100
try this in terminal


gpg --keyserver keyserver.ubuntu.com --recv A445E8CCD1A0D2FB
gpg --export --armor A445E8CCD1A0D2FB | sudo apt-key add -


hope this helps you

---

### Post by haha100 on 2010-04-10
> **l.billon said:**
> Bonjour,

Ce message provient d'une source qui a été mal installée, peux-tu donner le résultat des commandes suivantes:

```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

**Oublies ce que j'ai dit, la solution de stilling est meilleure**

ok merci

---

### Post by haha100 on 2010-04-10
> **stilling said:**
> @haha100
try this in terminal


gpg --keyserver keyserver.ubuntu.com --recv A445E8CCD1A0D2FB
gpg --export --armor A445E8CCD1A0D2FB | sudo apt-key add -


hope this helps you

think you stilling

---

