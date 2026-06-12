---
title: "Question on how apache loads compared to iis"
date: 2010-08-18
forum: Server Platforms
---

### Post by thegaffney on 2010-08-18
Hey there, the company i work for is starting to want to mess around with linux to see how it works compared to our windows setup

Currently the whole company uses a web app i made to run and manage the company/inventory/orders etc and we have a windows sbs server with iis and php

I just setup 3 computers in linux, one for the web/email one to serve the database and a 3rd as client, the first 2 use the server edition 10.04 

A few things i noticed are different, first loading and using the web app seems a tad bit slower then the windows setup we have now, i dont know if its the database or apache thats doing it though. Also the main thing i noticed is, with the iis setup we use, you click on a button to load a page, and the first part of the page loads right away, allowing my little div that shows a loading icon to appear, then when the page is done loading i have it disapear. 

Now when playing with the linux stuff, i click a button to load something and it doesnt display anything, or change anything it seems untill the entire page is loaded, so my loading icon never shows, the browser just sits there untill the whole thing is done, and the only indication you have that its loading is firefox's notifications,status bar etc of coarse.

This is kinda a let down, because with our current setup you can do a large query from the database, and it will actually show it loading each record, and you can scroll the page, do whatever while its still loading, and the users see my loading icon while its doing that so that they know its not frozen or anything. 

I know for a fact the people here are going to be clicking search again or reloading the page manually because they think its frozen if they do a large search using the linux setup and dont see anything happening untill the entire thing is loaded. Sometimes they are loading hundreds of thousands of records and even i would be frustrated not seeing any progress, or a blank screen for a minute plus.

Any way to change a setting somewhere to get it to act like iis does?


Btw, all this learning how to set up the server and everthing i did up to this point was kinda fun, and not as hard as i though it would be.

Oh and we use firebird for a database if that matters


EDIT:

Got some page load time from the same computer and browser and the linux setup is running i bit faster, i guess it just seems slower since i cant see anything happening, so the first issue can be ignored :)

---

### Post by cdenley on 2010-08-18
Nevermind, I just noticed you said it is a PHP applicaton.

---

### Post by thegaffney on 2010-08-18
I did say, just once though in the beginning :) php

But yeah ive read about buffers once before, but never really messed with it since i didnt really need to use it, but doing that might help with apache and php?

---

### Post by cdenley on 2010-08-18
Either use the flush function

[http://www.php.net/manual/en/function.flush.php](http://www.php.net/manual/en/function.flush.php)

or turn off output_buffering in /etc/php5/apache2/php.ini

---

### Post by thegaffney on 2010-08-18
ah, yeah putting that in there is now showing the div, but still not showing each record as its found, but thats probably better/faster anyways? So im totally ok with that, 

Thanks for the help!!

---

### Post by cdenley on 2010-08-18
> **thegaffney said:**
> ah, yeah putting that in there is now showing the div, but still not showing each record as its found, but thats probably better/faster anyways? So im totally ok with that, 

Thanks for the help!!

I assume you just flushed the buffer after printing the div using the "flush" function? If you need your browser to render something which gets output after looping through each record, then you need to use the "flush" function in that loop. When that function is run, all output up to that point is sent to the client. Or you could just disable buffering entirely.

---

### Post by thegaffney on 2010-08-18
yeah thats what i did, 

im trying a few things with my php settings

changing implicit_flush to on and buffer to off does what the windows server does, 

changing implicit_flush to on and buffer to on for any size stops it from doing that
so does leaving implicit_flush to off and changing buffer to off

does iis do something to override php's settings because on my windows server auto flush is off and buffering is on but it still outputs to the client after each thing thats loaded?

Anyways, running a long script it took 59.51 to load with buffering On and auto flush off ( the default)

and 60.16 seconds with auto flush on and buffering off (the only setting that shows it each time)

also i put it back to the defaults and instead put flush at the end of the while loop and that took 62 seconds

so i really dont see a large difference, especially for large search like that, glad its figured out though

---

