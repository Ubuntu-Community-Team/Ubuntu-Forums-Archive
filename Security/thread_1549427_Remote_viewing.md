---
title: "Remote viewing"
date: 2010-08-09
forum: Security
---

### Post by McTwitch on 2010-08-09
I keep getting a window saying that who ever is trying to remote view my desktop, and then asks me if I would like to accept or decline this. As of yet, I've declined it, because I don't know what they can do from there. The last attempt wasn't too long ago, and I wrote down the address it told me.

"190-176-153-146.speedy.com.ar"

I went to speey.com and it's an auto repair website. So...I don't really understand what's going on here. Anyone?

---

### Post by bodhi.zazen on 2010-08-09
If you do not use remote desktop connections you should disable it.

If you do , you should learn to use ssh instead as VNC is not a very secure connection.

Just be sure to learn to secure ssh (use keys, disable passwords).

---

### Post by cdenley on 2010-08-10
> **McTwitch said:**
> I went to speey.com and it's an auto repair website. So...I don't really understand what's going on here. Anyone?

It's not "speedy.com", but "speedy.com.ar". A computer with the ISP "Telefonica de Argentina" is trying to connect to your VNC server, which you apparently enabled without setting a password, but required that you confirm connections locally.

System>Preferences>Remote Desktop

That is probably a bot trying to connect to your server, and found your IP at random looking for an unsecured VNC server. Don't enable features you don't understand.

---

### Post by scottuss on 2010-08-10
You should disable VNC straight away, and perhaps consider either buying yourself a router or activating a firewall on your computer. And fast!

---

### Post by cdenley on 2010-08-10
> **scottuss said:**
> You should disable VNC straight away, and perhaps consider either buying yourself a router or activating a firewall on your computer. And fast!

He may already have a router with UPnP enabled, and checked the "configure network automatically to accept connections" checkbox. Either way, I don't think a firewall is necessary, just don't enable servers you don't intend to run or don't know how to configure!

---

### Post by scottuss on 2010-08-10
> **cdenley said:**
> He way already have a router with UPnP enabled, and checked the "configure network automatically to accept connections" checkbox. Either way, I don't think a firewall is necessary, just don't enable servers you don't intend to run or don't know how to configure!

Yeah but a firewall will blanket stop all outside access to anything you may want to enable without further fuss.

---

### Post by cdenley on 2010-08-10
> **scottuss said:**
> Yeah but a firewall will blanket stop all outside access to anything you may want to enable without further fuss.

Why would you enable something just to filter it? Most listening processes you enable so people can access them.

---

### Post by scottuss on 2010-08-10
> **cdenley said:**
> Why would you enable something just to filter it? Most listening processes you enable so people can access them.

I'm not saying you would/should, but in this case it looks like the OP *does*

You could argue that getting into the habit of not enabling stuff unless you need it is good, but I don't see your issue with enabling a firewall.

For those that know what they want to activate (my desktops have the firewall switched off) that's great, but for some users, a firewall is a good idea, and there is no logical reason to argue against that except for argument's sake, or so it would seem...

---

### Post by cdenley on 2010-08-10
Enabling a firewall would be a quick-fix for McTwitch, but I think whether a firewall is used or not, the proper solution would be  to disable the server. Unless there are servers running the user did not intent to run, a firewall will only make things more difficult when the user does intend to run a server.

---

### Post by scottuss on 2010-08-10
> **cdenley said:**
> Enabling a firewall would be a quick-fix for McTwitch, but I think whether a firewall is used or not, the proper solution would be  to disable the server. Unless there are servers running the user did not intent to run, a firewall will only make things more difficult when the user does intend to run a server.

And if he/she *intends* to run a server, one quick bit of firewall config should be the least of their worries. Anyway, this is getting tiresome now.

To the OP:
sudo ufw default deny
sudo ufw enable

Job done, no more messages, and extra security (who knows whatever servers he/she may have accidently activated, but who cares with the firewall running)

---

### Post by wacky_sung on 2010-08-10
> **scottuss said:**
> And if he/she *intends* to run a server, one quick bit of firewall config should be the least of their worries. Anyway, this is getting tiresome now.

To the OP:
sudo ufw default deny
sudo ufw enable

Job done, no more messages, and extra security (who knows whatever servers he/she may have accidently activated, but who cares with the firewall running)

Do you know that a lot of servers getting owned are partly due to misconfiguration inspite with the firewall running.Firewall just act as barrier to protect your system.Any open doors will lead to intrusion inspite with the firewall running.Ask the developer here why Ubuntu by default has disable most services?The reason is because of security inspite with no firewall running.

---

### Post by McTwitch on 2010-08-10
Right...I've already removed the remote desktop viewer program, as well as any components associated with it. If it's alright with all of you, I think I'll mark this as solved.

---

### Post by scottuss on 2010-08-13
> **wacky_sung said:**
> Do you know that a lot of servers getting owned are partly due to misconfiguration inspite with the firewall running.Firewall just act as barrier to protect your system.Any open doors will lead to intrusion inspite with the firewall running.Ask the developer here why Ubuntu by default has disable most services?The reason is because of security inspite with no firewall running.

You contradicted yourself.

"Firewall just act as barrier to protect your system.Any open doors will lead to intrusion inspite with the firewall running."

With a firewall running (and properly configured), the doors are closed, I'd argue it's nearly as good as not having the service running/installed at all.

---

### Post by wacky_sung on 2010-08-13
> **scottuss said:**
> You contradicted yourself.

"Firewall just act as barrier to protect your system.Any open doors will lead to intrusion inspite with the firewall running."

With a firewall running (and properly configured), the doors are closed, I'd argue it's nearly as good as not having the service running/installed at all.

I think it is better for you to do some read up before you commented.If my words are wrong,look around those websites that has been compromised and been used as phishing site.Go to [phishtank]("http://www.phishtank.com/") on the submission link of those phishing site.Alternative, you can email the phishing site owner (getting owned) to verify that do they running any firewall.

Another example of owning the website is through web application hack such as SQL / XSS injection in which you can bypassed the firewall.From that you can determine the admin username and crack their md5 password using rainbow table.

---

### Post by scottuss on 2010-08-13
> **wacky_sung said:**
> I think it is better for you to do some read up before you commented.If my words are wrong,look around those websites that has been compromised and been used as phishing site.Go to [phishtank]("http://www.phishtank.com/") on the submission link of those phishing site.Alternative, you can email the phishing site owner (getting owned) to verify that do they running any firewall.

Another example of owning the website is through web application hack such as SQL / XSS injection in which you can bypassed the firewall.From that you can determine the admin username and crack their md5 password using rainbow table.

The services exploited were allowed through the firewall, no? If so, this completely ruins your argument.

You need to figure out whether your arguments are applicable here. Hint: they're not. Use your head, you just said that sites get owned through XSS or SQL injection. The firewall must, by definition, allow access to at least one port for people to view the site, so yes, that service may be exploitable. If no ports are open, which is what my advice suggests, then there are no vulnerable services exposed.

I think rather than telling me to do some reading, you need to find material that is relevent to the conversation.

---

### Post by wacky_sung on 2010-08-13
> **scottuss said:**
> The services exploited were allowed through the firewall, no? If so, this completely ruins your argument.

You need to figure out whether your arguments are applicable here. Hint: they're not. Use your head, you just said that sites get owned through XSS or SQL injection. The firewall must, by definition, allow access to at least one port for people to view the site, so yes, that service may be exploitable. If no ports are open, which is what my advice suggests, then there are no vulnerable services exposed.

I think rather than telling me to do some reading, you need to find material that is relevent to the conversation.

I think you are just a newbie in regard to security.Pardon me i am not a IT security expert to explain things in detail technically but i do web application / exploitable hacking(using exploit) as my personal hobby ethically.

PS:Pls do not take it personal as my comments meant not harm or any personal attack.

---

### Post by scottuss on 2010-08-15
> **wacky_sung said:**
> I think you are just a newbie in regard to security.Pardon me i am not a IT security expert to explain things in detail technically but i do web application / exploitable hacking(using exploit) as my personal hobby ethically.

PS:Pls do not take it personal as my comments meant not harm or any personal attack.

This has nothing to do with "web" security, per se. It's simple network security. 

Whilst I don't find your comment that I am a newbie to security offensive, allow me to assure you that this is not the case. Where you do ethical "hacking" as a hobby, I am currently contracting for a large organisation where security is taken very seriously, in all aspects, not just web application, SQL injections etc. However, this, as your comments, is out of context with regard to the OP's issues.


For the OP, who is a home user, enabling his firewall is an insanely easy step to stopping the problem he has now, and probably others. Whilst this is not securing him 100%, it is providing an easy to set-up solution that ***will*** be of benefit.

This thread has been marked as solved now, which I'm glad of, the OP is obviously happy and therefore I am unsubscribing from this thread, I'd urge you to do the same :)

---

