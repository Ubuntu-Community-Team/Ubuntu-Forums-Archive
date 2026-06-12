---
title: "Does LTSP use the server to run programs and log in, or the client?"
date: 2009-12-09
forum: Server Platforms
---

### Post by Frogging101 on 2009-12-09
I have successfully set up an LTSP system with two machines (the server and a client), and can get to the GUI login. But, I cannot log in! This is what happens:

1. The client boots
2. The GUI login prompt is presented
3. I type my username and password
4. The client says 'Authentication Failure"

The username and password I use are the same as on the server. In other words, I have not created any users in the LTSP chroot (/opt/ltsp/i386) environment. That means that there is no home directory in /opt/ltsp/i386/home, but it is in /home on the server. I don't know if that is the correct thing to do. Am I supposed to create a user in the chroot?

When I create a user in the chroot environment, I can log in that way, but it doesn't appear to be using any resources on the server. If I look at the RAM in the system monitor, it says something around 3 GB of ram, and AMD Athlon processor cores. The server has 4 GB of ram, and AMD Phenom processor cores.

Also, on the client, if I look in the /tmp directory, there's a bunch of stuff. If I go to the server and look in the /opt/ltsp/i386/tmp directory, there is nothing there.

I thought that LTSP was supposed to use the server's CPU and RAM, and other resources.

What is going on here?

**UPDATE:**
I am getting closer. See my post (in this thread) here: [http://ubuntuforums.org/showthread.php?p=8517198#post8517198]("http://ubuntuforums.org/showthread.php?p=8517198#post8517198")

---

### Post by lykwydchykyn on 2009-12-09
It should work the way you're doing it, you shouldn't have to add any users to the chroot environment.

Essentially, the login manager (ldm) on the client is supposed to connect back to the server by tunneling X11 through ssh, so that your actual desktop is running on the server.  At least, that's my understanding of it.

Are you working with a more-or-less default setup at this point, or did you modify a lot of things troubleshooting the last error?

---

### Post by Frogging101 on 2009-12-10
As far as I know, I have modified the following relevant files (since discovering LTSP):

**IN THE CHROOT:**

initramfs.conf
ltsp_client_setup

**ON THE SERVER:**
/etc/nbd-server/config
dhcpd.conf
/..../pxelinux.cfg/default
lts.conf

Also, prior to even knowing about LTSP, I set up an ssh server so I could access the terminal through the internet. This server was openssh. I am saying this just in case it is relevant. And also, I did run ltsp-update-sshkeys, it returned no output but when I looked at ssh_known_hosts, it had my IP and all that. 

And by the way, the original problem was NOT that the dhcpd.conf did not point to the right place, because I had edited when switching between architectures.

---

### Post by Frogging101 on 2009-12-10
Bump.

---

### Post by Frogging101 on 2009-12-10
Here are all my config files that I mentioned. (ATTACHED)

---

### Post by lykwydchykyn on 2009-12-10
Looking it over, nothing jumps out at me as wrong.  Have you edited the ssh server settings at all?

I did notice the initramfs.conf is set to boot to nfs root, but I'm not sure if that's just an old setting or not.  Did you change that or was it that way (either way, if it were wrong I'd think it'd just stop you from booting).

Does /var/log/auth.log have any more info to offer on your failed logins?

---

### Post by nobrac on 2009-12-10
You shouldn't have to do much manual configuration to get LTSP working. In the PXE boot process the thin clients send a broadcast request for a an IP address and a boot image, which the LTSP server provides. Generally everything runs on the server. So, you have to make the user accounts on the server, not in the thin client image.

If you have problems more serious than creating user accounts on the LTSP server, it might be easiest to rebuild the boot image following the LTSP quick start document: 
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

Once ltsp-server-standalone and openssh-server are installed, do the following:
sudo ltsp-build-client
sudo ltsp-update-sshkeys
sudo ltsp-update-image

---

### Post by Frogging101 on 2009-12-11
I wish it was that simple, nobrac. I tried doing simply that, and I had all these problems. I haven't changed much about the ssh server... but I don't remember. Maybe I should just try reinstalling that. Right now I am at school, with an ssh connection to my desktop. Here are some relevant lines from /var/log/auth.log:

```

Dec 10 17:02:22 192.168.3.101 kerrighednode1 gdm-session-worker[3452]: PAM adding faulty module: /lib/security/pam_gnome_keyring.so
Dec 10 17:02:27 192.168.3.101 kerrighednode1 gdm-session-worker[3452]: pam_unix(gdm:auth): check pass; user unknown
Dec 10 17:02:32 192.168.3.101 kerrighednode1 gdm-session-worker[3452]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 
```

It says nothing after logname= or ruser= or the other ones, but I didn't remove them for security. That is the exact output of /var/log/auth.log . My complete auth.log is attached.

---

### Post by Frogging101 on 2009-12-11
Also, it seems that an image is mounted in /rofs on the client. If I make a new file in /opt/ltsp/i386 on the server, it doesn't show up there unless I do sudo ltsp-update-image on the server, and then reboot the client. There also seems to be some kind of seperate filesystem on the client in /, that isn't linked to anything. I don't know where it is stored, or where it comes from.

---

### Post by lykwydchykyn on 2009-12-11
can you check that libpam-gnome-keyring is installed on the server?

---

### Post by Frogging101 on 2009-12-11
I checked, and yes, it is installed.

---

### Post by lykwydchykyn on 2009-12-11
> **Frogging101 said:**
> Also, it seems that an image is mounted in /rofs on the client. If I make a new file in /opt/ltsp/i386 on the server, it doesn't show up there unless I do sudo ltsp-update-image on the server, and then reboot the client. There also seems to be some kind of seperate filesystem on the client in /, that isn't linked to anything. I don't know where it is stored, or where it comes from.

That all sounds correct.  /opt/ltsp/i386 is not mounted by the client in NBD mode; rather, it's the chroot filesystem used to generate the boot image (which is done when you run ltsp-update-image).  You change what you like in it, then create a new image for the client to download.

/rofs I assume stands for read-only filesystem, everything else will exist in RAM.

I wish I could give you some more ideas about what is preventing you from logging in.  I'm not sure what else to check, but if I think of it, I'll drop in and mention it.

---

### Post by Frogging101 on 2009-12-11
I am using wireshark to monitor network traffic, and I don't see ANY packets that have anything to do with SSH. Maybe that suggests a problem?

---

### Post by Frogging101 on 2009-12-11
Also, at one point when I was trying to make this work, I managed to get to a login screen, but the mouse and keyboard didn't work. That login screen looked different than the one I have now. It was white with a line of 'paint' close to the left. The login screen I get now is the regular 9.10 login screen.

Just posting this in case it makes a difference.

---

### Post by Frogging101 on 2009-12-14
bump...

---

### Post by Frogging101 on 2009-12-17
bump -_-

---

### Post by Frogging101 on 2009-12-17
I have gotten further! Now, it boots to a GUI login, with a 'paint splattered' background. Great. When I enter my username and password, it says "Verifying Password", and then goes to a blank screen. It sits at this screen for a minute or two, and then goes back to the login screen asking for my username. No error message on the client, not even "Authentication failure".

Meanwhile, I am monitoring network traffic with Wireshark. I see some ssh packets (which is also a step forward), and nothing seems amiss (no auth errors, etc.). Then, I see some traffic on its way to the syslog. This traffic contains kernel errors regarding NBD. Here is some data from some of the packets:

```
Dec 17 13:04:38 kerrighednode1 kernel: [  395.946762]  nbd9: unknown partition table
Dec 17 13:04:38 kerrighednode1 kernel: [  395.954806] nbd9: NBD_DISCONNECT

[some cisco-sccp packets]

Dec 17 13:04:42 kerrighednode1 kernel: [  399.984604] nbd9: Receive control failed (result -32)
Dec 17 13:04:42 kerrighednode1 kernel: [  399.984665] nbd9: queue cleared
```

If you NEED more info, then PM me for the tcpdump. Only do that as a last resort, as I want to avoid giving possibly private info (passwords, etc.) over the internet.

---

### Post by Frogging101 on 2009-12-18
Bump.

---

### Post by lykwydchykyn on 2009-12-18
I'm not really sure what would cause this; honestly, the times I've set up LTSP 5 it's been pretty straightforward and worked out-of-the-box.

Are you using the default client image, or have you modified it in some way?

Can you post the contents of ~/.xsession-errors for the user that you're logging in as?  (this would be on the server).

Have you tried a different crossover cable?

---

### Post by AlexanderDGreat on 2009-12-18
If you're having trouble, try these guys out, irc.freenode.net, #ltsp. They're really helpful.

---

### Post by Frogging101 on 2009-12-18
> **lykwydchykyn said:**
> I'm not really sure what would cause this; honestly, the times I've set up LTSP 5 it's been pretty straightforward and worked out-of-the-box.

Are you using the default client image, or have you modified it in some way?

Can you post the contents of ~/.xsession-errors for the user that you're logging in as?  (this would be on the server).

Have you tried a different crossover cable?

I created a new xsession-errors, and booted the ltsp client. This is what is now in the file:

```
Xsession: X session started for john at Fri Dec 18 12:59:38 EST 2009
xrdb: Resource temporarily unavailable
xrdb: Can't open display 'localhost:11.0'
xhost:  unable to open display "localhost:11.0"
/etc/X11/Xsession.d/80_ltsp-sound: 7: /usr/bin/asoundconf: not found
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

** (x-session-manager:16267): WARNING **: Cannot open display: 
```

Cannot open display? Hmm...

---

### Post by Frogging101 on 2009-12-18
YES!!!!!

It works. After reading "Resource temporarily unavailable" over and over about ten times, I got an idea.

On my server, I was already logged in as 'john'. Maybe that caused a conflict (can't log in on the same user in two places). So, I created an account called 'test', and used that.

**AND IT WORKED!!!**

Due to the lack of recent and relevant documentation on the subject of LTSP 5, I will be submitting a guide on how to do this.

---

### Post by AlexanderDGreat on 2009-12-19
Good for you then! :)

---

### Post by Frogging101 on 2009-12-20
Crap. New problem. The keyboard response time on the client is HORRIBLE. everything else is fast, I can even play videos on the client. What is wrong?

---

### Post by felixvah on 2009-12-30
I'm trying to setup thinclient server, but I did not find any information on how to.  Can you provide some information on how you done it?  I followed the follwing website, but I did not get the option Install an LTSP server?
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall). 

I did hit F4 but that option isn't there.  What did I do wrong?

---

### Post by lykwydchykyn on 2009-12-30
> **felixvah said:**
> I'm trying to setup thinclient server, but I did not find any information on how to.  Can you provide some information on how you done it?  I followed the follwing website, but I did not get the option Install an LTSP server?
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall). 

I did hit F4 but that option isn't there.  What did I do wrong?

Are you using the alternate CD?

Even if you aren't, you can just go ahead and install Ubuntu, then install the "ltsp-server-standalone" package after install.  It should amount to the same thing.

---

### Post by felixvah on 2010-01-14
I have my thin client up and running by following this link: [http://www.youtube.com/watch?v=8yD0QV_Cm2w](http://www.youtube.com/watch?v=8yD0QV_Cm2w).

my problem is I can't get the client to login automatically and I can't find anything on the web related to Ubuntu 9.10 thin client.  If you got the answer please share it with me. thank you.

---

### Post by felixvah on 2010-01-14
thanks got to work now.. need to get the clien to log on automatically now.. any suggestion?  Ubuntu 9.10

---

### Post by lykwydchykyn on 2010-01-14
see this page: [http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/customizing-thin-client.html](http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/customizing-thin-client.html)

Scroll down about a third of the way to the section called "auto login features".

I haven't tried this with karmic, but I set it up a while back and it worked fine.

---

### Post by felixvah on 2010-01-14
it didn't work for me.  Did I do any thing wrong?  Here's what I have on the lts.conf file:

# This is the default lts.conf file for ltsp 5.
# For more information about valid options please see:
# /usr/share/doc/ltsp-client/examples/lts-parameters.txt.gz
# in the client environment.
#
# Note that things like sound and local device support are
# auto-enabled if the corresponding packages are installed,
# there is no need to manually set these options anymore.
#
# **** THIS FILE SHOULD NO LONGER BE USED FROM HERE !!! ****
#
# With the introduction of the nbd/unionfs/squashfs structure
# the lts.conf file moved to the tftp root please create:
# /var/lib/tftpboot/ltsp/i386/lts.conf instead for your changes
#
# In case you want to use the lts.conf here, this still works,
# but you need to run ltsp-update-image after every change.
[example]
key=value

[Default]
LDM_AUTOLOGIN = True

[192.168.110.2]
[00:11:43:B5:4C:CC]
LDM_USERNAME=public
LDM_PASSWORD=password
LDM_SERVER = 192.168.110.19

---

### Post by Boris TT on 2010-08-22
Thank u felixvah :) this solution works pretty well for me

---

