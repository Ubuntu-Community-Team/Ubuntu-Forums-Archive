---
title: "Test Case Needs Revision"
date: 2015-12-30
forum: Ubuntu Development Version
---

### Post by jprzybytek on 2015-12-30
I'm do a live test on 16.04 and I notice the testcase posted does jive with what I'm seeing.

I'm expecting the current test case:
```

[Testcase]("http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/109550/testcases/1303/results#")*Proceed in your native language if you wish. Instructions will remain in English*
 Test-case Live Session Start
 Boot up the imageUbuntu GNOME boot screen is displayed
When ubiquity starts select your language in the left column
Language is selected, all labels are changed to translated versions
Press "Try Ubuntu GNOME" and wait for the Live session to start
The default desktop is displayedTest-case Live Session Usage
 Use and execute the default applications found for the desktop enviroment being runAll applications should function without error[B]
    If all actions produce the expected results listed, please [submit]("http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/109550/testcases/1303/results#add_result") a 'passed' result.
    If an action fails, or produces an unexpected result, please [submit]("http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/109550/testcases/1303/results#add_result") a 'failed' result and [file a bug]("http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/109550/buginstructions"). Please be sure to include the bug number when you [submit]("http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/109550/testcases/1303/results#add_result") your result.[/B]
 



```

What I'm finding is that the live DVD takes me straight to the desktop

1. So there is no "Ubuntu GNOME boot screen is displayed"
2. No opportunity to set the language
3. No opportunity to "Press "Try Ubuntu GNOME" and wait for the Live session to start"

We just go to the desktop. So, no pass is given even though everything seems to work fine.

Is what I see what is intended? If so can we get the test case updated.

---

### Post by kansasnoob on 2015-12-30
Ubiquity is borked and has been for some time:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1527353](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1527353)

Or maybe it's actually a casper problem? Not sure but the current images stink, and the current kernel is unusable on 2 out of 3 of my test platforms :(

---

### Post by ventrical on 2015-12-31
> **jprzybytek said:**
> I'm do a live test on 16.04 and I notice the testcase posted does jive with what I'm seeing.

I'm expecting the current test case:


What I'm finding is that the live DVD takes me straight to the desktop

1. So there is no "Ubuntu GNOME boot screen is displayed"
2. No opportunity to set the language
3. No opportunity to "Press "Try Ubuntu GNOME" and wait for the Live session to start"

We just go to the desktop. So, no pass is given even though everything seems to work fine.

Is what I see what is intended? If so can we get the test case updated.

Just fail it. Eventually  it  will be back up.

Regards..

---

### Post by jprzybytek on 2015-12-31
> **ventrical said:**
> Just fail it. Eventually  it  will be back up.

So I will assume that what I have been seeing is not what is intended (but it was a nice experience!) and I will fail it.

john

---

### Post by kansasnoob on 2015-12-31
Colin Watson said last night that he thought he might have it fixed:

[https://lists.ubuntu.com/archives/ubuntu-release/2015-December/003488.html](https://lists.ubuntu.com/archives/ubuntu-release/2015-December/003488.html)

But I haven't had time to check it out yet, not even sure if a 20151231 build has dropped yet.

---

### Post by ventrical on 2015-12-31
> **jprzybytek said:**
> So I will assume that what I have been seeing is not what is intended (but it was a nice experience!) and I will fail it.

john

Yes. But as you notice - kansasnoob says that there may be a fix already ... so we just keep on trying. Usually right about this time there is major breakage in many modules because of completely re-structuring or one component not entirely catching up with another.

 Reporting a 'fail' is not wasted time or testing. It chronicles  the testing of the  current development version and expands the knowledge base of 'fails' across various form factors. So a fail may be recorded on an older framework, not a newer one, yet a fix can be rendered to include the older hardware form factor without affecting the the current newer form factor.

Regards..

 and thank you for your testing efforts.

---

### Post by Doug S on 2016-01-02
Several people tried the fixed ISO yesterday, and all were O.K.
There are two bug reports, [here]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1525446") and [here]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1527353").
There is also another forums thread, [here]("http://ubuntuforums.org/showthread.php?t=2306703").

---

