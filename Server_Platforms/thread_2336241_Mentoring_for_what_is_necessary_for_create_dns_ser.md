---
title: "Mentoring for what is necessary for create dns server, I guess"
date: 2016-09-06
forum: Server Platforms
---

### Post by sed_faster on 2016-09-06
Hello,

I don't know if I am in right section, but let's go!
I have only a domain, e.g. domain.com, and when my client try access this domain I like which he redirect for another domain, e.g. domain2.com. I think this is a dns server, right?

I have a server with Ubuntu 16.04 LTS and I like do a project like this, or at least study something which get close more what I really need do and know about this. I don't know what is necessary and don't know which termology study.

I will apreciate yours help,
Thanks

---

### Post by SeijiSensei on 2016-09-06
If you mean you visit a website named [www.example.com](www.example.com) and get redirected to [www.somewhere-else.com](www.somewhere-else.com), that can be handled by DNS or by the web server software.  In a DNS server you would use a "CNAME" record in the "zone file" for example.com like this
```

@               IN SOA  example.com. support.example.com. (
[stuff]

www     IN CNAME www.somewhere-else.com.
[more stuff]

```
That repoints the name "www.example.com" to "www.somewhere-else.com".

Or you can use a redirect in Apache:
```

<VirtualHost *:80>
ServerName www.example.com
Redirect / http://www.somewhere-else.com/
</VirtualHost>

```

DNS management is among the more difficult tasks a system administrator faces.  The software uses fairly arcane configuration files and is very picky.  I'd start here: [https://www.linode.com/docs/networking/dns/dns-records-an-introduction](https://www.linode.com/docs/networking/dns/dns-records-an-introduction)

---

### Post by sed_faster on 2016-09-06
Hello,

Thanks for your help. But I see, as you speak, this matter are very  hard for beginner. But I will study :)

My situation is: I have a domain and I want, when client accessed my domain redirect him for pages.github.com.
The company, where I bought the domain asked my for dns domain/name, but on github pages I haven't this information. I called with their and they said I needed the company hosting. But I think this stupid, because I won't pay hosting, every months, for only redirect domains.

I don't know any company, and I don't know if exist, will provide only this service (redirect domains). If you help I will appreciate your help :)
thanks

---

### Post by SeijiSensei on 2016-09-07
You can redirect [www.example.com](www.example.com) to pages.github.com via DNS.  Your DNS provider should offer you a control panel where you can point the "www" name in your domain to pages.github.com using a CNAME record.  You don't want to manage a DNS server if you can avoid it. Let your DNS registrar handle that for you.

However that will not redirect [www.example.com](www.example.com) to a specific page within pages.github.com, only to the top-level host.  To point to a specific page you would need to have an Apache server somewhere that can do the second type of redirect above, with the complete URL to your page in place of "http://www.somewhere-else.com/".  You could probably use a free service like [AWS S3]("https://aws.amazon.com/s/dm/optimization/server-side-test/sem-generic/storage-b/?sc_channel=PS&sc_campaign=acquisition_US&sc_publisher=google&sc_medium=s3_b&sc_content=s3_e&sc_detail=aws%20s3&sc_category=s3&sc_segment=101664430962_test_q3_2016&sc_matchtype=e&sc_country=US&s_kwcid=AL!4422!3!101664430962!e!!g!!aws%20s3&ef_id=VRMy6gAABHRfzl@S:20160907135741:s") for that, but that's just a guess.  I've never used AWS as I rent virtual servers in the cloud from [Linode](http://www.linode.com/).

---

