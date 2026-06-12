---
title: "&quot;Pretend&quot; static ip vs. dyndns web and mail server"
date: 2008-05-25
forum: Server Platforms
---

### Post by volkswagner on 2008-05-25
I have a new install 8.04 server following perfect server on HowtoForge. I have installed ispconfig.  I think I would have preferred webmin.

My goal is to run mail server from home.  I am just testing now for a future setup which will include dyndns.  I was trying to set up without dyndns services to eliminate one part of the debug process.

Is it possible to pretend my ip is static?  It does not change often and this is not a mission critical setup.  I would manage the changes myself.

One problem I have run into is my forwarded hostname.  I have a .com domain from godaddy.  I currently have it forward to my ip address.  This works for website.  Mail may be a different story.  I wanted to use pop3 mail from my server.  I wanted to set up a mail account on my desktop in evolution.  I get errors when trying to connect.  Either no route to host or password fails.  I think the problem is DNS.  Since my domain is forwarded using godaddy's DNS service, the mail client is going to the godaddy ip not my server.  Sound correct?

Can I make this work?  Do I change the DNS at godaddy to my isp provided DNS?  Should I just set up dyndns and forget the pretend static ip?  I discovered this when at the server trying to telnet.  I can telnet local host.  I can telnet my actual isp provided ip address.  When I try to telnet my domain name, telnet hangs.
 
I have checked open ports.  I confirmed ports are open, 25, 80, 110, and are forwarded to my server via router.

I have attached some items which may help.

---

### Post by volkswagner on 2008-05-26
Well I guess you all can kind of forget the above.  I set up DYNdns and configured my router.  I also followed this how to for ddclient.

[http://ubuntuforums.org/showthread.php?t=683270]("http://ubuntuforums.org/showthread.php?t=683270")

I stopped the forwarding from godaddy and entered dyndns's DNS ip's at my godaddy account.

When I try to send mail from my server using web interface, mail sent to my gamil account get bounced right away saying can't receive from dynamic address.  When i try to sen mail to my email provided by my isp, they don't get returned, nor sent to my email.  I do see similar warnings can talk to dynamic address.

So how do I set it up using my isp's mail?  I just want vanity mail.  The purpose is so I can update elysa with my info.  My main goal is SEO.

---

### Post by hyper_ch on 2008-05-27
most mail server will not accept email from a dynamic IP address HOWEVER you could setup your mailserver in such a way, that you server will relay the email through your internet provider.

I've never done that with a server so I don't know where you can look this up, but google should be able to help you. There might even be a howto at howtoforge.

Furthermore I think there's a howto on how to setup the server using a domain registered through godaddy. That might have all the relevant information.

---

### Post by windependence on 2008-05-27
> **hyper_ch said:**
> most mail server will not accept email from a dynamic IP address HOWEVER you could setup your mailserver in such a way, that you server will relay the email through your internet provider.

I've never done that with a server so I don't know where you can look this up, but google should be able to help you. There might even be a howto at howtoforge.

Furthermore I think there's a howto on how to setup the server using a domain registered through godaddy. That might have all the relevant information.


I always wonder what the purpose of doing that is. I mean,if you are going to relay it through the ISP's mail server, you might as well just USE the ISP mail server, no? I can't figure that out.

-Tim

---

### Post by hyper_ch on 2008-05-27
well, using the ISPs mailserver won't allow you to say an email is from a given domain.

However realying through it you can use your own domain.

At least I think there's the difference.

---

### Post by windependence on 2008-05-27
> **hyper_ch said:**
> well, using the ISPs mailserver won't allow you to say an email is from a given domain.

However realying through it you can use your own domain.

At least I think there's the difference.

My ISP allows masking so I guess that's why it seems strange to me. :)

-Tim

---

### Post by hyper_ch on 2008-05-27
well, I never hosted a domain on a dynamic IP so I was never forced to look closer into this matter.

---

### Post by volkswagner on 2008-05-27
A couple questions.  How does the gmail servers know my ip is dynamic?  Are the ip address numbered to identify it as dynamic?

How can a simple php script embedded in a webpage successfully  send mail to gmail on the same server.  This is frustrating.  I will look into masking, and relay.  I notice dyndns has some email solutions, mailhop cost money though.
```

So how does the following succeed by a fully configured mail server fail?  Seems I do not understand soooo much!

<?php
  $email = $_REQUEST['email'] ;
  $message = $_REQUEST['message'] ;

  mail( "yourname@example.com", "Feedback Form Results",
    $message, "From: $email" );
  header( "Location: http://www.example.com/thankyou.html" );
?>

```

---

### Post by cdtech on 2008-05-27
This site will explain sending mail using gmail as your relayhost:

[[COLOR="DarkRed"]postfix with gmail[/COLOR]]("http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html")

Hope this clears some things.

I use this method to text server status messages to my cell.

---

### Post by windependence on 2008-05-27
> **volkswagner said:**
> A couple questions.  How does the gmail servers know my ip is dynamic?  Are the ip address numbered to identify it as dynamic?

How can a simple php script embedded in a webpage successfully  send mail to gmail on the same server.  This is frustrating.  I will look into masking, and relay.  I notice dyndns has some email solutions, mailhop cost money though.
```

So how does the following succeed by a fully configured mail server fail?  Seems I do not understand soooo much!

<?php
  $email = $_REQUEST['email'] ;
  $message = $_REQUEST['message'] ;

  mail( "yourname@example.com", "Feedback Form Results",
    $message, "From: $email" );
  header( "Location: http://www.example.com/thankyou.html" );
?>

```


I could tell just by doing a traceroute on you. I'm sure their servers can detect the hops and they probably have the dynamic hosts IP addresses in their databases. 

Hosting this way is just really a hack. Change ISPs if you can or get a business acct. It's not usually that much more. Many people can't get to your site if it's dynamically hosted because a lot of companies block these connections as they think they are spam or people trying to hack their sites. E-mail is also problematic because it can be rejected if the recipient's e-mail server detects it has been relayed or that it doesn't have a reverse DNS record.

-Tim

---

### Post by volkswagner on 2008-05-27
I am still wondering about the simple .php script.  Why does this work, but postfix does not.  When the script is part of a web page, people can fill in the form and I receive the mail message.  What is the MTA in this scenario?

I have a call into Time Warner.  They don't offer static ip for residential customers.  They are also the only high speed provider in my area.  I will need to upgrade to business class.  Still waiting for a salesperson to call me back with pricing.  The last time I asked about it, the price was tripple ($150 vs. $50).  I will probably be better off with outside hosting or even outside virtual server.  :(  Heck, I could get a dedicated server for $64/mo.

I am looking for advice on the most cost effective way to get SEO.  Do I need to update Alexa.com with my info?  To do this I need vanity mail.  The site in question is my wifes new business.  There is no traffic do to lack of SEO.  The site is currently hosted for free at webng.com.  I was hoping to generate income before investing in paid hosting.  I do not have mail for this domain. So can I create a mail server for this domain and leave it hosted a webng?  This would allow me to receive mail and update Alexa.com.  Or can I set up mail hop at Dyndns to forward the mail so I can activate changes at Alexa.com?

Sorry for the long wind.  I am just really confused.

---

### Post by windependence on 2008-05-27
Uhgggg, Alexa, one of the worst spyware vectors on the planet. Customers hate them and for good reason. Why do you suppose most spyware sofwater removes Alexa? If you want to do this to your customers fine but I wouldn't.

I would suggest google adsense, and link to as many externel sites as you can. Linkshare is also good.

-Tim

---

### Post by hyper_ch on 2008-05-28
you can get a dedicated server for &#8364; 20.-/m (haven't found anything cheaper yet)

---

### Post by MJN on 2008-05-28
> **windependence said:**
> I always wonder what the purpose of doing that is. I mean,if you are going to relay it through the ISP's mail server, you might as well just USE the ISP mail server, no? I can't figure that out.
 
-Tim
 
The relaying only affects outgoing mail, you are still in full control of incoming mail and all the anti-spam measures, accounts, etc.
 
If you are referring to clients using the ISP's mail server instead of yours there are many reasons why you would still want them to connect via you to then relay on to the ISP such as controlling user's outgoing mail access (again including anti-spam), redundancy (i.e. having multiple smarthosts at your disposal hence eliminating an otherwise single point of failure), network security etc.
 
Mathew

---

### Post by windependence on 2008-05-28
> **MJN said:**
> The relaying only affects outgoing mail, you are still in full control of incoming mail and all the anti-spam measures, accounts, etc.
 
If you are referring to clients using the ISP's mail server instead of yours there are many reasons why you would still want them to connect via you to then relay on to the ISP such as controlling user's outgoing mail access (again including anti-spam), redundancy (i.e. having multiple smarthosts at your disposal hence eliminating an otherwise single point of failure), network security etc.
 
Mathew

Doesn't seem compelling enough for me. I use my own smtp server to send outgoing mail. I only had to have a static IP and revers dns set up to do it, so it was rather easy. Also, my ISPs smtp servers have never been down in 5 years so single point of failure doesn't seem valid especially since I am sure they better hardware and redundancy than I do. I'm still not getting the concept I guess. I use my own SMTP server because I want that control and don't want to have to mask my e-mail, other than that, I would just use theirs for outgoing mail.

-Tim

---

### Post by MJN on 2008-05-28
You're missing the point that one tends to only look to relay outgoing mail via their ISP if they have no choice but to have a dynamically-allocated IP address (as in the OP's case). If you have a static address then there is no advantage to relaying, indeed quite the opposite.
 
Mathew

---

### Post by windependence on 2008-05-28
Must have missed the dynamic IP thing somewhere, sorry. I am thick tonight.

-Tim

---

### Post by MJN on 2008-05-28
No worries! :)
 
These oversights are always good the for the archives anyway, as they help highlight to others the subtleties of what's being discussed!
 
Mathew

---

### Post by volkswagner on 2008-05-28
Tim, Thanks.  I had no idea about Alexa being spyware.  Does the same hold   true for about.com?  I think it may as I recall years ago my home page being auto-restet to about.com due to a virus.  I am still learning.  I have just signed up for google AdWords.



> **hyper_ch said:**
> you can get a dedicated server for € 20.-/m (haven't found anything cheaper yet)

hyper, can you tell me the us dollar value, and where you are referring to?

I am still hoping for an explanation on the .php question above.

I am also not sure of the proper syntax to set up my mail account in evolution.  I get denied using my user name and password. I have tried the following settings.

       pop.volkswagner.com, pop3.volkswagner.com, pop-server.volkswagner.com...  smtp.volkswagner.com, smtp-server.volkswagner.com

I did make an error on my security certificate for TLS.  I am not sure how to fix it or if I should just start with a new one.  I entered my town name in place of state on the second part of the certificate.

When I go to [https://mysite.com](https://mysite.com) I get a pop up:

"Website Certified by an unknown authority"
"Unable to verify the identity of wwwdotvolkswagnerdotcom as a trusted site."

I have always temporarily enabled as I am not sure what to do.  Again I did make an error.  What shall I do to fix it?

---

### Post by hyper_ch on 2008-05-28
> **volkswagner said:**
> hyper, can you tell me the us dollar value, and where you are referring to?

well, the dollar value changes (on a daily base) but € 20.- would be now USD 31.50. For currency conversation I use [http://www.oanda.com](http://www.oanda.com)

The host I am speaking of is OVH [http://www.ovh.com/fr/particulier/produits/kimsufi08.xml](http://www.ovh.com/fr/particulier/produits/kimsufi08.xml) (unfortunately in the UK they charge in £ than € so that would make it about USD 40.-/m).

The boxes aren't high load servers but they feature:

Intel Celeron 220 1.2 GHz L2: 512Ko, FSB: 533 MHz
or
Intel Celeron D 2.00 GHzL2: 256Ko, FSB: 400 MHz

32 / 64 bits
1 GB ram 
250 GB disk
100 mbit connection
unlimited traffic (I did seed Edgy for a week at full speed on there withouth restriction through rtorrent)
1 dedicated IP
250 GB ftp backup space (can be wonderfully used with the ftplicity script to create incremental ENCRYPTED backups)
remote reinstall of the server
24/7 monitoring
bandwidth monitoring
remote reboot
netboot
...
...
...

and you can choose among various linux distros, windows or freebsd as OS.

If you want a dedicated server on a reliable net it's a good offer I think - except if you can get a dedicated IP address from your cable provider at the same or cheaper rate.

---

### Post by volkswagner on 2008-05-29
I guess I shall start a new thread for the php question.

I finally was able to speak to a live person at Time Warner.  Sad to say I would need to pay $150/mo. to get a static ip.  :mad:

I will be looking into outside hosting or renting a server/virtual server.  I certainly can't justify the extra $100/month.

---

