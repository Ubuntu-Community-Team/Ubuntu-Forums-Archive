---
title: "Security &amp; Privacy Install"
date: 2013-06-11
forum: Security
---

### Post by KushtyKushty on 2013-06-11
Hi guys,

I have recently installed 12.04 on a fresh laptop and want to make it as secure and as privacy orientated as possible. I am not after tools to crack passwords and sniff networks, i just want to ensure im anonymous to browse the web.

I have listed below what I plan to install to make this successful, i was hoping someone here could give me some feedback on the list, recommend any better services or even add some. Remember, all I want is to stay anonymous online and ensure my laptop is as secure as possible to stop anyone tracking/tracing me.


[LIST]
[*]UBUNTU 12.04 LTS DESKTOP OPERATING SYSTEM
[*]VPN SERVICE
[*]TOR (WILL THIS BE NEEDED WITH VPN?)
[*]FIREFOX + ADBLOCK + NOSCRIPTS
[*]SNORT &#8211; NETWORK INTRUSION DETECTION
[*]FIREWALL CONFIGURATION 'GUFW'
[*]CLAMAV ANTIVIRUS
[/LIST]

---

### Post by Lars Noodén on 2013-06-11
The VPN might not be necessary.  Which services, may I ask, might you consider tunnelling over the VPN?

Tor runs on its own without the need of a VPN.  It's a SOCKS proxy.  The best way to use it to browse the web is to download the [Tor Browser Bundle](https://www.torproject.org/projects/torbrowser.html.en) and use that if you can.  That will included noscript.  It will also be more 'standardized' reducing the likelihood of successful tracking through browser fingerprinting. 

Firefox is not needed if you have the Tor Browser Bundle and plan on running everything through Tor.  If not, then NoScript is good to have.  NoScript will block most of the offensive ads, the others you might let through by not installing adblock.  It rewards them for making ads with less offensive technologies.  You might want a VM like VirtualBox to open non-HTML pages like PDFs in so the network can be off when viewing the document.  Otherwise it is technically possible for them to compromise your anonymity.

Snort won't be much good on a desktop AFAIK.  You won't have any outward facing services but you will be scanned all the time anyway.  GUFW will take care of that.

GUFW will give you basic filtering which should be enough for a desktop.  There's not much more in the way of locking the machine down that can be done without getting severely in the way.  On an unchanging production server things are different.

ClamAV is only needed if you are doing a lot of file serving or file exchange with Windows users in binary formats.  It might be fun to play with, but is not essential.

---

### Post by KushtyKushty on 2013-06-12
Thanks for the comments.

I realized I made a mistake on my first post, this is a laptop not a desktop. My bad.

The reason for using a private VPN is due to Tor being really slow, I was hoping I could use a VPN which is encrypted and keeps no logs whilst still running standard Firefox ect, same results just a faster browser (<< Prob wrong). I am new to the whole Privacy thing but with recent events in the news and more and more leaks regarding government snooping and data collection (e.g. Google).

I want to ensure i can browse the internet anonymously with noone tracing it back to me or collecting every single thing I do, enough is enough, what I do on MY computer is MY business, not the governments.

---

### Post by SeijiSensei on 2013-06-12
Well you could start by just using a different provider like DuckDuckGo instead of Google.

Please don't use Tor; leave it for the political activists in authoritarian countries who really need it.

---

### Post by KushtyKushty on 2013-06-13
I have stopped using Google for searches, but there is over 10 other ways they collect information from you, everything from you access a website using Google Analytics to having adwords to installing cookies, this is the kind of stuff i want to stop.

Would FireFox + AdBlock + NoScripts stop this? Or is Googles code impossible to hide from unless behind some kind of proxy? Anyways,

I don't want to use Tor, which is why i suggested using a VPN instead, i was hoping being behind a VPN witch connects several users to a single IP, i would be able to stay somewhat, more private.

---

### Post by wildmanne39 on 2013-06-13
*Thread moved to **Security Discussions**.*

---

### Post by Lars Noodén on 2013-06-13
> **SeijiSensei said:**
> Well you could start by just using a different provider like DuckDuckGo instead of Google.

Please don't use Tor; leave it for the political activists in authoritarian countries who really need it.

DDG is a good start for search engines.  So is ixquick or startpage.

One way to help Tor would be to run a relay.  AFAIK, that can be done without a fixed IP number.  If you have a static IP number then you could also consider running a bridge relay.  The are standing requests for that kind of help.

---

### Post by matt_symes on 2013-06-13
Hi

I would also add Ghostery to the list of plugins.

Browser fingerprinting is also an interesting topic..

[https://panopticlick.eff.org/](https://panopticlick.eff.org/)

You may want to randomise your user agent string

[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)

As has been stated, don't use tor.

Here is a list of some common plugins.

[http://www.digitizd.com/2012/07/27/10-firefox-extensions-for-security-anonymous-browsing/](http://www.digitizd.com/2012/07/27/10-firefox-extensions-for-security-anonymous-browsing/)

I also use the WOT (web of trust) plugin.

Kind regards

---

### Post by kleenex on 2013-06-13
Hi. I suggest a **BetterPrivacy** addon for Firefox and maybe **HTTPS-Everywhere**. Of course the most important thing: enable AppArmor profile for Firefox, because it is disabled by default. It is very important.

```
[COLOR=#ff0000]$[/COLOR] [COLOR=#008000]sudo aa-enforce /etc/apparmor.d/usr.bin.firefox[/COLOR]
```

Kushty, you can also install apparmor-profiles package, which contains additional profiles for various applications. Oh, one more thing: mounting an ext3, ext4 etc. partitions with **nosuid**, **nodev**, **noexec** options. Please remember, that placing **/tmp** in **noexec** mode can prevent certain scripts from executing properly. Example:

```
/dev/sda3 /tmp noatime,nodev,nosuid,noexec 0 0
/dev/sda4 /var noatime,nodev
/dev/sda6 /home noatime,nodev,nosuid
```

And many, many more. :-)

---

### Post by Lars Noodén on 2013-06-13
+1 for HTTPS Everywhere

Keep in mind though that not all sites support HTTPS.  The Forums is one of them.

---

### Post by tubbygweilo on 2013-06-13
KushtyKushty,
I would suggest that Ghostery is **not** to be installed due to their practice of passing browsing habits on to advertisers [http://venturebeat.com/2012/07/31/ghostery-a-web-tracking-blocker-that-actually-helps-the-ad-industry/](http://venturebeat.com/2012/07/31/ghostery-a-web-tracking-blocker-that-actually-helps-the-ad-industry/) [https://www.ghostery.com/](https://www.ghostery.com/) but as in all things do your own research and thinking.

A simple idea would be to use FireFox in private browsing mode that ensuring that your history is not recorded on your machine.

Also remember that your IPS may well keep records of sites visited and that many visits to a VPN while may being legal may by some act as a flag to suspect browsing habits.

keep asking questions and carefully evaluate the answers.

---

### Post by matt_symes on 2013-06-13
Hi

> I would suggest that Ghostery is **not** to be installed due to their practice of passing browsing habits on to advertisers [http://venturebeat.com/2012/07/31/gh...e-ad-industry/]("http://venturebeat.com/2012/07/31/ghostery-a-web-tracking-blocker-that-actually-helps-the-ad-industry/") [https://www.ghostery.com/](https://www.ghostery.com/) but as in all things do your own research and thinking.

Interesting although incorrect according to their privacy policy. 

I thought you have to opt into "Ghost Rank" that and it was not enabled by default. It is disabled by default in my chromium, firefox browsers.

I don't tend to take sample of 1 either way (one blog entry or one privacy policy) so i won't research it on the internet, i'll actually look at my traffic and see if there's any merit in it.

Kind regards

---

### Post by ShadowVegan on 2013-06-13
You can use Off The Record for IM and VOIP. You'll also want to change some Firefox and Tor settings. For Tor, I suggest downloading the Tor Browser bundle. You'll want to turn off @font-face (if fonts are allowed, you can be identified by what fonts you have installed). HTTPS-Everywhere or NoScript (I forgot which) has an option to do this. You'll also want to get HTTPS-Everywhere and NoScript (and turn off @font-face) in default Firefox. You'll want to turn off geolocation in Firefox (this is off by default in Tor, but not in Firefox). To do this, type about:config in the address bar and set 'geo.enabled' to false. In both browsers you'll want to set 'network.http.use-cache' to false. In default Firefox you'll want to set a secure search engine such as StartPage as default (already set up in Tor browser). To set Startpage as the default browser, to to about:config and set the value of 'keyword.URL' to 'https://www.startpage.com/do/search/?q='. You can also get an add-on to use Startpage in the search engine bar on the Startpage website. Avoid using other search engines, **especially google**. A useful, though not necessary, add-on is the Web Of Trust add-on (I have it installed in default Firefox, but not in Tor browser). Enable NoScript in Tor browser of course--it's not enabled by default. In both browsers, in settings->privacy, select 'use custom settings for history' (Tor's default 'never remember history' allows cookies, so don't leave it at that) then check 'always use private browsing mode' and disable all cookies, even first party (make exceptions for the sites you need cookies for). Also go through all the Firefox settings and change anything that looks insecure, for example, 'block reported web forgeries' and 'tell sites I do not want to be tracked' (not very useful, but doesn't do any harm). Go through add-on settings too. You can confirm that Tor's settings are secure with [www.ip-check.info]("http://www.ip-check.info"). Also, if someone tells you to do './start-tor-browser --debug', don't--it logs stuff.

With browser stuff out of the way, I would recommend getting rid of 12.04 and getting 13.04 because it gives you an option to encrypt the entire OS. I believe 12.04 only allows you to encrypt the home folder. You can also use TrueCrypt for an extra layer of encryption (or for encrypting files on external devices) for certain files you want to be extra secure. Lastly in the area of browsers, if you want, you can go to about:config and set 'browser.fixup.alternate.enabled' to false--this just disables your browser guessing what you meant if you type something other than a URL into the address bar, which means you'll never end up on a site you didn't try to go to.

Default Ubuntu comes with some tracking software, and some other software depends on the tracking software. To get rid of it all while keeping Ubuntu working can be a bit of work--for that reason it could be easier to start with a variant like Lubuntu--but it is doable. The first thing to be concerned about is Zeitgeist, it tracks your activity. You can disable it without uninstalling it with the program 'activity-log-manager'. If you uninstall Zeitgeist and related packages, Nautilus (the default file manager) will no longer run, so you would have to uninstall Nautilus and replace it with something like pcmanfm. (if you want to do this and your desktop icons and wallpaper disappear, send me a PM, I can give you a walkthrough for a fix that should work) You can also uninstall 'whoopsie' which is error-reporting software that could potentially compromise privacy. And then there's geolocation software, but again, some other software relies on some of the geo software. To find the geo software, enter 'dpkg -l | grep geo' in the terminal and you'll see all software you have installed that contains geo in the name. Make sure to look up what it is before removing it. You can do the same command but replace 'geo' with something else like 'zeitgeist' to see files with another keyword. You may also want to remove all software relating to Ubuntu One. If you use gedit (you can replace it with leafpad if you prefer) you can disable 'backup files' in preferences, otherwise it will create a duplicate when you save a file, and the duplicate file is hidden by default. You may also want to install dconf-tools (contains dconf-editor) and use dconf-editor to make some additional changes, specifically disabling geoip in com->ubuntu and disabling data usage storage in com->canonical->indicator->appmenu->hud. Lastly, I'm not sure exactly what it does, but I read somewhere that it's a good idea to add a line with 'exit 0' at the beginning of the file /etc/default/ntpdate to 'disable NTP call home requests on boot'.

Of course, even with all of that Ubuntu isn't that secure. Much better than Windows, but if you want real security you'll need to use a different OS like TAILS (much slower than Ubuntu but very secure).

If you want any clarification on anything, feel free to send me a PM.

---

### Post by uRock on 2013-06-13
> **kleenex said:**
> ```
[COLOR=#ff0000]$[/COLOR] [COLOR=#008000]sudo aa-enforce /etc/apparmor.d/usr.bin.firefox[/COLOR]
```

Just tried that and this is what I got.```
*****@*****:~$ sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
sudo: apparmor-enforce: command not found

```

---

### Post by matt_symes on 2013-06-14
Hi

> **uRock said:**
> Just tried that and this is what I got.```
*****@*****:~$ sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
sudo: apparmor-enforce: command not found

```

```
sudo apt-get install apparmor-utils
```

```
sudo aa-enforce ...
```

Kind regards

---

### Post by ubuntu27 on 2013-06-14
See this image for alternative software or applications:
[ATTACH=CONFIG]243795[/ATTACH]

---

### Post by uRock on 2013-06-14
> **matt_symes said:**
> Hi



```
sudo apt-get install apparmor-utils
```

```
sudo aa-enforce ...
```

Kind regards

Thanx!

---

### Post by memilanuk on 2013-06-14
Anybody else using DoNotTrackMe in Firefox?

---

### Post by uRock on 2013-06-14
> **memilanuk said:**
> Anybody else using DoNotTrackMe in Firefox?
I think everyone does, but I don't think it does much good, since Ghostery is still blocking a lot of sites.

---

### Post by auntclauds on 2014-02-28
> **SeijiSensei said:**
> Well you could start by just using a different provider like DuckDuckGo instead of Google.

Please don't use Tor; leave it for the political activists in authoritarian countries who really need it.

WE may just be this in our own country now, "Please don't use Tor; leave it for the political activists in authoritarian countries who really need it" Yikes! (But, you make a very good point and leave it for those ten steps further into tyranny than we.)

---

