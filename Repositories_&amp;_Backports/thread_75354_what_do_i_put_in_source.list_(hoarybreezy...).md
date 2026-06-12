---
title: "what do i put in source.list (hoary/breezy/...)?"
date: 2005-10-13
forum: Repositories &amp; Backports
---

### Post by broseamus on 2005-10-13
i have installed hoary and did 'apt-get dist-upgrade', does that make my installation Breezy, or do i have to change my source.list to breezy first?
If it did made my installation to Breezy do i need to change source.list as well?

---

### Post by majikstreet on 2005-10-13
[QUOTE=broseamus]i have installed hoary and did 'apt-get dist-upgrade', does that make my installation Breezy, or do i have to change my source.list to breezy first?
If it did made my installation to Breezy do i need to change source.list as well?[/QUOTE]
If you are on Hoary, you need to change all instances of hoary to breezy in your /etc/apt/sources.list and comment out the backports for now because they don't work.

---

