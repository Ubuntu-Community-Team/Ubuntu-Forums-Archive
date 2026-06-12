---
title: "Apache CGI https variable is blank instead of off?"
date: 2014-01-31
forum: Server Platforms
---

### Post by Martie_Henry on 2014-01-31
I am new to Ubuntu. 
Running Ubuntu 12.04 on server with Apache and Cold Fusion 10.
Evidently, something in the Apache installation is not specified properly, as Apache is returning the CGI https variable as an empty string to Cold Fusion, rather than off (SSL is disabled).
Other CGI variables are set properly.

[TABLE="width: 500"]
[TR]
[TD]CGI Variable
[/TD]
[TD]Value
[/TD]
[TD]if HTTP
expecting
[/TD]
[TD]if HTTPS
expecting
[/TD]
[/TR]
[TR]
[TD]HTTPS
[/TD]
[TD][empty string] 
[/TD]
[TD]off
[/TD]
[TD]on
[/TD]
[/TR]
[TR]
[TD]SERVER_PROTOCOL
[/TD]
[TD]HTTP/1.1
[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]SERVER_SOFTWARE
[/TD]
[TD]Apache/2.2.22 (Ubuntu)
[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

I wasn't able to find anything in the documentation about CGI variables, just allowing CGI execution.

Can anyone assist me in resolving this?

Thank you in advance!

---

