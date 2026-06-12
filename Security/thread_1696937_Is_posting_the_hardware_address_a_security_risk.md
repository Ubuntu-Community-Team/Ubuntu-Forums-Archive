---
title: "Is posting the hardware address a security risk ?"
date: 2011-02-28
forum: Security
---

### Post by oygle on 2011-02-28
When posting results from ifconfig, it shows the hardware address of etho, etc.

Would you consider that to be a security risk ?

Oygle

---

### Post by An Sanct on 2011-02-28
MAC addresses can be spoofed really easily, so someone could hijack your MAC and do bad stuff.

The question is: How do YOU want to see that? :) If big brother is watching you and you shred every physical mail you receive, securely delete your deleted files and have a separate 8-16 mixed character password for every account you have online, then the answer would probably be yes...

IMHO, no ... rather rethink that password thing I said :)

---

### Post by oygle on 2011-02-28
Okay thanks. It's one of those 'yes/no' answers though, isn't it.  :confused:

I don't understand how anyone can gain access via the MAC though (not that I want to see 'how'), **IF** sufficient firewall protection is in place, and other security measures are taken (e.g. strong passwords, etc).

---

### Post by An Sanct on 2011-02-28
Nobody can gain access via MAC to your system, they can just spoof it. 

They can say, "My MAC is this: '*your mac*'", and in that way *pretend* they are you (on one level), but nobody actually does that, since it is not an accurate unique identifier :)

The only bad thing would be if you have MAC address filtering to allow/deny connections (lets say for your WIFI or something)

So if I would have to consider if it is a security risk, I would say "definitely no." or in percent, maybe 2-4%

---

### Post by Grenage on 2011-02-28
MAC locking is a terrible security measure, but it's still used in some areas of the industry.  Most people use it as an additional level of 'protection', and there's no real risk when giving it to others.

Hell, it's broadcast over the network all the time.

---

### Post by Boondoklife on 2011-02-28
> **oygle said:**
> Okay thanks. It's one of those 'yes/no' answers though, isn't it.  :confused:

I don't understand how anyone can gain access via the MAC though (not that I want to see 'how'), **IF** sufficient firewall protection is in place, and other security measures are taken (e.g. strong passwords, etc).
Just in-case the answers given do not do it for ya:

Having the MAC only does one thing for you as mentioned, it lets you spoof a known good MAC. The only way this would help a would be black-hatter is if the only protection enabled on your wireless network is MAC limiting. If you only limit connections by MAC, forgoing any encryption or passwords, then once they spoof your MAC they would be able to gain access to your network. Then again the same could be accomplished via a wired connection, keeping your hard-line ports secure or disabled when not used is a must.

From here it is a matter of server security as to what they can do. If you have default shares/accounts enabled on boxes inside your network then you can assume those will be compromised easily and first. Once they have that, then gaining further access is not that far fetched.

Unfortunately a firewall only helps to keep people out of your network, it is perfectly happy to do what ever someone already on the network wants to do.

In closing, I have never thought twice about posting data with my MAC in it. I have never had a problem with people access my network without my knowledge. As far as a simple yes/no answer; No, it is not a security issue (unless you use ONLY MAC filtering to secure your network.)

---

### Post by psusi on 2011-02-28
In a word, no.

Anyone trying to spoof your MAC address would have to have physical access to your LAN, in which case, they can find it out anyway.

---

### Post by doas777 on 2011-02-28
yes in that any piece of info about your network can be used against you if you are identified. 

no in that most people would not be in a position to hurt you with that info.

so it could conceivably be a risk, but for most it is not. hows that for a straight answer?

---

### Post by oygle on 2011-02-28
Okay, thanks everyone for your replies, much appreciated.  :)

I'm having trouble digesting all that info, but I should explain my setup. Only my wife and myself have physical access to the network (only 2 computers, one a gateway, one a client). I don't use MAC address (only) for stopping intrusions. I only have a wireless broadband (ppp0) connection, so no router where I can specify NAT or MAC addresses, etc.

So, all I have is GUFW/UFW (I have dropped Firestarter, but now no client connection, some sharing issue) on both computers. They are both set to default 'allow out' and 'deny in', so I feel that is protected enough.

It seems from the replies that a person needs physical access to the LAN, which no one (else) does, to spoof the MAC address.

One day I will get a router, to offer a bit more protection though.

Thanks muchly for your replies. :D

I know know that I don't need to worry about posting info from ifconfig', or posting MAC addresses anywhere.

Oygle

---

### Post by Boondoklife on 2011-02-28
> **oygle said:**
> It seems from the replies that a person needs physical access to the LAN, which no one (else) does, to spoof the MAC address.

Most certainly not true! It is possible to do this via wireless too.

> **Boondoklife said:**
> Having the MAC only does one thing for you as mentioned, it lets you  spoof a known good MAC. The only way this would help a would be  black-hatter is if the only protection enabled on your wireless network  is MAC limiting. If you only limit connections by MAC, forgoing any  encryption or passwords, then once they spoof your MAC they would be  able to gain access to your network. Then again the same could be  accomplished via a wired connection, keeping your hard-line ports secure  or disabled when not used is a must.

---

### Post by psusi on 2011-02-28
> **Boondoklife said:**
> Most certainly not true! It is possible to do this via wireless too.

Well yes, if they are within range of your wireless router and you don't password protect it, which of course, you do ;)

---

### Post by doas777 on 2011-02-28
mac spoofing also allows an attacker another tool once they have established a beachhead within your network. many varieties of local network attacks rely on the ability to make a host unreachable, and impersonate it. 

granted, if someone has a presence on your network for long enough, they will gather all your macs, but knowing that info upfront would aid them somewhat. 

but this is all pretty unlikely for a home network, as things currently stand.

---

### Post by Jive Turkey on 2011-03-01
If someone has the intention of attacking a computer, discovering that computer's MAC address is pretty trivial if I'm not mistaken.

---

### Post by oygle on 2011-03-01
Well, thanks for the replies. You people are security experts, I'm certainly not.

I will simply not post any info like that, even though it's just a home network, and we control who uses the computer.

Thanks,

Oygle

---

### Post by An Sanct on 2011-03-01
It will not harm to snip out the MAC if you have (or are asked) to post the output of ifconfig here, people here are interested in other data, that helps them troubleshoot the potential problem, like IP config, network status, ... other non harmful data.

---

### Post by oygle on 2011-03-01
Okay, thanks. :)

---

