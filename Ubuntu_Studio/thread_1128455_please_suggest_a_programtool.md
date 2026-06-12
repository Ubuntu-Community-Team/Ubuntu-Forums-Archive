---
title: "please suggest a program/tool"
date: 2009-04-17
forum: Ubuntu Studio
---

### Post by StevenChan on 2009-04-17
HI All,

I would like to let the site visitors see what the webcam sees right now (live streaming) through a JAVA applet/Flash..etc intergated into a web page...

No recording is required..

Could anyone please give me a suggestion of which program/tool to use?

Thanks

---

### Post by timcredible on 2009-04-17
first of all, you'll want to use [joomla]("http://joomla.org") for your webpage, trust me.  then, you can try [this app]("http://extensions.joomla.org/extensions/multimedia/streaming-&-broadcasting/5162/details") or [this app]("http://extensions.joomla.org/extensions/multimedia/streaming-&-broadcasting/7449/details").

---

### Post by StevenChan on 2009-04-18
Thanks for your reply.

But I have been using Drupal to manage my web site...

Are there any similar module for Drupal?

Thanks again.

---

### Post by StevenChan on 2009-04-20
I urgently need it.

Could anyone please suggest me a program?

---

### Post by skullmunky on 2009-04-21
The fast and dirty way is to use the "webcam" program.  You can install it from synaptic or using apt-get from the command line.  "webcam" is a little program that just captures images and uploads them via ftp to a server.  All you have to do on the website side is put in an image tag, and the image at that location gets repeatedly updated.  

I'll try and walk through the setup for ya, this is kind of from memory ...

1. make sure your webcam works with Linux ... use, for example, "Cheese".  

2. works ok?  alright.  install the "webcam" program:
```

sudo apt-get install webcam

```

3. create a configuration file, to tell it where to upload the images and such.  Open gedit, create a new text file, enter configuration like this:

```


[ftp]
host = localhost
user = nobody
pass = xxxxxx 
dir = /home/youraccount
file = webcam.jpg
tmp = imageup.jpg
local = 1

[grab]
device = /dev/video0
width = 320
height = 240
delay = 1
input = camera
norm = ntsc
quality = 75
trigger = 180


```

save it in your home directory as "webcam.conf"

4. run the webcam program.  from the terminal:

```

webcam webcam.conf

```

5. if you look in your home directory you should see a file called "webcam.jpg" magically appear, and it should refresh every 1 second.

6. Ok?  now for the uploading part.  open webcam.conf and change the ftp section like this:

```

[ftp]
host = ftp.yourwebsite.com
user = YourAccountOnYourWebsite
pass = YourPasswordOnYourWebsite
dir = /path/to/directory/on/your/website/documents
file = webcam.jpg
tmp = imageup.jpg
local = 0

```

You'll need to change host, user, pass, and dir according to how your server is set up.  "dir" is the directory path on the server, NOT the URL.  

run the webcam program again.  (if it's still running, Ctrl-C in the terminal to quit it before running again).

7. point your browser at
```

http://yourwebsite.com/webcam.jpg

```

8. now, put it in an image tag in an HTML page on your site:

```

<img src="webcam.jpg">

```

9. to make it auto-refresh you can either use the HTTP Refresh Meta tag, to refresh the whole page, or make a Javascript timer to keep refreshing the IMG tag.

---

