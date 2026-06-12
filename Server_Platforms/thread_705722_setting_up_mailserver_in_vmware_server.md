---
title: "setting up mailserver in vmware server"
date: 2008-02-23
forum: Server Platforms
---

### Post by Abandon on 2008-02-23
I' m working on a Ubuntu feisty machine and created an virtual machine with Vmware server. I installed Ubuntu server edition and created a LAMP install. This works the way it should be. ([www.pixelclub.nl](www.pixelclub.nl), but only live during office hours in Europa.)

I can't however get postfix to run. When I do a telnet mail.pixelclub.nl 25 the process stops trying to connect with my providers IP adress. I did open port 23, 25, 80, 110 on my router

So I am doing something wrong, or is it not possible to run postfix from within a virtual machine?

---

### Post by HermanAB on 2008-02-23
Here is a postfix based mail server appliance for VMware:
[http://www.allard.nu/mailserver/](http://www.allard.nu/mailserver/)

---

### Post by Abandon on 2008-02-24
Ok, but that does not answer my question. Do you need such a solution, is it not possible to use a normal postfix setup?

---

### Post by kwambus on 2008-02-24
Yes it is entirely possible to run Postfix in a Virtual Appliance, I have done many times.

With regard to your port problems, it is helpful to post portions of your /var/log/mail.log when you start the postfix service. This may help identify the issues you have.

Also, try "telnet localhost 25" and it should indicate whether Postfix is actually running locally.

---

### Post by Abandon on 2008-02-24
> **kwambus said:**
> Yes it is entirely possible to run Postfix in a Virtual Appliance, I have done many times.

With regard to your port problems, it is helpful to post portions of your /var/log/mail.log when you start the postfix service. This may help identify the issues you have.

Also, try "telnet localhost 25" and it should indicate whether Postfix is actually running locally.

telnet localhost 25 is working properly. I will look at /var/log/mail.log. Thanks for you' re reply.

---

### Post by Abandon on 2008-02-24
ok,  I did find the time to check:

telnet localhost 25 works and gives this enty in my log:

Feb 24 14:13:46 pixelclub postfix/smtpd[4320]: connect from localhost[127.0.0.1]
Feb 24 14:14:37 pixelclub postfix/smtpd[4320]: 9EF4FCC0C7: client=localhost[127.0.0.1]
Feb 24 14:14:57 pixelclub postfix/cleanup[4323]: 9EF4FCC0C7: message-id=<20080224131437.9EF4FCC0C7@pixelclub.lan>
Feb 24 14:14:57 pixelclub postfix/qmgr[4048]: 9EF4FCC0C7: from=<root@localhost>, size=358, nrcpt=1 (queue active)
Feb 24 14:14:57 pixelclub postfix/local[4324]: 9EF4FCC0C7: to=<jos@localhost>, relay=local, delay=31, delays=31/0.04/0/0.03, dsn=2.0.0, status=sent (delivered to maildir)
Feb 24 14:14:57 pixelclub postfix/qmgr[4048]: 9EF4FCC0C7: removed
Feb 24 14:15:01 pixelclub postfix/smtpd[4320]: disconnect from localhost[127.0.0.1]

My servername is pixelclub
My router identifies this as pixelclub.lan
My domainname is pixelclub.nl

There is no record in the log when I give the command telnet mail.pixelclub.nl 25

---

### Post by faulkes on 2008-02-24
> **Abandon said:**
> 
There is no record in the log when I give the command telnet mail.pixelclub.nl 25

```

dig mail.pixelclub.nl

and

host mail.pixelclub.nl 

```

Faulkes

---

### Post by kwambus on 2008-02-25
Looks initially like your Postfix install is running fine, issues must be outside of the box. Check the DNS, check using telnet from another machine this side of your router/firewall. Also check telnet from outside of your router/firewall.

It's all a case of elimination.

---

### Post by Abandon on 2008-02-25
I have learned a lot these past da'ys. First, I have setup a mailserver within vmware server, but within the bridged modus. Meaning I have chosen vmware to be installed with this setting:

"Use bridged networking:

give the guest operation system direct access to an external ethernet 
network. The guest must have its own ip address on the external network."

In this setup I was trying to locate my own mailserver from my internal network. I now know that this is not possible. When I use another netwerk I can use the "telnet mail.pixelclub.nl 25 the way it is supposed to.

So..now I can receive and sent mail from my own server at home using thunderbird but I have to use my ipnumber:110/25 for connecting to pop and smtp. I have not yet figured it out from another network.

Slow...but learning :)

---

