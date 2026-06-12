---
title: "Problems with ubuntuzilla and eclipse SWT (&quot;no more handles&quot;)"
date: 2008-06-21
forum: Ubuntuzilla
---

### Post by OregonPete on 2008-06-21
Just thought I'd add this in case anyone else has an unofficial firefox release (outside of the normal Ubuntu distribution) installed -- such as the one installed using ubuntuzilla -- and is getting the "no more handles" error when working with eclipse.

The problem occurs if the link from eclipse to the official ubuntu firefox installation (the one in the official ubuntu distribution) is somehow broken and is now pointing to the ubuntuzilla firefox release. 

I fixed the problem by changing the eclipse script (on my system it's in in /home/user_name/bin) and pointing LD_LIBRARY_PATH and MOZILLA_FIVE_HOME to the firefox library of the official distribution. In my installation it looked like this: 

```
#!/bin/sh
export LD_LIBRARY_PATH="/usr/lib/firefox/"
export MOZILLA_FIVE_HOME="/usr/lib/firefox/"
export ECLIPSE_HOME="$HOME/opt/eclipse"

$ECLIPSE_HOME/eclipse $*
```

The actual problem is that the SWT browser in eclipse needs a firefox version that is compiled with linkable Gecko libraries, and the firefox downloads from Mozilla.org don't fulfill that criteria. If you'd like more information on the problem and how to solve it, here's a valuable link:

_[http://www.eclipse.org/swt/faq.php#browserlinux](http://www.eclipse.org/swt/faq.php#browserlinux)_

Hope I could help someone with this info...

---

### Post by nanotube on 2008-06-21
thanks for posting this info! i'm sure it will come in very handy to a few people down the road. :)

---

