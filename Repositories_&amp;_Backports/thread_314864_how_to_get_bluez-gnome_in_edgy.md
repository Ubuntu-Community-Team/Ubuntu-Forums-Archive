---
title: "how to get bluez-gnome in edgy"
date: 2006-12-08
forum: Repositories &amp; Backports
---

### Post by jimmi on 2006-12-08
Hi,

I wanted to have bluez-gnome in my edgy installation and, following the howtos found on the web, I added the feisty repositories and I created /etc/apt/preferences with:

Package: bluez-gnome
Pin: release a=feisty
Pin-Priority: 999

By installing it I got upgraded other 8 packages like libc6 and some other.

When, after that, I gave "dist-upgrade" I realized that apt wanted to upgrade a lot of packages to feisty release; after learning some more I added to /etc/apt/preferences some line:

Package: bluez-gnome
Pin: release a=feisty
Pin-Priority: 999

Package: *
Pin: release a=edgy
Pin-Priority: 700

Package: *
Pin: release a=feisty
Pin-Priority: 650

but after that apt was trying to remove gnome completely and upgrade several packages. I end up in removing the feisty repositories and now all is quiet ;) 
Now my questions are:

- are perhaps now my dependencies broken (for the packages upgraded the first time) and may I expect some problem in future upgrade? (or even earlier) How to check it?

- did I do any mistake with my "apprentice wizard" modification?

- or is this normal and I should upgrade all gnome to feisty release in order to obtain bluez-gnome?

Thanks in advance for your help :)

Jimmi

---

### Post by jimmi on 2006-12-08
I learned that in edgy exists one package that may do the same job for me: bluez-passkey-gnome.

Now comes one more question: how to know which packages are actually from feisty repository and downgrade them?

---

