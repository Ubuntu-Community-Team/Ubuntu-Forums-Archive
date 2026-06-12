---
title: "5 Billionth search scam"
date: 2020-03-11
forum: Security
---

### Post by r-done on 2020-03-11
Hello,

I'm hoping someone could give me some help and guidance on this.  I use Kubuntu 18.04 and Firefox 73.0.1 (64-bit).  I was looking for web sites dealing in mattresses and in the search results was a site <snip>.  After clicking on the link, there was a slight delay and then a page appeared with animated confetti saying I'm Firefox's 5 billionth search and I've won a prize.   Thought it was a scam straight away and closed Firefox and restarted it.  Have used various flavours of Ubuntu for a few years now and never had anything like this before.  Did searches on net for info on the scam and it seems to be spread by adware.  I checked add-ons in Firefox and I only had 'OpenH264 Video Codec' and 'Widevine Content Decryption Module'.   As far as I can remember, I haven't installed any extra programs that didn't come from Kubuntu's software centre and these are only VLC player, LibreOffice, Chromium (only have this for testing in case have problem seeing a page in Firefox), Thunderbird mail, Cantata, K3b, ClamTK. In Firefox, I've gone to Help->Troubleshooting information->refresh Firefox which put everything back to default settings. I have since reset back to recommended settings described in [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) and now have just 'OpenH264 Video Codec' as the only plug-in (as it's automatically installed by Firefox).  Is there anything more I can do to safeguard myself?

Regards

Rob

---

### Post by EuclideanCoffee on 2020-03-11
First, I'm sorry that you felt so much anxiety over a typical search result. You shouldn't have such a negative experience just looking for furniture.

Now though it is possible to have adware or spyware or malware advertise to you specifically, in this case I think it's unlikely malware but a Javascript function that read your browser agent and created a popup using your agent to make it seem like it was specifically targeting you. These are things available to websites simply because you browsed their webpage. With Javascript, software that is rendered by your browser, which means Firefox runs the software, you write a program that knows the following items about you.

1. Your approximate location via your IP. Note, your IP is how your computer is addressed, and from this address a website and determine where you live easily.
2. Your browser and sometimes your operating systems. This is how websites typically determine if you need to use the mobile version of their websites for example.
3. Where you came from, your last click, meaning they know you arrived from Google or any other search engine website like duckduckgo.

What does this mean?

From this, we know that the website could've known all of this information without needing to spread malware, which is illegal and requires work. Because this is the easiest way to scam you, they will likely use the easiest method and not even worry about developing the malware you may have imagined. Though that malware is very possible, it's less likely in your situation.

You should be safe. But you may also want to reformat your machine if you'd like.

I'm writing some free software that I hope to have as an PPA (available to Ubuntu users) soon that should help with automating security vulnerabilities on your computer and assist with fixing them. Let me know if this would be something that interests you, and I can PM you the project. Or if anyone else is interested, simply send me a note via my visitor's page. I feel like posting in thread would be advertising, and I haven't checked the rules recently on that.

Additional recommendations:
1. Install addons that block scripts, such as ublock origin or umatrix.
2. Install addons that ensures your traffic is encrypted, such as HTTPS Everywhere.
3. Install addons for privacy such as privacybadger.

---

### Post by webaake on 2020-03-11
Totally agree with EuclidianCoffee. I recently clicked on an apparently ligit link in a google search and came to a site like the one you encountered.  I immediately closed the tab down and thought no more of it. Nothing happened here on my system or in my Google Chrome, so it is cool. What I think has happened is that that site got it's domain name hijacked somehow, and present crap and spam instead. The Google search engine doesn't always keep up with old or malfunctioning link/web sites.  

If you still feel un-cool you can uninstall Firefox and purge it. And delete it's config directory - /home/youruser/.mozilla Note the dot before .mozilla. And then reinstall it. You'll lose all settings you had in Firefox but......

---

### Post by r-done on 2020-03-12
Thanks, EuclidianCoffee, for the help and the reassurance.  I will follow your tips for making myself a bit safer.  I would also be interested in the utility your developing and be glad for you to PM me with your site.  Many thanks. 

Also thanks for your input Webaake.

---

### Post by ipv on 2020-03-14
> **r-done said:**
> I haven't installed any extra programs that didn't come from Kubuntu's software centre and these are only VLC player, LibreOffice, Chromium (only have this for testing in case have problem seeing a page in Firefox), Thunderbird mail, Cantata, K3b, ClamTK.

if you got clamtk you probably also have clamav. why not run a few scans? 

> **r-done said:**
> In Firefox, I've gone to Help->Troubleshooting  information->refresh Firefox which put everything back to default  settings.

better than refresh delete the firefox profile or uninstall reinstall firefox as already suggested. 

> **r-done said:**
> I have since reset back to recommended settings described in [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) 

enable firewall & install gufw. if you want a squeaky clean ubuntu avoid wine.

---

### Post by EuclideanCoffee on 2020-03-14
Since most threats are carried via port 80 or 443, which is web traffic, you can still receive what is called a "payload" even when firewalls are up. I'm not saying that firewalls don't help, but if you're largely browsing the web, it does you no good. Instead, look into enabling apparmor.

[https://flatlinesecurity.com/posts/firefox-apparmor/](https://flatlinesecurity.com/posts/firefox-apparmor/)

This explains the problem in more detail and provides you with some practical commands in the commandline.

---

### Post by ipv on 2020-03-14
> **EuclideanCoffee said:**
> Instead, look into enabling apparmor.

[https://flatlinesecurity.com/posts/firefox-apparmor/](https://flatlinesecurity.com/posts/firefox-apparmor/)



thanks.

---

### Post by ipv on 2020-03-22
> **EuclideanCoffee said:**
> look into enabling apparmor.

[https://flatlinesecurity.com/posts/firefox-apparmor/](https://flatlinesecurity.com/posts/firefox-apparmor/)



can this be done on debian too ? if yes please guide me.

---

### Post by EuclideanCoffee on 2020-03-23
Yes, exactly as it is written. Please post a new thread if you have a specific question about app-armor in Debian, as this thread has been resolved more or less.

---

### Post by ipv on 2020-03-23
> **EuclideanCoffee said:**
> Please post a new thread if you have a specific question about app-armor in Debian, as this thread has been resolved more or less.

[https://ubuntuforums.org/showthread.php?t=2439110&p=13940871#post13940871](https://ubuntuforums.org/showthread.php?t=2439110&p=13940871#post13940871)

---

### Post by somelinuxuser123 on 2020-04-02
Hi. I found this thread on Google. 

I've encountered the "5 billionth search" thing twice now. Once when I was looking up a Youtube video for learning Polish, which had a link in the video description, which was posted a couple years ago, for some small/unheard of site about learning Polish. That was a couple days ago. I immediately closed the browser tab. Today, when I googled a local business and went to their site, I encountered the "5 billionth search" redirect a second time. I'm using Linux. You go to the website, and then it instantly redirects to a different domain name. You clicked on the legitimate domain, but then it redirects and looks like a spammy domain name instead of the original link you clicked on. 

I don't have much installed on this computer. In Firefox, I have HTTPS Everywhere, LastPass, and uBlock Origin installed. No other extensions.

Do you think it's a phishing thing or a malware thing? 

My hypothesis is that, if someone were able to get malware on my computer, they'd be able to harvest info by doing keylogging or whatever. Why would they need me to manually input information into a website?

I think the more likely explanation is that someone found a way to hack websites running certain software, and makes them redirect to phishing sites. They hack legitimate sites, but maybe they're just running a really old version of Wordpress or something. Once a hacker knows a way to exploit a certain security issue on web server software, such as a CMS or something, they can do it any number of times. Maybe it's a known vulnerability (a CVE) because the website hasn't been updated in a while.

Neither the old Polish learning website nor the local business are tech companies. I also doubt they have a big budget for their website. They might've paid someone to set up a website, and then didn't bother with security updates. Many small/local businesses use CMSs, especially Wordpress. Wordpress can be secure if you install updates etc. but I'm guessing these small businesses don't know or care about security that much.

I don't think it's malware on my computer running Linux.

Long story short, I think the website got hacked, not my computer.

What do you think of my hypothesis?

---

### Post by EuclideanCoffee on 2020-04-02
It's a likely hypothesis. Thanks for sharing.

Could you please share the URLs with me if you still have them? Moderators will remove your post, so you can send them to me in a private message.

If it's a 0-day, I will need to notify Debian security.

It appears the common part of this problem is Google.

---

### Post by somelinuxuser123 on 2020-04-02
I don't remember the phishing URLs, and I don't remember the exact Polish learning website URL anymore (I cleared my history), but I do know the local business site, and I can message it to you if you want.

EDIT: Additional info: this might be completely irrelevant, but maybe not. I forgot to mention that I also have ExpressVPN installed on my computer. Is this related? No idea. Just including this info. I've also heard of router malware, too. Like I read about how hacked routers change DNS or something. But my router is running DD-WRT, recently updated, and with no remote access enabled.

I still think it's just a case of the websites being hacked and redirecting to phishing sites.

EDIT 2: the "billionth search" scam didn't appear every single time I visited the website. Also, I remember reading about something called a traffic distribution system a while ago, which is software on a web server (used by criminals) that can selectively redirect a user to a web page or malicious payload. It can be based on many different factors, like user agent, cookies, browser, browser version, OS, etc. So one user will go to the link and see one thing, and another user can go to the same link and be redirected to something else entirely. This might not be a TDS, but it is weird that the scam didn't show up every time.

EDIT 3: one of the websites I visited that had the "billionth search" redirect is in fact using Wordpress (and a ton of plugins). These articles might be related:
[https://portswigger.net/daily-swig/url-redirect-malware-infects-thousands-of-wordpress-sites](https://portswigger.net/daily-swig/url-redirect-malware-infects-thousands-of-wordpress-sites)
[https://securityboulevard.com/2020/01/malicious-javascript-used-in-wp-site-home-url-redirects/](https://securityboulevard.com/2020/01/malicious-javascript-used-in-wp-site-home-url-redirects/)

Considering the fact that many people on social media complained about this same issue (websites redirecting to a phishing page), and they were on many different operating systems (iOS, Android, Windows, macOS, Linux), I think it's safe to say this is a website issue rather than a malware issue.

---

### Post by aminbahgat on 2020-04-03
> **EuclideanCoffee said:**
> First, I'm sorry that you felt so much anxiety over a typical search result. You shouldn't have such a negative experience just looking for furniture.

Now though it is possible to have adware or spyware or malware advertise to you specifically, in this case I think it's unlikely malware but a Javascript function that read your browser agent and created a popup using your agent to make it seem like it was specifically targeting you. These are things available to websites simply because you browsed their webpage. With Javascript, software that is rendered by your browser, which means Firefox runs the software, you write a program that knows the following items about you.

1. Your approximate location via your IP. Note, your IP is how your computer is addressed, and from this address a website and determine where you live easily.
2. Your browser and sometimes your operating systems. This is how websites typically determine if you need to use the mobile version of their websites for example.
3. Where you came from, your last click, meaning they know you arrived from Google or any other search engine website like duckduckgo.

What does this mean?

From this, we know that the website could've known all of this information without needing to spread malware, which is illegal and requires work. Because this is the easiest way to scam you, they will likely use the easiest method and not even worry about developing the malware you may have imagined. Though that malware is very possible, it's less likely in your situation.

You should be safe. But you may also want to reformat your machine if you'd like.

I'm writing some free software that I hope to have as an PPA (available to Ubuntu users) soon that should help with automating security vulnerabilities on your computer and assist with fixing them. Let me know if this would be something that interests you, and I can PM you the project. Or if anyone else is interested, simply send me a note via my visitor's page. I feel like posting in thread would be advertising, and I haven't checked the rules recently on that.

Additional recommendations:
1. Install addons that block scripts, such as ublock origin or umatrix.
2. Install addons that ensures your traffic is encrypted, such as HTTPS Everywhere.
3. Install addons for privacy such as privacybadger.
thank you alot

---

### Post by EuclideanCoffee on 2020-04-03
This is appears to be a virus.

Be sure to have all your updates installed and protection software installed as I mentioned earlier. I'll do some amateur digging.

Edit: Confirmed this is related to website hacking. Keep your browsing safe, everyone. :)

This website could possibly install software onto your computer. The best way to protect yourself is to not trust Javascript upon visiting a new website. See my post above, which is quoted.

---

### Post by somelinuxuser123 on 2020-04-04
Are you really sure it's a virus instead of just a redirect on the site itself? Aside from going to a site and seeing the "5 billionth search" page, nothing else happened. No weird activity on my computer or online accounts. Now that I avoid the two websites where I saw that redirect, I'm not noticing anything out of the ordinary on my computer. I ran a ClamAV scan and it didn't find anything. 

If you really think it's malware, I will reinstall my OS. But it's a hassle to do so. If it's just a website redirect, rather than malicious code on my computer, then I'd rather not do that.

---

### Post by EuclideanCoffee on 2020-04-04
I guess I mean it's a site exploit. But it's malware regardless. Avoid websites that redirect. I would reinstall my os if this happened to me.

---

### Post by alaudacorax on 2020-06-12
I ran into that scam a couple of months ago.

I ran a search (with DuckDuckGo). I chose the first hit, which seemed  a straightforward answer, and instead got a survey purporting to be by  Firefox. I was suspicious of it, so I tried to go back one page, but it  wouldn’t let, just dumping me on the same or similar pages. So I got  back to my seach via browser history, tried again, and the same thing  happened, but this time purporting to be a Google survey. So, I decided to search on this problem, something like ‘are these  firefox surveys real’, finding them to be scams. Firefox  advised checking your add-ons list for something suspicious. Well,  there was nothing on there that I didn’t put there, so I thought that  was a no go, but I did decide to remove Startpage which I'd installed a short time before but wasn't using any more. Then I clicked on that hit for a third time … and lo and behold  it went through properly to a kosher web page. Never had it happen before; never had it happen since.


 Perhaps not definitive proof, I know, but it certainly looks as if Startpage was my problem.

---

### Post by EuclideanCoffee on 2020-06-12
Interesting. I don't think StartPage develops an add-on. It could be that someone has maliciously placed an add-on on the market place with hopes someone may use it thinking it's official.

---

