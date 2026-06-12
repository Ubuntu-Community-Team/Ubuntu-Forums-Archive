---
title: "ufw :: Failing to Start"
date: 2013-01-30
forum: Server Platforms
---

### Post by jonedney on 2013-01-30
When trying to setup & configure ufw, I ran into a couple errors.  Below are the steps I have taken up to where I am now.

First, I installed ufw.
```
sudo apt-get install ufw
```

Then, I created a couple rules
```
sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow "custom ssh port"
sudo deny 22
```

Next, I enabled ufw, received and accepted the message following the command.
```
sudo ufw enable
Command may disrupt existing ssh connections. Proceed with operation (y|n)?
```

I then received the following error immediately after proceeding with the above operation.
```
ERROR: problem running ufw-init
```

After doing some digging around on the net, I found that disabling IPV6 would resolve this problem, so I edited '/etc/default/ufw' to make the following change.
```
IPV6=no
```

Returning to my terminal, I disabled ufw, rebooted my VPS, then re-enabled it again.  Same ssh connection warning as before of course, and also received the same error, so I ran the following command, per another forums post.
```
sudo /lib/ufw/ufw-init start
```

That command offered the following error, which is where I am now.
```
Skip starting firewall: ufw (not enabled)
```

Not looking for answers, but some direction.  I'm running an up-to-date 12.04 LTS on an OpenVZ VPS.

---

### Post by darkod on 2013-01-30
I don't know if that error shows in more than one situation but I have seen it when you have syntax errors in a rule.

Are you using the before.rules or after.rules files? Or not?

What is "custom ssh port", are you sure it can understand it?

I only used ufw once to create a firewall machine and towards the end of the process I realised it would have been much better and cleaner with iptables. If you are willing to, I suggest you use iptables directly, not ufw.

The usual way is to create a file that will hold all your rules, like /etc/iptables.rules and call it on boot by adding a command to your /etc/network/interfaces file in the eth0 section:
post-up iptables-restore < /etc/iptables.rules

That will load the file as soon as eth0 is up.

When I was investigating my project, iptables looked too complicated but later I realised it was only because it exsts since ages ago, and many tutorials are very old, they mention scripts, etc. The above method is very clean, easy, and the rules syntax gives you great flexibility.

---

### Post by jonedney on 2013-01-30
This is my first shot at running a firewall on the system.  I host my personal sites on it which get practically no traffic, so it was never a concern before.  I hid the "custom ssh port", as I changed it for security reasons from the default port 22, to something different.

I'm willing to try using iptables, as really I'm only foreseeing allowing ssh & http remotely for obvious reasons, and not have anything too crazy until I begin working on the mail server end of things (not any time soon).  What are the differences between using ufw & iptables?

---

### Post by steeldriver on 2013-01-30
I'm still confused about what you mean by "custom ssh port" - did you actually create a custom app profile in /etc/ufw/applications.d/? or is it just shorthand for a rule you entered on the 'ufw allow ... ' command line? and I presume 'sudo deny 22' is a typo?

---

### Post by darkod on 2013-01-30
ufw doesn't seem to clear the NAT table when it reloads, but if you are not using it in your case, it might not matter. I am using it, but figured it out too late into the project.

Even if you change the SSH port (I have it changed too) you can use the numeric port as opposed to a string. In your case, the rule set would be simple, the content of /etc/iptables.rules would be something like:
```

# Default policy settings
:INPUT DROP[0:0]
:FORWARD DROP[0:0]
:OUTPUT ACCEPT[0:0]

-A INPUT -i eth0 -p tcp --dport 80 -j ACCEPT
-A INPUT -i eth0 -p tcp -s <your public IP> --dport <ssh port> -j ACCEPT

```

That should allow port 80 traffic for everyone, and traffic on your changed ssh port only from your public IP.

-i means incoming interface
-p protocol type
--dport destination port of the traffic
-s source IP (if you want to limit source)

One good thing of iptables-restore is that it's temporary.

When doing the initial tests, don't put the command in /etc/network/interfaces yet. Create the rules file, and at the command line run:
sudo iptables-restore < /etc/iptables.rules

That will flush iptables rules and load your rules from the file. In case it locks you out, rebooting the server makes the rules go away since you don't have the post-up set up yet.
When you are happy with the rules, you can set the post-up.

Of course, for this to work when locked out you have to have a way to reboot the server from a VPS control panel etc.

I hope I didn't make an error in the rules. :)

EDIT PS: If you notice in my example the default INPUT policy is DROP, which means you don't specifically need to deny any traffic. It denies everything unless you allow it in the rules you enter in the file.

---

### Post by jonedney on 2013-01-30
I've changed my SSH port in the ssh_config on my server, to something that is NOT 22, lt's say it's 2200 for reference.  So I ran the sudo ufw allow 2200 for that purpose, then also ran sudo ufw deny 22, as it's the default port and I wanted to block connections to it.

I will look into iptables moving forward, since that is an additional viable options.  The only reason I went with ufw was due to it being referenced in the help documentation for security.

---

### Post by bantuvez on 2013-01-30
IMHO:

```
sudo ufw allow ssh
```This will look in the /etc/services file for the ports of ssh. Default is 22. Because you changed your ssh port it now maybe your "custom ssh port". So this will allow port 22 or your "custom ssh port". So if your /etc/services file contain the port 22 for ssh then this rule will contradict with the 
```
 sudo ufw deny 22 
```rule. If your /etc/services file contain the "custom ssh port" for ssh, then the
```
sudo ufw allow "custom ssh port"
```rule is not needed.

---

