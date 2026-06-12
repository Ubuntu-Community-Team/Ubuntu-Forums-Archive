---
title: "windows update fails w/ installing updates"
date: 2008-06-23
forum: Windows
---

### Post by linuxmann on 2008-06-23
When windows update tries to install updates, it fails and cannot install those updates. I want to know if there is anything i could do to bypass the errors or if there is any solution for this. I have screenshots of the problem to help with the explanation.

I have Windows XP Pro SP3

---

### Post by Bungo Pony on 2008-06-23
Choose custom install and DON'T mark the trouble updates for install. You have a list of the trouble ones, so make a note of them. I believe you can also tell Windows to NEVER ask you to install those particular updates again.

---

### Post by Midwest-Linux on 2008-06-23
I am familiar with this problem, I fixed it by using a program called dial a fix. Many IT professionals have used it.


[http://www.softpedia.com/get/System/System-Miscellaneous/Dial-a-fix.shtml](http://www.softpedia.com/get/System/System-Miscellaneous/Dial-a-fix.shtml)



"Dial a fix description
Dial-a-fix is a collection of known fixes which addresses issues with Windows Update, Microsoft Installer, and more
Dial-a-fix is a collection of 'known fixes' that have been compiled over the past year that really knock out some serious Windows problems, all with one or two clicks. "When in doubt, check 'em all".

Dial-a-fix tackles issues with SSL/Cryptography, Windows Update, Microsoft Installer, and many miscellaneous shell problems. Example: If you get a blank screen when trying to visit Windows Update, simply checkmark the main Windows Update checkmark (in box #3) and click GO. Most issues can be resolved in a similar manner, if not by combinations of fixes. There is
also a 'check all' button which is useful as a last ditch effort, or when you don't understand where a particular problem is coming from.

Most of the fixes Dial-a-fix uses are found in various Microsoft Knowledgebase articles, and articles written by Microsoft MVPs. When you see a list of DLLs that need to be registered using REGSVR32.EXE, chances are they are already listed in Dial-a-fix. Mouseover a checkbox or button to obtain more information about what will be executed, or what DLLs will be registered."

---

### Post by linuxmann on 2008-06-23
> **Midwest-Linux said:**
> I am familiar with this problem, I fixed it by using a program called dial a fix. Many IT professionals have used it.


[http://www.softpedia.com/get/System/System-Miscellaneous/Dial-a-fix.shtml](http://www.softpedia.com/get/System/System-Miscellaneous/Dial-a-fix.shtml)



"Dial a fix description
Dial-a-fix is a collection of known fixes which addresses issues with Windows Update, Microsoft Installer, and more
Dial-a-fix is a collection of 'known fixes' that have been compiled over the past year that really knock out some serious Windows problems, all with one or two clicks. "When in doubt, check 'em all".

Dial-a-fix tackles issues with SSL/Cryptography, Windows Update, Microsoft Installer, and many miscellaneous shell problems. Example: If you get a blank screen when trying to visit Windows Update, simply checkmark the main Windows Update checkmark (in box #3) and click GO. Most issues can be resolved in a similar manner, if not by combinations of fixes. There is
also a 'check all' button which is useful as a last ditch effort, or when you don't understand where a particular problem is coming from.

Most of the fixes Dial-a-fix uses are found in various Microsoft Knowledgebase articles, and articles written by Microsoft MVPs. When you see a list of DLLs that need to be registered using REGSVR32.EXE, chances are they are already listed in Dial-a-fix. Mouseover a checkbox or button to obtain more information about what will be executed, or what DLLs will be registered."

Thank you for the fix! It works perfectly. I can install the updates now!

---

