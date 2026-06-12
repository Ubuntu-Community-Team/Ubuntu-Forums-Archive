---
title: "Passwords and Keyrings"
date: 2010-03-26
forum: Security
---

### Post by OpenTangent on 2010-03-26
Since i can remember, the [Default Keyring bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/34898") has existed in Ubuntu popping up every time the network manager wants to connect to my wireless network. The only way to get around this bug is to remove the password for the default keyring which therefore exposes all you passwords to any one who knows where to look. This is a major security issue that i've overlooked for far too long.

Now for the first time since i started using Ubuntu i need change my password. I went to "Users and Groups" and changed the password and got a comforting "Your password has been changed" message. I would normally carry on with my tasks and forget about it but because of the [Default Keyring bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/34898") i thought i'd better make sure things are as they should be. I logged out and attempted to log back in with my new password.

No luck, the new password is sternly denied and the old password is accepted. Unbelievable, Linux security is something i've often boasted about but the truth is the security in Ubuntu is in a shocking state and has been this way for years. This is not acceptable.

---

### Post by The Cog on 2010-03-26
I see no reason why the keyring password should match the login password. In fact, I think to tie them together would be silly. The keyring should be able to have its own password (and you have discovered that it can). I believe the keyring password can be changed in the keyrings configuration utility. 

Asking for your keyring password every time it wants to connect to wireless gets on my nerves too. It was one of the reasons I started using wicd instead. The other reasons were for better reliability (although NM has got better), and wanting wireless to work even when nobody is logged into the GUI.

---

### Post by OpenTangent on 2010-03-27
I do agree that the keyring password should be able to be separate from your user password but i feel that by default it should be unlocked when you log in unless you explicitly tell it to ask every time.

As for changing of the user password; i got it right by running "Users and Groups" as super user:
```
sudo users-admin
```
I think this could be considered a papercut.

---

### Post by The Cog on 2010-03-28
> **OpenTangent said:**
> I do agree that the keyring password should be able to be separate from your user password but i feel that by default it should be unlocked when you log in unless you explicitly tell it to ask every time.


I thought (could be wrong) that if the passwords matched then the keyring was automatically unlocked as part of the login process. 

As far as I can tell, your complaint boils down to the fact that changing the login password didn't also chang the keyring password. That's an interesting proposition. Maybe it should, if the passwords happen to match in the first place. But I do see problems;

What if root (or some other admin user acting as root) changes your password with the users and groups dialog. Should the keyring password change then? 

Should the Gnome users and passwords GUI widget change the KDE kwallet password?

And if the password is changed by command line (passwd command or by root using the "passwd <username>" command directly? Should the non-gui commands try to find out if the user has a seahorse/kwallet/other-desktop password protected keyring/wallet/whatever and change the password then?

I'm not saying it can't be done, but I think it's not as simple as you think.

---

### Post by guneza on 2010-03-29
> **The Cog said:**
> I thought (could be wrong) that if the passwords matched then the keyring was automatically unlocked as part of the login process. 

That is correct.

The only complaint I have is that changing the default gnome keyring password is not intuitive. Had to click a little bit around before I actually found out to right click on the "Passwords: login" folder in the Passwords tab in Seahorse.

I definitely agree that there should not be anything automatic between the 'passwd' command and the Seahorse GUI. Login passwords are not the same as keyring encryption passwords or passphrases.

My two cents.

---

### Post by OpenTangent on 2010-05-25
Just to post an update here, I just tested on Ubuntu 10.04 and Default keyring still does not automatically unlock (matching login password). I will therefore continue to use a blank password for my default keyring. At least seven Ubuntu releases have gone out with this [bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/34898").

---

### Post by FuturePilot on 2010-05-25
There should be an option if you expand the Details part of the password dialog that says automatically unlock the keyring when I log in, or something like that.

---

### Post by OpenTangent on 2010-06-05
Is this maybe an issue with the auto Ubuntu login? Maybe the keyring is only unlocked if you physically type your password at login?

---

### Post by OpSecShellshock on 2010-06-05
> **OpenTangent said:**
> Is this maybe an issue with the auto Ubuntu login? Maybe the keyring is only unlocked if you physically type your password at login?

That could very well be. I've never used the auto-login and have never had a problem with the wireless network connecting or with anything else that uses the keyring. Having said that, I've not bothered to test that by implementing auto-login either.

---

### Post by bodhi.zazen on 2010-06-05
> **OpenTangent said:**
> Is this maybe an issue with the auto Ubuntu login? Maybe the keyring is only unlocked if you physically type your password at login?

That is the issue. Auto login is considerd by most, including the Gnome and Ubuntu developers, such that autologin disables automatic decryption of your home directory and also the keyring.

You would need to re-write the code yourself to change this behaviour and such a project would not be supported on these forums.

You could file a bug report, but my guess is it would not be implemented.

---

