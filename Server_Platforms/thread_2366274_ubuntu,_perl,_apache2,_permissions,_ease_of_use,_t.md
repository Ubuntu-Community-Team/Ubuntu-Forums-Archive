---
title: "ubuntu, perl, apache2, permissions, ease of use, total noob"
date: 2017-07-15
forum: Server Platforms
---

### Post by jamroll on 2017-07-15
hi, folks.

name's jarett, or jamroll...doesn't matter.

i'm a true noob with *nix OS.  Just rid myself of the most tenacious virus ever created, MS Windows (specifically win10).  anyway.  i've made SOME progress in getting things to work on this new setup - ubuntu 17.04.  Running apache2.  Opened up my browser, and pointed it at [http://localhost/](http://localhost/) and got the expected "welcome" page that is setup by default by apache.  i then deleted that file, and dumped all of my perl scripts into the same folder index.html lived in.  changed the permissions so i could edit and such.  reload the browser page, and i get a 403 Forbidden msg.  I don't even know what to search to correct this error.  I know what it means - i am forbidden from access the file.  right.  vague, and so cryptic.

i don't want to have to continually "sudo" into my files, that's cumbersome and hugely time consuming - especially when my password is rather tough to type - a few symbols, letters and numbers.  even more inconvenient when i'm working in the dark.  anyway....this is VERY frustrating, indeed.

I just need unfettered EASY access to these files so i can continue my WORK.  this having to fart around in terminal all the time is just plain silly.  There HAS to be a better and easier way....please help me.  it's important i get back to work rather than dickin around with sudo, and gksudo all the time...

---

### Post by jamroll on 2017-07-15
alright, i fixed the 403, and now i get my code displayed in the browser, instead of apache actually running the script...so, clearly i have to setup the .conf file correctly.  searches of the web tell me i gotta download something, and compile it.  this is WAY TOO MUCH WORK! It was really simple before i transitioned from windows.  all i had to do was uncomment one line in the conf file and add a couple of extra bits to the server section of the conf file and i was good to go...this is turning into a MAJOR PROJECT!!!  MAJOR.  this is FAR too complex.  There MUST be a simpler way...dropping in and out of terminal, and sudo'ing in/out of things is super boring and having to enter my password all the time is getting really really tedious!

---

