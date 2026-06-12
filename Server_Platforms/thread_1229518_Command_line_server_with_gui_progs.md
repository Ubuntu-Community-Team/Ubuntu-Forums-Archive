---
title: "Command line server with gui progs?"
date: 2009-08-02
forum: Server Platforms
---

### Post by Markstar on 2009-08-02
Hi,
even though I'm still pretty new at Ubuntu, I'm trying to slowly replace my Win2k server (WAMP + torrent + eMule + shared directories). So far users connect via VNC to take control of the Windows GUI.

I have got the Ubuntu server installed (as a VM for now), together with AMP, but since this is command line only, I was wondering if I can have the Ubuntu server without X, but have the clients use a GUI for torrents and donkey-related stuff? If so, which programs do you recommend for this?

Or should I just install a normal Ubuntu version with all the services and programs there?

Thank you in advance for your advice!

---

### Post by slakkie on 2009-08-02
You can install the apps on your server, and then let your clients connect via ssh with X-forwarding, like done in this screenshot: [http://www.euronet.nl/users/wesleys/dig/X-for-ward.png](http://www.euronet.nl/users/wesleys/dig/X-for-ward.png)

---

### Post by Markstar on 2009-08-02
@slakkie: Thank you for your reply! I have googled for X forwarding and managed to run aMule from my other computer. :)

Alright, this might sound stupid but I have some questions about this:
If I log in to the server and start aMule (for example), an instance of aMule will open on the server, but the window opens on my local screen. When I quit aMule, the application quits as well (which does make sense)...

1) ...but how do I set it up so aMule always runs on the server and the users just access the GUI?
2) What if I have more than one user? How do I make it so all access the same aMule (and not one instance per user)?

---

### Post by Markstar on 2009-08-03
I just realized there is obviously another problem with the solution from above:
The clients have to be running their computer as well while the program is running. 

How do I make it that programs are running 24/7 on the server with only the command line, while the users can access the programs via a GUI? Is that even possible or do I need to install X11 on the server and then use VNC? 

I would really appreciate any help on this!

---

