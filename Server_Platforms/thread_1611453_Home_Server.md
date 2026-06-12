---
title: "Home Server"
date: 2010-11-01
forum: Server Platforms
---

### Post by starbase527 on 2010-11-01
Hi,

I'm a bit of a newbie when it comes to servers etc., but I've been wondering about setting up a home server using Ubuntu server.

Mainly I'm not sure about what services this can provide us with, but would definitely like to have network logon, or something with similar effect.

Our Hardware:
iMac
MacBook x2
Time Capsule
Canon MP990 Wireless Printer
2.8 GHz PC running Ubuntu Desktop @ the moment

All the Macs are running Mac OS X Snow Leopard

I don't mind about not having windows integration for anything other than basic internet supply. I have windows XP on the iMac using Bootcamp, but don't use it much at all

Thanks for any advice on what I can/should do

---

### Post by arrrghhh on 2010-11-01
What are you looking to achieve?  Shared files?  Web server?  UPNP media streaming...?

Not sure what you mean by network login... like LDAP authentication?  That's doable, but by no means easy on Ubuntu.  Other distros have better LDAP integration, IMHO.

Also if you're looking to setup a PDC, I don't think samba4 is quite ready yet by any means... it's still alpha.

---

### Post by starbase527 on 2010-11-01
The services that I want:
 &#8226; iTunes library access on any computer
 &#8226; iPhoto Library access on any computer
 &#8226; Web Server on the home network
 &#8226; Printing from any computer wirelessly
 &#8226; Time Machine backups on the Time Capsule
 &#8226; Home folder contents and preferences to be either synced or accessible on all of the computers

I'm not sure what LDAP or PDC is, but I was thinking maybe I could use NFS mounts on startup with symbolic links to the network home folders in the computer's home folders

Also, I'd rather not spend any more money on computers. The PC has 1GB RAM, it should be fine for the server shouldn't it?

Thanks

---

### Post by kenada on 2010-11-02
Printing, Home folders and the iPhoto side should be easy enough with Samba.
You can store your iTunes library with Samba too, but syncing between clients can become an issue.

Did you want to add Time Machine functionality to the server? Doable ( [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/) ) but If you have a dedicated device for that already then why change it? 

Web server, that's quite doable with LAMP or just Apache depending on what content you intend to serve.

---

### Post by starbase527 on 2010-11-02
I thought Samba was designed to file share with windows.

Isn't there a better way to use Mac/Linux file sharing?

---

### Post by arrrghhh on 2010-11-02
I believe macs work with NFS, which would be better to use over samba - I only use that for my windows machines.

There's some threads on timemachine or time capsule whatever the heck it's called - search for those.

For iTunes library sharing by far the best way to do that is [FireFly](http://www.fireflymediaserver.org/) (IMHO).

[quote=starbase527]&#8226; Home folder contents and preferences to be either synced or accessible on all of the computers[/quote]

Not sure what you mean by this.  You can share whatever is on the server, but I'm not sure how you're going to get all the clients synced, unless maybe you set something up on the client PCs to sync their data when connected... I'll probably need more info on what you want here.

With that said, you should be fine with 1gb of RAM.  None of the things you describe are very CPU or RAM intensive.

For printing, I think CUPS would be better for you, but you may also want to look at how samba shares printers.  CUPS allow you to use IP printing, which I prefer.

---

### Post by Boondoklife on 2010-11-02
One more point of view for ya:

Printer:
As far as printing, if your printer is a network ready printer (HP C4795 for example) all you have to do is connect it to your router and all the devices can print from it. You will need to map it in each computer but that is all that should be needed.

iTunes/Music:
As far as itunes, you can try out firefly and the other daap services but once you get to a large library size it can take a while to get the list shown on the computer. I have ~20k and it takes a good 3-4 minutes before I can even select a song to play as it has to send the list first (The server is a bit resource strapped but just a fyi). I personally have found it more effective to just share the folder and let the media application of your choice cache up the file list. This way there is no waiting needed, just access to the network drive.

File Sharing:
I personally think you should just go with samba if you have windows boxes or will have windows boxes. The reasoning behind this it is much easier to control just one service. If you have NFS and Samba you will need to be very careful that the settings and rights match or you could end up with a headache.

Roaming home folders:
Really this is just a bad idea, a better idea would be to have personal folders inside which each user stores his/her data. this way you can mount it regardless of the os and know where on the computer to find it. As far as the preferences, this is just a disaster waiting to happen. If you are really hard up about making sure your desktop is exactly the same on each box then maybe you should be looking into thin clients and running everything on a main server.

Network logins:
You can set this up with samba and winbind, this is where that PDC thinking comes into play. I really don't see a big point for this in your case, especially with a laptop in there. If you disable local logins you would not be able to get into your laptop without being at home. I think a better idea would be to have a reasonable password update routine. Write your self a memo every 3 months to change your passwords and do it on each box all at once.

IPhoto:
Now I have seen services out there that off this, but I dont know if they will have the same issue I mentioned with daap. If so then you prolly just need to share this via a shared folder from the server.

Remote Access:
If you need to access your files while you are out, you may want to look into setting up a VPN. This will allow you to login to your network from where ever and get your just by mounting a network share like you normally would.

Time Capsule:
Don't have much experience here but if you have one why replace it? If you want another option, you could install a tftp server and have it serve up a clonezilla image. This will allow you to make images of your computers and store then in another place (another partition, DVD, network, etc). You can also use the image to restore the images too.

---

### Post by BobVila on 2010-11-02
The time machine backups will require some command-fu on the mac side. It's doable, but is really icky, in my experience. I spent a few hours getting over through the process, but wouldn't recommend it if you've already got a time capsule. It also seems to change with the Mac OS releases, so keeping up with a hackjob backup could be irritating. Might be worth looking into other options there.

---

