---
title: "accessing www root directory with SSH"
date: 2008-02-09
forum: Server Platforms
---

### Post by william5271 on 2008-02-09
I have an ubuntu server edition server and I want to be able to use ssh to work on files in the www root folder. I haven't turned on the root account feature, I just have a primary account I use. I can't edit stuff in the /var/www/ folder with my account. Should I set up root and login using root or is there a safer way to allow my user account to have access rights to the /var/www/ directory?

---

### Post by faulkes on 2008-02-09
> **william5271 said:**
> I have an ubuntu server edition server and I want to be able to use ssh to work on files in the www root folder. I haven't turned on the root account feature, I just have a primary account I use. I can't edit stuff in the /var/www/ folder with my account. Should I set up root and login using root or is there a safer way to allow my user account to have access rights to the /var/www/ directory?

Typically /var/www/ is owned by root:root, the easiest to allow yourself to move and or edit files in there is to change permissions.

You should never be doing anything as root, always use sudo for that.

Therefore, my suggestion would be to change to root:admin and give the admin group write permission, alternatively you could chown it to your own user group (this would be safer), or if you have many users, create a www group and use that.

```

sudo chown /var/www root:<my username> or admin

and then

sudo chmod g+w /var/www/

```

Finally however, the safest way would be to create a new site for apache, then create that directory in /var/ww and give it permissions for your user and user group, ultimately that would be best solution as it wouldn't impact any default system created directories.


Faulkes

---

### Post by rickyjones on 2008-02-10
> **william5271 said:**
> I have an ubuntu server edition server and I want to be able to use ssh to work on files in the www root folder. I haven't turned on the root account feature, I just have a primary account I use. I can't edit stuff in the /var/www/ folder with my account. Should I set up root and login using root or is there a safer way to allow my user account to have access rights to the /var/www/ directory?

I'd just slap sudo in front of your command so that you can edit those files. Example: sudo vim /var/www/index.html

-Richard

---

