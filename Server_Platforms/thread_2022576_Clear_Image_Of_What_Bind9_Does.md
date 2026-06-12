---
title: "Clear Image Of What Bind9 Does"
date: 2012-07-11
forum: Server Platforms
---

### Post by pijamaz on 2012-07-11
Hi,
I have purchased this VPS which runs Ubuntu 11.10 and  Domain say "domain.com" with a registrar, both VPS and Domain are from different companies.

To make and use my own name servers and mail exchange records (MX) , inside my domain control panel I've created sub-domains as "ns1.domain.com","ns2.domain.com" (Glue Records), "mx0.domain.com" , "mx1.domain.com". they all point to my VPS IP address and I use them for my "domain.com" as  DNS Name server and MX record settings ( I set these inside my domain control panel).

 I'm kind of new to VPS configuration and customization and I want to make sure that my understanding of related technologies before using them is correct. so excuse me for amateur questions in advance.

in various tutorials I've seen that in a step they guide me through installing Bind9 on my Ubuntu VPS. And in the configuration process in some files (related to bind9) I have to use information above (ns1.domain.com,ns2.domain.com,...).
this is kind of confusing for me that what bind9 does that my configuration inside my domain registrar control panel does not? I mean is it really necessary to use bind9 when I'm using such glue records? and how does bind9 help the DNS process? 

In some sites that they provide tools for testing your domain dns configuration such as [http://www.dnssy.com/ ]("http://www.dnssy.com/")
when I tested my domain I face errors such as "your dns name server ns1.domain.com and ns2.domain.com does not return A-Record", Does Bind9 help me define A-records to solve this issue?(when I'm not a domain registrar and I run my own DNS server using bind9)

Sorry because I've a lot of confusing information and questions if someone can help me with achieving a better understanding of bind9 functionality. 

thanks for your time.

---

### Post by darkod on 2012-07-11
I am not too much in depth with bind, but if your VPS has a static public IP, it's enough to work with the control panel of your domain provider.

Their control panel will do the DNS service. That's exactly what DNS is, translation from domain.com into public IP.

So when anyone uses domain.com, your records pointing to your VPS IP are enough to send the packet there. Your VPS webserver/mailserver accepts it, replies, case closed.

There is rarely a need to run your own DNS servers (bind), and in this case it seems to me you don't need to.

EDIT PS: If you created ns1 and ns2 for dns service, you can delete them. As discussed above, I don't think you will need that. As for mx0 and mx1, you do need records for the mail server, but there is no point having two recored pointing to the same server. If it's down, it's down. :)

So, leave just the mx0 A-record (or depending how it's called in your provider) pointing to the VPS IP. And then you create the MX record for your domain to be mx0.domain.com (for mail it doesn't work with IP directly, hence you need to have the mx0.domain.com). But note, this is NOT a sub-domain we are talking about. It's just a record. You should have this option in the control panel, somewhere in DNS.

---

### Post by pijamaz on 2012-07-11
Thanks for your reply;
Excuse me for not mentioning this:
I have 3 Ip addresses on my VPS control panel which is SolusVM.
one public Ipv4 and two Ipv6. I currently use the public IPv4 address for the main domain.com that correctly points to my VPS but as I read some documentations on my domain registrar describing how to use your own name servers, they advised  using glue records for this matter and I kind of liked the idea using my own name servers therefore I created ns1.domain.com and ns2.domain.com which point to my VPS using IPv6 addresses provided in my solusVM control panel. 
I rather not use any control panel such as koloxo because of some performance issues, and inside SolusVM I couldn't find anything related to entring MX records or such. 
how about this? if I want to use my own name servers do I need to install bind? or not?
take look at here, this is right thing to do or not?
[http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/]("http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/")

---

### Post by darkod on 2012-07-11
Well, if you are using your own nameservers, then yes, you will need to install and configure bind. I'm not much help there I'm afraid, I've never configured bind.

The MX records would usually be with your registrar, not Solus. Of course, with your own nameservers you can also make MX records in the bind settings too. That's why I think you can't find anything about MX at Solus.

If you set at the registrar to use your own nameservers, I think the control is passed onto them, which means all A records, www, MX, etc will be in your bind configuration.

EDIT PS: That dns tutorial looks simple and easy. As you can see, in the cachecluster.com.db he is setting up the A records we were talking about, pointing to the public IP:
ns1 IN A xxx.xxx.xxx.xxx
 ns2 IN A xxx.xxx.xxx.xxx
 [COLOR=Red]mail[/COLOR] IN A xxx.xxx.xxx.xxx

On the other hand, the MX record is set up to point to mail.cachecluster.com, which in turn is pointing to the IP through the mail A records set:
cachecluster.com. IN [COLOR=Red]MX[/COLOR] 10 [COLOR=Red]mail[/COLOR].cachecluster.com.

It does look like a simple procedure to get you going.

---

### Post by SeijiSensei on 2012-07-11
I **strongly** recommend you let the domain provider handle your DNS.  It shouldn't be hard to figure out how to add the appropriate records.  All you'll need is one or more A records that point hostnames to your virtual server, and one or more MX records to point to any mail server(s) you maintain.  That's a lot easier than maintaining your own DNS.

Also if you maintain your own DNS you'll need to have two servers running BIND, a primary and a backup, with each configured properly to have changes on the primary get transferred to the secondary.  Do you have a second server?  See [RFC 1912](http://www.ietf.org/rfc/rfc1912.txt) for details.

---

