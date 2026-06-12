---
title: "a Q about firestarter"
date: 2006-04-11
forum: Server Platforms
---

### Post by Ob1 on 2006-04-11
Firestarter was one of the first programs i installed on my system. And each time I boot I see it on the start up list(or whatever it's called), does that mean i don't have to start it's GUI? does it automatically start when you boot?

---

### Post by slipk487 on 2006-04-11
if its set to boot when the machine is loged on then it should ask u a password to start it

---

### Post by dreamsINdigital on 2006-04-11
Isn't the GUI the only thing that Firestarter does?  The firewall itself should be always on, whether or not you have Firestarter installed/enabled, as far as I know.

---

### Post by Ob1 on 2006-04-11
yea, it asks for a password everytime i boot.

---

### Post by slipk487 on 2006-04-11
then its starting up fine but if u close it out then it closes out firestart unless u check a prefence that says minimize to tray when closed

---

### Post by ice60 on 2006-04-12
here are some Firestarter commands, they are self explanatory

sudo /etc/firestarter/firestarter.sh status

sudo /etc/firestarter/firestarter.sh start

sudo /etc/firestarter/firestarter.sh stop

---

### Post by Ob1 on 2006-04-12
ice60 you should change your avatar, it makes it difficult for me to read your replies.

---

### Post by frodon on 2006-04-12
The firestarter GUI is useful only the first time you firestarter to configure rules or when you want to changes the rules, except that the GUI is useless. 
Firestarter is a front end for iptables, what it does is translating what you choose in the GUI in iptables rules.
Thus firestater generates for you an iptables script which is handle by the firestarter init.d script therefore all the iptables rules are loaded on boot before the login screen that's why you're not asked for a password to start the firewall on boot.
To bring more insight, the ubuntu firewall (also the firewall of kernel > 2.4) is netfilter and iptables is a language to handle netfilter : [http://www.netfilter.org/](http://www.netfilter.org/)

---

### Post by ice60 on 2006-04-12
[QUOTE=Ob1]it makes it difficult for me to read your replies.[/QUOTE]
that's probably not a bad thing, you might miss all my mistakes that way :D 
[http://www.deviantart.com/view/11117162/](http://www.deviantart.com/view/11117162/)

---

