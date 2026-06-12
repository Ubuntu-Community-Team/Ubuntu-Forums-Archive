---
title: "Pidgin 2.2.2 Released, will we see it in Gutsy Repositories?"
date: 2007-10-26
forum: Repositories &amp; Backports
---

### Post by Old Pink on 2007-10-26
Pidgin 2.2.2 is here, with only one change from 2.2.1:
[LIST]
[*]Various bug and memory leak fixes[/LIST]Will we see it in the Gutsy repositories? Considering it's just a bugfix? I know you're not fans of adding new features and software before the next 6 month release, but this is a 0.0.1 upgrade, tiny really.

I was hoping once we got to Gutsy, all Pidgin updates would hit the repositories, as with the Firefox upgrade/repository situation.

---

### Post by Twintop on 2007-10-26
I'd imagine that they'll include Pidgin 2.2.x, but not anything from 2.y.x where y > 2. It's kind of like Firefox's update from 2.0.0.6 to 2.0.0.8 being pushed down, or Gnome 2.20.1 in Feisty.

---

### Post by geeknik on 2007-10-27
Pidgin 2.2.2 is a security release.  It needs to be in the repositories.

[http://www.pidgin.im/news/security/?id=24](http://www.pidgin.im/news/security/?id=24)

---

### Post by FredB on 2007-10-27
> **geeknik said:**
> Pidgin 2.2.2 is a security release.  It needs to be in the repositories.

[http://www.pidgin.im/news/security/?id=24](http://www.pidgin.im/news/security/?id=24)

Just wait a little, and it will be in gutsy security repositories. Surely before a week.

---

### Post by Fr@nKy on 2007-10-31
GetDeb doesn't build Pidgin anymore? I can't even find 2.2.1 :(

---

### Post by Old Pink on 2007-11-08
**Still **no sign of this?

---

### Post by KLiFF on 2007-11-09
[1] In synaptic add this the source list:

deb [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) gutsy main

deb-src [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) gutsy main

[2] download the key file: 

[http://apt.schmidtke-hb.de/aptrepository.asc](http://apt.schmidtke-hb.de/aptrepository.asc)

[3] import key file in synaptic   "aptrepository.asc"

[4] refresh list

[5] update pidgin

[6] be happy

---

### Post by Old Pink on 2007-11-10
> **KLiFF said:**
> [1] In synaptic add this the source list:

deb [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) gutsy main

deb-src [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) gutsy main

[2] download the key file: 

[http://apt.schmidtke-hb.de/aptrepository.asc](http://apt.schmidtke-hb.de/aptrepository.asc)

[3] import key file in synaptic   "aptrepository.asc"

[4] refresh list

[5] update pidgin

[6] be happyFor security reasons, I don't recommend adding third party repositories, without first checking out all maintainers, searching to find how reliable they are and looking for an official/more trustworthy repository first.

After adding this, the owner, or maintainers, can install literally anything on your Ubuntu installation, and could put your data at risk. 

When posting a third party repository, explain the risks associated with it and try to explain why the one posted doesn't suffer from these risks.

For example, some third party repositories are kept and updated by people high up in the ubuntu project, who just want to provide third party bleeding edge applications on the side. I'd trust these people, but with no background knowledge on that particular repository, I won't be in any hurry to add it.

I know how to upgrade if I wanted to. I know where to find a third party repository if I wanted to. I've been here over a year, and contributed over 1,100 posts. However, neither of these were the aim of this thread. I just want to know when it'll be in the official repositories, which you'd understand if you read above. 

You joined this month and have one post, which makes me even more nervous of your posted repository. Why join just to post that? Especially when browsing the directory of that site, I found [this file](http://schmidtke-hb.de/repo.html) which suggests 2.2.2 isn't even in this repository, only 2.2.1, which is in official repositories. So your post is utterly useless.

---

### Post by 1337455 10534 on 2007-11-10
[http://ubuntuforums.org/showthread.php?t=608846](http://ubuntuforums.org/showthread.php?t=608846)

If you are still interested, just compile it. Its got all of the necessary steps.

---

### Post by potentia on 2007-11-12
> **FredB said:**
> Just wait a little, and it will be in gutsy security repositories. Surely before a week.

This post is now 2 weeks old... Why so confident.

---

### Post by potentia on 2007-11-12
> **Old Pink said:**
> 
You joined this month and have one post, which makes me even more nervous of your posted repository. Why join just to post that? Especially when browsing the directory of that site, I found [this file]("http://schmidtke-hb.de/repo.html") which suggests 2.2.2 isn't even in this repository, only 2.2.1, which is in official repositories. So your post is utterly useless.

2.2.2 is actually there, but only for Gutsy.

What a mess. Isn't it funny that it is available for Windows within hours after release, and so easy to install on Windows whereas you have to compile it to run this bug-fix release on the secure Linux.

:^o

---

### Post by Old Pink on 2007-11-12
> **potentia said:**
> 2.2.2 is actually there, but only for Gutsy.

What a mess. Isn't it funny that it is available for Windows within hours after release, and so easy to install on Windows whereas you have to compile it to run this bug-fix release on the secure Linux.

:^o

It's the Pidgin developer's fault for not supplying .deb files, even though they're hugely popular with the growth of Ubuntu. 

Can't really put the Ubuntu devs at fault for not adding such a minor release to the repositories. There's not a lot new anyway, there never is, Pidgin is essentially bugfix after bugfix after bugfix, with all suggested features postponed to stupid dates.

Then you ask why in the IRC channel and they tell you to write the program yourself. Idiots.

---

### Post by potentia on 2007-11-12
I was worried by the new category "patches welcome":

[http://developer.pidgin.im/milestone/Patches%20welcome](http://developer.pidgin.im/milestone/Patches%20welcome)

This is where tickets regarding new features are buried. It reminds me too much of what is happening to OpenOffice.

---

### Post by 1337455 10534 on 2007-11-12
Stupid file transfers only work after disabling proxy and switching to ICQ transfer mode. Grrr. I get 20 kbps on that!

---

### Post by potentia on 2007-11-12
I have to ask my friends to launch Skype every time they want to send me something big. Transfers on Yahoo does not work at all in Pidgin, on my connection. I can't see their Personal Status Messages (and it just cannot be rocket science to support them), and my network use them intensively. Support for custom emoticons would also be nice. They really add something to a conversation, but I can live without them.

Otherwise I pretty much like Pidgin. I am not a teen anymore, and I don't use all the fancy stuff in MSN and Yahoo Messenger. I hope they will add features to Pidgin soon, not everyone are as humble as I am. Without live video etc. etc. I think Pidgin will loose supporters in the long rung.

---

### Post by 1337455 10534 on 2007-11-12
Is there a complain/improvements/open blueprint for Pidgin?
Wanna make some friendly suggestions. They do (did?) a great job, but.. it needs some polishing.

---

### Post by potentia on 2007-11-14
Uhm, perhaps you want to discuss it with them here?

[http://pidgin.im/listinfo.html](http://pidgin.im/listinfo.html)

Or perhaps make a bug report as an enhancement request.

To be honest, I gave up making big or even smaller than that suggestions to open source projects. I used all my energy on openoffice.org. Generally my suggestions was accepted, but developing them took forever. Pidgin is no exception, nor is GIMP.

Google's wonderful *Summer of Code* is a huge helping hand, but also demonstrates the value of money combined with another precious resource: time.

---

