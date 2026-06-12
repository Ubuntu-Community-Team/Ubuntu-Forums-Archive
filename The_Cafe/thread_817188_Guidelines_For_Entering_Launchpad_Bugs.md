---
title: "Guidelines For Entering Launchpad Bugs"
date: 2008-06-03
forum: The Cafe
---

### Post by cmnorton on 2008-06-03
Are there guidelines, formal or otherwise, for posting bugs in launchpad or suggesting to users in these forums that a bug be posted in launchpad?

---

### Post by nhandler on 2008-06-04
wiki.ubuntu.com is full of information about reporting bugs. You might want to start [here]("https://help.ubuntu.com/community/ReportingBugs"). That page provides information about when and how to report a bug. You might also be interested in reading [this]("https://wiki.ubuntu.com/Bugs/HowToTriage#head-5b3a5b790509899a66ff050de3e68944af4f7594") page. It is lists various pieces of information that a bug needs to include before a developer can start working on it.

Hopefully those wiki pages will provide you with enough information to report the bugs. If you still have questions, feel free to ask them.

---

### Post by 23meg on 2008-06-05
Also, when you go to [http://bugs.launchpad.net/ubuntu/+filebug](http://bugs.launchpad.net/ubuntu/+filebug) , enter a summary and click "Continue", you're shown the following text:

> Please include, if possible:

The source package you found the bug in, for help see [https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage) .

1) The release of Ubuntu you are using, via 'lsb_release -rd' or System -> About Ubuntu.
2) The version of the package you are using, via 'apt-cache policy packagename' or by checking in Synaptic.
3) What you expected to happen
4) What happened instead

A lot of this information is gathered when you use an application's 'Report a Problem' feature. See [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) for instructions.

The Ubuntu community has also created debugging procedures for a wide variety of packages at [https://wiki.ubuntu.com/DebuggingProcedures](https://wiki.ubuntu.com/DebuggingProcedures) . Following the debugging instructions for the affected package will make your bug report much more complete. Thanks!

Other useful resources:

[list][*] ["Bug reporting in Ubuntu"]("http://bryceharrington.org/drupal/node/35") by Bryce Harrington
[*] ["The bug reporting culture: 10 things to avoid, 10 things you can do"]("http://www.fabianrodriguez.com/blog/archives/2008/01/18/the-bug-reporting-culture-10-things-to-avoid-10-things-you-must-do/") by Fabián Rodríguez
[*] ["How to Report Bugs Effectively"]("http://www.chiark.greenend.org.uk/~sgtatham/bugs.html") by Simon Tatham
[*] ["Howto: File a bug report on Launchpad"]("http://kmandla.wordpress.com/2007/12/20/howto-file-a-bug-report-on-launchpad/") by K.Mandla
[/list]

---

