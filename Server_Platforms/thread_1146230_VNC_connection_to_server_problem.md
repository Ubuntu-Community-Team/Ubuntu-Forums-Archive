---
title: "VNC connection to server problem"
date: 2009-05-02
forum: Server Platforms
---

### Post by torfosnaes on 2009-05-02
Ubuntu 9.04 server installed; dyndns active; port forwarding established; ssh works; webserver works.
RealVNC connection only works if a user is logged on to server already; if server is waiting with login screen VNC connection fails. Any suggestions or assistance using Webmin to solve problem much appreciated. Thanks.

---

### Post by HermanAB on 2009-05-02
Howdy,

VNC is mainly a Windows thing.  On Linux systems, SSH works much better and is more powerful.  So install ssh-server from synaptic then connect to it like so:
```
$ ssh -X -C -c blowfish user@server.example.com
```

and you can run GUI programs like so:
```
$ ssh -X -C -c blowfish user@server.example.com "gedit /etc/fstab"
```

or even
```
$ ssh -X -C -c blowfish user@server.example.com gnome-panel
```

and go click happy.

You can do that from Windows using Xming (run it first!) and PuTTY.

---

### Post by torfosnaes on 2009-05-03
Howdy and thanks Herman AB.
I now have hope, and a some questions, the answers to which should get me sorted out:

1. ssh is installed and running on my server box; synaptic doesn't show an "ssh-server" package; is your ssh-server something other than the standard ssh installed as part of the ubuntu 9.04 server distro?

2. I can ssh connect to server terminal from my laptop if I am outside the router; as the ssh connection times out from another computer inside the router am I correct that ssh connections MUST be from outside the router? If it should work from the same side of the router, what might be configured wrong on either computer (remote or server or both)?

3. is there a way to pretend to be outside the router so I can check the connection?

4. blowfish?

5. do I need anything special installed on the remote computer (outside the router) other than the standard terminal (it is running ubuntu 9.04)?

6. your gnome-panel command is to open the gnome desktop/menus; is this correct?

---

### Post by torfosnaes on 2009-05-03
Oh, gee!

That was easy; I am afraid I was over-complexifying the whole thing; thinking Windows instead of linux.
I am able to connect inside the router using ssh and sftp but have to go to an outside the router network connection to practice my newfound skills.

Thanks again Herman AB, your answer was the tip point to get me thinking clearly about server access.
Hopefully others will strike on our exchange and find their way.

Cheers.

---

### Post by HermanAB on 2009-05-03
Howdy,

Glad you got things going.  It is worth while reading the 'Snail Book' in order to explore the capabilities of SSH.

All you need for external access is to forward port 22 in your router to the server.  However, I strongly suggest that you configure a second listener on the SSH server and forward a non-standard port, in order to throw script kiddies off.

Edit file /etc/ssh/sshd_config and look for the 'Port 22' setting. If it is commented out, remove the ; and directly under it add 'Port 22222' (or whatever you fancy).  Then restart sshd and forward this weird port in the router.

---

### Post by rush_ad on 2009-05-06
on a similar but separate note, my problem is that i cannot connect to my home (ubuntu) laptop from work (XP) desktop using VNC viewer client.

from work, i could connect to my home XP using Remote Desktop. This tells me that at work, port 3389 (outbound) is open. but then i try to connect to my home VNC server i cannot connect. this tells me that port 5900 (outbound) is blocked from work.

now... how can i configure VNC so that it uses port 3389 instead of 5900?

---

### Post by HermanAB on 2009-05-06
Simple:
Uninstall VNC.
Install ssh-server.
Proceed as described above.

VNC is insecure and will get your laptop hacked if you expose it to the wild wild web.  Don't use VNC.

Note that Windows Remote Desktop is secure.  It is OK to use that over the internet.

---

### Post by brendan.lefoll on 2009-05-06
> **HermanAB said:**
> Simple:
Uninstall VNC.
Install ssh-server.
Proceed as described above.

VNC is insecure and will get your laptop hacked if you expose it to the wild wild web.  Don't use VNC.

Note that Windows Remote Desktop is secure.  It is OK to use that over the internet.

Just to reiterate RDP is a lot better than VNC, faster and more secure. There is little point to VNC for what you are doing.

---

### Post by rush_ad on 2009-05-06
> **brendan.lefoll said:**
> Just to reiterate RDP is a lot better than VNC, faster and more secure. There is little point to VNC for what you are doing.

security is not what i am concerned over. my laptop is no data on it. i use to play around with different operating system. most of the times it is not working anyway. hence... security is not at all something that i am worried about.

please tell me how to solve my problem regardless.

appreciate your help.

---

### Post by torfosnaes on 2009-05-07
Herman AB's ssh advice is good, it works, but there is a final problem I am encountering.

I can ssh to my server.
I can invoke sftp and get graphical navigation (explorer) screens and can move about the various folders.
I can click a file and have it open in appropriate app (swriter; scalc, etc.) and modify file BUT it won't save or save as an edited file.
I can navigate to Desktop, for example, and click on an app there and I get an error message saying that I can't run commands from a remote location with the added advisory that "This is disabled for security reasons."
Does this error come from the server or the remote laptop I am using to make the ssh connection?
Both are running ubunru 9.04.

I log on as a user to the server; then run sftp from the Secure Shell window and attempt to run apps on the server Desktop.

I have edited sshd_config and ssh_config on the server to forward X11 and AllowTcpForwarding; all the ports are set properly.
Are these two files the only controls over remote accessa nd use?
What else should I look for?
Should I be setting up the remote laptop in some special way or are the "security reasons" a function at the server only?

I'll bet Herman AB has the answer; that it is something simple and can be solved with a small edit to something or another.

Thanks in advance.

---

### Post by torfosnaes on 2009-05-08
When I log in over ssh through the terminal on the server provided by Secure SHell I see this

/usr/bin/X11/xauth:  /home/tor/.Xauthority not writable, changes will be ignored

OK. That appears to be the problem.
Now, what do I tune to solve this; and, will this allow for sftp to at leasr save documents; will this stop the Display error message when I try to, for example, sudo gedit filename, from the sderver terminal ??

So close ... so close!

---

### Post by torfosnaes on 2009-05-09
FInally, I discovered that user:group entry inn X11Authority on server was set to 0:0 instead of username:groupname.

As sson as I changed 0:0 to username (no group name yet) X11 works a treat.
Probably slow but working.

Next is to get in and tangle with the public and private keys stuff.

I've logged these events here in order to help someone el;se figure out why their server doesn't work out of the box; perhaps some ubuntu boffin can determine why this extra X11 tweak is required or why it isn't documented somehwere as being a potential problem.

Cheers and best of luck to everyone out there struggling with server setups.

---

### Post by windependence on 2009-05-09
> **brendan.lefoll said:**
> Just to reiterate RDP is a lot better than VNC, faster and more secure. There is little point to VNC for what you are doing.

I don't agree. RDP is not as secure as ssh. Herman is right on the money. This works great with a Mac BTW, since an X server is already built in.

-Tim

---

