---
title: "How do I report this sort of bug?"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mcellius on 2012-03-05
How do I report a bug that does not involve a crash?  For example, I  install a program called ... oh, let's call it Brainfreeze.  After  installing it, I open the Dash, find the icon, and try to run it.   Either it just doesn't do anything at all, or it opens and then just  doesn't work.  No crashes, no errors, just nothing.  Clearly it isn't going to get me anywhere, so I uninstall it.

Or I've installed a theme that doesn't look right (washed out fonts,  whatever), but there is no crash and it actually does install.  Yet it's not right.  But it's  not a program.

Now, how would I report that?  Apport doesn't seem to work unless it finds the program installed, but by now I've removed it.

---

### Post by Script Warlock on 2012-03-05
> **mcellius said:**
> How do I report a bug that does not involve a crash?  For example, I  install a program called ... oh, let's call it Brainfreeze.  After  installing it, I open the Dash, find the icon, and try to run it.   Either it just doesn't do anything at all, or it opens and then just  doesn't work.  No crashes, no errors, just nothing.  Clearly it isn't going to get me anywhere, so I uninstall it.

Or I've installed a theme that doesn't look right (washed out fonts,  whatever), but there is no crash and it actually does install.  Yet it's not right.  But it's  not a program.

Now, how would I report that?  Apport doesn't seem to work unless it finds the program installed, but by now I've removed it. try to launch the app and find the pid and type apport-bug (pid) or (app).

---

### Post by mcellius on 2012-03-06
> try to launch the app and find the pid and type apport-bug (pid) or (app).

In some of these cases I already deleted the app and I'd rather not install it again.  And in the case of themes that don't work properly, there is no pid or app to report.

---

### Post by Script Warlock on 2012-03-06
> **mcellius said:**
> In some of these cases I already deleted the app and I'd rather not install it again.  And in the case of themes that don't work properly, there is no pid or app to report. heres [how]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by mcellius on 2012-03-06
> heres [how]("https://help.ubuntu.com/community/ReportingBugs")

So it appears there is no way, because the instructions on that page require the use of apport.  For a theme that doesn't work with 12.04, there is no information that apport can gather because there is no running program (that I know of) or PID.  And in the case of apps that just won't install, there is no way, either.
[]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by Script Warlock on 2012-03-06
some methods i know on reporting a bug:
- using the help menu > "report a problem" on some apps
- [this]("https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect") one
- and here #ubuntu-bugs
- or [here]("http://www.ubuntu.com/community/report-problem")

---

### Post by cariboo on 2012-03-06
> **mcellius said:**
> So it appears there is no way, because the instructions on that page require the use of apport.  For a theme that doesn't work with 12.04, there is no information that apport can gather because there is no running program (that I know of) or PID.  And in the case of apps that just won't install, there is no way, either.
[]("https://help.ubuntu.com/community/ReportingBugs")

You can create a bug report against a package, for example you can create a bug report against openssh-server using the following command:

```
ubuntu-bug openssh-server
```

or

```
apport-bug openssh-server
```

the above method will work, but you should have the package installed to give the developers the maximum amount of information.

---

### Post by mcellius on 2012-03-06
> some methods i know on reporting a bug:
- using the help menu > "report a problem" on some apps
- [this]("https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect") one
- and here #ubuntu-bugs
- or [here]("http://www.ubuntu.com/community/report-problem")

The "_this_ one" is what I was looking for!  Thanks!  I had several such "bugs" I couldn't report, but using that link I was able to do so.
[]("http://www.ubuntu.com/community/report-problem")

---

