---
title: "SSH help"
date: 2010-08-27
forum: Security
---

### Post by linuxnovice on 2010-08-27
Hello,

I apologize if this is a wrong place to post my question.

This is the problem I have: There is a computer B which is running a software and sending data through port 6665. This computer is connected to an ad-Hock network with computer H acting as a bridge. Now, I can connect to computer B by ssh'ing from my machine to computer H and then ssh'ing to computer B from there. There is a graphical viewer to view the data sent by the software running on computer B. 

Now here is my question. I was told that there is a way for me to do some port forwarding so that I can transmit that data from computer B to computer H and then to my machine. This way I can run the graphical viewer on my machine and connect to localhost and view the data. But I have no idea how to do this. This would be great as opposed to sshing to computer H with X, then sshing to computer B from there with X again.

As a background, computer B is actually a mobile robot and H is just a server which acts as a bridge between the ad-hock network and internet.

Thanks.

---

### Post by BkkBonanza on 2010-08-27
There's a couple ways to handle this. Probably the easiest is to use ssh as a dynamic (SOCKS5) proxy.

On your machine, (which has no name above?) call it D for desktop. Run,

**ssh -fND 8080 user@ip-or-name-for-H**
(-f = background, -N = no command, -D = dynamic proxy)

Ths starts the proxy on your localhost at port 8080. Any connection made to that port using SOCKS5 will be routed to machine H instead and actually operate there.

So if you are using a X viewer and you tell it to use a SOCKS proxy at localhost:8080 (or if not directly supported in options it may use the system settings at "Systems->Prefs->Network Proxy"). Now tell it to view data at ip-or-name-for-B:6665 and it should relay that connection to H, which will open a connection to B.

When done remember to kill the ssh process still running in the background.

This method works as long as your viewer can use a SOCKS5 proxy. There is a way to do it if it can't but then you may find it easier to use a tunnel.

There is a handy util in the repos called gSTM that gives you a GUI tool to start/stop the ssh proxy, which makes it a bit easier. One command isn't very hard though.

---

### Post by linuxnovice on 2010-08-28
> **BkkBonaza said:**
> There's a couple ways to handle this. Probably the easiest is to use ssh as a dynamic (SOCKS5) proxy.

On your machine, (which has no name above?) call it D for desktop. Run,

**ssh -fND 8080 user@ip-or-name-for-H**
(-f = background, -N = no command, -D = dynamic proxy)

Ths starts the proxy on your localhost at port 8080. Any connection made to that port using SOCKS5 will be routed to machine H instead and actually operate there.

So if you are using a X viewer and you tell it to use a SOCKS proxy at localhost:8080 (or if not directly supported in options it may use the system settings at "Systems->Prefs->Network Proxy"). Now tell it to view data at ip-or-name-for-B:6665 and it should relay that connection to H, which will open a connection to B.

When done remember to kill the ssh process still running in the background.

This method works as long as your viewer can use a SOCKS5 proxy. There is a way to do it if it can't but then you may find it easier to use a tunnel.

There is a handy util in the repos called gSTM that gives you a GUI tool to start/stop the ssh proxy, which makes it a bit easier. One command isn't very hard though.

Thanks for you reply. However, this doesn't seem to work. This is what I did: I ran 
**ssh -fND 6665 user@ip-or-name-for-H** on my machine. Then I ssh into H and from there ssh into B. In B I ran the software. On my machine in another terminal I launched the view and it failed to launch because it couldn't connect to localhost:6665.

Also, I have no problems dealing with the terminal so I appreciate any sort of help on this.

Let me elaborate on my first post. These are the naming conventions:

Softwares: player(software running on the robot), playerv(viewer)

player listens/sends data on localhost:6665. playerv listens on localhost:6665 and captures the data that comes in and displays it graphically. 

Machines: M, H, B

M - my machine (either laptop or desktop at home)
H - bridge between the ad-hock network for the robots (which includes B) and another network (to which I have direct access to)
B - robot where software player is running.

So what I want to do is run playerv on M and player on B and view data sent by player on B using playerv on M. However, I can only connect to B from M through H. 

Also, the ports are important here as player and playerv only uses localhost:6665. So basically playerv will be connecting to M:6665 (localhost:6665 on M) and player will be connecting to B:6665(localhost:6665 on B) with H between them. My problem is connecting these two ports. As I mentioned earlier, I am under the impression that connecting these ports and just sending the data for viewing is much faster than using ssh with X on both M to H and H to B and run playerv on B directly. Because, I tried this already and it was painfully slow.

Thanks.

---

### Post by BkkBonanza on 2010-08-28
The problem is that playerv tried to connect to localhost:6665 when you would need to use it as a proxy, and then connect to H:6665. However, if the playerv is limited and cannot use a proxy or connect to H:6665 then this method won't work. (Although using a program like tsock can fix that).

So if playerv can ONLY connect to localhost:6665 then you would have to setup a double tunnel.
[B]
ssh -fNL 6665:H:6665 user@H[/B]
(opens a tunnel from localhost:6665 over to H:6665)

As a trial then,

**ssh user@H**
(login into H)
**ssh -fNL 6665:B:6665 user@B**
(open a tunnel from H over to B)

If that works then you can combine both those steps into one command to make it easier to script from M alone:

**ssh user@H "ssh -fNL 6665:B:6665 user@B"**
(which opens a tunnel on H over to B)

The result of this is a tunnel from M to H to B. When playerv connects to localhost:6665 it gets sent through to H to B where it should get to the data.

[As a side note... if you could configure H to act as a hotspot rather than peer connection to B, then you could gain direct access to B from M. That would allow a single tunnel. However, configuring H as a hotspot would require it have a master mode capable wifi adapter. And generally most adapters don't do that well, and even when they do, it's some work to get it going. On the other hand, if B has net access, then the tunnel could be run there to go direct to M allowing it to feed data out directly to M.]

---

### Post by linuxnovice on 2010-08-28
> **BkkBonaza said:**
> The problem is that playerv tried to connect to localhost:6665 when you would need to use it as a proxy, and then connect to H:6665. However, if the playerv is limited and cannot use a proxy or connect to H:6665 then this method won't work. (Although using a program like tsock can fix that).


Thanks. I discovered playerv is not limited at all. Here is what playerv help gives me:

```
PlayerViewer 3.0.0
Xlib:  extension "RANDR" missing on display "/tmp/launch-HHeLN2/:0".
Connecting to [localhost:6665]
playerc error   : connect call on [localhost:6665] failed with error [61:Connection refused]
playerv : error in /opt/local/var/macports/build/_opt_local_var_macports_sources_rsync.macports.org_release_ports_science_playerstage-player/work/player-3.0.0/utils/playerv/playerv.c
  connect call on [localhost:6665] failed with error [61:Connection refused]

PlayerViewer 3.0.0, a visualization tool for the Player robot device server.
Usage  : playerv [-h <hostname>] [-p <port>] [-rate <Hz>]
                 [--<device>:<index>] [--<device>:<index>] ... 
Example: playerv -p 6665 --position:0 --sonar:0

```

So given that it accepts -p as an command line option, I believe we could do what you suggested the first time. I would however, appreciate it if you could elaborate more on what I need to do (i'm a network noob as you might've guessed already :))

> **BkkBonaza said:**
> 
So if playerv can ONLY connect to localhost:6665 then you would have to setup a double tunnel.
[B]
ssh -fNL 6665:H:6665 user@H[/B]
(opens a tunnel from localhost:6665 over to H:6665)

As a trial then,

**ssh user@H**
(login into H)
**ssh -fNL 6665:B:6665 user@B**
(open a tunnel from H over to B)

If that works then you can combine both those steps into one command to make it easier to script from M alone:

**ssh user@H "ssh -fNL 6665:B:6665 user@B"**
(which opens a tunnel on H over to B)

The result of this is a tunnel from M to H to B. When playerv connects to localhost:6665 it gets sent through to H to B where it should get to the data.

This seems to work except, this is what I get on the player end and playerv end:

player:
```
listening on 6665
Listening on ports: 6665 
channel 2: open failed: connect failed: Connection refused

```

playerv:
```
PlayerViewer 3.0.0
Xlib:  extension "RANDR" missing on display "/tmp/launch-HHeLN2/:0".
Connecting to [localhost:6665]
playerc error   : incomplete initialization string
playerv : error in /opt/local/var/macports/build/_opt_local_var_macports_sources_rsync.macports.org_release_ports_science_playerstage-player/work/player-3.0.0/utils/playerv/playerv.c
  **incomplete initialization string**

PlayerViewer 3.0.0, a visualization tool for the Player robot device server.
Usage  : playerv [-h <hostname>] [-p <port>] [-rate <Hz>]
                 [--<device>:<index>] [--<device>:<index>] ... 
Example: playerv -p 6665 --position:0 --sonar:0

```

> **BkkBonaza said:**
> 
[As a side note... if you could configure H to act as a hotspot rather than peer connection to B, then you could gain direct access to B from M. That would allow a single tunnel. However, configuring H as a hotspot would require it have a master mode capable wifi adapter. And generally most adapters don't do that well, and even when they do, it's some work to get it going. On the other hand, if B has net access, then the tunnel could be run there to go direct to M allowing it to feed data out directly to M.]

Unfortunately, I have no control over H as it belongs to the university.

Thanks for your help!

---

### Post by BkkBonanza on 2010-08-28
It's hard for me to know because I'm not familiar at all with the player apps.
It could be order of setup. I think it should be,

1. start player on B
2. start tunnel on H to B
3. start tunnel on M to H
4. start playerv

It seems like playerv tried to connect to player and was refused. 
---------

For the first method to work playerv has to support a SOCKS proxy. It doesn't indicate that in the help info unless it has more info via **man playerv**.

There is a program called tsocks that you can run first and it will virtualize the port access to use a SOCKS proxy even if playerv doesn't natively support it.

If you want to try that here's how,

**sudo apt-get install tsocks**

Edit /etc/tsocks.conf to have port value desired, eg. 8080 (not sure what default is), but proxy values must match ssh cmd below, 127.0.0.1 is same as localhost, and I think that is default.

**ssh -fND 8080 user@H**

**tsocks playerv -h B -p 6665**    (that is B meaning B machine IP value)

(tsocks provides an emulation layer to playerv. playerv thinks it's talking to B:6665 but actually tsocks feeds it thru to the proxy at localhost:8080, which in turn is routed to H where it opens the connection to B:6665)

Wow, eh. But that should work and is only two local commands (after setup that is). Of course, player on B needs to be running already so it is listening, otherwise playerv will be refused.

Note also that on B the port 6665 must be "open", ie. not firewalled so that H can connect to it. If it's normally used to talking on localhost then it may be blocked by default.

---

### Post by linuxnovice on 2010-08-28
> **BkkBonaza said:**
> It's hard for me to know because I'm not familiar at all with the player apps.
It could be order of setup. I think it should be,

1. start player on B
2. start tunnel on H to B
3. start tunnel on M to H
4. start playerv

It seems like playerv tried to connect to player and was refused. 
---------

For the first method to work playerv has to support a SOCKS proxy. It doesn't indicate that in the help info unless it has more info via **man playerv**.

There is a program called tsocks that you can run first and it will virtualize the port access to use a SOCKS proxy even if playerv doesn't natively support it.

If you want to try that here's how,

**sudo apt-get install tsocks**

Edit /etc/tsocks.conf to have port value desired, eg. 8080 (not sure what default is), but proxy values must match ssh cmd below, 127.0.0.1 is same as localhost, and I think that is default.

**ssh -fND 8080 user@H**

**tsocks playerv -h B -p 6665**    (that is B meaning B machine IP value)

(tsocks provides an emulation layer to playerv. playerv thinks it's talking to B:6665 but actually tsocks feeds it thru to the proxy at localhost:8080, which in turn is routed to H where it opens the connection to B:6665)

Wow, eh. But that should work and is only two local commands (after setup that is). Of course, player on B needs to be running already so it is listening, otherwise playerv will be refused.

Note also that on B the port 6665 must be "open", ie. not firewalled so that H can connect to it. If it's normally used to talking on localhost then it may be blocked by default.

For some reason I keep getting a bus error when I run tsocks. In any case, I sort of got it work doing this:

**ssh -fNL 6665:localhost:6665 user@H**
**ssh -fNL 6665:localhost:6665 user@B**

Then I ran player on B and playerv on M and it worked without that error about the initialization string. I could even get the laser data from player. However, I couldn't get the camera data. But thats another problem.

What I'd like to know is why this would work and not the previous 
**ssh -fNL 6665:H:6665 user@H**
and so on. What am I doing different here?

Thanks.

---

### Post by BkkBonanza on 2010-08-28
Could just be I gave you wrong info. Since I can't actually try it I could be wrong.
I'd have to go check the manual but the middle host parm could be relative to the logged in system and hence localhost would work correctly.

There is a first host value that is localhost by default and dropped. ie. 
localhost:6665:localhost:6665 is what you are doing. And it would mean from localhost:6665 to localhost:6665 *on the target system*.

Anyway, if it works then it works.

I gather that the second ssh line you gave is once your'e logged in on H. Because if you can connect directly to B from M, then you don't need to go through H at all. So you could just use one tunnel.

Also, incidentally, if you want to start player on B without a seperate login then you can do the tunnel and command in one line,

**ssh -fL 6665:localhost:6665 user@B player**

(this opens the tunnel and starts the player at the same time)

---

### Post by BkkBonanza on 2010-08-28
A couple more notes...

It could be using H as the host opens the tunnel on the public IP and it's blocked by default. So localhost actually makes more sense since that is open by default.

It is possible to wrap this all into one command on M,

ssh -fL 6665:localhost:6665 user@H "ssh -fL 6665:localhost:6665 user@B player"

This opens tunnel to H, runs the ssh command to open tunnel to B and in turn runs player. In theory. I haven't tested it but it *should* work. But after done, you'd want a fancy pants command to kill them too.

---

### Post by linuxnovice on 2010-08-29
> **BkkBonaza said:**
> 
This opens tunnel to H, runs the ssh command to open tunnel to B and in turn runs player. In theory. I haven't tested it but it *should* work. But after done, you'd want a fancy pants command to kill them too.

Thanks. It works beautifully. And what might that fancy pants command be :P ?

---

### Post by BkkBonanza on 2010-08-29
Hmmm, this is just off the top of my head - so test carefully, it may not be quite right... 

ssh userH@H "ssh userB@B pkill player && pkill -u userH ssh" && pkill -u userM ssh

(ssh to H and from there ssh to B where we kill player, then back on H kill the second tunnel, then back on M kill the first tunnel)

However, **pkill -u user ssh** will kill all **ssh** run by that user, so if you have other sessions open, beware. The better way to do all this is probably to make a script that records what the process ids are (in /var/run is typical) so that they can be killed later by id. That way no mistaken ssh sessions would be killed. Here, I added the **-u user** to limit it at least to your own.

---

