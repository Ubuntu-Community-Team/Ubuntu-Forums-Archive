---
title: "Openfire Server"
date: 2008-03-20
forum: Server Platforms
---

### Post by mreynaga on 2008-03-20
ok this is giving me fits. i am trying to install and configure Openfire and i get all the way to the point where i need to add it to startup and when i give the command:

update-rc.d openfire defaults

it tells me that openfire file or directory does not exist. 

yet when i cd into the directory and list the contents there it is.

anyone have any experience with this it is driving me nuts.

thanks

---

### Post by cdenley on 2008-03-20
Are you sure the file is there?
```

ls -l /etc/init.d/openfire

```

---

### Post by mreynaga on 2008-03-21
nevermind. i stripeed the server back down to the core install and started over and it worked the second time, hard to tell you what happened as i am pretty positive i did everything exactly the same. 

its up and running and i am loving it.

thanks anyway

---

