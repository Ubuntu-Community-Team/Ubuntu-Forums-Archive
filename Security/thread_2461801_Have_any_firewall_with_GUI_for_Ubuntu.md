---
title: "Have any firewall with GUI for Ubuntu ?"
date: 2021-05-07
forum: Security
---

### Post by aug7744 on 2021-05-07
For Ubuntu 21.04 has any firewall with GUI and when happen any access is displayed and GUI to choice if allow or block the access or any program trying connect to internet ?
Have any firewall with GUI how is Comodo Internet Security ?
Thanks for reply.

---

### Post by ajgreeny on 2021-05-07
I do not know Comodo Internet Security nor even if it works with Linux but the GUI to administer the firewall is **gufw** which you can install as usual with apt or software-centre or synaptic.

---

### Post by aug7744 on 2021-05-09
Thanks for your reply , not exaclty that I want to use.
I need an firewall or tool where when happen in or out access is displayed and GUI to choice if allow or block the access.

---

### Post by CharlesA on 2021-05-09
> **aug7744 said:**
> Thanks for your reply , not exaclty that I want to use.
I need an firewall or tool where when happen in or out access is displayed and GUI to choice if allow or block the access.

As far as I am aware, there isn't a firewall tool that will prompt you to allow or deny an application on Ubuntu. You can set rules via port or IP address via ufw or gufw if you want a GUI, or you can dig into iptables itself, but the syntax is a bit of a pain for beginners.

---

### Post by T6&amp;sfpER35% on 2021-05-09
if i understand you correctly you are trying to block certain programs to connect to internet?
might want to look into [this]("https://serverfault.com/questions/550276/how-to-block-internet-access-to-certain-programs-on-linux")
seems firejail is what you might look into , i have no experience with firejail though so this is just something i searched

as for comodo on linux, that's a no no , from experience

---

### Post by aug7744 on 2021-05-15
Thanks very much

---

