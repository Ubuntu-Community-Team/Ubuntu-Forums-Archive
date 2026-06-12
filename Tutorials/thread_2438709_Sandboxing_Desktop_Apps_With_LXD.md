---
title: "Sandboxing Desktop Apps With LXD"
date: 2020-03-17
forum: Tutorials
---

### Post by DuckHook on 2020-03-17
***Table of Contents***

[Introduction]("https://ubuntuforums.org/showthread.php?t=2438709&p=13939382#post13939382")
[Installing LXD into Ubuntu Bionic]("https://ubuntuforums.org/showthread.php?t=2438709&p=13939383#post13939383")
[Setting up a ZFS pool to act as container storage]("https://ubuntuforums.org/showthread.php?t=2438709&p=13939384#post13939384")
[Configuring a profile to work with X11 and pass sound to the host]("https://ubuntuforums.org/showthread.php?t=2438709&p=13939385#post13939385")
[Installing and configuring Firefox]("https://ubuntuforums.org/showthread.php?t=2438709&p=13939386#post13939386")
[Accessing files between host and container]("https://ubuntuforums.org/showthread.php?t=2438709&p=13939388#post13939388")
[How to both take snapshots and roll back to earlier snapshots]("https://ubuntuforums.org/showthread.php?t=2438709&p=13939389#post13939389")
[Installing and configuring WINE]("https://ubuntuforums.org/showthread.php?t=2438709&p=13939392#post13939392")
[Installing and configuring Steam]("https://ubuntuforums.org/showthread.php?t=2438709&p=13939393#post13939393")
[Running a Full, Separate Distro]("https://ubuntuforums.org/showthread.php?t=2438709&p=13943827#post13943827")
[Problems and Troubleshooting]("https://ubuntuforums.org/showthread.php?t=2438709&p=13945979#post13945979")
[Tips and Tricks]("https://ubuntuforums.org/showthread.php?t=2438709&p=13946023#post13946023")

---

### Post by DuckHook on 2020-03-17
LXD containers are often presented as an alternative to Virtual Machines. They have many advantages over VMs like smaller resource usage, native bare metal performance and bypassing the need for the hardware gymnastics of VT-x/AMD-V virtualization or GPU passthrough.

But, as of time of writing, LXD's most significant drawback is its lack of accessible documentation, tutorials or howtos for the general user. Although it is a solid and dependable technology and is the backbone of many giant server farms, it is currently confined to the enterprise and has been too arcane and obscure for the general desktop user.

What follows is a simplified implementation of LXD on the desktop. I hope to show users the steps involved in:

[LIST]
[*]Installing LXD into Ubuntu Bionic
[*]Setting up a ZFS pool to act as container storage
[*]Configuring a profile to work with X11 and pass sound to the host
[*]Installing and configuring Firefox
[*]Accessing files between host and container
[*]How to both take snapshots and roll back to earlier snapshots
[*]Installing and configuring WINE
[*]Installing and configuring Steam
[*]Running a Full, Separate Distro
[*]Problems and Troubleshooting
[*]Tips and Tricks
[/LIST]
The power and flexibility of LXD is too vast to cover in one tutorial and, in any case, this writer is not sufficiently knowledgeable to guide you. Therefore, the following instructions are bound to be limited in scope and understanding. If readers require guidance or have further ideas they wish to contribute, please post these in the Virtualization forum.

---

### Post by DuckHook on 2020-03-17
From Focal onward, LXD can only be installed as a snap. Therefore, there is no point in providing instructions for a .deb install.
```
duckhook@Zeus:~$ sudo snap install lxd
```
After installing LXD, check to see if we are members of the *lxd* group by invoking the *id* command. It should look something like the following:
```
duckhook@Zeus:~$ id
uid=1000(duckhook) gid=1000(duckhook) groups=1000(duckhook),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),118(lpadmin),128(sambashare),132(libvirt),137(vboxusers),999(lxd)
```
We must be members of the lxd group to run unprivileged containers which are essential for higher security. If we need to add ourselves to that group:
```
duckhook@Zeus:~$ sudo usermod -a -G lxd $USER		# you can replace $USER with your username
```

Do not run lxd until we set up a zfs pool in the next panel.

---

### Post by DuckHook on 2020-03-17
ZFS is another huge topic in and of itself. We will only cover the basics needed to create a pool sufficient for container storage. An easy introduction to ZFS is available at: [https://ubuntu.com/tutorials/setup-zfs-storage-pool#1-overview](https://ubuntu.com/tutorials/setup-zfs-storage-pool#1-overview)

The following assumes that you have an extra partition somewhere on your system that you can dedicate to ZFS. This will greatly simplify the future maintenance of your containers. If you do not have such a partition yet, then you must create one if you wish to follow along with this tutorial. It doesn't have to be massive, but I would recommend one no smaller than 50 GB. If you intend to use it for lots of games (we will be using it for WINE and Steam), then you might need more than 50 GB.

Since there are well nigh infinite variations to people's HW configurations, it will be left as an exercise for the reader to create the partition. There are many internet tutorials that can be used for guidance. For our purposes, I assume an empty partition /dev/sdd1.

Install the toolkit for ZFS with:
```
duckhook@Zeus:~$ sudo apt install zfsutils-linux
```
Let's create our pool and call it containers (since we will be using it for lxd containers).
```
duckhook@Zeus:~$ sudo zpool create containers /dev/sdd1
```
The newly created pool is mounted at /containers  . We are fine with this.

It's a good idea to check the new pool's status:
```
duckhook@Zeus:~$ sudo zpool status
[sudo] password for duckhook:
  pool: containers
 state: ONLINE
config:

	NAME                        STATE     READ WRITE CKSUM
	containers                  ONLINE       0     0     0
	  sdd1                      ONLINE       0     0     0

errors: No known data errors
```
**Note**> It is possible to use another file system for LXD instead of ZFS. Of particular note is LVM. If you already use LVM and have LVM volumes set up, you may wish to replace ZFS with LVM instead—at the cost of a reduced feature set. What's important to LXD is the use of a filesystem that supports things like cloning and snapshots. In this regard, LVM is a less capable but acceptable alternative. But since LVMs are not the default in LXD, I will leave its implementation as an exercise for the reader.

We are now ready to initialize LXD. We do so by running lxd init  . This will bring up a series of questions, each of which has a default. Be careful. We cannot accept all defaults because we have already created a zfs pool that we want to use for our containers. Therefore:
```
duckhook@Zeus:~$ lxd init
Would you like to use LXD clustering? (yes/no) [default=no]: 
Do you want to configure a new storage pool? (yes/no) [default=yes]: 
Name of the new storage pool [default=default]: containers
Name of the storage backend to use (dir, lvm, zfs, ceph, btrfs) [default=zfs]: 
Create a new ZFS pool? (yes/no) [default=yes]: no
Name of the existing ZFS pool or dataset: containers
Would you like to connect to a MAAS server? (yes/no) [default=no]: 
Would you like to create a new local network bridge? (yes/no) [default=yes]: 
What should the new bridge be called? [default=lxdbr0]: 
Would you like LXD to be available over the network? (yes/no) [default=no]: 
…
```
Note that we do not accept the defaults at step #3 and step #5, but substitute our values instead. Remember that Linux is case sensitive. The name of the storage pool must be exactly what we created in the ZFS procedure. The rest of the initialization can be done using the defaults.

It is also worth noting that you must accept the creation of a network bridge if you want to connect to the internet. We answer "no" (the default) to whether we want LXD to be available over the network. For our purposes, containers do not need to be enabled for contact from the outside. We will not be running web or mail servers from our containers. Rather, we want them to be as secure as possible.

:!: **NOTE** :!:
> If installing on a host that is already using ZFS as its underlying file system, see [Tips and Tricks]("https://ubuntuforums.org/showthread.php?t=2438709&p=13946023#post13946023") below.

Once LXD has been initialized, we are ready to create the profile.

---

### Post by DuckHook on 2020-03-17
Here's where things get interesting (and a little complicated).

The act of initializing LXD automatically creates a default profile that sets up essential functionality like a network bridge, mapping LXD to the container pool and the other primary services needed to operate a LXD instance. If we were to create such an instance at this point, it would already be quite usable. We could invoke a shell to login and we could install usable command line apps like *mutt*, *lynx* and *irssi*. However, we would not be able to launch graphical apps because we don't yet have the hooks that the instance needs in order to display graphics through x11 and output sound through pulseaudio. To make those hooks, we must create another profile that links internal container audio-visual outputs to host outputs.

It's best to do this by creating a plain text file first so that we can edit it to our heart's content. We will then export this text file into LXD once it's been vetted and finalized. I store all configuration files of this sort in my personal bin directory.
```
duckhook@Zeus:~$ nano /home/duckhook/bin/x11.profile  # use your GUI editor if you prefer
```
Paste the following into x11.profile:
```
config:
  environment.DISPLAY: :0
  environment.PULSE_SERVER: unix:/var/pulse-native
  user.user-data: |
    #cloud-config
    runcmd:
      - 'sed -i "s/; enable-shm = yes/enable-shm = no/g" /etc/pulse/client.conf'
    packages:
      - x11-apps
      - mesa-utils
      - pulseaudio
    write_files:
      - owner: root:root
        permissions: '0644'
        append: true
        content: |
          PULSE_SERVER=unix:/var/pulse-native
        path: /etc/environment
description: GUI LXD profile
devices:
  PASocket1:
    bind: container
    connect: unix:/run/user/1000/pulse/native
    gid: "1000"
    listen: unix:/var/pulse-native
    mode: "0777"
    security.gid: "1000"
    security.uid: "1000"
    type: proxy
    uid: "1000"
  X1:
    bind: container
    connect: unix:@/tmp/.X11-unix/X0
    listen: unix:@/tmp/.X11-unix/X0
    security.gid: "1000"
    security.uid: "1000"
    type: proxy
  mygpu:
    type: gpu
name: x11
used_by:
```
Some very important things to note:

[LIST=1]
[*]This file makes no allowance for proprietary graphics drivers. If you use closed-source drivers like many people who have nVidia GPUs do, then additional settings are needed. I do not use nVidia, so the following are purely settings gleaned from on-line sources. I cannot troubleshoot them and cannot help you with them. For nVidia GPUs using the closed-source drivers, add the following lines under config:
```
  nvidia.driver.capabilities: all
  nvidia.runtime: "true"
```
[*]If you only have nouveau installed, DO NOT use these lines. If you have no nVidia GPU, DO NOT add these lines. These options will break the profile for any GPU that is not nVidia running on closed-source drivers.
[*]This profile assumes a standard x11 display environment on the host of "0". If you have more than one monitor or you access through RDP, your display environment might not be "0", in which case, you must change this line:
```
    connect: unix:@/tmp/.X11-unix/X0
```
&#8230;and replace X0 with whatever your display environment is: say, X1. To determine what your display environment is, do:
```
printenv DISPLAY
```
If the result is :0, then keep the setting at X0. If the result is :1, then change the setting to X1.
[*]Check your work carefully, save x11.profile and exit.
[/LIST]
Next, we create a profile called x11
```
duckhook@Zeus:~$ lxc profile create x11
```
Then, we pipe the contents of x11.profile into the profile just created:
```
duckhook@Zeus:~$ cat ~/bin/x11.profile | lxc profile edit x11
```
Alternatively, you can also just open up the x11 profile with:
```
duckhook@Zeus:~$ lxc profile edit x11
```
&#8230;then copy and paste the contents of x11.profile into the empty profile. However, lxc uses VIM as its default editor and most general users find VIM to be a difficult editor to learn.

There's a lot going on here. If you wish to unpack the meaning for these keys, the primary resource that I used was: [https://blog.simos.info/running-x11-software-in-lxd-containers/](https://blog.simos.info/running-x11-software-in-lxd-containers/)

If everything went smoothly, we are now ready to launch our first container. Before doing so, I should touch upon a few further points:

[LIST]
[*]To launch our first container instance, we need to base it on a specific image. LXD has a number of images prebuilt online, one of which must be downloaded before the container instance can be launched.
[*]This download can take some time and will use considerable bandwidth. Mine was over 1.3 GB of data. Make sure that you have a fast, decent connection when downloading an image for the first time.
[*]LXD has an impressive collection of images. One doesn't have to use Ubuntu. Containers can be based on Arch, Debian, Gentoo, Fedora, you name it. To see all the images available, do:
```
duckhook@Zeus:~$ lxc image list images: | less
```
To see just the list of Ubuntu images:
```
duckhook@Zeus:~$ lxc image list ubuntu: | less
```
Piping through less is a good idea because the selection is pretty extensive.
[*]For our purposes, we will use Ubuntu 22.04. We want to base our container on a familiar and well tested image with known stability.
[*]Once an image is downloaded, it resides within the image directory of LXD. Thereafter, creating new containers based on that image is very fast because it is not necessary to download it again. Of course, basing containers on a different image will require that image to be downloaded in its entirety the first time.
[/LIST]
Let's create our first container and call it firefox:
```
duckhook@Zeus:~$ lxc launch ubuntu:22.04 --profile default --profile x11 firefox
```
We are using two profiles for this container: the default profile created in the LXD initialization process and the x11 profile that we just created. The first is necessary for basic functionality; the second enables a working GUI.

Start the container:
```
duckhook@Zeus:~$ lxc start firefox
```
To check its status:
```
duckhook@Zeus:~$ lxc list
```
Let's start a shell and log in:
```
duckhook@Zeus:~$ lxc exec firefox -- sudo --user ubuntu --login
```
You can poke around to your heart's content. If you have a favourite bash profile, feel free to edit .bashrc.

The first item of importance is to check that all the parts we wanted are present and working:
```
ubuntu@firefox:~$ glxinfo -B
```
Mine returns the following. Yours will differ depending on your video subsystem:
```
ubuntu@firefox:~$ glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: X.Org (0x1002)
    Device: AMD TAHITI (DRM 2.50.0, 4.15.0-88-generic, LLVM 9.0.0) (0x679a)
    Version: 19.2.8
    Accelerated: yes
    Video memory: 3072MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.5
    Max compat profile version: 4.5
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 2194 MB, largest block: 2194 MB
    VBO free aux. memory - total: 2019 MB, largest block: 2019 MB
    Texture free memory - total: 2194 MB, largest block: 2194 MB
    Texture free aux. memory - total: 2019 MB, largest block: 2019 MB
    Renderbuffer free memory - total: 2194 MB, largest block: 2194 MB
    Renderbuffer free aux. memory - total: 2019 MB, largest block: 2019 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 3072 MB
    Total available memory: 5115 MB
    Currently available dedicated video memory: 2194 MB
OpenGL vendor string: X.Org
OpenGL renderer string: AMD TAHITI (DRM 2.50.0, 4.15.0-88-generic, LLVM 9.0.0)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 19.2.8
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.5 (Compatibility Profile) Mesa 19.2.8
OpenGL shading language version string: 4.50
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 19.2.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
```
For fun, and also to test x11, lets try xclock, glxgears and xman:
```
ubuntu@firefox:~$ xclock
ubuntu@firefox:~$ glxgears
ubuntu@firefox:~$ xman
```
This should bring up each of these three X apps on your desktop.

Now, to test if the pulseaudio hooks have been properly mapped:
```
ubuntu@firefox:~$ pactl info
```
Mine looks like this. Yours should look similar:
```
ubuntu@firefox:~$ pactl info
Server String: unix:/home/ubuntu/.pulse-native
Library Protocol Version: 32
Server Protocol Version: 32
Is Local: yes
Client Index: 46
Tile Size: 65472
User Name: duckhook
Host Name: Zeus
Server Name: pulseaudio
Server Version: 11.1
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.usb-Logitech_Logitech_Wireless_Headset_000D44B25A6A-00.analog-stereo
Default Source: alsa_input.usb-Logitech_Logitech_Wireless_Headset_000D44B25A6A-00.analog-mono
Cookie: 0793:b74f
```
:!: **NOTE** :!:
> If you don't see something like the above, you will have to troubleshoot. Sound is often problematic and may not work at the outset. If you do not get sound, try rebooting the container and wait a few minutes for the needed modules to load before logging in with a shell. If pulseaudio continues to be problematic, we may have to use a different approach. See [Problems and Troubleshooting]("https://ubuntuforums.org/showthread.php?t=2438709&p=13945979#post13945979").

Before installing anything, your first real action should be to update the container image:
```
ubuntu@firefox:~$ sudo apt update && sudo apt full-upgrade && sudo apt autoremove && sudo apt clean
```
If the update installs a new kernel or other system-level component, you should reboot the container before proceeding further:
```
ubuntu@firefox:~$ sudo reboot
```
If all of the above turn out well, pat yourself on the back. The hardest part is over and we should be good to go for the prize.

---

### Post by DuckHook on 2020-03-17
Installing Firefox in Ubuntu versions prior to Jammy (22.04) is straightforward because Firefox is still a self&#8209;contained .deb package in Ubuntu's main repository. But from Jammy onward, Firefox is a snap package. Even though a Firefox .deb package exists in the repos, this is just a stub that installs the snap version. As of the time of this edit, snap apps won't play audio in LXD. Therefore, we must use a workaround (if using Ubuntu versions prior to Jammy, skip to step number 5):

We install Firefox from the official Mozilla Team PPA. Although I usually caution users against using PPAs, this is an acceptable workaround for this special situation. The risk is minimal only because the PPA is maintained by the official Mozilla team, so it is important to double check that you are installing the proper PPA and not some unofficial one. This PPA solution has the added advantage of giving us the latest and most secure version of Thunderbird, which is always lagging in the repos.

[list=1]
[*]Add the PPA:```
ubuntu@firefox:~$ sudo add-apt-repository ppa:mozillateam/ppa
```
[*]Create the file:```
ubuntu@firefox:~$ sudo nano /etc/apt/preferences.d/mozillateamppa
```
[*]Fill it with the following, which will set the PPA to a higher priority than the snap version of FF:```
Package: firefox*
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 501
```
[*]Run the usual update:```
ubuntu@firefox:~$ sudo apt update
```
[*]Now we are ready to install Firefox. The installation of Firefox, or any graphical app for that matter, drags in a lot of dependencies. So be prepared for this. But because we are also installing a GUI app while bypassing a full DE installation, some components tend to get left behind. In particular, Firefox will throw up errors and sometimes refuse to run unless the canberra modules are loaded. It throws up errors on fonts too, but these can be ignored (or install the missing fonts if you like). So, to install Firefox:```
ubuntu@firefox:~$ sudo apt install firefox libcanberra-gtk-module libcanberra-gtk3-module
```
[*]Now for the good part:```
ubuntu@firefox:~$ firefox
```
[/list]
You should now have an instance of Firefox up and running. Your first visit should be to an audio site like Youtube or Spotify to check that audio works. If it does, start your process of customizing FF to your heart's content. It is reasonably sandboxed (although remember that X is inherently insecure) and runs much faster than it does in a VM.

Downloaded files will also be sandboxed in the container. We will talk about exchanging files later. To detach FF and run it independently to free up your shell:
```
duckhook@Zeus:~$ nohup lxc exec firefox -- sudo --user ubuntu --login firefox &
```
You can create a .desktop file for FF and add it to ~/.local/share/applications  . From there, you can tag it as a favourite to add to the gnome launcher. firefox.desktop can look something like this:
```
[Desktop Entry]
Version=1.0
Name=Firefox in LXD
Comment=Access the Internet with Firefox through a LXD container
Exec=lxc exec firefox -- sudo --login --user ubuntu /usr/bin/firefox %U
Icon=/usr/share/icons/hicolor/48x48/apps/firefox.png
Type=Application
Categories=Network;WebBrowser;
```
Once you have everything running reasonably well, I strongly advise that you take a snapshot of the container. This option is a big reason we went to all this trouble. After you have a snapshot in hand, you can tinker with the container all you like. Breakage becomes immaterial when you can just roll back to a known good snapshot.

Though beyond the scope of this tutorial, you can further harden FF with apparmor. You can activate ufw and restrict both outgoing and incoming ports. You can add Onion routing or OpenVPN so that this installation of Firefox is always anonymized. You can experiment in all sorts of ways.

---

### Post by DuckHook on 2020-03-17
It's a core function of web browsers that they must download files. But we've sandboxed this installation of FF pretty effectively within a container. So any file that it downloads will also be jailed within that container. How, then, do we exchange files with the host?

It is possible to access the container's files from the host using an arcane method that is described in this blog: [https://blog.simos.info/how-to-view-the-files-of-your-lxd-container-from-the-host/](https://blog.simos.info/how-to-view-the-files-of-your-lxd-container-from-the-host/)

However, there are a number of good reasons why this is not a good idea, mainly having to do with uid/gid problems that make the resulting file difficult to work with.

Thankfully, there is a much easier way to achieve our goal. LXD has a built-in function that allows the host to push and pull files directly to and from the container. Only the host has this functionality; the container does not. This preserves the sandbox around the container.

For illustrative purposes, let's create an empty file:
```
duckhook@Zeus:~$ touch testfile.txt
```
To push a copy of this file into the container:
```
duckhook@Zeus:~$ lxc file push testfile.txt firefox/home/ubuntu/testfile.txt
```
To pull a copy of the same file:
```
duckhook@Zeus:~$ lxc file pull firefox/home/ubuntu/testfile.txt testfile2.txt
```
It is even possible to edit this file within the container:
```
duckhook@Zeus:~$ lxc file edit firefox/home/ubuntu/testfile.txt
```
The file is automatically pulled from the container, opened in the editor defined by your EDITOR environment variable, then pushed back to the container upon closing the editing session.

But the above is all command line driven. What if we want something that works in, say, Nautilus?

This can be achieved using ssh. The Ubuntu 18.04 image that was downloaded as our template image has openssh-server pre-installed. It is easy to ssh into the container after setting up public/private paired keys. After that, we can set up a permanent sftp directory in the container that is always accessible to the host.

One can either find the container's ip address with ifconfig, or:
```
duckhook@Zeus:~$ lxc list
+---------+---------+--------------------+-----------------------------------------------+-----------+-----------+
|  NAME   |  STATE  |        IPV4        |                     IPV6                      |   TYPE    | SNAPSHOTS |
+---------+---------+--------------------+-----------------------------------------------+-----------+-----------+
| firefox | RUNNING | 10.36.16.88 (eth0) | xxxx:xxxx:xxxx:xxxx:xxx:xxxx:xxxx:xxxx (eth0) | CONTAINER | 1         |
+---------+---------+--------------------+-----------------------------------------------+-----------+-----------+

```
I have masked my IPV6 address because it is unique and can therefore identify me. However, the default behaviour of LXD sets up the IP4 network as a NAT. So my assigned address of 10.36.16.88 is isolated from the outside world though LXD's built in virtual router. Your address will likely be different. I can ssh into my container with:
```
duckhook@Zeus:~$ ssh ubuntu@10.36.16.88
```
We can also sftp into or scp to/from the container using this same address. On Nautilus, it's as simple as creating an sftp mount with: +other locations &#8594; Connect to Server, then entering the sftp address in the usual syntax:
```
sftp://ubuntu@10.36.16.88/home/ubuntu
```
In terminal, an easy method is Midnight Commander, which has a built-in sftp client (same above syntax).

If using a different image, you may have to install openssh-server, then configure it. ssh and sftp are huge topics that are beyond the scope of this tutorial. There are thousands of tutorials on the web that effectively explain how to implement this indispensible technology. Setting up openssh-server will be left as an exercise for the reader (hint—it's not that difficult).

**Note**> One can obviously also just set up a plain ftp server. But as a matter of principle, I never recommend insecure solutions. Bad habits are both bad and habits. Once they dig their tenacious claws into our psyche, they are difficult to remove. Best not to start down that road in the first place.

---

### Post by DuckHook on 2020-03-17
***Snapshots***

One of the most useful properties of containers is the ability to preserve snapshots and roll back to that snapshot should disaster strike. In our firefox example, we can take a snapshot of the container just after FF is installed. Then, if we are unfortunate enough to visit a bad site or download some file that proceeds to encrypt our whole install, the damage will be confined to the container. By simply restoring the original snapshot, the damage is contained.

It doesn't even have to be foul play. The comfort of a good snapshot frees us to experiment within the container as wildly as we like.

Remember that our underlying file system is ZFS? This is where it shines. ZFS is very efficient at storing snapshots. It stores only the data that has changed. Therefore, disk space is optimized and snapshots tend to grow slowly. Many users take multiple snapshots of their containers over time, eliminating the oldest ones, but keeping sufficient backups to always be safe.

Taking a snapshot could not be easier. Using the example of our firefox container:
```
duckhook@Zeus:~$ lxc snapshot firefox 2020-03-16_pristine_snap
```
You can call your snapshot whatever you like, but it is advisable to give it a descriptive name and date for easier future reference. My naming convention starts with the date in international format for easier sorting and parsing.

To restore a snapshot:
```
duckhook@Zeus:~$ lxc restore firefox 2020-03-16_pristine_snap
```
Voilà—damage instantly undone.

To delete a snapshot:
```
duckhook@Zeus:~$ lxc delete firefox/2020-03-16_pristine_snap -i
```
The -i switch forces user confirmation. It's a good habit to always use it. Like many Linux commands, LXD assumes you know what you are doing and, without the -i switch, will delete your snapshot without further protest.

If you wish to see the combined information of your container and all of its snapshots:
```
duckhook@Zeus:~$ lxc info firefox
```
***Cloning***

Snapshots are wonderful, but there are occasions when I have taken great pains and spent considerable time tweaking a container to a desired state. I don't want to repeat this process for every new container. Instead I want to base new containers on this carefully optimized one. The solution? Clone your template container:
```
lxc copy firefox name_of_new_container
```
The new container will be identical to the original except for keys and settings which need to be unique (like MAC addresses, etc). It will also start out with an empty snapshot slate, ready to tread its own path in life.

Stéphane Graber is one of the lead developers for LXD. His blog is an immensely valuable resource for those wanting to learn more: [https://stgraber.org/](https://stgraber.org/)

---

### Post by DuckHook on 2020-03-17
> Other sections of this tutorial have been reviewed and updated to work on Ubuntu Jammy (22.04), but when this tutorial was written, the versions used in this section were current. However, I chose to leave this section in its original form because, at time of writing, it illustrated three important concepts. One of those concepts&#8212;the ability to install a newer version container onto an older version host&#8212;remains valid, if one makes the mental adjustment to account for versions that were then current but are now out of support. It should go without saying that one should never run end&#8209;of&#8209;life versions and should substitute current supported versions for a current installation.
The process of installing WINE allows us to delve into some LXD features that further illustrate the power and flexibility of containers. These benefits include:

[LIST]
[*]The ability to run a later version of an OS within a container
[*]Adding libraries and dependencies for 32-bit architecture without compromising our base install
[*]Adding PPAs more securely because they are sandboxed within the container
[/LIST]
As of time of writing, the latest version of WINE requires *libfaudio0* as a dependency. However, Ubuntu 18.04 does not have this library in its repository. So we either have to install it standalone or add yet another PPA. Neither choice is ideal: standalone libraries don't get updated and the practice of adding PPAs is a big security risk at any time. But Ubuntu 19.10 *does* have this dependency in its repos. Therefore, the easiest solution is to create a container based on 19.10.

WINE also requires that 32-bit architecture be installed and enabled. However, we may not want 32-bit libraries bloating up our base install. A clean base install offers the smallest attack surface to bad guys and many of us try to practice good computing hygiene by limiting our base install to only the default apps and services. Therefore, containerizing WINE is doubly beneficial.

Let's create an Ubuntu 19.10 container named wine. As a new image, it must be downloaded for the first time. Mine was over 2 GB and took more than half an hour to complete. Use a good reliable connection and be patient:
```
duckhook@Zeus:~$ lxc launch ubuntu:19.10 --profile default --profile x11 wine
```
Start the wine container:
```
duckhook@Zeus:~$ lxc start wine
```
Now, let's make use of the power from "Exchanging files". I like to customize .bashrc to define additional aliases, so:
```
duckhook@Zeus:~$ lxc file edit wine/home/ubuntu/.bashrc
```
I also have a customized .screenrc that I have put many hours into and tweaked to my liking over the years:
```
duckhook@Zeus:~$ lxc file push .screenrc wine/home/ubuntu/.screenrc
```
Let's add our ssh public key to the container for easy ssh/sftp:
```
duckhook@Zeus:~$ lxc file push ~/.ssh/id_rsa.pub wine/home/ubuntu/.ssh/authorized_keys
```
Let's invoke a shell and login to our new container:
```
duckhook@Zeus:~$ lxc exec wine -- sudo --user ubuntu --login
```
Check that everything is working and update the container image:
```
ubuntu@wine:~$ glxinfo -B
ubuntu@wine:~$ pactl info
ubuntu@wine:~$ sudo apt update && sudo apt full-upgrade && sudo apt autoremove && sudo apt clean
ubuntu@wine:~$ sudo reboot
```
The last command will drop us out of the container. If everything looks okay, now is a good time to take a snapshot:
```
duckhook@Zeus:~$ lxc snapshot wine 2020-03-17_pristine_wine
```
Now let's get ready to install WINE. Firstly, a few considerations: if you want to run the WINE app available in the repo, this is perfectly fine. It has been tested to work with the version of Ubuntu we are running and can be installed with the usual sudo apt install. However, the Ubuntu repo version of WINE is always older than the most current version&#8212;sometimes by quite a few releases. Since WINE is often installed to run the latest games, an old WINE version is a serious drawback, in some cases, unacceptably so. Therefore, it is one of the few exceptions to my "no PPAs" rule.

In fact, while there do exist a number of PPAs for WINE, the best and most secure way is to add WINE's own repository to sources.list.

Firstly, we must add 32-bit architecture:
```
ubuntu@wine:~$ sudo dpkg --add-architecture i386 && sudo apt update
```
Let's get the WINE repo's key:
```
ubuntu@wine:~$ wget -nc https://dl.winehq.org/wine-builds/winehq.key
```
Add the key to the container's keychain:
```
ubuntu@wine:~$ sudo apt-key add winehq.key
```
Now let's add the WINE repository itself. Make sure to use the proper repo for your version, in our case, eoan:
```
ubuntu@wine:~$ sudo apt-add-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ eoan main'
```
Do the usual update and housekeeping:
```
ubuntu@wine:~$ sudo apt update && sudo apt full-upgrade && sudo apt autoremove && sudo apt clean
```
The repo is now added and ready to rock and roll. We have three choices: WINE stable, development or staging. Let's use the boring but more reliable stable. Note that staging will sometimes be better for newly released games and apps at the price of less stability. Development is the most bleeding edge of all, but be prepared for lots of instability, bugs, regressions and reporting.

Again, it's a big download: over 200 MB on my system. Try to use a fast and reliable connection:
```
ubuntu@wine:~$ sudo apt install --install-recommends winehq-stable
```
The above instructions are also available and should be kept current on [WINEHQ's website]("https://wiki.winehq.org/Ubuntu").

Now is a good time to take another snapshot:
```
duckhook@Zeus:~$ lxc snapshot wine 2020-03-18_wine_stable
```
Now let's install winetricks and supporting services (be prepared for yet another large download):
```
ubuntu@wine:~$ sudo apt install winetricks zenity
```
Then launch winetricks for the first time, which should create the default .wine directory under our home directory tree:
```
ubuntu@wine:~$ winetricks
```
WINE has an ancient version of Internet Explorer (ver 5.0) bundled with it. Let's launch it using WINE syntax:
```
ubuntu@wine:~$ env WINEPREFIX="/home/ubuntu/.wine" wine C:\\\\windows\\\\command\\\\start.exe /Unix /home/ubuntu/.wine/dosdevices/c:/'Program Files (x86)/Internet Explorer/iexplore.exe'
```
You should now have a primitive version of Internet Explorer running. This version of Internet Explorer is so riddled with security holes that it must not be used for surfing. We invoke it only for purposes of illustration.

**NOTE:**> By its nature, WINE tries to shoehorn alien programs into an operating system for which they were never designed. Given that WINE is essentially an attempt to force a round peg into a square hole, program misbehaviour is usually due to WINE/program incompatibility and not to container misconfiguration. That said, I have found that audio remains the buggiest area of LXD implementation and sound will sometimes work only intermittently for maddeningly elusive reasons.

WINE is so vast and complex that it is far beyond the scope of this tutorial, but the following links should at least get you started.

[LIST]
[*][A (somewhat old) primer for WINE syntax]("https://www.linuxquestions.org/linux/answers/applications_gui_multimedia/complete_guide_using_wine_command_line")
[*][A good introduction to installing programs in WINE]("https://itsfoss.com/use-windows-applications-linux/")
[*][WINEHQ's list of WINE commands]("https://wiki.winehq.org/List_of_Commands")
[/LIST]

---

### Post by DuckHook on 2020-03-17
Steam is easier to install and configure, and has fewer issues, than those which confront WINE.

I've found that the most stable way to run Steam is to match the container's version to the host's. Therefore:
```
duckhook@Zeus:~$ lxc launch ubuntu:22.04 --profile default --profile x11 steam
duckhook@Zeus:~$ lxc start steam
```
Set up our working environment the way we like:
```
duckhook@Zeus:~$ lxc file edit steam/home/ubuntu/.bashrc
duckhook@Zeus:~$ lxc file push .screenrc steam/home/ubuntu/.screenrc
duckhook@Zeus:~$ lxc file push ~/.ssh/id_rsa.pub steam/home/ubuntu/.ssh/authorized_keys
```
Login to a shell:
```
duckhook@Zeus:~$ lxc exec steam -- sudo --user ubuntu --login
```
Make sure x11 and pulseaudio are working:
```
ubuntu@steam:~$ glxinfo -B
ubuntu@steam:~$ pactl info
```
Steam is a 32-bit app, so we activate the i386 repos:
```
ubuntu@steam:~$ sudo dpkg --add-architecture i386
```
Update sources.list and do upgrade and housekeeping:
```
ubuntu@steam:~$ sudo apt update && sudo apt full-upgrade && sudo apt autoremove && sudo apt clean
```
We are now ready to install steam. Steam is unusual in being a two-step install. The first step does not install the actual game engine: it installs only another installer. This is an interesting strategy because, by nesting their app in this way, Steam can continuously upgrade their game engine without having to wait for Ubuntu version upgrades:
```
ubuntu@steam:~$ sudo apt install steam-installer
```
The first time we launch Stream, it will download the game engine, which could take a while:
```
ubuntu@steam:~$ steam
```
Steam will launch after the game engine finishes downloading and you can then log into Steam and download all of your individual games.

***Some very important notes:***

[LIST]
[*]Modern games are massive. Increasing your ZFS storage pool is outside the scope of this tutorial, but it is far easier to do this with ZFS than it is with an older file system. Many instructions are available on line.
[*]Steam browser does not follow Linux conventions in its window management. Whereas Linux convention calls for the parent process to terminate when its child window is closed, Steam browser's default is to continue running the parent process when the child window is closed. It works around this issue by trying to place an AppIndicator on the system tray from which we are supposed to be able to reattach a new child window to the running process. However, to enforce good security, LXD may not permit contained processes to access other system resources like the system tray. If the Steam AppIndicator is missing on the system tray, then closing or even minimizing the Steam browser window leaves one with no obvious way to reconnect with the still running parent process, except to kill it. This is inelegant and may possibly corrupt your data. Having contained Steam within LXD, do not minimize the browser window and be sure to exit Steam browser properly through its file menu by choosing "Exit".
[/LIST]
We can bypass Steam's browser and launch any game directly by adding the game ID when calling Steam. Example: the game ID for Sid Meier's Civilization 5 is 8930. The syntax for launching the game would be:
```
lxc exec steam -- sudo --login --user ubuntu /usr/games/steam -no-browser steam://rungameid/8930
```
If we don't want to tie up a terminal shell just to run this game, then (in vanilla Ubuntu) we can call up an app launcher with <Alt> + <F2> and paste this line into the command box. Creating a Civilization.desktop file with this Exec line is another alternative.

:!: **NOTE** :!:> Steam has a nasty flaw: it refuses to close properly. When the player exits a game, zombie processes are usually left running. Aside from eating up resources, they cause other hard-to-trace breakages like video corruption and audio glitches. They are like memory leaks by design. This is not an Ubuntu or LXD problem; it is entirely a function of poor Steam design. It plagues Steam installations even on bare metal installs.

After quitting a game, from your host:
```
duckhook@Zeus:~$ lxc exec steam -- sudo --user ubuntu ps -eF | grep [s]team
```
If you still see steam processes running when you know that all steam apps ought to be shut down:
```
duckhook@Zeus:~$ lxc exec steam -- sudo --user ubuntu killall steam
```
This should free up those resources and unhook audio/video from zombie Steam processes.

---

### Post by DuckHook on 2020-04-03
Let's say we want to run another full, separate 'buntu distro within a container. Assume that our host is running vanilla Ubuntu 22.04 and we want to create a Xubuntu container based on 23.04:
```
lxc launch ubuntu:23.04 --profile default --profile x11 xubuntu
```
Do our update and housekeeping:
```
ubuntu@xubuntu:~$ sudo apt update && sudo apt full-upgrade && sudo apt autoremove && sudo apt clean
```
Now prepare for a long download of the full Xubuntu desktop:
```
ubuntu@xubuntu:~$ sudo apt install xubuntu-desktop
```
Reboot:
```
ubuntu@xubuntu:~$ sudo reboot
```
It's almost too easy. After these simple steps, we have a working Xubuntu image. To bring up the Xubuntu desktop: <Alt> + <F2> &#8594;
```
lxc exec xubuntu -- sudo --login --user ubuntu xfce4-panel
```
But running two different desktop environments concurrently is a schizophrenic experience. Panels overlay each other, are unreadable and unreachable. Let's clean things up.

The lower Xubuntu XFCE panel should be at the bottom of your screen. Let's customize things so that only the bottom panel is used (it's really the only one we need):  Right click on it &#8594; Panel &#8594; Panel Preferences. If all panels are hidden such that the mouse can't reach them, then from a shell do:
```
ubuntu@xubuntu:~$ xfce4-settings-manager
```
&#8230;and select *Panels*. On my installation, the bottom panel is "Panel 2".

[list=1]
[*]First, under the "Display" tab, let's permit this panel to float by turning off *Lock panel*.
[*]Set *Automatically hide the panel* to "Never"
[*]Set *Mode* to suit your taste.
[*]Set *Row size, Number of rows* and *Length* to suit your taste.
[*]In the "Items" tab, click the "+" button and add either *Applications Menu* or *Whisker Menu* to the panel.
[/list]
Panel 2 is now configured with everything we really need and can be moved to anywhere on our desktop. Clicking on its Applications or Whisker menu allows us to choose any of the apps that come preinstalled with the Xubuntu desktop.

You may notice that Xubuntu's top panel is a faint ghostly presence hidden behind the Gnome panel and none of its features are reachable with the mouse. To deal with this:

[list]
[*]In Panel Preferences, switch to "Panel 1".
[*]We can either play around with the Display properties to put it where we want, or delete it altogether with the "-" button. I decided to delete mine because it was redundant.
[/list]
When we launch the XFCE panel, all that we are really doing is invoking a means to get at Xubuntu's apps. We're keeping our host Gnome environment for our desktop because we only want to deal with one DE.

It's pretty cool to effortlessly bring up newer versions of apps. Try launching the 23.04 version of GIMP and compare it to Jammy's. You can have both versions running at the same time because one belongs to the container and the other to the host.

:!: **Note** :!:
> Some apps won't work properly when launched from Xubuntu's panel menu (eg gnome-software). This may be due to permissions, ownerships, paths or some other obscure parameters. In such cases, the app may behave well if launched from a proper shell. Also remember that the container is not a real computer. System apps like power settings and display utilities will fail because the container is tightly jailed and cannot touch the host's resources&#8212;which is in fact what we desire. But it means that Xubuntu system apps will crash. We should not remove the apps because they may be integrated into Xubuntu. But if the presence of these useless menu launchers is distracting, eliminating them is left as an exercise for the reader.

:!: **Note** :!:
> We cannot log out of our Xubuntu instance the normal way, using the Logout menu entry in the Panel. Shutdown, Reboot and Logout are system calls and this is one of the ways in which a container is not like a VM. We have already established that a containerized instance is prohibited from accessing system resources. If it were allowed to, these system calls would shut down our host, not our container.

To close the XFCE panel, **right click** on it, then &#8594; Panel &#8594; Logout. We may get a message that closing the panel will also kill X, but it is safe to proceed. The message is referring to the container's X server, not the host's.

I hope this tutorial is sufficient to get us on the way to compartmentalizing many of our desktop apps. Used in conjunction with VMs it will hopefully add one more tool to our collection of security measures in our continuing battle with the bad guys.

Good Luck and Happy Ubuntu-ing!

---

### Post by DuckHook on 2020-04-11
***Pulseaudio Alternative:***

I've recently started playing with a beta Focal install.

Simos's proxy stack doesn't appear to work in Focal. At least, I can't get pulseaudio to map. Therefore, it was necessary to go back to [Simo's earlier stack]("https://blog.simos.info/how-to-easily-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/") which maps X and audio as disk devices. For reference, his stack is reproduced below:
```
config:
  environment.DISPLAY: :0
  raw.idmap: "both 1000 1000"
  user.user-data: |
    #cloud-config
    runcmd:
      - 'sed -i "s/; enable-shm = yes/enable-shm = no/g" /etc/pulse/client.conf'
      - 'echo export PULSE_SERVER=unix:/tmp/.pulse-native | tee --append /home/ubuntu/.profile'
    packages:
      - x11-apps
      - mesa-utils
      - pulseaudio
description: GUI LXD profile
devices:
  PASocket:
    path: /tmp/.pulse-native
    source: /run/user/1000/pulse/native
    type: disk
  X0:
    path: /tmp/.X11-unix/X0
    source: /tmp/.X11-unix/X0
    type: disk
  mygpu:
    type: gpu
name: gui
used_by:
```Note the main difference—*type: disk* instead of *type: proxy*.

Therefore, a better strategy may be as follows:

[list=1]
[*]Since X as a proxy appears to work without issues, create a pure x.profile:```
config:
  environment.DISPLAY: :0
  user.user-data: |
    #cloud-config
    packages:
      - x11-apps
      - mesa-utils
description: GUI LXD profile
devices:
  X0:
    bind: container
    connect: unix:@/tmp/.X11-unix/X0
    listen: unix:@/tmp/.X11-unix/X0
    security.gid: "1000"
    security.uid: "1000"
    type: proxy
  mygpu:
    type: gpu
name: x11
used_by: []
```
[*]Create the x profile:```
duckhook@Zeus:~$ lxc profile create x
duckhook@Zeus:~$ cat /bin/x.profile | tee lxc profile edit x
```
[*]Then create two different pulseaudio profiles, one of the proxy type (pa_proxy.profile) and the other as the disk type (pa_disk.profile):```
config:
  environment.PULSE_SERVER: unix:/home/ubuntu/.pulse-native
  user.user-data: |
    #cloud-config
    runcmd:
      - 'sed -i "s/; enable-shm = yes/enable-shm = no/g" /etc/pulse/client.conf'
    packages:
      - pulseaudio
description: pulseaudio proxy LXD profile
devices:
  PASocket1:
    bind: container
    connect: unix:/run/user/1000/pulse/native
    listen: unix:/home/ubuntu/.pulse-native
    security.gid: "1000"
    security.uid: "1000"
    uid: "1000"
    gid: "1000"
    mode: "0777"
    type: proxy
name: pa_proxy
used_by: []
``````
config:
  raw.idmap: "both 1000 1000"
  user.user-data: |
    #cloud-config
    runcmd:
      - 'sed -i "s/; enable-shm = yes/enable-shm = no/g" /etc/pulse/client.conf'
      - 'echo export PULSE_SERVER=unix:/tmp/.pulse-native | tee --append /home/ubuntu/.profile'
    packages:
      - pulseaudio
description: pulseaudio disk LXD profile
devices:
  PASocket:
    path: /tmp/.pulse-native
    source: /run/user/1000/pulse/native
    type: disk
name: pa_disk
used_by:
```
[*]```
duckhook@Zeus:~$ lxc profile create pa_proxy
duckhook@Zeus:~$ cat /bin/pa_proxy.profile | tee lxc profile edit pa_proxy
duckhook@Zeus:~$ lxc profile create pa_disk
duckhook@Zeus:~$ cat /bin/pa_disk.profile | tee lxc profile edit pa_disk
```
[*]Now we can just mix and match:
```
duckhook@Zeus:~$ lxc launch ubuntu:19.10 --profile default --profile x --profile pa_proxy test
```…or…```
duckhook@Zeus:~$ lxc launch ubuntu:19.10 --profile default --profile x --profile pa_disk test
```You may have to experiment to find the pulseaudio stack that works for you.[/list]


***White Screen of Death***

On some video cards (example: old nVidia GPUs), Chromium and browsers based on its Blink rendering engine will display only a white screen of death. The browser launches and the screen is indeed populated with fields and text, but nothing can be seen. Apparently, Blink makes use of X system calls on these cards that LXD does not pass through to the host. The only workaround that I've found is to force Chromium into a specific software rendering mode. It is not enough to disable gpu. One must specifically invoke the swiftshader rendering engine:```
chromium-browser --use-gl=swiftshader
```Firefox and derivatives don't appear to suffer from this problem.

---

### Post by DuckHook on 2020-04-11
***LXD on a ZFS-based Install***

Starting with Eoan and then with Focal, it is possible to install the host OS to a ZFS file system. But the ZFS file system takes up the whole disk. Therefore, running LXD on such a host involves a slightly different strategy.

In a default Focal install, a small pool called *bpool* is created for the boot directory and all files needed to boot. The rest of the disk is dedicated to OS and user data. Let's see what a typical ZFS install looks like:```
duckhook@Zeus:~$ sudo zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              170M  1.58G       96K  /boot
bpool/BOOT                                         169M  1.58G       96K  none
bpool/BOOT/ubuntu_mdulm6                           169M  1.58G     91.7M  /boot
rpool                                             3.70G   207G       96K  /
rpool/ROOT                                        3.69G   207G       96K  none
rpool/ROOT/ubuntu_mdulm6                          3.69G   207G     2.03G  /
rpool/ROOT/ubuntu_mdulm6/srv                        96K   207G       96K  /srv
rpool/ROOT/ubuntu_mdulm6/usr                       304K   207G       96K  /usr
rpool/ROOT/ubuntu_mdulm6/usr/local                 208K   207G      144K  /usr/local
rpool/ROOT/ubuntu_mdulm6/var                       610M   207G       96K  /var
rpool/ROOT/ubuntu_mdulm6/var/games                  96K   207G       96K  /var/games
rpool/ROOT/ubuntu_mdulm6/var/lib                   604M   207G      471M  /var/lib
rpool/ROOT/ubuntu_mdulm6/var/lib/AccountServices    96K   207G       96K  /var/lib/AccountServices
rpool/ROOT/ubuntu_mdulm6/var/lib/NetworkManager    220K   207G      132K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_mdulm6/var/lib/apt              89.9M   207G     34.2M  /var/lib/apt
rpool/ROOT/ubuntu_mdulm6/var/lib/dpkg             39.5M   207G     31.3M  /var/lib/dpkg
rpool/ROOT/ubuntu_mdulm6/var/log                  4.71M   207G     3.46M  /var/log
rpool/ROOT/ubuntu_mdulm6/var/mail                   96K   207G       96K  /var/mail
rpool/ROOT/ubuntu_mdulm6/var/snap                  112K   207G      112K  /var/snap
rpool/ROOT/ubuntu_mdulm6/var/spool                 200K   207G      120K  /var/spool
rpool/ROOT/ubuntu_mdulm6/var/www                    96K   207G       96K  /var/www
rpool/USERDATA                                    5.81M   207G       96K  /
rpool/USERDATA/duckhook_ief1eb                    5.61M   207G     3.50M  /home/duckhook
rpool/USERDATA/root_ief1eb                         104K   207G      104K  /root
```
Note that the bulk of the disk is assigned to *rpool*. What we want to do is define a dataset within *rpool* for LXD containers:
```
duckhook@Zeus:~$ sudo zfs create rpool/containers
```
Now we can proceed to initialize LXD in the usual way ([Setting up a ZFS pool]("https://ubuntuforums.org/showthread.php?t=2438709&p=13939384#post13939384")) but with the following change:```
duckhook@Zeus:~$ lxd init
…
Name of the existing ZFS pool or dataset: rpool/containers
…
```
The dataset assigned to LXD is unconstrained and will grow as needed. Once initialized, it will be owned by LXD and will no longer be visible to general users.



***Accessing the CDROM Drive***

Installing old games via the CDROM drive into a WINE container can be done the following way:

[list=1]
[*]Physically insert the game CD. Your system will likely automount it.
[*]We must unmount it from the host before we can pass the mount into the container```
duckhook@Zeus:~$ sudo umount /media/path/to/CD
```
[*]Now we can mount it within the container:```
duckhook@Zeus:~$ lxc config device add <container_name> cdrom disk readonly=true source=/dev/sr0 path=/media/cdrom
```
The syntax breaks down as follows:
[LIST]
[*]*lxc config device add* is obvious.
[*]*<container_name>* replace with the name of your container
[*]*cdrom* is the host label we assign to the device. You can name it anything you want.
[*]*disk* is the device type.
[*]*readonly=true* permits only read access.
[*]*source=/dev/sr0* self-explanatory
[*]*path=/media/cdrom* defines the mountpoint inside the container
[/LIST]
[/list]
We can now access the CDROM within the container. This can be done with DVDs and Blu-Rays too. Note that the container has exclusive unshared access to the drive and it becomes inaccessible to the host. Therefore, when finished with its use, we must release it from the container (make sure there are no container processes still dependent on it). Also, the container may refuse to start after a reboot if the CD that it is expecting has been ejected, which is another good reason to clean up properly. To unmount it:
```
duckhook@Zeus:~$ lxc config device remove <container_name> cdrom
```

Some might decide that it's better to just copy the CD's contents into some directory in the container, chmod that directory and all its contents to 555, then map that directory to some disk in winecfg and designate it as a CDROM. This is a viable strategy especially if the game requires a CD to run, but it can be space-intensive. In our world of cheap storage, this is less of a consideration.

---

