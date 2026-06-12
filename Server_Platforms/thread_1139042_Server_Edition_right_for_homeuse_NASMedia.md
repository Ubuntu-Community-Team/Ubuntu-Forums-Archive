---
title: "Server Edition right for homeuse NAS/Media?"
date: 2009-04-26
forum: Server Platforms
---

### Post by Ellipsys on 2009-04-26
Hello all. I've never worked with Server Edition before, but I was wondering if it would be useful for the new PC I just built. It needs to do the following things...

1. Primary function as network attached storage. It needs to be able to serve files to both windows and linux PCs on a small home network, such as ISOs, video files etc...
2. Media streaming would be nice
3. The ability to run occasional server programs such as those for TeamSpeak/Ventrilo, dedicated servers for video games, BitTorrent  etc..
4. The idea thing would spawn an easy to use web interfaces for the administration of various tasks, so I'm sure there will be additional programs needed to do this.  (Think OpenFiler + torrent webUI etc..) 

Do you think that Ubuntu Server 9.04 x64 would be right for a build like this? Thanks

---

### Post by ByteJuggler on 2009-04-26
In short, yes.  If you plan on using it as a terminal server (GUI desktop running on server) as well, then you might install the desktop edition anyway as you'll need the GUI stuff to be installed then.   (It is not generally the done thing for Linux/Unix servers to have a GUI, but since this is a *home* server I reckon it might be a good idea.  So to reiterate: The server version does not have a GUI so you'd have to manually install that if you wanted it on the server edition, and the only real difference between the server and desktop editions are the sets of packages installed by default, includign of course, the GUI. So you might as well install the desktop edition and add the server packages you want. )

---

### Post by TuckLive on 2009-04-27
I use the Server Edition for most of the things you described.  For serving media I use Subsonic, which is web-based, and for the various tasks like you described I use Webmin, which is also web-based.  I'm extremely happy with the setup I have.

---

### Post by Ellipsys on 2009-04-27
Thanks guys. Could anyone point me towards the packages I'd need for the things I described below?  I may just go with the desktop version, considering I'm a newbie, but I wouldn't object to tutorials on getting the Server Version tools ready either.  For instance, what is the fastest way to share media on a LAN? I hear something about Samba and NFS being necessary, right? 

Thanks again!

---

### Post by Jive Turkey on 2009-04-27
I don't recommend NFS even for a pure linux environment, while it is super easy to configure, it seems windows only pretends to support it.  I use openssh-server which gives me terminal access to the box when I want it.  I use webmin for the stuff that might help me to have a gui.  The package "swat" also gives a very nice way to configure samba via browser interface.  

On the client side i like to use sshfs to mount the share I want in linux, and in windows I mount the samba shares via the "mount network drive" feature.  You can use the program PuTTY fro terminal based control of the server from windows too.  I like to remove swat and webmin after I get things set up how I want due to paranoia.  A problem with swat that I have is that I havent been able to get it to work without doing "sudo passwd root"  as when I log in as a user it doesn't show all of the options I need.  I also like to set samba to be a WINS server to make things easier.  

I dont know much about streaming media, I just mount the shares on the client.

If you google "howto <packagename> ubuntu" the fist couple hits should have pretty good tutorials.

---

