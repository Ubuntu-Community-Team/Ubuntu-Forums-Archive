---
title: "Increasing Security By Modifying Default Content Settings in Google Chrome"
date: 2019-03-01
forum: Security
---

### Post by johnanderson974123 on 2019-03-01
Greetings,

I'm trying to make my computer more secure by changing the default  settings in Google Chrome to better fit my security needs.  Unfortunately, there's quite a few settings in Chrome that I'm not sure  about, specifically under Settings > Advanced > Content settings.  Here are some of the questions I can't find a decent answer to:

1) What are payment handlers? Are there any privacy/security risks  associated with using payment handlers? Somehow, the idea of having my  financial information stored in a browser makes me feel uncomfortable. I  almost always use PayPal whenever I decide to shop on non-Amazon  websites to avoid giving my financial information directly to the  website, so should I disable this? Do I need to have this enabled if I  ever plan on using Google Pay?

2) What about unsandboxed plugins? I've read Google was planning on  getting rid of plugins in Chrome anyway. Is this setting basically for  Flash sites? If I don't plan on using Flash would I be more secure if I  just disabled sites from asking me if they can use a plugin to access my  computer, or are there sites out there that do require plugins besides  Flash?

  3) What about allowing sites to ask when they want access to USB  devices? Why would I ever want a website to have access to a USB device?  Do I need to have this enabled if I ever plan on using a Yubico  security key?

  4) What about the privacy/security risks of allowing sites to use  system exclusive message to access MIDI devices? Could you explain what  MIDI devices are in simple terms as well as their contemporary  relevance?

  5) What about the security risks of allowing sites to ask when they  want to download multiple files automatically to my computer? Are there  any legitimate websites out there that do this? This seems like  something that could easily be abused by nefarious actors.

  Your help is greatly appreciated,

John

---

### Post by TheFu on 2019-03-01
I have a hard time thinking that privacy and google-chrome browser are possible together. I could easily be wrong, but considering exactly what Google's business model entails ....  at some point common sense shouldn't be ignored.

YMMV.

Now, if you'd like to talk about Chromium browser and security, I run it inside a firejail with --private option. This prevents any data from being written to disk, though chromium doesn't realize it. No settings. No downloads. Every run of the browser seems like a fresh diaper, just waiting. ;)

I have a yubikey, but haven't found any of the large cloudy sites that will enable it without giving up a cell phone first.  It does work with my nextcloud installation, however.  1-click to install and 2-clicks to enable it for my NC account. Unfortunately, neither my phone or tablet are compatible with the yubikey, so I've never left that 2FA enabled more than a few hours.  I know it works with firefox. Cannot say if it works with chrome/chromium running inside a firejail.  It wouldn't be THAT hard to allow access, I suppose.  Local overrides for each program's firejail profile isn't rocket science.

---

### Post by CharlesA on 2019-03-01
> **TheFu said:**
> 
I have a yubikey, but haven't found any of the large cloudy sites that will enable it without giving up a cell phone first.  It does work with my nextcloud installation, however.  1-click to install and 2-clicks to enable it for my NC account. Unfortunately, neither my phone or tablet are compatible with the yubikey, so I've never left that 2FA enabled more than a few hours.  I know it works with firefox. Cannot say if it works with chrome/chromium running inside a firejail.  It wouldn't be THAT hard to allow access, I suppose.  Local overrides for each program's firejail profile isn't rocket science.

I guess I shouldn't feel too bad then. I bought a pack of Yubikeys intending to use them as 2FA for LUKS and some web services, but all I could find were hacky ways to get it to play nice with LUKS - like sending a text string when the button was pressed and using that as your passphrase.

Web services seem to be hit or miss, but mostly miss, which makes me wonder what the point of the Yubikey is.

On a different topic, firejail is basically a sandbox that gets wiped when the application is closed, right? That sounds quite handy. What OS did you get it set up on?

@OP: Why not try changing each option one at a time and see if it affects anything? I use Chromium if I need a Chrome-based brower, but my main browser is Firefox and I haven't really tweaked many of the default settings.

---

### Post by johnanderson974123 on 2019-03-02
[QUOTE=TheFu]I have a hard time thinking that privacy and google-chrome browser are  possible together. I could easily be wrong, but considering exactly what  Google's business model entails ....  at some point common sense  shouldn't be ignored.[/QUOTE]

I think Chrome is a privacy  nightmare, but I didn't really ask about privacy, my questions were  mostly about security. Sure, it's often called the most secure browser  on the internet, but at what price? I don't really use Chrome, I only  use it when Firefox doesn't work with a website, which does happen  occasionally, even with NoScript, uBlock Origin, and Privacy Badger,  disabled. But I'd still like to know what some of the settings do in  Chrome, only because, for better or worse, Chrome is the most popular  browser on the internet, and I like to keep up with tech issues. The  rapid growth of Google Chrome always appeared to me as being  non-organic, mainly through advertising, unlike Firefox, which did see  organic growth. To be honest, when I first tried it, it gave me the  impression of being clunky. To illustrate what I mean, suppose you  wanted to keep your search history private -- no, I'm not necessarily  talking about visiting adult sites -- when you have guests or relatives  over, but don't necessarily feel like going incognito every time. All  you would need to do is press Ctrl+Shift+Delete every time. But what if  you forget to press Ctrl+Shift+Delete? And, trust me, you will forget.  There's no way you can change the settings in Chrome. Sure you can use  extensions, but that type of functionality should really be built-in to  Chrome. Also, the default settings in Chrome, like I said before, are  really a privacy nightmare. Just take a look at Settings > Advanced  under Privacy and Security. By default, when you type a URL in the omnibox, it will send what you type to a remote server before you even pressed Enter. Right after you've pressed Enter, Chrome will preload a page of all the links that are found on the website you've asked for, in case you decide to click on one of those links. You'll say Google won't necessarily know the exact URL of the website you've typed into its omnibox, but if you leave the second setting on by default, Google can glean important information and make a guess what type of website you're on just by looking at the links that are found on the website. Same thing with navigation errors. If you mistype a URL, and you will, before you get an error message about how the website is unreachable, the mistyped URL will be sent to Google's remote server in order for it to make a suggestion based on what you typed. Same thing with spell-checking. Safe browsing is a little different. Desktop browsers are more susceptible to drive-by malware, so you might want to leave that setting on, and that's assuming you're not sending automatic usage statistics. Like I said, a privacy nightmare. But, TheFu, if you know the answer to any of my questions, please feel free to answer. I've tried asking the same questions over at BleepingComputer.com, first in the security forum, then in the Web Browsing forum, without any luck. At one point I got a little ticked off by the lack of response that I wrote: "Since it's been a couple of days since I created this thread without  anybody responding, is it safe to conclude that the internet has no idea  what half the settings in the most popular browser on the internet do?" Even if I don't use Chrome regularly, I still want my browsing session to be as secure as possible during the times when I do.

I already know about firejail. @CharlesA I've tried it in Ubuntu and Lubuntu 16.04. It's in the repositories. You can read more about it [here]("https://easylinuxtipsproject.blogspot.com/p/sandbox.html").

@TheFu Also, any luck on using your Yubikey with an online password manager like LastPass?

---

### Post by TheFu on 2019-03-02
> **CharlesA said:**
> I guess I shouldn't feel too bad then. I bought a pack of Yubikeys intending to use them as 2FA for LUKS and some web services, but all I could find were hacky ways to get it to play nice with LUKS - like sending a text string when the button was pressed and using that as your passphrase.

I enter a passphrase, then use the static, long, characters from the yubikey to unlock LUKS.  Also have an 80+ character, passphrase which is stored inside keepassxc. The yubikey way in is much easier. Since LUKS has 8 slots, I see using 2 as a reasonable method, with the really long one there should I lose both cloned yubikeys.

> **CharlesA said:**
> 
Web services seem to be hit or miss, but mostly miss, which makes me wonder what the point of the Yubikey is.


Most of the popular web services seem to support U2F or TOTP, so I don't blame YubiCo.  My issue is that these services demand an SMS 2FA cell setup BEFORE they will pair an U2F device to the account. It is purely a policy decision.  I wasn't able to get github to move, though they did understand my concern. A real human responded to my query 4 yrs ago at github. I can't say anything about the current management - it may not have changed. I don't know. Closed my account there.

> **CharlesA said:**
> 
On a different topic, firejail is basically a sandbox that gets wiped when the application is closed, right? That sounds quite handy. What OS did you get it set up on?

Firejail uses the same techniques that Linux Containers use to segment off different parts of the OS, the hardware, etc.  We have control over how much or how little is allowed.  Firejail has been in Ubuntu for 3+ yrs.
> **CharlesA said:**
> 
@OP: Why not try changing each option one at a time and see if it affects anything? I use Chromium if I need a Chrome-based brower, but my main browser is Firefox and I haven't really tweaked many of the default settings.
I use chromium as stated in my first post, but use Firefox as my main browser when visiting trusted sites - that's about 20. I limit addons in firefox and do not use any addons in chromium.  Most of the sites I visit in FF are LAN hosted.  I self-host many web-apps which are my window/firewall to the rest of the dangerous world of the internet.

@OP - I don't think Chrome is the most secure browser. Nowhere near.  The most secure is **lynx**.  It has some drawbacks.  Next would be **dillo**.  It has fewer drawbacks, but they are still significant to most people (including me).

Firefox descends from Netscape Navigator in the 1990s.  I can probably find the box I bought at the local computer store and floppy disc somewhere here.

Too hard to read the rest of that paragraph - walls of text are hard to parse. Sorry.

LastPass fails my "does it smell bad" test.  Common sense matters.  If you want to keep something secure, don't put it on the internet, in someone else's computer, inside someone else's data center. Do so just smells funny to me.
But since I use keepass universal DBs for my different platforms, the main issue with Yubikeys is the lack of support for my tablet and phone.  I had a phone that supported NFC and a yubikey that output NFC for authentication.  Problem was it only worked 1:10 attempts.  

I need a way for authentication of the passwd DB to be possible on my tablet. Until that works, I'm stuck using a 30+ character passphrase.  Clearly, a 1st world-problem.

---

### Post by CharlesA on 2019-03-02
> **TheFu said:**
> I enter a passphrase, then use the static, long, characters from the yubikey to unlock LUKS.  Also have an 80+ character, passphrase which is stored inside keepassxc. The yubikey way in is much easier. Since LUKS has 8 slots, I see using 2 as a reasonable method, with the really long one there should I lose both cloned yubikeys.

That makes sense. I hadn't thought to configure LUKS that way. I tried setting it up with the Yubikey in the past using this: [https://github.com/cornelinux/yubikey-luks](https://github.com/cornelinux/yubikey-luks) but didn't have much luck with my test system.

> 
LastPass fails my "does it smell bad" test.  Common sense matters.  If you want to keep something secure, don't put it on the internet, in someone else's computer, inside someone else's data center. Do so just smells funny to me.
But since I use keepass universal DBs for my different platforms, the main issue with Yubikeys is the lack of support for my tablet and phone.  I had a phone that supported NFC and a yubikey that output NFC for authentication.  Problem was it only worked 1:10 attempts.  

I need a way for authentication of the passwd DB to be possible on my tablet. Until that works, I'm stuck using a 30+ character passphrase.  Clearly, a 1st world-problem.

That's my issue with lastpass, but I know people who use it because convenience > security. I use keepass but I haven't tried associating it with my Yubikey. I might have to look into that. Do you carry it on your keychain or something similar?

---

### Post by TheFu on 2019-03-03
> **CharlesA said:**
>  That's my issue with lastpass, but I know people who use it because convenience > security. I use keepass but I haven't tried associating it with my Yubikey. I might have to look into that. Do you carry it on your keychain or something similar?

I have a wire loop Hicarer with selected USB flash drives and a few different yubikeys. But it doesn't usually leave the house more than a few times a week. I work from home.  I have forgotten to bring it with me a few times over the years.  I can access a jump system remotely using a borrowed computer/phone/tablet, pull down my keepass v2 DB and unlock it.  It should be understood that I use keepass about 3 times a week. It isn't a daily thing and I'll login to multiple places all at once for convenience and stay logged in for the week.

Until there is a solution to make the u2f authenticate useful for phones and tablets, it really won't be all that important. KeePassXC really needs to support multiple authentication methods similar to the way that LUKS does it.  Maybe that is already possible, I don't know.  About once a year, I'll seek out a solution for a few hours, not find one, then ignore the problem for another year or so.

If you like Yubikeys, check out **onlykey**. It is basically 6 yubikeys, with pin unlock access and pin wipe features, all for the price of 1 yubikey.  I don't have one, but it is on a wish list.

---

