---
title: "Synergy"
date: 2010-04-19
forum: Security
---

### Post by Namibnat on 2010-04-19
I have two computers running side by side and would like to connect them with synergy so that I can use one keyboard to control both.

On the how to [https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto) it says that it is not very secure.  Does that mean that it is not very secure between those to computers or that it generally opens the computers up to vulnerabilities?

I use one computer as my main one and the other is basically justed used for ssh.  I can work fine as I do, but it would certainly be convenient to get rid of one keyboard.

---

### Post by OpSecShellshock on 2010-04-19
It's not secure because you're setting up one computer to be remotely controlled by another. The tutorial also appears to explain how to set the client computer up such that it is network enabled even without an active user session. Any one of those conditions would be bad enough by itself, but both together is probably an unnecessary risk if it's just for the sake of convenience. You'd be better off with a hardware KVM switch since they're right next to each other.

---

### Post by airtonix on 2010-04-19
> **OpSecShellshock said:**
> It's not secure because you're setting up one computer to be remotely controlled by another. The tutorial also appears to explain how to set the client computer up such that it is network enabled even without an active user session. Any one of those conditions would be bad enough by itself, but both together is probably an unnecessary risk if it's just for the sake of convenience. You'd be better off with a hardware KVM switch since they're right next to each other.

1. stream not encrypted, therefore
2. stream open to man-in-the-middle interception and injection.
3. buffer overflow checks untested.

simple : 

don't use it over un-encrypted networks if you really care.

---

### Post by Namibnat on 2010-04-19
Thanks

---

### Post by Dayofswords on 2010-04-19
call me crazy but.... use a splitter of some sort to avoid the security issue?

(they have to exist, just have it)

---

### Post by xpod on 2010-04-19
I`ve regularly used synergy for a good couple of years+ on our own network, which currently sits behind a standard router with built in firewall, and never had any problems with it.

EDIT: The QuickSynergy Gui, if you prefer one, makes for easy configuration.

---

### Post by a.walker on 2010-04-20
You can also run synergy through an SSH tunnel. I think there are instructions on the sourceforge site, but I'll admit it has been a while since I messed with it.

---

### Post by shazbut on 2010-04-20
I have synergy running across 3 machines, tunnelled over ssh, with the middle one being the server.
Here's the script for one of the client machines (replace serverIP as necessary):
```
killall synergyc
ssh -f -N -L localhost:24800:serverIP:24800 serverIP
synergyc --daemon localhost
```
I've saved it as ~/.synergy/startclient.sh , make sure it's executable, and linked it to a panel launcher.

On the server I just have a panel launcher with the command:
```
synergys --daemon -c ~/.synergy/synergy.conf
```

Also, on both client and server I have the file ~/.synergy/synergy.conf 
Replace LEFT/RIGHT/CENTRE with the hostnames of the machines (you won't need either LEFT or RIGHT for a 2 machine setup:
```
section: screens
	CENTRE:
	LEFT:
	RIGHT:
end
section: links
	CENTRE:
		left = LEFT
		right = RIGHT
	LEFT:
		right = CENTRE
	RIGHT:
		left = CENTRE
end

```

Then all I need to do is launch the server, then launch the client and enter the ssh password.

---

