---
title: "UFW:can you block  specific IPs for some applications only?"
date: 2014-07-07
forum: Security
---

### Post by cogset on 2014-07-07
I suspect this may not be possible using UFW,however I just have to  ask:is it possible to prevent some specific IP addresses from connecting  to some applications only,_but still allow them in a normal web browser_?

Here's  an example:I've seen Thunderbird sometimes connecting to an handful of  IP addresses on port 80 (on the server side),probably nothing malicious  since they appear to be legitimate websites that  I normally visit in my  web browser,but still:what if I wanted to access those IPs *only* from my web browser and never have them connecting to my email client?

I  reckon this could be for a number of reasons,maybe web feeds on those  sites,or email alerts,or who knows what other feature,but what can I do  to prevent this?

Obviously I can't simply block traffic to and  from port 80 for those websites,or else I won't be able to access them  with a web browser:so here's my question,is there such a fine grained  control with UFW to accomplish what I'm after? 

I would lean towards no,in that case is there some other way to do that with iptables?

---

### Post by thnewguy on 2014-07-07
I don't think UFW will block access to a particular server/port for just one application. Since Thunderbird usually does not contact any servers (aside from stuff like Mozilla or sites where you have subscribed to feeds) you might be better off looking at why Thunderbird is contacting those sites. Chances are you are either A) getting e-mail from that site and Thunderbird is downloading content which will display inside your e-mail or B) you are subscribed to a feed on that server. In either case you should want Thunderbird to be able to communicate with the server.

In short, I don't think the solution here is to block Thunderbird, but to find out why it is contacting websites you say you visit.

---

### Post by cogset on 2014-07-08
I agree with that > In short, I don't think the solution here is to block Thunderbird, but  to find out why it is contacting websites you say you visithowever I've sort of done that already and concluded that most if not all of them are websites that I normally visit with Firefox:maybe I've subscribed to some email alert and forgot about it,maybe it's some web feed,still sometimes I can see no reason why Thunderbird should connect to port 80 of some servers.
Case in point,I can see -between others- occasional connections to Canonical servers:now I'm reasonably sure I don't have web feeds coming from there and my Thunderbird installation is from a bzip archive and not from repo,so why is that?
To clarify,I'm certainly not worried,just wanted to know what can be done to ensure,_if only as a proof of concept_,that Thunderbird strictly  connects to only the mail provider server.
I know that UFW,to the best of my knowledge,can't do this as it can only block applications based on the specific default ports that those applications are supposed to use:in this case since we are talking about port 80,I certainly can't block outgoing connections to that port or I won't be able to access those websites in my browser.

Maybe this could  be done with iptables,although it's currently beyond my ability to find out how?

---

### Post by thnewguy on 2014-07-08
Rather than IPTables, my thought would be to look into AppArmor profiles. It is possible a Thunderbird profile could be made to limit connections, though I'm not sure about that.

Regarding Thunderbird's outgoing connections, I think both Thunderbird and Firefox share some code (web rendering, plugin code, etc). If Firefox is your main browser, there may be some overlap with the two applications sharing functionality.

---

### Post by Gyokuro on 2014-07-08
Hi

You can generate a list with IP's you want to block and load the file content in your uwf (there are file lists you can download - search for something like geo-region list blocking, file should contain only the IP's you want to block):

 **while read line; do sudo ufw deny $line; done < block_ips.txt**

however this is global for your system for applications you will need an application firewall ([https://en.wikipedia.org/wiki/Firestarter_%28firewall%29](https://en.wikipedia.org/wiki/Firestarter_%28firewall%29))

- HTH

---

### Post by cogset on 2014-08-07
Would this be just temporary,like adding  some chains to iptables,or would this overwrite in some way my current ufw rules?

And,are you advising Firestarter because it has traffic monitoring capabilities or because it can deliver a more fine-grained control than  ufw?

---

