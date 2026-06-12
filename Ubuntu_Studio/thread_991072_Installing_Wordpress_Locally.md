---
title: "Installing Wordpress Locally?"
date: 2008-11-23
forum: Ubuntu Studio
---

### Post by Crackity Jones on 2008-11-23
This is about websites so I guess the thread should go in the multimedia category.

Right, I'm practising my web design skills and one of the things I need to get good at is designing themes for wordpress. One essential ingredient is having Wordpress installed locally alongside PHP and MySQL etc.
Back in my 'cave-man-days' I used XAMPP on XP. It worked fine.
I was wondering if there is an easy-to-install Linux equivalent. I'm guessing there probably is as so many developers use this platform.

Please help me out, cheers.

---

### Post by Stochastic on 2008-11-23
I think a read-through of this: [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress) will answer all of your questions and then some.

You may want to look at installing the server edition of Ubuntu too as I seem to recall LAMP being quite easily configured on fresh installs.

---

### Post by paulmerchant on 2008-11-24
If you are used to running WordPress on XAMPP, why not do the same thing. Just download XAMPP and unzip it into your opt folder and you're off. (If you get stuck with anything, XAMPP provides some instructions for Linux.)

---

### Post by osarusan on 2009-05-25
Hi,

I also wanted to do the same thing as OP. I followed the instructions on [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress) and I've hit a wall.

I think I have things set up correctly. I can access phpmyadmin from localhost and files I put in my local directory show up in firefox if I point it to localhost. The problem is, after installing wordpress in Ubuntu, I get a 404 error if I go to [http://localhost/wordpress/](http://localhost/wordpress/)

The files are definitely there! But why does it error??




Edit:
I don't know why, but it works now, after following the directions here:
[http://www.jonathanmoeller.com/screed/?p=235](http://www.jonathanmoeller.com/screed/?p=235)

---

### Post by Stochastic on 2009-05-25
If the files are there and you get a 404 error, chances are that it's stemming from incorrect permissions set somewhere.  Good to see you've solved it now though.

---

