---
title: "Nginx 1.14 Support on Ubuntu 18.04"
date: 2020-09-01
forum: Server Platforms
---

### Post by jesseb81 on 2020-09-01
All,
Our vulnerability scanner has flagged nginx as being end-of-life on our Ubuntu 18.04 with a high risk factor. I do see that Nginx 1.14 is EOL on the nginx.org site, however, I wanted to check to see if Ubuntu will still be providing updates for Nginx 1.14 while Ubuntu 18.04 is supported. I could look into switching to the official PPA, however, I am concerned about the changes in configuration between the Ubuntu version in the nginx PPA version. For example, I do not believe the PPA uses the sites-avaialble and sites-enabled setup.

Any information you could provide would be greatly appreciated.

---

### Post by TheFu on 2020-09-01
LTS releases get security fixes backported during the support period.
The point of an LTS is to remain feature stable and secure.

---

### Post by jesseb81 on 2020-09-02
Thank you for your reply. I wanted to confirm that this included the components outside of the OS which you confirmed for me. I am going to submit a false positive for the security scanner.

---

### Post by TheFu on 2020-09-02
> **jesseb81 said:**
> Thank you for your reply. I wanted to confirm that this included the components outside of the OS which you confirmed for me. I am going to submit a false positive for the security scanner.

It includes those packages that Canonical supports - not everything outside some magical list.  After all, how do you define the "OS" for a system built with software from 60,000+ different teams?  The packages in the Canonical repos would be the ones supported.

Use apt search for that information:
```
nginx-full/xenial-updates,**xenial-security** 1.10.3-0ubuntu0.16.04.5 amd64
  nginx web/proxy server (standard version)

```

---

### Post by ameinild on 2020-09-11
You could also run the latest nginx with Docker.
[https://hub.docker.com/_/nginx](https://hub.docker.com/_/nginx)

I would also have suggested snap, but generally server apps have poor snap support, and thus no nginx package is available.

---

### Post by LHammonds on 2020-09-11
FYI - On Ubuntu Server 20.04.1 LTS, the repository shows nginx 1.18.0

You  may not want to do this now but when upgrading from one OS version to  another, I create a new virtual server and install all the current  software needed to replace the old server.  Then I modify the  configurations to match the old server (not just copy old configs due to  potential compatibility / feature issues).  At this point, I prove or  disprove that the base system on the new OS and new versions will work  or not.  If they work, I proceed to migrate the data over and test the  end-result of the entire system running on the new OS.  If it all works,  I will have documented what it took and what configuration changes need  to be made on the new versions and can then schedule the production  system migration which is essentially the exact same process but done in  a much faster time-frame and the end-result is the swap of the server  IP addresses so the new production system is using the old production's  IP address...so nothing on the firewall/DNS servers need to be modified  for the system to work (if exposed to the Internet or internally to the  local network).

LHammonds

---

### Post by kevdog on 2020-09-12
> **LHammonds said:**
> FYI - On Ubuntu Server 20.04.1 LTS, the repository shows nginx 1.18.0

You  may not want to do this now but when upgrading from one OS version to  another, I create a new virtual server and install all the current  software needed to replace the old server.  Then I modify the  configurations to match the old server (not just copy old configs due to  potential compatibility / feature issues).  At this point, I prove or  disprove that the base system on the new OS and new versions will work  or not.  If they work, I proceed to migrate the data over and test the  end-result of the entire system running on the new OS.  If it all works,  I will have documented what it took and what configuration changes need  to be made on the new versions and can then schedule the production  system migration which is essentially the exact same process but done in  a much faster time-frame and the end-result is the swap of the server  IP addresses so the new production system is using the old production's  IP address...so nothing on the firewall/DNS servers need to be modified  for the system to work (if exposed to the Internet or internally to the  local network).

LHammonds

Nice workflow -- I'm not sure at home I take so many precautions however its good someone espouses a very safe way to do this.

---

