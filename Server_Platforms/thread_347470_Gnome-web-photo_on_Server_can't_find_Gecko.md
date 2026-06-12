---
title: "Gnome-web-photo on Server: can't find Gecko?"
date: 2007-01-27
forum: Server Platforms
---

### Post by kale77in on 2007-01-27
I'm trying to run gnome-web-photo on an Ubuntu server to automate thumbnailing of hosted sites. 

I solved the need for an X-Display by apt-get-installing xdm (though that will be reviewed for security and probably kept away from any production servers). When I run xdm, echo the $DISPLAY, I find localhost:10.0 is now set. 

I've scripted this on account of all the command line settings:

```
> cat getSiteThumbnail
#!/bin/bash
gnome-web-thumbnail --width=1024 --size=256 --timeout=60 \
--display=localhost:10.0 $1 $2
```

When I run this on any site I get the following results. 

```
502 > ./getSiteThumbnail http://google.com google.png
Failed to initialise gecko (rv = 80004005)!
```

Using absolute paths seem to make no difference here. Firefox has been installed on the server, which I understand gnome-web-photo to require. 

I haven't found anything about this online. Can anyone suggest how I can get Gecko to initialise here?

---

### Post by solva on 2008-03-19
Hi there,

I'm having the same problem -- gecko could not initialise.  Did you have any luck with this?

I have managed to take a screenshot with a solution involving Xvfb, firefox and import, but using gnome-web-photo would be nicer, and allow me to get full-length screenshots.


    Andy

---

