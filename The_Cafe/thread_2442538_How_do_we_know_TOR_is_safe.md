---
title: "How do we know TOR is safe?"
date: 2020-05-04
forum: The Cafe
---

### Post by iamtheeggman2 on 2020-05-04
Hi,

I was lead to believe TOR was safe for doing anonymous web surfing, I went onto YouTube to see some videos (before you ask I did not sign in) and yet laughingly it produced like 5 or 6 items in a suggestions list that were topics and channels I had visited recently on my normal browser which were topics that had absolutely nothing to do with the targeted youtube content.

 Of the thousands of topics and millions of recent videos publicised every week, how is this possible??????

---

### Post by slickymaster on 2020-05-04
*Thread moved to **The Cafe**.*

---

### Post by iamtheeggman2 on 2020-05-04
> **slickymaster said:**
> *Thread moved to **The Cafe**.*


Well I am struggling to understand why this has been moved to the cafe,  if the application is secure and assuming the recommended videos are not  a coincidence, then it is a problem in the ubuntu installation...

---

### Post by slickymaster on 2020-05-04
> **iamtheeggman2 said:**
> Well I am struggling to understand why this has been moved to the cafe,  if the application is secure and assuming the recommended videos are not  a coincidence, then it is a problem in the ubuntu installation...

It's not a support request, hence it was moved.

From the Security forum label:> **Forum: Security**
Questions about security in Ubuntu and the official flavours.

---

### Post by iamtheeggman2 on 2020-05-04
Whilst I am not looking for an argument, I would disagree this is not a support request as I am concerned that TOR is possibly not working because it shows up results that are part of my normal usage of the browser in ubuntu. I was under the impression for using TOR previously it popped up a connection in other places of the world beyond your own and that you usually get greeted by YouTube in a foreign language yet i connected up in English.

---

### Post by EuclideanCoffee on 2020-05-04
You didn't say what operating system you are on. 20.04 LTS has a newer version than 18.04 LTS.

The package doesn't appear to receive updates to 18.04 LTS. It's actually behind Debian in patches, going into the universe repository, which is typically where community supported packages end up.

[http://changelogs.ubuntu.com/changelogs/pool/universe/t/tor/tor_0.3.2.10-1/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/t/tor/tor_0.3.2.10-1/changelog)

[https://metadata.ftp-master.debian.org/changelogs//main/t/tor/tor_0.3.5.10-1_changelog](https://metadata.ftp-master.debian.org/changelogs//main/t/tor/tor_0.3.5.10-1_changelog)

You're probably better off asking for support from the project or general discussion from the cafe.

You can also offer to help by patching the fix in the bionic release yourself on Launchpad.

---

### Post by slickymaster on 2020-05-04
> **iamtheeggman2 said:**
> Whilst I am not looking for an argument, I would disagree this is not a support request as I am concerned that TOR is possibly not working because it shows up results that are part of my normal usage of the browser in ubuntu. I was under the impression for using TOR previously it popped up a connection in other places of the world beyond your own and that you usually get greeted by YouTube in a foreign language yet i connected up in English.

That's exactly the point. The thread is not about security issues related to an Ubuntu official flavour, but related to the TOR network.

In all cases you are welcome to start a thread in the [Resolution Center]("https://ubuntuforums.org/forumdisplay.php?f=123") sub-forum if you think this move should be reviewed by the other forum admins.

---

### Post by iamtheeggman2 on 2020-05-04
> **slickymaster said:**
> That's exactly the point. The thread is not about security issues related to an Ubuntu official flavour, but related to the TOR network.

In all cases you are welcome to start a thread in the [Resolution Center]("https://ubuntuforums.org/forumdisplay.php?f=123") sub-forum if you think this move should be reviewed by the other forum admins.

OK well I am not really interested in forum politics, I am more  concerned about the fact TOR is not dong on ubuntu 20.04 like I observed  in previous releases of ubuntu re going to another country. You shouldn't assume this is a TOR problem, if ubuntu is telling the browser what topics I've been viewing on YouTube lately then the whole point of TOR  browser on ubuntu is a waste of time. 

I don't care which subsection of the forum this is on, I just want to understand how its possible 5-6 videos of topics magically appeared in the recommends that I have watched in the last week that have little to do with the video I was looking for in TOR.

---

### Post by iamtheeggman2 on 2020-05-04
> **EuclideanCoffee said:**
> You didn't say what operating system you are on. 20.04 LTS has a newer version than 18.04 LTS.

The package doesn't appear to receive updates to 18.04 LTS. It's actually behind Debian in patches, going into the universe repository, which is typically where community supported packages end up.

[http://changelogs.ubuntu.com/changelogs/pool/universe/t/tor/tor_0.3.2.10-1/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/t/tor/tor_0.3.2.10-1/changelog)

[https://metadata.ftp-master.debian.org/changelogs//main/t/tor/tor_0.3.5.10-1_changelog](https://metadata.ftp-master.debian.org/changelogs//main/t/tor/tor_0.3.5.10-1_changelog)

You're probably better off asking for support from the project or general discussion from the cafe.

You can also offer to help by patching the fix in the bionic release yourself on Launchpad.

I'm on 20.04 with TOR installed from the software manager

---

### Post by EuclideanCoffee on 2020-05-04
Right, so I recommend going upstream for some answers, as this is an application related issue at this point unless a user in cafe can answer.

---

### Post by The Cog on 2020-05-04
I gather that your evidence for TOR not working is that you-tube appears to recognise your browser.
I don't think this is very good evidence agains TOR. 
Even if your browser is operating in ingognito mode so not sending cookies back to Google, they have other ways of recognising yoru browser. 
[https://blokt.com/guides/browser-fingerprinting](https://blokt.com/guides/browser-fingerprinting)
[https://pixelprivacy.com/resources/browser-fingerprinting/](https://pixelprivacy.com/resources/browser-fingerprinting/)
They probably have other methods too. They don't really need your IP address to get a very good idea about you, and your IP address is all that TOR hides as far as I know.

---

### Post by yetimon_64 on 2020-05-04
> **iamtheeggman2 said:**
> Hi,

I was lead to believe TOR was safe for doing anonymous web surfing, I went onto YouTube to see some videos (before you ask I did not sign in) and yet laughingly it produced like 5 or 6 items in a suggestions list that were topics and channels I had visited recently on my normal browser which were topics that had absolutely nothing to do with the targeted youtube content.

 Of the thousands of topics and millions of recent videos publicised every week, how is this possible??????

Tor from the repos has you still using the same browser (and its history list, cookies, etc) as you use normally everyday. It just redirects all traffic from your computer to the tor network and if the browser you are using has a history list then that is still available to sites like youtube. It is possible to use the tor-browser bundle directly from the tor project as it supplies and optimizes the browser to be used so no history is then available for sites like youtube.

I would suggest you remove/purge the repo version of tor and then go to [[COLOR=#0000ff]--this link--[/COLOR]]("https://www.torproject.org/download/") and use the linux download link from there. The browser bundle is run from the home folder or an external usb drive, ie. from wherever it is stored; it is fully standalone. If you are only interested in browsing privacy then the browser bundle should be enough, I would only use the repo version if other applications or services are needed to be routed via the tor network.

Note the browser fingerprinting links The Cog posted, this is one reason it is good to use the browser supplied with the tor browser bundle pack over the repo package and your usual browser. The browser bundle is optimized to avoid such techniques and will even give a stern warning about maximizing the browser window as the site you are on then can then tell your screen resolution in use. There are many different tactics the browser bundle is optimized to protect you against for privacy purposes. 

Regards, yeti.

---

### Post by DuckHook on 2020-05-04
New users commonly confuse TOR and TORBrowser. The majority of general users do not need TOR. They need TORBrowser. AFAIK, the repo version of TORBrowser and the external one are the same. This is because the repo does not actually install the browser itself, but just a launcher that then goes and downloads the latest TORBrowser. From that point onwards, the browser will continually check for updates and is no different than the bundle downloaded directly from the TOR site.

---

### Post by yetimon_64 on 2020-05-04
> **DuckHook said:**
> ...AFAIK, the repo version of TORBrowser and the external one are the same...

Seems you are right there, from "apt-cache show torbrowser-launcher"...
> ```
When you first launch Tor Browser Launcher, it will download TBB from
 https://www.torproject.org/ and extract it to ~/.local/share/torbrowser,
 and then execute it.
 Cache and configuration files will be stored in ~/.cache/torbrowser and
 ~/.config/torbrowser.
 Each subsequent execution after installation will simply launch the most
 recent TBB, which is updated using Tor Browser's own update feature.
```

Thanks for pointing that out I wasn't aware the repo supplied exactly the same/current version. Cheers.

@ OP, instead of using the link I posted in post #12 it would be easier for you to just issue the next command in the terminal if it is only the browser protection that is needed ...
```
sudo apt install torbrowser-launcher
```

Regards, yeti

---

### Post by TheFu on 2020-05-05
Just installing and using TOR isn't sufficient to be anonymous on the internet.  Multiple behaviors must be altered too.

---

### Post by DuckHook on 2020-05-05
> **TheFu said:**
> Just installing and using TOR isn't sufficient to be anonymous on the internet.  Multiple behaviors must be altered too.
&#8593;+10&#8593;
People need to get rid of their "magic app" thinking.

---

### Post by iamtheeggman2 on 2020-05-05
The thing is though this is a browser that advertises itself as a completely anonymous browsing facility and it had no real use, should have no cache or any internet history access to my firefox browser.

---

### Post by yetimon_64 on 2020-05-05
> **TheFu said:**
> Just installing and using TOR isn't sufficient to be anonymous on the internet.  Multiple behaviors must be altered too.
Yes, absolutely. That is very important for anyone considering using tor to take heed of.

> **iamtheeggman2 said:**
> The thing is though this is a browser that advertises itself as a completely anonymous browsing facility and it had no real use, should have no cache or any internet history access to my firefox browser.
OP, please confirm which package/s you installed, it seems your  expectations are not being met as you may have installed the wrong tor  package for private browser usage.

See the next screenshot for the tor browser bundle version of firefox which is using private browsing by default vs. the ubuntu repo version of firefox that uses normal browsing as default.
If you are using the tor service and the standard firefox version then your browsing is NOT private by default. Note I do NOT have tor installed yet can run a tor browser with the standalone browser bundle package ...

[ATTACH=CONFIG]285751[/ATTACH]

```
yetiman:~ $  apt-cache policy tor
tor:
  Installed: (none)
  Candidate: 0.3.2.10-1
  Version table:
     0.3.2.10-1 500
        500 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
``` 

Regards, yeti.

---

### Post by DuckHook on 2020-05-05
> **iamtheeggman2 said:**
> The thing is though this is a browser that advertises itself as a completely anonymous browsing facility and it had no real use, should have no cache or any internet history access to my firefox browser.
TOR Browser does *not* advertise itself as a "completely" anonymous browsing facility, but rather, as the "most" private. This claim happens to be true: it *is* the most private.

However, there is no app, service or facility anywhere on the planet that can protect a person from the bad consequences of his/her own actions. It is simply not possible. An elementary example: if you visit your banking site using TOR Browser and enter your username/password, you are no longer anonymous. You've just bypassed TOR anonymization by telling the bank who you are. Ergo: there is no point using TOR Browser to visit such sites. Every app ever written relies on the user to work *with* it to allow it to do its job, and it cannot protect users who are intent on working *against* it.

Another factor to consider is usability: TOR Browser's NoScript settings are pretty lax by default. They are set this way partially to facilitate a decent user experience, but also because unique NoScript settings that are only halfway properly set are also (perversely) a method that sites can use for browser fingerprinting. These are nuances that most users are not knowledgeable enough to understand. It is sometimes better to visit sites using regular Firefox, but with all scripts disabled through aggressive NoScript settings, than with TOR Browser. If one turns off cookies, all scripts, spoofs a different user-agent, uses a proper DoH service, connects through a VPN, sandboxes the browser (TheFu uses Firejail, I use a combo of AppArmor and unpriviliged LXD containers) and doesn't visit questionable sites, then one is pretty effectively hardened against even the worst that the Internet can throw at us. If you really want to take that ultimate step, then substitute a more primitive browser like Dillo or Links2 for FF and you've got almost all of your bases covered. Just be prepared for an ugly and primitive browsing experience that won't work at all on some sites.

You're getting an avalanche of info here, but what should come through clearly is this: stop relying on apps or services or promises to protect you. Your primary and weakest link when it comes to online safety is the guy you see in the mirror. It is difficult to practice really good surfing hygiene; way more difficult than most people are willing to put up with. People think that they can continue behaving in a slovenly way so long as they use TOR Browser, and this false sense of security is perhaps the biggest downside of all to its use.

---

### Post by jp41 on 2020-05-27
also installed Tor from their [official page]("https://www.torproject.org/download/") 
went to youtube and nothing looked familar,search / watched historywise 
also on 20.04 , so dont think anything wrong with distro.

---

