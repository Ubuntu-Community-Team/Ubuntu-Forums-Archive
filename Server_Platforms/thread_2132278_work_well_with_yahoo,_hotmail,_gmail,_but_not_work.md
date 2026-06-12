---
title: "work well with yahoo, hotmail, gmail, but not work with some domain"
date: 2013-04-04
forum: Server Platforms
---

### Post by computerzman on 2013-04-04
hello, all my dear members,

i setup a new mail server in my home to use it in e-marketing
i have take real (static) ip from my ISP
i configure postfix & dovecot
everything work well when i send to yahoo, hotmail, gmail
but when i want to send  or receive from or to for some other domains for some real sites, i got the following errors 

_**i supposed the following:**_
- [COLOR=#ff0000]**targethost.com**[/COLOR] -> is the domain which i want to send to it from my server (i have hosting in hostgator not in my home)
- [COLOR=#ff0000]**example.com**[/COLOR] - > is my configured home server.

_**i want to mention for something important**_
when i change [COLOR=#ff0000]**myorigin **[/COLOR]value from [COLOR=#ff0000]**example.com**[/COLOR] to [COLOR=#b22222]**server1**[/COLOR][COLOR=#ff0000]**.example.com**[/COLOR] everything work well and all messages sent correctly. 
but my mail when i use this way appear as [COLOR=#ff0000]**myusername**[/COLOR]**@**[COLOR=#b22222]**server1**[/COLOR][COLOR=#ff0000]**.example.com**[/COLOR] , but i don't it to appear as it. 
i want it to appear as [COLOR=#ff0000]**myusername**[/COLOR]**@**[COLOR=#ff0000]**example.com**[/COLOR].


_*** When I try to send from my home server to [COLOR=#ff0000]targethost.com[/COLOR]:**_

Apr  4 09:50:01 example postfix/smtp[4415]: 0B4DE381AF6: to=<**admin**[COLOR=#b22222]@[/COLOR][COLOR=#ff0000]**targethost.com**[/COLOR]>, relay=[COLOR=#ff0000]**targethost.com**[/COLOR][xx.xx.xx.xx]:25, delay=3, delays=0.29/0.13/2.3/0.3, dsn=5.0.0, status=bounced (host [COLOR=#ff0000]**targethost.com**[/COLOR][xx.xx.xx.xx] said: 550-Verification failed for <[COLOR=#ff0000]**myusername**[/COLOR]**@**[COLOR=#ff0000]**example.com**[/COLOR]> 550-No Such User Here 550 Sender verify failed (in reply to RCPT TO command))
\\\\\\\\\\\\\\\\\\\\\\

**and when i go to the [COLOR=#ff0000]targethost.com[/COLOR] and try to send from it to [COLOR=#ff0000]myusername[/COLOR]@[COLOR=#ff0000]example.com[/COLOR]:**
-------------------------------------------------------------------------------------------------
This message was created automatically by mail delivery software.

A  message that you sent could not be delivered to one or more of its  recipients. This is a permanent error. The following address(es) failed:

  **[COLOR=#ff0000]myusername[/COLOR]@[COLOR=#ff0000]example.com[/COLOR]**
    No Such User Here

--------------------------------------------
excuse me for bad English ...  

Anyone can help me?

---

### Post by darkod on 2013-04-04
I think it has to do with authentication, but I'm not 100% sure. You can use [email]username@domain.com[/email] only if you actually have domain authentication (Active Directory, LDAP, etc). Otherwise, local users created in ubuntu would have the format [email]username@computername.domain.com[/email] if I'm not mistaken. That's why it works if sending from [email]username@server1.example.com[/email].

Also double check the postfix config file if you have the domain that you want to use specified there.

I might be wrong, but the above sounds logical to me.

---

### Post by computerzman on 2013-04-04
> **darkod said:**
> I think it has to do with authentication, but I'm not 100% sure. You can use [EMAIL="username@domain.com"]username@domain.com[/EMAIL] only if you actually have domain authentication (Active Directory, LDAP, etc). Otherwise, local users created in ubuntu would have the format [EMAIL="username@computername.domain.com"]username@computername.domain.com[/EMAIL] if I'm not mistaken. That's why it works if sending from [EMAIL="username@server1.example.com"]username@server1.example.com[/EMAIL].

Also double check the postfix config file if you have the domain that you want to use specified there.

I might be wrong, but the above sounds logical to me.

Thank you (darkod) form replying, OK, If I Install LDAP in the same machine, does it solve this problem?
If it will solve, do you have any good tutorial links for that?

Thanks in advance....

---

### Post by darkod on 2013-04-04
As I said, I'm not 100% sure it will solve the issue or not. You mght have another issue with authentication, and how you present your domain and user. You are probably aware that there are strict rules in place for mail servers to try and prevent spamming. If data doesn't match, in most cases emails will be declined by the receiving server.

Otherwise, the ubuntu server documentation section about network authentication is here:
[https://help.ubuntu.com/12.04/serverguide/network-authentication.html](https://help.ubuntu.com/12.04/serverguide/network-authentication.html)

---

### Post by computerzman on 2013-04-04
> **darkod said:**
> As I said, I'm not 100% sure it will solve the issue or not. You mght have another issue with authentication, and how you present your domain and user. You are probably aware that there are strict rules in place for mail servers to try and prevent spamming. If data doesn't match, in most cases emails will be declined by the receiving server.

Otherwise, the ubuntu server documentation section about network authentication is here:
[https://help.ubuntu.com/12.04/serverguide/network-authentication.html](https://help.ubuntu.com/12.04/serverguide/network-authentication.html)


Any way thank you (darkod) for your help, I will wait, may be anyone can help me ....

---

