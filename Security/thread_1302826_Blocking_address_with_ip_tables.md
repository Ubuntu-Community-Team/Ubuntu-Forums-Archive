---
title: "Blocking address with ip tables"
date: 2009-10-27
forum: Security
---

### Post by jmore9 on 2009-10-27
I keep blocking a ip by using the following but i keeps coming back !

What am i doing wrong here ?

This is the format i used ( not the correct ip of course )

iptables -A INPUT -s 111.222.33.444 -j DROP #

They keep returning and i keep blocking them.

---

### Post by dummy910 on 2009-10-27
you can also place and addy into your host file to prevent sites from loading.
```
gksudo gedit /etc/hosts
```
then place say a line that states:
127.0.0.1  111.222.33.444

for those interested in pesky ad-site blocking via the above method, check out the following text-file.
[http://www.mvps.org/winhelp2002/hosts.txt](http://www.mvps.org/winhelp2002/hosts.txt)

---

### Post by lovinglinux on 2009-10-27
You can also use [moblock](http://moblock-deb.sourceforge.net/) or [iplist](http://iplist.sourceforge.net/).

---

### Post by Ghostbear121 on 2009-10-28
You don't happen to have INPUT set to "accept" do you? ;)

Also check that you aren't appending (-A = append, right?) AFTER an 'allow-all' rule or something.  Insert the IP blocking rules at the top of your list of rules, instead of at the bottom.  See if that helps.

---

### Post by Lars Noodén on 2009-10-29
As ghostbear mentions, you want the new rules to be in the right place.  --append puts the rule at the end of the chain, so if there was an earlier --jump ACCEPT that matches the packet then the packet gets accepted.

Try
iptables [b]-I[b] INPUT -s 111.222.33.444 -j DROP #

For connections that have a chance of coming from legitimate hosts, please consider [using the target REJECT instead of DROP](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject).

---

### Post by jmore9 on 2009-10-29
OK I will try both of them i was doing it a little different

thanks for your time

---

