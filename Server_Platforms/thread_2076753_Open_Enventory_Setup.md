---
title: "Open Enventory Setup"
date: 2012-10-26
forum: Server Platforms
---

### Post by kwrogers on 2012-10-26
I recently installed the server applications on my ubuntu 12.04 LTS desktop setup, including apache2, php5, and mysql services.

I have successfully configured everything to allow outside access to my hosted site, and can also access and manipulate databases using phpmyadmin through the browser.

I am trying to install and get working "Open Enventory" (the 2012-09-28 build), a scientific, web-based application suite. After following the provided directions (which were translated from german using google) and information from a few forum posts when the provided directions were unclear, I do have access to the login page via the web but cannot log in.

I am given the following error: (the database I'm trying to access is named 'science')

**Login failed, access to database science denied. **

I made sure, several times, that the user name I was trying to use had all global permissions and I even created another user that was also granted global permissions. Same error message.

Sorry for the long winded intro, but has anyone else tried and succeeded setting up open enventory? Or have any pointers?

Thanks!

---

### Post by kwrogers on 2012-10-31
Turns out you have to log in as root and then create users within Open Enventory; it doesn't use the same users as mysql.

Hope this helps others.

---

