---
title: "Website timing out"
date: 2011-04-19
forum: Server Platforms
---

### Post by ktz84 on 2011-04-19
I have 2 websites which I have setup using apache2 virtual hosts and they have been running for a while now without issue however today I'm getting time outs.

I can connect to the sites from within firefox on the server itself. On my Windows pc on the same network I can connect to the default website but it will not connec to the other site (just times out). I cannot connect to either website from an external machine.

I have checked the router and it appears to be setup correctly in that http is forwarded to the correct ip address and I have checked the ip address in the server and in the router logs.

As I can connect to both websites from the browser in the server that suggests to me that the apache virtual hosts is working correctly or else it wouldn't be able to find both websites or is that an incorrect assumption?

Sort of puzzled as to where to start. (I'm not really technical - I can follow a guide which is how I set the thing up in the first place).

---

### Post by ttshivers on 2011-04-19
Your ISP may be blocking port 80, which is the default port for apache.  You may want to change it to another port.  You can specify a port in the url bar by typing something like this: [http://www.websitename:8080/index.html](http://www.websitename:8080/index.html).  Replace 8080 with your port number.  This might help you with changing the default port [http://httpd.apache.org/docs/2.0/bind.html](http://httpd.apache.org/docs/2.0/bind.html)

---

### Post by ktz84 on 2011-04-19
Thanks for that. It actually put me on the the right path to finding the problem. I took a close look at my internet connection and spotted that my static ip had changed so I've now contacted the ISP and they have changed it back. Problem Resolved.

---

