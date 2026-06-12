---
title: "suEXEC sucks HELP!"
date: 2009-03-27
forum: Server Platforms
---

### Post by parkofgrey on 2009-03-27
OK im going to write this as well as I can but I’ve been trying to fix this for hours and hours and hours,  and at this point im just a few minutes away from collapsing on my keyboard. Ive been trying to install and use suEXEC for apache server, and have followed in detail the instructions provided from : [http://www.howtoforge.com/how-to-set-up-apache2-with-mod_fcgid-and-php5-on-ubuntu-8.10](http://www.howtoforge.com/how-to-set-up-apache2-with-mod_fcgid-and-php5-on-ubuntu-8.10) . At first I thought it was a problem with the virtual host part of apache, then the dns, and eventually I realized that it was actually the suEXEC trying to execute that was causing all the problems. I think, and I am not sure that the problem is that there is nothing in the exec /usr/lib/cgi-bin/php… I tried to link it to directories that have a php file in them but when I run it in terminal I get a exec 6 permissioned denied and with the default I get exec: 6: /usr/lib/cgi-bin/php not found… this looks like whats wrong with it, but I don’t quite understand what this is looking for and how I can find it. I’m new to linux and between this thing and ndiswrapper im about ready to lay my head down on the train tracks. I should also mension that I searched for php, the did arrange by size, and the only php file I could find was in an old lamp dir, and that’s what gave me the permissions response. HELP!!!!

---

