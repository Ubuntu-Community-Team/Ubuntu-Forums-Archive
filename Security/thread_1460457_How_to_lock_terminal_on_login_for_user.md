---
title: "How to lock terminal on login for user"
date: 2010-04-22
forum: Security
---

### Post by Crazedpsyc on 2010-04-22
Hello, I recently set up a family computer for a friend, and now his son is "experimenting" with the terminal (randomly entering commands). since he could accidentally do something bad, I am supposed to prevent him from using terminals, but only as hi user. I tried vlock and away, but with vlock it says 'this terminal is not a virtual console', and away can't seem to lock all consoles.  please help before he erases his own home directory lol!

---

### Post by Sef on 2010-04-22
Make sure he has no admin privileges.  That way sudo will not work.

---

### Post by Dayofswords on 2010-04-22
and remove the terminal link in the menu

---

### Post by Agent ME on 2010-04-22
If the son has his own account (and no admin/sudo privileges), then the most he can possibly mess up is his own account. Let him use it if he wants to.

---

### Post by OpSecShellshock on 2010-04-23
> **Agent ME said:**
> If the son has his own account (and no admin/sudo privileges), then the most he can possibly mess up is his own account. Let him use it if he wants to.

This is good advice. Take away the capacity to do system damage and let him try things. It's the best way to learn, and it's a good skill to have.

---

### Post by norseman-has-a-laptop on 2010-04-23
i say let him mess with it and when he messes up the system have him reinstall and put it back to the way it was lol

ubuntu is that hard to fix its like not even 30 minutes for the actual working os 

so yeah let him mess with it  we all started some where right

---

### Post by Crazedpsyc on 2010-04-23
Lol thanks guys! But I have my "orders" so I still have to lock the terminal. His parents don't want him to lose a month of schoolwork if he messes up his account, and he doesn't need the menu shortcut, since he knows the command, and can just make a launcher (he would too). Personally, I like that advise, but I got a very simple answer when I asked my friend: "NO". He did say if I could make the terminal just look like it works, but actually not affect the computer, he would accept that. is there a way to just set it up so it shows him the normal prompt but either says 'bash: command not found' or simulates all the normal stuff, but uses only commands put in a certain directory, and then redirects the commands to a safe folder/file

---

### Post by bodhi.zazen on 2010-04-23
I would suggest :

1. Teach him how to back up his files. Learning the utility of backups is one of the first lessons all computer users should learn. Data loss is not a matter of if, but when ...

2. Use a separate /data partition and teach his parents how to back up their data. Learning the utility of backups is one of the first lessons all computer  users should learn. Data loss is not a matter of if, but when ...

3. Give him a playground - Use either the guest account or an alternate test account or better his own partition to manage and learn on.

4. Use apparmor to confine him or her.

At the end of the day, if the user has physical access there is not a whole lot you can do other then teach 'em right.

---

### Post by OpSecShellshock on 2010-04-24
To a certain sort of curious user, restriction is a form of enticement. If they are not talented enough to overcome restrictions at the moment, they certainly will become so before long. The best thing you can do in those cases is to limit the potential damage and try to channel the curiosity constructively.

---

### Post by MooPi on 2010-04-24
The beauty of having a system that you are in full control of (linux) is that it's repairable without cost. Your son is learning and that is a beautiful thing as well so let the learning commence. I didn't learn a thing about computers using them I learned by changing!

---

### Post by Crazedpsyc on 2010-04-24
Ooh nice scotty MooPi! Thanks i'll try apparmor, but If that doesn't confine him from even his own files while in the terminal, I still need another option. Also, a program to monitor what he does would be nice, but I tried things like lkl and they are too obvious because of bugs, so maybe one that just records from terminal, but can start on login. I just got ttyrec, but have no idea how to use it for this.

Just an important related thing: How do I make it start Firestarter when he logs in? it requires sudo, but I think giving him the root password would be a very bad idea lol

---

### Post by Agent ME on 2010-04-24
If I remember correctly, tools like Firestarter are just for editing iptable's firewall settings. You don't need to run Firestarter for its rules to take effect; only to change the rules.

---

### Post by bodhi.zazen on 2010-04-24
I should have mentioned earlier - you could use one of the various kiosk modes

[http://live.gnome.org/Sabayon/](http://live.gnome.org/Sabayon/)
[http://live.gnome.org/Pessulus](http://live.gnome.org/Pessulus)

[http://ubuntuforums.org/showthread.php?t=741386](http://ubuntuforums.org/showthread.php?t=741386)

google search kiosk -)

---

### Post by dino99 on 2010-04-25
thats what i do for kids and untrusted users: they have their own account into virtualbox, and they do all they want. I only have one original image i can use to replace their broken account if needed to replace it: easy and fast. Everything else is locked.

---

### Post by Crazedpsyc on 2010-04-25
lol, I know, but it provides a nice GUI for doing it, and it shows active connections, and has an aplet etc. Much better than having to make all that myself!
Both sabayon and Pessuslus sound  great, thanks! I almost got Sabayon before but didnt really understand the description. I'll post again if either are perfect!

---

### Post by Crazedpsyc on 2010-04-26
I tried Sabayon, it crashed when I clicked  "Edit" so now I'll try Pessuslus
Doesn't it seem odd that there is a gaming/media version of Gentoo called Sabayon? lol
Ahh, I am so glad Ubuntu can be installed multiple times free! I just had to use my backup ubuntu to reinstall network-manager because I accidentally deleted it lol!
Ok, now I am wasting time.... Pessulus is installing..... umm no it is not...
alright, opening terminal..
apt-get install pessulus.. blah blah blah... [Y/n] y
....installed
pessulus
blah.. tada!
umm, it doesn't seem to be able to change stuff for individual users?

going back to sabayon..:
MainThread 2010/04/26 10:28:12.3865 (admin-tool): Creating profiles dialog
MainThread 2010/04/26 10:28:12.4949 (admin-tool): Starting main loop

then the window opens.. I add Ph3x2 as a user.. I select him and click the Edit button..
a window pops up that says:
A fatal error has occurred.  You can help us fix the problem by sending the log in /toot/sabayon-debug-log.conf to [http://bugzilla.gnome.org](http://bugzilla.gnome.org)

in the terminal it says:
MainThread 2010/04/26 10:31:36.7903 (USER): Starting to edit profile 'Ph3x2'
MainThread 2010/04/26 10:31:37.0253 (USER): Got fatal error: Fatal exception in callback; exiting main loop
MainThread 2010/04/26 10:31:37.0263 (USER): Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/sabayon/errors.py", line 125, in wrapper
    return func (*args, **kwargs)
  File "/usr/lib/pymodules/python2.6/sabayon/profilesdialog.py", line 422, in __edit_button_clicked
    session.start ()
  File "/usr/lib/pymodules/python2.6/sabayon/profilesdialog.py", line 216, in start
    self.temp_xauth_path = self.__copy_xauthority ()
  File "/usr/lib/pymodules/python2.6/sabayon/profilesdialog.py", line 90, in __copy_xauthority
    shutil.copy2 (xauthority, temp_path)
  File "/usr/lib/python2.6/shutil.py", line 99, in copy2
    copyfile(src, dst)
  File "/usr/lib/python2.6/shutil.py", line 52, in copyfile
    fsrc = open(src, 'rb')
IOError: [Errno 2] No such file or directory: '/tmp/libgksu-ZUO2xH/.Xauthority'

Exception AttributeError: "'Session' object has no attribute 'temp_xauth_path'" in <bound method Session.__del__ of <Session object at 0xa75b784 (sabayon+profilesdialog+Session at 0xa83c3d0)>> ignored
MainThread 2010/04/26 10:31:37.2364 (admin-tool): Terminating main loop
MainThread 2010/04/26 10:31:37.2366 (admin-tool): Exiting abnormally; dumping log due to a fatal error
Dumped debug log to /toot/sabayon-debug-log-2010-04-26-10-31-37.txt

the log is attached

ok, now I tried running sabayon as non-toot (rootish) with sudo (whats the diff though?) and it worked. I opened the edit thing for Ph3x2 and it opened a window that logged in as something called sabayon-admin
now what do I do?

---

### Post by bodhi.zazen on 2010-04-26
See also : [http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm)

If you get those kind of error messages I suggest you file a bug report on Launchpad.

---

### Post by Crazedpsyc on 2010-10-22
Ok, forget it. I'm just going to make a python shell and use chsh to make it his default. I can have a list of comands like
```
legalcommands = [cp, vi, gedit, echo, festival, help, man]
```
and have it run anything he types through this list to make sure it is allowed.

---

