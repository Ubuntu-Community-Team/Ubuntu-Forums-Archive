---
title: "ProFTPD &amp; Groups"
date: 2005-08-02
forum: Server Platforms
---

### Post by rotten777 on 2005-08-02
I've got proftpd setup successfully and have no issues when login in as the initial user made when installing ubuntu but all the other users i have setup cannot login.

I've checked " /etc/ftpusers " for the other users being banned and they are not.

I've checked " /etc/group " and added the other user i"m troubleshooting to everygroup my main user is included in. 

No luck. 




I'm out of ideas. Any help is appreciated.

---

### Post by LordHunter317 on 2005-08-02
Is their shell valid?  How about their password?

---

### Post by rotten777 on 2005-08-02
[QUOTE=LordHunter317]Is their shell valid?  How about their password?[/QUOTE]

their password is fine. not sure what you mean by shell though.

---

### Post by LordHunter317 on 2005-08-03
The shell their account has set (in /etc/passwd).  Without changing a proftpd option, the user must have a valid shell listed in /etc/shells for their account, or they will not be able to login to proftpd.

---

### Post by rotten777 on 2005-08-03
[QUOTE=LordHunter317]The shell their account has set (in /etc/passwd).  Without changing a proftpd option, the user must have a valid shell listed in /etc/shells for their account, or they will not be able to login to proftpd.[/QUOTE]


it was a problem with both. the home directory was wrong in /etc/passwd and the /bin/false entry wasn't even in /etc/shells.

Fixed. Thank you very much :)

---

