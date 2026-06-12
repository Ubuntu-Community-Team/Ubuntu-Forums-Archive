---
title: "A complete newbie help needed please!"
date: 2008-12-14
forum: Server Platforms
---

### Post by Neil_948 on 2008-12-14
Hi all,
        I have only just started working with Ubuntu i have ver 8.10 and have installed a web server for my website spent a few hours going through help sections and got the server configured so it can be used on the intranet and internet which was great although i have know uploaded the files that where needed to start configuring everything else to do with my site and when i localhost it everything works fine and shows what it should do. but when i try to access it externally i get an open message, Which reads "You have chosen to open (then no filename just a blank space) Which is a: PHTML file from: (then my website address) and then the usual underneath that asking what firefox should do open,save,e.t.c.

I have checked all the help pages and can only find answers to common setup problems of which i am past the stages that they are covering can anyone please tell me which file/service needs to be installed to stop this from happening.


Thanks in Advance.

---

### Post by bluefrog on 2008-12-14
restart apache. in the worst case reboot, should be ok afterwards. I encountered the problem not long ago.

---

### Post by sergevn on 2008-12-14
sudo /etc/init.d/apache2 force-reload

that should do the trick, restarting is not necessary.:popcorn:

---

### Post by Neil_948 on 2008-12-14
Thanks guys,
             I had restarted Apache2 for other changes that i had made to config files but reboot sorted it out.:p

---

