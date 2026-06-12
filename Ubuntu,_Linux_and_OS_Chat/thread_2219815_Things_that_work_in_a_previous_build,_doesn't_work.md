---
title: "Things that work in a previous build, doesn't work in the new one!"
date: 2014-04-25
forum: Ubuntu, Linux and OS Chat
---

### Post by CDR Services on 2014-04-25
I have 3 machines that I generally run Ubuntu on, a Samsung QX410 laptop with an I5, and an ASUS x200E small laptop with an I3. as well I have a Dell Studio 1909 all in one with a Pentium q8500.  I have run all 3 machines on ver 12.04 through to 14.04 and in general they all "Mostly" work fine! there are always certain exceptions for example 12.04 didn't support the touch screen or the lan port on the Asus but 12.10 the touch screen worked but the lan did not. These things I understand as newer releases support newer hardware, but I always find it odd something that works just fine in an earlier build ends up broken in the later one, for example with 13.04 through 14.04 on both laptops with logitech wireless mice. With the usb module plugged in the mouse doesn't respond until I unplug it and plug it back in! It works the same way with 3 different logitech mice i own! The easy solution switch to another brand of mouse, but why!

---

### Post by matt_fussell2 on 2014-04-25
It's always a bit of a game with hardware manufacturers - on the software side of things, it's quite easy to get hosed if a new firmware update gets pushed by hardware and then they drag their feet indefinitely getting the necessary code to the software side. There's also the conversation of who may have paid off whom in the meantime, but that ends up being hearsay.

---

### Post by cariboo on 2014-04-25
There are changes in the kernel that may affect some of your hardware, I'd suggest that you [create bug reports ]("https://help.ubuntu.com/community/ReportingBugs")for  the hardware you are having a problem with, in most cases you would use the following command:

```
ubuntu-bug <package-name>
```

In the above command substitute linux for <package-name>, you should be willing to do everything the developer that is looking after the problem asks you to.

For example in 13.10 my D-Link nic stopped working, after submitting a good bug report, a developer posted in the bug report asking me to try the mainline kernel, after determining that the problem was still in the vanilla kernel, he asked me to do a [git bisect]("http://webchick.net/node/99"), using that procedure we determined that there was a commit change in the kernel concerning my network adapter, he came up with a solution, and submitted it to to the kernel, and within a week my problem was solved.

---

