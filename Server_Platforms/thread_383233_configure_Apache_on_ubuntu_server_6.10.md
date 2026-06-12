---
title: "configure Apache on ubuntu server 6.10"
date: 2007-03-13
forum: Server Platforms
---

### Post by tutone on 2007-03-13
I have a server running ubuntu server 6.10 and have apache running on it as well. I am trying to set up apache so that I can host multiple users so that their webpages will be something like [www.foo.com/~user1](www.foo.com/~user1) where user1 is the users account. I know this is a common practice but I am not having any luck getting it to work. The main index page at [www.foo.com](www.foo.com) works fine. Can anyone help me to set this up. In addition, I would like to set up ftp accounts so that each user will ftp into their own home directories where their public html files go.

Any help would be greatly appreciated.

---

### Post by Strider on 2007-03-13
Take a look at this link from Apache's documentation.  It outlines what you need to do.

[http://httpd.apache.org/docs/2.2/howto/public_html.html](http://httpd.apache.org/docs/2.2/howto/public_html.html)

-Mike

---

### Post by tutone on 2007-03-13
Thanks Mike, I have stumbled around that page a little already with little results. I thought i had the UserDir configured but I must be in the wrong file. When I create a user account ubuntu does not create the public_html files nor does ftp go to that directory when the user logs in. I'll dig through this page some more. Thanks again.

---

### Post by Slackheadz on 2007-03-13
I would run that on another distro but if you have any neccessity to do so, well be more specific and i'll help you.

---

### Post by SishGupta on 2007-03-13
When you make a new user account the public_html folder is not automatically created.
just mkdir /home/<username>/public_html/
or you can instruct the user to make the directory on their own.
Then the user must place all html files they want accessed within that folder.

You don't necessarily want to force users into the public_html directory as the root of their home dir can be quite useful for storing files securely so they can not be accessed from the web. However, if you wanted to that would be up to your ftp server, not apache.

If the public_html directory doesn't work it is because you don't have the userdir mod enabled, which I can help you with. I will subscribe to this thread so I am notified of any updates.

@slackheadz, Why?
What would you prefer? Slackware?

---

### Post by tutone on 2007-03-14
I am not stuck on this distro, I am just trying this out. Which distro would you recomend?

---

### Post by tutone on 2007-03-14
Thanks SishGupta, I will try this. As is right now I am remoting in and i set up the public_html directory but my firewall keeps asking me for a password when I try to access the page via port 8080 which apache is listening on. I will try it in the morning and see if it works from inside the LAN. Thank you for you help. I will let you know how it works in the morning.

---

### Post by tutone on 2007-03-16
Thanks SishGupta, that did the trick. For some reason when i am in the LAN I can FTP to the acounts but cannot directly load a file to the public_html file. I can upload the file to the root directory and copy it from there to the public_html directory. But hey, the mkdir hint did it. Thanks!

---

