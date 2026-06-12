---
title: "DIY remote downloader- i made it myself :) it even works"
date: 2008-04-15
forum: Testimonials &amp; Experiences
---

### Post by matt freeman on 2008-04-15
this isnt one of the "wow i switched to ubuntu and i love it" posts, i switched a good few months ago, its a im happy 'cause i made something do exactly what i want post.

my aim was to be able to somehow pass download URL's to my server, and for it to automatically download them- so i could turn my laptop off at night, and my downloads would happily continue on.

i managed, it took me an entire afternoon, but i managed.

i found this - [http://www.linux.com/articles/59457]("http://www.linux.com/articles/59457")
which explains how not use "wget" to download a list of URLS, and to use a script to delete a URL from the file after wget has downloaded it.

next problem: get script to run when you put a URL into the file
after alot of searching i found "monit" which is a brilliant program, and will automate anything at all.

every 20 seconds monit checks the URL file, if the timestamp on the file is less than 20 seconds old, it runs the script to set wget downloading the url's in the file. 

so all i have to do, is open up the URL list from any computer i like (its in a samba share) paste in a URL, save it, close it and the file appears in the downloads folder (also a samba share)
its like magic.

im feeling quite proud of myself, my first bit of properly making use of linux.

Matt

---

