---
title: "What does this exactly mean?"
date: 2007-09-30
forum: Server Platforms
---

### Post by mickbuntu on 2007-09-30
Hello, I have a question in the server log what does this mean?

Does: 
::1 - - [30/Sep/2007:07:36:05 -0400] "GET /" 400 528 "-" "-"

Mean someone logged into virtual terminal 1  and received  a bad request?

Thanks in advance

---

### Post by koenn on 2007-09-30
it looks like a http request. Do you have a web server ?

---

### Post by steve.horsley on 2007-09-30
::1 is the loopback address, suggesting that the request came from your own machine.

---

### Post by mickbuntu on 2007-09-30
1. Yup, I was running a web server but turned it off recently. Moved my site, to a dedicated web server.
 
 
2. Thanks for the information must been when power got cut and restarted.
 
 
:-)
 
 
[SIZE=5]EDIT: It is apache restarting in the morning hours.[/SIZE] One of the logs show graceful restarts,  the log got rotated.

---

