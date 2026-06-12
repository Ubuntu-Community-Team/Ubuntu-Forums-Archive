---
title: "LTSP client refuses to logon."
date: 2006-07-24
forum: Server Platforms
---

### Post by secunda007 on 2006-07-24
I recently setup LTSP(-server-standalone) on my Ubuntu 6.06 Server, using an Edubuntu 6.06 installation CD for the ltsp-build-client files. However, when I try to boot the client PC, the logon screen appears, but I cannot login to my account (the screen clears and refreshes itself, and returns to the logon screen). Any solutions? Thanks.

---

### Post by apjone on 2006-07-24
check you can login remotely using XDMCP, try resseting your password, remember root probably will not login remotely

---

### Post by secunda007 on 2006-07-24
I've tried to login via the terminal screen (tty1) on the thin client PC, but it keeps saying "login incorrect," even though the user/password I enter is correct. The user/password that I am trying to use to login to the thin client PC is the same user/password that I use to login to my server. Do I have to add separate LTSP users to the server?

---

### Post by bpdoyle@gmail.com on 2006-07-25
I am having the same login problems.  I started out using the breezy edubuntu release, and wasn't able to get anywhere.  So know I went and got the dapper release hoping for better luck, but still can only get to the same point.  I am use PXE boot though I did not build a set of client boot files.  

I get the client to boot up to the graphical login just fine.  But from that point on it acts like it doesn't see the server.  I have tried adding users, using the default user I created during my install.  I have gone into the gdmsetup and under the remote tab set it to the same as local. Under the security tab I even tried unchecking 'deny tcp connections to X Server' and checking 'allow remote system administrator login'.  I have also tried setting up NAT thinking maybe the client just needed to hit the internet for something.  I tried updating the thin-client NFS root.  I also tried creating a lts.conf from the default options listed on the edubuntu site.

I am pretty confused at this point, and have not be able to get a user to login through the thin client at this point.  And everything I read seems to say it just works out of the box.

Any help would be appreciated.

---

### Post by bpdoyle@gmail.com on 2006-07-25
ok I finally figured out my problem.  I am not sure if is the same as your problem afterall, but figured I would post the info just incase.

I found the info in the [https://help.ubuntu.com/community/HowToCookEdubuntu/Chapters/LTSPManagement?highlight=%28howtocookedubuntu%2Fchapters%29](https://help.ubuntu.com/community/HowToCookEdubuntu/Chapters/LTSPManagement?highlight=%28howtocookedubuntu%2Fchapters%29)
webpage.

It was related to changing the IP address of the server.  If you look at the bottom section of that page it talks about what you need to do if you change the server ip address.

You have to run
sudo ltsp-update-sshkeys

You should see output similar to the following, and your clients will now be able to log in again.

pete@edubuntu:~$ sudo ltsp-update-sshkeys
# Creating dsa-hostkey for edubuntu
# Creating rsa-hostkey for edubuntu
# Creating dsa-hostkey for 172.29.103.77
# Creating rsa-hostkey for 172.29.103.77

In my case I was installing edubuntu with two NICs, and only setting up the  outside NIC during the install.  Then going in a configuring the inside NIC for the thin clients to connect to.  Since the edubuntu LTSP is running through SSH to be more secure you have to update the keys for your NICs after you make any changes to them I am guessing.  Could be wrong, but from what I did that is my best guess ( I am still a n00b though ).

Hope this helps!

---

### Post by OMRebel on 2006-07-25
How did you get the client to even connect to the server?  It looks like it can't find the image.  My server is handing the client an IP address, but that's as far as it's getting.  

Loading 192.168.0.1:/ltsp/pxelinux.0 ..error: not a valid image
Unable to load file

---

### Post by bpdoyle@gmail.com on 2006-07-27
sounds like your ltsp root is either not there, has a different location than your /etc/ltsp/dhcpd3.conf file specifies, or is corrupted.  But I am pretty new to this myself.
And you are doing this off an Ubuntu system right?  I am using the edubuntu OS, so my LTSP was builtin when I installed the OS.

Check out your /etc/ltsp/dhcpd3.conf and verify the path of the root.  Then go check out that path.  If the root for ltsp is all there and your dhcpd3.conf is pointing to the right place, I am thinking you need to re-install your LTSP root.

Here is my dhcpd3.conf file:

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.20 192.168.0.250;
  option domain-name "example.com";
  option domain-name-servers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  option routers 192.168.0.1;
  option subnet-mask 255.255.255.0;

  filename "/ltsp/pxelinux.0";
  option root-path "/opt/ltsp/i386";
}

I didn't even edit it this time.  I just took the default setup that was builtin.  I set my internal IP to 192.168.0.1 so I wouldn't have to edit anything this time.

The root-path should exist.  When you go into /opt/ltsp/i386 you should be able to browse around the ltsp root, and the structure should just like your basic root structure of any linux system.

Hope this helps.

---

### Post by OMRebel on 2006-07-27
Thanks for your reply.  Problem turned out to be the rom image I was using.  For some reason that image worked with a K12 LTSP, but not with Edubuntu.  I created a different image, and it worked. :p

---

### Post by Kalif on 2006-10-31
Hi!

it seems like there can be several problems with the ldm
not logging the user properly into the system.
Setting up the server's host key is important as a previous
post has pointed out.

Since I have been using LTSP with UBUNTU for almost a
year now, there has been a few stones to stumble upon
my path](*,) 

Frankly speaking, I have never been able to log on using
ldm. To me it is *NOT* an issue about wrong host keys,
and before Edgy Eft, a "LOCAL_APPS=N" in lts.conf fixed
the problem (using XDMCP instead of the secure SSH
protocol). With Edgy Eft, my local keyboard and mouse
is dead when connecting to a remote gdm.
Hence I am also trying to work things out using the
official ldm way. Looking into the ssh-log on the
server reveals that the password used for authentication
is wrong. How wrong can it be when I can use it for
all other authentication purposes except ldm?!  :confused: 

Anyone got a clue?

Best,
K.

---

### Post by fnjordy on 2006-10-31
> **Kalif said:**
> Hi!
Looking into the ssh-log on the
server reveals that the password used for authentication
is wrong. How wrong can it be when I can use it for
all other authentication purposes except ldm?!  :confused: 

Try logging in to the server via SSH from the server and from the client on a different VT.  You might see a different error message on the console.

---

### Post by Kalif on 2006-11-02
Thanks fnjordy,
but I resolved the problem myself yesterday, sorry for
not posting my success story here. 8-)

My first guess was that since I had never been able
to log on by using ldm before, maybe the account
I was using (yes, I am using a sand-box account for
this kind of purposes not to mess up my production
environment), so I changed the password on the
account and -Bingo!- I could log on using ldm.
Then I changed the password back and I got locked
out again....

It turned out that I had some parameters in my
PAM-configuration that required passwords longer
than 6 letters which I think is good for anything
but sandboxing :-)

Hence problem solved,
K.

---

### Post by jonas_larson on 2008-03-29
Hi all,

The problem for me wasn't the ssh keys (created root password, logged in through ssh -l <username>  <ip-address> without any problem.

If I choosed another session (in ldm) other then default it worked...

Choosing "gnome-session" worked like a charm for me.

Best of luck

Jonas

---

