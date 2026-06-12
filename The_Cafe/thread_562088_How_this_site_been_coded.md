---
title: "How this site been coded"
date: 2007-09-28
forum: The Cafe
---

### Post by Yizi on 2007-09-28
I'm really interested to make a site like this, but anyone know where i can get the special Yahoo Messenger code for it?

[http://www.xeeber.com/](http://www.xeeber.com/)

What is Xeeber?
Xeeber is a professional online service which can help u to recognize the status of all Yahoo users, to see who is online, offline or invisible mode easily.

---

### Post by Yizi on 2007-09-28
**I foudn this as well i think coders know what this is all about i don't get it:**

How does it work?
When you make a query, this website connects to a Java backend using PHP and Ajax technology! The backend uses YMSG protocol to connect to Yahoo! Messenger server and logs in multiple Yahoo! bots. Every time you make a query one of those bots sends a special packet to Yahoo! Server which has different responses for Offline and Invisible, and that way our program finds out the user's real status.

---

### Post by happysmileman on 2007-09-28
> **Yizi said:**
> **I foudn this as well i think coders know what this is all about i don't get it:**

How does it work?
When you make a query, this website connects to a Java backend using PHP and Ajax technology! The backend uses YMSG protocol to connect to Yahoo! Messenger server and logs in multiple Yahoo! bots. Every time you make a query one of those bots sends a special packet to Yahoo! Server which has different responses for Offline and Invisible, and that way our program finds out the user's real status.

If you don't get it I wouldn't try implement it, basically it connects to the Yahoo messenger service using a Bot, checks if the user is online, and then returns it to the site. 

Try do it in stages, first of all make a bot for Yahoo (not sure how difficult, I've only made IRC bots which would be much easier) and have it check to see if someone's online.

Then try get a PHP script to call that program with the argument of the username.
Then finally you need to incorporate that into a webpage, and have AJAX set up (maybe try without AJAX first)

And remember, object oriented programming will be your best friend if you do it like this, all the bot commands and variable are in one class, that way you can change around everything else in the program without changing that object at all, or you can add features to it with minimal changes to program, which is useful for any large project.

---

### Post by Yizi on 2007-09-28
I kind go what you mean but is there not any ready made code for this because i found another website exactly like this. :-s

---

### Post by USPB on 2007-09-28
I think its coded using PHP

---

### Post by mostwanted on 2007-09-28
> **Yizi said:**
> **I foudn this as well i think coders know what this is all about i don't get it:**

How does it work?
When you make a query, this website connects to a Java backend using PHP and Ajax technology! The backend uses YMSG protocol to connect to Yahoo! Messenger server and logs in multiple Yahoo! bots. Every time you make a query one of those bots sends a special packet to Yahoo! Server which has different responses for Offline and Invisible, and that way our program finds out the user's real status.

The reason you don't get it is probably because you - I assume - don't know anything about programming. If you want to understand it you have to *learn* it. You won't learn to program servers and clients by creating a topic on a message board.

Sorry, if it seems like I'm being harsh, but tell me, do you expect to understand the finesses of other crafts too *just like that*?

---

### Post by Old Pink on 2007-09-28
It's not the coding he's interested in, despite his idiotic requests.

Visit [http://www.vbulletin.com/](http://www.vbulletin.com/)

Pay for and download that. Upload it to a host, and buy a domain. You have your own forum, just like this, and many other vBulletin forums.

Minimal coding knowledge required.

Frankly, if you didn't understand the extract:> When you make a query, this website connects to a Java backend using PHP and Ajax technology! The backend uses YMSG protocol to connect to Yahoo! Messenger server and logs in multiple Yahoo! bots. Every time you make a query one of those bots sends a special packet to Yahoo! Server which has different responses for Offline and Invisible, and that way our program finds out the user's real status.you posted, you have no chance of starting anything remotely code-related on the internet, yet.

---

### Post by Yizi on 2007-09-28
Too harsh but thanks at least i know what I'm doing now.

---

