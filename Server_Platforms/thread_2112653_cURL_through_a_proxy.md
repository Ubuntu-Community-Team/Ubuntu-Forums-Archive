---
title: "cURL through a proxy"
date: 2013-02-05
forum: Server Platforms
---

### Post by Ms. Daisy on 2013-02-05
I am playing with simple cURL commands and succeeding in retrieving web pages when I'm not behind a proxy. But when I try to go through the proxy I am getting errors "400 bad request."

Here's my command
```
curl --user-agent "Mozilla/1.22 (compatible; MSIE 10.0; Windows 3.1)" --proxy-user username: -x my.proxy.com:8080 http://www.google.com >> output.txt
```

I *think* that command is telling my request to say it is internet explorer 10.0 on a windows machine. It will pass the proxy my username, then prompt me for a password if it needs one. -x tells it to use the proxy that i have named along with port 8080. My target url is google. Finally, cURL will dump the output into the file called "output.txt".

It returns the error "400 bad request."

What am I doing wrong?

---

### Post by Lars Noodén on 2013-02-05
Don't you need to also include the protocol in the proxy specification?

-x 'http://my.proxy.com:8080/'

---

### Post by Ms. Daisy on 2013-02-06
That is the fully qualified domain name of my proxy, so I wouldn't think it would need the http:// if I'm using an internal DNS server.  If I were relying on an external DNS that would make sense.  I gave it a try anyway and got the same result.

---

### Post by Lars Noodén on 2013-02-07
OK. The manual page does show that protocol is optional.  

I've set up squid and configured to require user authentication, but am not able to duplicate your error. The following syntax works for me.  It's the same as you listed above.

```

curl --proxy-user user:passwd -x proxy.example.org:3128 http://www.google.com/

```

Have you also tried -v for verbose output with curl to see more of what's happening?

---

### Post by Ms. Daisy on 2013-02-09
Thanks, -v seems to say that it's the proxy returning the 400 bad request error, not google. I don't think the proxy knows what to do with the curl request. I imagine that I could pass some more options in the command that would tell the proxy how to handle the packets, but that will require some testing, reading, and dumb luck.

Or....
```
service squid stop
ufw disable
curl http://www.google.com >> output.txt
``` and done.
LOL

---

