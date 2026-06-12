---
title: "Apache2 with multiple domains: server reacts only to the IP but to non of the domains"
date: 2013-07-19
forum: Server Platforms
---

### Post by frankoo on 2013-07-19
Hi,
I have a basic server with only the important packages and appache2 installed (no plesk or other administration tools). I am renting this server on a hoster to whom i imported 3 domains from another (my old) webhoster.

The apache is in the default configuration, there is the default virtual host (no other virtual hosts) and my understanding is that all browser requests to my ip: 123.456.7.8
should be handled by the default virtual host (i.e. should use the Document Root directory defined in the default file).

In my case the server only shows the default page when using the server ip in the browser, when using one of the domains i got the error that no website was available.

I just want to clarify if this is because of the domain transfer process is not finished or if there is a configuration issue.
Is it so that when the domain transfer process is finished that the domains should be leading to the server ip? In the moment they are not.

---

### Post by sandyd on 2013-07-19
> **frankoo said:**
> Hi,
I have a basic server with only the important packages and appache2 installed (no plesk or other administration tools). I am renting this server on a hoster to whom i imported 3 domains from another (my old) webhoster.

The apache is in the default configuration, there is the default virtual host (no other virtual hosts) and my understanding is that all browser requests to my ip: 123.456.7.8
should be handled by the default virtual host (i.e. should use the Document Root directory defined in the default file).

In my case the server only shows the default page when using the server ip in the browser, when using one of the domains i got the error that no website was available.

I just want to clarify if this is because of the domain transfer process is not finished or if there is a configuration issue.
Is it so that when the domain transfer process is finished that the domains should be leading to the server ip? In the moment they are not.

Does that mean that your domains are currently not pointing at your webserver's ip?

If that is the case, the content on the domains are not served by your server, and will continue to be not served until the ip Address is updated in the DNS

---

### Post by nerdtron on 2013-07-19
To see it the server handles virtual hosts correctly, set the IP in you conputer's /etc/hosts file.
123.456.7.8 [www.domain1.com](www.domain1.com)
123.456.7.8 [www.domain2.com](www.domain2.com)
Then try typing the [www.domain1.com](www.domain1.com) and [www.domain2.com](www.domain2.com) in your web browser. It the web pages are displayed correctly, then it is a DNS issue.

---

### Post by volkswagner on 2013-07-20
To find what your current dns settings for each domain run dig, host commands.

```
host yourdomain.com
```
```
dig yourdomain.com
```

If the ip address returned is not your server, you'll need to update your dns settings at your domain registrar, or
wherever you have pointed you nameservers.

---

