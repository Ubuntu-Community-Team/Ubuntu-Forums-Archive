---
title: "How can I reject specific IPs from strings in FAIL2BAN v0.9 ?"
date: 2020-12-16
forum: Security
---

### Post by mikecolley on 2020-12-16
Hi and thanks in advance for your help.

How do I configure fail2ban v 0.9.0 to jail specific IPs based on strings for example these strings/IPs:

     ----- Invalid user admin from 185.117.215.9 port 48052

----- Failed password for root from 82.221.131.5 port 43278 ssh2

----- Unable to negotiate with 112.85.42.151 port 9898: no matching key exchange method found. Their offer: diffie ...

I'm new to fail2ban and I'm afraid I'm asking a question that  doesn't have a simple answer.  I am a 15 year linux user. Step by painful step directions works good for me.  I hope I am asking for the correct advice.  I just use SSH, I don't know how it works.

Background:
I put Ubuntu 20.04 server on a core2duo laptop and it receives mail and serves web pages connected to the internet just fine.  It was even easy to install, GREAT!  No apache so far.

I  did a ```
tail -f /var/log/auth.log
``` and was horrified at all  the unauthorized login attempts.  So I installed fail2ban (v 0.9) from the distribution, helped a lot but,  but, but,
I still have a lot of authentication failures, a lot of  them.  I've been reading the fail2ban docs and well, it ain't easy, it  ain't even hard, fail2ban documentation is very very difficult.

```
user1@srvr1:/etc/fail2ban/filter.d# fail2ban-client status sshd
Status for the jail: sshd
|- Filter
|  |- Currently failed:    0
|  |- Total failed:    2383
|  `- File list:    /var/log/auth.log
`- Actions
   |- Currently banned:    36
   |- Total banned:    1259
   `- Banned IP list:    124.152.118.194 110.170.31.181 81.68.244.19 139.59.7.225 200.44.50.155 122.160.31.101 122.51.200.223 201.48.115.235 37.187.181.155 51.254.143.190 212.83.141.237 51.255.28.53 184.71.9.2 58.62.18.194 103.55.191.141 221.165.252.143 64.227.72.109 193.112.172.57 139.59.102.170 119.28.51.99 185.156.74.65 148.70.151.100 185.117.215.9 207.244.70.35 147.135.203.181 82.221.131.5 64.113.32.29 152.136.195.211 173.254.225.107 106.54.72.168 62.234.239.134 125.161.137.97 210.10.208.238 15.161.131.78 121.204.213.37 49.88.112.71

```


/etc/fail2bn/jail.local is pretty standard except 1 ssh failure is jail for over an hour.

```
user1@srvr1:/etc/fail2ban# head jail.local
#
# WARNING: heavily refactored in 0.9.0 release.  Please review and
#          customize settings for your setup.
#
# Changes:  in most of the cases you should not modify this
#           file, but provide customizations in jail.local file,
#           or separate .conf files under jail.d/ directory, e.g.:
#
# HOW TO ACTIVATE JAILS:
#

```

My goal is two fold 1-Reduce unauthorized attempts  2-reduce traffic

Thank You all for your time - Mike

---

### Post by mikecolley on 2020-12-18
I think I found a solution even though I really don't know what I am doing.
Reading [HTML]https://www.linux-magazine.com/Online/Features/Intrusion-Detection-with-fail2ban[/HTML]
I edited ```
/etc/fail2ban/filter.d/sshd.conf
```
and in the section named ```
cmnfailre =
``` 
I added the following lines at the end of the section:
```
            ^Invalid user <F-USER>.+</F-USER> from <HOST> port .*s$
            ^Failed password for invalid user <F-USER>.+</F-USER> from <HOST> port .* ssh2s$
            ^Unable to negotiate with <HOST> port .*$
            ^pam_unix\(sshd\:auth\)\: [Aa]uthentication failure\; logname= uid=0 euid=0 tty=ssh ruser= rhost=<HOST>s$ 

```
--- Note I edited the Unable line above, this one works so far ---
This looks like it works for me, greatly lowering the traffic.  

I saved the file and performed ```
sudo systemctl restart fail2ban
```

I have to emphasize that I don't know what I am doing so you are welcome to try this, but beware you are doing it at your own risk.  If someone can improve the formulas or method I would appreciate them telling me a better way.

Thanks! - Mike

---

### Post by mikecolley on 2020-12-18
I can't seem to figure how to mark this problem solved so I am adding a reply that says [Solved] - Mike

---

### Post by deadflowr on 2020-12-18
> **mikecolley said:**
> I can't seem to figure how to mark this problem solved so I am adding a reply that says [Solved] - Mike

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

Edit: For some reason your thread has already been properly marked as solved.
Whether you marked it as such I'm not sure...

---

### Post by jedi123 on 2020-12-19
You know this would be easy if you just added an 'iptables" rule to your router . But you need a router compatible with DD-WRT. 

PS, having a dd-wrt router or similar like openWRT , Tomato etc.  is good for another reason, you can block your printer from accessing the internet and doing firmware updates that render (read:block) recycled or third party ink cartridges and make them useless.

---

### Post by mikecolley on 2020-12-24
jedi123 said "You know this would be easy if you just added an 'iptables" rule to your router ."  
Mike says: Thank You, excellent idea.  I will probably look at accomplishing that.
Makes me wonder if there is a fail2ban that would work in cooperation with my router?????

---

### Post by mikecolley on 2020-12-26
All: huge reduction in traffic by following directions: [https://visei.com/2020/05/incremental-banning-with-fail2ban/](https://visei.com/2020/05/incremental-banning-with-fail2ban/)
- Mike

---

