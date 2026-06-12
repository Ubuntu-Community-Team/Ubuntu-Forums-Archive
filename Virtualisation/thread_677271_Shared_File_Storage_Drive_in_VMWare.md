---
title: "Shared File Storage Drive in VMWare?"
date: 2008-01-24
forum: Virtualisation
---

### Post by dbsoundman on 2008-01-24
I may have missed this option while installing VMWare, but is there a way I can create a shared file storage drive so that I can share files between my virtual Win2K install and Ubuntu? I use the Win2K for importing music to my MP3 player which is strictly windows compatible, and I was hoping I could then use the normal MP3 files I ripped in Win2K in Ubuntu if I felt the need. How might I do this? I have a feeling the whole NTFS/ext3 thing might be a problem, but I'm just looking for ideas. Thanks!

-Dan

---

### Post by HermanAB on 2008-01-24
On VMware Worrkstation, Click VM, Settings, Options, Shared Folders.

Cheers,

Herman

---

### Post by dbsoundman on 2008-01-24
I have VMWare Server, and it doesn't seem to have that option...did I maybe download the wrong version of VMWare for my applications?

-Dan

---

### Post by HermanAB on 2008-01-24
If it doesn't have it, then use SSH (or FTP).  Install OpenSSH on your host and use Nautilus, Konqueror (horror) the command line to copy files around.

---

### Post by dcstar on 2008-01-26
> **dbsoundman said:**
> I may have missed this option while installing VMWare, but is there a way I can create a shared file storage drive so that I can share files between my virtual Win2K install and Ubuntu? I use the Win2K for importing music to my MP3 player which is strictly windows compatible, and I was hoping I could then use the normal MP3 files I ripped in Win2K in Ubuntu if I felt the need. How might I do this? I have a feeling the whole NTFS/ext3 thing might be a problem, but I'm just looking for ideas. Thanks!

-Dan

Install SAMBA on the host and share a folder that way - I have just done this and it works fine (plenty of HOWTOs around exactly on this topic).

---

### Post by fjgaude on 2008-01-26
> **dcstar said:**
> Install SAMBA on the host and share a folder that way - I have just done this and it works fine (plenty of HOWTOs around exactly on this topic).

And after you have done the share folder bit don't forget to enter your name and password so that Samba can recognize you:

```
sudo smbpasswd -a yourloginname
```

That's done it. You get to the shares through Windows Explorer through Networks, or through any program that can go to Networks.

Works great, and under VMware server, speed is about 60% of what it would be in a direct boot. Not bad.

---

### Post by diablo75 on 2008-01-27
Can someone help me with a similar problem I am having?

I have VMware Server.  And I think samba is installed on my Gutsy, but not sure.  I suppose I could check with synaptic about that (it's on a computer elsewhere at the moment).  I have a folder on my Ubuntu computer that is shared using SMB, and I also have a folder on a guest XP VM that is shared.  The guest has also been set up to use bridged, NAT and host only (I've tested all three methods).  I can connect to the Internet with no problem using the first two, so there is connectivity there.  But I have never been able to get nautilus network places to show my guest share or even the computer that's sharing them.

I'd like help covering all the bases setting up a samba share from beginning to end so I can figure out how to do this right.

---

### Post by fjgaude on 2008-01-27
You have used the menus in Gnome to setup your shares in Ubuntu, you have entered your password like shown in the previous post? Yes.

The better way I know of to exchange files, see them, is in WinXP using any program, like Explorer, to go to Network usually at the bottom of the list of directories, and click Entire Network, then Microsoft Windows Network, then whatever you declared in Ubuntu as your workgroup. Click on your computer name and then you see the shares you setup in Ubuntu. You have full access to everything if you have your password handy.

Another way which I don't use is in Ubuntu find out what the IP address of your WinXP guest is and use that in Nautilus by going to Files/Service type/Windows Shares. From there you likely can do what you wish.

See if you can find the IP of your guest. Hint: In WinXP, click Start, then Run. At the prompt enter cmd and then your Enter key. Then enter ifconfig, Enter key. Notice the IP address as something like: 170.16.104.70. That's the one you use to Nautilus and in your hosts file.

Let us know how you are doing.

---

### Post by dbsoundman on 2008-01-29
Ok, so I haven't really been able to find much helpful information regarding what I want to do. Maybe I'm just looking in the wrong places. I set up my shared folder to be the "my documents" folder in my Windows 2000 guest machine, and the machine has no password, only a user with my name. How exactly do I get samba to mount that directory in ubuntu? If there's a howto out there on how to do this that I missed, feel free to point me in the right direction. Thanks!

-Dan

---

### Post by fjgaude on 2008-01-30
AFAIK there is no how-to, but I know exactly how to do what you wish. I'll have to take the time to explain it in more detail than done in the previous post.

Have to run now, but will get back with you. You have to find out what the IP address of your guest is through the use of the command: ipconfig in Windows.

See you down the lines...

---

### Post by dbsoundman on 2008-01-30
Excellent, thanks! No hurry, I'm not desperate to set this up immediately...it would just be nice, so I can eventually basically backup my music on my mp3 player on my external hard drive and do things like that.

-Dan

---

### Post by fjgaude on 2008-01-31
Okay, Dan, I've not used Win 2000 for seven years and have forgotten its details. But the first thing you have to do is find out how to enter a terminal and get to the command line through some "run" command, then enter the command "cmd". From there you will be able to enter the command "ipconfig".

The screen will then show the IP connection: 172.12.104.128. Something like that.

When you get this IP address, let me know. Then we will go from there.

---

### Post by WSmart on 2008-01-31
No idea on the VM machine stuff, FYI.   I just set up an XP Ubuntu share, both ways.   Seems similar.

I made sure that my firewalls were set up to accept the IP addresses.  You have to save your settings in ZoneAlarm.  You can't just enter it.  You have enter and save, I found out after eight hours of nothing.

You can right click on the folder and select share from the context menus in both Ubuntu and Windows.  I never opened Nautilus or whatever.  

I installed Samba from Synaptic, the depostiory-I have it all selected except the beta stuff.

You have to go to a special location to view the shared folders, in both operating systems. 

In Ubuntu you go to the Places menu and you'll see the computer name of the Windows system listed there which opens all your shares from that system.  

With windows it's a folder on the desktop called My Network Places, and you'll have to have Windows actively look for the Ubuntu share, or I did.  You hit the Add Network Place link which is normally on the left under Network Tasks, and then choose Other Network places, Browse, Entire Windows Network, My Home, and your Ubuntu machine should be listed there. 

Give some feedback if you figure this out, please;  I'm watching this.

Edit:  I got the IP addresses from my DSL router configuration page.

---

### Post by fjgaude on 2008-01-31
Okay, WSmart, but I'm trying to lead Dan through this process, step-by-step. It'll become clear to what I'm doing and why. I've got it working on my system, fully, but on Windows XP, not 2000.

---

### Post by dbsoundman on 2008-02-01
Thanks for helping, fjgaude!

I ran ipconfig and found that my IP address is 192.168.1.105. What's next?

-Dan

---

### Post by fjgaude on 2008-02-01
You are not running NAT, but Bridged, connected directly to your router?

Okay, if that is the case, in a terminal in Ubuntu, run this command:

```
sudo skgedit /etc/hosts
```

At the bottom of the file add this along with whatever you have called your Windows install:

```
192.168.1.105 nameofvminstall
```

In Nautilus, click on File, then Connect to Server. Click on the top line and then click on Windows Shares. Enter your nameofvminstall there. If you are asked for a password, give your Windows one.

You should now see your Windows shares that you declared as shares in Windows. We are close and likely when you access those shares you will get an icon on your Ubuntu desktop.

Let me know what happens.

---

### Post by dbsoundman on 2008-02-01
OK, I added the IP address and install name to the /etc/hosts file, and I see now if I open my network settings manager it appears under my list of hosts. Was something supposed to appear on the desktop or something, or am I to do something with samba to see the shared folders like you said?

-Dan

---

### Post by fjgaude on 2008-02-01
Simply click, double-clcik on the host name and a window should open. At the same time an icon comes onto the desktop.

You might be asked for your Windows password.

---

### Post by dbsoundman on 2008-02-01
Excellent, thanks! It works now. At first I was looking at the wrong thing...I restarted the VM, went to Connect To Server, and connected, and it's all good. The only problem I had was figuring out what password I set, but I got it now. I'm glad it was so easy!

-Dan

---

### Post by fjgaude on 2008-02-01
What a trip... we live and learn, eh?

So glad you have what you sought.

---

### Post by Shazaam on 2008-02-01
Another thing you can do is a vm dual boot. I have a vm with 8 os's installed and running fine. :)
1. dsl
2. Puppy
3&4 -2 versions of Knoppix (2.4 and 2.6 kernels)
5. Mepis
6. Mandriva
7. Ubuntu Gutsy
8. Ubuntu Dapper

---

