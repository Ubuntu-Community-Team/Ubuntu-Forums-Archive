---
title: "Ubuntu Desktop != Ubuntu Server or is 32bit != 64bit"
date: 2011-07-13
forum: Server Platforms
---

### Post by linuxnizer on 2011-07-13
Hi,
  I have Ubuntu Server 32bit 10.04 LTS installed about a year ago. I keep updating my server to make sure it's secure (basically it's a public fileserver)

  I also installed Ubuntu Desktop 64bit 10.4 LTS. Also, fully patched with the latest updates.

Now, 

uname  on _32bit server_ says that I have: **2.6.35-25-generic-pae #44~lucid1-Ubuntu SMP Tue Jan 25 21:00:01 UTC 2011 i686 GNU/Linux**
uname  on _64bit desktop_ says that I have: [B]2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux

[/B]As you can see, the server kernel has relatively newer kernel.
Not sure is it 64bit kernel lagging in updates or is it the desktop stream is behind in kernel updates.

It's not big deal, I'm just curious to know :).

Cheers,
Abdul

---

### Post by snowpine on 2011-07-13
2.6.32 is the 10.04 kernel and 2.6.35 is the 10.10 kernel.

My guess is you're using backports on the server?

[http://packages.ubuntu.com/lucid/linux-image-generic-pae-lts-backport-maverick](http://packages.ubuntu.com/lucid/linux-image-generic-pae-lts-backport-maverick)

---

### Post by linuxnizer on 2011-07-13
I used dist-upgrade on both machines

---

### Post by linuxnizer on 2011-07-13
> **snowpine said:**
> 2.6.32 is the 10.04 kernel and 2.6.35 is the 10.10 kernel.

My guess is you're using backports on the server?

[http://packages.ubuntu.com/lucid/linux-image-generic-pae-lts-backport-maverick](http://packages.ubuntu.com/lucid/linux-image-generic-pae-lts-backport-maverick)

Actually, the 10.04 server x86 backport is here: [http://packages.ubuntu.com/lucid-updates/linux-image-2.6.35-25-generic-pae](http://packages.ubuntu.com/lucid-updates/linux-image-2.6.35-25-generic-pae) (exact version as the one installed on my server [SIZE=1]2.6.35-25.44~lucid1)[/SIZE] 

And the same kernel is available for x86_64 @ [http://packages.ubuntu.com/lucid/amd64/linux-headers-generic-lts-backport-maverick/download](http://packages.ubuntu.com/lucid/amd64/linux-headers-generic-lts-backport-maverick/download) ....!!


Hmmm, is it then the desktop version that didn't get the new kernel!



So...fired aptitude on my 64bit desktop (with old  .32 kernel)....

Headers are available for the new .35-25 kernel
[IMG]http://mlfat.com/terminal-screen-capture.png[/IMG]

Notice the last 4 lines are "the same" kernel but with different flavors.
1- virtual 
2- server
3- generic
4- <blank>


OK...Then....looked into some linux images....the latest one (i.e. .35-25)....and the generic type :)
[IMG]http://mlfat.com/Screenshot.png[/IMG]

And behold...it's applicable for both 32bit AND 64bit :)

So....more reading to figure out what's going on....


Cheers,
Abdul

---

