---
title: "postfix user accounts"
date: 2020-02-10
forum: Server Platforms
---

### Post by PeterK2003 on 2020-02-10
This is probably a stupid question...

I have POSTFix setup to relay email on my network.  No Auth need.  Works fine.

I have a few security cameras that no matter what I put in the config insist on authenticating.  How can I setup a user account on postfix so that these cameras work without getting into a whole lot of config?

Thanks,
Peter

---

### Post by TheFu on 2020-02-10
Any local userid on the system is a postfix userid.  If you like, you can create a local username using any tool you like, say "camera", set a password for it, ensure the password is random and at least 25 characters long, and have the camera email through that.
You didn't say which release, version, server or desktop, so ... 
[https://help.ubuntu.com/lts/serverguide/user-management.html#adding-deleting-users](https://help.ubuntu.com/lts/serverguide/user-management.html#adding-deleting-users)
That will work regardless.

For desktops: [https://help.ubuntu.com/stable/ubuntu-help/user-add.html.en](https://help.ubuntu.com/stable/ubuntu-help/user-add.html.en)  But the server instructions are much faster and work everywhere.

If you want to understand more, here's a no-hassle, free, ebook, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  I use it for my Linux Administration 101 classes.

---

### Post by PeterK2003 on 2020-02-10
Ubuntu Linux 16.04

I did try that it didn't seem to work.  Maybe I have something messed up now...

---

### Post by TheFu on 2020-02-10
> **PeterK2003 said:**
> Ubuntu Linux 16.04

I did try that it didn't seem to work.  Maybe I have something messed up now...

What did you try? Can you prove it?

BTW, I've been an email admin over 25 yrs and have been using postfix over 20 yrs.  Local accounts work. You can test them with **Mail** or **mail** programs to read and send email on the local system.

---

### Post by PeterK2003 on 2020-02-10
OK well I am trying to connect remotely.  I can do it without authentication but not with.

---

### Post by TheFu on 2020-02-10
> **PeterK2003 said:**
> OK well I am trying to connect remotely.  I can do it without authentication but not with.

Clients usually connect using 587/tcp or 465/tcp, not 25/tcp.  Port 25/tcp is for server-to-server SMTP connections, unauthenticated. STARTTLS is commonly used to provide authenticated SMTP connections. I use thunderbird as a emall client.

Would be worth looking at the postfix logs to see where the connection is failing.

---

### Post by PeterK2003 on 2020-02-11
I did the client is trying to login.  There is no option not to use authentication on the client.

---

### Post by TheFu on 2020-02-11
> **PeterK2003 said:**
> I did the client is trying to login.  There is no option not to use authentication on the client.

If thunderbird doesn't allow sending email (picking up email doesn't use SMTP), then don't expect anything else to work.
If thunderbird can send email, then the problem is either
a) with the camera
b) with understanding the camera-to-SMTP server setup

I use USB connected cameras, so software snaps a photo every 30 seconds of my front yard/driveway, then those files can be sent anywhere using normal Linux tools.  I would expect IP cameras to support "pull" of the images by a client, but I really don't know.  I don't trust IoT stuff.

---

### Post by PeterK2003 on 2020-02-11
Yes i understand that it is a limitation of the camera firmware but I was looking for a work around

---

