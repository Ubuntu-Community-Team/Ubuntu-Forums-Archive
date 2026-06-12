---
title: "VNC over SSH question."
date: 2010-11-30
forum: Security
---

### Post by theDaveTheRave on 2010-11-30
Hi all,

I previously had a problem with VNC not recognising my keyboard input, and during the discussion on that [thread]("http://ubuntuforums.org/showthread.php?t=1629842") I got the impression that my method for VNC-ing to my box was potentially not secure.

My solution was to change to using FreeNX, or exporting X over my SSH connection - depending on the circumstance.

However my concern on my methodology still stands, so I would like your input.

Here is how I started my VNC server, and then logged into the connection....

1. SSH into my box from my laptop.
[ ssh davem@MyHomeServer ]

2 now at my server connection I start the VNC server 
[ tightvncserver start ]

3 open up the VNC client on my laptop pointing it toward 'MyHomeServer' - using xvnc4server

The discussion on the other thread gives me the feeling that this method isn't secure?

Please note that this is no longer an issue as I am now using FreeNX - I am asking this question purely from a position of wanting to better understand why what I was doing was wrong.

Thanks in advance

---

### Post by movieman on 2010-11-30
1. Configure the VNC server to only listen on localhost.
2. Start the server.
3. SSH from anywhere into the machine running the VNC server and tell ssh to forward localhost:5901 on your local machine to localhost:5901 on the machine running the VNC server.
4. Run VNC viewer on your local machine and tell it to connect to localhost:1.

You then connect to localhost:5901 and ssh forwards that to the remote machine through an encrypted tunnel.

I think the command is ssh -L localhost:5901:localhost:5901 user@remote, but don't quote me on that :).

---

### Post by bodhi.zazen on 2010-11-30
> **theDaveTheRave said:**
> Please note that this is no longer an issue as I am now using FreeNX - I am asking this question purely from a position of wanting to better understand why what I was doing was wrong.

Thanks in advance

VNC has two security flaws:

1. The connection is not encrypted by default.

2. The only thing that prevents an intruder from using the connection is a password. All too often people either use weak passwords or what they though was a strong password is actually weak.

If you use ssh, you should use keys and disable password logins.

---

### Post by cgb on 2010-11-30
Are we talking about connecting to your Desktop from inside or outside your LAN?  If inside the LAN then security is not much of a concern, just make sure all ports are blocked to the outside world.  If outside then like bodhi.zazen mentioned, if you want to use VNC Server securely you really need to be establishing a SSH tunnel with private keys, no password authentication, or you could also setup a VPN connection to the network and block any other external ports.  Then local security is not much of a concern if this is a private controlled network.  Even with using FreeNX I would typically connect through a VPN tunnel so that no ports are open to local PC's directly.

---

### Post by CharlesA on 2010-11-30
> **cgb said:**
> Are we talking about connecting to your Desktop from inside or outside your LAN?  If inside the LAN then security is not much of a concern, just make sure all ports are blocked to the outside world.  If outside then like bodhi.zazen mentioned, if you want to use VNC Server securely you really need to be establishing a SSH tunnel with private keys, no password authentication, or you could also setup a VPN connection to the network and block any other external ports.  Then local security is not much of a concern if this is a private controlled network.  Even with using FreeNX I would typically connect through a VPN tunnel so that no ports are open to local PC's directly.

That's a good point. I hardly even use VNC even inside my lan at home. It's either FreeNX or nothing.

If I am working remotely (which I have been lately), I connect to my server with SSH (key-auth only) and then create a tunnel to whatever machine I want to connect to, then connect with localhost:someportnumber.

FreeNX really is way better then VNC when it comes to high latency links.

---

### Post by theDaveTheRave on 2010-12-02
Hi guys.

Thanks for the input, you've definately cleared things up for me.

So here is my current understanding.

Although I was connecting through SSH (using rsa_id keys and not a password) I was then starting VNC in an insecure method.

I should have continued to pass the command

ssh -L localhost:5901:localhost:5901 user@remote

to my vnc server from within my ssh shell effectively creating the required tunnel.

As I would like to just point out. I am now using FreeNX (which was very easy to set up, once I had the SSH working) or if I only need to view a few output lines and not do any 'it is easier using the GUI' stuff I would simply forward X for my ssh login (which again is very cool).

Also I mostly only use this from within my local 'home' network. Although I'm thinking of setting up port forwarding for my SSH so as I can log in from anywhere, but I don't require it yet so I'm not going to set it up.

Thanks again to the community for being so cool with 'relative newbs' - we are all newbs at something!

David

---

### Post by HermanAB on 2010-12-02
Howdy,

Once you got SSH working, you don't really need VNC.

Try this:
$ ssh -C -c blowfish -X user@server gnome-panel

VNC should not be lightly discarded.  It should be thrown, with great force.

---

### Post by CharlesA on 2010-12-02
> **HermanAB said:**
> Howdy,

Once you got SSH working, you don't really need VNC.

Try this:
$ ssh -C -c blowfish -X user@server gnome-panel

I've seen you mention that many, many times and it works really well. :)

I've been using FreeNX, myself, but that's cuz I like suspending the session instead of having to close everything.

---

### Post by bodhi.zazen on 2010-12-02
> **CharlesA said:**
> I've been using FreeNX, myself, but that's cuz I like suspending the session instead of having to close everything.

that is what screen is for =)

---

### Post by CharlesA on 2010-12-02
> **bodhi.zazen said:**
> that is what screen is for =)
Even the graphical apps that were forwarded over X?

I've used screen many times for CLI apps, but not for graphical apps.

---

### Post by bodhi.zazen on 2010-12-02
> **CharlesA said:**
> Even the graphical apps that were forwarded over X?

I've used screen many times for CLI apps, but not for graphical apps.

I am not sure about graphical apps to be honest. I do not ssh -X enough.

---

### Post by CharlesA on 2010-12-02
> **bodhi.zazen said:**
> I am not sure about graphical apps to be honest. I do not ssh -X enough.
Lisewise, I'm curious now, though.

---

### Post by theDaveTheRave on 2010-12-13
Hi all,

thanks for the input. But I'm not sure my original query has been answered in a way that I had expected...

Both Movieman and Bodhi seem to have answered my question, but then again.... I'm not sure.

Put simply, was my original method secure or not?

In a more complex way....
I have my laptop and my desktop.
I SSH from the laptop to the desktop.
In the terminal I start with a prompt of
```

davem@laptop:~$

```
after I've started the desktop (using wake on lan) I then SSH to the box, and I now have the following prompt
```

davem@desktop:~$

```

it is from this prompt that I now start the VNC server, or should start the tunnel with the command
```

ssh -L localhost:5901:localhost:5901 user@remote

```

so in my terminal I would now see...
```

davem@desktop:~$ ssh -L localhost:5901:localhost:5901 user@remote

```

or should I have been using this command from my laptop prompt...
ie..
```

davem@laptop:~$ ssh -L localhost:5901:localhost:5901 user@remote

```

sorry I'm just a bit confused, and want to better understand SSH and VNC

HOWEVER, I would once again like to point out that security is no longer a problem as I am connecting mostly from within the LAN, and I am using FreeNX or simply forwarding X over my ssh connection... so please don't jump up and down about security, that isn't the issue, comprehension is.

yes my name is.... er what is my name  :confused: Oops silly me its at the top of the page in bold.

David

---

### Post by CharlesA on 2010-12-13
The syntax for creating the ssh tunnel looks off, it should be something like this:

```
ssh -L 5901:remotehost:5900 user@host
```

As long as you are connecting via "localhost:5901" VNC will be tunnelled.

If you are just accessing it locally, I'd not bother with encryption.

---

### Post by theDaveTheRave on 2010-12-15
> If you are just accessing it locally, I'd not bother with encryption. 

True, but as I am connecting over a wifi link, I think that encryption is a better option, not that I expect anyone around here knows how to sniff wifi.... but I think it's better to get into good habits.

Also if I could connect via a dedicated ethernet port I would probably not be concerned. I always think along the lines of - if the connection is 'physical' and 'direct' security isn't going to be a problem. Otherwise, caution is probably best.

Thanks to everyone for the input.

David

---

### Post by CharlesA on 2010-12-15
> **theDaveTheRave said:**
> True, but as I am connecting over a wifi link, I think that encryption is a better option, not that I expect anyone around here knows how to sniff wifi.... but I think it's better to get into good habits.

Also if I could connect via a dedicated ethernet port I would probably not be concerned. I always think along the lines of - if the connection is 'physical' and 'direct' security isn't going to be a problem. Otherwise, caution is probably best.

Thanks to everyone for the input.

David

Is the wifi encrypted (using WPA or WPA2)? Is so, no one will be able to read your packets. WEP is a pathetic excuse for security.

---

### Post by kevdog on 2010-12-19
> **HermanAB said:**
> Howdy,

Once you got SSH working, you don't really need VNC.

Try this:
$ ssh -C -c blowfish -X user@server gnome-panel

VNC should not be lightly discarded.  It should be thrown, with great force.

I love tunneling over the X window system, but doesn't this crash for you a lot as it does me?  

And as a side comment, I'm most certain screen is only for command line and not GUI.

---

### Post by CharlesA on 2010-12-19
> **kevdog said:**
> I love tunneling over the X window system, but doesn't this crash for you a lot as it does me?  

And as a side comment, I'm most certain screen is only for command line and not GUI.
It crashes for me quite frequently, but it seems that it only crashed when doing certain things - like trying to go to "settings" in VirtualBox, where it'll close everything out with a "segmentation fault."

I'm not sure if it's due to my setup, VirtualBox being a pain, or if it's because I haven't used the right command when SSHing in, as I normally just use ssh -X user@host.

---

