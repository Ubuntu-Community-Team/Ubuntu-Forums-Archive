---
title: "Connect to Internet-Ubuntu Server?"
date: 2011-12-02
forum: Server Platforms
---

### Post by cookiemonster1 on 2011-12-02
Hi All,

I am planning on installing ubuntu server on an old desktop soon. I have it downloaded and burnt to a disk. This may be a total new question, but I think i will run into a problem when trying to get it up and running. Here are the details:

Drivers and installed fine, and an ethernet cord will be connected. However, I will be connecting it at school, and to access the internet I will need to login, which is normally done via the web browser. I would install a minimal UI such a Xubuntu, etc, but to do that via the command line I will need internet....?

Question is, is there anyway to connect to my schools internet via the command line, or is there a way to download a minimal UI and install via the disk drive?

Any help is much appreciated.

Thanks

---

### Post by cookiemonster1 on 2011-12-02
I just found out I can log in another device if I know its MAC address. Anyone know the command in Ubuntu Server to locate this?

---

### Post by papibe on 2011-12-02
Hi cookiemonster1. Welcome to the forums.

The command 'ifconfig' can show you several information including your MAC (displayed as HWaddr).

Hope it helps,
Regards.

---

### Post by cookiemonster1 on 2011-12-02
Awesome. Thank you for your help. I knew this was the right place to come.

---

### Post by cookiemonster1 on 2011-12-02
I was able to get the MAC address but when I go to remotely authenticate, it says the address was not found. Is there any other way to connect??

---

### Post by jonobr on 2011-12-02
Hey there cookiemonster1

the details are a little vague on what your trying to connect to so its hard to make a suggestion.

Is there any chance that the sysadmin or IT crowd can help you out to connect?

You could try connecting using a text based browser like w3m which requires a bit of getting used to.
If it works , may that would work for you, but again, the most pain free way is probably taking to the admins who implement the security

---

### Post by cookiemonster1 on 2011-12-02
Edit:Fixed

---

### Post by cookiemonster1 on 2011-12-03
So I have been following this guide on how to host a website using ubuntu webserver. I was able to install apache, mysql, and php. However, when i point my browser to my IP, it doesnt respond/doesnt load/times out. Help here? I have an internet connection?

---

### Post by Groggster on 2011-12-03
> **cookiemonster1 said:**
> So I have been following this guide on how to host a website using ubuntu webserver. I was able to install apache, mysql, and php. However, when i point my browser to my IP, it doesnt respond/doesnt load/times out. Help here? I have an internet connection?

So, you are trying to access your web server using an external machine? Is this is the case, you should definitely be able to get access to your server.

First of: Is your server located in the same LAN as your client?
Second: Are you being NAT:ed? The easiest way to determine this, is to look at your servers IP-address using the command ifconfig. Please post your result here.

---

### Post by cookiemonster1 on 2011-12-03
I just setup a static ip and that didnt seem to work. 

First: I assume so. My server is plugged directly into the wall, and when I check it on my laptop or my phone it times out/doesnt respond.
Second: [IMG]http://s9.postimage.org/r6irjr2b3/IMAG0117.jpg[/IMG]

---

### Post by Groggster on 2011-12-03
Well, that is a public address, likely supplied directly from your school, so in order to access your server, you have to pass through your schools network, and this is likely where the fun ends, since they probably have blocked a couple of ports/protocols to increase the networks security. The only good way to fix this, is to talk to your schools administrators to see what is going on.

However, if that address is supplied directly from the ISP, pings over the Internet should work. If that is the case, check your firewall in the server.

---

