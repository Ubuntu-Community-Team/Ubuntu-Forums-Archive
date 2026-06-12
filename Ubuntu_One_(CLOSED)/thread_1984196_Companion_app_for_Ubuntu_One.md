---
title: "Companion app for Ubuntu One"
date: 2012-05-21
forum: Ubuntu One (CLOSED)
---

### Post by thnewguy on 2012-05-21
Hi all,

I've been working on a companion app for Ubuntu One. I like the way One works and find it really handy, but it doesn't appear to have the ability to sync files directly between peers. So, for example, let's say I have Ubuntu One running on my laptop, syncing files to the Ubuntu servers. That's good, but I also want to sync those files to a local server, or to my desktop. Plus, maybe I want to share just one folder with a friend.

My app, called Fish, allows users to sync multiple folders between multiple machines. It has a graphical front-end for desktop boxes and a command-line only version for servers and other headless machines. It allows users to sync specific folders to specific computers. The only requirement is each computer we sync to must have an OpenSSH server running.

The app is still in its early stages and I'm hoping to get some feedback. Please check it out and let me know what you think. Fish can be downloaded from [http://fishsync.sourceforge.net/](http://fishsync.sourceforge.net/)

---

### Post by nll on 2012-05-23
Nice idea! Good luck there!

---

### Post by Dragonbite on 2012-05-24
Is this anything like Dropbox's Sync-over-LAN?

With SoL, when a file is updated and sent to the Cloud storage area, the online service will recognize that there are multiple people associated with that account, on the same LAN. It then tells the computers to get the updated file(s) from the other computer instead of downloading it from the web.

Does that make sense?

So for example, my laptop and desktop are on and both are set to synch with my dropbox account.  I add a file with my laptop which is then uploaded to dropbox in the cloud.  That dropbox, when it is done receiving the file, updates the desktop to say there is a new file.

Ordinarily the desktop would then download this new file from the cloud service but instead it knows (somehow) that the file is on the laptop, whether dropbox cloud service tells it, or otherwise, and the desktop begins to pull the file from the laptop instead of the internet.

This has been a lifesaver function as every time I try a new distro, or run a clean upgrade, I have to re-download all of the files in my dropbox account which over my slow internet connection would take an estimated 2-3+ hours.  With Sync-over-LAN it is done in approximately 30 minutes and my wife's computer can continue to surf the internet unabated.

This is a killer feature for me as nobody else provides this capability and 2-3 hours is only for about a gig-and-a-half!  If this moves upwards (my SkyDrive has 5 gb and can go up to 25!) it makes it unbearable.  It takes me 15 hours to download a 4 gb DVD if that gives you any reference.

---

### Post by thnewguy on 2012-05-24
There is a similarity between this application and Dropbox's sync over LAN feature. However, there are a few key differences.

1. Fish does not connect to a central location to coordinate syncing files. Configuration of which folders/files to sync is handled locally.

2. Only one computer in the group needs to have Fish installed. Each computer _can_ have Fish installed, but only one computer in the group needs to have it. All other computers only need OpenSSH installed, which means Fish can sync to a variety of platforms, including phones that can run OpenSSH servers.

3. Fish isn't restricted to a LAN, it can sync to any computer on the Internet, as long as you know its address and the remote machine has OpenSSH installed.

4. Fish uses all open source components, meaning you can examine it and modify it if you wish. Dropbox, so far as I know, is closed-source.

---

