---
title: "mysql configuration for server use"
date: 2008-04-29
forum: Server Platforms
---

### Post by ahlandberg on 2008-04-29
I am currently setting up my ubuntu box for a major software development project.
For this reason, I require to setup MySQL and configure it in exactly the same fashion as the server that the project will be hosted on. I have access to view the current system variables on the remote hosting server, but I need to know if/how I can change these config settings on my machine.

Sorry for the novice question, but this is the first time I really have to deal with the config myself.

Any help appreciated!

---

### Post by hyper_ch on 2008-04-29
I don't know what you mean or where config would be different...

---

### Post by Brazen on 2008-04-29
What are the "current system variables" on the remote hosting server?

---

### Post by cdtech on 2008-04-29
If you want to mirror the same as the server you could use rsync and using mysqldump to keep both the server and your box in sync with each other. I use this method for my web site development.

From my laptop:
```
mysqldump -u user -p database > database.copy
```

From my laptop:
```
rsync -e "ssh -ax" -avz --delete --stats /var/www/mysite/ webadmin@mysite.com:/var/www/mysite
```

From my laptop:
```
scp photolog user@mysite.com:/var/www/mysite
```

You could use the same procedure to keep in sync with your development project.

Hope this helps.......

---

