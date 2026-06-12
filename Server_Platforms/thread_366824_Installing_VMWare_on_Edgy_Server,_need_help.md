---
title: "Installing VMWare on Edgy Server, need help"
date: 2007-02-21
forum: Server Platforms
---

### Post by caffienda on 2007-02-21
I think this should be a pretty simple question.  I have installed Ubuntu Server 6.10 and want to install VMWare server on top.  Since 6.10 doesn't use a GUI, is this still possible?  Will VMWare have a GUI?  

Here is what I want to do.  I want to run this box that I have set up as a file server, but would also like to be able to run a couple VM's off it as well.  

I am pretty new to Linux and am wondering if I am biting off a little more than I should with a bare server install.  Would it be a better idea to run something with a GUI?

Finally, this is a very novice question, but I really don't know.  Are there programs that use GUI's that run on Server 6.10?  Can you run programs like Firefox if you needed to?  Also, if there is a program loaded on the server, like GIMP, can someone connect across the network and run it off the server?

I know there are a lot of questions here, but I need to figure out which version is best suited for my needs before I waste any more time.  Thanks.

---

### Post by veloce on 2007-02-21
> **caffienda said:**
> I think this should be a pretty simple question.  I have installed Ubuntu Server 6.10 and want to install VMWare server on top.  Since 6.10 doesn't use a GUI, is this still possible?  Will VMWare have a GUI?  

Here is what I want to do.  I want to run this box that I have set up as a file server, but would also like to be able to run a couple VM's off it as well.  

I am pretty new to Linux and am wondering if I am biting off a little more than I should with a bare server install.  Would it be a better idea to run something with a GUI?

Finally, this is a very novice question, but I really don't know.  Are there programs that use GUI's that run on Server 6.10?  Can you run programs like Firefox if you needed to?  Also, if there is a program loaded on the server, like GIMP, can someone connect across the network and run it off the server?

I know there are a lot of questions here, but I need to figure out which version is best suited for my needs before I waste any more time.  Thanks.

Not quite sure what you are meaning when you ask about running the vms.  

You can install vmware-server on your server box - which you do at the command line so don't need a gui.

To access and run your vms you need the gui vmserver interface.  This can be installed on a different box  that logs onto the server box.  you can then run your vms across your network.  The processing is done on the server and the gui displayed on the client.

---

### Post by evilspoons on 2007-02-22
If you want a GUI on the server to do administration and configuration and stuff without having to wrap your head around the command line, you can do:
sudo aptitude install gnome-core gdm xorg

This gave me a no-frills Gnome install that I could work from more comfortably on my server - I hate moving files around from the command prompt, and copy and paste is always handy :)

---

### Post by caffienda on 2007-02-22
Thank you for both of those responses, that is what I was looking for.  

Veloce:  by VM's I did mean Virtual Machines.  I should have stated that.  I guess I'm just so used to that abbreviation.

Evilspoons: Thanks for the GUI tip.  I was starting to really hate the CLI of the server.

---

### Post by veloce on 2007-02-22
> **caffienda said:**
> Thank you for both of those responses, that is what I was looking for.  

Veloce:  by VM's I did mean Virtual Machines.  I should have stated that.  I guess I'm just so used to that abbreviation.

Evilspoons: Thanks for the GUI tip.  I was starting to really hate the CLI of the server.

Sorry for the confusion, it wasn't the abbreviation I was unsure of but which part of the system you wanted to "run" on the server (the vm runs on the server, but the gui can be on the local machine.)

On another forum, I saw that you can use a another machine on the network to run an X session on the server.  Something like ssh -X to logon to the server then you can get a gui interface running locally as if it were the server.  

Using all these tools you could put the server in a cupboard with no screen attached but still use the server's processing power with a gui interface.

---

### Post by caffienda on 2007-02-22
> **veloce said:**
> Sorry for the confusion, it wasn't the abbreviation I was unsure of but which part of the system you wanted to "run" on the server (the vm runs on the server, but the gui can be on the local machine.)

On another forum, I saw that you can use a another machine on the network to run an X session on the server.  Something like ssh -X to logon to the server then you can get a gui interface running locally as if it were the server.  

Using all these tools you could put the server in a cupboard with no screen attached but still use the server's processing power with a gui interface.

That sound great!  I have 2 P3 1Ghz Dell's sitting around that I don't know what to do with.  I think  they could be used for something productive..  Test servers at least.  

Is the default GUI in Ubuntu X or Gnome, and how do you tell what which version is running?  
I just installed KDE and  "gnome-core gdm xorg"   now I need to figure out how to run that on boot.

So the ssh -X means to remote connect using the X GUI Remote desktop client?

---

### Post by veloce on 2007-02-22
Gnome and KDE are a layer above X so I assume that whichever is the local default will run.  I haven't tried and tested this so not sure how it would work.

---

### Post by caffienda on 2007-02-22
I installed KDE but I don't know how to get it to run on 6.10 server.  Once it is installed, how do you get the GUI to come up?

---

### Post by kvonb on 2007-02-22
If you don't want to start x on every boot, you should be able to type:

startx

at the prompt, and it will run as the currently logged in user.

There are proper ways of starting X on each boot using gdm or kdm, but a quick/hack way is to put the startx command just before "exit 0" in /etc/rc.local, then make sure rc.local is executable like this:

```
sudo vi /etc/rc.local
```

add startx near end of file, just before "exit 0",

```
sudo chmod +x /etc/rc.local
```

In theory it should start X on every boot :).

---

### Post by caffienda on 2007-02-23
> **kvonb said:**
> If you don't want to start x on every boot, you should be able to type:

startx

at the prompt, and it will run as the currently logged in user.

There are proper ways of starting X on each boot using gdm or kdm, but a quick/hack way is to put the startx command just before "exit 0" in /etc/rc.local, then make sure rc.local is executable like this:

```
sudo vi /etc/rc.local
```

add startx near end of file, just before "exit 0",

```
sudo chmod +x /etc/rc.local
```

In theory it should start X on every boot :).

Ok, that's for X, but what about KDE?  Sorry, I've never had to load a GUI and have never even experimented with the different ones!

---

