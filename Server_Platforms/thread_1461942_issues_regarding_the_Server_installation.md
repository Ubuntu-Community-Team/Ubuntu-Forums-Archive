---
title: "issues regarding the Server installation"
date: 2010-04-24
forum: Server Platforms
---

### Post by AresArtemis1 on 2010-04-24
hi, any professionals, I want to install a website hosting server, a DNS server, a Email server, for learning purpose. could you tell me which version Ubuntu server system is the best, and could you tell me the link of help documents of how to install those server, and does Ubuntu server provide a friendly install and configure interface(like windows), so I could configure those server easy.



best regards and thanks,

:guitar:

---

### Post by windependence on 2010-04-24
Do you want to learn, or do you want an easy GUI install thing like Windoze? If you want to learn, you really don't want to install a GUI on the server version. If you want easy, then use the desktop version to implement your plans. The server optimizations are not going to help you in your learning experience anyway.

-Tim

---

### Post by Vegan on 2010-04-24
> **AresArtemis1 said:**
> hi, any professionals, I want to install a website hosting server, a DNS server, a Email server, for learning purpose. could you tell me which version Ubuntu server system is the best, and could you tell me the link of help documents of how to install those server, and does Ubuntu server provide a friendly install and configure interface(like windows), so I could configure those server easy.



best regards and thanks,

:guitar:

From a fresh intall of Ubuntu Linux Server

sudo tasksel lamp
sudo tasksel bind9
sudo apt-get install postfix

you can manage all this from webmin, like I do, so that a desktop is not needed. I installed the desktop though to be able to have a backup browser when the Windows box craps out.

---

### Post by AresArtemis1 on 2010-04-24
ye, I just want an easy GUI to help me install server and configure the web hosting server, for example, a GUI interface of configure DNS, mail, Apach, Mysql server, does the new version 10.0x Ubuntu server provide those GUI?

and does highest version 10.0x Ubuntu server mean the highest performance?

best thanks:guitar:

---

### Post by windependence on 2010-04-25
> **AresArtemis1 said:**
> ye, I just want an easy GUI to help me install server and configure the web hosting server, for example, a GUI interface of configure DNS, mail, Apach, Mysql server, does the new version 10.0x Ubuntu server provide those GUI?

and does highest version 10.0x Ubuntu server mean the highest performance?

best thanks:guitar:
The server edition comes with no GUI on purpose:

> **No X server by design**

  By design, Ubuntu Server Edition does not include an X server or any  graphical desktop applications. This is a deliberate choice as we  believe that most servers should be serviced remotely, are safer without  the addition of code that needs direct communication from user space to  hardware, and should not be used as a desktop by their administrator.  
 [INDENT]  	"*So I applaud the Ubuntu team’s common  sense (and courage) in keeping the X Window System out of the default  installation of Ubuntu Server.*"
	--Mick Bauer in April 2008 Linux Journal - "Security Features in Ubuntu  Server"
[/INDENT]

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)

As to performance, no, latest and greatest does NOT mean it will be the fastest OR the most stable. Frankly, I would wait a good few months until you are sure they have the major bugs worked out before deploying.  We will run a test box in our shop, but I probably won't deploy on the new LTS server for at least 3 months. Many times the new versions are actually slower than previous versions. Of course, YMMV.

-Tim

---

### Post by AresArtemis1 on 2010-04-25
thank you, my American friend, I understood, so could I use my Ubuntu Studio 9.10 laptop to connect the server, which I am going to install, and does the Ubuntu Studio 9.10 provide any tool, which has the GUI interface to let me develop and configure the server, for example, as I know that we have a database develop tool like the MySQL admin to develop the database, do does Ubuntu Studio provide other GUI tools to let me configure the DNS server, the mail server, the Apache server, etc..

best regards,

your Canadian friend

---

### Post by windependence on 2010-04-26
I would recommend installing WebMin if you want to configure your server graphically without having a heavy GUI installed. WebMin can be installed fairly securely by using SSL.

-Tim

---

