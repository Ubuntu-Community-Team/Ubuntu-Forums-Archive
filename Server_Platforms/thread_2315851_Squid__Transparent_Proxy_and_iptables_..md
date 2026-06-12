---
title: "Squid  Transparent Proxy and iptables ."
date: 2016-03-03
forum: Server Platforms
---

### Post by gardenair on 2016-03-03
hi,
     Just for testing purpose  I have just configured squid and add the server IP address in the client side browser  using windows 7. I have disable the iptables on it on the test server .
  Internet will works fine on the client side .Now I change my squid for Transparent Proxy.Add this in squid.conf file

```
http_port 3128 transparent
```

*My firewall is already disable*.

Actually I have never study iptables ,just disable it and do rest of the configuration. _The thing which I want to discuss is for  Transparent Proxy there is a  need to learn  iptables  ? Yes yes then it means that I have to learn 1st the iptable rules ? Am I correct ? _

I fallow this site [http://ubuntuserverguide.com/2012/06/how-to-setup-squid3-as-transparent-proxy-on-ubuntu-server-12-04.html](http://ubuntuserverguide.com/2012/06/how-to-setup-squid3-as-transparent-proxy-on-ubuntu-server-12-04.html)

but at in iptable i just disable it. 

please guide me for  Transparent Proxy  configuration.

---

### Post by SeijiSensei on 2016-03-03
Yes, you need to have an iptables rules to run a transparent proxy.  Usually it looks like this:
```
/sbin/iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 3128 -s local_subnet --dport 80
```

Replace "local_subnet" with the appropriate value for your network, e.g., 192.168.1.0/24.

That may be all you need if there are no other firewalling rules on the box.  Try running that command from the terminal prompt and see if it fixes the problem.  If so, you can put the rule in the file /etc/rc.local (without the sudo prefix) so the rule will be set whenever the machine reboots.

---

### Post by gardenair on 2016-03-04
Thanks "[COLOR=#000000]SeijiSensei" for your kind reply. Well I am new in iptables ,I want to learn iptables from scratch .any good site from where I may start its tutorials .

2- As for the [/COLOR]transparent proxy you write the iptable for it which you have mentioned ,I just write the same statement in my terminal window,press enter key it show me message " Bad argument 'PREROUTING'.

I google for transparent proxy and it show me site

[http://www.iitk.ac.in/LDP/HOWTO/TransparentProxy-4.html](http://www.iitk.ac.in/LDP/HOWTO/TransparentProxy-4.html)

and for iptables 

[http://www.iitk.ac.in/LDP/HOWTO/TransparentProxy-5.html](http://www.iitk.ac.in/LDP/HOWTO/TransparentProxy-5.html)

I did according to it (only IPTABLES) , it silently access enter key without any message but in client side no success.

---

### Post by SeijiSensei on 2016-03-04
You need to run iptables as root with sudo.  Sorry I left off the sudo at the beginning of the command.  If you put the command in /etc/rc.local, don't include the sudo.  That script runs with root privileges by default.

If it still doesn't work, please report the exact command you used here inside [noparse]```

```[/noparse] tags.

To see if the rule has been added you can run the command
```
sudo iptables -t nat -L -nv
```

The first page you linked to is for an older version of Squid like 2.x.  Take a look at [http://wiki.squid-cache.org/SquidFaq/InterceptionProxy](http://wiki.squid-cache.org/SquidFaq/InterceptionProxy) instead.  The page about iptables shows a rule nearly identical to the one I gave you, except rather than specifying the source of the traffic with "-s" it uses "-i eth0" which refers to the interface to which the local network connects.  Either way works, though you need to make sure you have the correct network subnet for "-s" or interface for "-i".

Just to make sure, this is a box with two network interfaces, right?  One that points upstream to the Internet and the other connected to your local network?  Oh, and I assume you've already tested this without the transparent proxy by explicitly configuring a browser to use the Squid box as a proxy.  Make sure that works before moving on to transparency.

I taught myself iptables by reading the man page and experimenting.  I can't point you to a specific source to learn from, but you might start with this: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by gardenair on 2016-03-04
thanks for the prompt reply. Well i use sudo command . I am using private ip address in my small office with 10.1.83.0/24 and my server own ip address is 10.1.83.10 which I address in client side network card gateway


```
# iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 3128 -s 10.1.83.0/24  --dport 80
Bad argument 'PREROUTING'
Try 'iptables -h or iptables --help for more information
```

**client side**
```
10.1.83.25
255.255.255.0
10.1.83.10

DNS 8.8.8.8
```

Well one thing I forgot to mentioned that i am using a single network card, (It is a test box) ,without transparent proxy my squid fetch the web pages.For a single network card which should be the iptables

---

### Post by SeijiSensei on 2016-03-04
I only ever have used transparency on hosts with two interfaces, one facing the Internet and one facing the LAN, with the Squid box defined as the network's default gateway.  To make transparency work with one box, you'd need to configure your *gateway router* to redirect traffic for port 80 back to the port 3128 on the Squid box.  You wouldn't need any iptables rules in this case, but how you do the redirection depends on the features of your gateway router.

I have no idea why you get the "bad argument" error.  I did a test on a 14.04 machine, and it worked for me.  Still it doesn't matter in your case unless you add another network interface to the Squid box and put it in between the LAN and the gateway router.

---

