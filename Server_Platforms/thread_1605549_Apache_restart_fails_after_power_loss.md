---
title: "Apache restart fails after power loss"
date: 2010-10-25
forum: Server Platforms
---

### Post by calast on 2010-10-25
I have observed a problem twice now with Apache trying to restart but hanging somewhere in the process. This happens after a power failure; the machine comes back just fine, but not the web server. The machine is on a UPS, but occasionally it runs out of "juice" before someone can get to it (we have a generator for emergencies).

When this happens, a ps indicates about three processes running that are trying to start Apache, but they just sit there - this time for three days since the power failure was on a Friday. I can fix this by killing those processes and doing an Apache restart - but that takes human intervention, which is not acceptable. 

I suspect this may have to do with SSL, since when I do a manual restart it asks me for the SSL password. There must be some way around this so the system can recover on its own. This system's web site runs under SSL since it maintains medical information that must by law be protected. But it also could be life-threatening to someone if the system can't come back and as a result a person can't get help.

So I would appreciate some guidance as to what I could change that would allow for system recovery without intervention. I'm happy to provide any configuration file info, if you tell me where to look.

Thanks.

---

### Post by Vegan on 2010-10-25
SSL is what the problem is, so if you need it up longer, get a bigger USP and make sure the generator is automatic.

You can also install SSL telnet and log-in remotely and see what the problems are and you restart anything from the CLI.

its called opensslserver,or smething like that

Then you can use a Windows, Mac or Linux machine and connect from the LAN, or open the port on the firewall and anywhere form the internet.

---

### Post by calast on 2010-10-27
So, you're telling me an Apache server with SSL can't be restarted automatically at power-up?

I already know how to fix the problem from home, which is what I do. In fact, this can only be fixed by remotely logging in to the machine, since there's no display or keyboard on the server. (Makes me wonder where it would be asking for a password...) But if no one tells me there's a problem, I don't know that I need to address the issue.

---

### Post by SeijiSensei on 2010-10-27
[http://www.modssl.org/docs/2.8/ssl_faq.html#ToC31](http://www.modssl.org/docs/2.8/ssl_faq.html#ToC31)

---

