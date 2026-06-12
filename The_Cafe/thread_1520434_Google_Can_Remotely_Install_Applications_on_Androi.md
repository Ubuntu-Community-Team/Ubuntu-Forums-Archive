---
title: "Google Can Remotely Install Applications on Android Phones"
date: 2010-06-29
forum: The Cafe
---

### Post by sudoer541 on 2010-06-29
While people are debating whether or not it is  right for Google to have the power of removing applications from Android  phones remotely, a security researcher points out that the company can  also install them in the same manner. In theory, the feature can have  security implications if an attacker manages to pull off a  Man-in-the-Middle (MitM) attack.

		[CENTER]  [/CENTER]
 		Last week, [**news broke out**]("http://news.softpedia.com/news/Google-Remotely-Wipes-Two-Apps-from-Android-Phones-145443.shtml") that Google  exercised its ability to remotely wipe out applications from smartphones  running Android. This feature is clearly stipulated in the [Android Market Terms of Service]("http://www.google.com/mobile/android/market-tos.html") (see  paragraph 2.4) and the company reserves the right to use it without  notice.

However, since in practice, most users never read license  agreements, terms of service and other such documents, a lot of people  were surprised to find out that Google has this power. In the true  spirit of the blogosphere, an entire debate over the ethical and privacy  aspects ensued.

In response to these concerns, security  researcher Jon Oberheide [points out]("http://jon.oberheide.org/blog/2010/06/25/remote-kill-and-install-on-google-android/") on his blog that Google  is also capable of remotely installing applications onto Android  devices. "If some people are upset that Google retains the ability to  kill applications remotely (I personally prefer the potential security  gains of the functionality), I fear what they’d think of the  INSTALL_ASSET feature," he writes.

The INSTALL_ASSET is a message  that Google's GTalk servers can send to Android's GtalkService and is  the reverse of the REMOVE_ASSET intent used by the company to remove  apps. The researcher explains that Android devices communicate with  Google's servers via the GTalkService pretty much all the time.

And  unlike REMOVE_ASSET, which Google only makes use of under certain  conditions - clearly [explained]("http://android-developers.blogspot.com/2010/06/exercising-our-remote-application.html") in a blog post by Rich Cannings, the  Android security lead - the INSTALL_ASSET command is actively used as  part of the normal application installation process. Every time the  "Install" button is clicked, Google's servers send an INSTALL_ASSET  intent forcing the device to download and install the APK package.

Oberheide  notes that in theory this feature could be abused if an attacker  manages to compromise the connection established between the device and  Google's servers and execute what is known as a Man-in-the-Middle  attack. "If an attacker is able to MITM this SSL GTalkService connection  for a particular device, it may be possible to spoof these  INSTALL_ASSET messages to deliver a malicious application payload. If  Google’s GTalkService servers were compromised, the malicious impact  would obviously be a bit more widespread," the researcher concludes.


Source: [Softpedia!!!]("http://news.softpedia.com/news/Google-Can-Remotely-Install-Applications-on-Android-Phones-145655.shtml")

---

### Post by AllRadioisDead on 2010-06-29
Who cares? 
At least this way they can install critical security fixes on the fly, I don't really see a problem with this. This looks like people trying to spread more paranoria over the internet.
My phone's rooted anyways, I won't be recieving any of these OTA updates.

---

### Post by Crunchy the Headcrab on 2010-06-29
> **ihermit said:**
> Who cares? 

Me.

Thanks for the article.  Good read.  It never hurts to know what is going on with your hardware.

---

### Post by Spr0k3t on 2010-06-29
If you are really wanting to take complete control over your android based phone, there is one way to go about it.  Root your android.  Install apps outside of the market.  Now you can control what apps install and remain on your android based phone.  Also, this news is old as Google has pulled this gun twice before.  So far, the only time they have pulled apps are when the apps in question do absolutely nothing (or next to nothing) for the user and collect data for the developer.

I love my rooted ANDROID based phone.

---

### Post by Bachstelze on 2010-06-29
I can barely imagine the uproar here if it were Apple. Nice brainswashing job, Google!

---

### Post by LeifAndersen on 2010-06-29
EDIT:  Woops, wrong thread...sorry.

---

### Post by NCLI on 2010-06-29
How is this any more risky than Update Manager? A potential attacker could simply disguise a malicious program as an important security update for X.org or something similar, then use the Man-in-the-middle approach to push it to all Ubuntu computers.

Sure, they can force install them on  android, but I doubt most users read the source code of updates, or don't install important security updates, so it's really no less risky.

---

### Post by alexan on 2010-06-29
Maemo seem more clean, sorry Google.. this ain't for me.

---

### Post by sn0m on 2010-06-29
I'm going to stick with nokia as well. Sorry google, you're doing an apple with this.

---

### Post by Old_Grey_Wolf on 2010-06-29
<sarcasm> I was considering an Android phone because the OS is based on the Linux kernel. It looks like they think I am renting the OS, and they can do whatever they want whenever they want. For me, they just lost any competitive advantage. If they are going to change the OS without my password then they are taking my security and freedom away. WTF. Do they think it is just a phone, and you shouldn't need to know anything about root or sudo to use it? </sarcasm>

:lolflag:

Honestly, this is based on the possibility that someone can implement a Man-In-The-Middle attack against the SSL (Secure Socket Layer).

---

### Post by jonojono on 2010-06-29
> **NCLI said:**
> How is this any more risky than Update Manager? A potential attacker could simply disguise a malicious program as an important security update for X.org or something similar, then use the Man-in-the-middle approach to push it to all Ubuntu computers.


Actually, that's incorrect.  Apt (and therefore update-manager) provides a digital signature for the Release files associated with any package updates.  This is why I say:

> 
Just as used in many desktop application auto-updating components, the update manifest and/or payload should be digitally signed by the distributor in addition to using SSL as a transport.


If you MITM the SSL connection for update-manager, you will _not_ be able to push a malicious update, unlike the current situation with Android.

Regards,
Jon Oberheide

---

### Post by chessnerd on 2010-06-29
My only thought is this:

Can users legally circumvent this ability?

If not, it seems like Google has too much power in this matter. 

At least users can avoid losing iPod support on their other applications by just not downloading the latest firmware update. Heck, some PS3 users could even have kept their Linux support by just refusing to upgrade. At least they have a choice (albeit a not-very-good one). This ability takes hold as soon as the phone has a signal. You can't even use the phone without a signal.

I have yet to see even Apple or Microsoft actually exercise this kind of control of their software. This is pretty powerful stuff. It should only be used in the event of an emergency situation. I think Google has a case that this recent situation was an emergency, but I think it can also be argued that it wasn't. 

We aren't talking about Windows Update or the Update Manager, we are talking about a forced update system where users don't have any control over whether or not their system gets updated. If I want to run Windows XP with no service packs for whatever reason Windows Update would bug me to upgrade, but it would never force it on me.

This type of total control should probably be voluntary.

---

### Post by Dr. C on 2010-06-30
> **chessnerd said:**
> My only thought is this:

Can users legally circumvent this ability?

If not, it seems like Google has too much power in this matter. 

At least users can avoid losing iPod support on their other applications by just not downloading the latest firmware update. Heck, some PS3 users could even have kept their Linux support by just refusing to upgrade. At least they have a choice (albeit a not-very-good one). This ability takes hold as soon as the phone has a signal. You can't even use the phone without a signal.

I have yet to see even Apple or Microsoft actually exercise this kind of control of their software. This is pretty powerful stuff. It should only be used in the event of an emergency situation. I think Google has a case that this recent situation was an emergency, but I think it can also be argued that it wasn't. 

We aren't talking about Windows Update or the Update Manager, we are talking about a forced update system where users don't have any control over whether or not their system gets updated. If I want to run Windows XP with no service packs for whatever reason Windows Update would bug me to upgrade, but it would never force it on me.

This type of total control should probably be voluntary.

There are two defenses:

1) Applications that were not installed from the Android marketplace are not affected by this. Unlike the iPhone there is no requirement that the Android marketplace be the sole source for applications.

2) > 4.2 Some components of Products (whether developed by Google or third parties) may also be governed by applicable open source software licenses. In the event of a conflict between the Terms and any such licenses, the open source software licenses shall prevail with respect to those components.  Open source licenses control when in conflict with the Android Marketplace terms. So for example an application under the GPL could not be revoked. Again very different from the iPhone.

Still for propriety applications downloaded from the Android Marketplace these are very poor terms since in effect the software license can be arbitrarily revoked.

---

### Post by Dustin2128 on 2010-06-30
> **Bachstelze said:**
> I can barely imagine the uproar here if it were Apple. Nice brainswashing job, Google!

Indeed.

---

### Post by AllRadioisDead on 2010-06-30
> **Crunchy the Headcrab said:**
> Me.

Thanks for the article.  Good read.  It never hurts to know what is going on with your hardware.

Was it honestly that much of a surprise to you though?
I never doubted Google had the ability to do that even before I bought my phone.

---

### Post by Johnsie on 2010-06-30
Isn't this similar to how Ubuntu automatically removes unneeded packages? When my Android wants to update itself it asks me if I want to do the update.

---

### Post by madnessjack on 2010-06-30
> **jonojono said:**
> Actually, that's incorrect.  Apt (and therefore update-manager) provides a digital signature for the Release files associated with any package updates.  This is why I say:



If you MITM the SSL connection for update-manager, you will _not_ be able to push a malicious update, unlike the current situation with Android.

Regards,
Jon Oberheide

I'm no expert (seriously not even close) but surely this isn't the case because these updates are not pushed via the Internet at all. They get invoked via the cell network and then pushed across the Internet via a secure connection.

---

### Post by HappinessNow on 2010-06-30
> **Johnsie said:**
> Isn't this similar to how Ubuntu automatically removes unneeded packages? When my Android wants to update itself it asks me if I want to do the update.Exactly.

For those who want to wear the Tin Foil Hats, have fun with that. I choose to enjoy Google services to the fullest.

---

### Post by AllRadioisDead on 2010-06-30
> **HappinessNow said:**
> Exactly.

For those who want to wear the Tin Foil Hats, have fun with that. I choose to enjoy Google services to the fullest.

For those who wear tinfoil hats, I'd advise against buying a smartphone in the first place.

---

### Post by Tristam Green on 2010-06-30
> **ihermit said:**
> Who cares? 
At least this way they can install critical security fixes on the fly, I don't really see a problem with this. This looks like people trying to spread more paranoria over the internet.
My phone's rooted anyways, I won't be recieving any of these OTA updates.

That's what I thought when I read the OP.  Then I saw who the OP was, and expected less.

> **Bachstelze said:**
> I can barely imagine the uproar here if it were Apple. Nice brainswashing job, Google!

No brainwashing, this is no different than an Apple updater or an MS updater.

> **HappinessNow said:**
> Exactly.

For those who want to wear the Tin Foil Hats, have fun with that. I choose to enjoy Google services to the fullest.

Seems to be a lot of those nowadays.

---

### Post by Frogs Hair on 2010-06-30
If the end user agrees to this not much can be done , also the applications that were removed were identified as adware . One application was movie trailer that was actually collecting user data. In that case I would be glad that Google discovered and removed it.

---

### Post by jonojono on 2010-06-30
> **chessnerd said:**
> My only thought is this:

Can users legally circumvent this ability?


I'll be releasing an application shortly that will allow users to selectively disable the REMOVE_ASSET/INSTALL_ASSET functionality.  A better approach would be to hook the code to prompt the user to approve/deny individual invocations of those intents, but I'm lazy. :-P

Regards,
Jon Oberheide

---

