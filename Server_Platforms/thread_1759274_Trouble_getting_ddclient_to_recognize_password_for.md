---
title: "Trouble getting ddclient to recognize password for zoneedit dynamic dns"
date: 2011-05-15
forum: Server Platforms
---

### Post by pinkepbj on 2011-05-15
I've been trying to get ddclient work for updating my ip with zoneedit.  I have configured my ddclient.conf file to the following:

```

daemon=300
pid=var/run/ddclient.pid
ssl=yes
protocol=zoneedit1
use=web, web='http://www.legacy.zoneedit.com/checkip.html/',
web-skip='IP Adress'
server=dynamic.zoneedit.com
login=myzoneeditlogin
password=myzoneeditpassword
mydomain.net
```With this configuration ddclient starts up ok but when I check /var/log/syslog I see the error:
WARNING:  null password specified for host web.
I've looked over my ddclient.conf again and again and I cant find anything out of place in regards to how the password is entered and formatted.  I would be ever so grateful to whoever may have some insight into why it may seem that its not seeing the password.

---

### Post by audstanley on 2011-09-13
You need to add 'yourpassword'

the ' before and after should solve your null issue... lol, my issue is that zoneedit doesn't recognize me at all. If I go to the browser [www.zoneedit.com](www.zoneedit.com) wont log me in and neither will their legacy.zoneedit.com

This is the email i got, but the URL is broken.
To access your account and begin using your new products and services, visit [http://www.zoneedit.com/auth/](http://www.zoneedit.com/auth/)

got to love it.

-Stanley

---

