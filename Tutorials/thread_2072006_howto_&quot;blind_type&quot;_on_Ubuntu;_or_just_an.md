---
title: "howto &quot;blind type&quot; on Ubuntu; or just an interesting use of vbetool"
date: 2012-10-16
forum: Tutorials
---

### Post by henriquemaia on 2012-10-16
[SIZE="4"]**how to turn off your screen regardless of what you do on the keyboard or mouse**[/SIZE]

[SIZE="3"]**Why?**[/SIZE]

Well, for several reasons. 

[LIST]
[*]Because you want to practice your typing skills.
[*]Because you need to type important things in a crowed space and you don't want others to see what you’re typing.
[*]Because you’re taking notes of your dreams at night and you don’t want the light of the screen to wake you further.
[*]Because you like testing crazy things.
[/LIST]

[SIZE="3"]**How?**[/SIZE]

First you have to install *vbetool*. 

Find it on the Ubuntu Software Center or type the following on the command line:

```
sudo apt-get install vbetool
```

[SIZE="2"]**Now what?**[/SIZE]

Now you have to do several things. First, vbetool can only be run as root. So you have to add the command to the sudoers as a no password command. 

*How?*

From [**here**]("http://askubuntu.com/questions/159007/specific-sudo-commands-without-password") (credit to whom the credit is due) we learn how to

> **Use the NOPASSWD directive**

You can use the NOPASSWD directive in your /etc/sudoers file.

If your user is called user and your host is called host you could add these lines to /etc/sudoers:

```
user host = (root) NOPASSWD: /sbin/shutdown
user host = (root) NOPASSWD: /sbin/reboot
```

This will allow the user user to run the desired commands on host without entering a password. All other sudoed commands will still require a password.

**Note!** Use the command visudo to edit the sudoers file to make sure you do not lock yourself out of the system – just in case you accidentally write something incorrect to the sudoers file.

[B]Using /etc/sudoers.d instead of modifying /etc/sudoers
[/B]

As an alternative to editing the /etc/sudoers file, you could add the two lines to a new file in /etc/sudoers.d 

e.g. 
```
/etc/sudoers.d/shutdown.
```

This is an elegant way of separating different changes to the sudo rights and also leaves the original sudoers file untouched for easier upgrades.

**Note!** Again, you should use the command visudo to edit the file to make sure you do not lock yourself out of the system:

```
sudo visudo -f /etc/sudoers.d/shutdown
```

This also automatically ensures that the owner and permissions of the new file is set correctly.


So, in this case, you need to run on the terminal

```
sudo visudo -f /etc/sudoers.d/**vbetool**
```

And we add there

```
your_user your_host = (root) NOPASSWD: /usr/sbin/vbetool
```

save the file. If everything is ok, we’re almost done.


[SIZE="2"]**So now what?**[/SIZE]

Just add this 2 commands as 2 separate keyboard shortcuts. You can test the commands without that, but once you blank your screen, you will feel lost and won't know how to turn it back on. There’s a trick though, don’t worry.

To add keyboard shortcuts refer to your favorite Ubuntu flavor how to do it. I’m on Lubuntu, so I have to edit a file by hand. I’ll not enter on details about that here, there are other howtos here on how to achieve that.

As for the commands, to **turn off** add as shortcut:

```
sudo vbetool dpms off
```

And to **turn** it back **on**:

```
sudo vbetool dpms on
```

But hey, I know you’re like me and you want to try the commands without the shortcuts. Go on and blank the screen. HOW DO I TURN IT BACK ON?!? (c'mon, don't do it) 

**The trick**:
If you have a keyboard shortcut to suspend your computer, suspend the computer. Then wake him up. The screen will be back on again.



Enjoy your your new blind typing machine and write your dreams with the new found pen of your imagination.

---

