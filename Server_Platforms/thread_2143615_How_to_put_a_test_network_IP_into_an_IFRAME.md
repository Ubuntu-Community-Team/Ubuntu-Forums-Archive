---
title: "How to put a test network IP into an IFRAME"
date: 2013-05-09
forum: Server Platforms
---

### Post by psyllex on 2013-05-09
Hello all,

I have a problem. I have a apache web site that I want to put in an iframe.  That's simple enough except that the site I want to put in the iframe is being redirected onto the test network and then we use the terminal to instantiate firefox to view it.  You can easily view the site on the management network but we're playing Hacker with it and when say we run a simple udp flood....we see no effect on the management network.  The test network obviously crashes, so this is the one we need to view with an iframe that holds some custom monitoring tools (graphs and such) we made.  I'm not sure how the redirect was done my partner did that but I know that I jump on the terminal and input ```
ssh -XC me@myipaddress
``` then I input ```
firefox
``` which brings up the browser with the site being redirected through the test network.  Can anyone help?  Thanks a lot

---

### Post by matt_symes on 2013-05-09
I have moved you thread to the **server platforms** subforum as you may get a better answer there.

Wireless and networking is used for driver, hardware, connections issues.

I have left a redirect in place for you though.

---

