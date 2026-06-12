---
title: "Vino is not secure"
date: 2011-05-28
forum: Security
---

### Post by Scott00 on 2011-05-28
I installed a fresh copy of Ubuntu 11.04 on my server about 2 weeks ago, I setup remote desktop and figured to just leave the password field out as it suppose to be pre-configured to only accept local connections, well, apparently not. I was noticing some strange network activity and checked my router connections and sure enough I see port 5900 to the server, open vino icon and see that there is someone else connected! (IP of unauthorized user: 77.29.51.239 ).. Immediately kick them and set a password. This should really be addressed and/or a password should be defaulted or at the very least the "Your desktop is only reachable over the local network." should be removed.

---

### Post by Irihapeti on 2011-05-28
The likely culprit is uPNP on your router. The Vino port (5900) is automatically forwarded to the internet with the predictable results.

To check that, you could run the custom port scan on [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) and get it to check ports 5800 and 5900.

There should be an option in Vino to tick if you want to approve a remote connect before it's allowed to connect. It sounds as though that was disabled as well.

If you have any doubt about what the intruder could have done, it might pay to reinstall Ubuntu.

Remote desktop is one of the top ways that people get hacked on Ubuntu desktop (another is ssh server). If I had my way, it would not be installed by default.

---

### Post by Scott00 on 2011-05-28
Perhaps you are right but it shouldn't make a difference if the port was enabled or not if it's configured to only listen for local connections.

It doesn't appear that anything was done, the server is only for a somewhat private game server and local file server which rarely gets activity and the router WAN-to-server bandwidth activity has been silent until then, luckily I was doing something with the router at the time and caught it right when it started. But just in case does Linux keep a log of recent console and nautilus activity?

---

### Post by Irihapeti on 2011-05-28
Nautilus does have a history of places visited. It's under the "Go" menu. I don't know what happens if someone, say, copies or deletes files via the GUI.

The console history is kept in the ~/.bash_history file. Bear in mind that a savvy intruder may have edited that file, which isn't hard to do.

Looking in the system log files might turn up something. If there are entries in the /var/log/auth file (which is added to whenever you run sudo) that you know you didn't do, that could be an indication of nasty activity.

---

### Post by CharlesA on 2011-05-29
In 10.04 and 10.10, there was a check box that would tell it to only accept local connections, pretty sure there it's still there in 11.04.

In any case, VNC is pathetically insecure as it's not encrypted and transmits everything in clear text. Use something like NXMachine or X forwarding if you need to access a GUI.

---

### Post by 0SNiX on 2011-05-29
[IMG]http://www.grc.com/image/transpixel.gif[/IMG]
 [FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=3][COLOR=#666666]Name: [/COLOR][/SIZE][/FONT][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#000066][IMG]http://www.grc.com/image/transpixel.gif[/IMG]
**vnc access**[/COLOR][/SIZE][/FONT]
[IMG]http://www.grc.com/image/transpixel.gif[/IMG]  [FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=3][COLOR=#666666]Purpose: [/COLOR][/SIZE][/FONT][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#000066][IMG]http://www.grc.com/image/transpixel.gif[/IMG]
**Virtual Network Computing**[/COLOR][/SIZE][/FONT]
[IMG]http://www.grc.com/image/transpixel.gif[/IMG]  [FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=3][COLOR=#666666]Description: [/COLOR][/SIZE][/FONT][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#000066][IMG]http://www.grc.com/image/transpixel.gif[/IMG]
This port (and port 5800) are opened by the VNC system allowing remote multi-platform console access.[/COLOR][/SIZE][/FONT]
[IMG]http://www.grc.com/image/transpixel.gif[/IMG]
[IMG]http://www.grc.com/image/transpixel.gif[/IMG]

---

### Post by 0SNiX on 2011-05-29
looks like my install of 11.04 got owned :(

---

### Post by tgm4883 on 2011-05-29
> **CharlesA said:**
> In 10.04 and 10.10, there was a check box that would tell it to only accept local connections, pretty sure there it's still there in 11.04.

In any case, VNC is pathetically insecure as it's not encrypted and transmits everything in clear text. Use something like NXMachine or X forwarding if you need to access a GUI.

If it's so bad, why is there not a push to remove it from the repositories?

---

### Post by CharlesA on 2011-05-29
> **tgm4883 said:**
> If it's so bad, why is there not a push to remove it from the repositories?
Same reason there are a load of other VNC servers in the repos.

It's fine for using on an internal network, but I wouldn't use it over the internet without having it tunneled.

---

### Post by Irihapeti on 2011-05-29
But why does it have to be installed by default?

This isn't one of those hypothetical "what-if" cases with no problems caused in practice. We see problems with intrusion via VNC almost every day.

It's too easy for people to just click on those boxes, not knowing anything about uPNP and routers, and get themselves into trouble.

I say it should be in the repos, but not installed by default.

But then, I suppose we could say that the other popular way of getting into trouble i.e. sshd, isn't installed by default and that doesn't seem to stop the problem.

---

### Post by CharlesA on 2011-05-29
Well it is installed by default, but isn't enabled.

I can't really think of a reason why it has to be installed by default.

Perhaps file a bug report on launchpad?

---

### Post by Irihapeti on 2011-05-29
> **CharlesA said:**
> Perhaps file a bug report on launchpad?

Done. [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/790009](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/790009)

Please add your support to this bug.

That goes for anyone who is reading this.

---

### Post by doas777 on 2011-05-29
op, you are correct, Vino is insecure, which is why it is not enabled by default. keep in mind though, the MS RDP server is no safer to allow to the outside world. either way, both are service that must remain internal only. I typically disable upnp on my routers just to make sure that anything that opens a listening port to the outside world has to be approved by me (via a manually set nat and firewall rule).

do you have an ssh instance on the server? are all your passwords strong? it is possible that someone is contacting your ssh service and using that to tunnel locally to the vino port. you could also use ufw to block access to vino except via 127.0.0.1.

---

### Post by tnt533 on 2011-05-30
Vino isn't turned on and accepting connections by default and, quite frankly, peoples hands can only be held so much. There are 10,000 different things a user could do to create a hole thats exploitable if they insist on doing things on their system that they know nothing about, like enabling remote desktop but not bothering to see if it is available on the outside of their firewall / router.

Seriously, I'm not trying to be a jerk here but the next time you enable anything that involves external connections to a host on a network, even if you "think" it will only accept local traffic, do yourself a solid and do some pen-testing before you let it run unattended. Scan ports at the gateway and make sure it's not visible.

The only secure system is one thats unplugged from the network, has no power and is buried in a vault under 100 feet of concrete.

---

### Post by mikewhatever on 2011-05-31
So, the command that runs by default from the Startup Applications is as follows:
```
/usr/lib/vino/vino-server --sm-disable
```

and I was wondering, doesn't it start a listening service on port 5900? Looks like it does just that:

```

sudo lsof -i -P -n | grep vino
[sudo] password for ...
vino-serv 4254  ...   16u  IPv6 100300      0t0  TCP *:5900 (LISTEN)

```

grc.com port prober agrees with the above.
[https://www.grc.com/x/portprobe=5900](https://www.grc.com/x/portprobe=5900)

---

### Post by doas777 on 2011-05-31
> **mikewhatever said:**
> So, the command that runs by default from the Startup Applications is as follows:
```
/usr/lib/vino/vino-server --sm-disable
```and I was wondering, doesn't it start a listening service on port 5900? Looks like it does just that:

```

sudo lsof -i -P -n | grep vino
[sudo] password for ...
vino-serv 4254  ...   16u  IPv6 100300      0t0  TCP *:5900 (LISTEN)

```grc.com port prober agrees with the above.
[https://www.grc.com/x/portprobe=5900](https://www.grc.com/x/portprobe=5900)

yes, you are correct, the VNC server listener is traditionally on tcp\5900, and connections range from 5901-5999 server-side.

---

### Post by doas777 on 2011-05-31
> **CharlesA said:**
> Well it is installed by default, but isn't enabled.

I can't really think of a reason why it has to be installed by default.

Perhaps file a bug report on launchpad?
I think its a feature parity thing. since windows has an integrated RDP system, Gnome or Canonical decided Ubuntu needed one as well. unfortunately, vino isn't as suited to the task, and besides, MS RDP isn't safe to expose to the outside either (though it is a little better, since it's integrated into the accounts system and can thus track failed login attempts). some of the problem is VNC, and some of it is vino's configuration (done to allow interactive session-sharing I think).

---

### Post by CharlesA on 2011-05-31
> **doas777 said:**
> I think its a feature parity thing. since windows has an integrated RDP system, Gnome or Canonical decided Ubuntu needed one as well. unfortunately, vino isn't as suited to the task, and besides, MS RDP isn't safe to expose to the outside either (though it is a little, since it's integrated into the accounts system and can thus track failed login attempts). some of the problem is VNC, and some of it is vino's configuration (done to allow interactive session-sharing I think).

Yep. I think that's the reason it's included by default as well. I've used it for session sharing a couple times, but I've switched to using NXMachine instead since it's encrypted and supports sessions.

The difference between vino and RDP is that RDP requires you to know a valid user account and password and vino only requires you to know a password (or no password, if none is set). Windows won't let you connect via RDP with an account that has a blank password. That and RDP uses encryption and vino (VNC) does not.

Of course, even with those features, I still wouldn't expose RDP directly to the internet.

---

### Post by mikewhatever on 2011-05-31
> **doas777 said:**
> yes, you are correct, the listener VNC server listener is traditionally on tcp\5900, and connections range from 5901-5999 server-side.

...but wasn't Ubuntu supposed to not have any listening services by default? When did it change?

---

### Post by doas777 on 2011-05-31
> **mikewhatever said:**
> ...but wasn't Ubuntu supposed to not have any listening services by default? When did it change?
I don't believe that it runs by default until you enable it via System->Preferences->Remote Desktop, or some other mechanism,l but that is based on Lucid and prior. I am sticking to LTS's anymore (except for VMs), so I don't have a lot of experience with maverick and natty. 

yes, it would be a major departure if vino was enabled by default, especially if the upnp options are on as well. yes, this would be a bug IMO.

---

### Post by bodhi.zazen on 2011-05-31
> **Irihapeti said:**
> Done. [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/790009](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/790009)

Please add your support to this bug.

That goes for anyone who is reading this.

I agree and posted on your bug report.

---

### Post by CharlesA on 2011-05-31
Posted in there too. Mine's kinda short, but to the point.

---

### Post by garycahill on 2011-06-01
To be safe tunnel Vino traffic over SSH, there's lots of HOWTOs out there and it stops lots of bad stuff happening.

---

### Post by bodhi.zazen on 2011-06-01
> **garycahill said:**
> To be safe tunnel Vino traffic over SSH, there's lots of HOWTOs out there and it stops lots of bad stuff happening.

Yes, but I think you are missing the point of this thread.

Although you can secure a VNC server, vino included, but tunneling it over ssh, out of the box, vino is configured so as to be insecure and worse UPnP will forward the port.

vino can be enabled at the click of a mouse, not true for tunneling over ssh.

---

### Post by CharlesA on 2011-06-01
Seems the bug report was marked as invalid and a comment posted to use the mailing lists.

[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/790009/comments/4](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/790009/comments/4)

---

### Post by Irihapeti on 2011-06-01
> **CharlesA said:**
> Seems the bug report was marked as invalid and a comment posted to use the mailing lists.

[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/790009/comments/4](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/790009/comments/4)

Yes, I saw that.

The idea of subscribing to the dev's mailing list is something I find rather daunting. My experience of mailing lists is that you get flooded with all messages, and I imagine that this particular one is rather busy.

Or can someone correct me on that?

---

### Post by CharlesA on 2011-06-01
> **Irihapeti said:**
> Yes, I saw that.

The idea of subscribing to the dev's mailing list is something I find rather daunting. My experience of mailing lists is that you get flooded with all messages, and I imagine that this particular one is rather busy.

Or can someone correct me on that?
I've not used a mailing list before, but that's what I picture as well.

Definitely an painful way to communicate.

---

### Post by doas777 on 2011-06-02
> **CharlesA said:**
> I've not used a mailing list before, but that's what I picture as well.

Definitely an painful way to communicate.
I've always been of the same impression. but that begs teh question, why do they still use them?

---

### Post by CharlesA on 2011-06-02
> **doas777 said:**
> I've always been of the same impression. but that begs teh question, why do they still use them?
I know. It's quite puzzling.

---

### Post by tgm4883 on 2011-06-02
> **CharlesA said:**
> I know. It's quite puzzling.

Probably because it's a little more difficult for the average user to work with. It's email, so it's available everywhere in a format you can likely read. You don't need to set up a forum somewhere. They are stuck in their old ways.

Pick one

---

### Post by CharlesA on 2011-06-02
> **tgm4883 said:**
> Probably because it's a little more difficult for the average user to work with. It's email, so it's available everywhere in a format you can likely read. You don't need to set up a forum somewhere. They are stuck in their old ways.

Pick one

As bizarre as that sounds, it kinda makes sense.

Doesn't mean that it couldn't be improved tho.

---

### Post by Irihapeti on 2011-06-02
The other thing is, mailing lists are very difficult to sort through to see if something similar has been posted.

Here on the forums, we can run a search. Even if it's not the best search engine, there is still something. On a mailing list, unless it's got an interface like gmane (where you can view it as though it were a blog), you are presented with myriad monthly archives in the form of text files. I think you'd have to download the lot and search through them all - not my idea of fun.

I suppose I'm trying to say that I don't feel motivated to join the list and post.

---

### Post by CharlesA on 2011-06-02
> **Irihapeti said:**
> I suppose I'm trying to say that I don't feel motivated to join the list and post.

Don't blame you for that.

---

### Post by Irihapeti on 2011-06-02
I've decided to give it a go. Currently, I'm waiting for approval. I'll post when I've got that.

If I turn up here looking all battered and confused, you'll know why. :lol:

---

### Post by CharlesA on 2011-06-02
Best of luck!

---

### Post by Irihapeti on 2011-06-03
OK, it seems like it's not regarded as a problem by list members, except perhaps for improving the information on the UI to point out the risks.

---

### Post by CVGH on 2011-06-04
Hi Guys,
Just started to mess with remote access methods on Ubuntu 10.10 with OpenSSH server.
I'm using an iPhone app that lets me either SSH or VNC or tunnel thru SSH to VNC. I also use Teamviewer6, but I think that is just using port 80. 
I am able to do this thru the 3G network fine, but haven't tried it yet from another wifi network.
I've set sshd_config to not allow root access and VNC requires a password which is a mix of caps/lowercase and characters.
What is my risk here?

Thanks!!

---

### Post by Irihapeti on 2011-06-04
One of the problems with the default version of VNC in Ubuntu (vino) is that it's unencrypted. Therefore, if you're accessing it through a public wifi network, anyone can see what you're sending/receiving, including your password.

The ideal would be running VNC through SSH, or using another encrypted VNC server on the machine you are wanting to access. A strong password of numbers, letters and special characters would be the minimum requirement, and it needs to be a decent length. The ideal would be an SSH key.

If you have to use passwords/phrases, then it would be a good idea to set up some sort of connection limiting, so that people can't keep trying to connect indefinitely and brute force the password. That can be done using iptables or by installing denyhosts or fail2ban. There are a number of posts in this forum giving details of how to do that.

---

### Post by CVGH on 2011-06-05
I've got Vino running through SSH and I've set " # ufw limit ssh/tcp".
Can I close port 5900 off in the router?

---

### Post by bodhi.zazen on 2011-06-05
> **CVGH said:**
> I've got Vino running through SSH and I've set " # ufw limit ssh/tcp".
Can I close port 5900 off in the router?

If you are tunneling over ssh , yes you can close port 5900

---

### Post by CVGH on 2011-06-05
bodhi,

When I close the port on the Airport router, the ssh part works, but cannot connect to VNC.  I have set "ufw limit 5900:5910/tcp" .
I'm wondering if it's the iphone app giving me trouble...

[http://rafsoftware.com/rafsoftware/home/](http://rafsoftware.com/rafsoftware/home/)


Found your blog, excellent info there!!

---

### Post by tgm4883 on 2011-06-05
> **CVGH said:**
> bodhi,

When I close the port on the Airport router, the ssh part works, but cannot connect to VNC.  I have set "ufw limit 5900:5910/tcp" .
I'm wondering if it's the iphone app giving me trouble...

[http://rafsoftware.com/rafsoftware/home/](http://rafsoftware.com/rafsoftware/home/)


Found your blog, excellent info there!!

If you can SSH but not VNC after closing that port on your router, then you aren't tunneling the traffic over SSH.

---

### Post by bodhi.zazen on 2011-06-05
> **tgm4883 said:**
> If you can SSH but not VNC after closing that port on your router, then you aren't tunneling the traffic over SSH.

This is spot on.

Here is a tutorial (written for windows, but it is essentially the same in Linux).

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

---

### Post by CVGH on 2011-06-05
Spot on guys, had the app set-up incorrectly!
Now to figure out how to get the public ssh key from
the app  to the server....
Many thanks!!!

---

### Post by Rebelli0us on 2012-05-16
Are you guys trying to scare people?

My Remote Desktop Viewer says "Your desktop is only reachable over the local network..." and in any case grc.com reports ports 5800 & 5900 as "stealth".

---

### Post by CharlesA on 2012-05-16
> **Rebelli0us said:**
> Are you guys trying to scare people?

My Remote Desktop Viewer says "Your desktop is only reachable over the local network..." and in any case grc.com reports ports 5800 & 5900 as "stealth".
Old thread, is old?

Vino is only accessible from the internet is you select "configure the network automatically" and have upnp enabled on your router.

---

### Post by Rebelli0us on 2012-05-16
> **CharlesA said:**
> Old thread, is old?

Vino is only accessible from the internet is you select "configure the network automatically" and have upnp enabled on your router.

Right, thank you, that's good to know. Old thread yes, but "Remote Desktop Viewer" is installed by default, so people Google and this comes up. :popcorn:

---

### Post by CharlesA on 2012-05-16
vino is just the "remote desktop" server installed in Ubuntu. The remote desktop viewer is a different program.

---

### Post by Rebelli0us on 2012-05-16
> **CharlesA said:**
> vino is just the "remote desktop" server installed in Ubuntu. The remote desktop viewer is a different program.

Thank you. I was able to control **any** computer on my network, I still have to **wake** the machine and **login**... but I hope it's secure.

---

### Post by CharlesA on 2012-05-16
> **Rebelli0us said:**
> Thank you. I was able to control **any** computer on my network, I still have to **wake** the machine and **login**... but I hope it's secure.
What OS are the machines you are connecting to running?

As long as you have remote access set up correctly, you should be fine.

---

### Post by bodhi.zazen on 2012-05-16
> **Rebelli0us said:**
> Are you guys trying to scare people?

Not scare them, but inform them.

Vino (VNC) is by far the most common crack into Ubuntu systems. So while you may understand the security implications, and while you may be behind a router, you need to make sure others are secure as well.

People not using a router, people forwarding ports, and UPnP are all too commonly cracked.

Education != FUD

---

### Post by Rebelli0us on 2012-05-16
> **CharlesA said:**
> What OS are the machines you are connecting to running?

As long as you have remote access set up correctly, you should be fine.

All Windows, and I'm converting to **all** Ubuntu, but I've hit a snag -- [wakeonlan does not work when target machine is running Linux.]("http://ubuntuforums.org/showthread.php?t=1980486")

---

### Post by Rebelli0us on 2012-05-16
> **bodhi.zazen said:**
> Not scare them, but inform them.

Vino (VNC) is by far the most common crack into Ubuntu systems. So while you may understand the security implications, and while you may be behind a router, you need to make sure others are secure as well.

People not using a router, people forwarding ports, and UPnP are all too commonly cracked.

Education != FUD

Thank you. As a Linux newbie it was incredibly easy to control machines on my network, I just enabled "Remote Desktop Viewer" and BANG I'm in! Made me think twice.

---

### Post by CharlesA on 2012-05-16
> **Rebelli0us said:**
> All Windows, and I'm converting to **all** Ubuntu, but I've hit a snag -- [wakeonlan does not work when target machine is running Linux.]("http://ubuntuforums.org/showthread.php?t=1980486")
D'oh!

I've only had to use WoL on a Windows box a couple times - and I sent the packet from the router (running *nix).

WoL is usually handled by the BIOS, so I don't know why it wouldn't work.

---

### Post by Rebelli0us on 2012-05-16
> **CharlesA said:**
> D'oh!

I've only had to use WoL on a Windows box a couple times - and I sent the packet from the router (running *nix).

WoL is usually handled by the BIOS, so I don't know why it wouldn't work.

Thank you, I'm stumped too. But it's gotta work, we routinely fetch files on the network and wake the machines remotely, there's no way we gonna walk around pressing power buttons.

---

### Post by CharlesA on 2012-05-16
If the files aren't really machine specific, wouldn't it be easier just to have a NAS and throw all the files there?

That's what I do.

---

### Post by bodhi.zazen on 2012-05-16
> **Rebelli0us said:**
> Thank you, I'm stumped too. But it's gotta work, we routinely fetch files on the network and wake the machines remotely, there's no way we gonna walk around pressing power buttons.

Use ssh. Putty is a graphical client for windows. Ssh is more secure, you can forward graphical applications ( ssh -X) with Xming

---

