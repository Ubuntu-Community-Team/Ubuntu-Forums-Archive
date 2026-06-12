---
title: "looking for complete syntax definition for UFW rules"
date: 2013-02-07
forum: Security
---

### Post by dvks on 2013-02-07
Hi,
I am looking for complete syntax definition for UFW rules definition using the command line.
I checked few links such as:
[http://manpages.ubuntu.com/manpages/precise/en/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/ufw.8.html)
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)
and the examples suggest that there are more options then defined by the manual page - [http://manpages.ubuntu.com/manpages/precise/en/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/ufw.8.html)
Thanks for any help

---

### Post by Ms. Daisy on 2013-02-09
Yup. Looks like you found some excellent sources.

If you're still having trouble then post whatever you're trying along with the error outputs.

---

### Post by dvks on 2013-02-09
Thanks for your feedback, I intend to implement some web-browser based interface for UFW and need the complete available syntax for the generation of UFW commands, I think that the resources I managed to find give information but not a complete definition and I assume that there is such command syntax definition some where

---

### Post by Ms. Daisy on 2013-02-09
If you're looking for general guides then this might help

[https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall)

If you read the man page carefully it will explain the syntax.

```
man ufw
```

---

### Post by dvks on 2013-02-09
Thanks again for your feedback.
I am actually looking for details beyond the general guides.
I am looking for the complete definition for the firewall rules definition syntax that can be used by UFW, something like:
 
ufw [insert N] {allow|deny|reject|limit} [in|out|both] [proto {tcp|udp}] [from {any|IP|IP/R}] [port {P[[,P|:P].... [,P|:P]]}] [to {any|IP|IP/R}]   port P[/{tcp|udp}] 
 
The above is something that I already compiled but:
1. I am far from having enough knowledge about the UFW
2. Even with my minimal knowledge of the UFW I know that the above syntax is only partial, far from being complete

---

### Post by dvks on 2013-02-09
for example the man for UFW define the rule syntax as:
 
       ufw [--dry-run] [delete] [insert NUM] allow|deny|reject|limit  [in|out]
       [log|log-all] PORT[/protocol]

       ufw  [--dry-run]  [delete] [insert NUM] allow|deny|reject|limit [in|out
       on INTERFACE] [log|log-all] [proto protocol] [from ADDRESS [port PORT]]
       [to ADDRESS [port PORT]]

1. how does it cover using service name?
2. how does it cover using application name
3. how does it cover the very simple example that they have on the same man page: 
      ufw allow 53
I can easily compile larger list of cases that are not covered.
My purpose is not to show that the given syntax is not complete but to find syntax that I can trust to cover all cases and use it since I do not know the complete definition

---

### Post by haqking on 2013-02-09
> **dvks said:**
> for example the man for UFW define the rule syntax as:
 
       ufw [--dry-run] [delete] [insert NUM] allow|deny|reject|limit  [in|out]
       [log|log-all] PORT[/protocol]

       ufw  [--dry-run]  [delete] [insert NUM] allow|deny|reject|limit [in|out
       on INTERFACE] [log|log-all] [proto protocol] [from ADDRESS [port PORT]]
       [to ADDRESS [port PORT]]

1. how does it cover using service name?
2. how does it cover using application name
3. how does it cover the very simple example that they have on the same man page: 
      ufw allow 53
I can easily compile larger list of cases that are not covered.
My purpose is not to show that the given syntax is not complete but to find syntax that I can trust to cover all cases and use it since I do not know the complete definition


So you are designing a Web Interface for UFW ? UFW is already an interface to IPTables in the Linux Kernel, GUFW would be the GUI for UFW.

neither UFW/GUFW are firewalls, they are both interfaces to the Linux firewall which is Netfilter/IPTables.

IPTables is well documented and the syntax covers everything.

There is already a minimal web interface for UFW [http://ufw2web.sourceforge.net/](http://ufw2web.sourceforge.net/) and it didnt get very far ;-)

Peace

---

### Post by dvks on 2013-02-09
I assume that if someone already put the efforts to create the UFW it may be easier to use it and build on top of it a web interface. The problem is that I am not sure I got the complete rule syntax for the UFW. 
I was looking for existing web interface implementations and in fact the only attempt I managed to find is the ufw2web, as you said it didn't move far.
The initial implementation is for embedded system we design but if it will prove to be a good tool I hope to find time to extract it and make it a stand alone tool sometime in the future with free license.

---

