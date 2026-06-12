---
title: "How to use rdesktop (Windows remote desktop connection)"
date: 2008-06-10
forum: Tutorials
---

### Post by qns8dn3 on 2008-06-10
rdesktop is a client program that allows you to connect from your Ubuntu computer to your Windows computer to remote control the Windows computer. In other words, while you are sitting in front of your Ubuntu computer at home, you can log into and access your Windows computer as if you are sitting in front of the Windows computer. See [remote desktop software](http://en.wikipedia.org/wiki/Remote_desktop_software).

**rdesktop and VNC and Terminal Server Client (comparison)**
 There is another similar program called VNC. VNC is slow compared to rdesktop and VNC connection is unencrypted while rdesktop connection is encrypted by default. But there is a [way to use VNC with encrypted connection](https://help.ubuntu.com/community/VNCOverSSH). VNC works on almost all operating systems. See [comparison of remote desktop software](http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software).
  Terminal Server Client (Applications > Internet > Terminal Server Client) is a GUI front-end to VNC and rdesktop. If you open Terminal Server Client, you will see Protocol option (RDP, RDPv5, VNC), RDP and RDPv5 are for rdesktop connection. You should use Terminal Server Client if it works fine and if you are ok with [this bug](https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/103208). If you want more control (such as connecting a specific local folder or other device redirection, hiding or keeping window manager decoration, using seamlessRDP), use rdesktop following this guide.


**What to do on the Windows side (the server side)**

The Windows computer you will connect to must be running Windows XP Pro or a higher version of Windows.

* If you have a weak Windows login password (such as john1, aaaaaaaaaaaaa, abcabc), change it to a stronger password that is longer than 10 characters and that is not a combination of words that can be found on a dictionary. You need to do this because if you enable Remote Desktop Connection, anybody with internet access can try to log into your Windows computer with automated cracking tools.

* Enable Remote Desktop Connection on the Windows computer following [this guide](http://www.microsoft.com/windowsxp/using/mobility/getstarted/remoteintro.mspx). If the Ubuntu computer you will be connecting from has a static ip address, you can set your Windows Firewall to allow remote desktop connection from only your Ubuntu computer and refuse connection from other computers. To do this, open Windows Firewall, click on the Exceptions tab, Select 'Remote Desktop', click 'Edit', click 'Change Scope...', choose 'Custom list' and enter the IP addresses of computers from which you want to remote connect (See the attached screenshot)

**What to do on the Ubuntu side (client side)**

* On your Ubuntu computer, open a terminal (Application > Accessories > Terminal) and enter the following command:
```
rdesktop
```
You'll see a long list of options for rdesktop. Think of it as an rdesktop cheatsheet.


If your windows username and Ubuntu username is the same and if the static IP address of your Windows computer is (suppose) 143.210.123.456, you can now connect to your Windows computer by entering the following command:
```
rdesktop 143.210.123.456
```

If the usernames are different and your Windows username is (suppose) john, enter:
```
rdesktop -u john 143.210.123.456
```

To disconnect, open Windows Start menu and click 'Disconnect'.

Most cases, you'll use one of the following two commands:
```
rdesktop -u john -fP 143.210.123.456
```
```
rdesktop -u john -g 100% -PKD 143.210.123.456
```

Both commands display remote desktop in full screen (corresponding option : -f, -g 100% -D) and bitmap cache is enabled for speed (-P). There is a bug and [clipboard functionality (copy paste between remote desktop and local one) doesn't work in full screen mode](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=335544). To make clipboard work, you need to escape full screen mode by pressing ctrl+alt+enter. ( Press ctrl+alt+enter again to get back to full screen mode. ) This bug only affects the first command and not the second command. So if you need to copy and paste between two desktops a lot, go with the second command. (Install [dragking](http://www.donationcoder.com/Software/Skrommel/index.html#DragKing) if you want to copy by selecting a text and paste by middle-click on your Windows desktop. dragking.ahk script requires [ahkstructlib.ahk](http://www.autohotkey.com/forum/viewtopic.php?t=4888)). The two commands also differs in how the keybindings are handled,

* First command : if you press alt+tab (keyboard shortcut for switching windows), it doesn't switch windows from Ubuntu desktop, it switches from the remote Windows desktop. And ctrl+alt+right (for switching to another workspace) doesn't work. This is useful when you want to alt+tab in the remote Windows.

* Second command :  keyboard shortcuts such as ctrl+alt+right and alt+tab works on your Ubuntu desktop. This is useful because you can put the remote desktop on the seperate workspace then you can switch between your local ubuntu workspace and your remote Windows desktop just by pressing ctrl+alt+right and ctrl+alt+left.


**Create a launcher**

Opening terminal every time you want to remote connect to Windows is of a hassle. To create a lancher, right click on the top panel, click 'Add to Panel...', select 'Custom Application launcher', click 'Add' button, type your command in the command field. (See the attached screenshot). if the command contains %, replace % with %%.


**useful rdesktop options**

-r disk:doc=/home/john/Documents,pic=/home/john/Pictures
With this option, rdesktop connects folders /home/john/Documents and /home/john/Pictures to Windows remote desktop. Open Windows Start menu and click 'My Computer' and you will see the connected folders named doc and pic.

 -r sound:local
This option is to hear sound from Windows remote desktop.

See /usr/share/doc/rdesktop/redirection.txt for more on device redirection.

-k ko
This sets the keyboard layout to Korean. This makes Hangul key work on the remote desktop. See /usr/share/doc/rdesktop/keymap-names.txt




**How to use rdesktop over ssh**

rdesktop is [vulnerable to man-in-the-middle attacks](http://sourceforge.net/mailarchive/message.php?msg_name=732099.24912.qm%40web45108.mail.sp1.yahoo.com). So you might want to use it over ssh.

Follow [this lifehacker article](http://lifehacker.com/software/home-server/geek-to-live--set-up-a-personal-home-ssh-server-205090.php) to set up an ssh server on the Windows computer. (You can edit sshd_config with a Windows editor supporting UNIX texts such as [notepad2](http://sourceforge.net/projects/notepad2/)) You might want to set Windows Firewall to disallow ssh access from IP addresses other than your Ubuntu computer's. Take note of the RSA key fingerprint by open a cygwin shell (Start > All Programs > Cygwin > Cygwin Bash Shell) and entering :
```
ssh-keygen -lf /etc/ssh_host_rsa_key.pub
```

On your Ubuntu computer, check if the local port 3389 (default listening port number for Windows Remote Desktop service) is available:
```
telnet localhost 3389
```
The output should be similar to :
```
$ telnet localhost 3389
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```
, which means the port is available. If the port is already in use the output should be similar to :
```
$ telnet localhost 3389
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
```

If the port is available, connect to windows ssh service with port forward:
```
ssh -L 3389:localhost:3389 john@143.210.123.456
```
The port 3389 of your Ubuntu is forwarded to the port 3389 of your Windows.  The output should be like :
```
$ ssh -L 3389:localhost:3389 john@143.210.123.456
The authenticity of host '143.210.123.456 (143.210.123.456)' can't be established.
RSA key fingerprint is f3:90:3b:70:20:a2:52:fe:fx:a2:90:70:3b:f3:6a:22.
Are you sure you want to continue connecting (yes/no)? 
```
Check if the presented RSA key fingerprint is the same as the one you took note of. If they are different, you should answer no, the host you are connecting to is not your real Windows computer, it may be a [man in the middle](http://en.wikipedia.org/wiki/Man_in_the_middle_attack). If they are same, answer yes and proceed. You can get out of the ssh session by entering 'exit' but don't do it now.

Open another terminal and make rdesktop connect to localhost:
```
rdesktop -u john localhost
```

The remote desktop will be a bit slow. cygwin is slow.

What if the port 3389 was already in use? Find a different available port (suppose, 3099) and connect to Windows ssh like this :
```
ssh -L 3099:localhost:3389 john@143.210.123.456
```
The port 3099 of your Ubuntu is forwarded to the port 3389 of your Windows.

Open a new terminal and make rdesktop connect to localhost at the port 3099 :
```
rdesktop -u john localhost:3099
```

---

### Post by ForksHolder on 2008-06-13
AWESOME!!!!
You helped me ALOT man, Thanks

---

### Post by CostaRica on 2008-06-13
Is there a way to remote desktop without a static-public IP? I use LogMeIn, but it does not work from Ubuntu... :(

---

### Post by CostaRica on 2008-06-13
I have 4 computers I need to do remote desktop to, but only 2 have static-public ips.  My question is, - is there an app where one can make one of the static-public ips to be the "remote desktop server" of the rest, so that the other computers keep reporting the server in which ip they are?  I suppose that is the way LogMeIn.com works.

---

### Post by Roasted on 2008-06-15
Is there any way you can do remote desktop without the end user's computer locking itself out?

I just tested it on my XP Pro laptop, and it locked my laptop and said it was in use. I'd like for the end user to still have visibility of what's going on.

---

### Post by qns8dn3 on 2008-06-18
CostaRica
Using a dynamic dns service can be a workaround. See [dynamic DNS service providers list](http://www.technopagan.org/dynamic/#TheList)

Roasted
have you tried "-0" (zero) option (attach to console)?
```
rdesktop -0 ipaddress
```

---

### Post by moloch16 on 2008-06-19
Thanks for the tips.  Has anyone been able to get sound to display on the local computer?  I'm running Hardy connected to a remote Windows XP box.  I'm using tsclient to setup the remote desktop.  When I choose to hear sound from the remote machine on the local machine I get the attached error on the Windows box.

---

### Post by argail1980 on 2008-08-21
Hi there,

I am trying to connect from a ubuntu 8.10 system to a windows XP system but I always get "connection refused". I followed the recommendations of this thread, set a firewall exception for my IP and still it doesn't work. Any idea what else could it be?


UPDATE:
ignore that post... I simply forgot a checkbox.

---

### Post by clarknova on 2008-09-10
Good tutorial, thanks.

ctrl-alt-enter doesn't get me out of full-screen mode. Well, it does for a fraction of a second, but then I'm right back into my windows desktop. Desktop switching doesn't appear to work for me either (ctrl-alt-direction arrow). Any ideas?

db

---

### Post by clarknova on 2008-09-11
> **clarknova said:**
> Good tutorial, thanks.

ctrl-alt-enter doesn't get me out of full-screen mode. Well, it does for a fraction of a second, but then I'm right back into my windows desktop. Desktop switching doesn't appear to work for me either (ctrl-alt-direction arrow). Any ideas?

db
Never mind. Amazing what a reboot will fix.

db

---

### Post by n8makar on 2008-09-14
Throughout the enitre internetz this is the best post for connecting ubuntu to windoze. excellent post

---

### Post by iainmackay85 on 2008-10-05
> **Roasted said:**
> Is there any way you can do remote desktop without the end user's computer locking itself out?

I just tested it on my XP Pro laptop, and it locked my laptop and said it was in use. I'd like for the end user to still have visibility of what's going on.


search google, There are instructions on hacking windows XP Pro to allow multiple sessions (upto 4) so this means that a person can be using the computer plus 3 others logged in. also an administrator can 'shadow' any of the users and watch what they are doing.

search google for 'remote desktop multiple sessions' I'm Feeling Lucky

---

### Post by cupcake on 2008-10-08
Have to agree; finding this post probably saved me a shed-load of time. Now i can connect to my work computer from my laptop - still not got it perfect yet but this was a real help!
 
Thanks!!

---

### Post by nidelius on 2008-11-06
Just wanted to share my shortcut string with you

rdesktop SOMEIPORADDRESS -k sv -g 1200x950 -K -a 16 -u Administrator -r disk:mylinuxdisk=/home/username


where -K makes rdesktop steal less commands from linux and
-a for making rdesktop faster over slow connections (bits of color sent)

-------------------------------
&#45236;&#44032; &#46020;&#50880;&#51060; &#46112; &#49688;&#51080;&#45716; &#55148;&#47581;&#51012;
Jag hoppas det kan hjälpa någon iaf :)

---

### Post by justinmiller87 on 2010-06-16
Hello, so here is my situation. I have a computer I have plugged into my television that has a broken screen and a keyboard that got ruined, so I though hey, I wonder if I can remote in. I followed the instructions in this guide, and I get the following:

justin@justin-acer:~$ rdesktop 192.168.2.3
Autoselected keyboard map en-us
ERROR: 192.168.2.3: unable to connect

That is the IP address on my local network for the computer I'm trying to connect to but cannot. I can ping it, but cannot connect remotely. I tried rdesktop and tsclient to no avail. Do you have any suggestions for me?

---

### Post by univexXx on 2010-07-01
i agree with justinmiller87 i am haveing the exact same prob and im at a loss if anyone could shed some light on this it would be great thank very much

-Adam

---

### Post by justinmiller87 on 2010-07-18
Bump

---

### Post by wlraider70 on 2010-07-22
Are you trying to RDP into a windows box or ubuntu?

Are you being asked for a password or user name?

---

### Post by justinmiller87 on 2010-07-28
> **wlraider70 said:**
> Are you trying to RDP into a windows box or ubuntu?

Are you being asked for a password or user name?
Windows and no. I don't even get the option to do that. I set up a user on there for the purposes of logging in using rdesktop but to no avail.

---

### Post by admiralspark on 2010-07-29
I also am having some problems. I've adjusted both my firewall and Windows firewall on the comp I'm trying to connect to and it still won't work. Doesn't prompt for username/password even. Heck, I've run through every rdesktop option and still none of them help.

---

### Post by dacman48 on 2010-07-29
@costarice, u can use a service like dyndns, which will sync your comp to a dns name, saves the trouble of rememberina a number and is completely static. and free

---

### Post by justinmiller87 on 2010-08-03
Hey guys, I solved my problem. Turns out the system I was trying to remote into is Windows XP Home. Well, XP Home doesn't have the proper remote desktop services, so I had to manipulate it into thinking it was XP Pro in order to install them.

Here's the link to the instructions as to how to do it.

[http://www.mydigitallife.info/2008/06/14/install-and-enable-remote-desktop-in-windows-xp-home-edition/](http://www.mydigitallife.info/2008/06/14/install-and-enable-remote-desktop-in-windows-xp-home-edition/)

---

### Post by rEnr3n on 2010-10-15
Is it possible to use SSH keys so that I don't need to enter the Windows password every time I remote it? I have done it on Ubuntu server but I don't have any idea on Windows.

---

### Post by karthick87 on 2010-10-30
I receive unable to connect error when connecting..Help me..!

---

### Post by elperrillo on 2011-03-09
Hi Carthick87

Read this guide on rdesktop, it worked for me

[http://geekyprojects.com/tutorials/how-to-use-the-real-windows-remote-destop-in-ubuntu/](http://geekyprojects.com/tutorials/how-to-use-the-real-windows-remote-destop-in-ubuntu/)

Hope it helps

---

### Post by Davidovitch on 2011-04-04
I am using rdesktop to connect to a Windows Server 2008 standard. I successfully get to the login screen and when entering username and password, it loads the welcome text, takes some time and than says "user name and password are incorrect" (entering a wrong user/pass gives that message directly). They are correct though, connecting via a windows machine using remote desktop with the same user works correctly. 

Anybody can anyone relate to this error?

---

### Post by Davidovitch on 2011-04-04
> **Davidovitch said:**
> I am using rdesktop to connect to a Windows Server 2008 standard. I successfully get to the login screen and when entering username and password, it loads the welcome text, takes some time and than says "user name and password are incorrect" (entering a wrong user/pass gives that message directly). They are correct though, connecting via a windows machine using remote desktop with the same user works correctly. 

Anybody can anyone relate to this error?

I am sorry for the spam. Ignore this message. Apparently I had the wrong domain...it works as it should!

---

### Post by philthyfill on 2011-09-23
How do you remote into a Windows machine with its computer name? I've tried the following and it didn't work.

```
rdesktop -n COMPUTERNAME
```

---

### Post by dcstar on 2011-09-29
I have just discovered the **remmina** package that is a far superior client to access Windows desktops than the RDP client - which is now apparently not being further developed or maintained.

The remmina versions from 0.8 onwards (10.10 onwards) use the freerdp backend which is still maintained.

The remmina package is in the Ubuntu repositories from 10.04 onwards, or you can use the PPA for the latest version:

[http://remmina.sourceforge.net/downloads.shtml](http://remmina.sourceforge.net/downloads.shtml)

---

### Post by satnelav on 2012-05-08
My question is: are there any default rdesktop settings and where are they stored? Thanks.

---

### Post by ahmedipa on 2012-09-27
nice tutorial I faced this problem 

[http://ubuntuforums.org/showpost.php?p=12264885&postcount=11](http://ubuntuforums.org/showpost.php?p=12264885&postcount=11)

how can I solved it 

thank you so much for this

---

