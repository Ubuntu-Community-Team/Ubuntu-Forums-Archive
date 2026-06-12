---
title: "Ubuntu Server 14.04 LTSP problems"
date: 2016-03-30
forum: Server Platforms
---

### Post by evan32 on 2016-03-30
Hi everyone,

This is my first post on the forum so just bear with me while I try to explain my situation. I followed this guide [http://ubuntuforums.org/showthread.php?t=2173749](http://ubuntuforums.org/showthread.php?t=2173749) 

I'm busy building an LTSP server on ubuntu server 14.04 LTS and I cannot seem to solve this issue whereby as I get to the bootsplash screen and logon, I enter in my user and password, enter and it just hangs on the splash screen forever.

Here are the syslogs from the server:

```
Mar 30 13:07:02 termsvr2 nbd_server[27738]: virststyle ipliteral
Mar 30 13:07:02 termsvr2 nbd_server[27738]: connect from 10.0.0.12, assigned file is /opt/ltsp/images/i386.img
Mar 30 13:07:02 termsvr2 nbd_server[27738]: Can't open authorization file (null) (Bad address).
Mar 30 13:07:02 termsvr2 nbd_server[27738]: Starting to serve
Mar 30 13:07:02 termsvr2 nbd_server[27738]: Size of exported file/device is 343355392
Mar 30 13:07:02 termsvr2 nbd_server[27738]: Disconnect request received.
Mar 30 13:07:02 termsvr2 nbd_server[27584]: message repeated 2 times: [ Spawned a child process]
Mar 30 13:07:02 termsvr2 nbd_server[27584]: Child exited with 0
Mar 30 13:09:53 termsvr2 dhclient: DHCPREQUEST of 10.0.0.11 on eth0 to 10.0.0.1 port 67 (xid=0x2f2e8b6f)
Mar 30 13:09:53 termsvr2 dhclient: DHCPACK of 10.0.0.11 from 10.0.0.1
Mar 30 13:09:53 termsvr2 dhclient: bound to 10.0.0.11 -- renewal in 271 seconds.
Mar 30 13:10:31 termsvr2 nbd_server[27584]: Spawned a child process
Mar 30 13:10:31 termsvr2 nbd_server[27815]: virststyle ipliteral
Mar 30 13:10:31 termsvr2 nbd_server[27815]: connect from 10.0.0.12, assigned file is /opt/ltsp/images/i386.img
Mar 30 13:10:31 termsvr2 nbd_server[27815]: Can't open authorization file (null) (Bad address).
Mar 30 13:10:31 termsvr2 nbd_server[27815]: Starting to serve
Mar 30 13:10:31 termsvr2 nbd_server[27815]: Size of exported file/device is 343355392
Mar 30 13:10:31 termsvr2 nbd_server[27815]: Disconnect request received.
Mar 30 13:10:31 termsvr2 nbd_server[27584]: Child exited with 0
```

Any ideas?

---

### Post by howefield on 2016-03-30
Thread moved to the "*Server Platforms*" forum.

---

### Post by Graham_Willis on 2016-03-31
Have you tried booting the server in single user mode? When you're in GRUB menu you should press 'e' having Ubuntu highlited, then find

```
linux /vmlinuz-3.13.0-32-generic root=/dev/mapper/ubuntu-vg-root ro
```

then append 'single' after that line (separated by a space), so it would like this way:

```
linux /vmlinuz-3.13.0-32-generic root=/dev/mapper/ubuntu-vg-root ro single
```

then Ctrl+X.

Let us know if it makes it possible for you to access the console and issue commands. If yes, it'd indicate that some services are blocking successful boot and it'd be necessary to identify them and turn off/determine why they cause boot process to basically fail.

---

### Post by evan32 on 2016-04-04
Hi Graham,

Silly error on my part...I wasn't understanding how LTSP worked and I put the desktop environment on the /opt/ltsp/i386 image instead of putting it on the server itself...Another issue arose where when I login to the Desktop with an account and when I log back out it continuously says "authentication error" under the password section and I cannot type in the password as it keeps resetting it?

---

### Post by MAFoElffen on 2016-04-07
Let me get this straight in my head:
- You get a successful net PXE boot from the TSTP server
- You receive your dhcp setting successfully.
- You get the ro image from the server
- It boot successfully to the Graphical login.
Then it fails on the credentials?

---

### Post by evan32 on 2016-04-08
First 4 correct :)

I made a mistake with my wording. Okay so whenever I LOCK the screen it does that flickering/password resetting thing with "authentication error" underneath the password field. However when I go to my user in the graphical interface and logout it it sends me to the boot splash LTSP screen and I can login again no problem.

---

### Post by MAFoElffen on 2016-04-08
I installed an LTSP server and a Client into a class 1 hypervisor (albiet v16.04b2) and recreated the same problem. Things did change from v12.04 to 14.04... but I see only similarities between 14.04 and 16.04 (as it relates to LTSP). But 16.04 still has the same problem.

I don't know yet. Here is what I see with the "recreation":
-> What I asked about in my last post, is what I see. It gets to the graphical login and when it goes from "that" with the credentials and to init xorg, it instead loops back to the graphical login.

Usual suspects are either something to do with the passing of the user credentials, ssh keys, or the User's .Xauthority file...
- I've ruled out the ssh keys. Or at least, I've recreated them enough times, that it would be unlikely that they are not there or incorrect.
- I get not visual error that is being displayed, that would indicate incorrect credentials. I've seen that enough to recognize what to look for in that... and that is not showing (that I can see so far). My admin user and other user is there with passwords...

I did find a few initial issues with xorg. Xorg needs and xorg authority file that is owned by the user, to hold the permissions and basic graphics profile (.Xauthority). That is generated initially when the user logs in the first time. Since it is an ro file system, of course it was not there I added it manual, with the correct permissions and ownership. But it still has the same behavior.

Had a few minutes before my next meeting, and is coming up... so will get back to this tonight.

---

### Post by evan32 on 2016-04-09
Thanks Mafoelffen, this is very good information for me. Yeah, so it goes from the LTSP boot splash screen to the desktop for me mostly, but now it goes to the gnome login screen(same screen you get when you lock the screen ofcourse).

I couldn't see anything alarming in the log files but I haven't really looked that far into Xorg so it could be something to do with that. I also recreated ssh keys(ltsp-update-sshkeys) multiple times, so it's not that.

It won't even give you a chance to login as it permanently resets the password field. Very weird error.

Thanks very much for your response mafoelffen :)

---

### Post by MAFoElffen on 2016-04-10
Well, mine goes to the attached screenshot. But when you enter the credentails, returns back to that same screen.

If I do an <Cntrl><Alt><F1>, I can login through ttty1. So the login itself is okay...

I find a permissions problem in the xinit:
```

xauth: timeout in locking authority file //.Xauthority

```
So that tells me, with the default install, there seems to be a permissions problem with the nfs share. But still digging.

---

### Post by evan32 on 2016-04-11
I've just managed to fix it now. From the login screen I enter the ttty1 shell and the restart the service X11-common. For some reason that allowed me to login and produced no errors. Very odd.

Almost forgot I changed permissions on my user to 777. chmod 777 /home/user

Hi MAF,

yes I've changed the permissions to 700 now for security purposes of course.

---

### Post by MAFoElffen on 2016-04-13
Congratulations on finding a solution!

You might want to play with those [permissions to see what the "least" level is that you cxan get away with, instead of opening it up to the world (777). Even though, the dhcp is only going to give read-only access to locally attached thin-clients, Just a good practice of least privilege security.

Please revisit this thread and use the link on the upper left of the page "Thread Tools" > and then "Mark as Solved". This will hep other users to find a solution to their similar problems when they search for it on the forum.

---

### Post by evan32 on 2016-04-14
Hi MAF,

yes I've changed the permissions to 700 now for security purposes of course.

---

