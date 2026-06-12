---
title: "does this ip belongs to google or is just a site made to look like google?"
date: 2009-06-26
forum: The Cafe
---

### Post by heyyy on 2009-06-26
the ip is 74.125.39.83

---

### Post by monsterstack on 2009-06-26
Well, it looks like Google. The whois report tells us,

```

Whois Record

OrgName:    Google Inc. 
OrgID:      GOGL
Address:    1600 Amphitheatre Parkway
City:       Mountain View
StateProv:  CA
PostalCode: 94043
Country:    US

NetRange:   74.125.0.0 - 74.125.255.255 
CIDR:       74.125.0.0/16 
NetName:    GOOGLE
NetHandle:  NET-74-125-0-0-1
Parent:     NET-74-0-0-0-0
NetType:    Direct Allocation
NameServer: NS1.GOOGLE.COM
NameServer: NS2.GOOGLE.COM
NameServer: NS3.GOOGLE.COM
NameServer: NS4.GOOGLE.COM
Comment:    
RegDate:    2007-03-13
Updated:    2007-05-22

OrgTechHandle: ZG39-ARIN
OrgTechName:   Google Inc. 
OrgTechPhone:  +1-650-318-0200
OrgTechEmail:  

```

But going to google.com puts me at the range of these addresses: 209.85.227.99, 209.85.227.147, 209.85.227.104, 209.85.227.103. Which are obviously completely different. Also at that site, I am not logged in to google's services. And I don't think it's a good idea to try. But the place is registered to Google's address. Very odd.

---

### Post by heyyy on 2009-06-26
is it normal to show me that google site is from germany?
i dunno if it matters but im located in europe

---

### Post by Dark Aspect on 2009-06-26
I thought Google was [74.125.65.103]("74.125.65.103")

---

### Post by LookTJ on 2009-06-26
This should tell you some of the IPs routed to Google.com

```
host google.com
```

---

### Post by Dark Aspect on 2009-06-26
> **Taylor said:**
> This should tell you some of the IPs routed to Google.com

```
host google.com
```

dude, that doesn't even show [74.125.65.103]("74.125.65.103")? that gives me

```
google.com has address 74.125.127.100
google.com has address 74.125.45.100
google.com has address 74.125.67.100
google.com mail is handled by 10 smtp4.google.com.
google.com mail is handled by 10 smtp1.google.com.
google.com mail is handled by 10 smtp2.google.com.
google.com mail is handled by 10 smtp3.google.com.
```

---

### Post by heyyy on 2009-06-26
can you suggest to me a good add on for firefox for showing mine and the server's ip which im currently visiting?

---

### Post by LookTJ on 2009-06-26
> **Dark Aspect said:**
> dude, that doesn't even show [74.125.65.103]("http://74.125.65.103")? that gives me

```
google.com has address 74.125.127.100
google.com has address 74.125.45.100
google.com has address 74.125.67.100
google.com mail is handled by 10 smtp4.google.com.
google.com mail is handled by 10 smtp1.google.com.
google.com mail is handled by 10 smtp2.google.com.
google.com mail is handled by 10 smtp3.google.com.
```
Note that I said some ;).  74.125.*.* seems to be Google's netblock acooding to the information provided.

---

### Post by monsterstack on 2009-06-26
> **heyyy said:**
> can you suggest to me a good add on for firefox for showing mine and the server's ip which im currently visiting?

[Here]("https://addons.mozilla.org/en-US/firefox/addon/590") you go.

---

