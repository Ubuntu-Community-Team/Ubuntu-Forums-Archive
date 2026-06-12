---
title: "Nx Client"
date: 2010-11-02
forum: Ubuntu Cloud and Juju
---

### Post by Steve N on 2010-11-02
Greetings,

I am trying out a EC2 desktop instance with the aim of using it to provide virtualised training. Using the nxclient from NoMachine and the installed neatx on 10.10 I have been able to get good desktop performance, even on a heavily loaded office link.

However the ability to connect to the instance is quite problematic. Often the nxclient (running on Mac) times out. The debug logs show that authentication succeeds, the server responds with nx> 105. At this point nx client should request a list of open sessions, but instead just goes silent, eventually timing out.

Most frustrating is that it *sometimes* works, that's how I know what it *should* be doing (by looking at the successful connections in the debug log).

Can anyone here recommend a website, debugging tools or other forums? How about a known working combination (e.g. FreeNX). Using the Nomachine server isn't really an options, since I'll need 10+ people connecting during training, although if that's the only way, I'll have to go back and suggest we spend the money to buy it.

 I'm not stuck using 10.10, so if Lucid is a better choice, happy to downgrade, although my experiments this morning show the same problem with Lucid.

Regards,
    - Steve

---

### Post by Steve N on 2010-11-03
Solved.

Apparently nxclient is able to run when the link is under heavy load, but not establish a connection. I closed down everyone but myself over lunch hour and was able to start/stop/resume sessions several times, and maintain those sessions.

Once the floodgates were opened up to the masses again though, the problem reappeared, although the already established sessions performed tolerably well. 

Now if I can just sort out the keyboard mappings....

SteveN

---

### Post by Gil Freuund on 2010-12-23
Just to say I have been having similar problems. Under high CPU usage, I will get disconnects and then either authentication errors or timeouts. 
Does not seem to be an issue with memory or disk space.

---

### Post by bmullan on 2011-01-02
> **Steve N said:**
> Solved.

Apparently nxclient is able to run when the link is under heavy load, but not establish a connection. I closed down everyone but myself over lunch hour and was able to start/stop/resume sessions several times, and maintain those sessions.

Once the floodgates were opened up to the masses again though, the problem reappeared, although the already established sessions performed tolerably well. 

Now if I can just sort out the keyboard mappings....

SteveN

You might want to try [x2go]("http://wiki.x2go.org/") instead of Neatx and NoMachine NX client.

I say this for several reasons.

Neatx is _not_ that actively developed.. at least the mail list from it doesn't show much if any activity.

x2go is actively developed.   It has its own "server-side" and clients (mac, pc, linux) and also a java plugin for simply using firefox for the client (plugin is available but not released yet... but it works).

x2go also comes out of the gate with sound/audio working whereas NoMachine's v3.x clients don't.   x2go also supports easy setup of shared directories for the user as well as local printing from the remote machine.

There is also a major update that should be available soon (when the plugin will also be officially released).

Recently there has also been strong development of a Python based x2go client called PyHoca.   You still install the x2go server on your remote 'server' but you can use the PyHoca client to connect.   You can read a little about the [PyHoca Python x2go client here]("http://das-netzwerkteam.de/site/?q=node/71").

x2go utilizes the NX protocol so you get the same great nx performance.

Note that there are 3 different versions of the x2go "server-side" application.   Read about what each does and decide what you need for your own use.

Setting it up is a no brainer on Ubuntu as you can use the Debian PPA's in the URL above to automagically install either the server or the client.

On Windows or Mac just follow the instructions to get up on those environments also.

If you go this route I'd advise joining the x2go mailing list to keep up with the project and also to ask questions.

I've used NoMachine's NX, FreeNX, NeatX and also Red Hat's SPICE but only x2go seemed to install simply and work correctly.

With NoMachine's NX going closed source in their version 4.0 release x2go is well worth taking a look at.

---

