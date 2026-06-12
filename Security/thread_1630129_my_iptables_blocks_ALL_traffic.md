---
title: "my iptables blocks ALL traffic"
date: 2010-11-24
forum: Security
---

### Post by djangobanana on 2010-11-24
Hello
I have set up my iptables following basic security guidelines, but all traffic is blocked if I follow the basic security rules of starting with :

[PHP]
iptables -t filter -P INPUT DROP 
iptables -t filter -P FORWARD DROP 
iptables -t filter -P OUTPUT DROP
[/PHP]Right now, I have these rules commented out, otherwise no traffic is allowed, which gives me no security if I understand correctly.

My entire iptables is as follows :

[PHP]
#!/bin/sh 
 
# empty current tables
iptables -t filter -F 
 
# empty personal rules
iptables -t filter -X 

iptables -Z
 
# forbid all in & out connection
iptables -t filter -P INPUT DROP 
iptables -t filter -P FORWARD DROP 
iptables -t filter -P OUTPUT DROP 
 
# --- 
 

# ICMP (Ping)  (drop for additional security)
iptables -t filter -A INPUT -p icmp -j DROP
iptables -t filter -A OUTPUT -p icmp -j DROP
 
# SSH In 
iptables -t filter -A INPUT -p tcp --dport 2222 -j ACCEPT 
# SSH Out 
iptables -t filter -A OUTPUT -p tcp --dport 2222 -j ACCEPT 
 
# DNS In/Out 
iptables -t filter -A OUTPUT -p tcp --dport 53 -j ACCEPT 
iptables -t filter -A OUTPUT -p udp --dport 53 -j ACCEPT 
iptables -t filter -A INPUT -p tcp --dport 53 -j ACCEPT 
iptables -t filter -A INPUT -p udp --dport 53 -j ACCEPT 
 
# NTP Out 
iptables -t filter -A OUTPUT -p udp --dport 123 -j ACCEPT 

# HTTP + HTTPS Out 
iptables -t filter -A OUTPUT -p tcp --dport 80 -j ACCEPT 
iptables -t filter -A OUTPUT -p tcp --dport 443 -j ACCEPT
# HTTP + HTTPS In 
iptables -t filter -A INPUT -p tcp --dport 80 -j ACCEPT 
iptables -t filter -A INPUT -p tcp --dport 443 -j ACCEPT 
iptables -t filter -A INPUT -p tcp --dport 8443 -j ACCEPT 

# FTP Out 
iptables -t filter -A OUTPUT -p tcp --dport 20:21 -j ACCEPT 
# FTP In 
iptables -t filter -A INPUT -p tcp --dport 20:21 -j ACCEPT 
 
# Mail SMTP:25 
iptables -t filter -A INPUT -p tcp --dport 25 -j ACCEPT 
iptables -t filter -A OUTPUT -p tcp --dport 25 -j ACCEPT 
# Mail POP3:110 
iptables -t filter -A INPUT -p tcp --dport 110 -j ACCEPT 
iptables -t filter -A OUTPUT -p tcp --dport 110 -j ACCEPT 
# Mail IMAP:143 
iptables -t filter -A INPUT -p tcp --dport 143 -j ACCEPT 
iptables -t filter -A OUTPUT -p tcp --dport 143 -j ACCEPT 
# Mail POP3S:995 
iptables -t filter -A INPUT -p tcp --dport 995 -j ACCEPT 
iptables -t filter -A OUTPUT -p tcp --dport 995 -j ACCEPT 
[/PHP]Does anyone has any idea why traffic is blocked even after allowing rules to let http and ssh through ?

Thank you

---

### Post by SebastianG63 on 2010-11-24
<iptables ... -P ...> creates a standard rule, while <iptables ... -A ...> appends additional rules. As long as you do not comment out the standard rules, the following ones might in your case, properly do just nothing, after you already droped packets from the section continaing:

[PHP]
# forbid all in & out connection
iptables -t filter -P INPUT DROP 
iptables -t filter -P FORWARD DROP 
iptables -t filter -P OUTPUT DROP 
[/PHP]So this part needs possibly a change, depending on what you want your firewall to do besides your ACCEPT rules for all remaining traffic.

But that's just a guess, since I am not an iptables expert.


Btw ... I do not get where you commented the rules out, since that would look like:
[PHP]
# forbid all in & out connection
#iptables -t filter -P INPUT DROP 
#iptables -t filter -P FORWARD DROP 
#iptables -t filter -P OUTPUT DROP 
[/PHP]But I did not see such section in your second code fragment?!

At least you might want to change the order of your <iptables ... -P ... DROP> rules take effect by placing them at the very end of your script?

---

### Post by emiller12345 on 2010-11-25
> **djangobanana said:**
>  [PHP]
# HTTP + HTTPS Out 
iptables -t filter -A OUTPUT -p tcp --dport 80 -j ACCEPT 
iptables -t filter -A OUTPUT -p tcp --dport 443 -j ACCEPT
# HTTP + HTTPS In 
iptables -t filter -A INPUT -p tcp --dport 80 -j ACCEPT 
iptables -t filter -A INPUT -p tcp --dport 443 -j ACCEPT 
[/PHP]Does anyone has any idea why traffic is blocked even after allowing rules to let http and ssh through ?

Thank you

Not sure but should this be?

```
# HTTP + HTTPS Out 
iptables -t filter -A OUTPUT -p tcp --dport 80 -j ACCEPT 
iptables -t filter -A OUTPUT -p tcp --dport 443 -j ACCEPT
# HTTP + HTTPS In 
iptables -t filter -A INPUT -p tcp --sport 80 -j ACCEPT 
iptables -t filter -A INPUT -p tcp --sport 443 -j ACCEPT 

```

---

### Post by SebastianG63 on 2010-11-25
--dport = destination port of the packet
--sport = source port of the packet

But this all this does not solve the problem, that all packets are thrown away before one of the ACCEPT-rules will ever see any packet.
'iptables' is order sensitiv when it comes to rules within the same processing stage.

The processing flow for packets is:

PREROUTING >> INPUT >> (Application-Level) >> OUTPUT >> POSTROUTING
PREROUTING >> FOREWARD >> OUTPUT >> POSTROUTING

Within the domain of INPUT the rules are stored by iptables just in order they were applied to 'iptables'. When a <...INPUT...DROP> for all types of packets is placed before any else rule, the following rules for <...INPUT...> will never take place no matter what flags they contain when stored (-P , -A, -I, ...).
'iptables' does not internally reorder the definitions by some scheme at any time, apart from when it is told to do so (-I flag).

Along with -P and -A definitions in the given script from the original poster we might expirience a **First comes, first fits, first serves** scheme.

But you are right, [emiller12345]("http://ubuntuforums.org/member.php?u=1095960"), the definitions containing all a '--dport' seems to be an issue also, or a very rare case scenario!
But we do not know if this machine is a pure client-machine or a server-machine and from this it is unclear where '--dport' and '--sport' would be correct with the script and the rules are possibly also incomplete, at least when performing something like 'ntpdate'?!

---

### Post by bodhi.zazen on 2010-11-25
See also:

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by djangobanana on 2010-11-25
Thank you SebastianG63 and emiller12345 for your explanations.

I actually made a few modifications, and it works, but i just don't see where the change could have come from

My primary goal was to make my server secure hence the 3 rules to start with :
[PHP]
# forbid all in & out connection
iptables -t filter -P INPUT DROP 
iptables -t filter -P FORWARD DROP 
iptables -t filter -P OUTPUT DROP  
[/PHP]but everything remained blocked even after adding these rules to open HTTP and SSH
[PHP]
# HTTP + HTTPS Out 
iptables -t filter -A OUTPUT -p tcp --dport 80 -j ACCEPT 
iptables -t filter -A OUTPUT -p tcp --dport 443 -j ACCEPT
# HTTP + HTTPS In 
iptables -t filter -A INPUT -p tcp --dport 80 -j ACCEPT 
iptables -t filter -A INPUT -p tcp --dport 443 -j ACCEPT  
[/PHP]so that's why I had commented out the first 3 rules, which left my server totally open ! not good !

But now, it works, I don't understand what I did that is different, at least in the logic it is the same :
first blocking all traffic with the 3 rules
then, open on a case by case basis, http and others...

But it works, so it's the most important ;)
> 
But we do not know if this machine is a pure client-machine or a server-machine
I'm looking to have an LAMP serving a few sites to the public.


Thank you bodhi zazen, i actually had found your page before, and will use your instructions to scan the security of my server

---

### Post by SebastianG63 on 2010-11-25
Perhaps it makes a good choice to re-order your script by the following scheme(?):


 1) Inject all individual excepetions from what you would like to allow for e.g. INPUT/OUTPUT, like [COLOR=Blue]iptables -t filter [COLOR=Red]-[/COLOR][/COLOR][COLOR=Blue][COLOR=Red]A[/COLOR] INPUT -s 141.1.1.1 -p tcp --dport 2222 -j DROP[/COLOR]

2) Inject all rules that allow stuff (-A flag) for e.g. INPUT/OUTPUT, like [COLOR=Blue]iptables -t filter [COLOR=Red]-A[/COLOR] INPUT -p tcp --dport 2222 -j ACCEPT[/COLOR]

3) Place your remaining default rules, for all what you want to disallow (DROP with -P flag) but did not specify before, like [COLOR=#000000][COLOR=Blue]iptables [/COLOR][COLOR=Blue]-[/COLOR][COLOR=Blue]t filter [/COLOR][COLOR=Red]-[/COLOR][COLOR=Blue][COLOR=Red]P[/COLOR] INPUT DROP[/COLOR][COLOR=#0000bb][COLOR=Black] or [/COLOR][/COLOR][/COLOR][COLOR=#000000][COLOR=Blue]iptables [/COLOR][COLOR=Blue]-[/COLOR][COLOR=Blue]t filter [/COLOR][COLOR=Red]-[/COLOR][COLOR=Blue][COLOR=Red]P[/COLOR] INPUT [/COLOR][COLOR=Blue]-[/COLOR][COLOR=Blue]p icmp [/COLOR][COLOR=Blue]-[/COLOR][COLOR=#0000bb][COLOR=Blue]j DROP[/COLOR]
[COLOR=Black]

Such scheme seems to be safe along with the order sensitive filtering mechanics, as long as you do not specify explicit ordering by making use of the [COLOR=Navy][COLOR=Blue]<... [COLOR=Red]-I[/COLOR] [num] ...>[/COLOR] [COLOR=Black]insertion flag[/COLOR][/COLOR].

The [COLOR=Blue]<... [COLOR=Red]-P[/COLOR] ...>[/COLOR] rules are used to specify fallbacks/defaults that are valid for all else cases, that were not explicitly defined.
So it's more like a rule to add at the end of something, to cover all what was not covered before, and possibly not the one to place right at the start of definitions?!
As long as ordering and [COLOR=Blue]<... --inject [num] ...>[/COLOR] exists, there is no guaranty that any packet will survive a general <[/COLOR][/COLOR][/COLOR][COLOR=#000000][COLOR=Blue]iptables [/COLOR][COLOR=Blue]-[/COLOR][COLOR=Blue]t filter [/COLOR][COLOR=Red]-[/COLOR][COLOR=Blue][COLOR=Red]P[/COLOR] INPUT DROP[/COLOR][COLOR=#0000bb][COLOR=Black]>[/COLOR][/COLOR][/COLOR][COLOR=#000000][COLOR=#0000bb][COLOR=Black] rule and ever see any else rule defined later after such a definition. In fact, if everything is all right, no packet will survive a general [/COLOR][/COLOR][/COLOR][COLOR=#000000][COLOR=#0000bb][COLOR=Black]<[/COLOR][/COLOR][/COLOR][COLOR=#000000][COLOR=Blue]iptables [/COLOR][COLOR=Blue]-[/COLOR][COLOR=Blue]t filter [/COLOR][COLOR=Red]-[/COLOR][COLOR=Blue][COLOR=Red]P[/COLOR] INPUT DROP[/COLOR][COLOR=#0000bb][COLOR=Black]>[/COLOR][/COLOR][/COLOR] rule!
[COLOR=#000000][COLOR=#0000bb][COLOR=Black]
Remember, all filtering rules injected by iptables, get internally at least a monoton incrementing sequence number, that describes at the same time the order of execution within the kernel filtering!

[/COLOR][/COLOR][/COLOR]

---

### Post by bodhi.zazen on 2010-11-25
1. You can drop the "-t filter" from your commands.

"iptables -t filter -P INPUT DROP" is the same as

```
iptables -P INPUT DROP
```

2. I think you need to read a bit on how iptables and ports work. See the link I gave you.

3. Rather then setting a default policy as DROP, I advise you make the last rule in your chain to drop all traffic

```
iptables -A INPUT -j DROP
```

This way if you flush your rules you do not lock yourself out.

4. You can not have your cake and eat it too. Either you allow connections or you do not.

Fron the clinet side, either you allow Firefox out onto the internet

```
iptables -A OUTPUT -p tcp --match multiport --dports 80,443 -j ACCEPT
```

Or you do not 
```
iptables -A OUTPUT -p tcp --match multiport --dports 80,443 -j DROP
```

As far as protecting from potential firefox exploits, keep firefox up to date and use Apparmor, iptables will not help.

Similar reasoning for accepting traffic on services. Either you run Apache as a public server (accept all traffic) or not (drop all traffic). 

Some services such as ssh you will run a white list allowed IP and drop the rest.

Some services, such as Apache and often ftp, you will allow most IP and drop or black list a short list.

So you need to understand what services you are running, what ports they listen on, what clients you allow, what ports they connect to, and if you wish to run a black list or white list.

---

### Post by djangobanana on 2010-11-29
Hi SebastianG63
```

The <... -P ...> rules are used to specify fallbacks/defaults that are valid 
for all else cases, that were not explicitly defined.

```i had it opposite. I thought you blocked all traffic to be safe, then open on a case by case basis what you need.


Hi bodhi.zazen

```
1. You can drop the "-t filter" from your commands.
```yes, i know, but since there are 3 tables as I understand correctly, i just like to be reminded of that, and it's more scholar, ain't it ;)

```
2. I think you need to read a bit on how iptables and ports work. See the link I gave you.
```yes I do ! thanks for the link


```
3. Rather then setting a default policy as DROP, I advise you make 
the last rule in your chain to drop all traffic

Code:

iptables -A INPUT -j DROP
```I don't understand. I want to allow certain traffic. If I put it at the end of my exceptions, it will block even these, no ?

```
4. You can not have your cake and eat it too.
```Darn !!!! ;-)

 ```
Either you allow connections or you do not.

Fron the clinet side, either you allow Firefox out onto the internet

Code:

iptables -A OUTPUT -p tcp --match multiport --dports 80,443 -j ACCEPT
```Not sure how that applies in my case. 
I'm running a server with no GUI, so I want to allow traffic in & out, just block all or most possible attempts to get a server intrusion.

Good day !

---

### Post by bodhi.zazen on 2010-11-29
> **djangobanana said:**
> ```
3. Rather then setting a default policy as DROP, I advise you make 
the last rule in your chain to drop all traffic

Code:

iptables -A INPUT -j DROP
```I don't understand. I want to allow certain traffic. If I put it at the end of my exceptions, it will block even these, no ?

No, traffic you wish to allow is accepted earlier in the chain.

Setting the policy to DROP is roughly the same as making the last rule in a chain to drop all traffic.

One difference is that iptables -F does NOT affect the default policy, thus you can lock yourself out easily with a default policy of DROP.

> iptables -A OUTPUT -p tcp --match multiport --dports 80,443 -j ACCEPT[/CODE]Not sure how that applies in my case. 
I'm running a server with no GUI, so I want to allow traffic in & out, just block all or most possible attempts to get a server intrusion.

Good day !

iptables is one part of security, so the answer to your question is that it depends. What servers are you running ? are they public or private ? What "possible attempts" are we talking about ?

Private servers = deny all , allow a white list.
Public servers = accept all, block a black list.

NIDS = snort (IMHO)
HIDS = OSSEC (or similar)
psad would be an alternate.

---

### Post by The Cog on 2010-12-01
Don't forget allowing RELATED,ESTABLISHED connections. Here's an example why: 

Imagine you want to keep your server mainly private, so you default block all packets:
> iptables -P INPUT DROP 
iptables -P FORWARD DROP 
iptables -P OUTPUT DROP  
But you want to allow the computer to make outgoing HTTP connections, perhaps to get software updates:
> iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
That lets the connect requests out, but the connection acceptance is not allowed back in. Somehow we also need to allow the connection reverse direction traffic too. Now wou could perhaps do:
> iptables -A INPUT -p tcp --sport 80 -j ACCEPT which allows any packets in that come from port 80 in the belief that this is a web server reply. But it's too open - it allows packets in from web servers that we haven't tried to speak to, and it allows packets from any client that happens to be calling from port 80 to any service on our server at all, e.g. hacker:80->server:22. This isn't right. So instead, ask iptables to keep track of the connections it has allowed to get started, and to also then allow responses on those connections:
> iptables -A INPUT --state RELATED,ESTABLISHED -j ACCEPT
This will allow incoming packets that are in response to an outgoing connection that iptables chose to allow.

Also, you should always allow input from interface lo, to allow inter-process communications. Without this, thigs like the CUPS print spooler cannot be used, even locally:> iptables -A INPUT -i lo -j ACCEPT

---

