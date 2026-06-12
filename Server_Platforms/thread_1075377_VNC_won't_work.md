---
title: "VNC won't work"
date: 2009-02-20
forum: Server Platforms
---

### Post by breauxlg on 2009-02-20
I've gone through a number of the vnc setup threads and cannot get vnc to work. When I try vncviewer localhost:1 it says unable to open display. I have a post on one of the install threads to that effect and haven't gotten a reply in a day. This is my first experience with Ubuntu. I've got a degree in computer science (1977) and have been developing application software most of my life and am not finding any of this intuitive. I am impressed that the system found all of my hardware and my printer and the gui works just fine. I need to be able to work from my workstation and vnc into the server to continue trying to use ubuntu. My goal is to set this server up as a mail server and learn something in the process.

---

### Post by cdenley on 2009-02-20
> **breauxlg said:**
> I've gone through a number of the vnc setup threads and cannot get vnc to work. When I try vncviewer localhost:1 it says unable to open display. I have a post on one of the install threads to that effect and haven't gotten a reply in a day. This is my first experience with Ubuntu. I've got a degree in computer science (1977) and have been developing application software most of my life and am not finding any of this intuitive. I am impressed that the system found all of my hardware and my printer and the gui works just fine. I need to be able to work from my workstation and vnc into the server to continue trying to use ubuntu. My goal is to set this server up as a mail server and learn something in the process.

What VNC server are you using? If you don't explain what you have done, it's hard to tell you what you are doing wrong.
Post the output from this command to see if you have any servers running.
```

sudo netstat -tlnp

```

---

### Post by HermanAB on 2009-02-20
Also bear in mind that VNC is a rather old idea mainly intended for Windows.  On Linux, SSH is better, secure and way easier to get to work.

Cheers,

H.

---

### Post by breauxlg on 2009-11-26
The problem was that when I setup the remote access password on the server, there is a funny thing that happens in the password field. When you enter the field, and press the first letter of the password, it doesn't take it. So if I wanted my password to be abcd, and I went to the password field and typed in abcd, the password only took bcd. So when I tried to hook up from the vnc viewer on my windows machine, the passwords never matched. I don't remember how I noticed it, but going to the field on the server, hitting any key, and then typing the password fixed the problem. Wierd. Thanks to everyone for the replies. Lynn

---

