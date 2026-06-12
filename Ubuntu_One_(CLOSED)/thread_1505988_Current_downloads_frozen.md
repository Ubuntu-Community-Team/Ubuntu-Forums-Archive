---
title: "Current downloads frozen"
date: 2010-06-09
forum: Ubuntu One (CLOSED)
---

### Post by Dave Smith on 2010-06-09
When I use the command *'u1sdtool --current-transfers'* in a terminal I have three files that are partially downloaded and now apparently frozen. They have been like this for several days and seem to be stopping the *metadata list* from processing on this particular computer.

The files concerned have now been deleted from their original computer but are still freezing one of the computers in the account.

Is there a way of refreshing the download process or clearing this in some way?

Thanks.

---

### Post by duanedesign on 2010-06-10
try and restart all the u1 processes.

```
killall ubuntuone-preferences; killall ubuntuone-login; u1sdtool -q; u1sdtool -c
```

Then you can monitor if there is any progress with the commands

```
u1sdtool --waiting-metadata | wc -l
```

```
u1sdtool --waiting-content | wc -l
```

the numbers returned by those commands should get smaller overtime.

After U1 has ran for a few minutes try this command, it returns status of the syncdaemon, and post what it returns:

```
u1sdtool -s
```

-
--

---

### Post by Dave Smith on 2010-06-10
Yes, that has done the trick - thanks.

In fact, I was able to do this using '*Restart*' from the preferences GUI.

---

