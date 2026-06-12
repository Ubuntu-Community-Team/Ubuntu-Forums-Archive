---
title: "Joomla Help"
date: 2008-07-25
forum: Server Platforms
---

### Post by poisonelegy on 2008-07-25
I am not completely sure this is where I need to be. Anyway, I am trying to setup Joomla on my server, I can get most everything working except one thing. I can't seem to find the configuration.php file (it is unwriteable wherever it is). I thought maybe I should rename the configuration.php-dist but that seemed to make everything worse lol. Any ideas? Thanks.

---

### Post by Uluen on 2008-07-25
```
# updatedb
```

```
# locate configuration.php
```

```
# ls -la /path/to/configuration.php
```

```
# chmod 777 /path/to/configuration.php
```

---

### Post by Kolipoki on 2008-07-26
> **poisonelegy said:**
> I am not completely sure this is where I need to be. Anyway, I am trying to setup Joomla on my server, I can get most everything working except one thing. I can't seem to find the configuration.php file (it is unwriteable wherever it is). I thought maybe I should rename the configuration.php-dist but that seemed to make everything worse lol. Any ideas? Thanks.

I ran into the same issue in my first attempt to install Joomla. Nonetheless Joomla actually shows -in the last installation step- the whole code needed in the configuration.php file. 

So in my case (me a newb', gotta admit it was a primitive solution) I worked it around by creating a text file with that code pasted in it, and then naming it: configuration.php, then dropping it with WinSCP (working remotely from a WinXP machine) onto the Joomla directory. 

I'm not quite sure why Joomla does that, cuz in another installation this problem didn't happen at all.

---

### Post by poisonelegy on 2008-07-26
> **Kolipoki said:**
> I ran into the same issue in my first attempt to install Joomla. Nonetheless Joomla actually shows -in the last installation step- the whole code needed in the configuration.php file. 

So in my case (me a newb', gotta admit it was a primitive solution) I worked it around by creating a text file with that code pasted in it, and then naming it: configuration.php, then dropping it with WinSCP (working remotely from a WinXP machine) onto the Joomla directory. 

I'm not quite sure why Joomla does that, cuz in another installation this problem didn't happen at all.

I have tried that and it doesn't do anything, I go back to the install screen.

---

### Post by cariboo on 2008-07-27
If you read the installation instructions they suggest renaming the configuration.php-dist to configuration .php. 

> Step 1 – Create and edit the configuration file

Open the local directory where you uncompressed the Joomla! Core distribution directories and files and copy the file configuration.php-dist.

Rename the copied file to configuration.php, and open it in your code editor. 

To do this in a terminal type:

```
cp configuration.php-dist configuration.php
```

Then you can edit your configuration.php file to add your mysql username, password and database. by doing it this way you still have the default configuration file if you screw up the new one.

Jim

---

### Post by ndedobbeler on 2008-08-20
All,

I have also a small problem with Joomla & Xampp
The install of Xampp and Joomla went fine. I was able to get it working until....
I ran "/opt/lampp/lampp security". After that I cannot go to //localhost/joomla15 anymore because he gives me the error could not connect to the mysql database or something like that.

I think it has something to do with the deactivation of "The MySQL daemon is accessible via network." 

Anyone an idea how I can turn that back or how to access my Joomla again ;-)

Nico

---

