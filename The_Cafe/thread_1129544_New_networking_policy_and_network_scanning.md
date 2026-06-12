---
title: "New networking policy and network scanning"
date: 2009-04-18
forum: The Cafe
---

### Post by jmmL on 2009-04-18
I recently received an email from the IT coordinator at my university explaining that some changes had been made to the network over the easter holidays. Previously, the policy was to register your PC via a webpage that was displayed when you first connected to the network. I assume that this then recorded your MAC address and you were free to go.

Now, we will apparently have to sign in every time we re-start our pc, and leave a scanning window of our browser open in the background. I'm 99% sure that the network is run on Red Hat-based servers, so my question is; which piece of software are they likely to be using for this?

I'm not interested in circumvention or anything like that; it's just pure curiosity. They claim they are virus scanning, and I'm not sure how they'll do that given that I'm running ubuntu. I suspect in the earlier registration they either read my user-agent string or used -OS flags with nmap to fingerprint. I'm also slightly concerned about how much monitoring they might be doing; I've been messing around with tcpxtract today; it's a fascinating piece of software. It kept picking up loads of html files; I finally looked at one and it turned out to be requests for weather information from the weather applet!

Sorry about the rambling..!


Edit: I've had a look around and I'm guessing they'll probably use something like this [http://en.wikipedia.org/wiki/Cisco_NAC_Appliance](http://en.wikipedia.org/wiki/Cisco_NAC_Appliance)
The authentication screens look familiar from looking at friends' Windows PCs with authentication troubles.

---

