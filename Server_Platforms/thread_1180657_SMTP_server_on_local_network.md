---
title: "SMTP server on local network"
date: 2009-06-07
forum: Server Platforms
---

### Post by lang79james on 2009-06-07
I have read and read and read and searched and searched.... But I have found no answers other then this is where windows is better. I have computer Server that is my main server,now down the road I might add Mysql to that server but not yet, and I have a Laptop that I am using to learn PHP. Seeing how my main server is the back bone of my main site that is running on a virtual machine I gave it a smtp server role. Not sure if it works but here is my main question. How do I configure my laptop php.ini so it will send mail to my server and then passes it to gmail

My goal is to use php to send mail using my gmail account and email
So when I make a page that sends mail to either my self or some else from my webserver it returns send the mail to my main server and passes it to gmail to my self or some one else.

My main server is running Linux mint
My Laptop is running Linux mint

I also know it is possible and hella easy to do with Windows because for a time I was running Moddle a php program to achieve the same thing.

I am trying to avoid using a local resources when I have other computers to run them. 

In addition how can I test to see if my main server smtp server is working... 

Any help would be nice 

What I have done so far
[behindmyscreen gmail in 101]("http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps#c1065314")

---

### Post by noway2 on 2009-06-07
Creating a mail sever is not an easy task.  My initial advice would be to read the many of the howto documents available.

An email server is really a collection of several programs, interacting on various layers.  You will first need a program, such as postfix, which acts as a Mail Tranfer Agent (MTA), which will provide the SMTP services.  On top of that, you will need a IMAP or POP server application. The two that seem to be most popular are Dovecot and Courier.  It is also possible to integrate these programs with a MySQL database to host virtual users and virtual domains.  I personally found this document to be very helpful: [http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/](http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/)

To answer your question about how to test your SMTP server, the simple answer is that you could telnet into it at port 25.  From there you can issue basic commands to the server and see if you get an appropriate (200-level) response.  Using the telnet you should be able to send and receive emails and verify that your user authentication works.

---

### Post by lang79james on 2009-06-07
Ok the more I read more this is going to be fun and full of enjoyment setting it up and all worth it in the end. But really MySql is really for web design and not for Email and the commen thing I see in a lot of how to's are trying to make their linux become a full mail server for their domain. I how every just want to send mail and not store it on my server. 

Now if I understand this right from what I am reading I would need for my needs

I needs a SMTP server in this case Postfix for sending the message. 
So assuming that this is working on my main server.

On my laptop I would need an email program to send the message to my main server that I have link in the php.ini

So if I am right the flow would be php code on laptop triggers the email program to send the message using my smtp server to where it needs to go in order to use the mail () code to work? Now this where I no longer follow how is that differant from the mailto html....or am I over thinking something that just works.

---

### Post by LepeKaname on 2009-06-07
You can use my script to install postfix/dovecot/spamassasin/clamav in less than 5 minutes. As it is interactive you can restart the whole process as many times you want. I have tested it in 4 servers and so far no problem. It has a medium-high security setting so it may help you to start from there.
Also, if you have time, you can read the tutorial, so you know exactly what it do and how it is done.

[http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html](http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html)

Before use them, I suggest you to check the --help of each script.
If you have any problem with my script you can post it here as well.

---

### Post by noway2 on 2009-06-08
Just to clarify on lang79james' post(s).

I am not sure you quite understand how the behind the scenes portions of the mail system works, or at least I don't understand your understanding of it ;)

At the back end, mail is transfered between mail transfer agents, such as a postfix.  These MTAs use the smtp protocol to hop the mail along on its chain.  If you look at the full headers in an email you can see the action of these smtp servers.  It will say something like Received from: some server.

Once the mail has reached its final destination, it will be 'delivered' by that MTA, as opposed to relayed.  In the delivery, it will be stored on the server for local retrieval.  Typically the mail is stored in either maildir or mailbox format.

Once it has been stored, you can use a mail user agent program, to retrieve the items (pop / imap) OR to connect to the smtp server.

I suppose, assuming this is what you are after, you could write a php script to run on your laptop and talk to the SMTP server.  The SMTP protocol isn't too difficult, at least in a basic sense, and the directions on how to test your mail configuration should get you started there - as well as test your smtp server.

---

