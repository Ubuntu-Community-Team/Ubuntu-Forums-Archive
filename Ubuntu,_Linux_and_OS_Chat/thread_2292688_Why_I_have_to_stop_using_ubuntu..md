---
title: "Why I have to stop using ubuntu."
date: 2015-08-30
forum: Ubuntu, Linux and OS Chat
---

### Post by bgeek12 on 2015-08-30
This is an FYI to the developer team - not a rant.  Just sharing the info.

I maintain some servers with large raid6 arrays.  Some are Hyper-V VMs.  I gave in to the LTS 12 expiration warnings and upgraded.  After the upgrade to 14.04, a kernel memory leak would cause the servers to hang after a few days.  Some searching confirmed that others had experienced the leak.  The solution was to upgrade the kernel.  So I had to upgrade to 15.x.  Alas, zfs isn't supported in 15.x.  So I must move on to another distro.

Crossing my fingers that CentOS will mount the array.

regards

---

### Post by CantankRus on 2015-08-30
...and what makes you think they'll be here?

---

### Post by RichardET on 2015-08-30
> **bgeek12 said:**
> This is an FYI to the developer team - not a rant.  Just sharing the info.

I maintain some servers with large raid6 arrays.  Some are Hyper-V VMs.  I gave in to the LTS 12 expiration warnings and upgraded.  After the upgrade to 14.04, a kernel memory leak would cause the servers to hang after a few days.  Some searching confirmed that others had experienced the leak.  The solution was to upgrade the kernel.  So I had to upgrade to 15.x.  Alas, zfs isn't supported in 15.x.  So I must move on to another distro.

Crossing my fingers that CentOS will mount the array.

regards

Do yourself a favor - go with a serious server OS - go with FreeBSD.

---

### Post by TheFu on 2015-08-30
> **bgeek12 said:**
> This is an FYI to the developer team - not a rant.  Just sharing the info.

I maintain some servers with large raid6 arrays.  Some are Hyper-V VMs.  I gave in to the LTS 12 expiration warnings and upgraded.  After the upgrade to 14.04, a kernel memory leak would cause the servers to hang after a few days.  Some searching confirmed that others had experienced the leak.  The solution was to upgrade the kernel.  So I had to upgrade to 15.x.  Alas, zfs isn't supported in 15.x.  So I must move on to another distro.

Crossing my fingers that CentOS will mount the array.

regards

What?  I don't understand. You don't need to change releases just to change the kernel and I'd be very surprised if ZFS didn't have a PPA.  Ubuntu 15.xx isn't a good idea for any server, IMHO.  Servers need to be LTS. It isn't like we want to reinstall a fresh server every 6 months.
 
A systemd/zfs bug - [https://bugs.launchpad.net/zfs/+bug/1431523](https://bugs.launchpad.net/zfs/+bug/1431523)

If you are using just an installer or some GUI, then I can understand.  GUIs only cover 10% (if that) on a server. The CentOS v7 installer disk subsection is very nice. I don't remember seeing ZFS in there - they are smitten with XFS.  That doesn't mean you can't use ZFS - just that it isn't part of the installer.

---

### Post by RichardET on 2015-08-30
ZFS is integrated into FreeBSD;  another point to ponder....oh and also no systemd.

I found a great intro to ZFS on Teds blog - it is OpenBSD centric, but explains many issues with use of ZFS - its worth a read;  one point he mentions is that ZFS is a total memory hog - I would second it;  it really is way too much for most needs, I think.

[http://www.tedunangst.com/flak/post/ZFS-on-OpenBSD](http://www.tedunangst.com/flak/post/ZFS-on-OpenBSD)

---

### Post by TheFu on 2015-08-30
> **RichardET said:**
> ZFS is integrated into FreeBSD;  another point to ponder....oh and also no systemd.

+1 on no systemd.  That little thing is turning into "THE BEAST" - seems they haven't found a feature request that didn't belong in the same code tree.  Did you see the plan to add "su" capability to systemd because **su** is too confusing?  Perhaps if 50 people sent him ***The Art of Unix Programming*** the clue would be gotten?

---

### Post by MartyBuntu on 2015-08-30
> **bgeek12 said:**
> I gave in to the LTS 12 expiration warnings and upgraded.

If you're referring to 12.04 LTS, it isn't even close to EOL...

---

### Post by QIII on 2015-08-30
As stated, the developers don't hang out here.

If you want to move to a new distro there is no reason for you to announce it here.  Are you looking for our permission?  You don't need it.  Nor do you need to apologize.

Use whatever works.

I've had a home server and a web server running Trusty servers for quite some time without encountering any kernel memory leaks.  Not sure what you might be running into.  Perhaps you might ask for help with what might be an easy fix rather than going through the effort of a distro migration?

---

### Post by Jordan_Cameron on 2015-08-31
ZFS is supported on 15.04, however the startup init script hasn't been upgraded for systemd in the ppa.  However if you search around there are answers on how to make it work.

Secondly, if ZFS is important, then yes, FreeBSD is a better option.

CentOS uses an older kernel then 14.04...just an FYI

---

### Post by Bucky Ball on 2015-08-31
Bit bemused why anyone would use an interim release supported for nine months for a server ... :-k

Bit off topic, but I thought the idea with servers was to avoid upgrading every six months and thus avoid downtime ...

---

### Post by Mike_Walsh on 2015-08-31
@Jordan_Cameron:-

You've got **my** old avatar there.....!! :lol:;)


Regards,

Mike.

---

### Post by bgeek12 on 2015-09-01
> **RichardET said:**
> ZFS is integrated into FreeBSD;  another point to ponder....oh and also no systemd.

I found a great intro to ZFS on Teds blog - it is OpenBSD centric, but explains many issues with use of ZFS - its worth a read;  one point he mentions is that ZFS is a total memory hog - I would second it;  it really is way too much for most needs, I think.

[http://www.tedunangst.com/flak/post/ZFS-on-OpenBSD](http://www.tedunangst.com/flak/post/ZFS-on-OpenBSD)

The servers are in my basement.  The only thing they do for me is serve ZFS.  It ZFS is a memory hog, that's OK.  I chose ubuntu for the large community and easy install.  Getting ZFS one it was really simple and it worked fine.

---

### Post by bgeek12 on 2015-09-01
> **CantankRus said:**
> ...and what makes you think they'll be here?

I don't know.  Maybe I'm juggling too many things and didn't bother to look for the support groups?

---

### Post by bgeek12 on 2015-09-01
FreeBSD you say?  Nice.  I'll give that one a try.

---

### Post by bgeek12 on 2015-09-01
Re: 12.04 not close to EOL.

I see that now.  Thanks for the info.  After updating the hardware layer and everything else I could, why would the system keep nagging me to upgrade to a newer release?  Interesting.

---

### Post by bgeek12 on 2015-09-01
Re: [COLOR=#000000]CentOS uses an older kernel then 14.04...just an FYI

[/COLOR]The CentOS 7 that I installed uses a newer kernel than 12.04 would ever give me.  14.04 has the memory leak that would hang the box.

---

### Post by bgeek12 on 2015-09-01
> **Bucky Ball said:**
> Bit bemused why anyone would use an interim release supported for nine months for a server ... :-k

Bit off topic, but I thought the idea with servers was to avoid upgrading every six months and thus avoid downtime ...


sorry for not explaining.  the servers are in my basement.  their sole purpose in life is to provide access to a large raid6 array via zfs.

downtime isn't a big deal.

I must have missed something upgrading 12.04.  It wouldn't stop nagging me to update to a later version.  I should have researched that problem more.  I can revert back to 12.04 and give it a go.  It's no big deal to fire up a new VM and attach the disks if it ever stops nagging.

thanks for the tips.

12.04 LTS?  FreeBSD?  Hmmm.

---

### Post by CharlesA on 2015-09-01
> **CantankRus said:**
> ...and what makes you think they'll be here?

The correct answer should have been to direct them to launchpad or one of the dev mailing lists. I think some of the devs hang out on IRC, but a bug report about a memory leak would benefit everyone using 14.04.

> **RichardET said:**
> Do yourself a favor - go with a serious server OS - go with FreeBSD.

I use debian, thank you very much. :p

> **TheFu said:**
> +1 on no systemd.  That little thing is turning into "THE BEAST" - seems they haven't found a feature request that didn't belong in the same code tree.  Did you see the plan to add "su" capability to systemd because **su** is too confusing?  Perhaps if 50 people sent him ***The Art of Unix Programming*** the clue would be gotten?

I heard about that and all I could think was... why...??? What is so confusing about su?

> **bgeek12 said:**
> Re: 12.04 not close to EOL.

I see that now.  Thanks for the info.  After updating the hardware layer and everything else I could, why would the system keep nagging me to upgrade to a newer release?  Interesting.

What is the message you are getting telling you to upgrade? I know I seen notifications on my 12.04 desktop box that 14.04 is available, but they aren't forcing me to upgrade the box. I believe you can disable those notifications too.

EDIT: Here's a link to where you can disable that notification:
[http://askubuntu.com/questions/515161/ubuntu-12-04-disable-release-notification-of-14-04-in-update-manager](http://askubuntu.com/questions/515161/ubuntu-12-04-disable-release-notification-of-14-04-in-update-manager)

Also: Here's the page showing EoL date for the currently supported Ubuntu versions: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

> **bgeek12 said:**
> sorry for not explaining.  the servers are in my basement.  their sole purpose in life is to provide access to a large raid6 array via zfs.

downtime isn't a big deal.

I must have missed something upgrading 12.04.  It wouldn't stop nagging me to update to a later version.  I should have researched that problem more.  I can revert back to 12.04 and give it a go.  It's no big deal to fire up a new VM and attach the disks if it ever stops nagging.

thanks for the tips.

12.04 LTS?  FreeBSD?  Hmmm.

Stick with 12.04 if it has been working for you and submit a bug report on the memory leak you found on 14.04, if you can.

---

### Post by TheFu on 2015-09-01
> **bgeek12 said:**
> sorry for not explaining.  the servers are in my basement.  their sole purpose in life is to provide access to a large raid6 array via zfs.

Ubuntu Server doesn't nag about anything. There is a "update available" message at the console login.  
```
New release '14.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.
``` That's it.  I'd rather have the landscape and utilization summary crap gone. [https://askubuntu.com/questions/318592/how-can-i-remove-the-landscape-canonical-com-greeting-from-motd](https://askubuntu.com/questions/318592/how-can-i-remove-the-landscape-canonical-com-greeting-from-motd) should solve my issue. That was easy.  Or better
```

sudo apt-get purge landscape-client landscape-client-ui landscape-client-ui-install landscape-common
```

Haven't seen the update GUI nag from a desktop install in a few years, but vaguely remember there was a checkbox to stop showing it.

---

