---
title: "Default Root password"
date: 2005-11-02
forum: Server Platforms
---

### Post by VaioLord on 2005-11-02
I have installed the Server to if we can use it in the office.  However now installed it will not allow me to login as root when it boots.  During setup it asked me for a standard username and password which I can use fine, but every time I try to install any app of update the config is says I am unable to.   

How can I login as root please....going crazy here.  

Thanks

Stephen

---

### Post by LordHunter317 on 2005-11-02
You can't login as root OOB.  Use sudo to elevate your privleges for a single command, or 'sudo -s' to get a root-level shell.

---

### Post by Rohan on 2005-11-02
If you really want a root account type "sudo passwd" and it will prompt you to type a new pass for the root account.

---

