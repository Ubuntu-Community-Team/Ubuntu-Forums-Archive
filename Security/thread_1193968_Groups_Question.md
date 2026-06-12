---
title: "Groups Question"
date: 2009-06-22
forum: Security
---

### Post by dawiba on 2009-06-22
I have a question about groups and security that has come up because I'm running a firewire interface.

When I was setting up, I went to the FFADO website and followed the instructions there and got to the section about checking permissions. As per the instructions I typed in:

```
ls -al /dev/raw1394
```

I got (and still get) the following:

```
crw-rw---- 1 root root 171, 0 2009-06-22 08:31 /dev/raw1394
```

I didn't get:

```
crw-rw---- 1 root video 171, 0 2008-10-21 00:50 /dev/raw1394
```

which is what the FFADO site suggested might appear.

As far as I could tell, this meant that if I wanted to use firewire, then I had to make myself a member of the 'root' group. I did this by doing System &#8594; Administration &#8594; Users and Groups and adding myself to the 'root' group.

Everything works fine, but because of my lack of Linux knowledge and some things I've read recently, I'm just a bit worried that my computer isn't secure when I'm using firewire. I don't seem to be able to find a definitive answer looking around online and wondered if anyone here could advise if this is okay.

Thanks

---

### Post by thorgal on 2009-06-22
you will need to set up a udev rule for this device node. I am surprised that you get root.root for such a device. Usually, udev comes with a serie of rules for all sorts of devices, and a firewire dev rule should be shipped with it.

try googling around "udev rule /dev/raw1394"

look here: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/369817](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/369817)

---

### Post by dawiba on 2009-06-22
Thanks Thorgal, but that just muddied the waters further for me.

By 'udev rule' I take it you mean something like the ones I've seen like this:

```
50-udev-default.rules:KERNEL=="raw1394*", GROUP="video"
```

I ask because I've seen stuff like this after googling around. In my etc/udev/rules.d, I don't have that one, but I do have one for the cd drive, one for my network interfaces and one for my printer and that's it. I assume I need to create one from scratch. Would that be right?

I looked at the Launchpad page in the hope of doing this, but was completely bemused after reading it two or three times.

I used the 'root' group (based on my understanding of things from the FFADO pages) because I didn't have a 'video' group, or a 'disk' group. For that matter, I didn't have an 'audio' group, but I created one of each by following various instructions I've seen online. So, if I could ask the first question again, is it safe to use the 'root' group?

---

### Post by thorgal on 2009-06-22
then the answer is no. It is not safe to use the root group from the start. But then again, everybody's using root all the time via sudo, without truly understanding what using root really entails (I guess that's what it takes if you want to attract a crowd that grew up with e.g. MS Windows).

Really, consider writing up the right udev rules. The fact that these intermediate unix groups (disk, video, etc) are not created from the start is a decision that belongs to the Ubuntu OS maintainers. In my opinion, it sucks. Maybe the claim is that there are security issues. Could be. But how much does this weigh when you give the newbie the power of sudo ?

By the way, could you post the content of /etc/group ? 
I would also like to know which system you are running (OS and kernel version).

And last but not least
```

dpkg -l udev* | grep ii

```

---

### Post by dawiba on 2009-06-22
Thanks Thorgal

When I type /etc/group I get

```
/etc/group: Permission denied

```

I'll follow your suggestion and take a look around to see how to write my own udev rules.

I'm running Ubuntu 9.04, kernel 2.6.28-13-generic

The last one gives me this:

```
dawiba@dawiba-laptop:~$ dpkg -l udev* | grep ii
ii udev 141-1.1 rule-based device node and kernel event manager
```

I take on board your comments about Ubuntu maintainers not creating these groups from the start, but I'm not conversant with the politics of these decisions and, to be honest, I like it that way.

I also take on board your comments about windows users coming to Linux. I'm trying this coming from using a Mac and have to say that my experience with the Mac is much simpler. I never had to deal with anything at this level using the Mac. The corollary to that is that I don't want to and I suspect this will be true for many others. This doesn't make me (or anyone else) a bad person ;).

Once again, I thank you for your time, patience and willingness to help.

---

### Post by dawiba on 2009-06-22
Okay....

Would I be right in pasting the following into a text document:
```

KERNEL=="dv1394[0-9]*",	NAME="dv1394/%n", GROUP="video"
KERNEL=="video1394[0-9]*",	NAME="video1394/%n", GROUP="video"
```

Then saving this as 50-udev-default.rules in /etc/udev/rules.d

---

### Post by thorgal on 2009-06-22
dawiba, nothing wrong with coming from windows or mac, really :)

coming from unix, you don't take using root lightly. But that's maybe not a problem when you use your machine as an individual desktop :)

Anyway, the /etc/group is a text file, not an executable. So you need to 'cat' it in order to see its content:
```

cat /etc/group

```

if you follow the link I gave above (udev bug), you learn in the last message that there's a fix in a version (udev 141-2+git4a74214).

I don't know if installing this version would help. I don't know if you can get this version at all. Depends on how important it is. If working with your workardound (belonging to the root group) is OK, then just do that until an official udev fix comes around. No need to spend too much time on all this geekerish crap :D

---

### Post by dawiba on 2009-06-22
Okay, I guess

```
KERNEL=="dv1394[0-9]*",	NAME="dv1394/%n", GROUP="video"
KERNEL=="video1394[0-9]*",	NAME="video1394/%n", GROUP="video"
```

would be the wrong thing to do :oops:

I'll read some more about udev in due course.

I see now that /etc/group, lists some of the same groups as those I get to by following the menu to get to Users and Groups.

I did read through to the end of that launchpad page (honestly!), but couldn't install the package because I couldn't find it. There's also mention of a missing '-', but to someone like me, that means nothing as no-one said where it was missing!

All that aside, there are plenty of things that I'm pretty geeky about, but just not computer code. Life's too short for that :wink:

Thanks again for taking the time to help.

---

### Post by thorgal on 2009-06-22
your udev stuff is
```

KERNEL=="dv1394[0-9]*",		NAME="dv1394/%n", GROUP="video"
KERNEL=="video1394[0-9]*",	NAME="video1394/%n", GROUP="video"

```

the corrected one is
```

KERNEL=="dv1394[0-9]*",		NAME="dv1394/%n", GROUP="video"
KERNEL=="video1394-[0-9]*",	NAME="video1394/%n", GROUP="video"

```

video1394 becomes video1394-

:)

---

### Post by cariboo on 2009-06-24
You may want to have a look at this [document]("https://help.ubuntu.com/community/Firewire") , it seems to have been updated, but at one point it stated that the firewire module was complied properly, and to just run as root, eg:

```
gksu kino
```

---

### Post by dawiba on 2009-06-24
> **cariboo907 said:**
> You may want to have a look at this [document]("https://help.ubuntu.com/community/Firewire") , it seems to have been updated, but at one point it stated that the firewire module was complied properly, and to just run as root, eg:

```
gksu kino
```

But isn't that effectively what I'm doing at the moment?

If I understand what I've done with my workaround, then I'm only running as root when I click the start button on Jack Control. Even then, would I be right in thinking that I'm only accessing the 'root' group, not actually running as root?

Sorry if the questions are dumb :redface:

---

### Post by sgx on 2009-06-24
> **dawiba said:**
> But isn't that effectively what I'm doing at the moment?

If I understand what I've done with my workaround, then I'm only running as root when I click the start button on Jack Control. Even then, would I be right in thinking that I'm only accessing the 'root' group, not actually running as root?

Sorry if the questions are dumb :redface:
As I understand it, to run your computer 'as root',  you would in many cases have to restart  your session, and login as root, or interupt a boot process, open a terminal, and login as root, then start the xserver/windowmanager as root.  Until you changed user id, all you do would be 'as root'.
Some distros disable the ability to start a session as root for security reasons.

When you as normal user, start apps, or do things causing processes to run, there are security limitations you will sometimes meet up with, and  you have the option of changing your user id to root, or altering permissions and ownership of certain things, in order to meet or defeat your systems built-in security boundaries. You may run apps as root, and therebye initiate processes that operate with root priveledges, but still the normal user has 'control of the computer', although a determined hacker might exploit breaches in security  that you make knowingly, or by mistake. Not too important for a DAW that is never connected to the net, but a complacent high-roller, always wallowing in the latest greatest wireless bluetooth streaming net apps, might find less money in his bank
account than the ID thief did, and 'all your PINs are belong to us!'
drawn on his splash-screen by the now wealthier hackers.:)

Cheers

---

### Post by dawiba on 2009-06-25
Okay, I completely screwed up the computer trying to write udev rules, so I've done a completely clean install of UbuntuStudio 9.04.

To get my firewire interface working this time, I've created a group called video in 'Users and Groups' and made myself a member. I've checked 'enable raw1394 access' using ubuntustudio controls (even though this gave me a security warning).

When I type

```
ls -al /dev/raw1394
```

I now get

```
crw-rw---- 1 root video 171, 0 2009-06-25 12:46 /dev/raw1394
```

Which matches pretty much the advice on the FFADO website. The good news is that now, when I launch jack control and click play, everything is working.

Can anyone say that this is the way I'm supposed to do this and it's secure to keep working like this?

Many thanks

---

### Post by Sef on 2009-06-25
Moved to Security Discussions.

---

