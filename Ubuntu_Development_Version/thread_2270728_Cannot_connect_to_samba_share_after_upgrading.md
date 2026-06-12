---
title: "Cannot connect to samba share after upgrading"
date: 2015-03-25
forum: Ubuntu Development Version
---

### Post by janot2012 on 2015-03-25
My Blackberry Playbook has ip 169.254.0.1 when connected via usb cable: 

[ATTACH=CONFIG]260894[/ATTACH]

Now when trying to open share I get following error:

[ATTACH=CONFIG]260893[/ATTACH]


    ```
~$ smbclient -L 169.254.0.1 -N
    Connection to 169.254.0.1 failed (Error NT_STATUS_IO_TIMEOUT)
```


    ```
~$ ping -c 1 169.254.0.1
    PING 169.254.0.1 (169.254.0.1) 56(84) bytes of data.
    --- 169.254.0.1 ping statistics ---
    1 packets transmitted, 0 received, 100% packet loss, time 0ms
```

Any ideas? Thanks

---

### Post by dino99 on 2015-03-25
maybe a quick glance at the wiki should help
[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

---

### Post by janot2012 on 2015-03-25
> **9d9 said:**
> maybe a quick glance at the wiki should help
[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!
I'm still newbie in both Ubuntu and samba, but isn't this guide about creating share while I need to access share?

---

