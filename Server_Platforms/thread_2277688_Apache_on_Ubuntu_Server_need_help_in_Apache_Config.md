---
title: "Apache on Ubuntu Server need help in Apache Configuration"
date: 2015-05-10
forum: Server Platforms
---

### Post by Prime_R. on 2015-05-10
Good day to all! its my first post in this forum and i'm new in ubuntu and apache.

I have a problem about my server. First let me describe my situation to you. 
I have a web server in ubuntu running in apache, at first it was really running well using a public ip provided by my ISP. However, the problem starts when my ISP change their configuration. Instead of providing me a separate IP address for my server, i believe they use port forwarding. The public ip is now 120.72.20.79:90 which forward to the server IP which is 192.168.254.100,i don't have problem accessing my server using local ip. i configure my server with two IP (192.168.254.100 and 192.168.6.117). I can access the server using 120.72.20.79:90 however its the default apache page comes out. i have a separate /sites-enabled/climex.conf with this configuration: 

<VirtualHost *:80>
    DocumentRoot "/www/example1"
    ServerName 192.168.254.100
    ServerAlias 120.72.2079:90
</VirtualHost>

Im not sure if putting ServerAlias with the public IP can resolve my problem. Really need help. 

thanks

---

### Post by nerdtron on 2015-05-11
Nope, don't put the public IP on the server if you are already port forwarding to it. 

I'll put your Public IP with the port 90 on the web browser and I see your default apache page.
From my browser here in the  Philippines, i can access the page [http://120.72.20.79:90/](http://120.72.20.79:90/) and it shows the default apache page. The only problem I see is that the port 90 is used instead of the default 80. If the port forward is controlled by you, then it would be better to change it to port 80, else, you ISP might need to change it.

---

### Post by Prime_R. on 2015-05-11
Its the ISP who change it to port 90. i can't do anything about it. they (ISP) are using it for other purpose. So i need to use the port 90. what are the things i need to do to access my server using port 90?
do i need to change 80 >> 90 
<VirtualHost *:[COLOR=#ff0000]90[/COLOR]>
    DocumentRoot "/www/example1"
    ServerName 192.168.254.100
    ServerAlias 120.72.2079:90
</VirtualHost>

---

### Post by SeijiSensei on 2015-05-11
You can't do anything to fix this.  Anyone wishing to see your site will need to use [http://120.72.2079:90/](http://120.72.2079:90/) or [http://somehost.example.com:90/](http://somehost.example.com:90/).  ServerName and ServerAlias have nothing to do with this.  They specify the textual hostnames used in URLs like 
```

ServerName    ubuntuforums.org
ServerAlias   www.ubuntuforums.org

```

If you want to use the correct port, 80, you need to change providers, move your site to a public hosting service, or rent a [virtual machine](http://www.linode.com/).

---

### Post by Prime_R. on 2015-05-11
Thank you for the info..maybe i need to talk to my provider now.

---

### Post by Prime_R. on 2015-05-11
I talked with my provider, he told me that when 120.72.20.79:90 is used, it is directed to my server using 192.168.254.100 in port 80. did i miss something here?

---

### Post by nerdtron on 2015-05-12
Are you using Named Virtual hosting? because, that is the correct behavior if you do.


BTW, you can bind the IP address to the virtual host using:
Add to the apache config:
```
Listen 192.168.254.100:80
```

Then your virtual host config should start at:
```
<VirtualHost 192.168.254.100:80>
```

Then restart apache.

---

### Post by SeijiSensei on 2015-05-12
> **Prime_R. said:**
> I talked with my provider, he told me that when 120.72.20.79:90 is used, it is directed to my server using 192.168.254.100 in port 80. did i miss something here?

Yes.  It means that anyone wanting to visit your site needs to tack :90 onto the end of the hostname or IP.  That's inconvenient, and many people will forget. You site also won't be indexed by search services.

---

### Post by Prime_R. on 2015-05-12
yes. i understand. However, the server is only intended for my partners. Thanks guys. Finally got it working. 

Thanks!

---

