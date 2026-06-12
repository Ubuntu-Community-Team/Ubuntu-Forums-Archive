---
title: "Gmail SMTP Setup?"
date: 2007-10-02
forum: Server Platforms
---

### Post by Oen386 on 2007-10-02
Hello everyone. I am trying to configure Gmail with SMTP using the setup directions from here:

[http://www.howtoforge.com/perfect_setup_ubuntu704_p5](http://www.howtoforge.com/perfect_setup_ubuntu704_p5)

That is how I have setup Postfix and SMTP.

I was wondering if anyone knew a way to modify the directions there to use Gmail instead.

My port 25 is blocked for my home server, otherwise I would not be doing this.

I believe the changes I need to make are adding the relayhost and login/pass. I believe the rest should work, but when I tried that before I did not get a working response. It would just time out.

Anyone have any suggestions?

Thanks.

---

### Post by Oen386 on 2007-10-02
I also meant to mention I am trying to get the PHP "mail()" function to use Gmail. I believe making the apporiate changes to Postfix will carry over to the PHP command.

---

### Post by milosz.galazka on 2007-10-02
Maybe you will find tips [here]("http://souptonuts.sourceforge.net/postfix_tutorial.html") ?

---

### Post by Oen386 on 2007-10-02
I read through about 80% of that, a lot seems redundant.

I was hoping someone would know a simple change or modification I could do to the tutorial I posted, rather than have to follow a much longer tutorial to get the same result.

---

### Post by Oen386 on 2007-10-04
So is that other guide my best bet then?

---

### Post by Scroobytec on 2007-10-04
Have you checked the Tips at GMail, they cover a number of clients. I used that to set-up both Thundebird and Evolution. But I do not remember all the different clients they covered, but there was one foe OTHER. These contain the ports and the security settings required for download.

---

### Post by Oen386 on 2007-10-04
Thanks for your input, but I am not trying to get an Email Client to connect, I am trying to get an Email Server to connect.

Also the guide that was posted doesn't cover my other concern: "I also meant to mention I am trying to get the PHP "mail()" function to use Gmail."

---

### Post by milosz.galazka on 2007-10-04
Maybe [this]("http://groups.google.com/group/list.postfix.users/browse_thread/thread/f9517a74d3c50e5a/41ad09f5f176ece9?lnk=gst&q=msmtp&rnum=7#") will help you...

---

### Post by vhof on 2007-10-10
or this: [http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html](http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html)

---

### Post by Oen386 on 2007-10-16
Thanks vhof that is what I was looking for. Also thanks to everyone else for helping me. :)

---

### Post by Oen386 on 2007-10-16
Well I jumped the gun... the link provided is very vague.

> The lines in tls_per_site, main.cf and master.cf are like the tutorial. Just paste them into your own versions, and you should be good to go.

Also people report he has information wrong:
> Worked great on Ubuntu 6.06 except for the Thawte certificate; so here's how to get it.
Download the Thawte root certificates from [http://www.thawte.com/roots/;](http://www.thawte.com/roots/;) uncompress the file and look for a file called ThawtePremiumServerCA_b64.txt.
You can then "cat ThawtePremiumServerCA_b64.txt >>cacert.pem " ant it should work.


Still can't get it to work. Everything looks fine. Yet no success.

---

### Post by gishaust on 2007-10-18
Oen368
I have just completed the same task.  and it works great but as a newbie things are a little vague so bear with me.

Packages
I have installed apache, mysq,l php, postfix and a dns server. I have a registered domain name.

Postfix is installed as a default server it  has to connect to the dns(you might be able to use your internet providers dns)to send the email.
The firewall is the real trick you have to get that right with the dns ports 53 tcp and udp
Post fix ports 25 tcp and udp( i don't get spam). 

All I use it for is my webpage so that I can use php mail()function
If you are using gmail it will end up in spam.
If you have questions ask I will try to answer them.

Gishaust

---

### Post by andrew.46 on 2008-01-16
Hi,

 I can see you getting into certificate trouble:

> **Oen386 said:**
> Well I jumped the gun... the link provided is very vague.
Also people report he has information wrong:
Still can't get it to work. Everything looks fine. Yet no success.

You can track down the required certificates and place them manually as is described here:

[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

But it may be easier to install the certificate pack and ssl for Ubuntu as follows:

```
$ sudo apt-get install openssl ca-certificates libssl0.9.8 libssl-dev
```And then you can point towards:

```
/etc/ssl/certs 
```for the Gmail certificates. There is a guide on the Ubuntu Forums that speaks of this:

[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)

OK I will admit: its my guide :-). OK I will also admit to writing the complicated one with all the ssl commands too :-)

      Andrew

---

