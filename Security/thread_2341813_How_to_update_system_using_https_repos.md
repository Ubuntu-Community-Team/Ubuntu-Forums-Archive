---
title: "How to update system using https repos"
date: 2016-10-31
forum: Security
---

### Post by hip13044b on 2016-10-31
I recently became aware of the package apt-transport-https. I'm wondering how I can install all Ubuntu updates & packages using https instead of http?

---

### Post by ian-weisser on 2016-10-31
One short answer is that the transport layer is not secure...but does not need to be secure. Each package is signed with a stronger key than https uses anyway, and apt automatically checks those signatures every time for you. In other words, a malicious actor could sniff the packages you download, or deny you access to the repo entirely, but cannot succesfully substitute a malicious package.

Another short answer is that some mirrors do provide https. [See here]("http://askubuntu.com/questions/146108/how-to-use-https-with-apt-get#comment568500_146117") for a bash script to find them.

An in-depth answer is at [http://askubuntu.com/questions/352952/are-repository-lists-secure-is-there-an-https-version](http://askubuntu.com/questions/352952/are-repository-lists-secure-is-there-an-https-version)
Another is at [http://askubuntu.com/questions/146108/how-to-use-https-with-apt-get?](http://askubuntu.com/questions/146108/how-to-use-https-with-apt-get?)

---

### Post by hip13044b on 2016-10-31
... and if the attacker steals Ubuntu's private key?

---

### Post by ian-weisser on 2016-10-31
...then https wouldn't be any protection either. Such an attacker would be inside Launchpad and the QA silos, and could poison anything the entire Ubuntu repo.
https prevents malicious substitution...and so does apt's current decade-old signature system.

---

### Post by hip13044b on 2016-11-02
[URL="https://ubuntuforums.org/member.php?u=2047311"][COLOR=#000000]I've put in my 2c here:
[/COLOR][/URL][COLOR=#000000][https://bugs.launchpad.net/ubuntu/+bug/1464064](https://bugs.launchpad.net/ubuntu/+bug/1464064)

I don't think an appeal to tradition "it's always been like this" is a strong argument. Networks are becoming a lot more hostile in recent years as governments discover the power of the Internet. Multiple layers of security are industry standard.[/COLOR]

---

### Post by ian-weisser on 2016-11-02
Discussion should probably be on the ubuntu-mirrors mailing list...or do a session on it at the Ubuntu Online Summit (in two weeks).
It's not a software issue, so nobody in the mirror community is likely to act on the bug report.
On the mailing list, you are likely to get real engagement with others interested in the topic.

Fair warning: Mirror people are hard to find, and they generally know their stuff. If you want to engage them, you need a strong argument for the extra hassle you are asking them to take on.

---

