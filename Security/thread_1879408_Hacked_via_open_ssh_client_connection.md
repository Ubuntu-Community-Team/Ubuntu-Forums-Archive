---
title: "Hacked via open ssh client connection ?"
date: 2011-11-11
forum: Security
---

### Post by jvictor on 2011-11-11
Hi Guys

I had a nginx webserver running on a ubuntu server 10.4 (running as a vm - bridged networking), which I think had a dictionary password. The host os was debian squeeze - minimal install, ssh port open.

I had a ssh connection from a mac,  open to monitor the logs.The vm and mac (osx lion) were on the same network. when I left in the morning, , In the afternoon when I came back, I see that the permissions on my Terminal.app have been set to deny execution, and other binary permissions also have been reset. So I had no other option but to format and re-install, I was concerned that they would've even replaced my other binaries.

The ssh connection had a prompt , you do not exist - go away. 

I'm bit concerned about this entire event and wonder if they have copied over data from my mac - it had some personal info in there.

Please advise.

---

### Post by OpSecShellshock on 2011-11-11
I would presume that the answer is yes. Change all passwords to everything, just in case. Don't allow password authentication for ssh access, instead use key-based authentication. If you had ssh open to the web and a dictionary word as your password, then yes, that's how it was done. Fully automated processes are scanning everything they can all the time looking for exactly that kind of setup.

OSX systems I think have a bunch of shared folders and things enabled by default, so they may have been open for the rifling. Might be best to check those settings and make sure though. If it were me I would rebuild all systems on the network.

---

### Post by jvictor on 2011-11-11
I have taken the webserver offline, and also rebuilt it after formatting / zeroing everything on the disk. It beats me how they could get control of my mac which has a kind of strong password.

---

### Post by Dangertux on 2011-11-11
> **OpSecShellshock said:**
> I would presume that the answer is yes. Change all passwords to everything, just in case. Don't allow password authentication for ssh access, instead use key-based authentication. If you had ssh open to the web and a dictionary word as your password, then yes, that's how it was done. Fully automated processes are scanning everything they can all the time looking for exactly that kind of setup.

OSX systems I think have a bunch of shared folders and things enabled by default, so they may have been open for the rifling. Might be best to check those settings and make sure though. If it were me I would rebuild all systems on the network.

Pretty much this. If you have "file sharing" enabled on your Mac OS X system the /public/ folder was accessible as well as anything else you may have shared separately.

In light of the post made before this one, it is not necessarily the case that your Mac was compromised, however what is of concern is the fact that Mac's tend to be very liberal with the data they freely distribute.

Hope this helps.

---

### Post by jvictor on 2011-11-11
There wasn't anything shared in the public dirs, but the fact that binary permissions got changed makes me uncomfortable. :(

---

### Post by Dangertux on 2011-11-11
That is a little odd to say the least, were you running any services on the Mac? Possibly evo cam's web server?

---

### Post by jvictor on 2011-11-11
Nope nothing that I have started off , not sure about the "default services" on OSX iTuneshelper etc..

---

### Post by HermanAB on 2011-11-13
Yup, there have been automated SSH and FTP attack scripts doing the rounds for many years, that can try tens of thousands of passwords per hour.  That is why you absolutely must use proper passwords for everything.

---

### Post by hakermania on 2011-11-13
Always remember that it is much better to use a password like
'black horse with red nails & filthy moustache' rather than
34@#$221AAa :P

---

### Post by Lars Noodén on 2011-11-13
> **HermanAB said:**
> Yup, there have been automated SSH and FTP attack scripts doing the rounds for many years, that can try tens of thousands of passwords per hour.  That is why you absolutely must use proper passwords for everything.

It also helps to use IP Tables to limit the rate of new connections.  

```

iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set
iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j REJECT
```

The actual values will vary depending on the real usage of the server.

---

### Post by HermanAB on 2011-11-13
Actually, a limit filter is a one liner nowadays:
```
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

---

### Post by jramshu on 2011-11-13
> **OpSecShellshock said:**
> Don't allow password authentication for ssh access, instead use key-based authentication. If you had ssh open to the web and a dictionary word as your password, then yes, that's how it was done. Fully automated processes are scanning everything they can all the time looking for exactly that kind of setup.


Glad I went back and re-read, I was just fixin to say the same.

---

### Post by mastablasta on 2011-11-13
> **hakermania said:**
> Always remember that it is much better to use a password like
'black horse with red nails & filthy moustache' rather than
34@#$221AAa :P

i've read about this before (xkcd) but how is this not a disctionary password? all words can be found in dictionary.

---

### Post by Dangertux on 2011-11-13
> **HermanAB said:**
> Actually, a limit filter is a one liner nowadays:
```
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

The original example is effective this one to an extent as well. However this rule would be more effective in the case of a webserver where it would require multiple connections per IP address. 

If you wanted the "best" possible rule for iptables rate limiting to SSH I would probably think it would be along the lines of something like this due to the nature of ssh's connection process.

```

iptables -A INPUT -p tcp --dport 22 -m hash-limit --hashlimit-name st_limit --hashlimit-mode srcip --hashlimit-above 4/sec --hashlimit-burst 4 -j DROP

```This will use the hash token method as opposed to the bucket token method. To be honest they are each effective though some are slightly tailored for different applications, and purposes. 

Note : this requires the xtables addon.

which is installed but wonky...you can utilize it by running

```

sudo ln -s /lib/xtables/libxt_hashlimit.so /lib/xtables/libipt_hash-limit.so

```

Or just install fail2ban or denyhosts :-P

Hope this helps.

---

### Post by jramshu on 2011-11-13
Good addition sir. You should really should start a server wiki.

Be thankful DT is a good guy and has no problem helping.

EDIT: In addition to DT's blog, everyone should read bodhi.zazen's tutorials and blog on securing servers, ssh, etc..

Will provide link if needed.

---

### Post by Dangertux on 2011-11-13
Umm thanks :-) 

It was just a different way of doing things though, it's really not even necessary :-)

---

### Post by jramshu on 2011-11-13
Haha. Just saying you know and help a lot.

I use denyhosts and it has pretty much stopped the abuse. Gave it a touchy trigger finger. lol

Disable PasswordAuth and use keys and denyhosts, that will help a lot. 

There are some clever mothods to help with DoSing too. Turning it back on the attacker. Kinda funny knowing they are DoSing themselves. hahaha

---

