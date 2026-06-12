---
title: "Temporary Proxy setup help..."
date: 2012-06-19
forum: Server Platforms
---

### Post by jesushero on 2012-06-19
I want to install Ubuntu Studio 12.04 on a machine with no internet access. I've been reading on the Ubuntu Studio support pages that you need internet access during and after installation to get all the components for it to run properly. 

I do not have a local mirror of 12.04 (yet). I was thinking of setting up a temporary proxy on either my server, or my laptop, and configure the Ubuntu Studio machine to use that proxy during install time. I then want to stop the proxy when this process is done, as there is no need for it after that. I don't want internet access on my studio computer, but it will have LAN networking to other computers on the network, some of which have access to the internet.

I had a brief look at squid, which I have never needed to use before. I was horrified by the tremendously long conf file and what seems like days or even weeks needed to make it work properly. I simply don't have that much time to learn how squid works. Is there a simpler proxy option? Is there a simpler solution altogether, without setting up a proxy?

Due to the way the LAN is set up, I cannot connect the Ubuntu Studio machine directly to the internet, not even temporarily.

Any help greatly appreciated..

---

### Post by d4m1r on 2012-06-19
Isn't squid only a HTTP proxy? Anyway, have you looking into OpenVPN? Should only take 2-3 hours to setup the first time and you can basically setup a VPN server on the machine that is connected to the internet and get that studio to connect through it.

After you can just uninstall the OpenVPN client from the studio machine and viola, no more internet access.

---

### Post by rukiaEnix on 2012-06-19
I don't think a proxy will work for what you want.

What I will do is this: Set the IP of a computer with Internet as the gateway  of the non-internet computer, and setup the correct DNS settings . It's just a try but it may work.

---

### Post by Cheesemill on 2012-06-19
Or you could set up an SSH tunnel to the internet connected machine and route traffic through that.

---

### Post by koenn on 2012-06-19
> what seems like days or even weeks needed to make it work properly. 
it takes 5 minutes to set up and get it working



> Or you could set up an SSH tunnel to the internet connected machine and route traffic through that.
> I don't think a proxy will work for what you want.
> Isn't squid only a HTTP proxy? Anyway
I don't know what all Ubuntu studio would need for components for it to run properly or what sort of internet connection the support pages mention, but it would be highly unusual if it wasn't just a matter of apt-get some packages, in which case a simple http proxy such as squid would do just fine

---

### Post by jesushero on 2012-06-19
Which of these options would work during install-time on Ubuntu-Studio? 

As for squid, I have trouble making it work. I've quickly skimmed through plenty of how-to's, guides, man pages, etc, but can't figure it out. No matter what I do, there won't be any server listening on the expected port showing up on netstat.

Do you have a simple conf file I can use as a template, to just allow any computer from the 192.168.1.0/24 range to access the internet (interface has 10.42.43.10 ip), without any regards for safety? I literally just want to enable something, go through the install, disable it again, and forget about it.

---

### Post by koenn on 2012-06-20
setting up squid is a 3 step process:

1- install squid (sudo apt-get ...)

2- edit squid.conf. 
you need to find the section that deals with acl, and make sure you have something like the following. Use an editor with a search function, it helps :-)
```

acl mynetwork src 192.168.1.0/24
http_access allow mynetwork

```

(you can simply add this; all other defaults are OK )
That is all -- unless something changed dramatically since the last time I've set up squid


3- restart squid


squid listens on 3128/tcp be default, so you can check it with telnet (from the squid server itself, or any host in the allowed network range(s) :
```

telnet 192.168.1.25 3128
Trying 192.168.1.25...
Connected to 192.168.1.25

```
note that the up address is the address of the squid server

If you don't get a connect, there's a problem. 
If you get "connected", you can further test by sending it a (fake) get request; this should return some data, mostly html, telling you your GET failed. This is expected (you asked an invalid url) and shows squid works correctly.

test:
```

telnet 192.168.1.25 3128
Trying 192.168.1.25...
Connected to 192.168.1.25
Escape character is '^]'.

get 123

```

reply:
```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<HTML><HEAD><META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=iso-8859-1">
<TITLE>ERROR: The requested URL could not be retrieved</TITLE>

```


And yes, this is the only one  off all suggested solutions that will work *during* an install. The installer does its downloads by http and _should_ allow you to specify a proxy (at some point during the "select a mirror" stage.
Disclaimer : the above describes debian text-mode installer. I'm assuming the Ubuntu (Studio) installer is not all that different

---

### Post by jesushero on 2012-06-25
> **koenn said:**
> setting up squid is a 3 step process:


And yes, this is the only one  off all suggested solutions that will work *during* an install. The installer does its downloads by http and _should_ allow you to specify a proxy (at some point during the "select a mirror" stage.
Disclaimer : the above describes debian text-mode installer. I'm assuming the Ubuntu (Studio) installer is not all that different

Thanks for that koenn.. That's what I was doing all along to install squid, but the problem was that the init.d scripts and the service functions do not work. I need to file a bug report for that.. I had to manually kill squid by using kill and the PID, then restart it by executing it from bin.

So now squid seems to work. I think from here onwards it should be fine. I'll test it from other computers later, and if it works I'll attempt to install. Ubuntu gives you an install-time option to set a proxy for internet access. Or at least it did, up until 10.04. Let's hope that some of the useful functionality has remained.

Thanks again!

---

