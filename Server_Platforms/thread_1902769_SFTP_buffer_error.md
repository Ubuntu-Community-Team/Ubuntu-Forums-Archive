---
title: "SFTP buffer error"
date: 2011-12-31
forum: Server Platforms
---

### Post by Mykle87 on 2011-12-31
I am having an issue with my Ubuntu 10.04.3 server. There are several files that when I download them using Filezilla over SFTP, I receive the following error message:

```
error while reading: received a short buffer from FXP_READ, but not at EOF
```

I'm guessing that maybe some of the files are corrupt? Has anyone else experienced this issue? Thanks.

---

### Post by rsvancara on 2012-01-01
I have not seen this issue.  However, it would be interesting as an experiment to try using sftp from the command line to copy your files and see if you get the same error.

---

### Post by Mykle87 on 2012-01-02
The same files stall when I download using the SFTP command from a livecd. I dropped the mtu according to this thread [http://ubuntuforums.org/showthread.php?t=805863](http://ubuntuforums.org/showthread.php?t=805863) but I'm still having the same issues. Any suggestions are appreciated.

---

### Post by CharlesA on 2012-01-02
Do other files transfer fine?

Sounds like they are corrupted to me.

---

### Post by Mykle87 on 2012-01-02
Yeah you're are probably right. One of the files stalled but eventually finished downloading and it worked perfectly fine. Maybe some of the data is fragmented?

---

### Post by CharlesA on 2012-01-02
Doubt fragmentation would throw that sort of error.

---

### Post by Mykle87 on 2012-01-02
Ok thanks for the info. Since I don't get an error with every file, I should be fine.

---

### Post by CharlesA on 2012-01-02
Yep.

I quick google didn't really turn up much info as to what causes the error either.

---

