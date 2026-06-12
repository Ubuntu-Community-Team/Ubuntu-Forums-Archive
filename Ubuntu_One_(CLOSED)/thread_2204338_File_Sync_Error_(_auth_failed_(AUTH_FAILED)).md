---
title: "File Sync Error ( auth failed (AUTH_FAILED))"
date: 2014-02-07
forum: Ubuntu One (CLOSED)
---

### Post by grantmcduling on 2014-02-07
Hi 

I am running Ubuntu 12.04 and Ubuntu One.. I have the settings set for default settings. Today I got the above message the sync failed. Any ideas?

---

### Post by fecus on 2014-02-08
Hello,

My Ubuntu One do the same. I tried reinstall, but nothing happened. Ubuntu 12.04.

---

### Post by deadflowr on 2014-02-08
I noticed this just yesterday.
Though my files were syncing fine, the UbuntuOne app kept showing this error.
the solution was to reinstall the certs
```
sudo apt-get install --reinstall ca-certificates
```
then reboot.
Also, you'll need to logout of UbuntuOne.
It's hard to figure out how, but a way to log out is to open seahorse and fine the entry for UbuntuOne and delete it.
It worked like a charm for me, but I would advise anyone to see if you can temporarily backup any files in case something happens that causes errors and possible file corruption/deletion.

Good Luck.

---

### Post by fecus on 2014-02-09
I did reinstall certificates: 0 added 0 removed.

I have nothing in seahorse. It said ** Message: failed to refresh: Couldn't communicate with key ring daemon

ps ax | grep 13580
13580 pts/1    Sl     0:00 gnome-keyring-daemon
13592 pts/1    S+     0:00 grep --color=auto 13580

gnome-keyring-daemon is running

What happened?

---

### Post by fecus on 2014-02-09
[This]("http://ubuntuforums.org/showthread.php?t=1459804") topic helps me.
The fifth post.

---

### Post by deadflowr on 2014-02-09
> **fecus said:**
> 
It said ** Message: failed to refresh: Couldn't communicate with key ring daemon


That seems to be a completely different error.
Did you go dig through this list to see if that error comes up
[https://one.ubuntu.com/help/faq/](https://one.ubuntu.com/help/faq/)
If not, maybe use the contact us link
[https://one.ubuntu.com/help/contact/](https://one.ubuntu.com/help/contact/)

I haven't seen that error, so it might be something you've come across through your own fruition.

---

### Post by fecus on 2014-02-09
Something interesting: in seahorse there isn't any registration. I start it from root terminal.
I open Passwords and Encryption Keys program from Applications and there are many registration. I can't delete registration of Ubuntu One via seahorse but I can via Passwords and Encryption Keys program. I thought these are same.

No everithing work in Ubuntu 12.04.[-o<

But I see in web login, the system forget my other machine at work which run win7. I will try to repair that on Monday....

---

### Post by Irihapeti on 2014-02-09
Unless I'm much mistaken, Passwords and Keys *is* seahorse.

Seahorse/passwords and keys is meant to be run as an ordinary user. If you're running seahorse as root, then you won't be able to do anything with your user keys.

You should be able to confirm this by running seahorse from an ordinary user terminal.

---

### Post by gmcduling on 2014-02-09
Many thanks for the tips and suggestions. Turns out updating the signatures and rebooting did the trick.

---

### Post by Irihapeti on 2014-02-09
Could you please mark the thread as solved? Thanks

---

### Post by grantmcduling on 2014-02-09
Sorry, seems it didn't fix my problem. Back to square one. I tried closing down my subscription and starting a new one but that didn't work either as it took me to my original subscription. I think I will stick with dropbox as it just works.

---

### Post by deadflowr on 2014-02-09
What about this
[https://one.ubuntu.com/help/faq/what-should-i-do-if-authentication-fails-auth_failed-state/](https://one.ubuntu.com/help/faq/what-should-i-do-if-authentication-fails-auth_failed-state/)

---

### Post by linuxgeoff on 2014-02-10
Seems you are not alone.  I have same problem after Ubuntuone working well for two years.  It now fails with this same error from both my ubuntu machines and my windows PC.  My account all seems to be correct, I have reinstalled certificates, double checked clocks, stopped & restared ubuntu one, and reloaded the app on the windows machine.  I'm awaiting a response from the help desk and will post back anything I learn

---

### Post by aquatabby on 2014-02-15
I'm using saucy 64-bit, and had exactly the same issue. Ubuntu One had been working absolutely fine for months, and then suddenly I get an AUTH_FAILED error. I tried all sorts of things, including de-authorising the machine from the web interface, changing my password, and re-installing the certificates. Nothing worked.

In the end, what *seems to have* worked is loading seahorse, removing the Ubuntu One entry, then starting Ubuntu One and going through the registration process again. The first time I started Ubtuntu One, this didn't work - it hung on 'Gathering information' until I killed it. But, when I started Ubuntu One after that, it seems (so far) to be fine.

Very odd that this should happen for no reason whatsoever. I'm sure this is affecting other people, I'd be interested to know the reason.

---

### Post by leggett-matthew on 2014-02-15
I'm getting this also on 13.04.  Been working fine since original install and suddenly a few days ago it packed up.  Exact same error and now files are no longer sync'ing.

I've tried removal of the U1 client through the software centre, reboot and reinstallation generating new certificates but no joy.  The U1 client shows my local device as a known device and also reports it through the web UI.  It's picking out my paid subscription also so that aspect is all working.  I just don't know why I'm getting this (auth failed AUTH_FAILED)) error with the client.

Any suggestions?

---

### Post by Irihapeti on 2014-02-15
My suggestion would be to leave a message at [https://one.ubuntu.com/help/contact/](https://one.ubuntu.com/help/contact/)

Note that they don't seem to be the fastest at responding. :(

---

### Post by grantmcduling on 2014-02-18
Sorry, turns out the problem still persists. So I am back to square one. Don't really know what I can/should do next. One the Ubuntu One web page, even the FAQ 
[LIST]
[*][Why am I getting an authentication failed error?]("https://one.ubuntu.com/help/faq/why-am-i-getting-an-the-authentication-failed-error-on-windows-225/") could not find the page. Seems it has been removed. So perhaps it's not just me having this problem.
[/LIST]

---

### Post by grantmcduling on 2014-02-24
Sorry, still not syncing so will wait and see if Ubuntu fix. Seems to me that it is a bug in their system. I have tried everything suggested to no avail. Patience is the key. Or dropbox.

---

### Post by mattdt on 2014-03-07
I've had this File Sync Error ( auth failed (AUTH_FAILED) for about a month now. I've reset the clock, reinstalled certificates, reinstalled Ubuntu One, checked my storage capacity on Ubuntu One, and made sure my account is current and active. Nothing has corrected the problem on the desktop application of Ubuntu One. I've sent several email support questions to Ubuntu support but never get a reply except an auto-response they will get back to me. I can only conclude it's a bug on Ubuntu One's end. Guess will have to find another storage option - at least for now. Super annoying!

---

