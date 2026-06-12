---
title: "FireStarter - 50+ hits in 5 min, all on port 56378"
date: 2009-07-06
forum: Security
---

### Post by whole.grains on 2009-07-06
I have no idea what's happening. I just finished installing Windows 7 R.C., booted back in to Ubuntu, FireStarter launched and went nuts. Ideas?

---

### Post by XanTrax on 2009-07-06
> **whole.grains said:**
> I have no idea what's happening. I just finished installing Windows 7 R.C., booted back in to Ubuntu, FireStarter launched and went nuts. Ideas?

Execute this command at a console:

```

sudo netstat -tnap

```

This will show you all connections on a TCP connection and show the program that is using it.  Likewise, you could do:

```

sudo netstat -tnap | grep -i 56378

```

To maybe make it a bit easier to read.  Feel free to post the output here if you want me to take a closer look at it.

---

### Post by lovinglinux on 2009-07-06
Have you been using a torrent client recently?

Possible explanation:

[http://ubuntuforums.org/showpost.php?p=7391948&postcount=3](http://ubuntuforums.org/showpost.php?p=7391948&postcount=3)
[http://ubuntuforums.org/showpost.php?p=7505977&postcount=3](http://ubuntuforums.org/showpost.php?p=7505977&postcount=3)

---

### Post by whole.grains on 2009-07-07
Thank you both for the replies. About an hour after I posted this I rebooted and everything was back to normal. I had not been using a torrent client, and my cable modem has been connected for a while so I don't think I got some IP that was just being used for P2P. Either way I've got some cool new terminal commands to try out if it happens again.

Is there no way to mark threads as solved now?

Thanks!

---

### Post by lovinglinux on 2009-07-07
> **whole.grains said:**
> Thank you both for the replies. About an hour after I posted this I rebooted and everything was back to normal. I had not been using a torrent client, and my cable modem has been connected for a while so I don't think I got some IP that was just being used for P2P. Either way I've got some cool new terminal commands to try out if it happens again.

Is there no way to mark threads as solved now?

Thanks!

Put a [SOLVED] in front of the title or add **solved** to the thread tags.

---

