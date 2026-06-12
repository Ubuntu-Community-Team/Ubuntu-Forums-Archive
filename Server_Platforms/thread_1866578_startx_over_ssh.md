---
title: "startx over ssh"
date: 2011-10-21
forum: Server Platforms
---

### Post by evarie on 2011-10-21
I search at all with google. Now i am tired about google after a week.


This is my terminal :

evarie@ubuntu-server.11.10:~$ dpkg-reconfigure x11-common
allowed_users=console


evarie@ubuntu-server.11.10:~$ startx

X: user not authorized to run the X server, aborting.
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
evarie@ubuntu-server.11.10:~$

---

### Post by dave01945 on 2011-10-21
you could try with sudo but can you explain why you want to startx over ssh

---

### Post by evarie on 2011-10-21
But i want only start x without root or sudo for safety reasons.
And for in the future i want keep my laptop clean as a client and my server in use as a server will do.

Please do not startx with root. I do not like it. Thanks

---

### Post by haqking on 2011-10-21
> **evarie said:**
> I search at all with google. Now i am tired about google after a week.


This is my terminal :

evarie@ubuntu-server.11.10:~$ dpkg-reconfigure x11-common
allowed_users=console


evarie@ubuntu-server.11.10:~$ startx

X: user not authorized to run the X server, aborting.
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
evarie@ubuntu-server.11.10:~$

If you mean you want to use graphical apps across ssh then you use:

ssh -X username@host

this allows you to run the remote graphical apps locally on your own local x server, mfor example once logged into the ssh session if you invoke gedit, it runs locally on your machine using your local X server but the app itself is running remotely

---

### Post by evarie on 2011-10-21
Yes i do : ssh -X user@192.168.2.x

I do this with a starter in ubuntu desktop on de iconbar.

I did also : xhost + 192.168.x.x

And xclock works good. But I want my hole desktop from my server through/with sshd.
So, there is no problem to start xclock.


Another try with Xnest :

user@ubuntuserver:~$ Xnest
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/100dpi/:unscaled, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/75dpi/:unscaled, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/100dpi, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/75dpi, removing from list!
[dix] Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server "localhost:10.0"
      after 135 requests (135 known processed) with 0 events remaining.

I did get a Xnest window, but it is only black.

---

### Post by ajgreeny on 2011-10-21
I don't think  you can run a complete xsession over ssh, or not simply, at least, but you can run the separate applications on the remote machine by starting them from the terminal that you get when the ssh connection has been made.

If you want a complete desktop, I think you need to run Remote Desktop, which I've never used.

I seem to remember reading that it is not as secure as ssh, so I would prefer just to ssh from client to server and start individual aps as needed

---

### Post by haqking on 2011-10-21
if you want a RDP solution that is secure then run VNC over a ssh tunnel

---

### Post by volkswagner on 2011-10-21
You can run your DE over ssh.  It is not a pretty solution and your session will likely complain if you already have a DE running.

In the past I have ran XFCE4 via ssh.

From memory the command was similar to:

```
ssh -X user@ubuntu xfce4-panel
```

I'm not sure what the command would be for your particular DE.

What is your remote machine running for DesktopEnvironment?

---

### Post by erixnow on 2011-10-22
Im confused now !   do you want to create an ssh tunnel and have a client server relationship with an Xwindows server ?

---

### Post by koenn on 2011-10-22
no, they're asking what *you* are trying to do.

in your OP, are you doing this at the keyboard of your server, or through ssh from your laptop ?

---

### Post by haqking on 2011-10-22
> **koenn said:**
> no, they're asking what *you* are trying to do.

in your OP, are you doing this at the keyboard of your server, or through ssh from your laptop ?

if you are responding to the post above you, they are not the OP ;-)

---

### Post by koenn on 2011-10-22
> **haqking said:**
> if you are responding to the post above you, they are not the OP ;-)

oops.

anyway, the question is still valid. startx in a plain ssh session is not going to work.

---

### Post by haqking on 2011-10-22
> **koenn said:**
> oops.

anyway, the question is still valid. startx in a plain ssh session is not going to work.

no worries, just pointing it out ;-)

Peace

---

### Post by pjlennon on 2012-04-10
Linux newbie and I don't know what I'm doing. After having ssh'd to my 10.0.4 box I tried to run [FONT="Courier New"]**startx**[/FONT] *(I just typed **startx** and pressed return)*. It didn't work so I instead physically went back to the 10.0.4 box to run the GUI. Apparently I've hosed something because now I can only run the GUI if type **% sudo startx **
Before I didn't have to **sudo** to run startx(*to start the GUI*). If I type only **startx** I get the following output.

[FONT="Courier New"]% startx
no protocol specified
..
no protocol specified
..
giving up
xinit : Resource temporarily unavailable (errno 11): unable to connect to X server
waiting for X server to shut down ddxSigGiveUp: closing log
xinit: server error
[/FONT]
What did I do? I tried restarting the whole box but the problem persists. Still, only if I now use sudo does it work. Does anyone know what I did and how I can fix it?

---

### Post by kevdog on 2012-04-11
Although one solution has already been proposed let me try to provide some light on the problem.

I tunnel X over ssh all the time to my windows box that acts as the client.  The client at all times needs an X server running.  This isn't a problem if the client is an Ubuntu or Linux box since an X server is built-in, but for windows with no native client I use a program called Xming. Just a major point of clarification.  The Xserver needs to be run on the CLIENT and not on the SERVER.  Yes I know this seems backwards, but the Xserver needs to run on the machine where the display is going to actually displayed.  In some cases you need to explicitly set the display variable, however we'll cover this if an error about not able to run the display is encountered.

Once the Xserver is running on the client, have the client connect over ssh to the ssh server.  This would be:

ssh -Y user@server
If ssh is run on a different port number, it would be:
ssh -p <port number> -Y user@server

Once inside the other box, I simply run, xfce4-panel&.  This gives me a very dumb GUI running only a xfce4-panel.  Its possible to run an entire gnome session or kde4 or xfce4 desktop (xfce4), however I would seriously advise not to do this since its really, really slow.  The xfce4-panel gives me a basic tool bar for a file browser (GUI) and terminal prompt.  From within the terminal, I can launch GUI programs such as gedit or firefox or whatever GUI program I need to.

Did this answer the question?

---

### Post by pjlennon on 2012-04-16
Thanks for your help. I'm so lost on this I don't even understand your answer. So the X server must be running on the client. I think that means that from my Mac I can use the X11 application. I managed from there to 
ssh -Y user@server
and then attempted
 xfce4-panel&
but I received the message 


[FONT="Courier New"]Last login: Mon Apr 16 09:06:48 2012 from ddb-dept-8.devbio.pitt.edu
/usr/bin/xauth:  error in locking authority file /home/ionadmin/.Xauthority
ionadmin@iontor104:~$ xfce4-panel&
[1] 5045
ionadmin@iontor104:~$ X11 connection rejected because of wrong authentication.
xfce4-panel: Cannot open display: 
ionadmin@iontor104:~$ 
[/FONT]
Wrong authentication is says. But I know I'm using the correct password for this administrative account. Could this be related to the above message "[FONT="Courier New"]error in locking authority file /home/ionadmin/.Xauthority[/FONT]" ?

---

### Post by biohazard2007 on 2013-01-08
Bumping and old thread here, but just in case if somebody needs this:
"x-session-manager" should start a new session (works for me)

---

### Post by cphuntington97 on 2013-05-20
If you want to connect to a tty by remote, you can install linuxvnc.

Ssh into your box, run linuxvnc, connect with vnc to the tty.

Then you can run commands like 'startx' and they will run as if you were sitting at the physical terminal.

Not sure if this is what OP wants to do, but it's what I want to do. :P

---

