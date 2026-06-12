---
title: "The HTML img tag in 14.04 Server"
date: 2014-12-17
forum: Server Platforms
---

### Post by cearlp on 2014-12-17
I have several files in the /usr/share/nginx/html directory with the tag <img src="images/logo.png" /> that do not display the logo image in any browser.
The images directory is in /usr/share/nginx/html directory along with the .html files containing the img tag and has a mode of 755.
The .png files in the images directory have a mode of 600. All have owner and group as root.
Is there a package that should be installed to get the logo to display when the file is served to a browser?

---

### Post by volkswagner on 2014-12-17
Try putting images/logo.png into your url, see if you get a permission or other error.

Like [http://mydomain.com/images/logo.png](http://mydomain.com/images/logo.png)

---

### Post by volkswagner on 2014-12-17
Try putting images/logo.png into your url, see if you get a permission or other error.

Like [http://mydomain.com/images/logo.png](http://mydomain.com/images/logo.png)

---

### Post by cearlp on 2014-12-18
Thanks volkswagner, Your suggestion worked. It gave me a 403 Error. Changing the .png file's mode to 644 from 600 solved the issue.

---

### Post by TheFu on 2014-12-18
nginx runs as a non-root account. If only root has read permissions to a file/directory, then other userids cannot read it.

---

