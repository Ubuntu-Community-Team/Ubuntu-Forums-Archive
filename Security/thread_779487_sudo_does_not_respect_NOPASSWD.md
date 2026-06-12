---
title: "sudo does not respect NOPASSWD"
date: 2008-05-02
forum: Security
---

### Post by Schizoid on 2008-05-02
when adding to /etc/sudouser 

username ALL=(ALL) NOPASSWD: ALL

username being my actual user name . I'm still prompted per session for my password

I know what this line does, and I'm know what I'm doing and have used this 1000 of times on my linux systems.

I'm wondering why this does not work in ubuntu?

---

### Post by aysiu on 2008-05-02
Did you add the line to the end of your /etc/sudoers file or to the middle/beginning?

---

### Post by Schizoid on 2008-05-02
at the beginning. but moving it to bottom does not have an effect.

---

### Post by kerry_s on 2008-05-02
> **Schizoid said:**
> when adding to /etc/sudouser 

username ALL=(ALL) NOPASSWD: ALL

username being my actual user name . I'm still prompted per session for my password

I know what this line does, and I'm know what I'm doing and have used this 1000 of times on my linux systems.

I'm wondering why this does not work in ubuntu?

that's very unsafe, you should make it application specific.

mine->

---

### Post by aysiu on 2008-05-02
> **Schizoid said:**
> at the beginning. but moving it to bottom does not have an effect.
That's weird. [This thread](http://ubuntuforums.org/showthread.php?t=135160) would seem to indicate that positioning matters.

I've never heard of the /etc/sudouser file. Have you tried editing /etc/sudoers instead?

---

### Post by kerry_s on 2008-05-02
also make sure your editing with->
**sudo visudo**

or you will corrupt it and sudo won't work anymore.

if you have to have something more gui-> sudo xedit /etc/sudoers <-will work, but won't tell you if you made a mistake. to save in xedit click save 2x.

---

### Post by |{urse on 2008-05-02
holy deja vu

---

### Post by Schizoid on 2008-05-02
my mistake I meant /etc/sudoers

regardless I've never had an issue with position. and moving position still does not resolve the issue.

---

### Post by Schizoid on 2008-05-02
> **kerry_s said:**
> also make sure your editing with->
**sudo visudo**

or you will corrupt it and sudo won't work anymore.

if you have to have something more gui-> sudo xedit /etc/sudoers <-will work, but won't tell you if you made a mistake. to save in xedit click save 2x.

of course I'm using visudo

---

### Post by Dr Small on 2008-05-02
Hmm, well, what does this do?
```
user host = NOPASSWD: ALL
```

---

### Post by lemming465 on 2008-05-02
Hmm.  Not sure why it isn't working for you; I just tried it on my hardy box and it worked fine.  I also notice:```
# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

```

At which point I'd be strongly tempted to try```
sudo usermod -G sudo -a $USER
sudo perl -pi -e 's/^# // if /%sudo/;' /etc/sudoers
```

---

### Post by Schizoid on 2008-05-02
ok I finally figured this out. turns out I didn't add myself to the last line like someone suggested. I thought i did but I must have not tested right. "kinda busy with other work also"

so it turns out the real issue is %admin ALL=(ALL) ALL overides all NOPASSWD statements since the default install user is added 
to admin. if you added a new regular user this wouldn't be the case. 

and if you actually uncommented  #%sudo ALL=NOPASSWD: ALL and add your username to the  sudo group . Odds are it wont work since %admin would override it . so you would have to move it to the last line also. see [https://answers.launchpad.net/ubuntu/+question/31811](https://answers.launchpad.net/ubuntu/+question/31811)

anyways, thanks for the help everyone

---

