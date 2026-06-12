---
title: "Web server CGI not working with parameters."
date: 2017-06-08
forum: Server Platforms
---

### Post by jirigerych2 on 2017-06-08
Hi there, 

hope you can help. 

I have fully working web server with PHP, MySQL and Apache2. I can run Wordpress site with no problem or any other sites. 
I have even simple CGI script in the users web directory working. 

With the CGI showing the test file working, I took it as the CGI is fully working. Which turns out it is not. 

My colleague has install Actinc / SellerDeck website on the server and uploaded the CGI .pl .pm files and we have then set the permission 755. 
When ever I click on page that requires CGI [pearl script] it will tell me - please see below. 

"**Internal Server Error**

[COLOR=#000000][FONT=&amp]The server encountered an internal error or misconfiguration and was unable to complete your request.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Please contact the server administrator at "email" to inform them of the time this error occurred, and the actions you performed just before this error.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]More information about this error may be available in the server error log.[/FONT][/COLOR]
[HR][/HR][FONT=Times New Roman]Apache/2.4.18 (Ubuntu) Server at newcastleart.nesolutions.co.uk Port 80[/FONT]

[FONT=Times New Roman]"
[/FONT]
I have then checked the logs and I have got error saying it can't run the pearl script as it can find the file or directory - which I then double check it - i have then noticed that the .pm file is trying to run parameters, so I have done my checks with permissions, settings in the files and more log files, but still pointing that the file is not there. 

Can anyone point me in the direction to try get this resolved. 

I have tried 3 different file types for CGI and all working - So i would like to say I have CGI working - but something is not working for sure. 

Any help would be appreciated. 

Thanks

---

### Post by cariboo on 2017-06-10
Moved to Server Platforms, as you may get a quicker answer here.

---

