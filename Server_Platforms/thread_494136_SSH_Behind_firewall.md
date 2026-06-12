---
title: "SSH Behind firewall"
date: 2007-07-06
forum: Server Platforms
---

### Post by mowbray on 2007-07-06
Hi, 

First post, so please accept apologies if this is the wrong forum...

I am new to Linux and have installed ubuntu 7.0.4 and the freenx packages for remote controlling it.

I want to remote control my machine from wherever I am on the Internet. I have setup my netgear firewall router to forward connections on port 22 to my ubuntu server, and the nomachine nx client on my laptop prompts for a user name and password to login when I connect.

What I am wondering about is if anyone can tell me if there are further steps I ought to take to secure my setup? I usually restrict connections to only those coming from my office IP address, but as I am going to be travelling a fair bit I dont want that restriction at present. I have seen quite a few attempts to connect to the port 22 on my machine in the last few days so I am wondering if I am opening my machine up for the whole world to have a go at, or is the ssh/nx security good enough not to worry too much?

Thanks in advance

---

### Post by madcow72 on 2007-07-06
Hey!  Great choice for an OS, and I hope you'll be very happy with the choices for VNC remote desktop that come by default in Ubuntu.  I am actually unfamiliar with freenx, but if all you want to do is remote desktop, then you just need to do the following:

[LIST]
[*]Instructions
Make sure that your firewall will recognize your remote IP address outside the firewall and port forward 5500-5900 to the dhcp address of the computer you want to remote control.  

Then, on your Ubuntu box behind the firewall, go to System -> Preferences -> Remote Desktop and check: "Allow other users to view your desktop", "Allow other users to control your desktop", and "Require the user to enter this password:"  (then give it a password.)

Uncheck the box: "Ask you for confirmation." because you most likely won't be at both computers at the same time to give yourself permission ;).

Now you're set up to VNC to your computer behind the firewall.  Assuming your computer on the outside is also Ubuntu, then you go to Applications -> Internet -> Terminal Server Client

On "Computer:" give it the ip address to your router/firewall, choose Protocol = VNC, and then give it the username for the account on the computer behind the firewall.

Finally, hit "Connect" and a little box will show up asking you for the password you chose earlier.  Once you enter that, a window will show up containing the desktop session for your VNC'd connection.  That's it!
[/LIST]

I know I just now wrote a lot, but I tend to be detailed.  It's really very easy.

Good luck!

---

### Post by madcow72 on 2007-07-06
Oh yeah, per your original question about ssh, just make sure you've added port 22 (as you said you did) and point it toward the internal IP for your firewalled computer just the same as the VNC connection.  Then, on your external computer, you should be able just:
```
ssh -l username ipaddress
```
to connect.

---

### Post by nix4me on 2007-07-06
You could always change the ssh port to something other than 22.  That will keep alot of the hacking attempts down.

Its easy to do in the config file.

nix4me

---

### Post by darkog on 2007-07-06
_to change ssh port:_

```
sudo nano /etc/ssh/sshd_config
```

change the entry 

```
port 22
```

to some other number other than 22.

```
sudo /etc/init.d/ssh restart
```

check [IANA]("http://www.iana.org/assignments/port-numbers") to make sure the port you choose isn't used by popular services or software.

---

### Post by snoop on 2007-07-06
Also installing fail2ban might help. I believe it locks people out after a certain number of tries. This should stop brute force attempts. Changing the port is also a good idea. Also, you may want to disable root logins for the ssh user(unless you need to admin the computer of course). This would prevent harm even if someone got in. 

And freenx is good stuff. Very handy.

---

### Post by mowbray on 2007-07-13
Thanks for all the replies. Already noticed someone trying to brute force a password from somewhere in south america, so looks like I will be changing the ports and locking down a bit more.

If I disable root login over ssh, will this stop me running commands using sudo once I am logged in with my ordinary user account?

TIA

---

### Post by Footballkid4 on 2007-07-13
No, if you want to stop running sudo commands, type:

```
sudo visudo
```

And remove the last line that says:

```
%admin ALL = (ALL) ALL
```

However, I wouldn't exactly advise that you do it.  By the way, just because SSH denies root login, you can still login as any ordinary user and then su to root if you have the root account setup.

---

