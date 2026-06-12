---
title: "Ubuntu One status &quot;capabilities mismatch&quot;"
date: 2013-06-01
forum: Ubuntu One (CLOSED)
---

### Post by Tulainas on 2013-06-01
Hey everyone!

 I'm running an acer netbook with Lucid (and i looooove it). It usually runs smoothly w/o any problems. 


 It turns out that since a few days ago i haven't been able to connect to the ubuntu-one service. this is the message i get in the terminal:

~$ u1sdtool --status
State: CAPABILITIES_MISMATCH
    connection: With User With Network
    description: capabilities mismatch
    is_connected: False
    is_error: True
    is_online: False
    queues: WORKING_ON_BOTH


 So I've tried to even re-install the service as suggested in this closed thread ([http://ubuntuforums.org/showthread.php?t=1304850](http://ubuntuforums.org/showthread.php?t=1304850), note it's from 2009), with no avail.

 So, does anybody have a clue what should i try?


 Thanks!


update:
 same instrucction, same account, different PC:

~$ u1sdtool --status
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing the commands pool
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING


Then, the problem is not the account.

---

### Post by romias on 2013-06-02
I have the same problem on my desktop ubuntu 10.04.
I have tried every possible solution I found available but the problem persists. I'm not sure but I think the problem occurred after updating the python a few days ago.
I always have access to the cloud from my android phone without any problem so this is not a problem in my account.
Any idea is welcome

---

### Post by smiki on 2013-06-02
same here. two days ago U1 stopped working. The same account works on two other PC's (with Precise) and a mobile phone. 
So the problem seems to be the old Lucid client.

---

### Post by Erteky on 2013-06-02
Same problem here, with Ubuntu 10.04. :(

State: CAPABILITIES_MISMATCH
    connection: With User With Network
    description: capabilities mismatch
    is_connected: False
    is_error: True
    is_online: False
    queues: WORKING_ON_BOTH

---

### Post by Irihapeti on 2013-06-02
It looks like the common factor here is the Lucid client.

Lucid has reached end-of-life. That means that there are no updates, which would include changes to the U1 client to match anything that they're doing at the server end.

It also means that it's upgrade or new install time.

If you don't like the idea of Unity or even Gnome-fallback in 12.04, you could try Xubuntu.

---

### Post by Tulainas on 2013-06-02
it's gonna be raring and gnome shell... i'll try fallback first

very nice way to invite to an upgrade though. I'd stayed forever with Lucid... so handy, so simple!

Sad.

---

### Post by Erteky on 2013-06-03
Can't we do anything to solve this problem? I don't want to update my OS for something like that... Ubuntu 10.04 works fine on my computer

---

### Post by Irihapeti on 2013-06-03
The trouble is that 10.04 isn't getting security upgrades, either. That could leave you vulnerable to exploits that have been patched in later versions.

If you want a version that you can stay with for 4 more years, Ubuntu 12.04 will be supported until April 2017.

---

### Post by Tulainas on 2013-06-04
I'm already on 12.04 and i'm missing so many "little things". Unity was too heavy for my hardware and i was getting annoying delays.  I switched to fallback mode and it is much MUCH better. :-)


 [Alt + tab] is not working, by the way... is it normal?

---

### Post by Tulainas on 2013-06-04
# how do I delete a repeated message?

---

### Post by Tulainas on 2013-06-04
# how do I delete a repeated message?

---

### Post by Irihapeti on 2013-06-04
Alt-tab should be working in 12.04.

You can't delete a double post, but you can use the "report post" button to ask the mods to do it for you. It's not just for reporting bad behaviour or spam.

---

### Post by Tulainas on 2013-06-04
Thank you! BTW, 12.04 in fallback mode is looking good. I think I like it. :-)

---

### Post by Bucky Ball on 2013-06-04
@ Tulainas: The way to delete posts is to do exactly what you did. Report it and staff will take care of it. There is currently no option for a regular user to delete their posts.

The two posts requesting how to delete posts have been deleted ... ;)

PS: Please refrain from duplicate reporting. There's only so many of us and can sometimes take awhile to get around to things. #-o

---

### Post by Irihapeti on 2013-06-04
I take it that Ubuntu One is working correctly?

---

### Post by Tulainas on 2013-06-04
Well, yes, in Precise... not in Lucid.

---

### Post by Irihapeti on 2013-06-04
That's what I meant &#8211; in Precise. Good to hear!

---

### Post by smiki on 2013-06-05
There seems to be a long open bug about this: 
[https://bugs.launchpad.net/ubuntuone-client/+bug/462828?comments=all](https://bugs.launchpad.net/ubuntuone-client/+bug/462828?comments=all)

---

### Post by Tulainas on 2013-06-07
again, it's a 2009 post...

---

### Post by Bucky Ball on 2013-06-07
> **Tulainas said:**
> again, it's a 2009 post...

... which stayed alive until 2011, went to sleep, and was then resurrected by smiki.

> **smiki said:**
> There seems to be a long open bug about this: 
[https://bugs.launchpad.net/ubuntuone-client/+bug/462828?comments=all](https://bugs.launchpad.net/ubuntuone-client/+bug/462828?comments=all)

@smiki: you were informed on that link that your issue was not about capabilities_mismatch and it was fully explained. From that thread:

[QUOTE=Bert Driehuis (driehuis)]Please read comment #13. The CAPABILITIES_MISMATCH that you're seeing is for your protection. It's ubuntuone's way of telling you: your client is outdated. The bug that you re-opened is not about CAPABILITIES_MISMATCH. It's about files being marked for deletion, which is not the case.[/QUOTE]

---

### Post by takanami on 2013-06-07
> **Erteky said:**
> Can't we do anything to solve this problem? I don't want to update my OS for something like that... Ubuntu 10.04 works fine on my computer

Me too. I don't want to update my OS. Ubuntu 10.04 works fine on my computer,too.

Is there anybody try to build ubuntu-one client for lucid from [https://launchpad.net/ubuntuone-client](https://launchpad.net/ubuntuone-client)  ?

---

### Post by lisati on 2013-06-07
> **takanami said:**
> Me too. I don't want to update my OS. Ubuntu 10.04 works fine on my computer,too.

Is there anybody try to build ubuntu-one client for lucid from [https://launchpad.net/ubuntuone-client](https://launchpad.net/ubuntuone-client)  ?

Upgrading to a newer version of Ubuntu has been suggested. An alternative would be to try the build yourself.

---

### Post by cariboo on 2013-06-08
> **takanami said:**
> Me too. I don't want to update my OS. Ubuntu 10.04 works fine on my computer,too.

Is there anybody try to build ubuntu-one client for lucid from [https://launchpad.net/ubuntuone-client](https://launchpad.net/ubuntuone-client)  ?

You have two choices, build the client yourself, there aren't any guarantees that it will work, or update to 12.04, if Ubuntu doesn't work for you, there is always [Xubuntu]("http://xubuntu.org/getxubuntu/"), [Lubuntu]("http://lubuntu.net/blog/lubuntu-1204-now-available"), or [Kubuntu]("http://www.kubuntu.org/news/12.04-release"). Ubuntu,  Xubuntu and Kubuntu 12.04 releases are supported until 2017, Lubuntu 12.04 being the new kid on the block is only supported for 18 months.

Seeing as 10.04 has reached the end of it's life cycle, you will more than likely lose more than security updates as time goes on. As new versions of packages are released you will find that they won't work with the version you are running. 

The big problem with running a version that reached it's EOL, is security, the chances that your system will be hacked becomes greater as time goes on, as exploits and critical bugs are found all the time, and patches to fix those problems will no longer be available for the version you are running.

Hopefully I've given you enough information to allow you to make a choice as to what version you want to use for the next 4 years, and you should be fully aware that any problems you run into running 10.04 will not be fixed, and even support on the forums will eventually stop, as almost no one is using that version any more

---

### Post by Bucky Ball on 2013-06-08
> **takanami said:**
> Me too. I don't want to update my OS. Ubuntu 10.04 works fine on my computer,too.



Welcome to the forums. +1 to cariboo's previous post. Unless you are using the server version, 10.04 LTS has reached end-of-life and is no longer supported. This means you will receive no updates from this Ubuntu repositories, *and this includes security updates*. The risk is yours. Third-party repos will still update/upgrade as normal.

Five year support for the LTS releases, to match the server versions, began with 12.04 LTS, supported until April 2017. You can upgrade directly from one LTS to the next (via Update Manager) or backup and clean install, but naturally, the choice of doing either or upgrading at all is yours ... good luck whatever you choose, but remember, 10.04 LTS is EOL and will receive no more security updates (not a worry if the machine is not used online).

PS: You could always install 12.04 LTS on a spare partition so you had 10.04 LTS to fallback on and transition. If Unity is putting you off there are plenty of options; I'm a longtime Xubuntu/Xfce user. ;)

---

### Post by takanami on 2013-06-08
lisati, cariboo907, Bucky Ball, thank you for your advice.:D
I'll make new partition and install  Xubuntu or Lubuntu and try them.
My Thinkpad X61 may be insufficient to work with 12.04 with Unity.


Thank you.

---

### Post by Tulainas on 2013-06-10
Seriously man, try fallback mode: Your [thinkpad X61]("http://www.notebookreview.com/default.asp?newsID=3765") surely can handle it.

 Worst case scenario: you may like it. :-)

---

### Post by edgar_knarretje on 2013-06-14
> **Erteky said:**
> Can't we do anything to solve this problem? I don't want to update my OS for something like that... Ubuntu 10.04 works fine on my computer

I really support this question, I have the same problem and currently I don't have the time to upgrade all my laptops/pcs. So, can we port the new version into 10.4? Or is there another trick? Only with clear instructions I can manage to create a version out of source... 

anyone who has idea's? 

greetings, Edgar

---

### Post by QIII on 2013-06-14
This issue has been answered several times in this thread and it is going in circles.

Thread closed.

---

### Post by lisati on 2013-06-14
> **edgar_knarretje said:**
> I really support this question, I have the same problem and currently I don't have the time to upgrade all my laptops/pcs. So, can we port the new version into 10.4? Or is there another trick? Only with clear instructions I can manage to create a version out of source... 

anyone who has idea's? 

greetings, Edgar

We appreciate that you want to stay with something that you're familiar with and that you know, for the most part, works.

Because 10.04 has reached the end of its life, it is no longer officially supported. Although there will currently be some people with experience of this version who frequent this forum, it's likely to get more difficult getting the help you are asking for.

---

