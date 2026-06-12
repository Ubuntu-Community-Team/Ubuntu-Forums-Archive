---
title: "Problem with Ubuntu Mate 18.04 Beta 2"
date: 2018-04-07
forum: Ubuntu Development Version
---

### Post by darrel_jw on 2018-04-07
I have an application (BibleAnalyzer) that runs beautifully in Ubuntu Mate 17.10. But when installing 18.04 Beta 2 and trying to run the same application I get the error message "Error: Dependency is not satisfiable: Python imaging (>=3.1)" and I cannot figure out how to satisfy the dependencies nor what it is looking for. I contacted the developer of BibleAnalyzer and he said "[COLOR=#333333][FONT=&quot]Apparently this version does not contain the Python Imaging Library (PIL or Pillow) or calls it something else.[/FONT][/COLOR]" So I installed everything I could find relating to "PIL" or "Pillow" and still no-go. Can anyone help me to understand what changed from 17.10 to 18.04?

Darrel

---

### Post by wildmanne39 on 2018-04-07
*Thread moved to **Ubuntu Development Version, a more appropriate forum**.*

---

### Post by Frogs Hair on 2018-04-07
In the development cycle there can be new packages added to the repository regularly or even daily. I wouldn't be overly concerned until the final release.

Edit: Do the packages in the image look familiar ? These are available on 18.04 and I found them with the synaptic package manager.

---

### Post by darrel_jw on 2018-04-08
Yes, I had (I think) installed both of those, but was still getting the Dependency not met error. I am back running on 17.10 and everything plays beautifully. I really want to install the Beta 2, but since I do a LOT of Bible study and research I have to have BibleAnalyzer working, and so far it will not play on 18.04.

Darrel

---

### Post by flocculant on 2018-04-08
python imaging isn't in the bionic repos - and if it's not there now it's extremely unlikely it will be in 3 weeks time.

You could try grabbing the artful version [https://packages.ubuntu.com/artful/python-imaging](https://packages.ubuntu.com/artful/python-imaging)

python-pil is in the repo's.

It's up to the developer of Bible Analyzer to do what's needed to make it work in Bionic.

---

### Post by darrel_jw on 2018-04-08
Hello!

Thanks for the reply and mentioning that .deb package. When I installed that BibleAnalyzer then installed beautifully. The only problem now is colors. It does not seem to matter what color scheme I use the background color always goes to blue when select a Strong's number or click on a verse. I am attaching two screen shots: the first is when I click on a Strong's number and the second when I click on a verse number.

Again it does not seem to matter what theme I use. I tried Radiant-MATE first and now am on Ambiant-MATE-Dark and the results are the same in both cases, with the background going blue.

Darrel

---

