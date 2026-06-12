---
title: "Tacacs+"
date: 2008-07-02
forum: Server Platforms
---

### Post by MatsB on 2008-07-02
I'm running tac-plus on Ubuntu server 6.10

Is it possible to get enable access to a Cisco device directly with tac-plus without entering router>enable?

If so, what commands do I need to enter in the router and in the tac-plus cfg file?

I tried this but did not help

```

$cat /etc/tacacs/tac_plus.cfg

# Use /etc/passwd file to do authentication

default authentication = file /etc/passwd

user = cisco {
  default service = permit
  login = file /etc/passwd
  service = exec {
    priv-lvl = 15
  }
}

#enable user
user = $enab15$ {
  login = cleartext enablepassword
}


```

Router conf
```

aaa new-model
aaa authentication login default group tacacs+ enable
aaa authentication enable default group tacacs+ enable
aaa authorization commands 1 default group tacacs+ none
aaa authorization commands 15 default if-authenticated group tacacs+
aaa accounting exec default start-stop group tacacs+
aaa accounting commands 1 default start-stop group tacacs+
aaa accounting commands 15 default start-stop group tacacs+
aaa accounting network default start-stop group tacacs+
aaa accounting connection default start-stop group tacacs+
aaa accounting system default start-stop group tacacs+
!
tacacs-server host x.x.x.x
tacacs-server directed-request
tacacs-server key 7 xxxxxxxx


```

---

### Post by Paris Heng on 2008-12-09
Hi, did you manage to solve or build this server already?

---

