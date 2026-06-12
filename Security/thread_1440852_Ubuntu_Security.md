---
title: "Ubuntu Security ??"
date: 2010-03-28
forum: Security
---

### Post by newpaul on 2010-03-28
OK, I know this question may seem to simple but I come from a Windows 
environment...


Can I run Ubuntu securely ??

I really like Ubuntu, but is it secure ?


I do a lot of online shopping and I don't want my credit card number to end up in enemy hands. Nor my DOB and SSN to become public record !!


With Windows I know most of the freeware Firewall/Virus scan/Spyware real time/scan tools to keep me reasonably safe. I also use several freeware admin/cleanup/optimizing tools to keep my Windows PC running quick and trouble free.


I've used several Linux platforms (Puppy Linux, Damn Small Linux and several others) and now have Ubuntu on one machine and Xubuntu on another machine.

However, I have yet to even put in the password to check my e-mail with the Linux machines, since I'm completely ignorant of security on Linux platforms.

So far, Ubuntu seems like an excellent full feature Desktop OS to replace Windows, but my lack of security knowledge in Linux makes me hesitant on using Ubuntu, or other Linux platform, as my primary OS.


Please educate me, on Linux and more specifically  , Ubuntu (and Xubuntu) security


Thanks in advance..

---

### Post by xnostradamusx on 2010-03-28
im not sure if this sticky would help you

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by slowth5 on 2010-03-28
In addition to bodhi.zazen's sticky that xnostradamusx provided, this article should help allay your fears.

[http://www.dedoimedo.com/computers/linux-security.html](http://www.dedoimedo.com/computers/linux-security.html)

---

### Post by ikt on 2010-03-28
> **slowth5 said:**
> In addition to bodhi.zazen's sticky that xnostradamusx provided, this article should help allay your fears.

[http://www.dedoimedo.com/computers/linux-security.html](http://www.dedoimedo.com/computers/linux-security.html)

That is an excellent link, thank you. :)

---

### Post by Jimtheplanner on 2010-03-28
Not sure if this helps.....

In my personal view having used Linux since Mark Shuttleworth was a mere boy. I would NOT go near windows to do any purchasing of banking on-line but that's just me.....

Oh and as for Linux I use it without any concerns or thought..

Jim

---

### Post by newpaul on 2010-03-28
Thanks to all for the responses..
 
After I get back from church I'm going to read through this and eval..
 
I did read the sticky: Ununtu Security before I posted, but it was dated July 2007 and I did not know if the info still applied.. i.e. back then not any/many viruses hitting Linux, but that was three years ago, what about now? But again, the other security info listed, password, changing root etc.. is more or less timeless and would still apply now.
 
I probably need to learn I bit about Linux from the command line. I probably would benefit from a Linux command line tutor site if I can find one. Nothing to deep just the basics.
 
Any other suggestions, please keep posting
 
 
Thanks

---

### Post by bodhi.zazen on 2010-03-28
> **newpaul said:**
> Thanks to all for the responses..
 
After I get back from church I'm going to read through this and eval..
 
I did read the sticky: Ununtu Security before I posted, but it was dated July 2007 and I did not know if the info still applied.. i.e. back then not any/many viruses hitting Linux, but that was three years ago, what about now? But again, the other security info listed, password, changing root etc.. is more or less timeless and would still apply now.
 
I probably need to learn I bit about Linux from the command line. I probably would benefit from a Linux command line tutor site if I can find one. Nothing to deep just the basics.
 
Any other suggestions, please keep posting
 
 
Thanks

The information in the sticky still applies.

I update the stick on a regular basis.

There are no known active viruses for linux. You system has been patched to the known viruses long ago.

For the vast majority of Desktop users :

1. Use strong passwords.

2. Use a router with a built in firewall or enable yoru firewall (single command - sudo ufw enable).

That's it.

If you need to "harden" Ubuntu, you will first need to understand how Linux works. Start with the security sticky. You can read the Hardening Debian manual as well.

DO NOT BLINDLY do these things, understand what and why you are making these changes. Blindly applying security advice without understanding why is bad practice on ANY OS.

---

### Post by movieman on 2010-03-28
> **bodhi.zazen said:**
> For the vast majority of Desktop users :

1. Use strong passwords.

2. Use a router with a built in firewall or enable yoru firewall (single command - sudo ufw enable).

That's it.


I would add:

3. Do not leave VNC accessible over the Internet; if you must run it, then forward the connection through ssh. VNC seems to be the vector for 99% of the attacks reported here.

---

### Post by bodhi.zazen on 2010-03-28
> **movieman said:**
> I would add:

3. Do not leave VNC accessible over the Internet; if you must run it, then forward the connection through ssh. VNC seems to be the vector for 99% of the attacks reported here.

I agree, but that is not a default setting, ie botha  router an dufw will block the connection.

Also, desktop sharing is not enabled by default.

---

### Post by Jive Turkey on 2010-03-28
In addition to what the others have said, beware of phishing scams.  It's probably the biggest vulnerability that you face at this point (having moved away from windows).  Consider using payment methods that don't hit your bank directly (ie debit cards).  Single use CC, CC's offer more protection against fraud.

Also keep in mind that many breaches occur with the vendors and banks not the clients' computers.

---

### Post by newpaul on 2010-03-28
question on the firewall..

I use a Linksys WRT54G router updated with the most recent firmware and of course the NAT firewall is on.  On the wireless side I use WEP and also MAC address filter it to only allow ONLY the computers in my house on the network.

my question.. do I still need to turn the soft firewall on via sudo ufw enable, or is the NAT on the Linksys all I need ?

based on the previous post it sounds like you indicate if the router NAT filter is present, then the soft firewall (sudo ufw enable) is not needed.  I have always realized the router hardware firewall is in fact the strongest firewall, and soft firewalls (at least in the windows environment) pale in comparison. However, I have always still installed a soft firewall for a "second layer" of protection just in case.

your thoughts..

---

### Post by bodhi.zazen on 2010-03-28
In general you will not need to enable a firewall on your desktop, your router is sufficient.

By default there are no significant listening services on Ubuntu, so there is nothing to firewall.

---

### Post by newpaul on 2010-03-28
thanks for clarifying on the firewall. I understand the hard NAT router firewall is enough, so I will not turn on the soft firewall.

---

### Post by slowth5 on 2010-03-28
> **newpaul said:**
> On the wireless side I use WEP and also MAC address filter it to only allow ONLY the computers in my house on the network.

This was a passing comment, but please know WEP is insecure and MAC filtering is trivial to overcome. This will deter most from joining your network, but someone with just a little knowledge can overcome your wireless security measures.

---

### Post by slowth5 on 2010-03-28
> **ikt said:**
> That is an excellent link, thank you. :)

Thank you, I'm glad you enjoyed it. :D The author simplifies a complex topic, but most of it is still good information. I've stumbled across a couple more good security articles on the site. It's worth exploring.

---

### Post by Random_Dude on 2010-03-28
> **bodhi.zazen said:**
> 
enable yoru firewall (single command - sudo ufw enable).


Is this advisable to do?

I'm a noob at linux, so the only security advice on firewalls that I heard so far was about not letting firestarter turned on.
Does this command provide additional security, or is it better not to do if you are inexperienced?

---

### Post by newpaul on 2010-03-28
Thanks for letting me know about the MAC filtering.  I knew that WEP was not the most secure, but I've had problems getting WPA to work on my router/PC, so I settled for WEP.  However, I thought the MAC address inclusion filtering gave me a more solid wall.  Thanks for letting me know it's a bit of a hole.

I'll consider working out my router config issues so I can go to WPA in the future.

---

### Post by slowth5 on 2010-03-28
> **newpaul said:**
> Thanks for letting me know about the MAC filtering.  I knew that WEP was not the most secure, but I've had problems getting WPA to work on my router/PC, so I settled for WEP.  However, I thought the MAC address inclusion filtering gave me a more solid wall.  Thanks for letting me know it's a bit of a hole.

I'll consider working out my router config issues so I can go to WPA in the future.

You're very welcome. Security is so complex, it takes all of us working together to make sense of it all. 

You seem to know what's going on, so I thought you were probably using WEP due to incompatibilities with WPA. There are just some inexplicable wireless bugs. I know I've dealt with my fair share. If you can sort out the WPA issue, then you could pretty much forget the MAC filtering. Take care.

---

### Post by rookcifer on 2010-03-28
> **newpaul said:**
> question on the firewall..

I use a Linksys WRT54G router updated with the most recent firmware and of course the NAT firewall is on.  On the wireless side I use WEP and also MAC address filter it to only allow ONLY the computers in my house on the network.

Flash that router with [Tomato.]("http://www.polarcloud.com/tomato")  If you have questions on how, just ask.

> my question.. do I still need to turn the soft firewall on via sudo ufw enable, or is the NAT on the Linksys all I need ?

The Linksys is all you need.  If you flash it with Tomato, it runs the same firewall as Ubuntu anyway (Tomato is nothing but Linux on a router, as is the factory firmware on Linksys routers -- they are all Linux).

---

### Post by EJeanmaire on 2010-03-29
In regards to phishing scams or man in the middle (and if you are going to use your credit card) make sure that if your browser tells you that the security certificate is invalid, impersonated, or expired... do not proceed.

---

