---
title: "Basic Server"
date: 2010-10-16
forum: Server Platforms
---

### Post by Phildough on 2010-10-16
Hey everyone-
I'm new to the forums/ new to Linux in general, so heres a bit of a doozie to start off:

I came across this ultra-simplified tutorial of how to set up a linux home server. [http://www.intac.net/build-your-own-server/](http://www.intac.net/build-your-own-server/)

I know, it's using xubuntu, when a more logical OS would be ubuntu server, or some form other, more basic form of linux (debian, redhat, whatever...). But I'm a college kid setting this up for five roommates and it would be nice to have a central computer we could all use with a decent GUI on top of it being a server....

Anyways, enough back story.

Following that tutorial to the T, blindly copying the config files, ran into a few errors (can't say I didn't expect it...). 

I've got it to the point where ssh'ing into it from our house network works fine. Set up a dyndns domain with it to account for changing ISP's, but when I try to ssh into it remotely I get a "port 22 connection refused" error. I've looked around these forums a bit for a solution, but most of them involved the assumption that the person asking the question knew a lot more than me and went way over my head haha. 

From what I did understand, I edited the /etc/hosts.allow file to ALL: ALL, and figured editing the /etc/ssh/sshd_config files was unnecessary since I was trying to use the default port 22. (BTW, I did check them to make sure they didn't have any PORT: SOMETHINGELSE lines in them...).

So yeah, I'm lost. Any help would be greatly appreciated. Can't promise I'll understand any complex terminology- I can maneuver my way around any unix shells, and thats pretty much it haha. Willing to start absolutely fresh with a clean install of linux if necessary... 

On that note- if anyone knows of a really simple, straightforward tutorial to set up a linux server that I could start from, that would also be great.

Hope to get into linux a lot more over the next couple of months, so hopefully I'll be hearing from you guys more often. Thanks!

---

### Post by James78 on 2010-10-16
It's going to take too much time to explain all of this, but here's some points and links.

1. Most everything that gets a connection refused means the ports blocked. Probably by your router. Forward the port to the local server IP.
2. Having a public server is dangerous. Many exploits and vulnerability scans take place by automated robots every day. Secure your server as much as possible!!
3. If you aren't hosting your server on an actual domain name, you don't need BIND (just for future reference).
4. This [tutorial]("http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3") might help you out.

P.S. Forget ISPConfig, you should use Webmin and Virtualmin instead. Don't install ISPConfig and follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=1197883") for the Webmin/Virtualmin install.

---

### Post by Phildough on 2010-10-16
Thank you very much for the quick response! 
I will definitely check out those tutorials.

A couple things...

1. I have no idea how to forward the ip adress... haha will google that shortly...
2. We kinda plan on just using it for external storage of big files like movies and music, maybe a document or two so we can access it from a school computer or something. No personal stuff whatsoever. Given this, is it really that big of a deal to keep it super-secure? Just out of curiosity, in your opinion, what is the worst they could do? I mean even if they copied our entire disk somewhere and then deleted all our stuff, it's not that big of a deal... right? Or am i being completely naive haha...
3. Don't know what BIND is... lol once again, plan on googling that real quick
4. Once again, thanks for all your help :)

---

### Post by James78 on 2010-10-16
> **Phildough said:**
> Thank you very much for the quick response! 
I will definitely check out those tutorials.

A couple things...

1. I have no idea how to forward the ip adress... haha will google that shortly...
2. We kinda plan on just using it for external storage of big files like movies and music, maybe a document or two so we can access it from a school computer or something. No personal stuff whatsoever. Given this, is it really that big of a deal to keep it super-secure? Just out of curiosity, in your opinion, what is the worst they could do? I mean even if they copied our entire disk somewhere and then deleted all our stuff, it's not that big of a deal... right? Or am i being completely naive haha...
3. Don't know what BIND is... lol once again, plan on googling that real quick
4. Once again, thanks for all your help :)
2. Yes, it is a big deal lol. What's the worst? Someone will hack into your server, and either wreck it completely, or use it as a zombified computer to send out junk to other people (how do you think they're using tons of zombified computers to brute force you? Ones that've already fallen...). Well, it's not that big of deal if you don't particularly care about what happens to your computer, but most of us do, as we put work into them!

---

