---
title: "Cannot login when AD server down"
date: 2011-09-23
forum: Server Platforms
---

### Post by mp21 on 2011-09-23
Hello all,

I have recently inherited a few ubuntu servers that are connected to our Win2k3 AD server for authentication. The problem is I am a bit of a newbie when it comes to Ubuntu server administration and whenever the AD connection is lost the forward facing SSH and FTP servers are not accessible even at the console.

I have googled and searched the forums for an answer but have been unsuccessful. This is probably due to me not knowing exactly what I am looking for. What we need it for the servers to fallback to local authentication when the AD connection fails.

If someone can point me in the right direction on this I would be eternally grateful.

Thanks in advance,
Bob

---

### Post by Dangertux on 2011-09-24
Without knowing exactly what your configuration looks like you might consult this documentation : 

[https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)


Hope that is helpful.

---

### Post by mp21 on 2011-09-24
Thanks for pointing me there, I think I got it now. I will post again if I have anymore problems.

---

