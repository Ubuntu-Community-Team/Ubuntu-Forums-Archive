---
title: "Adding foreign key using MySQL Administrator fails!"
date: 2010-08-27
forum: Server Platforms
---

### Post by klaasvg on 2010-08-27
I want to setup my MySQL database and have MySQL up and running. I sill look for a good editor to add and configure my tables, it appears that MySQL Administrator is the only GUI client available.
But when I try to add a foreign key to one of my tables, there appears to be a problem. Both of my tables are InnoDB and both have a primary key.
-First I choose the tab "Foreign Keys" on my CLIENT table.
-Then I press the green + sign to add a foreign key, it is default named new_fk_constraint.
-I choose my table USER in the Refer.Table dropdownbox
-And then I should be able to match the FK field and the PK field in the box on the right... but this box is empty. Double clicking shows nothing. I only can drag the user_id of the USER table to it, but have no option to select the foreign column. 
What the hell is wrong here??? This client is years old and should be really REALLY working IMHO! I was told by a friend that there is no good  client availalble and therefore he is using some Windows program for this...

Any ideas?
TIA, Klaas

---

### Post by rubylaser on 2010-08-27
If you want a frontend for mysql, why don't you use phpmyadmin?

```
sudo apt-get install apache2 phpmyadmin
```

Browse to [http://ipaddress/phpmyadmin](http://ipaddress/phpmyadmin) login, and you can administrate mysql from a web browser.

---

### Post by craigp84 on 2010-08-27
> **klaasvg said:**
> I want to setup my MySQL database and have MySQL up and running. I sill I was told by a friend that there is no good  client availalble and therefore he is using some Windows program for this...


Sounds like the more sensible option! What's stopping you using the windows program instead?

---

### Post by klaasvg on 2010-08-27
OK thanx 4 your replies! I am a confident Ubuntu user and while I have one old PC running Windows, I would think that I am not the first person looking for a good MySQL client app... and I find it pretty strange that there appears to be no one for Ubuntu.
PHPMyAdmin is an option, of course but it is not a standalone GUI tool but it is usable indeed. I tried it but it is not as intuitive as some Windows clients I used in the past. So Microsoft still cannot be dismissed completely to my regret... ;)

---

