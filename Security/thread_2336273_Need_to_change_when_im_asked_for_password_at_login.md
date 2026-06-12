---
title: "Need to change when im asked for password at login"
date: 2016-09-06
forum: Security
---

### Post by linkwulluf on 2016-09-06
under "user settings" the "password:" option  I changed "asked at login" to "not asked on login" but now it just wont let me into that user now. i am in the guest account right now just to post this. if i ctrl alt f1 i can still login as that user but i dont know how to change that setting back to normal for terminal. can someone help me out with what commands i need to run to change it so that the user is asked for password on login? did sudo visudo and change line to read NOPASSWD:ALL but still wont let me sign in

---

### Post by yetimon_64 on 2016-09-06
Firstly I'd alter the "sudo visudo" changes back to standard if it didn't work, adjusting that file can cause some serious problems if not done correctly. 

I have my 16.04 install set to log in automatically (works fine) and I have noted the file /etc/lightdm/lightdm.conf has an entry ...
> autologin-user=yetiman

I would suggest you log into your user account in the tty terminal (ctrl + alt + F1) and try to edit the /etc/lightdm/lightdm.conf file in nano (the terminal editor). If the autologin-user line exists there you could comment it out or delete it and save the file, then try a restart or log out / log in etc. Hope that works for you, yeti.

**edit**: try the command ...
```
sudo nano /etc/lightdm/lightdm.conf 
``` to edit the file. I forgot to add above, you will need to use root privileges to edit that file.

---

### Post by steeldriver on 2016-09-06
I don't usually use the GUI for this kind of thing, but I just tried it in a 16.04 VM. 

What appears to happen when you select "Log in without password" from the Users and Groups setting pane is:


[LIST=1]
[*]it adds your user to the **nopasswdlogin **group (this is different from the lightdm **autologin **mechanism) 
[*]it sets an empty password for the account 
[/LIST]

Unfortunately a side effect of (2) is that you can no longer authenticate yourself via either 'sudo' or 'pkexec' in order to remove yourself from (1) (it does NOT appear to actually remove you from the 'sudo' group)

HOWEVER, you can give yourself a new, non-empty password without elevated permissions. So what you need to do is:


[LIST=1]
[*]log in to the virtual terminal 
[*]change your password by using ```
passwd
``` and following the instructions (no 'sudo' required - it's your own account) 
[*]remove yourself from the nopasswdlogin group using ```
sudo gpasswd --delete *username *nopasswdlogin
``` where *username * is replaced by your actual account username (or the equivalent groupmod / usermod etc. command) 
[/LIST]

---

