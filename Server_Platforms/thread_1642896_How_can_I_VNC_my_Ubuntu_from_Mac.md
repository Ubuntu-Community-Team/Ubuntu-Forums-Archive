---
title: "How can I VNC my Ubuntu from Mac?"
date: 2010-12-11
forum: Server Platforms
---

### Post by yangjiangnan on 2010-12-11
I have installed VNC Server x11vnc on my Ubuntu 10.10 according to instructions on [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC) .
I can ssh to my Ubuntu from my macbook OS X 10.6 through home router and get output like:
...
11/12/2010 00:18:51 screen setup finished.
11/12/2010 00:18:51 
The VNC desktop is:      localhost:0
PORT=5900
...

However, no matter what I tried, I cannot use a VNC client to view my Ubuntu desktop from my macbook. Every time connection failed. I have tried Chicken of the VNC and some other vnc clients, but they just don't work. Can somebody tell me how can I connect to my Ubuntu, please? I wanna know which client is used and its version or download link, and exactly how to set it up.

Many thanks!

---

### Post by BugBuster on 2010-12-11
Can your mac "see" the vnc service on Ubuntu. You could run a port scan from the mac on your ubuntu computer to check that. Also Ubuntu desktop comes with a VNC server pre-installed. Check out System -> Preferences -> Remote Desktop. Did you try it?

---

### Post by krunge on 2010-12-11
> **yangjiangnan said:**
> 
I can ssh to my Ubuntu from my macbook OS X 10.6 through home router and get output like:
...
11/12/2010 00:18:51 screen setup finished.
11/12/2010 00:18:51 
The VNC desktop is:      localhost:0
PORT=5900
...

However, no matter what I tried, I cannot use a VNC client to view my Ubuntu desktop from my macbook. Every time connection failed.
Please show the entire remaining x11vnc messages including when you try to connect via the vnc viewer.  The above you show is before any viewer tries to connect.

Also indicate what you typed into the vnc viewer to specify the vnc server.

---

### Post by yangjiangnan on 2010-12-11
> **BugBuster said:**
> Can your mac "see" the vnc service on Ubuntu. You could run a port scan from the mac on your ubuntu computer to check that. Also Ubuntu desktop comes with a VNC server pre-installed. Check out System -> Preferences -> Remote Desktop. Did you try it?
 
Thanks. But how can I run a port scan?
Now I have tried Remote Desktop and successfully connected to my Ubuntu by Chicken. However, when I scroll up and down this website (using Firefox) using two fingers from Chicken of the VNC, it does not work right. Every time when I scroll up, it directly goes to the bottom. I guest this is a bug of Chicken. 

And when I set the desktop sharing on Ubuntu, it said:"Your desktop is only reachable over the local network. Others can access your computer using the address 192.168.0.2 or jiangnan-PC.local." So, can I connect Ubuntu via Internet rather than just from home? Can use some portforwarding on the router to achieve this?
Finally, Chicken seems to have too few options to set, is it possible that the connection would be too slow if I connect via Internet? Any solutions to this? Thanks.

---

### Post by yangjiangnan on 2010-12-11
> **krunge said:**
> Please show the entire remaining x11vnc messages including when you try to connect via the vnc viewer.  The above you show is before any viewer tries to connect.

Also indicate what you typed into the vnc viewer to specify the vnc server.


First, I typed "ssh jiangnan@192.168.0.2" and connected to Ubuntu from Mac. Then 

jiangnan@jiangnan-PC:~$ x11vnc -safer -localhost -nopw -once -display :0
10/12/2010 23:56:26 -safer mode:
10/12/2010 23:56:26    vnc_connect=0
10/12/2010 23:56:26    accept_remote_cmds=0
10/12/2010 23:56:26    safe_remote_only=1
10/12/2010 23:56:26    launch_gui=0
10/12/2010 23:56:26 x11vnc version: 0.9.10 lastmod: 2010-04-28  pid: 5083
10/12/2010 23:56:26 Using X display :0
10/12/2010 23:56:26 rootwin: 0xac reswin: 0x7400001 dpy: 0xa37c30
10/12/2010 23:56:26 
10/12/2010 23:56:26 ------------------ USEFUL INFORMATION ------------------
10/12/2010 23:56:26 X DAMAGE available on display, using it for polling hints.
10/12/2010 23:56:26   To disable this behavior use: '-noxdamage'
10/12/2010 23:56:26 
10/12/2010 23:56:26   Most compositing window managers like 'compiz' or 'beryl'
10/12/2010 23:56:26   cause X DAMAGE to fail, and so you may not see any screen
10/12/2010 23:56:26   updates via VNC.  Either disable 'compiz' (recommended) or
10/12/2010 23:56:26   supply the x11vnc '-noxdamage' command line option.
10/12/2010 23:56:26 
10/12/2010 23:56:26 Wireframing: -wireframe mode is in effect for window moves.
10/12/2010 23:56:26   If this yields undesired behavior (poor response, painting
10/12/2010 23:56:26   errors, etc) it may be disabled:
10/12/2010 23:56:26    - use '-nowf' to disable wireframing completely.
10/12/2010 23:56:26    - use '-nowcr' to disable the Copy Rectangle after the
10/12/2010 23:56:26      moved window is released in the new position.
10/12/2010 23:56:26   Also see the -help entry for tuning parameters.
10/12/2010 23:56:26   You can press 3 Alt_L's (Left "Alt" key) in a row to 
10/12/2010 23:56:26   repaint the screen, also see the -fixscreen option for
10/12/2010 23:56:26   periodic repaints.
10/12/2010 23:56:26 
10/12/2010 23:56:26 XFIXES available on display, resetting cursor mode
10/12/2010 23:56:26   to: '-cursor most'.
10/12/2010 23:56:26   to disable this behavior use: '-cursor arrow'
10/12/2010 23:56:26   or '-noxfixes'.
10/12/2010 23:56:26 using XFIXES for cursor drawing.
10/12/2010 23:56:26 GrabServer control via XTEST.
10/12/2010 23:56:26 
10/12/2010 23:56:26 Scroll Detection: -scrollcopyrect mode is in effect to
10/12/2010 23:56:26   use RECORD extension to try to detect scrolling windows
10/12/2010 23:56:26   (induced by either user keystroke or mouse input).
10/12/2010 23:56:26   If this yields undesired behavior (poor response, painting
10/12/2010 23:56:26   errors, etc) it may be disabled via: '-noscr'
10/12/2010 23:56:26   Also see the -help entry for tuning parameters.
10/12/2010 23:56:26   You can press 3 Alt_L's (Left "Alt" key) in a row to 
10/12/2010 23:56:26   repaint the screen, also see the -fixscreen option for
10/12/2010 23:56:26   periodic repaints.
10/12/2010 23:56:26 
10/12/2010 23:56:26 XKEYBOARD: number of keysyms per keycode 6 is greater
10/12/2010 23:56:26   than 4 and 2 keysyms are mapped above 4.
10/12/2010 23:56:26   Automatically switching to -xkb mode.
10/12/2010 23:56:26   If this makes the key mapping worse you can
10/12/2010 23:56:26   disable it with the "-noxkb" option.
10/12/2010 23:56:26   Also, remember "-remap DEAD" for accenting characters.
10/12/2010 23:56:26 
10/12/2010 23:56:26 X FBPM extension not supported.
10/12/2010 23:56:26 X display is capable of DPMS.
10/12/2010 23:56:26 --------------------------------------------------------
10/12/2010 23:56:26 
10/12/2010 23:56:26 Default visual ID: 0x21
10/12/2010 23:56:26 Read initial data from X display into framebuffer.
10/12/2010 23:56:26 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/5464
10/12/2010 23:56:26 WARNING: Width (1366) is not a multiple of 4. VncViewer has problems with that.
10/12/2010 23:56:26 
10/12/2010 23:56:26 X display :0.0 is 32bpp depth=24 true color
10/12/2010 23:56:26 
10/12/2010 23:56:26 Autoprobing TCP port 
10/12/2010 23:56:26 Autoprobing selected port 5902
10/12/2010 23:56:26 Listening also on IPv6 port 5902 (socket 10)
10/12/2010 23:56:26 
10/12/2010 23:56:26 Xinerama is present and active (e.g. multi-head).
10/12/2010 23:56:26 Xinerama: number of sub-screens: 1
10/12/2010 23:56:26 Xinerama: no blackouts needed (only one sub-screen)
10/12/2010 23:56:26 
10/12/2010 23:56:26 fb read rate: 197 MB/sec
10/12/2010 23:56:26 fast read: reset wait  ms to: 10
10/12/2010 23:56:26 fast read: reset defer ms to: 10
10/12/2010 23:56:26 The X server says there are 12 mouse buttons.
10/12/2010 23:56:26 screen setup finished.
10/12/2010 23:56:26 

The VNC desktop is:      localhost:1
PORT=5901

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: [http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)


Then, in the SSVNC which is an "Enhanced TightVNC Viewer", I typed localhost:1 in the VNC Host:Display field and clicked connect, but the connection just failed. And in Chicken of the VNC, when I did the same thing, I got "Could not connect to server localhost:1, connection refused: connect()."

---

### Post by mathspeedy on 2010-12-11
You need to enter the IP address of the Ubuntu box not localhost.
Localhost is the computer you're on. 
For Internet use, you need to setup portforwarding and remember the IP address of the router, or use a free DNS provider.

---

### Post by krunge on 2010-12-11
> **yangjiangnan said:**
> First, I typed "ssh jiangnan@192.168.0.2" and connected to Ubuntu from Mac. Then 

jiangnan@jiangnan-PC:~$ x11vnc -safer -localhost -nopw -once -display :0
10/12/2010 23:56:26 -safer mode:
10/12/2010 23:56:26    vnc_connect=0
10/12/2010 23:56:26    accept_remote_cmds=0
10/12/2010 23:56:26    safe_remote_only=1
...

The VNC desktop is:      localhost:1
PORT=5901

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: [http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)


Then, in the SSVNC which is an "Enhanced TightVNC Viewer", I typed localhost:1 in the VNC Host:Display field and clicked connect, but the connection just failed. And in Chicken of the VNC, when I did the same thing, I got "Could not connect to server localhost:1, connection refused: connect()."

Your log shows that NO VNCVIEWER whatsoever initiated a connection to your x11vnc process.  So we have to solve that problem (you are not trying to connect correctly)

I suggest adding "-L 5901:localhost:5901" to your SSH command line. This is required; it enables an encrypted SSH tunnel for port 5901 between the two machines.

And then add "-rfbport 5901" to your x11vnc cmdline (please don't skip this.)

And then use "localhost:1" in your Mac VNC viewer (either SSVNC or Chicken of the VNC)

Some Mac's don't know what "localhost" is.  If that is your case, use "127.0.0.1:1" instead of "localhost:1".

Report back here how it goes.

---

### Post by krunge on 2010-12-11
> **mathspeedy said:**
> You need to enter the IP address of the Ubuntu box not localhost.

No he/she has to use localhost (and I assume wants to).  He is using SSH for tunnelling so the viewer connects to localhost to go through the SSH tunnel.

Note that "-localhost" was supplied to the x11vnc cmdline, so some sort of tunnel connection must be used. Incoming ethernet connections will be denied when using this option.

---

### Post by yangjiangnan on 2010-12-11
> **krunge said:**
> No he/she has to use localhost (and I assume wants to).  He is using SSH for tunnelling so the viewer connects to localhost to go through the SSH tunnel.

Note that "-localhost" was supplied to the x11vnc cmdline, so some sort of tunnel connection must be used. Incoming ethernet connections will be denied when using this option.

Yes. I wanna use the SSH tunnel. And by using the two command line you suggested, I successfully connected to my Ubuntu via Internet. Thanks!

I list them as below:

1. Install ssh and x11vnc on Ubuntu. Forward port 22 to Ubuntu PC's IP in the router.
2. On mac terminal, run: ssh username@ip  -L 5901:localhost:5901
3. After open the ssh, run " x11vnc -safer -localhost -nopw -once -display :0 -rfbport 5901 "  on Ubuntu.
4. Use SSVNC to connect to localhost:1, using None at the bottom rather than SSL or SSH.

I can only connect by SSVNC, but not Chicken of the VNC, that's kinda weird. But that's enough. :D

---

### Post by mathspeedy on 2010-12-11
Damn, I didn't notice he was trying to tunnel his VNC session via SSH. :tongue:
I was on my iTouch and didn't read everything...

---

### Post by krunge on 2010-12-11
> **yangjiangnan said:**
> Yes. I wanna use the SSH tunnel. And by using the two command line you suggested, I successfully connected to my Ubuntu via Internet. Thanks!
Glad you got it working!
> 
I can only connect by SSVNC, but not Chicken of the VNC, that's kinda weird. But that's enough. :D
I wonder what is happening with Chicken of the VNC for you; it works for me.  But SSVNC vnc viewer is much better than Chicken of the VNC of course. :-)

BTW, since you are using SSVNC, you can click on Options -> Mode -> Terminal Services (tsvnc).  Then enter "username@ip" in the "VNC Terminal Server" entry.  When you then click on "Connect" it will 1) start SSH tunnel for you automatically and 2) start x11vnc for you automatically.  You can save it in an ssvnc profile to Load whenever you want to use it.

Alternatively, you can select "Use SSH" and enter the x11vnc commandline you desire (i.e the one you mention in your post) in "Remote SSH Command".

In both cases you will need to supply a password or passphrase to ssh (either in terminal or in ssh gui prompt depending on your setup) to log in to the ubuntu machine.  ssh-agent is handy for automating this.

---

### Post by yangjiangnan on 2010-12-11
> **krunge said:**
> Glad you got it working!

I wonder what is happening with Chicken of the VNC for you; it works for me.  But SSVNC vnc viewer is much better than Chicken of the VNC of course. :-)

BTW, since you are using SSVNC, you can click on Options -> Mode -> Terminal Services (tsvnc).  Then enter "username@ip" in the "VNC Terminal Server" entry.  When you then click on "Connect" it will 1) start SSH tunnel for you automatically and 2) start x11vnc for you automatically.  You can save it in an ssvnc profile to Load whenever you want to use it.

Alternatively, you can select "Use SSH" and enter the x11vnc commandline you desire (i.e the one you mention in your post) in "Remote SSH Command".

In both cases you will need to supply a password or passphrase to ssh (either in terminal or in ssh gui prompt depending on your setup) to log in to the ubuntu machine.  ssh-agent is handy for automating this.

Thank you. But it does not seem to be working this way. When I did exactly using your first method, all I got was a terminal that quickly disappeared, saying:

Last login: Sat Dec 11 18:34:51 on ttys001
/tmp/darwin_terminal_cmd.16641-328215197.4.Ff6iLg ; exit;
Jiangnan-Yangs-MacBook-Air:~ yangjiangnan$ /tmp/darwin_terminal_cmd.16641-328215197.4.Ff6iLg ; exit;
try-1: termpid= mypid=16670
try-2: termpid= mypid=16670
try-3: termpid=16644 mypid=16670

SSVNC_LIM_ACCEPT_PRELOAD=/Users/yangjiangnan/Downloads/ssvnc/bin/Darwin.i386/lim_accept.so

Running ssh:
env DYLD_FORCE_FLAT_NAMESPACE=1 DYLD_INSERT_LIBRARIES=/Users/yangjiangnan/Downloads/ssvnc/bin/Darwin.i386/lim_accept.so ssh -x -x -f  -t -C -D 5930  "jiangnan@192.168.0.2" "PORT= x11vnc -display WAIT:cmd=FINDCREATEDISPLAY-Xvfb -localhost -nopw -timeout 120 -o $HOME/.tsvnc.log.yangjiangnan -env FD_SESS=kde -env AUTO_PORT=5950"

/Users/yangjiangnan/Downloads/ssvnc/bin/util/ss_vncviewer: line 3023: 16832 Trace/BPT trap          $ssh -x -f $ssh_port $targ $C $ssh_redir $ssh_args "$uath" "$ssh_cmd" > $tport 2> $tport2
found: PORT=''

ssh_pid=''

PPROXY v0.4: a tool for Web, SOCKS, and UltraVNC proxies and for
PPROXY v0.4: IPv6 and VNC VeNCrypt bridging.
proxy_host:       127.0.0.1
proxy_port:       5930
proxy_connect:    127.0.0.1:
pproxy_params:    socks5://127.0.0.1:5930
pproxy_listen:    5961
pproxy_reverse:   
io_socket_inet6:  1

pproxy 1st: 127.0.0.1:5930	- socks5
pproxy 2nd: 	- 
pproxy 3rd: 	- 

pproxy interface: localhost
pproxy: listening on localhost:5961
vncviewer -noraiseonbeep -encodings copyrect tight zrle zlib hextile -encodings copyrect tight zrle zlib hextile 127.0.0.1:61

pproxy: Connection refused
pproxy: Connection refused / Connection refused
vncviewer.x11: VNC server closed connection

VNC Viewer exiting.

vncviewer command failed: 0
Done. You Can Ctrl-C this Terminal if you like. Use Ctrl-\ to pause.
sleep 5





The alternative method does not work either. I think the problem is it is impossible to run the x11vnc command before I ssh to the server and create a tunnel for ssvnc. I use username@ip in the VNC Host:Display field, select Use SSH and then enter the x11vnc command as the Remote SSH Command, but again, it does not work. In the terminal:

Last login: Sat Dec 11 19:42:40 on ttys001
Jiangnan-Yangs-MacBook-Air:~ yangjiangnan$ /tmp/darwin_terminal_cmd.23686-276296802.5.Ii6tfx ; exit;
try-1: termpid= mypid=23715
try-2: termpid= mypid=23715
try-3: termpid=23689 mypid=23715
+ ssvnc_cmd -ssh -sshcmd 'x11vnc -safer -localhost -nopw -once -display :0 -rfbport 5901' jiangnan@192.168.0.2 -noraiseonbeep -encodings 'copyrect tight zrle zlib hextile'

SSVNC_LIM_ACCEPT_PRELOAD=/Users/yangjiangnan/Downloads/ssvnc/bin/Darwin.i386/lim_accept.so

Running ssh:
env DYLD_FORCE_FLAT_NAMESPACE=1 DYLD_INSERT_LIBRARIES=/Users/yangjiangnan/Downloads/ssvnc/bin/Darwin.i386/lim_accept.so ssh -x -x -f  -t -C -L 5930:127.0.0.1:5900  "jiangnan@192.168.0.2" "x11vnc -safer -localhost -nopw -once -display :0 -rfbport 5901"

dyld: could not load inserted library: /Users/yangjiangnan/Downloads/ssvnc/bin/Darwin.i386/lim_accept.so

/Users/yangjiangnan/Downloads/ssvnc/bin/util/ss_vncviewer: line 3023: 23864 Trace/BPT trap          $ssh -x -f $ssh_port $targ $C $ssh_redir $ssh_args "$uath" "$ssh_cmd"

ssh to "jiangnan@192.168.0.2" failed.
+ set +xv

Done. You Can Ctrl-C this Terminal if you like. Use Ctrl-\ to pause.

sleep 5

---

### Post by krunge on 2010-12-11
Hmmmm, I wonder what is happening.

Please try this. Before connecting, do: Options -> Advanced and then UNSET 'SSH Local Port Protections'.  Maybe that trick is broken on your version of macosx..

---

### Post by yangjiangnan on 2010-12-12
> **krunge said:**
> Hmmmm, I wonder what is happening.

Please try this. Before connecting, do: Options -> Advanced and then UNSET 'SSH Local Port Protections'.  Maybe that trick is broken on your version of macosx..


Wow... You are so right! It works! Thank you very very much! :D

---

### Post by krunge on 2010-12-12
> **yangjiangnan said:**
> Wow... You are so right! It works! Thank you very very much! :D
I guess something changed in macosx 10.6.  I only have access to 10.5 machines. However, I will be able to test on a 10.6 laptop in a couple weeks so I will check then.

---

### Post by krunge on 2010-12-12
> I guess something changed in macosx 10.6.  I only have access to 10.5 machines. However, I will be able to test on a 10.6 laptop in a couple weeks so I will check then.
Well I put in a check to see if the SSH local port protection feature works and to disable it if not.  I uploaded it to  the 1.0.29 development SSVNC tarballs:

[INDENT][http://www.karlrunge.com/x11vnc/ssvnc.html#download](http://www.karlrunge.com/x11vnc/ssvnc.html#download)[/INDENT]

Try it if you get the chance and let me know how it goes.  It should work out of the box without any need to manually disable the feature (be sure you have the feature enabled if you use a saved profile.)

---

### Post by yangjiangnan on 2011-01-04
> **krunge said:**
> Hmmmm, I wonder what is happening.

Please try this. Before connecting, do: Options -> Advanced and then UNSET 'SSH Local Port Protections'.  Maybe that trick is broken on your version of macosx..

 I encounter a serious problem when using VNC. My Ubuntu on PC often crashes when I use SSVNC on Mac to connect to the Ubuntu desktop and use it. The Ubuntu usually automatically turn into a black screen and then display the user login window. And after I walk to the PC and log in, all the opened programs have been closed, just like after restarting the computer or re-login. At the beginning of the connection, the VNC works fine. However, suddenly, when I open a website or do some other stuffs in Ubuntu from SSVNC on Mac, I first seen the black screen on the PC monitor and then VNC disconnection on Mac. This does not always happen, but happens frequently after connected for a few minutes or tens of minutes. 
After disconnection, the terminal opened by SSVNC displays the following (I repeated the process twice, each time ending with the Sleep 5 line, and "disable via env SSVNC_DELAY_SYNC=0 if there are painting errors" was displayed BEFORE the disconnection):

Last login: Tue Jan  4 20:15:58 on ttys000
/tmp/darwin_terminal_cmd.4004552280738.2.0r52Jy ; exit;
Jiangnan-Yangs-MacBook:~ yangjiangnan$ /tmp/darwin_terminal_cmd.4004552280738.2.0r52Jy ; exit;
try-1: termpid= mypid=4012
try-2: termpid= mypid=4012
try-3: termpid=4007 mypid=4012

Running ssh:
ssh -x -x -f  -t -C -D 5930  "jiangnan@192.168.1.2" "PORT= x11vnc -display WAIT:cmd=FINDCREATEDISPLAY-Xvfb -localhost -nopw -timeout 120 -o $HOME/.tsvnc.log.yangjiangnan -env FD_SESS=kde -env AUTO_PORT=5950"

jiangnan@192.168.1.2's password: 
found: PORT='5950'

ssh_pid='4156'



PPROXY v0.4: a tool for Web, SOCKS, and UltraVNC proxies and for
PPROXY v0.4: IPv6 and VNC VeNCrypt bridging.
proxy_host:       127.0.0.1
proxy_port:       5930
proxy_connect:    127.0.0.1:5950
pproxy_params:    socks5://127.0.0.1:5930
pproxy_listen:    5960
pproxy_reverse:   
io_socket_inet6:  1

pproxy 1st: 127.0.0.1:5930    - socks5
pproxy 2nd:     - 
pproxy 3rd:     - 

pproxy interface: localhost
pproxy: listening on localhost:5960
vncviewer -noraiseonbeep -encodings copyrect tight zrle zlib hextile 127.0.0.1:60

proxy_request1: SOCKS5 via 127.0.0.1:5930 to 127.0.0.1:5950

pproxy parent[4289]  listen_handle -> socket
pproxy child [4298]  socket -> listen_handle


Proto: RFB 003.008

Connected to RFB server, using protocol version 3.8
Security-Type: 1 (rfbSecTypeNone)  Latency: 6228.17 ms
No VNC authentication needed
VNC authentication succeeded (0) for rfbSecTypeNone (RFB 3.8)

Desktop name "jiangnan-PC:0"

VNC server default format:
  32 bits per pixel.  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Using default colormap which is TrueColor.  Pixel format:
  32 bits per pixel.  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
geometry: 1366x768+35+43 ycrop: 0
create_image()
try_create_image: shm image create fail: image == NULL
try_create_image: created *non-shm* image: 1366x768
try_create_image: image->bytes_per_line: 5464

guessed: -compresslevel 8
guessed: -qualitylevel  4
enabling 'delay_sync' mode for faster local drawing,
disable via env SSVNC_DELAY_SYNC=0 if there are painting errors.
pproxy[4298]: Input is EOF.
pproxy[4298]: finished xfer.
pproxy[4298]: kill TERM parent 4289
pproxy[4289]: got SIGTERM.
vncviewer.x11: VNC server closed connection

VNC Viewer exiting.


Terminating background ssh process
kill -TERM 4156

Done. You Can Ctrl-C this Terminal if you like. Use Ctrl-\ to pause.

sleep 5






Last login: Tue Jan  4 21:27:37 on ttys000
Jiangnan-Yangs-MacBook:~ yangjiangnan$ /tmp/darwin_terminal_cmd.4331755886285.3.MaGht6 ; exit;
try-1: termpid= mypid=4339
try-2: termpid= mypid=4339
try-3: termpid=4334 mypid=4339

Running ssh:
ssh -x -x -f  -t -C -D 5930  "jiangnan@192.168.1.2" "PORT= x11vnc -display WAIT:cmd=FINDCREATEDISPLAY-Xvfb -localhost -nopw -timeout 120 -o $HOME/.tsvnc.log.yangjiangnan -env FD_SESS=kde -env AUTO_PORT=5950"

jiangnan@192.168.1.2's password: 
found: PORT='5950'

ssh_pid='4483'



PPROXY v0.4: a tool for Web, SOCKS, and UltraVNC proxies and for
PPROXY v0.4: IPv6 and VNC VeNCrypt bridging.
proxy_host:       127.0.0.1
proxy_port:       5930
proxy_connect:    127.0.0.1:5950
pproxy_params:    socks5://127.0.0.1:5930
pproxy_listen:    5960
pproxy_reverse:   
io_socket_inet6:  1

pproxy 1st: 127.0.0.1:5930    - socks5
pproxy 2nd:     - 
pproxy 3rd:     - 

pproxy interface: localhost
pproxy: listening on localhost:5960
vncviewer -noraiseonbeep -encodings copyrect tight zrle zlib hextile 127.0.0.1:60

proxy_request1: SOCKS5 via 127.0.0.1:5930 to 127.0.0.1:5950

pproxy parent[4616]  listen_handle -> socket
pproxy child [4626]  socket -> listen_handle


Proto: RFB 003.008

Connected to RFB server, using protocol version 3.8
Security-Type: 1 (rfbSecTypeNone)  Latency: 6232.05 ms
No VNC authentication needed
VNC authentication succeeded (0) for rfbSecTypeNone (RFB 3.8)

Desktop name "jiangnan-PC:0"

VNC server default format:
  32 bits per pixel.  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Using default colormap which is TrueColor.  Pixel format:
  32 bits per pixel.  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
geometry: 1366x768+35+43 ycrop: 0
create_image()
try_create_image: shm image create fail: image == NULL
try_create_image: created *non-shm* image: 1366x768
try_create_image: image->bytes_per_line: 5464

guessed: -compresslevel 8
guessed: -qualitylevel  4
enabling 'delay_sync' mode for faster local drawing,
disable via env SSVNC_DELAY_SYNC=0 if there are painting errors.
pproxy[4626]: Input is EOF.
pproxy[4626]: finished xfer.
pproxy[4626]: kill TERM parent 4616
pproxy[4616]: got SIGTERM.
vncviewer.x11: VNC server closed connection

VNC Viewer exiting.


Terminating background ssh process
kill -TERM 4483

Done. You Can Ctrl-C this Terminal if you like. Use Ctrl-\ to pause.

sleep 5



Thank you for your help!

---

### Post by krunge on 2011-01-05
I think the $HOME/.tsvnc.log.yangjiangnan on the x11vnc side would contain more info perhaps since that is the side where your Xorg server is crashing...

Anyway, if you search these forums for '-noxrecord' you will see that there is a recent bug in the Xorg server in that it crashes when x11vnc tries to use the RECORD extension.  So if you add '-noxrecord' to the x11vnc cmdline then that is a workaround until Xorg fixes the bug.

If you don't know how to get SSVNC to put '-noxrecord' on the x11vnc cmdline just ask.

---

### Post by yangjiangnan on 2011-01-06
> **krunge said:**
> I think the $HOME/.tsvnc.log.yangjiangnan on the x11vnc side would contain more info perhaps since that is the side where your Xorg server is crashing...

Anyway, if you search these forums for '-noxrecord' you will see that there is a recent bug in the Xorg server in that it crashes when x11vnc tries to use the RECORD extension.  So if you add '-noxrecord' to the x11vnc cmdline then that is a workaround until Xorg fixes the bug.

If you don't know how to get SSVNC to put '-noxrecord' on the x11vnc cmdline just ask.

I go to Option -> Advanced ->Unix ssvncviewer, and input -noxrecord in the Extra Options box, is this right? And this is what the .tsvnc.log.yangjiangnan file contains:

jiangnan@jiangnan-PC:~$ more .tsvnc.log.yangjiangnan 
06/01/2011 00:52:39 x11vnc version: 0.9.10 lastmod: 2010-04-28  pid: 2909
06/01/2011 00:52:39 
06/01/2011 00:52:39 wait_for_client: WAIT:cmd=FINDCREATEDISPLAY-Xvfb
06/01/2011 00:52:39 
06/01/2011 00:52:39 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
06/01/2011 00:52:39 
06/01/2011 00:52:39 Listening for VNC connections on TCP port 5950
06/01/2011 00:52:39 Listening also on IPv6 port 5950 (socket 4)
06/01/2011 00:52:39 

The VNC desktop is:      jiangnan-PC:50
06/01/2011 00:52:40 Got connection from client 127.0.0.1
06/01/2011 00:52:40   other clients:
06/01/2011 00:52:40 check_access: client 127.0.0.1 matches host 127.0.0.1
06/01/2011 00:52:40 incr accepted_client=1 for 127.0.0.1:45998  sock=5
06/01/2011 00:52:40 wait_for_client: got client
06/01/2011 00:52:40 client progressed=0 in 15/10 0.009444 s
06/01/2011 00:52:40 client_set_net: 127.0.0.1  0.0005
06/01/2011 00:52:40 wait_for_client: running: env X11VNC_SKIP_DISPLAY=''  /bin/s
h /tmp/x11vnc-find_display.GLiYSy

The program "Xvfb" could not be found in PATH and standard locations.
You probably need to install a package that provides the "Xvfb" program.
Without it FINDCREATEDISPLAY mode may not be able to create an X display.

06/01/2011 00:52:45 running: chvt 7 >/dev/null 2>/dev/null &
06/01/2011 00:52:47 Using X display :0
06/01/2011 00:52:47 rootwin: 0xac reswin: 0x5200001 dpy: 0x1739d50
06/01/2011 00:52:47 
06/01/2011 00:52:47 ------------------ USEFUL INFORMATION ------------------
06/01/2011 00:52:47 X DAMAGE available on display, using it for polling hints.
06/01/2011 00:52:47   To disable this behavior use: '-noxdamage'
06/01/2011 00:52:47 
06/01/2011 00:52:47   Most compositing window managers like 'compiz' or 'beryl'
06/01/2011 00:52:47   cause X DAMAGE to fail, and so you may not see any screen
06/01/2011 00:52:47   updates via VNC.  Either disable 'compiz' (recommended) or
06/01/2011 00:52:47   supply the x11vnc '-noxdamage' command line option.
06/01/2011 00:52:47 
06/01/2011 00:52:47 Wireframing: -wireframe mode is in effect for window moves.
06/01/2011 00:52:47   If this yields undesired behavior (poor response, painting
06/01/2011 00:52:47   errors, etc) it may be disabled:
06/01/2011 00:52:47    - use '-nowf' to disable wireframing completely.
06/01/2011 00:52:47    - use '-nowcr' to disable the Copy Rectangle after the
06/01/2011 00:52:47      moved window is released in the new position.
06/01/2011 00:52:47   Also see the -help entry for tuning parameters.
06/01/2011 00:52:47   You can press 3 Alt_L's (Left "Alt" key) in a row to 
06/01/2011 00:52:47   repaint the screen, also see the -fixscreen option for
06/01/2011 00:52:47   periodic repaints.
06/01/2011 00:52:47 
06/01/2011 00:52:47 XFIXES available on display, resetting cursor mode
06/01/2011 00:52:47   to: '-cursor most'.
06/01/2011 00:52:47   to disable this behavior use: '-cursor arrow'
06/01/2011 00:52:47   or '-noxfixes'.
06/01/2011 00:52:47 using XFIXES for cursor drawing.
06/01/2011 00:52:47 GrabServer control via XTEST.
06/01/2011 00:52:47 
06/01/2011 00:52:47 Scroll Detection: -scrollcopyrect mode is in effect to
06/01/2011 00:52:47   use RECORD extension to try to detect scrolling windows
06/01/2011 00:52:47   (induced by either user keystroke or mouse input).
06/01/2011 00:52:47   If this yields undesired behavior (poor response, painting
06/01/2011 00:52:47   errors, etc) it may be disabled via: '-noscr'
06/01/2011 00:52:47   Also see the -help entry for tuning parameters.
06/01/2011 00:52:47   You can press 3 Alt_L's (Left "Alt" key) in a row to 
06/01/2011 00:52:47   repaint the screen, also see the -fixscreen option for
06/01/2011 00:52:47   periodic repaints.
06/01/2011 00:52:47 
06/01/2011 00:52:47 XKEYBOARD: number of keysyms per keycode 6 is greater
06/01/2011 00:52:47   than 4 and 2 keysyms are mapped above 4.
06/01/2011 00:52:47   Automatically switching to -xkb mode.
06/01/2011 00:52:47   If this makes the key mapping worse you can
06/01/2011 00:52:47   disable it with the "-noxkb" option.
06/01/2011 00:52:47   Also, remember "-remap DEAD" for accenting characters.
06/01/2011 00:52:47 
06/01/2011 00:52:47 X FBPM extension not supported.
06/01/2011 00:52:47 X display is capable of DPMS.
06/01/2011 00:52:47 --------------------------------------------------------
06/01/2011 00:52:47 
06/01/2011 00:52:47 Default visual ID: 0x21
06/01/2011 00:52:47 Read initial data from X display into framebuffer.
06/01/2011 00:52:47 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/5464
06/01/2011 00:52:47 rfbNewFramebuffer(0x1729eb0, 0x0, 1366, 768, 8, 1, 4)
06/01/2011 00:52:47 WARNING: New width (1366) is not a multiple of 4.
06/01/2011 00:52:47 Pixel format for client 127.0.0.1:
06/01/2011 00:52:47   32 bpp, depth 24, little endian
06/01/2011 00:52:47   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
06/01/2011 00:52:47 
06/01/2011 00:52:47 X display :0.0 is 32bpp depth=24 true color
06/01/2011 00:52:47 
06/01/2011 00:52:47 calling setTranslateFunction()...
06/01/2011 00:52:47 Pixel format for client 127.0.0.1:
06/01/2011 00:52:47   32 bpp, depth 24, little endian
06/01/2011 00:52:47   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
06/01/2011 00:52:47 no translation needed
06/01/2011 00:52:47   done.
06/01/2011 00:52:47 TS_REDIR is empty, restarting...
06/01/2011 00:52:47 
06/01/2011 00:52:47 Xinerama is present and active (e.g. multi-head).
06/01/2011 00:52:47 Xinerama: number of sub-screens: 1
06/01/2011 00:52:47 Xinerama: no blackouts needed (only one sub-screen)
06/01/2011 00:52:47 
06/01/2011 00:52:47 fb read rate: 152 MB/sec
06/01/2011 00:52:47 fast read: reset wait  ms to: 10
06/01/2011 00:52:47 fast read: reset defer ms to: 10
06/01/2011 00:52:47 The X server says there are 12 mouse buttons.
06/01/2011 00:52:47 screen setup finished.
06/01/2011 00:52:47 

The VNC desktop is:      localhost:50

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: [http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)

06/01/2011 00:52:47 Client Protocol Version 3.8
06/01/2011 00:52:47 Protocol version sent 3.8, using 3.8
06/01/2011 00:52:47 Battling with something for -norepeat!! (1 resets left)
06/01/2011 00:52:47 Disabled X server key autorepeat.
06/01/2011 00:52:47   to force back on run: 'xset r on' (2 times)
06/01/2011 00:52:47 created   xdamage object: 0x520002f
06/01/2011 00:52:47 rfbProcessClientSecurityType: executing handler for type 1
06/01/2011 00:52:47 rfbProcessClientSecurityType: returning securityResult for c
lient rfb version >= 3.8
06/01/2011 00:52:47 Pixel format for client 127.0.0.1:
06/01/2011 00:52:47   32 bpp, depth 24, little endian
06/01/2011 00:52:47   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
06/01/2011 00:52:47 no translation needed
06/01/2011 00:52:47 Using compression level 8 for client 127.0.0.1
06/01/2011 00:52:47 Using image quality level 4 for client 127.0.0.1
06/01/2011 00:52:47 Enabling X-style cursor updates for client 127.0.0.1
06/01/2011 00:52:47 Enabling full-color cursor updates for client 127.0.0.1
06/01/2011 00:52:47 Enabling cursor position updates for client 127.0.0.1
06/01/2011 00:52:47 Enabling LastRect protocol extension for client 127.0.0.1
06/01/2011 00:52:47 Enabling NewFBSize protocol extension for client 127.0.0.1
06/01/2011 00:52:47 Using tight encoding for client 127.0.0.1
06/01/2011 00:52:47 copy_tiles: allocating first_line at size 44
06/01/2011 00:52:47 Pixel format for client 127.0.0.1:
06/01/2011 00:52:47   32 bpp, depth 24, little endian
06/01/2011 00:52:47   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
06/01/2011 00:52:47 no translation needed
06/01/2011 00:52:47 Using compression level 8 for client 127.0.0.1
06/01/2011 00:52:47 Using image quality level 4 for client 127.0.0.1
06/01/2011 00:52:47 Enabling X-style cursor updates for client 127.0.0.1
06/01/2011 00:52:47 Enabling full-color cursor updates for client 127.0.0.1
06/01/2011 00:52:47 Enabling cursor position updates for client 127.0.0.1
06/01/2011 00:52:47 Enabling LastRect protocol extension for client 127.0.0.1
06/01/2011 00:52:47 Enabling NewFBSize protocol extension for client 127.0.0.1
06/01/2011 00:52:47 Switching from tight to ZRLE Encoding for client 127.0.0.1
06/01/2011 00:52:47 client 1 network rate 249.7 KB/sec (13220.9 eff KB/sec)
06/01/2011 00:52:47 client 1 latency:  2.7 ms
06/01/2011 00:52:47 dt1: 0.0402, dt2: 0.2788 dt3: 0.0027 bytes: 79287
06/01/2011 00:52:47 link_rate: LR_UNKNOWN - 2 ms, 249 KB/s
06/01/2011 00:52:53 created selwin: 0x5200030
06/01/2011 00:52:53 called initialize_xfixes()


By the way, this problem can occur even if I only open the SSVNC connection on my Mac and do all the operations on the Ubuntu PC directly.

---

### Post by krunge on 2011-01-06
> **yangjiangnan said:**
> I go to Option -> Advanced ->Unix ssvncviewer, and input -noxrecord in the Extra Options box, is this right?
No.  That is options for the viewer, ssvncviewer, not x11vnc.

Here is the C&D way to do it.  I assume you are using SSVNC in 'Terminal Services' mode:

[INDENT]Options -> Advanced -> X11VNC Options

A dialog comes up.  Put -noxrecord in Options: entry box.

Click Done on the Dialog.

Click Done on the Advanced menu.

Click Connect on the main menu.
[/INDENT]

Let me know if it worked.

---

### Post by yangjiangnan on 2011-01-07
> **krunge said:**
> No.  That is options for the viewer, ssvncviewer, not x11vnc.

Here is the C&D way to do it.  I assume you are using SSVNC in 'Terminal Services' mode:
[INDENT]Options -> Advanced -> X11VNC Options

A dialog comes up.  Put -noxrecord in Options: entry box.

Click Done on the Dialog.

Click Done on the Advanced menu.

Click Connect on the main menu.
[/INDENT]Let me know if it worked.


Yes, it probably works. I have tested the vnc a whole day, and it has not crashed once now. I will let you know if it crashes again. Thank you very much!

---

