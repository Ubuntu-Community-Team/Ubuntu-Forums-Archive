---
title: "rdesktop does not work well"
date: 2017-08-31
forum: Virtualisation
---

### Post by someone613 on 2017-08-31
I have a Windows 10 computer with a user on which to do RDP


I run rdesktop on my ubuntu and connect to my computer
Most quality is fine
Only videos I see the screen moves slowly

On the same computer that I run ubuntu if I run Windows 10 and run through it RDP I see excellent

What setting should I change in Linux to get quality like Windows rdp ??

Thanks

---

### Post by TheFu on 2017-09-01
Remote watching of videos doesn't work well on pretty much any remote desktop solution with Windows - except the paid ones like Xen's VDI stuff.

Using a Linux desktop, accessing a Linux desktop inside a VM running KVM using QXL and SPICE protocols can support it, however.  This assumes you are sitting on the same machine where the desktop is running.  There are QXL/SPICE video drivers for Windows7+ - I've never tried Win10, so I don't know how it works.  Further, my KVM servers don't have any graphics, so while I've used SPICE to connect to a remote Win7 guest VM, I've never attempted to watch videos in that way.

There is GPU passthru for Windows on a Linux KVM host. I think the VMware Workstation supports this too, for specific versions of Linux, Windows, on specific hardware.  Both require specific hardware.

**An alternative.**
Storage sharing methods DO work well between Windows and Linux systems.  The key is to make the video playback on the desktop you are sitting behind, regardless of where the file is located.  I use this ALL-THE-TIME.  If the files are on Windows, use a samba-client to access them, after setting up file sharing on Windows first.  If the files are on Linux, use NFS to share the location to any Unix/Linux/OSX clients.  NFS is about 20-30% more efficient.  Neither NFS nor samba/CIFS should be used over the internet due to security considerations.

If you want to share media over the internet, something like Plex Media Server can do that and will transcode the files based on settings. In the version I use, manual control over the transcode bitrate is used.  It can also be used on the LAN and doesn't require any transcoding thanks to the much higher bandwidth.

**Another alternative.**
Windows media center is a DLNA server.  Plex is also a DLNA server and there is miniDLNA, if you prefer that.  Pretty much any OS has DLNA clients/controllers. You can use any of these to access the DLNA server.  The neat thing about plex is that it has different transcoding profiles based on where the video is being rendered.  That makes it really handy to use with Chromecast, Amazon Fire Sticks, or Kodi on a Raspberry-Pi.

I access my Plex using an ssh SOCKs proxy from all over the planet. This way, the connection is secured by a VPN-like tunnel, and no Plex account is needed.  It always works for audio and usually works for video, provided the location I'm at has sufficient bandwidth. 

So ... you have lots of options.

Of course, if you just need productivity applications to work, then RDP should be fine.  When I need a remote desktop on a Windows machine and I'm not on my LAN, I will use a 
Linux--Linux--Windows setup.
The Linux-2-Linux is over x2go.  Then the middle linux machine runs RDP to connect to Windows.  x2go is 2-3x faster than any RDP I've seen.  It won't work for video, but for productivity, it is pretty great, considering.

---

