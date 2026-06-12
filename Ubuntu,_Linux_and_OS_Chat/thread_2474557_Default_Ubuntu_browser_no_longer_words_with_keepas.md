---
title: "Default Ubuntu browser no longer words with keepassxc?"
date: 2022-05-02
forum: Ubuntu, Linux and OS Chat
---

### Post by Elven Decker on 2022-05-02
I've been using Linux since it was distributed on floppies and I honestly thought Ubuntu would be my distribution choice forever. I've had second thoughts though since 22.04 Firefox was made into a snap without first making sure it would still work with keepassxc.  Not that it's a bad inconvenience, but because it indicates that the user experience of the maintainers and developers is starting to overshadow the user experience of the users. It's sad, but I've started to shop around. My other issue is that I wasn't sure where to send this feedback to Canonical. Best

---

### Post by poorguy on 2022-05-02
I'm using Lubuntu 22.04 and I downloaded and installed Firefox 99.0.1.tar.bz2 and it works like a charm.

[https://www.mozilla.org/en-US/firefox/linux/?utm_medium=referral&utm_source=support.mozilla.org](https://www.mozilla.org/en-US/firefox/linux/?utm_medium=referral&utm_source=support.mozilla.org)

[https://support.mozilla.org/en-US/kb/install-firefox-linux](https://support.mozilla.org/en-US/kb/install-firefox-linux)

---

### Post by oldfred on 2022-05-02
I installed Firefox from ppa.
That is because I have my Firefox profile in my data partition, not the normal location.
And I use KeePassXC. Some recent update in 20.04 made it a bit less convient to copy & paste id & pw. But works better again in 22.04.

Remove snap Firefox & use ppa
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

### Post by vanadium on 2022-05-03
There are indeed too many small and bigger issues with Firefox as a snap. The workaround with the least pain is to install Firefox as a deb: [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

### Post by Elven Decker on 2022-05-03
Thank you for those suggestions.  I will no doubt go ahead and use one of the various workarounds for the problem.  The deeper issue remains unresolved.  It appears Canonical is using the same strategy in rolling out Snap that they used in rolling out the Unity interface.  Ship it and fix it in the field.  It failed for GE. What makes Canonical think they can do better?  The 22.04 release notes say:
[INDENT]The Firefox snap does not support the [NativeMessaging protocol 48]("https://launchpad.net/bugs/1741074")  yet but this feature is planned to be added soon. This means for  instance that installing GNOME Shell extensions from Firefox won’t work.  As a workaround, you can try the gnome-shell-extension-manager app. [https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668](https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668)
[/INDENT]

But where is the evidence that the feature support is coming soon?  The thread shows the problem was identified in 2018, and finally confirmed (if I understand the process) on 4/21/2022.  I'm not seeing the "plan". I'm definitely not seeing "soon".  Many things depend on the Native Messaging protocol, not just GNOME Shell extensions.  It appears that voices noted the problem years ago.

So now I go back to playing with multiple versions of Linux, looking for a team with an approach that's a little more respectful of the precious time we waste when trying to make our distros behave.

---

