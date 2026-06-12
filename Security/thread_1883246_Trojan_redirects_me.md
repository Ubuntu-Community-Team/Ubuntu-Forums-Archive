---
title: "Trojan redirects me"
date: 2011-11-18
forum: Security
---

### Post by lob0 on 2011-11-18
Hello guys.

I used to use windows 7. I'm very careful and all but somehow I got a trojan (at least I think it is one.) It redirects me to a weird hosting site full of ads when I try to go to some specific sites. I checked the same sites on other computers in my home network and mine is the only one with the problem. So formatted it. Three times. The last one was a low-level formating. The trojan survived. I had used Ubuntu before and was wating for a chance to go back to it, so I did. I downloaded the latest version of it, formated and installed it. It was trojan free for 2 days, but yesterday, it was back!

I got some experience with computers but I'm still new to Ubuntu.

Really need your help guys...

Thank you.

---

### Post by Dangertux on 2011-11-18
> **lob0 said:**
> Hello guys.

I used to use windows 7. I'm very careful and all but somehow I got a trojan (at least I think it is one.) It redirects me to a weird hosting site full of ads when I try to go to some specific sites. I checked the same sites on other computers in my home network and mine is the only one with the problem. So formatted it. Three times. The last one was a low-level formating. The trojan survived. I had used Ubuntu before and was wating for a chance to go back to it, so I did. I downloaded the latest version of it, formated and installed it. It was trojan free for 2 days, but yesterday, it was back!

I got some experience with computers but I'm still new to Ubuntu.

Really need your help guys...

Thank you.

Might I suggest next time you reformat using NoScript before visiting your favorite sites (which are likely hijacking your browser).

Also it's not a trojan (necessarily). It's more than likely a browser hijack, which is something entirely different.

What browser are you using?

---

### Post by whatthefunk on 2011-11-18
What browser do you use?  What version of Ubuntu?

---

### Post by lob0 on 2011-11-18
What's NoScript?

Is it normal for it to have survived all these formatings?

I'm using firefox on Ubuntu 11.10

---

### Post by CharlesA on 2011-11-18
> **lob0 said:**
> What's NoScript?

Is it normal for it to have survived all these formatings?

I'm using firefox on Ubuntu 11.10
It's an addon for firefox.

My guess would be it is just browser hijacking.

---

### Post by lob0 on 2011-11-18
> **CharlesA said:**
> It's an addon for firefox.

My guess would be it is just browser hijacking.

How do I proceed?

---

### Post by CharlesA on 2011-11-18
> **lob0 said:**
> How do I proceed?
Install that addon and see if you get redirected when visiting whatever site you are visiting.

---

### Post by Dangertux on 2011-11-18
> **lob0 said:**
> What's NoScript?

Is it normal for it to have survived all these formatings?

I'm using firefox on Ubuntu 11.10

It likely didn't "survive" anything. What I think is happening is your browser is being hijacked. This means that a piece of malicious code on a website you normally visit is exploiting a flaw in your browser that allows either your hosts file to be written to or your about:config to be modified.

It modifies it in such a way that certain popular sites will redirect you to whatever the creator of the code wants.

NoScript is an addon for Firefox that will help mitigate these types of malicious code from running. Configuration guide here : [URL="http://dangertux.wordpress.com/tutorials/ubuntu-no-script-configuration-guide"]http://dangertux.wordpress.com/tutorials/ubuntu-no-script-configuration-guide
[/URL] 
Ultimately, you are reformatting -- then when you reinstall you are likely visiting the compromised site again, which thusly recompromises your browser, so it APPEARS to be surviving but in reality is not.

Hope this helps.

---

### Post by SavageWolf on 2011-11-18
Uh, this is not what is happening, the OP said that this problem does not exist on other computers, and writing to the host file in Windows 7 is unfathomable.

What are the sites that get "hijacked"?

---

### Post by Dangertux on 2011-11-18
> **SavageWolf said:**
> Uh, this is not what is happening, the OP said that this problem does not exist on other computers, and writing to the host file in Windows 7 is unfathomable.

What are the sites that get "hijacked"?


Exactly, it would not persist on other machines, because about:config / hosts would not be changed on those machines. Writing to the hosts file in windows 7 is easy you'll find it in C:\windows\system32\drivers\etc. It's frequently written to , google some recent chrome vulnerabilities on both Windows and Linux and you'll find that it's happening.

So really you're left with a browser hijack or ARP poisoning. Since I doubt someone is sitting in front of the OP's residence re-arping their router. Alternatively DNS poisoning which is even less likely. Or you could have someone sitting around send ICMP redirect messages constantly.

In all reality the browser hijack is the most likely situation.

Also if your point was that he visited those sites on the other machines and those browsers would also be compromised.  This would only occur if the machines had the same vulnerable browser version OR if the OP even tested it long enough to trigger a redirected site.

---

### Post by haqking on 2011-11-18
> **SavageWolf said:**
> Uh, this is not what is happening, the OP said that this problem does not exist on other computers, and writing to the host file in Windows 7 is unfathomable.

What are the sites that get "hijacked"?

ha ha thanks for the laugh.

Your signature is a sure fire way of of getting a giggle from me ;-)

Peace

---

### Post by SavageWolf on 2011-11-18
What about a good ol' social engineering attack?

Also, he reformatted the computer 3 times, I'd expect him to have at least two different versions (Windows and Linuxes have different versions of Firefox). I'm not saying that this isn't a browser exploit, I'm saying that you should at least try to collect some information rather than yelling "ADBLOCK! NOSCRIPT!" Ugh...

Also, doesn't AppArmour protect against this sort of thing?

lob0, what sites are affected, and what browsers have you tried?

---

### Post by haqking on 2011-11-18
> **SavageWolf said:**
> What about a good ol' social engineering attack?

Also, he reformatted the computer 3 times, I'd expect him to have at least two different versions (Windows and Linuxes have different versions of Firefox). I'm not saying that this isn't a browser exploit, I'm saying that you should at least try to collect some information rather than yelling "ADBLOCK! NOSCRIPT!" Ugh...

Also, doesn't AppArmour protect against this sort of thing?

lob0, what sites are affected, and what browsers have you tried?

no offence but for someone with your signature you probably shouldnt be arguing or discussing the technologies involved in browser security ;)

---

### Post by SavageWolf on 2011-11-18
> **haqking said:**
> no offence but for someone with your signature you probably shouldnt be arguing about browser security ;)

Well done, rather than actually justifying your opinion, you have responded with arrogant hostility, now can we wait until the OP replys with anything interesting?

EDIT: After posting this, I edited my signature for clarity or something, here's the old version for the sake of "fairness": "[...] Also, don't block JavaScript, I see no possible security flaws, and I can't fathom how you could do without it!"

---

### Post by Dangertux on 2011-11-18
> **SavageWolf said:**
> What about a good ol' social engineering attack?

Also, he reformatted the computer 3 times, I'd expect him to have at least two different versions (Windows and Linuxes have different versions of Firefox). I'm not saying that this isn't a browser exploit, I'm saying that you should at least try to collect some information rather than yelling "ADBLOCK! NOSCRIPT!" Ugh...

Also, doesn't AppArmour protect against this sort of thing?

lob0, what sites are affected, and what browsers have you tried?

Apparmor -- Only if its enabled, which by default the firefox profile is not. Assuming its a fresh install its safe to assume no. Even then without additional tweaking the Firefox apparmor profile is pretty lenient on jscript.

I don't use Adblock, NoScript however is a different thing altogether. It protects against a wide variety of attacks and is very good at what it does.

Also of the attack vectors possible Social engineering is the least likely, since it would provide a negative return on investment for getting you to visit a marketing site, or anything else for that matter. Also browser exploits are commonly used in conjunction with SE attacks.

I hope this clarifies.

---

### Post by haqking on 2011-11-18
> **SavageWolf said:**
> Well done, rather than actually justifying your opinion, you have responded with arrogant hostility, now can we wait until the OP replys with anything interesting?

justifying my opinion ?

it is not an opinion, it is well known fact.

Ever heard of XSS (persistent and non persistent) it is a little thing since the 90's still very prevalent today in some of the most commonly used sites such as facebook etc.

Javascript exploits and flaws are more than well documented

edit. i better point out however that not all XSS is javascript based, i was using it as an example and of course not all javscript flaws are XSS related

---

### Post by lob0 on 2011-11-18
> **SavageWolf said:**
> What about a good ol' social engineering attack?

Also, he reformatted the computer 3 times, I'd expect him to have at least two different versions (Windows and Linuxes have different versions of Firefox). I'm not saying that this isn't a browser exploit, I'm saying that you should at least try to collect some information rather than yelling "ADBLOCK! NOSCRIPT!" Ugh...

Also, doesn't AppArmour protect against this sort of thing?

lob0, what sites are affected, and what browsers have you tried?

Thanks for all the replies guys.

Back when I had windows 7 I tried it on Internet Explorer and had the same result.

When I try to go "www.terra.com.br" which is a popular Brazilian website, it redirects me to that weird hosting site. It also happens with "www.globo.com" and with others.

---

### Post by SavageWolf on 2011-11-18
Yes I know what XSS attacks are, I even found one once. Also, flaws and exploits are everywhere in everything. I have a file on my server consisting of 500MiB of the letter "x", which web browsers try to display. Yes, there are a few security flaws, but they are outweighed by the sheer usefulness of JavaScript as a whole. As I have said somewhere before probably, this is like not leaving your house without bulletproof armour and armed guards and cool sunglasses because there is a lot of crime, or something.

Ugh...

---

### Post by haqking on 2011-11-18
> **SavageWolf said:**
> Yes I know what XSS attacks are, I even found one once. Also, flaws and exploits are everywhere in everything. I have a file on my server consisting of 500MiB of the letter "x", which web browsers try to display. Yes, there are a few security flaws, but they are outweighed by the sheer usefulness of JavaScript as a whole. As I have said somewhere before probably, this is like not leaving your house without bulletproof armour and armed guards and cool sunglasses because there is a lot of crime, or something.

Ugh...


so first you say javascript has no security flaws, and now it has.

And with that the discussion has ended.

---

### Post by CharlesA on 2011-11-18
Still sounds like either a DNS redirect or a browser hijack to me.

---

### Post by uRock on 2011-11-18
> **CharlesA said:**
> Still sounds like either a DNS redirect or a browser hijack to me.

+1 

lob0, NoScript can be found here, [https://addons.mozilla.org/en-US/firefox/addon/noscript/](https://addons.mozilla.org/en-US/firefox/addon/noscript/)

---

### Post by lob0 on 2011-11-18
> **uRock said:**
> +1 

lob0, NoScript can be found here, [https://addons.mozilla.org/en-US/firefox/addon/noscript/](https://addons.mozilla.org/en-US/firefox/addon/noscript/)

Thank you sir. I'll try that right now.

---

### Post by Ms. Daisy on 2011-11-18
> **lob0 said:**
> Thank you sir. I'll try that right now.Hi lob0, Noscript can be a bit annoying in that it blocks everything until you manually allow what you want.  Take a little time to make sure you understand how to get it functioning properly so you don't endure too much frustration. [http://noscript.net/features](http://noscript.net/features)

Ask back if you have any questions.

---

### Post by guestolo on 2011-11-18
Do you still have Windows machines hooked to your network?
It's very possible that you have a router hijacker
If your positive that your Windows clients are clear, if any, maybe think about resetting your router if you have one
[http://www.techsupportforum.com/2763-reset-for-linksys-netgear-d-link-and-belkin-routers/](http://www.techsupportforum.com/2763-reset-for-linksys-netgear-d-link-and-belkin-routers/)

---

### Post by OpSecShellshock on 2011-11-18
There's been recent activity at Brazilian ISPs that has involved DNS poisoning on the server side. This may not be an issue with the local machine at all. It's happening at the service providers, and they would be the ones who would have to fix it.

See [here]("http://www.securelist.com/en/blog/208193214/Massive_DNS_poisoning_attacks_in_Brazil").

Terra and Globo are specifically mentioned as sites that are being redirected.

---

### Post by Dangertux on 2011-11-19
> **OpSecShellshock said:**
> There's been recent activity at Brazilian ISPs that has involved DNS poisoning on the server side. This may not be an issue with the local machine at all. It's happening at the service providers, and they would be the ones who would have to fix it.

See [here]("http://www.securelist.com/en/blog/208193214/Massive_DNS_poisoning_attacks_in_Brazil").

Terra and Globo are specifically mentioned as sites that are being redirected.


Remember when I said highly unlikely. Congrats you're the 1% lol.

Nice find. You might consider using public DNS  like Google DNS.

---

### Post by OpSecShellshock on 2011-11-19
> **Dangertux said:**
> Remember when I said highly unlikely. Congrats you're the 1% lol.

Nice find. You might consider using public DNS  like Google DNS.

Thanks. That's why they pay me nearly enough to live on ;)

---

### Post by Dangertux on 2011-11-19
> **OpSecShellshock said:**
> Thanks. That's why they pay me nearly enough to live on ;)

So I guess if the OP comes back to this thread... Still keep NoScript but it's probably not going to fix this check out public DNS or wait it out. It probably won't last more than a few days. 

Also I feel your pain on $ OpSecShellshock.

---

### Post by CandidMan on 2011-11-19
I would add to the already good advice that it's meaningless to continually re-format your drive; software isn't like a stain or chemical. You can't 'scrub' it out, it's either recognized by your system as valid data or it's not i.e. 'deleted' or damaged

---

### Post by ikt on 2011-11-19
> **guestolo said:**
> Do you still have Windows machines hooked to your network?
It's very possible that you have a router hijacker

I've seen a few of these lately, I would definitely checkout the router to make sure it hasn't been compromised.

---

### Post by Paddy Landau on 2011-11-19
> **ikt said:**
> I've seen a few of these lately, I would definitely checkout the router to make sure it hasn't been compromised.
How does the router get hijacked? Is it because the default password has not been changed and it allows changes from outside the LAN?

---

### Post by Ms. Daisy on 2011-11-19
> **Paddy Landau said:**
> How does the router get hijacked? Is it because the default password has not been changed and it allows changes from outside the LAN?default password is one, UPnP is another:
[http://www.informit.com/articles/article.aspx?p=461084](http://www.informit.com/articles/article.aspx?p=461084)

BTW, we discuss it in the Basic Security Wiki, too.

---

### Post by CharlesA on 2011-11-19
> **Ms. Daisy said:**
> default password is one, UPnP is another:
[http://www.informit.com/articles/article.aspx?p=461084](http://www.informit.com/articles/article.aspx?p=461084)

BTW, we discuss it in the Basic Security Wiki, too.
Pretty much. ^

---

### Post by Paddy Landau on 2011-11-20
> **Ms. Daisy said:**
> default password is one, UPnP is another:
[http://www.informit.com/articles/article.aspx?p=461084](http://www.informit.com/articles/article.aspx?p=461084)

BTW, we discuss it in the Basic Security Wiki, too.
Thank you.

I already do as the article suggests, except for turning off PnP, which I shall do. I had not realised that PnP was such a risk!

I shall read the basic security Wiki.

---

### Post by Ms. Daisy on 2011-11-20
> **Paddy Landau said:**
> I shall read the basic security Wiki.That would be great. Feedback is welcome!

---

### Post by Paddy Landau on 2011-11-20
> **Ms. Daisy said:**
> Feedback is welcome!
I realise that I have read it before. Nicely written, suitable for people (like me) without a great deal of technical knowledge.

---

### Post by CharlesA on 2011-11-20
> **Paddy Landau said:**
> I realise that I have read it before. Nicely written, suitable for people (like me) without a great deal of technical knowledge.
Awesome.

---

### Post by MrLeek on 2011-11-20
> **Paddy Landau said:**
> I realise that I have read it before. Nicely written, suitable for people (like me) without a great deal of technical knowledge.

Really good news and both Ms Daisy and I welcome the feedback. Feel free to provide more detailed feedback via pm if you like - we're still working on it and there's a lot more things that we want to look at.

---

### Post by emiller12345 on 2011-11-22
> **Dangertux said:**
> 
So really you're left with a browser hijack or ARP poisoning. Since I doubt someone is sitting in front of the OP's residence re-arping their router. Alternatively DNS poisoning which is even less likely. Or you could have someone sitting around send ICMP redirect messages constantly.

Also consider DHCP hijacking in the future.  DHCP has no authentication mechanism, making it vulnerable.

---

### Post by CharlesA on 2011-11-22
> **emiller12345 said:**
> Also consider DHCP hijacking in the future.  DHCP has no authentication mechanism, making it vulnerable.

If you are using an internal DHCP server (your home router more then likely) the risk is minimal.

If you are connecting over public wifi, the risk is greater, but if you are doing that, you should always encrypt and data sent over an insecure connection.

DNS poisoning/hijacking would be more likely.

For example, my ISP hijacks any web searches I do via the address bar and redirects them to their own search engine. Changing my DNS servers stopped that from occurring.

---

### Post by Dangertux on 2011-11-22
> **emiller12345 said:**
> Also consider DHCP hijacking in the future.  DHCP has no authentication mechanism, making it vulnerable.

DHCP spoofing was not as likely in this particular case as you're in a race condition against the default DHCP server, since it was mentioned there was a router in place, in the given situation it would be almost impossible for a machine sitting on the network particularly over wifi to beat out the true DHCP server.

---

### Post by Starfleet on 2011-11-23
> **lob0 said:**
> Hello guys.

I used to use windows 7. I'm very careful and all but somehow I got a trojan (at least I think it is one.) It redirects me to a weird hosting site full of ads when I try to go to some specific sites. I checked the same sites on other computers in my home network and mine is the only one with the problem. So formatted it. Three times. The last one was a low-level formating. The trojan survived. I had used Ubuntu before and was wating for a chance to go back to it, so I did. I downloaded the latest version of it, formated and installed it. It was trojan free for 2 days, but yesterday, it was back!

I got some experience with computers but I'm still new to Ubuntu.

Really need your help guys...

Thank you.

You may also want to make sure you have the latest 'Java' Plugin installed as the 1.6.0_26 is seriously flawed and can easily be breached allowing malicious code to be used on your machine. You need to make sure you are running version 1.6.0_29 for maximum security. When I last looked the latest version still wasn't in the repos for Ubuntu. So you may need to go here to test what version you have and download the latest version if needed.  Click here: [http://www.java.com/en/download/installed.jsp]("http://www.java.com/en/download/installed.jsp")

---

### Post by Paddy Landau on 2011-11-23
> **Starfleet said:**
> You may also want to make sure you have the latest 'Java' Plugin installed...
Good point. Apparently, the default Java that comes with Ubuntu (Icedtea) does not suffer from that security problem; so if you have not installed Sun's version, you should be OK.

---

### Post by Starfleet on 2011-11-23
Well done Paddy, that's useful to know. I tend to use 'To do lists' to set up my system after installation because I find them so good. I've usually installed something other than the iced tea version. :)

---

### Post by BC59 on 2011-11-23
You don't have to scratch your HDD just take care of your router.

The router caught a virus.

[http://tidystorm.com/423/the-redirect-virus-was-in-my-router/](http://tidystorm.com/423/the-redirect-virus-was-in-my-router/)

---

### Post by emiller12345 on 2011-11-23
> **CharlesA said:**
> If you are using an internal DHCP server (your home router more then likely) the risk is minimal.


I agree, the risk is minimal, but still one thing to consider when trouble shooting. I usually go down the list of protocols in use on the network and try to determine which ones are most at risk of being problematic.

---

### Post by Paddy Landau on 2011-11-23
> **Starfleet said:**
> I've usually installed something other than the iced tea version.
In the past, I found Icedtea to be problematic. However, the latest version (I am on 11.04 at the moment) has given me no problems whatsoever.

---

### Post by lob0 on 2011-11-23
So, just to update you guys...

I read everything you posted so far. Here's what I tried:

NoScript: I think I got it to work properly, but the problem goes on.

"The virus might have caught the router": Both my modem and router were too old so I bought new ones. Yeah. The problem still happens.

"There's been recent activity at Brazilian ISPs that has involved DNS poisoning": would that affect other computers in my home network? I'm still the only one affected.

Sorry it took too long post back, but at home I get a message saying that "The message is too short" for me to post, so I can only post when I'm at work.

Weird stuff.

Thanks for all the help.

---

### Post by lob0 on 2011-11-23
Oh, I still gotta try to update my Java plug-in. I couldn't find it in my firefox plug-in window, tough.

---

### Post by OpSecShellshock on 2011-11-23
> **lob0 said:**
> Oh, I still gotta try to update my Java plug-in. I couldn't find it in my firefox plug-in window, tough.

The latest versions of Firefox should have this disabled by default, if Oracle Java has even been installed.

---

### Post by OpSecShellshock on 2011-11-23
> **lob0 said:**
> So, just to update you guys...

I read everything you posted so far. Here's what I tried:

NoScript: I think I got it to work properly, but the problem goes on.

"The virus might have caught the router": Both my modem and router were too old so I bought new ones. Yeah. The problem still happens.

"There's been recent activity at Brazilian ISPs that has involved DNS poisoning": would that affect other computers in my home network? I'm still the only one affected.

Sorry it took too long post back, but at home I get a message saying that "The message is too short" for me to post, so I can only post when I'm at work.

Weird stuff.

Thanks for all the help.

And to answer this, the next thing that I would probably do is see if the DNS settings are the same for all of the computers on the home network. On the Ubuntu machine you can click on the network icon in the panel and select "connection information" from the drop-down menu.  I'm kind of blanking on how to do it in Windows, but I'm sure it's similar. You'll want to see if it's the same for all of them. On a network behind a router the primary DNS entry should be the router's private IP address I think.

The article I linked to before said something about letting users through to the destination site once they agreed to load the malware, so for a machine that has already done so it would make sense for websites to display normally. For a computer that the malware can't run on, the obstacle page would be the one that displays every time a user attempts to access a site affected by the DNS poisoning. If that's what's going on (and this is all speculative at this point) then your computer would be failing to display websites because it's the one that *doesn't* have malware on it, if that makes sense.

---

### Post by emiller12345 on 2011-11-24
> 'The message is too short'
You might check that NoScript might be blocking yui.yahooapis.com (or something else) which is needed to post in the Ubuntu forums.  When this is blocked, none of the formatting buttons above the text area will function and any text you type in the text area will be erased when you click submit.

---

### Post by lob0 on 2011-11-28
> **OpSecShellshock said:**
> And to answer this, the next thing that I would probably do is see if the DNS settings are the same for all of the computers on the home network. On the Ubuntu machine you can click on the network icon in the panel and select "connection information" from the drop-down menu.  I'm kind of blanking on how to do it in Windows, but I'm sure it's similar. You'll want to see if it's the same for all of them. On a network behind a router the primary DNS entry should be the router's private IP address I think.

The article I linked to before said something about letting users through to the destination site once they agreed to load the malware, so for a machine that has already done so it would make sense for websites to display normally. For a computer that the malware can't run on, the obstacle page would be the one that displays every time a user attempts to access a site affected by the DNS poisoning. If that's what's going on (and this is all speculative at this point) then your computer would be failing to display websites because it's the one that *doesn't* have malware on it, if that makes sense.

They are all the same in all computers, I just checked.

It's getting worse. Most of the sites are redirecting me.

What do I do guys? Any other ideas?

Thanks

---

### Post by lob0 on 2011-11-28
> **emiller12345 said:**
> You might check that NoScript might be blocking yui.yahooapis.com (or something else) which is needed to post in the Ubuntu forums.  When this is blocked, none of the formatting buttons above the text area will function and any text you type in the text area will be erased when you click submit.

It was happening before I installed NoScript.

---

### Post by CharlesA on 2011-11-28
> **lob0 said:**
> They are all the same in all computers, I just checked.

It's getting worse. Most of the sites are redirecting me.

What do I do guys? Any other ideas?

Thanks

What DNS servers are you using?

I had to switch from using my ISPs DNS servers to google's since they would hijack search results.

---

### Post by Cavsfan on 2011-11-28
> **lob0 said:**
> Oh, I still gotta try to update my Java plug-in. I couldn't find it in my firefox plug-in window, tough.

Try the links in my signature to update your Java version.

In both windows and Ubuntu, I would also suggest the WOT add-on. If you click on the 2 green (recommended) check boxes when it restarts after you install it,
It will show a green circle by good websites and a red circle by bad websites.

I use SpyBot Search and Destroy to occasionally scan windows 7 for malicious software. You just have to manually update it since it is free.
You can also "immunize" with it, including adding malicious sites to the hosts file.

Also I have Avira Free Antivirus on my windows 7 system. It finds most things before they even get on your PC. Much better than Norton or any paid for or free programs

---

### Post by emiller12345 on 2011-11-29
You could try to run a trace route on a few of the URL's that are giving you problems.  If there ends up being no problem with the trace route's then it's probably a problem with your browsers. To run a trace route in Windows, first open a cmd.exe window... 
```
C:\Users\username> tracert www.google.com
```
or from Linux...
```
$ traceroute www.google.com
```
you can try other hostnames as well, the first few lines will look up the ipaddr of the url, which will give some insight into the dns lookup and handling

---

### Post by SparTacux on 2011-11-29
> **lob0 said:**
> Hello guys.

I used to use windows 7. I'm very careful and all but somehow I got a trojan (at least I think it is one.) It redirects me to a weird hosting site full of ads when I try to go to some specific sites. I checked the same sites on other computers in my home network and mine is the only one with the problem. So formatted it. Three times. The last one was a low-level formating. The trojan survived. I had used Ubuntu before and was wating for a chance to go back to it, so I did. I downloaded the latest version of it, formated and installed it. It was trojan free for 2 days, but yesterday, it was back!

I got some experience with computers but I'm still new to Ubuntu.

Really need your help guys...

Thank you.

Did you do an Md5sum check on that Ubuntu download? Did you download the software from Ubuntu.com or somewhere else? It's possible you got a dodgy download ;-) 

Also use Noscript - it's possible someone may be targeting you. You've not been upsetting anyone have you :-) 

Create another desktop user account on your computer and launch your browser from the new account and see what happens. See if the redirects happen straight away with this new user account or after a couple of days. You may be  getting targeted by a website you visit with some sort of compromise in your local directory???

---

### Post by |{urse on 2011-11-29
I did not read the whole thread yet but at this point I'd flash all my routers (firmware reset or upgrade). And yeah most likely browser hijacking, but just to be safe.

---

### Post by lob0 on 2011-12-14
could any of this go on even if I bought a new modem and a new router?

---

### Post by lob0 on 2011-12-14
I bought new ones and I've been using NoScript ever since... it went away for a while but I still have the problem. I've tried everything you guys told me to try... not sure what else to do.

---

### Post by OpSecShellshock on 2011-12-14
So it's still going on even with new network hardware, and with the use of script blocking? Ugh, I'm really sorry. It may still end up being a problem at your ISP, which would put it outside your control. Are all sites being redirected or only certain sites? Also, have you attempted to change DNS providers? I can't remember if that had been suggested yet.

---

### Post by lob0 on 2011-12-14
Only certain sites, like terra.com.br and twitter.com. How can change DNS providers?

Thanks for still trying to solve this.

---

### Post by OpSecShellshock on 2011-12-15
In the administration page of your router there should be entries somewhere in the settings that list the IP addresses of your primary and secondary DNS servers. To use Google's public DNS, change them to 8.8.8.8 and 8.8.4.4 (it shouldn't matter which is primary and which is secondary). They do recommend writing down the old DNS server IP addresses first in case you need them.

Another alternative is to use OpenDNS, which I think is free but you need to sign up for. See [here]("https://store.opendns.com/get/home-free").

---

### Post by Cavsfan on 2011-12-15
Also, make sure you install the add-on called WOT (web of trust). Good sites appear with a green circle next to them while 
bad sites have a red circle next to them. Some sites have yellow circles which means iffy.
People have contributed their time to rating these sites and determining if malicious software has initiated from the sites.
If it has a blue circle with a small question mark, it just means it has not been rated yet.

Maybe install WOT and see if the sites causing you the problems show as red.
You can google a site name and the results will have red, green, yellow or blue circles by each result on google.

But, since I installed WOT both on Ubuntu firefox and in windows too. I never touch a site that has a red circle by it.
If you accidentally click on a red, I believe it stops you and asks if you are sure you want to go on to this site.
It is sort of like NoScript as you can middle click on a site in the NoScript window and a WOT website will open up with several sites, 
one of which will tell you how many people have gotten malicious software from visiting that site.

HTH

---

### Post by Paddy Landau on 2011-12-15
WOT is a good plug-in, and I endorse what you said.

However, bear in mind that WOT is not perfect. Sometimes people will rate a site as red even when it has no malicious software, simply because it carries advertising. If you get a red-flagged site, read the comments to find out why it was flagged.

You can double-check a site with Google and McAfee with the site name as follows:
[www.google.com/safebrowsing/diagnostic?site=ubuntuforums.org]("http://www.google.com/safebrowsing/diagnostic?site=ubuntuforums.org")
[www.siteadvisor.com/sites/ubuntuforums.org]("https://www.siteadvisor.com/sites/ubuntuforums.org")
Obviously, replace "ubuntuforums.org" with the site name you are checking. If you use the plug-in NoScript, it gives you a semi-automated way to do this.

---

### Post by Cavsfan on 2011-12-15
> **Paddy Landau said:**
> WOT is a good plug-in, and I endorse what you said.

However, bear in mind that WOT is not perfect. Sometimes people will rate a site as red even when it has no malicious software, simply because it carries advertising. If you get a red-flagged site, read the comments to find out why it was flagged.

You can double-check a site with Google and McAfee with the site name as follows:
[www.google.com/safebrowsing/diagnostic?site=ubuntuforums.org]("http://www.google.com/safebrowsing/diagnostic?site=ubuntuforums.org")
[www.siteadvisor.com/sites/ubuntuforums.org]("https://www.siteadvisor.com/sites/ubuntuforums.org")
Obviously, replace "ubuntuforums.org" with the site name you are checking. If you use the plug-in NoScript, it gives you a semi-automated way to do this.

I agree. I use both NoScript and WOT. I really like the 4th site down when you middle click on a site in the NoScript list - "Safe Browsing Diagnostic".
That site will actually tell you if any malicious software has come from the site.
What is scary it looking at that page for google.com itself!

---

### Post by Paddy Landau on 2011-12-16
> **Cavsfan said:**
> I agree. I use both NoScript and WOT. I really like the 4th site down when you middle click on a site in the NoScript list - "Safe Browsing Diagnostic".
That site will actually tell you if any malicious software has come from the site.
What is scary it looking at that page for google.com itself!
Yes, it can be misleading. It shows if a site hosted on that domain has had malware. So, for example, if Google hosts third-party sites, one of them might have distributed malware while Google itself is still safe.

---

