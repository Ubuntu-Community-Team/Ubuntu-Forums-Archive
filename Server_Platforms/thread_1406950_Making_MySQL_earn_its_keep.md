---
title: "Making MySQL earn its keep"
date: 2010-02-14
forum: Server Platforms
---

### Post by Vegan on 2010-02-14
At present I use MySQL like lots of other web operators to support the forum on my site. Its easy to install so its very popular. No problem.

Given that the forum messages are small text items it is light duty indeed.

So how about images, at present I use some PHP code to scan a folder for pics and show them. Crude but effective, the folder becomes a defacto database.

Would it be all that hard on MySQL to host the images along with additional information such as say GPS details all searchable from PHP SQL statements?

How about an image that contains elevations for each pixel.

An examply of a lot of POST activity, consider the old [Shoemaker-Levy]("http://en.wikipedia.org/wiki/Comet_Shoemaker-Levy_9") comet that smacked Jupiter some 15 years ago now. I recall hearing that 1 million images were dispatched from JPL alone to the database in 3 weeks. That is a lot of disks even today.

So can MySQL keep up with that much of a flood?

---

### Post by Satoru-san on 2010-02-14
use php's function base64encode.

---

### Post by theDaveTheRave on 2010-02-23
Vegan,

I have a bunch of database tables that have something like 4 million entries (with 15 fields in each entry).

it takes my old laptop (500mb memory, 1.2ghz) about 15 minutes to push all of that through a terminal.

MySQL will definately be able to handle the data for you. The question is how long does it take to load any given page / image??

The solution would be to hold the image (and pixel data) and then get the user to demand it if required. Throw up a little dialogue box mentioning that it may take a while for all the data to upload to the page when the user confirm that they really want it.

Then you can get away with just sending a "small" version to everyone, and they can then select the extra info if required.

Also if you are planing on using large full screen "high def" images that will be a LOT of pixels !

should be fun!

David

---

