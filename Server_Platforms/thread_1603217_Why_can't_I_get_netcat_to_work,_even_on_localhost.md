---
title: "Why can't I get netcat to work, even on localhost?"
date: 2010-10-22
forum: Server Platforms
---

### Post by ayqazi on 2010-10-22
OK here's what I'm doing:

On terminal 1, I enter:

$ nc6 -vlp 5000
nc6: listening on 0.0.0.0 5000 ...

On terminal 2, I enter:

$ nc6 -v localhost 5000
nc6: ygt-asfandq (127.0.0.1) 5000 [5000] open


Now, as SOON as I make the connection on terminal 2, both netcats immediately quit back to the command prompt.  The return code for both is 0.

I do not have ANYTHING in my firewall (I checked with sudo iptables -v -L)

I have attached a wireshark trace of the conversation... can anyone help me decipher it?

Thanks

---

### Post by HermanAB on 2010-10-22
Here is a guide:
[http://www.aeronetworks.ca/netcat-howto.html](http://www.aeronetworks.ca/netcat-howto.html)

---

### Post by ayqazi on 2010-10-22
Thanks for your response.  However would you mind re-reading my post?  You will see that my problem is a lot more complex than basic usage.

I should mention that I have tried the commands in my original post on another box and it all works fine.

Thanks,
     Asfand

---

