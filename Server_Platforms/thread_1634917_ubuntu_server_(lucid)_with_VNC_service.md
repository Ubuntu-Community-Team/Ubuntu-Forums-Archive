---
title: "ubuntu server (lucid) with VNC service"
date: 2010-12-01
forum: Server Platforms
---

### Post by wonghang on 2010-12-01
Hi everyone,

  I have just installed a version of 32 bits Lucid LTS on a server box. I would like to setup a VNC service so that I will be able to login to the server with VNC viewer and spawn a gnome-session.
  I ran the following command:

```
apt-get install ubuntu-desktop
apt-get install Xvnc xinetd
```

  I was in front of the server and make sure that I can start a gdm locally. Then, I added Xvnc service to xinetd following the guide here:

[http://linuxreviews.org/howtos/xvnc/](http://linuxreviews.org/howtos/xvnc/)

  I was only using a session, and /etc/xinetd.d/Xvnc is as follow:


```
service Xvnc
{
	type = UNLISTED
	disable = no
	socket_type = stream
	protocol = tcp
	wait = yes
	user = root
	server = /usr/bin/Xvnc
	server_args = -inetd :1 -query localhost -desktop RemoteDesktop -geometry 1024x768 -depth 16 -rfbwait 30000 -rfbauth /etc/vncpasswd -fp /usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/Speedo/,/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/75dpi/,/usr/share/fonts/X11/100dpi/ -co /etc/X11/rgb -DisconnectClients -once 
	port = 5901
}
```

  Also, run "vncpasswd /etc/vncpasswd" for the password.

  Then, I modify the config at /etc/gdm/gdm.schemas to enable XDMCP:

```
    <schema>
      <key>xdmcp/Enable</key>
      <signature>b</signature>
      <default>true</default>
    </schema>

```
and allow for more hosts locally:

```
    <schema>
      <key>xdmcp/DisplaysPerHost</key>
      <signature>i</signature>
      <default>2</default>
    </schema>
```

  After all, I restart gdm by "/etc/init.d/gdm restart". When I try to start a VNC connection from another machine, I can see Xvnc running successfully. But XDMCP does not run properly and I cannot see a traditional ubuntu login screen. I am sure that port 177 UDP is opening by looking at the output of "netstat -anp".
  Is there anything missing? Please help.

  Thank you very much.

---

### Post by arrrghhh on 2010-12-01
I know this isn't the answer you're looking for, but it sounds like you're trying to fit a round peg into a square hole.

If you need/want a GUI, install ubuntu-desktop.  You'll get all the packages you installed with ubuntu-desktop, plus you can run any of the services you want sessionless just like ubuntu-server.

I just don't understand why anyone would want to add a GUI to ubuntu-server... that's kinda the point, run lean&mean with only essential packages installed/getting updated.

---

### Post by wonghang on 2010-12-01
yes...maybe I was using a wrong solution.

In fact, why I choose server edition is that I need to run a server  program written in Java, however, that server program is so terrible that its need a GUI display to make it works. Therefore, I come up with a Ubuntu Server+VNC solution.

I will try ubuntu desktop edition today. Hopefully it works.

Thanks.

---

### Post by arrrghhh on 2010-12-02
> **wonghang said:**
> yes...maybe I was using a wrong solution.

In fact, why I choose server edition is that I need to run a server  program written in Java, however, that server program is so terrible that its need a GUI display to make it works. Therefore, I come up with a Ubuntu Server+VNC solution.

I will try ubuntu desktop edition today. Hopefully it works.

Thanks.

You can always forward X apps over ssh using -X switch on the ssh connection.

If your client is Windows-based, look at putty and xming.

---

### Post by linknet on 2010-12-02
> **arrrghhh said:**
> You can always forward X apps over ssh using -X switch on the ssh connection.

If your client is Windows-based, look at putty and xming.

must be the same whether in WORKGROUP

---

### Post by arrrghhh on 2010-12-02
> **linknet said:**
> must be the same whether in WORKGROUP

Uhm... I'm sorry what?

---

