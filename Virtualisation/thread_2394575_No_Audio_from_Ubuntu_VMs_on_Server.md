---
title: "No Audio from Ubuntu VMs on Server"
date: 2018-06-18
forum: Virtualisation
---

### Post by dlfuller@ClientandFuller. on 2018-06-18
I'm trying to get audio working from a virtual machine to a host that uses Microsoft Remote Desktop (RDP) for controlling the VM.  Internet searches for a solution have simply been confusing with too many options.

The setup is Ubuntu and Windows 10 VMs on an Ubuntu 18.04 Server.  The host is MacOS 10.13.5 using SSH to control the server through the CLI.  Then phpVirtualBox 5.2-0 connects using wired Ethernet to VirtualBox 5.2 running on the server.  Finally, Microsoft Remote Desktop 10.1.8 displays and controls the running VMs.  They do all have the VirtualBox Extension Packs installed.

Everything works great except no sound from the Linux VMs!  But, at least sound does work from the Windows 10 VM.

I first thought since it was easy with the Microsoft approach it should also work from the Linux VMs by using some sort of remote desktop setup getting analog or digital audio.  But not so with the Microsoft Remote Desktop.

So my next step next was to check Linux audio settings, packages installed on the server, and if pulseaudio might be the approach to serve audio to the host.  Yes, a bunch of alsa and pulseaudio files and modules are there on the server and AlsaMixer displays data as though everything is there.

But, then there are multiple choices for audio devices in the configuration of the Linux VMs besides the default ALSA Audio Driver and Intel HD Audio.  And the differences between virtualized and real hardware all became overwhelming considerations while searching for solutions.

Any guidance to a workable solution and clarification of the virtualized served audio situation would be appreciated.

---

