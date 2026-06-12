---
title: "Postfix Setup"
date: 2007-02-26
forum: Server Platforms
---

### Post by ton80 on 2007-02-26
Hello Forum,

I am working on setting up an email server for my own education.  The documentation I found for doing this with Ubuntu talks about using TLS.  Is it required to do this?  Is this how normal email servers are configured?  I don't recall having to deal with certificates before.
Just trying to get this going and I want to do it correctly.

Thanks,
Mike

---

### Post by Mr. C. on 2007-02-26
TLS is an encryption layer, used to secure communication over an insecure network.  It is useful when you have remote clients that need to connect to your server to submit email.

For your personal use, you probably don't need it.

If you decide you want to send email via your server remotely, you can either setup a VPN, create and SSH tunnel, or use TLS.

---

### Post by ton80 on 2007-02-26
Ok,
So does that mean I can ignore the configuration section regarding TSL?  Will there be any adverse affects on the configuration?

Thanks for the help,
Mike

---

### Post by Mr. C. on 2007-02-26
I'm not sure which documentation you are using, nor how you are going about your setup of postfix, so I can't give advice on that without more info.

Postfix will use TLS only if it has been compiled into the postfix binaries, and its configuration files are configured to use TLS.  So if you are downloading precompiled binaries, then you can choose the non-TLS binaries if you desire.  If you are building from source, you can simply not configure TLS in the compile line.

---

### Post by Abhi Kalyan on 2007-03-09
Hi,
Am working on postfix too. Could you please point me to the documentation that you are talking about?

---

