---
title: "Access Home Computer from another location."
date: 2009-12-14
forum: Server Platforms
---

### Post by Sugi on 2009-12-14
I want to setup access via OpenSSH Server or use the best method possible to access my home computer from my parent's house.  So of course, I have access to both firewalls and both computers that will only be used by me.

I haven't tried this before, but I found a nice step by step process on how to set this up. (See below)

My only questions are, 

Will this be any different for me that I have access to both firewalls and computers freely?

> Use the command "netstat -lntp" to see that vino-server is listening on port 5900 and that sshd is listening on port 22. All OK? Hopefully. Don't continue until this part is working. Use that web page you have to get and write down your home IP address assigned by your ISP (but remember it could change so you may need to config dyndns).

Can I just use my Router's IP table to find out what's my IP?  And I also already have dyndns setup, so if I'm correct, I wouldn't need my IP for this step, just use the dyndns instead?

> It will prompt for your password and if it can login successfully then you now have a tunnel to your home machine.

Is this password we talk about from the OpenSSH?  So, I should look into a tutorial on how to setup OpenSSH server?

I have used Remote Desktop Viewer access my friend's computer, but it was terrible slow and I could ONLY control his mouse.  Clicking and keyboard commands didn't work. :/  This won't be a problem with OpenSSH, right?


Sorry for all of these question.  I'm not at home yet, but when I get there I want to be prepared to setup everything correctly.

Specs:
Both Computers running Ubuntu 9.10
dysdns already setup
access to both firewalls

Thanks everyone for reading,
Sugi


> **BkkBonaza said:**
> Maybe I can make this more step by step.

For VNC using a secure tunnel - forward, normal style...

Use Synaptics to select and install openssh-server on your home machine.

Select menu System, Prefs, Remote Desktop and choose the check mark to enable.
(In Ubuntu Remote Desktop is installed by default and is VNC using vino-server. vino-server listens for a connection on port 5900 by default).

Ok. So now vnc is listening on port 5900. Ideally you should further config vino to only listen for local connections not internet connections. AFAIK this has to be done with a command,

gconftool-2 --set /desktop/gnome/remote_access/local_only --type bool true

VNC will now not accept connections from the net but only from the local LAN. In your case that should mean only your machine. That's good.

Use the command "netstat -lntp" to see that vino-server is listening on port 5900 and that sshd is listening on port 22. All OK? Hopefully. Don't continue until this part is working. Use that web page you have to get and write down your home IP address assigned by your ISP (but remember it could change so you may need to config dyndns).

Now go to work or somewhere else on the net. Open a terminal shell and type,

ssh -f user@homeip -L 5900:localhost:5900 -N

Of course, replace user with your user name and homeip with your home IP address.
It will prompt for your password and if it can login successfully then you now have a tunnel to your home machine.

So what's going on now? ssh will listen on 5900 on your work machine and direct any traffic to port 5900 on your home machine. But what's listening on 5900 at home? vino-server. Hence, any traffic to 5900 on the work machine (localhost) is tunnelled to 5900 vino-server at home.

Lastly, at work open a remote desktop viewer, menu item Applications, Internet, Remote Desktop Viewer. Choose VNC, and enter localhost and Connect. If successful then it should now show you your home desktop.

There are other ways to do this as well. But this should work and is fairly straightforward. You can make a shortcut icon for the ssh command.

If you need a reverse tunnel instead because you can't open ports at home on your ISP connection then let me know. It's only slightly different.

This first time we've done some config but after this at work you only need the ssh command (set up a shortcut icon) and then start the remote dekstop. What could be easier? You could install gSTM with Synaptics - it will give a gui interface to ssh tunnels instead of the command.

What else? After you have this working you can take the extra steps to make it more secure. The page mentioned by CharlesA above has details.
[http://ubuntuforums.org/showthread.php?t=1353579&highlight=remote+desktop&page=2]("http://ubuntuforums.org/showthread.php?t=1353579&highlight=remote+desktop&page=2")



Update:
I had one issue, I couldn't get ssh to use port 22 and I had to switch it to another port to get Remote Desktop Viewer to work with ssh.

The Fix:
If port 22 is already in use, you need to change SSH's port.

 - Edit the SSHD, to change the port number
# sudo gedit /etc/ssh/sshd_config

Default:
# What ports, IPs and protocols we listen for
Port 22

Change to:
# What ports, IPs and protocols we listen for
Port 2314

*Use some random number

 - Then restart the SSH
# sudo /etc/init.d/ssh restart

Use this command when starting the localhost
-p portnumber

Example:
ssh -f -p 2314 user@homeip -L 5900:localhost:5900 -N



Thanks everyone and enjoy,
Sugi


PS:  I want to specially thank BkkBonaza for his time and effort.  I wouldn't be able to run SSH right now if it wasn't him.

---

### Post by BkkBonanza on 2009-12-14
> **Sugi said:**
> 

Will this be any different for me that I have access to both firewalls and computers freely?

No. But you will need the server firewall to be open for ssh on port 22.

> **Sugi said:**
> 
Can I just use my Router's IP table to find out what's my IP?  And I also already have dyndns setup, so if I'm correct, I wouldn't need my IP for this step, just use the dyndns instead?

You can use your dyndns domain or IP however you get it.

> **Sugi said:**
> 
Is this password we talk about from the OpenSSH?  So, I should look into a tutorial on how to setup OpenSSH server?

The first step in the step by step tells you how to install openssh. The password is your normal user login password.

> **Sugi said:**
> 
I have used Remote Desktop Viewer access my friend's computer, but it was terrible slow and I could ONLY control his mouse.  Clicking and keyboard commands didn't work. :/  This won't be a problem with OpenSSH, right?

The speed depends completely on your connection speed. SSH doesn't make it faster or slower, it simply secures the connection with encryption. The mouse/keyboard behavior depends on VNC settings. If you disable "control" in the Remote Desktop Settings then you cannot control the desktop, just view it.

---

### Post by Sugi on 2009-12-14
With the VNC and connecting to my friend's computer, the screen wasn't refreshing.  I could see his desktop, but when he opened an application it wouldn't come up on my VNC viewer.

If I could get the default Control Desktop Viewer/VNC viewer to work with my friend's computer, (IE: control his mouse clicks, keyboared commands, and refreshing the screen.)  What would be the advantages to using OpenSSH server over VNC viewer?  Well except for the point with VNC viewer you have to be at both computers, one to accept the request and the other to control the other computer.  And if I understand this correctly, the VNC viewer/Remote Desktop Viewer isn't a secure connection between both computers?

Thanks for the fast replies and helpful comments,
Sugi

---

### Post by BkkBonanza on 2009-12-14
It's VNC that you are running over SSH, not the other way round.
SSH just acts as a secure transport, it secures the traffic so that anybody sniffing your connection isn't able to log and view it - and hence, get your login password or other important details. ie. use SSH to secure your VNC usage. When connected locally in the same room this isn't really an issue but if you want to control your computer from across town via the net then this is abig issue - much more so if using wifi, because everything is broadcast and can be easily captured out of the air.

The whole purpose of VNC is that you don't need to be at both ends. What good is remote control if you need to be at both computers? The problem you're having is that you haven't chosen suitable options in the Remote Desktop settings. One option is that you have to manually confirm the request to take control, and anothe option is even allowing control. If you are actually using this remotely then both those options need to be set correctly. ie. no confirm required and control allowed.

---

### Post by Sugi on 2009-12-15
vino-server and sshd are on different ports.  Should I just go with them?  or change them to the default ports?

Thanks,
Sugi

---

### Post by BkkBonanza on 2009-12-15
You can use whatever ports suit you. People often change the ports to obscure their use. Just need to adjust the ssh command to match the ones actually being used by VNC.

---

### Post by Sugi on 2009-12-15
Everything is up and running.  I want to specially thank BkkBonaza for his time and effort.  I wouldn't be able to run SSH right now.

My problem?  I couldn't get ssh to use port 22 and I had to switch it to another port to get Remote Desktop Viewer to work with ssh.

The Fix:
If port 22 is already in use, you need to change SSH's port.

 - Edit the SSHD, to change the port number
# sudo gedit /etc/ssh/sshd_config

Default:
# What ports, IPs and protocols we listen for
Port 22

Change to:
# What ports, IPs and protocols we listen for
Port 2314

*Use some random number

 - Then restart the SSH
# sudo /etc/init.d/ssh restart

Use this command when starting the localhost
-p portnumber

Example:
ssh -f -p 2314 user@homeip -L 5900:localhost:5900 -N


Thanks guys and enjoy,
Sugi

---

