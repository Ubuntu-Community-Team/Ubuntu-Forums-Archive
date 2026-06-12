---
title: "Updating PHP"
date: 2009-07-23
forum: Server Platforms
---

### Post by chrislynch8 on 2009-07-23
Hi,

I have Ubuntu 6.06 LTS and it has PHP 5.1.2 on it I want to upgrade to PHP5.2.10

How can this be acheived? When I run aptitude update, upgrade it keeps the PHP 5.1.2

Rgds
Chris

---

### Post by dragos2 on 2009-07-23
> **chrislynch8 said:**
> Hi,

I have Ubuntu 6.06 LTS and it has PHP 5.1.2 on it I want to upgrade to PHP5.2.10

How can this be acheived? When I run aptitude update, upgrade it keeps the PHP 5.1.2

Rgds
Chris

It is normal. Only when there are security updates the Ubuntu buildin mechanism will update
the corresponding applications.

If you want the latest version you should install it by hand.

---

### Post by chrislynch8 on 2009-07-23
OK, perfect

When I do an upgrade next time will aptitude overwrite my php install?

Rgds
Chris

---

### Post by Cheesemill on 2009-07-23
Ubuntu Backports may be what you're after.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

