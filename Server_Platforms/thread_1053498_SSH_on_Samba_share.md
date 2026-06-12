---
title: "SSH on Samba share"
date: 2009-01-28
forum: Server Platforms
---

### Post by Zillion on 2009-01-28
Hi,

After struggling a lot I managed to setup Ubuntu server.

I created a Samba share under my home user folder which works fine. Also I setup SSH which also works ok on my home user folder, but has no upload, create or erase rights on the share folder. 

I noticed that the share folder has owner id 65534, and all the files copied and created by Samba too. While files created by SSH get owner id 1000. Maybe thats got something to do with it?

How can I get SSH give create rights on the share? Bare with me cuz I am still a newbie ;)  thx

---

### Post by albinootje on 2009-01-28
> **Zillion said:**
>  I noticed that the share folder has owner id 65534, and all the files copied and created by Samba too. While files created by SSH get owner id 1000. Maybe thats got something to do with it?

How can I get SSH give create rights on the share? Bare with me cuz I am still a newbie ;)  thx

65534 is user nobody.
Is you ssh user the only samba user you need ?

You can use the "force user" in your samba share configuration, 
for example :
```

[test]
        force user = your_user
        comment = testing
        path = /var/www
        force group = your_user

```
where "your_user" is your ssh user.
Remember to recursively correct the permissions for your shared folder.
For example :
```

sudo chown -R 1000:1000 /home/your_user/your_share-name/

```

---

### Post by Zillion on 2009-01-28
Thanks a lot!! Was looking for hours now for a solution, however I learned a lot while looking, but this immediately is what I need!! 8-)

---

