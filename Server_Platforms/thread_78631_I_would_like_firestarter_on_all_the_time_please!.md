---
title: "I would like firestarter on all the time please!"
date: 2005-10-18
forum: Server Platforms
---

### Post by mit on 2005-10-18
Hi,

I have just installed firestarter by using:

sudo apt-get install firestarter

it looks like yet another great program to me. When i took an online security check it said my machine was very good! :KS 

My question is that i would like it running evertime i have a "live" connection.

I have read the user notes and think that because i installed it via the sudo command it remains live. Am i right? 
It looks like as soon as i close the firestarter gui down it stops, as the blue icon disapeers. :confused: 

I have looked [http://www.fs-security.com/docs/persistence.php]("http://www.fs-security.com/docs/persistence.php")

here but am not 100 % on the Linux language yet. I am trying. 

Thanks for looking.

---

### Post by fannymites on 2005-10-18
It's a while since I used Firestarter but if I remember rightly, you need to minimize the config window rather than close it.  I think there's an option to minimize to tray.

---

### Post by mit on 2005-10-19
Oh, thanks! :)

---

### Post by A-star on 2005-10-19
firestarter is automatically started when you boot your pc.
The interface you see in Gnome is just that an interface.
When you close the interface it just keeps on running.

---

### Post by mit on 2005-10-19
oh, so even if i forget to applications.....system tools....firestarter... evertime i use my laptop i am still protected by it?

---

### Post by A-star on 2005-10-19
[QUOTE=mit]oh, so even if i forget to applications.....system tools....firestarter... evertime i use my laptop i am still protected by it?[/QUOTE]
That is correct.
you only use the gui of firestarter to configure it. (and sometimes restart or stop it).

So if you don't start the gui you are still protected.

---

### Post by mit on 2005-10-19
Thanks for your help A-star. :KS

---

### Post by towsonu2003 on 2005-10-19
sudo /etc/firestarter/firestarter.sh status

will show you whether it's running or stopped. If you do

sudo /etc/firestarter/firestarter.sh stop

then it will really stop (i.e. no firewall)-

sudo /etc/firestarter/firestarter.sh start 

will start it.

---

### Post by mit on 2005-10-19
Thanks! Another useful set of commands to add to my newbie notes!

---

### Post by gamerchick02 on 2005-10-25
Question:  Do I have to have the terminal running to use firestarter?  I started it there and it closes when I close the terminal.

Amy

---

### Post by gamerchick02 on 2005-10-25
Never mind.  I found the icon in my menus.  Silly me!  I should look before posting.

Thanks anyway,

Amy

---

### Post by cstudent on 2005-10-25
This is the link to the FAQ for Firestarter. I found it took care of most of questions.

[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

Bill

---

