---
title: "Who has logged in to my remote desktop? [ubuntu]"
date: 2012-01-22
forum: Security
---

### Post by sinnadyr on 2012-01-22
Yesterday some unknown IP suddenly logged in (twice) to my computer which I use as a mediacenter, and I think a script was executed but didn't work as it should since I had xbmc running.
Does anyone have an idea where I might find the list of IP's who has logged in to my remote desktop?

Running Ubuntu 9.10. 


Thank you very much in advance!

---

### Post by BC59 on 2012-01-22
The only I know is that is dangerous to use such an old version, without support anymore. There is a big reason to use the latest versions of every OS.

---

### Post by shymega on 2012-01-22
Hi,

Ubuntu 9.10 is no longer supported and I recommend that you upgrade to Ubuntu 10.04 LTS. 

To find out who logged in on the Remote Desktop, you may want to try this: last -t 20120121HHMMSS. (Replacing HH, MM, SS with Hours, Minutes and Seconds of time that the intruder logged in at). 

You may also want to check your router's logs to see if anyone logged in via there as well.

--
sm

---

### Post by collisionystm on 2012-01-22
> **sinnadyr said:**
> Yesterday some unknown IP suddenly logged in (twice) to my computer which I use as a mediacenter, and I think a script was executed but didn't work as it should since I had xbmc running.
Does anyone have an idea where I might find the list of IP's who has logged in to my remote desktop?

Running Ubuntu 9.10. 


Thank you very much in advance!


check

/var/log/auth.log

and others in /var/log

---

### Post by Lars Noodén on 2012-01-22
You can use [last](http://manpages.ubuntu.com/manpages/oneiric/en/man1/last.1.html)

```

last  -a | grep pts | less

``` 

Also 9.04 was supported only until October 2010.  You might give serious consideration to upgrading.  If you do not want to upgrade too often then you might use the upcoming LTS release, Precise Pangolin.  It will be released in April, but it is already quite usable.

---

### Post by sinnadyr on 2012-01-22
But my XBMC works so well so I don't wanna configure it all over again. 
Anyway, my log in /var/log/auth.log.1 says

Jan 21 13:50:37 mediacenter sshd[32624]: Failed password for bin from 184.107.179.242 port 39850 ssh2
Jan 21 13:50:44 mediacenter sshd[32638]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=184.107.179.242  user=bin
Jan 21 13:50:46 mediacenter sshd[32638]: Failed password for bin from 184.107.179.242 port 33878 ssh2
Jan 21 13:50:52 mediacenter sshd[32652]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=184.107.179.242  user=bin
Jan 21 13:50:54 mediacenter sshd[32652]: Failed password for bin from 184.107.179.242 port 38258 ssh2

and 50 more of the same. 

What could this be?

---

### Post by shymega on 2012-01-22
Now, that's interesting. One, because the remote host seems to be logging into your 'bin' user. It's not really used for remote logins. 

The IP Address in that log you posted seems to have been involved in a lot of attacks: [http://www.blocklist.de/en/view.html?ip=184.107.179.242](http://www.blocklist.de/en/view.html?ip=184.107.179.242)

If you have a firewall/router, could you provide the firewall logs?

--
sm

---

### Post by Lars Noodén on 2012-01-22
That's someone hammering on your ssh server trying to guess usernames and passwords.  You can kick them out if they try too many times using IP Tables:

```

   ip6tables -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT
   iptables  -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT

```

---

### Post by sinnadyr on 2012-01-22
> **Lars Noodén said:**
> That's someone hammering on your ssh server trying to guess usernames and passwords.  You can kick them out if they try too many times using IP Tables:

```

   ip6tables -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT
   iptables  -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT

```
But how come this user suddenly logged in to my remote desktop? And I can't seem to find the log over remote desktop connections.

---

### Post by shymega on 2012-01-22
Do you have a firewall restricting access to your network?

--
sm

---

### Post by Lars Noodén on 2012-01-22
> **sinnadyr said:**
> But how come this user suddenly logged in to my remote desktop? And I can't seem to find the log over remote desktop connections.

You're fine.  They're not logged in.  The attempts are failing:

```

Jan 21 13:50:37 mediacenter sshd[32624]: **Failed** password for bin from 184.107.179.242 port 39850 ssh2
Jan 21 13:50:44 mediacenter sshd[32638]: pam_unix(sshd:auth): authentication **failure**; logname= uid=0 euid=0 tty=ssh ruser= rhost=184.107.179.242 user=bin

```

They're trying to get in via SSH not the remote desktop.

---

### Post by Dangertux on 2012-01-22
> **Lars Noodén said:**
> You're fine.  They're not logged in.  The attempts are failing:

```

Jan 21 13:50:37 mediacenter sshd[32624]: **Failed** password for bin from 184.107.179.242 port 39850 ssh2
Jan 21 13:50:44 mediacenter sshd[32638]: pam_unix(sshd:auth): authentication **failure**; logname= uid=0 euid=0 tty=ssh ruser= rhost=184.107.179.242 user=bin

```They're trying to get in via SSH not the remote desktop.

Well...We can't really confirm they're not doing both can we? 

Obviously the OP's SSH is being bruteforced as has been already addressed, however is VNC available to the internet or only locally?

---

### Post by Lars Noodén on 2012-01-22
Good point, I hadn't expected anything other than a tunneled remote desktop.

@sinnadyr what kind of remote desktop have you enabled and are you tunneling it over SSH?

---

### Post by CharlesA on 2012-01-22
> **Lars Noodén said:**
> Good point, I hadn't expected anything other than a tunneled remote desktop.

@sinnadyr what kind of remote desktop have you enabled and are you tunneling it over SSH?
That was my first thought when I saw the log.

I am hoping that VNC isn't being exposed to the internet as the default vino server does not keep any logs last time I checked.

---

### Post by sinnadyr on 2012-01-22
I have activated the native remote desktop sollution in Ubuntu, nothing else, and it says it is not connectible from the internet, even though I am able to.

Simple SSH server is set up, no tunneling to remote desktop. 

But seriously, the remote desktop was connected to from another, unknown computer, since I am watching my movies and suddenly "another user is controlling your computer"  pops up and windows are changing, movie is stopped and appearently a lot of keys is sent to my computer. 

I don't have any specific firewall set up, only running standard DD-WRT on my router.

---

### Post by Lars Noodén on 2012-01-22
Ok.  The first thing is to disable and remove the remote desktop sharing.

---

### Post by CharlesA on 2012-01-22
> **Lars Noodén said:**
> Ok.  The first thing is to disable and remove the remote desktop sharing.
+1. I would reinstall tbh, once a machine has been cracked there is little you can do to make sure you have cleaned it up completely.

---

### Post by sinnadyr on 2012-01-22
> **Lars Noodén said:**
> Ok.  The first thing is to disable and remove the remote desktop sharing.
Of course, won't use it until the case is cleared, so to speak :)

---

### Post by sinnadyr on 2012-01-22
> **CharlesA said:**
> +1. I would reinstall tbh, once a machine has been cracked there is little you can do to make sure you have cleaned it up completely.
Thats true... Damn it

---

### Post by CharlesA on 2012-01-22
> **sinnadyr said:**
> Thats true... Damn it
Back everything up and reinstall. I would suggest installing either 10.04, or 12.04, even though 12.04 won't be released for another 3 months, it is quite stable from what I have heard.

---

### Post by sinnadyr on 2012-01-22
> **CharlesA said:**
> Back everything up and reinstall. I would suggest installing either 10.04, or 12.04, even though 12.04 won't be released for another 3 months, it is quite stable from what I have heard.
Well, a little bit off topic, but is xbmc stable for 12.04? I am only using this box for xbmc and had a lot of struggle getting it up and running, and haven't touch it since. That is two years ago now, so you could say I am paranoid about loosing my xbmc for a couple of days :P

---

### Post by CharlesA on 2012-01-22
> **sinnadyr said:**
> Well, a little bit off topic, but is xbmc stable for 12.04? I am only using this box for xbmc and had a lot of struggle getting it up and running, and haven't touch it since. That is two years ago now, so you could say I am paranoid about loosing my xbmc for a couple of days :P
I don't use it, but a quick google found this:
[http://www.noobslab.com/2011/12/install-xbmc-on-ubuntu-1204-precise.html](http://www.noobslab.com/2011/12/install-xbmc-on-ubuntu-1204-precise.html)

---

### Post by TheFu on 2012-01-23
Dude - check out** fail2ban **and please, please, please move your sshd to any other port but 22 from the outside world. You don't need to change it on the server, just in the router.

Using something like 50022 on your WAN side and redirect that to 22 internally.

Also, all the folks telling you to update are doing you a favor. The newer versions of XBMC are really nice and the setup/config is pretty painless these days.

A little blog post on more secure ssh connections: [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

If you are allowing VNC from the outside world, **that's a really bad idea****.** It is not secure.  You can VNC through an SSH tunnel if you need to, or look into using FreeNX server and any NX client when you are remote. It is more bandwidth efficient than VNC AND includes ssh tunneling in the protocol.

---

### Post by CharlesA on 2012-01-23
Having ssh listening on port 22 is fine as long as you secure it properly and use a strong password.

DenyHosts or Fail2ban are good, but you can use iptables to accomplish the same thing. ;)

---

### Post by sinnadyr on 2012-01-24
Thank you all! This is really appreciated. Will make sure to upgrade my computer and play a bit more secure in the future. 

Thank you!

---

