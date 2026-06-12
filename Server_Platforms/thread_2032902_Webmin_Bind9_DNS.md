---
title: "Webmin Bind9 DNS"
date: 2012-07-24
forum: Server Platforms
---

### Post by phpkid on 2012-07-24
I need help setting up the Bind DNS is this right

i repleace my website with "mywebsite.com"

is this right im i suppose to use the lan ip address
or am i suppose to use my ip-adress the one i get when you go to [www.whatsmyip.org](www.whatsmyip.org)

$ttl 38400
mywebsite.com.	 IN	SOA	mywebsite.com. 
hostmaster.mywebsite.com. (
1341713681
10800
3600
604800
38400 )
mywebsite.com.	 IN	 NS	 mywebsite.com.
mywebsite.com.	 IN	 A	 192.168.1.3
[www.mywebsite.com](www.mywebsite.com).	 IN	 A	 192.168.1.3
ns1.mywebsite.com.	 IN	 A	 192.168.1.3
ns2.mywebsite.com.	 IN	 A	 192.168.1.3
mywebsite.com.	 IN	 NS	 ns1.mywebsite.com.
mywebsite.com.	 IN	 NS	 ns2.mywebsite.com.

---

### Post by papibe on 2012-07-24
Hi phpkid.

Are you setting bind as DNS for your home/office network?

Do you administrate  a public Internet domain?

Regards

---

### Post by phpkid on 2012-07-24
Home but I want this to host my website that Im creating

---

### Post by papibe on 2012-07-25
For home use you are using the correct LAN addresses.

If you want to host your server to the world, what you may need is [Dynamic DNS]("http://en.wikipedia.org/wiki/Dynamic_DNS"). There are several free services (check this [list]("http://dnslookup.me/dynamic-dns/")).

As a side note, there are several issues for hosting a web server at home. For limited to small access it could be possible, but it gets tricky beyond  that.

Regards.

---

### Post by phpkid on 2012-07-25
Will Dynamic DNS let me use my domain or will it be something like mydomain.dynamicdns.com

---

### Post by papibe on 2012-07-25
If you own a domain, and have a public static IP, you can set that on your registrar provider.

If you own a domain, and have a regular ISP service, you can forward the domain you own to the dynamic DNS name, so people won't notice it  when they use 'mydomain.com'.

If you don't own a domain, you'll have to use what is available on the dynamic DNS provider you choose (not perfect, but usable).

Regards.

---

### Post by phpkid on 2012-07-25
I own a domain and have a regular ISP service im going to try to see if it works

---

### Post by phpkid on 2012-07-25
im planning to buy a static ip address from my isp would i change

mywebsite.com.	 IN	 A	 192.168.1.3
[www.mywebsite.com](www.mywebsite.com).	 IN	 A	 192.168.1.3
ns1.mywebsite.com.	 IN	 A	 192.168.1.3
ns2.mywebsite.com.	 IN	 A	 192.168.1.3

to  

xxx.xxx.xxx.xxx is the ip would get

mywebsite.com.	 IN	 A	 xxx.xxx.xxx.xxx
[www.mywebsite.com](www.mywebsite.com).	 IN	 A	 xxx.xxx.xxx.xxx
ns1.mywebsite.com.	 IN	 A	 xxx.xxx.xxx.xxx
ns2.mywebsite.com.	 IN	 A	 xxx.xxx.xxx.xxx

---

### Post by SeijiSensei on 2012-07-25
Are you actually planning to host the public DNS for this domain?  What are you going to use for the mandatory backup DNS server?

You'd be better off letting the domain registrar host your records and pointing the A record for [www.domain.name](www.domain.name) to your public IP address.

---

### Post by phpkid on 2012-07-25
yes i want to host the publiyic dns server only for one month . Do I set it up like #8 above

---

### Post by phpkid on 2012-07-26
Can some help me out on how to set it up if possible

---

### Post by papibe on 2012-07-26
The common practice is:
[LIST]
[*]Go to your admin registrar page.
[*]And there, forward the domain you own to one you got from a dynamic dns service.
[/LIST]
Here's an example on how to do that on GoDaddy: [Forwarding or Masking Your Domain Name]("http://support.godaddy.com/help/article/422/forwarding-or-masking-your-domain-name").

Regards.

---

