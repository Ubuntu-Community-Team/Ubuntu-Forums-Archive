---
title: "Windows XP shared folder issue"
date: 2014-05-05
forum: Virtualisation
---

### Post by yan4 on 2014-05-05
Hi, I am at U14.04 and VB 4.3.10.

I have installed windows XP and I do know that I am running with very low RAM (4 GB total) but I don't think that THIS is the root of my issue here.

I have another Linux partition with a folder into this called 'Customers' that I shared and added to shared folders at my WXP VM. It doesn't keep in the list and I believe that it happens because I don't have the checkbox 'make permanent' to check it. How can I fix it?

Thanks!

---

### Post by voidofone on 2014-05-06
I assume you are referring to XP losing the mapping after it is restarted/period of time?...
While this is really a windows question, do this:

[in windows xp] start --> run -->  
[FONT=courier new][SIZE=2]net use * \\server\share /user:<domain|server-name>\user password /persistent:yes[/SIZE][/FONT]

---

