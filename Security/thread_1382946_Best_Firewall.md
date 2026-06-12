---
title: "Best Firewall?"
date: 2010-01-16
forum: Security
---

### Post by bmesta on 2010-01-16
Can someone please suggest the best firewall out there for ubuntu? I need user friendly GUI[LEFT][/LEFT]

---

### Post by zero-n on 2010-01-16
There is a firewall installed in Ubuntu by default you can install a GUI for it Like firestarter.

```
sudo apt-get install firestarter
```

---

### Post by running_rabbit07 on 2010-01-16
```
sudo ufw enable
``` ```
sudo apt-get gufw
``` ```
sudo gufw
``` UFW is already built into Ubuntu, just has to be enabled. GUFW is the easily configured GUI for UFW.

---

### Post by bodhi.zazen on 2010-01-17
> **bmesta said:**
> Can someone please suggest the best firewall out there for ubuntu? I need user friendly GUI[LEFT][/LEFT]

The firewall in Linux is called iptables.

Iptables is in turn a front end for netfilter.

All the other applications (ufw, gufw, firestarter, shorewall, etc) are fron tends for iptables.

If yo are looking for a front end, what features do you want ?

Personally it is easiest to simply use iptables directly, iptables is very straight forward and there are a number of powerful options.

The only problem with iptables is that it takes a little time to learn.

---

### Post by hortstu on 2010-02-16
sudo apt-get gufw isn't working for me.

terminal returns 

E: invalid operation gufw

I'm using hardy...

---

### Post by Charlietje on 2010-02-16
> **hortstu said:**
> sudo apt-get gufw isn't working for me.

terminal returns 

E: invalid operation gufw

I'm using hardy...

you should use:
```
sudo apt-get install gufw
```

---

### Post by hortstu on 2010-02-16
> **Charlietje said:**
> you should use:
```
sudo apt-get install gufw
```

Thanks but I get the same error with that command.

---

### Post by lukjad on 2010-02-16
Really? Hm. Can you make sure to copy/paste exactly what is there into the terminal:

```
sudo apt-get install gufw
```

There should then be a request for your password. 

Just as a tip, to paste via the keyboard in the terminal the key combo is Ctrl+Shift+V

---

### Post by hortstu on 2010-02-16
yes it requested my password but then I got this...

```
mike@mike-laptop:~$ sudo apt-get install gufw
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gufw
mike@mike-laptop:~$ 
```

---

### Post by bodhi.zazen on 2010-02-16
> **hortstu said:**
> yes it requested my password but then I got this...

```
mike@mike-laptop:~$ sudo apt-get install gufw
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gufw
mike@mike-laptop:~$ 
```

What version of Ubuntu are you running and what repositories are you using ?

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gufw&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gufw&searchon=name&subword=1&version=all&release=all)

---

### Post by DawieS on 2010-02-16
Just to get back to the original question, I prefer **firestarter** over **gufw** mainly because it also has a panel showing the active connections. You can see who is connected at any time, and thus can take corrective action if you see abnormal activities.

Over the past 2 months or so, I have compiled an address list of most of the websites I regularly visit, as well as servers from which updates are downloaded. I keep **firestarter** permanently open in one corner of the screen, and have it auto-start at boot time by including it in the **System-Preferences-Startup Applications** tab. I avoid having to type a password by adding the following line to the **/etc/sudoers** file:

%admin HostName=(root)NOPASSWD:/usr/sbin/firestarter
(where HostName is the name of your machine)

To be able to edit the **/etc/sudoers** file, you have to use the '**sudo visudo**' command in a terminal.

To be able to catch the unwanted visitors spying on me in the act, I have copied the '**Take Screenshot**' icon to the top panel, and have to click only twice to have the offending addresses stored for review - it normally happens too fast to write it down. I use the 'Whois' tab of '**Network Tools**' (available in **Synaptic Package Manager**) to determine the identity of addresses, and then decide whether or not I should have any affiliation with them.

As I read through the pages of this forum, I expect '91.189.94.12' to show up in **firestarter** for about 2 seconds as I turn to the next page. If anything else, I take a screenshot and review it later. Just last night I have added 3 addresses to my block-list:
204.9.163.163 - Quiet Touch - Toronto - Skype QTT-1-NET
38.99.76.31  -  Ezri / ImageShack Corp.  - Los Gatos  - CA
208.94.2.100  - Ezri Inc - IMAGESHACK.US  - Los Gatos  - CA
The last 2 even gave me a cookie for free! I suspect that these are spy-bots eavesdropping at DNS servers and hooking onto traffic passing by, thereby able to breach the router hardware firewall.

My block-list thus far contains about 20 address ranges, of which only 2 was due to hacking attacks, which have breached the router firewall, but was stopped by the iptables/netfilter firewall.

The way things are going now, soon it will be less effort to block all by default, and add allowed addresses only.

It is a pity that **firestarter** is no longer supported, it is clearly a better interface than **gufw** in its present form.
[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by 2hot6ft2 on 2010-02-16
> **DawieS said:**
> 
It is a pity that **firestarter** is no longer supported, it is clearly a better interface than **gufw** in its present form.
[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]
I agree, but then GUFW is still under development and is already able to use IPV6 (ip6tables). Maybe they can incorporate a view current connections window in the future.

EDIT: I just added it as a feature request in launchpad. Ask and you may receive. It's titled "[Current Connections View]("https://blueprints.launchpad.net/gui-ufw/+spec/2hot6ft2")" in launchpads blueprints.
If anyone wants to help it along.

---

### Post by hortstu on 2010-02-16
> **bodhi.zazen said:**
> What version of Ubuntu are you running and what repositories are you using ?



[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gufw&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gufw&searchon=name&subword=1&version=all&release=all)

hardy but I'm not sure about the repositories... how do i find out so I can tell you?

---

### Post by bodhi.zazen on 2010-02-17
> **hortstu said:**
> hardy but I'm not sure about the repositories... how do i find out so I can tell you?

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by hortstu on 2010-02-17
Thanks bodhi...

I  enabled backports and that did the trick.

I'd mark this solved but I hijacked the thread...

---

### Post by bodhi.zazen on 2010-02-17
> **hortstu said:**
> Thanks bodhi...

I  enabled backports and that did the trick.

I'd mark this solved but I hijacked the thread...

It's OK, I doubt "Best firewall" will ever be solved. IMO it is best that there are options, why do people have to have these endless arguments  about which is "best" ?

to add my 2c, iptables is best, It is simple to use (once you learn the syntax, lol), powerful, and most of the gui tools offer limited features. rather then using iptables people often install additional tools such as fail2ban or denyhosts.

---

