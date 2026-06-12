---
title: "Emix4 listening on Port 25"
date: 2009-10-02
forum: Security
---

### Post by styxcoverbnd on 2009-10-02
Quick question for everyone. When I go into the terminal and run netstat -vatn to see my open connections I recieve:

127.0.0.1:631
127.0.0.1:25

Port 631 is CUPS and a sudo -nestat -tnlp shows that emix4 is the process listening on port 25 (port 25 I believe is usually for SMTP?) Anyone know what emix4 is, a quick google search did not bring up an answer? I'm assuming because emix4 is listening on port 25 for the local host that I am safe and it's nothing to worry about? I used to use evolution for email so could this be what is using emix4 on port 25?

---

### Post by scrooge_74 on 2009-10-02
emix4 or exim4? cause exim is the smtp server and he needs to listen at port 25

---

### Post by styxcoverbnd on 2009-10-02
> **scrooge_74 said:**
> emix4 or exim4? cause exim is the smtp server and he needs to listen at port 25

Oops sorry it is exim4. I am just running a standard desktop install of Hardy not the server version. Since exim4 is listening on the local host I don't have to worry about anything do I? I didn't install anything to setup an email server not sure what is using exim4.

---

### Post by scrooge_74 on 2009-10-02
maybe you installed something else that needs exim to send mail, check and if you dont really needed you can remove it.

---

### Post by styxcoverbnd on 2009-10-02
> **scrooge_74 said:**
> maybe you installed something else that needs exim to send mail, check and if you dont really needed you can remove it.

Thank you. My question now is if I do a netstat and receive 127.0.0.1:25 that means that exim4 is only listening to the local host not to outside connections correct? If that is the case that exim4 is only listening locally I'm not at risk to be attacked from the outside, that is if my router was set to allow connections to port 25? (Please note I'm just trying to understand exactly what the 127.0.0.1:25 means). Thanks.

---

### Post by rookcifer on 2009-10-02
> **styxcoverbnd said:**
> Thank you. My question now is if I do a netstat and receive 127.0.0.1:25 that exim4 it is only listening to the local host correct? If that is the case I'm not at risk to be attacked from the outside, that is if my router was set to allow connections to port 25? (Please note I'm just trying to understand exactly what the 127.0.0.1:25 means). Thanks.

Yes, when you see:

127.0.0.1:25

this means it is bound to localhost.

If you see:

0.0.0.0:25

It is listening to the Internet at large.  

In your case, everything is safe.

---

### Post by styxcoverbnd on 2009-10-02
> **rookcifer said:**
> Yes, when you see:

127.0.0.1:25

this means it is bound to localhost.

If you see:

0.0.0.0:25

It is listening to the Internet at large.  

In your case, everything is safe.

Thank you, I did not know that 0.0.0.0:25 would mean that it is listening to the Internet

---

