---
title: "how to prevent apache2 under ubuntu 12.10 from blocking HTML Frames?"
date: 2013-03-06
forum: Server Platforms
---

### Post by dvks on 2013-03-06
How can I prevent Apache from blocking HTML frames:

I have my website A installed on /var/www/A
I have 3rd party website B installed on /var/www/B
Pages on website A include HTML frames that reference pages on website B
When connecting to A from a local LAN the frames are working and showing the pages from B
When connecting to A from the Internet frames doesn't work and instead I get timeout messages.

I suspect that it relates to X-FRAME directives but not sur if this is the problem or the only problem.
I already modified the 3rd party website and remove from page "template.php"  the line- 
**[COLOR=black][FONT=Calibri][SIZE=3]Header(‘X-Frame-Options: Sameorigin’);[/SIZE][/FONT][/COLOR]**

This made it possible to open the pages on the LAN but still can't open them when connecting from the internet

Tried also to look for X-Frame under .htaccess but not sure I am looking at the right places.

I appreciate any help since I am lost at this point.
Thanks.

---

### Post by theDaveTheRave on 2013-03-06
Are you able to navigate to web site B directly (without passing through from site A) ?

If so an #include statement in our html file should do the trick.

Can you post a snippet of code for how you currently get the page to display inside of A.

Also depending on how you 'display' the embeded pages from siteB in the frame of siteA may make a difference in Apache.

are you using the actual < web address > of the siteB page, or are you using a < relative filesystem link >, if you are using a filesystem link this will not very likely work from the net ;)

David

---

### Post by dvks on 2013-03-06
> **theDaveTheRave said:**
> Are you able to navigate to web site B directly (without passing through from site A) ?

If so an #include statement in our html file should do the trick.

Can you post a snippet of code for how you currently get the page to display inside of A.

Also depending on how you 'display' the embeded pages from siteB in the frame of siteA may make a difference in Apache.

are you using the actual < web address > of the siteB page, or are you using a < relative filesystem link >, if you are using a filesystem link this will not very likely work from the net ;)

David
David , I appreciate your feedback, thanks.  Yes I can navigate to website B directly, not through A. The PHP line that does the frame is==> echo "</br><IFRAME SRC= 'http://" . "$ipaddr" . "/B' WIDTH='90%' HEIGHT='600'></IFRAME></br></br>";  as you can see, yes I am using the actual web address (placed in $ipaddr ) and not a relative file system address.  by the way for some reason I can't get the line feed work on this browser I hope that my feedback is not a total mess.

---

### Post by morgandival on 2013-03-06
[FONT=arial]It could be the way you have nested your quote marks.
[/FONT]
[FONT=courier new]echo '</br><IFRAME SRC="http://' . $ipaddr . '/B" width="1000" height="600"></IFRAME></br></br>';
[FONT=century gothic]
[FONT=arial]Also, the width and height attributes of the iframe tag only take pixel values.[/FONT][/FONT]
[/FONT]

---

### Post by morgandival on 2013-03-06
The style attribute can be applied to achieve the desired effect:

[FONT=courier new]echo '</br><IFRAME SRC="http://' . $ipaddr . '/B" style="width:90%; height:600px"></IFRAME></br></br>';[/FONT]

---

### Post by dvks on 2013-03-06
It works when I connect from another computer on my LAN it doesn't work only when I connect from the Internet so I assume it is not a syntax or address or the size of the frame but some kind of security setting issue?

---

### Post by dvks on 2013-03-07
You lost me, is this the solution for having the frame being blocked when connecting from the internet but ok when connecting from the local LAN?

---

### Post by morgandival on 2013-03-07
When you get the error message, is it just the IFrame that shows the error, or the whole page?

---

### Post by dvks on 2013-03-07
It is an IFRAME problem

---

### Post by GordThompson on 2013-03-07
> **dvks said:**
> The PHP line that does the frame is==> echo "</br><IFRAME SRC= 'http://" . "$ipaddr" . "/B' WIDTH='90%' HEIGHT='600'></IFRAME></br></br>"; as you can see, yes I am using the actual web address (placed in $ipaddr ) and not a relative file system address.
[...]
It works when I connect from another computer on my LAN it doesn't work only when I connect from the Internet
Does $ipaddr contain the server's private local IP address (e.g., 192.168.x.y or 10.x.y.z), or does it contain the public external IP address?

---

### Post by dvks on 2013-03-07
As much as I remember it is the public address but let me try it and get back in few minutes

---

### Post by dvks on 2013-03-07
:P  Hi GordThompson you made my day, thanks for you the simple question/answer you gave, yes you are correct it was trying to use the local server address .... and I wasted so much time trying to find out what happen. Thanks again, I modified the address to be the external address and surprisingly enough it works.

---

### Post by dvks on 2013-03-07
:P I am posting my feedback again since I can't see my last post:  Hi GordThompson you made my day, thanks for the simple question/answer you gave, yes you are correct it was trying to use the local server address .... and I wasted so much time trying to find out what happen. Thanks again, I modified the address to be the external address and surprisingly enough it works.

---

### Post by morgandival on 2013-03-07
IFrames are fickle things. Just make certain that the address you are passing is a valid address. If the IFrame is returning a HTTP Status Code, please post it here as this may provide a clue as to what is actually happening.

---

### Post by dvks on 2013-03-07
Thanks the problem was the IP address, it was the server local LAN address instead of the external WAN address

---

