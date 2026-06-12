---
title: "NIS server"
date: 2006-10-04
forum: Server Platforms
---

### Post by tumelo_lathane on 2006-10-04
is it possible to have a windows nis cleint? if its possible how do we do it? my nis server is ubuntu :-k

---

### Post by Macchi on 2006-10-04
Hello tumelo_lathane,
Maybe you mean authentication of windows clients through a Samba emulation of a Primary Domain Controller (PDC)? Plus file and printer 

This can be solved with the fantastic Samba, but depending on your number of flight-hours I would recommend approaching it in small steps:

1) file sharing to Windows clients on a workgroup
2) file+printer sharing, eventually add multiple shares.
3) file+printer shares+Samba PDC authentication 
4) file+printer shares+Samba PDC authentication with roaming profiles. 

Links:
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

The official website for Samba.org ha everything but it would be easier and faster to start with documentation in the Ubuntu wiki:

If you whant the best then try O'Reilly, that has excellent books on the subject. There is an incredible number of tutorials on the internet as well.


PS:
I have used a Samba PDC controller for a long time ago, when the continents where still togheter in Pandea and I had Windows clients. Now we have moved entirely to Ubuntu and I don't have to worry about those things anymore. The arrangement with roaming profiles may be problematic if the machines have different HW and SW configurations. A lot of people that do not recommend roaming profiles but they are cool.

I am also crazy to get an "out-of-the-box" working configuration that works for LDAP,Active Directory to authenticate Ubuntu and Windows clients from my small server. This would be a key component for many small companies.

---

### Post by sonic2000gr on 2006-10-04
> **tumelo_lathane said:**
> is it possible to have a windows nis cleint? if its possible how do we do it? my nis server is ubuntu :-k

Maybe you would like to have a look [at this page]("http://www.microsoft.com/technet/interopmigration/unix/sfu/default.mspx").

Microsoft provides a big download, possibly will allow you to use a Windows machine as a NIS client. Have not tried it myself though.

---

