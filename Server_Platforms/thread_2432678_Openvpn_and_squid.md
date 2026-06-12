---
title: "Openvpn and squid"
date: 2019-12-06
forum: Server Platforms
---

### Post by Tommy_Holmgren on 2019-12-06
[COLOR=#28292E][FONT=Roboto]Hello[/FONT][/COLOR]
[COLOR=#28292E][FONT=Roboto]I have already setup openvpn and squid proxy on my vps but it refuse to connect with my client pc. Anyone knows how to config ufw or iptables for this correctly?[/FONT][/COLOR]

---

### Post by TheFu on 2019-12-06
More details of the setup are needed. Where is the client? Where is the server?  What is the goal?  There are many, many, different configurations of those tools which could be employed. Cannot tell what you are trying to accomplish.

I'm confused where you want to configure ufw or iptables too. On your clients?

I'm just confused.

---

### Post by SeijiSensei on 2019-12-06
Are you trying to connect to squid over an OpenVPN tunnel?  Do you have an ACL for the OpenVPN address block? An http_access declaration for that ACL? Is Squid listening on its default port of 3128?  Have you configured your browser to use the proxy?  

You shouldn't need much in the way of iptables rules unless you're trying to set up a transparent proxy.  Then you need a rule like
```
/sbin/iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 3128 --dport 80
```
and the Squid directive
```
http_port 3128 transparent
```

---

