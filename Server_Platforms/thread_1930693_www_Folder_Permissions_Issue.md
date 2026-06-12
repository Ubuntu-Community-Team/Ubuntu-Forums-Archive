---
title: "www Folder Permissions Issue"
date: 2012-02-24
forum: Server Platforms
---

### Post by ShogunJ on 2012-02-24
Hi All,

I wonder if someone can help? I have recently installed the LAMP server on 11.10. My only issue is I would like to remove any permission issues from the var/www folder completely, so I can read write and share freely?

I have installed Samba,and when I try to share I get 'Nautilus needs to add some permissions to your folder "www" in order to share'.

I have already included 'usershare owner only = false' to the conf file on Samba, but this is still not working..

Is there anyway to just remove any permission restriction from "www" all together?

Thanks All!
James

---

### Post by Lars Noodén on 2012-02-24
If you are going to be the only user of the directory, then you can simply take ownership of it and that will be that:

```

sudo chown -R james /var/www

```

If you are going to be sharing access to the folder with a bunch of people, then you can set up group access.

```

sudo addgroup webmasters
sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws  "{}" \;

# repeat for each user:
sudo gpasswd --add james  webmasters

```

---

### Post by ShogunJ on 2012-02-24
Ahhh that makes sense, I will give it a go.

Thank you greatly!!!

James

---

### Post by ShogunJ on 2012-02-24
Thanks Lars,

But I am still getting

'Could not change the permission of folder "www"'

Also is there a way to add guest to a group?

Any ideas?

** Edit ** Seems only to be when I try to add r/w permissions etc ??

---

### Post by Lars Noodén on 2012-02-24
If you change group membership, you have to log out and then log back in for it to take effect.  Which method are you trying?

---

### Post by ShogunJ on 2012-02-24
Using the latter bud.


sudo addgroup webmasters
sudo chgrp -R webmasters /var/www
sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws  "{}" \;
sudo gpasswd --add james  webmasters

Didnt get any errors, seemed to work fine, just wont allow me to right click and share the folder with read/write permissions?

---

### Post by Lars Noodén on 2012-02-24
With those steps, everyone in the group 'webmasters' should have read-write permission.  To further change the permissions, you need to be owner of the folder or else use sudo/gksudo.

---

### Post by ShogunJ on 2012-02-24
Ahhh, would there be no way of modifying the folder from another computer on the same network?

I can access the folder from my windows laptop, but only read only.

Is that as far I am going to get?

---

