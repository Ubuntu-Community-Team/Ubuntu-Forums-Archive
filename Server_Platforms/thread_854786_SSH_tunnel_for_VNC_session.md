---
title: "SSH tunnel for VNC session"
date: 2008-07-09
forum: Server Platforms
---

### Post by papatrpt89 on 2008-07-09
Hello,

I have set up a server running Xubuntu 8.04 on an old box I had laying around.  I have a basic LAMP configuration set up and running just fine.

My question involves remote administration.  I have SSH (openssh) and VNC (x11vnc) set up, both working correctly.  When using via VNC, I tunnel through SSH, which is also working as it should, forwarding the VNC port to the machine I am administering from.  However, I can also connect to VNC without using encryption.  I would like to disable this.

I have done some digging, and unearthed a thread of interest.
[http://ubuntuforums.org/archive/index.php/t-11808.html](http://ubuntuforums.org/archive/index.php/t-11808.html) - This thread mentions using the hosts.allow and hosts.deny files.  I believe this is what I need to edit.  However, I do not understand what options I need to set in these files, nor am I 100% sure this is what I need to do.

For the moment, this is mostly a hypothetical problem, because I have a router.  I simply do not forward the VNC port on the router, and there isn't a path to VNC except via SSH from the WAN.  However, this is still possible in the LAN, and this router may not always exist in the equation.

Thanks in advance for your responses.  I am relatively new to setting up Linux servers (this is my first) but I have a decent understanding of networking and am certainly eager to learn more!

---

### Post by HalPomeranz on 2008-07-10
Actually the easiest thing to do is to just start your x11vnc server with the "-localhost" option.  This will tell the server to only listen on the internal 127.0.0.1 network address.  Thus it will only be available to connections that originate from "inside" the machine, like the endpoint of your SSH tunnel.  It will not be available to unencrypted connections from outside the machine.

Note also that there's alternate an example in the x11vnc manual page ("man x11vnc" for more info) on how to run x11vnc remotely via SSH:

```

In brief:

     ssh -t -L 5900:localhost:5900 far-host ’x11vnc -localhost -display :0’

% vncviewer -encodings ’copyrect tight zrle hextile’ localhost:0

```

Run the first "ssh ..." command in one window and the "vncviewer ..." command in another window.  The advantage to this approach is that the remote VNC server will only run for as long as you leave the SSH connection open and will close down when you close the session.  OTOH, this may not be what you want.

---

