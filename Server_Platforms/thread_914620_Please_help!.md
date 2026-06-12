---
title: "Please help!"
date: 2008-09-09
forum: Server Platforms
---

### Post by rebelyell on 2008-09-09
Hey everyone, I run a mustang website. [www.sn95forums.com](www.sn95forums.com)

I made the html portion of the website, and I keep it up to date. Well I did, up until January when our FTP went offline.

So me and the rest of the staff @ sn95forums, Emailed our server owner asking for help. He refuses. He either doesn't answer emails, or askes the same stupid question, which is what is your root password. Well I got him on the phone, he told me I needed to use shell access to fix the problem...

Well. I don't know anything about root passwords or shell access. I tried rebooting our server, that didn't work. I'm good with HTML, but anything else I'm lost.

I don't even know where to begin figuring this out. But I am very motivated right now. I need some direction. Please help me figure this out.

---

### Post by Oldsoldier2003 on 2008-09-09
You would probably get a better response if you posted an abbreviated version of this post in the [Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339") subforum with a descriptive title.

---

### Post by rebelyell on 2008-09-09
> **Oldsoldier2003 said:**
> You would probably get a better response if you posted an abbreviated version of this post in the [Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339") subforum with a descriptive title.

What do you mean by abbreviated?

Can you move it for me? Or should I repost it?

Thanks for bearing with me... I came across this website doing a random search. I have no idea what ubuntu is. I am so lost. Any help I can get I appreciate.

---

### Post by Sef on 2008-09-09
> I have no idea what ubuntu is.

What is your operating system that you are running your server on?

---

### Post by rebelyell on 2008-09-09
Server Information	

Hostname -	6679167162.us.coreisp.nl
Plesk version - 	psa v8.0.0_build80060331.13 os_CentOS 4.2
Operating system -	Linux 2.6.9-11.EL

---

### Post by Bucky Ball on 2008-09-09
Ubuntu is a Linux distibution, Linux being based on Unix, which is what your server is probably running with. :)

---

### Post by jerome1232 on 2008-09-09
> **rebelyell said:**
> Server Information	

Hostname -	6679167162.us.coreisp.nl
Plesk version - 	psa v8.0.0_build80060331.13 os_CentOS 4.2
Operating system -	Linux 2.6.9-11.EL

It looks like you running CentOS 4.2 on a 2.6 kernel, I know nothing of CentOS but looking at it's website [http://www.centos.org/](http://www.centos.org/) it's debian based, so is Ubuntu so alot of things "should" be similiar.

Do you know what program is being used to host the ftp service?

edit: oops it's NOT based on debian sorry.

---

### Post by rebelyell on 2008-09-09
> **jerome1232 said:**
> It looks like you running CentOS 4.2 on a 2.6 kernel, I know nothing of CentOS but looking at it's website [http://www.centos.org/](http://www.centos.org/) it's debian based, so is Ubuntu so alot of things "should" be similiar.

Do you know what program is being used to host the ftp service?

psaftp

---

### Post by Sef on 2008-09-09
> It looks like you running CentOS 4.2 on a 2.6 kernel, I know nothing of CentOS but looking at it's website [http://www.centos.org/](http://www.centos.org/) it's debian based, so is Ubuntu so alot of things "should" be similiar.


That is not correct.  Centos is based on RedHat, so it is [RPM based]("http://www.centos.org/modules/smartfaq/faq.php?faqid=33").

---

### Post by jerome1232 on 2008-09-09
My bad, I just glanced at the page and saw debian, looking at again it's saying it's not based on debian.

---

### Post by inphektion on 2008-09-09
Plesk is a big pile of ****.  However since you don't know anything about shell access you can or should be able to use Plesk to start the FTP service.  However if the server owner says you need shell access to fix the problem then you very well may as Plesk is really just a GUI-ish control panel for setting things up on the server.  I usually uninstall plesk and manage everything myself.  
Either way you either need to turn on FTP from within Plesk, open the ftp ports in the firewall, or let the server owner login and fix the issue via shell.

---

### Post by Rocket2DMn on 2008-09-09
Threads merged.

---

### Post by rebelyell on 2008-09-09
> **inphektion said:**
> Plesk is a big pile of ****.  However since you don't know anything about shell access you can or should be able to use Plesk to start the FTP service.  However if the server owner says you need shell access to fix the problem then you very well may as Plesk is really just a GUI-ish control panel for setting things up on the server.  I usually uninstall plesk and manage everything myself.  
Either way you either need to turn on FTP from within Plesk, open the ftp ports in the firewall, or let the server owner login and fix the issue via shell.

ok... so open ports? Which ones?

---

### Post by rebelyell on 2008-09-09
The Firewall is set to allow FTP.

Any other ideas?

---

### Post by rebelyell on 2008-09-09
Nobody can help?

Please, give me some things to try. I figured out the shell access, I just dont know what to do from there.

---

