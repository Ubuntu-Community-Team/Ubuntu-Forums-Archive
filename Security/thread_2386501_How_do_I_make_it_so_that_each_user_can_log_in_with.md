---
title: "How do I make it so that each user can log in without a password"
date: 2018-03-06
forum: Security
---

### Post by xeraster on 2018-03-06
Hello everyone. I'm using Ubuntu 17.10. I've been pulling my hair out trying to figure out how to make it so that on the log in screen, each user isn't required to put in a password to log in to their account.

I am aware that it is possible to edit the sudoers file to make it so that any user that you do this for wouldn't be required to type in their password into the terminal each time they use a sudo command. This isn't what I'm trying to do.

I am also aware that it is possible to make it so that a user account of your choice gets automatically logged in without having to manually type the first password when the computer initially boots (but **not** if they log out after that). This isn't what I'm looking for either.

There are a whole lot of posts on the internet saying how to accomplish those two things but what I'm trying to do is different. I'm trying to get it so that each user can log off, log back on and not be asked for their password. It needs to be possible to press the switch user button, select a different user account, and get logged on without entering a password. This doesn't necessarily mean that there shouldn't be passwords on anything but I really need it so that logging in doesn't need a password.

I hate to use Windows as an example, but in Windows 8 and before (as well as 10 if you go out of your way to set up a local account), you could set it so that your account just simply doesn't have a log in password. You could switch accounts, log in (if no password was set) and just go on about your day without typing in an unnecessary password.

So how can I do this? It's on a home computer where password security just hinders and gets in the way. The only reason we prefer to even use user accounts on this system is simply so that each others' desktop and documents clutter doesn't get in each other's way.

I've tried looking in dconf and gconf at Gnome 3's settings. I tried installing Cinnamon thinking that it would give me the option to turn it off but it doesn't. This just seems to be a "Ubuntu" level setting not a window manager setting. Despite having a different Window manager it still shows the login screen from before with all the same graphics.

Thanks in advance.

---

### Post by holiday on 2018-03-06
In Standard desktops for MATE and XUbuntu 17.10, System.admin.usersandgroups.users settings, there is a "password" field that can be set to "not asked on login". This works for multiple users at the GUI login. 

The $su command will still ask for a password, as will of course ssh.

---

### Post by HermanAB on 2018-03-09
Just bear in mind that if you are so generous and run a system without authentication, then if any user would start a server of any kind, then anybody else around the world can also log into your system without a password and set up a spam server or bitcoin miner for their use and they will all be very happy with your generosity.

---

### Post by holiday on 2018-03-09
I may have misunderstood, but I think xeraster is asking about the GUI login -- in which case the user is either at the physical machine or has previously authenticated a remote session. Disabling GUI login does not remove the requirement to supply a password. 

That being said, the 'passwordless' remote login using ssh keys is more secure than a login requiring passwords.

---

### Post by deadflowr on 2018-03-09
You can set desktop users to be able to login without a password by adding them to the nopasswdlogin group.
(You should be able to set at least all local desktop users with this ability.
I would not do the same for remote users, or at the very least I would have at  some authentication layer for those users)

While only a single user can be set to automatically login, without any intervention.
(Maybe there's a way somehow to allow multiple users that ability, but I have not found it; but ftr, I am not looking very hard)

You can set as many as you want to be able to login just by pressing the Enter key, if they are in the nopasswdlogin group.

This group does this one thing and this one thing only.
It does not allow you to do anything beyond that such as install or remove software.
Or make changes to the system beyond the files owned by the logged in user.
It simply allows you to login without the need to enter a password.
Plain and simple.

All functional users will still need a password, though non-admin user passwords will probably be useless, since logging in is probably the only place those users would ever really need to use it.
(there are other places a non-admin-user might need to enter their password, but they are few and far between, really. imo)

Caveat would be I do not think user's with encrypted home folder's can use the nopasswdlogin as is.
Since they would still need to enter something to unlock the folder.

hope it helps

---

### Post by xeraster on 2018-03-14
> **holiday said:**
> I may have misunderstood, but I think xeraster is asking about the **GUI login**  -- in which case the user is either at the physical machine or has  previously authenticated a remote session. Disabling GUI login does not  remove the requirement to supply a password. 

That being said, the 'passwordless' remote login using ssh keys is more secure than a login requiring passwords.

Yes you are correct that I am talking about the GUI login and not logging in from a terminal or using sudo. I can't figure out how to get rid of that password requirement for anything!


> **deadflowr said:**
> **You can set desktop users to be able to login without a password by adding them to the nopasswdlogin group**.
...
...
This group does this one thing and this one thing only.
It does not allow you to do anything beyond that such as install or remove software.
Or make changes to the system beyond the files owned by the logged in user.
It simply allows you to login without the need to enter a password.
Plain and simple.

The nopasswdlogin only seems to get rid of the password when it comes to using the terminal (unless I'm using it wrong). I am trying to make it so that you can log in, through the gui, without typing in a password.
Here is what I have in my /etc/sudoers file in case maybe the gui password only goes away based on punctuation or some cryptic stuff that I couldn't guess. admin1 is the username.
```

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

admin1 ALL=(ALL)  NOPASSWD: ALL
# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d


```
Again, unless I am doing it wrong, this only removes the password requirement for sudo and, I assume, logging in from a terminal. I don't want that. I want to log in, through the gui, without having to enter a password.

I attached a picture of the screen I want there to not be a password on since everyone is so confused.

[https://i.imgur.com/mq0RWti.jpg](https://i.imgur.com/mq0RWti.jpg)

[https://i.imgur.com/TZljyGd.jpg](https://i.imgur.com/TZljyGd.jpg)

---

### Post by xeraster on 2018-03-14
Ok guys quick update. I found a way to somewhat fix it by just deleting the user password by typing: ```
sudo passwd -d "username"
```
When I do this, Gnome doesn't ask for a password and just skips the prompt completely.
This probably isn't the best idea, but for what I need, this is a more ideal solution than just dealing with typing a login password every time. If anyone has an idea to not require a login password but still being secure and having a password, let me know,

---

### Post by wildmanne39 on 2018-03-14
I believe after removing your user password you will no longer be able to update your system or perform any tasks that require sudo, I believe you will have to enable the user password for these tasks.

---

### Post by wildmanne39 on 2018-03-14
Please use the attachment facility by clicking on the paperclip or use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by xeraster on 2018-03-14
> **wildmanne39 said:**
> Please use the attachment facility by clicking on the paperclip or use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.
It wouldn't work, I was able to upload 1 picture but the forum software crapped out and wouldn't let me upload more than 1. It kept uploading and not showing up.

Also, yeah this sucks. I can't authenticate when Ubuntu asks for a password when installing stuff from Ubuntu Software Center or something. This sucks!!!

If I could just find a way to either disable those Ubuntu Authentication prompts or just login without a password like I have been trying to do in the first place I would be really happy.

---

### Post by holiday on 2018-03-14
You want the Desktop GUI to permit access without passwords. The Desktop GUI is an application with some rules of its own. Its behavior cannot be completely controlled from the system level.  

So you must look for a GUI solution. In my first post to your question I show how this is done in MATE and Xubuntu. I am not sure if other Desktop systems offer the same feature, but I do know that what you want is possible with those two Desktop systems at least. 

This will be an option in the GUI user configuration of your Desktop system. Which are you using?

---

### Post by deadflowr on 2018-03-14
> The nopasswdlogin only seems to get rid of the password when it comes to using the terminal (unless I'm using it wrong). I am trying to make it so that you can log in, through the gui, without typing in a password.
That's a quirk of GDM, I guess.
It's rather easy to fix, though.
You need to add one line to the /etc/pam.d/gdm-password file.
At the top of the file (after the #%PAM-1.0 line)
put this
```
auth sufficient pam_succeed_if.so user ingroup nopasswdlogin
```
and save.
From then on, any user in the nopasswdlogin group will login without needed to input a password.

References: [https://wiki.archlinux.org/index.php/GDM#Passwordless_login]("https://wiki.archlinux.org/index.php/GDM#Passwordless_login")


Other flavors of Ubuntu such as Xubuntu and Ubuntu Mate use Lightdm, which has the ability to do this without the need to fumble about with PAM files.
Making it much easier. And the one I have used for years.
GDM is new, again, to the main Ubuntu desktop.
They switched back to GDM when they switched back to the Gnome desktop.
Prior to the switch Ubuntu used the Unity desktop, which used lightdm, like the rest of the Ubuntu flavors do (mostly).


Sidenote: I tested this on a virtual machine of Ubuntu 17.10 and found it works.
But I'm not sure if the behavior it showed was virtual machine related or not.
Basically, when you select your user and hit enter. Instead of showing the password field for the selected user, it sort of glitches out for a second or two, then brings up the user's desktop screen.
It looked weird is all.

---

### Post by xeraster on 2018-03-15
It worked!!!!! :biggrin::biggrin::biggrin::biggrin:=d>=d>=d>:grin:

Now it does have some weird behavior though. When logging in, it does indeed not ask for a password.
When using the "lock" button, it will ask for a password but a way to get around that is to select "log in as a different user" and then it will let you log in as the user you just switch from without a password.

But hey this is a big improvement so I'm happy with it now.

EDIT: After like a day, it fixed itself so I have 100% zero problem with this fix.

Thanks again guys

---

