---
title: "Ubuntu 10.10 and Apache 2.2"
date: 2010-11-27
forum: Server Platforms
---

### Post by ingeva on 2010-11-27
I've made several attempts to make Ubuntu server 10.10 work with the gnome desktop, and finally,
with an updated kernel (2.6.35-23) it worked.
However, when trying to update Apache with my own settings, I get the following messages:

```
apache2: Syntax error on line 203 of /etc/apache2/apache2.conf: Syntax error on line 1 of
/etc/apache2/mods-enabled/php5.load:
Cannot load /usr/lib/apache2/modules/libphp5.so into server:
libdb-4.7.so: cannot open shared object file:
No such file or directory
```I have placed the libphp5.so file into the location indicated, but that did not help.
libdb-4.7.so is nowhere to be found. Since Apache ends with an error my local
web pages are not found.

There are several other problems with this version and I can't find much understandable
information about the migration, but I'll take one thing at a time. Can anyone help?

---

### Post by windependence on 2010-11-27
Have you installed php5?
 
Try installing the libdb-4.7.so package.
 
-Tim

---

### Post by ingeva on 2010-11-27
> **windependence said:**
> Have you installed php5?
 Try installing the libdb-4.7.so package.
 -TimI have installed php5 and apache from the installation CD, and I updated them using these commands:

```
aptitude -y install apache2
aptitude -y install php5 php5-common php5-cli php5-gd

```I mentioned that libdb-4.7.so was nowhere to be found.
That includes searching from the Synaptic package manager.

The installation itself goes fine. The error occurs when attempting to restart the apache server:

```
/etc/init.d/apache2 restart
```Everything done in SU mode, of course.

---

### Post by Vegan on 2010-11-27
Try this

```
sudo dpkg -r --force-all php5
sudo apt-get install php5
sudo /etc/init.d/apache2 restart
```

---

### Post by windependence on 2010-11-27
Can you post the first 10 or 15 lines of your /etc/apache2/mods-enabled/php5.load file?
 
-Tim

---

### Post by ingeva on 2010-11-27
> **Vegan said:**
> Try this

```
sudo dpkg -r --force-all php5
sudo apt-get install php5
sudo /etc/init.d/apache2 restart
```Did that. Nothing new installed. Same error.

---

### Post by ingeva on 2010-11-27
> **windependence said:**
> Can you post the first 10 or 15 lines of your /etc/apache2/mods-enabled/php5.load file?
 
-Tim
There's only one line:

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

Maybe I should just delete it? :)

---

### Post by windependence on 2010-11-27
Well, if you delete it, php5 won't load. If you don't need php (and you don't necessarily need it for a web server) then you can safely delete it.
 
I think the problem is your php5 installation is hosed. Apparently, the ph module is dependent on the libdb-4.7.so package. If it was me, I would completely uninstall php5 and reinstall not from the disks but from the repositories. To uninstall:
 
```
 
sudo apt-get --purge remove php5 php5-common php5-cli php5-gd

```
[FONT=Courier New]Then reinstall php5:[/FONT]

```
sudo apt-get install php5 php5-common php5-cli php5-gd
```
[FONT=Courier New]
 
-Tim
[/FONT]

---

### Post by ingeva on 2010-11-27
> **windependence said:**
> Well, if you delete it, php5 won't load. If you don't need php (and you don't necessarily need it for a web server) then you can safely delete it.
 
I think the problem is your php5 installation is hosed. Apparently, the ph module is dependent on the libdb-4.7.so package. If it was me, I would completely uninstall php5 and reinstall not from the disks but from the repositories. To uninstall:
 
```
 
sudo apt-get --purge remove php5 php5-common php5-cli php5-gd

```[FONT=Courier New]Then reinstall php5:[/FONT]

```
sudo apt-get install php5 php5-common php5-cli php5-gd
```[FONT=Courier New]
 
-Tim
[/FONT]Well, this actually solved the problem!
I have re-installed php5 more times than I could count, but I did NOT remove it first.
It has evidently not been installed correctly from the CD.
Also, Apache worked perfectly without php, but of course it just used the files like they were html files or pure text.

Please allow me to ask: Was "hosed" a misprint? Whatever it was, what does it mean? F***ed up? :)

Thank you VERY much for your help! Why didn't I think of that? :)

Digression:
In the meantime I have also solved the other problems I had by myself, so I'm pretty proud of that, and happy that I'm finally up-to-date with the latest version. Couldn't use 10.04 Lucid because there was no connection from my wireless keyboard.
The problems were: Samba wouldn't start (Solution: used sudo restart samba)
and NFS crashed the computer when installing it (Solution: Make sure to CD into the correct directory in my install script).

Please allow me to keep this unsolved until I have your response.

inge

---

### Post by windependence on 2010-11-27
Yes, hosed did in indeed mean screwed up. :-)
 
Glad you were able to get it fixed. Just FYI, the latest and greatest is not always the best, especially with Linux. I am still running 8.04 LTS on all my production machines for one reason - they are STABLE. Packages will still get updated to the latest version for 5 years from the release date of 8.04 so I will stay with it until the next LTS release. 
 
-Tim

---

### Post by ingeva on 2010-12-10
> **windependence said:**
> Yes, hosed did in indeed mean screwed up. :-)
 Glad you were able to get it fixed. Just FYI, the latest and greatest is not always the best, especially with Linux.
-Tim
Thanks, and I agree, and I used 8.04 for a long time, but I also want to keep myself updated in small steps because there are new surprises with every update and I don't want to handle too much at one time.
I can still boot 9.10 if I want, and it shares the home directory with 10.10 without problems.

Now there's only one problem left to solve before I can move one computer (Server and backup) from the kitchen to the shed outside, where it can stay on 24/7 without making disturbing noise and free some space on the kitchen table. :)
I hope I can have that resolved this evening or some time tomorrow.

Ubuntu rules!

---

