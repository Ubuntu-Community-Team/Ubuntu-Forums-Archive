---
title: "Opera"
date: 2006-09-25
forum: Repositories &amp; Backports
---

### Post by tedux on 2006-09-25
any one get opera installed, I keep getting depen unsuff

thanks

---

### Post by Kabal on 2006-09-25
What version of opera are you trying to install?

---

### Post by tedux on 2006-09-25
I tried 9.0  and 9.02

---

### Post by aysiu on 2006-09-25
Get a fresh sources.list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then paste this command in the terminal: ```
sudo aptitude update && sudo aptitude install opera
```

---

### Post by tedux on 2006-09-25
Thank you aysiu. I keep fresh source. I can usely find it in synaptic but just could find it this time. tried diffrent sudo's with no find. But this worked just fine thank you again. know don't have to use firefox. bye

---

### Post by tedux on 2006-09-25
how do you know these commands, I was seaching for flash and saw your reply on a thread and use it worked very well thanks

---

### Post by aysiu on 2006-09-25
> **tedux said:**
> how do you know these commands, I was seaching for flash and saw your reply on a thread and use it worked very well thanks
Every person who helps you was (once upon a time) helped by someone else.

---

### Post by tedux on 2006-09-25
you know What. I can't find opera, it said done, I rebooted. where did it go.

---

### Post by tedux on 2006-09-25
Oh it said no candidate version found for opera

---

### Post by aysiu on 2006-09-25
That's weird. It's definitely in the commercial repositories.

I suppose we could always try it the old-fashioned way: ```
wget -c http://archive.canonical.com/ubuntu/pool/main/o/opera/opera_9.00-20060616.7_i386.deb
sudo dpkg -i opera_9.00-20060616.7_i386.deb
rm opera_9.00-20060616.7_i386.deb
```

---

### Post by tedux on 2006-09-25
I don't think I had a fresh rep. them back ports get me

---

### Post by tedux on 2006-09-25
how did you add the commercial

---

### Post by tedux on 2006-09-25
Thank you, I didn't have it as fresh as I thought

---

### Post by aysiu on 2006-09-25
> **tedux said:**
> how did you add the commercial
By following these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Make sure to copy *over* your old sources.list.

---

### Post by tedux on 2006-09-25
i don't seem to beable to edit the main title to soved. and i can't spell soved. thanks I am now using opera.

---

### Post by picpak on 2006-09-27
It's easier to just go to Add/Remove Programs and install Opera. It does it all automatically.

Of course, if you don't have it, you can just install gnome-app-install.

---

