---
title: "Error connecting to server during large file uploads in moodle"
date: 2017-09-20
forum: Server Platforms
---

### Post by pally12 on 2017-09-20
Greetings, i have encountered a problem which i cannot solve, im trying to upload some ocurses in Moodle which are quite large in osme cases, i have incresed all upload limits, post limits [COLOR=#595959][FONT=&quot]execution time and so on, but nothing works.

Server log gives me this:

[/FONT][/COLOR][PHP][Wed Sep 20 11:56:37.749271 2017] [fcgid:warn] [pid 27633:tid 140230833182464] [client 78.28.195.35:53949] mod_fcgid: HTTP request length 62914660 (so far) exceeds MaxRequestLen (62914560), referer: http://blah blah blah/blah/backup/restorefile.php?contextid=31[/PHP]


i have modified fcgid.conf like this:

[PHP]<IfModule mod_fcgid.c>  FcgidConnectTimeout 20  FcgidMaxRequestLen 1047527424  <IfModule mod_mime.c>    AddHandler fcgid-script .fcgi  </IfModule></IfModule>[/PHP]


restared the server but it stil wont upload, gives the error i mention above in the logs and returns **Error connecting to server in moodle **during the upload.


Any suggestions?


Thank you!

---

### Post by pally12 on 2017-09-20
For anyone whos interested, I managed to solve this problem by going into Webmin - Servers - apache Webserver, picked my virtual server for my website, went into Edit directives and changed the value of FcgidMaxRequestLen XXXXXXXX to the number i needed.

---

### Post by ajgreeny on 2017-09-20
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

