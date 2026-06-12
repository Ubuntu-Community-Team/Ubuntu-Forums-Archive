---
title: "I want resolve host name in the log of dansgaurdian"
date: 2009-09-25
forum: Server Platforms
---

### Post by csejo123@yahoo.com on 2009-09-25
dear expert


i am using squid + dansgaurdian  for proxy server 
when i look in tail -f /var/log/dansgaurdian/access.log

I can see  the ip address  now here i want the name to be shown instead
of ip

Please help


009.9.25 6:07:05 - 192.168.1.8 [http://www.bseindia.com](http://www.bseindia.com) *SCANNED*  GET 33126 -150  1 200 text/html   -
2009.9.25 6:07:06 - 192.168.1.8 [http://www.bseindia.com/include/css/Home_op.css](http://www.bseindia.com/include/css/Home_op.css) *SCANNED*  GET 7123 0  1 200 text/css   -
2009.9.25 6:07:06 - 192.168.1.8 [http://www.bseindia.com/latests.htm](http://www.bseindia.com/latests.htm)  GET 0 0  1 304 -   -
2009.9.25 6:07:06 - 192.168.1.8 [http://www.bseindia.com/datarefrenn.asp?0.569368728831953](http://www.bseindia.com/datarefrenn.asp?0.569368728831953) *SCANNED*  GET 213 0  1 200 text/html   -
2009.9.25 6:07:06 - 192.168.1.8 [http://www.bseindia.com/applet/ticker/TickerData_new.asp?&no=0.11668108208270489&datafile=1](http://www.bseindia.com/applet/ticker/TickerData_new.asp?&no=0.11668108208270489&datafile=1) *SCANNED*  GET 2335 0  1 200 text/html   -
2009.9.25 6:07:06 - 192.168.1.8 [http://www.bseindia.com/applet/announce/Finalnews_js.asp?id=0.4188956904778666](http://www.bseindia.com/applet/announce/Finalnews_js.asp?id=0.4188956904778666) *SCANNED*  GET 2043 -30  1 200 text/html   -

---

### Post by Bachstelze on 2009-09-25
You don't know which machine of your network has this IP?

---

