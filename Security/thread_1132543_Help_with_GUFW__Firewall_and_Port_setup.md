---
title: "Help with GUFW / Firewall and Port setup"
date: 2009-04-22
forum: Security
---

### Post by Laibcoms on 2009-04-22
Hi,

I always prefer the status of "stealth" for my ports.  Under WinXP, if the port is not being used by any application, it stays as stealth.  If I run an application that I set to use my port, then the status will change to "open".

As I understand, that's how applications and ports are supposed to work.  An app opens a port if it requires it.  However, I'm trying the same thing for Ubuntu (Jaunty) but I can't achieve it.

Here's what I did:
** My GUFW port setting is like this: 12345 ALLOW 12345  (that is: To Action From) **

#1
- to achieve a "stealth" status for my ports, I use GUFW
- then I add the ports my apps particularly need, example: 12345
- I run the app but it can not get through.  Additionally, if the port is detected externally, it still stays as "stealth".  Should be "open" since the app using that port is running.

#2
- Now if I disable GUFW, "non-standard" (if that's the proper term to use) ports now gets the status "closed" if detected externally.
- if I run the app using port 12345 (again as an example), the application can get through fine.  Then if the said port is detected externally, it shows as "open".

#3
Now if I change my GUFW setting to: 12345 ALLOW Anywhere (that's: To Action From), the said port will "open" if there's an app using it, otherwise it will be "closed".  Again, not the result I am looking for which is "stealth".

So my question then, is there a way to achieve "stealth" using GUFW/UFW and still allowing the applications to open ports if they're using it?

Or is this a bug?

Or should I do it at the iptables level and uninstall GUFW?


Thanks in advance!!
               			                 
[LIST] 					 				
[/LIST]

---

### Post by brian_p on 2009-04-22
> **Laibcoms said:**
> 

As I understand, that's how applications and ports are supposed to work.  An app opens a port if it requires it.  However, I'm trying the same thing for Ubuntu (Jaunty) but I can't achieve it.


Your understanding needs fine-tuning. Running a service causes the service to listen on a port. If netfilter is rejecting or dropping packets destined for that port the service will not hear anything.

In this light your observations make sense.

---

### Post by bodhi.zazen on 2009-04-22
That and the term "stealth" ...

Do you know what a stealth port means vs a closed port ?

In Linux, and most firewalls I know, the terms for port are open and closed. A closed port can REJECT or DROP a packet.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

There was a time when DROP *may* have been more secure, but, with modern cracking techniques, those days are over.

---

### Post by Laibcoms on 2009-04-23
> **bodhi.zazen said:**
> That and the term "stealth" ...

Do you know what a stealth port means vs a closed port ?

In Linux, and most firewalls I know, the terms for port are open and closed. A closed port can REJECT or DROP a packet.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

There was a time when DROP *may* have been more secure, but, with modern cracking techniques, those days are over.

So it means then, it doesn't matter whether it's Stealth/Drop or Reject?

From the given link, DROP produces the "Stealth" mode, since in a way it is similar to sending it to /dev/null.  While REJECT will produce the "Closed" mode when ports are sniffed (in this case, by ShieldsUP!) because it sends back an error message.

But if it's sniffed by other sniffers, DROP and REJECT both produces "closed".  And with modern cracking techniques, even if DROP is used, someone using the right technique can still figure things out.

Am I understanding it correctly?

If it is the case, based on my observation (see above/OP), iptables (only) uses REJECT if no service is listening to a port.  While on the other hand, UFW/GUFW uses DROP.

But then, somewhere UFW/GUFW is preventing an application using a particular port to use it unless the FROM field is set to "anywhere".  And if set as such, it starts to use REJECT, as per my observation (above).


Thanks for the replies ^_^  I'm not versed with networking and so I'm only relying much on what I read and what other people share and/or have documented.  (And with so many of those, it is hard to filter out which is the latest and/or accurate.)

Thanks a bunch!  Much appreciated.

---

