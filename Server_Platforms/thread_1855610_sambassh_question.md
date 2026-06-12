---
title: "samba/ssh question"
date: 2011-10-06
forum: Server Platforms
---

### Post by Maddjokerz on 2011-10-06
I have recently created a samba/ssh server on an old desktop. I would like to be able to access my samba server outside of my home network and can not find any information on how to do that. I also have found information on how to port forward so then I can ssh from outside my network. I would just like to connect to those files from any network, any help will be appreicated.):P

---

### Post by smurphy_it on 2011-10-06
For starters, get yourself a DDNS account on something like no-ip.org, dyndns.org so you don't need to remember the IP all of the time.

Second setup a port forward in your router and allow access to that port from the internet.

---

### Post by collisionystm on 2011-10-06
> **Maddjokerz said:**
> I have recently created a samba/ssh server on an old desktop. I would like to be able to access my samba server outside of my home network and can not find any information on how to do that. I also have found information on how to port forward so then I can ssh from outside my network. I would just like to connect to those files from any network, any help will be appreicated.):P


Are you going to access your box using a Windows computer?

If so, just worry about port forwarding SSH.

You can use WINSCP to access your box via ssh and browse it just like you would in samba.

[http://winscp.net/eng/download.php](http://winscp.net/eng/download.php)

To port forward your stuff, we just need to know what kind of router you have. I assume its linksys?

You can probably just open your web browser and type

[http://192.168.1.1](http://192.168.1.1)

This will take you to a login page

your credentials are probably one of these

username = <blank>
password = admin

username = admin
password = admin

username = admin
password = password

username = cusadmin
password = highspeed

---

### Post by Maddjokerz on 2011-10-06
Thanks I will have to try those out once I get off of work, now I'm excited about losing more sleep than I did last night :biggrin:

---

### Post by collisionystm on 2011-10-06
> **Maddjokerz said:**
> Thanks I will have to try those out once I get off of work, now I'm excited about losing more sleep than I did last night :biggrin:

lol its easy.

I assume you have no performed any custom DHCP scopes at your house... so 192.168.1.1 is the 99.9% correct router address.

Once you are in, you will see a section for port forwarding.

Forward port 22 to your servers IP address.

Then go to [http://www.whatismyip.com/](http://www.whatismyip.com/) to get your internet visible ip address.

Then remotely you should be able to ssh to that address and hit your server! Have fun. WINSCP is a great program. Just found it the other day....

---

