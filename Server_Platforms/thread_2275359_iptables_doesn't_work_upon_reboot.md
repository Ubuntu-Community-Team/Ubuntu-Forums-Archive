---
title: "iptables doesn't work upon reboot"
date: 2015-04-25
forum: Server Platforms
---

### Post by fizgig on 2015-04-25
I followed the [tutorial]("http://sharadchhetri.com/2014/02/16/save-iptables-permanently-on-ubuntu/") here to make the iptables changes I make persistent.

I see that it does indeed make a /etc/iptables/rules.v4 file with everything I want in there.

Before rebooting to test, I ran **iptables -L -n -v > before_reboot**
I then rebooted and, you guessed it, ran **iptables -L -n -v > after_reboot** 

I compared the two files and they were basically identical (packet numbers were different but that's to be expected).

What's odd is that after rebooting, none of the rules of iptables are being followed.  I have to run my script that adds the rules one by one upon which it starts working again.  The output of **iptables -L -n -v** doesn't change but iptables starts working.  Anyone else see something like this?  Am I going to have to make a startup script that runs my iptables script every time?

---

### Post by darkod on 2015-04-25
I don't know how that package works, but I see it as completely unnecessary. Simply create a file with all your rules inside, and load it at boot. When you want to modify rules, you modify that file. That's it...

The issue why the iptables are not loaded as you expect on boot, might be because that tutorial doesn't mention loading at boot. It only mentions how to save rules in a file.

The usual way to load iptables in ubuntu server is using iptables-restore. You put that in /etc/network/interfaces in the main interface section (like eth0), below the address, netmask, etc lines. To load your file it would be like:
```
auto eth0
iface eth0 inet static
   address ...
   netmask ...
   gateway ...
   ......
   post-up iptables-restore < /etc/iptables/rules.v4
```

The post-up means after the interface is up, run the command. In this case the command is iptables-restore < /path/file.

Try that... And you might consider uninstalling that package and only control the iptables file manually.

---

### Post by fizgig on 2015-04-25
Thanks for the tip.  I uninstalled that package and did it the way you suggest.  Unfortunately, it didn't seem to make a difference.

Remember, after a reboot, when I examine the iptables in "effect", they are as they should be.  The problem is, they are being ignored (nat'ng doesn't work, etc...)  As soon as I run my script which flushes the tables and reinserts them, all is well.  The rules in iptables still look the same.

On a whim, I changed the post-up to run my script instead of the iptables-restore command.  No difference.  

I added my script to /etc/rc-local and that works.

---

### Post by darkod on 2015-04-25
As far as I know, there are no rules in effect and rules not in effect. The list of rules shown are the rules applied at that moment. So far I haven't seen on any machine a case where the list of rules shown is not the one applied.

I would double check the files, the order in which the rules are applied, etc... In case of any errors.

I don't know what your script looks like, but iptables-restore flushes the rules and inserts the rules from the file passed to it. So in theory it should do the same as your script flushing and inserting rules. All of this under the assumption the rule syntax and order is correct in the file passed to iptables-restore.

---

### Post by fizgig on 2015-04-25
My script is just a list of iptables rules.  That's it.  I then do a iptables-save to a file and an iptables-restore from that file on boot and it doesn't work.

Oh well, my script in rc.local appears to be getting it going anyhow.

---

### Post by darkod on 2015-04-25
If you want to you can post the content of the file created by iptables-save so we can have a look. You are free to hide any public IPs or similar data before publishing the file here, just don't hide too much because we need to take a look at the rules.

Speaking of NAT for example, the part you need to NAT your private IP from internal interface with the public IP on external interface is usually:
```
*nat
:POSTROUTING ACCEPT [0:0]

-A POSTROUTING -o <ext_int> -j MASQUERADE

COMMIT
```

That is enough for traffic going out through the ext_int (external interface) to be NAT-ed.

---

### Post by Doug S on 2015-04-26
I use the /etc/network/interfaces file method Darko mentions also. However, I use "pre-up" instead of "post-up", because I want the rule set in place before the network stuff. Also, I use a bash script to create the rule set, because I have some non-iptables, but related things to do also, and I want it all in one place.

---

