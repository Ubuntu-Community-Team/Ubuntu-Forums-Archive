---
title: "Help? Linux alternative to WHS/media server"
date: 2011-01-03
forum: Server Platforms
---

### Post by backlash666 on 2011-01-03
Hi

I have used Linux on and off for the last 2 years so I have a general understanding.

I currently have a server running Windows Home Server and was wanting to know if Ubuntu Server could do the following requirements I currently enjoy

1. Media Streaming, to multiple devices simultaniously i.e. pc/xbob360/PS3 all at the same time. Possibly re-encoding OTF.

2. Remote Access, not just to the server but linking(so i can rdp to my main rig through the server from any internet location) to other systems on the "Home" Network both Linux and Windows.

3. Drive Pooling with redundancy, I want to be able to add and remove HDD and just have it expand the pool so current folders can just grow, but also have it duplicate or make redundant copies so if a HDD fails it can still be recovered.

4. Backup of machines on the network, either manual or scheduled, of both Linux and Windows machines

5. App sharing would be a plus but not required, so I could run a Linux app from the server seamlessly on my windows pc.

6. Basic file storage and browsable structure from windows machines.

I realise this may be a tall order and I don't expect it to be easy or straight forward in any way, but I really hate WHS, it has the slowest file access speed of any os i have ever seen, and is so buggy its unbelievable.

I have all the hardware I need now all I need is the knowhow.

If anyone can help I would really appreciate it.

Thanks

---

### Post by backlash666 on 2011-01-04
have found Twonky media server may do the streaming job but am still at a loss to the others.

any help would be appreciated.

Thanks

---

### Post by Boondoklife on 2011-01-04
For the remote access, VNC connections should work just fine, though you may want a gui installed to make this easier for ya.

Drive pooling, you might wanna read up on LVM and RAID

For machine backups, check out clonezilla. Optionally you could also get a tftp server running so you can boot a clonezilla image and restore/backup images across the network using pxe.

app sharing, again sounds like VNC would fit the bill. You would not be running the apps on the local computer but instaed in the remote desktop instance on the server.

Network file sharing can be handled by Samba.

---

### Post by backlash666 on 2011-01-04
thanks Boon

LVM seems a little awkward to set up for me, does it install with wizards or am I really gunna have to do my homework?

not sure which version of desktop I should install am used to gnome if that is an option.

Do you know of a way to pass VNC through to other machines so if I'm in another country and i connect to my server it lists the other machines on the network and lets me connect?

I think I'm asking a lot here but I hope Linux can do these things so I can say bye to windows.

Thanks

---

### Post by Boondoklife on 2011-01-04
Yea, anytime you are playing with LVM or RAID, you want to do your homework (Unless you have time to waste and don't value the data your placing on it ;)).

As for the GUI, GNOME is fine and I use it the most.

For the VNC, if you can VNC into your server, then you would just need to VNC from there to what ever box on your network you like. This is not EXACTLY what you are describing, but will have the same result.

Linux can definitely do everything you are wanting to do, but there may not be wizards and what not to do it. You will prolly have to roll up your sleeves and get into it.

---

### Post by backlash666 on 2011-01-04
sounds like a plan. Thanks mate

any other sugestions and any HOW-TO's would be grately appreciated.

Thanks

---

### Post by lykwydchykyn on 2011-01-04
A few suggestions:

 - For remote access, you may want to look at [ nxserver](http://www.nomachine.com).  It runs over ssh and performs much better than VNC over slow links (like the Internet).

 - You may want to look into [Zentyal](http://www.zentyal.com) (formerly ebox), which is basically a nice web interface for a lot of common services.  It runs on Ubuntu server, and can actually be installed over an existing Ubuntu install.  It may take the pain out of a lot of the configuration.

 - Another popular web-based administration option is [webmin](http://www.webmin.com).  I'm a webmin user myself, but I don't know that it really makes things much easier conceptually most of the time.

---

### Post by egpetrich on 2011-01-04
For remote access, I use SSH and tunnels. My Linux box accepts SSH connections (which is, I believe, the default). I have my home router set up to forward SSH to the Linux machine, but I leave other ports on the router closed.

I could use a dynamic DNS service to provide a domain name for outside access, but I haven't needed it. My IP address isn't static, but it has historically lasted for months without changing. Just in case, I keep track of changes using some CGI scripts on my ISP home page and a cron job on the Linux box. That way I can determine my home's current IP address. (Yep, this is a bit clunky, but I viewed it as an Exercise for the Student. Plus, I don't have to keep track of another account to handle dynamic DNS.)

To connect, I use PuTTY from Windows machines. The PuTTY documentation walks you through the process of creating an authentication key pair. PuTTY comes with a key manager called Pageant, which uses your authentication key to allow SSH connections without a password. (Well, you have to enter a passphrase when you start Pageant, but that's one time per Windows boot. Put it in your Startup folder, and you don't even have to remember to start the program.)

PuTTY gives you SSH, and it also lets you set up SSH tunnels. Again, a bit clunky, but once you have them configured they are established whenever you log in. For example, the Windows desktop is running VNC server as desktop 0 (the default). Create a tunnel from local port 5900 to desktop:5900, and you can connect from your remote machine's VNC client by connecting to localhost:0.

I've had good results with this method. Performance is limited by your uplink speed, but it's sufficient for occasional use. You may have to leave your home machine running, though, so we don't do that very often. (Built my own system, but forgot to check that the motherboard had wake-on-LAN! Won't make that mistake again....)

Oh, yes, this does mean that your Linux machine may have to be left running any time you want to have outside access. I haven't found a way to wake a system remotely. (Wake-on-LAN is for the local network only. There are some other threads on this forum that discuss it in more detail.) I use a relatively low-powered mini-ITX system and just leave it on 24/7 (about 40W idle).

You may have inferred that I'm a bit paranoid about security. I will note that I have seen a **lot** of failed login attempts in my system logs. So far, I don't believe that anyone has succeeded in getting in, but that's a strong reason why I don't forward anything but SSH on a permanent basis.

---

### Post by Girya on 2011-01-04
> **backlash666 said:**
> thanks Boon

LVM seems a little awkward to set up for me, does it install with wizards or am I really gunna have to do my homework?

not sure which version of desktop I should install am used to gnome if that is an option.

Do you know of a way to pass VNC through to other machines so if I'm in another country and i connect to my server it lists the other machines on the network and lets me connect?

I think I'm asking a lot here but I hope Linux can do these things so I can say bye to windows.

Thanks

LVM is the default install for 10.10 server you just accept the defaults when you install. 

installing new disks into the volume group is easy. 

you might want to experiment with server configs on virtualbox 

for backups I've had good luck with backuppc

---

### Post by jarek.k on 2011-01-05
for remote access i can recommend nxserver. it's got clients for both linux and windows.
you can access via ssh/ tunneling as egpetrich described (I've almost identical setting as he has and it works great).

for streaming to xbox360 I recently installed uShare.
I've only tried to stream music to xbox so far, but it's easy to install and configure. Not sure how it will work with PC movies etc. but worth to have a quick look.

---

### Post by vidtek on 2011-01-08
> **backlash666 said:**
> Hi

I have used Linux on and off for the last 2 years so I have a general understanding.

I currently have a server running Windows Home Server and was wanting to know if Ubuntu Server could do the following requirements I currently enjoy

1. Media Streaming, to multiple devices simultaniously i.e. pc/xbob360/PS3 all at the same time. Possibly re-encoding OTF.

2. Remote Access, not just to the server but linking(so i can rdp to my main rig through the server from any internet location) to other systems on the "Home" Network both Linux and Windows.

3. Drive Pooling with redundancy, I want to be able to add and remove HDD and just have it expand the pool so current folders can just grow, but also have it duplicate or make redundant copies so if a HDD fails it can still be recovered.

4. Backup of machines on the network, either manual or scheduled, of both Linux and Windows machines

5. App sharing would be a plus but not required, so I could run a Linux app from the server seamlessly on my windows pc.

6. Basic file storage and browsable structure from windows machines.

I realise this may be a tall order and I don't expect it to be easy or straight forward in any way, but I really hate WHS, it has the slowest file access speed of any os i have ever seen, and is so buggy its unbelievable.

I have all the hardware I need now all I need is the knowhow.

If anyone can help I would really appreciate it.

Thanks

I've been playing with linux on and off since about 2003, got serious about it last year when I installed MythBuntu on and oldish amd box.  Mythbuntu makes setting up the HTPC server very simple, believe me I've tried them all.
I now use Mythbuntu ver 23 with a kDE4 interface so it's easy to play with, and my main machine with meerkat 10.10 and kubuntu running 23 mythtv.

It works beautifully.

I have a Fusion single channel pci tv card and compro usb stick on the old amd box and 
Hauppauge 2200 PCIe tv card in the main box (i7 6gb ram nvidia 250)

Mythweb enables me to remotely schedule my system from my HTC Desire  mobile phone or from my work computer at any time.

Mythbuntu is the best thing since slice bread and I've now totally dumped Windows 7 as my HTPC.

The only thing I now use windows for is to control my swimming pool chlorinating software using virtualbox and w7 over bluetooth.

It can all be done, but it is not for the faint-hearted or newly-married.

of your listed requirements I have achieved 1 through to 5--- I no longer need 6---yay!!

Best of luck to you, Tony.

---

### Post by slooksterpsv on 2011-01-09
#6 - Setup as a Samba, and setup a designated location to share your files from.

A lot of the configuration may need to be done in the terminal (Command-Line Interface), but its hard to really use a tool to do it for you once you do Terminal.

system-config-samba is a gui tool you can use to configure samba shares


I ran a server using Ubuntu for a year or two, till I moved and had to switch ISPs, and let me say, I used Gnump3d to stream my music; it worked on my PSP, Phone (blackberry), computers, etc. And my upload was only 512Kb/s - So if you can access it via the web, you should be able to stream it.

---

### Post by Offoffoff on 2011-01-17
Use mythbuntu! It works as you want.

---

### Post by SeijiSensei on 2011-01-17
You might benefit from browsing this [forum on Linux HTPCs]("http://www.avsforum.com/avs-vb/forumdisplay.php?f=76") at [www.avsforum.com](www.avsforum.com).

---

### Post by ContagiousIdea on 2011-01-17
Just did this, if you click my user and find other posts you'll see a great rubylaser tut for the raid5. Don't worry about an LVM he's right it's a heck of a lot more to go wrong.

If you have advanced format drives (EARS) then the formatting is slightly different but I can walk you through that.

Install SSH if you like CLI if you'd prefer a gui then use PinguyOS (properly working flash and most other things out of the box excellent ubuntu distro) Once you have a gui use teamviewer, yes I know it runs in wine but it's extremely fast and you can login with the teamviewer client or from their website and it's all free for personal use. Works really well


Setup samba shares for other PC's and use uShare or Twonky for streaming DLNA.

Network backups either use a cloner like what the others have mentioned or do an opensource dropbox with syncing. Eventually this will support 'versions' as well. I'm going to do this sometime this week so I'll get back to ya on that part.

As far as an RTSP streaming server over the internet that part is the extremely difficult part, I've been working on it for weeks and still no solution. I was going to go VAIL but microcrap removed the drive extender. Rubylaser goes over how to add a spare to the array and then expand it.

---

### Post by ChasHutch on 2011-02-01
Nobody mentioned the Amahi home server.  While it's currently based on Fedora, I believe there is a debian (ubuntu) port in the works.

---

