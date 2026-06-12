---
title: "What level of security do you use?"
date: 2015-08-18
forum: Security
---

### Post by Richard_Romick on 2015-08-18
I am torn between trying to provide enough security to avoid zero day vulnerabilities in browsers (I use Firefox, my wife uses Chrome) and not providing so much security the web becomes difficult to use.  

I usually listen to Steve Gibson on Security Now about what to use for security.  He gave up No Script because it was high maintenance.  He was using browser sandboxing before the latest Firefox exploit that was stealing your ssh keys since it involved reading files, not changing them.  Now he suggests creating a small VM, perhaps running Tiny Core Linux, to run the browser in.  

I think that is a little extreme; I am currently running Firefox in Firejail sandbox hoping it keeps me safe.  The latest vulnerability in Firefox mentioned above isn't stopped by this, since running Firejail with the flag --private breaks Evernote Web Clipper.

I wanted to ask some more experienced Linux users (that would be you) what you use to keep yourself safe online.

---

### Post by vasa1 on 2015-08-18
> **Richard_Romick said:**
> ...

I wanted to ask ... what you use to keep yourself safe online.
There was a community wiki on the topic. I'm sure someone will post a link. But if you're listening to Gibson and using FireJail it looks like you're ahead of the game :)

All I use with Firefox is uBlock Origin :( but none of my bank accounts have been hacked so far (and this is not an invitation or challenge).

---

### Post by Richard_Romick on 2015-08-18
Do you mean this link? [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

It is true that this webpage has a lot of goodies (I will have to try Tiger later).  However, I wanted to get the security practices of multiple real people, since the amount of protection considered adequate but not overbearing is a very complicated subject.

Thanks for your response :D.  You make it sound like if Gibson says we should be using VM, I should really consider using a VM.

---

### Post by matt_symes on 2015-08-18
Hi

Steve Gibson and Leo have excellent content in that podcast.

You may want to consider confining Firefox with an apparmor profile. A pain to set up initially but excellent at what it does as part of a multi-layered strategy to secure Firefox.

Kind regards

---

### Post by maglin2 on 2015-08-18
There is already a default firefox apparmor profile provided but not enabled.

To enable it:

sudo mv /etc/apparmor.d/disable/usr.bin.firefox ~

and reboot

if it causes problems move the disable symlink back and reboot (never actually tested this).

I have never had any problems with it, but I have also read elsewhere on this forum that the profile is very permissive and may be of limited security value. You could create your own stricter profile. I've had a couple of attempts and given up each time.

I do use noscript (I don't find it to be too high maintenance). I also have three user accounts. One is for admin only, and is the only place the sudo password is ever entered. Two is for general browsing, enail etc. The third is used only for sensitive transactions (internet banking etc). 

My hope from this strategy is that if I ever encounter a trojan/keylogger etc it is most likely to be in account two, and can only install itself there, where it will never have access to the sudo password. Thus the third account where I do sensitive stuff will be unaffected.

This may all be hokum - and if the trojan can gain elevated privileges through exploiting some vulnerability it will be. 

My main hope is that since I only ever install from the repo, and don't have flash or java installed, I am unlikely to be vulnerable to the most common exploits anyway.

---

### Post by buzzingrobot on 2015-08-18
The best protection is using your head. Loading up on add-ons can lead to a false sense of security and a readiness to blithely click on anything.

Linux is such a small target that anyone writing/selling/using viruses for profit will focus elsewhere. That's nice, Other forms of attacks via the web and mail are probably more common these days.

I use ad blockers, both to eliminate the annoyance and to attempt to thwart that avenue of attack. 

I don't open, or allow my mail client, to display the contents of a message unless I recognize the sender.  Otherwise, I delete it. Many IMAP clients can be configured to download only message headers, leaving the content on the server until specifically request, i.e., clicked on.

I make a distinction between privacy and security, but I do also use a password manager, the HTTPS Everywhere extension, and the Privacy Badger extension. The best way for me to preserve my privacy is to be careful about the personal info I publish to the web. I'm not that interested in cookies and such following me around the web, the extensions notwithstanding.  That's annoying, but keeping a close hold on data that could cost me money is the real issue. (I use online banking via one app on one device; two-factor-authentication is required to do anything that moves, or could enable the movement of, money out of the account. Banks and credit cars issuers send me alerts on any transaction over $X and any international transactions of any amount.)

Attachments can be tricky if they come from family/friends who are passing along some funny cat video they found in their own mail.  Discourage that kind of thing.

Zero-days are called that because they're new and no response is available. I have a few security blogs in my RSS reader.  When, for example, I see there's yet another zero day attack using Flash, I disable the thing until Adobe releases the patch.  (I also use Chrome and always turn on "Let me choose when to run plugin content" so Flash on a oage isn't going to run unless I right-click on an individual element and make it happen.)

---

### Post by Richard_Romick on 2015-08-18
I looked at AppArmor, and appreciate its customizability.  However, to start out with, I wanted a sandbox that would give me good protection right off with minimal config needed by me (hopefully configured by someone smarter than me).  As you said, AppArmor's default profile had minimal restrictions that need to be built up through config.  That is definately something I will look into later.

---

### Post by drm200 on 2015-08-20
I use two browsers ... Firefox only for banking and Chrome for everything else
My Firefox browser has all sites blacklisted except for my banking sites.  No Adobe flash installed/allowed.  I've installed the following Firefox extensions
    HTTPSEverywhere
    NoScript
    uBlock Origen
    uMatrix


    I use the default NoScript setup and then under advanced/https .. force my banking sites to use HTTPS


I've added the following extensions to Chrome:
    ublock Origen
    umatrix
    HTTPS Everywhere
    WOT
    BitDefender Trafficlight
    AutoHistory Wipe


Additional Precautions
    Use a paid for VPN.  Do not use a free VPN
    KeePassX for your storing your passwords offline  ... i don't believe in saving passwords online
    FreeFileSync to easily setup configurations to backup your sensitive data on regular basis
    There are several browser specific settings that give extra security.  This is one good source with recommendations for Ubuntu, FF, and Chrome:
           [http://thesimplecomputer.info/debian-family-hardening](http://thesimplecomputer.info/debian-family-hardening)


More Firefox hardening (in firefox open link about:config)


	Disable the WebRTC service
		Set media.peerconnection.enabled to FALSE


	Disable weak encryption
		Disable RC4 ciphers, search for "security*rc4". Set them all to FALSE.
		Disable 3DES cipher. search for "security*des". Set to FALSE (breaks Facebook as Facebook uses this relatively weak cipher but should not be a problem for your bank)



	Force Firefox to reject insecure negotiation attempts with websites
		search for "security.ssl.require_safe_negotiation" and set to TRUE (breaks Facebook)
		search for "security.ssl.treat_unsafe_negotiation_as_broken" and set to TRUE (breaks Facebook)


	Disable Firefox cache to disk
		Set "browser.cache.disk.enable" to FALSE.
		Set "browser.cache.disk_cache_ssl" to FALSE.
		Set "browser.cache.offline.enable" to FALSE.


	Disable Firefox access to the clipboard
		Set "dom.event.clipboardevents.enabled" to FALSE.


	Disable Geolocation to prevent FF from sending network and location info to 3rd parties
		Set "geo.enabled" to FALSE.


	Instruct Firefox to throw away all cookies every time you close the browser.
		Set "network.cookie.lifetimePolicy" to 2


    Manage Firefox Connections:
	Reference: [https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections?redirectlocale=en-US&redirectslug=how-stop-firefox-automatically-making-connections](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections?redirectlocale=en-US&redirectslug=how-stop-firefox-automatically-making-connections)


	datareporting.healthreport.service.enabled set to false
	datareporting.healthreport.uploadEnabled set to false
	browser.aboutHomeSnippets.updateUrl. set to blank string
	browser.search.geoip.url set to blank string
	extensions.getAddons.cache.enabled set to false
	network.http.pipelining; true


And then there are additional steps to harden Ubuntu

---

### Post by TheFu on 2015-08-28
Linux Foundation Workstation Security Checklist [https://github.com/lfit/itpol/blob/master/linux-workstation-security.md](https://github.com/lfit/itpol/blob/master/linux-workstation-security.md)

---

### Post by bashiergui on 2015-08-29
> **TheFu said:**
> Linux Foundation Workstation Security Checklist [https://github.com/lfit/itpol/blob/master/linux-workstation-security.md](https://github.com/lfit/itpol/blob/master/linux-workstation-security.md)
That's a pretty solid list. Thanks for sharing.

---

### Post by kurt18947 on 2015-08-29
Unlike other O.S.s, linux distros don't care how many installs I have running so I have 2; one for everyday use and one just for important stuff. The two installs are unaware of another as far as I can tell. The more secure install is pretty minimal - no flash, no java, no email in any form. I haven't found a legitimate need for any of that on the sites this install is used for. This install only connects to perhaps half a dozen web sites and needless to say Facebook or other social media are not among them. I could maybe accomplish the same thing with a VM guest but I'm not confident about properly configuring that.

---

