---
title: "Problem displaying info.php file"
date: 2018-11-14
forum: Server Platforms
---

### Post by mwoosley on 2018-11-14
Howdy everyone ;)  I hope my request for help will be a quick and painless one.

While I'm running several Linux 18.04 servers, my main concern is trying to figure out why my index.html file shows up in the browser, but when I try to display my info.php file, it returns an error... 404 file not found.  The file is located in the same folder as the index.html (/var/www/html/).  Like I previously mentioned, when I enter 192.168.1.250/index.html, I can see that file, but not so with 192.168.1.250/info.php.

Ultimately, I am going to want to return the appropriate files with the virtual hosts as well, but I plan to ask that question later... unless someone has some good input for me now.

Thanks a million!

Mike

---

### Post by mwoosley on 2018-11-14
Problem solved... not 100% sure what fixed it, but for now, I have access to the info.php file.  I did visit Apache's website and messed with the 000-default.conf file, changing a couple override options and adding a couple things.  After resetting the server, I now have what I was looking for.  Sorry, for not being able to provide the exact solution, but I'll try to take better notes as I make changes to hopefully determine what exactly impacted the change.

Thank you

---

