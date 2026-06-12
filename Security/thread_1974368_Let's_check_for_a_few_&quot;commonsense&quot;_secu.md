---
title: "Let's check for a few &quot;commonsense&quot; security ideas:"
date: 2012-05-06
forum: Security
---

### Post by OpenSourceRules on 2012-05-06
1)  Do you install whatever programs you find on the Internet.
2)  Download only from reliable sources; media is a great way for intrusion.
3)  Do you use personal accounts on any public computers.

I guess many people have loads of experience with security, though.

---

### Post by confused57 on 2012-05-06
> **OpenSourceRules said:**
> 1)  Do you install whatever programs you find on the Internet.
2)  Download only from reliable sources; media is a great way for intrusion.
3)  Do you use personal accounts on any public computers.

I guess many people have loads of experience with security, though.

A lot of this has already been discussed, you can get useful security links in this thread:
[http://ubuntuforums.org/showthread.php?t=1873643](http://ubuntuforums.org/showthread.php?t=1873643)

The discussion in the above thread resulted in the Basic Security Wiki:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
I would advise anyone concerned about security in Ubuntu(or any other OS, for that matter) to read.

---

### Post by OpenSourceRules on 2012-05-06
One thing though: May people enjoy auto login, so encrypting the home folder isn't an option.
The truth is: I dont't do online shopping or any pecuniary businesses online anyway.

---

### Post by SparTacux on 2012-05-06
I use a separate user account for using the internet with auto log-in. I tend to delete that account on a week by week basis and create a new one just to clear it out.

I have another user account for my email which uses a password. Internet activity is strictly limited to email using a secure connection. Home Directory permissions have been changed on this account to stop other users reading the directory. It's possibly a good idea to use encryption on this home directory. I keep some confidential documents in here but most of my material is stored on a computer with NO network connection.

Local machine Firewall - deny all traffic in and use a restrictive outgoing policy - all of which are fully logged. Modem firewall also in place with similar restrictions on traffic. Again - all traffic fully logged.

Using fixed IP's on my LAN enables me to see what the computers are doing plus avoids any DHCP vulnerability issues.

Webrowser using NOSCRIPT. Javascript and Flash use strictly limited to trusted sites. Deny all cookies except trusted sites. 

I tend to use the whois tool quite a lot to see if I'm on a legit site especially when internet shopping or providing personal details. I view my browsing logs and check the IP's using whois just to be sure.

Behave yourself on line and don't attract any trouble :-)

These are just a FEW of the precautions I take.

---

### Post by rookcifer on 2012-05-06
> **OpenSourceRules said:**
> 1)  Do you install whatever programs you find on the Internet.

No, and neither should you.

> 2)  Download only from reliable sources; media is a great way for intrusion.

I only download from sources where the code is signed.  

> 3)  Do you use personal accounts on any public computers.

No.  Have no reason to really.

---

### Post by OpenSourceRules on 2012-05-06
> **SparTacux said:**
> I use a separate user account for using the internet with auto log-in. I tend to delete that account on a week by week basis and create a new one just to clear it out.

I have another user account for my email which uses a password. Internet activity is strictly limited to email using a secure connection. Home Directory permissions have been changed on this account to stop other users reading the directory. It's possibly a good idea to use encryption on this home directory. I keep some confidential documents in here but most of my material is stored on a computer with NO network connection.

Local machine Firewall - deny all traffic in and use a restrictive outgoing policy - all of which are fully logged. Modem firewall also in place with similar restrictions on traffic. Again - all traffic fully logged.

Using fixed IP's on my LAN enables me to see what the computers are doing plus avoids any DHCP vulnerability issues.

Webrowser using NOSCRIPT. Javascript and Flash use strictly limited to trusted sites. Deny all cookies except trusted sites. 

I tend to use the whois tool quite a lot to see if I'm on a legit site especially when internet shopping or providing personal details. I view my browsing logs and check the IP's using whois just to be sure.

Behave yourself on line and don't attract any trouble :-)

These are just a FEW of the precautions I take.

Do these add additional hassles?

---

### Post by Hungry Man on 2012-05-06
NoScript is a pain in the *** to use if your usage habits are similar to mine. It also breaks the web, which is why it works so well (XSS and CSRF are in fact features and entirely necessary for many websites to function.) Breaking standards is not the right way to handle security...

Setting up a firewall can be a pain but afterwards it's simple.

---

### Post by ubuntu27 on 2012-05-07
I used to use NoScript. But, now I replaced it with **Ghostery**. It is much more convenient.

---

### Post by SeijiSensei on 2012-05-07
> **ubuntu27 said:**
> I used to use NoScript. But, now I replaced it with **Ghostery**. It is much more convenient.

I think I put up with Noscript for about two days then dumped it.  I'm a big fan of Ghostery, and AdBlock Plus as well.

I can't imagine doing all the things SparTacux suggests, but then I rely on a small number of sites like Amazon for shopping.  I do use online banking with a strong password, and my bank's interface has some procedures that allow me to be sure I'm talking to my own account.  I run firewalls (two in fact), but I no longer log traffic at home since experience has taught me that there's little to be learned.  Lots of machines bang on my door every day; my firewall ignores them.  I have public machines out on the network where I do more extensive logging, but for my home I don't see the value.  

I've built firewall gateways for organizations that do a lot of logging and have quite elaborate rulesets, but mostly to keep track of users.  Blocking direct threats from outside the network is the easy part.  It's controlling what random users are doing that's harder.  We're very vigilant about keeping out malware and use a variety of tools to block executables that might be delivered by mail or over the web.  The biggest culprit is people bringing in infected USB pendrives; for that, my clients have to rely on their own Windows-based antivirus software.  If it were up to me, I'd fill the USB sockets on their computers with epoxy.  Letting people bring in laptops from home is another very difficult problem that I luckily don't have to deal with.

I use whois every once in a while, but since my only online transactions are with a few trusted sites, I'm usually not worried about the ownerships of the domains I visit.  My email resides on a server in my home forwarded over an OpenVPN tunnel from one of my public servers.  If I need to read my mail from outside, I have Squirrelmail running with SSL.  My wifi router uses WPA-PSK2 with a very long passphrase.  I have my own DNS server which communicates directly with the roots.

Oh, and I almost never install software except from the repositories in Linux, or in the few cases where I use Windows, from known commercial entities.  I occasionally build software from source; I've never been bitten by that practice either.  These days I can count on one hand the number of applications I use that I've built from source.  In some cases the code is quite a few years old now and has been in continous use over a long period.

I have followed these procedures for well over a decade without incident.

---

### Post by OpenSourceRules on 2012-05-07
No script means loads of inconvenience here&#65307; I gave it up at last, too.

---

### Post by SparTacux on 2012-05-07
> **OpenSourceRules said:**
> Do these add additional hassles?


It takes a bit of self discipline ;-)

When you've had your email lifted and all your private browsing habits exposed you tend to be a bit  more cautious than normal. Ubuntu can EASILY be breached - I've seen it done quite a few times. 

My main aim here is to protect my email and confidential data which is stored in a separate user account. Also Keeping most of your personal documents on a separate computer makes good sense to me.  
I'm not too worried about the internet account I use for browsing as the only data that's stored there are my latest downloads. Firefox options are set to clear all data on exit. No passwords are stored.  Using NOSCRIPT is easy enough after a while.

What you consider a trusted site may well be used as an attack site. It just takes one rogue employee to make it so. Keep that in mind.

 I'm probably seen as over cautious here but there is a good reason for it.

---

### Post by Ms. Daisy on 2012-05-07
> **Hungry Man said:**
> NoScript is a pain in the *** to use if your usage habits are similar to mine. It also breaks the web, which is why it works so well (XSS and CSRF are in fact features and entirely necessary for many websites to function.) Breaking standards is not the right way to handle security...

Setting up a firewall can be a pain but afterwards it's simple.
Did you just say that there are websites that need to use a vulnerability in order to function?

I'm going to need a source on this.  I googled and found source after source saying that xss is a vulnerability that needs to be fixed, but nothing saying what a handy tool it is for web development.

---

### Post by Hungry Man on 2012-05-07
Because XSS and CSRF are exploit techniques based on functions that pretty much need to exist. Kinda the same way SQL Injection exists because you can query an SQL Database. Sending data to the database is not a bad thing, it's just not handled properly and that's where the exploit is. 

We do not solve SQLInjection by preventing the user from submitting forms... we fix it by sanitizing input.

This is actually the same way we handle XSS and CSRF, same origin policy and checking headers and other methods.

XSS is when an attacker gets scripts onto a page and is then able to pull information from any other server. Of course... this is a necessary function of the web. Think of a web advertisement. You need multiple servers hosting information on the same page for embedded videos, for advertising, for all sorts of things.

Same origin policy tries to limit this damage.

CSRF is more complicated. I actually think I have a link for that. It's the same ideas though, there's a browser function that gets exploited - it's not a code vulnerability, it's a design standard.

If you'd like I can probably find a link explaining this further.

---

### Post by OpenSourceRules on 2012-05-07
> **SparTacux said:**
> It takes a bit of self discipline ;-)

When you've had your email lifted and all your private browsing habits exposed you tend to be a bit  more cautious than normal. Ubuntu can EASILY be breached - I've seen it done quite a few times. 

My main aim here is to protect my email and confidential data which is stored in a separate user account. Also Keeping most of your personal documents on a separate computer makes good sense to me.  
I'm not too worried about the internet account I use for browsing as the only data that's stored there are my latest downloads. Firefox options are set to clear all data on exit. No passwords are stored.  Using NOSCRIPT is easy enough after a while.

What you consider a trusted site may well be used as an attack site. It just takes one rogue employee to make it so. Keep that in mind.

 I'm probably seen as over cautious here but there is a good reason for it.

Doesn't matter; my email isn't even very important (I hardly receive any emails!), and due to frequent reinstallations, this computer doesn't even contain much in the way of information.

---

