---
title: "Is there any  need Firewall software  for Home PC ?"
date: 2021-03-20
forum: Security
---

### Post by gardenair on 2021-03-20
Hi,
      I am using Ubuntu computer and normally it remain turn on 5 to 6 hours.My daily task are browsing ,working of GIMP , Office suit etc etc.
Linux systems are more secure than Windows ,there are no virus  issues in Linux operating system. Is there any need of Firewall software to protect my PC while i am online ?  
Thanks

---

### Post by ajgreeny on 2021-03-20
If you are not running any services, eg a server, open to the wider web you are probably fine without a firewall running.

A lot of users simply enable the firewll with command ```
sudo ufw enable
``` and leave it at that but does not add very much, if anything, when compared with the default settings of Ubuntu.

However if you run any servers open to the internet you most definitely should have the firewall setup with appropriate rules; I will have to leave it to others to give advice in detail as I've never run any servers so have never in my 16 years of Ubuntu used a firewall.

---

### Post by thumper76 on 2021-03-21
I think Linux gives a lot of people a false sense of security. Sure it's a lot more secure than Windows, but that not saying much. When you think of all the automated probes running continuously on the net and all the zero day exploits, etc, it's probably wise to use anything that might give you some added protection. Installing UFW is trivial and its default is block all incoming and allow all outgoing. When I check the UFW log I'm amazed at all the junk that get through my router firewall. Most of it is probably harmless, but you never know. When it comes to security, think of it as a layered process. Make use of every tool.

---

### Post by TheFu on 2021-03-21
Computer security needs to be multi-layered. What is necessary depends on your network architecture, the security built into that network, how good you are with consistently patching, how good your backups are, and whether the users are prone to click "OK" to every browser dialog box or not.

At the top of this page: [https://ubuntuforums.org/forumdisplay.php?f=338](https://ubuntuforums.org/forumdisplay.php?f=338) - that's the Security Sub-forum here, is a sticky thread for basic security and the question about Firewalls at the top.
My signature below has more links.

Whether anyone needs a firewall, cannot be simply answered.  The only correct answer is "it depends."  Enabling a firewall on Ubuntu certainly can help security at the cost of a little more hassle.  **gufw** has an easy-to-use interface with home, work, and public profiles, based on which network you might be on.

Good luck. Stay patched. Keep your router patched and the firewall on it on, don't click "ok" to most browser questions, have automatic backups and everything will probably be fine for a typical home user.  Businesses have different needs and some businesses have much higher security needs because they are targets.  If you are the owner of a business, you are a target.

---

### Post by ajgreeny on 2021-03-21
> **thumper76 said:**
> < snip >
Installing UFW is trivial and its default is block all incoming and allow all outgoing.
< snip >
That is exactly the situation even without ufw installed and enabled so it does not really add anything to your security if using a standard desktop setup with no servers.

---

### Post by gardenair on 2021-03-21
Thanks for the replies.Appreciate it. Well yes, my concern is only to protect my system from the external thread. I  have limited sites in which I just do browsing and do my work. My system is not like a server it is just what you can say for normal personal usage.
Thanks for guiding me.

---

### Post by DuckHook on 2021-03-23
I'm late to the party, but here are my observations:

The primary firewall for most people is the one in their router. However, TheFu raises a good point: we always council users to practice security in depth. This means that, generally, the more layers you have, the better.

[LIST=1]
[*]Example 1: if an IoT device is corrupted by a bad guy such that it phones home to some C&C server for further instructions, then firewall rules prohibiting outgoing connections for that IoT device would be an effective short term band&#8209;aide.
[*]Example 2: if that same corrupted IoT device manages to download those instructions, it is now behind your router firewall and free to roam your LAN. But if your servers, workstations, mobile devices and, most of all, your router, are in turn firewalled from that device, then the damage it can inflict can be somewhat contained.
[/LIST]
The big downside to this amount of safety is a discouraging level of complexity and maintenance. It's hard to see how anyone would be willing to set aside the time or put up with the frustration.

---

### Post by Graham1 on 2021-04-17
I think it would be a good idea for Ubuntu to add GUFW by default. It has a simple GUI which would fit in well with Ubuntu. I have it installed and only really need it to allow traffic for 0.A.D. It would also make new users feel more secure and advanced users could either uninstall or replace with something else.

:)

---

### Post by ipv2 on 2021-04-20
you can also use clam av as an on-demand scanner especially if you sharing flash drives with windows machines or sharing files from windows machines via samba.

for me clam av has also many times detected unwanted stuff that got in via the browsers.

```
sudo apt install clamav
```

if you prefer clam av with gui :

```
sudo apt install clamtk
```

---

### Post by kevdog on 2021-04-20
Frankly I find clam horrible, it slow and ties up the processor.  I'm not a security expert but I've never had clamav ever catch anything.

---

### Post by CharlesA on 2021-04-21
> **kevdog said:**
> Frankly I find clam horrible, it slow and ties up the processor.  I'm not a security expert but I've never had clamav ever catch anything.

Same. All I've gotten when I've run ClamAV is false positives.

The same can be said for other AV too.

---

### Post by ipv2 on 2021-04-21
clam scan run on home folder via clamtk :

[ATTACH=CONFIG]288355[/ATTACH]

---

### Post by makitso on 2021-04-21
> [COLOR=#000000]Is there any need of Firewall software to protect my PC while i am online ?[/COLOR]
[COLOR=#000000]Thanks[/COLOR]

IMHO, probability is a more important factor.  Folks that use linux are a bit more technically sophisticated than the general windows population.  So, the changes of being a target of a virus or malware is lower since there linux users are less apt to click on an unknown email attachment, etc.

Detection or Prevention;  nothing has been said about prevention.  If you have a good ad blocker such as Ublock Origin, then much of the malware, embedded in ad's will be blocked again lowering the probability factor.

---

### Post by Skaperen on 2021-04-22
you don't *need* a firewall if everything in your network is secure.  but it is an added layer you *should* include.  it *should not* be on the same machine as other stuff.  on the router is ideal, in theory.  but, many routers are poorly designed and weak at security.  a false sense of security is a bad idea unless you are running it as a honeypot.

---

### Post by CharlesA on 2021-04-22
> **Skaperen said:**
> you don't *need* a firewall if everything in your network is secure.  but it is an added layer you *should* include.  it *should not* be on the same machine as other stuff.  on the router is ideal, in theory.  but, many routers are poorly designed and weak at security.  a false sense of security is a bad idea unless you are running it as a honeypot.

You should be running a firewall on any client machine regardless if you think your network is secure or not.

Ideally, you would have your network segmented and any risky devices such as game consoles, smart TVs, or other IoT junk should be on their own subnet and blocked from communicating with anything on the trusted network.

I'd probably go so far as to say you should do the same for the guest network as well.

---

