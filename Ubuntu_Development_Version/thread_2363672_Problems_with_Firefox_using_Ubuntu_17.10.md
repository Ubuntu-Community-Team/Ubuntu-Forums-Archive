---
title: "Problems with Firefox using Ubuntu 17.10"
date: 2017-06-13
forum: Ubuntu Development Version
---

### Post by forgotten2011 on 2017-06-13
Hi
I am having a problem running either Google Chrome and Firefox. chrome doesn't even come up. Firefox comes up but except for the menus at the top left, the center screen is all black. I upgraded to Ubuntu 17.10 in the hope that the problem go away, it didn't. I got an error mesaage when this first happened, ubuntu 17.04 quipzilla crashed  with sigabrt. I can't bring up the VPN connection either. Skype still comes up ok. I can still ping out to [www.yahoo.com]("http://www.yahoo.com") with a command prompt.
My computer is the Dell T3600 with a 6 core Xeon cpu.
I would like to avoid reinstalling Ubuntu if I can avoid it. Can someone point me in the right direction? Has anyone had the problem? 

Any help is appreicated.

Thank you

---

### Post by wildmanne39 on 2017-06-13
*Thread moved to **Ubuntu Development Version**.*

You do know that this is the developmental version of Ubuntu that does not come out until October?

---

### Post by forgotten2011 on 2017-06-13
I can try uninstalling 17.10? or reinstalling 17.04 ?

---

### Post by wildmanne39 on 2017-06-13
17.04 is only supported about seven more months, if it were me I would install 16..04 LTS it has support until April 2021.

---

### Post by forgotten2011 on 2017-06-13
> **wildmanne39 said:**
> 17.04 is only supported about seven more months, if it were me I would install 16..04 LTS it has support until April 2021.
That's probably a good idea I will reinstall 16.04

---

### Post by ventrical on 2017-06-13
> **forgotten2011 said:**
> Hi
I am having a problem running either Google Chrome and Firefox. chrome doesn't even come up. Firefox comes up but except for the menus at the top left, the center screen is all black. I upgraded to Ubuntu 17.10 in the hope that the problem go away, it didn't. I got an error mesaage when this first happened, ubuntu 17.04 quipzilla crashed  with sigabrt. I can't bring up the VPN connection either. Skype still comes up ok. I can still ping out to [www.yahoo.com]("http://www.yahoo.com") with a command prompt.
My computer is the Dell T3600 with a 6 core Xeon cpu.
I would like to avoid reinstalling Ubuntu if I can avoid it. Can someone point me in the right direction? Has anyone had the problem? 

Any help is appreicated.

Thank you

I  have a Dell Precision T3400 Core2Duo Quad core with nVidia video adapter. It was running slow on 14,04, 16.04 but I fresh installed artful-desktop daily 17.10 (ubuntu-gnome) and it is running faster than previous version of (unity-desktop). I am running this  on my KVM stack.  I have no problem logging in through wayland session or gnome-shell. 

 There are problems with this particular Dell hardware but 17.10 artful-desktop fresh install seems to have cleared a lot of issues.

Regards..

---

### Post by forgotten2011 on 2017-06-15
Posting for help here has been no help what so ever.

---

### Post by forgotten2011 on 2017-06-15
I will use google.com for help next time.

---

### Post by rrnbtter on 2017-06-15
Greetings,
Google is the best way to find solutions for Ubuntu and Linux problems. You will very often be led back to this site but there are posts all over the Internet. If you have a system that you depend on for daily use the LTS version is best. Most of us in this development area don't mind a reinstall and often will invite one.

---

### Post by coffeecat on 2017-06-15
> **forgotten2011 said:**
> Posting for help here has been no help what so ever.

I&#8217;m sorry to hear that. However, to get the help you need here, you need to help others to help you, by using the forum in the best way possible. Let me give you some pointers.

You started the thread stating that you were using Ubuntu 17.10, the current development version and, because of this, it was moved to the Ubuntu Development Version sub-forum. This is a good place to discuss the development version, but most people do not use development versions for their primary or production system.

You then stated that you &#8220;will&#8221; install 16.04, but gave no further details and did not post again until the post that I quote. Two points: this is not the place to get help for 16.04 &#8211; people looking to help with issues such as yours look in other sections &#8211; and without knowing whether or not you did indeed install 16.04, and whether the problem you describe is also present in 16.04, no one can really offer anything further.

Also &#8211; you left your thread to go stale for two days by not bumping or giving further information before apparently giving up. 

Three tips:

[list][*]Ensure that your thread is in the correct place, and ask the staff to move it if you think it isn't by using the report post button on one of your posts in order to send a request to the staff area.
[*]If you change your system in any way, give a coherent narrative of exactly what you have done, and whether that has made any difference to your original problem. People cannot help if you don&#8217;t tell them what is happening and/or what you have done.
[*]Bump your thread occasionally &#8211; say after 12-24 hours of no activity. [/list]

---

### Post by ventrical on 2017-06-15
> **forgotten2011 said:**
> I will use google.com for help next time.

Did you remove ppa before you upgraded?

It would have helped if you told us quipzilla was a ppa Obviously there are problems with it.

```

sudo add-apt-repository ppa:nowrep/qupzilla
sudo apt-get update
sudo apt-get install qupzilla

```



Regards..

---

