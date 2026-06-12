---
title: "LAN website not accessible from any Windows LAN browsers"
date: 2011-01-12
forum: Server Platforms
---

### Post by molinus on 2011-01-12
I have a website on a standalone Ubuntu server (using virtual host). 
I can access the site from 3 different Macs using Safari, Firefox and Chrome.
I can access the site from my Mac using virtual Windows XP Pro in VirtualBox.

But I cannot access the site from any Windows machine on the LAN, and it's frustrating :frown:
I cannot get to it with name resolution nor with IP address.

Here are some of my related configs:

In sites-available (also in sites-enabled)
_mywebsite.conf_
<VirtualHost *:80>
DocumentRoot /var/www/mywebsite
ServerName mywebsite
ServerAlias *mywebsite
Directory /var/www/mywebsite
</VirtualHost>

_ports.conf_
NameVirtualHost *:80
Listen 80

_UFW_
22                         ALLOW IN    Anywhere
80                         ALLOW IN    Anywhere
8080                       ALLOW IN    Anywhere
137/udp                    ALLOW IN    192.168.2.0/24
138/udp                    ALLOW IN    192.168.2.0/24
139/tcp                    ALLOW IN    192.168.2.0/24
445/tcp                    ALLOW IN    192.168.2.0/24
3306/tcp                   ALLOW IN    192.168.2.0/24

Does anyone know why I can get my site on Macs, but not Windows?

---

### Post by R.Bucky on 2011-01-12
If you are not operating DNS, you need to add your sites to the Windows /etc/hosts. Here is a how-to [http://nwlinux.com/change-the-etchosts-values-in-windows/]("http://nwlinux.com/change-the-etchosts-values-in-windows/")

---

### Post by molinus on 2011-01-12
Thanks for the reply Mark, but I already have the host file populated on each Windows machine with all IPs and names, plus running Ubuntu as the WINS server.
Network name resolution works perfectly fine for network file sharing on all machines, Windows, Linux & Mac.
Samba works fine too, and the Windows machines can access WWW with no problems.
I can access [COLOR="Sienna"]mywebsite[/COLOR] from the Macs and Linux machines, but not the Windows machines.
I was able to access [COLOR="Sienna"]mywebsite[/COLOR] from one Windows machine by turning off its Windows firewall.  I haven't tried it on any others yet, because I'm wondering what Windows firewall exception is needed to make it work - ports 137, 138, 139, 445 and 3306 are already open in the Windows firewall, and 80 is open, since there is never a problem accessing any www sites.

---

### Post by airtonix on 2011-01-13
WINS is only an layer seven protocol, so it only resolves name resolution for Samba.

To resolve names at the level required by apache you need to have a layer three protocol service like avahi or bind running.

This is why your macs can resolve the address but no the windows machines.

easiest way to address this and minimise the amount of host file editing is to install "bonjour printing services for windows", this allows windows to see the avahi/bonjour broadcasts on your LAN.

You'll also need to allow traffic on port 5353 udp on your local computers for avahi/bonjour to work properly for your local area network.

Your ability to access websites on the internet by hostname is nothing to do with you being unable to access the website on your local network.

You might also be interested in this : 

[http://stackoverflow.com/questions/775233/how-to-route-all-subdomains-to-a-single-host-using-mdns/3896533#3896533](http://stackoverflow.com/questions/775233/how-to-route-all-subdomains-to-a-single-host-using-mdns/3896533#3896533)

---

### Post by molinus on 2011-01-13
Thanks for the reply, but that is what is so maddening about this.

Avahi has always been running on the Ubuntu server, and Bonjour has always been running on Windows.
I mentioned Samba and WWW access to show that there are no networking issues.

I have an exact copy of mywebsite plus several other websites running through Xampp on my Mac, and all the machines (Mac, Windows & Linux) can access them all, both with name resolution and IP address.

So it must be a problem with a configuration in either Ubuntu or Apache2.  That is why I put my conf info in the first post.

I am befuddled.

---

### Post by arrrghhh on 2011-01-13
> **molinus said:**
> So it must be a problem with a configuration in either Ubuntu or Apache2.  That is why I put my conf info in the first post.

Why do you think that?  Especially if turning off the Windows firewall fixed it on that one Win machine...

I also assume all these machines are on the same switch, vlan, router, what-have-you?

---

### Post by molinus on 2011-01-13
I apologize, I should have mentioned that my Windows firewall statement was incorrect.

When tried to access mywebsite with the firewall off, I entered the IP for the Mac-hosted mywebsite by mistake in my frustration and haste.

Firewall or not, using Window machines, I cannot get to the Ubuntu-hosted mywebsite via IP or name, but I can get to all of the Mac-hosted sites.

I don't know if this could be part of the problem or solution, but the Mac-hosted sites use a single httpd.conf under xampp, whereas the Ubuntu-hosted sites use individual .conf files under Sites-Available & SItes-Enabled.

Also, yes - 1 gateway router for ISP, and 1 24-port switch - 1 subnet.

---

### Post by chrislynch8 on 2011-01-13
Ok the Wins PCs that cannot access the site. Can you do the Following.

1: Ping the IP address of the Server - do you get a respond.
2: Can you access the site as serverip/mywebsite
3: Does entering serverip into the browser bring to you to the default apache page

Rgds
Chris

---

### Post by molinus on 2011-01-13
Thanks for the tips Chris - I assumed there was connectivity since mounted network drives worked.

I don't know the explanation, but here is what happened:

Pinging the server IP (and Name) was fine from all the Macs, but timed out from all the PCs.

Then on 2 different PCs, I got the same results by doing this:
1) Pinged server IP (and Name) again (timed out)
2) Went to Network Browser, and even though no ping response, found the server name listed and connected to a shared folder on the server, then closed it.
*Note: I did not have to log in to the server - I just opened the shared folder from Network Browser.*

After that, pinging the server IP (and Name) worked and mywebsite was available.

I don't know why I would have to connect to the server via Network Browser first, to make the website available, and only from PCs.

---

### Post by molinus on 2011-01-13
**Update:**

I just went back after lunch, and cannot get to the server via the Network Browser, nor can I get mywebsite again (just from the PCs).

During that time, there have been no interactions (no input/output) on either the server or the PCs!!!

Something is severely fubar with Ubuntu.

I think maybe WINS is not working correctly - it seems to work intermittently, so I am considering setting up BIND DNS on Ubuntu.

Does anyone think BIND DNS might solve the website issues and Network Browsing from all machines?

---

### Post by arrrghhh on 2011-01-13
> **molinus said:**
> **Update:**

I just went back after lunch, and cannot get to the server via the Network Browser, nor can I get mywebsite again (just from the PCs).

During that time, there have been no interactions (no input/output) on either the server or the PCs!!!

Something is severely fubar with Ubuntu.

I think maybe WINS is not working correctly - it seems to work intermittently, so I am considering setting up BIND DNS on Ubuntu.

Does anyone think BIND DNS might solve the website issues and Network Browsing from all machines?

If you've modded hosts files, or tried going directly thru the IP - then no, BIND would make no difference (methinks).

---

### Post by molinus on 2011-01-13
Good point - I forgot about the hosts file on each machine - duh.
That should take care of any IP name resolution issues.

From a networking standpoint, I have Samba configured to be domain master, local master, preferred master, and os level 255, and all PCs WINS set to the server IP.
The server is always on.

I think I need to concentrate on getting Samba networking consistently with Winblows before moving forward with the website issue.

Thanks to all for your time and support.

---

### Post by airtonix on 2011-01-14
when you say you pinged the hostname, you need to clarify this.

avahi hostnames are only useful in my example if you use the hostname they create : 

so if your ubuntu machine is called "heimdal", then the avahi hostname for it will be heimdal.local

here is a valid virtual-host definition file for such an address : 
 a. assuming your network device is eth0, and 
 b. that you have disabled the defaul virtual-host : 
```

sudo a2dissite default
sudo a2dissite default-ssl

```
 c. make sure that /etc/apache2/sites-enabled no longer contains files named "default"

1. For development purposes add yourself to the apache usergroup.
```

sudo adduser $USER www-data

```

2.Create the virtual host file system for the virtual host
```

sudo mkdir /var/www/heimdal.local/logs -p
sudo touch /var/www/heimdal.local/logs/errors.log
sudo touch /var/www/heimdal.local/logs/access.log
sudo touch /var/www/heimdal.local/logs/authentication.log
sudo mkdir /var/www/heimdal.local/cgi-bin -p
sudo mkdir /var/www/heimdal.local/db -p
sudo mkdir /var/www/heimdal.local/public_html -p
sudo mkdir /var/www/heimdal.local/public_html/css -p
sudo mkdir /var/www/heimdal.local/public_html/js -p
sudo mkdir /var/www/heimdal.local/public_html/img -p
sudo touch /var/www/heimdal.local/public_html/index.html
sudo touch /var/www/heimdal.local/public_html/favicon.png
sudo touch /var/www/heimdal.local/public_html/favicon.ico

```

3. Modify the permission giving ownership to the apache user group. and making it readable by any user account on the machine.
```

sudo chown www-data:www-data /var/www/heimdal.local/ -R
sudo chmod 775 /var/www/heimdal.local/ -R

```

4. Create the virtual host definition file for the new virtualhost
```

sudo nano /etc/apache2/sites-available/heimdal.local

```

Paste the following
```

<VirtualHost *:80>
 ServerAdmin root@localhost
 ServerName heimdal
 ServerAlias heimdal.local
 DocumentRoot /var/www/heimdal.local/public_html

 <Directory /var/www/heimdal.local/public_html/>
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  allow from all
 </Directory>

 Alias /robots.txt /var/www/heimdal.local/public_html/robots.txt
 Alias /favicon.ico /var/www/heimdal.local/public_html/favicon.ico

 LogFormat "'time'='%t', 'user'='%u', 'client-ip'='%a', 'server-ip'='%A', 'server-name'='%v', 'url'='%U', 'status'='%>s'" authentications
 ErrorLog /var/www/heimdal.local/logs/errors.log
 CustomLog /var/www/heimdal.local/logs/access.log combined
 CustomLog /var/www/heimdal.local/logs/authentications.log authentications
</VirtualHost>

```

save it : 
```

ctrl + o
ctrl + x

```

5. Enable it : 

```

sudo a2ensite heimdal.local
sudo service apache2 restart
sudo service avahi-daemon restart

```

6. Allow access to the apache and avahi ports : 
```

sudo ufw allow in on eth0 to any port 80
sudo ufw allow in on eth0 to any port 5353

```

7. access it via avahi/bonjour enabled operating systems with 
```

http://heimdal.local/

```

---

### Post by chrislynch8 on 2011-01-14
So if I have correct.

Your MACs can all connect to the website using the serverip or hostname. They can access the Samba shares with no issues?

Your PCs can do none of the above?

Are your MACs and PCs recieving the same IP address etc. from the same DHCP server or are they static?

If it is working for the MACs and not the PCs then I don't think it is a Ubuntu issue, it is an issue on the PCs. I don't understand how you get no replies from a PING but you are then able to browse to the Samba Share on the Server. 

On a PC do start->run->//serverip and OK. This will connect to the Samba Share on the Server. If that works then I fail to understand why you cannot access the websote on the same server


Rgds
Chris

---

### Post by molinus on 2011-01-14
Hi Chris,

Thanks so much for your responses and your time - I'm going to whip this or die trying.
Please see my answers below (I think the numbered list 1 thru 4 is the most telling):

> **chrislynch8 said:**
> So if I have correct.

Your MACs can all connect to the website using the serverip or hostname. They can access the Samba shares with no issues?
    [COLOR="Magenta"]That is correct[/COLOR]

Your PCs can do none of the above?
    [COLOR="Magenta"]That is correct[/COLOR]

Are your MACs and PCs recieving the same IP address etc. from the same DHCP server or are they static?
    [COLOR="Magenta"]All IPs are static and:
1) I can successfully ping all PCs from all the Macs and from Ubuntu server
2) I can successfully ping all the Macs from all the PCs
3) I can successfully ping all the PCs from all the other PCs
4) I just cannot successfully ping the Ubuntu Server from any PC[/COLOR]

If it is working for the MACs and not the PCs then I don't think it is a Ubuntu issue, it is an issue on the PCs. I don't understand how you get no replies from a PING but you are then able to browse to the Samba Share on the Server.
   [COLOR="Magenta"]I mention an Ubuntu problem, because yesterday I was able to connect to a Samba share from 2 PCs, then an hour later I was not able to connect from them, but I have always connected from the Macs - it seems like there may be an intermittant Samba disconnect to only the PCs[/COLOR]

On a PC do start->run->//serverip and OK. This will connect to the Samba Share on the Server. If that works then I fail to understand why you cannot access the websote on the same server
    [COLOR="Magenta"]I am going to set at least one series of 200 pings to Ubuntu from a PC and see if any of them connect to test for an intermittent problem[/COLOR]


Rgds
Chris

---

### Post by chrislynch8 on 2011-01-14
> **molinus said:**
> Hi Chris,

Thanks so much for your responses and your time - I'm going to whip this or die trying.
Please see my answers below (I think the numbered list 1 thru 4 is the most telling):

Yes 1 -> 4 is very strange. This suggests that the problem in on the PC. Did you say earlier that the PCs can access the internet?

Are the Statis settings for DNS, WINS, gateway etc. correct on the PCs?

---

### Post by arrrghhh on 2011-01-14
Do you have some group policies being pushed on the PCs?  

**Anything** different with the network configuration between the MACs and PCs?

Have you tried bringing in another PC (like a laptop running Win) just to see if there is something funky with the PCs in your network?

It definitely seems client-related if the other machines on your network don't have an issue getting to the server.

Oh, I didn't ask - you said all IPs are static, did you put in default gateway and DNS information on the network interfaces?  Stupid question, I just am grabbing at straws here!

---

### Post by molinus on 2011-01-14
Re posts #16 & 17:

I am grasping at straws too - all machines have Internet access, and Gateway / Mask / DNS / WINS IPs are configured correctly (see the numbers 1-4 mentioned in post #15).

Here are the spooky results of my test running 200 pings of 32 bytes to the server:

The first 188 pings timed out.
The last 12 responded!
  time to reply - 3263ms for the first one, two at 1ms, one at 250ms, and the other 8 at 1ms.

??????

I am now on a quest.

**Update:**

On three different Windows machines (laptop running XP Home - desktop running XP Professional - desktop running Windows 7) I got the same results: after awhile it would connect and I had access to mywebsite and all server shares. 5 minutes later it would not connect.
The 3 Macs have been connected to the server all day with no interruptions...

---

