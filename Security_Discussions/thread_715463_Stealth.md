---
title: "Stealth"
date: 2008-03-04
forum: Security Discussions
---

### Post by Feivel on 2008-03-04
Man...windows takes a bit of playing with to get stealth on ShieldsUp at grc.com. Ubuntu 8.04 out of the box gets stealth. Bye-bye microsoft :)

---

### Post by ung/xunil on 2008-03-05
Hi Feivel,

just want to say that I find it somewhat strange what you are reporting. I'm not saying it's wrong (I'm using Gutsy ATM, with shorewall), but I've been watching the evolution of this webpage: [https://wiki.ubuntu.com/UbuntuFirewall]("https://wiki.ubuntu.com/UbuntuFirewall")

One thing it says it's:

> Release Note

**The tool will not affect users in the default installation as the tool will initially be disabled on installation (ie default ACCEPT policy).** 

So now I'm confused. Is this new firewall tool working "out-of-the-box", or you must activate it first?

---

### Post by Feivel on 2008-03-05
> **ung/xunil said:**
> Hi Feivel,

just want to say that I find it somewhat strange what you are reporting. I'm not saying it's wrong (I'm using Gutsy ATM, with shorewall), but I've been watching the evolution of this webpage: [https://wiki.ubuntu.com/UbuntuFirewall]("https://wiki.ubuntu.com/UbuntuFirewall")

One thing it says it's:



So now I'm confused. Is this new firewall tool working "out-of-the-box", or you must activate it first?

Don't think it's enabled. Hardy Heron just seems to be much more secure than windows.

---

### Post by Oldsoldier2003 on 2008-03-05
> **ung/xunil said:**
> Hi Feivel,

just want to say that I find it somewhat strange what you are reporting. I'm not saying it's wrong (I'm using Gutsy ATM, with shorewall), but I've been watching the evolution of this webpage: [https://wiki.ubuntu.com/UbuntuFirewall]("https://wiki.ubuntu.com/UbuntuFirewall")

One thing it says it's:



So now I'm confused. Is this new firewall tool working "out-of-the-box", or you must activate it first?
iptables are setup "out of the box" to lockdown your desktop.

---

### Post by ung/xunil on 2008-03-05
I know iptables is setup as ACCEPT by default. That's why I'm confused. 

A fresh ubuntu install, until now, with iptables set to ACCEPT by default in all 3 chains. When you test a fresh Ubuntu on grc.com you got (until now at least) all ports CLOSED, not stealth. To have sealth in grc.com you have to set iptables chains to DROP, so no responses is given, not even port closed.

> **Feivel said:**
> windows takes a bit of playing with to get stealth on ShieldsUp at grc.com. **Ubuntu 8.04 out of the box gets stealth**. Bye-bye microsoft :)

So my real question is: in Hardy really stealth out-of-the-box on grc.com?

Thanks.

---

### Post by Oldsoldier2003 on 2008-03-05
> **ung/xunil said:**
> I know iptables is setup as ACCEPT by default. That's why I'm confused. 

A fresh ubuntu install, until now, with iptables set to ACCEPT by default in all 3 chains. When you test a fresh Ubuntu on grc.com you got (until now at least) all ports CLOSED, not stealth. To have sealth in grc.com you have to set iptables chains to DROP, so no responses is given, not even port closed.



So my real question is: in Hardy really stealth out-of-the-box on grc.com?

Thanks.
well grc.com actually talks to your dsl gateway if you are a dsl user... the results would only be vaild for ports you have forwarded to your computer.

---

### Post by Feivel on 2008-03-05
> **ung/xunil said:**
> I know iptables is setup as ACCEPT by default. That's why I'm confused. 

A fresh ubuntu install, until now, with iptables set to ACCEPT by default in all 3 chains. When you test a fresh Ubuntu on grc.com you got (until now at least) all ports CLOSED, not stealth. To have sealth in grc.com you have to set iptables chains to DROP, so no responses is given, not even port closed.



So my real question is: in Hardy really stealth out-of-the-box on grc.com?

Thanks.
Considering I am running Hardy Heron with no mods to the IP tables and am stealh, I would say **YES**.

---

### Post by ung/xunil on 2008-03-05
If it is a Yes, I find it very strange, it should be CLOSED, not stealth (unless you have some router/modem with firewal in the way), and that wiki.ubuntu webpage  says that the new ubuntu firewall isn't enabled by default.

Can someone confirm or clarify this, please?

---

### Post by Feivel on 2008-03-05
> **ung/xunil said:**
> If it is a Yes, I find it very strange, it should be CLOSED, not stealth (unless you have some router/modem with firewal in the way), and that wiki.ubuntu webpage  says that the new ubuntu firewall isn't enabled by default.

Can someone confirm or clarify this, please?

Why dont you install Hardy Heron with Wubi (so you can delete it) and then go to grc.com and run check to see. Take my word for it. I tried the same thing in Windows and even with a router I wasn't stealth.

---

### Post by The Cog on 2008-03-05
> **Oldsoldier2003 said:**
> iptables are setup "out of the box" to lockdown your desktop.

I don't think I believe this. Although I don't have a Hardy install to hand, iptables has never been configured to block anything in the default install in any previous version of Ubuntu, and neither does the Hardy alpha 5 live CD. I have seen no suggestion of a change in policy for Hardy other than the wiki page linked above whcih says the new firewall will also default to not blocking anything.

The reason grc says there are no ports open is that there are no TCP ports open (no listening services running), **not** because iptables is blocking things.

Please (if you have not configured the firewall yourself yet), run this command:
**sudo iptables -nvL**
and see what iptables rules are in effect in a default install. If you find that iptables is blocking by default, please post the output here.

---

### Post by Oldsoldier2003 on 2008-03-05
> **The Cog said:**
> I don't think I believe this. Although I don't have a Hardy install to hand, iptables has never been configured to block anything in the default install in any previous version of Ubuntu, and neither does the Hardy alpha 5 live CD. I have seen no suggestion of a change in policy for Hardy other than the wiki page linked above whcih says the new firewall will also default to not blocking anything.

The reason grc says there are no ports open is that there are no TCP ports open (no listening services running), **not** because iptables is blocking things.

Please (if you have not configured the firewall yourself yet), run this command:
**sudo iptables -nvL**
and see what iptables rules are in effect in a default install. If you find that iptables is blocking by default, please post the output here.

actually you are right its not iptables- its Ubuntu itself

> By default, Ubuntu includes a firewall, iptables, but by default nothing is engaged. This is reasonable as a default Ubuntu install opens zero ports to the outside world, so a firewall is redundant. [http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)

---

### Post by ung/xunil on 2008-03-06
> **Feivel said:**
> Why dont you install Hardy Heron with Wubi (so you can delete it) and then go to grc.com and run check to see. Take my word for it. I tried the same thing in Windows and even with a router I wasn't stealth.

I use Ubuntu full time for 2 years now, as posted previously, now I'm with Gutsy and shorewall. Ubuntu has always (since its start, or a least since 5.10 Breezy when I first tried it) came with no services listening (no ports open) and no firewall/iptables configuration:
```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

``` 
That means that when you go to grc.com and test your connection with a fresh Ubuntu install, grc.com would "fail" because all ports scanned where reported as CLOSED. 

This is because each port would refuse the connection saying that the port is CLOSED. Iptables is not set, so it ACCEPT the incoming connection. There is no application listening in any port, so the connection is dealt by the kernel itself, and the kernel sends packets saying to the other computer (grc.com in this case) that the port is closed. From [grc.com own words]("http://www.grc.com/faq-shieldsup.htm#STEALTH"):
> Q: ShieldsUP! shows my ports as 'Closed' and not 'Stealth', but I want Stealth! How do I get 'Stealth'?

A: 'Stealthed' ports are a, strictly speaking, a violation of proper TCP/IP rules of conduct. Proper conduct requires a closed port to respond with a message indicating that the open request was received, but has been denied.

'Stealthed' ports are a, strictly speaking, a violation of proper TCP/IP rules of conduct. Proper conduct requires a closed port to respond with a message indicating that the open request was received, but has been denied [...]

There is no danger in this, since there is no service/application/program listening in any port. You can ping a fresh Ubuntu install, you can scan all its ports, but you can't get a connection with it because nothing is listening to for calls.

From the grc.com developer own words:
> 
I coined the term 'Stealth' when I developed this site's port probing technology to describe a closed port that chooses to remain completely hidden by sending nothing back to its attempted opener, preferring instead to appear not to exist at all.

To have this stealth behaviour iptables policies must be set to DROP, so no responses are made, not even reporting the port as closed. The new ufw firewall will be a way to deal with iptables to do this.

Now the [ufw wiki page]("https://wiki.ubuntu.com/UbuntuFirewall") says 
> The tool will not affect users in the default installation as the tool will initially be disabled on installation (ie default ACCEPT policy).
and the OP is saying that Ubuntu is reported as stealth in grc.com.

Forgive me for being such a pain, and sorry if I'm wrong, but something is not right here.

---

### Post by Feivel on 2008-03-06
> **ung/xunil said:**
> I use Ubuntu full time for 2 years now, as posted previously, now I'm with Gutsy and shorewall....
Forgive me for being such a pain, and sorry if I'm wrong, but something is not right here.

As I said, try installing Hardy Heron (version 8.04) and you will see. Either way, i have not installed a firewall nor do i have any router with a firewall. Essentially, you are telling me i am lying well try Hardy Heron and see for yourself otherwise STOP calling me a liar.

---

### Post by ung/xunil on 2008-03-06
Feivel, please... I've not called you nothing. Don't take this personally, please.

I'm saying that things:
- Ubuntu always had ACCEPT in iptables;
- Ubuntu hadn't any service listening;
- Ubuntu used to report all ports closed on grc.com.
- The ufw webpage says that the new firewall souldn't be enabled by default to change this behaviour;
- You are reporting it is.
- I think it's a great change and I don't see it in any docs. I'm in doubt, not calling you anything - sorry if I offended you in some way, never mean to.

I'll try to install Hardy in qemu later today and will confirm this personally, since nobody else is doing it - a simple "sudo iptables -L" on the liveCD would do it, I think.

Cya in some hours, after I try it.

---

### Post by Feivel on 2008-03-06
> **ung/xunil said:**
> 
- The ufw webpage says that the new firewall souldn't be enabled by default to change this behaviour;
- You are reporting it is.

No I am not. Reread the thread. I never said squat about iptables, I said stealth and you ASSUME I mean ufw.

---

### Post by ung/xunil on 2008-03-06
Yes I did assume. I justify this because ufw is planned for Hardy and is the only thing that could be installed by default, since it is planned to be available for Hardy - but not installed by default to my knowledge and from the docs I've read - but that can have changed. The ufw page does say:
> The tool will not affect users in the default installation as the tool will **initially** be disabled on installation (ie default ACCEPT policy).
So, ufw could be installed by default now, but the page was not updated.

If it isn't ufw, then Hardy should have the same reports  from grc.com as the other releases until now: all ports closed - if you are directly connected to the Internet.

Downloading [daily Desktop Hardy cd build]("http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-i386.iso") to test it.

Hope to have some answers for this soon.

---

### Post by Feivel on 2008-03-06
> **ung/xunil said:**
> Yes I did assume. I justify this because ufw is planned for Hardy and is the only thing that could be installed by default, since it is planned to be available for Hardy - but not installed by default to my knowledge and from the docs I've read - but that can have changed. The ufw page does say:

So, ufw could be installed by default now, but the page was not updated.

If it isn't ufw, then Hardy should have the same reports  from grc.com as the other releases until now: all ports closed - if you are directly connected to the Internet.

Downloading [daily Desktop Hardy cd build]("http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-i386.iso") to test it.

Hope to have some answers for this soon.

Considering I never mentioned ufw or even iptables I really don't understand what your problem is. I am getting stealth so your choice is either believe it or not. Don't accuse me of saying ANYTHING I didn't.

---

### Post by ung/xunil on 2008-03-06
Ok, just to make it clear. 

This thread has a title that says "Stealth" and the first post states:
> **Feivel said:**
> Man...windows takes a bit of playing with to get stealth on ShieldsUp at grc.com. Ubuntu 8.04 out of the box gets stealth. Bye-bye microsoft :)

I've downloaded the current daily build of Ubuntu 8.04, booted it with virtualbox and opened a terminal:
```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```
Then I've checked if ufw was installed:
```
$ dpkg --get-selections|grep ufw
ufw                            install
```
Then I've checked the installed documentation about ufw and read the file /usr/share/doc/ufw/README.Debian, were it states the following:
```
On installation, ufw is not automatically enabled. To load the firewall and enable it on boot, run:

# ufw enable
```
So the question still remains: where is the stealth out-of-the-box?

I'm not arguing about what is happening to you and what kind of internet connection you have. For what I know, Ubuntu isn't stealth out-of-the-box ATM. I just don't want people to find this thread and think that their Ubuntu Hardy should be stealth out-of-the-box, which will not happen unless they type "sudo ufw enable".

Have a nice day.

---

### Post by Oldsoldier2003 on 2008-03-06
> **ung/xunil said:**
> Ok, just to make it clear. 

This thread has a title that says "Stealth" and the first post states:


I've downloaded the current daily build of Ubuntu 8.04, booted it with virtualbox and opened a terminal:
```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```
Then I've checked if ufw was installed:
```
$ dpkg --get-selections|grep ufw
ufw                            install
```
Then I've checked the installed documentation about ufw and read the file /usr/share/doc/ufw/README.Debian, were it states the following:
```
On installation, ufw is not automatically enabled. To load the firewall and enable it on boot, run:

# ufw enable
```
So the question still remains: where is the stealth out-of-the-box?

I'm not arguing about what is happening to you and what kind of internet connection you have. For what I know, Ubuntu isn't stealth out-of-the-box ATM. I just don't want people to find this thread and think that their Ubuntu Hardy should be stealth out-of-the-box, which will not happen unless they type "sudo ufw enable".

Have a nice day.

The whole thing is misleading because a lot of dsl gateways will return stealth results to grc because they use nat and port forwarding.

The packets coming from the grc are mostly unsolicited so the router handles them because it doesn't know which host to send them to unless you have them port forwarded to a specific machine.(they aren't in response to an outbound from one of your boxes)  The only way to get truly verifiable answer is to connect a stock Ubuntu box directly to the internet with a modem, no gateway or sharing device.

---

### Post by ung/xunil on 2008-03-06
Yes, i know as I posted in [post #8]("http://ubuntuforums.org/showpost.php?p=4460252&postcount=8") and in [post #18]("http://ubuntuforums.org/showpost.php?p=4465619&postcount=18") of this thread. I defenitly think it's Feivel case.

---

### Post by Feivel on 2008-03-06
> **ung/xunil said:**
> Ok, just to make it clear. 

This thread has a title that says "Stealth" and the first post states:


I've downloaded the current daily build of Ubuntu 8.04, booted it with virtualbox and opened a terminal:
```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```
Then I've checked if ufw was installed:
```
$ dpkg --get-selections|grep ufw
ufw                            install
```
Then I've checked the installed documentation about ufw and read the file /usr/share/doc/ufw/README.Debian, were it states the following:
```
On installation, ufw is not automatically enabled. To load the firewall and enable it on boot, run:

# ufw enable
```
So the question still remains: where is the stealth out-of-the-box?

I'm not arguing about what is happening to you and what kind of internet connection you have. For what I know, Ubuntu isn't stealth out-of-the-box ATM. I just don't want people to find this thread and think that their Ubuntu Hardy should be stealth out-of-the-box, which will not happen unless they type "sudo ufw enable".

Have a nice day.

Did you run ShieldsUp at gru.com?

---

### Post by Oldsoldier2003 on 2008-03-06
> **Feivel said:**
> Did you run ShieldsUp at gru.com?
for the record:
3 computers on lan:
with everything on grc reports all service ports stealth  except 22
results are the same whether i run it on windows xp, windows xp under a virtual machine  ubuntu 7.10,  ubuntu 8.04, or ubuntu 8.04 under a virtual machine. the only difference is when I unplug my server then all ports  stealthed. 

I don't have a standalone dsl modem. bottom line GRC's test is crap and doesn't mean anything in the context of this thread. The only time it would be vaild is a standalone box with a direct connection because any NAT device will make the test lie...

---

### Post by Feivel on 2008-03-06
> **Oldsoldier2003 said:**
> for the record:
3 computers on lan:
with everything on grc reports all service ports stealth  except 22
results are the same whether i run it on windows xp, windows xp under a virtual machine  ubuntu 7.10,  ubuntu 8.04, or ubuntu 8.04 under a virtual machine. the only difference is when I unplug my server then all ports  stealthed. 

I don't have a standalone dsl modem. bottom line GRC's test is crap and doesn't mean anything in the context of this thread. The only time it would be vaild is a standalone box with a direct connection because any NAT device will make the test lie...

You running Heron? I ran the same back when I had XP and I had NOTHING stealth. Vista was a bit better because of the windows firewall. That is why running windows without a firewall is mostly suicidal.

---

### Post by Oldsoldier2003 on 2008-03-06
> **Feivel said:**
> You running Heron? I ran the same back when I had XP and I had NOTHING stealth. Vista was a bit better because of the windows firewall. That is why running windows without a firewall is mostly suicidal.
yep latest daily build. results all the same because of nat and forwarding. the xp in the virtual machine was brand new the xp plain was a 4(? i think, hell its been on the box since forever) year old install.

---

### Post by Salpiche on 2008-03-07
Never Mind!

---

### Post by saltedlight on 2008-06-19
I'm using Hardy, i have enabled ufw and went to grc.com. Results: all ports are stealth but did reply to ping.
After that i have uncomented the *net/ipv4/icmp_echo_ignore_broadcasts = 1* line in **/etc/sysctl.conf** restarted networking and checked again with grc.com. The same results: all ports are stealth but did reply to ping.

I would like to know what do i have to do to be really stealth, since ufw somehow disables /etc/sysctl.conf (or whatever is doing with it)...

#edit:

I found the answer here: [https://answers.launchpad.net/ufw/+question/26585](https://answers.launchpad.net/ufw/+question/26585)
I have commneted back the line in /etc/sysctl.conf and then i have commented the line in /etc/ufw/before.rules and 
after that i had to disable/enable ufw and networking. And it worked. "TruStealth" rating.

Is not really out of the box, but at least is much more than nothing. ;)

---

