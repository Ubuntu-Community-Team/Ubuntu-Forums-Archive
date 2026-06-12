---
title: "Proper way to set up Webmaster account"
date: 2006-08-05
forum: Server Platforms
---

### Post by NobodySpecial on 2006-08-05
I want to give a trusted person SSH access to my server to run my website.  I want him to be able do everything he needs to run Apache, etc but not full root access.

So I first need to give him access to /var/www and I suppose I would change this directory to a different group and make him a member of the group so he can write.

Then I think I need to give him certain /sbin commands by:
sudo visudo
webmaster ALL=(root) /usr/sbin/(whatever commands)

So my question is, what root commands would I need to add for the webmaster to do his job?  Or is there a better way to accomplish all this?  I could simply give him a root account, but I thought there must be a way to give more limited access.

Thanks for any help.

---

