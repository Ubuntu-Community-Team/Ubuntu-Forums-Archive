---
title: "ubuntu one and lxde/lubuntu"
date: 2010-05-22
forum: Ubuntu One (CLOSED)
---

### Post by cannonfodder on 2010-05-22
After experiencing problems on some hardware, I finally managed to install Lubuntu on one of my machines and its a winner.

Only thing missing is Ubuntu One :)

Have installed ubuntuone-client (from default repos & then from ppa) but nothing appears in the menu and can't find any other way of launching the client.

Am I missing something here?

Can anybody report a working install of Ubuntu One under either Lubuntu or Ubuntu LXDE or Ubuntu + Openbox for that matter?

---

### Post by joshuahoover on 2010-05-24
> **cannonfodder said:**
> After experiencing problems on some hardware, I finally managed to install Lubuntu on one of my machines and its a winner.

Only thing missing is Ubuntu One :)

Have installed ubuntuone-client (from default repos & then from ppa) but nothing appears in the menu and can't find any other way of launching the client.

Am I missing something here?

Can anybody report a working install of Ubuntu One under either Lubuntu or Ubuntu LXDE or Ubuntu + Openbox for that matter?

I haven't tested this configuration myself. One way to test things from a command line is to run the following:

```
u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```Thank you,

Joshua

---

### Post by phillw on 2010-05-24
Hi,

I have no knowledge of ubuntu one, but will be happy to either [list]
Use my existing lubuntu install.
Set up a partition with lubuntu on it that can be used to get a set of instructions written whilst not endangering my main lubuntu installation.[/list]

I'll tag myself for update alerts to this thread, let me know if I can help out in any way.

Regards,

Phill.

---

### Post by Plumtreed on 2010-05-26
Ubuntu One goes OK for me in Lubuntu. Installed from synaptic without issue but I only use it for 'storage'

Also goes in PeppermintOS!

---

### Post by ChiVampir on 2010-09-08
Know this is a old post but:

> **Plumtreed said:**
> Also goes in PeppermintOS!

How did you get it to work? I'm still trying but I even after installing ubuntuone-client  and all it's dependencies I cant find it in the menues nor get it to sync with my ubuntu one account.

So did someone manage to get Ubuntu One to show up in the menu in Lubuntu or other distros based on it?

---

### Post by duanedesign on 2010-09-08
try using the u1sdtool from the commandline. You can see all the commands with:

```
man u1sdtool
```

To connect:

```
u1sdtool -c
```

To quit:

```
u1sdtool -q
```

Status:

```
u1sdtool -s
```

---

### Post by Plumtreed on 2010-09-11
> **ChiVampir said:**
> Know this is a old post but:



How did you get it to work? I'm still trying but I even after installing ubuntuone-client  and all it's dependencies I cant find it in the menues nor get it to sync with my ubuntu one account.

So did someone manage to get Ubuntu One to show up in the menu in Lubuntu or other distros based on it?

Recognized this post and from memory, in Peppermint, I just used Synaptics and it seemed to work without any probs???

I tried it again with the Ice version of Peppermint and it also worked. If you are still interested, reply to this and we can at least confirm all the items 'ticked' in Synaptics.

---

### Post by repunante on 2010-10-02
> **ChiVampir said:**
> Know this is a old post but:



How did you get it to work? I'm still trying but I even after installing ubuntuone-client  and all it's dependencies I cant find it in the menues nor get it to sync with my ubuntu one account.

So did someone manage to get Ubuntu One to show up in the menu in Lubuntu or other distros based on it?

I tried today Ubuntu One in Kubuntu and I couldn't make it work. But I don't think it is a problem of installation, I think it is a problem in the way Ubuntu One connects with the computer, or something like this.
In [here]("https://wiki.ubuntu.com/UbuntuOne/FAQ") in points 1.1 and 1.2 they explain how to add the computer to Ubuntu One and in both it is the same way, you have to delete the password in the keyring. I managed to do it when I upgraded from Ubuntu 10.04 to Ubuntu 10.10 but today I couldn't manage to do it in Kubuntu 10.10, the Kwallet thing was too much for me.

Hope this helps.

---

### Post by bailout on 2010-10-03
I use ubuntuone in Lubuntu. You need to install ubuntuone-client-gnome to get the menu entry and gui.

---

