---
title: "Need help with blocking websites in Firefox v.65 (64 bit)"
date: 2019-01-31
forum: Ubuntu, Linux and OS Chat
---

### Post by la.khan on 2019-01-31
Hi all,

I need help with blocking website(s) on my laptop. Till recently, I used /etc/hosts to list websites I wanted blocked on my laptop. This used to work fine with both Chromium (v. 71) & Firefox (v. 64 64 bit).

However, recently, I upgraded Firefox to v.65 (64 bit) and it finds & loads websites I listed in /etc/hosts. In my research, I found that Firefox does not query the OS about /etc/hosts anymore; it uses cloud-flare DNS service to load website(s). I have verified that Chromium does NOT load any of the websites I listed in /etc/hosts.

I could install a Firefox extension (for ex. uBlock Origin) that blocks website(s). But, this is user specific and can be easily over ridden. Is there a way to stop Firefox from loading website(s) for all user accounts on my laptop, protected by admin privileges? Any ideas/suggestions/workarounds?

OS: Ubuntu Linux 18.04 LTS (64 bit); Gnome 3.28.1; Firefox 65 (64 bit); Chromium 71.0.3578.98.

Thanks for your help!

---

### Post by TheFu on 2019-01-31
I don't have v65, still on v64 here, and haven't done any research about this change, but suspect there is a way to disable it somewhere in the FF preferences.

FF bug report: [https://support.mozilla.org/en-US/questions/1197204](https://support.mozilla.org/en-US/questions/1197204)  has inks to steps that seem to start working as needed later, magically, according to posts there.  Clearing the cache is important.

If /etc/hosts isn't being used anymore, I suspect only the firewall will work as a local solution.  
Which firewall interface are you using?

If you have another system or an unused raspberry-pi, something like pi-hole might work, at least on the LAN you control.
 [https://pi-hole.net/](https://pi-hole.net/)

---

### Post by maglin2 on 2019-01-31
Possibly set[COLOR=#1A1A1B][FONT=&amp] network.trr.mode = 5?
[/FONT][/COLOR]https://www.reddit.com/r/sysadmin/comments/94r885/firefox_will_soon_be_sending_all_dns_requests_to/

---

### Post by Dennis N on 2019-01-31
Consider the "Block Site" Firefox extension.

---

### Post by la.khan on 2019-02-01
Hi all,

Thanks for your replies!
> 
If /etc/hosts isn't being used anymore, I suspect only the firewall will work as a local solution.  Which firewall interface are you using?

I have ufw 0.35 currently installed. I looked at Google to see if I can use ufw to block access to website(s). This can be done with IP addresses, not by URLs. This also gave me the idea to look at iptables. Turn off access using iptables. These will be applied to all users of my laptop; to change the iptables, any user of my laptop will need admin privileges. This is my preferred solution.
> Consider the "Block Site" Firefox extension.
That may work, but that is user specific. Also, user can disable the extension :(
> Possibly set[COLOR=#1A1A1B][FONT=&amp] network.trr.mode = 5?[/FONT][/COLOR]
I looked at Firefox's about:config. For my user account, it was set to 2. I changed it to 5 and all access to website(s)/URLs listed in /etc/hosts file was turned off :) But again this is user specific. I have login to each user account to set it to value of [COLOR=#1A1A1B][FONT=&amp]network.trr.mode to 5.

I logged into admin account and see that [/FONT][/COLOR][COLOR=#1A1A1B][FONT=&amp]network.trr.mode is set to 0 (default). My admin account cannot access any of the [/FONT][/COLOR]website(s)/URLs listed in /etc/hosts. Same with my wife's account. I verified access to website(s)/URLs listed in /etc/hosts from her account. By default, [COLOR=#1A1A1B][FONT=&amp]network.trr.mode is set to 0, and this setting gives[/FONT][/COLOR] no access to website(s)/URLs listed in /etc/hosts.

I logged into my account, changed [COLOR=#1A1A1B][FONT=&amp]network.trr.mode to 0 (default). I cannot access any of the [/FONT][/COLOR]website(s)/URLs listed in /etc/hosts :D Though my problem is resolved, my preferred solution is to work on iptables so that I am not dependent on FF config settings.

---

