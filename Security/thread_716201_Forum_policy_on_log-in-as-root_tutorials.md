---
title: "Forum policy on log-in-as-root tutorials"
date: 2008-03-05
forum: Security
---

### Post by aysiu on 2008-03-05
**Policy**
Tutorials explaining how to enable the root account for a graphical login or autologin will not be supported on the forums and will be moved to the Jail. Although we believe people should have the freedom to run their computers however they want, we also believe in supporting Ubuntu's security model. You can find or post information elsewhere on the internet regarding graphical Ubuntu root logins; such tutorials do not have to be hosted on the Ubuntu Forums.

Users posting such tutorials after this announcement will be given a warning or infraction at the discretion of the staff.

**Rationale**
We believe in and offer technical support for Ubuntu's default security model, which uses *sudo* for temporary privilege escalation on particular tasks for particular users with a password authentication. Generally speaking, those who desire a graphical root login fall into one of three categories: [list][*]Users new to Linux who receive an error message telling them they need to be root in order to execute a certain command or who are trying to follow a tutorial for a non-Ubuntu Linux distribution in which they are instructed to log in as root. [*]Users new to Ubuntu who have experience with other *nix systems in which they are used to logging in as root. [*]*nix experts who have very specialized tasks that can be accomplished only through a root login.[/list] The first group (users new to Linux) simply needs to be educated about how Ubuntu works, since all they want to do is accomplish a certain task they *believe* requires a root login. Once they realize the task can be accomplished more simply with Ubuntu's *sudo*, they should have no reason to still want a root login.

The second group (Linux vets new to Ubuntu) may theoretically know about *sudo* but is acculturated to logging in as root. Many of our forum staff and forum members started out this way as well and disliked *sudo* at first. However, once we got used to *sudo*, we liked it better than the traditional root/user model, and realized there were both security and usability benefits to Ubuntu's security model. In other words, give Ubuntu a fair chance.

The third group (experts who know of special situations that require a root login) definitely does not need a root login tutorial. If they're really experts, they can easily figure out on their own how to enable a root login. And if they can't figure it out, perhaps they're not the experts they think they are.

To sum it up, if you can't figure out how to log in as root in Ubuntu, then you should be educated on how to use Ubuntu's *sudo* security model properly; and if you can figure out how to log in as root in Ubuntu and want to, then you certainly don't need a tutorial on how to do it.

Variations on the second and third groups are those who falsely believe *sudo* security model to be less secure than the traditional root/user model. You can find out more about Ubuntu's reasons for using *sudo* and the pros and cons of both security models here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

**Quick reference: popular ways to accomplish tasks people *think* they need a root login for**
If a website instructs you to log in as root and then run a certain command (e.g., *apt-get update*), then instead of logging in as root, you simply preface the command with the word *sudo*: ```
sudo apt-get update
``` and when prompted for a password, enter your own password.

If you have several commands you want to run as root, and you're tired of typing the word *sudo*, you can assume temporary root access without activating the root account. So instead of typing ```
sudo apt-get update
sudo apt-get remove kubuntu-desktop
sudo apt-get autoremove
sudo apt-get install amarok
``` you can type ```
sudo -i
apt-get update
apt-get remove kubuntu-desktop
apt-get autoremove
apt-get install amarok
exit
```

If you want to drag and drop files to system folders, you can run one of the following commands to launch a file browser as root. You can run the command from the Run dialogue by pressing Alt-F2. You can run it from the terminal. Or you can run it as keyboard shortcut or launcher command. 

For Ubuntu ```
gksudo nautilus
``` For Kubuntu ```
kdesu konqueror
``` for Xubuntu ```
gksudo thunar
```

**FAQs**
*I don't want to be "educated." I know the risks and want to enable the root account. Why can't I run my computer the way I want?*
You can run the way your computer the way you want the same way we can run these forums the way we want. We do not want to support you in subverting Ubuntu's security model. If you want to find help outside of these forums, you're welcome to do so.

*But what if I want to use the graphical interface instead of the terminal?*
You can accomplish graphical root tasks by using *gksudo* or *kdesu* in front of the application names. For example, *gksudo synaptic* launches the graphical package manager Synaptic with root privileges. If you don't like repeatedly typing *gksudo* in front of a command, create a keyboard shortcut or launcher icon for the command.

*But aren't there situations in which a root login is necessary?*
Apart from using Ubuntu's recovery mode (which logs you in as root to fix a problem), anyone who has use for such situations should be able to figure out how to log in as root without the need for Ubuntu Forums-hosted tutorials on the subject.

*Isn't knowledge power? What's the harm in having these tutorials posted?*
Let's say you put your money into a bank and the bank gives you an ATM card allowing you to withdraw money if you enter a password in. You decide, however, that you don't want to have to enter a password. You'd rather just be able to put the card into the ATM machine and withdraw cash with just the card and no password. Let's also say that there is a way to tweak the card so as to no longer require a password. If you know the tweak, do you have the right to use it? Well, you probably wouldn't, but let's say the bank's policies on this matter were a little lax. Does the bank have to host tutorials on the card tweak? Absolutely not. The bank wants you to use the ATM with a password and supports that method of security.

Likewise, we on the forums support Ubuntu's security model. If people are able to set up Ubuntu in other ways and still be secure, they can find ways to do that without the forum providing those ways.

*What potential problems come up for the forums when a root account is enabled? Surely there's no problem with users enabling the root account, right?*
Security aside, from a strictly support perspective, root logins complicate support in a couple of ways. One situation is users enabling a root account and forgetting their root password. It's come up more than once that when a user has enabled the root account and forgotten her root password, she is unable to boot into recovery mode, and then alternate means of recovering the Ubuntu installation have to be employed (more complicated means).

---

### Post by bodhi.zazen on 2008-03-06
Sudo offers a finer grain of control over root access and offers options such as insults and lectures. Insults, at the name implies, will insult users who fail to enter the proper password.

Care must be taken when configuring sudo and IMO, as it affects security, is one of the exceptions to my "RTFM" position. I strongly advise you read and understand the features and options of sudo before you alter it's default configuration.

[img]http://forum.wirefree.ro/style_emoticons/default/closed.gif[/img]

General tips : 

[list=number][*]It should go without saying, **you configure sudo at your own risk. Always confirm the advice you receive.**


[*]I ***STRONGLY*** advise against weakening your overall security. Keep in mind, if you are connected to the internet you are **not** the only potential user (as any network monitoring application will show in short order).


[*]Back up your /etc/sudoers before you edit the file.

```
sudo cp /etc/sudoers /etc/sudoers.bak
```


[*]Use ```
sudo visudo
``` to configure sudo (visudo will use nano by default). Nano is a terminal text editor and is easy to use. Use the arrow keys to navigate in the file. Ctrl-X to exit, you will be asked if you wish to save the changes (type Y for yes; N for no).

> visudo edits the sudoers file in a safe fashion, analogous to [noparse]vipw(8)[/noparse].  visudo locks the sudoers file against multiple simultaneous edits, provides basic sanity checks, and checks for parse errors.

Visudo helps reduce errors / typos from disabling root access.


[*]You can use an alternate editor, for example gedit

```
export EDITOR=gedit && sudo visudo
```

[color=navy]~ Thanks to[/color] [color=red]p_quarles[/color]


[*]I advise you allow minimal access to minimal users. If multiple users have full root access system administration can become difficult (too many cooks ...). So if a user needs root access for a single application, allow access to only that application.


[*] Links for options ;)

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

[http://www.debian-administration.org/articles/33](http://www.debian-administration.org/articles/33)[/list]

---

