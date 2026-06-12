---
title: "How safe am I from viruses while browsing the web?"
date: 2017-08-06
forum: Security
---

### Post by jonathan90 on 2017-08-06
I know that Linux isn't "immune" to viruses, but I was wondering how safe am I when surfing the web on Ubuntu? Particularly, how safe am I from getting viruses on "sketchy" websites that make tons of pop ups and spam ads. Does it mean that on Ubuntu, I can safely browse websites that would otherwise give me tons of viruses on Windows? Thanks!

---

### Post by Autodave on 2017-08-06
Yes, you are MUCH safer on Linux than Windows. That does NOT mean the you are immune to viruses on Linux though.  I have 13 machines running under Linux with multiple users in their homes. These machines are their only PCs, so I am sure that they pretty much use them for everything: good or bad. I have yet to get a virus on any of them.

---

### Post by vasa1 on 2017-08-06
People could also fall victim to "social engineering" exploits which rely on users' gullibility.

And browser nuisances such as pop-ups are probably cross-platform. You need to configure your blockers appropriately.

---

### Post by vocx on 2017-08-06
> **jonathan90 said:**
> I know that Linux isn't **"immune" to viruses**, but I was wondering how safe am I when surfing the web on Ubuntu? Particularly, how safe am I from getting viruses on "sketchy" websites that make tons of pop ups and spam ads. Does it mean that on Ubuntu, I can safely browse websites that would otherwise give me tons of viruses on Windows? Thanks!
What exactly is a virus? Can you answer this question yourself or not? If you can't, then you need to do a bit more research on what constitutes an exploit in a computer system.

In many cases a virus is a binary file, an executable file, a really small program, that copies itself when it gets into your computer and then it does something, like connecting to a remote server. If you visit sketchy websites, you may inadvertently download this program. Most of these programs are meant for Windows systems, so if they are in your Linux system, they simply will not run. You will download them, but they won't run. They just are not binary compatible with the Linux system libraries.

So, yes, just by using a Linux system you are protected against binary programs intended for Windows, making your environment inherently safer.

However,
> **vasa1 said:**
> People could also fall victim to **"social engineering"** exploits which rely on users' gullibility.

And browser nuisances such as pop-ups are probably cross-platform. You need to configure your blockers appropriately.
A bigger problem nowadays, I think, is phising and social engineering. If somebody tricks you into opening a bad website, you are at their mercy. Websites are operating system independent. So, you won't get any additional protection for these types of exploits.

You will get protection from binary viruses but not from website based attacks in general.

---

### Post by jonathan90 on 2017-08-06
What do you mean by being at the mercy of a bad website? Sure, they can spam pop ups, but if I go on to to them, they can't put malware on my system or log my keystrokes in another browser tab, right?

---

### Post by wildmanne39 on 2017-08-06
*Thread moved to **Security**.*

---

### Post by &amp;KyT$0P# on 2017-08-06
> **jonathan90 said:**
> What do you mean by being at the mercy of a bad website? Sure, they can spam pop ups, but if I go on to to them, they can't put malware on my system or log my keystrokes in another browser tab, right?
The biggest danger from bad websites is not what they can do to your local computer.  It is what they can do with other websites.

For instance, Cross-site scripting (XSS) - A bad website injects its code into, say, your banking site.  Your banking site then runs the malicious code in its own context.  It's like how the cuckoo bird lays its eggs in other birds' nests, and those other birds raise the cuckoo chicks as their own.

That's just one example.  Others, such as [Clickjacking]("https://en.wikipedia.org/wiki/Clickjacking"), involve a bit more social engineering.

These threats are not operating-system dependent.  Running Linux doesn't make you any more or less safe from them.  But some browser extensions can help.  What browser are you using?

---

### Post by vasa1 on 2017-08-06
[https://securelist.com/steganography-in-contemporary-cyberattacks/79276/](https://securelist.com/steganography-in-contemporary-cyberattacks/79276/) :)

---

### Post by jonathan90 on 2017-08-07
> **halogen2 said:**
> The biggest danger from bad websites is not what they can do to your local computer.  It is what they can do with other websites.

For instance, Cross-site scripting (XSS) - A bad website injects its code into, say, your banking site.  Your banking site then runs the malicious code in its own context.  It's like how the cuckoo bird lays its eggs in other birds' nests, and those other birds raise the cuckoo chicks as their own.

That's just one example.  Others, such as [Clickjacking]("https://en.wikipedia.org/wiki/Clickjacking"), involve a bit more social engineering.

These threats are not operating-system dependent.  Running Linux doesn't make you any more or less safe from them.  But some browser extensions can help.  What browser are you using?

I'm using Chrome right now. Do people get hit with XSS attacks very often, or is it a rare thing?

---

### Post by vasa1 on 2017-08-07
> **jonathan90 said:**
> ... Do people get hit with XSS attacks very often, or is it a rare thing?
What is your personal experience and that of people known to you? I am not aware of being hit by an XSS attack ever. My basis for saying so is that my bank account and various financial assets which I access online are unaffected over the years.

---

### Post by lisati on 2017-08-08
> **vasa1 said:**
> My basis for saying so is that my bank account and various financial assets which I access online are unaffected over the years.
Likewise here.

The only suspicious online activities I recall experiencing over the years that could potentially compromise my various financial assets were the occasional phishing attempts by email. Even though they're getting better, there's usually some clue that something's a bit off, and it usually has little, if anything, to do with XSS attacks.

---

### Post by HermanAB on 2017-08-08
Hmm, some level of paranoia is good, but too much of it, is a waste of time.  

Therefore, relax and enjoy your safe and secure Linux machine!

---

### Post by &amp;KyT$0P# on 2017-08-08
> **jonathan90 said:**
> I'm using Chrome right now. Do people get hit with XSS attacks very often, or is it a rare thing?
I don't think it's that common.  Most of the examples I've seen are poorly designed sites deliberately doing it to themselves.  If I'm remembering right, the only real XSS attacks I've seen involved ad servers.

This stuff is less likely to be problematic if you use an isolated browser session to visit sensitive sites.  That is, completely quit the browser before and after visiting the sensitive site, and don't visit other sites even in other tabs.

For Chrome, if you want to protect yourself, start with uBlock Origin and uBlock Origin Extra.  That should prevent adserver/webbug based shenanigans.  It's even better if you enable the malware domains subscriptions in uBlock Origin.

If you're an advanced user you will really benefit from adding uMatrix as well.

---

### Post by jonathan90 on 2017-08-11
> **halogen2 said:**
> I don't think it's that common.  Most of the examples I've seen are poorly designed sites deliberately doing it to themselves.  If I'm remembering right, the only real XSS attacks I've seen involved ad servers.

This stuff is less likely to be problematic if you use an isolated browser session to visit sensitive sites.  That is, completely quit the browser before and after visiting the sensitive site, and don't visit other sites even in other tabs.

For Chrome, if you want to protect yourself, start with uBlock Origin and uBlock Origin Extra.  That should prevent adserver/webbug based shenanigans.  It's even better if you enable the malware domains subscriptions in uBlock Origin.

If you're an advanced user you will really benefit from adding uMatrix as well.

Thanks! I mean in general, do you think I'm safe on Linux if I'm browsing one of those spammy sites? I mean survey/free gift card sites, or something of that sort.

---

### Post by ardouronerous on 2017-08-11
> **halogen2 said:**
> For Chrome, if you want to protect yourself, start with uBlock Origin and uBlock Origin Extra.  That should prevent adserver/webbug based shenanigans.  It's even better if you enable the malware domains subscriptions in uBlock Origin.

If you're an advanced user you will really benefit from adding uMatrix as well.

For Chromium, I have Disconnect, HTTPS Everywhere, Privacy Badger, Ghostery and uBlock Origin installed, what additional protection does uBlock Origin Extra provide?

For Firefox, I have Ghostery, Disconnect, HTTPS Everywhere, NoScript, Privacy Badger and uBlock Origin installed, is there anything else I should install on Firefox?

---

### Post by &amp;KyT$0P# on 2017-08-11
> **jonathan90 said:**
> I mean in general, do you think I'm safe on Linux if I'm browsing
In general, not unless you've taken steps to protect yourself.  Start with the aforementioned Chrome extensions.  For better protection of your computer, run your browser in a firejail sandbox.

> **ardouronerous said:**
> what additional protection does uBlock Origin Extra provide?
Basically it prevents websites circumventing uBlock Origin.  For more info see [its readme]("https://github.com/gorhill/uBO-Extra/blob/master/README.md").

> is there anything else I should install on Firefox?
You've got the essentials, but you might want to look into [NoRedirect]("https://addons.mozilla.org/addon/noredirect/").

Also, if you're an advanced user, [uMatrix]("https://addons.mozilla.org/addon/umatrix/").

---

### Post by ardouronerous on 2017-08-11
> **halogen2 said:**
> In general, not unless you've taken steps to protect yourself.  Start with the aforementioned Chrome extensions.  For better protection of your computer, run your browser in a firejail sandbox.

How do I do this?

> Basically it prevents websites circumventing uBlock Origin.  For more info see [its readme]("https://github.com/gorhill/uBO-Extra/blob/master/README.md").

Thanks for the info, I'll be installing this on Chromium, and apparently this is not necessary for Firefox, so no Firefox add-on.

> You've got the essentials, but you might want to look into [NoRedirect]("https://addons.mozilla.org/addon/noredirect/").

Unfortunately NoRedirect is not compatible with Firefox 54.0.

> Also, if you're an advanced user, [uMatrix]("https://addons.mozilla.org/addon/umatrix/").

I've tried uMatrix and it was very difficult to use and understand, I find NoScript easier. What's the difference between uMatrix and NoScript? Because reading the comments, uMatrix is an alternative to NoScript.

---

### Post by &amp;KyT$0P# on 2017-08-11
> **ardouronerous said:**
> How do I do this?
First install firejail -
```
sudo apt-get install firejail
```
Then
```
firejail chromium-browser
```
If you want to use firejail's [FONT=Courier New]--overlay-tmpfs[/FONT] option, you might need to disable Chromium's sandbox to get it to start -
```
firejail --overlay-tmpfs chromium-browser --no-sandbox
```

> What's the difference between uMatrix and NoScript?
Pretty much everything other than script blocking.  Good explanation in [this NoScript forum thread]("https://forums.informaction.com/viewtopic.php?f=8&t=22001#p83579").

> Because reading the comments, uMatrix is an alternative to NoScript.
Not unless you only care about blocking scripts.

---

### Post by juan53 on 2017-08-13
Answering to the original post thread:

Fist of all you have to use a good web browser. Without any doubt, I recommend you to use Firefox.
Secondly, restrict the cookies aceptance. Deny third party cookies to be admited in your browser.
In third place, choose the option to clear browser history when each session ends.
Add a couple of extensions:
[https://addons.mozilla.org/es/firefox/addon/noscript/](https://addons.mozilla.org/es/firefox/addon/noscript/)
[https://addons.mozilla.org/es/firefox/addon/https-everywhere/?src=ss](https://addons.mozilla.org/es/firefox/addon/https-everywhere/?src=ss)
[https://addons.mozilla.org/es/firefox/addon/clickclean/?src=search](https://addons.mozilla.org/es/firefox/addon/clickclean/?src=search)

Choose one of them:
[https://addons.mozilla.org/es/firefox/addon/privacy-badger17/?src=search](https://addons.mozilla.org/es/firefox/addon/privacy-badger17/?src=search) (it might be a bit messiy)
[https://www.mozilla.org/en-US/lightbeam/](https://www.mozilla.org/en-US/lightbeam/)

Finally, because you are supposed to run a Ubuntu system, install and enable AppArmor's profile for this browser:
sudo apt install apparmor-profiles
sudo apt install apparmor-utils
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
(note that if you are running the gnome variant and you want to install gnome extensions in your system, AppArmor will prevent you from doing that, then you have to put the profile in complain mode (sudo aa-complain /etc/apparmor.d/usr.bin.firefox) or to modify the profile.

I hope that you find it useful.

---

### Post by TheFu on 2017-08-13
There is no replacement for a smart end-user.  Installing some "security" addon, plugin, software, then still performing risky behaviors is a good way to discover a new, previously unseen, attack first hand.  

Security is about limiting exposure and mitigation of risks.  A smart, informed, user is required.

If you visit a website that causes a Windows virus to be run AND your Linux computer has the WINE subsystem installed, what will happen?  Sometimes it will do what the virus maker intended.  Being on Linux isn't always a prophylactic.

There are Linux specific attacks too, but these generally require a user to run server software like wordpress or mysql.  For a typical end-user who avoids the spammy, nasty, parts of the internet, the risks are minimal, provided they 
* don't do stupid things
* routinely patch and
* routinely make versioned backups.  

**Versioned backups are still the number #1 security technique.**
Versioned backups allow 
* recovery from any possible hardware, software or corruption issues.
* ability to see any changes made from backup to backup version. Analysis of those changes is extremely helpful in determining how an issue happened, where it started, and probably how to prevent the issue from happening again.

---

### Post by gordie692 on 2017-08-14
is clamav good I heard it wasn't very affective I tried downloading comodo but didn't allow me to so I just my updates everyday and I use firefox for one thing and chromium for another

---

### Post by TheFu on 2017-08-14
> **gordie692 said:**
> is clamav good I heard it wasn't very affective I tried downloading comodo but didn't allow me to so I just my updates everyday and I use firefox for one thing and chromium for another

I use clamav on my email server, nowhere else.  AV scanners on Linux scan for Windows malware, so it really isn't needed on a non-Windows network.

Plus, even the best native Windows virus/malware scanners are [only about 50% effective]("https://www.theguardian.com/technology/2014/may/06/antivirus-software-fails-catch-attacks-security-expert-symantec"). If you run 3-5 of them, that gets to about 80% effectiveness.

Worrying about AV just isn't productive any more, especially on Linux/Unix systems.  Get some versioned backups working.

---

