---
title: "ltsp-build-client error"
date: 2008-03-30
forum: Server Platforms
---

### Post by bitmonkeyagi on 2008-03-30
ok...I'm this close to being where I want to be, I'm sure.  I'm installing ltsp using Edubuntu 7.10.  I've got the server up, and the thin clients are connecting via pxe.  everything worked - once - last night.  today, for whatever reason, nothing worked.  A small child may have been involved, but I don't know.  I struggled all day yesterday (scratch that, it's now day-before-yesterday...) and finally got everything to work, using this thread: ([http://ubuntuforums.org/archive/index.php/t-465021.html](http://ubuntuforums.org/archive/index.php/t-465021.html))  

During that process, when I ran: sudo ltsp-build-client --arch i386, I kept getting an error that said:

"Note: adding default dist and components to security mirror:
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy main restricted
Note: Root Directory /opt/ltsp/i386 already exists, this will lead to problems, please remove it before trying again.  Exiting
error: LTDP client installation ended abnormally"

So...as I said, I kept getting this error.  I wish I could document what changed, but at one point, (I think I rebooted and went back to terminal), anyway, suddenly it actually did something, I can only presume it built a client list.  Took a long time to do, too.  and then everything worked - I could log in with the client, etc.  (well, there was the issue of no gui, but I think I know what happened there).  There was Great Joy amongst the peasants.

So I came in to the comp room this morning, with evidence that a small child had become involved, and it didn't work (logging in from the thin client, that is).  something about a pxe-t01 error.  I uninstalled ltsp, id all sorts of undocumented, ill-advised, and probably morally bereft activities to get things back.  Ifound info, made changes, reinstalled ltsp, worked through the pxe error.  but again, as yesterday, I couldn't get the "build client" stage to actually work.  what it says is true, that directory IS there.  I cleared it out using "rm -rf /opt/ltsp, and reinstalled, but in using the steps in the above-mentioned thread, I keep getting the same results - error.

So...I'm reasonably confident that my login problems are because the ltsp-build-client process hasn't run, but I don't know why it won't.  I need to get this issue resolved by Tuesday - I'm supposed to be teaching a class on these comps by then.  Any help is GREATLY appreciated.

---

### Post by bitmonkeyagi on 2008-03-30
Alright...after knocking my head against the wall all day and all night, and reading over and over how easy it is to set this up, I guess I must be the dumbest rock in the box.  Nonetheless...forget the ltsp-build-client error thing.  I just couldn't figure it out.   let's start over.

As we speak, I have Edubuntu server software installing on the main server computer of my system.  I formatted the drive, and I expect in about 15 minutes the initial install will be done, and I'll set the thing to doing the inevitable initial updates.  It's an AMD 2400 with 512M of RAM and a 40G hard drive.  I'm using two NICs, eth1 connects to the outside world, using DHCP through my DSL, eth0 is going to be the ltsp-server connection, at static IP 192.168.0.1.  Later I'm going to upgrade, but I just want to get this thing started.  For now, I have two pentiumIII boxes that will be thin clients.  They both have hard drives, but the cdroms in them won't read the edubuntu install disk, and for whatever reason the 3 dozen floppy disks I have lying around won't work.  maybe because they spent 3 winters in the garage, and at least 5 years since I used them last.  And I'm too lazy/cheap to go to the store and buy more.  so...thin client.  The NIC cards are both willing and able to load via PXE, and in fact get me to the point of wanting to log in to the system, so I feel good about them.  So in review:


- One freshly installed Edubuntu server 7.10 - no custom settings, just the automatic updates after loading. (that's not even done yet, but it will be soon...
- two thin client comps just waiting to feel the love.
- one apparently-clueless keyboardist.
- 5,645,361 internet claims that this ltsp setup should be drop-dead simple

Can anyone help from here?  I keep feeling that all the advice I see either starts somewhere further down the line than the beginning, or that I'm trying to apply the wrong technique to the wrong thing.

---

### Post by bitmonkeyagi on 2008-03-31
since I know all 31 or so of you are just hanging on the edge of your chairs waiting for an update...and I like to keep conversation going, even if it's just with myself, here's an update:

after the aforementioned installation, updates, etc., I have done the following:

-  using this website, ([http://yogharp.wordpress.com/2007/03/01/class-room-ltsp-with-edubuntu/](http://yogharp.wordpress.com/2007/03/01/class-room-ltsp-with-edubuntu/))
I performed the alteration of the dhcp.conf file, except that I realized that in my system this file was called dhcpd.conf.  It now reads as follows:
  
#
# thinmonkey LTDP dhcpd.conf config file
#

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
     range 192.168.0.20 192.168.0.250;
     option domain-name "thinmonkey.com";
     option domain-name-servers 192.168.0.1;
     option broadcast-address 192.168.0.255;
     option routers 192.168.0.1;
#  next-server 192.168.0.254;
#  get-lease-hostnames true;
     option subnet-mask 255.255.255.0;
     option root-path "/opt/ltsp/i386";
     if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
          filename " /ltsp/i386/pxelinux.0";
     } else {
          filename "/ltsp/i386/nbi.img";
     }
}

I'd love to hear the breakdown of what's going on here.  At any rate, so that's the dhcpd.conf file.  

- step 2 was to "sudo /etc/init.d/dhcp start" which I had to substitute with, "sudo /etc/init.d/dhcp3-server restart" which was taken from another thread, mentioned in my first post above.  The claim appears to have been that I should be living in the Promised Land at this point.  and yet...I find myself at the diametric counterpole.

- step 3:  taking matters into my own hands, I attempted to run the ltsp build client again, and again, as follows:

sudo ltsp-build-client --arch i386

I still get an error that says:

"Note: adding default dist and components to security mirror:
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy main restricted
Note: Root Directory /opt/ltsp/i386 already exists, this will lead to problems, please remove it before trying again. Exiting
error: LTDP client installation ended abnormally"

so I went back to the thread by manway ( [http://ubuntuforums.org/archive/index.php/t-465021.html](http://ubuntuforums.org/archive/index.php/t-465021.html))
and made my /etc/network/hosts file look like this:

gedit /etc/network/hosts

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.20 192.168.0.235;
option domain-name "thinmonkey.com";
option domain-name-servers 192.168.0.1;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
option subnet-mask 255.255.255.0;

filename "/ltsp/pxelinux.0";
option root-path "/opt/ltsp/i386";

You'll note the domain-name, and the upper range (235) are different than the example.
}


I then went on to copy steps 5,6,and 7. 
step 5:  I used "thinmonkey" instead of "HCSU", because I thought HCSU was something peculiar to his example, and not mine.  
step 6: the first part tells me it's already installed
            the second step gives me the same error mentioned before
            the third step doesn't appear to do anything - just goes on to the next cursor line, without returning any info.  maybe normal, maybe not...
Now...having done all that, one thing is different on the thin client.  before this, when it first accepted the concept of getting dhcp, there was a line at the top that said "client ip: 192.168.0.250 mask: 255.255.255.0 DHCP IP: 192.168.0.254.  it nows ends in 192.168.0.1.  this appears to be due to adding the etc/network/hosts file.  but note that in that file I specified .235 as the high end of the range, but I'm still getting a .250 client ip range.

At this point, the thin client gets its address, attempts to find pxelinux, but it can't.  I did something before  (meaning before I uninstalled and reinstalled) that let it find the pxelinux.0 file.   

I edit the /etc/ltsp/dhcp3.conf file, changing the upper range limit to 192.168.0.235, save, restart, and now booting the thinclient gets the new, limited address, and goes through the edubuntu splash and on to a login screen again (after a quick ctrl-alt-f1).  Hurray for me, I'm back where I started!

I attempt to log in with the same user name as what I log in to the server comp (format: "plain username", "password for that username".  it says the login is incorrect, and waits for me to try again.  Am I supposed to add something pertaining to the server's name?  I tried, it didn't work.  

Oh...did I mention I installed Wireshark?  I did.  And I used it to open up a session to capture what goes through eth0 upon login.  the very first line when I try to log in says, in the info column: "Authpriv.warning: login(3513): pam_unix(login:auth): check pass; user unknown\n

Ok...I must rest now.  otherwise I will hurt someone or something.  Please...if you have any info, please share.  I've absolutely got to get this thing up by Tuesday...  And if you find these flailings of mine entertaining, let me know, too.  I'm probably missing the biggest, most obvious thing in the world...

---

### Post by likuidkewl on 2008-04-01
I realize it is Tuesday but hopefully these links will help:
Also remove Sabayon if installed this causes similar problems to the clients not logging in due to the fact that Sabayon wants every user to have sabayon profile and it is a pain in the ****....
Oh, and make sure you are not running 2 dhcp servers

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)
[https://lists.ubuntu.com/archives/edubuntu-users/2007-June/001199.html](https://lists.ubuntu.com/archives/edubuntu-users/2007-June/001199.html)

---

### Post by bitmonkeyagi on 2008-04-01
Saybayon isn't installed ("apt-get remove sabayon" returns something about "not installed, so not removed")

how would I have gotten two dhcp servers running, and how would I know?

---

