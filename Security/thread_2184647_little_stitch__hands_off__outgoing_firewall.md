---
title: "little stitch // hands off // outgoing firewall"
date: 2013-10-30
forum: Security
---

### Post by MikeCyber on 2013-10-30
Installed yesterday osx86 Mavericks and found hands off to be cool for blocking outgoing 
traffic (apple etc.)
Since on 13.10 I had a huge boot delay I wonder if that could have been a keylogger etc. 
and hence I'll try soon on 13.04:
[URL="http://sourceforge.net/projects/leopardflower/"]
http://sourceforge.net/projects/leopardflower/[/URL]

Anyone tried it? Works fine for all connections on 13.04?

---

### Post by 3rdalbum on 2013-11-02
> **MikeCyber said:**
> 
Since on 13.10 I had a huge boot delay I wonder if that could have been a keylogger etc.

Please, please, please don't say that.

"Something slightly different happened on my computer, therefore OMG I've got viruses!" - is paranoia.

Firstly, this isn't Windows, there are no keyloggers that can just worm their own way into your computer. Secondly, there's nothing about a keylogger that would cause a delay in startup. Thirdly, any programmer smart enough to create a self-replicating keylogger would also be smart enough to have it start itself concurrently - thus causing no delay to bootup and no sign that it's running. Fourthly, a long bootup sequence is usually caused by one of a dozen different normal factors like "Everything is waiting for the network to be up before they can continue" or "The X configuration file is wrong, so X has to probe the hardware several times to figure out what's actually connected".

> [URL="http://sourceforge.net/projects/leopardflower/"]
http://sourceforge.net/projects/leopardflower/[/URL]

Anyone tried it? Works fine for all connections on 13.04?

Last updated one year ago; it's probably been abandoned.

If you don't have a keylogger - and trust me, you don't - then you also don't need an outgoing firewall. That's a bit controversial from what I can gather, usually when I say that I get some people agreeing with me and some people telling me it's bad advice. So if you want to try that software, go ahead. But nothing that you've told me in this post suggests to me that you've got a keylogger.

---

### Post by cariboo on 2013-11-02
Iptables/netfilter only block by port, or user. There is no way to block an applications access to the internet, as they all use random ports when creating a connection. To check what ports are in use with established connections you can use the following command:

```
sudo lsof -i -P -n
```

The following is and example of what the output should look like:

```
chromium- 4750 cariboo  166u  IPv4 444552      0t0  TCP 192.168.0.104:38883->130.57.66.5:80 (ESTABLISHED)
chromium- 4750 cariboo  185u  IPv4 444352      0t0  TCP 192.168.0.104:42585->173.194.33.76:443 (ESTABLISHED)
chromium- 4750 cariboo  186u  IPv4 444330      0t0  TCP 192.168.0.104:60612->74.125.28.84:443 (ESTABLISHED)
chromium- 4750 cariboo  196u  IPv4 442786      0t0  TCP 192.168.0.104:59619->173.194.33.72:80 (ESTABLISHED)
```

To explain what you are seeing, chromium has four connection established:

[LIST]
[*]Command = chromium
[*]PID (program ID) = 4750
[*]User = cariboo
[*]Fd (file descriptor) = 166u
[*]Type = IPv4
[*]Device = 444552
[*]Size/Offset = 0t0
[*]Node = TCP
[*]Name = 192.168.0.104:38883->130.57.66.5:80 (ESTABLISHED)
[/LIST]

The name section has the connection information in this example:

[LIST]
[*]192.168,0.104 = my computer ip address
[*]38883 = the out going connection
[*]130.57.66.5 = the ip address of the system I'm connected to
[*]80 = the port I'm connected to on the remote system
[/LIST]

The other 3 connections show that the outgoing port is different from the first line that I used as an example. You can also see the 2 of the connections are to port 443 or https and the last connection is to port 80 again.

So you can see that chromium is using 4 different out going ports, and just filtering the application, would be pretty hard to do, as there is no set port needed to establish a connection.

---

### Post by MikeCyber on 2013-11-03
Just tried leopardflower and it's exactly what I was looking for. I needed to allow firefox etc. and have blocked a geo position request to canonical. A little more complicated to 
compile as on osx but works fine and was last updated in 2012.
I've never cared about keylogger etc. since 1998 but as I saw such in mavericks and after the nvidia repos bug in 13.10, which even forced my back to 13.04, I think to use it 
from now on. What I wanted to says is that the delay, probably the nvidia repos as always, could be anything. If such bugs appear they could have also easily overlooked some troians or whatever. 
Not sure if I also need to look into a firewall. I only want to keep my passwords secret!-

---

