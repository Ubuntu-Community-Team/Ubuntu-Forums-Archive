---
title: "Can I lock myself out of my server?"
date: 2008-09-12
forum: Server Platforms
---

### Post by cpetercarter on 2008-09-12
I run a website from a dedicated server (Ubuntu 6.06 LTS) at a remote location. I use ssh to administer the server from my home computer (8.04).

I have successfully set up RSA key-based login to the server, and I am now considering whether I should disable password login,to improve security. But I need to consider how I could access the server in an emergency. Suppose my home computer's hard drive failed, or I needed to re-install the OS -obviously this would remove the RSA authentication keys from the computer. I could generate new keys of course, but could I transfer the public key to the server? I ask this because the server normally asks for a password before it accepts a key. Will it still do this if I have disabled password authentication? Or will I be unable to transfer the new key and hence be effectively locked out of the server? 

And if I would be locked out, what is the best answer eg always make sure that at least two different computers are enabled for key-based login to the server?

---

### Post by fmartinez on 2008-09-12
try creating a default user other than your own. I do that on my own server just in case i forget my password. I always have a way back in.

---

### Post by cpetercarter on 2008-09-12
Thank you for this suggestion. However, I am not sure that it helps me. I am looking at a situation where I have disabled password authentication, and only have key-based authentication, and then my computer goes down and I lose the keys. I may be missing something but I do not see how having an additional username available would be of any use in these circumstances.

---

### Post by Vivaldi Gloria on 2008-09-12
I email my passwords and keys to my gmail account in case something happens to my computer. Actually I encrypt them with a password (always the same one) and then email to myself.

---

### Post by windependence on 2008-09-12
Well, worst comes to worst you can always boot from a recovery CD and mount your drives, and delete the keys. You can also get into single user mode and change things from there. Everyone should learn how to recover from something like this, especially if you run a server with important stuff on it.

Of course, in a case like yours, you really could lock yourself out and would have to drive to the co-lo or get someone there to load stuff for you.

Why are you so paranoid about password login? I have several seb servers exposed to the net, one for more than 4 years and the first two were bare without a firewall, and I have not been compromised, BUT, I do these things:

Now, I run a good hardware firewall.

My LAN is NATed.

I do not use dictionary words or any part of dictionary words in ANY of my USER names OR passwords. Make 'em work for it.

I use blowfish encryption for password files

I don't run a GUI or any other service that is not absolutely necessary.

I have ONE box on the LAN that is the ssh gateway. I do NOT ssh directly in to the web servers.

There are probably a few more but you get the idea.

-Tim

-Tim

---

### Post by cpetercarter on 2008-09-12
I think that what you are all saying is - yes, I would find myself locked out in the circumstances I have outlined. If the server was sitting beside my desk and I could connect a keyboard and a monitor to it, there would be no problem of course, since I could simply open a terminal and re-enable password authentication, or whatever else I needed to do. But the server is actually about 40 miles away, and I would need to ask the folk who own it to sort the problem out, and they would no doubt charge me lots of money to do so!

I don't think I am being paranoid about password authentication. I see in my logs lots of attempted break ins (fortunately fail2ban throws them out after the first few failures) and I have read lots of advice which tells me that disabling password authentication is a sensible way of improving security on the server. Of course there is no substitute for strong user names, passwords and keys. Some physical measures mentioned in the previous post (eg hardware firewall, LAN configuration) are however not possible in my case since I only lease the server.

---

### Post by windependence on 2008-09-12
Yes, that's what I meant, in your situation you actually could lock yourself.

Look, I'm not gonna sit here and tell you that passwordless auth is not more secure. It certainly is. The point I'm trying to make is it's not necessary. I have seen those logs for years and years, and for someone who is not around that all day, it seems scary. Don't be fooled, most of those "attempts" aren't really attempts at all, they're port scans, and if they are attempts they're just automated garbage. They couldn't hack their way through a paper bag. I see the same thing on my web servers. We get over 13,000 page views a day and over 5 million hits per month and I don't run denyhosts or fail2ban or anything else, just a good firewall. Your server provider, if they are professionals should certainly have you behind a firewall that you can control. If not, you should start asking lots of questions.

-Tim

---

### Post by schettj on 2008-09-12
If you don't want to disable logins, do the following

1) no root login
2) only selected users (ie, just the one)

3) run sshd on a non-standard port
and/or
4) iptables blocks for access to sshd port, only allow from known ips or ranges

5) use fail2ban. Kills probes dead.

doing 3 alone will drop probes to 0. In the unlikely event a true badguy finds your sshd then 1&2&5 will cover your **** nicely.

---

### Post by windependence on 2008-09-13
@schettj,

The script kiddies today will find your ssh port no matter where you put it although a port in the higher range is less likely to be scanned.

I'm not disagreeing with you here, go for the non-standard port, just bringing up a point that it will probably not reduce them to zero. IMHO the single best thing you can do is put a good firewall with UTM in front of your entire network and only run the services and ports you absolutely need.

-Tim

---

