---
title: "Advice on testing Alpha/Betas' in VBox or by Dual-booting? Does it matter which?"
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mikodo on 2012-03-02
Hi,

An easy question, I'm sure.

I want to learn to file good bug reports, because I suck at it now, but it will just take doing the learning. :>)

I have read that some people prefer dual-booting, when trying newer releases, because it easier to discern, if the problem is from the release and not possibly a virtual problem.

I like the idea of testing something until I break it, alpha/beta releases, apps... whatever, filing a bug-report, then reverting back to an earlier state in the .vdi, before I broke it.

So, does it really make a difference, on the outcome of good bug-reporting, if it is from an "on metal install" or virtual?

Thanks.

---

### Post by grahammechanical on 2012-03-02
I would say dual boot if you want to take testing beyond just trying it out. And if you want to share in this:

[http://www.theorangenotebook.com/2012/03/opportunity-manual-application-testing.html]("http://www.theorangenotebook.com/2012/03/opportunity-manual-application-testing.html")

How to file a bug report? Watch the video

[http://www.omgubuntu.co.uk/2012/02/how-to-file-a-bug-in-ubuntu/]("http://www.omgubuntu.co.uk/2012/02/how-to-file-a-bug-in-ubuntu/")

All help is appreciated. Also note that there is on this forum a section called Ubuntu+1 (Precise Pangolin). A few days after 12.04 is offically released that section will become Ubuntu+1 (Whatever 12.10 is called).

One more thing. The handling of crashes is now much improved. There is a program called Apport that detects when something closes unexpectedly and as well as notifying you, it will collected data and make the connection to Launchpad to report the bug if you so choose.

Sometimes the bug has already been reported. Apport will tell you that and you can add your experience to the existing report.

Sometimes the crash is due to obsolete packages and it cannot be reported. When that happens it is due to some packages being upgraded and others held back because they are not ready. This is usually fixed by doing daily updates.

Regards.

---

### Post by mikodo on 2012-03-02
grahammechanical:

I am aware of Apport, and have used it but, I don't know that much about it. 

I am glad I asked, and I am appreciative of your reply, with the information and links. 

OK, dual-booting it is! (I probably would have used VBox, had I not asked). 

Thanks.

---

### Post by mikodo on 2012-03-02
And, from post number 3 [here]("http://www.theorangenotebook.com/2012/03/opportunity-manual-application-testing.html"):

[I]checkbox currently requires  physical hardware to work properly -- so it won't work in VM's right  now. I would suggest simply using the livecd as a workaround for now.  Hopefully we'll be able to make this work in VM's as well. Thanks for  testing!
[/I] 
That explains, your answer.

Thanks

---

### Post by bodhi.zazen on 2012-03-02
I use VM for testing, KVM or Virtualbox. They have the advantage of being disposable if something breaks and can be used for testing and development.

The disadvantage is that it is not running on your actual hardware, so can not be used for testing hardware.

So , although the two are intertwined ...

Software testing (Development) -> VM

Hardware testing (Testing nvidia card, wireless, etc) -> Install onto a partition.

---

### Post by mikodo on 2012-03-03
Thank you, bodhi.zazen.

Your post, clarifies it even more.

:>)

---

