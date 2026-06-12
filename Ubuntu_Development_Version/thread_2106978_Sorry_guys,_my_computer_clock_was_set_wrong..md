---
title: "Sorry guys, my computer clock was set wrong."
date: 2013-01-20
forum: Ubuntu Development Version
---

### Post by kevpan815 on 2013-01-20
It was all due to the fact that Windows 8 sets the BIOS to Real Time and Ubuntu sets the BIOS to UTC! I did NOT even notice that I had NOT reset the Time after booting back into Windows 8 again!

---

### Post by seeker5528 on 2013-01-20
> **kevpan815 said:**
> It was all due to the fact that Windows 8 sets the BIOS to Real Time and Ubuntu sets the BIOS to UTC

If you need it '/etc/default/rcS' is where that setting is kept.

'gksudo some-text-editor /etc/default/rcS' or 'kdesudo some-text-editor /etc/default/rcS'

some-text-editor being gedit, kate, vim, nano, etc...

change 'UTC=yes' to 'UTC=no'.

Later, Seeker

---

### Post by kevpan815 on 2013-01-20
Thanks, but now that I figured out that my Ubuntu Nightly Build Crashing Problem was due to my Second Monitor being Plugged In, I won't need to return to Windows 8 until Next Month's Security Updates are Available on the Second Tuesday of the Month, and/or when I do my Taxes on HRBlock.com (which still says Ubuntu is an Unsupported Operating System).

---

### Post by cariboo on 2013-01-20
Welcome back seeker5528.

---

### Post by jfernyhough on 2013-01-20
> **kevpan815 said:**
> (which still says Ubuntu is an Unsupported Operating System).

Have you tried
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)
?

---

### Post by kevpan815 on 2013-01-21
No I have not tried that Add-on that you mentioned, and even if I did try it, I still need Apple ITunes in Windows 8 to Update my Sprint Wireless Apple IPhone 5 to the IOS Beta Builds I get from the Apple Developer Program (Also known as ADC).

---

