---
title: "Restore machine back to default settings on boot"
date: 2010-12-19
forum: Security
---

### Post by tranduyhung on 2010-12-19
Hi,

This is my idea:

I have a fresh installation of *buntu machine. I will let kids play with this machine, they could remove or install applications, delete folders, data,... or do whatever they want. And after rebooting the machine, it's back to default settings with default data, like a fresh installation.

I'm still searching for a solution.

If you know any way to do this. Please tell me.

Thank you so much :). 

Regards,
Hung

---

### Post by HermanAB on 2010-12-20
Howdy,

VMware.

Create a VM of your OS of choice and make a tar ball of the whole VM directory.  When you want to restore it, untar and overwrite the working copy from the archive.

---

### Post by CharlesA on 2010-12-20
A VM with snapshots would work as well.

---

### Post by bodhi.zazen on 2010-12-20
Either a virtual machine or a live CD.

---

### Post by tranduyhung on 2010-12-20
Hi all,
Virtual machine is really a good idea. But we need a real machine.
My idea comes from [Deep Freeze]("http://www.faronics.com/en/Products/DeepFreeze/DeepFreezeCorporate.aspx") program in Microsoft Windows. Is there any free and open source program like Deep Freeze in Linux?

---

### Post by CharlesA on 2010-12-20
I found this: [http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Deepfreeze_for_Linux](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Deepfreeze_for_Linux)

That might work, it goes on the principle of setting the machine up as a kiosk and replacing the home directory after a reboot.

---

### Post by HermanAB on 2010-12-21
You can use Kiosk mode, buta VM will allow you to easily use the machine normally still.

---

### Post by Megaptera on 2010-12-21
Have a look at Ofris!
 This "If you ever went to a cyber cafe, you probably noticed that any changes you make to their system: create or delete files, settings and so on, everything resets when you restart the computer. That's what the Deep Freeze program does.


Ofris is a Deep Freeze like application for Linux that is very easy to use - once you install it, you can "deep freeze" your Linux computer in a matter of seconds."

From here:[http://www.webupd8.org/2010/08/ofris-deep-freeze-like-application-for.html](http://www.webupd8.org/2010/08/ofris-deep-freeze-like-application-for.html)

With simple usage described here: [http://www.webupd8.org/2010/09/ofris-gets-appindicator-gofris-deep.html#more](http://www.webupd8.org/2010/09/ofris-gets-appindicator-gofris-deep.html#more)

---

### Post by Rubi1200 on 2010-12-21
> **Megaptera said:**
> Have a look at Ofris!
 This "If you ever went to a cyber cafe, you probably noticed that any changes you make to their system: create or delete files, settings and so on, everything resets when you restart the computer. That's what the Deep Freeze program does.


Ofris is a Deep Freeze like application for Linux that is very easy to use - once you install it, you can "deep freeze" your Linux computer in a matter of seconds."

From here:[http://www.webupd8.org/2010/08/ofris-deep-freeze-like-application-for.html](http://www.webupd8.org/2010/08/ofris-deep-freeze-like-application-for.html)

With simple usage described here: [http://www.webupd8.org/2010/09/ofris-gets-appindicator-gofris-deep.html#more](http://www.webupd8.org/2010/09/ofris-gets-appindicator-gofris-deep.html#more)
Have you tested this? Is it reliable? Is the source (PPA) trustworthy?

Sorry for the questions, but I don't think we would want to mess up someone's system without knowing more details.

---

### Post by bodhi.zazen on 2010-12-21
I would again suggest a live CD =)

---

### Post by CharlesA on 2010-12-21
> **bodhi.zazen said:**
> I would again suggest a live CD =)
That would probably be the easiest thing to do.

You can even create your own custom one by using Remastersys.

---

### Post by Megaptera on 2010-12-21
> **Rubi1200 said:**
> Have you tested this? Is it reliable? Is the source (PPA) trustworthy?

Sorry for the questions, but I don't think we would want to mess up someone's system without knowing more details.

No I've not tested that one but have used many tutorials from that site that I got linked to from a thread here in this forum (can't recall which thread) so I think they post reliable stuff ... at least I've not trashed my laptop doin' anything from there :p

---

### Post by tranduyhung on 2010-12-21
> **Megaptera said:**
> Have a look at Ofris!
 This "If you ever went to a cyber cafe, you probably noticed that any changes you make to their system: create or delete files, settings and so on, everything resets when you restart the computer. That's what the Deep Freeze program does.


Ofris is a Deep Freeze like application for Linux that is very easy to use - once you install it, you can "deep freeze" your Linux computer in a matter of seconds."

From here:[http://www.webupd8.org/2010/08/ofris-deep-freeze-like-application-for.html](http://www.webupd8.org/2010/08/ofris-deep-freeze-like-application-for.html)

With simple usage described here: [http://www.webupd8.org/2010/09/ofris-gets-appindicator-gofris-deep.html#more](http://www.webupd8.org/2010/09/ofris-gets-appindicator-gofris-deep.html#more)

Thank you for your suggestiom, I tried ofris, it only restores your home directory and when you remove programs, if you install new programs when your computer is "freezed", the new programs are still there after rebooting.

And I tried lethe, it works well for me, so maybe I would use this application.

I can't choose livecd solution because of RAM memory and maybe I would use a netbook with no cdrom.

---

