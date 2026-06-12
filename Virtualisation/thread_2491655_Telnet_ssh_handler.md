---
title: "Telnet ssh handler"
date: 2023-10-16
forum: Virtualisation
---

### Post by imehrdad on 2023-10-16
Telnet Handler
Hi
i run eve-eng (simulator network) on vmware , and coonect to the with firefox and ip address when , i add node (switch or router) when click on them it must be open telnet consloe or ssh consloe , i searche in internet about them telnet handler and , i change something like that but not work !
can i help me?eve

---

### Post by SeijiSensei on 2023-10-16
Well, I have no idea if you're using Ubuntu (or indeed any Linux flavor) or not. On most any Linux system, the simple answers are
```

$ telnet ip.addr.of.server

```
and 
```

$ ssh ip.addr.of.server

```

---

### Post by MAFoElffen on 2023-10-17
Use ssh...
> 
Telnet is not a secure communication protocol because it does not use any security mechanism and transfers the data over network/internet in a plain-text form including the passwords and so any one can sniff the packets to get that important information.


---

