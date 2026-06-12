---
title: "Mailserver - Citadel - Could use some help!"
date: 2008-01-18
forum: Server Platforms
---

### Post by tonydm on 2008-01-18
Hi gang,

I just set up Citadel in a VM. I can't seem to get things working. Let me give you some vitals to chew on:

Let me first note that I have a functioning mail server on another windows machine.  I just want to better what I have; spam control, speed, reliability, you know...

I have a the following: I own my own domain (mydomain.com), and have a static IP, and Reverse DNS setup with my ISP.

I have several domains that point to ZoneEdits nameservers, including the mydomain.com. I then use Zoneedit to direct traffic to my static ip. for all those domains. The MX records point to mail.mydomain.com which point to my public IP.  I have an apache server set up to host all those domains.

I have a separate server qualified as mail.mydomain.com.

I route all port 25,110, 143, 993, 995, 465 traffic through my firewall/router to the mail server running the Citadel VM (Ubuntu 7.10)

I can login to the Citadel server lan IP 172.16.0.5, VM's IP 172.16.0.8:504 no problem.

I seem to be able to send email within from the server to the server and to any external domain. Been testing with my gmail account.  But I can't get a reply back to my Citadel server.  

My mail client on another machine can't connect.)

I can't telnet to any port mydomain.com 25 for example.  I can't with localhost 25.  I can with 172.16.0.8 25 (VM's IP)

my /etc/hosts file shows
127.0.0.1 localhost
127.0.1.1 mail.mydomain.com

I'm not used to working with VM's.  But there seems to be a problem with the binding.  Yes/No? I wanted to get this up and running to test drive it before I did a full blown install.  Some, I've read, have had no problems getting Citadel to run in a VM.  And indeed I have not either.  I just can get it to exchange email.

Any help would be appreciated.

Tony

ANY help would be great! Thanks All

Tony D.

---

### Post by HermanAB on 2008-01-18
Use a proper IP address.  This not correct:
127.0.1.1 mail.mydomain.com

Most email problems are due to DNS issues.  You must have an A record, PTR record and MX record and it must all resolve properly to this mail server name and IP address.

Cheers,

Herman

---

### Post by tonydm on 2008-01-18
@HermanAB,

Thanks for the reply.  I too thought this was an odd entry.  It was put there by some other script, not entered by me.  Not sure if it should be removed or what would be the proper entry.  As I mentioned, I have a working email server.  So I know my ZoneEdit A Records, and MX Records are correct.  My Reverse DNS is setup at my ISP and I confirmed that it is correct.  The problem lies on the mail server and the VM connection I believe.

Tony D.

---

### Post by HermanAB on 2008-01-18
Well, if everything is correct and it doesn't work, then something is wrong, so don't accept anything at face value - test it.

Use telnet to test the server connectivity and get a better idea of where things are broken:
$ telnet mail.server.com 25
You should get a banner.

Use dig and nslookup to verify the DNS entries.  Test all - forward, reverse and MX.

Cheers,

H.

---

### Post by tonydm on 2008-01-19
@HermanAB,

I appreciate the words of wisdom.  And all things being equal, I would agree.  Something is broke.  But the problem does not lie out on the internet with my isp, registar, or zoneedit.  But to be fair to myself, and your suggestion, I took your advice and did a dig and found all to be working correctly.

I believe the problem is that there is a break between the VM and the actual real OS.  Somehow traffic is not getting to the VM.  If I direct port traffic on my router to my "working" mail server, I can telnet in, do all the mail activities I want on POP/IMAP, etc.  Directing port traffic back to my test Ubuntu mail server running the Citadel VM, everything goes dead.  Oh, except that I can send mail out.  But I cannot telnet into the server from say telnet mydomain.com 25.  But I can into the VM by explicitly pointing to the VM IP address, ie: telnet 172.16.0.8 25.  So again, I believe the problem to ly at my server.  I'm not experienced much with bind.  But somehow I need to route traffic locally.

Tony

---

### Post by tonydm on 2008-01-19
Ok, a dumped the VM, Killed the VM Server and installed Citadel directly onto my server.  I can now telnet into the server from another location, ie telnet mydomain.com 25.  I can, as before, send out an email.  But no incoming mail is received.  I have gotten an email client off network to login and get the IMAP folders and updates.  It too can send mail.  But nothing comes in.  When I said I can telnet I can on all ports, 25, 110, 465, 993, 995.  Heres some info for someone who might spot something:

server IP: 172.16.0.6

tonydm@mail:~$ hostname
mail

tonydm@mail:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local         *               255.255.0.0     U     1000   0        0 eth0
172.16.0.0      *               255.255.0.0     U     0      0        0 eth0
default         172.16.0.2      0.0.0.0         UG    100    0        0 eth0

tonydm@mail:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:5B:3B:4A:B8 
          inet addr:172.16.0.6  Bcast:172.16.255.255
          Mask:255.255.0.0
          inet6 addr: fe80::211:5bff:fe3b:4ab8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:631760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:342690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:796489017 (759.5 MB)  TX bytes:31783386 (30.3 MB)
          Interrupt:21 Base address:0xe000

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3849410 (3.6 MB)  TX bytes:3849410 (3.6 MB)

Any more ideas?  Thanks guys!!

Tony

---

### Post by HermanAB on 2008-01-19
OK, your hostname must be a FQDN: mail.something.com and it must be in the DNS.

Fix the hostname and reboot.

If you tell me what your FQDN is then I can test it from here.  "172.16.0.6" is not a public routable address so that doesn't help and "mydomain.com" doesn't help either.  You got to give me the real information.

Cheers,

H.

---

### Post by tonydm on 2008-01-19
I changed my hostname to:

tonydm@mail:~$ hostname
mail.netald.com

Would you be speaking of the DNS on my mail server or the Public DNS servers? I´m in the public DNS for sure.  If I need to add an entry to my local server&#347; DNS I can do that.  Just need a little nudge.  Thanks!

Tony

---

### Post by HermanAB on 2008-01-19
OK, lemme do a DNS test:
$ dig mail.netald.com
mail.netald.com.        7200    IN      A       65.39.83.102

$ nslookup 65.39.83.102
102.83.39.65.in-addr.arpa       name = mail.netald.com.

$ dig netald.com MX
netald.com.             7200    IN      MX      0 mail.netald.com.
mail.netald.com.        6888    IN      A       65.39.83.102

The above confirms that your DNS is definitely configured correctly.

So, let's try telnet:
$ telnet mail.netald.com 25
Trying 65.39.83.102...
Connected to mail.netald.com (65.39.83.102).
Escape character is '^]'.
220 mail.netald.com ESMTP Citadel server ready.

Cool, Citadel answers.  Things are probably working now.

If you send me a private message with your email address, then I can send you a test message.

Cheers,

Herman

---

### Post by tonydm on 2008-01-19
Hey Herman,

Thanks bud.  But nothing has changed on my end.  But figure this out.  I´ve been testing with my gmail account.  Nothing comes back from it.  But I send a test email from the Zoneedit SMTP Uitlity and I get the email.  What gives?  I´ll send you an email address to futther test.  Thanks for all your help!!

Tony D.

---

### Post by HermanAB on 2008-01-19
I wonder how long ago you configured the DNS.  Maybe Google still doesn't have it.  It can take a few days to propagate.

BTW, I sent a message to [email]postmaster@netald.com[/email] and it went without a complaint.

---

### Post by tonydm on 2008-01-19
My other mail server has been up for a year.  The A, PTR, MX Records have been configured for as long.  I think they may have seen my test email as spam or something.  Did you get my email and then reply?  If you did, I didn´t get the response.

Tony

---

### Post by HermanAB on 2008-01-19
Uhmmm, yawn, just got up - sent a response to your rmessage of 8h12.  It went out without error.

Cheers,

H.

---

### Post by tonydm on 2008-01-20
Interesting, emails (created or replied to) have been trickling in all day from gmail.

Tony

---

### Post by HermanAB on 2008-01-20
Cool, so it is all working now.  My guess is that Gmail finally updated their DNS and only now know how to reach you.

---

