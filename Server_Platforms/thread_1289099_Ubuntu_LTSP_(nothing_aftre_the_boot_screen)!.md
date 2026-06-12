---
title: "Ubuntu LTSP (nothing aftre the boot screen)!"
date: 2009-10-12
forum: Server Platforms
---

### Post by Data-Base on 2009-10-12
Hello,

I managed to test Ubuntu LTSP 64 bit, the installation went OK so far!

I created a 32Bit client

```
sudo ltsp-build-client --arch i386
```

I configured our DHCP Server (Juniper NetScreen 25) to help our diskless clients boot from Ubuntu LTSP Server and worked some how.

BUT I get just a black screen with the white pointer blinking on the upper-left corner!

the client starts OK, shows the Boot screen for Ubuntu (With the logo and the progress bar) then it goes to the black screen!

any one know what can make this? and how to solve it?

---

### Post by epsolon77 on 2009-10-12
> **Data-Base said:**
> Hello,

I managed to test Ubuntu LTSP 64 bit, the installation went OK so far!

I created a 32Bit client

```
sudo ltsp-build-client --arch i386
```

I configured our DHCP Server (Juniper NetScreen 25) to help our diskless clients boot from Ubuntu LTSP Server and worked some how.

BUT I get just a black screen with the white pointer blinking on the upper-left corner!

the client starts OK, shows the Boot screen for Ubuntu (With the logo and the progress bar) then it goes to the black screen!

any one know what can make this? and how to solve it?

I installed a LTSP "server" about a year ago as a test bed.  If memory servers I had a similar issue involving desperate video cards.  There was a driver error involving display properties and I had to create a line in the X-server's config for the video.  I hope this takes you in the correct direction.  Sorry my memory is so sketchy at the moment.

---

### Post by epsolon77 on 2009-10-12
I found some notes from my testing.

Try running the liveCD of whatever your server is on your client to make sure the hardware is compatible with ubuntu first (trust me, this eliminates a ton of questions and work down the road).

Assuming this work you will need to create a custom config in //opt/ltsp/i386/lts.conf and then run ltsp-update-image.  I wish I could help you create a custom x11 script, but at that I know very little.  I think I actually installed ubuntu on the thin client and copied the X11 perams.

---

### Post by Data-Base on 2009-10-12
Thanks allot

in that case I got 2 questions, I'm testing the LTSP, I run it under vmware! do you think that may cause the problem?

the server is in text-mode no GUI
do I need to have GUI installed?


cheers

---

### Post by epsolon77 on 2009-10-12
Installing LTSP should not be a problem in VMWARE, assuming you have it configured to the network requirements LTSP has.  I have not tried to run LTSP in a virtual environment though.  I have always run LTSP with two NIC's on separate LAN's.  

Your LTSP server must have a GUI if you want your client to have a GUI.  Remember that your remote clients are booting in to view what is on your server through X11.  If you do not have an xserver and gui, there is nothing to sign in to.  

I personally recommend you just install your OS straight off the Ubuntu Alternate CD of your choice.  When the installer asks if you would like to install, just hit f4 and select install LTSP.  This way you know the server is set up correctly.

---

### Post by Data-Base on 2009-10-13
Thanks allot,

here what I did

I installed Ubuntu Server Core Only then

[LIST=1]
[*]Install SSHd
[*]Set Static IP address
[*]Install LTSP
[*]Uninstall the DHCP Server
[*]Build the Thin Client Image
[*]Configure our DHCP Server (Juniper NetScreen-25)
[/LIST]

while installing the LTSP I saw it downloaded some Xserver stuff and other GUI things

any way I will do as you recommended
but which version of Ubuntu Alternate CD I should use? 8.04/8.10/9.04 ?

cheers

---

### Post by epsolon77 on 2009-10-13
> **Data-Base said:**
> Thanks allot,

here what I did

I installed Ubuntu Server Core Only then

[LIST=1]
[*]Install SSHd
[*]Set Static IP address
[*]Install LTSP
[*]Uninstall the DHCP Server
[*]Build the Thin Client Image
[*]Configure our DHCP Server (Juniper NetScreen-25)
[/LIST]

while installing the LTSP I saw it downloaded some Xserver stuff and other GUI things

any way I will do as you recommended
but which version of Ubuntu Alternate CD I should use? 8.04/8.10/9.04 ?

cheers

Any will work, I have been enjoying 9.04 quite a bit lately.

Just to clarify, there maybe a way to have your server running at the CLI and still boot your thin clients to a GUI, I just don't know how.  I do, however, know that the alternate CD's work.  I just don't want anyone to think that there isn't a way, there could be, I just don't know what it is if it exists.  The server install on 9.04 is barely taxing my pathetic little P4 with a 1GB of ram with three clients booted into it, so I wouldn't be worried about the extra overhead too much.

---

### Post by epsolon77 on 2009-10-13
Another similar thread had some great resource material I wanted to share.

> **AlexanderDGreat said:**
> @epsolon7 - Hi, I found this, [www.ltsp.org/~sbalneav/LTSPManual.pdf](www.ltsp.org/~sbalneav/LTSPManual.pdf)

Do all configs in this manual pertain to lts.conf? Haven't read the whole thing yet, but it sure will be handy in the future.

I'm new to localapps but here's the link: [https://help.ubuntu.com/community/UbuntuLTSP/LTSPLocalAppsJaunty](https://help.ubuntu.com/community/UbuntuLTSP/LTSPLocalAppsJaunty)

[http://ubuntuforums.org/showthread.php?p=8097850#post8097850](http://ubuntuforums.org/showthread.php?p=8097850#post8097850)

---

