---
title: "SDK problems"
date: 2016-10-22
forum: Ubuntu Application Development
---

### Post by sitongia on 2016-10-22
I'm trying the SDK (which is Qt Creator, eh?) for the first time on my desktop (Intel NUC i3, Ubuntu 14.04.1). I'm going through the introductory instructions at
[https://developer.ubuntu.com/en/phone/platform/sdk/installing-the-sdk/](https://developer.ubuntu.com/en/phone/platform/sdk/installing-the-sdk/)
I've created the HTML5 project.
The SDK recognizes my Nexus 4. Didn't have to do much there. The device status meatball shows a green dot. It is ready.
I also tried to create the Emulator. It has been starting up for about 20 minutes and how shows the orange Ubuntu screen, but no change in the dots under the word "Ubuntu".
When I try to deploy to my Nexus 4, it works for a short time and then an alert window pops up saying "Unknown Error". It has an "OK" button.
The Issues tab has three messages. Unfortunately, I cannot copy and paste them:
   desktop:Exec:Try HTML5:found unexpected Exec with architecture 'all':./qtc_device_debughelper.py
   security:policy_groups_safe:TryHTML5:debug:(REJECT) reserved policy group 'debug':not for production use
   security:policy_groups_webapp:TryHTML5.apparmor:found unusual policy groups:debug

Can I get this fixed?
Thanks.

---

