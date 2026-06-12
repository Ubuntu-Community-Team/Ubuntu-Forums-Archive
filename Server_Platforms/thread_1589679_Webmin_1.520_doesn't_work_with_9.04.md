---
title: "Webmin 1.520 doesn't work with 9.04"
date: 2010-10-06
forum: Server Platforms
---

### Post by 1serveyou on 2010-10-06
I just wanted to give everyone a heads up, that when I upgrade to the newest Webmin(1.520) didn't work. I forget its exact errors as it was a week or so ago, but when I switched back to 1.510, it worked fine.

My other server running 10.04 runs 1.520 fine though.

Hope I've saved at least 1 person from the frustration that I went through.:)

---

### Post by lisati on 2010-10-06
Your experience seems to reflect mine. My server was previously 9.04, and I ran into problems after upgrading webmin to the latest version. Before I upgraded my server to 9.10 I reverted to an older version of webmin.

---

### Post by CharlesA on 2010-10-06
Haven't tried installing that version on 9.04, but did you install it after adding the repo?

It would be helpful to know what the error message was.

---

### Post by arrrghhh on 2010-10-07
> **CharlesA said:**
> Haven't tried installing that version on 9.04, but did you install it after adding the repo?

It would be helpful to know what the error message was.

Wasn't it removed from the repo's?

Were you trying to install the deb from the site?  I'm not running 9.04, I'm on 10.04... and this version of Webmin is running just fine for me :D

FYI, got the .deb from their website.

---

### Post by CharlesA on 2010-10-07
> **arrrghhh said:**
> Wasn't it removed from the repo's?

Were you trying to install the deb from the site?  I'm not running 9.04, I'm on 10.04... and this version of Webmin is running just fine for me :D

FYI, got the .deb from their website.

I don't think it's in the Ubuntu repos, but you can add the Webmin repos to yer sources.list and grab it from there.

I ran 1.510 on Lucid without any problems (before I decided to not bother with it, since it was unneeded).

---

### Post by arrrghhh on 2010-10-07
> **CharlesA said:**
> I don't think it's in the Ubuntu repos, but you can add the Webmin repos to yer sources.list and grab it from there.

I ran 1.510 on Lucid without any problems (before I decided to not bother with it, since it was unneeded).

Yea, I like taking a peek at it for SMART stats, and mucking with samba whenever I have too.

I wish there was some spiffy lookin plugin or tool that would show me hard disk utilization like that gnome app does...

---

