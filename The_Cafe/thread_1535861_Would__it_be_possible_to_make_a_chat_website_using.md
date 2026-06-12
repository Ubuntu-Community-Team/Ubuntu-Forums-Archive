---
title: "Would  it be possible to make a chat website using HTML5?"
date: 2010-07-21
forum: The Cafe
---

### Post by TheNerdAL on 2010-07-21
So I have an idea for a site that I think will grow big like Facebook and Twitter, it's a chat site that is like Xat but a bit better and I would like to ask if it's possible to replace Flash with HTML5?

---

### Post by mendhak on 2010-07-21
Depends on your skills.  HTML5 is just a specification, what will allow you to use the <canvas> tag as a drawing surface - that's your main area of work, with knowledge of javascript and CSS.  

I hope you're not basic your decision off the "omg html5 is going to replace flash!!1" hype.  It's simply making a certain feature available to you, but how far you go with it depends on your skill as well as scripting language limitations.  There will still be areas where flash does things far better than you could ever do with your canvas.

---

### Post by TheNerdAL on 2010-07-21
> **mendhak said:**
> Depends on your skills.  HTML5 is just a specification, what will allow you to use the <canvas> tag as a drawing surface - that's your main area of work, with knowledge of javascript and CSS.  

I hope you're not basic your decision off the "omg html5 is going to replace flash!!1" hype.  It's simply making a certain feature available to you, but how far you go with it depends on your skill as well as scripting language limitations.  There will still be areas where flash does things far better than you could ever do with your canvas.

I think it's possible to replace Flash, we never know. ;)

---

### Post by fatality_uk on 2010-07-22
Start here:
[http://adityayadav.com/DeployingHTML5.aspx](http://adityayadav.com/DeployingHTML5.aspx)

Understand this:
[http://en.wikipedia.org/wiki/Web_Sockets#Server_Implementations](http://en.wikipedia.org/wiki/Web_Sockets#Server_Implementations)

Look at this:
[http://html5demos.com/postmessage2](http://html5demos.com/postmessage2)


30 minutes coding should see you with something. I created a small local chat

---

### Post by Merk42 on 2010-07-22
> **mendhak said:**
> I hope you're not basic your decision off the "omg html5 is going to replace flash!!1" hype.
**+1**


> **TheNerdAL said:**
> So I have an idea for a site that I think will grow big like Facebook and Twitter, it's a chat site that is like Xat but a bit better and I would like to ask if it's possible to replace Flash with HTML5?

HTML5 alone? No

HTML5 with Javascript right now, MAYBE, though most of that is from Javascript, NOT HTML5


It is possible to make a non Flash, even without using HTML5, look at the chat in Facebook that you yourself mentioned.

---

### Post by murderslastcrow on 2010-07-23
Seeing as how CS5 itself has preliminary canvas support, I assume whatever you can make in flash will be convertible. It really does just depend on your skill level and ability to understand and take advantage of the technology available.

Of course, you need to incorporate CSS and Javascript for a lot of the final touches. Canvas doesn't do everything.

---

### Post by 3rdalbum on 2010-07-23
Most people think of Flash as being "The way that Youtube delivers videos". Flash is a LOT more than that. HTML5 can sometimes replace Flash for the video delivery, but not always, and it can't replace Flash entirely.

You could definitely make an HTML-based chatroom rather than a Flash-based one, but I think you'd still need a database backend.

---

### Post by asddf on 2010-07-23
This is already possible with Ajax/Javascript.

I've worked with Flash, HTML, Ajax/Javascript, PHP, SQL, so most web technologies.

I would quiet honestly go with Flash.....It can be a resource hog, but it's much more flexible.

---

### Post by TheNerdAL on 2010-07-23
I'm a noob, where do I begin to learn HTML5 and Javascript and everything in between? :(

---

### Post by Merk42 on 2010-07-23
> **TheNerdAL said:**
> I'm a noob, where do I begin to learn HTML5 and Javascript and everything in between? :(
I think it's best to figure out what specifically you want to do and learn that way. You mentioned a chat room, and asddf has said it's already done with Ajax/Javascript. So just search for making a chat room with Ajax and javascript and it may lead you in the right direction.
It may also be way over your head and you'd have to start with a simple "hello world", or maybe an existing library like jQuery, mootools, prototype, etc.

Keep in mind HTML5 isn't really viable right now as it isn't finished and no browser supports everything and a lot of browsers support none of it. Don't go "oh HTML5 is the new hip buzzword I want to do that". Think "I want to do a chat room, but not use Flash, what is the best way to go about it?"

Javascript, I'd first just look into an existing library like jQuery to see what it can do.

---

### Post by Penguin Guy on 2010-07-23
HTML is a [markup language]("http://en.wikipedia.org/wiki/Markup_language") and cannot be used alone for chat, *PHP* chat, however, is more common than Flash chat. I've attached a basic PHP chat prgram I experimented on a while ago, perhaps it'll be usefull.


> **TheNerdAL said:**
> So I have an idea for a site that I think will grow big like Facebook and Twitter
> **TheNerdAL said:**
> I'm a noob, where do I begin to learn HTML5 and Javascript and everything in between? :(
Good luck.

---

### Post by tadcan on 2010-07-23
If you want to learn HTML then have a look at [http://www.w3schools.com/html/](http://www.w3schools.com/html/) which will show you the basics.

The biggest thing to know is that HTML code is changing, some tags such as <bold>word</bold> is deprecated will still work. Browsers are very permissive, incorrect code can work. So use [http://validator.w3.org/](http://validator.w3.org/) to check your code.

This is important for HTML 5 because the deprecated code will be removed. If you find tutorials online check the date, if it over three or four years old it may include old code.

---

### Post by phrostbyte on 2010-07-24
You don't even need HTML5 to make a chat website. The major thing you'd probably use is AJAX, which is supported in like 99% of all web browsers. :)

---

### Post by phrostbyte on 2010-07-24
mispost

---

