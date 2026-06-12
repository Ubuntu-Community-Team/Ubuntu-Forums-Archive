---
title: "ssh issue &quot;important&quot;"
date: 2008-07-07
forum: Security
---

### Post by jcup on 2008-07-07
On my network, I have recently set up two virtual machines, both running Ubuntu. I have a workstation running Ubuntu as well. 

The virtual machines are pretty secure (from what I can tell), I've checked the logs, and I am the only one that logs into them. I have the virtual machines using port 33333 (example) for ssh.

My Ubuntu workstation uses the default port 22 for ssh...

I have never connected to the virtual machines with my Ubuntu workstation, only from my windows workstation, In other words the virtual machines should not even be aware of my workstation, they have never met.

So my question is, firestarter (firewall) is showing that these virtual machines are trying to talk to my Ubuntu workstation on port 22. Why would they do that, like I said they shouldn't even be aware of my workstation. 

Does Ubuntu have something built into it that will try to find other Ubuntu machines.   

I am fairly certain that these virtual machines have not been compromised, they are fresh installs, They do not have public IP addresses, no ports exposed to the internet. I have tripwire installed on them and the reports are fine, and my IDS (Intrusion Detection System) has never seen any traffic going to or from them.

So whats going on here...

My thanks in advance to anyone who reads or responds to this

---

### Post by The Cog on 2008-07-07
Ubuntu doesn't normally try to talk to port 22 on other machines. It's certainly not normal behaviour.

I think I would be inclined to double-check what the firewall is saying - maybe confirm source IP and mac address and TCP flags. See if netstat shows any syn-sent connections to your workstation on the VMs.

---

### Post by jcup on 2008-07-07
Thanks for the advice, yeah, I was pretty sure that was not normal behavior. I am gonna have to dig a little deeper, I'm not real proficient with Ubuntu yet. And wasn't too sure what to check other than the logs...

Thanks

---

### Post by jcup on 2008-07-09
So I did some diggin, and found out that I did at one time connect the virtual machine to my workstation when testing out rsync, I though I had only connected it to one of the servers...

But I only connected it on time, and I did not set up any cron job or anything like that to tell it to connect again... 

Also, the virtual machines were only trying to connect to my workstation at regular intervals of once a week, does that make sense?

I'm really not sure whats going on here, I have investigated the virtual machines thouroghly and i don't see any indication that something is wrong with them...

Any thoguhts anyone?

Thanks!

---

### Post by jcup on 2008-07-22
bump-

Anyone have any ideas...?

---

### Post by konsole on 2008-07-22
> **jcup said:**
> So I did some diggin, and found out that I did at one time connect the virtual machine to my workstation when testing out rsync, I though I had only connected it to one of the servers...

But I only connected it on time, and I did not set up any cron job or anything like that to tell it to connect again... 

Also, the virtual machines were only trying to connect to my workstation at regular intervals of once a week, does that make sense?

I'm really not sure whats going on here, I have investigated the virtual machines thouroghly and i don't see any indication that something is wrong with them...

Any thoguhts anyone?

Thanks!


Have you checked /etc/cron.weekly/ on the virtual machines?

Also crontab for any users; usually crontab -l

---

### Post by jcup on 2008-07-22
Thanks konsole...

I had checked that and nothing, also, I am the only user, but I double checked anyway. (I'm a little paranoid about it)

These are critical virtual machines, I am using them to rsync some really important data from the office to an offsite backup target.

Security is very important on this project, so I really appreciate your input. 

Both of the VMs were trying to connect to my workstation on Tuesdays, but at seemingly random times of the day? What I havn't been able to find out is what passwords the VMs were trying to use. Is there a log on my workstation that could tell me that? All 3 machines have different passwords...

I never did find anything on the VMs that indicated that they tried to connect to my workstation...

Anyway, I have turned off the VMs for now, and I may just rebuild them... for now though I am just baffled.

Thank you for your help though...

---

