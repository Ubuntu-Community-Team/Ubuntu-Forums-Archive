---
title: "So I just installed the LAMP server"
date: 2008-07-01
forum: Server Platforms
---

### Post by dethredic on 2008-07-01
Ok, I just installed the Ubuntu 7.1 LAMP server and the XUbuntu desktop environment. I have set up my network. 

I still need to install bind9, but after that what configuration/setting up do I need to do to get my server online?

---

### Post by windependence on 2008-07-02
What are you going to do with this box? Are you gonna run a static web page or pages, or a forum? Or CMS?

You probably don't need bind 9 unless you have a ton of computers on your network, otherwise, there is no need for you to run your own DNS server.

-Tim

---

### Post by dethredic on 2008-07-03
Umm, it is just going to host a webpage for my dad's work. It will be mainly for sharing files and having them all in 1 place. I see very few databases or php in my future. I mainly just need apache up and if I don't need Bind9 some other way to get the domain name working.

---

### Post by windependence on 2008-07-03
You just need Apache for this. You shouldn't need bind9 for sure and I doubt you need MySQL.

-Tim

---

### Post by ixus_123 on 2008-07-03
You wont need bind at all.

The only reason to install DNS is if you want to use names instead of IP addesses to access computers on your local network.

If your ISP has given you a static address you probably already have a namespace reserved for this.  If not you can register a domain.  Even without a static IP, service like DynamicDNS should make webserving a personal site good enough.  You ISP will also have name servers that you are probably using (inputted into your router).

You can test if apache is up by finding your IP address (local and wan) and navigating to that.

Apache works pretty much out of the box and all you have to do is place your content in /var/www

You should get an Apache test page on your LAN IP.  If you can't access that page on your WAN - ie from your outside address, then your firewall needs to be opened up for forward port 80.

---

### Post by dethredic on 2008-07-04
Ok, I will do some of those things tomorrow and report back. Also, it would be easier I think if I did the work on the webpages etc on my main desktop computer and transfered them to the server. I can think of two ways of doing this. Using an external HDD, and moving it over or usinf FTP. If I use FTP, I don't have to run around as much and I guess I can remove the desktop enviroment.

How hard will it be for me to install and configure a FTP server or get that setup?

---

### Post by jombeewoof on 2008-07-04
> **dethredic said:**
> ...How hard will it be for me to install and configure a FTP server or get that setup?

ftp server is very easy.
install vsftp and use this config.

```
dirmessage_enable=YES
anonymous_enable=NO
anon_world_readable_only=YES
syslog_enable=YES
connect_from_port_20=YES
pam_service_name=vsftpd
listen=YES
ssl_enable=NO
anon_mkdir_write_enable=NO
anon_upload_enable=NO
chroot_local_user=YES
ftpd_banner=Welcome message
idle_session_timeout=900
local_enable=YES
local_root=/ftp
log_ftp_protocol=NO
max_clients=10
max_per_ip=5
pasv_enable=YES
pasv_max_port=40500
pasv_min_port=40000
write_enable=YES
user_config_dir=/etc/vsftp_user_dir/
download_enable=YES

```

It will allow local users to log in with their regular user accounts and lock them to the /ftp directory. You might want to change this to /var/www or whatever.

---

### Post by windependence on 2008-07-04
> **dethredic said:**
> Ok, I will do some of those things tomorrow and report back. Also, it would be easier I think if I did the work on the webpages etc on my main desktop computer and transfered them to the server. I can think of two ways of doing this. Using an external HDD, and moving it over or usinf FTP. If I use FTP, I don't have to run around as much and I guess I can remove the desktop enviroment.

How hard will it be for me to install and configure a FTP server or get that setup?

You don't need ftp. If you are on a windows box you can just install WinSCP on your windoze box and transfer the files securely that way.

-Tim

---

### Post by dethredic on 2008-07-04
> **windependence said:**
> You don't need ftp. If you are on a windows box you can just install WinSCP on your windoze box and transfer the files securely that way.

-Tim

I am on Ubuntu on my main desktop as well.

EDIT: Apache is up and running.

---

### Post by dethredic on 2008-07-04
> **ixus_123 said:**
> You wont need bind at all.

The only reason to install DNS is if you want to use names instead of IP addesses to access computers on your local network.

If your ISP has given you a static address you probably already have a namespace reserved for this.  If not you can register a domain.  Even without a static IP, service like DynamicDNS should make webserving a personal site good enough.  You ISP will also have name servers that you are probably using (inputted into your router).


I believe I am supposed to have a static IP, but it does change every month or so (I am not too sure). I have a domain name purchased. I didn't find any nameservers in my router (WRT54G) after going through all the tabs.
I will look at DynamicDNS.

---

### Post by windependence on 2008-07-04
> **dethredic said:**
> I am on Ubuntu on my main desktop as well.

EDIT: Apache is up and running.

Even better yet. You should be able to open up a Konqueror window or Nautilus window and sftp directly to your server.

[http://ubuntuforums.org/archive/index.php/t-289908.html](http://ubuntuforums.org/archive/index.php/t-289908.html)


-Tim

---

### Post by dethredic on 2008-07-04
> **windependence said:**
> Even better yet. You should be able to open up a Konqueror window or Nautilus window and sftp directly to your server.

[http://ubuntuforums.org/archive/index.php/t-289908.html](http://ubuntuforums.org/archive/index.php/t-289908.html)


-Tim

Actually, I just used SSH. (I had some familiarity with it).

Everything is working, but the domain name. The site can be accessed by IP. What is the easiest way to do this?

---

### Post by windependence on 2008-07-05
You have to set up DNS records with your domain registrar and point them at your IP.

-Tim

---

### Post by dominiquec on 2008-07-05
Is this supposed to be a public web server?  If it is, you should probably just subscribe to a web hosting account.  Several companies out there, many of them offering it at around $5-$7 a month.  Saves you all this trouble of setting up, plus, it'll be on 24x7.

---

### Post by windependence on 2008-07-05
> **dominiquec said:**
> Is this supposed to be a public web server?  If it is, you should probably just subscribe to a web hosting account.  Several companies out there, many of them offering it at around $5-$7 a month.  Saves you all this trouble of setting up, plus, it'll be on 24x7.

For that price you are going to get a shared hosting account with HUNDREDS of other sites on the same server. You will only be able to run what your hosting company lets you run and you will not have physical access to your server. If that's what you want, that's fine but the whole reason to host your own is to avoid these problems or even learn about hosting. For me, I have to have access to my servers period.

-Tim

---

### Post by dethredic on 2008-07-05
> **windependence said:**
> For that price you are going to get a shared hosting account with HUNDREDS of other sites on the same server. You will only be able to run what your hosting company lets you run and you will not have physical access to your server. If that's what you want, that's fine but the whole reason to host your own is to avoid these problems or even learn about hosting. For me, I have to have access to my servers period.

-Tim

This as well as it is fun to know these things and the knowledge could come in handy sometime.


> You have to set up DNS records with your domain registrar and point them at your IP.

-Tim
So, pretty much I need nameservers. That is the extent of my knowledge. I was going to use Bind9 but someone said that was a bad idea.

---

### Post by skunkbad on 2008-07-05
> **dethredic said:**
> So, pretty much I need nameservers. That is the extent of my knowledge. I was going to use Bind9 but someone said that was a bad idea.

All you need to do is go buy a domain, and set up a zoneedit account. I buy my domains from godaddy.com, and zoneedit is at zoneedit.com. When you buy your domain, you will go to the settings and set your nameservers to what zoneedit tells you. Then in your zoneedit account, you set the IP (A record) to your WAN IP. It's really that simple. Once you do that, just install the ddclient service with apt-get:

sudo apt-get install ddclient

Set up ddclient to grab your WAN IP from the router or the web, and it will auto update your zoneedit A record anytime your WAN IP changes. You will then have access to your server by using SSH anywhere you can install putty, or if your on a mac you can just use the terminal. If you like FileZilla, the new FZ3 will work in SSH mode.

Oh yeah, you will need to do the port forwarding on your router so that SSH can get through. This is port 22 by default.

One last thing to consider is that if the server is getting its LAN IP from the router through DHCP, you should make your server use a static IP so that if the router is reset you won't have to go in and manually change your port forwarding setup.

Easily done and ready to enjoy in 30 minutes.:)

---

### Post by windependence on 2008-07-05
Well you don't need to run your own nameservers, you can use your registrar's. If you have a static IP (recommended) you don't need zoneedit or any other dyndns stuff. If you do have to go that way, I personally like no-ip better than the rest, but still there will be some people who cannot access your site. You may never know it because they can't get there, but there are many companies who do not let their employees go to redirected sites by way of their routing policy. Most of your traffic will come from people surfing from work even if they don't admit it. :)

-Tim

---

### Post by dethredic on 2008-07-06
> **windependence said:**
> Well you don't need to run your own nameservers, you can use your **registrar's**. If you have a static IP (recommended) you don't need zoneedit or any other dyndns stuff. If you do have to go that way, I personally like no-ip better than the rest, but still there will be some people who cannot access your site. You may never know it because they can't get there, but there are many companies who do not let their employees go to redirected sites by way of their routing policy. Most of your traffic will come from people surfing from work even if they don't admit it. :)

-Tim

By this do you mean my ISP's? I have not found any by them. Where would I get those?

---

### Post by dethredic on 2008-07-06
Ok, I just installed Bind9 and set it up. My domain name is up and running.

Two more quick questions:
1) I have a .htaccess file in one of my directories, but it does not appear to be working. It is supposed to make a password required, but that is not happening. The files work when I uploaded them to a test server, so I am guessing it is something to do with the server and how it is configured.

2) Now that the server is set up I do not really need the xubuntu desktop, but I would like to keep it as a backup. Currently it boots straight into the desktop. Is there any way to make it boot into the command line to start and then I can type in startx if I need to start the desktop environment?

---

### Post by cariboo on 2008-07-06
Just remove gdm from the rc*.d  and you should be ok 

```
/etc/rc2.d/S30gdm -> ../init.d/gdm
```

There will be others in the other run levels.

Jim

---

### Post by dethredic on 2008-07-07
What do you mean by:
> There will be others in the other run levels.

---

### Post by windependence on 2008-07-07
Each runlevel has it's own init script. For example

/etc/rc2.d
/etc/rc3.d
/etc/rc4.d

......and so on. You will want to comment out the startup scripts for the runlevels where you don't want X to start by default.

-Tim

---

### Post by dethredic on 2008-07-08
I am still not fully understanding. Will I need to uncomment all the run levels, or just 1?

I want apache and bind9 etc to be running when I turn it on, but I don't want like the xubuntu desktop to start so I can minimize the strain on the computer.

---

### Post by windependence on 2008-07-08
[http://techpatterns.com/forums/about230.html](http://techpatterns.com/forums/about230.html)

-Tim

---

### Post by dethredic on 2008-07-10
> **windependence said:**
> [http://techpatterns.com/forums/about230.html](http://techpatterns.com/forums/about230.html)

-Tim

Great thanks for the link. With that information, I did some searching and found [this]("http://ubuntuforums.org/showpost.php?p=35758&postcount=6").

I think that is exactly what you guys were talking about. I completed his instructions. I will find out tomorrow if disabling the gdm worked.

EDIT: It worked great. THanks guys

---

