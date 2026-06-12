---
title: "Problem disabling cupsys"
date: 2016-02-09
forum: Security
---

### Post by juan53 on 2016-02-09
Hi
I write this post because I tried to disable cupsys and related services.

With no activity on the desktop, after using nmap tool by typing:
nmap localhost
999 ports were closed and port 631 was opened by using ipp which aparently is related with printing services.
When I issued:
sudo service cups stop
And I checked ports again, All of 1000 ports were closed. To this point all were normal.
I issued:
sudo update-rc.d -f cupsys stop
Nothing special happened. I rebooted and checked the ports again: 999 closed, one opened (631).
I installed "bum" and unchoose the capsys and capsys-browser. I reinstalled, and again, 999-1.

I checked ports by using "netstat -plnt" and two ports were listened: 53 (tcp) (which I supposse that this is the port to say the router "ey, hello, i'm here") and 631 (tcp).

I checked the service asociated with the port (cat /etc/services | grep 631) with this result:
ipp 631/tcp #Internet Printing Protocol
ipp 631/udp

Could you tell me what is going on in my laptop and how could I close this port (I don't need network printer)?

I want to add that I've got ufw with no permission over port 631. In fact I try to close it by using ufw deny 631 (with no effect over the port).
Thanks for your time.

---

### Post by juan53 on 2016-02-09
For other users in the same situation. I solved the situacion by removing all the pacages related with cups, with the exception of libraries and python-related parts.
I issued:

dpkg -l | grep cups

The elements related with cups were listed. After that, I removed one by one:

sudo apt-get remove (cups/cups-browsed/cups-bsd/cups-client/cups-common/cups-core-drives/cups-daemon/cups-filters/cups-filters-core-drivers/cups-pk-helper/cups-ppdc/cups-server-common)

I guess if you could reinstall all the pacages you could, but I think it's a risk you can aboid if your is not conected to your local network.

---

