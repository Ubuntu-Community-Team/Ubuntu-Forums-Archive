---
title: "Using Ubuntu as a router."
date: 2007-10-15
forum: Server Platforms
---

### Post by Ikith on 2007-10-15
So I have a few extra network cards and I find this subject very interesting. What I am wanting to do is take an extra box and turn it into a router. Not only can I get extra credit in school but it would feel great being able to do this and learning on the way. Currently the extra box is really used for nothing I have server 2003 but I know using that to do this would be a bad idea.

Anyway I found a guide that seems to be a little old so I was wondering if there was a newer guide to doing this.

What I'm looking for exactly is to turn this into a wired and wireless router. 

From what I understand I need to install webadmin and set my which card is my input and set up DHCP and DNS. So any new guide or anyone I can talk to live about setting this up step by step. Anything would be help honestly.

---

### Post by galeron on 2007-10-15
There's a howto in the Tutorials and Tips subforum. I think the guide you're talking about is on a particular blog. If that's the case, my advice is to use the guide found in UF.

Fair word of caution, Webmin doesn't play nice with iptables. You can end up having 2 sets of configurations (one in Webmin and another manually edited file) and not knowing which one is active.

---

### Post by Ikith on 2007-10-15
Yikes... Is there any way to test which one is active? If so can you delete the inactive one without affecting the router?

Can you go into more detail about this problem?

Edit: Also can you give me a link to the guides I go to the Tut and Tips section and do a search on "Howto turn ubuntu into a router" and I get an error and making it vague gives me other bad results that really have nothing to do with what I'm looking for. Either I'm bad at searching... Or I'm bad at searching.

---

### Post by Brazen on 2007-10-15
> **galeron said:**
> There's a howto in the Tutorials and Tips subforum. I think the guide you're talking about is on a particular blog. If that's the case, my advice is to use the guide found in UF.

Fair word of caution, Webmin doesn't play nice with iptables. You can end up having 2 sets of configurations (one in Webmin and another manually edited file) and not knowing which one is active.

hmm, as long as you haven't created your own funky rc script and config file, this should not be the case, which is pretty much how it is with anything if you create your own rc scipts.  The thing I love most about Webmin is it plays EXTREMELY well with iptables.  It's rather complicated though since it lets you manually configure any and all iptables rules.  For a newbie or someone who does not have or want an in depth knowledge of networking, you would be better of using Shoreline Firewall, which is also manageable through Webmin, but has an easier to use syntax which it translates into iptables rules.

---

### Post by Ikith on 2007-10-15
will using this guide:
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

work or is it missing some instructions?

---

