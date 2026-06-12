---
title: "LTSP Fat client not loading GDM"
date: 2009-02-19
forum: Server Platforms
---

### Post by Azdour on 2009-02-19
Hi all,

I've been asked to look at Server - Fat Client setup in Ubuntu 8.04. I've installed and setup LTSP, DHCP and NFS.

I'm using the nubae fat client plugin script to build a chroot fati386.

I had to modify the fat client script to change the mediubutu repository from intrepid to hardy. 

I also remove realplayer, mplayer, mozilla_mplayer, acroread and mozilla_acroread. This was because they could not be found in any of the repositories and made the creation of the chroot fati386 fall over and not complete. 

Once these changes were made the fat client script worked.

At first the fat client booted over the Network, and started to load Ubuntu, but it would always halt on Start Gnome Display Manager. The [OK] status would never appear and it would just sit there doing nothing.

On the Ubuntu LTSP wiki I found reference to a 'hack' if the gdm did not start correctly - a startgdm.sh that would called /etc/init.d/gdm restart' followed by '/usr/sbin/gdm'. The startgdm was then added to the lts.conf.

Now when the client boots, the GDM seems to be loading and falls over. I see the normal ubuntu login background color, and the busy cursor appears.

The screen then disappears and I'm back at a screen with a '_' character in the top left corner.

If I hit Ctrl+Alt+F7 it switches to the gdm screen, which is either sitting there with the busy cursor forever or when I start to enter the username no characters appear and the caret disappears and it seems to freeze (although I can still move the mouse).

I'm trying to figure out why the gdm is not starting and why I have to hit Ctrl+AltF7 to switch to the login screen. I was hoping the screen would have been shown automatically - especially if I'm to use this in a larger network.

Are there any logs I can look at?

I've checked the DHCP server with a normal Ubuntu client (not booting over the network) and it's running fine. I've also checked that NFS is working by mounting the /home of the server on a test client, and that works fine.

In the nfsmount.sh I did see the line:

mount -t nfs :/home /home

Which I changed to:

mount -t nfs 192.168.1.2:/home /home

So its uses the actually server IP.

Any help or pointers would be greatly appreciated.

---

### Post by Azdour on 2009-02-19
Follow-up:

When the fat client boots, after pressing Ctrl+Alt+F7 I see the gdm login screen waiting for the username to be entered.

The mouse works, but the keyboard does not (its a standard ps/2). I'm still not sure that gdm is starting correctly - because I do not automatically see the login screen.

I've also noticed the following error displayed in Ctrl+Alt+F5:

mkdir: cannot create directory '/var/run/drives' : File exists

---

