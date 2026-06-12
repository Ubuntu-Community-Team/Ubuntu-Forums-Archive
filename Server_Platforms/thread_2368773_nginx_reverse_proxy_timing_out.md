---
title: "nginx reverse proxy timing out"
date: 2017-08-14
forum: Server Platforms
---

### Post by maxvandersluis on 2017-08-14
I am trying to set up a development area for myself at home with nginx serving as reverse proxy for apache, nodejs, etc.

I am used to using apache but due to the nature of nginx being a better reverse proxy (or so I've been told many times over) I decided it'd set up reverse proxy for apache as my first victim.
I've read a couple of articles about doing this but I keep timing out.
I've disabled my ufw for it and netstat gives me this:
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      0          10982       806/sshd        
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      109        13878       1264/mysqld     
tcp6       0      0 :::8080                 :::*                    LISTEN      0          30013       11168/apache2   
tcp6       0      0 :::21                   :::*                    LISTEN      0          14444       819/vsftpd      
tcp6       0      0 :::22                   :::*                    LISTEN      0          10984       806/sshd        
udp        0      0 0.0.0.0:68              0.0.0.0:*                           0          14337       804/dhcpcd      
udp        0      0 192.168.178.250:123     0.0.0.0:*                           0          12710       866/ntpd        
udp        0      0 127.0.0.1:123           0.0.0.0:*                           0          12709       866/ntpd        
udp        0      0 0.0.0.0:123             0.0.0.0:*                           0          12703       866/ntpd        
udp        0      0 0.0.0.0:35029           0.0.0.0:*                           105        12242       490/avahi-daemon: r
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           105        12240       490/avahi-daemon: r
udp6       0      0 :::49721                :::*                                105        12243       490/avahi-daemon: r
udp6       0      0 fe80::b6c3:1098:9e7:123 :::*                                0          12712       866/ntpd        
udp6       0      0 ::1:123                 :::*                                0          12711       866/ntpd        
udp6       0      0 :::123                  :::*                                0          12704       866/ntpd        
udp6       0      0 :::5353                 :::*                                105        12241       490/avahi-daemon: r

```
as you can see there is no port 80 yet in /etc/nginx/sites-available/vhosts:
```

server {
        listen 80; 
        root /var/www/local/controller; 
        index index.php index.html index.htm;
        server_name local; 
        location / {
            try_files $uri $uri/ /index.php;
        }
        location ~ \.php$ {
            proxy_set_header X-Real-IP  $remote_addr;
            proxy_set_header X-Forwarded-For $remote_addr;
            proxy_set_header Host $host;
            proxy_pass http://127.0.0.1:8080;
         }
         location ~ /\.ht {
                deny all;
        }
}


```

vhost file apache for reference
```

<VirtualHost *:8080>
  # Admin email, Server Name (domain name), and any aliases
  ServerAdmin webmaster@email.com
  ServerName  local
  # ServerAlias example.com
 
  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.php index.html index.htm
  DocumentRoot /var/www/local/controller
  <Directory /var/www/local/controller>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride all
        Order allow,deny
        Allow from all
        Require all granted
  </Directory>
 
  # Log file locations
  LogLevel warn
  ErrorLog  ${APACHE_LOG_DIR}/error.local.log
  CustomLog ${APACHE_LOG_DIR}/access.local.log combined
 
</VirtualHost>

```
127.0.0.1:8080 works and gives me the apache landing page for that domain.

But when I try to actually got to the domain itself it loads for ages then it'll say [COLOR=#646464][FONT=sans]ERR_CONNECTION_TIMED_OUT

[/FONT][/COLOR]If you need me to provide any other information other then the stuff above it'd be happy to add.

TL;DR:
nginx isn't showing up in netstat/nmap etc, it won't reverse proxy the vhost.


UPDATE:
links in Linux are weird. apparently I can't link like this:
```

ln -s vhosts ../sites-enabled/vhosts

```

Ahh well another few hours of my life well spent, aye?

---

### Post by BloodyIron on 2017-08-15
If you're still stuck I recommend revisiting if your client computer can resolve the hostname/domain that you want to reach in your environment. That's one thing I have had to deal with, split-horizon stuff!

---

### Post by 5mall5nail5 on 2017-08-15
Actually, I think there's a bug in 16.04 Xenial w/ nginx right now.  I just installed a vanilla web host w/ nginx and it won't start complaining about some PID stuff when I do systemctl status nginx, it says its running, but it's not listening.

---

### Post by TheFu on 2017-08-18
I'm running nginx as a reverse proxy on 16.04 without issues.  I do not run apache on the same machine.  

For a reverse proxy, I use the "upstream {}" stanza before the server {} stanza.

Does that help?  [https://www.digitalocean.com/community/tutorials/understanding-nginx-http-proxying-load-balancing-buffering-and-caching](https://www.digitalocean.com/community/tutorials/understanding-nginx-http-proxying-load-balancing-buffering-and-caching) has a simple example about 30% from the top.

---

