---
title: "MYSQL Server resets my password?"
date: 2012-11-15
forum: Server Platforms
---

### Post by Jacob72 on 2012-11-15
Hello,

I keep on finding that my password for phpmyadmin no longer works. I have reset it a few times now but after a new boot I am locked out again?

Thanks

---

### Post by cj13579 on 2012-11-15
Sounds like there is something/someone trying an old or incorrect password and is locking your account. Is it just a particular account or for more than one?

---

### Post by Jacob72 on 2012-11-16
Just one.

---

### Post by cj13579 on 2012-11-16
Perchance is it the "root" account and is the box visible from the net?

---

### Post by Jacob72 on 2012-11-23
> **cj13579 said:**
> Perchance is it the "root" account and is the box visible from the net?

It was the root account, I only have one account, I am using lamp to test locally. I have not configured lamp to be visible on the net, but I am not 100% sure if it is, would I just find out the ip address and give it a go?

I had my sites set up outside of www/var folder, but have since completely removed apache2/phpmyadmin and am in the default folder. I am no longer being locked out of Phpmyadmin :)

Are there security steps I should take in regards to my personal folders that exist on my Xubuntu setup when running LAMP?

---

