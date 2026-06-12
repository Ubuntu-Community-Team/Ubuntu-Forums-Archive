---
title: "Setup a VPN?"
date: 2010-11-23
forum: Security
---

### Post by PDA1 on 2010-11-23
I travel a lot and use hotel wifi.....which I simply don't trust for security reasons

I've heard about VPN's and would like to configure my computer for it.  I assume that'll let me browse the web with a bit more security than just simple web browsing.


Is there an easy way to setup a VPN?  Please, I'm really new at this sort of stuff and not too clever in understanding computer language.....so make it simple if you would.

Thanks

---

### Post by DodgeV83 on 2010-11-24
Do you have a spare machine at home?  If so, install OpenVPN on it.  Now, I've found the normal OpenVPN installation to be incredibly difficult to setup, almost impossible for someone who isn't technical, so I recommend OpenVPN Access Server (OpenVPN AS for short)

[http://openvpn.net/index.php/access-server/download-openvpn-as.html](http://openvpn.net/index.php/access-server/download-openvpn-as.html)

The free version allows up to 2 simultaneous users, which should be enough, and took me under a minute to setup.  Once installed you can export a "client.ovpn" file, which will automatically connect to your home VPN when run on your laptop.  Unfortunately, it does not work with the Network-Manager in Ubuntu, so you can't just click the Wireless icon and click on the VPN.

I created a bash script on my desktop that simply runs:

```
sudo openvpn --config /home/rob/Downloads/client.ovpn
```

Simple :)

---

### Post by Drenriza on 2010-11-24
What is the idea in this?
 
From the hotel, VPN to an local machine and from their browse the net?

---

### Post by DodgeV83 on 2010-11-24
> **Drenriza said:**
> What is the idea in this?
 
From the hotel, VPN to an local machine and from their browse the net?

Correct.  It creates an encrypted tunnel to your home network, then uses your home internet connection to browse for you.  Once you start the VPN in the background on your laptop, just browse the web as normal, all of your internet packets are routed through your home computer.

[IMG]http://cdn.techpp.com/wp-content/uploads/2009/07/flowvpn.jpg[/IMG]

I'm not familiar with these free VPN services, but they may be worth a look.  Of course I wouldn't do anything confidential while on a free VPN service, so it may not be worth it...

[http://www.avinashtech.com/internet/15-best-free-vpn-for-secure-anonymous-surfing/](http://www.avinashtech.com/internet/15-best-free-vpn-for-secure-anonymous-surfing/)

[http://www.crispytech.com/2010/01/22/top-best-5-free-vpn-services-web-proxies-anonymous-web-browsing-surfing/](http://www.crispytech.com/2010/01/22/top-best-5-free-vpn-services-web-proxies-anonymous-web-browsing-surfing/)

---

### Post by PDA1 on 2010-11-24
So the idea is that I set up the VPN on my notebook and on my machine at home.

When I'm out-and-about-and-around I use my notebook to connect to my home machine which will allow me to connect, securely, to the web.

Is that correct?

I noticed that Synaptic has OpenVPN on it and OpenVPN.net mentions that.

I just tried to get OpenVPN working from the OpenVPN.net.....what a pain.  I have no idea what they're talking about.  It certainly IS NOT easy to install and use OpenVPN.

---

### Post by DodgeV83 on 2010-11-24
> **PDA1 said:**
> So the idea is that I set up the VPN on my notebook and on my machine at home.

When I'm out-and-about-and-around I use my notebook to connect to my home machine which will allow me to connect, securely, to the web.

Is that correct?

I noticed that Synaptic has OpenVPN on it and OpenVPN.net mentions that.

I just tried to get OpenVPN working from the OpenVPN.net.....what a pain.  I have no idea what they're talking about.  It certainly IS NOT easy to install and use OpenVPN.

I agree, which is why I pointed you to the OpenVPN Access Server:

[http://openvpn.net/index.php/access-server/download-openvpn-as.html](http://openvpn.net/index.php/access-server/download-openvpn-as.html)

Here is the install guide:

[http://openvpn.net/index.php/access-server/quick-start-guide.html](http://openvpn.net/index.php/access-server/quick-start-guide.html)

Essentially, you double click on the install file, press enter a bunch of times, then point your browser to [https://localhost:943/admin](https://localhost:943/admin) to finish the setup.

---

### Post by Legeril on 2010-11-24
I've been trying this, I get as far as here 

> then point your browser to [https://localhost:943/admin](https://localhost:943/admin) to finish the setup. 	  	14 Hours Ago 09:35 PM

but I can't figure out how to log in, it says the same credentials as my system but when I try this it says I don't have root access. Am I missing something basic here? I did default for everything on the installation...

---

### Post by DodgeV83 on 2010-11-25
> **Legeril said:**
> I've been trying this, I get as far as here 



but I can't figure out how to log in, it says the same credentials as my system but when I try this it says I don't have root access. Am I missing something basic here? I did default for everything on the installation...

I used the same credentials I use to login to Ubuntu.  The user guide says:

> You can now go ahead and login with your root credentials or the username you set via the Initial Configuration Tool.

If your normal credentials aren't working, try doing the installation again and choose a username.

---

### Post by Legeril on 2010-11-25
I tried this it says this installation process has already happened on this computer so use "--force" I tried this also didn't work =(

I've tried my default login credentials and it says I don't have root access, so maybe I mistyped somewhere but I always used the default jazz so I'm a bit confused - as obviously I'm using the right credentials but not having the right access

---

