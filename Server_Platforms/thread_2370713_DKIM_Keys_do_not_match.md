---
title: "DKIM Keys do not match"
date: 2017-09-06
forum: Server Platforms
---

### Post by costa_g on 2017-09-06
Hi,

I am having a problem with my server getting the DKIM key to work on my server configuration with Digital Ocean.

I am runnung Ubuntu 16.04.3 LTS. I have followed the tutorial below and searched for a solution online but I am unsure on how to solve the issue with this configuration:

[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-14-04)

When running below command it says 'keys do not match'.

opendkim-testkey -d domainname.com -s mail -k mail.private -vvv

Any help with this would be appreciated.

Kind Regards,

Costa

---

### Post by costa_g on 2017-09-06
After giving it some time and going through the process again I have managed to get things going and outputting as follows:

```
opendkim-testkey: using default configfile /etc/opendkim.conf
opendkim-testkey: key loaded from mail.private
opendkim-testkey: checking key 'mail._domainkey.rockpaperclicktalent.com'
opendkim-testkey: key not secure
opendkim-testkey: key OK

```
Despite this when validating using [http://dkimvalidator.com](http://dkimvalidator.com) it shows the following.

DKIM Information:

```
DKIM Signature


Message contains this DKIM Signature:
DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/simple;
	d=rockpaperclicktalent.com; s=mail; t=1504707122;
	bh=WBggpZrfs7F0OzQkyE7LiZPHyfFFhl7N4CNav2f5YVw=;
	h=Subject:To:Date:From:From;
	b=mpTAzIWwiNbV+nErku2sg1OKwtYKDVW1P+tidilxzyXkdx3BLW2lB2UaIR2V8zF3E
	 l2eBGqjTmxnxNWKKq0PC+A2zFXexg/TPcaKX72BFkyqqvvYwrSWBMhu/OluWR4KnVo
	 J3yyGPelYrWxpM3ASQD2rJUONcsjrK+wniGKxqzc=


Signature Information:
v= Version:         1
a= Algorithm:       rsa-sha256
c= Method:          relaxed/simple
d= Domain:          rockpaperclicktalent.com
s= Selector:        mail
q= Protocol:        
bh=                 WBggpZrfs7F0OzQkyE7LiZPHyfFFhl7N4CNav2f5YVw=
h= Signed Headers:  Subject:To:Date:From:From
b= Data:            mpTAzIWwiNbV+nErku2sg1OKwtYKDVW1P+tidilxzyXkdx3BLW2lB2UaIR2V8zF3E
	 l2eBGqjTmxnxNWKKq0PC+A2zFXexg/TPcaKX72BFkyqqvvYwrSWBMhu/OluWR4KnVo
	 J3yyGPelYrWxpM3ASQD2rJUONcsjrK+wniGKxqzc=
Public Key DNS Lookup


Building DNS Query for mail._domainkey.rockpaperclicktalent.com
Retrieved this publickey from DNS: v=DKIM1; k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDmk8ws9KcywNx0CePk13LZiKwq3SVH402cktfw4ATFPkODRscRzRlS/GRS/duhXKQDSeyA03LqrkQY8a/kWZPZ/9hD9uReJ8S9lQ05vt/XjvJlfwzFV+7kgBEoN5hz2TQHmV7sUt1Jc3hsk4gwfthGx7TlMfdizic71sh+DbVH6wIDAQAB
Validating Signature


result = fail
Details: bad RSA signature

```
Any suggestions would be appreciated. I will keep things posted.

---

### Post by costa_g on 2017-09-07
Running "opendkim-testkey -d rockpaperclicktalent.com -s mail -k mail.private -vvv" now outputs:

opendkim-testkey: using default configfile /etc/opendkim.conf
opendkim-testkey: mail.private: stat(): No such file or directory

---

### Post by costa_g on 2017-09-07
I have checked the directory for the file and it is there.

---

### Post by costa_g on 2017-09-07
Running "chmod 700 /var/run/opendkim" seems to have solved the last problem however when running

opendkim-testkey -d rockpaperclicktalent.com -s mail -k mail.private -vvv

I am receiving the output below again:

opendkim-testkey: using default configfile /etc/opendkim.conf
opendkim-testkey: key loaded from mail.private
opendkim-testkey: checking key 'mail._domainkey.rockpaperclicktalent.com'
opendkim-testkey: key not secure
opendkim-testkey: key OK

How should I go about securing the key?

Thanks,

Costa

---

### Post by costa_g on 2017-09-08
After running opendkim-testkey -d rockpaperclicktalent.com -s mail -k mail.private -vvv

in /etc/opendkim and /etc/opendkim/keys/rockpaperclicktalent.com I found the keys did not match in the keys directory.

After copying mail.private from /etc/opendkim to /etc/opendkim/keys/rockpaperclicktalent.com I found everything to be working.

---

