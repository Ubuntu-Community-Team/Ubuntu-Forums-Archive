---
title: "questions about web server setup"
date: 2009-07-23
forum: Server Platforms
---

### Post by Linux&amp;Gsus on 2009-07-23
Hi all,
I have  bunch of question about setting up a web server and more questions might follow in the discussion. It might even be that I ask some stupid questions. So, please bear with me.

**Let me quickly explain what I want to do.**
First of all, I do have a little server at home on which I have played around in the past and have setup websites for my own development, etc. So, I'm comfortable with using the command line, getting the server running to host web sites and the like. But all that is really just at home in my own little network, not for the public.

However, within my circle of friends I've been asked by a few people about web sites, how to create them, how to host them, etc. Well, sorta the typical things you get asked when people think you are a geek... ;)
Anyways, I personally have a couple sites, plus if I would help everyone who wants a site it would be actually cheaper to rent a root server and host the sites myself. Only problem is that I'm not familiar with all aspects of running/maintaining a server like that.

I did do a fair bit of reading on the topic but still have questions. I would like to keep the discussion on a technical level. Meaning I know and I have read about the concerns of some people about doing something like this for friends in regards to money, trouble shooting, etc.

So, I found a host with good reputation that offers very good priced root servers. As OS, besides others, they offer Ubuntu Server 9.04 as 32 and 64 Bit version. Although, a 32Bit OS on a server with 12GB RAM is kinda pointless, I guess. So, Ubunut 9.04 64Bit would be my preferred option.
The servers are Quad-Core Intel i7-920 with 2x1500GB HDD in RAID1 or i7-975 with 3x1500GB HDD in RAID5, depending on the offer to pick. LAMP is pre-installed, as far as I understand it.


**So, here are my questions.**

1)
I don't know if I can choose on how the drives are partitioned. But if so, what would you recommend based on the above specs for a web server?

2) 
In case I have options regarding the file systems, what would you recommend?

3)
Software. What do you recommend to use and why?

3a)
Since this is not only for me at home I need to provide people an easy to use interface to manage their site/account. I searched around and found some stuff but kinda don't like to invest in commercial product like Plesk, etc. I found some FOSS like ispCP Omega or ispConfig, etc. But I have absolute no experience with these. What can you tell me about any FOSS options, good and bad.

3b)
What do I need to monitor the server? I know it'll be monitored by the web host since I rent the server, so they are responsible from a hardware point of view. Still, I would like to know about the servers health.

3c)
In regards to the monitoring what are my (best, fastest, easiest,...) options to get notified about issues? How easy is it set up email notification, e.g to an out side email service like Yahoo, Gmail, etc? But what when the email service is down for what ever reason? How easy is it setup a SMS service, how does that work, what does it cost me to send an SMS (internationally)?
Are there other options, e.g. like checking the server periodically from my server at home? How would I do that, how would I get notified, what is the quickest way, what the most reliable/fail safe to get notified about issues?

3d)
What do I need to know and take care of in regards to security? E.g. how can I enforce a minimum requirement for passwords. Is Fail2Ban a good option to consider, are there others? What do I need to know about brute force or what ever else attacks?

3e)
FTP, how do I make sure that when someone logs in via FTP that they only see their own files/folders? 
Technically, I would like to provide SFTP and disable FTP (non-encrypted) access. How am I doing this?

3f)
Same for email, e.g. I only want to allow POP-SSL but disable non-encrypted POP. How is this done?
Also on the topic of Email. I have never setup an email server. What do I need for that?

I know that I need an MX-Record. I haven't really got me head around how to do that. It's DNS entry, if I got that right. But how does it really work? Say, I get a server that is in the network of "myHost" and then I have 10 websites "domain1", "domain2", "domain3"..."domain10". How does the MX-Record look like?

3g)
Speaking of SSL. If I do that, do I need an "official" SSL certificate issues by one of the "big ones" so that peoples browser and email clients don't freak out?
I have set up my own root CA to remote connect to my server at home via VPN over SSL. But how do I install such an "official" SSL certificate, what if a few of the users want SSl. I can't just use a self-signed certificate since the visitors' browsers will terrify their users about unknown/un-secure site etc blah blah.

3h)
What can I use for billing? I would prefer that to be automated and sent as PDF attachment sent to the people.
Is something like that integrated in the software mentioned in 3a? How good is it or what else to use instead?

3i)
The web host I'm interested in the most provides 100GB backup space. Out of the potential hundreds of GBs of data (over time) what would you recommend me to backup and how is it done the best? E.g like only the databases, what about server config files, list of installed apps...?

3j)
What other software do I need?

4)
So far I personally have an all inclusive web package. Meaning web space and 3 domain names inclusive. Since I then, obviously, want to get my sites hosted somewhere else I need to get my domain name transfered to another registrar.
Which registrar would you recommend and how is this done?

5)
With the above mentioned specs what do you think how many websites can be hosted on these servers. I know that it fully depends on the sites and the expected traffic. But I'm not talking about the next Ubuntu Forums, Slashdot or Wikipedia kinda sites. More like ordinary personal Blog (Wordpress, Drupal, Joomla,...), maybe a small online store on a couple sites or so (one off the interested folks is a musician), but really nothing massive. A rough estimation is more than enough for me to know.

6)
What else have I forgotten or overlooked? Other recommendations, opinions, etc.




I know it was a lot, thanks for reading all the way through. Also thanks for any help and info on the topic.

Cheers,
L&G

---

### Post by Linux&amp;Gsus on 2009-07-25
No one any thoughts? :(
Or did I write too much in a single post?

Cheers,
L&G

---

### Post by jeffathehutt on 2009-07-25
I will help where I can, but I don't have much experience hosting web sites.

1) Partitioning depends on how you want to set it up.  Do you want each user to serve their content from /home/user/public_html or something similar?  In that case, you would make /home the largest partition.  If you want to serve out of /var/www (which it sounds like you don't, usually that would be for one site only) then you would make /var a very large partition.  Keep in mind that database files are usually kept in /var, as well as logs and other things, so make sure you have enough space there as well.

2) Personally I stick with ext3.  It's usually fast enough, and very robust and stable.  Reiser is known to be very fast when you have many small files, rather than a few large ones.  So, if most content is html and not videos or music, then reiser might be worth looking in to.

3) What do you need the software to do?  Tell us some specific functions you need (like web server, email server, etc.) and we can give recomendations.

3b) The top command can give you basic stats, things like the currently running programs, and how much ram / processing power they are using.  Also you can see how much free ram you have.

3e) SFTP is done over ssh, so as long as you have a working ssh server (openssh-server most likely) you should be able to log in with sftp.  To disable ftp access, just don't run an ftp server ;)

3g) If you don't want a user's browser to complain, you will need a certificate from one of the "big ones".  I am not sure how to install them, but I would assume you would get instructions when you buy it.

4) Usually, the registrar and host (in this case, you ARE the host) do not have to be related.  I use GoDaddy as a registrar for all my domains, which is different than my web host.  If you want to, you can transfer your existing domains over to GoDaddy (there are instruction on their web site).  Basically, all that matters with the domains is the dns servers associated with it, not the registrar from where you bought the domain.

5) I doubt disk space will be a problem regardless of how many accounts you have.  Most personal blogs use less than 10 GB disk space.  4 cores is also decent.  As long as your sites don't get too much traffic at once, you can probably fit at least 50+ accounts on one machine with very little lag (most likely many more, but like you said it does depend on multiple factors).  Whatever you do, **don't oversell!**  Putting 3000 accounts on one machine will leave you with many angry customers. :)  It's better to host 50 fast and responsive sites rather than 3000 slow sites that take 5 minutes to load every time someone tries to load the page.

Sorry I can't really offer much more.  I have very little experience with hosting web sites, but hopefully this will at least get you started.

---

### Post by Linux&amp;Gsus on 2009-07-26
Hi & Thanks, that's good stuff

> **jeffathehutt said:**
> 1) Partitioning depends on how you want to set it up.  Do you want each user to serve their content from /home/user/public_html or something similar?  In that case, you would make /home the largest partition.  If you want to serve out of /var/www (which it sounds like you don't, usually that would be for one site only) then you would make /var a very large partition.  Keep in mind that database files are usually kept in /var, as well as logs and other things, so make sure you have enough space there as well.
While it makes sense still the question comes to mind how much space I would need for Database or Logfiiles. How big will they grow? Well, sure logfiles should be checked and potentially periodically deleted if there is no issue. I don't see a need to save them over an extended period of time.
But I would guess it's a bit of a problem if the layout turns out to be all wrong at the end. So, wouldn't it then be wise to have a rather small /var and symlink that to, say /home/var and have all the database a log files there? Or is there anything I'm missing?? Well, or at lest the database and taking care that log files don't fill up the remaining space in /var?



> **jeffathehutt said:**
> 2) Personally I stick with ext3.  It's usually fast enough, and very robust and stable.  Reiser is known to be very fast when you have many small files, rather than a few large ones.  So, if most content is html and not videos or music, then reiser might be worth looking in to.
I guess that most people put their videos on something like YouTube and link it them in their Blogs. However, one of my friends is a musician who potentially wants to put up an online store where people can listen to samples and by and download his music. Which potentially could turn out to become the most traffic intense site.
Unless people put up larger Galleries, that is. Although, I have the impression that many prefer Facebook for that. Simply because of the Social Networking aspects of it. But I might be wrong.



> **jeffathehutt said:**
> 3) What do you need the software to do?  Tell us some specific functions you need (like web server, email server, etc.) and we can give recomendations.
Well, people have email accounts with their websites. So, I guess a webmail interface isn't a bad idea. I know about Squirrel Mail, is there more?
Also, people need to be able to administer their accounts, add/delete email accounts, database, checking traffic (AWStats??), etc. Basically all these things you can do when you sign up for web hosting at any host out there. However, I don't see a point in paying for something like Plesk, etc. It would only make it more expensive for us all.
I don't want to do that to make money but to help some friends an family who don't know how to do that on their own. And from my calculations it doesn't take too many people to actually be a lot cheaper then renting individual web space for everyone. Not to speak of the flexibility and the issue with over-selling that you mention later on.
Having said that, I would much more prefer a OpenSource solution and if there's extra money donate to various projects.

So, the question here is, what OpenSource solution can be recommended instead of something like Plesk?



> **jeffathehutt said:**
> 3b) The top command can give you basic stats, things like the currently running programs, and how much ram / processing power they are using.  Also you can see how much free ram you have.
TOP, you are right. Sometimes I can be so blind to the obvious things. Thanks for the reminder.
However, I would like to know if people think that I need more software to monitor the server. I'm mean, something like PHPMyAdmin and Webmin is obvious. I would be too lazy to not have that. But what about e.g. Nagios? Is that a must have or not needed? After all I "only" rent a server, so the host is responsible for the hardware, anyways, and will monitor that.



> **jeffathehutt said:**
> 3e) SFTP is done over ssh, so as long as you have a working ssh server (openssh-server most likely) you should be able to log in with sftp.  To disable ftp access, just don't run an ftp server ;)
Now, just to clarify that. I don't need to install a FTP server to use SFTP?
I would have thought that I need a FTP server + SSH server to use SFTP.




> **jeffathehutt said:**
> 5) I doubt disk space will be a problem regardless of how many accounts you have.  Most personal blogs use less than 10 GB disk space.  4 cores is also decent.  As long as your sites don't get too much traffic at once, you can probably fit at least 50+ accounts on one machine with very little lag (most likely many more, but like you said it does depend on multiple factors).  Whatever you do, **don't oversell!**  Putting 3000 accounts on one machine will leave you with many angry customers. :)  It's better to host 50 fast and responsive sites rather than 3000 slow sites that take 5 minutes to load every time someone tries to load the page.
Over-selling is one of the big reasons why I look into this option of hosting myself. I have so many friends asking me about websites plus I see the trouble I have with what I'm looking after just now, that I most likely have less issues doing it myself.
Just to get that straight, I know it's quite some work to set up, maintain, look after that. But if I would scale the trouble I have with web hosts right now with the handful sites I look after to 50 sites then it would need 3 people working full time on that, no kidding. Sometimes I'm asking myself if they break things on purpose or if I just happen to have bad luck.

So, 50 sites, you think? And I was concerned if 20 is too much. By the time I help hosting 50 sites I would have thought I need 3 servers...:D
I agree that HDD space is most likely not the issue for the average site. Since most folks put videos, etc on 3rd party sites anyways. I'm more concerned about page loads. Although, I guess that big popular CMSs like Joomla do their share to slow down load times since they kinda built to be able to do everything. Whether you need all that functionality or not.



> **jeffathehutt said:**
> Sorry I can't really offer much more.  I have very little experience with hosting web sites, but hopefully this will at least get you started.
Don't say it's not much. The more opinions the better. Everything is helpful to get my brain around it. After all, if I end up doing that I need to know what I'm getting myself into.

So, thank you very much,
L&G

---

### Post by R.Bucky on 2009-07-26
Dude! that is one hell of a long post. Yes, too many questions. I host a little over a half-dozen sites from home. So, I'll give some brief help. PM me if you want more... no worries.

It makes sense to create 3 partitions. One for your "/" directory, one for your swap (make sure that it is double your available RAM), and a third for your web server files. If your distribution fails, you can always reinstall and not lose your files (you should have a solid backup regardless).

Go with ext3.

Number 3 is a big question. If you want to host you are out of luck. Based on the questions that you are asking, you need to learn more before you start hosting. otherwise, your clients will be pissed when you get compromised...

GoDaddy is a great registrar. But, HostGator is well recommended [www.hostgator.com/](www.hostgator.com/)

As mentioned before, I host a half dozen sites and run about a GIG of RAM during heavy processing. 

further questions - PM me

---

### Post by Linux&amp;Gsus on 2009-07-27
> **R.Bucky said:**
> Dude! that is one hell of a long post. Yes, too many questions.
Some people are verbal processors, I'm not, I guess I just write a lot...:oops:


> **R.Bucky said:**
> It makes sense to create 3 partitions...
Thanks


> **R.Bucky said:**
> Go with ext3.
OK, will do, if I have an option to choose from, anyways.


> **R.Bucky said:**
> Number 3 is a big question. If you want to host you are out of luck. Based on the questions that you are asking, you need to learn more before you start hosting. otherwise, your clients will be pissed when you get compromised...
My goal is to not get compromised...:D LOL
No, really, I know that I need to learn more before I start doing something like that. That's the reason I ask all the questions here, before I start doing anything. Actually, this is the best way for me to learn, asking questions on a forum, discussing things that way.

Having said that, I'm very open to get pointed to the right direction, e.g. for online tutorials, other threads or sites where this has been discussed before, recommendations on good books about that topic, etc.


> **R.Bucky said:**
> GoDaddy is a great registrar. But, HostGator is well recommended [www.hostgator.com/](www.hostgator.com/)
Haven't heard of HostGator before, so will have a look there. Thanks.


Cheers,
L&G

---

### Post by hessiess on 2009-07-27
Don't bother renting servers or offering services to outher people until you know exactly what you are doing. There are a very large number of potential security vulnerabilities relating to shared servers, and missing just one leaves you/ your users open to attack. There are plenty of dirt cheep, secure, shared hosting solutions already available from reputable companies, and thus there is no reason whatsoever to offer your own hosting.

If you want to learn server configuration, just play around with setting up servers on your own computer, lock it down, and try to find ways of hacking into it, then fix those problems and repeat;)

> 
3g)
Speaking of SSL. If I do that, do I need an "official" SSL certificate issues by one of the "big ones" so that peoples browser and email clients don't freak out?
I have set up my own root CA to remote connect to my server at home via VPN over SSL. But how do I install such an "official" SSL certificate, what if a few of the users want SSl. I can't just use a self-signed certificate since the visitors' browsers will terrify their users about unknown/un-secure site etc blah blah.

You cannot offer SSL unless you are doing IP based virtual hosting.

> 
The web host I'm interested in the most provides 100GB backup space. Out of the potential hundreds of GBs of data (over time) what would you recommend me to backup and how is it done the best? E.g like only the databases, what about server config files, list of installed apps...?

Back up *EVERYTHING* that you can, you would need to be hosting a *lot* of websites to even get close to using 100GB. Most small websites aren't even close to a gig in size.

---

### Post by R.Bucky on 2009-07-27
+1 @ hessiess - > don't bother renting servers...

There are many open-source alternatives to Cpanel. None of which I have tried out. EHCP is a hosting solution similar to cPanel. However, there are quite a few forum thread on this topic. For instance, try this [Google search]("http://www.google.com/search?q=site%3Aubuntuforums.org+alternatives+to+cPanel&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a").

One necessity for configuring any of these would be the installation and successful integration of BIND9. You need DNS in order for hosting to be worthwhile. You should work on that first.

If you are going to be hosting sites yourself, you need to harden your security. Stick with Ubuntu Server 8.04LTS until the next LTS comes out. Two minor security configuration edits to the standard ssh protocol might include installation of fail2ban and changing the default ssh port of 22. Read [this blog post]("http://buckycomputing.net/blog/securing-ssh-on-your-server/") on how to do that. 

Additional learning resources might include [nixCraft]("http://www.cyberciti.biz/"), [Linux Networking Fourms]("http://www.linuxhomenetworking.com/forums/index.php"), and these Ubuntu Forums. They are a great resource.

---

### Post by helix2301 on 2009-07-27
Use virtual hosts and you could host multiple sites on one box partitioning is kind of at your own if you have a lot of big sites then you are going to need a big hard drive and you are going need a big partition for your /home.

---

### Post by Linux&amp;Gsus on 2009-07-28
Thanks for the replies, guys. I'll look into all those things.
Pointing me to the sites where I can learn more is the kinda information I need.


Just to clarify that again. I don't mean to randomly jump into this self hosting kinda deal. I am very well aware of the security risks, as I mentioned before I take care (technical aspects) of some websites for others, 7 sites all together by now. So, yes, I do know that there are "bad boys" out there and I can't and wont take that lightly.

That's one of the reasons I'm here for, to learn about that stuff. When I know what I need to learn I can learn it, and when I learned it I can go ahead and do it.
Otherwise I would have just done it instead of asking all these *silly* question and then come here to ask for solutions for the trouble I got myself into ;-)

Speaking of LTS vs 9.04. The host I feel most comfortable with atm is not offering 8.04LTS anymore, only 9.04. Of course, I would have preferred LTS. I could choose another distro they offer to install, like e.g. Debian. But then I would like to not have a gazillion different distros to maintain.
That is for my pure laziness.

Well, for all I know even 9.10 could be out by the time I get my hands into this hosting stuff. If they offer that to install as well, then AFAIK it would be only one step to the next LTS with which I would stick then until the next LTS comes out, etc.


Cheers,
L&G

---

