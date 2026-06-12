---
title: "Denyhosts &amp; Custom Regex"
date: 2008-11-06
forum: Security
---

### Post by anthro398 on 2008-11-06
I'm running SSH on both port 22 and port 80.  Denyhosts works fine blocking multiple login attempts on port 22.  I've written a custom regular expression to add to hosts.deny addresses that visit port 80 more than once.  It doesn't work though. 

An example of the target string in /var/log/auth.log:
```
Nov  5 20:52:06 server sshd[26186]: Bad protocol version identification 'GET / HTTP/1.0' from 999.999.999.999

```

The custom regex added to /etc/denyhosts.conf:
```
USERDEF_FAILED_ENTRY_REGEX=sshd.*Bad protocol version identification.* from (::ffff:)?(?P<host>\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})

```

The target string is matched by SSHD_FORMAT_REGEX, so the user defined regex should be applied.  I've verified the matches in Kodos.

Any idea what I'm doing wrong?

By the way, running SSHD on port 80 is really useful when you're behind public wireless access points that limit all outgoing traffic to port 80.  In that case, one can't use either VPN or tunnel over SSH and all traffic must be sent in the clear.  Running SSHD on port 80 provides a mechanism to secure traffic on those networks.

When one visits an SSH server with a browser one sees the version string of the SSH server, in this case SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1.  I could just let this pass and let denyhosts catch the IP address when the visitor turns to an SSH client after discovering the SSH server with a browser.

Thanks.

---

### Post by bodhi.zazen on 2008-11-08
I do not think you need to do any of that. denyhosts uses /etc/hosts.deny and thus is a tcp wrapper and is not dependent on the port.

See : [http://denyhosts.sourceforge.net/ssh_config.html](http://denyhosts.sourceforge.net/ssh_config.html)

[http://denyhosts.sourceforge.net/faq.html](http://denyhosts.sourceforge.net/faq.html)

To be honest, I stopped using denyhosts and I am not sure it adds much.

I advise you secure your ssh server with 2 things :

1. Keys.

2. Add a list of "allowed users" in /etc/ssh/sshd_config

See [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

If you do those things, and disallow logins without a key, deny hosts does not add much.

---

### Post by anthro398 on 2008-11-08
Thanks for writing.  I appreciate your desire to help, but I would have thought it would have been clear that I am not new and that I have a purpose and situation that precludes me from limiting access to predefined IP addresses.  You've completely missed the point of my post.

See, my problem is not that I think denyhosts isn't paying attention to what is happening on port 80.  What I wanted was to add addresses to the hosts.deny file that visit port 80 with more than once with a web browser.  I'm well aware, as evidenced by the log line that I included, that SSHD events are being parsed out of the auth.log by denyhosts.  Nor is my problem that I'm really concerned that an attacker will brute force my user name and password.  

The reason for my post is exactly as I have described it and I'm intensely curious why anyone would responded without addressing it.  

Thanks.

---

### Post by bodhi.zazen on 2008-11-08
I am indeed having a difficult time understanding what you are trying to do, I would suggest you write a "simple" set of IP tables rules ;)

[http://www.ducea.com/2006/06/28/using-iptables-to-block-brute-force-attacks/](http://www.ducea.com/2006/06/28/using-iptables-to-block-brute-force-attacks/)

---

### Post by anthro398 on 2008-11-08
> **bodhi.zazen said:**
> I am indeed having a difficult time understanding what you are trying to do, I would suggest you write a "simple" set of IP tables rules ;)

[http://www.ducea.com/2006/06/28/using-iptables-to-block-brute-force-attacks/](http://www.ducea.com/2006/06/28/using-iptables-to-block-brute-force-attacks/)

Again, thanks for writing.  It seems that you aren't familiar with denyhosts, which leads me to wonder at the multiple responses trying to discourage me from what I find to be the most likely solution.  

I'll try to be more explicit.  I travel.  I often use random wireless networks that I don't trust.  I'd like to encrypt traffic.  Often, outgoing traffic is limited to destination TCP port 80.   

So, you see, I can' use iptables, though I'm very familiar with iptables and use it to secure other ports, because I don't know the IP addresses from which I'll be connecting.  Therefore, I can't whitelist them.  I could try the solution in the link you provided, but there is a reasonable likelihood that I'll lock myself out.

Forgive me if I seem testy.  I emailed this issue to my local LUG and received the same response- well intentioned people apparently with no experience configuring denyhosts who graciously tried to point out other, unworkable solutions.  So far I've been told here: 1)don't worry about it, 2)use keys, 3)create allowed users in sshd_conf, 4)use iptables.  You can see from the title of the thread, "Denyhosts and Custom Regex", that I'm asking for assistance using custom regular expression with denyhosts.  You can perhaps see how it might be frustrating to receive responses unrelated to the topic.  Had the thread been something like "Secure SSH on port 80?", I would have expected responses unrelated to regex in denyhosts.

Anyway, thanks for your time.

As an aside, I use keys, but not exclusively.  There are times I connect from machines that are not my own and I want to be able to scp data from machines that I don't own to my machine.  In the first case, I wouldn't be able to connect.  In the second case, my private key would be vulnerable to snooping by other users.  I do specify allowed users. 

I could allow SSHD to listen to all requests and expect the likelihood of compromise to be very low.  However, campus IT, should they discover that I'm running SSHD and that it's open to all requests, would probably be unhappy.  By being able to demonstrate that denyhosts limits connection requests to 2, I put myself in a much stronger position to defend my decision.

---

### Post by bodhi.zazen on 2008-11-08
did you ever stop to think that you might be trying to use the wrong tool for the task at hand ?

You should not assume you know more then me, or anyone else for that matter, about denyhosts.

Also, I had not idea you were trying to access your campus internet without permission, for that reason I am closing this thread not. This type of activity is not supported on these forums.

---

### Post by anthro398 on 2008-11-08
> **bodhi.zazen said:**
> did you ever stop to think that you might be trying to use the wrong tool for the task at hand ?


As a matter of fact, yes.  As I noted, every alternate option you proposed is unworkable.  This is, in fact, what denyhosts is designed for.  

> 
You should not assume you know more then me, or anyone else for that matter, about denyhosts.


What an absurd thing to say.  If I assumed that I know more than anyone else about it, why would I spend time asking for advice?  Really, your attempt to portray me as a know-it-all is just silly.

> 
Also, I had not idea you were trying to access your campus internet without permission, for that reason I am closing this thread not. This type of activity is not supported on these forums.

Since you are obviously not aware of my campus policy, please let me enlighten you.  There are no prohibitions against faculty, which I am, running services.  We must, if challenged, demonstrate that those services are secure.  That's exactly the tone and purpose of this thread.  

If you want to close this thread because you feel insulted then I suppose that's your prerogative.  I couldn't agree more.  This thread is insulting.  You've wasted my time by repeatedly disregarding the clear intent of this thread- to discuss the use of custom regular expressions in denyhosts.  Your move is transparent and childish.

Please, if you have any intelligent advice to offer regarding the use of regex in denyhosts, offer it now.

---

### Post by bodhi.zazen on 2008-11-08
> **anthro398 said:**
> Since you are obviously not aware of my campus policy, please let me enlighten you.  There are no prohibitions against faculty, which I am, running services.  We must, if challenged, demonstrate that those services are secure.  That's exactly the tone and purpose of this thread.

Silly me, I forgot to close the the thread :redface:

Since you are a faculty member and you have permission I am sure your IT department will help you.

---

