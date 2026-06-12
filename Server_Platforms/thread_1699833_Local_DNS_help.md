---
title: "Local DNS help"
date: 2011-03-04
forum: Server Platforms
---

### Post by Cerox Rex on 2011-03-04
Hello.

I'm up and running with a caching dns server and it works really well. I also have a total of two servers on my local network. on old sparc server running debain for dns and dhcp and one ubuntu for webhosting.

Both have webmin installed and running, but in order to accsess these i have to use the server ip adress wich is static.

I wish to add these two servers to my DNS server so i can accsess them by typing "nameofserver.local" in my webbrowser.

My dnz is configured autmaticly at install and have the following zones exept the root zone.

they are called "0","127","255"and"localhost"

Where do i add my servers? I'v tried to put em under localhost, but have not been able to make it work.

---

### Post by BkkBonanza on 2011-03-04
You should look into using "**dnsmasq**". It is very good for local DNS and DHCP combined and acts as caching nameserver for external names too. It's commonly used in linux based routers like the well known Linksys ones. A very good, easy to setup all round DNS/DHCP solution.

---

### Post by koenn on 2011-03-04
> **Cerox Rex said:**
> 
I wish to add these two servers to my DNS server so i can accsess them by typing "nameofserver.local" in my webbrowser.

you'd have to create a zone "local", and add A-records for your servers.
consult the manual for whatever DNS server you're running.

alternatively, if you run dnsmasq as BkkBonanza suggested (and +1), add the relevant names and addresses to the DNS server's /etc/hosts file and dnsmasq will resolve them.

---

### Post by hawkmage on 2011-03-04
Here is a link to an official Ubuntu BIND9 How To: [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
And here is a link to an old post here on the forums with info on setting up BIND9 as well: [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

---

### Post by Cerox Rex on 2011-03-06
Thanks for all tips. Feels good to make som progress :)

---

