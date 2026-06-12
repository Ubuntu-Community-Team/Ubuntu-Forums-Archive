---
title: "Sharing Network in VirtualBox"
date: 2013-09-05
forum: Virtualisation
---

### Post by emptycoder on 2013-09-05
Hi, I have Windows 7 guest and Ubuntu Host, the Windows 7 has Internet connection, how do I share it with Ubuntu host? or how to make Ubuntu see guest's sharing network?
Thanks.

---

### Post by SeijiSensei on 2013-09-05
Life would be easier if the Ubuntu host were connected to the Internet.  Then, using the default NAT mode in VB, the Windows guest would see the Net as well.  Is this not possible?

---

### Post by emptycoder on 2013-09-05
Yes life would be easier if my USB modem was detected on Ubuntu and save the whole trouble, but in my case I need to use VirtualBox to access the Internet.
I believe it's about to set some IP and netmask to vboxnet0 and create a share connection on Windows, but I need some details, especially how to let Ubuntu see Windows Guest sharing network.

---

### Post by SeijiSensei on 2013-09-06
In the default NAT mode, the Windows guest will be assigned an IP in 10.8/16 with a corresponding IP assigned to vboxnet0.  You can communicate with the guest simply by IP.  However you'll need to a bit of fancy footwork to reach the Internet, since you'll need to use the Windows host's IP as your Ubuntu default gateway, then use Windows Connection Sharing to masquerade the Ubuntu machine out to the Internet.  If the Windows guest has 10.8.0.2 as its IP, you'd add a default route in Ubuntu like this:

```

sudo ip route del default             # just in case there is one already
sudo ip route add default gw 10.8.0.2

```

---

### Post by emptycoder on 2013-09-06
I have assigned all the IPs and other settings to let Ubuntu communicate with Windows:
Adapter 1 Host-only
IP address 192.168.56.1 netmask 255.255.255 gateway 192.168.56.2
I added those to vboxnet0 and to Windows shared network while DHCP is disabled.
I tried out the ping command [ping 192.168.56.1] and it works, ubuntu can see it.
But there's only a one thing that drives me crazy, how to make Ubuntu connect to the guest? Do I create a Wired Connection or what? because there's no network detection at all.
Also, I checked Network Servers and I found Windows Network but when I double click it it asks me for a password, the root password not working and Windows doesn't have a password.
Any idea?

---

