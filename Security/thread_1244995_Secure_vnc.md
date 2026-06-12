---
title: "Secure vnc"
date: 2009-08-20
forum: Security
---

### Post by Zaiken on 2009-08-20
I recently tested vnc on my computer becuase I intended to access it from my laptop when i was away from home, problem is someone managed to bypass the password and get into my system. when they got access it seems they setup anacron to poll my ip address to a certain ip to find me again later. after that they also attempted to install mswins.exe which seems to be a trojan/keylogger I assume they intended to use with wine. all of this happened in a very short period of time as I only had vnc for a couple of days and it was accessed by someone else for only a few mins. The speed of this attack was suprising and although I managed to cut them off I would still like to use vnc securely. I plan to enable it for local host only through a secure tunnel application. are there any other steps i can take to ensure something like this does not happen again?

---

### Post by sefs on 2009-08-20
If you run it on the default port 5900 then the speed of attack is not surprising.  That port is constantly being scanned for.  I hope you did not use a weak password (less than 20 characters)


1) Install SSH and configure for key based authentication only...no password logins!!!

2) Configure VNC to tunnel over your SSH 


And then what you would do is then connect from laptop to PC using putty 

Then connect with vnc to a port on your local machine which in turn will route any info sent to that port over ssh to your distant pc. 

When you setup ssh DO NOT use a default port of 22, change it!  Unless of course you will use a different port on your router that can then forward to port 22 on your pc, which is probably easier.

This will increase your pc security even though you are using key authenticaton

Google vnc over ssh to find out how to configure vnc to work over ssh with putty.


UPDATE:  acutally now i think of it ... that sort of tutorial may be here on this very forum if i remember correctly.

Type in resumeable sessions in the search feild of the forum. I think i have resumeable spelt wrong.

---

### Post by HermanAB on 2009-08-20
Yup, I think that the Ubuntu developer's insistence on pushing the use of VNC instead of SSH is almost criminal.  Every time someone complains on these forums about getting hacked, it is because he used VNC.

Install SSH Server, then connect like this:
$ ssh -X -C -c blowfish user@server gnome-panel

That works way better than VNC and it is secure.

---

### Post by XCan on 2009-08-20
SSH or FreeNX still cannot provide the same functionality as VNC enabling the user to continue an open session.

---

### Post by HermanAB on 2009-08-20
Yup, you sure don't want the hackers to need to start a new session every time they log in - it would ruin their spam sending productivity...

---

### Post by XCan on 2009-08-20
Believe it or not, some people do use their machines to work, and some people do like to work from several locations. If you claim that firewall + ssh tunnel isn't secure enough for VNC, then perhaps you shouldn't be connected to the internet.

---

### Post by scorp123 on 2009-08-20
> **HermanAB said:**
> Every time someone complains on these forums about getting hacked, it is because he used VNC. Can we see the threads please?

> **HermanAB said:**
>  Install SSH Server, then connect like this:
$ ssh -X -C -c blowfish user@server gnome-panel Ah yes. And what happens if you get disconnected? Can you resume your disconnected session? Nope. :)

---

### Post by scorp123 on 2009-08-20
> **XCan said:**
>  If you claim that firewall + ssh tunnel isn't secure enough for VNC, then perhaps you shouldn't be connected to the internet. He keeps claiming that in every thread where anyone mentions VNC. And until this day I have not seen a proof for his claim that a lot of people got hacked "because of VNC". Really. I'd like to see those threads. :D

---

### Post by sefs on 2009-08-20
Why dont you all quit arguing and assist the OP.

Anyway... SSH (with key based authentication) + VNC will make you magnitudes better off than plain vnc.  Personally I think it is rock solid barring 0day exploits :)

---

### Post by cariboo on 2009-08-20
Here's three:

[list]
[*][You got owned]("http://ubuntuforums.org/showthread.php?t=980832&highlight=hacked")

[*][hacked]("http://ubuntuforums.org/showthread.php?t=1182223&highlight=hacked")

[*][I just got hacked, and I think I know how]("http://buntuforums.org/showthread.php?t=1144417&highlight=hacked")

[/list]

These all happened in the last 6 months, there are quite a few more from last year if you care to search for them yourselves.

---

### Post by doas777 on 2009-08-20
VNC is not safe to expose to the internet, especially in the ubuntu shared-session mode, since no passwd is usually required for login, and the password limitation of 8 char is problematic from a brute force perspective.

it is possible to tunnel vnc over ssh. it will persist the session,and work exactly like vnc usually does, but you have to be sure to block non-ssh'd vnc connections on your firewall, while allowing connections from 127.0.0.1 on the port your tunneling to.

ssh and freenx are really the best methods to use, unless you want to get into VPNs.
both are easy to setup and use, and you can persist a nx session (but it is not shared with the locally logged in users).

if you have a vpn capable router, that may be your best bet, to use vnc safely.

---

### Post by sefs on 2009-08-21
> **doas777 said:**
> VNC is not safe to expose to the internet, especially in the ubuntu shared-session mode, since no passwd is usually required for login, and the password limitation of 8 char is problematic from a brute force perspective.

it is possible to tunnel vnc over ssh. it will persist the session,and work exactly like vnc usually does, but you have to be sure to block non-ssh'd vnc connections on your firewall, while allowing connections from 127.0.0.1 on the port your tunneling to.

ssh and freenx are really the best methods to use, unless you want to get into VPNs.
both are easy to setup and use, and you can persist a nx session (but it is not shared with the locally logged in users).

if you have a vpn capable router, that may be your best bet, to use vnc safely.

the free version of nxserver over at nomachine.com is also an alternative to freenx.  It requires ssh to be installed also, and tunnels over it.

---

### Post by sefs on 2009-08-21
I am curious.

I have vnc4server installed, and even though I have connections being tunneled over ssh and no port open for it on the router or machine firewall (ufw).. I would like to lock it down that only local host can connect to the vnc server running how would I do that.

my /etc/xinetd.d/Xvnc looks like the below

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
	server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
	port = xxxx
}

```

Is there some argument that I can apply to server_args?

UPDATE:

I think pertaining to this...

```

...
VNC parameters:

Parameters can be turned on with -<param> or off with -<param>=0
Parameters which take a value can be specified as -<param> <value>
Other valid forms are <param>=<value> -<param>=<value> --<param>=<value>
Parameter names are case-insensitive.  The parameters are:

Global Parameters:
  localhost      - Only allow connections from localhost (default=0)
...

```

all I should have to do is append -localhost=1 to server_args in /etc/xinetd.d/Xvnc?  Is that correct?

Thanks.

---

### Post by XCan on 2009-08-21
I have always believed it was due to Ubuntu not warning the user to set a password that users are hacked. The 8-char limit is hardly an issue, and I doubt many users have even that for their SSH. The unencrypted data by default may be, but if someone is willing to spend that time, you're in trouble anyway.

I pertain, for remote-desktop capabilities, SSH+VNC+Firewall is secure enough and easy enough for everyone to setup. Even VNC+non-standard port alleviates tons of the issues. FreeNX and SSH+X are good, but neither can replace VNC (or even Windows' Remote Desktop Protocol) fully.

---

### Post by scorp123 on 2009-08-21
> **XCan said:**
>  I pertain, for remote-desktop capabilities, SSH+VNC+Firewall is secure enough and easy enough for everyone to setup. Yes, same opinion here.

> **XCan said:**
>  Even VNC+non-standard port alleviates tons of the issues. FreeNX and SSH+X are good, but neither can replace VNC (or even Windows' Remote Desktop Protocol) fully. Yes, same opinion here.

If getting hacked by VNC is such a big issue in general on Linux (about which I shall arrogantly claim: it's not or there would be far more threads that would have caught my attention ... [-(  ) then I'd assume that there would be a few better and more secure alternatives out there already. Or Canonical would have sponsored the development for such a program I assume?

---

### Post by doas777 on 2009-08-21
> **XCan said:**
> I have always believed it was due to Ubuntu not warning the user to set a password that users are hacked. The 8-char limit is hardly an issue, and I doubt many users have even that for their SSH. The unencrypted data by default may be, but if someone is willing to spend that time, you're in trouble anyway.

I pertain, for remote-desktop capabilities, SSH+VNC+Firewall is secure enough and easy enough for everyone to setup. Even VNC+non-standard port alleviates tons of the issues. FreeNX and SSH+X are good, but neither can replace VNC (or even Windows' Remote Desktop Protocol) fully.

well, there are a few problems with the passwords in ubuntus version of VNC. first, I have tried to use ubuntus tools to set a password for vnc on fiesty, gusty, hardy, but it never worked. wouldn't allow any connection when a password was set. they just wouldn't do it. in Intrepid and jaunty it works fine though. 

but the big problem with Ubuntu Remote desktop vnc passwords, is that since there is no account associated with the vnc session, the password can be easily bruteforced, because there is no account lockout after x number of invalid login attempts. that means that your password could be cracked in days or even hours, with one script invocation by the cracker.  
usually if you expose ssh to the internet it is recomended that you install fail2ban ( [http://www.howtoforge.com/fail2ban_debian_etch](http://www.howtoforge.com/fail2ban_debian_etch) ) to prevent such attacks.


ultimatly the differance between being safe, and being secure, is the  important question. if you feel safe using vnc directly exposed to the internet, then proceed as thou wilt. I personally would not feel that that was safe, but I have lots of data that I value, and i don't trust what a cracker would do to my network once he/she got in.  prolly use my resources to commit a cyber crime, leaving me, holding the bag as it were.

---

