---
title: "VPN for Dummies"
date: 2012-06-12
forum: The Cafe
---

### Post by Docaltmed on 2012-06-12
Though this isn't an Ubuntu-specific question, I thought you guys would be the best to ask.

Like any small company, I have concerns about data privacy. This is even more important because I'm in the health care industry. 

Until now, to remotely access data, I've been using SSH. It is clumsy, slow and inelegant, and I suspect still leaves holes. 

So I've been thinking about implementing a VPN -- the service appears to be pretty cheap -- but I'm a VPN idiot.

I mean, ok, I sign up for the service. Then what? Do I have to reconfigure my office's router? Is there client-side software that needs to be installed? Are VPN tunnels destination-specific (i.e., I can get a tunnel from my home computer to the office server, but that's it. If I go to Amazon, I leave VPN security?)

Also, how do I pick a good VPN provider? 

Any answers or links to a decent tutorial on the subject will be met with great happiness, but I will refrain from posting any lolcats.

---

### Post by mips on 2012-06-12
Depends on your current setup and there's no one answer fits all scenarios.

Some background info
[http://www.cisco.com/en/US/tech/tk583/tk372/technologies_tech_note09186a0080094865.shtml](http://www.cisco.com/en/US/tech/tk583/tk372/technologies_tech_note09186a0080094865.shtml)
[http://www.howstuffworks.com/vpn.htm](http://www.howstuffworks.com/vpn.htm)

---

### Post by HermanAB on 2012-06-12
Howdy,

SSH is secure.  It also has the advantage that you only run it when you need it - effectively an ad-hoc VPN.  So the security risk with SSH is significantly less than that of a permanent VPN.

BTW, if you set up a key system and a Nautilus bookmark, then you can open a remote file system with a double click.  So if you find SSH clunky then you have not configured it properly.

---

### Post by SeijiSensei on 2012-06-12
I'd put a Linux box in the office and use a [static-key OpenVPN tunnel]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") back to your house.

---

### Post by spynappels on 2012-06-13
Where is the data stored normally? In your Office? Where do you need access to it? Other offices, your laptop for mobile access, a phone?

Depending on the answers to these questions, you may find that SeijiSensei's suggestion is the best, or some solution built on you hosting a OpenVPN server in the office and connecting to that from other locations.

OpenVPN is a good solution and is well documented.

---

### Post by spynappels on 2012-06-13
It may be useful to ask admins to move this to the Security subforum where there are often discussions on the merits and otherwise of different VPN options and systems.

---

### Post by Docaltmed on 2012-06-13
Wow. Excellent suggestions, all. Thanks for your help!

---

### Post by Ms. Daisy on 2012-06-13
You weren't very specific about what kind of business it is or where you're located.  If you're in the US, there are some regulatory requirements in regards to security/privacy in the health care industry that might apply to you.  If you're not in the US, there may still be regulations. Might be worth looking into before you find yourself failing an audit.

---

### Post by SeijiSensei on 2012-06-13
One rather arcane regulation you should be aware of if you're in the US is the limitation on what algorithms you can use for encryption.  The OpenVPN default is to use Blowfish, but that doesn't conform to Federal regulations.  For the tunnel I maintain with a health-care client, I use the approved [AES256]("http://en.wikipedia.org/wiki/Advanced_Encryption_Standard") instead.  I also used it to encrypt patients' information when stored in a database.

---

