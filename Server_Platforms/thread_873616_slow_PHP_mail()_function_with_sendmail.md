---
title: "slow PHP mail() function with sendmail"
date: 2008-07-29
forum: Server Platforms
---

### Post by zmartant on 2008-07-29
I was having some issues with SendMail, as it took close to 45 seconds to send an email.  I viewed the mail log located at /var/log and then viewed the mail.log (cat mail.log |tail).  I noticed that there was a delay in my emails being sent out (at least 45 seconds) due to relay.  I searched and searched for over two days, and all the post that I read noted in changing the php.ini config and other configurations, but the issue continued.  I was going over my servers configurations, and noticed the following under /etc/resolv.conf:
search MyDomain
nameserver 192.168.1.1

I changed the above information to reflect my current configurations:
search MyDomain.com
nameserver my actual name server and not my router/gateway, as I am not behind a router, but I was when I configured the server
nameserver my backup name server

When I tested my sendmail script again, it fired off like a charm!

I was trying to post this on the original post with the same title, but for some reason, I got only read access to that post. :(

I hope this will help someone resolve their issue with the delay with sendmail, as the issue was very frustrating in figuring out what was causing the long delay in sending my emails.

Cheers,
Zmartant

---

### Post by Gigcsjcx on 2009-11-11
up:popcorn:

---

### Post by nadeem37 on 2009-12-24
> **zmartant said:**
> I was having some issues with SendMail, as it took close to 45 seconds to send an email.  I viewed the mail log located at /var/log and then viewed the mail.log (cat mail.log |tail).  I noticed that there was a delay in my emails being sent out (at least 45 seconds) due to relay.  I searched and searched for over two days, and all the post that I read noted in changing the php.ini config and other configurations, but the issue continued.  I was going over my servers configurations, and noticed the following under /etc/resolv.conf:
search MyDomain
nameserver 192.168.1.1

I changed the above information to reflect my current configurations:
search MyDomain.com
nameserver my actual name server and not my router/gateway, as I am not behind a router, but I was when I configured the server
nameserver my backup name server

When I tested my sendmail script again, it fired off like a charm!

I was trying to post this on the original post with the same title, but for some reason, I got only read access to that post. :(

I hope this will help someone resolve their issue with the delay with sendmail, as the issue was very frustrating in figuring out what was causing the long delay in sending my emails.

Cheers,
Zmartant
Thanks very much for your support, but i changed my domain search in the /etc/resolv.conf file and still getting delay to send mail. My compueter name is lamp and my dns search path is localdomain 
 
i changed it to localdomain.com but then also it is taking time to send mail.

can you just help me out..........

I am searching for the help on internet from last 5 days........

---

### Post by HighCommander540 on 2009-12-24
> **nadeem37 said:**
> Thanks very much for your support, but i changed my domain search in the /etc/resolv.conf file and still getting delay to send mail. My compueter name is lamp and my dns search path is localdomain 
 
i changed it to localdomain.com but then also it is taking time to send mail.

can you just help me out..........

I am searching for the help on internet from last 5 days........

That is not what he changed to make it go faster. He got rid of the 192.168.1.1, because what happens it is checks your router for the domain name, which takes forever. Just edit your file to only have the DNS server's your ISP provides and not your router as one of the DNS lookups.

The MyDomain.com, has nothing to do with it actually.

---

### Post by nadeem37 on 2009-12-25
> **HighCommander540 said:**
> That is not what he changed to make it go faster. He got rid of the 192.168.1.1, because what happens it is checks your router for the domain name, which takes forever. Just edit your file to only have the DNS server's your ISP provides and not your router as one of the DNS lookups.

The MyDomain.com, has nothing to do with it actually.
Thanks for your prompt reply sir.

I have given ip and DNS to my system which is i got from the ISP. I have the static ip with me. and given the same which i have got from the ISP . but then alos mail is taking time to send.

can you just help me out.....

---

### Post by HighCommander540 on 2009-12-26
> **nadeem37 said:**
> Thanks for your prompt reply sir.

I have given ip and DNS to my system which is i got from the ISP. I have the static ip with me. and given the same which i have got from the ISP . but then alos mail is taking time to send.

can you just help me out.....

This is what your resolv.conf file needs to look like:

```

search MyDomain
nameserver IP
nameserver IP

```

MyDomain: Is the domain that your ISP provides. If you are using a router your router can tell you this. Otherwise if it is a direct connection you need to use DHCP to find out what this is.

Namesver IP: This needs to be your DNS servers. Don't have anything else in the file. And if you are using a router make sure to take out the IP that looks like this 192.168.x.x.

---

### Post by zmartant on 2010-01-17
> **nadeem37 said:**
> Thanks for your prompt reply sir.

I have given ip and DNS to my system which is i got from the ISP. I have the static ip with me. and given the same which i have got from the ISP . but then alos mail is taking time to send.

can you just help me out.....

Hi nadeem37,

I hope that you have sorted this out.  What HighCommander540 has noted is correct!  When you stated that mail is taking time to send, your mail does get sent, right?  If this is the issue, again, what HighCommander540 has noted could be the solution.  If your mail does not go out, then that is another topic, as the issue might be due to your ISP blocking DCHP type of IPs to sent out mail or just blocking SMTP port 25 on their network.

If you still need further assistance with this issue, please provide us with your resolv.conf and also your send mail log (change any identifying information).

Well, I hope that you got this issue sorted out, as I see you have not posted for three weeks.  

Best wishes,
Zmartant

---

### Post by spanda on 2010-04-07
Hi Z
 
Thanks a ton. We were struggling to fix this issue, before I came across this post. Really appreciate it.

---

