---
title: "ubiquity hangs when trying to install mythubuntu from live session"
date: 2014-03-29
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-03-29
As stated above, I can still work the live session but Ubiquity will not come up from live session so as one can install to disk. I marked my live test at q&a tracker as a pass for the live but forgot to do this test - so it is a fail.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1299473](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1299473)

---

### Post by sudodus on 2014-03-29
- Could it be a problem with too little memory? How much RAM is there in the computer?
- Did you try in another computer with more memory?
- Does it work to start the installer directly from the syslinux menu?

---

### Post by ventrical on 2014-03-29
> **sudodus said:**
> - Could it be a problem with too little memory? How much RAM is there in the computer?
- Did you try in another computer with more memory?
- Does it work to start the installer directly from the syslinux menu?

2GB Core 2 Duo 3.00GHz

  Iv'e seen this happen before in Ubuntu cycles from OO .. So I just use "install ubuntu" from Ubiquity.

 Perhaps you can  give your opinion here:

[http://ubuntuforums.org/showthread.php?t=2213619&page=2&p=12971434#post12971434](http://ubuntuforums.org/showthread.php?t=2213619&page=2&p=12971434#post12971434)

The q&a tracker is a little bit vauge.  It does say machine ip but does not specify internal or external ip but I am assuming  it is internal.

*note*

have not tried syslinux menu as of yet.

---

### Post by Elfy on 2014-03-29
> The q&a tracker is a little bit vauge. [https://bugs.launchpad.net/ubuntu-manual-tests/+filebug](https://bugs.launchpad.net/ubuntu-manual-tests/+filebug) add a bug - make sure to note the testcase number, it'll get looked at. I know that for fact, it's often me doing the looking.

---

### Post by ventrical on 2014-03-29
> **Elfy said:**
> [https://bugs.launchpad.net/ubuntu-manual-tests/+filebug](https://bugs.launchpad.net/ubuntu-manual-tests/+filebug) add a bug - make sure to note the testcase number,

Yes .. thank you. I did leave a report on that above but since I was locked out I had to use another bug to leave my description report on that bug, However I can now refer to the 'testcase number'. One more thing while I am here .. it is hard to report a bug when your system is locked up (lol) and when trying to make a description report of behaviour of bug it will not accept submit unless you enter a bug number !! This doesn't make any sense to me at all but I will keep looking into the literature on the matter. Perhaps I have missed something .

---

### Post by ventrical on 2014-03-29
@elfy

Here is another example.

[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1299496](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1299496)

So I left the  testcase number in the description in the tracker session which I failed.

---

### Post by ventrical on 2014-03-31
> **sudodus said:**
> - Could it be a problem with too little memory? How much RAM is there in the computer?
- Did you try in another computer with more memory?
- Does it work to start the installer directly from the syslinux menu?


Tried it on another machine . Same fail.

---

### Post by sudodus on 2014-03-31
Then I think it is a bug.

My problem is that I don't know how to install front-ends and back-ends. I have no experience of mythbuntu and what is necessary for it to run. But Ubiquity should be independent of that(?)

If you need an 'affects me too' at Launchpad, what should I do? Would it be enough to download the mythbuntu iso file and try to install it into some computer?

---

### Post by ventrical on 2014-03-31
> **sudodus said:**
> Then I think it is a bug.

My problem is that I don't know how to install front-ends and back-ends. I have no experience of mythbuntu and what is necessary for it to run. But Ubiquity should be independent of that(?)

If you need an 'affects me too' at Launchpad, what should I do? Would it be enough to download the mythbuntu iso file and try to install it into some computer?


You can 'me too' this bug:


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1299473](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1299473)

and/or you can try the .iso, go live and then try to install by double clicking the 'install' icon on the live desktop. If  you get the 'spinner' then you can still go to terminal from GUI and then:

```

ubuntu-bug ubiquity

```

Thanks..

ps.. my bug reports incomplete.

---

### Post by sudodus on 2014-04-01
I clicked 'affects me too' after testing, and I was prompted into another bug report

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1300645](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1300645)

---

### Post by Elfy on 2014-04-01
I marked it as a dupe- I can't confirm - though I tried in a vm

---

### Post by ventrical on 2014-04-01
> **sudodus said:**
> I clicked 'affects me too' after testing, and I was prompted into another bug report

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1300645](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1300645)


 Thanks to the both of you. Also there are several other bugs in the testcase related to actually running the front end. The whole weird thing about this .iso is that xfce desktop runs so beautifully.. I just don't get it  :) lol, that xubuntu desktop doesn't run this way .. but thats another matter.

  Regards..

---

### Post by ventrical on 2014-04-03
> **Elfy said:**
> I marked it as a dupe- I can't confirm - though I tried in a vm


Ok... I got that confirmed through apport-collect 1299473  and marked it.

edit:

I did get a message that stated it was a kernel issue and  I just  seen that I collected info from the installed version and not the live .iso version :)lol

```

Looks like a kernel issue:

Mar 29 14:10:05 mythbuntu kernel: [ 66.096048] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
Mar 29 14:10:05 mythbuntu kernel: [ 66.096055] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
Mar 29 14:10:11 mythbuntu kernel: [ 72.108031] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
Mar 29 14:10:11 mythbuntu kernel: [ 72.108038] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
Mar 29 14:10:17 mythbuntu kernel: [ 78.120065] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
Mar 29 14:10:17 mythbuntu kernel: [ 78.120072] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED

-- 
You received this bug notification because you are subscribed to the bug
report.
```

---

### Post by ventrical on 2014-04-03
zsynced the daily and still ,the bug is there. Will not install from windows(xfce) desktop icon.

---

