---
title: "Can't login to bankofamerica.com"
date: 2010-10-29
forum: Security
---

### Post by bcelli on 2010-10-29
Apologies in advance if this is a noob question or answered elsewhere, but I've tried a bunch of things already and searched around the web for an answer to no avail...
 
The problem I'm having is that with my newly installed Ubuntu 10.04, I can't seem to log in to my online banking with Bank of America. What happens is I get to their home page, enter my id, try to sign in, then it starts to load the page with the "site key" where you enter your password, loads it about halfway, then just redirects me back to the home page.
 
I tried the simple stuff like clearing cookies and cache, and making sure pop-ups are allowed for the site. Primarily I've been trying to get this to work with Firefox, but also downloaded Chromium and got the same problem. I also tried from another machine (my old laptop) with the same version fo Ubuntu and Firefox and got the same problem. I can get to any other site I've tried, and logged into other secure sites for credit card companies, etc. I also changed the id I log in with to be an administrator in case there was a permissions thing going on. I installed additional flash plug-ins, disabled ad-block, and a bunch of other settings tweaks and nothing seems to change.
 
What confuses me is that with a fresh install on two different machines I get the same problem with a broadly used web site like BoA, so I have to imagine this is something common / simple. After some pretty extensive searching though, I can't seem to find anyone else having posted this same problem. Am I missing something obvious here?
 
Thanks in advance.

---

### Post by amendt on 2010-10-29
I don't think you have to worry about this being a newbie question. So your browser (Chromium / Firefox) locks up when it tries to do run this script <script language="JavaScript" type="text/javascript" src="sas-docs/js/oasSignon.js"> </script> <script language="JavaScript" type="text/javascript" src="sas-docs/js/pm_fp.js"> </script>  I did a cntl-u to get this info.  Your trouble shooting was great -- you reproduce the error on different computers and different browsers.  
You might try User Agent Switcher

---

### Post by bcelli on 2010-10-29
Thanks for the quick response. I haven't tried User Agent Switcher yet, but will when I have a chance later.

---

### Post by bcelli on 2010-10-29
No luck with User Agent Switcher, same problem occurs. I'm currently playing with Wine, but no luck so far.

---

### Post by cariboo on 2010-10-29
Instead of using wine, I'd suggest running XP in virtual-box.

---

### Post by tgm4883 on 2010-10-29
Just logged into it fine on my 10.04 system

---

### Post by bcelli on 2010-10-29
Trying that next, but it seems like a bit of a pain just to get to one web site. If it works I'll go with it though ... IE in Wine had the exact same problem so that's ruled out.

I'm wondering if there's something else going on here, but curious that I can recreate the same exact problem on two different PCs, and wondering why this isn't more wide spread. Assuming BoA is a popular bank and with a fresh install of Ubuntu + Firefox I can't log in, shouldn't a lot of other people be having this problem?

---

### Post by stvdel on 2010-10-29
I had trouble logging on to a bank website a while ago and it turned out to be the Adblock plus Firefox add-on that was causing me trouble. You might want to try to start a fresh Firefox profile and try to log in with that.

---

### Post by nevius on 2010-10-29
The following are a few random stabs in the dark at a solution to this problem.

1) Try setting your privacy settings to their defaults and disable things like noscript / adblock.

2) Check for updates to your computer. It might be that the website detects vulnerable versions of browsers and won't let them connect.

3) Try using opendns - Click on System>Preferences>Network Connections then click on your network card and then 'edit'. Go to IPv4 Settings and change the Method to "Automatic (DHCP) addresses only". Then set your DNS Servers to "208.67.222.222, 208.67.220.220"

---

### Post by OpSecShellshock on 2010-10-30
Also, make sure that you're allowing cookies for the bank's website.

---

### Post by Velnias on 2010-10-30
Sorry to hear bcelli, rumors says, that all people from Redmond have difficulties with Linux.
I suggest You moving to Oregon - according tgm4883, there Ubuntu works just fine.

---

### Post by florus on 2010-10-30
Look in Preferences>Privacy>Exceptions and make sure that no BoA website is listed there.

---

### Post by WeAreLinux on 2010-10-30
Some more "stabs in the dark" :)

1) Try logging in BOA's alternative website:

[https://www4.bankofamerica.com/](https://www4.bankofamerica.com/)

Source: [http://www.businessinsider.com/how-to-access-your-account-online-while-bank-of-americas-website-is-down-2010-1](http://www.businessinsider.com/how-to-access-your-account-online-while-bank-of-americas-website-is-down-2010-1)

[http://en.wikipedia.org/wiki/Business_Insider](http://en.wikipedia.org/wiki/Business_Insider)

It seems to be a legit BOA website, but personally I would still be cautious.

2) Have you tried logging in with Opera? You never know.

[http://www.opera.com/](http://www.opera.com/)

3) Try contacting Bank of America. Maybe it's a reported problem in your area? or on their end?

---

### Post by bcelli on 2010-11-01
Thanks for all the suggestions. That at least gives me some new things to try. This is starting to drive me nuts, to the point where the suggestion to move to Oregon even sounds somewhat reasonable.
At this point I'm pretty much convinced it has nothing to do with the browser, or possibly even the OS. I followed the suggestion of VirtualBox, and with a clean XP SP3 install using IE I got the same exact problem. The only thing I did do is make sure pop ups are allowed for BoA. I can still log in fine with my work laptop from home which runs XP.
At this point I'm thinking it has something to do with whatever the BoA site does to identify the PC. It must be something more complex than just checking for a cookie, but I seem to recall that the first time you log in from a new computer it asks some extra security questions (it's been a while since I had to do that). Perhaps it's getting confused somehow because they've retained some record of me connecting with this same PC when it ran windows? Maybe that's a stretch, but I'm grasping at straws at this point.
Anyway, the good news is now with VirtualBox I can at least call BoA and expect some degree of tech support since I can say I'm running Windows now.

---

### Post by Jive Turkey on 2010-11-02
My first suggestion even if you aren't having this problem is to use a different bank.  BoA is evil.

One thing that is probably the same between all of the OSes you have tried is the DNS, forgive me for not reading the entire thread to see if you tried using a different DNS (ie OpenDNS).

---

### Post by tgm4883 on 2010-11-02
> **Jive Turkey said:**
> My first suggestion even if you aren't having this problem is to use a different bank.  BoA is evil.

One thing that is probably the same between all of the OSes you have tried is the DNS, forgive me for not reading the entire thread to see if you tried using a different DNS (ie OpenDNS).

Why is BoA evil?

---

### Post by bcelli on 2010-11-08
I'm not sure what BoA's alignment is, but I did finally solve  my problem. After trying much of the advice provided above and  continuing to be frustrated by the same problem, I tried something  simpler: I asked someone else to login to their BoA account from my  computer. And it worked. Logged into my own account from another PC, changed my user name, and now all of a sudden it works. I think it must be some info BoA keeps on their end associating an ID with a PC that got confused after the new install. Perhaps by MAC address if they can get that? At any rate, I'm all good now, though curious if others that install a new os on their pc would have the same issue.

Thanks again for everyone's help.

---

