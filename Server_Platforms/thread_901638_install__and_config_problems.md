---
title: "install  and config problems"
date: 2008-08-26
forum: Server Platforms
---

### Post by Low_E on 2008-08-26
I am working, as a volunteer, on a school-network. This network consist of about 100 pc's (running Win2K and WinXP) and a server.

The server we had, a home-made-linux-from-scratch-thing, gave us many problems. It was running a domain for our windows-clients but stalled frequently, making it impossible for all pc's to log in on the domain and run netwerk-shared-applications.
Also the person that made and configured this server, doesn't help us no longer.

I would like to switch to a new distro, where we can tune everything ourselves, based on a stable platform and that is why I installed Ubuntu Server on our server-pc. (I previously switched the hard drive, so that I can always return to the previous situation in case of disaster.

My problem is that I am only an amateur in IT, have some experience in WInows-networking, but am very noob in Linux ... and I'm stuck now.
The Ubuntu-server was installed, but only detected 1 networkadapter in stead of the two there are.
So I wanted to add this eth0 and runned "vi /../interfaces"
but wasn't able to.

I am NOT looking for exact answers. Just some good directions, so that I can find the solutions myselve are ok, + I learn most this way ... but unfortunatly Time is running short and I do not have the time to do extensive research.
SO please give me some tips:

first question: how can I override the read-only-settings of these conf-files?

second: can I ad this extra eth-card, just by adding the settings in de interfaces-file?
The two eth-cards are identical (offc not the MAC-address), so it should not be a problem about drivers.

third: Alldough I selected the correct country and language-settings in teh installation-screens, the server now suddenly runs a different keyboard-layout.
I got used to typing QWERTY on an AZERTY-keyboard but it is not very easy .. AND .. I am now unable to log in on the root-account (it has a difficult password with é"#-@ things)
How can I correct this?

Any help will be GREATLY appreciated!


Ludo

ps: strange thing, alldough I encoutered many problems so far, I really like the no-nonsens way of functioning of Linux.
I really want to make this work and learn a lot from it.

---

### Post by cdenley on 2008-08-26
> 
how can I override the read-only-settings of these conf-files?

You need need edit configurations as root using the sudo command.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
```

sudo nano /etc/network/interfaces

```

> 
can I ad this extra eth-card, just by adding the settings in de interfaces-file?

The network adapters must be found and assigned in order to configure it in /etc/network/interfaces. To see all available network adapters, run this command
```

sudo ifconfig -a

```

> Alldough I selected the correct country and language-settings in teh installation-screens, the server now suddenly runs a different keyboard-layout.
```
sudo dpkg-reconfigure console-setup
```

---

