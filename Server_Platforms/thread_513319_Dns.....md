---
title: "Dns...."
date: 2007-07-30
forum: Server Platforms
---

### Post by hockey97 on 2007-07-30
Hi I am getting domain names soon well going to buy it.

I want to know how do setup a domain name in bind9 ??

I am able to host 1,000 websites, with domain names and I have 1 server to host it on.

is it possible to make those domains link to my computer to the folder for that certain  domain name's contensts like webpage ??

like for 1,000 domains is 1,000 different webpages, so I could make 1,000 different folder's and assing each folder to those certain 1,000 domain names.

also I want to provide an e-mail adress, do I need a domain name for that??

like for example [email]webmaster@mydomain.com[/email]

how would I set stuff up??

---

### Post by koenn on 2007-07-30
weird question. you're going to buy 1000 domain names to host 1000 websites. You have 1 server, and no idea what you're doing. 
You're best effort at describing the problem is "how do i set stuff up" - you probably don't even realise that this is not something that can be answered in 3 lines. 

Anyway, 
to host domain names on BIND, you need to install bind, configure it so that it behaves the way you want/need it to, and create zone files for the domain names you'll be hosting. 
This should get you started : 
[http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#dns](http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#dns)

I think there's some sort of rule that says you if you're hosting domain names, you need at least 2 DNS servers - for redundancy. 

to offer email adresses, you're going to have to set up MX records in (the zone files of) your DNS server. You'll also need a mail server to handle that mail. You can run it yourself or have it set up by a company. 

Hosting websites is yet another, completely different story. You'll need to set up a web server, eg apache. 
You should also ask yourself wheter that server will be able to handle the load of 1000 websites

Enjoy. 
.

---

### Post by Brazen on 2007-07-30
Dude, just tell him how to make millions overnight.  You have 30 seconds.

---

### Post by koenn on 2007-07-30
> **Brazen said:**
> Dude, just tell him how to make millions overnight.  You have 30 seconds.
What do you mean, that it's not possible, without any knowledg of Linux and TCP/IP networks, not to mention security,   to put in a Live CD, click OK 6 times, and then enjoy  the full power of a superior, Unix-like operating system with amazing networking capabilities,  to  run a a couple of applications such as a public DNS server, web server and mail server ? This is Ubuntu ! Linux for human beings !

:)

---

### Post by murraymca on 2007-07-30
Hiya,

This link will help with using BIND, I found it so far to be the best online resource I've used:  [http://www.zytrax.com/books/dns/](http://www.zytrax.com/books/dns/)

Other links that might help get the basic concepts out of the way:
[http://www.madboa.com/geek/soho-bind/](http://www.madboa.com/geek/soho-bind/) (bind9 for small LAN)
[http://www.tldp.org/HOWTO/DNS-HOWTO-5.html](http://www.tldp.org/HOWTO/DNS-HOWTO-5.html) (DNS how-to:  A simple Domain (covers a bit about mail)

With regards to mail I have limited experience so won't post any links (since I know you can't just follow them step-by-step as i tried).  1000 folders...I'm not up with scripting, but here you will find tutoriasl:  [http://www.tldp.org/guides.html](http://www.tldp.org/guides.html) I'm sure you could make a script that makes 1000 folders for you, unless you want to type 'mkdir' 1000 times.

All the best...

---

### Post by hockey97 on 2007-07-30
> **Brazen said:**
> Dude, just tell him how to make millions overnight.  You have 30 seconds.

wow, I didn't ask to make me millions over night...

what I am asking is that I am going to host 1,000 max domain names and web site's I am asking how would I do this in bind9 having to manage and make each folder for each domain name so when someone types
their domain name it will go to that folder and pick up the main page but that folder would just be for that one domain name and their are 1,000 domain name possible.

I know c++ and python, I know html and php, and I lready have apache, I alread have a mail server ,
just asking how to connect domain names to the websites and e-mail adress'es.

I didn't ask for everyone to do all the work , I didn't ask to make me some multi-million dollor programs.

I don't not aim for a million dollor's, right now.

I am just asking how to connect those domain names to my pages and e-mail service.

basicly the configurations, well like how to make that domain name  when  request comes that it will look for it's main folder.

I already have a DNS server, bind9, .

---

### Post by jtc on 2007-07-30
> **hockey97 said:**
> ...I am asking how would I do this in bind9 having to manage and make each folder for each domain name so when someone types
their domain name it will go to that folder and pick up the main page...

That part has nothing to do with Bind.

[http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/)

---

### Post by brooksbp on 2007-07-30
> **koenn said:**
> What do you mean, that it's not possible, without any knowledg of Linux and TCP/IP networks, not to mention security,   to put in a Live CD, click OK 6 times, and then enjoy  the full power of a superior, Unix-like operating system with amazing networking capabilities,  to  run a a couple of applications such as a public DNS server, web server and mail server ? This is Ubuntu ! Linux for human beings !

:)

ahhhhhhhhhhhhhaahahahahha... i love it..

---

### Post by koenn on 2007-07-31
> **hockey97 said:**
> 
I am just asking how to connect those domain names to my pages and e-mail service.

Ok, in brief :

- you "set up" a domain name (say, uselesspublications.com) by creating a zone file in DNS (bind) that says that your server is authoritive for that domain (uselesspublications.com). 

- to host websites under a domain name, you'll need an Adres record  (in the zone file) that points to your server addres -
say [www.uselesspublications.com](www.uselesspublications.com)  A   123.123.123.123

- to set up mail with a domain name, you make an MX record + an Adres record for your mail server. - something like
MX    10   mail.useless.publications.com
mail.uselesspublications.com A  123.123.123.123

- in your apache config , create a site configuration for [www.uselesspublications.com](www.uselesspublications.com) and a directory (eg /var/www/uselesspub).  Set that directory as Document Root for [www.uselesspublications.com](www.uselesspublications.com). 

- configure your mail server to receive mail destined to and send from (users@) uselesspublications.com.

obviously, mail and webserver's ip address should match does given in DNS.


Detailed instructions : links provided throughout this thread. Use Wikipaedia to get your bearings, and google to find additional info, or come back with detailed, concrete questions.

---

### Post by hockey97 on 2007-08-02
Thanks alot that's what I was asking for,
It cleared on what I need to do.

Thanks for the help.:popcorn::guitar::lolflag:

---

