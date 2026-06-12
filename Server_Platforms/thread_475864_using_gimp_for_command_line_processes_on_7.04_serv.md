---
title: "using gimp for command line processes on 7.04 server"
date: 2007-06-16
forum: Server Platforms
---

### Post by itsalmostreal on 2007-06-16
im creating a new database app for my company to allow designers to upload their photoshop (.psd) documents through a php driven dynamic website and i've run into rather large snag: converting the psd files to several sized jpg thumbnail images.

first, i tried using imagemagick by creating a php script that is activated via cron on the upload directory. the php script is very simple, as it just has a series of exec() commands that first convert the psd to a flat tiff file in a temp directory, then converts that image to 4 separate jpg images. i've noticed that the first step is quite slow. i've tried converting the temp file (the tiff file) into several other formats but it still takes multiple minutes to convert the psd.

i've tested the same process using the gimp (i didnt make a script-fu yet, but i think that'd be doable), and its MUCH faster. faster than using photoshop on an xserve fast. at any rate, i tried to install gimp on ubuntu server 7.04, and while the apt-get install gimp command seems to install the app, it fails to start with messages that make it seem like i need x-server installed to use it. is this the case? does anyone have any experience using gimp on ubuntu server? any help would be greatly appreciated.

---

### Post by Reugen on 2007-06-18
gimp can run without x if you specify the -i option and --batch-interpreter for a script-fu.
Hope it works for you.

---

