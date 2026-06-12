---
title: "Kopete sending/recieving webcam at same time?"
date: 2006-07-08
forum: The Cafe
---

### Post by Rackerz on 2006-07-08
I was wondering if anybody has this working? I can only send but not recieve or recieve but not send. If anybody has, how have they done it?

---

### Post by Randomskk on 2006-07-08
I have it working, it pretty much worked out of the box for me.

One little thing, I do have some port forwards set form before that might be helping out.
Ports 6890 to 6900 TCP *and* UDP forwarded to my desktop and it seems to work.

---

### Post by Rackerz on 2006-07-08
In my router I have the option to set a 'Trigger port' and a 'Public Port' would I put 6890 as the Trigger and 6900 as the Public? 

Thanks.

EDIT: I tried doing that and it worked perfectly! Thanks for your help :).

---

### Post by Randomskk on 2006-07-08
Trigger ports tend to be for mass forwarding many ports once a certain port is accessed, although this may change depending on router. Look for an option to port forward, you need to port forward all the ports between 6890 and 6900 inclusive UDP and TCP.
If you need help, [www.portforward.com](www.portforward.com) should have a guide for your router.

---

