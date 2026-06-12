---
title: "Limiting User Access in SSH?"
date: 2005-03-14
forum: Server Platforms
---

### Post by Belldandy on 2005-03-14
Hello everyone,

Oh my server I have three accounts: myself and two other co-workers. I want to limit the SSH access of my coworkers to only their home directories and /var/www/userswebsitehere

How can I do this? And once i do this, is there a way to place a "shortcut" in the users home directory that will route them to the /var/www/userwebsitehere folder? For example, if they are in their home directory, they will see a "web" folder, then they type in "cd web" via their terminal, it will link them to /var/www/userswebsitehere/ instead of /home/username/web.

Any ideas?

Thank you!

---

### Post by deuce868 on 2005-03-15
You want to set up a chroot jail for them. 

Start here:
[http://www.google.com/search?q=debian+chroot+jail+ssh+user&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial](http://www.google.com/search?q=debian+chroot+jail+ssh+user&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial)

---

### Post by alastair on 2005-03-15
I think chroot jail might be overkill perhaps.

I think this is just a question of good unix permissions. Basically, who cares if they can "cd /" as long as they cannot read or change things they have no permission for?

For the "web" folder - same thing. Give them (as a group perhaps) the right permissions for this directory access and you are set (make a symlink on their desktop if you want). There's no need to complicate matters.

---

### Post by haselden on 2005-03-16
Try the AllowUsers directive in your sshd_config file.

A 'man sshd_config' will give you more info on it

---

