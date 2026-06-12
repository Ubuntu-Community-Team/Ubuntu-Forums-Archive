---
title: "Please help! with bind/dns issue new record inside.."
date: 2009-10-12
forum: Server Platforms
---

### Post by Linuxwho? on 2009-10-12
$ttl 38400
xyz.net.	IN	SOA	mail. admin..xyz.net. (
			1255388564
			10800
			3600
			604800
			38400 )
xyz.net.	IN	NS	mail.
mail.xyz.net.	IN	MX	10 mail
mail            IN      A       192.168.21.24

I am using webmin for this..an GUI application to set DNS/Bind.  When I click to apply changes it says..
"NDC command failed : rndc: 'reload' failed: empty label"

I have no idea what this means or how to fix.:confused:

---

### Post by Linuxwho? on 2009-10-12
I just want the mx and A records to resolve locally.  Why is that so hard to do using 8.04?

---

### Post by Linuxwho? on 2009-10-12
I took this right out of the help docs and it simply does not work.  
$ttl 38400
xyz.net. IN SOA mail. admin..xyz.net. (
1255388564
10800
3600
604800
38400 )
xyz.net. IN NS mail.
mail.xyz.net. IN MX 10 mail
mail IN A 192.168.21.24

I am using webmin for this..an GUI application to set DNS/Bind. When I click to apply changes it says..
"NDC command failed : rndc: 'reload' failed: empty label"

I have no idea what this means or how to fix.  I simply want the hostname and mx record to resolve locally.

---

### Post by cariboo on 2009-10-12
Please don't create multiple threads on the same subject. I have merged your two thread.

Please be patient, we are volunteers here, you may have to wait a bit for the person that can answer to see it.

---

