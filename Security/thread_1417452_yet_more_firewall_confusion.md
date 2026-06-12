---
title: "yet more firewall confusion"
date: 2010-02-27
forum: Security
---

### Post by Bear number one on 2010-02-27
Could another forum user please verify if I am correct in thinking the following:

If ufw is set to *ufw enable* it allows connections both to and from the internet.

If ufw is set to *default deny* then it allows connections from a users computer to the internet but blocks all incoming traffic.

---

### Post by OpSecShellshock on 2010-02-27
I don't believe that to be the case. Just took a look at it via the gufw interface, and my guess is that "enable" allows ufw to act on/influence iptables in the first place, and setting the default to "deny" will block any incoming connection that is not a response to an outgoing initiation from the firewall host. Setting the default to "allow" would, I expect, allow everything. Generally the ufw/gufw application is written so that you really don't have to mess with it.

---

### Post by Enigmapond on 2010-02-27
> **OpSecShellshock said:**
> I don't believe that to be the case. Just took a look at it via the gufw interface, and my guess is that "enable" allows ufw to act on/influence iptables in the first place, and setting the default to "deny" will block any incoming connection that is not a response to an outgoing initiation from the firewall host. Setting the default to "allow" would, I expect, allow everything. Generally the ufw/gufw application is written so that you really don't have to mess with it.

I second this. As long as it's enabled you are good and the only time you really need to adjust it is to set certain rules if you need...but more often you won't. "Allow" and "Deny" are for the rules...not the firewall on/off...if that makes any sense at all...:D

---

### Post by Bear number one on 2010-02-27
So just activating the firewall by ufw enable should be enough to secure my computer?

I have looked around the forums and the how to's and I'm wondering if those of us new to linux security are making it all rather more complicated than it actually is in regards to firewalling.

There's a lot of info about adding rules etc but without the very basics it gets confusing.
Using a firewall such as norton in windows is generally an install, activate and forget about it experience.

Is ufw much the same thing that only needs to get complicated  should you wish to delve a little deeper?

---

### Post by Enigmapond on 2010-02-27
For the average user, just enabling the ufw if safe enough. It gets complicated when you are running a server, FTP or something...It will deny ALL incoming unless it's a response to your outgoing. Plus if you are behind a router, that has a firewall as well...so relax..the "out of the box" ufw is a really good firewall.:D

Cheer!

---

### Post by FuturePilot on 2010-02-27
Are you running any servers on your machine? Ex: SSH, Apache, etc. If you're not then there is little need to have a firewall. If nothing is listening for connections, then there is nothing to firewall.

---

### Post by Enigmapond on 2010-02-27
> **FuturePilot said:**
> Are you running any servers on your machine? Ex: SSH, Apache, etc. If you're not then there is little need to have a firewall. If nothing is listening for connections, then there is nothing to firewall.

Well I wouldn't go as far as that...there is network traffic and various pinging, ICMP traffic and if someone is malicious, they can see in...so better to just enable it and deny all that rot.

---

### Post by Bear number one on 2010-02-27
No servers, just me and my pc.

I think this is referred to as the 'windows mindset' by the replies I'm getting, i:e, paranoid computer user raised on windows............

On a serious note, and looking at some past queries regarding ufw, I do think that windows refugees are in danger of been put off linux by misunderstanding and over-complicating certain security issues (will someone stop that ostrich from staring at me) 

Maybe ufw should be given its full title at all times [COLOR=Red]'uncomplicated firewall'[/COLOR].

Thanks for all replies.

---

### Post by Enigmapond on 2010-02-27
> **Bear number one said:**
> 
 (will someone stop that ostrich from staring at me) 


:lolflag: He's wondering why you're staring at HIM...LOL

Cheers!!:D

You should mark the thread as solved in the thread tools..;)

---

### Post by Bear number one on 2010-02-27
Thanks for all the help from all that have replied. I've just found the thread tools button and will now mark as solved.

All smile at the ostrich..............;)

---

