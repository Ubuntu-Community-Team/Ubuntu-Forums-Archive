---
title: "UFW-ERROR: Could not find a profile matching &quot;xxxx&quot;"
date: 2016-02-21
forum: Security
---

### Post by caver12 on 2016-02-21
Everytime I try to add a rule to UFW I get- ERROR: Could not find a profile matching 'xxxxx.'
If I go sudo ufw deny 172.18.37.125, I get- ERROR: Could not find a profile matching '172.18.37.125'
           sudo ufw deny outgoing- ERROR: Could not find a profile matching 'outgoing'
No matter what rule whether it's deny or allow.
I have reset ufw and uninstalled and reinstalled UFW.
Ubuntu 14.04x64

---

### Post by irvine_himself2 on 2016-02-22
Not an expert on UFW, but for the last few days I have been playing around with UFW on Wiley Werewolf running from an external hard disk and have had similar issues. I also tried using GUFW and successfully denied all incoming and outgoing, then, subsequently, opened tcp ports 80 and 443 for http and https, along with UDP 53 for DNS, (port numbers need checked.) So, since GUFW is a front end for UFW, I am fairly sure the problem was with me.

My advice is to set up some rules with GUFW, try:  "sudo ufw status"  to see how they work, then flush and disable GUFW before trying to write your own matching rules.

Irvine

---

### Post by caver12 on 2016-02-22
I know how to write rules for UFW. I just did a clean reinstall of Ubuntu 14.04. This is when the profile problem started.I am trying to setup UFW the way I had it before. What I want to know is why is UFW searching for profiles for every rule. As far as I know UFW profiles are for apps to allow a specific app access. Profiles have nothing to do with aloowing/denying IPs,ports,whatever.  Thanks for your reply.

---

### Post by deadflowr on 2016-02-22
You need to express a direction.
to or from

---

### Post by steeldriver on 2016-02-22
I think the syntax you're looking for is 'ufw **default** deny outgoing'

```

$ sudo ufw deny outgoing
ERROR: Could not find a profile matching 'outgoing'

```
```

$ sudo ufw default deny outgoing
Default outgoing policy changed to 'deny'
(be sure to update your rules accordingly)

```

The short-form needs to be followed by a port/protocol or application name, as described in the man page

```

EXAMPLES
       Deny all access to port 53:

         ufw deny 53

       Allow all access to tcp port 80:

         ufw allow 80/tcp

```

```

         ufw allow <name>

```

---

### Post by caver12 on 2016-02-22
No if you don't put in/out in is the default.

---

### Post by caver12 on 2016-02-22
ufw allow  is for apps that are in your app profile. not for other rules. In the past if I entered a rule I have never had "could not find profile for xxxx"Now that is all I am getting.sudo ufw allow from 123.45.67.89= ERROR: Could not find a profile matching '123.45.67..89' same for deny, and that is the right syntax.

---

