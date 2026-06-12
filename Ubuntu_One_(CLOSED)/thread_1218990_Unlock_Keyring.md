---
title: "Unlock Keyring"
date: 2009-07-21
forum: Ubuntu One (CLOSED)
---

### Post by irv on 2009-07-21
Ever since I installed Ubuntuone at boot up I get this message:
Unlock Keyring
> This Application 'Ubuntuone-client-Applet' (/usr/bin/python2.6) wants access to the default keyring, but it is locked.
The options are Deny or OK. 
Is this something normal? And it is something I should worry about for security reasons?

---

### Post by zekopeko on 2009-07-21
This is completely normal.
A keyring is where Ubuntu stores password from applications that support the keyring. If you use Firefox it's similar to the Master password option so that you don't have to re-type your different password over and over.
You can OK-it.

---

### Post by irv on 2009-07-21
> **zekopeko said:**
> This is completely normal.
A keyring is where Ubuntu stores password from applications that support the keyring. If you use Firefox it's similar to the Master password option so that you don't have to re-type your different password over and over.
You can OK-it.

Thanks that answered my questions.

---

### Post by cariboo on 2009-07-21
If you disable automatic login, like they've done in Karmic, the keyring doesn't ask for a password, as you've just logged in. :)

---

### Post by FatalChaos on 2009-07-25
They haven't disabled auto login in karmic. When I installed karmic they still asked me if I wanted to use auto login. I said yes, which is a mistake because what they have done is disable the login manager, and so far I haven't found a way to revert back to a regular login.

---

### Post by zekopeko on 2009-07-25
> **FatalChaos said:**
> They haven't disabled auto login in karmic. When I installed karmic they still asked me if I wanted to use auto login. I said yes, which is a mistake because what they have done is disable the login manager, and so far I haven't found a way to revert back to a regular login.

Not at my Linux box but you might try looking in the gconf-editor under gdm.
or search in the karmic sub forum.

---

### Post by volkswagner on 2009-07-26
> **FatalChaos said:**
> They haven't disabled auto login in karmic. When I installed karmic they still asked me if I wanted to use auto login. I said yes, which is a mistake because what they have done is disable the login manager, and so far I haven't found a way to revert back to a regular login.

I also enabled auto login.  There is an option to enable/disable it in

<System> <Administration> <Login Window> then select the Security tab.

---

### Post by zekopeko on 2009-07-26
> **zekopeko said:**
> Not at my Linux box but you might try looking in the gconf-editor under gdm.
or search in the karmic sub forum.

Scratch that. Didn't read carefully.
There is no Login Window applications in Karmic. The GDM is a new code base and they didn't provide a similar tool.

Anyway this shouldn't be discussed here but in the Karmic forum.

---

### Post by irv on 2009-07-26
> **zekopeko said:**
> Scratch that. Didn't read carefully.
There is no Login Window applications in Karmic. The GDM is a new code base and they didn't provide a similar tool.

Anyway this shouldn't be discussed here but in the Karmic forum.

Yes I agree, I started this thread out in Ubuntuone because it was not a Karmic issue.
For the record I am back to loging in and the Unlock Keyring went away. If I do the auto login it comes back. So either way I have to login. to unlock the keyring.

---

### Post by xagapiou on 2009-09-21
> **irv said:**
> Yes I agree, I started this thread out in Ubuntuone because it was not a Karmic issue.
For the record I am back to loging in and the Unlock Keyring went away. If I do the auto login it comes back. So either way I have to login. to unlock the keyring.
It is true that this behaviour is not a karmic only behaviour. In jaunty it exists also. 

I have managed with the network asking for permission to access the keyring by enabling the "Available to all" option. Is there a similar one in ubuntuone or a gdm option for ubuntuone to autounlock the keyring??

---

### Post by community nerd on 2009-09-22
I get it every time I type my wep key. It can't remember it becuase my password does not work. It is not the same as my login password. Should I delete the default keyring and add a new one with my log-in password?

---

### Post by joshuahoover on 2009-09-25
> **community nerd said:**
> I get it every time I type my wep key. It can't remember it becuase my password does not work. It is not the same as my login password. Should I delete the default keyring and add a new one with my log-in password?

Yes, I would delete your default keyring if you can't remember the password. Chances are you changed your login password at one point and it wasn't kept in sync with the keyring password.

-Joshua

---

### Post by psypher on 2009-11-25
Joshua, deleting your default keyring does not work. And the keyring password was never different from the login password, default fresh install of karmic.

Very annoying! Do you have any other suggestions on a permanent fix? Should we log a bug? Although I am not convinced this is a U1 issue but a karmic issue as I have the keyring password pop-up for evolution alarm notifier  before I setup or started U1 for the 1st time.

Thanks

---

### Post by joshuahoover on 2009-11-25
> **psypher said:**
> Joshua, deleting your default keyring does not work. And the keyring password was never different from the login password, default fresh install of karmic.

Very annoying! Do you have any other suggestions on a permanent fix? Should we log a bug? Although I am not convinced this is a U1 issue but a karmic issue as I have the keyring password pop-up for evolution alarm notifier  before I setup or started U1 for the 1st time.

Thanks

Hi Psypher,

This is strange (and, if you're experiencing it, annoying!) Deleting the keyring doesn't prompt you to reset the password? This should work. How did you try to delete your keyring password? From a terminal session you can do:

sudo rm -rf ~/.gnome2/keyring

Then restart and after login you should get a prompt to reset your keyring password.

Thank you,

Joshua

---

### Post by psypher on 2009-11-26
oh no, it did prompt me to recreate the keyring, that was fine. Recreated, ensured it's the same as the login password(which was the same from the start anyway so that is no the problem). the command you provided now did nothing though. are you not having this issue on a fresh install of karmic, after updates?

---

### Post by joshuahoover on 2009-11-30
> **psypher said:**
> oh no, it did prompt me to recreate the keyring, that was fine. Recreated, ensured it's the same as the login password(which was the same from the start anyway so that is no the problem). the command you provided now did nothing though. are you not having this issue on a fresh install of karmic, after updates?

I have not had this problem on any of my Karmic installs, fresh or upgrades. I set my keyring password to not prompt me once I set it. The first time you set the keyring password, I believe it provides a checkbox to remember (or not prompt) you for the password going forward.

Thank you,

Joshua

---

### Post by psypher on 2009-12-12
i have never seen that check box and do not know where to force it. PLEASE can anyone tell me how and where to find this check box or force ubuntu to ask for this check box. is this a bug???

---

### Post by joshuahoover on 2009-12-15
> **psypher said:**
> oh no, it did prompt me to recreate the keyring, that was fine. Recreated, ensured it's the same as the login password(which was the same from the start anyway so that is no the problem). the command you provided now did nothing though. are you not having this issue on a fresh install of karmic, after updates?

My apologies, the command I should have provided is: sudo rm -rf ~/.gnome2/keyrings

I tried that command on a test Karmic environment I have and was prompted to reset the password. After I rebooted the environment and logged in, I was prompted to enter my password and had an "Automatically unlock this keyring when I log in." check box under the password field. I'm attaching a screenshot of what I was presented with. I hope this helps and works for you!

Thank you,

Joshua

---

### Post by actetylcholine on 2009-12-31
I have the same with the ubuntuone client requesting access to the keyring everytime the laptop is booted. Unfortunately I don't get the checkbox Joshua sees. Any idea how I can give the ubuntuone-client access to the keyring automatically? I've attached a screenshot of the dialogue box (without the checkbox).

Thanks, Thomas

---

### Post by psypher on 2010-03-25
I re-installed my PC and the check box to save the password appeared. Still no way of getting it to display if you did not tick that box this 1st time.

Bug?

---

### Post by badaveil on 2010-03-25
> **joshuahoover said:**
> My apologies, the command I should have provided is: sudo rm -rf ~/.gnome2/keyrings

I tried that command on a test Karmic environment I have and was prompted to reset the password. After I rebooted the environment and logged in, I was prompted to enter my password and had an "Automatically unlock this keyring when I log in." check box under the password field. I'm attaching a screenshot of what I was presented with. I hope this helps and works for you!

Thank you,

Joshua

Hi Joshua

Just wanted to share my experience:I'm on Karmic and have a wireless card in my pc at the same time wired to a wireless modem. I took your advice with "sudo rm -rf ~/.gnome2/keyrings", after a reboot, yes, the default keyring password dialog box doesn't exist anymore. What comes up instead is the wireless network security dialog box. If I pull the wire off the modem, I definitely need to enter my wireless password but if I had the wire connected to the modem, I get auto logged onto the internet. Because of that modem-wireless card setup, Ubuntu doesn't know which internet access I want so the wireless network security dialog box appears when I start the computer, it's OK, at least I understand now why it happens.;)

---

### Post by irv on 2010-06-02
I thought I would just do a quick update on this thread. This problem was found in karmic, jaunty and also Lucid Lynx. It's not really a problem, it just means if you use Ubuntu One, you need to login at boot up if you don't want to keep unlocking the kernel.

---

