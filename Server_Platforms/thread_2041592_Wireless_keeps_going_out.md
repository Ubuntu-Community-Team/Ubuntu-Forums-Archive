---
title: "Wireless keeps going out"
date: 2012-08-12
forum: Server Platforms
---

### Post by computerfox on 2012-08-12
Hello everyone,

    I've been having this issue for a while and I've run out of ideas to fix it myself.

    I have Ubuntu Server with a Netgear WG311 PCI Wireless card.  I installed the driver via madwifi.  I've confirmed it was installed because it does find my network and it does connect to it.

    Now it goes on just fine anytime I do dhclient, but then after about 5 minutes gets knocked off.  I've tried disable dhcpd via renaming it and then rebooting.  Same thing.

    I also set up interfaces via:

auto wlan2
iface wlan2 inet static
      wireless-essid [wireless name]
      address  [address]
      .
      .
      .

but it still doesn't stay connected.

   Does anyone have any advise for me how I can connect to the network wirelessly and STAY connected?

---

### Post by computerfox on 2012-08-12
Update:

    When I just did iwconfig, it showed that I was no longer connected.  So, I believe the actual problem is that for some reason it gets disconnected from the network itself.  What would cause this?

---

### Post by kennethconn on 2012-08-12
Does it connect and then disconnect after 5 minutes consistently?

---

### Post by computerfox on 2012-08-12
> **kennethconn said:**
> Does it connect and then disconnect after 5 minutes consistently?

Correct!

I've found this thread:[http://ubuntuforums.org/showthread.php?t=1396470](http://ubuntuforums.org/showthread.php?t=1396470) , but I'm on a server edition so I'm not sure if this is apart of it.  I believe I did install network manager while installing the driver for madwifi, but again, I'm a server edition.

---

### Post by computerfox on 2012-08-13
Now I'm getting REALLY annoyed

Update:

  I set the default route via 

route add default gw [ip for the server] [device name]

It was up for about 20 minutes this time.  What the heck is going on?

---

### Post by kennethconn on 2012-08-13
When you say Wireless keeps going out, is it unable to connect via names AND by IP addresses?
 
Are you getting the same results via a wired connection?

---

### Post by computerfox on 2012-08-13
not sure what you mean...

it does connect, then eventually it does disconnect from my router.  i simply run iwconfig [device name] essid [network name] and it's back up.  i'm just getting frustrated that i have to keep doing that and there should be no reason why it's happening since my server is right in front of my router.  why not just connect it to ethernet?  i want to be able to connect via wireless because we're planning to move and regardless of what happens i want to be able to keep my server up.

---

### Post by kennethconn on 2012-08-13
When your wireless is gone out, can you ping a website by IP address (not by name), or can you access network resources by IP address (not by name)?
 
The reference to the wired connection is purely for testing, so are you staying connected to your network and the internet with the wired connection?

---

