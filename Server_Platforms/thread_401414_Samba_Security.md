---
title: "Samba Security"
date: 2007-04-04
forum: Server Platforms
---

### Post by Aberrix on 2007-04-04
I have a server (6.10) with ISPConfig installed. It is open to the world (dmz behind my router), however it does have a firewall (ISPConfig built in), I would like to use Samba but am scared about attacked via the web.

I would like to lock it down so shares are only accessible via my LAN (192.169.0.X) and also need to know what port(s) to open in my firewall.

anyone done anything like this before? thanks in advance.

---

### Post by huygens on 2007-04-04
If I wanted to share files on my server which is accessible via internet, I would do it with SSH. Not only can Linux mount a SSH connection as a hard drive (go to Places->Connect to server in the Gnome menus), but you could tunnel Samba through SSH.
With SSH you can set strong authentication using keys. SSH connection can be both encrypted and compressed.

To simply mount SSH connection, just enter the correct information in the menu item I have just pointed out above.
For the second option, perhaps you could look at an [article on tunneling through SSH (includes an example with Samba)]("http://www.berthon.eu/wiki/perso:dump:lnx:list_of_useful_commands#tunneling") I have written. However, this article is just a brain dump for commands I know/learned, so it might be techy/uncomprehensible/difficult/messy.... you name it ;-)

If you want to have Samba only accessible from your local network, you need to use the "interfaces" option that you can find in your smb.conf (under /etc/samba)
For example if your server does have two interfaces one eth0 connected to the local lan, the other eth1 connected to internet. You should put only eth0 for interfaces, like: 
```
interfaces = 127.0.0.0/8 eth0
```However, if you have one interface only, you will need to set the rule on the firewall and it becomes a bit more complex and I do not know how to help you, because this set of rules would be dependant of your DMZ or network set-up... which I do not know.

---

