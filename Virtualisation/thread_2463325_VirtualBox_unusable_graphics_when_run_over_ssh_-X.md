---
title: "VirtualBox unusable graphics when run over ssh -X"
date: 2021-06-08
forum: Virtualisation
---

### Post by &amp;KyT$0P# on 2021-06-08
So I'm trying to set up remoting into another machine over [FONT=Courier New]ssh -X[/FONT] on the same Wi-Fi LAN so that I can use VirtualBox on the server machine from the client machine.  VirtualBox runs fine.  VMs run fine (so far).  But it displays unusably badly.

In the VirtualBox manager interface, every visible "section" of the GUI is cut in half and one of each half does not redraw in real time.  When running VirtualBox VMs, there is a lot of display tearing on the VM screen and often the VM screen stops updating.

Both client and server machines are running Xubuntu 20.04.  VirtualBox version on the server is 6.0.24 and changing that is not currently an option.  (VirtualBox is not installed on the client, which is not powerful enough to run the VMs in question.)  [FONT=Courier New]LIBGL_ALWAYS_SOFTWARE=1[/FONT] is set because it fixed similar issues in other Qt 5 apps.  But it doesn't make any difference here (nor does setting it when physically on the server machine result in the issue showing up there).  [FONT=Courier New]QT_QPA_PLATFORMTHEME[/FONT] is not set, and setting it didn't make any difference to this issue.

Remoting into the VMs directly is not an option because they are disposable and sometimes they are offline live CD environments that don't have that capability available.

This setup will mostly be used to compile and test software, so I don't need or expect gaming-capable performance across the connection, but I do need to be able to see the graphics well and in real time.  How to get VirtualBox's graphics when used remotely over [FONT=Courier New]ssh -X[/FONT] to be on par with other remote apps' graphics?

---

### Post by Tadaen_Sylvermane on 2021-06-08
Wifi is one big problem. I'm not sure why but I've never gotten advertised bandwidth on any linux machine wifi regardless of my access points. On wired I can run my text editors and such, but video or anything with any real motion just sucks. I'm guessing a desktop experience just won't happen.

---

### Post by &amp;KyT$0P# on 2021-06-09
In light of post #2 I tried physically connecting both machines directly with a relatively short ethernet cable.  It was much faster than over the Wi-Fi LAN.  But it had no effect on this issue.

---

### Post by MAFoElffen on 2021-06-10
Just a few curiosities to give you some ideas. There are 100 ways to do the same thing...

Note that in the past, if I was doing ssh with X (with some of my personal servers and VM's on my KVM hosts), the performance was terrible, so I would do a minimum X install on top of Core, where XServer was loadable as an instance, and make the resolution intentionally lower, so that transport of X was a lot better. There was less graphics to transport. Because what happens with trying to do it that way (ssh with X on the same layer), is that the performance of the ssh Host gets hit with encrypting the X along with everything else... the on the other end, the ssh client has to unencrypt "everything." Does that make sense? Besides, if you "are" worried about security, there are lots of discussions on if ssh with X on the same layer is really that secure.

You know there are a lot better, more efficient ways to do that right? If you are worried about security (not a private network) then you can use shh for your tunnel, and use VNC as your X Session tunneled through it. The same with XRDP. That way, the only performance hit of encryption is to initially establish the tunnel. Once it is established (moments on two VM's) then it is just two VNC sessions talking with each other. It would be the same if you were using a VPN tunnel.

If you are on a private network, then you can just use VNC or XRDP without the tunnel.

---

### Post by &amp;KyT$0P# on 2021-06-10
Thanks for the reply MAFoElffen!

> **MAFoElffen said:**
> You know there are a lot better, more efficient ways to do that right?

Actually no I don't.  I could tunnel something else over SSH to get remote GUI apps.  Could you recommend or suggest something better than [FONT=Courier New]-X[/FONT] option of [FONT=Courier New]ssh[/FONT] for doing seamless integration of remote windows, including a dock (Plank in my case) and notifications (which I currently set up in a script manually run after logging in remotely)?

(As TheFu put it in another thread: what I've set up is basically "an integrated desktop, but without the desktop."  And I need to keep that design.)

---

### Post by MAFoElffen on 2021-06-10
[FONT=arial]Okay... Lets see if I can make this somewhat short and summarized. If too summarized, just ask questions to clear it up...

Let's say your server's effective IP is 192.168.1.8, running ssh server and has the default for Ubuntu, VNC app, Vino installed... ssh'es default port is 22. Vino's default port is 5900.
[/FONT]```

[FONT=arial]# open the ssh tunnel to the remote machine, using the listening port for Vino VNC on that machine...[/FONT][FONT=arial]
ssh -L 5900:localhost:5900 UserName@192.168.1.8
[/FONT]
```
[FONT=arial]When you connect from Vino from your client, to your server, instead of connecting to IP 192.168.1.8:5900, your are going to connect to localhost:5900, because you've already established the tunnel to that remote host and that is the entrance to it...[/FONT]

[FONT=arial]You can use any VNC or XRDP viewer you want, and just adjust the port listener to that specific viewer. [/FONT]

[FONT=arial]Note: Vino, does have it's own internal Vino-to-Vino encryption, which had problems connecting to dissimilar versions or to other VNC viewers, so to remedy that, you used to have fix that by turning the internal encryption off by issuing:[/FONT]
```

[FONT=arial]gsettings set org.gnome.Vino require-encryption false[/FONT]

```

---

### Post by &amp;KyT$0P# on 2021-06-10
Ok, so I looked into vnc type stuff and seems there isn't one that can do seamless.  So I decided to try using **both** vino/vnc tunneled through ssh **and** [FONT=Courier New]ssh -X[/FONT] .  And with that I can just run VirtualBox in the vnc session using KRDC as the client.  And no more screen tearing!

Problem solved - and this also has the added benefit that I can use the tunneled vnc also for stuff where I want to use the server machine's GPU.

The only thing I don't like about this is that the physical screen session must be unlocked and turned on for the vnc to work.  But I can live with that.

Thanks for your help MAFoElffen! :KS

* By the way, for other readers: being on Xubuntu, I configured vino with dconf-editor editing [FONT=Courier New]/org/gnome/desktop/remote-access[/FONT] .  Turns out this method of configuring vino is nice and intuitive.

---

### Post by MAFoElffen on 2021-06-10
You are very welcome. I'm happy that I could help. 

Thank you for remembering to mark this thread as Solved.

---

### Post by TheFu on 2021-06-10
**x2go** is 2-3x faster than vnc or rdp, and includes the ssh tunnel as part of the tunnel and authentication. By reducing the size of the image and letting x2go know the bandwidth you'd like used, it will compress the desktop images more efficiently.

On a LAN, **ssh -X** is 100x more convenient than VNC or rdp or x2go.  Plus, it doesn't have the full-desktop problem. Windows are integrated into the normal windows displayed on the client.  The X/buffer is shared between them - this is very convenient, but also a security issue.

Wifi performance is almost always a problem, at least for me.  It is bad enough that I don't use it with systems at home unless absolutely necessary.  Depending on the number of wifi clients connected and the wifi protocol level, the bandwidth could be halved with each new client.  In theory, AC (wifi-5) and later versions should be much better at that, provided no older clients are also connecting.  There's only so much RF bandwidth that can be shared. More clients means splitting that bandwidth between each of them.

Anyway, ssh -X should work between bridged virtual machine clients just fine.  Check that the IPs are on the same LAN, that each machine can ping the other and try **ssh -vvvvX** to see any issues with the connection.

---

### Post by scorp123 on 2021-06-11
> **halogen2 said:**
> So I'm trying to set up remoting into another machine over [FONT=Courier New]ssh -X[/FONT] on the same Wi-Fi LAN 

You can get more speed out of "ssh -X" if you play with the parameters and apply some tweaks. I myself use this command sequence a lot:
```
ssh -c aes128-ctr -C -X youruser@your.target.server.name
```

This gives me more than enough speed over WAN connections (e.g. I connect from my workplace to my PC at home to quickly open my web browser ...). For more serious desktop work I'd use a "x2go" session but for single applications this tweaked version of "ssh -X" should do.

What the parameters will do:

[LIST]
[*]-c aes128-ctr :  Use a faster 128-bit encryption instead of the safer but slower 256-bit or higher algorithms
[*]-C :  use compression
[*]-X :  Redirect X11 traffic. Together with the other parameters this should work a lot faster, programs should be more fluid.
[/LIST]

---

### Post by &amp;KyT$0P# on 2021-06-14
scorp123, thanks for trying to help but this is not a speed problem.  I had already played with all that before starting this thread, and using the optimal of those settings doesn't affect this issue even over direct wired connection.

Anyway I came back here to say that while the tunneled-VNC solution works for *starting* VMs, it isn't working so well for *using* the VM as some keys don't register properly through VNC.  Apparently this is a known issue with translating VNC keystrokes into key codes.  The workaround I chose is based on a post I found in VirtualBox forum: I use VNC for the VirtualBox manager interface and powering on the VM, but for actually working in the VM VirtualBox has its own RDP server (Settings > Display > Remote Display) which I can also tunnel through SSH and point KRDC to that.  It's not as fast as VNC but I think it's still good enough for my intended sort of use.

---

