---
title: "[apache2] - run virtual hosts with different users"
date: 2018-04-16
forum: Server Platforms
---

### Post by dam034 on 2018-04-16
Dear users,

I have some virtual hosts configured in my VPS, but they are running under the same user, www-data, and this involves some security problems.

I thought to run each virtual host with a different user, so a website under a vh can't damage the others.

I tried to set this in vh1.conf:
```
User vh1
Group vhosts
```
And I also created vh1 user in ubuntu.

But when I call phpinfo() I see in each virtual host that the user is www-data.

How can I fix this issue?

Thanks

---

### Post by SeijiSensei on 2018-04-16
You can't do this unless the virtual hosts listen on ports other than 80.  Then you could run separate instances of apache for each port running as different users.

The better question is why having www-data be the only user is a security problem.  The www-data user should have extremely limited write privileges or no write privileges at all.  Users could have www-data as their group with 750 permissions,  but only the users themselves should be able to write into the directories under the DocumentRoot.

My virtual hosts have a DocumentRoot that points to a directory under the user's home with group www-data and 750 permissions.

---

### Post by dam034 on 2018-04-18
So what you advice me?
And what shared hosting companies do on their servers?

Thanks

---

### Post by SeijiSensei on 2018-04-19
My advice was to enforce strong security on the individual users. Unless you tell us specifically what the "security problems" are, that's all I can suggest.

---

### Post by dam034 on 2018-04-23
I want to avoid that the website under a virtual host can damage another of them.

As shared hosting.

Thanks

---

### Post by SeijiSensei on 2018-04-23
At a minimum, set the permissions on the website directories and files as full privileges to the owner, and read-only to everyone else.  The only way one person can "damage" another website is if you let them all write into each others' directories.  

In general, though, I'd choose a more stringent setup.  First I'd set the default home directory permissions to 711 so only the owner can touch the files therein, but others can see though not read them.  Then set up a subdirectory under each home that contains the website files. Put that directory in the same group as www-data and set the directory's privileges to 750.  Then the owner and apache can read the files, but no one else can touch them.  Make that directory the DocumentRoot for the corresponding virtual host in Apache.

---

