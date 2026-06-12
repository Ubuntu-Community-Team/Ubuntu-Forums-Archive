---
title: "postfix help."
date: 2007-12-21
forum: Server Platforms
---

### Post by hockey97 on 2007-12-21
I have postfix installed.

what can I do to make a secure e-mailing system.

I want to make  my own php script to make a webmail for my website.

I tested my postfix and looks like it  works but when I send mail to well know e-mail servers I it dosen't get delivered.

what test's could I run to see if postfix is working.

and would I need to make a certificate in order to have my users able to send mail to well know e-mail services?

I right now just want to get a working e-mail system up.

---

### Post by HermanAB on 2007-12-21
Hmm, I have run Postfix for 5 years for my own mail and installed quite a few systems for other companies.  However, nowadays I don't bother with Postfix anymore.  It is just waaaay to much work to set it up.

Rather see this:
[http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)

and install using the Easy Install script, which takes about 20 minutes:
[http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)

Cheers,

Herman

---

### Post by hockey97 on 2007-12-21
well I have postfix already installed and use webmin to easly config postfix.

I mainly want to have a e-mail system where I have control over must be secure and have a spam filter.

I mainly want to create my own php script to grab the user's mailbox. 
so I can mainly have a webmail page for my users.

I mainly  want a mail server to be secure and spam free well at least try to .and  want to be able using php to grab mail for users and also can send mail using php with my mail server.

I mainly heard that postfix is a  industry standard.  I want the mail server to be able to send mail to other well known e-mail services like hotmail ect.

---

### Post by HermanAB on 2007-12-21
Yup, a combination of postfix, apache, dovecot, roundcube, spam assassin, clamav, spamhaus, spamcop, dcc and razor can do that.  It will take you at least two weeks of full time effort to get it to work though.

Or, you can use Citadel and have it all working in under an hour.

The best howto guides for postfix, are on the postfix.org web site.

Cheers,

Herman

---

### Post by hockey97 on 2007-12-21
is it possible to map or connect posftx in some way to use mysql?

---

### Post by HermanAB on 2007-12-21
Yes, postfix can use pretty much any SQL database for virtual users:
[http://wispdirect.com/docs/sasl-howto.html](http://wispdirect.com/docs/sasl-howto.html)

---

### Post by hockey97 on 2007-12-22
What is postfix2 ?? 

 I have postfix and have the postfix-mysql  would I still have to compile the file?
I read somewhere on the internet that if I downloaded postfix-mysql then I am all set I should be able to just make the database and the tables for it and it should be all set.

is that right?

The link you gave look's to be outdated.  I just heard that now you just need to install posfix-mysql and then config some files to point to mysql and then create the database and tables for m y e-mail server then from their I can program my own php page to mainly grab the user's mail box and also send mail.

I found here a  page explaining to connect mysql with postfix.   [http://www.postfix.org/MYSQL_README.html](http://www.postfix.org/MYSQL_README.html)   
just woundering if I should follow that instead?

---

### Post by HermanAB on 2007-12-22
Hmm, that page you found on postfix-mysql certainly looks good.

Cheers,

Herman

---

### Post by hockey97 on 2007-12-22
you will need to add -DHAS_MYSQL and -I for the directory containing the mysql headers, and the mysqlclient library (and libm) to AUXLIBS.

what are the mysql headers?

---

### Post by hockey97 on 2007-12-23
Would I need to generate a certificate to have well known e-mail services to accept my out-going mail. 

according to that website I asked about, it say's that if I installed postfix-mysql I cna skip the building part.

then the next part is nothign but making one file and  config the main.cf file in postfix , and just make 3 databases. 

I don't mainly understand the whole setup, will post fix just grab from the database only the mail server mx domain.
so that it can listen for requests on those mx domains.  

I don't fully understand the whole  mail setup.  I mainly want postfix to  securely drop e-mails into a database with the username also include. 
I don't mainly know  how I can get my users to have a  address like [email]myuser@mydomain.com[/email] .

How can I test the mail server and how could I grab my current user info?

---

### Post by hockey97 on 2007-12-25
Hi got a question for you guys.  in my domain provider area I created  one mx record and one A record for my mail server.  I done a test and I can connect to my mail server but when using those domain names to get to my mail server it connects to my webserver.

like it would connect and then I get a error saying time out  wrong data.

for mail servers do I need an A record??  I have an A record and a mx recrod pointing to my ip address to my server's. 

I mainly can't send e-mail or anything I would get a error.

any ideas what might be the problem? I also followed the config thing to have postfix use mysql but it dosen't work.

---

### Post by rsw686 on 2007-12-25
You should look at Postfix Admin. It provides a nice web gui to edit domain mailboxes/aliases for postfix with mysql. It tied in nicely with postfix, dovecot, and horde/imp.

---

### Post by HermanAB on 2007-12-26
You need three: MX, A and PTR records

If any one is missing, your mail will be bounced.

---

### Post by hockey97 on 2007-12-26
PTR??  I have a revers address record. on my server but  not at my domain name providor. They don't have an option to do such a thing.

I heard I have to call my ISP to ask them to allow such a thing.

---

### Post by rsw686 on 2007-12-26
> **hockey97 said:**
> PTR??  I have a revers address record. on my server but  not at my domain name providor. They don't have an option to do such a thing.

I heard I have to call my ISP to ask them to allow such a thing.

Yep there is no option at the domain provider since a PTR is a reverse lookup based on your IP. It's not really a big deal though. Just set your mail server's helo name to your IP's reverse lookup name. Your ISP probably also allows you to use their smart hose to relay mail. I ended up using that for Hotmail and Yahoo addresses as my messages would end up in the junk folder otherwise. You just add the correct entries to the transport file.

---

### Post by hockey97 on 2007-12-26
well postfix now interacts with mysql with no problems. Now just domain name problems I have.

for the virtual domains I have  name: demonicproductions.com  maps to mail.demonicproductions.com

is that right that is the same with  how I done the transport and also the mx record  in my domain providor.

went I test the mail server with tools found on the internet. I get this   ERROR: Timeout while waiting to read data from host mail.demonicproductions.com.:25, Unknown error 3219790784
what would that mean?

---

### Post by MJN on 2007-12-27
I haven't been following this thread but having read your latest message I can confirm your DNS is not quite configured correctly. You need to enter MX records for your domain, demonicproductions.com, but the target for these records should be a *name* and not an *IP address*. An A record is then used for this name to translate it into an IP address.

Hence, you need:

demonicproductions.com IN MX 10 mail.demonicproductions.com
mail.demonicproductions.com IN A 67.149.150.40

As things currently stand you have a mail.demonicproductions.com MX record pointing to an IP address (this is not allowed) and you don't have an MX record for demonicproductions.com (it ideally needs one).

All that said, attempted connections to 67.149.150.40 on port 25 do indeed time out hence, assuming this is your address, you need to ensure any port forwarding on your router(s) is correctly configured, any firewall(s) in place are passing the port, and that your ISP does not block incoming port 25 (it's normally outgoing 25 they block but anything's possible).

Mathew

---

### Post by hockey97 on 2007-12-27
HI I have the mx record for my domain name, on both my server and my domain providor. 

 I now got postfix to interface with mysql. So postfix now grabs the data from mysql.

 their are 3 tables one for virtuial domains , another for the domain for the mail server. and the last is the users and their mailboxes. 

these are what postfix grabs.
ever since I have that working I got that error that you said.

my router is config right otherwise you would not be able to see my mywebsite.

I don't know if my ISP would block 25.  if I have to call them to unblcok it they would probally charge me.

what is  transport maps??  I have one but don't know the purpose of it? Is it to deliver mail??

---

### Post by hockey97 on 2007-12-28
I need to know  basicly how e-mail comes in and goes out  in postfix. 

like  if I send e-mail to someone in the web  what domain names and what dns records it would use to get their, and same with incoming mail.  I  messed up the config even more. 

postfix now can use mysql but I maid  3 tables one for alises one for domain and one for users. 

however I don't know what postfix needs from those tables, like example for the domain table do I need to put the mail domain   which is  mail.demonicproductions.com  or a normal domain the one with www.  ??  
and same for alises. I am not ever sure about users. would I need to put in users like [email]user@maildomain.com[/email]?

---

### Post by MJN on 2007-12-28
> **hockey97 said:**
> HI I have the mx record for my domain name, on both my server and my domain providor.
 
You have now, but they're still wrong:
 
```
$ dig demonicproductions.com mx
; <<>> DiG 9.3.2 <<>> demonicproductions.com mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10494
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 2
;; QUESTION SECTION:
;demonicproductions.com.                IN      MX
;; ANSWER SECTION:
demonicproductions.com. 604800  IN      MX      1 mail.demonicproductions.com.
;; ADDITIONAL SECTION:
mail.demonicproductions.com. 3600 IN    A       192.168.1.101
mail.demonicproductions.com. 3600 IN    A       67.149.150.40
;; Query time: 147 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Fri Dec 28 18:00:15 2007
;; MSG SIZE  rcvd: 93
```
 
You've got two A records for mail.demonicproductions.com but only one of them (67.149.150.40) is valid for the outside world. The consquence of the current configuration is that correct resolution of the MX record will only occur 50% of the time.
 
However, even when the DNS is fixed you're still not good to go as connections to port 25 are failing:
 
```
$ telnet 67.149.150.40 25
Trying 67.149.150.40...
telnet: Unable to connect to remote host: Connection refused
```
 
That's a different situation to how it was earlier (connections were timing out, not being actively refused).
 
> my router is config right otherwise you would not be able to see my mywebsite.
 
On the contrary, just because we can see your website doesn't mean we can connect to your mail server. They are entirely seperate.
 
Besides which, we can't see your website anyway - your DNS is broken in the same way as above, and connections to port 80 are not working.
 
> I don't know if my ISP would block 25. if I have to call them to unblcok it they would probally charge me.
 
Fix your website first as then you can at least be confident you've got networking connectivity, then you can move on to ascertaining whether or not port 25 access is being allowed.
 
Mathew

---

### Post by hockey97 on 2007-12-28
ya I have 2 A records one for people outside my network and one for people inside my network. and my website does work just don't have a layout yet.

I know mail server is different than a website or web server. but what I mean was that my website was config right I mean like on my router it's port forwared right.  if I was not able to port forward my website would gave me problems. The only problem I have now is that the ip address internal alway's changes when I shut down my computer or reboot the computer.

I have the mx record  as  name:demonicproductions.com  goesto: mail.demonicproductions.com

then 2 a records mail.demonicproductions.com ip:externale . 
then the next points to internal ip.  so people outside my network or inside my network can just type in the domain name and go into my website.

If I just made a external ip address record then only people outside my network can get to my website. and people that are in my network would be directed to my router.

I mainly just want to know how to setup posfix just so that I can e-mail people and I can get e-mails.  after than then I plan to use secure stuff like anti-spam.

my main forcus is just getting a working mail server up and running.

---

### Post by rsw686 on 2007-12-28
> **hockey97 said:**
> postfix now can use mysql but I maid  3 tables one for alises one for domain and one for users. 

however I don't know what postfix needs from those tables, like example for the domain table do I need to put the mail domain   which is  mail.demonicproductions.com  or a normal domain the one with www.  ??  
and same for alises. I am not ever sure about users. would I need to put in users like [email]user@maildomain.com[/email]?

Like I stated earlier check out Postfix Admin. Even if you don't want to use the web interface it has a sql file with the needed tables for postfix.

You'll also need to create the virtual mapping files which are covered in all postfix virtual mail hosting tutorials.

---

### Post by MJN on 2007-12-29
> **hockey97 said:**
> ya I have 2 A records one for people outside my network and one for people inside my network.

Your current configuration will not work as you intend. Period. If you require different resolutions for different clients (internal/external) then you need to look at using split DNS or BIND views. Putting two A records like you have now will not work - the lookup will result in an indeterminate result and hence on average 50% of external lookups will fail.

> and my website does work just don't have a layout yet.

What I meant was your web server was not responding when I attempted to connect. It is now, but only half the time (when I happen to get your 67.149.150.40 address as opposed to 192.168.1.101 when resolving [www.demonicproductions.com](www.demonicproductions.com))

> I know mail server is different than a website or web server. but what I mean was that my website was config right I mean like on my router it's port forwared right.  if I was not able to port forward my website would gave me problems.

Yes, but just because you are successfully running a website (which you're not given the broken DNS) doesn't mean your mail server will work - you still have to forward port 25 assuming your ISP doesn't block it.

> The only problem I have now is that the ip address internal alway's changes when I shut down my computer or reboot the computer.

Statically address your server or configure your DHCP service to always issue the same address to that machine.

> I have the mx record  as  name:demonicproductions.com  goesto: mail.demonicproductions.com

then 2 a records mail.demonicproductions.com ip:externale . 
then the next points to internal ip.  so people outside my network or inside my network can just type in the domain name and go into my website.

No, when people outside your network look the name up they will get your internal address half the time.

> If I just made a external ip address record then only people outside my network can get to my website. and people that are in my network would be directed to my router.

Not necessarily - many (most?) routers support NAT loopback hence your internal clients will be quite able to connect to your web server with the same name/address as external. Tell us what router you have and we should be able to find out if this applies to you. If, from experimenting, you find internal clients always get the router config page then try changing the port it uses away from 80.

> I mainly just want to know how to setup posfix just so that I can e-mail people and I can get e-mails.  after than then I plan to use secure stuff like anti-spam.

my main forcus is just getting a working mail server up and running.

That's fine, but without a correctly configured DNS you've got no chance.

Mathew

---

### Post by rsw686 on 2007-12-29
> **MJN said:**
> Not necessarily - many (most?) routers support NAT loopback hence your internal clients will be quite able to connect to your web server with the same name/address as external. Tell us what router you have and we should be able to find out if this applies to you. If, from experimenting, you find internal clients always get the router config page then try changing the port it uses away from 80.

What you are talking about is NAT reflection, which is resource intensive for the router. The request has to go to the router and back to the internal server using double the bandwidth. The correct way to do this is with an external and internal view on the DNS server.

---

### Post by MJN on 2007-12-29
<duplicate post deleted>

---

### Post by MJN on 2007-12-29
NAT reflection == NAT loopback. Two terms for the same concept. If your router cannot handle the load then you probably need a new router.

I've already mentioned the use of split DNS, however I am getting the impression the OP wants to achieve his goal as simply as possible.

Mathew

---

### Post by rsw686 on 2007-12-29
> **MJN said:**
> NAT reflection == NAT loopback. Two terms for the same concept. If your router cannot handle the load then you probably need a new router.

I've already mentioned the use of split DNS, however I am getting the impression the OP wants to achieve his goal as simply as possible.

Mathew

Split DNS is just as easy to configure in BIND as regular DNS. You just make a copy of the zone file for the internal network. Then add a view tag in named.conf.

Looping network traffic through the router and back when it doesn't need to is pointless and a waste of resources. Sure the router can handle it, but why??

---

### Post by hockey97 on 2007-12-29
well I have linksystem and  i can't  assign or make the router assign to a specific ip address.   i  tested my  website with those 2 A records and I have a couple of friends on my website a couple of times. Then never had problems right now I currently when I am not using the computer that has the server I turn it off.
so that's why you had problems connecting to my website.   

I currently reinstalled postfix.  I am now currently trying to follow this tutorial. 
[http://www.howtoforge.com/linux_postfix_virtual_hosting](http://www.howtoforge.com/linux_postfix_virtual_hosting)

how ever the file that gives the mail info meaning the user's e-mail addres and the maildir I am using mysql.  I don't mainly know now if it's working. 

when I test the mail server I get connected to the server but I get a timeout and say's  reading data unknown error.

---

### Post by MJN on 2007-12-30
> **rsw686 said:**
> Split DNS is just as easy to configure in BIND as regular DNS. You just make a copy of the zone file for the internal network. Then add a view tag in named.conf.

Sure, it's doable but as the OP isn't running their own DNS I consider it easier for internal and external clients to be using the same address.

[quote=hockey97]well I have linksystem and i can't assign or make the router assign to a specific ip address. i tested my website with those 2 A records and I have a couple of friends on my website a couple of times. Then never had problems right now I currently when I am not using the computer that has the server I turn it off.
so that's why you had problems connecting to my website.[/quote]

Hockey97, your DNS is broken. I'm not saying that's the reason for your current problem/error but I am saying it will **not** work properly until you fix the DNS.

```
$ dig demonicproductions.com mx

; <<>> DiG 9.3.2 <<>> demonicproductions.com mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10104
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 2

;; QUESTION SECTION:
;demonicproductions.com.                IN      MX

;; ANSWER SECTION:
demonicproductions.com. 604800  IN      MX      1 mail.demonicproductions.com.

;; ADDITIONAL SECTION:
mail.demonicproductions.com. 3600 IN    A       192.168.1.101
mail.demonicproductions.com. 3600 IN    A       67.149.150.40

;; Query time: 162 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Sun Dec 30 12:23:38 2007
;; MSG SIZE  rcvd: 93

$ dig www.demonicproductions.com a

; <<>> DiG 9.3.2 <<>> www.demonicproductions.com a
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 23541
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.demonicproductions.com.    IN      A

;; ANSWER SECTION:
www.demonicproductions.com. 3600 IN     A       192.168.1.101
www.demonicproductions.com. 3600 IN     A       67.149.150.40

;; Query time: 179 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Sun Dec 30 12:25:24 2007
;; MSG SIZE  rcvd: 76
```At the very least you need to fix your DNS. Don't believe me? Try putting 'demonicproductions.com' into [www.dnsreport.com]("http://www.dnsreport.com") and lookout for the MX record failure warning(s).

I don't know what your mail server problem is as I cannot connect using the IP address (hence bypassing the DNS problems) but without logs etc any diagnosis would be pure guesswork.

Mathew

---

### Post by HermanAB on 2007-12-30
Yup. The 192.168.x.y addresses are not public routable.  Don't put them in a public DNS.

Cheers,

Herman

---

### Post by hockey97 on 2007-12-30
HI I ran a test on here:  [http://www.dnscolos.com/dnsreport.php](http://www.dnscolos.com/dnsreport.php)  
they only show that mx fails by the connection and greeting. that's it. 

it say's I need to have an A record point to my mx record what does that mean?

I right now have an A record  with host mail.demonicproductions.com pointing to my external ip address. 

 I deleted all the internal ip address A records .  It didn't really do anything just now my internal computers can't get to my website. and I do have NAT enabled on my router. but when I attempt on my computer to connect to my website it takes me to the router I  tried switching the port form 80 to 88 and what I experienced that it lost connection to our computers. so I had to unplug my router for a few min and plug it back in pressing the reset button got me back to my defaults.

I then had to config my router back to where it was.

I read around and found websites that people said that the router has to be on port 80 if you config to another port it requires some config in the comptuter in the network setings to point to that port.

but that's what I done so far.  

for the MX recrod I have the host  as  demonicproductions.com  and the goes to is mail.demonicproductions.com 

then an A record where the host is mail.demonicproductions.com and the ip address is my external one.

you guy's told me to delete my internal records that was published so I did .
right now you should't see 2 same A records with different ip address only one A record that has my external ip pointing too.

---

### Post by rsw686 on 2007-12-30
Your out of luck with that router if it can't run on another port besides port 80. Does it support NAT reflection? If not you either need a new router or you need to setup an internal DNS server.

---

### Post by hockey97 on 2007-12-30
I have a dns server up on my computer bind9. and no my router dosen't support that it supports dynamic routing. and NAT.

I ran a dns report. I got this for the mx record. the mx record is the only thing that faild.   I got 2 fails from it.

here is what the report spit out : Connect to mailserver mail.demonicproductions.com   FAILED (could be greylisting)
   ,  The server should have an A record which points to the mailserver for the hostname
which is presented in the greeting

mail.demonicproductions.com

how would you create a certificate?? and do I need a certificate to allow others to send mail to my mail server?

and also can you explain what's wrong with my dns config??? if it was becuse  I had 2 same A records but both had different ip address one internal and one external and  you say that it's a 50%  chance to get either one, so it will work for one person 50% of the time. I deleted the A record that contained my internal ip address.

so other than that is my dns config still messed up?

and tell me how you think I could fix the config.

---

### Post by hockey97 on 2007-12-30
read the post adove I made.  also for postfix all I get from a website a tool the debugs a dns I  failed on the connection to my mail server and also the mailserver greeting.

the tool spit out saying they think my mail server may be greylisted.

how to fix that???

---

### Post by hockey97 on 2007-12-31
now my mx records is not working at all. now when I do a dns report on my domain I  get  a mx records 0  just yesterday their was 1 detected and everything was good except the connection to the mail server and the greeting. Those were th only problems that's it until now.

now I have the fail looking for the mx record dectects nothing. 

and I didn't change anything but just deleting my internal A records yesterday that was it. how does it go from almost workiing to not working at all.

Should I post my postfix config file?? the main.cf file?

I  did an nslookup  using the terminal and it shows that  demonicproductions.com   has a correct mx record.    nslookup -type=mx demonicproductions.com
So why when I use some websites tool to test my dns I get no mx record found??

now it works just now got to work on the connection. I now am back to where I was yesterday.

update:  I  saw some post onlin today that said that I need to get an SSL certificate in order to no get greylisted.

I also post a message on that fourm and they told me that that's all I need to do my dns confi is right . I am right now just my mail server is getting rejected becsue spam filters think anything sent from my mail server would be spam.

so I need the certificates to avoid this. 

Do you guy's think so??

---

### Post by rsw686 on 2007-12-31
> **hockey97 said:**
> now my mx records is not working at all. now when I do a dns report on my domain I  get  a mx records 0  just yesterday their was 1 detected and everything was good except the connection to the mail server and the greeting. Those were th only problems that's it until now.

now I have the fail looking for the mx record dectects nothing. 

and I didn't change anything but just deleting my internal A records yesterday that was it. how does it go from almost workiing to not working at all.

Should I post my postfix config file?? the main.cf file?

I  did an nslookup  using the terminal and it shows that  demonicproductions.com   has a correct mx record.    nslookup -type=mx demonicproductions.com
So why when I use some websites tool to test my dns I get no mx record found??

now it works just now got to work on the connection. I now am back to where I was yesterday.

update:  I  saw some post onlin today that said that I need to get an SSL certificate in order to no get greylisted.

I also post a message on that fourm and they told me that that's all I need to do my dns confi is right . I am right now just my mail server is getting rejected becsue spam filters think anything sent from my mail server would be spam.

so I need the certificates to avoid this. 

Do you guy's think so??

Don't even worry about the SSL certificate. You need to get it working first, then you can add that. Plus if your ISP has a smart host you can just forward the mail through it. I do this for yahoo and hotmail mail to get through their junk filters.

---

### Post by hockey97 on 2007-12-31
I think my ISP has it but not fully sure they don't say .   

but is my dns ok??? like no problems with the dns?

becuse when I do a smtp test I get a timeout error.

I  then found fourms where people said to fix it you have to play around with the timeout value of your mail server so I change it a couple of times and didn't do anything.

---

### Post by MJN on 2007-12-31
Try connecting to your server using the IP address, then you can completely ignore DNS for the time being.

```
$ telnet 67.149.150.40 25
Trying 67.149.150.40...
Connected to 67.149.150.40.
Escape character is '^]'.
```The above shows that a TCP connection is made, but nothing more.

What does your log file (/etc/log/mail.log) say when a connection is made via telnet? Note that given your router doesn't support NAT loopback that you'll need to use it's internal/private address if testing internally.

Incidentally, your DNS is now fine but as mentioned above we can leave it out of the way for now.

Mathew

---

### Post by hockey97 on 2007-12-31
I tried the telnet with my external ip addres I got connection refused.

it's the same what you done. 

but then tried my local ip address and it worked.

here is the log just a few lines to the latest one.
```
Dec 31 14:50:00 DemonicProductions postfix/master[10942]: warning: process /usr/lib/postfix/smtpd pid 12060 exit status 1
Dec 31 14:50:00 DemonicProductions postfix/master[10942]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec 31 14:51:00 DemonicProductions postfix/smtpd[12069]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Dec 31 14:51:00 DemonicProductions postfix/smtpd[12069]: fatal: open database /etc/postfix/valias.txt.db: No such file or directory
Dec 31 14:51:01 DemonicProductions postfix/master[10942]: warning: process /usr/lib/postfix/smtpd pid 12069 exit status 1
Dec 31 14:51:01 DemonicProductions postfix/master[10942]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec 31 14:52:01 DemonicProductions postfix/smtpd[12080]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Dec 31 14:52:01 DemonicProductions postfix/smtpd[12080]: fatal: open database /etc/postfix/valias.txt.db: No such file or directory
Dec 31 14:52:02 DemonicProductions postfix/master[10942]: warning: process /usr/lib/postfix/smtpd pid 12080 exit status 1
Dec 31 14:52:02 DemonicProductions postfix/master[10942]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
```

---

### Post by hockey97 on 2007-12-31
here is more of the log. ```
Dec 31 15:02:13 DemonicProductions postfix/master[10942]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec 31 15:02:19 DemonicProductions postfix/postfix-script[12373]: warning: not owned by root: /etc/postfix/main.cf~
Dec 31 15:02:19 DemonicProductions postfix/postfix-script[12374]: warning: not owned by root: /etc/postfix/valias.txt
Dec 31 15:02:19 DemonicProductions postfix/postfix-script[12375]: warning: not owned by root: /etc/postfix/vhost.txt
Dec 31 15:02:19 DemonicProductions postfix/postfix-script[12376]: warning: not owned by root: /etc/postfix/vmaps.cf
Dec 31 15:02:19 DemonicProductions postfix/postfix-script[12377]: warning: not owned by root: /etc/postfix/vmaps.cf~
Dec 31 15:02:23 DemonicProductions postfix/postfix-script[12497]: warning: not owned by root: /etc/postfix/main.cf~
Dec 31 15:02:23 DemonicProductions postfix/postfix-script[12498]: warning: not owned by root: /etc/postfix/valias.txt
Dec 31 15:02:24 DemonicProductions postfix/postfix-script[12499]: warning: not owned by root: /etc/postfix/vhost.txt
Dec 31 15:02:24 DemonicProductions postfix/postfix-script[12500]: warning: not owned by root: /etc/postfix/vmaps.cf
Dec 31 15:02:24 DemonicProductions postfix/postfix-script[12501]: warning: not owned by root: /etc/postfix/vmaps.cf~
Dec 31 15:02:25 DemonicProductions postfix/postfix-script[12578]: warning: not owned by root: /etc/postfix/main.cf~
Dec 31 15:02:25 DemonicProductions postfix/postfix-script[12579]: warning: not owned by root: /etc/postfix/valias.txt
Dec 31 15:02:25 DemonicProductions postfix/postfix-script[12580]: warning: not owned by root: /etc/postfix/vhost.txt
Dec 31 15:02:25 DemonicProductions postfix/postfix-script[12581]: warning: not owned by root: /etc/postfix/vmaps.cf
Dec 31 15:02:25 DemonicProductions postfix/postfix-script[12582]: warning: not owned by root: /etc/postfix/vmaps.cf~
Dec 31 15:02:25 DemonicProductions postfix/postfix-script[12625]: refreshing the Postfix mail system
Dec 31 15:02:25 DemonicProductions postfix/master[10942]: reload configuration /etc/postfix
Dec 31 15:02:28 DemonicProductions postfix/postfix-script[12668]: warning: not owned by root: /etc/postfix/main.cf~
Dec 31 15:02:28 DemonicProductions postfix/postfix-script[12669]: warning: not owned by root: /etc/postfix/valias.txt
Dec 31 15:02:28 DemonicProductions postfix/postfix-script[12670]: warning: not owned by root: /etc/postfix/vhost.txt
Dec 31 15:02:28 DemonicProductions postfix/postfix-script[12671]: warning: not owned by root: /etc/postfix/vmaps.cf
Dec 31 15:02:28 DemonicProductions postfix/postfix-script[12672]: warning: not owned by root: /etc/postfix/vmaps.cf~
Dec 31 15:03:13 DemonicProductions postfix/smtpd[12728]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Dec 31 15:03:13 DemonicProductions postfix/smtpd[12728]: fatal: open database /etc/postfix/valias.txt.db: No such file or directory
Dec 31 15:03:14 DemonicProductions postfix/master[10942]: warning: process /usr/lib/postfix/smtpd pid 12728 exit status 1
Dec 31 15:03:14 DemonicProductions postfix/master[10942]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec 31 15:04:14 DemonicProductions postfix/smtpd[12732]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Dec 31 15:04:14 DemonicProductions postfix/smtpd[12732]: fatal: open database /etc/postfix/valias.txt.db: No such file or directory
Dec 31 15:04:15 DemonicProductions postfix/master[10942]: warning: process /usr/lib/postfix/smtpd pid 12732 exit status 1
Dec 31 15:04:15 DemonicProductions postfix/master[10942]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec 31 15:04:19 DemonicProductions postfix/postfix-script[12778]: warning: not owned by root: /etc/postfix/main.cf~
Dec 31 15:04:19 DemonicProductions postfix/postfix-script[12779]: warning: not owned by root: /etc/postfix/valias.txt
Dec 31 15:04:19 DemonicProductions postfix/postfix-script[12780]: warning: not owned by root: /etc/postfix/vhost.txt
Dec 31 15:04:19 DemonicProductions postfix/postfix-script[12781]: warning: not owned by root: /etc/postfix/vmaps.cf
Dec 31 15:04:19 DemonicProductions postfix/postfix-script[12782]: warning: not owned by root: /etc/postfix/vmaps.cf~
Dec 31 15:04:57 DemonicProductions dovecot: ssl-build-param: SSL parameters regeneration completed
Dec 31 15:05:15 DemonicProductions postfix/smtpd[12852]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Dec 31 15:05:15 DemonicProductions postfix/smtpd[12852]: fatal: open database /etc/postfix/valias.txt.db: No such file or directory
Dec 31 15:05:16 DemonicProductions postfix/master[10942]: warning: process /usr/lib/postfix/smtpd pid 12852 exit status 1
Dec 31 15:05:16 DemonicProductions postfix/master[10942]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec 31 15:06:16 DemonicProductions postfix/smtpd[12860]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Dec 31 15:06:16 DemonicProductions postfix/smtpd[12860]: fatal: open database /etc/postfix/valias.txt.db: Invalid argument
``` 

look's like postfix is having trouble finding or reading the files.

---

### Post by MJN on 2007-12-31
> **hockey97 said:**
> I tried the telnet with my external ip addres I got connection refused.

it's the same what you done. 

but then tried my local ip address and it worked.

What do you mean 'it worked'? Do you mean you just connected? Or that you could converse with the mail server?

> Dec 31 14:51:00 DemonicProductions postfix/smtpd[12069]: fatal: open database /etc/postfix/valias.txt.db: No such file or directoryPresumably you have got a textfile of the name /etc/postfix/valias.txt (no .db extension)? If so, create the lookup table for Postfix to use with **sudo postmap /etc/postfix/valias.txt** then restart Postfix with **sudo /etc/init.d/postfix restart**.

What do the logs say now?

Please try and be more clear with your descriptions with what's happening - this combined with your defensive stance regarding your configuration is making it a rather protracted thread at post #41 and only just getting to the point of heading in the right direction to sort you out.

Mathew

---

### Post by hockey97 on 2007-12-31
what I meant about worked out was that I got connected with only using my internal ip .

I am not being defensive about my config. I just don't know how to go about it I asked on other fourms and look on google for other sources of help during the lag of time meaning when I post on this fourm I don't get a quick response and I don't expect quick responses since it'a  board fourm so when I wait for a reply I am using that time look at other board fourm through google. I get confused when their are 2 people that  each are on different fourms and are giving advice about setup of postfix  and one say's one thing the other person say's the total oppisite.
I feel sorry if I gave an impression of defending my config.  I was just saying about what other people on the internet said and wasn't sure what to do to take.
I thank you very much on your advice.

ok it look's somewhat ok but here is what I get in the mail log

```
 31 17:40:19 DemonicProductions postfix/smtpd[14100]: lost connection after CONNECT from unknown[64.85.73.124]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14100]: disconnect from unknown[64.85.73.124]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14102]: connect from 77-103-161-36.cable.ubr05.chap.blueyonder.co.uk[77.103.161.36]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14104]: connect from 77-103-161-36.cable.ubr05.chap.blueyonder.co.uk[77.103.161.36]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14105]: connect from 77-103-161-36.cable.ubr05.chap.blueyonder.co.uk[77.103.161.36]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14090]: lost connection after CONNECT from unknown[64.85.73.124]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14090]: disconnect from unknown[64.85.73.124]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14099]: lost connection after CONNECT from unknown[64.85.73.124]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14099]: disconnect from unknown[64.85.73.124]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14101]: lost connection after CONNECT from unknown[64.85.73.124]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14101]: disconnect from unknown[64.85.73.124]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14097]: lost connection after CONNECT from srv195086.webreus.nl[87.119.195.86]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14097]: disconnect from srv195086.webreus.nl[87.119.195.86]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14102]: disconnect from 77-103-161-36.cable.ubr05.chap.blueyonder.co.uk[77.103.161.36]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14108]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14100]: connect from srv195086.webreus.nl[87.119.195.86]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14107]: lost connection after CONNECT from www.demonicproductions.com[192.168.1.101]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14107]: disconnect from www.demonicproductions.com[192.168.1.101]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14090]: connect from srv195086.webreus.nl[87.119.195.86]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14090]: lost connection after CONNECT from srv195086.webreus.nl[87.119.195.86]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14090]: disconnect from srv195086.webreus.nl[87.119.195.86]
Dec 31 17:40:19 DemonicProductions postfix/smtpd[14099]: connect from srv195086.webreus.nl[87.119.195.86]
Dec 31 17:40:19 DemonicProductions postfix/trivial-rewrite[14109]: fatal: match_list_parse: open file /etc/postfix/vhosts.txt: No such file or directory
Dec 31 17:40:20 DemonicProductions postfix/smtpd[14106]: connect from 77-103-161-36.cable.ubr05.chap.blueyonder.co.uk[77.103.161.36]
Dec 31 17:40:20 DemonicProductions postfix/smtpd[14106]: disconnect from 77-103-161-36.cable.ubr05.chap.blueyonder.co.uk[77.103.161.36]
Dec 31 17:40:20 DemonicProductions postfix/master[10942]: warning: process /usr/lib/postfix/trivial-rewrite pid 14109 exit status 1
Dec 31 17:40:20 DemonicProductions postfix/master[10942]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Dec 31 17:40:22 DemonicProductions postfix/smtpd[14104]: disconnect from 77-103-161-36.cable.ubr05.chap.blueyonder.co.uk[77.103.161.36]
Dec 31 17:40:30 DemonicProductions postfix/smtpd[14105]: too many errors after UNKNOWN from 77-103-161-36.cable.ubr05.chap.blueyonder.co.uk[77.103.161.36]
Dec 31 17:40:30 DemonicProductions postfix/smtpd[14105]: disconnect from 77-103-161-36.cable.ubr05.chap.blueyonder.co.uk[77.103.161.36]
Dec 31 17:41:21 DemonicProductions postfix/trivial-rewrite[14146]: fatal: match_list_parse: open file /etc/postfix/vhosts.txt: No such file or directory
Dec 31 17:41:22 DemonicProductions postfix/master[10942]: warning: process /usr/lib/postfix/trivial-rewrite pid 14146 exit status 1
Dec 31 17:41:22 DemonicProductions postfix/master[10942]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Dec 31 17:42:22 DemonicProductions postfix/trivial-rewrite[14186]: fatal: match_list_parse: open file /etc/postfix/vhosts.txt: No such file or directory
Dec 31 17:42:23 DemonicProductions postfix/master[10942]: warning: process /usr/lib/postfix/trivial-rewrite pid 14186 exit status 1
Dec 31 17:42:23 DemonicProductions postfix/master[10942]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Dec 31 17:42:55 DemonicProductions postfix/postfix-script[14223]: warning: not owned by root: /etc/postfix/main.cf~
Dec 31 17:42:55 DemonicProductions postfix/postfix-script[14224]: warning: not owned by root: /etc/postfix/valias.txt
Dec 31 17:42:55 DemonicProductions postfix/postfix-script[14225]: warning: not owned by root: /etc/postfix/valias.txt.db
Dec 31 17:42:55 DemonicProductions postfix/postfix-script[14226]: warning: not owned by root: /etc/postfix/vhost.txt
Dec 31 17:42:55 DemonicProductions postfix/postfix-script[14227]: warning: not owned by root: /etc/postfix/vmaps.cf
Dec 31 17:42:55 DemonicProductions postfix/postfix-script[14228]: warning: not owned by root: /etc/postfix/vmaps.cf~
Dec 31 17:43:02 DemonicProductions postfix/postfix-script[14279]: stopping the Postfix mail system
Dec 31 17:43:02 DemonicProductions postfix/master[10942]: terminating on signal 15
Dec 31 17:43:05 DemonicProductions postfix/postfix-script[14319]: warning: not owned by root: /etc/postfix/main.cf~
Dec 31 17:43:05 DemonicProductions postfix/postfix-script[14320]: warning: not owned by root: /etc/postfix/valias.txt
Dec 31 17:43:05 DemonicProductions postfix/postfix-script[14321]: warning: not owned by root: /etc/postfix/valias.txt.db
Dec 31 17:43:05 DemonicProductions postfix/postfix-script[14322]: warning: not owned by root: /etc/postfix/vhost.txt
Dec 31 17:43:05 DemonicProductions postfix/postfix-script[14323]: warning: not owned by root: /etc/postfix/vmaps.cf
Dec 31 17:43:05 DemonicProductions postfix/postfix-script[14324]: warning: not owned by root: /etc/postfix/vmaps.cf~
Dec 31 17:43:05 DemonicProductions postfix/postqueue[14365]: warning: Mail system is down -- accessing queue directly
Dec 31 17:43:11 DemonicProductions postfix/postfix-script[14404]: warning: not owned by root: /etc/postfix/main.cf~
Dec 31 17:43:11 DemonicProductions postfix/postfix-script[14405]: warning: not owned by root: /etc/postfix/valias.txt
Dec 31 17:43:11 DemonicProductions postfix/postfix-script[14406]: warning: not owned by root: /etc/postfix/valias.txt.db
Dec 31 17:43:11 DemonicProductions postfix/postfix-script[14407]: warning: not owned by root: /etc/postfix/vhost.txt
Dec 31 17:43:11 DemonicProductions postfix/postfix-script[14408]: warning: not owned by root: /etc/postfix/vmaps.cf
Dec 31 17:43:11 DemonicProductions postfix/postfix-script[14409]: warning: not owned by root: /etc/postfix/vmaps.cf~
Dec 31 17:43:11 DemonicProductions postfix/postfix-script[14449]: starting the Postfix mail system
Dec 31 17:43:14 DemonicProductions postfix/master[14450]: daemon started -- version 2.4.5, configuration /etc/postfix
Dec 31 17:43:14 DemonicProductions postfix/postfix-script[14491]: warning: not owned by root: /etc/postfix/main.cf~
Dec 31 17:43:14 DemonicProductions postfix/postfix-script[14492]: warning: not owned by root: /etc/postfix/valias.txt
Dec 31 17:43:14 DemonicProductions postfix/postfix-script[14493]: warning: not owned by root: /etc/postfix/valias.txt.db
Dec 31 17:43:14 DemonicProductions postfix/postfix-script[14494]: warning: not owned by root: /etc/postfix/vhost.txt
Dec 31 17:43:14 DemonicProductions postfix/postfix-script[14495]: warning: not owned by root: /etc/postfix/vmaps.cf
Dec 31 17:43:14 DemonicProductions postfix/postfix-script[14496]: warning: not owned by root: /etc/postfix/vmaps.cf~
```

---

### Post by hockey97 on 2008-01-01
well my mail server works well the config is right.

I get only an error when I send  the mail to an email address like [email]somthing@aol.com[/email]  

I would get this  :     Relay access denied

that's it. but I done a dns check and everything is good even the connection.

---

### Post by rsw686 on 2008-01-01
> **hockey97 said:**
> well my mail server works well the config is right.

I get only an error when I send  the mail to an email address like [email]somthing@aol.com[/email]  

I would get this  :     Relay access denied

that's it. but I done a dns check and everything is good even the connection.

Are you rejecting non authenticated if so you need to enable smtp authentication in your email client.

---

### Post by hockey97 on 2008-01-01
I don't really know. How can I tell ?? Should I look in the main.cf file???

---

### Post by rsw686 on 2008-01-01
Here's what that section of my main.cf looks like. You need something of this sort to make it work.

```

smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions =
        permit_mynetworks,
        permit_sasl_authenticated,
        reject_non_fqdn_sender,
        reject_unknown_sender_domain,
        reject_non_fqdn_recipient,
        reject_unknown_recipient_domain,
        reject_unauth_destination,
        reject_rbl_client zen.spamhaus.org,
        reject_rbl_client bl.spamcop.net,
        permit

```

---

### Post by hockey97 on 2008-01-01
I tested my mail server again but this time I just tested [email]aaron@demonicproductions.com[/email]  .

I wanted to see if I can e-mail myself.

and I got this error.

: Recipient address rejected: User unknown in virtual mailbox table

---

### Post by hockey97 on 2008-01-01
it seems I am having trouble with the lookup.

it can't find my user [email]aaron@demonicproductions.com[/email]  

it fails on lookup and spitting out an error that mainly say's no such user.

---

### Post by rsw686 on 2008-01-01
Verify that you have something similar to the below in your main.cf and that those files have the correct database credentials and sql statement.

```

virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf

```

---

### Post by hockey97 on 2008-01-01
I have instead of mysql: then the files ect.

I have  proxy:mysql: then the dir to the files

can their be 2 query's? or no?
I wanted to select 2 col one domain and one maildir. 

I don't think I have to select the username meaning the [email]user@domain.com[/email]
column .

---

### Post by rsw686 on 2008-01-01
I mentioned twice before to use the mysql layout from postfix admin. You can just import the sql file into mysql. Then you can use any number of tutorials which give you the exact commands for each of the need files.

[http://sourceforge.net/projects/postfixadmin/](http://sourceforge.net/projects/postfixadmin/)

At the bottom of this page is how to import the sql file
[http://www.howtoforge.com/virtual_users_postfix_courier_mailscanner_clamav_centos_p2](http://www.howtoforge.com/virtual_users_postfix_courier_mailscanner_clamav_centos_p2)

And towards the end of this page is the syntax for the virtual maps files
[http://www.howtoforge.com/virtual_users_postfix_courier_mailscanner_clamav_centos_p3](http://www.howtoforge.com/virtual_users_postfix_courier_mailscanner_clamav_centos_p3)

---

### Post by hockey97 on 2008-01-01
> **rsw686 said:**
> I mentioned twice before to use the mysql layout from postfix admin. You can just import the sql file into mysql. Then you can use any number of tutorials which give you the exact commands for each of the need files.

[http://sourceforge.net/projects/postfixadmin/](http://sourceforge.net/projects/postfixadmin/)

At the bottom of this page is how to import the sql file
[http://www.howtoforge.com/virtual_users_postfix_courier_mailscanner_clamav_centos_p2](http://www.howtoforge.com/virtual_users_postfix_courier_mailscanner_clamav_centos_p2)

And towards the end of this page is the syntax for the virtual maps files
[http://www.howtoforge.com/virtual_users_postfix_courier_mailscanner_clamav_centos_p3](http://www.howtoforge.com/virtual_users_postfix_courier_mailscanner_clamav_centos_p3)

I followed those. I just now done what you suggested now I my mail server connection failed.

---

### Post by rsw686 on 2008-01-01
What failed? You need to be more specific. The error logs will tell you exactly what is wrong.

---

### Post by hockey97 on 2008-01-01
this is what shows in the log.

Jan  1 18:07:02 DemonicProductions postfix/trivial-rewrite[9198]: warning: connect to mysql server localhost: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

---

### Post by rsw686 on 2008-01-01
Are you sure that mysql is running? Try restarting mysqld.

---

### Post by hockey97 on 2008-01-01
ya it's running. I ran test's on some website that gives a dns report and mine fails only on connections but at random times I sometimes get a fail on the greeting.


here is a smtp error : K, connected to demonicproductions.com...
< 220 demonicproductions.com ESMTP mail.demonicproductions.com (Ubuntu)
> HELO edit.dnsvr.com
< 250 mail.demonicproductions.com
> MAIL FROM:<aaron@demonicproductions.com>
ERROR: Timeout while waiting to read data from host demonicproductions.com.:25, Unknown error 3219790784

---

### Post by hockey97 on 2008-01-02
I have been monkeying around with the config files and still can't get the connections right.

in the log I get permission warnings becsue I have the files at permission 777 and also the  in the log it show's it's reading the mysql database and then right after all the mysql ok's then I get a lookup failure. then it times out and then restarts.

---

### Post by rsw686 on 2008-01-02
The config files should all be root owned and have 644 permissions.

---

### Post by hockey97 on 2008-01-02
ok I got the connections working.

but  I still get an error.  this is the error: Recipient address rejected: User unknown in virtual alias table

I am using those mysql files that you recommended.

here is  my mail log.

```
Jan  2 15:48:05 DemonicProductions postfix/postfix-script[9668]: warning: group or other writable: /etc/postfix/./mysql_virtual_mailbox_maps.cf
Jan  2 15:48:05 DemonicProductions postfix/postfix-script[9669]: warning: group or other writable: /etc/postfix/./mysql_virtual_mailbox_limit_maps.cf
Jan  2 15:48:05 DemonicProductions postfix/postfix-script[9670]: warning: group or other writable: /etc/postfix/./mysql_relay_domains_maps.cf
Jan  2 15:48:31 DemonicProductions postfix/smtpd[9715]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Jan  2 15:48:33 DemonicProductions postfix/smtpd[9715]: connect from srv195086.webreus.nl[87.119.195.86]
Jan  2 15:48:35 DemonicProductions postfix/trivial-rewrite[9719]: warning: do not list domain demonicproductions.com in BOTH virtual_alias_domains and virtual_mailbox_domains
Jan  2 15:48:35 DemonicProductions postfix/smtpd[9715]: NOQUEUE: reject: RCPT from srv195086.webreus.nl[87.119.195.86]: 550 5.1.1 <info@demonicproductions.com>: Recipient address rejected: User unknown in virtual alias table; from=<relaytest@dnscolos.com> to=<info@demonicproductions.com> proto=SMTP helo=<dnscolos.com>
Jan  2 15:48:35 DemonicProductions postfix/smtpd[9715]: disconnect from srv195086.webreus.nl[87.119.195.86]
Jan  2 15:48:35 DemonicProductions postfix/smtpd[9715]: connect from srv195086.webreus.nl[87.119.195.86]
Jan  2 15:48:36 DemonicProductions postfix/smtpd[9715]: lost connection after CONNECT from srv195086.webreus.nl[87.119.195.86]
Jan  2 15:48:36 DemonicProductions postfix/smtpd[9715]: disconnect from srv195086.webreus.nl[87.119.195.86]
Jan  2 15:48:36 DemonicProductions postfix/smtpd[9715]: connect from srv195086.webreus.nl[87.119.195.86]
Jan  2 15:48:39 DemonicProductions postfix/smtpd[9715]: disconnect from srv195086.webreus.nl[87.119.195.86]
Jan  2 15:49:21 DemonicProductions postfix/smtpd[9715]: warning: 64.85.73.124: address not listed for hostname mail.dotster.com
Jan  2 15:49:21 DemonicProductions postfix/smtpd[9715]: connect from unknown[64.85.73.124]
Jan  2 15:49:22 DemonicProductions postfix/trivial-rewrite[9721]: warning: do not list domain demonicproductions.com in BOTH virtual_alias_domains and virtual_mailbox_domains
Jan  2 15:49:22 DemonicProductions postfix/smtpd[9715]: NOQUEUE: reject: RCPT from unknown[64.85.73.124]: 554 5.7.1 <shyhockeyboy@aol.com>: Relay access denied; from=<aaron@demonicproductions.com> to=<shyhockeyboy@aol.com> proto=SMTP helo=<edit.dnsvr.com>
Jan  2 15:49:22 DemonicProductions postfix/smtpd[9715]: lost connection after RCPT from unknown[64.85.73.124]
Jan  2 15:49:22 DemonicProductions postfix/smtpd[9715]: disconnect from unknown[64.85.73.124]
Jan  2 15:49:39 DemonicProductions postfix/smtpd[9715]: warning: 64.85.73.124: address not listed for hostname mail.dotster.com
Jan  2 15:49:39 DemonicProductions postfix/smtpd[9715]: connect from unknown[64.85.73.124]
Jan  2 15:49:40 DemonicProductions postfix/smtpd[9715]: NOQUEUE: reject: RCPT from unknown[64.85.73.124]: 550 5.1.1 <aaron@demonicproductions.com>: Recipient address rejected: User unknown in virtual alias table; from=<aaron@demonicproductions.com> to=<aaron@demonicproductions.com> proto=SMTP helo=<edit.dnsvr.com>
Jan  2 15:49:40 DemonicProductions postfix/smtpd[9715]: lost connection after RCPT from unknown[64.85.73.124]
Jan  2 15:49:40 DemonicProductions postfix/smtpd[9715]: disconnect from unknown[64.85.73.124]
```

I am going to chmod those files to 644

---

### Post by hockey97 on 2008-01-02
I chmod those files to permission 644  .

I don't know in the database if I put the right info in their.

---

### Post by hockey97 on 2008-01-03
I read the logs and  everything looks good. the only problem is my lookup fails.

mysql at first didn't allow postfix to lookup so I fised it with adding localhost to host.allow file and it works.

but still I am getting error's that postfix can't find such a user.

I put [email]aaron@demonicproductions.com[/email] 
would I have the wrong e-mail address I have in the database the user as [email]aaron@demonicproduciton.com[/email] .

but in the postfix config the hostname is demonicproductions.com

the destination is mail.demonicproductions.com

how can I find the user info on what postfix sees are users?

---

### Post by hockey97 on 2008-01-04
HI I  I got it to work now only I can get mail from other people but can't send it to others.

also How can I have it setup so that the e-mails go into the mysql database. 
my mail server put's incomeing mail in the dir /var/mail/user.

but dosen't put it where I made the maildir that I put in mysql database.

I plan to use this mail server for 2 domains.

---

### Post by hockey97 on 2008-01-05
does anyone know how I can change the maildir.  I followed tutorials for postfix with mysql.

and it mainly just tells me to put the maildir I want in the mailbox column but I done so but postfix uses just still uses a default area which is at /var/mail/user

I want it to take the mail to /home/user/domain/user and make it able to be in the database so I can just use php to bring up the e-mail in a webpage enviroment.

I also have problems sending mail to well know e-mail providors like aol ect.

do I need  a certificat I don't think my isp has a smarthost. that I can use to get behind the blacking ro refused error.

---

