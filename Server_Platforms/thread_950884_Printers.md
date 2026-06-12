---
title: "Printers"
date: 2008-10-17
forum: Server Platforms
---

### Post by happyhacker on 2008-10-17
I want to take all our printers from locally windows connected to networked printers so we can reduce the number of them and make them available to all users. I haven't actually got a printer connected to the server itself currently.

What involvement should the Ubuntu server have in this role?

Is it best to buy some print servers so that I can have a printer (or two) in each room?

---

### Post by lykwydchykyn on 2008-10-17
That would probably be my preferred approach, it would save space and power.

How many users and printers are you dealing with, and how large is the space?

---

### Post by cariboo on 2008-10-17
It really depends on home many printers, and how many users you have. As well as how well supported your printers are.

Jim

---

### Post by happyhacker on 2008-10-18
We have 3 rooms on each floor and 3 of those rooms have 3 PCs but therse rooms are close together so I plan to reduce the printers to 1 in those rooms saving 6 printers.

Are the printers managed from the Ubuntu F&P server? How is it arranged so that the printer drivers are not installed on the PCs but just one place (the Ubuntu server or where)?

---

### Post by lykwydchykyn on 2008-10-18
Hrm.. three times three, plus three -- no minus six, carry the two... erm... Yeah sounds like a good plan to me :-)

Anyway, I can't claim to have done the driver sharing thing, but check this out:
[http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876](http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876)

---

### Post by happyhacker on 2008-10-19
Thanks, I'll have a good read of that. That does not look like a graphical setup process to me. I would have thought it would be simpler.

---

### Post by lykwydchykyn on 2008-10-19
> **cantthinkofanickname said:**
> Thanks, I'll have a good read of that. That does not look like a graphical setup process to me. I would have thought it would be simpler.

Well yes and no; once you understand the gist of what needs to be done to publish the printers and drivers in Samba, you can probably set it up using whatever graphical Samba admin tool you want.  

Here's another take on it that uses a slightly more graphical approach if that's what you like:

[http://www.netadmintools.com/art258.html](http://www.netadmintools.com/art258.html)

---

