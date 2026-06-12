---
title: "cron bash script appending ^M  at end of filename"
date: 2005-10-27
forum: Server Platforms
---

### Post by rayloewy on 2005-10-27
I have been using bash scripts in cron.hourly for many years 
with Red Hat and Fedora. I have started to use Ubuntu 5.10 "The Breezy Badger" on one of my webservers, but when the script runs 
it appends control-m (cr, lf) to the end of the file name.
Here is a sample of the script in cron.hourly:

cat /root/http_scripts/index_top>/var/www/html/index.html
cat /root/http_scripts/nav_head>>/var/www/html/index.html
cat /root/http_scripts/index_body>>/var/www/html/index.html
cat /root/http_scripts/nav_foot>>/var/www/html/index.html

If I paste this into a bash shell it runs correctly.
Hope someone can help with this mystery...

---

### Post by Glut on 2005-10-27
I'm assuming that the ^M is at the end of the line.
The possiblility that leaps to mind is using an editor that has inserted the ^M for you. If that's the case, re-editing the file with a terminal editor such as nano or vi or pick a religion, would allow you to remove all of newlines and replace them.

---

### Post by rayloewy on 2005-10-27
I use nano and pico to edit the files, just as I did in Red Hat and Fedora. When I was trying to discover a solution to the problem, I re-edited all the files with vi, and the filename was created as (for example) index.html^M, so I am not so sure it is an editor issue. And as I said I can copy the cat command lines and paste them into a bash shell and it does work without appending ^M to the filename. I am thinking this might be a problem with the cat command, but I am not sure.

---

