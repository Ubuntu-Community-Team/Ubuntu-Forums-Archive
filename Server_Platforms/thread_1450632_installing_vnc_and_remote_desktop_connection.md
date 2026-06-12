---
title: "installing vnc and remote desktop connection"
date: 2010-04-09
forum: Server Platforms
---

### Post by toms003 on 2010-04-09
Hi,
I am new to ubuntu/linux. i have installed ubuntu 9.04 and desktop xubuntu. i want access the sever from my windows xp using either rdp or vnc. i am able to use the ssh but thats only command line. i need the gui desktop. i have installed x11vnc,tightvnc etc. but whenever i try to connect from my vnc manager,its giveout error.machine actively refused it. i havent configured any port or anything like that. please help with a detailed instructions please.
thanks

---

### Post by moetunes on 2010-04-09
Have you installed vncserver on the linux box?

---

### Post by toms003 on 2010-04-09
yes i have

---

### Post by moetunes on 2010-04-09
do you have a xstartup file in .vnc in your home folder on tr linux box?

---

### Post by cdenley on 2010-04-09
You have to actually start an instance of the VNC server before you can connect.
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by Paddy Landau on 2010-04-09
Whilst VNC works, it can be difficult to set up because of the need to have port forwarding.

Have a look at [Yuuguu]("http://www.yuuguu.com/"). It automates the process, and you can connect Windows, Mac and Linux. The free version is perfectly adequate for normal use.

---

### Post by HermanAB on 2010-04-09
Please, please, please note that VNC is the one and only true way to get your otherwise secure Ubuntu machine hacked.  There are many tales of woe on these forums.

You should consider using SSH instead.  There is a good reason why all newbies use VNC and all greybeards use SSH...

---

### Post by cdenley on 2010-04-09
> **HermanAB said:**
> Please, please, please note that VNC is the one and only true way to get your otherwise secure Ubuntu machine hacked.  There are many tales of woe on these forums.

You should consider using SSH instead.  There is a good reason why all newbies use VNC and all greybeards use SSH...

I agree, but didn't suggest it because they are connecting from windows. Is there a free, simple solution to use X over ssh from a windows client?

---

### Post by HermanAB on 2010-04-09
Here you go:
[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by cdenley on 2010-04-09
> **HermanAB said:**
> Here you go:
[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

Not quite free. You can't download until you make a donation.

---

### Post by HermanAB on 2010-04-10
Hmm? You *can* download without a donation.

Otherwise, use Cygwin.

---

### Post by Claus7 on 2010-04-10
Hello,

> **toms003 said:**
> Hi,
i want access the sever from my windows xp using either rdp or vnc. ... i need the gui desktop. ... i havent configured any port or anything like that. please help with a detailed instructions please.
thanks

Even though you were clear at your thread, I would advice you, if you have time, to check [nxclient]("http://www.nomachine.com/download.php"). The installation process is not so straightforward, yet you will be able to remotely see your desktop. Unfortunately, some graphical applications might not work (whereas from an ubuntu home pc to an ubuntu pc server would work normally).

> **HermanAB said:**
> 
Otherwise, use Cygwin.

I'm not so sure, yet cygwin alone can provide graphical support? I think that he needs also an x environment. Correct me if I'm wrong.

Regards!

---

### Post by cdenley on 2010-04-10
> **HermanAB said:**
> Hmm? You *can* download without a donation.

Download from where?
[http://www.straightrunning.com/candidate/Xming-7-5-0-18-setup.exe](http://www.straightrunning.com/candidate/Xming-7-5-0-18-setup.exe)
```

cdenley@cdenley:~$ echo -e "GET /candidate/Xming-7-5-0-18-setup.exe HTTP/1.0\nHost: www.straightrunning.com\n"|nc www.straightrunning.com 80
HTTP/1.1 401 Authorization Required
Date: Sat, 10 Apr 2010 13:00:36 GMT
Server: Not-allowed
WWW-Authenticate: Basic realm="Xming Website Releases"
Content-Length: 401
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>401 Authorization Required</title>
</head><body>
<h1>Authorization Required</h1>
<p>This server could not verify that you
are authorized to access the document
requested.  Either you supplied the wrong
credentials (e.g., bad password), or your
browser doesn't understand how to supply
the credentials required.</p>
</body></html>

```
> 
By donating you will get a Donor Password sent by return email, enabling access to Xming Website Releases and Development Snapshots for private individuals.


---

### Post by HermanAB on 2010-04-10
Hmm, sorry that is new to me - having used Xming in the past.

You can install Cygwin on Windows for free:
[http://www.cygwin.com/](http://www.cygwin.com/)

Cygwin has many more features, basically being a general purpose cross platform kit for Windows, it can do almost anything you can do on Linux.

---

### Post by toms003 on 2010-04-12
guys still not got it right...i have installed quite a lot of stuff now. i can get the ssh working fine.but not the vnc.i need the gui desktop(xubuntu) on my windows machine. how to check if the port 5900 is open or not. i tried using netstat but that port is not listed there.. how to open the port?
Tom

---

### Post by cdenley on 2010-04-12
> **toms003 said:**
> guys still not got it right...i have installed quite a lot of stuff now. i can get the ssh working fine.but not the vnc.i need the gui desktop(xubuntu) on my windows machine. how to check if the port 5900 is open or not. i tried using netstat but that port is not listed there.. how to open the port?
Tom

You need to run something that listens on that port, such as a vnc server. Did you install a vnc server? If so, which one?

---

### Post by toms003 on 2010-04-12
hi 
I have installed xtightvncserver and x11 on it
tom

---

### Post by cdenley on 2010-04-12
> **toms003 said:**
> hi 
I have installed xtightvncserver and x11 on it
tom

I assume you mean "tightvncserver" and "x11vnc"?

To start an instance of tightvncserver:
```

tightvncserver

```
Notice it gives you output that include "hostname:1". That means you must connect on 5901. If it were "hostname:2", you would connect on 5902.

To start an instance of x11vnc:
```

x11vnc

```

---

### Post by toms003 on 2010-04-12
> **cdenley said:**
> I assume you mean "tightvncserver" and "x11vnc"?
 
To start an instance of tightvncserver:
```

tightvncserver

```
Notice it gives you output that include "hostname:1". That means you must connect on 5901. If it were "hostname:2", you would connect on 5902.
 
To start an instance of x11vnc:
```

x11vnc

```
 Ok i will try this. so i should go the terminal and type in tightvncserver????(sorry for my ignorance,just very very new to this)

---

### Post by cdenley on 2010-04-12
> **toms003 said:**
> Ok i will try this. so i should go the terminal and type in tightvncserver????(sorry for my ignorance,just very very new to this)

Yes. From a local terminal, or the terminal started when you create the SSH tunnel. Typically, VNC connections are tunneled through ssh for security.

---

### Post by toms003 on 2010-04-12
> **cdenley said:**
> Yes. From a local terminal, or the terminal started when you create the SSH tunnel. Typically, VNC connections are tunneled through ssh for security.
 ok thanks. i will have to do this tomorrow when i am in work. another one to clarify.
1) i can use ssh connection from windows xp machine to xubuntu server .
2) after doing the terminal tightvncserver on the ubuntu server,i go to my windows pc and use the vnc to connect to the ubuntu server is that right?

---

### Post by cdenley on 2010-04-12
> **toms003 said:**
> ok thanks. i will have to do this tomorrow when i am in work. another one to clarify.
1) i can use ssh connection from windows xp machine to xubuntu server .
2) after doing the terminal tightvncserver on the ubuntu server,i go to my windows pc and use the vnc to connect to the ubuntu server is that right?

1. Yes, with putty.

2. Yes. By default, I don't think it will be very useful, though. You have to configure what kind of desktop you want.
[https://help.ubuntu.com/community/VNC/Servers#Customising%20your%20session](https://help.ubuntu.com/community/VNC/Servers#Customising%20your%20session)
I'm not sure how to edit that to make xfce start.

---

