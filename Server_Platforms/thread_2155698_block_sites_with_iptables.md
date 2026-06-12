---
title: "block sites with iptables"
date: 2013-06-19
forum: Server Platforms
---

### Post by iacoposk8 on 2013-06-19
Hello to all! I have to block access to certain sites to a network of PCs.
On the server - firewall I wrote:
```
iptables -A OUTPUT -d ip_site_to_be_blocked -j DROP
```

If I try to ping me error (and before restarting the service: /etc/init.d/iptables restart, this error was not there)
But the client (windows 7) continues to make the table correctly (after the restart) .. how to solve?
thanks :)

ps: this is squid as a proxy server, but in the configuration file is written that has been disabled (but do not know how and I can not start it again)

---

### Post by Cheesehead on 2013-06-19
The restart flushes IPtables. It forgets all previous commands and starts clean.
After restarting, the command must be input again. 

One easy way I use to input custom firewall commands is a script in /etc/network/if-up.d. Scripts in that directory are run each time an interface comes up using (using the ifup command). My script flushes IPtables, and then adds any rules I want.

Alternately, tools like UFW help you create persistent-across-restart firewall commands.

(Tip if you decide to use scripts: Comment everything! Six months in the future you won't remember what the commands mean or how to make changes. Also, link the script to your /home so you can find it again)

---

### Post by iacoposk8 on 2013-06-19
I entered again:
```
iptables -A OUTPUT -d ip_site_to_be_blocked -j DROP
```
this time I don't restarted iptables and if I ping the server I read (and rightly so):
```
ping: sendmsg: Operation not permitted
```
while the client ping works correctly (unfortunately): (

---

### Post by SeijiSensei on 2013-06-19
> **iacoposk8 said:**
> ps: this is squid as a proxy server, but in the configuration file is written that has been disabled (but do not know how and I can not start it again)

If squid is actually running as an HTTP proxy, and the clients are configured to use it, then you will have difficulties blocking HTTP traffic with iptables.  All the clients' traffic is sent to the proxy port, usually 3128, and then resent to the sites themselves.  So if you wrote a rule blocking a remote address on port 80, or even a rule for that address on port 3128, it will never be matched since all the traffic is sent to port 3128 on the proxy.

If you run the command "ps ax | grep squid" do you see a daemon running?  If not, try running "sudo service squid3 start".

If you are using squid, then you will need to learn how to write "[access control lists]("http://wiki.squid-cache.org/SquidFaq/SquidAcl")" to block specific domains or IPs.  For instance, you can have a ACL and related access rule like this:

```

acl facebook dstdomain -i facebook.com
http_access deny facebook

```

Then squid will block any traffic sent to the facebook.com domain.  (The "-i" means "case-insensitive.")  You can also replace "facebook.com" with the name of a file that contains a list of sites you wish to block.  Follow the link above for details.

---

### Post by iacoposk8 on 2013-06-20
if I run "ps ax | grep squid" I see:
```

12835 ?        Ss     0:00 /usr/sbin/squid -DYC
12837 ?        S      0:00 (squid) -DYC
19276 pts/0    S+     0:00 grep --colour=auto squid

```
if it can be useful, I think squid has been disabled so, but I'm not sure:
```

iptables -D PREROUTING -i eth0 -p tcp -m iprange --src-range 192.168.0.2-192.16$

```

---

