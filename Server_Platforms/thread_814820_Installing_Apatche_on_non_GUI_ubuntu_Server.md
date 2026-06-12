---
title: "Installing Apatche on non GUI ubuntu Server"
date: 2008-06-01
forum: Server Platforms
---

### Post by amlife on 2008-06-01
Hello I'm a new to servers world.. 

trying to install Apache on non GUI ubuntu server, I reached to the point where I need to open a webpage browser. what can I do now .. there is no webpage browser here .. 

I don't want to use xwindow on this server I really need max performance. 

is there is any way a can go around it ?

I faced the same problem with webmin no browser !! :(

Thank you

---

### Post by quelx on 2008-06-01
On the server itself run **ifconfig |grep inet** and copy down the second (or whicever is not *127.0.0.1*) **inet addr:** number (of the format xxx.xxx.xxx.xxx).

On a different computer on the same network (perhaps the computer you are using to post here) open firefox and type that number into the address bar and enter.

For webmin use the same # followed by **:10000** and it will redirect you to a secure page (accept the security warnings) eg. [https://192.168.1.10:10000](https://192.168.1.10:10000)

---

### Post by hyper_ch on 2008-06-01
there are cli browsers:   sudo apt-get install lynx

---

### Post by quelx on 2008-06-01
> **hyper_ch said:**
> there are cli browsers:   sudo apt-get install lynx

**lynx** and **webmin** would not be an effective combination

---

### Post by atbnet on 2008-06-01
apt-get install apache2 will install apache2 for you.

If you need the other stuff such as php, mysql use this guide
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by windependence on 2008-06-02
> **amlife said:**
> Hello I'm a new to servers world.. 

trying to install Apache on non GUI ubuntu server, I reached to the point where I need to open a webpage browser. what can I do now .. there is no webpage browser here .. 

I don't want to use xwindow on this server I really need max performance. 

is there is any way a can go around it ?

I faced the same problem with webmin no browser !! :(

Thank you

Ok you were missing an important point here. To run Webmin you need to acces it from another machine on your network. Also, what do you need to open a web browser for at this point? Is it to test the site? If so, you want to do this from another machine also using the IP of your machine as was suggested by another poster.

BTW, I applaud your effort to keep X off your production server.

Good luck!

-Tim

---

