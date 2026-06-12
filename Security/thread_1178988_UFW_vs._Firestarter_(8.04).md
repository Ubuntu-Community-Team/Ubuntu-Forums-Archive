---
title: "UFW vs. Firestarter (8.04)"
date: 2009-06-05
forum: Security
---

### Post by logos34 on 2009-06-05
Any compelling reason to switch to G/UFW Uncomplicated Firewall if my Firestarter is working fine?  I don't know what all the fuss is--I find Firestarter to be very easy to configure...But is it less secure?  They're both essentially just frontends for iptables

This is for a home desktop workstation, behind a wired router.  Other than torrents, web-surfing, and file sharing on lan, not much networking

---

### Post by pedja_portugalac on 2009-06-05
Firestarter don't filter ipv6 packets and as far as I know the project is stealth for some time. On the other hand ufw is officially supported by canonical and ubuntu community, it filters both ipv4 and ipv6 packets and is very easy to use on desktop. All you have to do is open your terminal and run:
> sudo ufw enable
Firewall is active and enabled on system startup with default policy of dropping all entering packets and allowing ipv6 only on local loopback. It's active on all interfaces so you don't have to change manually between eth0 and wlan, par example, like it was the case with firestarter.  
If you want to disable icmp (ping) responses you have to edit /etc/ufw/before.rules
> sudo gedit /etc/ufw/before.rules
Add the "#" sign before
> -A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
Now you have configured firewall witch successfully pass shields up test and if you want to add some new rule please read "man ufw". Its very easy, par example you can run on terminal

sudo ufw allow 25

       This  rule  will allow tcp and udp port 25 to any address on your host.To specify a protocol, append ’/protocol’ to the port. For example:

sudo ufw allow 25/tcp

       This will allow tcp port 25 to any address on this host. ufw will  also check  /etc/services  for the port and protocol if specifying a service by name.  Eg:

sudo ufw allow smtp

*** Please read man ufw***

PS. Firestarter was really helpful long time, and still it is, for tons of people around the world and I am really very sad that it seams to be the end of the project.

---

### Post by lovinglinux on 2009-06-05
There are controversies about the development status of Firestarter. Some say it is inactive, some say it doesn't need further development. Anyways, there is an increasing number of threads regarding issues with Firestarter recently, most likely due to the fact that it hasn't been updated for a while.

As already explained in the previous post, UFW is currently supported, installed by default and has an active development.

Another thing is that UFW does not provide a way to monitor connections, which is kind of good. Most users that use Firestarter keep it running all the time to monitor connections, which is bad. Firestarter needs root privileges to run and there are some discussions about possible exploitations that could compromise your entire system. Since both programs are just frontends for creating iptables rules, they can be closed after configuring the firewall settings, but most Firestarter users don't do that.

*UKeywords: 649167 2009 june firestarter ufw gufw iptables root connection monitoring*

---

### Post by logos34 on 2009-06-05
thanx guys for the info...I'll definately check out the man page and rules file for UFW...yeah, FS runs at startup (have to enter pwd a second time for FS, annoying) and the icon sits in my tray, lighting up everytime there's a hit.  Probably time to move on to a supported frontend.  Took a while to set up the ports just so for torrents and router, so I'm reluctant to touch it again.  Networking is my weakpoint (to tell the truth it bores the daylight out of me).  

Can someone point me to a good G/UFW howto?

---

### Post by bodhi.zazen on 2009-06-05
> **logos34 said:**
> Any compelling reason to switch to G/UFW Uncomplicated Firewall if my Firestarter is working fine?  I don't know what all the fuss is--I find Firestarter to be very easy to configure...But is it less secure?  They're both essentially just frontends for iptables

This is for a home desktop workstation, behind a wired router.  Other than torrents, web-surfing, and file sharing on lan, not much networking

First, If firestarter is working for you there is no reason to change.

With that said ... (and since you asked)

Firestarter is no longer maintained and, IMO, is starting to show it's age. I personally find :

1. Do you really need a firewall ?

2. If so, iptables should not be that difficult for you to learn (you seem experienced enough in Linux to grasp iptables). It takes an hour or so, but it is easy to configure iptables. One or two lines in iptables has replaced such things as denyhosts and fail2ban on my servers.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

Want to try ? 

ssh [EMAIL="root@ssh.bodhizazen.net"]root@ssh.bodhizazen.net[/EMAIL]

you have 8 chances, they you will be shut out.

To be honest, it takes as long to learn iptables as it does to download, configure, and install denyhosts, BUT you need to understand a fair amount about how linux and networking work first, and iptables is certainly not for everyone (nor would I advise it).

3. The default firewall in Ubuntu is now UFW. Ufw comes with a gui front end. Firestarter will almost certainly conflict with UFW, so why install additional packages if iptables / UFW / GUFW meets your needs. 

We should teach users to use the default tools rather then tell them to install Firestarter, which then conflicts with the default tools.

And if UFW / GUFW does not meet their needs we should understand their needs before blindly advising they install Firestarter, which may or may not meet their needs.

My question to you is, have you looked at GUFW ? If so, what features does it lack.

Please tell me you are not using Firestarter to monitor your network traffic, :lolflag:

4. If you have more complex networking, meaning virtual machines or you are configuring a box with multiple interfaces, to be used as a router, Firestarter will start to give you problems or outright fail.

5. If the argument that since it is no longer being developed means there are no problems we would all be on ubuntu 5.04 , which is no longer being developed or maintained either. The fallacy in that argument is obvious.

Firestarter is no longer being maintained. Where would you file a bug report if you found one ? How would a security hole be patched ? Such are the issues in advising an application that is no longer being developed.

Over time people will use firestarter less and less. It is one of those applications that has a loyal base and it works for many people, many of whom may not understand iptables or looked at the current alternates (GUFW, guarddog, sorewall, etc).

Take a look at GUFW and guarddog. Guarddog in particular has very nice built in help, which in my experience, is really helpful for new users.

So right back at you ---

Why are you insisting people use Firestarter when there are several viable alternates available ?

If you wish to learn ufw, see [Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw")

The syntax of ufw is almost identical to iptables, so once you are comfortable with ufw, simply

```
sudo iptables -L -v
```

and you should be able to migrate to iptables fairly easily.

---

### Post by blueridgedog on 2009-06-06
I recommend simply using iptables over any other approach.  the reasons are:

-It can be learned in about the same amount of time
-It can be managed from a ssh session
-It is likely to be on every system you administer
-Learning it will assist in really understanding networking
-It is a simple process (you can managed Linux routers with multiple nics with a few lines of code).
-It is portable, in that rules can be developed and shared or copied to new systems

---

### Post by cariboo on 2009-06-06
One other thing to keep in mind is, that if you are behind a router, Shields Up only checks your router and can't even see any computers behind the router.

If you need to see what ports are open, I would suggest using nmap, there is even a gui available. Nmap and zenmap are both in the reposiotires.

---

### Post by logos34 on 2009-06-06
thanks everyone

---

### Post by NET WT on 2009-06-08
I didn't want to start a new thread, but I have a question. I currently have firestarter installed on an Ubuntu 8.04 computer. I want to switch to Gufw, since I like it better. Is there a certain way that I should do this? Or do I just uninstall firestarter then install Gufw?

---

### Post by lovinglinux on 2009-06-08
> **NET WT said:**
> I didn't want to start a new thread, but I have a question. I currently have firestarter installed on an Ubuntu 8.04 computer. I want to switch to Gufw, since I like it better. Is there a certain way that I should do this? Or do I just uninstall firestarter then install Gufw?

Just uninstall one and install the other.

---

### Post by NET WT on 2009-06-08
So I just finished installing Gufw. I opened Gufw and checked the "Enabled" option. It isn't remembering any of my settings that I enter though, after I close it they are gone. Any idea why this is happening and how to fix? Also which of these should I choose? Deny, Reject, or Allow?

---

### Post by lovinglinux on 2009-06-08
> **NET WT said:**
> So I just finished installing Gufw. I opened Gufw and checked the "Enabled" option. It isn't remembering any of my settings that I enter though, after I close it they are gone. Any idea why this is happening and how to fix?

I don't use Gufw, because I create my own iptables rules, so I don't know exactly how it should behave, but that sounds weird. When you open it again, is it still activated? 

After setting the rules and closing it, run the following commands in the terminal and paste the results here.

```
sudo ufw status
```

and 

```
sudo iptables -L
```

> **NET WT said:**
> Also which of these should I choose? Deny, Reject, or Allow?

Gufw allows all outgoing traffic, so those options are for incoming traffic only. Deny will block connections without any replies, Reject will send a message to the source stating that it was rejected and Allow wil allow everything. The most common setup is to use Deny and create rules to open any port you need for incoming connections.

---

### Post by kevdog on 2009-06-08
Maybe someone can clarify this point for me, but I dont think guarddog has been updated for a long time either.  I think this project has gone the same way as Firestarter.  If one could clarify this for me it would be great.

---

### Post by bodhi.zazen on 2009-06-08
When you remove firestarter you need to purge it (to remove the config files).

```
sudo apt-get remove --purge firestarter
```

Then install gufw.

You may need to re-install and re-remove firestarter.

You may need to run gufw as root, I am not sure as I also use iptables.

```
gksu gufw
```

Hard to know if it a conflict with firestarter or a lack of root power.

---

### Post by NET WT on 2009-06-09
Sorry for the delay...

After setting Gufw, I ran ```
sudo ufw status
``` It said that the firewall was loaded. Opened up Gufw again but the "enabled" checkbox wasn't checked.
 
So I removed Gufw and re-installed firestarter, then ran that ```
sudo apt-get remove --purge firestarter
```Afterwards I installed Gufw again. Still having same issue though.

For now, I have firestarter installed again. Since it worked okay.

---

### Post by Soul-Sing on 2009-06-17
> **pedja_portugalac said:**
> Firestarter don't filter ipv6 packets and as far as I know the project is stealth for some time. On the other hand ufw is officially supported by canonical and ubuntu community, it filters both ipv4 and ipv6 packets and is very easy to use on desktop. All you have to do is open your terminal and run:

Firewall is active and enabled on system startup with default policy of dropping all entering packets and allowing ipv6 only on local loopback. It's active on all interfaces so you don't have to change manually between eth0 and wlan, par example, like it was the case with firestarter.  
If you want to disable icmp (ping) responses you have to edit /etc/ufw/before.rules

Add the "#" sign before

Now you have configured firewall witch successfully pass shields up test and if you want to add some new rule please read "man ufw". Its very easy, par example you can run on terminal

sudo ufw allow 25

       This  rule  will allow tcp and udp port 25 to any address on your host.To specify a protocol, append ’/protocol’ to the port. For example:

sudo ufw allow 25/tcp

       This will allow tcp port 25 to any address on this host. ufw will  also check  /etc/services  for the port and protocol if specifying a service by name.  Eg:

sudo ufw allow smtp

*** Please read man ufw***

PS. Firestarter was really helpful long time, and still it is, for tons of people around the world and I am really very sad that it seams to be the end of the project.

About how to disable icmp (ping) responses in gufw, done/tried that many times, but my system does not pass the shieldsup test on that ping/icmp part.
I know marcos (one of the dev. of gufw) made this how to, but again it does not work for me...
Tested on hardy heron 0.20.7 gufw.

---

### Post by bodhi.zazen on 2009-06-17
> **leoquant said:**
> About how to disable icmp (ping) responses in gufw, done/tried that many times, but my system does not pass the shieldsup test on that ping/icmp part.
I know marcos (one of the dev. of gufw) made this how to, but again it does not work for me...
Tested on hardy heron 0.20.7 gufw.

Shields up tests your router, not your computer. So unless you are connected directly without a router ufw will not affect the results.

Second, responding to a ping is really not something to be concerned about, IMHO.

If you wish to know how to ENABLE ping with ufw see here (by defalt ufw blocks ping) :

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw#Enable%20PING](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw#Enable%20PING)

---

### Post by Soul-Sing on 2009-06-17
```
If you wish to know how to ENABLE ping with ufw see here (by defalt ufw blocks ping) :
```

1) Thx.
2) And indeed I'am behind a router....

---

