---
title: "Having Permissions Issues"
date: 2006-11-21
forum: Server Platforms
---

### Post by cgCivie on 2006-11-21
First off, I'll apologise for being a complete and utter noob when it comes to servers. Second I hope this is in the right place since I suppose it borders on a how-to question.

I have installed and have running Ubuntu 6.06, I managed to get the GUI on top of that and everything appears to work well. Now, I am trying to install an LMS named Moodle, normally this involves dropping the Moodle folder into the server root, navigating to the setup page provided on localhost and following the steps there. 

My first problem came when I went to put the file in our document root. I kept getting a message saying I didn't have the permisions to do that (using the user I created during the install). I got around this by changing the ownership of the directory. I'd like to know what I was doing wrong with that part of the problem.

The second problem came once I browsed to local host I started the install process then the package came to a point where it needed to create a folder. It told me that the file needed to be readable and writeable by the server. It couldn't create the folder by itself and wouldn't recognise it even after I put the folder there myself. No idea what the problem is. 

Any help would be greatly appreciated, I'm going to have to learn how to do all of this in a one-hour window and I'm currently lost and on hour 6.

Also, I was wondering if it had something to do with not having FTP or something setup (which I have not been able to do for the life of me).

---

### Post by tturrisi on 2006-11-21
You need to be root to write to document root.  Open a termional and type gksudo Nautilus
enter your password
navigate & move the dirs & files

---

