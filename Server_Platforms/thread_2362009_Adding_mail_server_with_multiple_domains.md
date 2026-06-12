---
title: "Adding mail server with multiple domains"
date: 2017-05-23
forum: Server Platforms
---

### Post by eyasso on 2017-05-23
Hello,

I hope I am in the correct sub forum.

I have installed Ubuntu version 16.04. I also installed apache2 and have two web sites with two different domains running on it.
Both domains accessible from the world.

I would like to add a feature (contact form) to my websites where users can fill in their details and send the details as mail.
I have a php script which attached to the html page.

My question is how do I configure the server to send email with the right domain per page with the right domain?
For example: i have tow domains and html websites: x.com and y.com.
When users clicks the "SUBMIT" button on the html page (x.com), php file calls mail() function which sends mail from [email]example@x.com[/email].
Same for y.com to send mail from [email]example@y.com[/email].

Thanks,

---

### Post by howefield on 2017-05-23
Thread moved to the "*Server Platforms*" forum for a better fit and welcome to the forums.

---

### Post by eyasso on 2017-05-29
Anyone?

---

### Post by SeijiSensei on 2017-05-29
I wouldn't bother to change the From address if all the notices are going to you.  Just use a sender address in the same domain as the server itself.  Make sure that the results sent back from the form specifically identify which web site is involved.  You might also consider using addresses with "+" signs to discriminate via the From address.  For instance, you could address replies for domain1 with "From:  [email]admin+domain1@example.com[/email]".   That would make it easy to construct a filter on your mail client to direct mail from each domain into separate folders.

How to do what you ask depends on the mail software you're using.  If it's Postfix, read this: [http://www.postfix.org/VIRTUAL_README.html](http://www.postfix.org/VIRTUAL_README.html).  For sendmail, make sure the www-data user is included in /etc/mail/trusted-users.  Then Apache can set the envelope sender to match the From address.

If your server is going to be sending notices to users as well, make sure you've set up [SPF records]("http://openspf.org/") for both your domains in their DNS like this:
```
IN     TXT     "v=spf1 a:yourserver.example.com  ~all"
```
That tells compliant servers that yourserver.example.com is a valid sending server for the domain.

---

### Post by eyasso on 2017-05-29
To start of, I have no idea how to configure mail server in Ubuntu. 
I want the email to send mails only and not receive. 

The mails go to different people, so the from and to are different.
Do you know where I can find tutorial to configure mail server?

Thanks,

---

### Post by SeijiSensei on 2017-05-29
SSMTP is a common solution for this.  See [https://help.ubuntu.com/community/EmailAlerts](https://help.ubuntu.com/community/EmailAlerts)

While that document concerns sending mail from the command prompt, once SSMTP is installed it should work for all applications.

---

### Post by eyasso on 2017-05-29
I have a web page which binds to php script. WHen user clicks "SUBMIT" button on the HTML page, a method on the php script is called. 
In the php script, I call mail() function. Mail function should send mail from the account attached to the domain of the html page.

Thanks,

---

### Post by SeijiSensei on 2017-05-29
Did you even read the document I posted?  You're just asking the same question over again.

SSMTP will provide a "listener" on the machine to which the PHP script can send mail using the mail() command.  SSMTP will then send out the message to the designated address.

A PHP script by itself cannot send mail even via the mail() function.  There has to be an SMTP server of some kind to which the mail is directed.  SSMTP is the simplest of these since it is outbound-only.

---

### Post by eyasso on 2017-06-01
Hello,

I understand what you say. I understand that a PHP script by itself cannot send mail even via the mail() function.
But I don't understand hot to configure SSMTP to send mail from specific domain (assuming I have several domains hosted on my server) assuming php script called from html page.

How do I bind SSMTP to send mail from domain (x.com) when called from (x.com html page) assuming I also have y.com and z.com domains hosted on my mcahine?

Thanks,

---

### Post by SeijiSensei on 2017-06-01
Just configure the application to use [email]something@x.com[/email] as the From address on the x.com website.  Use equivalent addresses on the other sites.  Configure ssmtp with the server's own domain.

If you were accepting mail for those domains, things would be more complicated.  In an outbound-only arrangement like yours, what matters more is having SPF records in the domains' DNS as I mentioned above. 

I'm assuming that this server is directly on the Internet.  If it's on a residential connection, you may not be able to send mail at all.

---

### Post by eyasso on 2017-06-05
So the mail server will know from which domain to send the mail based on the from?
The server in in Amazon.

Thanks,

---

### Post by SeijiSensei on 2017-06-06
There really isn't anything else involved with "knowing which domain to send from" other than the From address.  The From domain need not match the domain in which the server resides, though the From domain should have a matching SPF record to tell receiving servers that your server legitimately sends mail for the domain.

Have you actually tried this yet?  Surely it shouldn't take more than a few minutes to configure the PHP apps accordingly.

---

