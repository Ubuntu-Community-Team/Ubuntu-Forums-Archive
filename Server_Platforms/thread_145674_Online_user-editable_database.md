---
title: "Online user-editable database?"
date: 2006-03-16
forum: Server Platforms
---

### Post by mgchan on 2006-03-16
I am looking for a simple web-based app that will allow users to enter text into an online database and then be able to view all the other data that has been entered.

For example, I would like to be able to specify a number of categories (say, 8 or 10) and then users can input the data for each category.  Each user's entry will be displayed in a sortable table that all other users can see.  Ideally they could also edit entries by just entering the same username or something.

Anyone know if something like this is available?  Security is not too much of an issue since the userbase would be fairly small and the data is not sensitive anyway.  I know it wouldn't be too hard to code, but I have almost zero experience in PHP or CGI.

---

### Post by Zelut on 2006-03-16
I have an editable contacts list PHP app that uses a mySQL backend for database storage.  You're welcome to check that out & alter it to what you need... its pretty basic.  If you have any programming experience (html/php) you should be able to figure it out to alter to your specs.

You can find it for download at my homepage (in the sig below)

---

### Post by rich on 2006-03-17
Have you discarded the phpmyadmin route ?

It's not pretty, but it works. If you create a mysql user with suitable permissions you can enter/view but not empty/drop. 

For a small number of users that are "close" to you it is a ready to wear option.



Rich

---

### Post by mgchan on 2006-03-17
rich: I considered phpMyAdmin but many of the users are far from computer proficient and I wanted something very simple.  

kyuaedz: I did check out your contacts app and it does look like it should work with some modifications.  It's something I can definitely work with - I can deal with scripting languages but just don't have the time to learn all the syntax.  Thanks!

One thing I've had a problem with is that apostrophe's don't work - they cause an error (at least in the fields that are varchar).  Is there anything that can be done about this?

---

### Post by majikstreet on 2006-03-17
as far as I remember, you have to escape the apostrophes - like /' or \' I can't remember which one it is.. you can build a script to do that automatically. .I think it's called sanitizing? well I would look online for tutorials that do guestbook scripts or form mails? also I think this may work - if you enclose stuff in double quotes rather than apostraphes.

[edit]try this: [http://us3.php.net/addslashes](http://us3.php.net/addslashes)  -- it makes much more sense than coding something yourself!

---

### Post by mgchan on 2006-03-17
Cool, thanks for the tip!  Looks like exactly what I need.

---

