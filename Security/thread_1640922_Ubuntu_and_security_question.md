---
title: "Ubuntu and security question"
date: 2010-12-08
forum: Security
---

### Post by havtrouble on 2010-12-08
I come to Ubuntu with the notion that it is much more secure than Windows. 
In XP I had an anti-virus, third-party firewall and sundry softwares against spybots, rootkits etc. The anitivirus blocked the suspicious web pages while browsing. I generally avoided public networks, carrying a portable internet device
Do I need similar stuff with Ubuntu.

---

### Post by CharlesA on 2010-12-08
You don't really have to worry about the same threats on a Linux box, as you would on a Windows box.

There are no viruses for Linux "in the wild," and the way Linux handles permissions allows, at most, your home directory to be compromised, unless you allow a malicious program root access.

Reading the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812") may help as well. :)

---

### Post by Megaptera on 2010-12-08
This is also a useful read [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by HermanAB on 2010-12-09
Howdy,

Ensure that you have a proper password with at least 9 characters for ALL user accounts, then relax and enjoy your Ubuntu system.

---

### Post by oldsoundguy on 2010-12-09
> **havtrouble said:**
> I come to Ubuntu with the notion that it is much more secure than Windows. 
In XP I had an anti-virus, third-party firewall and sundry softwares against spybots, rootkits etc. The anitivirus blocked the suspicious web pages while browsing. I generally avoided public networks, carrying a portable internet device
Do I need similar stuff with Ubuntu.

QUOTING: "Linux is NOT Windows."
the millions of items of malware written to attack Windows ... attack Windows .. they can NOT attack Linux.
Virtually NOTHING can get into the Linux kernel unless YOU, the user, give it permission by using your password.
PLUS, the malware would have to have been written FOR Linux.
Now, your BROWSER can be re-directed and damage to IT can happen if you do not exercise the usual cautions when surfing.

---

### Post by havtrouble on 2010-12-09
What about password thefts by keyloggers etc. How careful should I be when I use banking pages

---

### Post by CharlesA on 2010-12-09
You'd have to give a keylogger root permission for it to install, or install it yourself.

---

### Post by movieman on 2010-12-09
> **CharlesA said:**
> You'd have to give a keylogger root permission for it to install, or install it yourself.

Or get it installed by a browser exploit.

The same points above generally apply, however: it would need to be a Firefox/Flash/whatever browser/plugin exploit which runs on Linux and isn't stopped by Apparmor.

Edit: Personally I have one account that's used for online banking and pretty much nothing else. That way even if there is a browser exploit that installs malware on my normal browsing account it's almost certainly not going to affect the banking one.

---

### Post by Sylos on 2010-12-09
Just to pop a thought ito the mix..... I think (from memory) the apparmor browser profiles are not enabled by default so the OP would need to enable one in order to get its protection.

---

### Post by ptn107 on 2010-12-09
> **Sylos said:**
> Just to pop a thought ito the mix..... I think (from memory) the apparmor browser profiles are not enabled by default so the OP would need to enable one in order to get its protection.

That is correct, but it's easy to enable them:
```
sudo aptitude install apparmor-profiles
sudo aa-enforce firefox
```

You should try enabling all of them unless you run into problems:
```
sudo aa-enforce /etc/apparmor.d/*
```

---

### Post by CharlesA on 2010-12-09
> **movieman said:**
> Or get it installed by a browser exploit.

The same points above generally apply, however: it would need to be a Firefox/Flash/whatever browser/plugin exploit which runs on Linux and isn't stopped by Apparmor.

Edit: Personally I have one account that's used for online banking and pretty much nothing else. That way even if there is a browser exploit that installs malware on my normal browsing account it's almost certainly not going to affect the banking one.
Yep that's true. Which is why I use AppArmor on firefox.

---

### Post by bodhi.zazen on 2010-12-09
> **havtrouble said:**
> I come to Ubuntu with the notion that it is much more secure than Windows. 
In XP I had an anti-virus, third-party firewall and sundry softwares against spybots, rootkits etc. The anitivirus blocked the suspicious web pages while browsing. I generally avoided public networks, carrying a portable internet device
Do I need similar stuff with Ubuntu.

On Ubuntu I use apparmor to confine all applications the are network aware.

I use a firewall on public (wireless) networks, although it is probably unnecessary to do so.

On a public network I assume my traffic is being sniffed and that anyone can read it. If I want privacy, use ssl (https) and tunnel over ssh.

I manage bad acting web sites with a dose of NoScript + Privoxy (I should blog about Privoxy, everyone seems interested in privacy these days, and Privoxy does a nice job, faster then TOR).

---

### Post by cariboo on 2010-12-09
> I manage bad acting web sites with a dose of NoScript + Privoxy (I should blog about Privoxy, everyone seems interested in privacy these days, and Privoxy does a nice job, faster then TOR).

Yes please do.

---

### Post by CharlesA on 2010-12-09
> **bodhi.zazen said:**
> I should blog about Privoxy, everyone seems interested in privacy these days, and Privoxy does a nice job, faster then TOR).

You've got my +1 about that.

:)

---

### Post by bodhi.zazen on 2010-12-09
OK, I got a start on a privacy post / blog.

Give me a little time, you really need to tweak your browser and privoxy a bit (it is not too bad, it just will take me a little time to write).

Privoxy is slow if it is not properly "tweaked".

---

### Post by CharlesA on 2010-12-09
No hurry, Bodhi. :)

---

### Post by ldarby on 2010-12-09
Since most users don't run public services, the browser and name resolution is the primary gateway for bad guys.  if your browser is set to auto proxy, your ISP is probably spying on your browsing. if you use default DNS, they track where you go that way. Noscript plugin for firefox will knock out 98% of the dirty tricks on the web, but you still give up a lot of info every time you connect with a browser unless you are using a privacy proxy and some of those are scams. If you do get that weird pop-up, never click to close the window (the close or x in the corner may actually be a disguised OK button) so use ctrl-w or Alt-f4.  If all else fails, installing ossec-hids will at least let you know if someone does break in.

---

### Post by havtrouble on 2010-12-10
I ran the command 
sudo aa-enforce /etc/apparmor.d/*
and the results are 

> suneel@Satellite-L310:~$ sudo aa-enforce /etc/apparmor.d/*
Setting /etc/apparmor.d/gdm-guest-session to enforce mode.
Setting /etc/apparmor.d/sbin.dhclient3 to enforce mode.
Setting /etc/apparmor.d/usr.bin.evince to enforce mode.
Setting /etc/apparmor.d/usr.bin.firefox to enforce mode.
Setting /etc/apparmor.d/usr.sbin.cupsd to enforce mode.
Setting /etc/apparmor.d/usr.sbin.tcpdump to enforce mode.


Is that done correctly?

---

### Post by bodhi.zazen on 2010-12-10
> **havtrouble said:**
> I ran the command 
sudo aa-enforce /etc/apparmor.d/*
and the results are 

<clip>

Is that done correctly?

Yes. Read the apparmor sticky for further information.

---

### Post by havtrouble on 2010-12-10
I have been given so much good advice that I am going to have to take it one at a time

> I manage bad  acting web sites with a dose of NoScript + Privoxy 

I installed Noscript to my Firefox and after that I find on my banking web page that "Click here to log in" does nothing. Disabling the script on that page allows me to proceed to the log-in page. Even posting replies on this forum requires disabling the scripts on the page. Are these observations valid ? If I am going to have to disable scripts for most of the pages, how does that make my browser secure? My fear is that I may be disabling scripts out of habit even on pages where it wouldn't be safe to do so.

---

### Post by CharlesA on 2010-12-10
Yes those observations are valid. You can whitelist pages and sites.

---

### Post by ldarby on 2010-12-10
I use noscript this way. I don't whitelist very many sites. Often I can do a lot on a site without it and if I need scripts, I select the temporary option,and only for the domain I am looking at, and not "all on this page".
If you are going to get whacked by a hostile site, it is going to happen in the first few seconds, and is probably going to be a search engine link, or an email link that you clicked on.  If you land on a badguys site without noscript, you are had.  If you have noscript, your chances of being compromised is pretty close to zip.

---

### Post by bodhi.zazen on 2010-12-11
You can also temporarily allow a site (click the NoScript icon on the bottom right).

---

### Post by havtrouble on 2010-12-11
Thanks to all. The following question is another part of the security question, but I will put it in a new thread if the Moderators believe it does not belong here
I have wireless internet connection at the office through which I can connect to the internet and the intranet.  The intranet provides access to the library. The office also provides an email account, the use of which I try and limit to Office related affairs. The laptop I use is my personal one and all the files and activity I do on the laptop are my personal work and no one else's buisness. Now, 

[LIST=1]
[*] What are the chances that the office computer people know whats in my office email? ( Afterall they provided the email account)
[*]What are the chances that they can read my mail in other email accounts when I open and read them ?
[*]Is it possible for them to spy on my internet searches?
[*]Is it possible for them to see my stored files?
[/LIST]

---

### Post by OpSecShellshock on 2010-12-11
> **havtrouble said:**
> Thanks to all. The following question is another part of the security question, but I will put it in a new thread if the Moderators believe it does not belong here
I have wireless internet connection at the office through which I can connect to the internet and the intranet.  The intranet provides access to the library. The office also provides an email account, the use of which I try and limit to Office related affairs. The laptop I use is my personal one and all the files and activity I do on the laptop are my personal work and no one else's buisness. Now, 

[LIST=1]
[*] What are the chances that the office computer people know whats in my office email? ( Afterall they provided the email account)
[*]What are the chances that they can read my mail in other email accounts when I open and read them ?
[*]Is it possible for them to spy on my internet searches?
[*]Is it possible for them to see my stored files?
[/LIST]


1. Of course they can. They maintain the servers.
2. If the pages are transmitted in clear text AND they're monitoring network traffic, then it's possible for them to at least partially view the contents while the data is in transit (but only if they want to).
3. Yes, if they're inclined to.
4. Probably not. You'd have to be allowing folders to be shared out to the network.

Remember that your office's network is owned by your employer, and all activity on it is subject to their policies. It is not reasonable to expect privacy. It may also be a good idea to confirm that the connection of personally-owned equipment is allowed just to keep yourself covered.

---

### Post by havtrouble on 2010-12-11
Coming back to my recent question of ISP spying on me, my office wireless is WPA encrypted connection to which I have been given password after they collected my MAC number (whatever that is). So I am allowed to connect and use freely. But the ISP has no right to monitor me or read my mails. As far as I know the office wireless connection has no policies regarding what is allowed and what is not. What I dont like is an unscrupulous techie in between who monitors mails etc. 
Can my passwords be compromised ?

---

### Post by bodhi.zazen on 2010-12-11
That is a very paranoid viewpoint and some of it may be incorrect, depending on local laws and your activity.

With that said, what would be the motivation to do such a thing ? do you have any idea how many billions of packets an ip provider sees in an hour ?

If you do not trust "the internet" :

1. Change ip providers.

2. Use ssl (https) or http over ssh (connect to a trusted thired party server), or a VPN. Most online mail servers, gmail for example, allow you to connect over ssl.

There are many how to's on tunneling http over ssh, many people do this on untrusted wireless (public) hot spots (google search).

---

### Post by havtrouble on 2010-12-11
I agree some of it is definitely paranoid. But doesn't the concept of internet security involve a healthy dose of paranoia? Forget the local laws and crime. If my job doesn't provide what I am looking for and I am in search of another, can my current employer spy on my email accounts on account of using the office wireless internet (Oh, rest assured he will be definitely interested) and jeopardize my chances. There is no paranoia here.  My employer can fire me and I have the equal right to chuck the job. No local laws will be broken by that.
What I want to know is
Is the only solution not to use the personal laptop in the office or stop opening personal mail accounts while connected to the office internet ?

---

### Post by bodhi.zazen on 2010-12-11
> **havtrouble said:**
> Is the only solution not to use the personal laptop in the office or stop opening personal mail accounts while connected to the office internet ?

IMO, yes. Your office computer and office network is your employers property and just as you would not ask potential new employers to call you at the office, or conduct an interview in your office, do not contact them via the internet from your office.

Connecting on the office network is essentially an untrusted network and you should not expect privacy. You could increase privacy via a number of techniques (ssh, https, VPN).

---

### Post by e79 on 2010-12-11
> **HermanAB said:**
> Howdy,

Ensure that you have a proper password with at least 9 characters for ALL user accounts, then relax and enjoy your Ubuntu system.

Make it 12 characters + if you're a freak like me  ;) 

"Password length should be around 12 to 14 characters if permitted, and longer still if possible while remaining memorable"  ([http://en.wikipedia.org/wiki/Password_strength](http://en.wikipedia.org/wiki/Password_strength))

---

### Post by havtrouble on 2010-12-11
Thanks all.  
Regarding passwords I use strong  case sensitive alpha-numerical-special character password and I use virtual keyboard as well as regular keyboard to enter them on my banking site. In addition I also use the revised Vesik method to enter them ([http://www.defendingthekingdom.com/archives/vesik-method-revised](http://www.defendingthekingdom.com/archives/vesik-method-revised)). I would fool no one if I said I am not paranoid and they dont make many like me:D

Regarding https, isn't a web page is either https or not ? Nothing I can do there. What about ssh and VPN ? I have done the Wiki on them. How do I go about that? I would be grateful if you could point me to a link where they explain all this for a beginner

---

### Post by OpSecShellshock on 2010-12-11
There may be restrictions on the company's network against connecting to external VPN or SSH servers. If such restrictions exist, then those sorts of connections are likely monitored. The best possible solution is to simply not use the company's network to perform any tasks that the company would not approve of. If you have any doubts, simply don't do it. Just wait until you get home.

---

### Post by CharlesA on 2010-12-11
> **OpSecShellshock said:**
> There may be restrictions on the company's network against connecting to external VPN or SSH servers. If such restrictions exist, then those sorts of connections are likely monitored. The best possible solution is to simply not use the company's network to perform any tasks that the company would not approve of. If you have any doubts, simply don't do it. Just wait until you get home.

This. If you are doing something that you want to keep private (bank details, whatever), don't do it on a corporate network. Do it at home.

---

### Post by havtrouble on 2010-12-11
I thank you for the advice.  What about using OSSEC-HIDS and Privoxy? I have Googled them and believe I partly understand them. Does using them confer any advantage? My experience level in Ubuntu is about one on a scale of 10 (managed to install Ubuntu on my laptop without messing it up)

---

### Post by CharlesA on 2010-12-11
I'd suggest not using personal equipment at work. I don't really see the need for something that's doing HIDS (intrusion detection) on a regular laptop.

---

### Post by bodhi.zazen on 2010-12-11
> **havtrouble said:**
> I thank you for the advice.  What about using OSSEC-HIDS and Privoxy? I have Googled them and believe I partly understand them. Does using them confer any advantage? My experience level in Ubuntu is about one on a scale of 10 (managed to install Ubuntu on my laptop without messing it up)

OSSEC is overkill for the vast majority of desktop users.

Privoxy is a tool, so depends on what you want to accomplish with it. I use privoxy for privacy and adblock and highly advise it. It needs a few tweaks to improve performance and privacy, I am working on a post with detailed information.

---

### Post by bodhi.zazen on 2010-12-20
> **bodhi.zazen said:**
> On Ubuntu I use apparmor to confine all applications the are network aware.

I use a firewall on public (wireless) networks, although it is probably unnecessary to do so.

On a public network I assume my traffic is being sniffed and that anyone can read it. If I want privacy, use ssl (https) and tunnel over ssh.

I manage bad acting web sites with a dose of NoScript + Privoxy (I should blog about Privoxy, everyone seems interested in privacy these days, and Privoxy does a nice job, faster then TOR).

Just a follow note on this, see:

[http://bodhizazen.net/Tutorials/Privacy](http://bodhizazen.net/Tutorials/Privacy)

---

### Post by guilleme on 2010-12-21
There are actually also firewalls for ubuntu, and you can download them (at lest one I know, called "firestarter") from the software center.

---

### Post by CharlesA on 2010-12-21
> **guilleme said:**
> There are actually also firewalls for ubuntu, and you can download them (at lest one I know, called "firestarter") from the software center.
All those are just frontends for iptables. If you are going to use one them them, only use one, as when you have more then one frontend installed, they can cause conflicts.

---

### Post by bodhi.zazen on 2010-12-21
> **guilleme said:**
> There are actually also firewalls for ubuntu, and you can download them (at lest one I know, called "firestarter") from the software center.

As has been pointed out ...

By default there are no significant open ports, and most people are behind a router, so adding (enabling) a firewall does little to add to security for the vast majority of desktop users.

Also Firestarter is no longer maintained, use ufw or if you want a graphical front end gufw.

---

### Post by wcdrotar on 2010-12-21
Don't know if this has been suggested yet but you may still want to install NoScript on Firefox.  Annoying as hell sometimes, but at least absolutely no scripts get executed without your consent.  And then outside the browser nothing affects your system unless you install it, run it, and give it root access with your password.  

It's pretty darn secure, yes.  I've never had a single problem with internet security on Linux, and I was on Backtrack for months, which always has root access by default.  It's pretty nice not having to worry about .NET Framework updates and worry about what crap you're downloading and running.  It's a nonexistent concern on Linux.  For software just apt-get update every once in a while.  

The only way you can screw up your machine is if YOU do it, so backup often!!

---

