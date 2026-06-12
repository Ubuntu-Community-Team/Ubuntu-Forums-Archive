---
title: "Newfound Powers Not Working"
date: 2005-12-13
forum: Server Platforms
---

### Post by popawheelie on 2005-12-13
A true beginner here seeking the guidance of my more experienced, seasoned programmers.
I've struck a knot in the branch here and wonder if anyone will help.
Here is my code:


<form method=POST action="http://dept11.info/cgi-bin/formmail.cgi" target="_top">
<INPUT TYPE="HIDDEN" NAME="recipient" VALUE="lakepointadmin@dept11.info">
<INPUT TYPE="HIDDEN" NAME="subject"  VALUE="WebSite Contact"> 
<INPUT TYPE="HIDDEN" NAME="redirect" VALUE="http://www.dept11.info/lakepoint/index.html">
 <INPUT TYPE="HIDDEN" NAME="required" VALUE="lakepointadmin@dept11.info"> 
<input type=hidden name="sort" value="through,your_name,phone,company_name,email,comments">

Upon using the send button, I get the "Form Dump", along with a message reading:

"lakepointadmin@dept11.info is missing"

My problem is that I do not know where it is missing from or how to put it where it needs to be.
Is there anyone who can assist and get me on my jounrey to better, safer and more productive code?  PLEASE
D.Wilie1onLine
Thanks forwarded

---

### Post by jwd45244 on 2005-12-13
This question really should be directed to a web application programming forum, not Ubuntu forums.  If there are nice folks out there who can help you, fine.

---

### Post by cwaldbieser on 2005-12-13
[QUOTE=popawheelie]A true beginner here seeking the guidance of my more experienced, seasoned programmers.
I've struck a knot in the branch here and wonder if anyone will help.
Here is my code:


<form method=POST action="http://dept11.info/cgi-bin/formmail.cgi" target="_top">
<INPUT TYPE="HIDDEN" NAME="recipient" VALUE="lakepointadmin@dept11.info">
<INPUT TYPE="HIDDEN" NAME="subject"  VALUE="WebSite Contact"> 
<INPUT TYPE="HIDDEN" NAME="redirect" VALUE="http://www.dept11.info/lakepoint/index.html">
 <INPUT TYPE="HIDDEN" NAME="required" VALUE="lakepointadmin@dept11.info"> 
<input type=hidden name="sort" value="through,your_name,phone,company_name,email,comments">

Upon using the send button, I get the "Form Dump", along with a message reading:

"lakepointadmin@dept11.info is missing"

My problem is that I do not know where it is missing from or how to put it where it needs to be.
Is there anyone who can assist and get me on my jounrey to better, safer and more productive code?  PLEASE
D.Wilie1onLine
Thanks forwarded[/QUOTE]

Yes, you are better off asking this in the programming forum.  You also might want to explain a little bit more what you are actually tring to do.  It looks like you are trying to POST some form data to a CGI page and it is giving you a message back.  However, the host [www.dept11.info](www.dept11.info) does not seem to be public on the Internet, so it is unlikely anyone will be able to figure out your intent without a little more explanation.

---

