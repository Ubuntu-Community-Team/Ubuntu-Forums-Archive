---
title: "Upgrade to Firefox 4 in Ubuntu 10.04 &amp; 10.10"
date: 2011-03-23
forum: Sudan Team
---

### Post by zero-n on 2011-03-23
1- Add Mozilla team repository
```

sudo add-apt-repository ppa:mozillateam/firefox-stable 

```2- Update repository list
```

sudo apt-get update

```3- Upgrade your Firefox
```

sudo apt-get upgrade

```

---

### Post by tumutanzi on 2011-03-24
Here is the easiest method ever on the earth.

Just copy the following command and paste it on the terminal of Ubuntu (Press the keyboard: Ctrl+Alt+T, or click Applications > Terminal).
**sudo add-apt-repository ppa:mozillateam/firefox-stable && sudo apt-get update && sudo apt-get upgrade**

Ref: [http://www.tumutanzi.com/2011/03/upgrade-to-firefox-4-in-ubuntu-1004.html](http://www.tumutanzi.com/2011/03/upgrade-to-firefox-4-in-ubuntu-1004.html)

---

### Post by zero-n on 2011-03-24
using && is good but if command exit status is not 0 which mean an error your method will not upgrade Firefox.
Specially some people are suffering from repository gpg key problem and they didn't fix it

---

### Post by abhinavy2j on 2011-05-13
The first command worked fine. But after the update command, i got this :

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Thanks for the help.

---

### Post by zero-n on 2011-05-13
its seems that you have problem with your Opera repository.

did you tried the upgrade command cause i think problem in one repository won't stop other repositories from update.

---

### Post by tumutanzi.com on 2011-09-29
> **tumutanzi said:**
> Here is the easiest method ever on the earth.

Just copy the following command and paste it on the terminal of Ubuntu (Press the keyboard: Ctrl+Alt+T, or click Applications > Terminal).
**sudo add-apt-repository ppa:mozillateam/firefox-stable && sudo apt-get update && sudo apt-get upgrade**

Ref: [http://www.tumutanzi.com/2011/03/upgrade-to-firefox-4-in-ubuntu-1004.html](http://www.tumutanzi.com/2011/03/upgrade-to-firefox-4-in-ubuntu-1004.html)

Sorry, the right link of "Upgrade to Firefox 4 in Ubuntu 10.04 & 10.10" is: [http://tumutanzi.com/archives/142](http://tumutanzi.com/archives/142)

Now the latest Firefox is the SEVEN version.

---

