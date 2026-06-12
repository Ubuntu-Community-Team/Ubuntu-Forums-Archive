---
title: "LAMP on Desktop 8.04.1"
date: 2009-04-26
forum: Server Platforms
---

### Post by DFHIII on 2009-04-26
I am a web application developer using MySQL, PHP, and Java Script.  I had LAMP installed on a previous machine the crashed.  I did not keep adequate notes to be able to recreate the development environment that was on the previous machine.  I have reached an impasse and would like help to get out of the weeds.

I did a clean install of desktop 8.04.1 using the full hard drive, no partitioning.  I installed all updates, about 287.

For LAMP I selected System/Administration/Synaptic Package Manager.  In Synaptic I selected Edit/Mark Packages by Task.  I then checked the LAMP server box and clicked OK.  The installation seemed to run without error.

I opened the browser (Firefox) and entered [http://localhost](http://localhost) and the page came back with "It works."

In order to test the browser with PHP I created an simple index.php file with the text editor and tried to save it in /var/www.  I got a message telling me I did not have permission to save a document in the folder.

How do I set permissions so I can save documents to /var/www?  Can I do it without going to the command line?  I will go to the command line if necessary.

On my previous installation under Applications/Programs I had two MySQL utilities.  On this installation there is no Programs option.

How do I add the Programs option to the Applications menu that contains the two MySQL utilities, one for administration and one for SQL editing and testing?

This time I am keeping good notes.

Thanks,

Dan H.

---

### Post by kanikilu on 2009-04-26
For the MySQL tools, I think there's a few options, but the one I've used most recently was the **mysql-admin** package from the repositories.

For permissions, I don't know if this is the most secure thing to do, but if it's just a test/development box, I don't see why you couldn't just chown /var/www to your user account...

---

### Post by steveneddy on 2009-04-26
IMHO - I would install the server version and add ubuntu-desktop

seems easier to me

---

### Post by nandemonai on 2009-04-26
For perms add yourself to the www-data group and chown the /var/www dir so that www-data owns it.

---

### Post by DFHIII on 2009-04-26
I searched Synaptic for mysql-admin under name, found it, and installed it.  That gave me the Programming/MySQL Administrator option.  I decided to try to search for just mysql under name.  In the list I found mysql-query-browser and installed it.  That is the other Programming option I was missing.

I used chown to change the permissions and was able to test php in the browser.  I am back to debugging my application -- right where I like to be.  

Thank you very much.

Dan H.

---

