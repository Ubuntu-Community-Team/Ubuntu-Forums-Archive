---
title: "mail from webserver question"
date: 2008-08-12
forum: Server Platforms
---

### Post by johan.alfa on 2008-08-12
Hello all,

Before I was using xampp.
Now I set up a lamp ssh ubuntu server.

I would like to send mail from some web pages.
I don't need mail read or advanced mail stuff.

In xampp I could change php.ini smpt and everthing worked fine.
Xammp used then my ISP smtp server.
How can I simulate this with ubuntu.

greetings,

---

### Post by dperfors on 2008-08-12
The same way, just change the /etc/php.ini

---

### Post by johan.alfa on 2008-08-12
Don't I have to install sendmail or something like postfix?
I thought the smtp setting in php.ini was windows only.

greetings,

---

### Post by hyper_ch on 2008-08-12
yes, you need a MTA... sendmail or postfix could be working. Not sure if you can set in the php.ini to actually relay email to another server.

---

### Post by dperfors on 2008-08-12
I thought this was possiblem but I am not 100% sure..

---

### Post by hyper_ch on 2008-08-12
I think it is - but I never was in such a situation where I needed to do it ;)

---

### Post by windependence on 2008-08-12
> **johan.alfa said:**
> Don't I have to install sendmail or something like postfix?
I thought the smtp setting in php.ini was windows only.

greetings,

Actually this should work by default since sendmail is installed, but as hyper_ch mentioned Postfix would be much better. You can use the php mail() function.

-Tim

---

### Post by johan.alfa on 2008-08-12
Is sendmail installed?
I only checked lamp and ssh during server install.

When typing sendmail on the command line I get a mention of packages which will install sendmail.

I do not want install software I do not need.

greetings,

---

### Post by windependence on 2008-08-12
Sendmail <should> be installed by defualt on most distros. I would be surprised if it isn't, however if not, don't install it, but install postfix instead, it's much easier to configure and more secure than sendmail.

-Tim

---

### Post by johan.alfa on 2008-08-13
Am I wrong thinking postfix will open a new port on the server?
I would like to send mails.
I do not neet te receive anything.
Is it possible to send mails some way without opening new ports?

Thanks,

---

### Post by gishaust on 2008-08-13
You need to make sure that you have the port open on the firewall on the box that has apache server, postfix and dns( i think). but I have never had the router onto the internet port open for postfix or dns. There is one draw back if you send the email to [email]fred@gmail.com[/email] I will turn up in spam. and some isp will block it altogether. Because they can't talk to postfix. but if you are only using it on a form on one or two web sites and you choose the right email address it is fine. I would go gmail

I think from memory you also need dns but it is a while since I did it? if you have a look at some of you old post you will see i asked something similar. Don't laugh to much I was very raw.:wink:

gishaust

---

### Post by MJN on 2008-08-13
> **johan.alfa said:**
> I would like to send mails.
I do not neet te receive anything.If you have access to an external mail server, e.g. that of your ISP's, then you might want to check out [Nullmailer]("http://untroubled.org/nullmailer/") - you'll find it in the repositories. It is a simple outbound-only MTA which will pass mail onto your upstream mail server for onward delivery.
 
Mathew

---

### Post by johan.alfa on 2008-08-13
Hello,

I could not find Nullmailer in the standard server repos.
Are they in the backport?

greetings,

---

### Post by MJN on 2008-08-13
You should find it in *universe*.
 
Mathew

---

### Post by johan.alfa on 2008-08-13
Hello,

Nullmailer is working fine over here.
Only problem I still have is php apche is sending mail as [email]www-data@bla.bla[/email].

Anybody knows how I can change the www-data to something else?

greetings,

---

### Post by MJN on 2008-08-13
The From: address can be specified in your PHP mail function as an additional header - see example #2 at [http://uk.php.net/manual/en/function.mail.php](http://uk.php.net/manual/en/function.mail.php)

Mathew

---

### Post by windependence on 2008-08-13
> **gishaust said:**
> You need to make sure that you have the port open on the firewall on the box that has apache server, postfix and dns( i think). but I have never had the router onto the internet port open for postfix or dns. There is one draw back if you send the email to [email]fred@gmail.com[/email] I will turn up in spam. and some isp will block it altogether. Because they can't talk to postfix. but if you are only using it on a form on one or two web sites and you choose the right email address it is fine. I would go gmail

I think from memory you also need dns but it is a while since I did it? if you have a look at some of you old post you will see i asked something similar. Don't laugh to much I was very raw.:wink:

gishaust

I see you have an MTA working and that's great!

Just for future reference and for everyone reading this, Postfix can be configured to do exactly the same thing and it's pretty easy.

Gishaust, you do not need a DNS server for sending mail OR for web hosting. For some reason, everyone here thinks you do. 

On the gmail thing, it has nothing to do with postfix, it has to do with people setting up "half baked" mail servers. I have postfix running on my formums and we have no problem sending to gmail accounts, BUT I have a static address, and reverse DNS is set up for my domains. What happens is if the gmail mail server cannot resolve your name from the IP it will reject the mail and rightly so. So if you are using some kind of work around like dynamic DNS service, it's not going to work because you don't have a static IP that resolves to your domain, therefore they think it's either being spoofed, or relayed.

Then there are some ISPs like Comcast that don't allow ANY mail to be sent from there IP range (unless you have a business account).

-Tim

---

### Post by johan.alfa on 2008-08-13
Hello all and thanks for helping,

@windependence 
I tried postfix and it does indeed the same if installed like a satelite. But I could not make the from address as I wanted.
With null mail I can make it look like [email]www-data@bla.net[/email]
But with postfix I had to make it like [email]www-data@bla.bla.net[/email] to work. This was one bla to much. 
I would like to use postfix or something else but the install is above my head for the moment.

greetings,

---

### Post by gishaust on 2008-08-13
Thanks for the info. This thread has been great learned so much.

---

### Post by MJN on 2008-08-13
> **johan.alfa said:**
> I tried postfix and it does indeed the same if installed like a satelite. But I could not make the from address as I wanted.
With null mail I can make it look like [EMAIL="www-data@bla.net"]www-data@bla.net[/EMAIL]Have you changed your PHP code now?

Mathew

---

### Post by obscenic on 2008-09-21
> **MJN said:**
> Have you changed your PHP code now?

Mathew

This does not work, nullmailer still sends from www-data.
I've been fighting with this all day to no avail.  If anyone knows of a solution, I would be extraordinarily grateful.

In my case, my SMTP (example.ca) - auth based SMTP, rejects mail in which from addresses are not from [email]validuser@example.ca[/email]

Any thoughts?

---

### Post by obscenic on 2008-09-21
Workaround:

On your SMTP host, create a mail account called www-data...
Stupid, but unless nullmailer comes up with a way to overwrite the from address, there's not really any other solution.

---

