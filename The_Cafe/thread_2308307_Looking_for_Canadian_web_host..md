---
title: "Looking for Canadian web host."
date: 2016-01-01
forum: The Cafe
---

### Post by waloshin on 2016-01-01
I want to host my three sites together with a Canadian host as I am tired of paying high American prices to host my sites. I am hosting with Bluehost and when I try to download my sites there server just times out so it is hard for me to transfer my files myself.

So I am looking for a web host that will migrate my websites for me for hopefully nothing.

---

### Post by HermanAB on 2016-01-02
Q9 Networks in Calgary?

---

### Post by SeijiSensei on 2016-01-02
How much do you pay to host three sites?  For $10/month you can rent an entire virtual server from [Linode]("http://www.linode.com/") and host as many sites as you want.  They don't have facilities in Canada, but besides their four locations in the US they also offer services in London, Frankfurt, Tokyo and Singapore.

---

### Post by CharlesA on 2016-01-03
> **waloshin said:**
> I want to host my three sites together with a Canadian host as I am tired of paying high American prices to host my sites. I am hosting with Bluehost and when I try to download my sites there server just times out so it is hard for me to transfer my files myself.

So I am looking for a web host that will migrate my websites for me for hopefully nothing.

How are you trying to transfer the files? If it's a shared host using cpanel, I believe you can FTP them rather than just doing a regular http get.

---

### Post by SeijiSensei on 2016-01-03
If the site just has plain HTML, CSS and graphics, you can suck the entire contents over with wget.

```
wget -r http://yoursite/
```

You might want to use the "-O" switch to direct the output to the proper location.

This obviously won't work if your site is scripted with a language like PHP or Python.  You'll just get the rendered HTML pages, not the code that generates them.

---

### Post by Dragonbite on 2016-01-03
I use Affordable Web Pages (or 3.75 hosting) which is ... you guessed it... $3.75 per month and another $0.25 for a MySQL database.  It is out of Canada.

[https://cp.awp-hosting.com:8443/psoft/servlet/psoft.hsphere.CP]("https://cp.awp-hosting.com:8443/psoft/servlet/psoft.hsphere.CP")

It feels like s smaller operation.

---

### Post by mastablasta on 2016-05-13
bluehost should have FTP Access available. connect to it using filezilla and try to donwload the whole folder.

---

