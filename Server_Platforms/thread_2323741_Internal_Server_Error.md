---
title: "Internal Server Error"
date: 2016-05-07
forum: Server Platforms
---

### Post by Larry_Mabry on 2016-05-07
[h=1]Internal Server Error[/h] The server encountered an internal error or misconfiguration and was unable to complete your request.
 Please contact the server administrator,  webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.
 More information about this error may be available in the server error log.
 [HR][/HR] Apache/2.2.22 (Ubuntu) Server at 10.1.32.10 Port 443 

Really new to this os system I have a NUC machine running vmware and a phonesuite vm running ubuntu 32 bit when i use the windows screen to log in I get the phone suite login screen but then get this error any Ideas or help would be appreciated

---

### Post by nerdtron on 2016-05-07
That is the error on the web browser. A more helpful error should be in the apache logs. What do the logs record when you see that error on the browser? 


[LIST]
[*]/var/log/apache2/access.log - records of every page served and every file loaded by the web server. 
[*]/var/log/apache2/error.log - records of all error conditions reported by the HTTP server 


Also, we need more info like, what ubuntu version are you using? Do you have multiple virtual host? Is that error happening on all web pages or just on a single page only? 
[/LIST]

---

### Post by Habitual on 2016-05-09
Tell us more about these VM hosts.

---

