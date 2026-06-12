---
title: "Headless or Desktop version for server ?"
date: 2012-05-31
forum: Server Platforms
---

### Post by starz677 on 2012-05-31
Hi,  It's time for me to rebuild my server from scratch.  I'm used to the Graphical Desktop version so the headless version is a bit daunting.  Anyway...HERE is the question.....  Is the headless version so much more secure that it's worth giving up all the graphical interfaces?  Or should I just go back with the Desktop version again and try to be more careful?  (I got haxed).  thx

---

### Post by arrrghhh on 2012-05-31
I guess it depends on how you were "haxed".  If you're lax about security on the Server Edition, you can easily get "haxed".

Both versions of Ubuntu ship with about the same level of security - no open ports, no running services, etc.

However, as soon as you start installing services they open ports automatically.  So you'll definitely want to run a simple software firewall to ensure you are only opening what you expect to open.  Hardware firewalls are also a good idea - I wouldn't put the server directly on the internet unless I had no other choice.  Then I'd probably run smoothwall or something more powerful than a basic software firewall.

So please, elaborate on how you were "haxed" and we can perhaps help nudge you in the right direction on how to properly secure your system.  Both the Desktop and Server editions can be secured in similar manners.  The Server Edition is perhaps more secure because it doesn't have a GUI (less packages to update, break; fewer attack vectors...) but in reality the security differences between the two platforms are pretty minimal.

To sum up - if you aren't careful with security, you can just as easily be hacked on the Server Edition as you can on the Desktop Edition.  Neither edition is 'hack-proof'.

---

### Post by pctx on 2012-05-31
First off,  

What, who and how were you "haxed"?

Secondly,
A headless server is recommended pretty much 10 times out of 10 in the linux world as most of the common exploits are in video drivers or "x session" forwards.  

2 years ago I asked the same question and I went headless and hacked away at the terminal and found that navigating command line in the terminal was 90% easier than using a UI for doing my tasks.  In the *nix world (aside from Windows server), a UI really is seen as a crutch.

The last thing I say is you should have a good knowledge of IP Tables, Shorewall or UFW before you just throw up your next server so you know exactly what is going in or out of your server at all times.

---

### Post by starz677 on 2012-05-31
I think I was acceptably careful and vigilant EXCEPT for ONE thing....UPDATES.

I have to admit I was very bad with doing updates and I'm thinking there's a high probability they got me that way.  Sometimes I would go months between updates.  Going forward, I'll turn on automatic updates.

Or..I installed a package that left the door open.   I run a Watchguard Firebox in front of the server and it's tightened down pretty tight also.

My security consisted of [COLOR=Red]**ipblock**[/COLOR] (with a custom list of thousands of sites including all major proxies and hundreds of lesser known proxies.  I also have a paid subscription that sends me about 150 newly discovered proxies daily and I add those daily.)
I also block all countries except for Canada and Australia because there is nothing on my server relevant to other countries.

[COLOR=Red]**fail2ban**[/COLOR] with all the usual filters plus a few.

A [COLOR=Red]**Watchguard Firebox hardware firewall**[/COLOR] that perma-blocks any attempt to connect to ANY port other than 80 or 443 instantly. plus provides the normal hardware firewall security such as packet filtering, spoofing detection, icmp attacks, MIM attacks and a host of other tricks.
[COLOR=Red][B]
Firestarter[/B][/COLOR] set to block ALL outgoing packets.

So, however they did it, they did it via port 443 or 80.

For a long time here I had posted that my server was acting suspiciously but noone here believed it.  Finally I got proof in the form of a obviously edited fail2ban jail.conf file where the haxor added an IP address to all the filters to exempt attacks from that IP address.

---

### Post by CharlesA on 2012-05-31
Their thread on the "haxing" is here:
[http://ubuntuforums.org/showthread.php?t=1989899](http://ubuntuforums.org/showthread.php?t=1989899)

Headless server > GUI on a server for more than that just security.

Less packages = less attack surface and not having a GUI means you need less resources to run the box.

---

### Post by pctx on 2012-05-31
> **starz677 said:**
> I think I was acceptably careful and vigilant EXCEPT for ONE thing....UPDATES.

I have to admit I was very bad with doing updates and I'm thinking there's a high probability they got me that way.  Sometimes I would go months between updates.  Going forward, I'll turn on automatic updates.

Or..I installed a package that left the door open.   I run a Watchguard Firebox in front of the server and it's tightened down pretty tight also.

My security consisted of [COLOR=Red]**ipblock**[/COLOR] (with a custom list of thousands of sites including all major proxies and hundreds of lesser known proxies.  I also have a paid subscription that sends me about 150 newly discovered proxies daily and I add those daily.)
I also block all countries except for Canada and Australia because there is nothing on my server relevant to other countries.

[COLOR=Red]**fail2ban**[/COLOR] with all the usual filters plus a few.

A [COLOR=Red]**Watchguard Firebox hardware firewall**[/COLOR] that perma-blocks any attempt to connect to ANY port other than 80 or 443 instantly. plus provides the normal hardware firewall security such as packet filtering, spoofing detection, icmp attacks, MIM attacks and a host of other tricks.
[COLOR=Red][B]
Firestarter[/B][/COLOR] set to block ALL outgoing packets.

So, however they did it, they did it via port 443 or 80.

For a long time here I had posted that my server was acting suspiciously but noone here believed it.  Finally I got proof in the form of a obviously edited fail2ban jail.conf file where the haxor added an IP address to all the filters to exempt attacks from that IP address.

I can help you with that.

Do this: (open up a terminal and run sudo nano, past in the code below)[FONT=&quot]
[/FONT]```
#!/bin/bash  
  # A script to run Aptitude and install any upgrades automatically. 
  # Add this to /etc/cron.daily to run the script every 24 hours. 
  
  # This prevents "TERM is not set, so the dialog frontend is not usable." error
  PATH="$PATH:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin"
  
  aptitude update
  aptitude safe-upgrade -y
  aptitude autoclean

```  [FONT=&quot][SIZE=3]Once completed hit ctrl+x to exit and save changes.  Save the file as: autoupdate.sh[/SIZE][/FONT]
  
  [FONT=&quot][SIZE=3]Do a ls -al to see your newly created file and permissions:[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]-rw-r--r-- 1 root     root      361 2011-09-22 09:08 autoupdate.sh[/SIZE][/FONT][SIZE=3]

[/SIZE]      [FONT=&quot][SIZE=3]You'll notice that this is not executable by default.  In order for CRON to use this, we must make it executable for the Root user.[/SIZE][/FONT][SIZE=3]

[/SIZE]      [FONT=&quot][SIZE=3]*NOTE* - If the bash script does not list (root | root) as it does in the ls -al command below run the following command:[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]sudo chown root:root autoupdate.sh[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]This changes group and user ownership to the Root group and Root user.  By default, Root (Group and User) should own this bash script.[/SIZE][/FONT][SIZE=3]

[/SIZE]      [FONT=&quot][SIZE=3]Type: sudo chmod +x autoupdate.sh[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]Run another command of: ls -al[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]-rwxr-xr-x 1 root     root      361 2011-09-22 09:08 autoupdate.sh[/SIZE][/FONT][SIZE=3]

[/SIZE]      [FONT=&quot][SIZE=3]Notice--- Permissions have been updated.[/SIZE][/FONT][SIZE=3]

[/SIZE]      [FONT=&quot][SIZE=3]Lastly, we move the bash script to the CRON folder(s).  [/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]sudo mv autoupdate.sh /etc/cron.daily[/SIZE][/FONT][SIZE=3]

[/SIZE]      [FONT=&quot][SIZE=3]Want to check the logs to make sure that this is running?  Run this command:[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]sudo tail -n 30 /var/log/aptitude (Adjust the #30 by the number of lines you'd like to see listed on the tail)[/SIZE][/FONT][SIZE=3]

[/SIZE]      [FONT=&quot][SIZE=3]Example of this:[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]===============================================================================[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3][UPGRADE] apt 0.7.25.3ubuntu9.5 -> 0.7.25.3ubuntu9.6[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3][UPGRADE] apt-transport-https 0.7.25.3ubuntu9.5 -> 0.7.25.3ubuntu9.6[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3][UPGRADE] apt-utils 0.7.25.3ubuntu9.5 -> 0.7.25.3ubuntu9.6[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3][UPGRADE] landscape-common 11.02-0ubuntu0.10.04.1 -> 11.07.1.1-0ubuntu0.10.04.0[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3][UPGRADE] linux-headers-2.6.32-33 2.6.32-33.70 -> 2.6.32-33.72[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3][UPGRADE] linux-headers-2.6.32-33-server 2.6.32-33.70 -> 2.6.32-33.72[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3][UPGRADE] linux-image-2.6.32-33-server 2.6.32-33.70 -> 2.6.32-33.72[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3][UPGRADE] python-apt 0.7.94.2ubuntu6.2 -> 0.7.94.2ubuntu6.4[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3][UPGRADE] tzdata 2011g-0ubuntu0.10.04 -> 2011j-0ubuntu0.10.04[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]===============================================================================[/SIZE][/FONT][SIZE=3]


[/SIZE]         [FONT=&quot][SIZE=3]To check for a specific package update for aptitude:[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]sudo cat /var/log/aptitude | grep -A 20 -B 20 php5 (this looks for the php5 package update).[/SIZE][/FONT][SIZE=3]
[/SIZE][FONT=&quot][SIZE=3].
All of my web servers run the unattended package update and I check the logs regularly.  Hope that gives you some confidence in them getting patched automatically if you use a GUI based server. :)
[/SIZE][/FONT]

---

### Post by starz677 on 2012-05-31
Super pctx  :p

will do this

---

### Post by starz677 on 2012-05-31
> **CharlesA said:**
> Their thread on the "haxing" is here:
[http://ubuntuforums.org/showthread.php?t=1989899](http://ubuntuforums.org/showthread.php?t=1989899)

Headless server > GUI on a server for more than that just security.

Less packages = less attack surface and not having a GUI means you need less resources to run the box.

With a Desktop server, I like to sometimes glance at the ipblocks that have occurred so I can get a feel for who's trying to get on the server and the frequency.   I also sometimes use Etherape to see certain things.

I'm so used to having all those graphical tools that NOT having them will seem like driving a car blindfolded.  How do you guys get a "Real Time" feel for what;s going on in terms of intrusions with a headless server?

---

### Post by CharlesA on 2012-05-31
> **pctx said:**
> I can help you with that.

It would be easier to just use the unattended-upgrades package.

> **starz677 said:**
> With a Desktop server, I like to sometimes glance at the ipblocks that have occurred so I can get a feel for who's trying to get on the server and the frequency.   I also sometimes use Etherape to see certain things.

I'm so used to having all those graphical tools that NOT having them will seem like driving a car blindfolded.  How do you guys get a "Real Time" feel for what;s going on in terms of intrusions with a headless server?

```
tail /var/log/auth.log
```

Or:

```
grep sshd /var/log/auth.log | less
```

---

### Post by pctx on 2012-05-31
> **CharlesA said:**
> It would be easier to just use the unattended-upgrades package.



```
tail /var/log/auth.log
```Or:

```
grep sshd /var/log/auth.log | less
```

I agree and I do.  I updated my post to reflect that this was on the assumption that he was going to use a GUI based server again.

---

### Post by CharlesA on 2012-05-31
> **pctx said:**
> I agree and I do.  I updated my post to reflect that this was on the assumption that he was going to use a GUI based server again.
I use unattended-upgrades on my web development box so I don't have to worry about updates. ;)

---

### Post by pctx on 2012-05-31
> **CharlesA said:**
> I use unattended-upgrades on my web development box so I don't have to worry about updates. ;)
Again true, but my whole point of posting that was to trojan horse him getting used to the terminal. ;)

---

### Post by CharlesA on 2012-05-31
> **pctx said:**
> Again true, but my whole point of posting that was to trojan horse him getting used to the terminal. ;)
D'oh! Almost worked!

---

### Post by arrrghhh on 2012-05-31
> **pctx said:**
> again true, but my whole point of posting that was to trojan horse him getting used to the terminal. ;)

lmao!

=D>

---

