---
title: "problems with xampp and sendmail"
date: 2007-09-25
forum: Server Platforms
---

### Post by Moezzie on 2007-09-25
Im currently developing a site in which i want to give the user to send a mail through the mail() function in php.

When i started out it didnt seem to work at all. After some googling and reading i figured out i didnt have sendmail installed, so installed it and tried again. 

The first tile it seemed to work well, exep i didn receve the mail i sent. 
But after this it totally stopped working. As soon as i hit the sendbutton on my script nothing more happens.
The statusbar in Firefox just tells me "Wating for my.ip.adress"(my.ip.adress resembles my ip) and after some time the script stops because of connection timeout.

Ive read so much about this, could throw up everytime i see the word sendmail ;).

Anybody have any surggestions?

*EDIR*
My php.ini is changed to 
; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail -t -i

---

### Post by GodsDead on 2007-11-09
hey im havieng the same problem, i know how to sort this out on a windows machine, as you have a GUI to do all the setup for the send mail programme, but not in linux, im new to linux you see =[

---

