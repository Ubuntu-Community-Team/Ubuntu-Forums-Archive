---
title: "Firewall...Ubuntu have one already or do I need one?"
date: 2011-10-27
forum: Security
---

### Post by RotorRick on 2011-10-27
Was just browsing throught the Software Center looking for browsers, and found:

"Firestarter - desktop firewall tool"

Which got me thinking: Does Ubuntu come with a firewall already, that I didn't know about? If so, is it activated by default, or do I need to turn it on?

Do I even NEED a firewall? I'm assuming I should have one.

Which firewall programs would you recommend to a n00b to the Linux world?

Are there any other security programs that I should really have for my Linux/Ubuntu system?:confused:

Toshiba laptop, Ubuntu 10.04 LTS

---

### Post by spiky001 on 2011-10-27
Hi by default you are safe regarding firewall, If you have enabled a service like ssh, web server then you need a firewall. Fire starter is obsolity now. Ufw is installed as standard (gfuw) is the graphical front to ufw. If you have a router then they normally have a firewall installed in them. Hope this helps

---

### Post by Gremlinzzz on 2011-10-27
sudo ufw enable

:popcorn:

---

### Post by pierreyy on 2011-10-27
hey !

 check this out:

>  [http://ubuntuforums.org/showthread.php?t=1857298&highlight=haqking+security](http://ubuntuforums.org/showthread.php?t=1857298&highlight=haqking+security) 


 that should answer your question... enjoy!

---

### Post by Dangertux on 2011-10-27
Ubuntu does come with a firewall , however by default it is disabled. In my opinion you SHOULD use one. However there are probably quite a few people on here that will argue that point with you. There are many reasons you should use a firewall.

As far as what the firewall is and how to enable it the Firewall utilized by Linux is the kernel modules encapsulated in the iptables/netfilter framework. You can interact with it directly by writing iptables rules.

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Or you can utilize the front end Ubuntu provides for it called UFW.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Things like Firestarter are also front ends for the iptables/netfilter framework like UFW. They are not necessary and conflict with UFW. Remember that all of these are controlling the same thing.

Other security applications you should regard with importance are a browser extension like NoScript for Firefox or NotScripts for Chrome. Additionally you should look into learning to use Apparmor to create confinement profiles for your applications.

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

For information on how and where a firewall can and can not protect you consult the following article I wrote that essentially sums up the debate on why you SHOULD (imho) use a firewall, while also clearing up some of the misconceptions behind firewalls in general.

[http://dangertux.wordpress.com/2011/10/03/a-firewall-is-not-a-catch-all/](http://dangertux.wordpress.com/2011/10/03/a-firewall-is-not-a-catch-all/)

I hope this helps. Additionally look at the security stickies on this forum

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by haqking on 2011-10-27
I would refer you to this current thread as a discussion to educate yourself

[http://ubuntuforums.org/showthread.php?t=1863680](http://ubuntuforums.org/showthread.php?t=1863680)

Netfilter is in the Linux kernel and managed through IPTables.

IPTables is most commonly managed through UFW or the graphical GUFW front end.

Firestarter is out of date and bug rich IMO.

for a basic configuration (i wont go into the whys and wherefores of whether you need one as it is discussed everywhere)

however this:

```
sudo ufw default deny
```

```
sudo ufw enable
```

I would remind you that nothing is 100% secure and security is not a product but a process and best works in a layered approach.

education is the best firewall/anti malware/ security solution you can get.

peace

Edit: ninja'd by dangertux above, he gets everywhere ;-)

---

### Post by Dangertux on 2011-10-27
@haqking - you know I couldn't resist ANOTHER one of these threads ;-)

---

### Post by haqking on 2011-10-27
> **Dangertux said:**
> @haqking - you know I couldn't resist ANOTHER one of these threads ;-)

Stay away and take your heart pills ;-)

---

### Post by weezyrider on 2011-10-28
While I'm interested in security, I'm more interested in maybe it should be called a nuisance.

My laptop uses XP and a lot of times online I get the message "Object blocked by Online Armor." Now the object in question is either Bing or Groupon. Both are already in the hosts file. And the message about being blocked is satisfying.
Bing is sneaking in as an addon in almost everything you download. Mozilla is bringing out a FF/Bing only browser. 
Would you be able to block a browser like that in Ubuntu? I know you can uninstall it. 

I'm using Ubuntu since I don't care what MS wants - if MS wants it, I usually don't. Nor do I like Apple's benign dictatorship.

But these stupid apps are in the browsers and not on the desktop/system. How would I prevent either app from ever running in Ubuntu 10.10?  There's another coupon site I would also like to ban. 

I saw the posts on IP tables and they didn't seem to apply. What's nice about Online Armor is I just tell OA to block and it does.

---

### Post by Dangertux on 2011-10-28
Due to the nature of Ubuntu and Canonical's views on proprietary software, I wouldn't think a proprietary browser would be much to worry about.

Like you said if you don't want to use it don't install it.

As far as neutering functionality through the hosts file, the same applies in Linux/Ubuntu. The host file can be found in 

/etc/hosts

As far as application security, you may wish to look into Apparmor further if you truly want to limit what your applications can use.

Hope this helps.

---

