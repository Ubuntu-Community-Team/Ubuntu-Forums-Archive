---
title: "Problems with ACID / BASE interface for SNORT IDS on remote host"
date: 2010-12-09
forum: Server Platforms
---

### Post by banescusebi on 2010-12-09
I've just installed SNORT and ACID/BASE following this step by step tutorial: [https://help.ubuntu.com/community/SnortIDS](https://help.ubuntu.com/community/SnortIDS)  on a remote host over SSH. The main difference being that I have  already setup a firewall that fillers all incoming traffic except for  SSH, HTTPS and loopback.
  
Now when I try to access [https://domain.xx/acidbase/base_db_setup.php](https://domain.xx/acidbase/base_db_setup.php) , i.e. acidbase's front end in  the final configuration step I get the following error:

```
** 403 FORBIDDEN**
You don't have permission to access /acidbase/base_db_setup.php on this server.
```  I have already run this command:
```
:/$ sudo sed -i "s#allow\ from\ 127.0.0.0/255.0.0.0#allow\ from\  127.0.0.0/255.0.0.0\ 10.10.1.10/255.255.255.0 my-vpn-gateway.xx#"  /etc/acidbase/apache.conf
``` and restarted Apache.
  

I also tried to access the URL from within my SSH session via Lynx  web browser but whenever I type: https ://localhost/ it tells me:
```
Unable to make secure connection to remote host.
```However when I type: https ://mydomain.xx/ it works. So maybe I also have some bug in my Apache configuration.


  The remote host is running an Apache 2.2 web server, and I disabled  the VirtualHost on port 80 and left only the one for port 443.


  Any help would be greatly appreciated.
  

Thank you,
Benny

---

### Post by windependence on 2010-12-09
Do you have 
```
 
NameVirtualHost *:80
Listen 80

```in your ports.conf file?
 
-Tim

---

### Post by kat_ams on 2010-12-17
The setup has moved to here

[http://localhost/acidbase/setup/](http://localhost/acidbase/setup/)

But if you type the same password as the snort user it will work without configuration at

[http://localhost/acidbase](http://localhost/acidbase)

---

