---
title: "Firestarter And iptables"
date: 2008-08-17
forum: Security
---

### Post by Nosophorus on 2008-08-17
Hallo!

I would like to know if installing firestarter would mess up the iptables default configuration. I am pondering on uninstalling that firewall but I feel a little insecure upon that, since I have in my mind that firestarter could mess up the iptables default configuration.

May I uninstall firestarter? Or doing it would mess up my system?

Thank you!

Nosophorus

---

### Post by dje on 2008-08-17
have you made any changes in Firestarter? as it is a gui configuration frontend to iptables, any changes you make in firestarter will be applied to iptables and thus will stick after you uninstall it. it will not mess up your system by uninstalling it

dje

---

### Post by Nosophorus on 2008-08-17
Hi!

Thank you for your quick reply! :)

I only did what I was told by this tutorial:

[Secure Ubuntu Desktop Using Firestarter Firewall]("http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html")

But I did not change anything upon policies and the password stuff.

Does that mess up something? Is it serious?

Thank you!

Nosophorus

---

### Post by dje on 2008-08-17
do you want to install firestarter or uninstall it? unless you are running web or ssh servers firestarter is not necessary (it is not a firewall, it is a configuration frontend to iptables, the built in firewall). So if you are wondering whether to install it or not i would say no unless you run software such as those mentioned above. If you want to uninstall it will not mess up your system.

dje

---

### Post by Nosophorus on 2008-08-17
Hallo!

I want to uninstall the firestarter. :)

Nice to know that my system will not be vulnerable to external attacks after uninstalling firestarter.

I am going to uninstall it right now.

Are there any means to know if my ports are being scanned by someone else?

Thanks!

Nosophorus

---

### Post by dje on 2008-08-17
i would suggest uninstalling firestarter using the built in firewall configuration tool (UFW) and just setting it do deny incoming connections by default:
```
sudo ufw enable
sudo ufw default DENY
```
for more information see [here]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html"), i use this just for peace of mind

dje

---

### Post by Nosophorus on 2008-08-17
Hallo!

I tried the ufw command, but I think that command is not included in Gutsy Gibbon version.

Thank you again! :D

Nosophorus

---

### Post by Nosophorus on 2008-08-17
Hallo!

By the way, I uninstalled firestarter and I was not able to run the command ufw, since Gutsy is not compatible with it. I tried "sudo apt-get install ufw", but it failed. :(

So, do you think my machine is vulnerable to external attacks?

Thanks!

Nosophorus

---

### Post by hyper_ch on 2008-08-17
(1) if you install firestarter it will alter the default settings of iptables
(2) in most cases you don't need to bother with altering iptables... linux is not windows.

---

### Post by dje on 2008-08-17
im not an expert on this but if you don't have ssh, ftp and web servers running then the default firewall settings are fine. when i ran feisty i did not use firestarter and it was fine. i think it comes down to personal choice, if you would feel better in yourself knowing that you have firestarter installed then install it

dje

---

### Post by Nosophorus on 2008-08-17
Hallo!

Thank you for the replies!

I uninstalled firestarter because it was boring me and, also, because a guy said it had scanned my IP. I have valuable informations in this machine from my projects at university and I would not like to lose them.

By thw way, I got a test at [GRC]("https://www.grc.com/x/ne.dll?bh0bkyd2") and the result was as following:

*Your system has achieved a perfect "TruStealth" rating. Not a single packet &#8212; solicited or otherwise &#8212; was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.*

All those ports, from 0 to 1055, are stealth, according to the test. Maybe I have no reason to worry about invasion in this machine.

Thank you!

Nosophorus

---

### Post by beyboo on 2008-08-17
May seem a bit out of topic, however my two cents on this issue. I have been using Firestarter since Gutsy Fiesty Fawn days. It is the single most important and easy to use tool which I rely on very heavily to control who comes in and goes out. 

On the net there is a heavy barrage of probes, malware and other packets coming your way. It is a pleasure to watch Firestarter / iptables drop all of it. 

Take a look at the snapshot I have just added to this post. Obviously its a pleasure to see the red lines which means packets were dropped from some prospective telnet guy out in the bad bad net :)

---

### Post by hyper_ch on 2008-08-17
do you have telnet installed?

---

### Post by Nosophorus on 2008-08-17
Hi!

Yes, I have telnet installed.

I think it means that someone outside could transfer data to my computer via that protocol - or vice-versa. Isn't it?

Thank you!

Nosophorus

---

### Post by hyper_ch on 2008-08-17
is there a reason to have telnet?

---

### Post by Nosophorus on 2008-08-17
Hi!

Sure not. But I think TELNET came by default in Ubuntu - or, if I am not wrong - I installed it just to play with.

Would be reasonable to uninstall it?

Thanks!

Nosophorus

---

### Post by brian_p on 2008-08-17
> **Nosophorus said:**
> Hi!

Sure not. But I think TELNET came by default in Ubuntu - or, if I am not wrong - I installed it just to play with.

The telnet progam is for **connecting to** other machines running telnetd. The default Ubuntu install does not come with telnetd so someone outside cannot connect to you.

> Would be reasonable to uninstall it?

If you did install telnetd and do not use it it would reasonable to uninstall it.

---

### Post by Nosophorus on 2008-08-18
Hi!

Thank you very much for the replies!

I have uninstalled TELNET. Thanks for the explanation, Brian.

But, my machine is still without firestarter. It's a little complicated to know if that is good or not.

Thank you!

Nosophorus

---

