---
title: "Not receiving mail Exim"
date: 2010-02-04
forum: Server Platforms
---

### Post by Rich78 on 2010-02-04
I've setup Exim4 as an MTA on my VM which has a static IP.

I've pointed the MX records both idential to this static IP.

I can send out via command line on the VM using Exim commands and receive the mail in my home account no problem, it also displays the correct from address ie [email]rich@mydomain.co.uk[/email]

So I'm not sure what's going on with receiving the mail.

If I send a mail from my home email to [email]rich@mydomain.co.uk[/email] (not real address), I don't get a bounce or anything, it just goes out never to be seen again.

Any help or suggestions greatly appreciated, I've lost many evenings on this.....

---

### Post by Rich78 on 2010-02-04
Sorry to bump this but I'm really stuck with this one.

Is there a way to test how far mail has got (client side) or that my mail server is accepting messages?

---

### Post by Rich78 on 2010-02-04
Just received this mail back from googlemail (account I used to send a test email to my server)

Note: I've edited my IP and domain from the below.

[IPAddress.mydomain.co.uk. (10): Destination address required]
[IPAddress.mydomain.co.uk. (20): Destination address required]

So I wonder if I've done something wrong with the MX records or if I need something else setup on the server?

I just used the same static server IP for the MX records of both priority 10 and priority 20.

---

### Post by Rich78 on 2010-02-05
Now solved with installing Bind9 and configuring DNS.

---

