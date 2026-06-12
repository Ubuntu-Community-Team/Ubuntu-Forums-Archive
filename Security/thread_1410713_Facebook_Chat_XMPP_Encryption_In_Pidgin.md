---
title: "Facebook Chat XMPP Encryption In Pidgin?"
date: 2010-02-19
forum: Security
---

### Post by curtissthompson on 2010-02-19
Facebook recently released [XMPP support]("http://blog.facebook.com/blog.php?post=297991732130") for Facebook Chat to allow users to directly add Facebook Chat to clients like Pidgin without the need of workarounds.  They also provided [instructions]("http://www.facebook.com/sitetour/chat.php") (as a part of their new site tour) for setting up Facebook Chat in pidgin:

[LIST=1]
[*]**Go to "Accounts" and select "Manage Accounts."**
**[*]On the Basic tab, enter the following info:**
Protocol: XMPP
Username: <your Facebook username>
Domain: chat.facebook.com
Resource: Pidgin
Password: <your Facebook password>
Local alias: <your Facebook name>
**[*]Click the Advanced tab, then enter the following info:**
Connect port: 5222
Connect server: chat.facebook.com
(Uncheck the box labeled "Require SSL/TLS")
[/LIST]

Normally I would assume they don't have SSL (or TLS) support for Facebook Chat based on those instructions, but I'm suspicious they may have it and merely don't want all users selecting the option either because of bandwidth consumption or glitches or some other concern.  I suspect they have SSL support for Facebook Chat because with the launch of their new site design came nearly full site-wide https, where not only can you access [https://facebook.com/](https://facebook.com/), now most site links will then appear with the https prefix. (Just a year or two ago they didn't even have https access and not long before that not even a secure login option).  I'm assuming that like the recent feature allowing you to select a username (useful for things like Instant Messaging screennames & email address creation other than just Vanity URL), that this recent ability of https browsing is a feature that was created with Facebook Chat in mind.

I've set it up Facebook Chat without any problem in Pidgin according to their directions, but I'd like to if possible find the settings to use encryption for Facebook Chat in Pidgin.

I tried using XMPP's secure port 5223 instead of the unencrypted 5222 port for Connect Port, but that alone didn't work as I expected.  I remember most of my other IM services use alternative Connect Server addresses for secure connections, usually with just a slightly different subdomain.

I'm wondering if anyone knows what (and how to find) the necessary Connect Server and other settings to use encryption with Facebook Chat in Pidgin?  I don't like to use a service unless they use open source software and open protocols and provide encryption of traffic (and login), so I'm hoping this feature is available and someone knows what settings to use.

Any help and information would be greatly appreciated!

---

### Post by EricSR on 2010-11-04
*bump*
It'd be really nice to have secure chat ability, cheers to firesheep.

---

### Post by sleepingdragon on 2010-11-07
Hey.

I use the OTR (Off The Record) plugin with Pidgin that encrypts the chat between users. No SSL is required. Instead, users exchange keys (the plugin will generate one for you), and these are verified before the conversation takes place. It is very similar to the system of "trust" that works in PGP encryption. OTR will also automatically switch to an encrypted chat if it has your friend's key.

The only downside to this is that both ends must use Pidgin with the OTR plugin in order for this to work. Pidgin is available for all three platforms (*NIX/Win/Mac), so this shouldn't be a major problem.

---

### Post by darkazurka on 2010-12-25
> **sleepingdragon said:**
> The only downside to this is that both ends must use Pidgin with the OTR plugin in order for this to work. Pidgin is available for all three platforms (*NIX/Win/Mac), so this shouldn't be a major problem.
No. Adium and Pidgin OTR works just as well. Pidgin uses it as a 3rd party plugin. There's Adium for example that has built-in OTR.(wow!)
See here for which programs support OTR(a lot!): [http://www.cypherpunks.ca/otr/software.php](http://www.cypherpunks.ca/otr/software.php)

---

