---
title: "What do I need to host my own website?"
date: 2012-05-25
forum: Server Platforms
---

### Post by TFroehlich3 on 2012-05-25
Hello Everyone, 
    I has been awhile since I have been on here but I'm glad to FINALLY be back! 

I was wondering what all I need to host my website from my home? I have a server all setup I just need to know how to configure it and get my internet all setup for it.

I know that I have to have the server has to have a static IP, that is no problem. 

What I need help with is the DNS Hostname, do I get a DNS service?

I also need help configuring that DNS service with my router. 

And I need to configure my FTP so I can also access it via the internet

Can someone help me get this up and running?

---

### Post by roelforg on 2012-05-25
DNS only translates a name to an ip.
no-ip is popular.

Configure the router to forward the ports you wish to open (i'd guess 21 (ftp), 80 (http)).

Maybe use:
```

tasksel install lamp-server

```
To setup a web stack.
And look around the wiki, forums, help and internet for the ftp.

---

### Post by TFroehlich3 on 2012-05-25
> **roelforg said:**
> DNS only translates a name to an ip.
no-ip is popular.

Configure the router to forward the ports you wish to open (i'd guess 21 (ftp), 80 (http)).

Maybe use:
```

tasksel install lamp-server

```
To setup a web stack.
And look around the wiki, forums, help and internet for the ftp.



Okay, I want to use my domain that I purchased, would I still use no-ip to assign my server IP to that domain?

---

### Post by roelforg on 2012-05-25
> **TFroehlich3 said:**
> Okay, I want to use my domain that I purchased, would I still use no-ip to assign my server IP to that domain?
With a domain usually comes a dns. (I though you didn't have one already, so ignore the no-ip thing).
Ask your registrar if they manage your dns (most do, almost all domains get sold with dns).

---

### Post by game1 on 2012-05-25
for ftp I recommend vsftpd. It has easy configuration and it is probably the most reliable. But it is better to transfer files via SSH because it is the most secure. Was you also thinking about email server?

---

### Post by TFroehlich3 on 2012-05-25
> **game1 said:**
> for ftp I recommend vsftpd. It has easy configuration and it is probably the most reliable. But it is better to transfer files via SSH because it is the most secure. Was you also thinking about email server?

I am planning on an email server in the future. For right now I am trying to setup a website server. I want to make sure the up time is 95% up before trying to host email.

---

### Post by kennethconn on 2012-05-25
When you say the server is using a static IP address, do you mean a public IP address? If that is the case, you should just need to make a change in your control panel / account with your registrar, and a port forward on your router to your chosen HTTP port.
 
If the server IP address is not a static one (public), then you'll have further work to do.
 
That would be my understanding of your post.

---

### Post by TFroehlich3 on 2012-05-25
> **kennethconn said:**
> When you say the server is using a static IP address, do you mean a public IP address? If that is the case, you should just need to make a change in your control panel / account with your registrar, and a port forward on your router to your chosen HTTP port.
 
If the server IP address is not a static one (public), then you'll have further work to do.
 
That would be my understanding of your post.

No the IP of the actual machine is static, not the IP for the internet. My ISP is dynamic, so how would I go about tackling this?

---

### Post by game1 on 2012-05-25
you can use dyndns.org. it is free solution. or buy static ip for your router from isp.

---

### Post by TFroehlich3 on 2012-05-25
> **game1 said:**
> you can use dyndns.org. it is free solution. or buy static ip for your router from isp.

Thank you I will look into that! And welcome to the forum new comer!

---

### Post by kennethconn on 2012-05-25
> **TFroehlich3 said:**
> No the IP of the actual machine is static, not the IP for the internet. My ISP is dynamic, so how would I go about tackling this?
 
Then you would need something like no-ip or dyndns as mentioned in previous posts. I use dyndns.com myself and I highly rate them. I came across [StartSSL DNS]("http://www.startssl.net/") when I was investigating SSL certificates but did not go any further (didn't suit my needs on the SSL certs side of things) and was happy with dyndns.
 
Also, game1, I don't think it would be free for the OP poster as they have their domain already. 
 
I would not go with the static IP address from your ISP if there is a cost involved (the previous service mentioned I would imagine would be cheaper).

---

### Post by anonymouschief on 2012-05-25
> **TFroehlich3 said:**
> Hello Everyone, 
    I has been awhile since I have been on here but I'm glad to FINALLY be back! 

I was wondering what all I need to host my website from my home? I have a server all setup I just need to know how to configure it and get my internet all setup for it.

I know that I have to have the server has to have a static IP, that is no problem. 

What I need help with is the DNS Hostname, do I get a DNS service?

I also need help configuring that DNS service with my router. 

And I need to configure my FTP so I can also access it via the internet

Can someone help me get this up and running?

Here is the documentation to get your webserver and sites up and running: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")
If it is just you who will need to access the server via FTP, I recommend that you use SFTP (Secure FTP). Here are example SFTP clients you can use: [FTP Clients Google Search Results]("https://www.google.ca/#hl=en&sclient=psy-ab&q=sftp+clients&oq=sftp+clients&aq=f&aqi=g4&aql=&gs_l=hp.3..0l4.1011.2867.0.2950.12.9.0.3.3.1.214.1259.1j5j2.8.0...0.0.fV0XSaIfkSY&pbx=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&fp=e59eb8a130ba0159&biw=1198&bih=742")
To get your domain name working, just call your domain registra support and have them help you point the domain to your external ip.

---

### Post by TFroehlich3 on 2012-05-25
> **kennethconn said:**
> Then you would need something like no-ip or dyndns as mentioned in previous posts. I use dyndns.com myself and I highly rate them. I came across [StartSSL DNS]("http://www.startssl.net/") when I was investigating SSL certificates but did not go any further (didn't suit my needs on the SSL certs side of things) and was happy with dyndns.
 
Also, game1, I don't think it would be free for the OP poster as they have their domain already. 
 
I would not go with the static IP address from your ISP if there is a cost involved (the previous service mentioned I would imagine would be cheaper).

How much are you paying dyndns? It says it's 29.99 a year for LOW TRAFFIC, my site isn't really low traffic... And no-ip, how much does that cost?

---

### Post by kennethconn on 2012-05-25
I would imagine most of your questions would be answered on their respective websites.
DynDNS had a free trial period, fire off a quick email to them with your questions if you don't find an answer on their FAQ / forums.

---

