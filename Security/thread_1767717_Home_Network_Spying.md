---
title: "Home Network Spying"
date: 2011-05-26
forum: Security
---

### Post by firefoxftw on 2011-05-26
Hi there. This story is a bit lengthy, but I feel I must fully explain my situation.  
 

 I currently share cable internet with my roommates, one of whom has the modem and all the network hardware in his room. I was the last to move in, so instead of a wired connection I just connect to the wireless network which is provided “free” with my rent. A couple months ago I discovered through overheard conversations and direct clues that the roommate with the modem had been somehow watching all of my traffic while I was online. He referred to conversations I had on facebook, emails, sites I had visited, etc. At first I figured that my computer (which is not mine but a borrowed laptop) is running windows, and the security on windows is so poor that anybody could hack into the computer itself. I installed Ubuntu immediately, started up GUFW firewall, changed all my passwords, and hoped for the best. I came to find out later that this had not changed anything, as I overheard him talking to another roommate and referring to an obscure story I had dug up online (privately), asking why anybody would be reading about something like that. I realize I need some advice from professional geeks.
 

 My questions (Feel free to answer just one, I really don't know where to begin with this query):
 

 --Due to the tentative nature of my stay, I cannot afford to confront the roommate with this. What are my technical options? (besides going to starbucks every time I want to go online). What should I be thinking about as I try to secure my personal connection?

 

 -Are there tools or procedures that can make me invisible or shielded on the home network, so he will not even know if I am online?
 

 -Is there a way to know when I am being spied on from my own home network, for example a program which can alert me?
 

 -Can I encrypt my connection somehow so he sees junk, but on the other end I am decrypted and can browse the internet normally? I guess this would require some kind of specialized proxy service or another computer set up for remote access by me?
 

 -What are some good programs to know everything there is to know about my home network? Are there any good tutorials you know of that can explain any of this?
 

 -Are there better firewall tools for ubuntu besides GUFW? I know this one is supposed to be simple and small, but I'm not too familiar with the appropriate way to set it up and I would rather trust my computer to a larger, more comprehensive firewall program, just in case he IS trying to directly access my computer.
 

 If you can help with any information, I would really appreciate it. I may be living here for quite a while because of money, and I wish I could partake of the free cable internet without some creeper watching my every move. :(

---

### Post by jamesjenner on 2011-05-26
G'day mate,

Not a nice situation your in, that's for sure.

I have students stay with me and as such I run IPCop. As a part of IPCop I use the adv proxy plugin and run it as transparent. This lets me use blacklists and so on to restrict access for the students to undesirable content. When I get a new student I will keep an eye on what they're looking at for a short period, mainly because the white lists don't get all the Asian sites that I wish to be banned.

To be honest I'm surprised at times what the proxy logs will pick up. Unless the guy is sniffin packets, I suspect he's just got a proxy and he's monitoring what your looking at. If your url shows HTTPS then all he will know is that you've looked at a website but he will not know what you posted to the website or what you viewed. If your using online email (eg. gmail) then this should be the case and he shouldn't be able to read your email. I'm not familiar enough with POP3 and so on to know if it's secure, you may have to investigate. 

As for stopping him from seeing what your looking at, well a third party proxy is the solution. Try googling open proxy and click on the first link. If it's blocked then you know he's monitoring what your doing and actively blocking what you can access.

There are VPN services that you can subscribe to. People do it to become anonymous on their P2P activities. I'm not sure on the prices but it may be worth the price just so you know he cannot look at what your doing.

Hope that helps.

James.

---

### Post by Grenage on 2011-05-26
Assuming that you really don't want to report this disagreeable fellow (I'd use harsher words) or confront him, I would use a basic VPN/proxy service.  If you're only browsing the web then speed should not be an issue, and the cost relatively low.

While they could be ok, you'd obviously want to change the passwords to any site you've used since being there - but change them from another connection.

---

### Post by jamesjenner on 2011-05-26
Oh I should have said in my post (but forgot) that a transparent proxy is exactly that, it's not obvious that your using it. I suspect that is what the drop kick is using. Though it may be more.

---

### Post by blujay on 2011-05-26
This is an interesting situation you are in!  I feel sorry for you, and I almost feel sorry for that other fellow as well: he needs to get a life!  I imagine him feeling so proud of himself, as if he has a little power domain of his own.

Well, you were wise to install Ubuntu, but that doesn't fix this problem, I'm afraid.  It's likely that James is right, that he's using a transparent HTTP proxy.  This is easy to circumvent: just use a proxy of your own **with SSL**.  If you don't use SSL, it won't change anything.  You also must be absolutely sure that the certificate is valid while you're surfing through your SSL proxy, otherwise he could be conducting a man-in-the-middle attack.

You said he had mentioned some of your email, but you didn't mention how you access your email.  If you use, e.g. Gmail over SSL, he wouldn't be able to sniff the cleartext traffic, unless he did a MITM--again, is your browser showing a valid cert?

If you're not using webmail, but POP3/IMAP/SMTP, you can still use SSL (and always should, as you should know by now), and should still take any cert warnings very seriously.  Thunderbird supports SSL, and so does KMail (KMail also makes it very easy to discover the right SSL/TLS settings, rather than trial-and-error).

However, neither of those solutions provides complete protection: DNS requests will still leak (though you may not care about them), and other protocols or apps may leak or may not respect proxy settings.

How long are you going to be in this situation?  Can you afford about $10/month?  I recommend opening an account with Dreamhost.  Then you can simply open an SSH tunnel with a SOCKS proxy, e.g.:```
ssh -D 8080 user@dreamhostaccount
```  Then you can set Firefox to use that SOCKS proxy (make sure you turn on the about:config flag to make DNS use the SOCKS proxy also), and then all of your Firefox traffic, whether SSL or not, will be tunneled through SSH and opaque to your attacker.  However, I won't promise that 100% of it will be--I'm not sure if, for example, some Flash applets may ignore proxy settings.

However, after doing that, you could set up a firewall on the laptop to block all outgoing traffic except that to the Dreamhost server.  There's probably a way to use the firewall to redirect traffic through it automatically, too, but I haven't researched that ("apt-cache search socks" is a good starting point).

You might also consider something like Anonymizer, but I haven't even been to their web site in years, so I can't vouch for them.  I'm sure there are also some VPN services that are as cheap as or cheaper than Dreamhost--some probably even work well with Ubuntu and would provide more complete coverage with less configuration.  Google is your friend here.  :)

Regarding passwords, whether he's using a MITM proxy or just using something like Firestarter (script kiddie, for sure), you should consider all (and I do mean all) of your accounts compromised.  He might not actually have your passwords, but he might have cookies or tokens that give him access to your accounts.  As long as those are valid, he can access your accounts and perhaps change your passwords as well, depending on the specific sites.

As soon as you get a secure channel up, you should change all of your passwords on all of your accounts, and you should consider changing any account-verification information as well.

The thing about network security is that it is hard--even the pros make mistakes (just look at all the attacks Sony has suffered lately).  If you are under attack, it's not the best time to learn about it--well, in a way it is, I suppose, but not if you have something to lose.

Let us know how it goes!

---

### Post by spynappels on 2011-05-26
If your parents/guardians have a good internet connection, consider running a VPN server there and connecting to it for all surfing, most likely this would involve less cost if there is a spare computer which could be left on constantly. You can use OpenVPN for this, and it will work on both Windows and Linux, for both the Server and Client modes.

---

### Post by bodhi.zazen on 2011-05-26
1. Get your own internet access - problem solved.

Short of that you will need to tunnel your traffic, over a VPN or ssh.

---

### Post by tgm4883 on 2011-05-26
> **bodhi.zazen said:**
> 1. Get your own internet access - problem solved.

Short of that you will need to tunnel your traffic, over a VPN or ssh.

+1. SSH tunneling FTW

---

### Post by emiller12345 on 2011-05-26
When I heard 'Roommate', I also hear 'Physical Access'.  Check for unusual wire connections on your computer.

---

### Post by Irihapeti on 2011-05-26
> **bodhi.zazen said:**
> 1. Get your own internet access - problem solved.


Sometimes "free" comes at too high a price.

---

### Post by firefoxftw on 2011-05-26
Thank you for all your responses, I am researching ALL of them! :) It may come down to actually having to pay for my own internet connection as I feared. I simply can't afford too many extra monthly payments right now, but if I'm certain my security is compromised I guess I'll have to cut back somewhere else!

I'm very interested in the proxy service because it may be much cheaper for me if it solves the problem.

---

### Post by djchandler on 2011-05-27
Just a thought about being confrontational. If this was me, I'd be getting all my money back and moving to a different place.

This creep is invading your privacy. If he advertised the room to rent and listed free internet access as one of the perks, then he could be legally obligated to also provide some assurance of privacy. He may be violating the law depending on where you are located. I would contact local law enforcement and see what the legal ramifications may be.

In the meantime, treat the situation as if you are using public internet access. The proxy, VPN and SSH suggestions are all good ones.

This would make a good case on The People's Court.

---

