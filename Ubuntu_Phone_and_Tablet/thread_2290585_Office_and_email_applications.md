---
title: "Office and email applications"
date: 2015-08-13
forum: Ubuntu Phone and Tablet
---

### Post by alaric-cundy on 2015-08-13
I purchased a bq Aquarius 4.5 with Ubuntu pre-loaded about four months ago.  Overall, I am very pleased, but I have a few comments / questions:
[LIST=1]
[*]Firefox is available as an App on Android phones.  Does anyone know if there are plans / progress to offer it via the UBUNTU app store?
[*]I use Dekko - described as a beta product, and consequently not 100% trouble free - for emails.  I was amazed as to how easy it was to set up for a UK 'BTInternet' email address, but never-the-less I was hoping there would be something more like Thunderbird or Evolution available.  Does anyone know if there are plans to make such an email client available for UBUNTU Phone?
[*]Possibly, for me, the biggest limitation is that I have not yet found any way of opening 'Office' documents or spreadsheets that regularly come in as email attachments from friends and colleagues.  Have I missed a trick somewhere?  Are there any plans to resolve it?  'Document Viewer' works perfectly well for PDF documents but not for documents with, for example, DOC, ODT, XLSX etc extensions.
[/LIST]

---

### Post by howefield on 2015-08-13
> **alaric-cundy said:**
> Firefox is available as an App on Android phones.  Does anyone know if there are plans / progress to offer it via the UBUNTU app store?

Good place to ask is the weekly Q&A session at ubuntuonair.com but I don't believe it is part of Canonicals plans.

> I use Dekko - described as a beta product, and consequently not 100% trouble free - for emails.  I was amazed as to how easy it was to set up for a UK 'BTInternet' email address, but never-the-less I was hoping there would be something more like Thunderbird or Evolution available.  Does anyone know if there are plans to make such an email client available for UBUNTU Phone?

As I understand, Dekko is likely to be made part of the default installation from the next OTA if all goes well. As far as I know that is the extent of Canonical plans for an email client.

> Possibly, for me, the biggest limitation is that I have not yet found any way of opening 'Office' documents or spreadsheets that regularly come in as email attachments from friends and colleagues.  Have I missed a trick somewhere?  Are there any plans to resolve it?  'Document Viewer' works perfectly well for PDF documents but not for documents with, for example, DOC, ODT, XLSX etc extensions.


Not sure about the proprietary formats but I believe there is work ongoing (but at an early stage) to support libreoffice, eg [https://blueprints.launchpad.net/ubuntu-docviewer-app/+spec/libreoffice-docviewer-integration](https://blueprints.launchpad.net/ubuntu-docviewer-app/+spec/libreoffice-docviewer-integration)

---

### Post by howefield on 2015-08-14
> **howefield said:**
> As I understand, Dekko is likely to be made part of the default installation from the next OTA if all goes well. As far as I know that is the extent of Canonical plans for an email client.

Or.. perhaps not the next OTA :)

[https://lists.launchpad.net/ubuntu-phone/msg14835.html](https://lists.launchpad.net/ubuntu-phone/msg14835.html)

---

### Post by grahammechanical on 2015-08-14
Firefox on Android is an official Android port by the Mozilla developers. It would require the Mozilla developers to make the port to the Ubuntu phone in order to see an official port of Firefox in the phone app store.

I do not think that Canonical developers are being tasked to make ports of other people's software. Besides the phone has an official web browser called Browser. It is part of the default install of desktop Ubuntu as well. Work has to be done to make Browser usable on phones, tablets and desktops. It is not feature comparable with a browser like Firefox. Not by any means.

For example, on the desktop it has only recently got tab browsing. So, in my opinion, if Canonical software engineers are going to be paid to develop a browser it would be the Ubuntu Web Browser. It may one day even supplant Firefox as the default browser. There is a long way to go before that happens.

I would apply the same reasoning to other so-called "must have" applications.

---

### Post by SeijiSensei on 2015-08-14
Does Ubuntu Phone include software to run apps written for Android?  If not, why not? 

I know nothing about Phone and am asking simply as an interested observer.

---

### Post by howefield on 2015-08-15
> **SeijiSensei said:**
> Does Ubuntu Phone include software to run apps written for Android?

No.

> If not, why not?

Canonical have invested in creating developer tools to aid making native applications or to port them from other platforms. There is also the (current) focus on scopes which attempt to take the focus away from the traditional app grid.

---

### Post by alaric-cundy on 2015-08-16
Thank you everyone for your helpful comments.  It seems that the gap between Ubuntu Phone and Ubuntu Desktop is much wider than some would expect.  Something akin to the Desktop 'WINE' would be very helpful for those who wanted to try to port their favourite Android Apps and would doubtless hugely broaden the appeal of UBUNTU Phone, but it sounds as though there are no immediate plans to do so.  For anyone who is just browsing these pages curious to find out more about UBUNTU phone - well it does basic Smart-phone functions well, albeit differently, but don't yet expect it to be a fully-fledged alternative to Android.

---

### Post by naomibrown on 2015-09-01
> **alaric-cundy said:**
> 
[*]Possibly, for me, the biggest limitation is that I have not yet found any way of opening 'Office' documents or spreadsheets that regularly come in as email attachments from friends and colleagues.  Have I missed a trick somewhere?  Are there any plans to resolve it?  'Document Viewer' works perfectly well for PDF documents but not for documents with, for example, DOC, ODT, XLSX etc extensions.

This is also the biggest problem for me! I have managed to get around this by using googlemail and clicking on Print (Google Cloud Print), then saving the document as a PDF in google drive. I can then open it :)

Not ideal by any stretch, but it does work.

---

### Post by ian-weisser on 2015-09-01
The idea of running Android apps on Ubuntu has been discussed in this forum, at Ubuntu Online Summits, and several other venues.

Ubuntu handles some services and permissions differently. The two systems are not easily mappable. A significant effort is needed to create an Android-compatible interface for Ubuntu. Nobody has offered to do that work.

Also, the ghost of OS2 comes up in most discussions. OS2 ran Windows applications...so it gained an undeserved image as a poor copy of Windows. Ubuntu developers are not interested in making an OS that will be viewed as a poor copy of Android. They want to make something different and better.

Why, another blog post [explaining the issue]("https://medium.com/@cparrino/on-the-ubuntu-phone-and-the-challenges-of-mobile-operating-systems-d539c4d08df5") popped up today:
> A problem that could only be aggravated by succumbing to the popular  suggestion of &#8220;why don&#8217;t you just support Android apps&#8221;&#8202;&#8212;&#8202;the perfect  way to ensure developers will never need to target your platform, and  for users to get a me too experience developed for someone else.

If somebody wants to start a project to create an Android-compatible interface for Ubuntu, feel free. It's open source.

---

### Post by grahammechanical on 2015-09-01
Of course, if there is a big enough market demand for Ubuntu Phones then Android app developers might have the incentive to port their apps to the Ubuntu phone. Especially, paid for apps. That is the optimum solution. Do Android apps run on Windows phones or Apple phones? Or have the apps been ported to those platforms?

Oh, by the way, there is a script for converting deb to snap. Now we need a script for converting apk to snap or click.

[https://github.com/mikix/deb2snap](https://github.com/mikix/deb2snap)

---

### Post by alaric-cundy on 2015-09-02
I don't know anything about Windows phones, but quite a lot of Apps are available both on Android and iPhones.  I would have thought that something similar to the LibreOffice Viewer App that I know is available free for Android phones is pretty well a 'must' for UBUNTU phones too...

---

### Post by jtappin on 2015-09-02
> **alaric-cundy said:**
> I don't know anything about Windows phones, but quite a lot of Apps are available both on Android and iPhones.  I would have thought that something similar to the LibreOffice Viewer App that I know is available free for Android phones is pretty well a 'must' for UBUNTU phones too...

I forget where I saw it, but I believe that it is being worked on.

---

