---
title: "Protecting Data From Cloning"
date: 2011-09-19
forum: Security
---

### Post by Brandoo_NZ on 2011-09-19
Hi,

I'm wondering if anyone has suggestions as to how to protect a system from cloning?

I understand it's near impossible to stop someone cloning a drive, but anyone have suggestions how to make it impossible to use the data?


If I were to hire out a computer system for a specific task, what would be the best way to ensure no one could just copy everything on the drive and duplicate what I've created?

Hope this makes sense

---

### Post by CharlesA on 2011-09-19
What exactly do you mean by "clone" ?

Encrypting the drive would be one thing, but that wouldn't exactly help if the machine is already booted up. Could jail the user or use the guest account, I support, but it would depend on what specific task that machine is meant to do.

---

### Post by tubbygweilo on 2011-09-19
If you give someone the means to physicaly access your data then you have little control over what they do with it. If using encrypted disk or data held withing something like a truecrypt container then you will have to give them the keys to access it. You could try and obscure the truecrypt key but security by obscuration is always second bets (if it works at all).

Can you keep the data on a web site you control and allow external users access to data under your control?

---

### Post by Paddy Landau on 2011-09-20
Once someone has physical access to your computer, all bets are off.

The only thing you can do is encrypt the data that the user must not have access to. But you cannot prevent the user from copying data that he needs access to.

---

### Post by walt.smith1960 on 2011-09-20
Would it be possible to keep your data on a removable drive?  Or create a /home directory for your stuff on a removable drive?  I don't know how to do it but it seems possible.

---

