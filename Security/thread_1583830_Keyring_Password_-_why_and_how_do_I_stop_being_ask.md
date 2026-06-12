---
title: "Keyring Password - why and how do I stop being asked for it?"
date: 2010-09-28
forum: Security
---

### Post by Tootler on 2010-09-28
When I installed Ubuntu (Lucid) on my new computer, As well as the login password I was asked for a keyring password. I gave one, but I am not sure exactly why I need this password. It seems that it was required to let me access the wifi - even though this has its own security code. I found I could stop the system asking for it every time I tried to connect to the internet using wifi by checking a button in the network setup, but when I registered for Ubuntu One, I was again asked for it - twice, once when I registered and again when I set up Tomboy notes sync. Now I get asked for it again every time I switch on. 

I would like to know why the keyring passwords are needed in addition to the login password for a single user computer, which mine is and also how I can stop it asking for this password when I switch the computer on.

One suggestion I have seen is to make the keyring password the same as my login password. If that is the case, then how do I change the keyring password?

TIA

---

### Post by cariboo on 2010-09-28
Does the Password and Encryption keys Window look like this?


This is the way it is setup by default.

---

### Post by Tootler on 2010-09-28
> **cariboo907 said:**
> Does the Password and Encryption keys Window look like this?


This is the way it is setup by default.

Yes, but underneath "**Passwords** login" it has another entry, "**Passwords** default" I found that if I right click on that entry, a drop down menu appears with an option to change password, so I changed the password so that it is the same as the login password.

If you expand the "**Passwords** default" item, there are three entries appear, two saying "Desktop Couch user authentication" and one saying "UbuntuOne token for [https://ubuntuone.com](https://ubuntuone.com)

I'll see if the password change has any effect.

An afterthought. On my previous computer where I had installed Lucid as an upgrade, I was not asked for a keyring password, nor was I on any previous installation (My first Ubuntu install was Intrepid), so this was new to me.

Cheers

Geoff

Geoff

---

### Post by cariboo on 2010-09-28
I've got 1 Lucid install, 1 Karmic install and 4 Maverick installs, I've never had to add a keyring password on the default install.

---

### Post by Tootler on 2010-09-29
> **cariboo907 said:**
> I've got 1 Lucid install, 1 Karmic install and 4 Maverick installs, I've never had to add a keyring password on the default install.

As you will gather from my original message, I was and it's a nuisance.

Changing the keyring password to match the login password has made no difference. I still get asked for the keyring password on startup so I am no further forward.

---

### Post by cariboo on 2010-09-29
Just as an experiment, what if you create a blank password, does it still ask for a password?

---

### Post by Tootler on 2010-09-30
> **cariboo907 said:**
> Just as an experiment, what if you create a blank password, does it still ask for a password?

Tried two things. 

Firstly simply clicking on cancel when asked for the keyring password. That dismissed the password box without any adverse effects. I assume that the system will ask for the keyring password when one is needed.

I then reset the password to blank as you suggested. That was accepted with a warning about anyone with access to my files having access to my stored passwords. On rebooting, I did not get asked for a keyring password. 

I will see what happens now. I think I'm getting there but I'll not mark this as solved yet.

Thanks

---

### Post by M4570D0N on 2010-10-07
This is seriously starting to drive me insane. I never had this issue with Linux Mint 9, but since I did a clean install of 10.10rc on a separate partition, I'm getting this crap constantly. I've been able to get it to stop asking for it to connect to the internet w/ Network Manager, but I still get it at least twice after every log in. 1 instance pops up every time I try to open Evolution, and another is from Ubuntu One but I dont know what specifically is causing that one.

---

### Post by Soul-Sing on 2010-10-07
: [http://ubuntuforums.org/showthread.php?t=1285651&highlight=keyring+pjotr](http://ubuntuforums.org/showthread.php?t=1285651&highlight=keyring+pjotr)
post #8
: [http://ubuntuforums.org/showthread.php?t=1577754](http://ubuntuforums.org/showthread.php?t=1577754)

---

### Post by Tootler on 2010-10-07
I reset the password to blank.

To reset the password to blank:

From Applications/Accessories, select "Passwords and Encryption Keys"

Right click on the line that says "Passwords Default"

Select "Change Password" from the drop down menu.

Leave the new passwords boxes blank and accept the warnings. You will not then be asked for a keyring password at startup.

---

### Post by M4570D0N on 2010-10-07
> **leoquant said:**
> : [http://ubuntuforums.org/showthread.php?t=1285651&highlight=keyring+pjotr](http://ubuntuforums.org/showthread.php?t=1285651&highlight=keyring+pjotr)
post #8
: [http://ubuntuforums.org/showthread.php?t=1577754](http://ubuntuforums.org/showthread.php?t=1577754)

I've seen that already. But why is that work around necessary? I had a keyring on Linux Mint 9, and it was not even the same password as my login password, yet I never had it popping up asking me to unlock the default keyring ever, especially not every session.

---

### Post by cariboo on 2010-10-07
> **M4570D0N said:**
> This is seriously starting to drive me insane. I never had this issue with Linux Mint 9, but since I did a clean install of 10.10rc on a separate partition, I'm getting this crap constantly. I've been able to get it to stop asking for it to connect to the internet w/ Network Manager, but I still get it at least twice after every log in. 1 instance pops up every time I try to open Evolution, and another is from Ubuntu One but I dont know what specifically is causing that one. 

You seem to be suffering from bug #[lpbug]631980[/lpbug].

To see if you have the updated version of gnome-keyring open a terminal and type:

```
apt-cache policy gnome-keyring
```

The result should look something like this:

```
apt-cache policy gnome-keyring
gnome-keyring:
  Installed: 2.92.92.is.2.31.91-0ubuntu4
  Candidate: 2.92.92.is.2.31.91-0ubuntu4
  Version table:
 *** 2.92.92.is.2.31.91-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ maverick/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Arlanthir on 2010-10-08
I have the same issue and I think the problem is that somehow applications add their keys to the "default" keyring instead of the "login" keyring (which is the one that gets unlocked at startup).

I'm not sure why the setting to unlock the "default" keyring doesn't stick, though. I clearly mark it every time and I have everything up-to-date (double-checked with the posted version).


**More secure fix:** 
Delete the "default" keyring (you will lose all your stored passwords).
Right click the "login" keyring and set it as default. Set the network password, the UbuntuOne password, RemoteDesktop, and everything you know you had.

Hope it helps, it worked for me without problems ;)

---

### Post by K_REY_C on 2010-10-11
I just did this and it solved my problem (so far) as well. Thanks.

Just a suggestion: Anyone know a way to migrate passwords from "Default" to "Login"? This might help those who've got lots of them stored up already.

---

### Post by joshh88 on 2010-10-11
awesome fixed mine instantly thanks

---

### Post by repunante on 2010-10-13
> **Arlanthir said:**
> I have the same issue and I think the problem is that somehow applications add their keys to the "default" keyring instead of the "login" keyring (which is the one that gets unlocked at startup).

I'm not sure why the setting to unlock the "default" keyring doesn't stick, though. I clearly mark it every time and I have everything up-to-date (double-checked with the posted version).


**More secure fix:** 
Delete the "default" keyring (you will lose all your stored passwords).
Right click the "login" keyring and set it as default. Set the network password, the UbuntuOne password, RemoteDesktop, and everything you know you had.

Hope it helps, it worked for me without problems ;)


Great help, thank you so much, that issue was driving me crazy.

---

### Post by chome4 on 2010-10-30
What sequence do you have to go through to delete the default keyring? Which menu?

---

### Post by Arlanthir on 2010-10-30
> **chome4 said:**
> What sequence do you have to go through to delete the default keyring? Which menu?

System > Preferences > Passwords and Encryption Keys

Right click on the default keyring, delete
Right click the login keyring, set as default

Notice the window will not update, don't be alarmed if the keyring doesn't disappear when you delete it ;)

---

### Post by cooltd825 on 2010-11-11
I have started another thread, and nobody seems to have answered it, but I set a different password than my login password (for security purposes).  the weird thing is, it prompts me three times to answer the password for the login keyring instead of once.  I can deal with once, but having to type in the same password three consecutive times is a bit ridiculous.  

There's already a bug open on Launchpad.  in the meantime, should I delete the keyring completely and let it reset?

---

### Post by wijit on 2011-01-18
Hi,
I agree that there are so many threads talking about this problem. However this one is most hit-the-point for me. I had 4 different computers with Lucid installed. Each was done at different time but from the same CD. A 3 year old Acer TravelMate 4720 and a 1 week Dell Inspiron n4030 work fine. But the other 2, an 8 year ECS notebook and a 7 year home assembled could not work with Empathy IM Client because of this problem. The first 2 computers mentioned above have 1 user each where as the other 2 have multiple users. I have 2 questions and someone who know can (actually please) take me from the dark.
1. Does the problem relate a pop-up bar that has 3 buttons, namely, remember this password, never for this site and ask me later or not for this time (either of these-forgive me for not clear)?
2. Does this problem relate whether the computer has multible users?
Thanks for reading.

---

### Post by karmila on 2011-03-10
> **Arlanthir said:**
> System > Preferences > Passwords and Encryption Keys

Right click on the default keyring, delete
Right click the login keyring, set as default

Notice the window will not update, don't be alarmed if the keyring doesn't disappear when you delete it ;)

Hi, which part that I supposed to delete?
[http://i980.photobucket.com/albums/ae286/jasbutut/PasswordsandEncryptionKeys_002.jpg](http://i980.photobucket.com/albums/ae286/jasbutut/PasswordsandEncryptionKeys_002.jpg)

I have only that one and under other tabs are empty.

---

### Post by Arlanthir on 2011-03-10
> **karmila said:**
> Hi, which part that I supposed to delete?
[http://i980.photobucket.com/albums/ae286/jasbutut/PasswordsandEncryptionKeys_002.jpg](http://i980.photobucket.com/albums/ae286/jasbutut/PasswordsandEncryptionKeys_002.jpg)

I have only that one and under other tabs are empty.

Then you shouldn't have to delete anything :)

---

### Post by karmila on 2011-03-10
> **Arlanthir said:**
> Then you shouldn't have to delete anything :)

I'm okay then, but sometimes I get a pop up keyring notification that I've never got before :confused:

---

### Post by cariboo on 2011-03-10
Right click login, and select change password, then give it a blank password.

---

### Post by karmila on 2011-03-15
> **cariboo907 said:**
> Right click login, and select change password, then give it a blank password.

Thanks! :D

---

### Post by Kixtosh on 2011-04-05
I've started getting this pop-up too, which I have never had before. It seems to be something to do with wireless networking, since if I disable Network Manager in the Startup Applications (from the Preferences Menu), I don't get the pop-up.

I can only see my login profile when I check Password and Encryption Keys from the Accessories menu. If I right click on my login, the Set as default is grayed out (but my laptop still starts up without asking for a password, as long as the Network Manager is disabled, as described above).

---

### Post by Kixtosh on 2011-04-05
Hmmm ... this might be a Chromium browser related issue. Here's what I did:

1) Disabled all Keyring related startup applications. No change.
2) Disabled Network Manager on startup. No pop-up, but no network either!
3) Enabled Network Manager and Keyring applications: pop-up returned.
4) Right clicked on wireless to Edit Connections, unchecked box Available to all users.
5) Right clicked on wireless to Edit Connections and checked box Available to all users.

Now what I'm getting is:

- No pop-up when starting up.
- No pop-up when starting Chromium.
- Pop-up appears when going to sites requiring a login and password, whether saved or not.
- Pop-up does not appear when using Firefox 4, even on these same sites.

I'll test this again with Firefox only in a minute, so if I don't post back within five minutes, it means it's working with no pop-up for Firefox, but is not working for Chromium, as described above.

---

### Post by Kixtosh on 2011-04-05
Yup, Chromium seems to be my problem. If I just click cancel, I can get to log in to my accounts (but I'll be asked for the Keyring every time, and have to click cancel every time). If I open the Chromium tools menu and check my Personal Stuff in Preferences: it lists no saved passwords. If I enter my login Keyring password the next time I'm prompted to do so, and then return to my Personal Stuff in Preferences: it now lists all my saved browser passwords.

Any ideas for a fix?! Maybe it's time for a new thread on this related, but slightly different topic.

---

### Post by uRock on 2011-04-05
Requiring a password to login instead of logging in automatically should fix you issues.

---

### Post by Kixtosh on 2011-04-05
> **uRock said:**
> Requiring a password to login instead of logging in automatically should fix you issues.If I switch to FF, I'll probably do that, since I understand that FF encrypts login and password information, whereas Chromium does not (unless this has changed, from what I read). I don't mind having to enter a password to login when booting, if I can feel safe saving all login and password information once my laptop is up and running.

That still wouldn't explain why everything works in FF, and no longer works in Chromium (it did until a few weeks ago).

---

### Post by Exhack on 2011-04-21
I just want to place on record my frustration that this whole keyring security stuff is imposed by the programmers. For reasons I don't know I started getting this prompt after trying to uninstall Ubuntu One, which I didn't want. 

The consequences of this were:

1) I get the prompt..and I have no idea what my keyring password is or how to find it.

2) I now have to give a password whenever I want to send mail from Evolution.

3) I cannot access my VPN address. (I could try reinstalling it but that's another chore).

I've looked at the Seahorse "manual" but it gets off to a bad start by referring to PGP and SSH keyrings as if all the world knew what they were. I don't

I can see that office workers or security maniacs might want/need to keep prying eyes off their stuff, but nobody else uses my machine and I don't care.

I am seriously considering formatting my Ubuntu partition and starting over.

---

### Post by cariboo on 2011-04-21
@Exhack, I'd suggest you read this complete thread, as there are solutions to your problem in it, no need to do a complete re-install.

---

### Post by ErikNJ on 2011-04-21
Instead of creating a blank key-ring password, you may also just make the "login" key-ring your default.  Then, once you login, all of the "defaults" will default to your "login" keyring.

---

