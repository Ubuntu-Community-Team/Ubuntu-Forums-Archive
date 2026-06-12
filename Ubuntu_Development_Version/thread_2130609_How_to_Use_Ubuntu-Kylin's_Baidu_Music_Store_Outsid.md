---
title: "How to Use Ubuntu-Kylin's Baidu Music Store Outside China?"
date: 2013-03-29
forum: Ubuntu Development Version
---

### Post by ping-wu on 2013-03-29
One of the China-localizations Ubuntu-Kylin provides vis-a-vis mother Ubuntu is that it includes Baidu music search in the Dash.  However, this feature only works when you are in China.

Does anyone know if there is any good proxy server that will allow Kylin users in the US to utilize this localized feature?

---

### Post by cariboo on 2013-03-30
I found an i386 package that you may find useful [here.]("https://launchpad.net/ubuntu/raring/i386/unity-china-music-scope/1.0.0-0ubuntu1"), it's also available in the repositories, including an amd64 package.

---

### Post by ping-wu on 2013-03-30
> **ping-wu said:**
> One of the China-localizations Ubuntu-Kylin provides vis-a-vis mother Ubuntu is that it includes Baidu music search in the Dash.  However, this feature only works when you are in China.

Does anyone know if there is any good proxy server that will allow Kylin users in the US to utilize this localized feature?

Thanks.  the unity-china-music-scope package has already been installed in Kylin (this is one of the main advertised features of Kylin).

My question is where and how to implement a proxy server so as to allow me to employ the Baidu music services.  These services are limited to IP addresses in China.  In the US, when I tried to run this package, I received a message that the service is not available in my area (i.e., not available outside China).

---

### Post by cariboo on 2013-03-30
I know there are proxies in China, as spammers use them. I did find this list of [proxy servers]("http://www.proxynova.com/proxy-server-list/country-cn/")

---

### Post by ping-wu on 2013-03-30
I have never used proxy before.  But when I tried to use some of the proxy servers on the list with Firefox (Edit -> Advanced -> Network -> Settings -> Manual proxy configuration -> HTTP Proxy), I received a message that they are refusing the connections.

---

### Post by grahammechanical on 2013-03-30
I have been reading this

[http://www.omgubuntu.co.uk/2013/01/baidu-music-search-available-for-ubuntu-13-04#comment-775553841](http://www.omgubuntu.co.uk/2013/01/baidu-music-search-available-for-ubuntu-13-04#comment-775553841)

I think that the issue has to do with the licensing arrangements of the Baidu Music site. There is a similar restriction in the UK regarding BBC iPlayer. We in the UK can use that site because we pay licence fees to watch TV and have already paid to view those programs and so we can view them over the internet. But people outside the UK have difficulty accessing those programs.

Regards.

---

### Post by ping-wu on 2013-03-30
I know the reason behind the blocking (outside China), but I thought we should be able to fake our IP by using an appropriate proxy.

I came across a list of proxy server addresses in a Ubuntu forum in Taiwan which would allow people in Taiwan to access many internet cites that are similarly limited to China IP addresses.  However, I forgot where this info was posted.

---

### Post by QIII on 2013-03-30
Because this line of discussion seems destined to cross into territory in violation of the CoC vis-a-vis licensincing, EULAs, commercial restrictions and governmental restrictions, I'm closing it for staff review.

---

### Post by Iowan on 2013-03-30
> **ping-wu said:**
> I know the reason behind the blocking (outside China), but I thought we should be able to fake our IP by using an appropriate proxy..Perhaps this would be a good time to review the Code of Conduct.
>  We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings

---

### Post by mörgæs on 2013-03-31
I think this calls for an overall discussion. 

The free software culture is not known for imposing artificial restrictions upon the user.

Do we always follow any given restriction that any given company (which might be Canonical) decides to implement or do we want to reserve the right to have our own opinion?

---

