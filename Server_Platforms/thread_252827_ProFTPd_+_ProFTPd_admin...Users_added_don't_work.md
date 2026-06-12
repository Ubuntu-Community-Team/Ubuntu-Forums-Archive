---
title: "ProFTPd + ProFTPd admin...Users added don't work?"
date: 2006-09-07
forum: Server Platforms
---

### Post by HedonismBot on 2006-09-07
Hi forum folk!

Installed 6.06 and ProFTPd-mysql, installed the ProFTPd admin interface, all looks good, no errors, checks status of FTP just fine...EXCEPT:

users I create in the interface are "invalid" for the server...clients return "user login invalid" ](*,) 

Anyone had this problem before? I'm sure I'm just missing some simple step, so any help pointing me in the right direction would be most appreciated :mrgreen: 

PS: I love you all.

:KS

---

### Post by JLTB on 2006-09-08
Hi,

I just installed ProFTPd a few minutes ago so I'll share my experiences with you.

1) Restart the proftpd daemon after everything you do
```
sudo /etc/init.d/proftpd restart
```

2) Have you tried logging in via a real shell account on your ftp site?  For instance, I log into my ubuntu server with the name 'james' and my password.  Have you tried logging in to your ftp with the same info?  This is how I set my ftp up, and it seemed to be configured that way right out of the box.

For my purposes I created a light weight, limited, shell account for my ftp.

```

sudo useradd -m -G nogroup ftp
sudo passwd ftp
Enter new UNIX password: <ENTER A PASS HERE>
Retype new UNIX password: <ENTER IT AGAIN>

```

That's what I did anyway :-)

---

