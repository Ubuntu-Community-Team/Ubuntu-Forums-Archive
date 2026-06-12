---
title: "lightdm config files location in 14.04"
date: 2014-02-15
forum: Ubuntu Development Version
---

### Post by WebDrake on 2014-02-15
Hello all,

Recent (last 6 weeks?) updates to lightdm seem to have changed the location of the lightdm config files.  What was in /etc/lightdm/lightdm.conf.d/ has been removed (only .bak files remain); the config now seems to be in /usr/share/lightdm/lightdm.conf.d/

However, a users.conf file remains in /etc/lightdm/ containing the following:

```

#
# User accounts configuration
#
# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserAccounts]
minimum-uid=500
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin

```

Meanwhile, /usr/share/lightdm/lightdm.conf.d/ contains the files 50-greeter-wrapper.conf  50-guest-wrapper.conf  50-ubuntu.conf  50-unity-greeter.conf  50-xserver-command.conf.

Can anyone clarify how things have changed here with lightdm?  (Incidentally, what's with the hidden-users nobody nobody4 noaccess?)

I should add that what I really want to understand is how to redo the tweaks that prevent Guest Session and Remote Login from showing up on the login screen, as the pre-14.04 instructions obviously no longer work with those -- and I'd also like to understand how to enable the unity-system-compositor (merely installing the package doesn't seem to have inserted anything in /usr/share/lightdm/lightdm.conf.d/).  But I'd like to understand properly why the location/layout of config files has changed, not just blindly follow a set of instructions on how to get what I want ;-)

Thanks & best wishes,

     -- Joe

---

### Post by Mateusz Stachowski on 2014-02-15
In Trusty you have to install ubuntu-desktop-mir package which will pull in other necessary packages and setup the XMir.

---

### Post by grahammechanical on 2014-02-15
With unity-system-compositor and ubuntu-desktop-mir installed I not only get Xmir running but 10-unity-system-compositor.conf in /etc/lightdm/lightdm/lightdm.conf.d and no bak files even as hidden files.

Everything happens for a reason. I am sure the developers have logical reasons but I am not confident that the normal visitors to this section of the forum can provide any enlightenment. I know that I cannot. I can only guess that it is in preparation for giving 14.04 users the login option of logging in to a Unity 8 preview session running on Mir/Xmir.

Have you tried adding allow-guest=false to either 50-unity-greeter.conf or 50-ubuntu.conf in /usr/share/lightdm/lighdm.conf? Someone has to be the first to crash and burn. At least the machine will not go up in smoke.

Regards.

Edit: No crash and burn. Adding allow-guest=false to /user/share/lightdm/lightdm.conf.d/50-ubuntu.conf removes both Guest Session and Remote Session from the login screen. A perfect 3 point landing for Graham.

---

### Post by ventrical on 2014-02-15
> **grahammechanical said:**
> With unity-system-compositor and ubuntu-desktop-mir installed I not only get Xmir running but 10-unity-system-compositor.conf in /etc/lightdm/lightdm/lightdm.conf.d and no bak files even as hidden files.

Everything happens for a reason. I am sure the developers have logical reasons but I am not confident that the normal visitors to this section of the forum can provide any enlightenment. I know that I cannot. I can only guess that it is in preparation for giving 14.04 users the login option of logging in to a Unity 8 preview session running on Mir/Xmir.


 Good guess :) Sooner or later ..

---

### Post by Mateusz Stachowski on 2014-02-15
Look at what just landed as an update in Trusty.

[https://launchpad.net/ubuntu/+source/ubuntu-docs/14.04.1](https://launchpad.net/ubuntu/+source/ubuntu-docs/14.04.1)

> [ Kevin Godby ]  * configure.in, html/Makefile, html/ubuntu.xsl, whats-new.page:
    - Bumped version number to 14.04.
  * Typo on printing-cancel-job.page fixed (LP: #1231655).


  ...


  [ Gunnar Hjalmarsson ]
  * The group "Add & remove software" highlighted on index.page by
    creation of the guide page addremove.page. Related links tweaking.
  [B]* shell-guest-session.page:
    - Added description of how you can disable the guest session[/B]
      **feature (LP: #1076740).**
  * Creation of prefs-language-install.page.
  * keyboard-layouts.page:
    - Rewritten to reflect the "System Settings -> Text Entry" design
      (LP: #1242626).
  * tips-specialchars.page:
    - Sections "Compose key" and "Input methods" removed.
  * debian/control:
    - Bump Standards-Version to 3.9.5.
  * Updated ubuntu-help.pot.

...

 -- Gunnar Hjalmarsson <gunnarhj@ubuntu.com>   Fri, 14 Feb 2014 18:07:00 +0100

I only cited the relevant changes but there are more of them. Anyway this is what it says on the mentioned shell-guest-session.page

> [B]Disabling the feature
[/B]
If you prefer to not allow guest access to your computer, you can disable the Guest Session feature. To do so, press Ctrl+Alt+T to open a terminal window, and then run this command (it's one long command, even if it may be shown wrapped on the screen - copy and paste to get it right):


sudo sh -c 'printf "[SeatDefaults]\nallow-guest=false\n" >/usr/share/lightdm/lightdm.conf.d/50-no-guest.conf'


The command creates a small configuration file. To re-enable Guest Session, simply remove that file:


sudo rm /usr/share/lightdm/lightdm.conf.d/50-no-guest.conf

---

### Post by grahammechanical on 2014-02-15
Ah! The developer sophisticated method as opposed by my brute forced method of editing 50-ubuntu.conf. Then, again gksu is not installed by default any more. Remember? Anyway, it works and it does not also remove the Remote login option.

I suppose the way to remove Remote Login would be to create a 50-no-remote.conf file. Only one way to find out.

Edit: Yes!

> [COLOR=#000000]*sudo sh -c 'printf "[SeatDefaults]\ngreeter-show-remote-login=false\n" >/usr/share/lightdm/lightdm.conf.d/50-no-remote-login.conf'*[/COLOR]

Creates the 50-no-remote-login.conf file with

> [SeatsDefault]
greeter-show-remote-login=false

And that removes Remote login. I suppose that creating a script is a much better way of doing things than telling to user to edit a really important script.

Edit: 16/02/2014

I have modified the command for removing remote login. The earlier command did not work. I was fooled by the delay in Remote login appearing at the login screen.

Regards.

---

### Post by david183 on 2014-04-02
> **grahammechanical said:**
> 

Have you tried adding allow-guest=false to either 50-unity-greeter.conf or 50-ubuntu.conf in /usr/share/lightdm/lighdm.conf? Someone has to be the first to crash and burn. At least the machine will not go up in smoke.

Regards.
.

Hi guys :)

I was curious. I did it. I added **allow-guest=false **in the **lightdm.conf**
Whatever the place I chose to put it in the file, whatever I created a dedicated section with brackets as done in the previous versions of Ubuntu, only one thing happened to me : Lightdm did not start and I had to take out the added line in order things to get well again.

Cheers

---

### Post by sorab on 2014-04-25
Hi

Fine that some here sorted out their specific problems. But can anyone please try answering the thread-opener's question:
[B][SIZE=3]"Where have the config files gone?"
[/SIZE][/B][SIZE=3][SIZE=2]
Precisely for my purposes: Where can I change the theme light dm will use, since there is no lightdm.conf anymore?

Even more precisely: How can I get rid that light dm greeter that got installed by the xubuntu-desktop metapackage, and which apparently does not only make the login screen ugly, but also somehow covers the desktop background on all other installed gtk based DEs (Unity, gnome) AFTER login. Simply removing the xfce light dm theme will only cause light dm to have NO configuration.[/SIZE][/SIZE]

---

### Post by zika on 2014-04-25
Apart from the (unusual for this place) tone of Your message, the answer is given in the thread: /usr/share/lightdm/lightdm.conf.d/
For example, You can make Your own files in that folder and control what You've used to control from previous default location...
```
cat  /usr/share/lightdm/lightdm.conf.d/50-&#1085;&#1077;&#1082;&#1086;_&#1080;&#1084;&#1077;.conf 
[SeatDefaults]
autologin-user=&#1085;&#1077;&#1082;&#1086;
allow-guest=false
greeter-show-remote-login=false
```
Simply put: (kind of) forget about /etc/lightdm folder or think about it as a wrong place to put anything You plan to use later and that should work... One word: depreciated...

---

### Post by ventrical on 2014-04-25
> 

[SIZE=3][SIZE=2]Precisely for my purposes: Where can I change the theme light dm will use, since there is no lightdm.conf anymore?

[/SIZE][/SIZE]
Here..

Keep in mind this is a Utopic convert..on xorg. (no xmir installed).

---

### Post by ventrical on 2014-04-25
Please see this note:

[http://ubuntuforums.org/showthread.php?t=1970289&page=9&p=12886871#post12886871](http://ubuntuforums.org/showthread.php?t=1970289&page=9&p=12886871#post12886871)

[s]Mir is affected also, at lease the  methods to revert back to xorg and remove it have not been updated at the wiki page. This could be a serious issue for new testers - so I thought I would make a note of it. [/s]

Regards..

edit: I updated the mir wiki.

[https://wiki.ubuntu.com/Mir/Installing](https://wiki.ubuntu.com/Mir/Installing)

---

### Post by sorab on 2014-04-25
OK, shame on me if the informality of my chosen words violated the CoC here. It just has been the how-many's? Internet post that read through today because its title promised the answer to my problem, just to find that the topic switched from "where is the config file?" to "how to disable the guest account?" or (as here) something about Mir, without answering the actual question.
(Maybe this excuses, and as far as I remember the original text was not insulting on anyone, unless config files can be insulted)

And the best in it is, the thread now end with the precise answer to the given question. Thank your very much for that, ventrical.

---

### Post by zika on 2014-04-26
> **sorab said:**
> And the best in it is, the thread now end with the precise answer to the given question. Thank your very much for that, ventrical.The answer could be called precise but it is not correct... According to pictures in that precise answer there is usefull stuff in one of folders that is (I wrote in message above that) depreciated and hence should not be used... ;) All the best ... ;)

---

### Post by cariboo on 2014-04-26
> **zika said:**
> The answer could be called precise but it is not correct... According to pictures in that precise answer there is usefull stuff in one of folders that is (I wrote in message above that) depreciated and hence should not be used... ;) All the best ... ;)

And with that, I think this thread has run it's course, Utopic development is open now, and any discussions of 14.04 problems should take place in other parts of the forum. Thread closed.

---

