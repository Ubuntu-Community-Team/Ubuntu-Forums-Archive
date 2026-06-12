---
title: "Help with ufw"
date: 2017-03-28
forum: Server Platforms
---

### Post by JoshM4789 on 2017-03-28
Im getting this error when i try to run this command (/lib/ufw/ufw-init start)

: not foundw-init: 3: /etc/default/ufw:

and when i try to run

ufw enable

i get this

ERROR: problem running ufw-init
/lib/ufw/ufw-init: 3: /etc/default/ufw:
: not found

any help would be nice
pretty sure i screwed up something somewhere but i dont know what.

---

### Post by darkod on 2017-03-29
Trust me, the best advice is do not use ufw. :)

Few years back when I had no idea of iptables I used ufw for one project, and it took very little time to realize iptables is much better to work with and ufw is just a frontend with many issues...

Usually you would make a file for example /etc/iptables.rules and put your rules there. Then load it by putting this line in /etc/network/interfaces within your main interface:
```
post-up iptables-restore < /etc/iptables.rules
```

That will load them on each boot. While testing you can load the rules on the command line with the same iptables-restore command.

When using iptables directly the rules are much clearer, and expecially their listing. If you run the following command on a system that uses ufw and one that doesn't you will see what I mean:
```
sudo iptables -L -n -v
```

As for your question, if you insist on using ufw, I guess something is wrong with the package and you can first try to purge it and reinstall it:
```
sudo apt-get purge ufw
sudo apt-get install ufw
```

If with any firewall rules (iptables or ufw), and especially if you have only remote access to the system, make sure you don't lock yourself out. :)

---

### Post by JoshM4789 on 2017-03-29
well im following this guide so if you know how to replace ufw in this case im all ears [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04).

---

### Post by JoshM4789 on 2017-03-29
but thanks it worked but if its as bad as you say im still willing for any changes

---

### Post by darkod on 2017-03-29
Well, this is a basic /etc/iptables.rules that I use:
```
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]

-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i ens3 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
-A INPUT -i ens3 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j DROP
-A INPUT -i ens3 -p tcp --dport 22 -j ACCEPT

COMMIT
```

That allows ssh from outside on standard port 22. Make sure to check the name of your public interface and adjust ens3 if necessary. In my case it was ens3.

On top of these basic rules, you can add any specific rules you need. Always add rules above the COMMIT line. The COMMIT should be last and it should always be there.

For example if you have webserver and you want to allow the whole world access on port tcp/80, you would add:
```
-A INPUT -i ens3 -p tcp --dport 80 -j ACCEPT
```

I think most of this is self explanatory. You have loads of examples of iptables rules on the internet, just integrate them into your setup.

But all of this is up to you. I personally like iptables more because it is cleaner when listing the rules. ufw has also a way to see current rules but if you use the standard iptables command:
```
sudo iptables -L -n -v
```

There is too much confusion for my liking in that list when using ufw. When using directly iptables, the list is cleaner and shows just your rules, nothing more.

---

