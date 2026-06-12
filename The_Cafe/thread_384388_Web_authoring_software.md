---
title: "Web authoring software"
date: 2007-03-14
forum: The Cafe
---

### Post by lwalper on 2007-03-14
Is there any good web authoring software written for Linux? I've been using DreamWeaver MX in Windows, but if I'm going to migrate to Linux I'd like to find something similar. I've installed Bluefish, but can't see how to import an existing site. Since I maintain several sites on at least a weekly basis I'm looking for something pronto.

---

### Post by karellen on 2007-03-14
maybe nvu would help you...though I miss dreamweaver in linux too. I couldn't find anything matching it in linux :confused:

---

### Post by 23meg on 2007-03-14
[http://www.ubuntuforums.org/showthread.php?t=371145](http://www.ubuntuforums.org/showthread.php?t=371145)
[http://www.ubuntuforums.org/showthread.php?t=383207](http://www.ubuntuforums.org/showthread.php?t=383207)
[http://www.ubuntuforums.org/showthread.php?t=314780](http://www.ubuntuforums.org/showthread.php?t=314780)

---

### Post by beercz on 2007-03-14
Applications->Accessories->Text Editor

Use it all the time!

---

### Post by DJ_Peng on 2007-03-14
> **karellen said:**
> maybe nvu would help you...though I miss dreamweaver in linux too. I couldn't find anything matching it in linux :confused:
Nvu? Not so much, IMO. Although I had seem something about [Aptana](http://aptana.org/) that may do the job. I haven't had a chance to play around with it yet so I can't tell you much about it. At least it seems to be able to handle PHP files, which Nvu doesn't know what to do with.

And yes, I use Text Editor as well, but if I couldn't run DW under Linux I'd be stuck in Windows, hating it more every day. I simply depend too much on being able to change my code and visually confirming that I haven't tried to rape the poor pooch. That's been known to happen every now and then if I depend on espressos to keep me going too long without breaks.

---

### Post by DarkN00b on 2007-03-14
I'm liking [Amaya]("http://www.w3.org/Amaya/"). You have a lot of options as to how you do things from WYSIWYG to hand coding. I usually land somewhere inbetween...

---

### Post by lwalper on 2007-03-14
Thanks ya'll. I've got a page to edit this very moment. Nvu looks good. Think I'll use it for today.

---

### Post by x1a4 on 2007-03-14
[Vim](http://www.vim.org/) and [gPHPedit](http://www.gphpedit.org/).

---

### Post by futz on 2007-03-14
> **lwalper said:**
> Is there any good web authoring software written for Linux? I've been using DreamWeaver MX in Windows, but if I'm going to migrate to Linux I'd like to find something similar.
There's nothing in linux that can touch Dreamweaver. I love Dreamweaver, tho I've never ever used the wysiwyg part of it. I hand code everything. It's just a great coding IDE and ftp tool.

But linux has some decent tools too. You found Bluefish, which is pretty good. I've tried nvu a few times, and tho it has improved lots lately, I still don't like it.

I just finished a small paying web-site project using 100% linux tools. The tools aren't as polished as the windows stuff, but they're free and did the job just fine. I used bluefish, gimp, inkscape, gftp and filezilla.

> I've installed Bluefish, but can't see how to import an existing site. Since I maintain several sites on at least a weekly basis I'm looking for something pronto.
To my (meager) knowledge the only linux program that does both editing and ftp in the same program is nvu, and I found it to not work the way I wanted it to. 

To import an existing site just use a good ftp client, like FileZilla. Even gFTP will do that, but not quite so nice and automatic as filezilla.

---

### Post by lwalper on 2007-03-15
I didn't use the FTP portion of DreamWeaver anyhow. I was using AceFTP which is very similar (in fact looks and works practically identically with FireFTP). I did enjoy the file management of DW -- maybe these others have something similar.

---

### Post by futz on 2007-03-15
> **lwalper said:**
> I didn't use the FTP portion of DreamWeaver anyhow.
Then you don't know what you were missing. Dreamweaver does smart site updating/synchronizing (with ftp) better than any program I've ever used. Makes life sooooo easy. It keeps track of all the piddly little details for you.

---

### Post by maniacmusician on 2007-03-15
> **lwalper said:**
> I didn't use the FTP portion of DreamWeaver anyhow. I was using AceFTP which is very similar (in fact looks and works practically identically with FireFTP). I did enjoy the file management of DW -- maybe these others have something similar.
If file management is important to you, Quanta Plus is great for managing various projects at once. 

I would also look into using a localhost apache server. What you have to do is install apache2 (use synaptic or the command line), put your html files into /var/www. Then, by typing "localhost" into a web browser, you can access your files as if they were on a real website! It simulates a server environment for you, really cool stuff. It's a lot easier to first see how your work is coming together rather than seeing mistakes after you upload them to the internet. This also makes it really easy to test sites across various browsers. 

I was going to say something else that was useful, but I've forgotten what it was...:-k

---

### Post by myownserver on 2009-09-09
I want to first say this is probably the most helpful post yet on web authoring software.  It seems far too often people would rather say "Well be a "real" designer and hand code the whole thing", but some of us don't fully understand it or would rather spend our time doing something else and get there quicker by using a WYSIWYG editor.  
That'd be like saying "Who needs a motor in a car when you can pedal a bicycle around?".  It's that kind of attitude that turns people away and back into the grips of the Microsoft tyrant.  Some of us want to be lazy, who cares?  
> **maniacmusician said:**
> 
I would also look into using a localhost apache server. What you have to do is install apache2 (use synaptic or the command line), put your html files into /var/www. Then, by typing "localhost" into a web browser, you can access your files as if they were on a real website! It simulates a server environment for you, really cool stuff. It's a lot easier to first see how your work is coming together rather than seeing mistakes after you upload them to the internet. This also makes it really easy to test sites across various browsers. 

I think referring to it as simulated is a misconception.  It is a REAL HTTP server.  You can also just as easily add MySQL, PHP, and phpMyAdmin to Apache for a full-blown web server and local developing environment.  I develop all of my stuff locally this way before launching it publicly and Ubuntu makes this so easy to setup and maintain with the Synaptic package manager.  
They make Windows look stupid in that way.

I will continue to wait til they make a good WYSIWYG editor for Linux or find a working way to port Dreamweaver using Wine.  (I tried this and almost cried when it didn't work, but it didn't suprise me since it's meant for Windows, not Linux.)

---

### Post by ade234uk on 2009-09-09
> **lwalper said:**
> Is there any good web authoring software written for Linux? I've been using DreamWeaver MX in Windows, but if I'm going to migrate to Linux I'd like to find something similar. I've installed Bluefish, but can't see how to import an existing site. Since I maintain several sites on at least a weekly basis I'm looking for something pronto.

Dreamweaver 8 works brilliantly using wine. Dreamweaver MX should also works. Dreamweaver 8 gets platinum in Wine. 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3482](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3482)

1) First thing to do is install Wine
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

2) Then install Dreamweaver MX using Wine.

Let me know how you get on. I had exactly the same issues as you coming to Ubuntu, but I have overcome this. And to be quite honest with you I don't notice the difference anymore.

---

### Post by Exodist on 2009-09-09
> **futz said:**
> Then you don't know what you were missing. Dreamweaver does smart site updating/synchronizing (with ftp) better than any program I've ever used. Makes life sooooo easy. It keeps track of all the piddly little details for you.

Yea I remember that also.. You could save a file locally and if it was connected it would auto update the file on the server at the same time.

If we had DW for linux, then we would have prob have 10,000 more users every week. 
Yea think I am crazy for saying 10k more per week. But in my experience over the past 10+ years using Linux.. Its the most requested program ever. Coming in 2nd is Quicken/Quickbooks.

---

### Post by Nevon on 2009-09-09
> **Exodist said:**
> Yea I remember that also.. You could save a file locally and if it was connected it would auto update the file on the server at the same time.

You can do that with any editor as long as you're using a proper web host that allows you to connect via ssh. All you need to do is connect to the server (in Ubuntu, that's Places &#8594; Connect to server), choose ssh and fill in your login information. That way you can mount your web space as a local folder, and any changes you make to files are uploaded via SCP. That's both faster and more secure than using FTP.

---

### Post by DJ_Peng on 2009-09-09
> **ade234uk said:**
> Dreamweaver 8 works brilliantly using wine. Dreamweaver MX should also works. Dreamweaver 8 gets platinum in Wine.
I was just about to post this info when I saw ade234uk's reply. Also, if you have [CrossOver Linux]("http://www.codeweavers.com/products/cxlinux/") (they did a free giveaway last year) I can say that DW8 definitely works, despite the fact that version 8 is "unsupported". I use it for editing a personal start page that I can't always edit in Geany and I have yet to find anything that doesn't work, although I haven't tried the integration with Fireworks 8 since I switched to the Gimp for my image editing work.

---

