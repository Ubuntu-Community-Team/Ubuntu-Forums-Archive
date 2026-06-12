---
title: "shutting down vmware player from command line"
date: 2010-01-19
forum: Virtualisation
---

### Post by davidmohammed on 2010-01-19
I particularly like Unity in vmware player 3 and would like to use vmware player to run as seamless as possible with my Karmic install.  VirtualBox seamless mode isnt seamless enough forcing you to have yet another taskbar hovering above the karmic taskbar.

Its straightforward to start my guest os when I login to karmic.  However, I cant figure out a clean way to shutdown vmware player when I logout/shutdown the PC.  

Ideally I would like to invoke the "suspend" option in vmware player without actually having to go through the keystrokes to open the vmware player unity window and clicking the suspend button.

Anybody have any ideas on this?

---

### Post by davidmohammed on 2010-01-20
...

OK I have now figured out how to suspend a vmware player session - install the vmware vix-api.  This gives you a new command line tool vmrun which allows you to control the guest

i.e. 
vmrun -T player suspend <vmx file name>

Any ideas - anyone - how in linux I would invoke such a command automatically whenever you either logout of the ubuntu desktop or if you invoke a shutdown/restart?

---

### Post by AlexanderDGreat on 2011-05-17
Any updates on this?

I find it shocking there's very few documentation on how to simply shutdown a guest in VMware Player!!!

Any ideas?

---

### Post by davidmohammed on 2011-05-17
... I havent found one ... still interested though. I'm still using a desktop launcher to shutdown the vmguest and then invoking a shutdown.

---

### Post by AlexanderDGreat on 2011-05-18
I still use Window's XP Scheduled Task Manager... :(

Please anybody out there?

---

### Post by AlexanderDGreat on 2011-06-03
Please... Anyone?

---

### Post by AlexanderDGreat on 2011-07-07
Hi davidmohammed

I followed your idea of installing VIX-API to suspend a guest, that way, it's far safer than a COLD TURN off.

My situation is this, I have a server in the office and I would like to shut it down from my house because sometimes I don't go to the office and people often leaver early when it's not busy.

I'm the only one who knows the password to the server because it's got confidential emails and files.

So I installed a SSH remotely, but we still use Windows XP to host a Database for our computers, that's why the VMware Player Windows XP.

So I want to safely shut it down remotely.

You said

> I'm still using a desktop launcher to shutdown the vmguest and then invoking a shutdown.

Can you tell me what is a desktop launcher? And how I could use it as well?

Thanks!

---

### Post by davidmohammed on 2011-07-07
Just right click on the desktop and choose "Create Launcher".

In the command field enter your VIX API call - in my case its the "vmrun ..." I said above.

As I said - double clicking the desktop launcher icon runs the "vmrun ..." command to suspend the VM.

For SSH - I presume you are just SSH'ing to your server and login as yourself.  Therefore you can just type "vmrun ..." to suspend your VM.

---

