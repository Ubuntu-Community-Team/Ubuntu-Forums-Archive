---
title: "Next step with Apache"
date: 2007-01-25
forum: Server Platforms
---

### Post by crabhunter on 2007-01-25
I've recently installed Apache2 on Ubuntu6.10.
All is working,if I goto [http://localhost/~username](http://localhost/~username) I can see my webpage.
I have 3 pc's and 1 laptop on a modem/router.
Only the server is running ubunto/Apache.
How can I find out the address of my webpage so that the other pc's on the network can veiw it and ultimately everyone else on the WWW.
Mike

---

### Post by hammonjj on 2007-01-25
Add to /ect/apache2/http.conf:

ServerName [www.yourdomain.com](www.yourdomain.com)

And then go to /etc/apache2/ports.conf and add:

Listen 80

That should already be there though, but if it is missing then just add it in.

Put all of your web documents under:

/var/www

which is the default or you can change it to some other directory.

Then just direct your domain name to your WAN address and forward port 80 on your router to you server address

If you have any questions, let me know.

---

### Post by kebes on 2007-01-25
What hammonjj suggested should work. However you could also just use the internal (LAN) IP address of the Ubuntu server. On the Ubuntu machine, go to a terminal and type:
ifconfig

It will list (among other things) the IP address of the server (it will be listed as "inet addr:"). For instance it may look like:

```

user@computer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:AA:AA:AA:AA:00
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: :::/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1923049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1365057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1096243388 (1.0 GiB)  TX bytes:984166469 (938.5 MiB)
          Interrupt:66 Base address:0x4000

```

In this example the internal IP is "192.168.0.101". From any computer in your local network, you should then be able to go to the page:
[http://192.168.0.101/~username/](http://192.168.0.101/~username/)


If you want a neat alias for your server then follow hammonjj's suggestions.

---

### Post by hammonjj on 2007-01-25
My suggestion will also allow everyone to see you webpage from the web too.

Don't forget to restart the server!

---

### Post by crabhunter on 2007-01-25
Thank you both for your advice.
I can now view my web page over my local network by the address 192.168.0.4/~myname
I don't have a domain name ie [www.myname.com](www.myname.com).
I am happy at this stage of playing around just to have a set of numbers so that anyone can have my page served from my computer.
using ifconfig can I get the info I need or will my address change every time I start the computer or reconnect to my service provider.
Mike

---

### Post by kebes on 2007-01-25
> **hammonjj said:**
> My suggestion will also allow everyone to see you webpage from the web too.

Yes, good point.

If you want your site visible to the whole internet you'll need to register a domain name. If you want free redirects, you can use services like "[DynDNS]("http://www.dyndns.com/")" or "[noip]("http://www.no-ip.com/")".

---

### Post by kebes on 2007-01-25
> **crabhunter said:**
> using ifconfig can I get the info I need or will my address change every time I start the computer or reconnect to my service provider.
Mike

To determine your "external" IP address, you can just go to a website like:
[http://whatismyipaddress.com/](http://whatismyipaddress.com/)

If you enable port-forwarding on your router, then when you go to that IP you should get the webpage on your server.

However with most internet providers your IP address changes from time to time. This is why it's neat to use services like DynDNS and noip, which I mentioned before. In fact noip provides a Linux client that runs and keeps updating the record, so that even if your IP address changes you can still get to your website! (This is all free if you want only the basic redirect.)

For details on all of this, see Step 5 in this how-to I wrote:
[http://www.ubuntuforums.org/showthread.php?t=268985](http://www.ubuntuforums.org/showthread.php?t=268985)

It describes in detail how to deal with dynamic IP address issues.

---

### Post by crabhunter on 2007-01-26
OK,my service provider seems to be blocking port 80 and I've tried 8080.
When configuring my router should I put in the local address of the server pc or the router itself?
I've been using the servers address.
So I signed up for no-ip and downloaded the app.
I unpacked it and cd'd to the directory but there is no configure file.
What do I do next to get it installed?
I have tried the add application from the applications menu but noip is not available I have also tried apt-get but it can't find noip.
Mike

---

### Post by chrisfay on 2007-01-26
> If you want your site visible to the whole internet you'll need to register a domain name.

....not symantically true. IP's work just fine for network testing purposes. :-s 

> When configuring my router should I put in the local address of the server pc or the router itself?

For what? If you're trying to access the web interface of the router you would obviously need to enter router's ip, if you're talking port forwarding, you would need route your ports to the server's internal IP. 

Also note, you'll need to configure your server with a static LAN IP instead of the default DHCP or you'll drive yourself crazy trying to track down the new one every time you reboot or restart your interfaces.

> So I signed up for no-ip and downloaded the app...
I'm a huge fan of zoneedit.com and ddclient, which ran a bunch of domains on my dynamic ip for a couple years, so I'm not totally sure on no-ip's specifics.

> I have tried the add application from the applications menu but noip is not available I have also tried apt-get but it can't find noip.
You can always check [http://packages.ubuntu.com](http://packages.ubuntu.com) for whats available.

---

### Post by kebes on 2007-01-26
When configuring your router for "port forwarding" you would enter the internal IP address (on the local network) of your computer.


Before installing the noip application, you should make sure that the redirect works if you manually update the noip service with your (external) IP address. Once that works you can worry about the noip application.


The noip application is not in the repositories. You have to install it manually. Once you untar it and go into that directory, there is a readme file that explains what you have to do. See also the details in Step 5 of [my previous thread]("http://www.ubuntuforums.org/showthread.php?t=268985"). If the steps in that guide do not work for you, please state exactly what step is not working, and I'll try to help...

---

### Post by crabhunter on 2007-01-26
I'm realy not sure what to do next.
I have been to noip open port check tool and it confirms that 8080 is open and it can access my service.
i have added Listen 8080 to the apache config file and restarted apache.
I have setup my router and rebooted it but I still can't see my webpage using the address I get from say ipaddress.com followed by :8080
What should I try next?
Mike

---

### Post by kebes on 2007-01-26
So, just to be clear, you logged into your noip account and set forwarding for "whatever.noip.com" to the (external) IP address of your internet connection, right? (You  need to tell noip what your IP address is.) Then you go to:
[http://whatever.noip.com:8080/](http://whatever.noip.com:8080/)

And you get nothing? If that's the case, then run through these checks (on the server computer) and let me know which ones work and which ones do not work:

[http://127.0.0.1/](http://127.0.0.1/)
[http://127.0.0.1:8080/](http://127.0.0.1:8080/)
[http://localhost/](http://localhost/)
[http://localhost:8080/](http://localhost:8080/)
[http://168.1.0.100/](http://168.1.0.100/)
[http://168.1.0.100:8080/](http://168.1.0.100:8080/)
[http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/)
[http://xxx.xxx.xxx.xxx:8080/](http://xxx.xxx.xxx.xxx:8080/)
[http://whatever.noip.com/](http://whatever.noip.com/)
[http://whatever.noip.com:8080/](http://whatever.noip.com:8080/)

In the above tests, replace "168.1.0.100" with your INTERNAL IP address (the one that "ifconfig" returns), and replace "xxx.xxx.xxx.xxx" with your EXTERNAL IP address (the one that you get from websites like [http://whatismyipaddress.com/](http://whatismyipaddress.com/) ). Also replace "whatever.noip.com" with the redirect you selected when you made your noip account.

By going through that list, and taking note of which ones work and which ones do not work, we can figure out which step in the chain is not working.

---

### Post by crabhunter on 2007-01-26
Thanks for all the trouble your taking over this for me,I do appreciate it.
It all goes belly up when I try going to [http://84.13.11.228/](http://84.13.11.228/)  that is the address returned from whatismyaddress.com.
Also adding :8080 to that makes no difference.

Mike

---

### Post by kebes on 2007-01-26
Okay, if that's the one that doesn't work, then it means that your router is not doing port forwarding.


Log back into your router admin page, and make sure that you have enabled it to do port forwarding of "8080" to the INTERNAL IP of your computer, on your local network. I'm sure you've already checked it a bunch of times, but check again (I can't tell you how many times it turns out just to be a typo in the router config!).

Also, have you ever been able to forward other ports on that router? (Maybe for a game, or SSH, or whatever?) Maybe try forwarding the port for some other service (FTP, SSH...) and see if that one works.

Sometimes routers are buggy and won't do what they say they are doing. (Linksys routers, in particular, seem buggy.) If no forwarding works on the router, you may need to flash the firmware. Maybe the latest version fixes a known problem. Check with the manufacturer webpage.


P.S.: If you check [http://168.1.0.100:8080/](http://168.1.0.100:8080/) from another computer in  your home network, you see your server, right?

---

### Post by crabhunter on 2007-01-26
Just rechecked the router again,it is set to port 8080 and the address is 192.168.0.4 the address returned by ifconfig.
I have never had dealings with this before to know if my router, a Belkin, works in this way.
I have done a check for updates and it has the latest firmware running.
I think I will have to try another router before I bother you any more.
Thanks again for the help.
Mike

Update no I cannot see my page from another pc on the network by going to [http://168.1.0.100:8080](http://168.1.0.100:8080)
or [http://127.0.0.1:8080](http://127.0.0.1:8080)

---

### Post by kebes on 2007-01-26
> **crabhunter said:**
> Update no I cannot see my page from another pc on the network by going to [http://168.1.0.100:8080](http://168.1.0.100:8080)
or [http://127.0.0.1:8080](http://127.0.0.1:8080)

Of course you checked [http://192.168.0.4:8080/](http://192.168.0.4:8080/) right? (The 168.1.0.100 was just an example...)

You can also try connecting the server directly to the internet, without the router, and see if it then works. If it works in that case, then you know for sure that the problem is with the router forwarding.

---

### Post by crabhunter on 2007-01-27
OK,
Going to 192.168.0.4 on any other pc on the network views the page,so does 192.168.0.4:8080.
I'm going to try a direct connection but that involves installing a USB modem so I can see trouble ahead!
Other than that I might see if I can find someone with a different service provider and take the server round there.
It was funny when I did the port check at the noip site it confirmed port 80 was blocked but 8080 passed the test!
Mike

---

### Post by chrisfay on 2007-01-27
> Going to 192.168.0.4 on any other pc on the network views the page,so does 192.168.0.4:8080

As a side note, using your LAN IP won't help you determine if the router's port forwarding is the issue; you would have to generate an inbound connection from outside your network for the router to utilize the port forwarding feature.  

This is also the reason why you can reach your server with or without adding the port in your browser; there's no need for port routing when each machine in your LAN has its own ip.

---

