---
title: "Problem on Internet browsing"
date: 2008-07-09
forum: Security
---

### Post by satimis on 2008-07-09
Hi folks,


Ubuntu LAMP 7.04 amd64


I don't know whether it is the right forum to post following probem;


Recently on Internet browsing clicking the URL will sometimes be directed to following site;

[http://guide.opendns.com/?url=h1.f352.mail.yahoo.com%2Fym%2FShowFolder%3FSearch%3D%26Npos%3D1%26next%3D1%26YY%3D41465%26inc%3D25%26order%3Ddown%26sort%3Ddate%26pos%3D0%26view%3Da%26head%3Db%26box%3DInbox](http://guide.opendns.com/?url=h1.f352.mail.yahoo.com%2Fym%2FShowFolder%3FSearch%3D%26Npos%3D1%26next%3D1%26YY%3D41465%26inc%3D25%26order%3Ddown%26sort%3Ddate%26pos%3D0%26view%3Da%26head%3Db%26box%3DInbox)


I have to click "go back" several times before I can visit the website on the URL.  Please advise where I have to check and how to fix the problem.  It only happens recently.  I haven't bookmarked this site.  TIA


B.R.
satimis

---

### Post by hyper_ch on 2008-07-09
it seems you use opendns as dns servers. So if a domain can't be found, you will be directed to opendns.

---

### Post by satimis on 2008-07-09
> **hyper_ch said:**
> it seems you use opendns as dns servers. So if a domain can't be found, you will be directed to opendns.
Hi hyper_ch,


Thanks for your advice.


$ dpkg -l | grep dns```

ii  dnsutils   9.3.4-2ubuntu2.2   Clients provided with BIND
ii  libdns22   9.3.4-2ubuntu2.2   NS Shared Library used by BIND

```

$ apt-cache policy bind```

bind:
  Installed: (none)
  Candidate: 1:8.4.7-1
  Version table:
     1:8.4.7-1 0
        500 http://us.archive.ubuntu.com feisty/universe Packages

```
BIND is not installed.


Previously if there was connection problem it only popup page NOT found without advertising.  NOW it popup with advertisement.  Therefore I thought it might be a problem.


B.R.
satimis

---

