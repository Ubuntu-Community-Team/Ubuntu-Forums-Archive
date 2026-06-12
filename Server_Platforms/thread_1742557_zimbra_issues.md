---
title: "zimbra issues"
date: 2011-04-29
forum: Server Platforms
---

### Post by num on 2011-04-29
Hello,

I installed Zimbra on my Ubuntu 10.04 LTS Server Edition and I got Apache and MySQL running but for some reason I am getting these errors even though the DNS is set correctly on GoDaddy:

> Operations logged to /tmp/zmsetup.04272011-202410.log
Installing LDAP configuration database...done.
Setting defaults...hostname: Name or service not known
No results returned for A lookup of
Checked nameservers:
        75.75.75.75
        75.75.76.76


DNS ERROR resolving
It is suggested that the hostname be resolveable via DNS
Change hostname [Yes] no


DNS ERROR resolving MX for
It is suggested that the domain name have an MX record configured in DNS
Change domain name? [Yes] yes
Create domain: greensevenstudios.com
        MX: mail.greensevenstudios.com (X.X.X.X)
        MX: mail.greensevenstudios.com (X.X.X.X)

        Interface: 10.1.10.29
        Interface: 127.0.0.1


And I cannot connect to Zimbra via web interface using port 7071 please help.

---

### Post by num on 2011-04-29
anyone??

---

### Post by arrrghhh on 2011-04-29
Are you pointing DNS to your WAN IP?  The two 'interface' statements at the bottom bothered me: > Interface: 10.1.10.29
Interface: 127.0.0.1

---

