---
title: "Apache2 / PHP5 / mySQL5 HELP!!!!!"
date: 2006-08-08
forum: Server Platforms
---

### Post by JonM1827 on 2006-08-08
I somehow made it so that whenever I try to access a php file through apache it only wants to save it... not just open...

so me being an idiot, I tried to apt-get --purge remove apache2 php5 (and a couple of other things)... then reinstalled... this didn't work, so I tried to delete the directories in /etc where there were files containing this programs (figuring they would re-install)... but they don't...

so now im even more screwed, because I don't have any of the /etc/apache2 or /etc/php5 folders.... or anything that was in the /var/www folder... (because i deleted the directories :sad:)

what can I do to get everything back up and running... or did i just completely F myself :confused: 

Any help is greatly appreciated,
-Jon

---

### Post by Brennan on 2006-08-08
I'm having the same problems, except that I somehow fixed the method where I would point to a .php file and it tries to open it or save it.  Now I'm having a problem where I only see the code when I point Firefox to any .php extension on my web server.  Any and all help will be greatly appreciated!

---

### Post by Brennan on 2006-08-08
Well, I found my answer!  If anyone else is having problems with a web server shooting out code when pointing to a .php file, add this line at the command prompt:

```
sudo a2enmod php5
```

---

### Post by JonM1827 on 2006-08-08
So is there any way to get those folders back? 
(especially the ones that were in the /etc [i.e. the apache2 folder with the conf files] folder)
because apparently i cant do much without them :p

Thanks,
-Jon

---

### Post by harisund on 2006-08-08
purge and reinstall the package apache2-common. 

Next time you delete a directory and want to reinstall it find out what package installed it by doing ```
dpkg --search filename
```

A quick dpkg --search /etc/apache2 reveals apache2-common is the package.

---

### Post by JonM1827 on 2006-08-08
OMG!!!! Thank you SOOOOOOOOOO much....

Now apache will acually load / php files wont ask to be saved...

you are a lifesaver :KS 

-Jon

---

### Post by Brennan on 2006-08-09
Awesome!  Thanks, Harisund, for the tip.  

Jon, don't delete any more files! ;)   I was searching how I fixed the same problem I had as you, but I used Synaptic and downloaded like 50 packages that were related to PHP and Apache, so I had a long list to run down.

Now we're on the path to enlightenment (for the time being) and hopefully we won't be hit with anymore nice surprises that make us ](*,)

---

### Post by JonM1827 on 2006-08-09
haha yeah... i should really work on that :p

Thanks again for all of the help... you 2 really saved me!!!

-Jon

---

### Post by harisund on 2006-08-09
You could use the package management link in my signature to find out most package-related commands you will likely need to know, before you delete folders :D

---

