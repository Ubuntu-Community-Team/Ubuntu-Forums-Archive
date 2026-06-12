---
title: "Server setup question"
date: 2010-12-17
forum: Server Platforms
---

### Post by h4mm3r0g0d on 2010-12-17
Hi I'm going to be setting up our company with a in office server in the next few days. I wanted to use ubuntu as my servers OS but after reading some of the documentations I come to realize there is no X server in the server OS. I am OK with doing everything in terminal but would prefer to do some things in a graphic interface. Am I able to install the Xfree86 and be able to configure some stuff through that? Also the machine I am building for the server is not a true server machine just a really fast computer with lots of memory and space. The specs are a 3.1 AMD 64bit processor, 16gig ram, 2x 1TB hdd 7200rpm sata. 

If the X server isn't a possibility on the server OS, I have read you can install all the server repositories on the Desktop Editions. Would that be a better option for me?

Here is what I would like the server to do. I am going to be running quick books on the server with 1 workstation that is dedicated to it. We have 3 workstations and 3 users. We also would like to implement a Shared filing system and print server. Eventually when our current contract with our web host expires we would like to migrate the base website (not the ecom side) to this server. 

Any ideas would be greatly appreciated. 

Thank you,
Kyle Dunn

---

### Post by R.Bucky on 2010-12-17
Of course you can operate a GUI on a server. However, you open yourself up a few more holes for intruders than if you were to go just command line. Depending on the GUI applications that you want to use, you could always forward X11 over SSH for specific programs (e.g. Firefox, gufw, or others).

---

### Post by h4mm3r0g0d on 2010-12-17
Thanks for the information. Basically I will have the server sitting next to me while I'm setting it up so I wanted to be able to configure somethings quickly and easily. I don't plan on letting the GUI start up automatically and only want it for ease of use if I have to figure out whats wrong with the server. Thank you for the help. 

I have one last question that IDK if you all would be able to help with or not. I want to reformat the workstations into windows 7 clients to the server but I'm having a mental lapse. The client form is just the basic windows with it connected to a domain right. Obviously using SAMBA as the active agent simulating a PDC.

Thank you,
Kyle Dunn

---

### Post by drdos2006 on 2010-12-17
For a GUI you might want to consider Webmin from an external browser.

Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

