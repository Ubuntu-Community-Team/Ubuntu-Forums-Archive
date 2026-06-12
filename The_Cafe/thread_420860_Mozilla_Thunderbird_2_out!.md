---
title: "Mozilla Thunderbird 2 out!"
date: 2007-04-24
forum: The Cafe
---

### Post by ZeroWing on 2007-04-24
[color=red]_[Clicky. ](http://www.mozilla.com/en-US/thunderbird/)[/color]_

 Someone needs to make a howto, quick!

---

### Post by slimdog360 on 2007-04-24
how to install thunderbird.

step 1) open folder
step2 ) click 'thunderbird'

---

### Post by Spyrious on 2007-04-24
I click on thunderbird but nothing happens.
Sorry because im new to linux.

---

### Post by aysiu on 2007-04-24
Here's a HowTo:
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

---

### Post by mykalreborn on 2007-04-24
i'm still waiting for thunderbird 2 to be put in the repos. i've downloaded and used 2.0, but it didn't have a settings and email importer from other thunderbirds. i sopose it will be in the repos pretty soon, right? :D

---

### Post by aysiu on 2007-04-24
> **mykalreborn said:**
> i'm still waiting for thunderbird 2 to be put in the repos. i've downloaded and used 2.0, but it didn't have a settings and email importer from other thunderbirds. i sopose it will be in the repos pretty soon, right? :D
That's an easy fix!

Just close Thunderbird and paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
mv ~/.thunderbird ~/.thunderbird.whoops
ln -s ~/.mozilla-thunderbird ~/.thunderbird
``` Then restart Thunderbird 2.0 again. It should have all your old settings and emails.

The problem is that the Ubuntu Thunderbird stores your profile in the /home/mykalreborn/.mozilla-thunderbird folder, but the Mozilla Thunderbrd stores it in the /home/mykalreborn/.thunderbird folder.

---

### Post by Spyrious on 2007-04-24
> **aysiu said:**
> Here's a HowTo:
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

Thanks

---

### Post by mykalreborn on 2007-04-25
thanks aysiu, i think i'll do just that. :D

---

