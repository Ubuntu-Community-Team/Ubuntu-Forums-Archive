---
title: "Can't get into http://localhost/xampp/"
date: 2015-08-18
forum: Server Platforms
---

### Post by mantazasas on 2015-08-18
Hello i can't get into [http://localhost/xampp/](http://localhost/xampp/) after installing xampp-linux-x64-5.6.11-1-installer.run
I'm get this: 
```

Object not found!The requested URL was not found on this server. If you entered the URL manually please check your spelling and try again.
If you think this is a server error, please contact the webmaster.
Error 404localhost
Apache/2.4.16 (Unix) OpenSSL/1.0.1p PHP/5.6.11 mod_perl/2.0.8-dev Perl/v5.16.3

```

Maybe someone know how to solve the issue ? 
Thanks in advice.

---

### Post by slickymaster on 2015-08-18
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by flaymond on 2015-08-18
The executable you downloaded is from here? - [https://www.apachefriends.org/download.html](https://www.apachefriends.org/download.html)

have you tried by navigating to - [http://localhost](http://localhost) or [http://localhost/xampp/index.php](http://localhost/xampp/index.php) first?

On LAMP, by navigating to the address, it will display a default page if it's working. I also see that the testing phase is quite similar - [https://www.apachefriends.org/faq_linux.html](https://www.apachefriends.org/faq_linux.html)



-o-




For me, it's better to install from the repository the easy way if I want to try Web development with PHP5, and by that this webpage provide a good tutorial to do that -
[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu)

Anyway, I found 2 solutions related with your question from old ubuntu thread - [http://ubuntuforums.org/showthread.php?t=1345947](http://ubuntuforums.org/showthread.php?t=1345947)

and from askubuntu - [http://askubuntu.com/questions/417771/object-not-found-in-lampp-ubuntu-13-10](http://askubuntu.com/questions/417771/object-not-found-in-lampp-ubuntu-13-10)

and a tutorial to set (xampp) from the ubuntu forums itself - [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)


You had to try which best suited with your current situation. Good luck!

---

### Post by mantazasas on 2015-08-18
Thanks for reply but i still can't get to xampp main page just lampp dashboard and  when i go to my own project's i get this: [PHP]

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/opt/lampp/htdocs/projektai/bandom2/index.php' (include_path='.:/opt/lampp/lib/php') in Unknown on line 0
[/PHP]

---

### Post by nerdtron on 2015-08-18
Be sure that your web folders are world readable. That is 
```
sudo chmod -R a+r /path/to/lampp
```

And be it is owned by the user running the webserver, probably either www-data user or the apache user
```
 sudo chown -R www-data:www-data /path/to/lampp 
```

---

### Post by mantazasas on 2015-08-19
Thank you now i can open my projects , but still i can't open [http://localhost/xampp](http://localhost/xampp) ...

---

### Post by nerdtron on 2015-08-19
Do you SSH to the server from your desktop? If yes, then you won't be able to access [http://localhost/xampp](http://localhost/xampp)  You should enter the domain name or IP address of the server like [http://192.168.x.x/xampp](http://192.168.x.x/xampp)

---

### Post by mantazasas on 2015-08-19
I downloaded and installed it from here: [https://www.apachefriends.org/download.html](https://www.apachefriends.org/download.html) 5.6.11 ver and i can't acess it neither by both localhost and 192.168.x.x ...

---

### Post by nerdtron on 2015-08-19
What error on the browser are you having? Did you configure apache to the DocumentRoot of XAMPP?
Is there a firewall? What is the output of 
```
sudo netstat -tulpn 
```

---

### Post by mantazasas on 2015-08-19
Error in both cases is:
```

**Object not found!**

[COLOR=#000000][FONT=Times New Roman]The requested URL was not found on this server. The link on the [referring page]("http://ubuntuforums.org/showthread.php%3ft=2291140") seems to be wrong or outdated. Please inform the author of [that page]("http://ubuntuforums.org/showthread.php%3ft=2291140") about the error.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]If you think this is a server error, please contact the [EMAIL="you@example.com"]webmaster[/EMAIL].[/FONT][/COLOR]
**Error 404**

[localhost]("http://localhost/")
Apache/2.4.16 (Unix) OpenSSL/1.0.1p PHP/5.6.11 mod_perl/2.0.8-dev Perl/v5.16.3

```


Output of netstat:
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1366/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      2185/cupsd      
tcp6       0      0 :::3306                 :::*                    LISTEN      5119/mysqld     
tcp6       0      0 :::80                   :::*                    LISTEN      4748/httpd      
tcp6       0      0 ::1:631                 :::*                    LISTEN      2185/cupsd      
tcp6       0      0 :::443                  :::*                    LISTEN      4748/httpd      
udp        0      0 127.0.1.1:53            0.0.0.0:*                           1366/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1352/dhclient   
udp        0      0 0.0.0.0:61629           0.0.0.0:*                           1352/dhclient   
udp        0      0 0.0.0.0:631             0.0.0.0:*                           1109/cups-browsed
udp        0      0 0.0.0.0:50231           0.0.0.0:*                           810/avahi-daemon: r
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           5191/chrome     
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           810/avahi-daemon: r
udp6       0      0 :::37060                :::*                                810/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                810/avahi-daemon: r
udp6       0      0 :::30581                :::*                                1352/dhclient   



```

And how do i can to [COLOR=#000000]configure apache to the DocumentRoot of XAMPP  ? [/COLOR]

---

### Post by krtica on 2015-08-25
There is no /opt/lampp/htdocs/xampp folder after 5.6.11 installation.
There is only a new XAMPP dashboard.
[https://www.apachefriends.org/blog/new_xampp_20150723.html](https://www.apachefriends.org/blog/new_xampp_20150723.html)

---

