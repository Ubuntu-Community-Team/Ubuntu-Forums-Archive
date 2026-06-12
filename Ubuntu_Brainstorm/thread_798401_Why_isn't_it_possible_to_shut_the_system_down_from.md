---
title: "Why isn't it possible to shut the system down from the command line?"
date: 2008-05-18
forum: Ubuntu Brainstorm
---

### Post by CrazyGuy123 on 2008-05-18
It seems possible to shut the system down from the GUI without sudo access, but shutting down from the command line does need sudo - why?

---

### Post by Brean on 2008-05-18
what about "sudo halt" ?

--------------------------
edit:
ok, this is about the rights that gdm has...
but you are right, I also can not think of any reason why the user can shut down the pc by GUI but not with the console. You can activate shoutdown for normal users on different ways, see [http://www.spencerstirling.com/computergeek/shutdown.html](http://www.spencerstirling.com/computergeek/shutdown.html)

---

### Post by Martje_001 on 2008-05-18
> **Brean said:**
> what about "sudo halt" ?
Please read, he's not asking that ;).

OP: I don't know. I think this is handled by GDM, which can only be triggerd through special gnome-daemons.

---

### Post by smartboyathome on 2008-05-18
I think the reason is another security one. If a script were able to do that without having to have your password, then it could represent a hole.

---

### Post by chrisccoulson on 2008-05-18
The way it currently is stops normal users from being able to shut down the machine if they are SSH'd in from a remote location. That is how it should be - allow the local user to shut-down but not users who are connected to the machine over a network.

---

### Post by CrazyGuy123 on 2008-05-19
I don't think it's really security, since if you wanted to you could script the mouse movements to shut the system down from the gui, or just use whatever api that shutdown dialog box uses.

My main point is it's inconsistant - from a security standpoint you as a user can either do something or you can't - it shouldn't depend on if you've got a mouse or a keyboard.

It could be considered similar to security by running all users as root but physically locking away the "r" key so the user can't type "rm" to delete files.  Effectively it's implementing security at the wrong level because there are other ways to delete a file.

---

### Post by shad0w_walker on 2008-05-19
Yes you could script the mouse to shutdown the system, but if you are able to execute scripts with out user intervention or having the executable bit set then you have alot of other problems on your system to worry about.

P.S. You can setup sudo to allow running shutdown without being prompted for a password, though for various reasons this isn't a great idea.

---

### Post by DizzyTech on 2008-05-19
sudo poweroff?

---

### Post by jediborger on 2008-05-19
When you login to GDM your password is saved to the keyring which gives you as a user certain privileges. One of those is to shutdown the computer. When you are using the terminal you are bypassing GDM and the keyring, thus you need to supply sudo with a password. If you want further reading look into sudo documentation and also how the /etc/sudoers file works.


BTW, here's a command to shutdown the computer from the cmdline as well as restart.

```
sudo shutdown -h now
```
This will shut down the computer now.

```
sudo shutdown -r now
```
This will reboot the computer now.

You can see the rest of the options by typing
```
man shutdown
```

Hope this answers your questions.

---

### Post by chrisccoulson on 2008-05-19
Are you sure that's how it works when you shut down from within GNOME? I thought that the shutdown happened via a DBUS call to HAL, and I think that the DBUS policy only allows that to happen if you're at the local console.

---

### Post by smartboyathome on 2008-05-19
> **chrisccoulson said:**
> Are you sure that's how it works when you shut down from within GNOME? I thought that the shutdown happened via a DBUS call to HAL, and I think that the DBUS policy only allows that to happen if you're at the local console.

I am pretty sure this is how it works. I know that E17 couldn't shut down before without using sudo, but can now.

---

### Post by CrazyGuy123 on 2008-05-20
Maybe we need a CLI utility to send a DBUS call to hal then so we can get the same functionality from the console?

---

### Post by hellomoto on 2008-05-20
you can shutdown the PC from the command line:

```


sudo shutdown -P now


```

Also you can shutdown the computer to a certain time/date or give the computer a "count down" to shutdown.

For a full use of the shutdown command type:

```

man shutdown

```

however, Im not sure as to why you need sudo status to do this, I agree it is a pain!

---

### Post by chrisccoulson on 2008-05-20
I might have a go at that. Can't imagine it would be that difficult really

---

### Post by CrazyGuy123 on 2008-05-20
hellomoto:  I mean WITHOUT sudo - it shouldn't be necessary to get extra privilidges to do something thats possible without extra privilidges.

chrisccoulson:  if you know how to do that that sounds cool - I wouldn't know where to start with dbus!

---

### Post by smartboyathome on 2008-05-20
Well, it is necessary. If you want to take on the task of doing this, ok, but I still think it would be a bad idea to include this due to someone being able to include this in a script which does something else and tricking someone else into running the script (thus shutting down their comp and loosing all data that was open and unsaved).

---

### Post by chrisccoulson on 2008-05-20
> **smartboyathome said:**
> Well, it is necessary. If you want to take on the task of doing this, ok, but I still think it would be a bad idea to include this due to someone being able to include this in a script which does something else and tricking someone else into running the script (thus shutting down their comp and loosing all data that was open and unsaved).

I'm pretty sure someone could already write a script which executes the dbus call in order to shut down the machine.

---

### Post by justin whitaker on 2008-05-20
If you hit ctrl-alt-delete while in terminal, it will reboot. Why mess with permissions when you can do something simple?

---

### Post by cubeist on 2008-05-20
> **justin whitaker said:**
> If you hit ctrl-alt-delete while in terminal, it will reboot. Why mess with permissions when you can do something simple?

You may be on to something... The settings for ctrl-alt-delete can be changed to whatever the user wants:
```
sudo nano /etc/event.d/control-alt-delete
```
change the *-r* to *-h* to halt (poweroff) the computer instead of restarting.

* You can also use gedit if you are not comfortable with nano

---

### Post by hellomoto on 2008-05-20
Sorry i was just posting the way i would shutdown from the command line, i was aware that you didn't want to use sudo.

Can i ask why you want to shutdown from the command line? and why you don't want to use the sudo command? -- is there a particular reason.

---

### Post by CrazyGuy123 on 2008-05-21
hellomoto:  I consider it bad practice to allow standard users sudo abilities, just like it's bad practice to give users administrator accounts in windows.

I also consider it important that a user can accomplish every task from the command line, since thats important for scripting actions, and useful for "advanced" users.

These two things can't work together with the current system.

---

### Post by Rinzwind on 2008-05-21
> **CrazyGuy123 said:**
> It seems possible to shut the system down from the GUI without sudo access, but shutting down from the command line does need sudo - why?

A normal user will not have a shutdown button in Gnome. 
Only sudo accounts have that. 

When you log into command line you are a normal user with the ability to use sudo to perform admin tasks. And guess what halt is? An admin task and hence the need to ask for your sudo password. 

And I consider being able to halt system in GUI without sudo password a bug and not being able to halt system from command line without sudo password to be the correct way. 

> chrisccoulson: Are you sure that's how it works when you shut down from within GNOME? I thought that the shutdown happened via a DBUS call to HAL, and I think that the DBUS policy only allows that to happen if you're at the local console.
Yes, this should be correct.

---

### Post by chrisccoulson on 2008-05-21
```
dbus-send 	--system --dest='org.freedesktop.Hal'	\
		--type=method_call --print-reply	\
		/org/freedesktop/Hal/devices/computer 	\
		org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
```

...in a script will shut down the machine from a terminal within your GNOME session, but fails from a TTY due to D-BUS policy settings.

---

### Post by CrazyGuy123 on 2008-05-21
Wow cool.

---

### Post by chrisccoulson on 2008-05-21
It has a bad side effect though, in that any applications running in your GNOME session don't terminate properly

---

### Post by chrisccoulson on 2008-05-21
> **Rinzwind said:**
> A normal user will not have a shutdown button in Gnome. 
Only sudo accounts have that. 

What version of GNOME do you use?

> **Rinzwind said:**
> When you log into command line you are a normal user with the ability to use sudo to perform admin tasks. And guess what halt is? An admin task and hence the need to ask for your sudo password. 

And I consider being able to halt system in GUI without sudo password a bug and not being able to halt system from command line without sudo password to be the correct way.
No! Why on earth should a user who is logged in locally via the GUI be unable to shutdown the system without sudo? That means every user who uses it has to be given the necessary admin privileges to use sudo and shut down the machine, or else they're only way of shutting it down is to pull the plug. 

What a ridiculous idea.

---

