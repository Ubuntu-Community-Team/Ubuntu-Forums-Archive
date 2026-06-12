---
title: "Starling. system would not boot after Update"
date: 2010-07-27
forum: System76 Support
---

### Post by Tart on 2010-07-27
My starling asked for Update yesterday, and it ran successfully. I shut it down after update and today it will not start :(. it only goes to purpley screen. You can move mouse for couple of seconds and then it freezes

Please help

---

### Post by msrinath80 on 2010-07-27
I don't know how or why, but a very similar problem occurred on my Lemur when I decided to change the grub2 theme from the default Ubuntu one to something called "solar".

Basically, I found that the way out of this problem was to get to one of the virtual consoles and run the update alternatives command again and reselect the Ubuntu theme.

I realize that this isn't the same circumstance as your problem, but at least you can try and see if you can get to a virtual console first? Dis you try a Ctrl+Alt+F1 or Ctrl+Alt+F2 yet?

---

### Post by Tart on 2010-07-27
Update: 

I pressed SHIFT during boot and selected recovery mode from GRUB.
Got to command line interface, restarted and everything works fine now. 
Not sure what happend, or why things got fixed.

---

### Post by isantop on 2010-07-28
Good to hear. Keep us updated on any other problems you have, or if this one recurs.

---

### Post by Tart on 2010-09-05
Help! Help! Help! It happened again. I updated yesterday and today it would not boot, same symptoms. Previous trick does not work!! I also tried booting into low-graphic mode - didn't help. I can get to command line interface.

Update. I think my starling decided to take a day off. It boots fine now. I saved syslog file, but it has so much info I'm not sure what to look for.

---

### Post by isantop on 2010-09-07
If it happens again, make a copy of your syslog (Best way is from the System76 Driver) and send it to us right away. I should be able to take a look in it and find out where the problem was. 

Otherwise, again, good to hear. Keep us updated!

---

### Post by Tart on 2010-09-10
It happened again :-(. It takes longer now and multiple restarts, and I'm not sure that fixes it.
I sent log files to [email]support@system76.com[/email] since they are too big to post them here. 

Thank you for your help.

---

