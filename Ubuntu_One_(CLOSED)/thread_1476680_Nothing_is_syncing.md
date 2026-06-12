---
title: "Nothing is syncing"
date: 2010-05-08
forum: Ubuntu One (CLOSED)
---

### Post by chemicalrubber on 2010-05-08
I have set up an account and added my Linux machine. After right-clicking on a document folder and selecting Synchronize with Ubuntu One, nothing happens. Nothing is uploaded into the cloud, and the only way to do it is use the one.ubuntu.com website. What is happening?

---

### Post by byStanderone on 2010-05-08
...read that ubuntu.one is currently under an upgrade or fixing, and will be back on the go after that.

---

### Post by duanedesign on 2010-05-08
The service is slower than it should be. The U1 team is working hard to cope with the increase in users from the Lucid release.It should be uploading, its just not as fast as it normally is. To check what the service is doing you can run the following command and post the results here:

```
u1sdtool -s
```

if is_connected: and is_online: is FALSE try running the following, waiting a minute and running the above commmand again.

```
u1sdtool -q; u1sdtool -c
```

Also I like to run the following in a Terminal if I want to monitor the upload.

```
tail -fn 50 ~/.cache/ubuntuone/log/syncdaemon.log

```

---

### Post by Pifilatakanemu on 2010-05-09
Just in case that you have an urgent need for a cloude storage service and can't wait until U1 handles the problems.
There is still [Dropbox]("https://www.dropbox.com/referrals/NTIwODg2NjM5"), which, IMHO, is a nice alternative.

It works cross plattform and offers more free space and more speed. Just to bridge until U1 works how it should.

---

