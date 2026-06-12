---
title: "virtual desktop delivery via remote server"
date: 2014-05-13
forum: Server Platforms
---

### Post by matt_fussell2 on 2014-05-13
I've known since shortly after starting with various flavors of *nix circa '04 that the OS is multi-user server environment. There remains a nagging issue that I just can't seem wrap my head around, and I'd like to solve it. Given that on effectively any virtual infrastructure (whether I own it or not) I can spin up this multi-user environment with relative ease and connect to it securely (as I can), and given that I can install and securely deliver applicaitons at no additional cost per application via ssh command line (which I can), why is complete, open delivery of a desktop environment such a pain? 

VDI solutions exist, but are nearly all geared towards Windows; this makes sense given that the Windows environment wasn't designed with multiple users in mind. Such tools that support linux exist, but are far less prevalent. Frustratingly, there exists a costpoint that far exaggerates the value delivered.

Furthermore, solutions seem to exist within the current scope of *nix OSs and Ubuntu specifically via LTSP, but when put into a public space (remote server), LTSP (to my knowledge) breaks down.

Getting to the question (this isn't a rant thread; I'm just frustrated because I haven't yet found a solution to this issue), is there a way to deliver a full desktop experience (sound, video, something skype-ish) via remote Ubuntu Server to a local Ubuntu client (I'll worry about other platforms later) that doesn't involve software costs?

Here's what I've tried so far:

Ubuntu 12.04 and Ubuntu 14.04 (desktop and server) using LXDE delivered via xrdp -> everything works wonderfully, except for sound.
Ubuntu 12.04 and Ubuntu 14.04 (desktop and server) gnome-session-fallback via freenx -> mixed results: 12.04 worked fairly well and I'm still working on that [video only, so far], 14.04 was a total bust: the only that works is an ssh prompt.
Ubuntu 12.04 and Ubuntu 14.04 (desktop) applications deliverd ssh + x -> works, except for sound
Ubuntu 12.04 and Ubuntu 14.04 (desktop) desktop delivered via xephyr -> remote screens blank

Any help is appreciated; I'll get back with the results of freenx on 12.04 as soon as possible - I'm working this in addition to administrating a windows network.

---

### Post by TheFu on 2014-05-13
Try **spice** over TLS. It may be limited to KVM-only VMs, I dunno. 

I still prefer FreeNX, but don't need video or audio.  Desktop productivity apps just work on 12.04 under FreeNX.   Don't have any 14.04 remote desktops yet - perhaps in a few months. No hurry here.

The XenServer VDI is probably the best of the solutions now, but it isn't free and I don't know if it does remote Linux desktops.

xdmp is worthless over the internet. It isn't secure.
ssh +X is too slow over most internet connections. I've tried.
ssh/openvpn + VNC ... er ... VNC basically sucks. VNC without a tunnel is non-secure.

[http://guac-dev.org/](http://guac-dev.org/) may be an option. HTML5, but I'd be concerned about using HTTPS for security now.

---

### Post by matt_fussell2 on 2014-05-13
> **TheFu said:**
> Try **spice** over TLS. It may be limited to KVM-only VMs, I dunno. 

I still prefer FreeNX, but don't need video or audio.  Desktop productivity apps just work on 12.04 under FreeNX.   Don't have any 14.04 remote desktops yet - perhaps in a few months. No hurry here.

The XenServer VDI is probably the best of the solutions now, but it isn't free and I don't know if it does remote Linux desktops.

xdmp is worthless over the internet. It isn't secure.
ssh +X is too slow over most internet connections. I've tried.
ssh/openvpn + VNC ... er ... VNC basically sucks. VNC without a tunnel is non-secure.

[http://guac-dev.org/](http://guac-dev.org/) may be an option. HTML5, but I'd be concerned about using HTTPS for security now.

Unfortunately, XenDesktop is [Windows only]("http://support.citrix.com/proddocs/topic/xendesktop-7/cds-sys-requirements.html"). I'll start looking into **spice** tomorrow as well as checking your other link. In your experience, can you achieve sound/video using FreeNX? I'm not opposed to further exploration if there is a payoff.

---

### Post by TheFu on 2014-05-13
> **matt_fussell2 said:**
> Unfortunately, XenDesktop is [Windows only]("http://support.citrix.com/proddocs/topic/xendesktop-7/cds-sys-requirements.html"). I'll start looking into **spice** tomorrow as well as checking your other link. In your experience, can you achieve sound/video using FreeNX? I'm not opposed to further exploration if there is a payoff.

I simply do not care about audio, so never tried to get it working. I actually find audio annoying. Sorry. Pulse audio does work remotely and if there is a VPN, that should solve it. Never outside a VPN.

The NoMachine NX server is another option. I've never attempted to use it - freeNX meets our small company requirements.

---

### Post by spynappels on 2014-05-14
Is the LTSP (Linux Terminal Server Project) sort of what you mean? Won't work truly remotely, but within an office environment it works well.

Or do you mean a completely distributed system, accessible from anywhere, so SSH to server and run desktop tunnelled through SSH connection type thing?

---

### Post by matt_fussell2 on 2014-05-14
> **TheFu said:**
> I simply do not care about audio, so never tried to get it working. I actually find audio annoying. Sorry. Pulse audio does work remotely and if there is a VPN, that should solve it. Never outside a VPN.

The NoMachine NX server is another option. I've never attempted to use it - freeNX meets our small company requirements.

I wish I had the option of skipping sound, but the directive I received was that it had to be a complete solution or nothing - otherwise I would have rolled out the xrdp solution. At any rate, thanks for the leads.

---

### Post by matt_fussell2 on 2014-05-14
> **spynappels said:**
> Is the LTSP (Linux Terminal Server Project) sort of what you mean? Won't work truly remotely, but within an office environment it works well.

Or do you mean a completely distributed system, accessible from anywhere, so SSH to server and run desktop tunnelled through SSH connection type thing?

Yes, I was referencing the Linux Terminal Server Project as a possible solution that I had explored - I have to service remote branches of our organization, so the PXE boot requirement nullifies LTSP. Effectively, what I've been called upon to deliver is XenDesktop/VMWare View experience but at a reduced cost point.

To answer your question, yes, I need something that is completely distributed and provides a complete user experience.

What would be great would be implementing something akin to LTSP but with the nodes able to connect from anywhere once the server is set up. I truly wish something as elegant as an option for such a connection would exist in the display manager, but that will have to wait for now.

---

### Post by TheFu on 2014-05-14
I believe the commercial NX server DOES audio and video. (confirmed)  How many users? It looks like $800 to get started, but users and CPUs used alter the licensing.  Heck, I'm temped to get the 10-pak just because it will solve some constant complaints by the non-technical people here.

I'd create 2-3 different budgets and let management choose by cost exactly how much audio/video is really worth. There is a huge price difference and for some video, addon packages will be desired, it seems.

While I'd rather donate to a F/LOSS project, supporting a mostly OSS team (even if commercial) is good too.

---

### Post by QIII on 2014-05-14
NoMachine does deliver audio and video ... BUT ... video is not good enough for watching your favorite action movie.

---

### Post by TheFu on 2014-05-14
> **QIII said:**
> NoMachine does deliver audio and video ... BUT ... video is not good enough for watching your favorite action movie.

Even with the h.264 client-side addon?

---

### Post by matt_fussell2 on 2014-05-14
> **TheFu said:**
> I believe the commercial NX server DOES audio and video. (confirmed)  How many users? It looks like $800 to get started, but users and CPUs used alter the licensing.  Heck, I'm temped to get the 10-pak just because it will solve some constant complaints by the non-technical people here.

I'd create 2-3 different budgets and let management choose by cost exactly how much audio/video is really worth. There is a huge price difference and for some video, addon packages will be desired, it seems.

While I'd rather donate to a F/LOSS project, supporting a mostly OSS team (even if commercial) is good too.

Right now the number of active users is less than 50, but we're also planning to scale.

---

### Post by QIII on 2014-05-15
> **TheFu said:**
> Even with the h.264 client-side addon?

Since ...

1.  fmpeg in the Ubuntu repos has moved to the libav fork
2.  installing ffmpeg can be dicey because both libav and ffmpeg periodically break backwards compatibility 
3.  NoMachine's H.264 addon doesn't seem to work with libav

... the H.264 addon is a headache on an Ubuntu client.

Let's just say I have been having disconcerting emotional events since Nomachine 4 was released.  I really, really want to NX to my Win 7 machine to watch content on Comcast's Xfinity, but each joy is followed by defeat shortly afterwards.

I haven't had the time or inclination to see how well it works on Fedora 20.  Sigh.

---

### Post by TheFu on 2014-05-15
> **QIII said:**
> Let's just say I have been having disconcerting emotional events since Nomachine 4 was released.  
Tried to get NM-v4 working with my server. Wouldn't work - and all the settings were "odd."  Decided to hoard v3.5.x programs.  There is always Remina, if I get desperate.

> **QIII said:**
>  I really, really want to NX to my Win 7 machine to watch content on Comcast's Xfinity, but each joy is followed by defeat shortly afterwards.

I dropped Comcast TV a few years ago when they encrypted more and more channels. The CSR didn't understand what I meant that my "TV" didn't work anymore.  "Cable Ready" used to mean it would work without they power-sucking extra boxes. Local OTA has 70+ channels, so it isn't like I'm missing anything important, though the Olympics coverage sucks without cable.  I'm pissed that I couldn't just pay them $80 for coverage without having them come to my home and screw with my TV setup first. Don't really care about any other popular sports here.  

Plus, I don't really use Windows directly, especially NOT for watching video (recording/editing, yes).  Windows use is mostly automated to limit my frustration. I don't understand how people can put up with all that point-n-click crap, day-after-day-after-day.  Do it once, then write a script for things that happen more than a few times. Strawberry Perl to the rescue on Windows.

The only remote desktop that I've heard can handle 720p from 1,000 miles away is from Citrix, but I suspect the people claiming that were running Windows desktops. They gave a talk at OuterZ0ne 2014 - video should be online ..... [http://www.outerz0ne.org/OZ10/](http://www.outerz0ne.org/OZ10/)   couldn't find the videos yet. IronGeek usually posts them once they are up.

---

### Post by matt_fussell2 on 2014-05-15
Have either of you worked with [Guacamole]("http://guac-dev.org/")? I have it installed following the instructions I located [here on the forums]("http://ubuntuforums.org/showthread.php?t=2183637"), but tomcat is reporting that the necessary guacamole.html does not exist. I replied to his thread, but checking his profile it doesn't seem that he is on more than once a week.

---

### Post by matt_fussell2 on 2014-05-29
Following the a solution from the [same link]("http://ubuntuforums.org/showthread.php?t=2183637") I mentioned above, with some slight additions and augmentations, [x2go]("http://wiki.x2go.org/doku.php") works beautifully. The [linked forum thread]("http://ubuntuforums.org/showthread.php?t=2183637") includes a nearly complete set of install instructions, with the gaps I found filled in with the replies I left on the thread. X2go works in Ubuntu 14.04 quite well. I'll post install scripts and configuration notes in the next few days.

---

### Post by TheFu on 2014-05-29
> **matt_fussell2 said:**
> Following the a solution from the [same link]("http://ubuntuforums.org/showthread.php?t=2183637") I mentioned above, with some slight additions and augmentations, [x2go]("http://wiki.x2go.org/doku.php") works beautifully. The [linked forum thread]("http://ubuntuforums.org/showthread.php?t=2183637") includes a nearly complete set of install instructions, with the gaps I found filled in with the replies I left on the thread. X2go works in Ubuntu 14.04 quite well. I'll post install scripts and configuration notes in the next few days.

Does x2go have any key-based encryption support?  I love that FreeNX uses 2-factor authentication (keys + passwords)

---

### Post by matt_fussell2 on 2014-05-29
> **TheFu said:**
> Does x2go have any key-based encryption support?  I love that FreeNX uses 2-factor authentication (keys + passwords)

The x2go configuration I'm using employs ssh to secure the connection and still requires password authentication by the individual user.

---

### Post by matt_fussell2 on 2014-06-02
As promised, it's time for scripts.

For the sake of simplicity, we'll assume fresh installs of both Ubuntu 14.04 server and Ubuntu 14.04 client - this setup has been successfully tested on these client/server versions. First things first - after you have installed Ubuntu Server, you'll need to install openssh and modify the sshd_config file. If you haven't done so already, you'll need to do the following:

```
sudo apt-get install openssh-server
```



Once the install is complete, you'll need to modify your sshd_config file - as always, you should create a backup of the file in the event that something gets broken.

```
sudo cp /etc/shh/sshd_config /etc/ssh/sshd_config.back
```

You will need to locate and change the following lines:

```
# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no
```

to

```
# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication yes
```

and

```
# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes
```

to

```
# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes
```



Once this is done, restart the ssh service:

```
sudo service sshd restart
```

If you're like me and this hasn't been working recently, the old-school method works as well.

```
sudo /etc/init.d/sshd restart
```



Once you've done that, you can use the install script to get things moving.

```
# This script assumes you have a fresh install of Ubuntu 14.04 Server.
# It will install the necessary software to run x2go.

# Add the x2go repository
sudo add-apt-repository ppa:x2go/stable -y

# Update the repositories
sudo apt-get update

# Add necessary software
# NOTE: add any additional software you want to install to this list.
sudo apt-get install -y lxde alsa pulseaudio paprefs x2goserver x2goserver-xsession

# Update the system and remove any unused packages
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get autoremove -y
sudo apt-get clean

# Put your username here:
user="myUserName"

# Add the administrative user to the x2go user group
sudo adduser $user x2gouser
```

On your client machine, run this script to install the x2go client:
```
# Install x2go PPA
sudo add-apt-repository ppa:x2go/stable
sudo apt-get update

# Install PAPrefs and the x2goclient
sudo apt-get install paprefs x2goclient
```

In order to login to your remote server, start the x2go program and put in the IP address (or URL if you have one) and your username. Make any other configuration changes that need to be done, and then go back to the tab with your username. Instead of selecting LXDE as the session type, select custom desktop. In the field next to this selector, insert the following string:

```
ck-launch-session startlxde
```



----
That pretty much sums it up - everything worked in my test setups, both on a local network and over the internet.
----

Successful connections were also made from varying Windows machines, and according to x2go's website, connections should be possible from Macs as well. The additional clients can be downloaded [here]("http://wiki.x2go.org/doku.php").

---

