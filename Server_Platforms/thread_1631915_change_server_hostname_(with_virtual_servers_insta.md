---
title: "change server hostname (with virtual servers installed)"
date: 2010-11-27
forum: Server Platforms
---

### Post by chaemil on 2010-11-27
hi. i have a problem with server bcs of the machine name. and i'm wondering how to change the server name to it's IP. bcs now it has name "chrochne". i've found hostname in /etc/host and in /etc/hostname. but i'm afraid of changing it in this files.

P.S. I'm using webmin and virtualmin to admin the server so can i change the name somewhere in the GUI?

---

### Post by windependence on 2010-11-27
You really should try to learn a little command line, it's not hard and we can help :-)
 
Edit your hosts file in a text editor and format like this:
 
```
 
123.123.123    chrochne

```
 
Where 123.123.123 is your ip address (substitute your real address here).
 
-Tim

---

### Post by chaemil on 2010-11-27
but "chrochne" is not the public name. i want to change the server name to the public IP like in the installation of the OS.
 
I'm dont want to change the content of the file /etc/hosts or /etc/hostname bcs i'm affraid of rebooting the server after that change. Isn't that too hard change of the system variables?

---

### Post by windependence on 2010-11-27
I'm not sure what you are refferring to as the public name of the server. Do you mean the fully qualified domain name? If so, it can't be an IP address.
 
What is the output of:
 
```
 
hostname

```
 
-Tim

---

### Post by chaemil on 2010-11-27
The hostname command print out "chrochne". But i dont have a domain name only public IP and on it i have some virtual servers. But I have problem with forwarding emails from webmail client on virtual host, bcs the "chrochne" don't have public dns.

---

### Post by windependence on 2010-11-27
Exactly, and that is the problem. Most mail servers won't even talk to you if you don't have proper public DNS set up including PTR or "reverse DNS". You really need domain names to do what you are doing.
 
-Tim

---

### Post by chaemil on 2010-11-27
And is there anyway to change the hostname in the all files. So it's only about translating IP to DNS?

---

### Post by windependence on 2010-11-27
You can change it temporarily to test it by doing :
 
```
 
hostname newhostname

```
 
Where newhostname is the name you want to give the server. It will stay that way until you reboot. If it works and you want to make it permanent, then you will have to change the /etc/hostname file.
 
-Tim

---

### Post by chaemil on 2010-11-27
thanks. but i've solved it some other way. it was not problem with the host name. i have reserved domain name in postfix, so i've removed it and now it's working. but i've another question what about firewall it's necessary to enable it?

---

### Post by windependence on 2010-11-27
IMHO you should always run a hardware firewall separate from the production box. I don't run the Ubunutu firewall on any of my boxes, they are protected by a pfsense harware firewall.
 
-Tim

---

