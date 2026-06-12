---
title: "No write access to /var/www with nginx"
date: 2021-05-20
forum: Server Platforms
---

### Post by Blix775 on 2021-05-20
Hi! I am setting up a server with nginx to run a dotnet core page using the Piranha cms. I am learning as I go. I added my user to the www-data group but it still won't let me write to the /var/www/html folder to run the code from there. Is there anything else I should do to gain write access to that folder? I just need to be able to run a command that creates all of the folders for the Piranha cms page. Thanks in advanced.

---

### Post by CharlesA on 2021-05-20
> **Blix775 said:**
> Hi! I am setting up a server with nginx to run a dotnet core page using the Piranha cms. I am learning as I go. I added my user to the www-data group but it still won't let me write to the /var/www/html folder to run the code from there. Is there anything else I should do to gain write access to that folder? I just need to be able to run a command that creates all of the folders for the Piranha cms page. Thanks in advanced.

You can verify the permissions by running this command:

```
sudo ls -ld /var/www/html
```

---

### Post by The Cog on 2021-05-21
And verify your own group membership with ```
id
```
You will need to log out and in again to pick up changes to your group membership.

---

### Post by mIk3_08 on 2021-05-21
you can use super user or you have to access it via root server to have permission to all kinds of changes to the server data. you just have to be more careful so that you will not be able to ruin the server. I know you already know this one.
```
sudo su
```

---

