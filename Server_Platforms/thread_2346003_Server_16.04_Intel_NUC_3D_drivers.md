---
title: "Server 16.04 Intel NUC 3D drivers"
date: 2016-12-10
forum: Server Platforms
---

### Post by WPtE on 2016-12-10
Hi,

I'd like to get 3D acceleration working on my Ubuntu server 16.04 installation for usage in virtualbox.
I tried to test if I had a working gpu by using heaven benchmark through xpra, I only got about 0.5fps and a very high cpu load.
Then I read about the intel graphics driver utility, I installed that and used it to update the gpu drivers with this as a result:
[ATTACH=CONFIG]272648[/ATTACH]

I tried the heaven benchmark again through xpra, and received 10fps easily, which is ok since the gpu in my Intel NUC isn't that powerful.

Now, a few months later I've installed virtualbox headless and received the message that it couldn't do 3D acceleration because there's no 3D support on the host.
I'm not really sure what to do now to asses the issue.
Does someone have experience with this? :)

---

