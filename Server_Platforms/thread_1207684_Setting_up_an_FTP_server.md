---
title: "Setting up an FTP server?"
date: 2009-07-08
forum: Server Platforms
---

### Post by helstreak on 2009-07-08
Hi,

I've recently be put in charge of setting up a data server for our research group.  We want to be able to use it to backup data and store other files on it so we can access it with any web browser.  I'm guessing Ubuntu Server Edition would work great for this but I'm not really sure what I should be looking into.  

Here's a little more explanation of what is desired:
Password protected
Download and upload to server from anywhere using a standard web browser

Would this be a simple FTP site?

Any links to tutorials would be greatly appreciated.

Thanks for your time.

---

### Post by HermanAB on 2009-07-08
That is quite trivial.  Use any kind of Ubuntu and install Proftp or Vsftp.  Either of them should work out of the box.  When you create user accounts, set their home directory to be the desired FTP directory then when they connect, they will go straight to the desired spot.

You would need Firefox with the FTP plugin.

---

