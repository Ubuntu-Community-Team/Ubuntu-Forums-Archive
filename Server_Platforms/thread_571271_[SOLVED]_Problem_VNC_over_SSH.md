---
title: "[SOLVED] Problem: VNC over SSH"
date: 2007-10-09
forum: Server Platforms
---

### Post by piercleo on 2007-10-09
Hello,

I'm trying to setup a VNC over SSH connection in order to be able to access my home CPU from my two laptops when I am away (and it happens a lot).

I've been trying for two days following many howto's and reading a lot of documentation, I just can seem to make it work. At the moment, i'm stuck at the VNC part.

So, I am running Feisty on all three computers. On all of them I did the following:

- System --> Preferences --> Remote Desktop

I have the following Remote Desktop Preferences:

Sharing -> Allow other users to view your desktop (Checked)
Allow other users to control your desktop (Checked)

Security ->
Ask you for confirmation (Un-Checked)
Require the user to enter this password: (Checked)
Password: I entered my password

- System -> administration -> firestarter: I opened a vnc port on 5900

- I use Terminal Server Client.

- At the moment, all three computers are behind the same router... i'll try VNC over the internet with SSH after, one thing at a time :-)

Now here is the thing: I want to be able to take control of all my CPU's desktop from any of the computers.
I am able to take control of my work laptop from my personal laptop and from my home computer.
When I try to take control of my personal laptop or of my home computer with my work laptop I get the following mistake:

"vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server"

I don't even get to enter my password !

If anybody has any idea it would be great. I am leaving on a shoot in two weeks for quite some time and I need to have access to my personal computer from my work laptop when I'll be away.

Thanks in advance,

Piercleo

---

### Post by dmizer on 2007-10-09
unless you have all of the following:

1) a gigabit local network
2) home broadband connection with bandwidth out the wazoo ('out the wazoo' = more than you know what to do with)
3) remote broadband connection with bandwidth out the wazoo.

remote vnc over ssh is probably not your best option here as it will be ploddingly slow and unusable.  what exactly are you hoping to accomplish by using vnc?

for example, if you use a command like:
```
ssh -Y you@yourhomemachinesip
```
you'll get command line access that will allow you to open gui applications (like firefox, rhythm box, gaim/pidgin, etc) on your remote box simply by typing their command.  so something like:
```
ssh -Y you@yourmachinesip
firefox
```
will give you firefox on your remote machine, but you will be browsing using your connection at home.  it's still a bit laggy, but far better than vnc, and at least usable if you have a moderately fast connection.

if your remote machine is windows, you can install [cygwin](http://www.cygwin.com) and use linux applications in an x environment.

---

### Post by HermanAB on 2007-10-09
Hmm, there is always more than one way to do it.  VNC works.  SSH works.  However, tunneling VNC over SSH is kinda redundant, since SSH can do everything you want to do already.

If you are running Linux on your laptop, then the trick is to ensure that the laptop and desktop use different desktop systems.  That is, if the laptop uses Gnome, make sure that the desktop has KDE installed and configured or vice versa.

Then if the laptop is running Gnome, do this:
$ ssh -X -C -c blowfish user@desktop
Password: whatever
$ kicker

Otherwise, if the laptop is running KDE:
$ gnome-panel

and click away...

If the laptop is running Windows, then install Cygwin with OpenSSL, or Xming with PuTTY, then run either gnome-panel or kicker.

Cheers,

Herman

---

### Post by piercleo on 2007-10-09
Hello, and thank you both for your answers,

Let's do this in order of importance:

*What do I want to do ?* When I am away for work (with my work laptop) of in holidays (with my leisure laptop), I want to be able to access documents (music, movies, open office documents) from my desktop. I will also need to launch some applications on the desktop. I work in the movie production field and I often have some directors who send me some big video files. Hence, I need to launch an application on the desktop so that when I get home I can watch the video that has been downloaded on my CPU; Last, i need to launch GAIM and thunderbird on the desktop and be able to take control of those applications from my laptop.

Next, let's start with Herman AB:

*"SSH can do everything you want to do already" :* i tried VNC yesterday and I find it amazing to be able to take control of a remote desktop from another computer. Will I be able to do this thanks to SSH ?

*"The trick is to ensure that the laptop and desktop use different desktop systems"*: I have Ubuntu on all three computers and since I am quite new to Linux, it kind of makes me feel better to have only one universe to apprehend. Is there no way to keep my settings and still get the same result ?

Now Dmizer:

No I don't have such an awesome connection as you describe. I have read a lot about VNCoverSSH being slow and I am not at all against doing it in another way if I find such a way. Yet, it seemed like a pretty safe way to do what I need and I kind of don't want everybody to have access to my files. I have no industrial secrets but still, I'd rather keep some intimacy :-)

I tried using the command you gave me (which is a first for me since I have no knowledge whatsoever about command lines). Nothing happened !
Maybe I am putting in the wrong information.
Since I am home right now testing, I wrote (after the @) the local IP (192.168.0.80) of the CPU I want to access (the desktop). As for the "you" part, I put in my session name of the laptop from which I am trying to access the desktop CPU.

Argh, i does seem all quite complicated and I already thank in advance anybody that would help me but I am a stubborn man and I really don't like it when I don't understand something ! So i'll just keep on looking for an answer.

Bye,

Pierre

EDIT: i just succeeded in using vncviewer to take control of my desktop CPU. I don't know what changed since yesterday, I just tried again using the Terminal Server Client and it worked.
And now the problem begins:  I have a screen problem, my desktop screen is way bigger than my laptop one and when I take control of the desktop I can only see a part of the windows and I need to scroll arg !

---

### Post by HermanAB on 2007-10-09
BTW, I don't know what will happen if you SSH in and launch gnome-panel when your local desktop is also gnome.  I know that KDE screws up spectacularly if you run kicker while the local machine is also running it - I don't know why it screws up though, but the end result is that you got to press ctrl-alt-backspace and blow X away.  So, just for kicks, go ahead and launch gnome-panel and see what happens.

It seems that you are beginning to discover why VNC isn't so hot.  I only use SSH and launch the programs I want to run straight off the CLI.  If you know the name of a program, then you can run it.  Running the panel is just a pointy-clicky convenience, not necessary.  Most program names are obvious, like firefox, thunderbird, gedit, gimp...

---

### Post by piercleo on 2007-10-09
Well since my last post I've been reading like crazy about this.

I followed your advice and was able to use ssh. In my case, I chose to use putty and was able to access my desktop.

Thing is I used my 192.168.0.80 adress, but when I won't be at home, I won't be able to use this adress right ? How do I know which adress to use when I'm away ?

Best regads,

Piercleo

PS: do I have a solution to transfer files from one CPU to another ?

---

### Post by bodhi.zazen on 2007-10-09
IMO ssh is very powerful. ssh -x to forward applications is nice, if your client is windows you need a X server (I use Cygwin).

From windows you can transfer files with winscp : 

[http://winscp.net/](http://winscp.net/)

For Linux -> Linux just use scp 

IMO the advantage of VNC is the viewer provides a X server and, IMO, it is faster then forwarding your desktop over an ssh connection.

To connect you open a port for **ssh** then tunnel VNC over ssh.

You need to configure you router to forward you port.

You need to get your IP address from your internet provider, or look here:

[http://showip.net/](http://showip.net/)

You will use this IP to connect. Now since you IP provider likely uses dhcp, your IP may change, so use something like this :

[http://www.dyndns.com/](http://www.dyndns.com/)

See these links :

[uwiki]SSHHowto[/uwiki]

[uwiki]VNCOverSSH[/uwiki]

Be sure to secure your ssh server :

[uwiki]AdvancedOpenSSH[/uwiki]

And for fun, see this

[http://ubuntuforums.org/showthread.php?t=541656](http://ubuntuforums.org/showthread.php?t=541656)

Note, this is not as secure, but it is fun :twisted:

---

### Post by piercleo on 2007-10-09
Thanks a tons Bodhi,

I've been reading tons of stuffs but the links are great. There is so much documentation you tend to easily get lost.

Anyway, I succeeded in doing a VNC over SSH connection and t works perfectly.

I also managed connecting in SSH but when I try to launch firefox I get the following error message: "(firefox-bin:11552): Gtk-WARNING **: cannot open display: "  (any idea where it might come from ?)

That's the reason why I ended up doing VNC over SSH.

I still have a couple of problems:

1 - I tried doing VNC over SSH when my session was closed on the remote CPU and got the following error

channel 3: open failed: connect failed: Connection refused
ReadFromRFBServer: rdr::EndOfStream

2. When I connect using VNC over SSH, I get an awfull screen resolution (my laptop screen is way smaller than the desktop one, and I end up only seeing part of the remote desktop which is quite annoying (even if, it's true, I can use the scrollbar).

I'm getting closer guys :-)

Thanks in advance...again.

---

### Post by HermanAB on 2007-10-09
Hmm, some help:
a. Cannot Open Display: It means that you forgot to run an X server on Windoze.  Install Xming from Sourceforge (Or install Cygwin), and remember to run it before you run Putty.
b. You can get your public IP address from the status panel in your home router configuration utility.  If it has a web based (all have these days) use a browser and go to [http://192.168.1.1](http://192.168.1.1) or whatever it is.  You also have to forward port 22 TCP to your desktop, to ensure that when you go to the public IP address port 22, you will get to the Desktop port 22.

Cheers,

Herman

---

### Post by piercleo on 2007-10-09
He he, found my ip managed to redirect the port from the router to my desktop. I even went to the neighbours'  house to test it and I was able to connect without any problem. One thing though, the keyboard didn't work whereas it was working when I did an VNC over SSH using the local ip !

Regarding the X server (in order to be able to launch applications using ssh): i am not using windows on any of the CPU, the are all Fesity Fawn. Do i still have to connect to a X server ?

Any idea regarding the screen resolution thing ?

Good night all, i'll check again tomorrow.

Best regards and thanks soooo much again.

Pierre

---

### Post by HermanAB on 2007-10-09
Ubuntu runs X to do the graphics, so all you need to do is ensure that you enable X forwarding in SSH.  Either turn it on permanently in /etc/ssh/ssh_conf, or supply the parameter '-X' on the command line:
$ ssh -X -C -c blowfish user@server

Legend:
-X: Enable X forwarding (need a local X server!)
-C: compress (good for a slow modem connection)
-c blowfish: fastest encryption (reduces processor load)

You should be able to loop back and log into your own computer simply by doing ssh from your desktop (or laptop) to your external public IP address, which will then come in again.

Once logged in, run a simple X application, such as gedit or gnome-calculator and see if it comes up.

Cheers,

H.

---

### Post by eldragon on 2007-10-10
may i add:

X forwarding never worked for me thorugh an internet connection, but im on 256kbit upload. through LAN works like a charm on a 100mbit connection

im doing vnc through ssh the following way:

instead of the Vino server (system, preferneces, remote desktop), i installed x11vnc because Vino was having some preformance issues.

i start x11vnc with the following command every time my session logs in (drawback, i have to be logged for it to work)

```
x11vnc -display :0 -shared -forever -scale 2/3
```

all options taken from man x11vnc

im not using a password since im not opening the 5900 port through the router, im tunneling it through the ssh session.

then, prior to running the vnc client, 

```
ssh -L 5900:localhost:5900 username@ssh.server.ip
```

which will pass all connections to the 5900 port on the client machine through the tunnel to the server's 5900 port.

so to connect the vnc session you just run 

```
vncviwer localhost
```
cheers

---

### Post by dmizer on 2007-10-10
to do xforwarding over ssh, you need to install a local x server on your windows machine.

i gave you the link for cygwin earlier, it contains both a windows x server as well as an ssh client.

then, open cygwin and type:
startx

then ssh to your remote server, and then you can open your applications from the command line.  don't expect to be doing any remote video editing though, there's just not enough bandwidth in the world for that.  but with ssh, it's easy enough to transfer those files to your local machine.

using the -Y option is more secure because it obfuscates passwords -X option does not, though otherwise the two options are identical.

---

### Post by piercleo on 2007-10-10
Ok guys, I am much more advanced then yesterday morning, thanks to your help.

I'm still having this screen resolution problem when I launch VNC over SSH but I found many posts about this so I'll just keep reading.

Thanks a lots, 

This is the reason I came to Linux: being able to have a CPU that matches my exact needs and so far, I must say I'm not disappointed, even if some things need time to set up...but at least, what is done is done.

Best regards and huge thanks,

Bye Piercleo

---

### Post by piercleo on 2007-10-10
How do I put solved in the title f the thread ? not just in the answer ?

EDIT: ok i found out all by myself :-)

---

### Post by dmizer on 2007-10-10
edit your first post, there's an option for it.

---

### Post by krunge on 2007-10-10
> **dmizer said:**
> using the -Y option is more secure because it obfuscates passwords -X option does not, though otherwise the two options are identical.

No, -Y is less secure than -X.  Under -Y the X clients are not subjected to the SECURITY X extension, and therefore can do more (e.g. read/write all properties, snoop keystrokes, etc).

A main drawback of the SECURITY X extension is that it breaks a lot of apps because they expect that they can read/write properties, etc. The most common example is if you try to paste into an app under SECURITY it crashes.

However, it is a good idea to try to use it, especially if you don't know much about the trustworthiness of the users on the remote machine.

AFAIK, both -Y and -X do the fake mit-cookie obfuscating you refer to.

---

### Post by krunge on 2007-10-10
> **eldragon said:**
> i start x11vnc with the following command every time my session logs in (drawback, i have to be logged for it to work)

Not really, have a look here:

[http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager")

but you will need root or sudo access to do it (basically to be able to read the display manager mit-cookie file, e.g. /var/gdm/:0.Xauth).

---

### Post by dmizer on 2007-10-10
> **krunge said:**
> No, -Y is less secure than -X.  Under -Y the X clients are not subjected to the SECURITY X extension, and therefore can do more (e.g. read/write all properties, snoop keystrokes, etc).

i stand corrected.  thank you.

---

### Post by bodhi.zazen on 2007-10-10
> **piercleo said:**
> Ok guys, I am much more advanced then yesterday morning, thanks to your help.

I'm still having this screen resolution problem when I launch VNC over SSH but I found many posts about this so I'll just keep reading.

Thanks a lots, 

This is the reason I came to Linux: being able to have a CPU that matches my exact needs and so far, I must say I'm not disappointed, even if some things need time to set up...but at least, what is done is done.

Best regards and huge thanks,

Bye Piercleo

Take a look at the link in vnc over ssh : [uwiki]VNCOverSSH[/uwiki]

If you use an alternate vnc server (tightvnc, vnc4server) you can start a new session with :

vncserver -geometry 800x600 -depth 16 :1

OR

vnc4server -geometry 800x600 -depth 16 :1

Change the geometry and depth to what you want (I use 1280x1024  and a depth of 24)

The :1 changes the port to 5901

---

