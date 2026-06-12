---
title: "DynDNS, tomcat6, ddclient, port forwarding"
date: 2011-05-30
forum: Server Platforms
---

### Post by J05HYYY on 2011-05-30
Hello, I want to run a java servlet on my computer for the world to see. I have signed up with DynDNS because I have a dynamic ip and installed ddclient (hopefully successfully). Tomcat6 runs on port 8080 but http requests are through port 80.

I heard that one can route using iptables but I have had no luck, everytime I go to [http://localhost:80](http://localhost:80) I get muck; "Unable to connect" the error is, hoping to get helped out by a computer techno wizz.


Cheers.

---

### Post by ruffEdgz on 2011-05-30
Can you show us the output of the following command:
```

iptables -L

```
This will display the chains in your iptables so we can take a look at what you have done there.

---

### Post by J05HYYY on 2011-05-30
I ran this:

```

sudo iptables -t nat -I PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080
```

"iptables -L" doesn't show much:

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

```

"iptables -t nat -L" shows this:
```

Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
REDIRECT   tcp  --  anywhere             anywhere            tcp dpt:www redir ports 8080 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination       
```

---

### Post by ruffEdgz on 2011-05-30
Thanks for showing both but the first one you showed might be the issue.

You will need to first accept traffic from all the ports you need involved so in this case, we need ports 80 and 8080 to be open:
```

iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT

```
You might have the redirect in place but the port 8080 should be blocked by iptables.

Hope that helps.

---

### Post by J05HYYY on 2011-05-30
Thanks, iptables now shows this but I still can't get to the tomcat success page by typing [http://localhost:80](http://localhost:80) - is this a problem?

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http-alt 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

---

### Post by ruffEdgz on 2011-05-31
I forgot one other question that could be helpful in this problem. Did you make the tomcat user and is it a normal user or system user? Also if you run the command below, do you see port 80 open?:
```

sudo nmap localhost

```
Thanks!

---

### Post by J05HYYY on 2011-06-01
Don't worry, I gave up trying to do this on the machine itself, instead, using my router, I forwarded port 80 to port 8080, seemed to work well although I am having troubles running my servlet from the outside.

---

