---
title: "Can't setup Zimbra in sub-domain :("
date: 2013-05-09
forum: Server Platforms
---

### Post by tommy smith on 2013-05-09
Hi, I had testing setup zimbra mail in my vps with a real domain and successful. In that domain I setup host :
127.0.0.1....
{ip}   mail.domain.com   mail

Hostname : mail.domain.com 

And in domain control I point both A Record for @ and mail into same ip, so all thing ok.

However, when I build in another domain that I want to build zimbra in sub-domain and do all same thing above, but in domain control I just use @ for website, and point mail1.domain.com in vps zimbra (that domain had mail for google app), but zimbra not run, I don't understand what wrong, If zimbra need both @ and sub for using, so how can I build website and mail same domain :confused:

---

### Post by volkswagner on 2013-05-09
I'm having a hard time understanding your scenario.

Do you have one Zimbra server which you hope to host mail for several domains?  Will websites be hosted on different server while you host mail on one Zimbra server?

You can have the following:
VPS1 = mail.domain.com xxx.xxx.xx1 ; which can host website domain.com and mail for any domain.
vps2 = domain2.com xxx.xxx.xx5 ; which can host websites domain2.com, sub.domain2.com and have mail hosted at mail.domain.com
       vp2 will have a records @ pointing to xxx.xxx.xx5 and mx records pointing at mail.domain.com
       if you want domain2.com to have webmail you can create an a record mail.domain2.com pointed at xxx.xxx.xx1

---

### Post by tommy smith on 2013-05-09
So sorry, my scenario not clear.

Firstly, I have domain1.com with configure : A Record : @ & mail | MX mail : point to vps 1.

Hostname : ip-vps1 mail.domain1.com mail
Host : mail.domain1.com

=> I build Zimbra running ok.

But my friend don't want to use new domain, he want to use his domain that built website and mail google apps before, so I said he point his domain : A Record mail1.domain2.com , and MX mail1 point to vps 2.

Hostname : ip-vps2 mail1.domain2.com mail1
Host : mail1.domain2.com

I build zimbra and feel confused with option "Change domain name" by DNS MX maybe error, I tried build 2 times domain2.com and later mail1.domain2.com but nothing working :(

If I build a Mail Server by other services such as Citadel, Iredmail...so all ok, except zimbra quit strange.

---

### Post by darkod on 2013-05-09
So, you don't want to use the same Zimbra server, you want to make a new one for your friend? If the new Zimbra is not working you have some error either in configuring it, or the FQDN hostname of the VPS2, etc. Otherwise it should work as long as the MX record for domain2.com is pointed correctly.

A records point to public IPs.
MX records point to a hostname.

For example, if the VPS2 server of your friend has the public IP 123.45.67.89 then in the DNS manager you set:
A record @ pointing to 123.45.67.89
A record mail pointing to 123.45.67.89
CNAME alias www pointing to @
MX record pointing to mail.domain2.com.

This is under the assumption both the websites and the mail server (Zimbra) are on the same machine, his VPS2.

You can check whether your dns works correctly with nslookup and similar tools. If the dns is fine, you have an issue with the Zimbra server, a firewall on the VPS2, or something similar...

On the other hand, if you want his domain2.com to use your Zimbra on VPS1, the dns configuration for domain2.com should be different from the above.

---

### Post by tommy smith on 2013-05-09
Thanks Darkod for reply.

Yes, my friend don't mind if using same zimbra with me, but I want to build for him a new one.

However, the problem is if I use a clear domain such as you said:

 A record @, mail and Cname www point all to ip 1.2.3.4, and MX mail point to mail.domain.com, so all fine, zimbra running ok.

But he want to use his domain that :

A record @, mail and Cname www point all to ip 1.2.3.4 for his website, and he has already MX mail point to mail.domain2.com running mail google apps.

That make me created new sub : mail1.domain2.com with A record mail1 point to my vps 5.6.7.8 and another MX mail1 point to mail1.domain2.com. But when I build zimbra, it's not run, I'm not sure that problem by conflict with MX google apps or zimbra need all @, sub and MX point same ip or something else !!!

---

### Post by darkod on 2013-05-09
No, zimbra doesn't care about the A and www records. The dns server is doing the resolving where to send the mail according to the MX record. As long as you have a valid MX record pointing to the Zimbra server, it should work.
But I don't know if the mail google apps can create a conflict, maybe that's the problem. Also, the MX records should have different priority, for example 10 and 20. You can't have two with the same priority. And the mail always tried to get delivered to the primary MX first.
I don't know what's the point of having two different mail servers since the mail will be sent only to the primary as far as I know. If they are identical servers that get syncronized, OK, I understand. But different mail servers, google apps vs Zimbra, I have no idea if it would work and how.

Also, the problem might be that you created another mail1.domain2.com host pointing to your VPS. You don't do it like that. Delete this mail1 A record, and in the domain2.com make the second MX point to mail.domain1.com (your mail host). It's allowed to use hosts from different domains, as long as they exist. It doesn't need to be host on domain2.com.

Maybe that's what zimbra is complaining about, if the check can show that both mail.domain1.com and mail1.domain2.com are same server.

Just use your mail host in his domain dns configuration.

---

### Post by tommy smith on 2013-05-10
Thanks Darkod.

I had testing in mydomain.com which I have already a Zimbra mail, I build mail1.mydomain.com with A mail1 and MX mail1 different mail =>

 If I send to [email]user@mydomain.com[/email], so email will transfer both 2 mailbox @mail and @mail1, but If I send to @mail1, so @mail with not receive.

If I change mx same priority mail & mail1 = 10, so sometime mail or mail1 will not receive.

Afterthat, I drop A record mail and MX mail, just keep mail1 and mx mail1, and rebuild zimbra, so I send to user@mail1 for send and receive ok. 

However, I don't want to use mail address [email]user@mail1.mydomain.com[/email], I want to use [email]user@mydomain.com[/email] that transfer to @mail1.mydomain.com, but I don't know why it's not working event I had deleted mail Record & MX (With my old mail record and mx, I can send to user@mydomain normal). I don't know what problem, just change mail to mail1 and rebuild samething. Oh, just have one different is @ record point to old ip mail zimbra - That's mean :

Mail : @ & Mail : same Ip 1.2.3.4 | MX : mail.mydomain.com => People can send [email]user@mydomain.com[/email] without [email]user@mail.mydomain.com[/email]

Mail1: @ -> ip 1.2.3.4 | Mail1 -> ip 5.6.7.8 | MX: mail1.mydomain.com => I can not send [email]user@mydomain.com[/email], it's not working and point to [email]user@mail1.mydomain.com[/email] 

How can I resolve it ?

Mai

---

### Post by darkod on 2013-05-10
I didn't understand. You don't send mail to [email]user@mail1.domain.com[/email]. If your domain is domain.com and it's a public, registered domain, the email addresses are [email]user@domain.com[/email].
Don't confuse the MX record with that. The MX record is assembled from the host (machine) name and the domain. So that's why it turns out as mail1.domain.com for example. mail1 is the machine (host A) name, it has nothing to do with the domain itself, and is not included in the email address after the @.

If you want the same Zimbra server to receive mail for two different domains, domain1.com and domain2.com, you have to configure that in Zimbra otherwise it will refuse the mails for the second domain. This could be the issue since you first set up Zimbra only for your domain, right? You need to tell it that it should accept mails for another domain too.

And in that case, if the Zimbra server is the same, the MX records for both domains will be identical: mail.domain1.com. I don't know why you are mentioning mail1.mydomain.com again.

Or maybe I misunderstood it again. Do you want the same Zimbra server to receive mails for both your domain and your friends domain, or not?

---

### Post by tommy smith on 2013-05-10
I don't want use same Zimbra for both my domain and his domain, and now I just testing Zimbra in mydomain with different MX mail and mail1 to created a scenario such as his server, use domain for both mail google apps and want me build new Zimbra mail1 for him.

I want to use [email]user@mydomain.com[/email] cuz he said he don't want to use domain [email]user@mail1.domain.com[/email], it's so ugly in business. He accept to deleted his old google apps mail to use Zimbra, but I need to make sure zimbra will working so I must build and mail1 for testing.

So I created a scenario in mydomain.com that build one more mail1.mydomain.com running same time with mail.mydomain.com. I had testing such as I said above, if not same MX, it's running quite ok but some time stuck with same MX.

And now I deleted mail.mydomain.com, and want to use mail1 to receive mail, and the problem is here : 

- If I use @ and mail same ip, in Zimbra Control it has already {user} @mydomain.com

- If I use @ and mail1 different ip, in Zimbra Control it has {user} @mail1.mydomain.com , and I had tried to add one domain @mydomain.com with under mail serve mail1.mydomain.com, and testing created acc [email]user@mydomain.com[/email] & sending to yahoo, and yahoo receive ok with [email]user@mydomain.com[/email] but can't rely or send mail to that [email]user@mydomain.com[/email] !!!

It's make me confuse, why zimbra don't use default @mydomain.com with mail1 ??? because I had deleted mail, maybe zimbra need @ and mail same ip. However, I stuck in receive mail after add domain @mydomain.com under server mail1 like I said above !!!

---

### Post by darkod on 2013-05-10
I think you are setting up zimbra wrong. Once again, the domain is ONLY mydomain.com, not mail1.mydomain.com or mail.mydomain.com. That the mail server Fully Qualified Domain Name, not the email domain.

When you set up zimbra, it seems you are telling it to receive mail for the domain mail1.mydomain.com (this makes it a subdomain then). Why? You need to tell zimbra to receive mail for mydomain.com. When it asks you which domain to receive mail for, is that what you answer: mydomain.com?

Mail servers do not depend on the main @ record for the domain, or the www record. They are only interested in the MX record. But the MX record must be a real host, not one the doesn't exist. So, if your friend domain is mydomain.com in the dns manager you need to have A host named 'mail' pointing to the IP.
Then in MX record you have mail.mydomain.com. with priority 10 for example.

That tells other mail servers where to send mails for mydomain.com.

Sending mails from your new server is not a proof of anything. Receiving mails is important, only that shows that everything is set up correctly. Sending mails works even from private servers with private domains (local) that can never receive mails. Sending mail to yahoo means nothing.

---

### Post by darkod on 2013-05-10
One more thing that is very important too. I think you are getting confused and setting up zimbra for subdomain for a test, because you want his main mail to work until you set up the new server. No problem.

Set up zimbra with his real domain name, not any subdomain. That's what he wants anyway, to send mails as [email]user@mydomain.com[/email] not [email]user@mail.mydomain.com[/email]. This will not affect his current mail receiving. Until you change the MX record of the domain, the system currently in place will keep working.
You can do tests on zimbra before changing the MX record to make sure it's working. For example sending mail from it. Testing the receiving is little tricky, but even if you temporarily set MX record with smaller priority that should not interrupt the current working system. You can do a short test like that.

The most important thing is to set up zimbra to handle mails for the real domain, don't invent subdomains because after that it will keep receiving mails for that subdomain and refuse the others.

---

### Post by tommy smith on 2013-05-10
Thanks Darkod for rely,

Yes, I read your help and understand that FQDN and mail domain not related. And I also want to tell zimbra that point into mydomain.com, but I'm stuck in the line when Zimbra ask me MX config (I'm building Zimbra in the guide here) : [http://ubuntuforums.org/showthread.php?t=1866784](http://ubuntuforums.org/showthread.php?t=1866784)

> 
DNS ERROR resolving MX for mail.domain.com
It is suggested that the domain name have an MX record configured in DNS
Change domain name? [Yes]  **[COLOR=Red]Yes[/COLOR]**
Create domain: [mail.domain.com]   **[COLOR=Red]domain.com[/COLOR]**
MX: mail.domain.com (192.168.0.10)

If I'm using all record same ip like guide above, so all thing ok, and zimbra using @domain.com for default. But the problem after I use @ point to ip 1.2.3.4 for vps building website, and mail1 point to ip 5.6.7.8 for Zimbra, and if I adding mail for google mail apps so it'll same scenario in my friend domain. Zimbra don't ask me change domain, it's auto recognize and get MX for mail1.mydomain.com.

 I think it's happen cuz mydomain.com point to other IP for site & different ip mail1 Zimbra - But I also thinks like you said, it's should not happen cuz in this domain, even different ip, but only have one MX, and I should using @mydomain.com not @mail1.mydomain.com..

He agree that using only Zimbra mail, so I will not worry about conflict MX, but still stuck in @ mail user. So headache..hixxx

---

### Post by darkod on 2013-05-10
You are still putting mail.domain.com as domain. Look at the message. It says it can't resolve the MX record for mail.domain.com not for domain.com. If i understand it right, you entered it wrongly. Put the domain as domain.com, it's asking for the domain and will look for the MX record itself.

The way you entered it, it looks for MX record of the domain mail.domain.com which doesn't exist so it returns an error.

And the MX can't be a local IP. 192.168.0.10 is a local IP. But that's irrelevant, just use the correct domain from the start. Then it shouldn't even ask you to change the domain name. You see how in the Create domain it has default value [mail.domain.com]??? Because you entred that as a domain somewhere earlier. What you needed to enter is domain.com.

Also that guide is old but it should still apply. On the zimbra website there might be a newer guide or better install procedure.

PPS. Also that tutorial installs bind9 to make dns nameserver on the machine. You don't need that, you simply need a mail server and the registrar control panel will do the dns. Do just what you need, don't complicate your life with making nameservers that you don't need. It looks like you might be failing at the nameserver setup, double check the configuration.

---

### Post by tommy smith on 2013-05-10
Hixx...No, Zimbra don't ask me what domain for MX, it's auto recoginze and continue process, I had rebuild Zimbra again and copy what it said :

> 
Setting defaults...     

MX: mail1.wecarehn.com (198.199.109.144)

        Interface: 198.199.109.144
        Interface: 127.0.0.1
        Interface: ::1
                198.199.109.144
done.


It's not notice me error MX, it's auto recognize MX in mail1.wecarehn.com and continue running...I'm not have change to chance it.

And this is my configure server :

> 
A    @     198.199.101.136 => Site
A    mail1 198.199.109.144 => Zimbra
MX    mail1 mail1.wecarehn.com


And configure in my vps mail1 :

> 
Hosts :

127.0.0.1        localhost.localdomain    localhost
198.199.109.144    mail1.wecarehn.com    mail1

Hostname:

mail1.wecarehn.com

I'm building same guide. I'm feeling so silly but don't know what wrong with my setting :(

---

### Post by darkod on 2013-05-10
It all looks good. Only the dns manager settings might be little different, but that depends on the registrar. For example in GoDaddy the MX record is usually:
MX @ 10 mail1.wecarehn.com

The mail1 in between might be wrong. Compare it with the dns settings of your domain. Is it the same?

---

### Post by tommy smith on 2013-05-11
Darkod, thanks you so much, I'm so appreciate your help very much :D

It's work, I'm using domain godaddy, and change like you said: MX mail2 10 mail2.wecarehn.com => MX @ 10 mail2.wecarehn.com, then rebuild zimbra and it's success, I can use [email]user@wecarehn.com[/email] and it's send to [email]user@mail2.wecarehn.com[/email].

And now, I had build one more Zimbra mail1 and same MX with mail2 for load balancing, I want to sysn 2 Zimbra with using same database, user, mailbox .etc... I want to use same LDAP for user and backup database such as iSCSI in a vps 3 for 2 Zimbra. Do you think it's possible and you can share me any good ideas, I'm still don't know where mailbox and database of Zimbra saving, so LDAP and iSCSI just a recommend of my friend but I'm still not find a helpful document or guide, could you help me some advices Darkod :)

---

### Post by darkod on 2013-05-11
Unfortunately I haven't worked with zimbra much. Their website might have some info how to set up load balancing or synced servers. Also, if these servers are VPSs and not physical servers in the same local network, I guess setting up VPN connection between them is the best choice. You can have a third server for LDAP in the same VPN and all their communication can go internally through the VPN network. That will simulate local network.

But these are general ideas, I don't have any tutorials for that.

---

### Post by tommy smith on 2013-05-12
Thanks, I'll consider your idea, I also found some document about scrip sysn servers but not try yet. Actually, the first mail server I'm building use Postfix, Courier, Mysql with postfixadmin and Roundcube, I also tried Iredmail but when testing Zimbra it's quite easy to setup more than other and have quite many apps available. However, some friends seem not favor Zimbra much, cuz they think it's look like an auto apps such as Windows and hard to control deeper than setup separate module like Postfix + Courier...above. What do you think about that idea, Darkod ? If you build a mail server for company, what kind of mail server or services you will use ?

Hi, anyway, by someone so enthusiasm like you Darkod, It's make linux still living :D

---

### Post by darkod on 2013-05-12
Selecting a mail server is not an easy question. I don't have much free time right now, but in about a month I am getting ready to do some test installations myself, and see how these programs work:
OpenChange
iRedMail
Zimbra

The OpenChage project should be very similar to Exchange, which might be what most people are looking for in a mail server especially if they are coming from windows background.

The iRedMail and Zimbra seem to use OpenLDAP (I'm not sure about Zimbra), which on the other hand might be much better for someone with linux background.

One option that I plan to try is Samba4 active directory (very similar to managing windows AD) and try to make postfix and dovecot to authenticate against it. Since it's LDAP compatible and they can authenticate against ldap, I guess there should be no issues. I only have to make it work because I don't know that much about mail servers... :)

---

### Post by LHammonds on 2013-05-13
My company is primarily Windows and I did some research over a year ago on what we can migrate to from Microsoft Exchange.  I selected Zimbra and created [this thread]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=195") which documents how I installed Zimbra OSE 7.20 on Ubuntu 10.04 LTS for the purpose of migrating from MS Exchange.

We have not done so yet due to other projects taking priority but I will be looking into it again soon with Zimbra 8 and Ubuntu 12.04 LTS.

LHammonds

---

