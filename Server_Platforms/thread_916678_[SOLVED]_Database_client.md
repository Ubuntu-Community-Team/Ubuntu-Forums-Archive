---
title: "[SOLVED] Database client"
date: 2008-09-11
forum: Server Platforms
---

### Post by kamaji792 on 2008-09-11
Hi,

This is a bit of an open question but I would be grateful for any advice.

I am about to start writing database for use where I work.  I am settled on using MySQL for the database.  The question I have is do I write the interface in PHP or Java.  I am an experience programmer but new to PHP and I get on fine with Java, with the exceptions below.

PHP seems a nice way to go as it will be easy to set up, running in a browser.  Looks fine if all you want to do it read the database.  The problems I have come when trying to use it to write to the database it starts getting messy if you want error checking.  Additionally I still have not worked out a good way of dealing with variable amounts of data (like say telephone numbers in a contacts database).

Java I really like as a programming language but I have never got to grips with laying out swing interfaces.  Though when I have had to do it I usually manage to cobble something together.  Why it does not come with a native way of positioning items using pixels I don't know.

Any advice or good books to read gratefully received.

---

### Post by windependence on 2008-09-11
Unfortunately, one of Java's weak areas is layout managers. gridbaglayout is the most flexible and powerful, but far from easy. Here is a decent tutorial:

[http://java.sun.com/docs/books/tutorial/uiswing/layout/visual.html](http://java.sun.com/docs/books/tutorial/uiswing/layout/visual.html)

Also, to simplify your life, try one of the visual IDEs like NetBeans, or Eclipse.

Personally, knowing a bit of Java and a wee bit of php, I would say you will get the most fleibility out of writing a php interface even though you will probably do more coding.

Take a look at this:

[http://www.nusphere.com/products/php_wysiwyg.htm](http://www.nusphere.com/products/php_wysiwyg.htm)

[http://www.phpedit.com/](http://www.phpedit.com/)

There are many more, I am sure, but I haven't done any major coding in quite a while.

-Tim

---

### Post by volkswagner on 2008-09-11
You can take a look at PunBB.  It is a php based forum site builder.  It may not be exactly what you are looking for.  You may be interested in checking it out, to see how it handles php and interacts with the database.

[https://help.ubuntu.com/community/PunBB]("https://help.ubuntu.com/community/PunBB")

---

### Post by kamaji792 on 2008-09-15
Thanks for the replies.  I've been a bit busy and only just got back to this but I am looking into it now :)

---

### Post by kamaji792 on 2008-09-24
To close this thread.

Thanks to **windependence** mentioning the **NetBeans IDE**.  I looked into this and it is the best visual IDE I have used (not that I used that many, mainly JBuilder).  On top of that Java is my sort of programming language (I started with C) so I am going down this route for writing the database interface.

It did take me a while to work out how to configure MySQL to accept request from my Java programs but I got there.

I still think that I will use PHP for some of the reading of the database but the data entry will be done with Java.

Thanks again.

May the source be with you

Kamaji

---

