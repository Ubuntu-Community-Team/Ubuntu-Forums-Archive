---
title: "Synaptic &amp; Mate &amp; vBox"
date: 2015-03-01
forum: Ubuntu Development Version
---

### Post by v3.xx on 2015-03-01
To reload package information in synaptic takes several minutes.

Apt-get update will do it in seconds.

Is anyone else seeing this?

Edit
Download rate in synaptic is less than 200 kB/s.

---

### Post by bapoumba on 2015-03-01
Sorry, not here but in VBox if that matters.

---

### Post by v3.xx on 2015-03-01
That did not occur to me.

<snip --no-bingo>

---

### Post by bapoumba on 2015-03-01
Bingo what ? :D
May be I was not clear, I'm running 15.04 in VBox and synaptic download rates are correct from what I can see elsewhere on my internet connection, above 900 kB/s.

---

### Post by v3.xx on 2015-03-01
Yes, I misread your post.

---

### Post by bapoumba on 2015-03-01
> **v3.xx said:**
> Yes, I misread your post.
Nah, I was not clear, sorry.

---

### Post by plucky on 2015-03-02
> **v3.xx said:**
> To reload package information in synaptic takes several minutes.

Apt-get update will do it in seconds.

Is anyone else seeing this?

Edit
Download rate in synaptic is less than 200 kB/s.

Are you running synaptic first and then apt-get?

Try running apt-get and then synaptic.

I have always found that if you download the index files and then try to download them again,apt-get/synaptic  is clever enough to realise the files are the same and will not down load all the index files again.This is my experience,not sure if correct.

Good Luck

---

### Post by v3.xx on 2015-03-02
Hi plucky

No I have not tried that.

The thing is my mate 14.04 (vBox) install does not have this problem, so I thought this could be a 15.04 bug.  But if I am the only one ..

---

### Post by jdeca57 on 2015-03-02
> **v3.xx said:**
> Hi plucky

No I have not tried that.



I did the apt-get update/upgrade and immediatly afterwards the software updater presented another 65 MB updates. So I'm a bit confused and my conclusion is that beta1 is what it says: some issues remain. By the way, is Firefox your default browser? Every time I start the program it complains about that.  ;-)

---

### Post by zika on 2015-03-02
> **jdeca57 said:**
> Every time I start the program it complains about that.  ;-)Tell him not to check that and it will not ask You that again... ;)

---

### Post by jdeca57 on 2015-03-02
> **zika said:**
> Tell him not to check that and it will not ask You that again... ;)
Well yes, but it is the default brower. ;-) But you're right of course, it is a minor issue and I just installed mate 15.04 so who knows.

---

