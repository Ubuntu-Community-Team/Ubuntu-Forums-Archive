---
title: "Mambo in repos?"
date: 2005-12-13
forum: Server Platforms
---

### Post by vvlist on 2005-12-13
Why isn't Mambo or Joomla in the repositories? Wouldn't this be an important factor in attracting people to use Ubuntu Server? Just a thought.

---

### Post by diebels on 2005-12-13
It's just a bunch of files you put in a webserver folder, and it has it's own web-based installer.

So I don't see any point of putting it inside a deb package. All the configuring is done through the web-installer. Most people use some extensions that make automatic updates unsafe too.

But if you can figure out how to integrate the configuration into debconf, and solve the automatic update stuff. It would be nice to have joomla and mambo in the repositories.

---

### Post by vvlist on 2005-12-13
Thanks for the reply. I didn't realize exactly how it could be installed until I downloaded it. Thank you

---

### Post by nocturn on 2005-12-13
Also, make sure to apply the latest patches (Mambo 4.5.2.3 or Joomla 1.0.4), they are very important.

---

