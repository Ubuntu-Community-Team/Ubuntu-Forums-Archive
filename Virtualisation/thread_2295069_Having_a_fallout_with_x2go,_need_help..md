---
title: "Having a fallout with x2go, need help."
date: 2015-09-15
forum: Virtualisation
---

### Post by Higgins909 on 2015-09-15
I need to use virt-manager and the only way I've been able to make it work on windows is use putty with x11 forwarding and have x2go open at the same time, in a terminal.
I got a virtualbox with ubuntu mate because I wanted to test it out and I'm pretty much running into the same problem.  after typing virt-manager I get error 50, something about a proxy and network.

altho with the ubuntu I was able to get the key over.. or atleast I think I did, but not sure what point it had, as it seems it more of a login assist.

---

### Post by TheFu on 2015-09-15
Probably not a virtual-machine question.

Does ssh work?
Does any desktop get displayed after the connection is made?
Do other applications work?

Anything in these to help?
[http://wiki.x2go.org/doku.php/doc:installation:x2goclient#detailed](http://wiki.x2go.org/doku.php/doc:installation:x2goclient#detailed) 
 [http://wiki.x2go.org/doku.php/doc:de-compat](http://wiki.x2go.org/doku.php/doc:de-compat)
[http://wiki.x2go.org/doku.php/doc:faq:start](http://wiki.x2go.org/doku.php/doc:faq:start)
[http://wiki.x2go.org/doku.php/doc:release-notes-mswin](http://wiki.x2go.org/doku.php/doc:release-notes-mswin)

---

### Post by Higgins909 on 2015-09-21
Nothing in there caught my eyes.
I've tried windows 7 windows 10 and ubuntu mate and they all end the same.
ssh works.
The server has no desktop?  It's just a cli/ssh.

Made this video a while ago but wanted to take the audio out and was having issues with my video editor, just I finally uploaded it raw.
[URL="https://youtu.be/n8woTyx2EeY"]https://youtu.be/n8woTyx2EeY
[/URL]

---

### Post by TheFu on 2015-09-22
> **Higgins909 said:**
>  
The server has no desktop?  It's just a cli/ssh.
 

The "server" must have desktop X-programs installed or x2go won't work. It provides a remote desktop by running all the desktop stuff (both client and server for X/Windows) on the remote machine, then shipping a compressed copy of that virtual-desktop over the network, thru an ssh-tunnel, back to whatever machine you are sitting behind.

The "server" must have at least a Window Manager loaded - something like openbox, fvwm, LXDE, XFCE ... 1 of those, or it won't work as a remote desktop.

Looking at your video ... 
Ok ... see the "session type" setting?  You've told it to display an xterm ... which it does. Why ignore that?  Type virt-manager into the terminal. It is likely you just didn't setup the "DISPLAY" environment variable. What is it as seen inside the xterm?

I wouldn't run a full remote desktop if I just want to run 1 program. If you want a desktop, change the "session type" to be for an "x2go supported" desktop and load that.

Oh - and check out "tab completion" - no need to type so much. [https://www.youtube.com/watch?v=7V-fovVlCvA](https://www.youtube.com/watch?v=7V-fovVlCvA)

---

### Post by Higgins909 on 2015-09-29
In my video I show how x2go won't work alone.  That xterminal will close with a error 50 or something (should be shown in video) when I type virt-manager in.
x2go is only there to be used by putty with virt-manager.  Without it, putty won't work, without putty x2go don't work at all, for the purpose I'm trying to do.

I don't understand why x2go won't work alone and why it works when it's used with putty.

I don't want a gui to constantly be using resources on my server, or does it only happen when x2go is connected?

...I just don't understand why putty can work virt-manager with the assistance of x2go and x2go can't solo it, without installing a gui?

---

### Post by TheFu on 2015-09-29
Running a WM is required for any X-program to have window controls -like a border. That is how X/Windows works.

Did you check the DISPLAY environment variable?
Did you set LXDE as the session type?

---

