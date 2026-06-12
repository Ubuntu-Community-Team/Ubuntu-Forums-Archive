---
title: "Help on setting up a root login detector and emailer"
date: 2011-04-12
forum: Security
---

### Post by Rytron on 2011-04-12
Hi.

I got this from a website (cant remember URL).

Be warned if someone actually does manage to login as root on your computer or server.

Edit .bash_profile for root. [COLOR="Indigo"]**How do I do this?**[/COLOR]

```
echo 'ALERT - Root Shell Access on:' `date` `who` | mail -s "Alert: Root Access from `who | awk '{print $6}'`" your@email.com
```

Replace [email]your@email.com[/email] with your own email. Save the file and exit.

---

### Post by sanguinoso on 2011-04-12
The root account on ubuntu is disabled by default, have you enabled it?

---

### Post by Rytron on 2011-04-12
> **sanguinoso said:**
> Ubuntu machines root account is disabled by default, have you enabled it?

Hi sanguinoso.
No. So does root account have its own home folder?

---

### Post by sanguinoso on 2011-04-12
I believe the home directory for root is /root. However, if you haven't enabled the root account no one will be able to login as root via the terminal or ssh.

---

### Post by Rytron on 2011-04-12
> **sanguinoso said:**
> I believe the home directory for root is /root. However, if you haven't enabled the root account no one will be able to login as root via the terminal or ssh.

Okay. I will test this out in a VirtualBox Ubuntu VDI.

---

### Post by sanguinoso on 2011-04-12
Also, you can check home directories for users with ```
cat /etc/passwd | grep username
```

---

### Post by bodhi.zazen on 2011-04-12
Depending on your needs, I would suggest ninja

[http://blog.bodhizazen.net/linux/how-to-ninja-ubuntu-10-04/](http://blog.bodhizazen.net/linux/how-to-ninja-ubuntu-10-04/)

---

### Post by bodhi.zazen on 2011-04-12
> **sanguinoso said:**
> I believe the home directory for root is /root. However, if you haven't enabled the root account no one will be able to login as root via the terminal or ssh.

That is not entirely true. With the default settings, on can not log in as root using password authentication.

They can log in using other methods, ssh + keys or kerberos.

---

### Post by sanguinoso on 2011-04-12
> **bodhi.zazen said:**
> That is not entirely true. With the default settings, on can not log in as root using password authentication.

They can log in using other methods, ssh + keys or kerberos.

Interesting, I did not know that. I just assumed that since the root login was disabled locally that it would be through ssh and kerberos as well.

---

### Post by Rytron on 2011-04-12
I have enabled root account in a VDI Ubuntu. But what command do I need to edit **.bash_profile for root**?

gksudo gedit ?????

---

### Post by SeijiSensei on 2011-04-12
> **sanguinoso said:**
> Interesting, I did not know that. I just assumed that since the root login was disabled locally that it would be through ssh and kerberos as well.

It's "disabled" in the sense that root doesn't have a password entry in /etc/shadow.  The root account itself must exist since root owns most of the files on the system and runs many of the daemon services as well.

However if your SSH public key is listed in /root/.ssh/authorized_users, you can log in and become the root user that way.


@Rytron
gksudo gedit ?????

Yes, or use a text editor in the terminal like nano: "sudo nano /root/.bash_profile".

---

### Post by sanguinoso on 2011-04-12
Yes that will work.```
gksudo gedit /root/.bash_profile
```

However, enabling the root account is less secure and you may want to take bodhi-zazen's advice and check out ninja.

---

### Post by sanguinoso on 2011-04-12
> 
It's "disabled" in the sense that root doesn't have a password entry in /etc/shadow. The root account itself must exist since root owns most of the files on the system and runs many of the daemon services as well.

However if your SSH public key is listed in /root/.ssh/authorized_users, you can log in and become the root user that way.

I knew of course that it existed I was just under the (albeit incorrect) impression that for ssh PermitRootLogin would be set to No and the similar flag for kerberos.

---

### Post by rosencrantz on 2011-04-12
I can recommend Webmin for settling access questions and managing login permissions.

---

### Post by Rytron on 2011-04-13
Hi guys.

I tried setting up a root login detector and emailer but it doest seem to work.

I remember now, this was the site where I found it: [http://www.unixmen.com/linux-tutorials/1623-9-best-practices-to-secure-your-linux-desktop-and-server](http://www.unixmen.com/linux-tutorials/1623-9-best-practices-to-secure-your-linux-desktop-and-server) Goto 3- Set up a root login detector and emailer.

---

