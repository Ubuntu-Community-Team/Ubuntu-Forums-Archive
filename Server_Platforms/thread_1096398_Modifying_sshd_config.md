---
title: "Modifying sshd_config?"
date: 2009-03-14
forum: Server Platforms
---

### Post by gibxam on 2009-03-14
Hello I'm trying to secure my SSH server via a couple adjustments: denying root login, changing the port I listen on, and making it so that I am the only user on my computer that can access my ssh server. I know that I have to modify the sshd_config file but I can't because I don't have permission, I've been searching around the forums/google but no one else seems to have this problem so I though I would ask. Thanks in advance :)

Max

---

### Post by littlegreiger on 2009-03-14
You don't have the permissions for it because it's owned by root. So you'll have to do something like ```
sudo nano -w /etc/ssh/sshd_config
```

---

### Post by hictio on 2009-03-14
> **gibxam said:**
> Hello I'm trying to secure my SSH server via a couple adjustments: denying root login, changing the port I listen on, and making it so that I am the only user on my computer that can access my ssh server. I know that I have to modify the sshd_config file but I can't because I don't have permission, I've been searching around the forums/google but no one else seems to have this problem so I though I would ask. Thanks in advance :)

Max

You have to use 'sudo' to do that. And not only 'sudo', but also a text editor; It'll ask your password before allowing you to do so.
Login to your Ubuntu Server box, and type:

```

sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bkp.14032009 ENTER

```

So you have a working copy no matter what, it is always wise to do so :D

Then open your favorite text editor:

```

sudo nano /etc/ssh/sshd_config ENTER

```

(You can use Emacs, vi, pico, whatever rocks you boat or whatever you have installed, but, remember, smart people use Emacs :D ;)  )

Edit your settings on the file, those should be:

```

Port XXXXX
PermitRootLogin no
AllowUsers your.Username.Here

```

And then, re-load the the sshd service config file (no need to re-init it):

```

sudo /etc/init.d/sshd reload ENTER

```

As usual, if you are accessing the server *only* thru ssh, be double and triple careful with typos, don't get lockup outside of your box.

---

### Post by gibxam on 2009-03-14
Terrific! thank you problem solved :)

---

### Post by gibxam on 2009-03-15
I've been trying to set up remote connection between my computer and another on my LAN but I keep getting connection refused and connection timed out messages. I checked out the ssh documentation on this site and it said to type ```
 ssh localhost 
```, I tried this and got ```
 ssh: connect to host localhost port 22: Connection refused 
```, then I remembered that I had changed the port # that listens for ports, IPs and protocols to **** in my sshd_config file; so I tried to adjust my command to ```
ssh localhost -p ****
``` but got the same result.

Has this been the reason why I haven't been able to access this box or others in my LAN?

How do I fix this problem?

Also I was using PuTTy on my brothers computer that runs xp (this computer is on my LAN) and why I tried tunneling to port **** his virus scanner detected a virus that didn't look like it had anything to do with the tunneling I was trying to do (AKA something about online videos) 

Can I transmit virus accidentally by tunneling to different computers on my LAN that do not run linux?

Lastly is it possible for me to adjust the title of this thread to something more applicable to my current question? I don't want to inundate the forums with new threads about the same type of thing but right now the title doesn't really reflect my question.

Thank you for any help you provide,

Max

---

### Post by windependence on 2009-03-15
You need to specify a user when using ssh. Here is an example:

```
ssh -p 1234 user@localhost
```

Otherwise, ssh will assume you want to ssh as the user you are logged on as. This is not always what you want to do. If you are sshing from a windows box, it assumes you want to ssh as the windows user.

-Tim

---

### Post by hictio on 2009-03-15
The best thing you can do, if you'll have to type all that (username, port) each time you'll connect to a given server, then create (or edit) a text file called 'config' on the (hidden) directory on the $HOME of the Linux box you are.
Like this:

```

nano ~/.ssh/config ENTER

```

And then add something like this:

```

Host server00 ## An easy to rember short name
        HostName sever00.somedomain.com ## FQDN or IP address of the remote server
        User the.Username.Of.The.Remote.Server
        Port xxxx # The port of the sshd on the remote server

```

---

### Post by gibxam on 2009-03-15
Thank you very much I now have ssh up and running perfectly! I can access my computer from any computer on my LAN provided they have ssh installed properly. I have yet to try it on a computer outside my network but, I am sure I'll be able to do it via tunneling. :)

Now I'm trying to get vncserver and vncviewer up and running so that I can work with my computer on a more visual level rather than just the terminal when start my vncserver via ```
vncserver
``` command this is the output
```
Couldn't start Xvnc; trying default font path.
Please set correct fontPath in the vncserver script.

New 'X' desktop is max-desktop:9

Starting applications specified in /home/max/.vnc/xstartup
Log file is /home/max/.vnc/max-desktop:9.log

```
Then If I am experimenting on my own computer and use the vncviewer via ```
vncviewer max-desktop:9
``` then I have success and vncviewer opens a new window with my desktop in it. However when I try to do this on another computer I get ```
Error: Can't open display 
```.

Could this have anything to do with these two lines of output when I start vncserver ```
Couldn't start Xvnc; trying default font path.
Please correct fontPath in vncserver script.
```?

If so, how do I correct this problem?
If not, how do I correct my vncserver script? And why is would I be getting the error message about not being able to start display when I am on another machine?

Thank you very much for all the help. I'm so close! :)

Max

---

### Post by Jack1989 on 2009-03-15
Hi, if you have ssh running, you don't need vnc, just hit CTRL + ALT + F2 and then login and type this (starts the X server):
```
xinit -- :1
```

Then you login via ssh
```
ssh -X username@domain.com
``` 

And then you starting a new gnome-session:
```
gnome-session
```

Of course you don't need to start a whole new gnome-session, it's okay with just gnome-panel, nautilus and metacity. If you choose to do this, skip the first steps and just start a terminal.

This is much faster and easier than vnc!

To return to your local gnome session:
CTRL + ALT + F7 (can be different, if so, try all of them, F7 - F12)

---

### Post by gibxam on 2009-03-15
Hey jack

Does the method your describing only work with computers that are both running linux?

I tried this on my brothers computer that is running XP with cygwin and it didn't like it too much.

xinit -- :1 - Didn't work unless I used sudo before, then session started but didn't allow me to type in any other commands unless i hit ctrl+C which terminated x session.

-logging in to ssh- When I connect to my computer isn't that already logging in via ssh?

gnome-session - this doesn't work, as because the other os is xp, correct?

I'm still curious how to get vnc up and running if I cannot get this to work.

Max

---

### Post by gibxam on 2009-03-16
I can get into my computer using PuTTy from an XP computer however I cannot start vncviewer!
Once I get in, I connect to the vncserver:
```

max@max-desktop:~$ vncserver

New 'X' desktop is max-desktop:12

Starting applications specified in /home/max/.vnc/xstartup
Log file is /home/max/.vnc/max-desktop:12.log

max@max-desktop:~$ 

```

Then i try to start vncviewer:
```

max@max-desktop:~$ vncviewer max-desktop:12

```
then I get an error
```

Error: vncviewer cannot display ""

```

How can I solve this problem?

Max

---

### Post by Jack1989 on 2009-03-16
It's like you say, it only works on Linux, and maybe Unix too.  You can do it, like you said, on Windows with some software. I've tried it, and yes, it's not good!

gnome-session should work even on XP, it did with me. But use gnome-panel instead, much faster than the entire dekstop.

xinit -- :1 (or another number) should work without sudo, you should do that on your own computer, not the server. And then it will start a terminal so you can connect/login via ssh. And from there you can start a program and forwarding the X-signals from the server to your X.

```
Error: Can't open display
```
I got that to when I used vnc!
This worked for me:

[SIZE="2"]Have you tried this (the easiest way in Ubuntu):[/SIZE]

**On the server:**
System -> Preferences -> Remote Desktop
 * Allow other users to view your desktop

**On the client:**
Applications -> Internet -> Terminal Server Client
 * Computer: the servers ip
 * Protocol: VNC
 * Password: if you have a password

[ Connect ]

Good Luck

---

### Post by gibxam on 2009-03-17
Jack Success!

I hadn't allowed remote connection from my own computer! Using vncviewer I can now connect no problem to my computer. However I don't understand; what is the point of SSH and even the vncserver and PuTTY if all I need to do is run the tightvnc viewer and I can connect/manipulate/view my computer?

Anyways, thank you Jack for your explanations, I'm going to try your other methods that you described later tonight.

Max

---

### Post by Jack1989 on 2009-03-17
Hi, nice!

My method is the same as yours, just that its easier and i don't think you have to think about displays.

There's no point of using SSH, it's just me who thinking that it's easier. But I can only access my server from a Linux computer, but I can live with that :-)

I don't really know what Putty is, but you probably wont need it, only a server and a client, like tightvncviewer.

// Jack

---

