---
title: "HTML problem in ubuntu server 14.04"
date: 2015-01-15
forum: Server Platforms
---

### Post by cearlp on 2015-01-15
I hope this is the correct forum. I just installed the 14.04 server edition of ubuntu and setup a web server with nginx, mysql and php. I moved some html & php files from a 14.04 desktop LAMP system to the server system.
All the html & php files worked on the desktop system but one gives me a 405 Not Allowed error when run on the server system. 
The html file has a form with an onsubmit attribute that fires off a Javascript Validate routine. If the routine fails an Alert is posted. If the routine succeeds it returns true.
When the routine fails the correct Alert does display, but if it succeeds I get the 405 error with the url from the action attribute in the form displayed in the browser address field.
Placing the cursor in the address field and sending it gets the correct page. 
I can't see why the page specified in the action attribute doesn't get processed instead of causing the 405 Not Allowed error. 
The form statement is:
<form name="info" method="post" action="sxmanage.php" onsubmit="return Validate()">
The Validate is:
<script language=javascript>
 function Validate()
 { 
   if (document.info.name.value == "zxy") 
   { 
      return (true); 
   }
   else 
   { 
      alert("BAD!");
      document.info.name.focus();
      return (false);
   }
 {
>/script>

---

