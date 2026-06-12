---
title: "Secure http server with apache"
date: 2011-09-25
forum: Server Platforms
---

### Post by vikkyhacks on 2011-09-25
Hello guys i was able to configure my apache2 server last week ... I am able to run my sites at very basic level with some scripts ...I need help on the security side .. My friends told that there are lots of hacks to hack a server down to floor .... The were talking of something called SERVER BRUTE-FORCE , XSS ATTACKS , RDOS and other DOS attacks on server .... I understand that XSS is web based one and i will deal with that later , at present I need help on BRUTE-FORCE, DOS, detection and prevention tools ,,, I also need to other ways of bringing a server down and its prevention ...


...................THANKS IN ADVANCED

---

### Post by Vegan on 2011-09-25
using a strong password for your server so that miscreants cannot hack it 

then security is reasonable, as long as updates are on

---

### Post by Dangertux on 2011-09-25
For web based attacks (XSS sqli  CSRF cst etc) I would install mod security  tutorial here :[http://dangertux.wordpress.com/tutorials/ubuntu-10-04-apache-current-mod-security/](http://dangertux.wordpress.com/tutorials/ubuntu-10-04-apache-current-mod-security/)

Also maybe set up an apparmor profile for apache.  Keep your system updated use strong passwords. 

For brute force of http? Not much you can do there use strong passwords and captcha as well as lock outs. 

For brute force of ssh and inetd services install denyhosts or fail2ban.

---

### Post by vikkyhacks on 2011-09-26
Wow these tools sound so cool ,,, Thanks guys ,,,,but i also need to know about SSH connections and is it possible to change my ordinary HTTP to HTTPS connection ????

---

### Post by vikkyhacks on 2011-09-26
Wow these tools sound so cool ,,, Thanks guys ,,,,but i also need to know about SSH connections and is it possible to change my ordinary HTTP to HTTPS connection ????

---

### Post by Dangertux on 2011-09-26
> **vikkyhacks said:**
> Wow these tools sound so cool ,,, Thanks guys ,,,,but i also need to know about SSH connections and is it possible to change my ordinary HTTP to HTTPS connection ????


SSH is a different ball of wax entirely and really has nothing to do with your web server. SSH offers remote access via an encrypted connection, it also allows file transfer over the same. You can install it via

```

sudo apt-get install openssh-server

```
More information about SSH here : [http://www.openssh.org/manual.html](http://www.openssh.org/manual.html)
And some information about configuring/securing SSH under Ubuntu 10.04 here : [http://dangertux.wordpress.com/tutorials/reasonably-secure-ubuntu-homesmall-business-server-tutorial/#mod3](http://dangertux.wordpress.com/tutorials/reasonably-secure-ubuntu-homesmall-business-server-tutorial/#mod3)


As far as HTTPS goes yes, you can set up an Apache server to accept connections over SSL as well, you can find more information about that here_: _[http://httpd.apache.org/docs/2.0/ssl/](http://httpd.apache.org/docs/2.0/ssl/)

It is important to note that you will need to have to Certificate (preferably signed by a Certificate Authority, these aren't free but usually relatively inexpensive) alternatively you can self sign your certificate, however any time a user visits your site they will receive a warning that it might not be legit due to the self signed cert.

---

### Post by ingramproductions on 2011-10-12
Fail2ban prevents a lot of brute force attacks. Here is a good tutorial on installing and configuring it in Ubuntu 10.04:

[http://itswapshop.com/content/how-install-and-configure-fail2ban-ubuntu-1004-ssh-and-pure-ftpd]("http://itswapshop.com/content/how-install-and-configure-fail2ban-ubuntu-1004-ssh-and-pure-ftpd")

---

### Post by vikkyhacks on 2011-10-12
Thanks guy's one more thing ... I have a http server setup at home ... I upload ani-shell and then bang !!! that is it the user is now able to traverse to any directory on my server ... but on sites like zedge.com 110mb.com if i upload that shell and try to move back my directory i get an error message saying PERMISSION DENIED !!! ... how can i now secure my server .....

[http://sourceforge.net/projects/ani-shell/](http://sourceforge.net/projects/ani-shell/) is where that shell is available ....

---

### Post by CharlesA on 2011-10-12
Why would you even put a shell on a website when you have access to SSH?

At the very least, you should use HTTPS and password protect the page you access it from.

---

### Post by Dangertux on 2011-10-12
> **vikkyhacks said:**
> Thanks guy's one more thing ... I have a http server setup at home ... I upload ani-shell and then bang !!! that is it the user is now able to traverse to any directory on my server ... but on sitehes like zedge.com 110mb.com if i upload that shell and try to move back my directory i get an error message saying PERMISSION DENIED !!! ... how can i now secure my server .....

[http://sourceforge.net/projects/ani-shell/](http://sourceforge.net/projects/ani-shell/) is where that shell is available ....

Umm, it's a web-shell and is designed to leverage systems compromised via remote file inclusion/upload. I'm confused as to what your question is?

If you want to protect directories above that where ani-shell is placed you need to use more restrictive permissions. However, I'm getting the feeling this isn't the question you're asking.

Also the reason you can't do that on hosting sites is because you're are chrooted in your webroot. Again if you look at the way your default Apache install handles file permissions you will see why that script can be used to read outside webroot.

If you take a deeper look at the features
> 
                                                                **Features**

                                                       
[LIST]
[*]Shell
[*]Mass Mailer
[*]DDos
[*]Web-Server Fuzzer
[*]Uploader
[*]Design
[*]Login
[*]Mass Code Injector (Appender and Overwriter)
[*]Encoded Title
[*]Back Connect
[*]Bind Shell
[*]Lock Mode Customisable
[*]Tracebacks (email alerts)
[*]PHP Evaluate
[*]PHP MD5 Cracker
[*]Anti-Crawler
[*]Mass Deface
[/LIST]
It starts looking a lot like something we can't really support you with here. What exactly are you asking for help in doing?

---

### Post by CharlesA on 2011-10-12
In light of what Dangertux has said, this thread is closed as we don't support this sort of thing here.

---

