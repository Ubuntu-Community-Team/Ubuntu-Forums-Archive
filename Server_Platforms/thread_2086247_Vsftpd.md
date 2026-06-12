---
title: "Vsftpd"
date: 2012-11-20
forum: Server Platforms
---

### Post by Toriku on 2012-11-20
I am trying to set up an FTP server with virtual users.

I am currently following [this tutorial (click here)]("http://www.mmncs.com/2011/07/how-to-setup-an-ftp-server-with-virtual-usersno-accounts-using-vsftpd-on-ubuntu/2/"), for VSFTPD
and I have encountered a problem with the "cat" command on the second page. I don't know what the "&gt" part is trying to do, I get a gt command not found error and I get a permission denied error...

```
cat /dev/null &gt; /etc/pam.d/vsftpd
```

Can anyone help me?
Thanks

---

### Post by pkadeel on 2012-11-20
```
&gt;
``` is html code for ```
>
``` you probably copied the command from a web page which converted > to &gt;

---

### Post by Toriku on 2012-11-22
thanks pkadeel, you are quite right!
"&gt;" is html for ">", this solved my problem


I had to sudo su to use cat for some reason though, sudo wasn't enough on its own...

---

