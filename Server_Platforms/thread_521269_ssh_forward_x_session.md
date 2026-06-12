---
title: "ssh forward x session"
date: 2007-08-09
forum: Server Platforms
---

### Post by hmhmhm on 2007-08-09
Hi,

I've recently installed an Openssh server on my server (sudo apt-get install openssh-server) and I am able to remotely logon to a console via ssh. However, I have no luck forwarding an x session with ssh -X -Y user@ip.
So far I've set "x11forwarding yes" in the /etc/ssh/sshd_config file on the server.
Thanks for any ideas!

---

### Post by EndPerform on 2007-08-09
Did you remember to restart the ssh server after your configuration change.  If not, you'll need to do that.

---

### Post by hmhmhm on 2007-08-09
I've restarted now, but still not working.
Not sure if I'm doing the right thing, but when I enter

xhost +client_ip

on the server console, it says:

xhost: unable to open display ""

Any suggestions?

---

### Post by EndPerform on 2007-08-09
When you get logged in via ssh -X hostname, type:

```
echo $DISPLAY
```

And see if that contains anything.  What OS is on the server?

---

### Post by hmhmhm on 2007-08-09
First of all thanks for the super quick replies EndPerform, really appreciate that!
When I enter echo $DISPLAY it says:

localhost:10.0

---

### Post by hmhmhm on 2007-08-09
...sorry, forgot to answer your question.
I'm running Ubuntu 7.04 Feisty Fawn server edition.

---

### Post by steve.horsley on 2007-08-10
I don't know what your problem is, but I can confirm a few things which may reduce your problem space a little.

I have done **ssh -X user@ip** from desktop to desktop no problems (using Dapper, Edgy and Feisty). I just checked, and echo $DISPLAY gives:
> steve@StevesPC:~$ echo $DISPLAY
localhost:10.0

which is what you get. So that looks good. You don't need to do the xhost + bit when using SSH X tunneling. I wonder if your problem is that your server is missing some critical X libraries (because X isn't installed at all?).

---

### Post by hmhmhm on 2007-08-10
That's a good point Steve. It may well be a missing library. I've only installed a light version of Gnome (see below) so there might be some libraries missing. Is there any way I can find out which ones? Or do I have to do a full Gnome installation (which I really didn't want to...)?

Here's how I installed the light Gnome desktop:

```

sudo apt-get update

sudo apt-get install x-window-system-core gnome-core gnome-media gnome-system-monitor gnome-system-tools gnome-utils gnome-app-install synaptic firefox

startx

```

---

### Post by woifi on 2007-08-11
hi!

i don't think there is a library missing.

in your sshd_config on your machine running openssh-server you should have this lines:```
X11Forwarding yes
X11DisplayOffset 10
```

and in your ssh_confog on your client you have to comment this line out:```
ForwardX11 yes
```

when you log in with **ssh -X user@server** you should be able to launch programs.

hth

woifi

---

### Post by hmhmhm on 2007-08-11
I can confirm that the 2 config files had these already included. On the client machine, there are only a few more settings like this:

> 
Host *
        GSSAPIAuthentication yes
ForwardX11Trusted yes


That's all there is in the client config file. All the other lines are preceeded by a #. There's heap more stuff in the server config file though. Please let me know if I should list them.

When I type ssh -X -Y user@server-ip, I get a 

> 
/usr/bin/X11/xauth:  error in locking authority file /home/hmair/.Xauthority


Not sure if this has something to do with it...but I still can log on to the console.

---

### Post by hmhmhm on 2007-08-17
I'm using Fedora 4 as the client. Would it make a difference if I use Ubuntu?
Thanks,
hmhmhm

---

