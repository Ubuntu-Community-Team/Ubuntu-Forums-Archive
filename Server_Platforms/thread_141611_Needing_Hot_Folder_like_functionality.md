---
title: "Needing Hot Folder like functionality"
date: 2006-03-08
forum: Server Platforms
---

### Post by nverhaar on 2006-03-08
Okay guys, here's the deal...

We've come up with a photo gallery system that photographers can use to book jobs and submit photos so they may be accessible to all of our users in a web based gallery hosted on an Ubuntu server.

All is working extremely well, but the photo submission process is very manual, and we want to automate as much as possible. We now require Hot Folder like functionality, so that as JPEG's are uploaded to a folder a process can be ran to resize and colour correct images via Image Magick, and then run a PHP script to add the new images to a database.

I have been told that DNOTIFY can be used in such a situation. Does anyone have any experience scripting with DNOTIFY, or any other similar solution that provides Hot Folder functionality on Ubuntu?

THANKS!!

---

### Post by gmclachl on 2006-03-08
Why don't you enable imagemagik in PHP and automate it that way?

 George

---

### Post by nverhaar on 2006-03-08
Image Magick is enabled in PHP, but we need to move files and run PHP scripts on files as they are created, in a hot folder like manner.

We also need to setup EPS hotfolders, so people can save EPS files to a folder and they are picked up, fonts are embedded, PDF is created and preflighted.

We have many many uses for Hot Folders, but need to work out the principles behind it.

Anyone got any ideas?

---

### Post by nihilocrat on 2006-03-09
Another idea is to make a script that checks certain directories for new files, and if it finds any, submits them to the image processing scripts.

You could then put this script in your crontab to run every minute or so. Since it's not a very high-resource process it probably wouldn't be a problem making it update so often.

---

