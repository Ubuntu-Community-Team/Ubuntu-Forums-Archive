---
title: "Local Area Network DNS Help"
date: 2009-01-18
forum: Server Platforms
---

### Post by mjfroggy on 2009-01-18
Hello all,

 I am new to using Ubuntu to setup a server and just setup a home server here using ubuntu server 8.10 I have the LAMP server all setup and am able to access my test web page on any coputer in my home using [http://xxx.xxx.x.xxx](http://xxx.xxx.x.xxx)
however what I want to be able to do is access the webpage by just entering http//marquee and then have the server automatically load the page I would come to if I where to enter [http://xxx.xxx.x.xxx](http://xxx.xxx.x.xxx)

I am hoping someone can point me to a tutorial or outline what I would need to do. I know I would most likly need to edit my http.conf file or some other dns http config file however I am new to setting up a server. This is my first experience and test/learing server I am setting up in my home so I can learn server administration.

Thanks for your help!

---

### Post by volkswagner on 2009-01-18
The simplest way is to edit /etc/hosts file.  Make sure you have set a static ip and add the ip and hostname to the file.

```
sudo nano /etc/hosts
```


Add line similar to this, with your ip information, under localhost line.
```

127.0.0.1 localhost
192.168.1.xxx yourhostname

```


You can do this on all your linux machines, allows ssh access with hostname.

Add all Lan hosts to each file.

Or you will need to setup your own DNS server.

---

### Post by mjfroggy on 2009-01-18
Thank you for your help,

So I edited the file so it looks like below

127.0.0.1 localhost
192.168.1.125 ubuntubox

I then save file and exit nano I even restarted apache2 (thinking that may be needed.
However I can still only access the test webpage by going to [http://192.168.1.125](http://192.168.1.125)   if I go to [http://ubuntubox](http://ubuntubox)  I just get a cannot display the webpage error  ??

---

### Post by volkswagner on 2009-01-18
Sorry about that.  Are you accessing the server from Widows, Linux, or Mac.

You will need to edit the host file for the client machine.

---

### Post by mjfroggy on 2009-01-18
All the other desktops and laptops in the house are Windows.

So again what I want is any desktop or even laptop in the home I want to be able to get to the webpage that is on the home server by typing in just [http://ubuntubox](http://ubuntubox)   and have it resolve or loadup the webpage that I would get as if I entered [http://192.168.1.125](http://192.168.1.125) in my browser

I should not have to edit anything on the other desktops/laptops I am sure it is some sort of dns setting in the server itself or maybe in the router? that I need to edit so anytime I type in that ip it will resolve/redirect to [http://ubuntubox](http://ubuntubox) ??

Thanks

---

### Post by capscrew on 2009-01-18
@mjfroggy,

The advice volkswagner has given you is correct.  On the other hand your notion: > I should not have to edit anything on the other desktops/laptops I am sure it is some sort of dns setting in the server itself or maybe in the router? is also true.  DNS is a response to that.

Most routers (DSL modems too) have a provision for mapping IP addresses to names.  Look on the config page of your router.  You could also set DNS up on the LAMP server.  The easiest is DNSmasq.  It's available through Synaptics.

---

### Post by cariboo on 2009-01-18
There is a hosts file in Windows XP, I'm not near a computer with XP at the moment, but I triple boot this one and in Windows 7 the hosts file is located in:

```
Windows/System32/drivers/etc
```

I've added an entry in hosts on small networks < 5 computers and a mix of windows versions, and it works quit well. You shouldn't  have to do anything on a Windows network, at least I never have to. I repair computers for selected customers, and as long as the computer is on the same workgroup as the server, all I have to do is enter http://<servername> and I can access the website on the server.

Jim

---

### Post by mjfroggy on 2009-01-19
Thanks

If I did not want to edit the windows/system32/drivers/host
file on all my desktops would it be best then just to install DNSmasq ?? I see some posts talking about just installing DNSmasq to do what I want to do and other posts talk about just installing dns/bind on the server itself ?

What is the simplest and most secure path to go do? setup DNSmasq or setup dns and bind on the server itself I should note the server is connected to a router which runs dhcp 
Or should I just login to the router itself and edit a file in their to make all desktops be able to access the servers webpage by a name only not an domain ?

Thanks all for your continued help

---

### Post by Iowan on 2009-01-19
I found [this]("http://www.sigmundvoid.com/2007/08/netbios-names-and-ubuntu/") link today in another thread.  Dunno if it'll help Windows boxes find Ubuntu, or if it's for the other way around.

---

### Post by capscrew on 2009-01-19
> **mjfroggy said:**
> Thanks

If I did not want to edit the windows/system32/drivers/host
file on all my desktops would it be best then just to install DNSmasq ?? 
Yes.  DNSmasq is perfect for your situation; local DNS name resolution.  Your wish to edit only one file for this process is exactly what DNSmasq allows.
> I see some posts talking about just installing DNSmasq to do what I want to do and other posts talk about just installing dns/bind on the server itself ?

DNSmasq only does local DNS resolution.  BIND is the app most favored for internet applications.  This would be the WAN side.  Those needs are taken care of by your ISP.
> 

What is the simplest and most secure path to go do? setup DNSmasq or setup dns and bind on the server itself DNSmasq by far is the easiest to set up for LAN (local) DNS name resolution. > I should note the server is connected to a router which runs dhcp 
AN excellent point.  Is the router capable of handling DNS?  Who made the router and what model is it? > 
Or should I just login to the router itself and edit a file in their to make all desktops be able to access the servers webpage by a name only not an domain ?Are you saying that you can set this up? IMHO this is the preferred way.> 

Thanks all for your continued help

---

