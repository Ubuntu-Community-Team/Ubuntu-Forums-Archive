---
title: "discovering why my server is slowly"
date: 2012-09-09
forum: Server Platforms
---

### Post by herbert tamayo on 2012-09-09
Hi, I have an ubuntu server running a LAMP app since april, everything was fine, but 2 weeks ago the server response is everyday slower, in highest traffic hours the connection to the app and the ssh connection is complicated, also in low traffic hours the performance is not the same. so i want to monitoring this behavior and do a performance increase plan, so my questions are:

1. in high traffic hours: what should I check? RAM? processor? concurrent connections?

2. the server based in ubuntu needs a performance increase plan? how often? how should this plan be?

3. is there a way to know if the network traffic is causing high times response?

any other suggestion?

regards

---

### Post by SeijiSensei on 2012-09-10
How are you measuring traffic?  What kind of connection do you have to the Internet?  Is there any reason to think it's not simply network congestion?

How much memory does this machine have?  Are you running other things on it?  If the server has to use swap rather than physical memory alone it will be much slower.  

Has the database grown considerably larger over time?  Did you build this app yourself or is it pre-packaged? If it's your own app, did you design the database?  How good are your indexes?  Try running the same queries the app would make using a command-line client and see how long they take.

---

### Post by ninadpchaudhari on 2012-09-10
Wow( & thanks) for the reply  from  :KS SeijiSensei  :KS Do check out those things, 
do check the top command !

---

### Post by HugoSerrano on 2012-09-10
*Like* on SeijiSensei Post.
Should be enough to start debug. Also, install "htop", it's more pretty then "top"

Did you make any code changes?

Regards!

---

