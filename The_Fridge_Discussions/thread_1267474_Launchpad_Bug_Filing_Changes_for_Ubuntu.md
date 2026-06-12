---
title: "Launchpad Bug Filing Changes for Ubuntu"
date: 2009-09-15
forum: The Fridge Discussions
---

### Post by TheFridge on 2009-09-15
As a part of the [Increase Apport Adoption specification]("https://wiki.ubuntu.com/QATeam/Specs/IncreaseApportAdoption") we are going
to kick off an experiment and redirect all of Ubuntu&#8217;s /+filebug links
in Launchpad to [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs). This
change has been tested on [staging.launchpad.net]("http://ubuntuforums.org/staging.launchpad.net") already and will be
landing shortly on [edge.launchpad.net]("http://ubuntuforums.org/edge.launchpad.net") (There will be a +filebug?no-redirect if you really really need it).

 If you review the specification and the documentation bug reporters will
be redirected to, you will notice that we spent a lot of time and energy
on ensuring that we improve the quality of bugs when they are reported.
The time many of us spend on triaging very incomplete bugs is not
sustainable given the volume of bug reports. Having reporters use
ubuntu-bug (apport more specifically) to report bugs will reduce many of
these problems for us.

 In order to make the transition for our users smoother, we&#8217;d like to ask
you to help out with a few things:

 1) If you take care of a high-profile package, consider adding it to
[https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage) which is linked to from
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs).

 2) Please consider writing an apport hook for the packages you take care
of, if you need special information in bug reports - it&#8217;s REALLY easy:
[https://wiki.ubuntu.com/Apport/DeveloperHowTo#Package%20Hooks](https://wiki.ubuntu.com/Apport/DeveloperHowTo#Package%20Hooks)

 3) If the area of Ubuntu that you take care of is better suited by
symptom based bug reporting (&#8220;storage&#8221;, &#8220;boot&#8221;, &#8220;install&#8221;, &#8220;sound&#8221;,
etc.), consider contributing to the apport-symptoms package - it too is
REALLY easy:
[https://wiki.ubuntu.com/Apport/DeveloperHowTo#Symptoms](https://wiki.ubuntu.com/Apport/DeveloperHowTo#Symptoms)

 By helping us receive higher quality bug reports, we will help to help
make Ubuntu even better!

 Originally sent to the ubuntu-devel-announce mailing list by Brian Murray on Tue, Sep 15, 2009 at 5:53 PM

 

[More...](http://fridge.ubuntu.com/node/1908)

---

### Post by overcast on 2009-09-18
As per mailing list announcement from matthew, new version of Lauchpad i.e 3.0 will be out soon.

---

### Post by blakamin on 2009-09-26
Just a thought, but you might want to make the screenshots on [https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs") all be in english so people have a bit of an idea where to find these options quickly.
F'rinstance, I saw a link to that page in another thread, had a quick look and thought "this must be the wrong link", and went back to my browsing without even reading it.

---

