---
title: "expect goes too quick"
date: 2012-01-03
forum: Server Platforms
---

### Post by ask21900 on 2012-01-03
I have a bash script that mounts a filesystem with password using expect as shown here:

```

spawn -ignore HUP /usr/bin/sshfs <filesystem> <mountpoint>
expect "assword:"
send "blahblahblah"
expect eof

```

First, I understand the many issues with doing this (security, etc), but it is absolutely necessary for certain reasons.

This script used to work perfect every time, but about a month ago stopped working about 90% of the time.  When I run the script manually, I can see that it is sending the password about 1-2 seconds before the password prompt.

Does anyone have an idea as to why the expect would not wait until getting that queue before sending?  Thanks in advance!

---

### Post by HermanAB on 2012-01-04
It means that the 'assword:' prompt is already in the expect input buffer, so it reacts to old data instead of waiting for the new data.  Try flushing the input buffer at the start of the script (can't remember how, sorry!).

---

### Post by ask21900 on 2012-01-07
I have tried clearing the buffer by using both
```
expect -re ".*"
``` and ```
expect -re $
```

I have also set the timeout as recommended by several posts I came across when looking for how to clear the buffer.

Now the script is acting as if I am using the wrong passwd.  Immediately after displaying the passwd prompt (about the time the send would run), a second passwd prompt is displayed.  Since this script occasionally still works I am confident that the password is correct, but I have verified just in case.

Any other ideas would be greatly appreciated!!

---

### Post by HermanAB on 2012-01-07
Soooo, you also have gunk in the output buffer?  But goodness knows how to clear that without actually sending it and handling the resultant error. Hmm, 10 backspaces as the first characters of the password maybe?

Anyhow, a robust script must handle errors and retries.

---

### Post by kevinthecomputerguy on 2012-01-08
does adding a ping help slow it down

like 

ping -c 30 127.0.0.1

That would wait about 30 seconds without much effort, and would let you know if the local nic is up.

---

