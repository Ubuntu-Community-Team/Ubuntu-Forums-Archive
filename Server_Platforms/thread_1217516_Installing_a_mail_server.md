---
title: "Installing a mail server"
date: 2009-07-19
forum: Server Platforms
---

### Post by Gannon8 on 2009-07-19
Hello all.

I have looked for a good tutorial for installing a mail server, but so far, none of them seem to work, even though I follow the instructions exactly.

Can anyone recommend a tutorial that actually works for ubuntu 9.04?

---

### Post by druhboruch on 2009-07-19
There are a few good tutorials on howto forge
[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04)

---

### Post by windependence on 2009-07-19
Unfortunately, doing this from scratch is more than most people think it is, you generally need to install 4 or 5 software packages AND configure them which can be daunting for someone new to this or as I have said even someone with experience like myself, it's a task I don't want to do.

Most all of my mail installs for my clients are Zimbra, which is a package that installs from a script and configures what you need. Zimbra is owned by Yahoo, but they maintain an open source version which is fully functional and very good. [http://www.zimbra.com/community/downloads.html](http://www.zimbra.com/community/downloads.html)

Another member here, HermanAB, uses and likes a similar package called Citadel. Same concept, a new user can have a mail server up and running within a half hour or so. Both packages have a nice configuration GUI after the install.

If you just want to learn how to do it the long way, there is documentation out there.

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04)

[http://postfixmail.com/blog/?p=629](http://postfixmail.com/blog/?p=629)

-Tim

---

### Post by Gannon8 on 2009-07-19
> **druhboruch said:**
> There are a few good tutorials on howto forge
[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04)

Yeah, thats one that I tried. My results didn't match the one on page 4 though.

> Most all of my mail installs for my clients are Zimbra
```
Operations logged to /tmp/install.log.11279
Checking for existing installation...
    zimbra-ldap...NOT FOUND
    zimbra-logger...NOT FOUND
    zimbra-mta...NOT FOUND
    zimbra-snmp...NOT FOUND
    zimbra-store...NOT FOUND
    zimbra-apache...NOT FOUND
    zimbra-spell...NOT FOUND
    zimbra-proxy...NOT FOUND
    zimbra-archiving...NOT FOUND
    zimbra-convertd...NOT FOUND
    zimbra-cluster...NOT FOUND
    zimbra-core...NOT FOUND
./util/utilfunc.sh: line 643: rpm: command not found


PLEASE READ THIS AGREEMENT CAREFULLY BEFORE USING THE SOFTWARE.
ZIMBRA, INC. ("ZIMBRA") WILL ONLY LICENSE THIS SOFTWARE TO YOU IF YOU
FIRST ACCEPT THE TERMS OF THIS AGREEMENT. BY DOWNLOADING OR INSTALLING
THE SOFTWARE, OR USING THE PRODUCT, YOU ARE CONSENTING TO BE BOUND BY
THIS AGREEMENT. IF YOU DO NOT AGREE TO ALL OF THE TERMS OF THIS
AGREEMENT, THEN DO NOT DOWNLOAD, INSTALL OR USE THE PRODUCT.

License Terms for the Zimbra Collaboration Suite:
  http://www.zimbra.com/license/zimbra_public_eula_2.1.html


Press Return to continue
Checking for prerequisites...
     FOUND: NPTL
     MISSING: sudo
     MISSING: libidn
     MISSING: fetchmail
     MISSING: gmp
     MISSING: /usr/lib/libstdc++.so.5
Checking for suggested prerequisites...

###ERROR###

One or more prerequisite packages are missing.
Please install them before running this installer.

Installation cancelled.
```
I understand fetchmail, libidn, and gmp, but sudo? :confused:

---

### Post by windependence on 2009-07-19
```
sudo chmod -R 775 [zimbra_directory]
```

Try that and see if  it fixes the problem.

-Tim

---

### Post by HermanAB on 2009-07-19
Howdy,

The easiest mail server to install is Citadel.  It takes about 20 minutes.

Installing a postfix/apache/roundcube/dovecot system can easily consume 2 weeks of continuous head banging.

There are a bunch of Citadel guides here: 
[http://aeronetworks.ca/linuxhowtos.html](http://aeronetworks.ca/linuxhowtos.html)

However, you can just as well dive right in:
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

---

### Post by harry_bk on 2010-02-02
Hi everybody,
I'm doing an internship in a company and I have been asked to setup a mail server for the company. I chose to install postfix following the tutorial of Flurdy on postfix(**flurdy**.com/docs/**postfix).** [I]I finished the basic setups a week ago but nothing works as expected. I don't really know where I made mistake because I've tried to follow this tutorial step by step. [IMG]http://ubuntuforums.org/C:%5CDocuments%20and%20Settings%5CHarold%5CMes%20documents%5CMes%20images%5Cimcmd.jpg[/IMG]. The results I got can be seen on the following screenshot
[IMG]http://ubuntuforums.org/C:%5CDocuments%20and%20Settings%5CHarold%5CMes%20documents%5CMes%20images%5Cresult.jpg[/IMG]. So If anyone could me fix that problem It would be great.

P.S: I am using ubuntu 9.10 server on VMWARE 6
[/I]

---

### Post by quietas on 2010-02-02
I highly recommend Zimbra. Citadel is organize weirdly and it does too  much if all you want is a mail server with calendaring and such. Clark Connect is a similar system.

I've run two servers at work for 2 years after replacing and aging PHPGroupWare IMAP server. Zimbra is easy to use and has a common web based style that nearly anyone can pickup quickly. Updates are frequent, plus the devs and forum staff are frequent to help. The community behind it is active and very informed.

From the code, it looks like the RPM version for Redhat/Fedora was installed. I've used older version of Ubuntu dating back to 6.06, 8.04, and currently we are running our production unit using the Zimbra Network Edition with Redhat 5.3 ES and a second Ubuntu 8.04 box which gets rebuilt whenever there is a new release.

Install is dirt simple. Grab the .tgz file from [http://www.zimbra.com/community/downloads.html](http://www.zimbra.com/community/downloads.html) according to your particular Ubuntu version (6.06/8.04, i386/x64). Uncompress (tar zxvf filename.tgz). Then run the installer (sudo ./install.sh). If there are any things lacking it will detect them and tell you prior to the install.

The Wiki has plenty of distro specific install directions and so do the Zimbra forums.

---

### Post by harry_bk on 2010-02-02
Thanks a lot Quietas, actually the company wher eI work in doesn't have neither an internet website, nor a domain name. The site is under construction by some developers and I was asked to setup a mail server, which could work with addresses related to the company's domain name. eg: if my name is harry my address should be [email]harry@domainname.com[/email] . I wanted to test it locally first before being able to add users regarding the real domain name, and I saw the tutorials about postfix. So could Zimbra do the same ( I mean locally and once the domain name and website will be all right)??
Thanks for your advice

---

### Post by quietas on 2010-02-02
Exatly. I personally have our company website hosted offsite by a hosting company so our company internet doesn't have to take the hit on our bandwidth and our mail is hosted at our central office server room. All you will need to do is adjust your DNS records to point to the IP of you mail server and also the MX records. You may want to do a bit of research on DNS and how it works.

As for testing, I also run a mail server on test.mydomain.tld to play with before updating my production machine.

Also to gice you some options, you might look at Google Apps for Your Domain as well. It's great for small businesses, and free infact if you are less than 25 employees. I've set up a few companies like this through my side job.

---

### Post by harry_bk on 2010-02-03
Thanks a lot quietas, I'll try to setup zimbra and let you know how it works soon.

---

### Post by steev182 on 2010-02-05
Thanks for this, after reading it, I ended up creating an 8.04 vm with zimbra on it and it's actually really nice! Gonna have some more fun learning with this I think.

---

### Post by quietas on 2010-02-05
You're welcome. I've found Zimbra to be one of the easiest, yet feature filled email alternatives. Second only to Exchange for business capabilites and great for personal use as well.

---

### Post by harry_bk on 2010-02-11
Hello everybody, 
I tried to download the Zimbra Collection Suite 6.0 open source in command line under my Ubuntu 8.04 LTS virtual machine(with the wget command), but I am not able to get it. I have the error 404which says not found. I then tried to ping the website but that didn't work. but when I did the same for other websites such as yahoo!, google etc...that worked. But when I get back to windows, the website is accessible and you can download anything you want. Do you know what could be the problem?

---

### Post by quietas on 2010-02-11
Generally I will go to the site in windows ([http://www.zimbra.com/downloads/os-downloads.html](http://www.zimbra.com/downloads/os-downloads.html)) and copy the link locations. Ubuntu 8.04 32bit for example is [http://h.yimg.com/lo/downloads/6.0.5_GA/zcs-6.0.5_GA_2213.UBUNTU8.20100202225756.tgz](http://h.yimg.com/lo/downloads/6.0.5_GA/zcs-6.0.5_GA_2213.UBUNTU8.20100202225756.tgz) and then I SSH to my box and wget that address.

Another option woulld be to install Lynx, Links, or some other command line web browser and download the file that way.

---

### Post by harry_bk on 2010-02-15
thanks a lot Quietas, 
I've installed Zimbra CS 6 open source and it is working fine. I'm just trying to get used to it now. I am also looking for information on how to use it with zimbra desktop without on a local domain. I thank you a lot for the information you gave me. I'll tell you soon about my improvements.

---

### Post by doudoufr on 2010-02-16
Hi all

I've got a question (or two ;))

In the opensource version (community) zimbra is not able to synchronise with pda phone right ?
You have to buy the licence ?

So do you know any other email groupware that will do that ? (exept Zarafa, the one I use for now). I would love to test zimbra, but only if there is a way to synchronize email and contact and calendar with a pda-phone (and for free :-)):P

Thk for the help guyz :popcorn:

---

### Post by quietas on 2010-02-16
You can't use the mobile devide to sync as though is were a native Exchange server without the paid Mobile Module and Network Edition. The cath is that you can sync it via imap for mail directly without contacts or calendar.

The other option if I remember right is to do something like Funmobl (speling?) I think other have made this work. I also played with using GMail to pull the mail and calendar, then syncing Gmail. I know the zimbra forums had some syncing threads (a lot) and many ways to do it there.

The other option is to just get Google Apps for Your Domain. I did this for my personal domain since I can have 25 free users, but my office I use Zimbra with 250 users.

---

### Post by harry_bk on 2010-02-18
Hi everybody,
I've recently installed zimbra CS 6.0 open source under ubuntu 8.04 LTS running on Vmware. Locally my zimbra server is working well and fine. I'm able to send mail to local users and receive mails from them. I'm even to send mails to my yahoo! account although they're sent to spams. It was the first step,because the company where I work wants to buy a public domain name in order to have a website. They also want me to configure zimbra so that it could send and receive internal and external mails. To summarize, my company wants to buy a public domain name like publicDomain.com and wants me to set up zimbra so that they could have zimbra accounts such as [email]myaccount@publicDomain.com[/email] which would be able to send and receive mails whether they are internal or not. Does anyone have a clue on how to proceed ??

---

### Post by graemefaulkner on 2010-02-18
i am also looking to set up a mail server for my new server running ubuntu, im currently running James mail server in windows but am told James isnt very efficient so decided to check out other options.

[]("https://help.ubuntu.com/community/MailServerCourierSpamAssassin?action=fullsearch&context=180&value=linkto%3A%22MailServerCourierSpamAssassin%22")One feature which i require more than any other is support for multiple domains, is this possible with zimbra?

---

### Post by quietas on 2010-02-18
@ Harry_bk: Depending on your company's size, you may want to look a hosted solution. I know there are many providers out there who run Zimbra from what I have seen via the Zimbra forums.

The other option would be to set up a static IP or asmall subnet of IP's via your ISP for your office. Setup your firewall on one IP, put your Zimbra server and web server on another couple contained within your DMZ or on your LAN with port forwarding. DMZ would be best and easiest, plus more secure and separated from internal PC's. A midrange server with VMware or Hyper-V could even run both easily using virtual machines.

Either option is farily easy, it just comes down to what IP's you use and where you point the DNS and MX info.


@ graemefaulkner: You can run multiple domains farily easily, Zimbra has the support built in. Definitely hit up the forums over there and also glance over the feature support on the website.

---

### Post by harry_bk on 2010-02-25
Hi quietas, 
I've come up with another idea. I want to buy a static IP address, and then make my server accessible through a NAT so that it could be accessed by entreprises users whether they are in or outside the company, and I could buy a domain name and set the A and MX to point to my mail server, so that it could send and receive mails from external public domain. Is my idea correct?

---

### Post by windependence on 2010-02-25
The easiest and best way to do this is with a static IP, which are getting cheaper by the minute. If the company has a web site, it has a static IP in most cases. 

You can also use no-ip's mail redirect service for port 25 if you cannot get a static IP. [www.no-ip.com](www.no-ip.com).

-Tim

---

### Post by quietas on 2010-02-25
If you have a single static IP you'll put a router/firewall with NAT and port forwarding on it. The router/firewall will be the point of contact for the outside world, it will have port 25, 80, 443, 993 (secure IMAP, or POP if you use it) forwarded to the mail server. This works fine if you are small company or for home/personal use.

For a bit larger you would by a small subnet and get a range of IP's. In my case I have a 8 host subnet from my ISP. They have a router for the T1's coming in and my firewall it attached to that. There are two of my 8 IPs. I then have my mail server and web server attached to the firewall's DMZ port with my LAN switches attached to the LAN port on the firewall. The DMZ devices each have a public IP while the LAN devices share the firewall's IP using NAT.

In either case you will need to adjust the DNS A name and add an appropriate MX record. Single IP will point at the IP of the firewall. Multiple IPs on a subnet will have the A/MX info pointing at the specific IP of the mail server with added records for any other DMZ devices such as seperate web servers and such. 

If you like the www. mail. ftp. whatever.domain.com can all point at the same IP even. I hope I didn't muddy the waters too much, but ask away, I'm glad to help.

---

### Post by schilders on 2010-03-09
> **HermanAB said:**
> Howdy,
 
The easiest mail server to install is Citadel. It takes about 20 minutes.
 
Installing a postfix/apache/roundcube/dovecot system can easily consume 2 weeks of continuous head banging.
 
There are a bunch of Citadel guides here: 
[http://aeronetworks.ca/linuxhowtos.html](http://aeronetworks.ca/linuxhowtos.html)
 
However, you can just as well dive right in:
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)
 
HermanAB, 
 
I have been trying, to no avail, to configure postfix/dovecot on a client's 64bit cloud server.  He hosts two domains on the server. When we browse to mail.mydomain1.com, the browsers resolves to the other domain on the server mydomain2.com.  Is this a DNS issue?  There are both A and MX records.  The A records are for mydomain1.com and mail.mydomain.com.  The MX records are mail.mydomain1.com and pop3.mydomain1.com.  The CNAME record is [www.mydomain1.com]("http://www.mydomain1.com") .
 
Ultimately, the client needs both domains' email to be managed through the MTA whether it be postfix or Citadel.  How do we set this up?  How does the MTA resolve user1 to mydomain1 instead of mydomain2?  Does Citadel do a better job in this case?
 
Thanks much for your help and guidance.
 
Sid

---

### Post by quietas on 2010-03-09
I tried Citadel when I was looking for our email solution at work. I found I did not like their room based solution. The whole process reminded me of an old BBS moved on to the web (I think it was actually) and it didn't flow well.

Literally Zimbra takes minutes to setup and it is Postfix based if that is a requirement. IMAP support or web based, and much more if you are paying for the Network Edition. I may sound a bit like I'm evangelizing, but I do so because like the best software, it just works. Also, Zimbra is now one for the top 3 email corporate services with Microsoft and IBM according to VMware who just bought them for that reason.

---

### Post by natta8 on 2010-03-10
Greetings all,

could you please help me. I'm new in the Linux sphere and  I don't manage well in that world. I'm trying to install mail server but reading  the instalation tutorials I get more and more confused. ](*,)

Please help me with  answers to a couple of fundamental questions:

 On UBUNTU server 9.10. pages  it sais the mail server is easy to install and that the installation of  POSTFIX and DOVECOT comes with the server. Reading tutorials I understand  something more is needed. 
- I therefore ask you to please adivse me what is  needed for simple mail server.? Virus and spam security isn't needed. I'm trying  to raise the mail server for education purpose only. 
I want to instal mail  server on WMVARE and have mail comunication with XP client on local net, i.e. MX  records are not essential.
Do I have to have MYSQL server for the mail server  and how do maintain, i.e. add, users?

A lot of questions. I hope to  receive at least a couple of answers. [-o<
Thank you in advance!

---

