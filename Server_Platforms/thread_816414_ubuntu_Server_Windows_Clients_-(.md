---
title: "ubuntu Server Windows Clients :-("
date: 2008-06-02
forum: Server Platforms
---

### Post by burntmonkiee on 2008-06-02
Hey all,

I was looking for some help regarding:

I have a small network 20+ computer (WinXP  Pro SP2 latest patches) I was hoping than I could administer them from a ubuntu server.

main goals;
       # Domain Controler 
          for client logins and distrubute patches, software over
          the network
       # Print Server
       # Web Proxy / DNS Server for managing net access

Could anyone please point me in the direction, ideals, preferable something _Open Source_ that I can work with later when I become more confident.

Thanks BurntMonkiee

---

### Post by quelx on 2008-06-02
> **burntmonkiee said:**
> 
       # Domain Controler 
          for client logins and distrubute patches, software over
          the network
Not Ubuntu but the basics (and most of the specifics) are the same.
[http://gentoo-wiki.com/HOWTO_Implement_Samba_as_your_PDC](http://gentoo-wiki.com/HOWTO_Implement_Samba_as_your_PDC)
>  # Print Server
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
 >       # Web Proxy / DNS Server for managing net access
[https://help.ubuntu.com/8.04/serverguide/C/squid.html](https://help.ubuntu.com/8.04/serverguide/C/squid.html)

---

### Post by HermanAB on 2008-06-02
If you want to run a domain controller, then you have to go to the Samba web site and read the Official Howto.

Cheers,

Herman

---

### Post by bluefrog on 2008-06-02
patch, software.

OCS inventory and GLPI should do the trick

---

### Post by gtdaqua on 2008-06-03
> **bluefrog said:**
> patch, software.

OCS inventory and GLPI should do the trick

Thanks for the info. Seems worthwile!

---

