---
title: "Can I temporarily disable my hostfile ?"
date: 2013-07-18
forum: Security
---

### Post by cogset on 2013-07-18
I suppose this can't be actually done,however what I actually wanted to ask is whether I can temporarily disable all the entries added to my hostfile,in case I need to check if a specific website doesn't open exactly because of some line added to that hostfile.

It has happened to me before,and going through the list manually commenting the lines that *could* prevent some website from loading is definitely annoying:I take a quick switch like **sudo ufw disable/enable** doesn't exist for the hostfile,right ?

---

### Post by CharlesA on 2013-07-18
No. You would have to comment all the lines out - or just create a new hosts file with just the default entries.

---

### Post by Hungry Man on 2013-07-18
Rename it temporarily. You could do

mv /etc/hosts /etc/hostess

and to undo

mv /etc/hostess /etc/hosts

---

### Post by HermanAB on 2013-07-19
Rename it, as described, but also be sure to make a new one with the default entries for localhost.

---

### Post by cogset on 2013-07-20
Yes,I should have thought about that...thanks.

---

