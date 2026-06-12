---
title: "Anonymous browsing"
date: 2008-12-10
forum: Security
---

### Post by whiteox on 2008-12-10
I am new to Ubuntu, got the disc loaded and the whole thing works like a dream. I want to anonymise my browsing so that I can walk quietly through the internet without disturbing others, or being disturbed in my turn. I know nothing about firefox or the Ubuntu system. Do I need to do anything to ensure I leave no tracks?

---

### Post by bodhi.zazen on 2008-12-10
it is not possible to be completely anonymous. With that said, use privoxy and / or tor (tor is slow).

[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

---

### Post by cdenley on 2008-12-10
> **bodhi.zazen said:**
> it is not possible to be completely anonymous. With that said, use privoxy and / or tor (tor is slow).

[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

Tor makes you more vulnerable to having your traffic analyzed by someone, so it becomes even more important that you don't send any sensitive data such as passwords unencrypted.

---

### Post by Sarmacid on 2008-12-10
Here's a nice guide to surf anonymously [http://www.howtoforge.net/ultimate-security-proxy-with-tor](http://www.howtoforge.net/ultimate-security-proxy-with-tor)

---

### Post by flynnguy on 2008-12-10
Well there's different kinds of privacy and yes, you will need to install some stuff. First get yourself the noscript plugin. Most sites use some sort of tracking. While it won't hide you from their logs, if you don't allow sites like google-analytics.com then most people won't notice you were on their site. Also the Tor network is another way of hiding where you came from. (Tor and noscript will do a pretty good job)

Also locally there's your cookies, history and cache that can give you away. Firefox does have a tool under Tools->Clear Private Data... which should get rid of most of your local browsing footprints.

---

### Post by teddks on 2008-12-10
This is best to do on Intrepid.

This is a short howto for setting up Firefox with hardened settings for maximum anonymity.

The very first thing we want to do is install Ubuntu with full-disk encryption. This is a bit of a lengthy topic in and of itself, and there are a lot of things you can do to tune this for security purposes, but I won't go into them here. You need this so that if Firefox you overestimate Firefox and it leaves garbage everywhere on your disk, you're still safe.

Now we need to set up a second fall-back encrypted volume, in case the FDE is compromised. Probably the best thing to do is to set up a Truecrypt hidden volume, so that you can put bank documents or taboo literature in the outer layer, and the really sensitive files in the hidden layer. You can also do encfs or ecryptfs, both of which can be automatically unlocked on login. However, neither of them offer the hidden-ness that Truecrypt does. While encfs is somewhat slow compared to ecryptfs and ecryptfs is easier to set up (just run ecryptfs-setup-private), ecryptfs reveals filenames, which can be just as damaging here, since we want anonymity.

Then run firefox from Terminal like this:
```
firefox -ProfileManager -no-remote
```

Set up a new profile called "banking" or "guest" or something innocuous. Then, create a new launch icon with the command ```
firefox -P <your profile name here> -no-remote
``` and then change the existing firefox icon to the command ```
firefox -P <default profile name here> -no-remote
``` This will allow you to launch the different profiles concurrently, but it will also mean that clicking that icon will start a new instance of firefox instead of connecting to the old one.

Now, open up ~/.mozilla/firefox and move the new profile folder to the encrypted folder. Make a symlink to the new folder and put it in the place of the old folder, like this:
```
ln -s /path/to/new/profile/folder/location ~/.mozilla/firefox/<name of profile folder>
```

Now you have a firefox that will only store cookies, cache, history, logins, etc., to this encrypted volume. Configure it NOT to store cookies, cache, or history, set a master password (a secure one) on logins, and set it to clear everything on shutdown. Then, install privoxy and Tor and configure it to point at both as described in the Tor docs.

Your setup is **still vulnerable** however, until you install the Noscript plugin. Noscript blocks pretty much all client-side content, such as javascript, java, and flash. All of these are able to break your anonymity on tor, so IF you enable them for any site, be EXTREMELY careful. You should also get the Forcehttps addon to force ssl-secured connections to sites that offer the option (this will let you allow javascript as long as you trust the other site). I also recommend the Web Developer Toolbar (which allows you to see a lot of the innards of a site very easily) and FireGPG, a firefox-addon interface to the Gnu Privacy Guard. You might want to consider changing your user agent with the user agent switcher addon to something like Windows XP; this will help you blend into the crowd.

Remember, while you are on Tor, **always assume that your connection is being monitored when it is not secure.** In a nutshell, don't send anything you care about over a connection that is not encrypted. Tor's internal .onion sites are encrypted end-to-end, as are any https sites.

You might want to look at the [Bypassing Internet Censorship](http://en.flossmanuals.net/CircumventionTools) manual from FLOSS Manuals for a few other things you can do to be anonymous in different ways. However, I've found that not much can beat a fully-hardened Tor system. It might not put you out of the reach of the NSA, NATO, or the Illuminati, but it certainly means your ISP or employer can't monitor you.

---

