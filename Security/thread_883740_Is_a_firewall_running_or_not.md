---
title: "Is a firewall running or not?"
date: 2008-08-08
forum: Security
---

### Post by ihatetryingtopickaloginna on 2008-08-08
I have been using firestarter in 8.04, since it was the only one I knew about and it does come packaged with the distro. Moving the mouse over it's icon shows the firewall is running. Now I hear that it is no longer supported and to use ufw.

But now when I type ufw status, it says the firewall isn't enabled. And after I enabled it, ufw says that it is enabled on system startup. After rebooting and querying ufw again, it says that the firewall isn't enabled. But firestarter shows it is running and occasionally even shows hits from websites that it is blocking.

Something ain't right here. I know that neither of these is the firewall and that the firewall is iptables, but if ufw is now preferred over firestarter then why doesn't it know the firewall is actually running.

---

### Post by HermanAB on 2008-08-08
Firestarter is just a configuration GUI for the Netfilter.  Netfilter is a kernel module and is always running.  Once Netfilter is configured with Firestarter, you don't need to run Firestarter anymore.  

Firestarter does tend to crash for no good reason, but it is a nice utility nevertheless and its crashing doesn't matter, so that is why it remains popular.

Cheers,

Herman

---

### Post by ihatetryingtopickaloginna on 2008-08-11
Okay, but I just want to know that the firewall is running. UFW says it isn't when I query it, but firestarter may be showing blocked hits at the same time. I can always run iptables -L and see that way, so might just do that.

---

### Post by tuxxy on 2008-08-11
```
sudo ufw status
```

to enable the firewall try

```
ufw enable

```

---

### Post by ihatetryingtopickaloginna on 2008-08-11
Everytime I've issued these commands, ufw reports that it isn't enabled. I take that to mean that the firewall isn't running. So when I enable ufw, it says 'Firewall started and enabled on system startup'.

But after rebooting and checking ufw again, it reports the firewall to not be enabled. Now if I run firestarter, it shows the firewall to be running and will occasionally show sites being blocked. Is there a difference in 'enabled' and 'running'? Maybe I'm just getting the words confused.

---

### Post by hyper_ch on 2008-08-11
do you actually need to run a firewall? In most cases you don't.

---

### Post by ihatetryingtopickaloginna on 2008-08-11
When I ran OS/2 Warp there was no need. After downgrading to XP, I had to turn off notifications in ZoneAlarm and later Comodo cause it was so distracting seeing all the ip addresses that were trying to break in. I would rather have the peace of mind knowing that one is running, and I now like to see when there is a hit since there are so few. It just seems strange not to get more breakin attempts with Linux getting so popular.

I really just want to know that it is running and why two configuration programs aren't agreeing that it either is or isn't. Like right now I just checked ufw and it says the firewall isn't enabled. About three hours ago, before I got up and walked away, it reported that it was enabled. Firestarter shows it to always be running and shows a hit if I get one. I think I'll just continue using firestarter and forget ufw.

---

### Post by jimv on 2008-08-11
They're not the same program/firewall, so they won't show the same status.  Just disable UFW and use Firestarter.

---

### Post by ihatetryingtopickaloginna on 2008-08-11
Isn't the firewall called iptables? And these two programs just used to configure iptables?

---

### Post by The Cog on 2008-08-11
The real proof of what the firewall is doing is to run the command
> sudo iptables -nvL
and see if any rules are listed under the three headings. All firewall front-ends end up setting iptables rules. If you're not sure the firewall front-end is telling you the truth, go underneath to the real firewall.

---

### Post by BugBuster on 2008-08-13
> **ihatetryingtopickaloginna said:**
> Everytime I've issued these commands, ufw reports that it isn't enabled. I take that to mean that the firewall isn't running. So when I enable ufw, it says 'Firewall started and enabled on system startup'.

But after rebooting and checking ufw again, it reports the firewall to not be enabled. Now if I run firestarter, it shows the firewall to be running and will occasionally show sites being blocked. Is there a difference in 'enabled' and 'running'? Maybe I'm just getting the words confused.

I had the same issue as well..ie when i had configured Firestarter on Ubuntu 8.04, Ufw did not work(atleast did not seem to).

Everytime I enabled ufw using <sudo ufw enable> it would say 'Firewall started and enabled on system startup' however after reboot it would not.

So I uninstalled Firestarter and then issued sudo ufw enable again..this time it worked like a charm..I could add/delete rules..and the rules were followed..

So from my personal experience I can say that as Firestarter and Ufw are gui's to the same iptables..and maybe iptables cannot take commands(rules) from both Firestarter and UFW simultaneously..

So in order to have ufw working remove firestarter and then issue the command : sudo ufw enable

It should work...

---

### Post by Nepherte on 2008-08-13
> **BugBuster said:**
> I had the same issue as well..ie when i had configured Firestarter on Ubuntu 8.04, Ufw did not work(atleast did not seem to).

Everytime I enabled ufw using <sudo ufw enable> it would say 'Firewall started and enabled on system startup' however after reboot it would not.

So I uninstalled Firestarter and then issued sudo ufw enable again..this time it worked like a charm..I could add/delete rules..and the rules were followed..

[..]

So in order to have ufw working remove firestarter and then issue the command : sudo ufw enable

It should work...
I never had firestarter installed, but ufw enable never worked after rebooting my system. I'm not sure if the rules created with ufw were loaded after startup though, I never bothered to check (iptables -L). If you really want it to be enabled on startup, just add /etc/init.d/ufw restart to your /etc/local.conf file.

---

### Post by hyper_ch on 2008-08-14
> **Nepherte said:**
> I never had firestarter installed, but ufw enable never worked after rebooting my system. I'm not sure if the rules created with ufw were loaded after startup though, I never bothered to check (iptables -L). If you really want it to be enabled on startup, just add /etc/init.d/ufw restart to your /etc/local.conf file.

If the rules are added to iptables why would you want to enable ufw at startup anyway?

---

### Post by Nepherte on 2008-08-14
> **hyper_ch said:**
> If the rules are added to iptables why would you want to enable ufw at startup anyway?
I believe the rules are added, but I wasn't sure. Anyways, I don't bother to enable ufw on startup. I'm just saying it is possible if he feels more comfortable with it.

---

### Post by ihatetryingtopickaloginna on 2008-08-14
Ufw doesn't say that ufw is enabled at startup, it says the firewall is. But it always reports the firewall as not enabled if ufw is queried after startup. If firestarter is running it will show that the firewall is also.

---

