---
title: "firefox updating to namoroka 3.6.10pre"
date: 2010-09-03
forum: The Cafe
---

### Post by kmsalex on 2010-09-03
Today i ran a system update, and my Firefox upgraded to namoroka 3.6.10pre. Update manager said nothing about firefox going from a stable to a daily build, I don't think i mind so much, asuming it will go back to stable when it comes out. But why/how did this happen? Anyone else experience this?

---

### Post by kpkeerthi on 2010-09-03
Do you remember adding mozilla-daily ppa lately?

---

### Post by kmsalex on 2010-09-03
No but when i looked in the source center of Ubuntu tweak Firefox stable is checked, but i don't even remeber enabling that. But even if that was the case shouldn't the change log in update manager have said going form Firefox 3.6.8 to namoroka 3.6.10 instead of Firefox 3.6.10?

---

### Post by Frogs Hair on 2010-09-03
I have been using Namoroka since 9.10 and the only way to get that update as far as know is to add the Mozilla daily or one day a month build  ppa. Check software sources in the other software tab  and see if Mozilla daily is listed .

To get back the normal Firefox release you will have to purge the ppa and reinstall Firefox from the software center. If you are using Ubuntu Tweak make sure you don't enable software sources you don't want .

---

### Post by VastOne on 2010-09-03
Have you recently installed Ubuntu Tweak?

That may have added it

---

### Post by handy on 2010-09-04
Namoroka is standard fare on Arch... <shrug>

---

### Post by cejack on 2010-09-04
I can't seem to get my new Ubuntu 10.04 upgrade install to update Firefox from 3.5.3 up to any 3.6.X release.  

Any ideas what may be holding me back?  Tried all the various PPA's in the software sources and no dice.  

Synaptic shows Firefox 3.6.10~hg..... is installed.

---

### Post by Frogs Hair on 2010-09-04
> **cejack said:**
> I can't seem to get my new Ubuntu 10.04 upgrade install to update Firefox from 3.5.3 up to any 3.6.X release.  

Any ideas what may be holding me back?  Tried all the various PPA's in the software sources and no dice.  

Synaptic shows Firefox 3.6.10~hg..... is installed.

You have the latest release , I think you're confusing .01 with .10 . If you would like to upgrade to 4.x beta there is a ppa for that.

---

### Post by lovinglinux on 2010-09-04
> **cejack said:**
> I can't seem to get my new Ubuntu 10.04 upgrade install to update Firefox from 3.5.3 up to any 3.6.X release.  

Any ideas what may be holding me back?  Tried all the various PPA's in the software sources and no dice.  

Synaptic shows Firefox 3.6.10~hg..... is installed.

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:


**1 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

