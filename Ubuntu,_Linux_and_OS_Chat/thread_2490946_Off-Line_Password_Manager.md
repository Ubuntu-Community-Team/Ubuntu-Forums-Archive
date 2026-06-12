---
title: "Off-Line Password Manager"
date: 2023-09-21
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2023-09-21
I'm looking at using a password manager and like the idea of browser integration - at the moment I use auto-fill in Firefox.   I do not like the idea of having my password manager in the Cloud and looking at off-line managers.  Bitwarden, for example, has off-line capability.  I feel setting this up might be beyond my capability but willing 'to have a go'.   I've read about using external hardware (to my single Desktop - I do not have a home LAN) but wondering if I could use a vm in someway.  I have seen a YouTube tutorial using 22.04 and Docker but I do not use Docker.  I have a LVM based Desktop and reasonably comfortable with qemu/kvm machines, but not sure how all this would hang together at a high level.  Is it feasible for me to look at implementing a password manager on my current Desktop?

---

### Post by TheFu on 2023-09-21
keepassxc

---

### Post by DuckHook on 2023-09-22
My password management strategy is a bit complicated.

The Executive Summary version is that I keep two password management systems: a "casual" password management system in my personal Nextcloud and a "secure" one that is confined to local storage and is not cloudy.

Now the details:

Cloudy password managers have been hacked (Lastpass, Lifelock) with dire results. Some cryptowallets had millions of $ stolen from them due to these hacks. By running my personal Nextcloud password manager, I am a little bit more protected (insofar as I maintain Nextcloud properly). In my opinion, browser&#8209;based password managers are not secure at all and I won't use them. The safest password managers are purely local, like keepassxc that TheFu has recommended.

But purely local password managers have a big downside: they are very inconvenient to use—in some cases debilitatingly so—which renders them practically useless in many cases. When you are travelling, or if you wish to log into something on a mobile device, a highly secure localized password manager restricted to your desktop machine just doesn't cut it.

However, what I found, at least in my personal case, is that my password usage tends to fall into two distinct camps.

On the one hand are hyper&#8209;secure passwords that I would not take travelling with me or trust to mobile devices in the first place. Things like my banking logins, govt logins and LAN infrastructure passwords fall into this basket. I don't do any of that work except at home using my desktop machine anyway. Therefore, keeping these passwords in a more secure and exclusively local password manager is fine. Like TheFu, I use keepassxc for this task.

But most of my passwords don't need such ultra&#8209;secure handling. For example, passwords for hotels, car rental agencies, news sites, etc. In short, anything that doesn't have any payment info or sensitive personal info attached. Yes, there is general personal data that could be leveraged to do nefarious things like SIM swapping and identity theft, but even there, I've taken to TheFu's suggestion by lying: I enter false data into these sites and keep track of that false data with the same password manager.

For the most part, this gives me the best of both worlds: I enjoy the better security of a local password manager for sites that I deal with from a set location while having the convenience of password access for sites that I use while mobile.

Occasionally I run into a dilemma with sites that are more sensitive but require mobile access. I then have to choose between better security or convenience. I usually choose better security, but thankfully, such dilemmas are few and not the norm.

We all have different risk tolerances and judge our needs differently. There's no one&#8209;size&#8209;fits&#8209;all strategy, but hopefully, the above will give you some options and food for thought.

---

### Post by TheFu on 2023-09-22
We've had the password manager discussion a number of times here;
[https://ubuntuforums.org/showthread.php?t=2484642&p=14134162#post14134162](https://ubuntuforums.org/showthread.php?t=2484642&p=14134162#post14134162) is one thread.

> The way I handle password DBs is simple. I have 2 DBs - work and home. They are sync'ed nightly from my primary desktop at home using rsync. The DB files are pushed to about 6 different locations, including inside nextcloud. 

Inside nextcloud, they are sync'd with my android devices. The nightly sync happens just after midnight, I know this, so as long as my desktop has the current kdbx file, it will be pushed everywhere needed nightly. When I'm not traveling, my main desktop at home is my "system of record". I make any kdbx file changes on that system. Simple.

After you setup a password manager, it becomes a 99.9999% read-only tool.  Perhaps 3x a year, I'll modify it, so doing that on my main desktop isn't exactly hard.

KeePassXC is far from perfect, but it is better than all the other options I've found.

In my mind, I'd like the KeePass DB to remain cross-platform like it is, but allow different authentication modes more like LUKS encryption does.  This way, I could use a 68 character passphrase if I didn't have one of my Yubikey's with me, but still get into the DB.  Alas, that isn't the way the DB is setup to work and to maintain cross-platform compatibility, I don't see that happening with all the different programs that make use of the kdbx files.  

Using an external "key file" which can be anything is an alternative, but now we need to have a file on all our desktop/tablet/phones to unlock the DB too.  That would be pretty easy to figure out which file based on access time on at least 1 of those platforms, but with 3+ platforms involved, the key file jumps out. Hardly secure.

Also, using a USB device for authentication seems like a good idea ... except for devices that don't have USB storage support.  Just try to do that on a recent iPhone. Not possible. Same for many android devices, even if they have USB ports.  That's why we need different modes to unlock the DB.  USB, yubikey, Oauth, Oauth2, NFC, typing in a long passphrase, and many others.  In short, nothing is perfect.  

Putting the password manager as a web-app just seems like a complete failure to me.  Why should we need multiple solutions?  We shouldn't.  

Memorize 3 passwords.
[LIST=1]
[*]Home login
[*]Work login
[*]Password manager access
[/LIST]
From there, a number of different 2nd factors should be possible.  Just not bio-metrics (fingerprints or retina scans).  Do we really want someone to be tempted to cut off a finger?

---

### Post by VMC on 2023-09-23
Here's the info on KeypassXC:
Secure Your passwords remain encrypted at all times and no data is stored on  remote servers, so you stay in full control of your data. No cloud, no  ads, no subscriptions.

---

### Post by Quarkrad on 2023-09-23
Thank you all for your wise words.  I have been 'playing' with keepassxc but not found it consistent enough for me.  However, on closer examination I believe my problem is not with keepassxc but in some of the url's I have.  Some logins work OK using the firefox password manager but not with keepassxc - I have discovered, for some sites, I need to make subtle changes to the url then it works. So my issue is not necessarily with Keepassxc.  My brief look at cloudy and local managers pointed me to keppassxc as the ideal tool - your words and advice has now convinced me to persevere with keepassxc and authenticate all my passwords :icon_frown:

---

### Post by TheFu on 2023-09-23
KeePassXC has a browser extension.  I know people who use it unimportant things so they are logged in nearly automatically.  I don't use it and just setup an auto-type script for each login.  Most of the time, that is just {USERNAME}{tab}{password}{enter}, but for places that put the username and password onto different webpages, I will admit to manually grabbing 1{enter}, then manually grabbing the other{enter}.  This might be more complex, but I feel it is worth it for banking sites and for sites that have money connected in any way.

Sure, there's a better way to do it, but it hasn't been worth my effort or the added risk of having an unnecessary, in my view, browser extension.

I will also admit to never, ever, using the built-in password manager for any browser due to security worries.  Browsers have hundreds of bugs and the project teams keep making them more and more complex, often breaking things.  Every bug is a security liability, especially in something like a browser.

Of course, we each have our different allowed "hassle factor" level that we will put up with before wanting to throw everything out a window.  Mine is low for some things and high for others. I don't think this is odd.

---

### Post by lammert-nijhof on 2023-09-23
I remember three passwords my normal password; my master password for 2 step authentication and my encryption passphrase for the VM running my banking.  I use the Firefox password manager for the websites, but I switched off syncing my passwords.  Once per 3 months, I might sync my passwords once manually after e.g a re-installation.  I don't trust Android with any of my PC passwords and I will never use it for banking. Note that I use my banking VM exclusively for banking and thus I avoid emails, social media, web browsing or any other job with that VM.

I'm in the process of moving my apps to snaps, because they are considerably more secure than deb files :)

---

