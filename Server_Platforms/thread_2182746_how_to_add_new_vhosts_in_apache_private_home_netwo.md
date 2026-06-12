---
title: "how to add new vhosts in apache private home network"
date: 2013-10-22
forum: Server Platforms
---

### Post by johnycage on 2013-10-22
Hello,
This is more of Apache problem and may have nothing to do with Ubuntu Server but still, I would like to know how to add virtualhost conf file in apache vhosts.

 I run Ubuntu 12.04 LTS as LAMP server for web-development & experiements. I also use it as file/ media server & keep my mp3/ video clips on it. So with regular /var/www, I would also love to include my media directories such as /srv/samba/mp3. 
It shoudl be accessible on my private home network, so I'm bringing them in http because samba/smb doesnt do the trick for you to view them from smartphones. 

I created new directory under 
/etc/apache2/sites-available/songs
as follows

```

<VirtualHost *:80>
DocumentRoot /srv/samba/mp3
ServerName 192.168.1.2/songs/
</VirtualHost>

```

But it's not working. I dont know what is the right way to add another virtualhost.

Apache Version: Apache/2.2.22 (Ubuntu Server 12.04 LTS)

---

### Post by SeijiSensei on 2013-10-22
Unless you use "[name-based virtual hosting]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html")", you need to set up your site as a subdirectory of /var/www.  Rather than moving all the files, you can create a "symbolic link" from your mp3 directory to /var/www like this:

```
cd /var/www
sudo ln -s /srv/samba/mp3 songs

```

If you type "ls /var/www" you'll see the link to /srv/samba/mp3.  It should be called /var/www/songs.

On 12.04 that should be enough since the default configuration permits symlinks.  Now just point a browser at [http://192.168.1.2/songs](http://192.168.1.2/songs) and see what you get.

---

### Post by johnycage on 2013-10-23
@seijiSensei Thanks for the tip. It worked. Thank you. 
But treating this as an academic question, how would one add another website/vhost located to different location? What am I missing in my vhost conf file?

I had disabled default conf by 
```
sudo a2dissite default
```
before adding new vhost file..

---

### Post by SeijiSensei on 2013-10-23
Read the linked document on name-based hosting.  Basically the server relies on the server name passed in the URL to determine which site to display.  So you would need to use unique names for each virtual host.  That requires either adding entries to the clients' hosts file that would all point to the common IP address, 192.168.1.2, or setting up a DNS server.  

For instance, if you were connecting from a Linux host, you could add an entry to /etc/hosts like this:

```
192.168.1.2    myserver site1  site2 site3
```

The first entry is the server's "canonical" name; the ones following are aliases.  Then if you set up virtual hosts with "ServerName site1", "ServerName site2", etc., you can define separate webservers.  Read [this section]("https://help.ubuntu.com/lts/serverguide/httpd.html#http-configuration") of the Ubuntu Server Guide for more information.

---

