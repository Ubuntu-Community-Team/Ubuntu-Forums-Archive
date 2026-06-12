---
title: "Starting Simple Server"
date: 2009-05-10
forum: Server Platforms
---

### Post by Muscovy on 2009-05-10
I'm trying to build a server to host one domain. It's on a pretty old computer, but it's good enough. However, I'm not at all familiar with the command-line style instead of GUI. How would I go about setting up the domain (no email, php, sql, perl, or anything)?
  I tried reading the documentation, but there's far too many pages.:rolleyes:

---

### Post by ikonia on 2009-05-10
this may sound a bit picky - but it's important information.


when you say "host a domain" what exactly do you mean, a domain as in a login domain, like a windows domain, a DNS domain, or just network name resolution ?

Once you answer that we can take it forward.

---

### Post by Muscovy on 2009-05-10
DNS domain.

---

### Post by ikonia on 2009-05-10
ok - well first of all, I don't recommend you do this

to run a DNS domain, you need 2 boxes both with static IP, yes you can do other things to get around this, but it's not worth the effort, and pain it will cause.

If you want to host a DNS service, use one of the public services, free or paid for, 

if you want to resolve a dns domain locally just put the hosts in your host file.

---

### Post by trentscott4 on 2009-05-10
I use the free service at zoneedit.com.

Another one to try is everydns.net.

You simply buy a domain name from a registrar like GoDaddy (Google for coupons to save a couple bucks), make an account at ZoneEdit/everyDNS and create an "A record" that points to your home IP address.  You can find that by going to whatismyip.com.  If you want to run mail (eventually), you'd create an additional "MX record" that points to your IP.

Then, you need to login to your router and forward port 80 (for a webserver) to your server machine's LAN (internal) IP.  i.e.  You can find that by opening a console on the server and typing 'ifconfig'.

Let me know if that helps.

---

### Post by Muscovy on 2009-05-10
This was for something fairly temporary. Heck, I can even just use IP.
  The main thing I don't understand is configuring the server to a port, and how to actually put the website html file on the server.

---

### Post by cariboo on 2009-05-11
If you install apache2 from the repositories everything is setup automagically, all you have to do is add your content to /var/www. 

Then depending on how you are connected to the internet, you will have to setup portforwarding from your router to your server. You will have to setup a static ip address on the server, as using dhcp may change the servers ip address after a reboot. 

Have a look [here]("http:///www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html") to setup a static ip address. You will have to check the documentation that came with your router to setup portforwarding as it is different for every manufacturer.

Once you have portforwarding setup, go to [canyouseeme]("http://www.canyouseeme.org/") to check if you have done everything correctly and to check if your isp is blocking any ports.

---

### Post by trentscott4 on 2009-05-11
To setup a static IP:

Note: This is for Ubuntu 8.10 Desktop, simply skip steps 1-2 if
you're running Ubuntu 8.10 Server.

Steps:

  1. Open a console (Alt+F2) and type:
     ```
gnome-terminal
```
  2. Remove 'Network Manager'.
```
sudo apt-get remove --purge network-manager
```
  3. Modify the /etc/network/interfaces file.
     ```
sudo vi /etc/network/interfaces
```
  4. Press 'Insert' to edit the file and enter the following
(customized to your network):
    ```
 # The primary network interface
     auto eth0
     iface eth0 inet static
     address 192.168.1.115
     netmask 255.255.255.0
     gateway 192.168.1.1
```
  5. Hit 'Esc' and type ':wq' to save the file and quit.
  6. Modify your DNS servers.
     ```
sudo vi /etc/resolv.conf
```
  7. Delete any existing lines and replace with your router's IP:
     nameserver xxx.xxx.x.x
  8. Hit 'Esc' and type ':wq' to save the file and quit.
  9. Restart your networking.
     ```
sudo /etc/init.d/networking restart
```
 10. Test your new settings:
    ```
sudo ifconfig
```

The output should reflect the changes you just made
(proper IP, gateway, etc.)

---

### Post by ikonia on 2009-05-12
that's not how to setup a static ip address, a static IP address must be allocated at the network / ISP level, that will only set a static IP address on the internal network which may or may not work depending on how his router responds to reservation of dhcp addresses.

---

### Post by ephmanjmm on 2009-05-12
I am unclear about something.  How does his router's response to reservation of dhcp addresses have anything to do with whether or not static ip addressing works?
The described method should implement a static ip address.  It will be a private address but static none-the-less.  Unless the assigned address is also in the list of addresses to be assigned by the dhcp server, there should be no problem.

---

### Post by ikonia on 2009-05-14
well 

1.) if he's asking for DNS services, he seems to imply a public address is needed, so setting up a static private address won't do anything to set that up, 

2.) yes, not knowing how his router deals with dhcp addressing can be a problem, as you've said if you've picked an address that is assigned to be a dhcp address it can cause a conflict, or the router may refuse to let him connect to it as it didn't assign that address.

---

### Post by ephmanjmm on 2009-05-14
well

You might infer that he needs a public ip address but that doesn't change the method of implementation.  The method described should work. It will set up a static address.  You stated that it wouldn't. A static ip does not have to be allocated at the ISP level.

---

