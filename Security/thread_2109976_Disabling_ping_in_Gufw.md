---
title: "Disabling ping in Gufw"
date: 2013-01-29
forum: Security
---

### Post by jsvidyad on 2013-01-29
Hello, 

   How do I disable replying to ping requests in Gufw? I am asking with reference to ubuntu 12.04.

---

### Post by Soul-Sing on 2013-01-29
You need to edit /etc/ufw/before.rules and remove the following lines:

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

or change the "ACCEPT" to "DROP"

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

or better
# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

---

### Post by Lars Noodén on 2013-01-29
> **Soul-Sing said:**
> or change the "ACCEPT" to "DROP"

It's often better to use REJECT instead of DROP, especially if you are going to be using the service yourself.  

[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)
[http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)

---

### Post by bodhi.zazen on 2013-01-29
Neither DROP or REJECTING a ping increases security because they can tell you are at the ip address.

There are a number of tools that will show you how this is done, but it is a bit beyond what we normally discuss here on the forums.

See nmap - [http://nmap.org/](http://nmap.org/)

What I do is rate limit ping.

[http://agix.com.au/blog/?p=2088](http://agix.com.au/blog/?p=2088)

[http://newartisans.com/2007/09/neat-tricks-with-iptables/](http://newartisans.com/2007/09/neat-tricks-with-iptables/)

Bottom line, IMO ...

The default settings with ufw/gufw are fairly tight and written by people who know security. If you want to change them, best do your homework first ;)

---

### Post by bodhi.zazen on 2013-01-29
> **Lars Noodén said:**
> It's often better to use REJECT instead of DROP, especially if you are going to be using the service yourself.  

[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)
[http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)

I agree, nice link

Additional iptables links

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)
[http://fedorasolved.org/Members/kanarip/iptables-howto](http://fedorasolved.org/Members/kanarip/iptables-howto)

---

### Post by Soul-Sing on 2013-01-29
> The default settings with ufw/gufw are fairly tight and written by people who know security. If you want to change them, best do your homework first 

lol, these suggestion are made by jamie stranboge and the devs of gufw.
# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

: [https://answers.launchpad.net/ufw/+question/26585](https://answers.launchpad.net/ufw/+question/26585)
etc etc etc

---

### Post by bodhi.zazen on 2013-01-29
> **Soul-Sing said:**
> lol, these suggestion are made by jamie stranboge and the devs of gufw.
# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

: [https://answers.launchpad.net/ufw/+question/26585](https://answers.launchpad.net/ufw/+question/26585)
etc etc etc

Not sure what you are getting at. You may agree or disagree with the default rules, I personally do not use them. 

BUT ...

My advice is that you understand what and why you are changing them before you edit the default rules.

IMO, ufw, and gufw even more so, is for people who do not want to be bothered to learn iptables and they just want to click an "enable" button. It serves this purpose well. When those people come to the security section to ask questions I think the best response is to educate them.

ufw is a great tool as the syntax is very similar to iptables.

At the end of the day, IMO, if you want a custom firewall, iptables is the best tool for the job.

---

### Post by jsvidyad on 2013-02-05
Isn't there any way to do this from the Gufw GUI without editing text files? I thought there was a proposal to include that in more recent versions of Gufw.

---

### Post by Lars Noodén on 2013-02-05
> **jsvidyad said:**
> Isn't there any way to do this from the Gufw GUI without editing text files? I thought there was a proposal to include that in more recent versions of Gufw.

There would be little to no point because the bad guys can find your computer just as easily without ping as with it.  Adding the ability to throttle the rate of pings might be useful but maybe not.  What problem are you trying to solve?

---

### Post by Soul-Sing on 2013-02-05
> **Lars Noodén said:**
> There would be little to no point because the bad guys can find your computer just as easily without ping as with it.  Adding the ability to throttle the rate of pings might be useful but maybe not.  What problem are you trying to solve?

shields-up test prob. with the FAILED testresult. :)

---

### Post by bodhi.zazen on 2013-02-05
> **jsvidyad said:**
> Isn't there any way to do this from the Gufw GUI without editing text files? I thought there was a proposal to include that in more recent versions of Gufw.

No, but you can file a bug report or feature request on LP.

I agree with the comments that disabling ping does little or nothing to increase security.

---

