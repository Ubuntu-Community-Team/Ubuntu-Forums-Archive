---
title: "Web server"
date: 2011-05-15
forum: Security
---

### Post by tapi0n on 2011-05-15
This summer I'm planning on setting up a web server at home for learning purposes and to fool around on.

Now I've never done something like this and I don't have a lot of experience with these things. So I was wondering if there are any steps I should take to make sure the server is and stays a secure testing environment without any external interferal. 

I apologize should this be in the wrong section but I think this was the most fitting place to post this question. 

Cheers

---

### Post by spynappels on 2011-05-15
As long as you are behind a router and do not forward any ports to your server IP, you should be fine and secure and you can access the server using its LAN IP.

---

### Post by tapi0n on 2011-05-15
Ok cheers!

---

### Post by bodhi.zazen on 2011-05-16
> **spynappels said:**
> As long as you are behind a router and do not forward any ports to your server IP, you should be fine and secure and you can access the server using its LAN IP.

And turn UPnP off (it is a "feature" on your router to automatically open ports).

---

### Post by spynappels on 2011-05-16
> **bodhi.zazen said:**
> And turn UPnP off (it is a "feature" on your router to automatically open ports).

Does Apache trigger/open that too? I did not know that.

---

### Post by CharlesA on 2011-05-16
> **spynappels said:**
> Does Apache trigger/open that too? I did not know that.

I don't think it does.

---

### Post by bodhi.zazen on 2011-05-16
I am not sure, I just turn it off anyways, I do not want any ports automatically opened by anything =)

---

### Post by Flightmare on 2011-05-16
Apache2 does not trigger it. But UPnP is a big security leak in general so it's best to turn it off anyways.

If you wanted to you could modify your apache's VirtualHosts to only accept certain IP-addresses, but this won't be needed if you don't forward Apache through your NAT.

---

### Post by wlraider70 on 2011-05-16
I don't want to get too off topic but does disabling UPnP mean that I have to specify every port that will be opened? Will outgoing packets still have the port open for them?

---

### Post by CharlesA on 2011-05-16
> **wlraider70 said:**
> I don't want to get too off topic but does disabling UPnP mean that I have to specify every port that will be opened? Will outgoing packets still have the port open for them?

UPNP only opens ports for incoming connections - such as torrents.

Outbound connections are usually allowed and anything related to existing connections are allowed through the firewall.

---

