---
title: "Blocking an unwelcome usage"
date: 2007-10-13
forum: Server Platforms
---

### Post by p_quarles on 2007-10-13
First: apologies for the vague subject line. I don't know exactly what this jerk is trying to do, so I can't be more specific.

Anyway, here's the deal. Over the past three weeks I've been getting between 6 and 12 hits a day from what I suspect is the same source. Apache logs them like so:
```
xx.xx.xx.xx - - [13/Oct/2007:20:51:04 -0500] "GET /index.php?tabindex=http://*other-url* HTTP/1.1" 200 1064 "-" "Wget/1.1 (compatible; i486; Linux; RedHat7.3)"
```
The remote IP address is usually different each time, but the the other details (wget, 486, Red Hat 7.3) are always the same. I'm assuming this is one person using proxies. 

The remote URL (the one after the equal sign) has so far been several addresses on two distinct networks. I'm not posting them since I have no idea whether those networks themselves are doing anything wrong. 

I'm relucant to call this an "attack," since it doesn't cause any problems in terms of bandwidth, CPU time or performance. What worries me is that every single hit has returned a 200 code in Apache's logs. Whatever it is, I'd like to be able to stop it.

First: does anyone know what this person is doing? As I said, it hasn't caused any noticeable problems on the server, but it does seem incredibly fishy (and persistent). 

Second: how do I block it? I've tried what I know (using iptables to block the remote URLs on both the INPUT and OUTPUT chains, and adding the remote URLs to the host.deny file). That has not had any effect. 

Thanks in advance for any input.

---

### Post by HermanAB on 2007-10-14
These kind of things are going on all the time.  There are worms/spambots that look for vulnerable Apache servers (Eg redone) and when found, they set up a spambot.

The way to prevent abuse is threefold:
a. Use proper passwords for ALL users (> 8 characters, randomized, or long pass phrases)
b. Do not allow scripts to execute inside the normal Web directories and enable taint checks in all Perl scripts.
c. Use iptables rate limiting on new connections to prevent brute force attacks.

Then sit back, relax and enjoy the nice weekend.

Cheers,

Herman

---

### Post by p_quarles on 2007-10-14
Yeah, I'm aware of all that. ;) 

The specific issue here is that this seems to be one person/machine that keeps coming back, and I am apparently unable to block it.

---

### Post by MJN on 2007-10-14
I wouldn't worry about it - as HermanAB says this is quite typical of botnet behaviour and something which you'll see all the time. If the IP changes then blocking on that basis is futile, you can't block on the user-agent given you'll be blocking genuine visitors and so all that's left is the URL - if you don't have the vulnerability that your 'attacker' is looking for (open proxy by the looks of it) then you need not worry (I suppose you could put a blackhole redirect in but you'll be forever chasing your tail with this one as there's a whole load of different URLs that such bots will be looking for).

Mathew

---

### Post by p_quarles on 2007-10-14
Yeah, I know that it's very common. It just seems particularly persistent, and it seems to be one machine (I mean, how many 486/Red Hat/wget boxes could possibly stumble across my little server?)

You're both saying I should be safe, which I'm inclined to agree with. My worry, though (and this is why this problem stood out from the normal pattern of exploit scanners) is that Apache keeps returning a 200 code to these requests. Is that grounds for concern? Is that just saying the primary page (my web site) was found? Or could it mean that there's a vulnerability that exists on my server that I don't know about? 

The blackhole redirect -- would I do this with iptables or with an .htaccess rule? I know it's not practical for every script/bot, but it sounds like something I should know about.

---

### Post by MJN on 2007-10-14
I thought you said it was multiple source IPs? In which case, it's not one machine but many.

The 200 code is simply the response to the index.php request. The parameters passed by the client after the ? are intended for the PHP script to parse so these do not effect the HTTP code.

The [redirect](http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirectmatch) would be done in .htaccess (or the Apache config) but I really don't recommend it.

Mathew

---

### Post by p_quarles on 2007-10-14
> **MJN said:**
> I thought you said it was multiple source IPs? In which case, it's not one machine but many.

The 200 code is simply the response to the index.php request. The parameters passed by the client after the ? are intended for the PHP script to parse so these do not effect the HTTP code.

The [redirect](http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirectmatch) would be done in .htaccess (or the Apache config) but I really don't recommend it.

Mathew
Multiple source IPs, yeah, but I'm assuming that's because this person is using some kind of anonymizer software or a proxy. The OS/agent details are too unusual for me to believe that this is a bunch of different people. 

Thanks for the explanation of the 200 code. That makes sense (and is comforting).

---

### Post by MJN on 2007-10-14
What's unusual about the user-agent? It is merely indicating the use of wget on a Red Hat box. Or is that theyare all the same? That could just be this bot's speciality!

Mathew

---

### Post by p_quarles on 2007-10-14
> **MJN said:**
> What's unusual about the user-agent? It is merely indicating the use of wget on a Red Hat box. Or is that theyare all the same? That could just be this bot's speciality!

Mathew
Yeah, about 200 hits over the past few weeks, all with the same details: Red Hat using wget on a 486. The source IP is the only thing that changes.

If it's multiple machines running the same bot, then I guess it would have to be providing false identification details, or it's a bot that specializes in infecting only really old computers running Linux :D  

Anyway, my assumption is that this is either 1) A single machine spoofing its IP address; or 2) multiple machines spoofing their IDs. Same difference from my perspective, as either way they are clearly all related to one another.

---

### Post by MJN on 2007-10-14
Of the two it's more likely to be the latter. Spoofing IP addresses, where a response is required (as opposed to a pure DOS attack which this isn't), is extremely difficult to the point of verging on being a practical impossibility.

Mathew

---

### Post by HermanAB on 2007-10-14
Well, if you want to have fun with annoying attackers and you have an old spare machine lying around, then you can configure an iptables mirror or tarpit and torture the attackers however long you please.

MIRROR
       This  is  an experimental demonstration target which inverts the source
       and destination fields in the IP header and retransmits the packet.  It
       is  only  valid  in the INPUT, FORWARD and PREROUTING chains, and user-
       defined chains which are only called from those chains.  Note that  the
       outgoing  packets  are NOT seen by any packet filtering chains, connec&#8208;
       tion tracking or NAT, to avoid loops and other problems.

   TARPIT
       Captures  and holds incoming TCP connections using no local per-connec&#8208;
       tion resources. Connections are accepted, but immediately  switched  to
       the persist state (0 byte window), in which the remote side stops send&#8208;
       ing data and asks to continue every 60-240 seconds.  Attempts to  close
       the  connection  are  ignored,  forcing the remote side to time out the
       connection in 12-24 minutes.

       This  offers  similar   functionality   to   LaBrea   <[http://www.hack&#8208;](http://www.hack&#8208;)
       busters.net/LaBrea/> but doesn't require dedicated hardware or IPs. Any
       TCP port that you would normally DROP or REJECT can  instead  become  a
       tarpit.

       To tarpit connections to TCP port 80 destined for the current machine:

              iptables -A INPUT -p tcp -m tcp --dport 80 -j TARPIT

       To significantly slow down Code Red/Nimda-style scans of unused address
       space, forward unused ip addresses to a  Linux  box  not  acting  as  a
       router (e.g. "ip route 10.0.0.0 255.0.0.0 ip.of.linux.box" on a Cisco),
       enable IP forwarding on the Linux box, and add:

              iptables -A FORWARD -p tcp -j TARPIT

              iptables -A FORWARD -j DROP

Cheers,

H.

---

### Post by p_quarles on 2007-10-14
Cool. Thanks for the tips.

Tarpit rocks, but I'm not sure if I can configure it to stop the bots without stopping all the legit traffic as well. I mean, I could try something like this:
```
iptables -I INPUT 1 -d *my_url*=*other_url *--dport 80 -j TARPIT
```
But I'm guessing that either wouldn't do anything or would block all traffic to my site. I'm an iptables rookie, though, so if there *is* a way to block specific requests like this, I'd love to know. 

I guess this string of hits isn't really a problem as long as my php parser is working correctly. At least, that's what you've both been telling me. Given that there are no performance/bandwidth problems, nothing picked up by Snort, and I've blocked the requested network, I should be able to relax. :)

---

### Post by HermanAB on 2007-10-14
I run sshd on a high port and tarpit ports 21, 22 and 23.  That keeps the script kiddies busy and is enough revenge for me...

---

### Post by p_quarles on 2007-10-14
> **HermanAB said:**
> I run sshd on a high port and tarpit ports 21, 22 and 23.  That keeps the script kiddies busy and is enough revenge for me...
lol . . . Good idea. I already use a high port for ssh, and block everything except that and 80 in the INPUT policy. Changing those ports to a tarpit sounds like more fun though. :)

---

### Post by ruibernardo on 2007-10-14
I was just trying to use this TARPIT feature here but, after looking at it in the man and here, but it didn't work.

There is an iptables module:
```
root@gutsy:~# ls -l /lib/iptables/|grep TARPIT
-rw-r--r-- 1 root root  3132 2007-07-05 02:58 libipt_TARPIT.so

```But when I tried it:
```
root@gutsy:~# iptables -A INPUT -p tcp --dport 6667 -j TARPIT
iptables: No chain/target/match by that name

```

I've tried it with Feisty too, but no love either.

Can anybody confirm if the Ubuntu kernel is working with TARPIT? Does it need a patch and/or recompilation with some option enabled?

---

### Post by HermanAB on 2007-10-14
Interesting - it doesn't work for me on Ubuntu either.  The machine I am using tarpitting on is running RedHat and I recompiled OpenSSL on that one.  I thought all the new versions will have it.

---

### Post by p_quarles on 2007-10-14
Apparently tarpit does require a patched kernel, and very few distros ship with the capability: 
[http://www.governmentsecurity.org/archive/t1708.html](http://www.governmentsecurity.org/archive/t1708.html)

---

### Post by HermanAB on 2007-10-14
Here is a nice writeup with graphs showing why tarpitting is better than dropping:
[http://www.secureworks.com/research/threats/ddos/?threat=ddos](http://www.secureworks.com/research/threats/ddos/?threat=ddos)

The issue is that the module is not yet easy to compile with the kernel, so the the only distro that has it out of the box is Gentoo.  I went through the compile pain last year on a RedHat system and hoped that by now it will be working for everyone, but apparently not.

---

### Post by dmizer on 2007-10-14
> **p_quarles said:**
> Multiple source IPs, yeah, but I'm assuming that's because this person is using some kind of anonymizer software or a proxy. The OS/agent details are too unusual for me to believe that this is a bunch of different people. 

you're assuming that a bot/script-kiddie is correctly reporting agent details?

---

### Post by p_quarles on 2007-10-14
> **dmizer said:**
> you're assuming that a bot/script-kiddie is correctly reporting agent details?
Excuse me?


[B]> **p_quarles said:**
> Anyway, my assumption is that this is either 1) A single machine spoofing its IP address; or 2) multiple machines spoofing their IDs. Same difference from my perspective, as either way they are clearly all related to one another.
[/B]

---

### Post by ruibernardo on 2007-10-14
> **HermanAB said:**
> I went through the compile pain last year on a RedHat system and hoped that by now it will be working for everyone, but apparently not.

Definitely a kernel compilation is needed to use TARPIT target in Ubuntu. 

I've checked both kernel options for Feisty and Gutsy, and no TARPIT options were found, so I've googled for "patch-o-matic-ng tarpit" and found a page in [howtoforge.com about it]("http://www.howforge.com/how-to-install-patch-o-matic-in-ubuntu") (not tested). I'll leave it here if anybody wants to try it. It applies to Edgy, so beware about that.

TARPIT is interesting, to say the least.

---

### Post by dmizer on 2007-10-14
> **p_quarles said:**
> Excuse me?

[QUOTE=p_quarles;3531553]Anyway, my assumption is that this is either 1) A single machine spoofing its IP address; or 2) multiple machines spoofing their IDs. Same difference from my perspective, as either way they are clearly all related to one another.
[/QUOTE]


just because the id is spoofed the same doesn't mean it's the same person controlling the script.  it also doesn't mean it's the same script, as the spoof could be part of a tool kit.

---

### Post by p_quarles on 2007-10-14
> **dmizer said:**
> just because the id is spoofed the same doesn't mean it's the same person controlling the script.  it also doesn't mean it's the same script, as the spoof could be part of a tool kit.
So, are you trying to offer some kind of solution, or are you looking for a pissing contest? 

I've already gone over this several times: same identification info, 90% of the hits go to a specific network, 100% of the hits are looking for a specific filetype on both of the two networks involved. I'm not making any fanciful assumptions here.

---

### Post by dmizer on 2007-10-14
> **p_quarles said:**
> So, are you trying to offer some kind of solution, or are you looking for a pissing contest? 

I've already gone over this several times: same identification info, 90% of the hits go to a specific network, 100% of the hits are looking for a specific filetype on both of the two networks involved. I'm not making any fanciful assumptions here.

fair enough.  and no pissing contest, merely trying to suggest that there's not likely too much to worry about.

in any case:
1 - is the specific file type/vulnerability available/vulnerable on your system?
2 - scanned port(s) open?

if not, then you're just part of a default block that's regularly scanned by this kiddie, or by this script.  preventing it from happening would be impossible.  securing your system from the attack is easy.

---

### Post by p_quarles on 2007-10-14
> **dmizer said:**
> fair enough.  and no pissing contest, merely trying to suggest that there's not likely too much to worry about.
Sorry to get my hackles up, then. I guess I mistook the tone of your first message as being confrontational, when that's not what you had intended (which is an internet danger that predates viruses and bots by a few years :) )

And, yeah, you're right, there's not much to worry about here. My initial alarm came about because Apache was giving these requests a 200. As MJN and HermanAB pointed out, though, the script/bot is looking for a PHP vulnerability, so whatever Apache does with it isn't that important. 

Thanks for the input.

---

### Post by dmizer on 2007-10-14
> **p_quarles said:**
> Sorry to get my hackles up, then. I guess I mistook the tone of your first message as being confrontational, when that's not what you had intended (which is an internet danger that predates viruses and bots by a few years :) )

And, yeah, you're right, there's not much to worry about here. My initial alarm came about because Apache was giving these requests a 200. As MJN and HermanAB pointed out, though, the script/bot is looking for a PHP vulnerability, so whatever Apache does with it isn't that important. 

Thanks for the input.

it's no problem ... the bane of text communication.

in any case, if apache is reporting 200's to undesirable scans to unsecured services of any kind, i suggest you take a look at your error handling/reporting.  you may be getting scanned frequently because it is reporting a 200, which may look like a successful attack to an unsophisticated bot, or kiddie.

---

### Post by arclight on 2007-10-14
You might consider installing [modsecurity]("http://www.modsecurity.org/") for Apache and writing a simple rule to block the pattern 'index.html\?tabindex=http' or equivalent. I can't imagine a situation where a field named 'tabindex' would take anything but a postive integer; regardless, if the traffic is unwanted, just filter it with modsecurity and get on with life.

---

### Post by p_quarles on 2007-10-15
> **dmizer said:**
> in any case, if apache is reporting 200's to undesirable scans of any kind, i suggest you take a look at your error handling/reporting.  you may be getting scanned frequently because it is reporting a 200, which may look like a successful attack to an unsophisticated bot, or kiddie.
That's a good idea. It would definitely explain the frequency & similarity of these scans. All the other scans get an error code of some flavor, and don't seem to come back for more. I will look into that.

> **arclight said:**
> You might consider installing [modsecurity]("http://www.modsecurity.org/") for Apache and writing a simple rule to block the pattern 'index.html\?tabindex=http' or equivalent. I can't imagine a situation where a field named 'tabindex' would take anything but a postive integer; regardless, if the traffic is unwanted, just filter it with modsecurity and get on with life.
That sounds good. I was attempting (without luck) to do the same thing with iptables and hosts.deny, but doing it from within Apache makes more sense. And, you're correct: "index.php?tabindex=" takes a value between 0 and 4.

---

