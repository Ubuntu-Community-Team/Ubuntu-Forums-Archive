---
title: "remote X -vs- X forwarding"
date: 2009-10-03
forum: Server Platforms
---

### Post by jeffsa12 on 2009-10-03
I've been thinking for some time about the following.

Lets say I have 2 Linux distros installed on 2 different computers on my local network. One (#1) with a normal graphical desktop environment and one (#2) without X installed, such as a server distro.

I think I understand ssh and x forwarding. It requires that the OS to be accessed has x installed and can be remotely accessed graphically (gui).

My question is, is it possible to access #2 via #1 using ssh, and display on #1 using a gui application and #1's x, etc.?

Lets say I'm more comfortable working with the file system via gui, but don't want to install x on my server, so I would use Nautilus on #1 to manipulate files on #2.

I'm thinking this would be possible, and probably is. Am I making something thats simple complicated here?

---

### Post by scorp123 on 2009-10-03
> **jeffsa12 said:**
>  Lets say I'm more comfortable working with the file system via gui, but don't want to install x on my server, so I would use Nautilus on #1 to manipulate files on #2.  Installing "nautilus" on the server will definitely pull in X11 stuff as dependency.

But if you have "nautilus" locally on your desktop ... why not use the "Connect to Server" feature and then simply mount the remote server as if it were an external network drive? Yes, this works with SSH/SFTP connections too.

Or ... if you're such a fan of SSH and the shell --congratulations, it's alwyay good to learn this stuff!-- why not use "mc"?

"mc" is like good old "Norton Commander" on MS-DOS. So yes, you'd be in a terminal, and yet you'd have a comfortable file manager that "just works" even though you're in text-mode.

As I see it there is absolutely no need for X forwarding in your scenario. Let the server be without X "as is". You don't need X there.

---

### Post by mbuell on 2009-10-03
Dude - when you find the answer I want to know!

Here is what I HAVE found - and this does work with two machines with gnome desktops on both. (thx to Ben Leov and sunstriker)

> On your client machine, run xhost +server_address. i.e
xhost +192.168.1.34

Within the same shell, connect to the remote pc, via ssh -X user@server_address. i.e

ssh -X admin@192.168.1.34 

Now run your application.

The thing of this is tho - that it runs the app on the remote pc, but displays it on the client. Not exactly what you asked for. 

Also, for file management - you could use Samba. You can also, using ssh, run something like midnight commander on the remote pc, if you have something like that installed. That would, from the client, let you see your files on the remote pc. Forgive me if you already know all this - just offering what I have. 

Best of luck, and please post your results
Hiero

---

### Post by mbuell on 2009-10-03
Scorp123 is right about "connect to server", but I have to use the URL to make this work - I can't do it using the server name. Don't know why.

And, this still isn't quite what you requested - but still adding to aggregate knowledge.

---

### Post by jeffsa12 on 2009-10-03
> if you have "nautilus" locally on your desktop ... why not use the "Connect to Server" feature and then simply mount the remote server as if it were an external network drive? Yes, this works with SSH/SFTP connections too.


OK... I believe that answers my question then.

Just to further calrify, my new server setup will have no x installed, but will have open ssh server installed.

Then I'll just connect to my server, using one of my desktop's "Connect to Server" with the ssh option and it will open via Nautilus?

I thought I'd have to have x installed on my server for that situation. 
Would this senerio be using remote x?

I use ssh via "Connect to Server" inputting the ip of the OS I want to access, all the time between my Linux desktops (currently Arch 64bit) on my local network, but they all have Gnome desktop, x, etc etc.

Why isn't this recommended more often as an alternative to installing a GUI (I know...BAD) on a server, rather than just raging on about how bad it is to do???

This, combined with Webmin, would be the perfect GUI solution to manage a home server...and no need to install x...best of both world!!!

I've played around a bit with MC but would prefer Nautilus if possible.

I thought Samba was for windoz access to the Linux file system via ssh, and I don't use windows.

I've set up a few home web site servers for myself, both virtual and real, and ended up installing Ubuntu desktop once and a very basic gnome the second time. I'd like to be able to do it without a GUI installed on the server, and realize the benifits. This would be a perfect option for me!!!

Thanks for all the input!!!

---

### Post by jeffsa12 on 2009-10-05
**Follow up:**

I did a fresh 8.04 32 bit lamp/ssh server install on real (not virtual) hardware today and got my website back up.

The Nautilus connection to a remote file system via ssh server works awesome!! 

This really should be promoted more often as a great option to installing a GUI on Ubuntu server to the newbs and GUI lovers like me. 

I did have to enable root login on my server to manipulate files remotely using Nautilus though. Sorry, it's not allowed to explain how to do that here. Perhaps someone will step in and explain an option thats better in this situation...

Could always disable root login after getting things set up...Now I'll have to go find that command!!

I installed mc, but I'm contemplating Webmin now though. I really feel the need to learn all the configuration through the command line. I'm totally comfortable navigating the file system via command line and editing files with nano...... I just need to get up to speed with server configuration.

I'm gonna install Wordpress soon, and I'm going to try using ssh and command line only and see how it goes. 

I'll try to follow up here with my results.

---

### Post by jeffsa12 on 2009-10-10
**Follow up 2**

Wordpress installed and up at [http://www.jeffstory.org/blog](http://www.jeffstory.org/blog) 

I didn't install WebMin. All SSH and command line.

Now I just have to get something worthwhile up to read!!!

---

