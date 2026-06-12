---
title: "AppArmor, Firefox, and plug-ins"
date: 2012-11-26
forum: Security
---

### Post by mike acker on 2012-11-26
Q: Does AppArmor protect Firefox from the installation and/or activation of un-wanted plug-ins?

particularly this new facebook thing? 

Q: How would we evaluate the AppArmor profile for Firefox in this regard ?

note: I'm running the profile provided by Canonical.

---

### Post by vasa1 on 2012-11-26
> **mike acker said:**
> Q: Does AppArmor protect Firefox from the installation and/or activation of un-wanted plug-ins?

particularly this new facebook thing? 

Q: How would we evaluate the AppArmor profile for Firefox in this regard ?

note: I'm running the profile provided by Canonical.

Recent versions of Firefox will inform you of attempts to install new plug-ins whether you use Apparmor or not.

AFAIK, the Facebook thing isn't on by default. If it is, you can turn it off from **about:config**. Enter **social** in the search bar of the about:config page and ensure that the relevant entries are set to false.
```
social.active;false
social.enabled;false
```etc

---

### Post by mike acker on 2012-11-26
> **vasa1 said:**
> Recent versions of Firefox will inform you of attempts to install new plug-ins whether you use Apparmor or not.

AFAIK, the Facebook thing isn't on by default. If it is, you can turn it off from **about:config**. Enter **social** in the search bar of the about:config page and ensure that the relevant entries are set to false.
```
social.active;false
social.enabled;false
```etc

thanks . as a fugitive from that other o/s i must say i did not appreciate it when sites attempted un-wanted browser updates . 

hopefully the only way Firefox gets a plug-in is when the owner selects tools | add ons and selects an update .

this is critical . a hidden update could be re-directing browser activity without the knowlege of the owner and that could be just a detrimental a a root kit .

---

### Post by cariboo on 2012-11-27
> **mike acker said:**
> thanks . as a fugitive from that other o/s i must say i did not appreciate it when sites attempted un-wanted browser updates . 

hopefully the only way Firefox gets a plug-in is when the owner selects tools | add ons and selects an update .

this is critical . a hidden update could be re-directing browser activity without the knowlege of the owner and that could be just a detrimental a a root kit .

If you are using Firefox from the repositories, auto-updating is turned off. The only way to update Firefox, is to update it using update-manager, the Software Centre, synaptic or from the command line. No hidden updates here. :-D

---

### Post by mike acker on 2012-11-27
> **cariboo907 said:**
> If you are using Firefox from the repositories, auto-updating is turned off. The only way to update Firefox, is to update it using update-manager, the Software Centre, synaptic or from the command line. No hidden updates here. :-D

thanks, pard, I appreciate that note.

I did go and check the switches as directed by the earlier post: they are set properly (both=false)

:)

the next question: can a script access that same page and turn the switches on ?  

AppArmor should prevent this  (I am running Firefox with AppArmor on, using the profile provided by Canonical ) .

---

### Post by zombifier25 on 2012-11-27
If you're really paranoid about malicious scripts, you should install NoScript. It gives you per-site permissions for scripts, and it also protects you from certain exploits.

---

### Post by SlugSlug on 2012-11-27
> **mike acker said:**
> 

particularly this new facebook thing? 



What new facebook thing?

---

### Post by zombifier25 on 2012-11-27
> **SlugSlug said:**
> What new facebook thing?

Firefox 17 has a new feature that integrates Facebook directly into the browser. Before anyone screams "PRIVACY INVASION!!1!!1", it's only a plugin that is activated only if the user chooses to.

---

### Post by SlugSlug on 2012-11-27
Ahh thanks - just found this 

[http://arstechnica.com/information-technology/2012/11/firefox-17-is-more-social-and-secure-but-doesnt-care-for-leopards/](http://arstechnica.com/information-technology/2012/11/firefox-17-is-more-social-and-secure-but-doesnt-care-for-leopards/)

---

