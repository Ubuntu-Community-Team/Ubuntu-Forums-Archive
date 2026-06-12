---
title: "why Apache2 says that?"
date: 2008-08-07
forum: Server Platforms
---

### Post by maxidrom11 on 2008-08-07
when I restart my Apache 2.2.8 
```
**sudo /etc/init.d/apache2 restart**
```
it says:
```
**Could not reliably determin the server's fully qualified domain name using xx.xxx.xxx.xx (IP address) for ServerName**
```
then:
```
**[error] VirtualHost *:80 -- mixing * ports and none-* with a NameVirtualHost address is not supported, proceeding with undefined results**
```

How to fix all these troubles? :confused:
thx

---

### Post by windependence on 2008-08-07
What is the output of

```
hostname -f
```

-Tim

---

### Post by maxidrom11 on 2008-08-07
hostname -f 

unknown 

where can I give name???

---

### Post by dmond on 2008-08-07
try changing your /etc/hostname and /etc/hosts file by using your editor (e.g. nano).

sudo nano /etc/hostname

yourdomainname.com

sudo nano /etc/hosts

127.0.0.1       localhost
127.0.1.1       yourdomainname.com
xxx.xxx.xxx.xx  yourdomainname.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

where xxx.xxx.xxx.xx is your ip.

if you're using a virtual hosting try looking at your /etc/apache/apache2.conf or /etc/apache/httpd.conf, try checking if you've input the correct settings.

P.S. backup the files first, before editing it.

---

### Post by windependence on 2008-08-07
Actually you want 

servername.yourdomain.tld

where servername is what you want to call the box, yourdoamin is your domain, and tld is your top level domain such as .com, .net, .org, etc.

-Tim

---

### Post by maxidrom11 on 2008-08-07
here is my **/etc/hosts** file 

```

# nameserver config
# IPv4
127.0.0.1 localhost
xx.xx.xx.xxx	Ubuntu-804-hardy-LTS-32-minimal
#
# IPv6
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
xx.xx.xx.xxx    Ubuntu-804-hardy-LTS-32-minimal

```

**/etc/hostname**

```
Ubuntu-804-hardy-LTS-32-minimal
```

please let me see how exactly these files should look like in my case

---

### Post by windependence on 2008-08-07
> **maxidrom11 said:**
> here is my **/etc/hosts** file 

```

# nameserver config
# IPv4
127.0.0.1 localhost
**192.168.1.3	servername.yourdomain.tld**
#
# IPv6
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
xx.xx.xx.xxx    Ubuntu-804-hardy-LTS-32-minimal

```

**/etc/hostname**

```
**servername.yourdomain.tld**
```

please let me see how exactly these files should look like in my case

Make them look like above, substituting your values of course.

-Tim

---

### Post by maxidrom11 on 2008-08-07
Thanks for your great help.

Now it's different topic but I need to solve this 
when I entered server before using SSH 
it was 
```
root@Ubuntu-804-hardy-LTS-32-minimal:
``` 
in command line 

later I changed some settings in HTTP_Header :confused: or something into "unknown" instead of "Ubuntu-804-hardy-LTS-32-minimal"

since then it was
```
root@unknown:
```in command line

now I changed **/etc/hostname** and **/etc/hosts** files according to your advice and now when type:
```
hostname -f
``` 
it says:
```
hostname: unknown host
```
how do I bring it back to normal work ???

---

### Post by windependence on 2008-08-07
You need to restart the network.

```
sudo /etc/init.d/networking restart
```

-Tim

---

### Post by maxidrom11 on 2008-08-10
I actually reboot and this stuff changed - thanks to you!

---

