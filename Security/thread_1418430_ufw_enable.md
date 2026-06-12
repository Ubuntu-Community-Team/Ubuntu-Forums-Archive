---
title: "ufw enable"
date: 2010-02-28
forum: Security
---

### Post by Advait on 2010-02-28
Hi All,

My goal is to have the firewall started automatically each time I boot into Ubuntu 9.10. Here's what's happening:

I enter "sudo ufw enable" and it replies that ufw will be enabled at startup. I then reboot my system.

Right after reboot I enter "sudo ufw status" and it replies "ufw inactive". That's not what I want. I want ufw to be active automatically when I boot up. When I start gufw and hit "enable" then ufw gets active. Then I reboot again and ufw goes back to being "inactive".

How can I get ufw to be active automatically after bootup?

I installed FireStarter a few days ago. Is it interfering? Should I uninstall it? Or purge it? 

Thanks,

Tom the Uber Newbie

---

### Post by cariboo on 2010-02-28
You're mistaking a firewall front end for the actual firewall. Iptables, is basically what you want to auto-start, which is does by default. To check the firewall rules, open a terminal and type:

```
sudo iptables -L
```

If you haven't enabled the firewall rules, the output of the above command should look something like this:

```
sudo iptables -L
[sudo] password for me: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```


If you have enabled the firewall rules the output of the command would look something like this:

```
sudo iptables -L
[sudo] password for me: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
jimk@alexis-lucid:~$ sudo ufw enable
Firewall is active and enabled on system startup
jimk@alexis-lucid:~$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere
```

The output above is shortened, as it goes on for several pages.

---

### Post by OpSecShellshock on 2010-02-28
Yes, uninstall Firestarter. It may or may not be interfering, but either way it is no longer supported.

As far as having the firewall start when the computer does, that always happens (in default configurations). The effective part (as far as playing the role of denying and allowing) is iptables, not ufw. What ufw and gufw do is allow users to interact with the rules in iptables more intuitively. I think the reason you're seeing what you see (ufw showing inactive until you start gufw, at which point it shows active) is because you aren't using ufw to configure iptables. Once you start up gufw, you have a session going, so it will show that it's active (meaning it's ready to make changes if you want it to). I guess the main thing to know is that it's iptables that you want to have running at startup, and it already is.

---

### Post by bodhi.zazen on 2010-02-28
> **Advait said:**
> I installed FireStarter a few days ago. Is it interfering?

Yes, that is the problem.

> Should I uninstall it? Or purge it? 

Thanks,

Tom the Uber Newbie

You need to purge firestarter.

If you already removed it, reinstall it and then purge it.

---

### Post by Advait on 2010-02-28
OK, I purged FireStarter. Thanks for the info. My understanding now is that iptables is ON by default and blocking all unsolicited incoming traffic. Good! I'm happy that I don't need to turn it on manually.

I'm using Ubuntu in a very simple, default setup so I'm guessing that I have no services running that would accept unsolicited traffic.

My understanding is that all outbound traffic is allowed.

I'm also guessing that because I have a very simple, default Ubuntu configuration, I have no need to set up any firewall rules. Let me know if this is not the case.

Thanks,

Tom

After 1 week I'm spending 90% of my time in Ubuntu. Love it!

---

