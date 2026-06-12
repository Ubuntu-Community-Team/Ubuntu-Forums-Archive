---
title: "Known issue in Karmic??"
date: 2010-01-30
forum: Server Platforms
---

### Post by artheus on 2010-01-30
Hey! I've got a little problem. Not really critical, but irritating.

On three different servers I've recently installed a copy of Ubuntu Karmic Server ED. And when I start them, and get to the log in screen. It will continue to write out stuff like this :

```

webServer login:   *Restarting OpenBSD Secure Shell server sshd
                                                         _

```

And sometimes it's a lot worse. It writes out all kinds of stuff.

Is this a know Karmic issue? Or is it just me making some kind of weird mistake??

Thanks,
Artheus

---

### Post by retko on 2010-01-30
I have some issue. :( 

Four independent instalations, all of them have this issue.

---

### Post by Vegan on 2010-01-30
What kind of machines are being used, my crystal ball is out of order today.

---

### Post by BkkBonanza on 2010-01-31
The message you're seeing for openssh is normal. It just happens to be emitted late, after the login prompt so it's confusing. 

The message occurs because the openssh server gets restarted during the boot sequence. I'm not sure this used to be the case but it seems to be now. I had a look because I was getting this as well. It's triggered by the /etc/network/if-up.d/openssh script which causes a restart when an interface gets brought up. It appears that in cases where openssh comes up before the interface it needs to get restarted after the interface. My guess is that this fixes some issues and so was added to the startup sequence recently. I don't recall it happening in earlier versions. It likely fixes issues in the transition to Upstart where ssh comes up too early.

If you also get fsck messages at boot, that's generally normal. 
As for other messages you'll have to be more specific.

---

### Post by artheus on 2010-01-31
[IMG]http://artheus.se/screen.jpg[/IMG]

This is the start screen of one of the servers.
I find that kind of weird..

//Artheus

---

### Post by BkkBonanza on 2010-01-31
Looks about right to me. I don't see any specific message to worry about.
Just hit enter to get the login prompt.
You have to remember that startup processes happen in multiple threads so messages can get emitted at overlapping times that sometimes intermix with each other. Sometimes this can concatenate messages onto the same line and look jumbled. If you check your /var/log/syslog file you'll see them all ordered by time.

On desktop installs this stuff is all hidden, but on the server they just let it dump to screen.

---

### Post by artheus on 2010-01-31
Okey! Thank you!

Then I will not worry anymore! :)

Cheers,
Artheus

---

### Post by nix4me on 2010-01-31
Its a DHCP "feature".  If you change to a static ip, it will not do that.

Search the bug reports, there are many, many entries about this exact behaviour.

Disabling dhcp and swithing to static ip is the only known solution to this "feature".

---

