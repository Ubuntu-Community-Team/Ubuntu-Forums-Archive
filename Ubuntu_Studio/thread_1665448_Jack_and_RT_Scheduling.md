---
title: "Jack and RT Scheduling"
date: 2011-01-12
forum: Ubuntu Studio
---

### Post by dawiba on 2011-01-12
Hi Everyone

As I understand it, I can install Jack with RT Scheduling enabled without having an RT Kernel installed. My understanding is this will give Jack elevated privileges to use RT scheduling to help prevent drop-outs etc. When installed this way, Jack creates audio.conf with the appropriate options in place for me, at least it did on my system. All I've had to do was make myself a member of the audio group to use my Firewire card.

Digging a bit deeper, I see that Jackaudio.org seem to recommend creating a group called 'Realtime' and making myself a member of that group as follows

```
groupadd realtime
usermod -a -G realtime yourUserID
```

Problem is, I'm not clear just what that would do (the site doesn't explain it, it just says to do it) and if I need to do it as my system is running fine just now without it.

Can anyone offer any insight as to what this does and if there is anything to be gained?

Thanks

---

### Post by Pablo_F on 2011-01-12
[http://jackaudio.org/linux_rt_config](http://jackaudio.org/linux_rt_config)

Read a bit below:

> If you are using a distribution that has already created the group and configured the "limits" file, you will need to determine the name of the group (it is likely called "audio" or "jackuser") and then you can just add yourself to the group with this command (run as the superuser inside a terminal window):

usermod -a G theGroupName yourUserId

substituting the real names for theGroupName and yourUserId

You already have it. In Debian/Ubuntu jackd package post installation script creates the limits file to give the privileges for the users belonging to the audio group. Afaik, that is a only a convention. You could name that group as you like. 

Paul is being generic in the explanation because other distros do it differentely or don't do it at all.

There is no more to it. 

Cheers! Pablo

---

### Post by dawiba on 2011-01-12
xThanks for the reply. That was the page I had been reading.

That's what I thought, that Jack had created the audio.conf file and all I needed to do was add myself to the audio group.

It's just that the way it's written (or perhaps just the way I read it), it looks as if after adding yourself to the audio group, you should then create a 'realtime' group and make yourself a member of that too.

As I understand it now, this step isn't necessary for me.

Thanks again

---

