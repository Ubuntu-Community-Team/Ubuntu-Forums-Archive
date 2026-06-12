---
title: "Remote administration help and ideas"
date: 2009-10-03
forum: Server Platforms
---

### Post by munchi3s on 2009-10-03
Well, to start things off I'm in charge of one of the computer labs in my school. (I'm a senior in High School) And this to me is so much fun because I am a fan of ubuntu servers. I have a great time working with ubuntu, although, my knowledge of ubuntu is in an infant stage of development. I have done some basic work with DHCP, DNS, LTSP, SSH/SFTP(remote administration), I have even created a CSS server, and a Garry's Mod server(Don't tell my teacher). 

My uncle works for a company that has fully invested into linux servers and he has told me that there is a way to use my server to send the information of a GUI based app, like firefox, and open it on my laptop which is ubuntu. For instance, if I wanted to change the port forwarding of my router to allow a new port for a new protocol that I am setting up. I could run a command "something something firefox" and it would open the firefox on my laptop, and I typed in 192.168.1.1 It would show the router in my lab instead of my home router.(I think my uncle mentioned something like this to me)

I want to know if what I would like is even possible and if it is not possible what are some things I should consider installing on my server to get the most out of my ubuntu server. I would also like other ideas on remote administration. Perhaps something that I have not thought about yet. Any links to informational tutorials that would advance my ubuntu and CLI knowledge would also be much appreciated.

A thousand thanks to any enlightenment on the subject.

---

### Post by cariboo on 2009-10-03
Please do not allow remote administration of the lab router, as you are just asking for trouble. You seem to have things well in hand as far as remote administration with ssh/sftp is concerned. As far as a gui for server administration, have a look at [Webmin]("http:///www.webmin.com/"), it is a web based server admin suite.

---

### Post by sunstriker on 2009-10-03
Hi!

I'm also using this technique to get a firefox open at home from my office (in case of port forwarding, or if the Win2003 TS Virtual Machine has crashed). What I do is the following (i'm working on Mac OS X, but I think this should also work on Ubuntu):

[LIST]
[*]Open a terminal
[*]Type "ssh -X [username]@[ip address of your server]
[/LIST]

this should start the X server (on mac os x, on ubuntu it'll be already running).
If you then type in "firefox" or any other kind of X program, it will just pop up on your desktop.

I believe it is also possible to use Xnest to start an entire Gnome session in a window.

I hope this helps!

Greetz

---

### Post by munchi3s on 2009-10-03
> **cariboo907 said:**
> Please do not allow remote administration of the lab router, as you are just asking for trouble. You seem to have things well in hand as far as remote administration with ssh/sftp is concerned. As far as a gui for server administration, have a look at [Webmin]("http:///www.webmin.com/"), it is a web based server admin suite.

I think you misunderstand what I'm trying to do. I already have Webmin installed and setup, I'm trying to avoid things like Webmin for server administration, unless I really need it because, It takes away from my learning of the CLI, but I would like to be able to is work on a GUI based program while at home and all the data coming to and from the program would be sent through my server and I could work with that program as if I was running it locally on the server. 

I will, however, try to use the Xserver solution. It sounds interesting, and I hope it works. Thanks to everyone that has helped and will help me.

---

### Post by munchi3s on 2009-10-03
> **sunstriker said:**
> Hi!

I'm also using this technique to get a firefox open at home from my office (in case of port forwarding, or if the Win2003 TS Virtual Machine has crashed). What I do is the following (i'm working on Mac OS X, but I think this should also work on Ubuntu):

[LIST]
[*]Open a terminal
[*]Type "ssh -X [username]@[ip address of your server]
[/LIST]

this should start the X server (on mac os x, on ubuntu it'll be already running).
If you then type in "firefox" or any other kind of X program, it will just pop up on your desktop.

I believe it is also possible to use Xnest to start an entire Gnome session in a window.

I hope this helps!

Greetz

It worked sorta. I was able to connect via the ssh -X command; I was also able to start firefox and gedit,
but they were so unbelievably slow that I couldn't do anything with them, I couldn't edit the document I wanted to with any efficiency and I wasn't able to get firefox to do anything, although it opened on my desktop. I think it may have something to do with our Internet connection. It is supposed to be a business connection, but when I tested it I got 1.2 mbs. At home I get 1.8 mbs. To me this is truly sad and I think were being jipped. 

Thanks for all your help. If anyone has any other ideas please post them.

---

### Post by sunstriker on 2009-10-05
Hi!

Yes, tunneling X through SSH is kinda slow. My server has an 1mbit upload and it's not really usable. Another solution (but can have some side-effects in Gnome) is sending XDMCP through VNC. If you connect to your server using VNC you'll get a login screen (just like M$'s RDP) and can start a session...

[http://ubuntuforums.org/showthread.php?t=795036]("http://ubuntuforums.org/showthread.php?t=795036")

However, my "gnome-setings-daemon" crashed under 8.04 when I use this solution.

---

