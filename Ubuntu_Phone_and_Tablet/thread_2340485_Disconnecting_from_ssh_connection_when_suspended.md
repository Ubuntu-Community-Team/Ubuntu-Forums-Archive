---
title: "Disconnecting from ssh connection when suspended"
date: 2016-10-19
forum: Ubuntu Phone and Tablet
---

### Post by wgarcia on 2016-10-19
I'm connecting to a server using ssh from the terminal app, but when the phone suspends the connection is dropped. Is there any way to avoid this to happen?

---

### Post by howefield on 2016-10-19
Not sure if this would help, but you could try running the ssh session with screen.

---

### Post by wgarcia on 2016-10-19
I can try, but I think some services like GPS just drop when the device is suspended. The network I think should still be running in suspended mode in a phone, and I think that is the case.

---

### Post by howefield on 2016-10-20
> **wgarcia said:**
> I can try, but I think some services like GPS just drop when the device is suspended. The network I think should still be running in suspended mode in a phone, and I think that is the case.

If that is the case try the simple 

```
fg
```

which might bring the session back to the foreground, hopefully without a broken pipe :)

---

### Post by wgarcia on 2016-10-20
Yes, I tried it, but just does not restore the ssh session. It looks like it is still running in the background, but the "phablet" shell prompt is shown and nothing comes up.

---

### Post by wgarcia on 2017-01-03
I found a solution for this. Get into the shell of the phone (with adb sheel or ssh) and give this command:

```
gsettings set com.canonical.qtmir lifecycle-exempt-appids "['com.ubuntu.terminal']"
```

---

