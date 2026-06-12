---
title: "Adding User."
date: 2010-07-24
forum: Security
---

### Post by Stormsy on 2010-07-24
Hi there,

I decided to completely install Ubuntu 10.04 on my HDD over my copy of Win Vista - I do not want to pay out more money for Antivirus software when instead I can use Ubuntu and not worry at all about viruses or firewalls etc!

Needless to say - the installation onto my Dell Inspiron 1525 went smoothly; the best installation experience I have had in some time :) (compared to Vista...)

I have a couple of questions - at the moment I am the sole user on the laptop and I have only one account which I log into the laptop.  I would like to create an additional account that would be used for everyday use, whilst leaving the original account (that was created when installing Ubuntu) to be used for updating Ubuntu and installing software from the repo's.

If I am not making much sense, please ask me to clarify.  What I guess I am trying to ask is how do I restrict access to the root directory?

Also - hypothetically, if Ubuntu released a newer version (say 11.02) how would I go about updating my version (10.04) to the latest version?

Thanks,
Stormsy.

---

### Post by noway2 on 2010-07-24
Creating a separate non privileged account shouldn't be necessary.  By default your normal user does not have admin privilege.  Only when you sudo (or by extension do something like sudo -i) do you have this kind of access.  This is unlike windows where the privilege level is tied to the account itself.  BTW, you should NOT enable the root account.  There have been several discussions of this in the forum if you are interested in the whys of it.

You will find that your system will want to periodically update as they become available.  You will get a pop-up "update manager" and you can simply let it do its thing.  It will prompt you for your (administrative) password which is your user password.  When distributions are released, you will get notification and you can choose to upgrade the distribution from the update manager.

---

### Post by Bachstelze on 2010-07-24
> **Stormsy said:**
> 
If I am not making much sense, please ask me to clarify.  What I guess I am trying to ask is how do I restrict access to the root directory?

It depends what you mean by "restrict".  By default, all user accounts (including the one you created during installation) can only write to their home directories, and have read-only access to everything else (modulo a couple files that are really sensitive and can be read only by the super-user).

The super-user is called "root" and basically has all access to everything.  Traditionally, you log into the root account just like you log into any other account: you type "root" at the login prompt, and enter the password that has been defined for this account.  Ubuntu, however, treats it a little differently: you "become root" not by logging into another account, but by using the [font=monospace]sudo[/font] command.  [font=monospace]sudo[/font] will ask for your password to verify that it is really you who is calling it, and then will let you run commands as if you were the super user. More on [font=monospace]sudo[/font] here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> Also - hypothetically, if Ubuntu released a newer version (say 11.02) how would I go about updating my version (10.04) to the latest version?

There will be a page created on the Wiki with update instructions.  For example, the page for updating to 10.04 is here:

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by Stormsy on 2010-07-24
Right - I understand what you are saying.  

To become the "root user" you use sudo.  Other than that, you login as usual without root access.  Initially I assumed that you could create an account with root access, like Windows - but obviously you can't do that.

Ubuntu is completely different from Windows.  I just took the "leap of faith" a couple of days ago and installed Ubuntu!  Woke up one morning and thought; "I'm not using Windows anymore..."  The rest, they say, is history!

Still learning new things - but its worth it!

Thanks for your help!  Greatly appreciated! :)
Stormsy.

---

### Post by OpSecShellshock on 2010-07-24
> **Stormsy said:**
> Initially I assumed that you could create an account with root access, like Windows - but obviously you can't do that.

Oh, you *can*, there's just not really any need to in most cases.

---

