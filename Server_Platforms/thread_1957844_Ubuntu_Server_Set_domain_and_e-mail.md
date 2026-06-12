---
title: "Ubuntu Server: Set domain and e-mail"
date: 2012-04-13
forum: Server Platforms
---

### Post by jsusnik on 2012-04-13
Hello!

I have server on which I installed Ubuntu Server 10.04 and I would like to set domain on it. I already buy domain, but I don't know how to set it. I would also like to set e-mail to have mail account with my domain name.

I don't know where to start, so I'm asking you, what I must set now?

Thanks in advance!

Sincerely,
jsusnik

---

### Post by terrykiwi83 on 2012-04-13
First of all you need to change the domains nameservers to that our your server. Is your server a home based server or do you have it hosted in a datacentre?

Have a look here [http://ubuntuforums.org/showthread.php?t=1110168](http://ubuntuforums.org/showthread.php?t=1110168)

---

### Post by darkod on 2012-04-13
Also, it depends what exactly do you mean by "set domain and e-mail". Did you buy just the domain name, without any hosting services, and you want your ubuntu server to be your webserver and email server?

For that you will need to install apache and what ever email server program you decide to use.

Also, in some cases your ISP might be blocking this type of traffic so you might not be able to host servers at home.

If you do have hosting services somewhere, there is no need to set anything about your domain on your home server. Also, if these services include mailboxes, then your website and email will be at your provider. You can read your email with any email client.

---

### Post by jsusnik on 2012-04-13
The server is at home and I already contacted ISP if I can have this type of services. The response was positive, so there is no problem with ISP and internet connection. I also have static and public IP and opened ports for webserver and others.

For now after I fast read thread, I have next questions:
- Do I need to find DNS provider or can I use settings at registrar's control panel?
- Can I somehow create subdomains then?
- What settings for DNS entries will I have to add - is there any good tutorial on that?

Thanks! :)

---

### Post by darkod on 2012-04-13
Since you have a static public IP all you need to do is enter the registrars control panel and create a record for your domain with your public IP. In that case your registrars servers will do the DNS (double check this with them).

If they don't do DNS service, then you will either need to add the DNS role to your server, or use some free dns service. In this case, in the registrars control panel you will enter the servers of the company where you opened a dns account, and in that dns account control panel create the record for your webserver with your public IP.

After you do that, and install apache on your server, you should be able to see the apache test page by entering your public IP in a browser.

---

### Post by SeijiSensei on 2012-04-13
> **darkod said:**
> Since you have a static public IP all you need to do is enter the registrars control panel and create a record for your domain with your public IP. In that case your registrars servers will do the DNS (double check this with them).

Specifically you need to create an MX record for the domain that points to your server.  While it's possible to have only an A record, it's not considered good practice.  Rather you should have a combination like:

```

       IN    MX    0 mail.example.com.
mail   IN    A     10.10.10.10

```

If you also want to host web services for the domain on the same address, you can either add another A record with "www" as the hostname and the same IP, or use a CNAME alias like this:

```

www    IN    CNAME  mail

```

---

