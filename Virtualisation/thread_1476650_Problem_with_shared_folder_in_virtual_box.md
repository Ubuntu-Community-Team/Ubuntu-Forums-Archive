---
title: "Problem with shared folder in virtual box"
date: 2010-05-08
forum: Virtualisation
---

### Post by Naterader on 2010-05-08
I can't seem to add a shored folder in my virtual box. I can choose a file but can't click OK? I'm lost. Please help. PS sorry if this is a easy fix, I'm new. Thanks.

---

### Post by lmarmisa on 2010-05-08
Whitespaces are not allowed in the Folder Name. Delete these whitespaces chars or change the Folder Name to a different name like, for example, share.

---

### Post by Naterader on 2010-05-08
Thank you. I can't believe I didn't catch that myself.

---

### Post by Naterader on 2010-05-08
One more thing. Once I get into my VM (XP) the "virtualbox shared folder" isn't showing up on my network. How do i set up my network adapter to get this to show up?

---

### Post by lmarmisa on 2010-05-10
Select in your Network Adapter 1 interface of Virtual Box the Bridge mode (not the NAT mode).

---

### Post by Naterader on 2010-05-11
> **lmarmisa said:**
> Select in your Network Adapter 1 interface of Virtual Box the Bridge mode (not the NAT mode).

I've tried all the different combos of bridged or NAT or internal with all the different adaptor types (advanced) still nothing shows up in my VM

---

