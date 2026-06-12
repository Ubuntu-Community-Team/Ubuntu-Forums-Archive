---
title: "How can I programmatically find a value of current DISPLAY for a session?"
date: 2023-06-27
forum: Ubuntu Application Development
---

### Post by and-account on 2023-06-27
I'm looking at [https://github.com/canonical/ubuntu-desktop-installer/blob/7957431cabbf304474be602dc6a37b98ff61561f/packages/ubuntu_desktop_installer/snap/local/subiquity-server#L22](https://github.com/canonical/ubuntu-desktop-installer/blob/7957431cabbf304474be602dc6a37b98ff61561f/packages/ubuntu_desktop_installer/snap/local/subiquity-server#L22)

I see:
```
export DISPLAY=:0

```

Is there a way to do the same, but programmaticaly find out in a shell script how many there are displays and what are the numbers. For example, it is not ":0" just now, it's ":10.0". Hard-code do not fit.

How do I know what are available current values for DISPLAY for a session?

thx!

---

### Post by TheFu on 2023-06-27
```
echo $DISPLAY
```

The DISPLAY usually is set automatically these days and if you use **ssh -X** it will be for you.  If you are doing a remote desktop, then it is up to you to understand which values are correct and should be used. Check the remote desktop documentation for how they handle it .... or better .... use a better remote desktop solution which just handles it better.  The NX-based solutions like x2go do this AND they are more secure AND they are faster.

It is just and environment variable and can be accessed or modified however you like. Of course, if you modify it incorrectly, no GUI will work.

---

