---
title: "PC audit server"
date: 2008-11-08
forum: Server Platforms
---

### Post by Ynothna on 2008-11-08
Hi, I'm new to the forum so I have no idea if this is the right place for this question.

I do a fair bit of windows based tech work in my area. I use Logmein for remote access to my clients computers and it has saved me countless hours and dollars. I'm wondering if there is some web based software out there that will allow me to run a PC audit on their computer (with their permission of course) and save the information to a database.

I was looking at [Lansweeper]("http://www.gtopala.com/") and it looks like it's exactly what I want, but it will only run on a windows web server. I have a Windows 2003 server but I'd prefer something on my Ubuntu 7.10 (soon to be 8.10) web server.

I don't suppose there is some way to make Lansweeper run on Ubuntu? I'm still pretty new to what Linux is capable of.

If anyone can make any suggestions that would be great. Thanks.

-Ynothna

---

### Post by loell on 2008-11-08
if it must be web based that will be reporting back to a specified server, then i think you'll gonna have to create one from scratch. probably in a form of firefox plugin.

but if you could do remote with your client like vnc, you could collect it by installing and running **sysinfo**, from there you can save there system info in a form of text file, which you can then upload to your server.

---

### Post by Ynothna on 2008-11-08
Web based isn't a must, I just figured it may have been easier then setting up a client/server program. 

I do have remote access to most of my client computers so sysinfo could definitely work. I'll have to look into it more. My only problem then is writing the code to insert it all into my database. I can do it, I just don't know if I have the spare time.

Thanks for the suggestion :) I'll be checking it out

---

