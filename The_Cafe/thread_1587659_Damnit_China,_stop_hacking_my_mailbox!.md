---
title: "Damnit China, stop hacking my mailbox!"
date: 2010-10-03
forum: The Cafe
---

### Post by Metallion on 2010-10-03
Woke up this morning to find an e-mail titled "beautiful" urging me to open up a file pretty.rar. What concerned me most is that this message came from one of my own mail accounts. I immediately changed my password and secret question (which wasn't easy to guess, nor was it available on any pages like facebook and such) but I still have a couple of questions.

18 hours ago my account got a pop3 request from 174.139.90.92. A whois on that gave me these results.
```
network:Org-Name:Luo, Wen
network:Street-Address:Room 701 Futian Building Shaoshan north Road
network:City:Changsha
network:State:China
network:Postal-Code:410005
```

Then 2 hours later, my account was accessed through a browser on 58.17.18.121. Whois gave me this:
```
person:         ChinaUnicom Hostmaster
nic-hdl:        CH1302-AP
e-mail:         abuse@chinaunicom.cn
address:        No.21,Jin-Rong Street
address:        Beijing,100140
address:        P.R.China
```

So that last one obviously is the internet provider of the perpetrator. Would be a good idea to report this to them and send them the ip?

Also that POP3 request two hours before the unauthorized access worries me. Could there be a flaw in POP3 that allowed him to hack my password? I personally doubt it but I still disabled POP3 on my account just to be sure.

---

### Post by CharlesA on 2010-10-03
Report it to the ISP.

Not much else you can do outside of changing yer password.

---

### Post by kevin11951 on 2010-10-03
> **Metallion said:**
> Woke up this morning to find an e-mail titled "beautiful" urging me to open up a file pretty.rar. What concerned me most is that this message came from one of my own mail accounts. I immediately changed my password and secret question (which wasn't easy to guess, nor was it available on any pages like facebook and such) but I still have a couple of questions.

18 hours ago my account got a pop3 request from 174.139.90.92. A whois on that gave me these results.
```
network:Org-Name:Luo, Wen
network:Street-Address:Room 701 Futian Building Shaoshan north Road
network:City:Changsha
network:State:China
network:Postal-Code:410005
```

Then 2 hours later, my account was accessed through a browser on 58.17.18.121. Whois gave me this:
```
person:         ChinaUnicom Hostmaster
nic-hdl:        CH1302-AP
e-mail:         abuse@chinaunicom.cn
address:        No.21,Jin-Rong Street
address:        Beijing,100140
address:        P.R.China
```

So that last one obviously is the internet provider of the perpetrator. Would be a good idea to report this to them and send them the ip?

Also that POP3 request two hours before the unauthorized access worries me. Could there be a flaw in POP3 that allowed him to hack my password? I personally doubt it but I still disabled POP3 on my account just to be sure.


You should know, you can spoof a persons email in the "From:" line without actually using their account to send the email...  In fact a lot of products will do it legitimately (eg. RAID cards).

If you have no other "proof" than the "From:" line, then I wouldn't worry about hacking...

---

### Post by Metallion on 2010-10-03
> **kevin11951 said:**
> You should know, you can spoof a persons email in the "From:" line without actually using their account to send the email...  In fact a lot of products will do it legitimately (eg. RAID cards).

If you have no other "proof" than the "From:" line, then I wouldn't worry about hacking...

It's a gmail account and google's logs clearly show that he accessed it through a browser. Also he sent the mail to some of my contacts. So I'm pretty sure it's not just a spoof.

---

### Post by Troublegum on 2010-10-03
I'm sure he does run his own mail server - he said its a gmail account. 

Very worrying indeed. Maybe you've accessed your webmail from an infected PC someplace else (internet cafe, public pc, a friend)?

---

### Post by TNT1 on 2010-10-04
I had a gmail account hacked last week. Google log also showed an ip address from china as being the source. I couldn't even access the account, but google were very helpful and very quick to assist me in getting the account back.

---

### Post by aladinonl on 2010-10-04
reporting to google is maybe more helpful than reporting to a china ISP. but well, it's just one email anyway.

---

### Post by sourchier on 2010-10-04
You can receive help from Google from the following web sites.

Gmail TOS
[http://mail.google.com/support/bin/request.py?hl=en&contact_type=abuse&rd=1]("http://mail.google.com/support/bin/request.py?hl=en&contact_type=abuse&rd=1")

Other Gmail support
[http://mail.google.com/support/bin/request.py?contact_type=contact_policy]("http://mail.google.com/support/bin/request.py?contact_type=contact_policy")

---

