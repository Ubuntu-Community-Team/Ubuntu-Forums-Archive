---
title: "No GUI on server or node"
date: 2010-10-15
forum: Ubuntu Cloud and Juju
---

### Post by ginga52 on 2010-10-15
Hello,
running two computer setup: 

1. 64 bit DELL Precision 470 running 10.10 UEC cluster controller (only thing setup on that computer, so UEC takes the entire setup)

2. 32 bit DELL latitude D430 running 10.10 UEC node (installed as a virtualbox guest on top of 32 bit Ubuntu desktop 10.10)

Both installed correctly from either a USB stick (1) and network image (2).

However when I reboot, I log in both and I am stuck at the command line not knowing how to invoke the web interface since I don't have any GUI available (Xwindows -- should I install Xstart from a package?) or may but there but I don't know how to invoke it. The instructions all seem to point to the fact the installer does everything for you and "all you need to do" is go into the web interface.

The node installed correctly and found the cluster controller with no issue. Both installed correctly and connected through Ethernet fine (even the one in virtual box).  Again though I don't know what to do from here in order to get the images / instances.  From the host OS on machine 2 (ubuntu desktop 10.10) when I start firefox and punch in the https address of the server, I can get into the interface no problem and retrieve the certs as well as changing the admin info so I know this works.  

Please help!  I am a noob in cloud computing and set this up at home so that when my kids ask me a question I won't sound too too dumb....

Cheers

---

### Post by marrusl on 2010-10-15
Hello,

No there won't be a GUI on the nodes.  I mean you *could* install ubuntu-desktop onto a node, but the expected mode of access is from a web browser running on another machine.  Which is what you did.

So, nope, that's the full GUI.  There should be a tab called "Store" where when you submit an empty search (just click the magnifying glass) will give you a list of some premade images.  Though long term, you'll want to learn how to import and register the latest official images from [http://uec-images.ubuntu.com/](http://uec-images.ubuntu.com/).

That will allow you to pull down an image and import it into the system.  However the actual starting, stopping, and creation of new images (among other things) all is done command-line from your workstation using the Euca2ools package.  Euca2ools is almost exactly like the ec2-api-tools you  use with Amazon EC2.  What's great about that is there is a lot of information on the web on EC2 which you can easily adapt to working with UEC/Eucalyptus.

Look through the install guides and additional resources here:
[https://help.ubuntu.com/community/UEC/](https://help.ubuntu.com/community/UEC/)

There's really only a couple of functions I ever find myself using the GUI for, it's really all CLI management.

What you can do to get going a little faster with a GUI interface is the Hybridfox add-on for Firefox which works with both EC2 and UEC.

One other note:  You need hardware virtualization support on the Node Controllers (like intel VT or amd svm support).  I'm not sure you'll be able to run that on Virtualbox.  Go to the console of your Node Controller and run the command "kvm-ok" to see if KVM virtualization is supported.  I've heard that you might be able to run a Node Controller virtually if you have an AMD, but I've never been able to try it myself.  If it does work it will be dog slow though.  If at all possible, put the NC on bare metal.

The other components (CLC,CC,Walrus,SC) can run on a virtual machine.

---

### Post by marrusl on 2010-10-15
Forgot to mention:

Wow!  You have some interesting kids.  I get credit  for being a computer genius from mine just for streaming movies to the playstation!  For some reason cloud talk doesn't seem to impress them.

:-D

---

### Post by Rusty au Lait on 2010-10-15
Good points marrusl.
I think jinga52, you should swap your computers. The CLC is only a manager and i/o. There is not much need for power there. Your machine 1 (64 bit DELL Precision) sounds more powerful than the other, though you have not described either machines more than that. If I am right, and the DELL has the musule, it should be used as an NC. the Nodes are the ones doing all the virtualization chores as well as the instances's cpu needs. You don't need a GUI on either the CLC or any NC. Keep your desktop on the machine it's on now, just switch the controllers.

It looks like you are ready to run an instance.
marrusl's excellent suggestion to get Hybridfox will make your life easy but as a noobe (like myself) I would suggest you start with the command line.

 My next action would be from the desktop open a command window and ssh into the virtual CLC and try something like:
~$ euca_describe_instances
If you get a list of something your in. Let us know what happened.

---

### Post by hex7 on 2010-11-10
funny how hard it is these days to have a text only console on your "desktop".

i just stumbled upon this thread trying to remove the startup / plymouth GUI that interferes with the test reporting of each process as it comes up.... just like solaris, bsds, most distros linux, hpux, etc..... at least there has typically been a way to deactivate gui easily (such as switching runlevel w/ redhat)..... but NOT ON UBUNTU 10.04. granted, i think it may be called desktop edition, but after reading thru diff posts from peepz here and elseware, people are not havin it.   is 10.10 a solution?  ill find out when its done downloading.  in fact, thats why im wasting time bs'ing here ;)

i guess im not the only one who likes console, ncurses, and lynx over firefox anyday.  remeber when it would be so hard to get X going? in my ideal world, X, if necessary, is something i would load modules and startup, on command (ie startx).... when im done with the X server, i turn it off. (such as for istance if i had to run vmware to look at XP for some god awful reason).... i mean y is X so important? is ~7TTYs not enough?

does any1 know an easier way to get rid of all GUI effects on 10.04 than to upgrading to 10.10 server?  im hoping there is no bs with plymoth on this "server" edition....  

 im aboout to serial in and spawn a getty.  that way i will finally have console.,,,,, then i have to change everything including BIOS to reditect or echo to that port? tooo much work. memories of console servers and db25 x 16 going to some crappy 2xxx cisco router.

ane1 happen to see the Plymoth (sic) dependencies list in package manager for this "I/O systemizer" or some crap? lmao..... alright 10.10 is almost done d/l now, hex7 signing off

---

### Post by marrusl on 2010-11-10
hex7, the simplest way to get what you are looking for is indeed Ubuntu Server Edition.  No GUI by default.  Promise.  But if you want to have the option of a GUI just not have it autostart, you are correct, you can't manage it by run level. Debian-based systems don't have the distinction between run levels 3 and 5.  It's really just 1 and 2.

But you can fix it pretty easily from within the desktop edition.  To stop GNOME from starting automatically edit the file /etc/init/gdm.conf.

Find the section (near the top) that reads:

start on (filesystem
               and started dbus
               and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
                        or stopped udevtrigger))
stop on runlevel [016]

And then add another condition that won't be met, for example (note: watch the parentheses):

start on (filesystem
               and started dbus
               and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
                        or stopped udevtrigger)
     and runlevel [5])
stop on runlevel [016]

Then when you want to fire up X, run:

$ sudo start gdm

and to exit X for the session, run:

$ sudo stop gdm


Kind of off-topic I guess, but since you asked.  ;-)

---

