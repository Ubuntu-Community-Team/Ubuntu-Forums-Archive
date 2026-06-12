---
title: "Bugzilla on apache problem"
date: 2008-06-19
forum: Server Platforms
---

### Post by elektro_komesar on 2008-06-19
Hi everybody,
I have very interesting problem. I have Ubuntu 8.04 server and Apache2 webserver installed. Bugzilla is running on that server with mysql DB.
Here is the problem: when the user opens bugzilla main page and try to login, browser reloads same page, clear both login fields (username/pass) - same thing for Firefox and IE, but with the fact that in Firefox adds line at the bottom of the page. Try another login, and same thing happens - new line at the bottom of the page (see attached picture). After 5-6 logins browser simply load blank page, and when I hit F5 it returns me to Main page and still won`t to accept login.
However, when I click at login at upper part of the page, browser opens other login page and that works fine (accepts credentials and login user). 
So, anybody has idea what`s going on? I think that this is something connected with Apache2 web server, but I`m not sure.

---

### Post by berck on 2008-06-30
I'm seeing something similiar. On the main page, I get an error trying to login using the login button. If I use the link that says Login, it works fine. From what I can see, the Login link puts you to

$HOST/cgi-bin/bugzilla/index.cgi?GoAheadAndLogIn=1

Pressing the 'login' button works from there, but pressing the login button on the main page.

$HOST/cgi-bin/bugzilla/index.cgi

Pressing the 'login' button tries to move the link to 

$HOST/cgi-bin/bugzilla/cgi-bin/bugzilla/index.cgi

---

### Post by MaGaM on 2008-09-17
I found the solution in changing the:
'urlbase' => './cgi-bin/bugzilla/' to 'urlbase' => '/cgi-bin/bugzilla'
in /etc/bugzilla/params file.
Maybe you already found the solution but for people who surf to this page first (like me) it's handy to have the solution presented here already. ;-)

Got it from [http://codintips.blogspot.com/2008/03/ubuntu-bugzilla-install.html](http://codintips.blogspot.com/2008/03/ubuntu-bugzilla-install.html)

Greetings!

---

