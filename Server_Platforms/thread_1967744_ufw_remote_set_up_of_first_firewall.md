---
title: "ufw: remote set up of first firewall"
date: 2012-04-28
forum: Server Platforms
---

### Post by AugustinMa on 2012-04-28
I am learning to set up my very first firewall remotely over SSH.

Since ufw is the default firewall front end with ubuntu, that's what I am learning to use. As I go along, I am trying to document the process:
[http://linux.overshoot.tv/wiki/server/ufw_uncomplicated_firewall](http://linux.overshoot.tv/wiki/server/ufw_uncomplicated_firewall)

Despite all the existing documentation I found on the web, I already have a question. Two, actually.

1) If one accidentally locks himself out and cannot reconnect to the remote server via SSH, what is the 'normal' process to recover control of the server?

2) In the wiki page linked above, I tried to document a method that I thought would allow a new sysadmin to test the new firewall without getting locked up. However, when I look at the iptables rules, I don't get the result I expected:
On a new system, there are absolutely no rules:
```
# iptables -L -n -v
Chain INPUT (policy ACCEPT 2793K packets, 569M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 1768K packets, 5488M bytes)
 pkts bytes target     prot opt in     out     source               destination   
```

Enable ufw:
```
ufw enable
```

then check the output of iptables again (same command as above): this time we have a loooooong list of rules, those enabled by default by ufw.

Disable ufw:
```
 ufw disable 
```

I kind of expected at this time for the iptable rules to be back to the empty set we had at the beginning. However, we still have all the rules that were added when we first enabled ufw.

What does this imply? Do those rules apply? Is there an effective firewall?
Is my logic somehow faulty in the 'Setting up your first firewall' section of the wiki here:
[http://linux.overshoot.tv/wiki/server/ufw_uncomplicated_firewall](http://linux.overshoot.tv/wiki/server/ufw_uncomplicated_firewall) 
??

Thank you for any insight that you can provide.

---

### Post by AugustinMa on 2012-04-29
I guess what I am asking is: if I disable ufw, how can I be sure that no firewall is running?

---

### Post by AugustinMa on 2012-05-01
This is all so confusing to me... :-/

---

### Post by darkod on 2012-05-01
I think there are no rules active after you disable ufw. The iptables command might still list them because I think the rules are reloaded the next time you enable ufw.

Recently I used ufw for the first time too, but later found out that using iptables directly seemed a better choice. Tutorials that you find about iptables might look complicated but you also need to look out for the dates. In time, controlling iptables has gotten easier, so older tutorials might look frightening to a beginner.

Are you getting stuck with ufw at some exact point or just asking in general?

---

### Post by AugustinMa on 2012-05-02
> **darkod said:**
> I think there are no rules active after you disable ufw. The iptables command might still list them because I think the rules are reloaded the next time you enable ufw.

Recently I used ufw for the first time too, but later found out that using iptables directly seemed a better choice. Tutorials that you find about iptables might look complicated but you also need to look out for the dates. In time, controlling iptables has gotten easier, so older tutorials might look frightening to a beginner.

Are you getting stuck with ufw at some exact point or just asking in general?


Thank you Darkod for your reply.

I am asking because I urgently need to set up a firewall, the first time I do so remotely, and I like to understand what I am doing before I do it. I don't want to be logged out.

Also, I like to document things as I go along, provide answers that I myself was having during my own learning process. Thus, it is not enough for me to get an answer in a forum and get the job done, I also want to write something that can help future newbies who may encounter the very same problem.

I had started writing the following tutorials using iptables:
[http://linux.overshoot.tv/wiki/server/setting_your_first_firewall_ssh](http://linux.overshoot.tv/wiki/server/setting_your_first_firewall_ssh) 
But when I enabled ufw, I noticed all those intimidating rules that are enabled by default. So I was thinking that the people who created ufw are more knowledgeable than me and created all those rules for a reasons. Thus I gave up the iptables route and concentrated on ufw.

I then started the following tutorial (already mentioned above):
[http://linux.overshoot.tv/wiki/server/ufw_uncomplicated_firewall](http://linux.overshoot.tv/wiki/server/ufw_uncomplicated_firewall)
but got stuck at the point where I asked the questions above.

And I still haven't got a firewall yet, because I am still trying to understand the logic.

If iptables rules do not by themselves constitute a firewall, how do we know whether any firewall is running or not?

---

### Post by darkod on 2012-05-02
This is one of my threads but it has other questions about ufw first. The questions about iptables and examples how to do it are towards page 3 and later.
[http://ubuntuforums.org/showthread.php?t=1947308](http://ubuntuforums.org/showthread.php?t=1947308)

The way I understand it, and I might be wrong, is that iptables rules do constitute a firewall but it's not working when ufw is disabled. Somehow.

Is this firewall intended to protect this machine, or another one?

If you need it to protect this machine, regardless whether you use iptables directly or ufw, you better configure the INPUT and FORWARD chains to DROP, and the OUTPUT to ACCEPT. Then you can only open what you need.

But doing everything remotely is a bit complicated. Before setting INPUT to DROP you have to make sure you configure rule(s) to let you access by SSH. If you lock yourself out I don't see another way except someone physically logging into the machine and disabling your firewall to let you in.

I did my firewall with ufw, but if I knew what I know now, I would have done it with iptables and the setup in /etc/network/interfaces as discussed in my thread I linked above.

The main thing I don't like about ufw, and I realized too late, is that if you have a syntax error in a rule in /etc/ufw/before.rules for example, it will not apply any of the rules in the file. That way it can lock you out if it doesn't apply the rule letting you in.

What I also noticed is that ufw is not always flushing iptables correctly. So, when you do ufw disable && ufw enable, it can create double entries with time.

Using a file with your iptables rules and doing the iptables-restore procedure is better I think. Even if you have syntax error in one rule, it just ignores that one. Unless I am wrong. I can't test now. Maybe later in vitrual box.

---

### Post by haqking on 2012-05-02
see here for instructions on setting up a firewall in Ubuntu.

[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

**IPTables is the firewall** regardless of what front end you use, UFW/GUFW etc are merely configuration front ends to manipulate IPTables rules.

Also if you lock yourself out from a remote connection then the only method of cirumventing that is to visit the machine physically ;)

Peace

---

### Post by darkod on 2012-05-02
For example, a simple way to activate iptables is to create a file /etc/iptables.rules for example. Note that you need to create it with sudo, for example if using nano editor:
sudo nano /etc/iptables.rules

The content might be:
```

*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]

-A INPUT -p tcp --dport 22 -j ACCEPT

COMMIT
```

That will configure a DROP in both INPUT and FORWARD chains, and ACCEPT in the OUTPUT chain which is sort of a default config. It will also add a rule to allow SSH connections on port 22 to prevent you locking yourself when activating the rules.

Change the port if you use different port for SSH. You can also limit it to accept SSH connections only from specific IP address (if you have a static public IP in your home/office and you want to prevent anyone trying to break into your server). And they will try, especially if you leave the port as 22. In that case the modified line would be like:
-A INPUT -p tcp -s <public IP> --dport 22 -j ACCEPT

You can activate the rules you saved in /etc/iptables.rules by:
sudo iptables-restore < /etc/iptables.rules

You can add a command to do this automatically at boot as it was discussed in the thread I linked earlier. Note that this way the rules are always flushed and only the rules specified in your file are activated. Also the counters are reset. If you want the counters to be saved and to continue counting, I think you need to add -c to the iptables-restore.

---

