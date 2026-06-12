---
title: "Hostname based ssh reverse proxy?"
date: 2009-01-02
forum: Server Platforms
---

### Post by moto_tux on 2009-01-02
Hi guys,

I have a small home network with a few (virtual) servers each with internal IPs.  I would like to be able to ssh to each server transparently based on name, in the same way that apache reverse proxy can work.

eg
[email]user@srv1.mydomain.com[/email]  goes to server 1
[email]user@srv2.mydomain.com[/email]  goes to server 2
etc...

where *.mydomain.com is the same IP as mydomain.com

I cannot tell from anywhere if the ssh protocols even send the destination name, the "srv1" bit being important, like http does...

I know it's possible to use a different port for each such as in this guide
[http://www.howtoforge.com/reverse-ssh-tunneling](http://www.howtoforge.com/reverse-ssh-tunneling)
but I like the elegance of this way, some pointers would be greatly appreciated :)

I should say I'm a relative newb in this kinda thing (and most others :? ), so maybe I'm barking up the wrong tree and there is a much better approach.  I simply want secure terminal access to each server in one "hop" so it's transparent.

thanks,
marc

---

### Post by HermanAB on 2009-01-02
Each VM should be configured with a static IP address.  Then simply put entries in /etc/hosts to define the FQDN and IP Address.  The machine Domain Name Resolver first look in the hosts file before querying a Domain Name Server.

Hope that helps.

Herman

---

### Post by moto_tux on 2009-01-02
Hi Herman,

Thanks for the response, I'm not sure it quite fits my situation though...

I think you are suggesting for each server to have it's own FQDN/internet route-able IP?

...Or that I put the internal static IPs (192.168.x.x) into /etc/hosts?

I should be clearer with my situation.  Each VM does have a static internal ip (192.168.1.xxx) but I would like external access as well.  As I only have basic home broadband with a single dynamic IP, i have registered with dyndns which works ok.

My firewall/router (IPCop) forwards all web requests to an apache reverse proxy (192.168.1.100) which "routes" (virtual hosts and libapache2-mod-proxy-html) http traffic based on the hostname:

[www.mydomain.com](www.mydomain.com) --> 192.168.1.101
dev.mydomain.com --> 192.168.1.102
demo.mydomain.com --> 192.168.1.103
etc

I am looking to achieve the same effect with ssh.  I know it's not as simple as that looks as the request is essentially re-issued by apache which can cause issues.

Currently I just forward ssh to one server then go from there...  I am not sure if what I want to do is feasible, but I am interested to know...

I have tried setting host's on IPCop but this only seems to have an effect from inside the network, and /etc/hosts on the proxy only effectual when leaving the host, so i need something to re-send it anyway.

Perhaps I'm not handling http requests in the simplest of ways either, I shall look more at IPCop configuration, pointers there would do no harm too

Thanks again (I hope I'm making some kind of sense here)
Marc

---

### Post by beeman on 2009-01-03
Interesting topic, I'd love to have the same sort of setup. I did a test using [nginx]("http://nginx.net/") as a name-based HTTP reverse proxy, which works quite well, but unfortunately I have not figured out how to do it with the SSH protocol.

---

### Post by HermanAB on 2009-01-03
1. Put the internal static IPs (192.168.x.x) into /etc/hosts.

If you have only ONE public IP address for yourdomain.com:
2. In each VM /etc/ssh/sshd_config add a line like "port 2201", "port 2202", "port 2203" for each VM so that each has an additional listener on a unique port, then restart sshd.
3. In IPcop, forward ports 2201 to 2203 to the IP addresses of the VMs.
4. To access your VMs from the public internet, use "ssh [email]user@yourdomain.com[/email] -p 2201" for example.

If you can waste three IP addresses for your domain.com, then you can simply forward those to port 22 on each VM, but I sure would not do that - IP addresses are costly.

Hope that helps.

Herman

---

### Post by moto_tux on 2009-01-03
Nice one, I have gone with your approach except I am forwarding from port 2201-2203 to port 22 for each VM in IPCop, so I can skip step 2 ;) Thanks for the tip though, it looks like the closest I am going to get.  You are right, I can't justify getting more IPs, and IPv6 seems to be dragging it's heels...

beeman, nginx looks interesting - i see it has mail proxy features too. I think I will stick with apache for the moment though, it's early days for me and I don't want to get too confused :rolleyes:

Thanks again, if I can find a way to forward based on the hostname then I'll share it here

---

### Post by timbobsteve on 2009-03-20
Just for future reference, Apache's HTTP Reverse Proxy functions are specific to the HTTP/HTTPS protocol and cannot be applied to other protocols. SSH specifically just uses the IP address and does not do any hostname lookups, so using mydomain.com or specifying the IP address manually will have the same effect on the SSH daemon.

The easiest method is to setup a single internal SSH server that has external port 22 forwarding to it, SSH to that then use that server as an intermediate to access all private servers. This is probably a lot safer too as it limits all external connections to one box on your network, which makes it easier to manage.

Hope this helps some people looking for similar solutions.

---

