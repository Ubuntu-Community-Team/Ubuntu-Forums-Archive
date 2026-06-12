---
title: "New user config"
date: 2010-06-20
forum: Server Platforms
---

### Post by skidz on 2010-06-20
Hi all.. I am renting a ubuntu server, that at first came only with root user (which I didn't think ubuntu could do).. So first thing I did was make a new user:

sudo useradd -d /home/me -m me
sudo passwd me

Then I added that user to the sudoers
me   ALL=(ALL) ALL

When I log in as me now, in ssl.. Its very different. Tab will not work, up key.. so on.. no colors.. 

How can I fix this? 

I searched for a solution, but as you can imagine, something like this is hard to find in a search.

---

### Post by Bachstelze on 2010-06-20
Change your shell to something more sophisticated than dash. ;)

```
chsh -s /bin/bash me
```

---

### Post by skidz on 2010-06-20
Worked Perfectly :D Thanks a bunch!

---

