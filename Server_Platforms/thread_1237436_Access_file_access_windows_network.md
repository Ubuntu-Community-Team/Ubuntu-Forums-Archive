---
title: "Access file access windows network??"
date: 2009-08-11
forum: Server Platforms
---

### Post by dajohnson1s on 2009-08-11
Hello,

I am new to the forums, apologies if this is the incorrect posting location (made the most sense at the time), please move it if need be.

I had been given an assignment to help a student radio station show their currently playing track on their website.   But I have run into a snag, I am using ubuntu 8.04, and virtually all other machines are windows boxes.  I am unable to go across the network and grab the file.  

I am thinking I need samba to do this, is this the correct assumption?  I hope there is an easier way, my admin skills are very very weak.

Thanks

---

### Post by garfonzo on 2009-08-11
I misread your post (my original response below). I think Samba may be your solution. However, I'm not sure how the server would grab the file itself. I would presume that you would want the server to be grabbing the file over and over to keep the website updated right?

If so, I'm not too sure how that might work. Presumably the server would be grabbing a music file so that it knows the name of the song playing? Something like that? Perhaps there is a Windows-side script that could be made which would fire off a song title to the server. 

I guess what I'm getting at is that I, personally, don't know how the Ubuntu Server can get stuff from a Windows box unless the Windows box 'gives' it to the server. 

What software does the Windows machine use to play the tracks? 

Original reply --------------------------------------------

If this is a one time deal (you don't need to be constantly retrieving windows files) then why not just use a USB stick? Pop it into the windows machine, put the file on it, pop it into the Ubuntu Server and mount the USB stick. There's your file. Or, if the server has email, just email it to the server.

Otherwise, yes, Samba might be your solution. Just make a share on the Ubuntu server visible to the network, then from the Windows machine drop the file to that share.

Just some thoughts :)

---

### Post by dajohnson1s on 2009-08-11
garfonzo,

Ah, forgot to mention that.  Yes, the file will need to be access multiple times.  From my understanding, the Master Control for the radio station builds a playlist, and outputs that to a file, when the playlist updates (ie. new song starts) the file is then 'rewritten'.  Then I read it again.

I thought samba would be the way to go, but like I said, my admin skills (esp. for linux) are weak.  

Now to find a few good tutorials to see what I need to configure.  :)

Thanks again

---

### Post by garfonzo on 2009-08-11
> **dajohnson1s said:**
> garfonzo,

Ah, forgot to mention that.  Yes, the file will need to be access multiple times.  From my understanding, the Master Control for the radio station builds a playlist, and outputs that to a file, when the playlist updates (ie. new song starts) the file is then 'rewritten'.  Then I read it again.

I thought samba would be the way to go, but like I said, my admin skills (esp. for linux) are weak.  

Now to find a few good tutorials to see what I need to configure.  :)

Thanks again

Samba is a piece of cake. Once you have it installed, you just need to make a share that others can see. There's a plethora of tutorials on making a share visible to the network.

This is how I might approach it, others may have a far better solution, but just to get the think-tank going...

What if, after getting your Samba share is visible, you were to make a script on whatever Windows computer it is that holds the playlist file. That script would run and, say, every 60 seconds, check the playlist file for changes. If it finds a change, it would copy that file (or even just write the new song title to a file on the Samba share). Then, on the server side, have a similar script that would re-read the playlist file every 60 seconds for the latest song added. 

I'm not sure how you are with programming, but the script on the Windows' side and the server side would be small. They would be running all the time, but use a tiny bit of resources (virtually unoticed by the computers).

Anyway, that's how I might approach it. Again, I'm no expert at all on server admin, but I have just enough experience in programming to get myself into trouble :P.

Keep us updated on how things go, this is an interesting problem.

---

### Post by dajohnson1s on 2009-08-11
Hey, your suggestion is remotely close to what I am currently doing.  Just to outline what I am dong, on the client side, I am using ajax to open my php file and read the contents.  The php file opens a local version of the billboard file (contains the songs) and reads the first line only (current track playing). 

Honestly, I think if I can read the remote file, then I am in business and can mark this as done.  But when I go to mount the share they had given me, I keep getting a "mount error 13: Permission denied".  

But I think you are right, if I can mount the windows share, then I should be able to read the file no problem.  Also, it could be an issue on their end, I am supposed to be able to stream the feed...but cannot do anything outside the network...or even have a page access it from the server (in the network).  

Here is the tutorial I was following that gave me the error: [http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/](http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/)
[U]
[client side]("http://wds.semo.edu/kdmc/demo.html")

[server side]("http://wds.semo.edu/kdmc/date.php")

[/U][CENTER][LEFT]__Thanks
[/LEFT]
__[/CENTER]

---

### Post by garfonzo on 2009-08-11
> **dajohnson1s said:**
> Hey, your suggestion is remotely close to what I am currently doing.  Just to outline what I am dong, on the client side, I am using ajax to open my php file and read the contents.  The php file opens a local version of the billboard file (contains the songs) and reads the first line only (current track playing). 


At this point, you should have that script write that first line to a file located on the Ubuntu server (accessed by having Samba set up on Ubuntu). Then the Ubuntu machine can read its own file with the current song playing.

> **dajohnson1s said:**
> 
Honestly, I think if I can read the remote file, then I am in business and can mark this as done.  But when I go to mount the share they had given me, I keep getting a "mount error 13: Permission denied".
So, you are trying to get the Ubuntu server to mount the windows share or trying to have the client computer mount the Ubuntu share??

If you are getting this error from the client computer, I would say that your samba share isn't set up to give read/write access (possibly your mount location on the Ubuntu machine may not have read/write access?)


Why not, instead, have the client computer mount an Ubuntu share with read/write access and dump that first line to a file on that Ubuntu Share. Then, the Ubuntu server just needs to read that file over and over.


I suppose a different approach, assuming your Ubuntu machine has access to the playlist file itself, would be to do something like:
```
cat //path/to/readable/playlist.txt > current_song.txt
```
Somehow run that in a loop within the website script to constantly read the playlist file. Of course, modify that so that it only reads the first line (or last line, wherever the current song is).

Just thinking out loud

---

### Post by dajohnson1s on 2009-08-12
garfonzo,

I will re-read your post in the morning (just got done with work)...but I figured I would mention I just got Samba working. So now I have the windows share mounted on my ubuntu server.

Now, the only issue is that it is in mnt/myshare and the www is in the usual spot.  So I will look for a way to go up a couple of levels to get into the mnt directory.

Or do the script like you suggested.

I guess I could mount their share in my [www...and](www...and) use htaccess to not allow users to view it.  But that is probably a bad idea, security issues and whatnot.  The only problem I have with adding a ubuntu share on their machine is that I eventually want to write this in asp.net to move to a new server.  I would have originally done this in .net, but needed it completed very quickly (I just got threw doing 3 big php projects so its pretty fresh).

Sorry to ramble.

---

### Post by dajohnson1s on 2009-08-12
garfonzo,

Great news.  I got it working...what I was doing was this:
```

$bilboard = "../../mnt/win/bilboard.asc";  //kept getting a "this file is not in /var/www/...so it was throwing me off a little

changed to

$billboard = "/mnt/win/bilboard.asc";  //path to the samba share



```Not sure how to explain what I was thinking when using the '..', the only thing I could think of was I was in CL mode, and wanted to move up a directory :P

Anyway its working.  -- now I just need to talk to these people about getting their file in order.

Thanks

---

### Post by garfonzo on 2009-08-12
> **dajohnson1s said:**
> garfonzo,

Great news.  I got it working...what I was doing was this:
```

$bilboard = "../../mnt/win/bilboard.asc";  //kept getting a "this file is not in /var/www/...so it was throwing me off a little

changed to

$billboard = "/mnt/win/bilboard.asc";  //path to the samba share



```Not sure how to explain what I was thinking when using the '..', the only thing I could think of was I was in CL mode, and wanted to move up a directory :P

Anyway its working.  -- now I just need to talk to these people about getting their file in order.

Thanks

That's great to here! Sounds like a fun project.

---

### Post by dajohnson1s on 2009-08-13
It was, I wish the way it was 'given/forced' on me was different.  But with the exception of the samba stuff, it was very easy.  

Here is the completed module if you would like to see it.
[http://wds.semo.edu/kdmc/demo.html](http://wds.semo.edu/kdmc/demo.html)

---

