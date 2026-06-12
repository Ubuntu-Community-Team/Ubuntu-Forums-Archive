---
title: "Seahorse.."
date: 2012-04-21
forum: Security
---

### Post by rookcifer on 2012-04-21
Seahorse is terrible.  What exactly is its purpose nowadays?  It seems to have lost a lot of functionality it used to have.  Now when I launch it, all it does is list my keys.  I cannot create new keys.  I cannot encrypt or decrypt files.  All I can do is look at my keyring.  In the past it allowed you to create keys, and it also fit into the Ubuntu menu so that you could right-click a file and hit "encrypt."  This functionality is completely gone now.  So, again, what is the point of it?

But the biggest problem with it is that it caches my GPG passphrase indefinitely and there's no way to turn that off.  This is a huge security risk.  I leave my machine on 24/7 and I do *not* want my gpg key to be unprotected 24/7.

I am thinking of uninstalling it and just using gpg-agent.

---

### Post by ottosykora on 2012-04-22
I was asking this here few times, but got somehow confusing answers.

[http://ubuntuforums.org/showthread.php?t=1928660](http://ubuntuforums.org/showthread.php?t=1928660)

see answer #10

but the integration of for example to the text editor is not given at the moment.

>But the biggest problem with it is that it caches my GPG passphrase indefinitely and there's no way to turn that off. This is a huge security risk. I leave my machine on 24/7 and I do *not* want my gpg key to be unprotected 24/7.<

this is then th biggest problem I can see, it has to follow the settings in the conf and not any junk transfered one way from the gui.

---

### Post by rookcifer on 2012-04-22
> **ottosykora said:**
> I was asking this here few times, but got somehow confusing answers.

[http://ubuntuforums.org/showthread.php?t=1928660](http://ubuntuforums.org/showthread.php?t=1928660)

see answer #10

but the integration of for example to the text editor is not given at the moment.

>But the biggest problem with it is that it caches my GPG passphrase indefinitely and there's no way to turn that off. This is a huge security risk. I leave my machine on 24/7 and I do *not* want my gpg key to be unprotected 24/7.<

this is then th biggest problem I can see, it has to follow the settings in the conf and not any junk transfered one way from the gui.

Yeah the only way you can clear the password cache is to logout.  Then once you log back in and get prompted to enter your GPG password (say for an e-mail) you can then select how long to cache the passphrase.  However, this shouldn't be necessary -- there should be a button to press to clear the password instantly and there should be a menu option available at all times that lets you select how long to store it.

But, again, Seahorse sucks.  It has got no functionality.  I am not even sure what it's for.

---

### Post by ottosykora on 2012-04-22
could you get those seahorse-nautilus installed?

I have just at the moment no 11.10 or 12.04 here so can not test, on my current computer I have still the 11.04 with all the luxury.

In fact the passphrase latency should be just in the conf and yes it should have an acces to it all the time. I mean if there is a gui for it it should be able to write and rewrite all the settings at any time and not only those which the dev apparently understood and found interesting just at the moment when he wrote the gui commands.

Anyway earlier I was told that things like file encryption in the nautilus will come back at least.

But it was supposed to work somehow different then with the right click menu or what.

---

### Post by ottosykora on 2012-04-22
found some more threads

[http://ubuntuforums.org/showthread.php?t=1890317&highlight=seahorse](http://ubuntuforums.org/showthread.php?t=1890317&highlight=seahorse)

[http://ubuntuforums.org/showthread.php?t=1863898&highlight=seahorse](http://ubuntuforums.org/showthread.php?t=1863898&highlight=seahorse)

---

### Post by rookcifer on 2012-04-22
> **ottosykora said:**
> could you get those seahorse-nautilus installed?

There is no such package in the repos anymore.

> In fact the passphrase latency should be just in the conf and yes it should have an acces to it all the time. I mean if there is a gui for it it should be able to write and rewrite all the settings at any time and not only those which the dev apparently understood and found interesting just at the moment when he wrote the gui commands.

The GUI in Seahorse is wothless.  It has like no options to do anything.  All you can do is view your keyring.  It's stupid and pointless.

> Anyway earlier I was told that things like file encryption in the nautilus will come back at least.

Hopefully that is true.  I personally don't care about the file encryption option since I am fully comfortable with the command line.  What annoys me is the inability to set the password cache time.  And if I try to remove seahorse (to use gpg-agent), it wants to take ubuntu-desktop with it.

---

### Post by ottosykora on 2012-04-22
either they were using the special repo:

sudo add-apt-repository ppa:mdeslaur/testing 
sudo apt-get update
sudo apt-get install seahorse-plugins

or it should be called now nautilus-seahorse or seahorse-nautilus, does this ppa exist?

I was told somewhere that this was the developemnt of the version for the gnome3 etc and would work on 12.04

---

### Post by ottosykora on 2012-04-22
do you have gpg 2.x or gpg 1.x? 

if gpg2.x one could use this GPA, which does unfortunately not support gpg 1.x on the other side thus all can lack some means of compatibility to older pgp versions.


This GPA does not handle all perfect, is also kind of MickeyMouse Picture GUI, but might do the job with file encryption at least.

---

### Post by ottosykora on 2012-04-22
got the advise above that there might be something in the univese repo.

Is it what you installed? If so then it is not what they promissed few months ago.

[http://ubuntuforums.org/showthread.php?t=1928660&page=2](http://ubuntuforums.org/showthread.php?t=1928660&page=2)

#12

---

### Post by l3lackEyedAngels on 2012-05-02
I found this in the Ubuntu Software Center:
[IMG]http://farm8.staticflickr.com/7116/6991206892_cd1e3deacc_b_d.jpg[/IMG]

I already had Passwords and Keys installed. When I installed the other three and restarted, I got two new icons on the Unity panel and options to encrypt and sign in the right click menu. One of the icons is named Verify Signature and the other is Decrypt File. Clicking on either of the icons appears to do nothing. When I use the right-click menu, it takes a little while but eventually I get a prompt asking me either where I want to save the signature or to which key would I like to encrypt the file. When I sign a file, seahorse-nautilus doesn't clearsign it. It saves the signature as an unreadable .sig file. I haven't tested the encryption option because it won't let me encrypt a file to one of my own private keys.

So, as it stands, I am unaware of a good GUI for GnuPG for Ubuntu. :(

---

### Post by ottosykora on 2012-05-03
and is there any sort of configuration? I mean the detached signature well this might be ok, but is it pgp signature or something completely different?

Encrypt file, well you have to encrypt it to public key not private key in fact.

---

### Post by ottosykora on 2012-05-03
> **rookcifer said:**
> Yeah the only way you can clear the password cache is to logout.  Then once you log back in and get prompted to enter your GPG password (say for an e-mail) you can then select how long to cache the passphrase.  However, this shouldn't be necessary -- there should be a button to press to clear the password instantly and there should be a menu option available at all times that lets you select how long to store it.

But, again, Seahorse sucks.  It has got no functionality.  I am not even sure what it's for.

I tried to enter some of the switches to the gpg-agent.conf as per man gpg-agent, but somehow it seems to have no effect at all. The stupid agent behaves all time the same.
I was entering the switch lines to the one in my home / gnupg directory.
Did you have any success in changing the behavior of the gpg-agent?

---

### Post by l3lackEyedAngels on 2012-05-03
> **ottosykora said:**
> and is there any sort of configuration? I mean the detached signature well this might be ok, but is it pgp signature or something completely different?

Encrypt file, well you have to encrypt it to public key not private key in fact. 
No, I am in aware of any new configuration options. I am pretty sure that it's a PGP signature. I will try to verify it with the command line later. You're right, but it wouldn't let me encrypt a file to the public key that corresponds to one of my private keys.

Enigmail in Thunderbird worked relatively well before the update to 12.04 (although my pass-phrase would get stored for who knows how long). I have yet to test that.

---

### Post by ottosykora on 2012-05-03
in the enigmail there is a separate entry in the GUI for time to store the passphrase.

But to me it looks like the gpg-agent running in the background is taking over and doing his preset 10 minutes.

Does enigmail still work normal so far?

The sig file, is it ascii armoured or is it binary?
If just .sig it is supposed to be the binary pgp signature in raw state.
Is it asking you any Q about if you want it to be text output or not?

---

### Post by ottosykora on 2012-05-17
So now I had finally time to upgrade to 12.04

During the upgrade procedure, the installer wanted remove many things, but I stopped this and so I have all previous parts which do not directly cause any collisions with other software.

I found, that the functionality of the seahorse plugin for nautilus is still present and works fine. Right click menu for encryption is working ok.

The key management was never very good, and ist is not better now, bbut it works.

The only things which lost now, is the text encryption in the gedit, the extension for that is gone.


The functions of the gpg-agent can be partially controlled from the gconf configuration editor. Under seahorse, one can disable the passphrase cache or set the time out which is 600s by default.

---

### Post by PDA1 on 2012-07-09
Exactly how do I change the amount of time a passphrase is stored?

Seahorse has no option to do it.

I'm running 12.04...in GnomeClassic desktop and use Thunderbird 13 for email.  No, Enigmail won't clear the passphrase as it says I'm using gnpg-agent...or something similar to that.

I'm pretty stupid about this sort of thing so if you could explain what file I should edit and what to add that would be very helpful.

Thanks

---

