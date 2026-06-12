---
title: "Move Google Chrome Cache to a ram disk and speed up page loading"
date: 2011-04-22
forum: The Cafe
---

### Post by dctrsatan on 2011-04-22
Got ample RAM installed? Want to speed up web page loading in Google 
Chrome? By moving your web cache to a RAM disk you can do just that. 
photo © 2008 William Hook | more info(via: Wylio) 
"It is possible to store a web cache on a RAM disk and this can 
improve the speed of loading pages. Due to the volatility of RAM 
disks, using a RAM disk has privacy advantages." ~ Wikipedia 
Roger Navelsaker sent us over the following tutorial for moving Google 
Chrome’s cache to a RAM disk. This not only speeds up page loading 
but, as he notes being an SSD user, helps saves on write cycles too. 
Move Google Chrome Cache to RAM Disc 
"As we all know, Google Chrome and Chromium does not give use a option 
on where to put the cache on disk. But clever use of bash script and 
symbolic links does the trick." he began before outlining the steps 
needed to achieve the desired effect. 
Open a fresh Terminal window and enter the following: - 
sudo gedit /etc/fstab 
Add the following line to the bottom of the text file that opens but 
BE CAREFUL – do not touch, edit or enter ANYTHING else: 
tmpfs           /media/ramdisk  tmpfs   defaults,noatime,mode=1777 0 0 
Once entered save and exit. 
Head back to the terminal window, this time enter the following: - 
sudo mkdir /media/ramdisk 
Now lets create the script that will do the ‘magic’ for us. 
Still in the Terminal enter: 
gedit ~/.chromecache 
add this inside the textfile 
#!/bin/sh 
#for the google chrome cache 
/bin/rm ~/.cache/google-chrome 
/bin/mkdir /media/ramdisk/google-chrome 
/bin/ln -s /media/ramdisk/google-chrome ~/.cache/google-chrome 
#for the chromium cache 
/bin/rm ~/.cache/chromium 
/bin/mkdir /media/ramdisk/chromium 
/bin/ln -s /media/ramdisk/chromium ~/.cache/chromium 
Save and exit. 
Make the script executable by issuing: 
sudo chmod +x ~/.chromecache 
Now go to ‘System > Preferences > Start-up Applications’ and add a mew 
entry using the following field data: - 
Name: Chrome Cache 
command: ~/.chromecache 
comment: moving chrome browser cache to ramdisk 
Source: [http://www.omgubuntu.co.uk/2010/11/move-google-chrome-cache-to-ramdisk/](http://www.omgubuntu.co.uk/2010/11/move-google-chrome-cache-to-ramdisk/)

---

### Post by dik angga on 2012-05-29
and after i did that method, what happen with my google chrome? 
is that method decrease my RAM size..?
my ram 1gb..if i do that method, is my RAM size decrease? 

sorry my very bad english

---

### Post by Bandit on 2012-05-29
> **dik angga said:**
> and after i did that method, what happen with my google chrome? 
is that method decrease my RAM size..?
my ram 1gb..if i do that method, is my RAM size decrease? 

sorry my very bad english

This is an year old thread. 

But if you only got 1GB of RAM or slow internet this method of moving the cache isnt for you. This should only be used for used with serious RAM like 8GB or more.. Actually I wouldnt even do it with 8GB. I would only do this with 16GB or more.

---

### Post by Copper Bezel on 2012-05-30
I'm glad it got bumped, though. I don't have any more RAM than I need, myself, but I have a friend who does, and she does most of her work from the browser, so this is a decent fit for her. She's on Windows, but it works there, too (if, like everything else, with fewer terminal commands and more sketchy "free" downloads. And I used to think that editing .desktop files in ~/.local/share/applications was awkward, until I saw the Windows equivalent.)

---

### Post by Paqman on 2012-05-30
> **Bandit said:**
> This is an year old thread. 

But if you only got 1GB of RAM or slow internet this method of moving the cache isnt for you. This should only be used for used with serious RAM like 8GB or more.. Actually I wouldnt even do it with 8GB. I would only do this with 16GB or more.

Personally I find my machine never even uses 4GB, and I've already got ramdisks for /tmp and logs. How big is Chrome's cache anyway? I think this would be very doable on 4GB.

---

### Post by sonnet on 2012-08-06
Sorry I just applied this method. Didn't get any error message.
Is there a way to check if Chrome cache is truly loaded in ram?

---

### Post by djudji on 2012-08-13
> **sonnet said:**
> Sorry I just applied this method. Didn't get any error message.
Is there a way to check if Chrome cache is truly loaded in ram?

I am also searching a way for checking it.
Have you maybe come up to move .cache to /tmp from home folder?

---

