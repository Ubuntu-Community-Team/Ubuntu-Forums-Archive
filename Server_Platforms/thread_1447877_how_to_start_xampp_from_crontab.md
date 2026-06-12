---
title: "how to start xampp from crontab"
date: 2010-04-05
forum: Server Platforms
---

### Post by tonjaa on 2010-04-05
i want to Xampp run and start all time when i start pc. i don know correct command 
for use crontab    when i want to use it i must delete ># m h  dom mon  dow  command
or not ?  please guide me by step .

---

### Post by richardjh on 2010-04-06
You don't use crontab to start services, you need to start the services at boot time using update-rc.d.

I would suspect for Xampp, you will need to start apache2 and mysql                                                                     
```
sudo update-rc.d apache2 defaults
sudo update-rc.d mysql defaults
```

I would strongly suggest you bin Xampp on Ubuntu and install a LAMP server using tasksel

```
sudo tasksel install lamp-server
```

This will configure apache to work with PHP and PHP to work with MySQL and set up services etc required to get you started.


With regards to your question on crontab, you do not need to delete the line # m h  dom mon  dow  command

It is a comment ( as it begins with a # sign ) so will be ignored. It is there to make it easier to remember which order to put the fields when adding entries.

Eg:
30 03 01 * * /path/to/script

Will run script at 03:30 on the first of each month.

For further help, check 

```
man tasksel
man update-rc.d
man crontab 
```

---

### Post by tonjaa on 2010-04-06
Thank you so much man .

---

