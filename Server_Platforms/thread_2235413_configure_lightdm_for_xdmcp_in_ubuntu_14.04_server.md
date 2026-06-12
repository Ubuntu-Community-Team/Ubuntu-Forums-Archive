---
title: "configure lightdm for xdmcp in ubuntu 14.04 server"
date: 2014-07-20
forum: Server Platforms
---

### Post by soongwooc on 2014-07-20
Help needed!

I installed ubuntu server 14.04 and install lightdm.
I extract lightdm.conf from /usr/share/doc/lightdm/lightgm.gz and put it in /etc/lightdm.
And then commented off as followings:

[SeatDefaults]
xserver-allow-tcp=true
greeter-show-remote-login=true
...
[XDMCPServer]
enabled=true
port=177

For client, the following command is run under win8.1 (cygwinX is installed)
# X -query 192.168.0.88

But, it is terminated with error such as
"failed to connect display :0"

is there anyone to help to resolve this issue or how-to configure xdmcp in 14.04?

soongwoo

---

### Post by e_defranco on 2014-08-12
Hi, I don't know if this can help you.

I am using a 12.04 xubuntu and this is my lightdm.conf:

[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu

[XDMCPServer]
enabled=true
port=177

I think that the error that you get is related to the tcp enabled and maybe on your server there are also missing something ...

Are you be able to get a login screen localy ?

And if you type in the local shell netstat -anu you see the port 177 listen ?

lightdm offer weird xdmcp support and is not more documented but usualy, in my esperience, I have not many problems to connet from a remote machine to one server by xdmcp.

Emilio

---

### Post by pinegreen on 2014-09-01
Try 
X --query 192.168.0.88 :1
Presumably you already run X on :0.

---

