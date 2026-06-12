---
title: "Google Chrome Extension that steals Login Details - How safe are we?"
date: 2010-07-10
forum: Security
---

### Post by dkd903 on 2010-07-10
In a major blow to Google Chrome’s claim of being one of the safest browsers, [a developer  has come up with an extension]("http://digitizor.com/2010/07/10/major-blow-for-google-chrome-extension-capable-of-stealing-login-details-developed/") that he says can steal login details of the user.

Andreas Grech has developed an extension for Google Chrome which he says can steal login details of the user. After installing the extension, he says it will send the login ID and passwords of users to him through email. He says that so far his method has worked with GMail, Twitter and Facebook, among other sites.

This is what Grech wrote:

    The Google Chrome browser allows the installation of third-party extensions that are used to extend the browser to add new features. The extensions are written in JavaScript and HTML and allow manipulation of the DOM, amongst other features.

    By allowing access to the DOM, an attacker can thus read form fields…including username and password fields. This is what sparked my idea of creating this PoC.

    The extension I present here is very simple. Whenever a user submits a form, it tries to capture the username and password fields, sends me an email via an Ajax call to a script with these login details along with the url and then proceeds to submit the form normally as to avoid detection.

    This simple procedure has been successful against Gmail, Facebook, Twitter and other major websites.

Grech has also published his code as a proof of how he achieved this. You can view it at [his blog]("http://blog.dreasgrech.com/2010/07/stealing-login-details-with-google.html").

Until Google comes up with a proper patch to fix this, be careful of the extensions you install.

---

### Post by wacky_sung on 2010-07-10
Well,i have no doubt it as i have already noted for the weakness of google login which does not come with a encrypted master password as firefox prior to what you have written.In fact,i try to refrain using addon / extension on either firefox /google chrome.On another case of firefox addon which contain trojan which happened eariler this year as well.Stay away from addon / extension help you to save another day.

[http://www.zdnet.com/blog/hardware/update-firefox-add-on-contained-toxic-trojan-code/7171](http://www.zdnet.com/blog/hardware/update-firefox-add-on-contained-toxic-trojan-code/7171)

---

### Post by lovinglinux on 2010-07-11
I have already posted my concerns about Chrome extension security on several threads. Is not because I don't like Chrome, but because I think there is a major flaw in the way they handle third-party extensions. 

Google Chrome extensions are "more secure" by design, because for them to access browser features, the developer needs to declare the extension permissions in the extension configuration file. Nevertheless, a developer with bad intentions could easily add all the permissions it needs. Since Google doesn't review any extensions submitted to the extension gallery, like Mozilla does with Firefox extensions (even updates), the self-contained permission model could be easily defeated and a malware extension could be spread easily.

Another thing that bothers me is that Google promotes the extension gallery to potential developers by comparing it with "other browsers" galleries,  saying that their extensions are made available immediately to users, because there is no review process. They have a huge EULA, that basically says Google has no responsibility for the quality of the extensions in their gallery.

Recently Google started to provide a method of running extensions in the incognito mode. While Mozilla has a policy in which extensions that do not comply with the Private Browsing mode will not be approved, [Google wrote this to the developers](http://blog.chromium.org/2010/06/extensions-in-incognito.html):

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=163073&stc=1&d=1278853389[/IMG][/CENTER]

Seriously? "**Try to be a good citizen**"? That basically says that if you don't care or has the competence to use the incognito API in your extensions it won't make any difference. Your extension will be available to Chrome users as well.

> **wacky_sung said:**
> On another case of firefox addon which contain trojan which happened eariler this year as well.Stay away from addon / extension help you to save another day.

In that case, the only extension affected was a Windows experimental extension, which means it wasn't approved by Mozilla editors. These extensions display warnings before the user is able to install them, making it clear that the extension hasn't be reviewed and could harm your computer. Nevertheless, Mozilla automatically scans all extensions, including the experimental ones, for infections. But on that particular case, the scanner failed. They already added two more malware scans to the extension validation chain and rescanned ALL extensions available on the site. They found only one other extension infected, which was in fact a false positive.

You can read more about that case [here](http://blog.mozilla.com/addons/2010/02/04/please-read-security-issue-on-amo/).

I'm a Firefox extension developer with 7 extensions already approved and I have more than 60 extensions installed. I must say I was impressed with how Mozilla deals with extension validation and security, when I started to submit extensions to their gallery. One of my extensions has been denied twice, just because of some javascript warnings (not even errors). 

When you submit an extension, there is a validation step, in which the system scans the code functions for possible vulnerabilities and flagged file types, in addition to the malware scan. If they are flagged, then only a senior editor can then approve it. All extensions submitted to Mozilla (not experimental) are reviewed manually and the extension is also tested individually. If your extension is approved, it doesn't mean you have a free pass. All new versions you submit needs to be reviewed too. For instance, if you look my extension [FlashVideoReplacer](https://addons.mozilla.org/en-US/firefox/addon/161869/versions/), you will notice that version 1.0.0 has been approved, but version 1.0.1 is still waiting for review.

---

### Post by wacky_sung on 2010-07-11
> I'm a Firefox extension developer with 7 extensions already approved and I have more than 60 extensions installed.

I am deeply appreciated for those firefox/google chrome developers writing all those addons/extensions.In my personal point of view we do not really need most of those addons/extensions because it just add those extra features in which we want it to incorporate into the browser.I have seem a lot of handy tools in the firefox addons which use to test/crack vulnerability in the webpage.I may not need it that does not mean it is a poison if you want it.Everybody live with a choice of their own.

---

### Post by lovinglinux on 2010-07-13
[http://blog.mozilla.com/addons/2010/07/13/add-on-security-announcement/](http://blog.mozilla.com/addons/2010/07/13/add-on-security-announcement/)

> **Add-on security vulnerability announcement**

One malicious add-on and another add-on with a serious security vulnerability were discovered recently on the Mozilla Add-ons site. Both issues have been dealt with, and the details are described below.

**Mozilla Sniffer**

Issue

An add-on called &#8220;Mozilla Sniffer&#8221; was uploaded on June 6th to addons.mozilla.org. It was discovered that this add-on contains code that intercepts login data submitted to any website, and sends this data to a remote location. Upon discovery on July 12th, the add-on was disabled and added to the blocklist, which will prompt the add-on to be uninstalled for all current users.

Impact to users

If a user installs this add-on and submits a login form with a password field, all form data will be submitted to a remote location. Uninstalling the add-on stops this behavior. Anybody who has installed this add-on should change their passwords as soon as possible.

Status

Mozilla Sniffer has been downloaded approximately 1,800 times since its submission and currently reports 334 active daily users. All current users should receive an uninstall notification within a day or so. The site this add-on sends data to seems to be down at the moment, so it is unknown if data is still being collected.

Mozilla Sniffer was not developed by Mozilla, and it was not reviewed by Mozilla. The add-on was in an experimental state, and all users that installed it should have seen a warning indicating it is unreviewed. Unreviewed add-ons are scanned for known viruses, trojans, and other malware, but some types of malicious behavior can only be detected in a code review.

Credit

This issue was originally reported by Johann-Peter Hartmann.

Note

Having unreviewed add-ons exposed to the public, even with low visibility, has been previously identified as an attack vector for hackers. For this reason, we&#8217;re already working on implementing a new security model for addons.mozilla.org that will require all add-ons to be code-reviewed before they are discoverable in the site. [Here&#8217;s more information about it](https://forums.addons.mozilla.org/viewtopic.php?f=19&t=1134&p=3158).

**CoolPreviews**

Issue

A security escalation vulnerability was discovered in version 3.0.1 of the CoolPreviews add-on. The vulnerability can be triggered using a specially crafted hyperlink. If the user hovers the cursor over this link, the preview function executes remote JavaScript code with local chrome privileges, giving the attacking script control over the host computer. Version 3.0.1 and all older versions have been disabled on addons.mozilla.org, and a fixed version was uploaded and reviewed within a day of the developer being notified.

Impact to users

Proof of concept code for this vulnerability was posted on [this blog](http://d.hatena.ne.jp/teramako/20100621/p1), but no known malicious exploits have been reported so far. If a user has a vulnerable version installed and clicks on a malicious link that targets the add-on, the code in the malicious link will run with local privileges, potentially gaining access to the file system and allowing code download and execution.

All users of CoolPreviews should update to the latest version as soon as possible in order to avoid exposure.

Status

Currently, 177,000 users have a vulnerable version installed. This is less than 25% of the current install base and it will continue to decrease as more users are prompted to update to a new version. Vulnerable versions will also be blocklisted very soon.

Credit

This issue was originally reported by Alice White.

---

