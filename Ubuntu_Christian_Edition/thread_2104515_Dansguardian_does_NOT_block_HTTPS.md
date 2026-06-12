---
title: "Dansguardian does NOT block HTTPS"
date: 2013-01-13
forum: Ubuntu Christian Edition
---

### Post by axy_david on 2013-01-13
So I found out why google isn't filtered, because it seems that dansguardian does not filter https websites, I tried the same thing on http and it blocked.
how do I apply filters to https aswell?

This is a possible fix:
```
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 443 -j REDIRECT --to-port 80
```

---

### Post by swiftthinker on 2013-01-13
I had the same problem. I found that you can block HTTPS in the /etc/dansguardian/list/exceptionsitelist and then the web sites that use HTTPS that you want to view put in the top of this file. So, you won't be able to use google. If you find another way please let me know.

Thanks

Swiftthinker

---

### Post by axy_david on 2013-01-13
can you give me the example, I'm not quite sure what you mean, I am thinking about forwarding https to http in privoxy (if that's possible)
the iptable trick didn't work for me.

---

### Post by nixblog on 2013-01-13
> **axy_david said:**
> So I found out why google isn't filtered, because it seems that dansguardian does not filter https websites...

Maybe this is the reason (source: Squid Proxy docs),

> HTTPS was designed to give users an expectation of privacy and security.  Decrypting HTTPS tunnels without user consent or knowledge may violate  ethical norms and may be illegal in your jurisdiction. Squid decryption  features described here and elsewhere are designed for deployment with *user consent*  or, at the very least, in environments where decryption without consent  is legal. These features also illustrate why users should be careful  with trusting HTTPS connections and why the weakest link in the chain of  HTTPS protections is rather fragile. Decrypting HTTPS tunnels  constitutes a man-in-the-middle attack from the overall network security  point of view. Attack tools are an equivalent of an atomic bomb in real  world: Make sure you understand what you are doing and that your  decision makers have enough information to make wise choices. 

---

### Post by swiftthinker on 2013-01-13
Ok, I just checked again, and no it does not work. So, I went to mozilla adons manager and installed the blocksite adon and put the sites that have HTTPS like google, duckduckgo, and ninjacloak. This seems to work. Let me know if you find something better.

---

### Post by axy_david on 2013-01-21
[http://wiki.squid-cache.org/Features/SslBump]("https://www.proxyssl.org/permalink.php?url=bvrNlWemj2YO3h7Unlb63dFCCFL6OHR4YpueoCLtw%2BzJ5Ezr3Kmt1Z0nY0ZKUTYQJS%2BIAH%2B%2BP%2FUCCcM3Y6iNjA%3D%3D")

Interesting article about a possibility of blocking SSL in squid.
I don't understand anything, can anyone explain?
Also do I need to rewrite all the http config in order to work in https?
If yes then can I block all traffic trough https with squid?

---

### Post by axy_david on 2013-01-21
```
firefox -p
```
the addons are pretty useless as the end user can easy bypass it

---

### Post by axy_david on 2013-01-25
FINALLY!!!!
I nailed it!!!!      [COLOR=Red] DO A BACKUP OF before.rules!!!!!![/COLOR]
Type in Terminal:
```
cd '/etc/ufw'
sudo gedit before.rules
```It will open up a text editor
Under 
:OUTPUT ACCEPT [0:0] (It's almost at the bottom of the text file)

Paste
-A OUTPUT -p tcp --dport https -j DROP
-A OUTPUT -p tcp -m tcp --dport https -j DROP
-A OUTPUT -p tcp -m tcp --dport 443 -j DROP
(I just tested all possibilities with https since I don't think it will do any harm it it's the same thing 3x)

Restart firewall service or the PC and voila! *[https://google.com](https://google.com)* won't load anymore!
WARNING!!! THIS WILL BLOCK ALL SSL CONNECTIONS!

P.S. If you wanna block all https except [COLOR=#000000]192.168[/COLOR][COLOR=#000000].1[/COLOR][COLOR=#000000].0[/COLOR]/[COLOR=#000000]24 then you type the following:[/COLOR]
-A RH-Firewall[COLOR=#000000]-1[/COLOR]-INPUT -s [COLOR=#000000]192.168[/COLOR][COLOR=#000000].1[/COLOR][COLOR=#000000].0[/COLOR]/[COLOR=#000000]24[/COLOR] -m state --state NEW -p tcp --dport [COLOR=#000000]443[/COLOR] -j ACCEPT
I didn't tested it and I think it's wrong but you can try :P

---

### Post by axy_david on 2013-01-25
The next thing we have to do is to figure out how to unblock youtube thumbails, and make it possible to comment on videos ;)
Don't forget that you can still access SSL as root.
Good to know if you want to upload something that only works via SSL(I suspect youtube force SSL uploading)
Here are Youtubes IP adresses if you wanna add exceptions:

[LIST]
[*] 208.65.153.238
[*] 208.65.153.251
[*] 208.65.153.253
[*] 208.117.236.69
EDIT: The content loads after around 30 seconds, maybe** REJECT instead of DROP?**
[*]EDIT2: Nope....seems the symptoms ar present on other websites as well.
[/LIST]

---

### Post by axy_david on 2013-01-27
yes, I forgot to do a backup of the before.rules file, can someone please upload it?

---

