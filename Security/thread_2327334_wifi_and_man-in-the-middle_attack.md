---
title: "wifi and man-in-the-middle attack"
date: 2016-06-09
forum: Security
---

### Post by alberto36 on 2016-06-09
I have the following question. Today, I connected my computer to the wi-fi hotspot of my Samsung and I noted something strange. The connection icon was not as usual (see the attachment, icon at the top-right representing a screen instead of the usual cone-like icon). I checked my smartphone and the list of connected devices was completely blank, whereas my computer was saying that I was actually connected. So, I am asking, what happened? Does someone know what that icon means? Thanks very much.

---

### Post by QDR06VV9 on 2016-06-09
Your icon looks to be the same as mine absent the same Theme perhaps:
But a quick whois check shows this.
> These addresses are in use by many millions of independently operated networks, which might be as small as a single computer connected to a home gateway, and are automatically configured in hundreds of millions of devices.  They are only intended for use within a private context  and traffic that needs to cross the Internet will need to use a different, unique address.
Comment:        
Comment:        These addresses can be used by anyone without any need to coordinate with IANA or an Internet registry.  The traffic from these addresses does not come from ICANN or IANA.  We are not the source of activity you may see on logs or in e-mail records.  Please refer to [http://www.iana.org/abuse/answers](http://www.iana.org/abuse/answers)
Comment:        
Comment:        These addresses were assigned by the IETF, the organization that develops Internet protocols, in the Best Current Practice document, RFC 1918 which can be found at:
Comment:        [http://datatracker.ietf.org/doc/rfc1918](http://datatracker.ietf.org/doc/rfc1918)
Ref:            [https://whois.arin.net/rest/net/NET-10-0-0-0-1](https://whois.arin.net/rest/net/NET-10-0-0-0-1)


OrgName:        Internet Assigned Numbers Authority
OrgId:          IANA
Address:        12025 Waterfront Drive
Address:        Suite 300
City:           Los Angeles
StateProv:      CA
PostalCode:     90292
Country:        US
RegDate:        
Updated:        2012-08-31
Ref:            [https://whois.arin.net/rest/org/IANA](https://whois.arin.net/rest/org/IANA)



---

### Post by alberto36 on 2016-06-09
The fact that the IP is a private address is another strange thing. I changed the password and the name of the WiFi connection. I reconnected and now everything looks normal.
The icon is like before. What I find strange is this. When I connect my computer to the hotspot of my Galaxy S4, the phone usually shows a list of connected devices, but the list was completely blank! To what was I actually connected?

---

### Post by QDR06VV9 on 2016-06-09
> To what was I actually connected?
Still shows the same provider.

If you are using WEP, it's virtually... no security. I'm connected to my WPA2 personal AES
You should be able to see all connected devices with:
```
arp -a
```

---

### Post by SeijiSensei on 2016-06-09
Use "sudo iwlist scanning" to see the list of available wifi device.

---

### Post by yoshii on 2016-06-15
In my hometown the local libraries use a certain locally well-known hotspot name.  
One day when all the libraries were closed for a federal holiday, I noticed the same hotspot name popped up in a different neighborhood than the library.  
I think it was somebody trying to spoof the library and harvest personal information.  
Often the OS'es will log the most recent hotspots connected to and try to automatically reconnect to them if given the chance.  
It's somewhat of a security risk.  
I reported the wifi fraud to the libraries and to the local law enforcement.  
It's since gone away I think, and the library changed their hotspot name as well as their log-in procedure.  

Wifi is notoriously slacking in security.  There's tons of articles and youtube videos about it's exploits.

---

