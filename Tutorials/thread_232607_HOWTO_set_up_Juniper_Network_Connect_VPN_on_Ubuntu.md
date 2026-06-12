---
title: "HOWTO set up Juniper Network Connect VPN on Ubuntu Dapper"
date: 2006-08-08
forum: Tutorials
---

### Post by madscientist on 2006-08-08
Hi all; I recently started a new job and I needs my remote access!  My previous employer used Nortel Contivity and I used the Apani Contivity client; this was a bit of a pain since it's a proprietary kernel module, but it worked well (and it supported split tunneling, which is sweet!)

My new job uses Juniper's Network Connect VPN, which does not use a KLM (nice!) but does not support split tunneling (boo!)  It has a very nice feature where it will try to download and install the software to your system the first time you run it... and it supports Linux!  Yay!  But, it only supports Red Hat (and other RPM-based distros, most likely)  Boo!  However, I was able to get it working with a bit of playing around :cool:

First, let me hand out props to [this Flexion.org blog post]("http://www.flexion.org/site/index.php?gadget=StaticPage&action=Page&id=50") by Martin... it got me going!  However, it's specific to Ubuntu 5.10 and perhaps an earlier version of Network Connect and I needed to do a few different things.

Here's what I had to do; make sure openssl and the proper libstdc++ libraries are installed, as well as Sun's Java:
```
sudo aptitude install openssl libstdc++2.10-glibc2.2 sun-java5-bin sun-java5-jre
```
The installer wants to use su, not sudo.  I just set my root password to something while I installed it, then reset it again later ([find out how]("https://help.ubuntu.com/community/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d")).

The installer also wants to run RPM to make sure you have openssl etc. installed.  Since it doesn't actually use RPM for anything other than a check, I decided to just make a fake rpm that always succeeds.  Do this:
```
sudo ln -s /bin/true /usr/bin/rpm
```
Finally, the service application tries to dlopen() the openssl library (I'm assuming, since ldd doesn't show it) and it's looking for libssl.so.0, which does not exist on our system per se.  So make it exist with a symlink:
```
sudo ln -s libssl.so.0.9.8 /usr/lib/i686/cmov/libssl.so.0
```
We're all set to install!  Connect to your server and use the "Start" button next to "Network Connect" under Client Application Sessions.  It will open a terminal and ask for a password for su: use the one you set above.  It will then install and connect and all should be working well.

At this point you can undo *some* of the customizations above: you won't need a root password anymore so you can undo that, and you can remove the rpm link:
```
sudo rm -f /usr/bin/rpm
```
I've only tried the most basic stuff but it seems to be working well for me!

---

### Post by mcewanbr on 2006-08-20
I have done the same thing, except I didn't fake it out using your symlink method for rpm.

Instead, I edited the $HOME/.juniper_networks/network_connect/xlaunchNC.sh.  Towards the bottom is the code that looks for rpm.```
rpm -q openssl 1>> $1/missing.info
if [ "$?" -ne "0" ]
then
    echo "RPM query for openssl failed." >> $1/missing.rpt
fi
```I just commented these lines out.  Then I ran```
chattr +i xlaunchNC.sh
```...on the file to prevent the logon script from overwriting this file on future logins to the vpn and reseting it back to default.

Works great for me!

---

### Post by timshadel on 2006-09-26
I also had to 

```
sudo apt-get install lesstif2
```

and

```
sudo ln -s /usr/lib/libXm.so.2 /usr/lib/libXm.so.3
```

so that if found libXm.so.

The dialog comes up, but it's filled with stuff like "label47".  It's unreadable, but the VPN works great. :-)

---

### Post by madscientist on 2006-11-09
I didn't need to install Motif or Lesstif.  Weird!

However, after updating to Edgy I had problems: it wanted to reinstall every time I tried to start my session.  It turns out that whomever is creating the install and setup shell scripts for these packages is a ***horrible*** shell scripter.  Really, I can't remember when I've seen worse.  It's one thing to have crappy scripts for internal processes but to release them to customers?  If you work for Juniper please find out who is responsible for this and beat them with a clue stick; they're embarrassing your company.

Since in Edgy /bin/sh is really dash, not bash, and these scripts are in no way valid POSIX sh scripts, they break badly... but for no reason other than they're poorly written.

I've attached new versions of these two scripts.  Copy them into ~/.juniper_networks/network_connect.  I made them immutable with chattr +i, as described elsewhere in this thread, although I'm not sure that's necessary.

Hrmph.  I can't attach anything.  When I try to and click the upload button FireFox gives me a dialog saying I want to open newattachment.php and what application do I want to use?  I tried "firefox" but that opened a blank window.  So I guess if you need these, email me or send me a private message.

---

### Post by madscientist on 2006-11-13
Another hint: I was having my login session messed up every so often.  After looking carefully I realized that my DHCP client kept rewriting my /etc/resolv.conf file every time my lease was re-acquired, so I was no longer using the VPN network's DNS servers.  It was also rewriting the search string so searches for hostnames weren't being resolved correctly.

The solution I used was to disable setting of the domain-name and domain-name-servers in my DHCP client; this means that if my DHCP server changed this I wouldn't automatically know about it which is a bummer, but that's very unlikely so it's the lesser of two evils.

What you need to do is edit /etc/dhcp3/dhclient.conf, and remove the domain-name and domain-name-servers from the "request" attribute list.  The docs are not very clear that this means that /etc/resolv.conf won't be updated, but in fact that seems to be the case.  Note you need to restart the DHCP client; an easy way to do that is to run "sudo ifdown eth0" then "sudo ifup eth0" (or whatever your network interface is).  I suppose you can also bring the interface down and back up through the GUI but I've had problems with that in the past.

---

### Post by lordmundi on 2006-11-17
Question:  I finally got the client to connect and work in my VMWare virtual machine of ubuntu, but as soon as it connected, the whole OS seemed to lock up.. and I think it may be because everything is getting routed through that adapter, and since I rely on NFS for my home dir and NIS for auth, that is probably killing it right?

Anybody else have this problem?  So my question is (and I suppose people might want this even if they weren't having this problem), how do I selectively route to this java adapter/client instead of it redirecting everything to that adapter?

FG

---

### Post by tworkemon on 2006-12-19
madscientist, could you try to attach those files again ?? Also anyone get this to work with Feisty ??

---

### Post by ariel on 2007-01-05
Hi madscientist, could you make Juniper "Network Connect" work with Edgy? If so can you update this howto? For the scripts, instead of attachments how about a simple copy/paste on a port here ?  :)

Thanks... hope you see this soon!

---

### Post by wilem on 2007-01-09
I was able to get this to work on Edgy following the first post. My only issue now is that I want tsclient to go through tun0 connection that Network Connect is using. Anyone know how to make that happen?

I changed the order of my DNS and that resolved the issue.

---

### Post by nikoli on 2007-02-08
I get this error when trying to connect...

[IMG]http://i138.photobucket.com/albums/q278/nikoli827/Screenshot.png[/IMG]

This is pretty much the closest I got with google...

[http://www.juniperforum.com/index.php?topic=3014.0](http://www.juniperforum.com/index.php?topic=3014.0)

That didn't help much and now I'm kinda stuck here :confused:

---

### Post by RichardBronosky on 2007-02-19
Using Edgy, this worked EXACTLY as described in the original thread!  God Bless You Hacker!!!

---

### Post by madscientist on 2007-02-23
Bleah!  I signed up to have private messages emailed to me but I don't get any email!  Frustrating.  Sorry I haven't checked this thread in quite a while.

Anyway, I'll try attaching my scripts again and maybe it will work this time.

---

### Post by madscientist on 2007-02-23
> **lordmundi said:**
> Question:  I finally got the client to connect and work in my VMWare virtual machine of ubuntu, but as soon as it connected, the whole OS seemed to lock up.. and I think it may be because everything is getting routed through that adapter, and since I rely on NFS for my home dir and NIS for auth, that is probably killing it right?

Anybody else have this problem?  So my question is (and I suppose people might want this even if they weren't having this problem), how do I selectively route to this java adapter/client instead of it redirecting everything to that adapter?
The system will automatically create a virtual IP interface using tun, then set up routes to send the VPN-bound traffic to the new interface.  It will also reset /etc/resolv.conf so that your DNS server is pointing to the server over the VPN, so you can resolve local addresses inside the VPN.

Either of these things may be causing you to have problems.  If the connect is not working properly, or if it throws some kind of invalid value into /etc/resolv.conf, then you won't be able to resolve any hostnames and that can often make it look like your system is locked up.  Check the contents of /etc/resolv.conf and make sure that the address(es) there for "nameserver" are accessible (you can try pinging them).

Also, if your remote site is using an overlapping IP address space, then you could have problems (although I don't think your system should lock up).  For example, on my home network I'm using the common 196.168.* class B range.  However, my work internal network also uses that same class B range (this is kind of bogus but...)  Now all traffic that I want to send to my local systems will instead get routed through the VPN.  Not good.  To fix this I modified my local LAN to use one of the other reserved IP address spaces.

---

### Post by madscientist on 2007-02-23
> **ariel said:**
> Hi madscientist, could you make Juniper "Network Connect" work with Edgy? If so can you update this howto? For the scripts, instead of attachments how about a simple copy/paste on a port here ?  :)
It works fine with Edgy, using the same directions.  I don't recall needing to do anything different.

I was able to get the attachment to work finally; check [post #12 for this thread]("http://ubuntuforums.org/showpost.php?p=2201028&postcount=12").

---

### Post by madscientist on 2007-02-23
> **nikoli said:**
> I get this error when trying to connect...

That didn't help much and now I'm kinda stuck here :confused:
Hm.  that library is provided as part of the network connect package.  Try using the scripts attached in post #12 and following the directions.  Make sure you're not overriding LD_LIBRARY_PATH in your shell setup (~/.bashrc or similar).

I don't really have any other suggestions right now... :-k.

---

### Post by Halcy0n on 2007-04-08
nikoli: I'm getting the same exact error as you.  Did you ever figure out how to resolve it?

---

### Post by jparsons on 2007-04-18
The Juniper didn't function at all before I found this thread so thanks y'all!

Got it to work using the main post on Edgy without any hassle.

My steps:
1. RPM Updates:
%%sudo aptitude install openssl libstdc++2.10-glibc2.2 sun-java5-bin sun-java5-jre
2. RPM fakery
%%sudo ln -s /bin/true /usr/bin/rpm
3. SSL Lib Setup - here the original post doesn't say where to create the link, so I assumed it was in the junpier's directory - ~/.juniper_networks/network_connect (This directory was created after my first attempt failed)
%%sudo ln -s libssl.so.0.9.8 /usr/lib/i686/cmov/libssl.so.0
4. Login to the Juniper and launch. Type su pw when requested.

---

### Post by 8i5 on 2007-04-26
These fixes worked great in Edgy...sadly since carrying out a fresh install of Feisty it's completely broken and I cannot get it going again. I get as far as the java gui loading but it disappears after a couple of seconds and no connection is made.

Anyone get feisty working with network connect? I can't believe Juniper don't support linux a little better than this.

---

### Post by madscientist on 2007-04-27
I upgraded to Feisty last week and my Juniper connection works fine.  Note that I upgraded rather than reinstalling, so this is really my previous installation that continues to work, rather than a brand new install.

---

### Post by puntium on 2007-05-01
Did anyone manage to get this working in some form on an amd64 feisty install?

I created a 32bit chroot for firefox anyways.. and followed the instructions there. I can get it to install, but it can't ever connect. Probably something that the ncsvc service is trying to do that doesn't work because it's a 32bit chroot running on a 64bit kernel?

---

### Post by trendzetter on 2007-05-13
I had a problem on my fresh install at first because I accedently skipped this step
"The installer wants to use su, not sudo. I just set my root password to something while I installed it"

It crashed the Network connect applet while connecting. After setting the password and installing the app everything runs smooth. :guitar:

---

### Post by dpiazza on 2007-05-14
Hi, I followed instructions of the first post. When I log into the Juniper home page, and I click the button Start besides "Windows secure application manager" I get the "Your OS/platform is not supported for this component." message. 
Neither the directory ~/juniper_networks is created. 
My customer has Juniper Secure Access SSL VPN. Is this the same you are succeeding to run here?
Where I'm going wrong?

thanks
Davide.

---

### Post by madscientist on 2007-05-15
Of course you should not click the button that says "Windows secure application manager", because you are not running Windows.  You are running GNU/Linux, and therefore the Windows secure application manager will not be supported on your system.

Instead, you should click the button above that that says "Network connect".

Then proceed as described.

---

### Post by dpiazza on 2007-05-16
thanks for the reply.
After logging in to the customer VPN site I have the page I attach so no "Network connect".
Any consideration on this?

Thanks
Davide.

---

### Post by madscientist on 2007-05-16
Looks like your company didn't deploy the non-Windows VPN solution.

I don't know that much about the administrative side of this so I can't say if that costs extra, or how you might go about getting it enabled.  You'll have to contact your IT folks and ask them to turn it on.

I've attached a screenshot of what the bottom of my VPN page looks like.

---

### Post by bence8810 on 2007-05-20
Hi

This thread has given me great hope, I am trying to connect to our corporate VPN, and I am unable to do so from Linux. Our company is basically only on MS, and our solutions dont focus on any other OSs.

The problem is that on our Juniper solution, if I authenticate on the website with the token, I will not see the Network Connect, nor the Windows Application Manager unless I am on the AD domain. I guess its the host checker which checks it? Any way to overcome that limitation?

When I connect from a windows machine thats on our Global AD, I am shown the Application Manager, etc.

Thanks
Ben

---

### Post by dpiazza on 2007-05-21
Is there anybody that can point me where to obtain the linux client software? is it enough to put the installation files in the ~/.juniper_networks foler?

thanks

---

### Post by bslattery on 2007-05-21
Hello,

I am also trying to get Ubuntu to work with Network Connect.  After supplying credentials, the Network Connect piece begins to load and the following error is displayed:

"rpm query for openssl failed".

Screenshot attached.

Any help on this is sincerely appreciated.

Respectfully,
Bob Slattery

---

### Post by madscientist on 2007-05-22
Did you follow the directions in the very first post on this thread?  If you had you wouldn't be getting this error ;)

---

### Post by bslattery on 2007-05-22
My humble apologies for breaking the first rule of posting to the thread - READ THE ENTIRE THREAD FIRST!!

After reading the complete thread, my fresh feisty install works wonderfully with Netwrok Connect except for DNS, no name resolution through the NC tunnel.  I am working on that issue now and believe I saw someone with the same issue posted here.

Thanks for *scold*, I needed it.

Respectfully,
bslattery

---

### Post by madscientist on 2007-05-22
Not to worry.  Reading the entire thread is always best, but note that in the "Tutorials & Tips" forums, with threads titled HOWTO, it's especially crucial to read the FIRST post, because the first post is the actual "tutorial" part.

Cheers!

---

### Post by bence8810 on 2007-05-22
Hi

Sorry to re-ask, but do you have any ideas about my problem, explained above? Its regarding the Host-checker, etc.

Thanks

Ben

---

### Post by madscientist on 2007-05-23
Sorry, but I don't know.  It sounds to me, if you can't see the Network Connect icon when you log in, that the server is not configured to support the Linux client or there some other server configuration issue.  I don't really know what "host-checker" is?

I'm completely unfamiliar with the server side of this solution; I've only ever used/seen the client.  Maybe you'd have more luck asking on a Juniper support forum?

---

### Post by bence8810 on 2007-05-24
Hi

Thanks a lot. I guess I am out of luck anyways, because when I logged in from a Windows box, that is on the AD, I can only see the Windows Secure Application Manager, and not the other one which may work for linux. So even if I can fake my Ubuntu box to act as if part of the domain, the windows applicaton manager will never launch on a Linux box.

Thanks for your kind help anyways, I will ask the Juniper guys just to be sure that my assumption is right,

Cheers

Ben

---

### Post by dpiazza on 2007-05-24
Ben, if you ever some feedback to juniper forums could you report it back here ? or post the link to the thread?

Many thanks
Davide.

---

### Post by arecibo on 2007-05-25
Hi, I am trying to get network connect working on Debian and found this page. I followed the instructions. The network connect dialog popped up but I couldn't connect. The diagnosis message indicates the NC installation check failed. The NC service is not running. Anyone has idea how to fix this problem?

Thanks!

---

### Post by dachinster on 2007-06-03
hi
i am using feisty
i followed the first post all the way through but i am getting this error (see pic)

---

### Post by dachinster on 2007-06-03
can anyone assist me ?

---

### Post by madscientist on 2007-06-04
That error message looks to me like you haven't linked RPM, like this:

sudo ln -s /bin/true /usr/bin/rpm

Are you SURE you successfully did that?  If you say "ls -l /usr/bin/rpm" what do you get?  If you run this "/usr/bin/rpm && echo ok" does it print "ok"?  If not then something is not right with this step.

Unfortunately Juniper only produces packages for RPM-based distros and they use the RPM program to find out whether the libraries, etc. they need are installed, instead of a more portable method such as ldd or whatever.  Anyway, in order to "fake out" the installer so that it won't complain that you don't have those libraries, you have to run the above sudo command.

---

### Post by dachinster on 2007-06-04
I did everything like you did in the first post.
Here is what you asked of me:

> dachinster@Ubuntu:~$ sudo ln -s /bin/true /usr/bin/rpm
ln: creating symbolic link `/usr/bin/rpm' to `/bin/true': File exists
dachinster@Ubuntu:~$ ls -l /usr/bin/rp
rpcclient  rpcinfo    rpl8       rpm        
dachinster@Ubuntu:~$ ls -l /usr/bin/rpm
lrwxrwxrwx 1 root root 9 2007-06-03 08:22 /usr/bin/rpm -> /bin/true
dachinster@Ubuntu:~$ /usr/bin/rpm && echo ok
ok
dachinster@Ubuntu:~$ 

---

### Post by madscientist on 2007-06-05
Hm, interesting.  I wonder if you have a very different version; yours seems to need Motif, which someone else mentioned in an earlier post here but which my version definitely does not need.

After an unsuccessful start, do you still have a ~/.juniper_networks directory?  Can you look at the file ~/.juniper_networks/network_connect/version.txt?  If so what does it say?

---

### Post by dachinster on 2007-06-06
What version do you have?
I think mine is an early version

When i check the version, this is what i see

> dachinster@Ubuntu:~/.juniper_networks/network_connect$ cat version.txt 
Version: 1.0
dachinster@Ubuntu:~/.juniper_networks/network_connect$ 

---

### Post by madscientist on 2007-06-06
My version is 1.2.  It seems like older versions of the tool might have been written in Motif?  If you look at post #3 on this thread there's one from someone else who also had to install Motif (lesstif is an open source reimplementation of Motif) to get his VPN working.  Start there and see if that helps at all.

Of course, you could also ask your IT folks to upgrade to the newer version; I'm sure there must be some security and other bug fixes that would be nice to have anyway.

---

### Post by Pgravestock on 2007-07-02
Just want to check I'm not missing a trick or two here:

1 Should I expect to connect to a Windows Citrix server using Juniper VPN on Ubuntu, or will this only work if I attempt to connect to the Citrix server using a Windows PC?

2 If the answer to above is yes I should be able to connect to a Windows Citrix server using Ubuntu and Juniper VPN, does the Citrx server have to be configured to handle a session from my Ubuntu box, or should it all work seamlessly?

Thanks

Paul

---

### Post by madscientist on 2007-07-03
Citrix doesn't have anything to do with Juniper VPN as far as I'm aware.  If you need the Juniper VPN  working in order to get network access to the Citrix server, and that you cannot get the VPN running, then we might be able to help if you describe the problem.

If you have the VPN running (or don't need it) and you're trying to get the Citrix client working, we can't help there: you want to look at a thread dealing with Citrix, like this: [http://ubuntuforums.org/showthread.php?t=17979](http://ubuntuforums.org/showthread.php?t=17979)

---

### Post by psaville on 2007-07-09
I am trying to follow the instructions on the first post, but I am seeing a few issues.

I'm running Ubuntu Fiesty (7.04 AM64).

First, I cannot install the c++ libs libstdc++2.10-glibc2.2-0. They cannot be found by either apt-get or aptitude.

I did try installing any other libc++ stuff I could find:
```
libstdc++5, libstdc++6, libglib2.0-0, libglib-java
```

I did try using the RPM package with Alien, but still the same behavior as follows. With Alien and RPM I tried both with and without the "fake-rpm" step before and after the alien install.

I see the Java download page, but I only get about 3 or 4 blocks in on the progress bar before FireFox just crashes (disappears).

If I look at the setup version file on my windows machine after connecting, this is what I see:
```
[Setup]
DisplayVersion=5.5.0.11711
DisplayName=Setup
SecurityPatch=1

```

I have just tried the lesstif install and the same result.

Anyone have any ideas why I cannot get it to work? How can I get more debug or log information to help find out what my problem is?

Final point: my ~/.juniper_networks folder is empty.

---

### Post by madscientist on 2007-07-09
First let me say that I wouldn't be at all surprised if the kit didn't work on a 64bit system.  Although it's obviously quite possible to run 32bit apps on a 64bit system, it requires the person creating the kit to do it carefully and properly, and in my experience most 3rd party proprietary software doesn't do that.

So, you may be out of luck unless you install a 32bit version of Ubuntu on your 64bit system (which will work, but seems a shame).  Or, you could try to do something super-fancy like create a 32bit chroot environment or something--but you'll have to go elsewhere for help with that.

That being said:

I checked my current install of Network Connect and it does not appear to require the old libstdc++ version 2 any longer: at least none of the programs on my system use it (according to ldd).  So, either only the installer uses it or that requirement has changed since the version I was using last summer.  If the former then you'll need to 

Second, I'm not sure what you mean when you said you used alien on the RPM.  What RPM?  When I did my install everything downloaded from the server and unpacked into my home directory by default.  There was no RPM installed, and nothing was installed into /usr or any other restricted directory.

Third, that version you see on your windows system is completely unrelated to the Linux version.

I think you need to re-ask your question with more precise details, because I couldn't really understand where the problem was from what you posted.  So, you connect to your remote server using FireFox and that works, right?  Then you see the Network Connect button and you click that, right?  Then... what happens?

---

### Post by psaville on 2007-07-09
I was working with our IT guy who was using the VPN on his Fedora machine... He has admin access to the VPN appliance where the application installers are located. So we tried downloading the RPM installer and then converting it using alien. That doesn't seem to really install it properly either. So I have removed it, alien and rpm.

I have tried again with lesstif and libmotif3 installed but still my browser crashes.

So to clarify what I was doing:
Yes, I can reach the logon page for my remote VPN.
Originally the default preferences were set to automatically load the "Network Connect" application upon logging on, and thus immediately after logging on the java download/ install progress bar is shown.
Now, I have changed the preferences to manually start the application.

Upon clicking on start, the java icon image is shown on a new page with a progress bar above it. The first two blocks of the progress bar complete very quickly. The third and then fourth take about 20secs to reach. The fourth block is painted and within 2secs of that - firefox disappears!!! Process, everything, gone.

I'm not sure where to look to find more information about why this happens. I have even left the root password enabled???

Please, any hints or let me know what commands to run in order to tell you what is installed that may be relevant.

While I cannot currently connect directly from linux, I have been able to run the machine in a vm using physical drive mappings. Using NAT allows the linux install to piggy back my windows VPN connection when it is active.

---

### Post by madscientist on 2007-07-11
Unfortunately I don't have any great ideas for you.  If FireFox goes down that seems to me to imply that at least the installer plugin is doing something very bad.  I'm still pretty suspicious about the 64bit thing.  The only place any sort of error log would appear would be in the ~/.juniper_networks directory I believe.

I suppose if you get desperate you could try running strace on the PID and see if it reveals anything interesting.

Something else you might try is booting your system off of a 32bit Ubuntu LiveCD, and trying to get onto the VPN using that.  Alternatively, since you have VMWare you could try installing a 32bit Ubuntu in VMWare and see if the VPN works there.

If it works in either of these situations, you'll have to file a bug report with Juniper and ask them to support 64bit Linux.

If you do get it installed and working in a 32bit environment you might try copying the installation stuff into your 64bit home directory and see if it works there.  I've seen software where only the installer was broken under 64bit, but once it was installed it worked fine.

---

### Post by bennyz on 2007-07-14
Works perfectly in feisty.  Just had to get the newest java plugin for firefox.  

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html).

Now I really can think of why I need windows.
Thanks!

---

### Post by tmai on 2007-08-21
madscientist,

I followed the instructions on the first page and am getting partial sucess.  Basically,I am still prompted for the su password.  I'm running Feisty btw.

The error: 
```
/home/username/.juniper_network/network_connect/installNC.sh: 9: cannot open such file
/home/username/.juniper_network/network_connect/installNC.sh: 9: 1: not found 
Service needs to be reinstalled.
```

When I enter the root/su passowrd, it connects fine.  If I cancel this (CNTRL-D) and 'N' to try again, I still get connected.

I tried:
[LIST]
[*]deleting ~/.juniper_networks
[*]Start netconnect
[*]Cancel password prompt
[*]deteting ~/.juniper_networks/network_connect
[*]cp -R ~/.juniper_networks/tmp to ~/.juniper_networks/network_connect/
[*]extracted your installNC.sh and xlaunchNC.sh to the network_connect directory
[*]chmod +x ~/.juniper_networks/network_connect/*.sh
[*]Login to the juniper box and start netconnect
[*]Still prompted for su password
[/LIST]

I noticed that ~/.juniper_networks/network_connect/ncsvc was owned by root:root

I tried chown'ing it to myself and it still prompts for su password.

Do you (or anyone who have had my problem) know what I'm missing?

Regards and thanks for the post!

---

### Post by madscientist on 2007-08-21
This is because apparently Juniper doesn't employ anyone who knows how to write shell scripts (or else they're busy elsewhere).  See my [post #4]("http://ubuntuforums.org/showpost.php?p=1737611&postcount=4") and also my [post #12]("http://ubuntuforums.org/showpost.php?p=2201028&postcount=12").  You'll need to replace the scripts in your package with the ones in the attachment, then (maybe) use chattr +i to make them immutable.

---

### Post by tmai on 2007-08-21
Thanks for the quick reply, madscientist.

Unfortunately, when trying to 'chattr -i' the files in question, I get:

```
chattr: No such file or directory while trying to stat install
```

I know this is not a VPN connectivity issue, but have you come across this before?  I'm running Feisty on REISERFS partitions.

I tried this on another Feisty installation and same problem.  The command did work on a RedHat machine (I copied the files onto USB drive and ran the commands on the files from RedHat).  

But when I took it back to my Feisty laptop, NetConnect would still prompt for reinstallation of the service.

Anyway, any insight (from someone with 5 cups) would greatly help a single-cupper.

T

---

### Post by madscientist on 2007-08-21
Sorry, you're out of luck if you're using reiserfs.  That filesystem doesn't support the chattr command.

There may be some other way to make files on reiserfs filesystems immutable even to root, but I don't know what they are.  You'll have to seek out someone using reiserfs filesystems (this is not a standard filesystem type for Ubuntu AFAIK).

It's possible you won't need this anyway; you should try it without the chatter, just replacing the scripts, and see if it works.  The Juniper stuff is hugely annoying in that it seems to unpack itself every time you connect, but maybe it will work anyway.

It's pretty obvious Juniper doesn't give a crap about Linux.  I guess they think we should be happy they offer any support at all.

---

### Post by Leotar on 2007-08-24
I am a rookie in Linux....!!! So pls pardon me if I am asking any silly Qs.

I can't really get past the following lines even after supplying my root password..What must be the problem.. ?

I have also edited the su commands to sudo in the script.. becoz i read somewhere that ubuntu uses sudo instead of su.. but even that didn't help me..
========================================
~/.juniper_networks/network_connect/installNC.sh: 9: 1: not found
Service needs to be installed for the first time.
Please enter the root/su password
Password: 
su: Authentication failure
Sorry.
Invalid su password and/or Unable to install ncsvc
Do you want to try again (enter y to try again):

---

### Post by madscientist on 2007-08-24
If you check the first message in the thread it says: "The installer wants to use su, not sudo. I just set my root password to something while I installed it, then reset it again later"  Unfortunately it looks like the link I provided there has been changed so it no longer tells you how to do that.  So, run this:

sudo passwd

then when it asks for a password type your password first.  Then it will ask for ANOTHER password; this will be the root password.  You can put whatever you like here, it's just temporary.  Then it will ask you to confirm the password; type the root password again.

Now, when you start up network connector and it asks for the root password, enter the one you created.  It should work.  It should also not need to do this again since it's installed what it needs to.

So, you should undo your root password again (trust me: the one and only time one of my Linux systems was hacked was because I forgot to reset the root password and I had used an easily-guessable one; someone brute-forced it 5 months after I had changed it :-/)  To unset it again use:

sudo passwd -l

to lock the root password again.


The reason changing the script doesn't help is because network connector unpacks the scripts again every time you start it.  Annoying, to be sure.

---

### Post by nofear07 on 2007-08-25
All this does work for feisty.  You need to make sure you have the packages as detailed in the begining:

```
apt-get install openssl libstdc++2.10-glibc2.2 sun-java5-bin sun-java5-jre

```
next do
```
ln -s /bin/true /bin/rpm
```

and I also had to change this
```
ln -s /usr/lib/libssl.so.0.9.8 /usr/lib/libssl.so
```

If you need any help try to PM me and I will be glad to help out as I can.  Juniper has chosen to only support RPM based programming.  If you want future mainline support get with your local Juniper rep and ask them to submit an ER to support DEB  or you can contact myself ;-)

best of luck

---

### Post by madscientist on 2007-08-25
I don't care so much about supporting only RPM (it would be nice to support DEB as well, but we can work with it).  I just wish they would spend a little time creating sane shell scripts instead of the buggy mess they have now.  That would make things MUCH simpler.  After that, if they could get a more traditional install model (where the install is a separate step, if it requires root privileges) that would be nice too.

But I have to say, I much prefer this model to the Nortel/Apani client model; that client is unquestionably more polished and has some features the Juniper one doesn't, but it (a) costs a lot extra, and (b) requires a proprietary kernel module which makes it a big PITA: you have to downgrade your kernel and/or run a custom kernel to use it.

Cheers!

---

### Post by aguevarra on 2007-08-27
from [https://lists.ubuntu.com/archives/ubuntu-users/2007-April/112723.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-April/112723.html)

ln -s /usr/lib/libssl.so.0.9.8 /usr/lib/libssl.so

resolves the libncui.so issue

---

### Post by Leotar on 2007-08-27
Thanx a Ton friends.. specially to madscientist and nofear07.. 

My VPN connection is working fine...I did exactly what madscientist mentioned in #56 thread and it solved the password issue...Fantastic.

BTW: How can I stop the shell pop-up which asks me to enter root password.. I have inactivated the password and the VPN works even after forcibly closing this shell, but How can I get rid of this pop-up?

---

### Post by madscientist on 2007-08-28
Hm.  I never get any kind of popup asking for a root password.  I wonder if something didn't "take" during your install, so the system thinks that you need to reinstall every time you start.  You might try adding back the /usr/bin/rpm symbolic link and see if that helps at all.

---

### Post by gfa on 2007-08-30
> **madscientist said:**
> Hm.  I never get any kind of popup asking for a root password.  I wonder if something didn't "take" during your install, so the system thinks that you need to reinstall every time you start.  You might try adding back the /usr/bin/rpm symbolic link and see if that helps at all.

Hi...

As you say in [#4]("http://ubuntuforums.org/showpost.php?p=1737611&postcount=4"), in Feisty /bin/sh is a symbolic link to /bin/dash, so, why not to change that to /bin/bash (like it is in Debian and other distros):

```
sudo ln -sf /bin/bash /bin/sh
```

Does it has other "side effects"???

P.D. i used to work with Debian and the reinstall window didn't show every time i logged on... because it uses bash, i've changed in Feisty and stopped showing :)

---

### Post by madscientist on 2007-08-30
It's an option.  In *theory* it shouldn't break anything, because dash is a 100% POSIX conforming shell (at least that's the goal) with no (or at least hardly any) extra added features, while bash is supposed to be a strict superset (almost, esp. if you set POSIXLY_CORRECT) of POSIX sh.  So, any script that works in dash should work the same way in bash.

However, for myself I'm not willing to go that route.  Call me a purist or anal retentive or whatever you want, but this "/bin/sh is /bin/bash" strikes me as the latest version of "all the world's a VAX" (for those of you old enough to remember what that means 8-)) and I refuse to give in.

Changing /bin/sh on your system is NEVER something to take lightly.  I prefer to fix the shell scripts, as my attachment in #12 does.

---

### Post by Leotar on 2007-08-31
I have replaced those files [installNC and xlaunch] with the ones in attachment, but I am still getting the pop-up.

I will install Debian/Ubuntu in one more m/c that I have here and try out from the beginning and reply with what I observe. I gotta give back something too, right!! :-)

---

### Post by madscientist on 2007-08-31
Did you use the "chattr +i" thing on them after you replaced them, as described in the post #4 ?

The Juniper software has the annoying habit of unpacking the package fresh every time you start the connector, thus overwriting any changes you made to it previously.  Setting the files immutable will "fix" this.

See, I told you this software was very badly designed! :(

---

### Post by weekdaysailor on 2007-09-05
MadScientist, you may be mad, but you rock! Your scripts + instructions worked flawlessly in Feisty Fawn on an IBM T41 on Fawn 7.04 running patches as of 9/5/2007.

-wds

btw - I work for Juniper and have reflected the need to support Ubuntu and the editorial comments about our scripts to the product manager...I'll update the thread if I hear anything productive.

---

### Post by madscientist on 2007-09-05
Thanks weekdaysailor!  Support for Ubuntu would be great, but as I've mentioned before just having valid POSIX shell scripts instead of the broken mess we get today would go a long way towards lessening the pain.

It looks like we're going to have to replace the old saying "all the world's not a VAX" with "all the world's not Red Hat" #-o

---

### Post by nofear07 on 2007-09-11
For some reason about a week ago my Network Connect quit working (and had been working fine)  I checked the ln for true and rpm.  I check the ln for the libssl  

I also removed all the files in $HOME/.juniper_networks/network_connect/ and retried still no go.  I'm wondering if I have updated a package that broke a dependency or something.  

This is the only thing in the ncui.log and yes I'm typing the password correctly:
20070910210414.493096 ncui[17246] ncapp.info New ncapp log level set to 3 (nccommon.cpp:75)
20070910210414.493165 ncui[17246] ncui.info read from params...  (nccommon.cpp:121)
20070910210414.493235 ncui[17246] ncapp.panic Failed to read password from prompt (nccommon.cpp:591)

Thoughts as to what to try next?

---

### Post by weekdaysailor on 2007-09-12
I slagged my install and started over (video crap driving me crazy) so I had a chance to re-do this howto. But this time I tested after every step and did NOT have to use the scripts Mad provided. (Feisty on IBM T41). In the meantime our SA box has been upgraded.

My point? Other things may have changed besides your OS. Check with your network admin and see if they upgraded or changed configs recently.

Cheers,

-Keith

---

### Post by madscientist on 2007-09-12
Interesting.  What version of netconnect are you seeing now?  It'd be nice to know when they fixed this.

---

### Post by nofear07 on 2007-09-13
Ok, I got it working.  Don't know why but after a reboot it was working fine.  So something was hanging the process.

Also I too did not have to use the scripts provided by madscientist.  This is for Netconnect 1.2

---

### Post by tribaal on 2007-09-26
Hi all

Thanks a lot for the scripts madscientist, they work a treat.
I have found a little annoyance while using Juniper VPN however, maybe you guys got around this already:

I use firestarter for firewall configuration, and I cannot seem to figure out what policy to add to allow all traffic from the VPN to go through. So far my "fix" is to turn the firewall off while connected to the VPN... Which is ok, but annoying. 

Does anyone know how to make firestarter understand I don't want it to filter (and block) traffic from the VPN?

Thanks a lot!

- Trib'

---

### Post by mjwood0 on 2007-10-01
This is really great news for me as my company just switched to the Juniper Network system (from Cisco).

I have a couple of questions --

1. Has anyone gotten this to work with 7.04 64-bit?  Or will I need to go to 32-bit for this to be happy.

2. I have a copy of XP that hasn't been activated.  I was waiting due to the fact that I'm going to be upgrading my hardware soon.  When XP Activates, how does this work on a virtual machine?  If I upgrade my hardware, but run the same virtual machine, does XP throw up a red flag?

Thanks for any help!

---

### Post by fangorious on 2007-10-09
Anyone have this working in gutsy? The GUI comes up for me and either immediately crashes or gives a connection failure. I'm running int the LiveDVD though, so I'm wondering if that's the problem. I couldn't get gutsy to install in Parallels on my Mac and don't want to install gutsy until I know I can get network connect working.

---

### Post by gadjou on 2007-10-09
> **fangorious said:**
> Anyone have this working in gutsy? The GUI comes up for me and either immediately crashes or gives a connection failure. I'm running int the LiveDVD though, so I'm wondering if that's the problem. I couldn't get gutsy to install in Parallels on my Mac and don't want to install gutsy until I know I can get network connect working.

It might be a live cd issue. I got it working on an installed festy. However, I tried to make a live cd with "reconstructor" based on the sames scripts and packages, but wasn't able to get it connect. It's probably a file permission problem since live cds use a special file system.
Anyway, I will check it again when I'll have time and inform you on this post.
Meanwhile, you might try it installing gutsy on a virtual machine.

---

### Post by madscientist on 2007-10-09
I haven't tried Gutsy yet; I usually wait until the official release unless there's something there I really want.  It doesn't seem likely that there's a problem here but you never know I guess.  I'll let you know how it goes (9 days to go!!)

---

### Post by fangorious on 2007-10-09
After a little finagling I was able to install the gutsy beta in VirtualPC on a Windows box. With no steps other than your original howto, the gui comes up and says Connected. Unfortunately I'm doing this already on the office network, so I can't really test the connection. But this does give me enough confidence to install 7.10 on my laptop, so I can test the actual connection from home after I've dont that.

---

### Post by gmcauley on 2007-10-10
> **mjwood0 said:**
> 

1. Has anyone gotten this to work with 7.04 64-bit?  Or will I need to go to 32-bit for this to be happy.

This is also my question.  Should I bother to try this in 64bit? 

What issue(s) would I likely run into with 64bit?

---

### Post by fangorious on 2007-10-10
ok, I have gutsy beta installed on my laptop, and this howto gets the NC up and running. Although I used java6 instead of java5.

---

### Post by madscientist on 2007-10-11
Yay!  Good to know, fangorious!

gmcauley: sorry but I don't have any 64bit systems so I can't address your question; you  might just have to bite the bullet and try it out 8-[

---

### Post by gmcauley on 2007-10-12
> **madscientist said:**
> gmcauley: sorry but I don't have any 64bit systems so I can't address your question; you  might just have to bite the bullet and try it out 8-[

Well I just tried it out and it did not work.  It failed without any message(s) after entering my password during the install.

You say that the libstdc++2.10-glibc2.2 is necessary.  This does not seem to be a 64 bit package. I have saw a post where 'dpkg -i --force-architecture' was used to install this package for another application.  I am tempted to try it, but don't want to stomp on anything.

Pardon my ignorance, this is new territory for me, but how can one know what exactly in this package is needed for NC?

---

### Post by harty83 on 2007-10-13
I really need this to work for 64 bit too!  I've actually got a 32bit firefox/java setup but the pop up does not show up after putting in my password.  Can't get it to work in 32bit or 64bit firefox/java in a 64bit environment.

---

### Post by madscientist on 2007-10-13
> **gmcauley said:**
> You say that the libstdc++2.10-glibc2.2 is necessary.  This does not seem to be a 64 bit package. I have saw a post where 'dpkg -i --force-architecture' was used to install this package for another application.  I am tempted to try it, but don't want to stomp on anything.

Pardon my ignorance, this is new territory for me, but how can one know what exactly in this package is needed for NC?This package contains an older version of the C++ STL and runtime library.  What we can infer from this requirement is that netconnect is a C++ program that was compiled with a much older version of GCC on a much older version of LInux.  This package contains a backward-compatibility library needed by such programs.

It's safe to install; it won't be used by any modern programs (thanks the magic of shared library versioning).

I'd like to help you guys but I just don't have a 64bit system available to test on and I'm not that familiar with how Linux does its multiarchitecture layouts.

---

### Post by zingo on 2007-10-13
Im also trying to get this working on amd64 Feisty install (Will try gutsy If I get this going)
I started with the stuff in the first post (ignored rpm part as I had rpm support)
I tried to force the libstdc++2.10-glibc2.2_2.95 into my system with the following (found it on the net)

```

wget http://ftp.acc.umu.se/mirror/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
sudo dpkg --force-architecture -i libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

```
then I started swiftweasel32 as root and loged on (dont know if I need to be root)
```

sudo swiftweasel32

```
Now I got the .juniper_network/ stuff in my home folder
but for some reason it complains that It don't find libXm.so.3
but I have 
```

lrwxrwxrwx 1 root root      14 2006-12-22 14:09 /usr/lib/libXm.so.2 -> libXm.so.2.0.1
-rw-r--r-- 1 root root 1538384 2006-06-20 03:12 /usr/lib/libXm.so.2.0.1
lrwxrwxrwx 1 root root      14 2007-09-04 23:36 /usr/lib/libXm.so.3 -> libXm.so.3.0.2
-rw-r--r-- 1 root root 2751576 2006-11-13 07:48 /usr/lib/libXm.so.3.0.2

```

But maybe I have to add a 32bit version of libXm.so.3?

I also discovered that I got version 1.1 so I will have a talk with "IT department" about an upgrade to version 1.2 (or newer)

---

### Post by m0rev on 2007-10-13
> **nofear07 said:**
> Ok, I got it working.  Don't know why but after a reboot it was working fine.  So something was hanging the process.

Also I too did not have to use the scripts provided by madscientist.  This is for Netconnect 1.2

Good for you ;) Reboot didn't help me :(

```
ncapp.panic Failed to read password from prompt (nccommon.cpp:614)
```

It used to work couple days ago, so I wonder if some package I've installed recently broke that. Or IT changed something...

Does anybody has similar experience?

---

### Post by marcw on 2007-10-15
Good news / bad news about Gutsy.

Good:
It works.  I had to change my shell from dash to bash because I kept getting the root login prompt but I was going to do that anyway because of all the command line work I do.  It's easy enough with:
```
sudo dpkg-reconfigure dash
```

Bad:
Upon exiting the vpn, my primary network connection doesn't return.  This behavior didn't happen previously.  This is easy enough to resolve with a little desktop script to restart the network but I'm not sure why this happens.

---

### Post by zingo on 2007-10-15
I found this link
[http://www.entropy.ch/blog/Mac+OS+X/2007/07/28/Juniper-Network-Connect-SSL-VPN-and-Virtualization.html]("http://www.entropy.ch/blog/Mac+OS+X/2007/07/28/Juniper-Network-Connect-SSL-VPN-and-Virtualization.html")
It describes how you can use the commandline to setup a connection with something like:
```

cd ~/.juniper_networks/network_connect ./ncsvc -h vpn.example.com -u joesixpack -p [PIN][SecurID token] -r SecurID -f vpn.example.com.der

```
maybe this is the solution for AMD64 since it might not neet the GUI stuff. But when I try I get:
```

ncsvc> DSSSL_load_so failed

```
If possible it would be nice to see if this method works for the people that allready have this working ...

---

### Post by madscientist on 2007-10-17
Ooooh, a command line interface!  That would be sweet!

Unfortunately, it doesn't work for me :(.  I was able to get the .der file but if I run ncsvc directly it stops with no error code or error message, but it doesn't do anything else either (that I can tell--definitely my VPN is not up).

I then tried invoking the Java app directly from the command line instead of the browser, and I got an authorization error.  I didn't do too much with it after that; I probably have other things I could play with.

The errors I got, though, don't look like the one that zingo saw, for whatever that's worth.

---

### Post by zingo on 2007-10-17
My test was on a AMD64 install, that could explain the different output.

Where did you get the .der file was it in the .jar or from the net? In my version 1.1 jar file I didn't get it.

---

### Post by madscientist on 2007-10-19
It's not sitting there on the disk.  You have to run a special command to get it.  I can't remember the command offhand, but if you follow the various links referenced in your post you'll find it.  I think it was in the Gentoo forums link somewhere; there's a step-by-step guide and it describes the commandline you need to invoke to get the .der file.

I still would like to poke at it some more before I conclude it will never work, but just following the directions as-is didn't work for me :sad:

---

### Post by zingo on 2007-10-19
I manage to get netconnect working in a virtualization enviroment (Virtualbox with Fesity i386) this might be my solution untill Junuper releases AMD64 binaries, now I will try to get a routing from virtualbox environment to my computer but that seems possible.

---

### Post by gmcauley on 2007-10-22
I have the command line method working:
[LIST=1]
[*]on a 32 bit system (have not tried it on my 64bit yet (which is what I really want))
[*]with the Java GUI
[*]and also with the ncsvc (w/o the Gui)
[/LIST]

At first I saw authentication errors from both methods.  The GUI method mentioned checking user/password/realm.  It turned out that I needed to specify a 'realm' for our VPN.  Once IT told me what that was, it worked!  It is very nice to not have to go through the web interface!

These links were very helpful:
[http://www.entropy.ch/blog/Mac+OS+X/2007/07/28/Juniper-Network-Connect-SSL-VPN-and-Virtualization.html](http://www.entropy.ch/blog/Mac+OS+X/2007/07/28/Juniper-Network-Connect-SSL-VPN-and-Virtualization.html)
[http://www.entropy.ch/blog-resources/2007-07-28-juniper-networkconnect.html](http://www.entropy.ch/blog-resources/2007-07-28-juniper-networkconnect.html)

I hope to try 64bit next.

---

### Post by gmcauley on 2007-10-22
> **zingo said:**
> 
```

cd ~/.juniper_networks/network_connect ./ncsvc -h vpn.example.com -u joesixpack -p [PIN][SecurID token] -r SecurID -f vpn.example.com.der

```
maybe this is the solution for AMD64 since it might not neet the GUI stuff. But when I try I get:
```

ncsvc> DSSSL_load_so failed

```


Bummer.  I get the same error message on my 64bit machine also.


Also, I get a Java exception when trying the Java GUI command line.


Finally, when trying to connect to the web interface, a dialog pops up saying:
"Cant find required libraries".

So, everything works (web interface, Java GUI command line, ncsvc command line) on my 32 bit machine, but none work on my 64 bit machine :confused:

---

### Post by kasulstyls on 2007-10-23
Thanks to the clear instruction, I got it running fine in Gutsy final release.

---

### Post by potsofdirt on 2007-10-24
I'm running Gutsy here and I can not get Juniper to connect properly.

After following various steps (symlinking rpm, the libs and changing the symlink for sh) I can get the client to install and open the java client.

The problem is that my SSL connection to the VPN times out. Here are the logs:

```

20071024135132.653355 ncsvc[28474] session.info ive_host = ive.{domain}.com (session.cpp:146)
20071024135132.653538 ncsvc[28474] session.info cookie = DSID=<hidden> (session.cpp:154)
20071024135132.653558 ncsvc[28474] session.info Will not use a proxy to connect to the IVE (session.cpp:193)
20071024135132.654772 ncsvc[28474] rmon.info got system route *.164.152.62/255.255.255.255 gw *.211.142.1 metric 1 via 0x00000000 (routemon.cpp:510)
20071024135132.654811 ncsvc[28474] rmon.info got system route *.211.142.0/255.255.255.192 gw 0.0.0.0 metric 0 via 0x00000000 (routemon.cpp:510)
20071024135132.654831 ncsvc[28474] rmon.info got system route 169.254.0.0/255.255.0.0 gw 0.0.0.0 metric 1000 via 0x00000000 (routemon.cpp:510)
20071024135132.654848 ncsvc[28474] rmon.info got system route 0.0.0.0/0.0.0.0 gw *.211.142.1 metric 0 via 0x00000000 (routemon.cpp:510)
20071024135132.654920 ncsvc[28474] rmon.info best route to *.164.152.62 is 0.0.0.0/0.0.0.0 via 0x00000000 metric: 0 (routemon.cpp:1382)
20071024135132.654960 ncsvc[28474] session.info connecting to ive ive.{domain}.com (session.cpp:257)
20071024135132.655432 ncsvc[28474] main.info Using DSSSL to connect to IVE (ncp.cpp:1698)
20071024135132.655466 ncsvc[28474] connect.info creating a new HTTP connection... (ncp_dsssl.cpp:136)
20071024135232.651648 ncsvc[28474] session.error Timed out connecting to ive ive.{domain}.com (session.cpp:280)
20071024135232.651782 ncsvc[28474] session.info disconnecting from ive ive.{domain}.com with reason 6 (session.cpp:379)

```

I've asked the VPN admin to see if his end is producing any meaningful logs to help out.

I've also tried running the command line ncsvc and it times out too.

Any pointers?

---

### Post by marcw on 2007-10-24
Is the cert properly installed in the browser?

---

### Post by zingo on 2007-10-25
gmcauley: if possible would you please supply a mini howto for the command line. And what version do you have of the netconnect software.

---

### Post by harryman01 on 2007-10-25
Guys

Thanks, however I have a Question, my vpn session and NC start and connec, but I have not idication of any kind of traffic (in or out)

I got this output form the NCC

I delete my IP address for confidentiality terms, however anyone can help me?

Thanks

C Diagnostics for Linux. 
Version 1.0.
Release Date/Time: Jul 16 2007 14:19:05
+==============================================================================+
|   Tests:			|    	 Results:		               |
+==============================================================================+

       o  NC Installation Check 	 Passed
       o  NC Diagnostics 			
             NC Service 		 Not Running
             NC Driver Test 		 Passed
             NC Tunnel Test 		 Established

       o  Host Details  			
             Hostname 			 Zeus
             Domainname 		 (none)
             IP Routing Enabled 	 No
             IP Loopback test 		 Passed
             Nameserver Details 	
                xx.xx.xx.xx 		 Ping Failed

                xx.xx.xx.xx 		 Ping Failed
             Gateway Ping Test 			 
               192.168.1.254 		 Ping Failed

       o  Network Connection Diagnostics  			

	     Interface:   		 lo
	     IP Address:  		 127.0.0.1
	     Netmask:     		 255.0.0.0
	     MTU:         		 16436

	     Interface:   		 eth0
	     IP Address:  		 192.168.1.3
	     Netmask:     		 255.255.255.0
	     Broadcast:   		 192.168.1.255
	     MTU:         		 1500

	     Interface:   		 tun0
	     IP Address:  		 10.175.xx.26
	     MTU:         		 1400
      o  Route Info 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ZZ.ZZ.ZZ.ZZ   192.168.1.254   255.255.255.255 UGH   1      0        0 eth0
10.XX.XX.11    10.175.210.26   255.255.255.255 UGH   1      0        0 tun0
10.XX.XX.12    10.175.210.26   255.255.255.255 UGH   1      0        0 tun0
10.XX.XX.1     10.175.210.26   255.255.255.255 UGH   1      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
10.0.0.0        10.175.210.26   255.0.0.0       UG    1      0        0 tun0
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 eth0

       Finished running tests 
+==============================================================================+

---

### Post by potsofdirt on 2007-10-26
@marcw

I can connect to the https web portal without any ssl warnings. I was also able to extract the der file and verify it using openssl, so I don't think it is a certificate issue.

harryman01 posted his diagnostics and I noticed his are a bit different than mine. Does anyone else get a warning about installation?

```

NC Diagnostics for Linux. 
Version 1.0.
Release Date/Time: Jul 16 2007 14:19:05
+==============================================================================+
|   Tests:			|    	 Results:		               |
+==============================================================================+

       o  NC Installation Check 	 Failed
       o  NC Diagnostics 			
             NC Service 		 Not Running
             NC Driver Test 		 Passed
             NC Tunnel Test 		 Not established

       o  Host Details  			
             Hostname 			 bond
             Domainname 		 (none)
             IP Routing Enabled 	 No
             IP Loopback test 		 Passed
             Nameserver Details 	
               *.*.142.10 		 Ping Passed

               *.*.180.228 		 Ping Passed
             Gateway Ping Test 			 
                *.*.142.1 		 Ping Passed

       o  Network Connection Diagnostics  			

	     Interface:   		 lo
	     IP Address:  		 127.0.0.1
	     Netmask:     		 255.0.0.0
	     MTU:         		 16436

	     Interface:   		 eth1
	     IP Address:  		 *.*.142.34
	     Netmask:     		 255.255.255.192
	     Broadcast:   		 *.*.142.63
	     MTU:         		 1500
      o  Route Info 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
*.*.152.62   *.*.142.1    255.255.255.255 UGH   1      0        0 eth1
*.*.142.0    0.0.0.0         255.255.255.192 U     0      0        0 eth1
*.*.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         *.*.142.1    0.0.0.0         UG    0      0        0 eth1

       Finished running tests 
+==============================================================================+


```

---

### Post by potsofdirt on 2007-10-26
Also, here is what my ~/.juniper_networks/network_connect/ dir looks like:

```

-rw-r--r-- 1 will will    118 2007-10-26 10:57 installnc.log
-rwxr--r-- 1 will will    716 2007-10-26 10:57 installNC.sh
-rw-r--r-- 1 will will   1100 2007-10-24 13:20 ive.{domain}.com.der
-rw-r--r-- 1 will will 493360 2007-10-26 10:57 libncui.so
-rw-r--r-- 1 will will      0 2007-10-26 10:57 missing.info
-rwxr--r-- 1 will will  24888 2007-10-26 10:57 ncdiag
-rw-r--r-- 1 will will   8533 2007-10-26 10:57 ncdiag.log
-rw-r--r-- 1 will will  45475 2007-10-26 10:57 NC.jar
-rws--s--x 1 root root 332044 2007-10-24 13:19 ncsvc
-rw-r--r-- 1 will will  20541 2007-10-26 10:58 ncsvc.log
-rw-r--r-- 1 will will    875 2007-10-26 10:57 ncuijava.log
-rw-r--r-- 1 will will   6179 2007-10-26 10:57 ncui.log
-rw-r--r-- 1 will will     14 2007-10-24 13:19 version.txt
-rwxr--r-- 1 will will   1632 2007-10-26 10:57 xlaunchNC.sh

```

The der file is from me trying to use the command line client.

---

### Post by zingo on 2007-10-28
Hello
I have the 1.1 version of netconnect the directory have some different files here
and the getx509certificate.sh is not part of the ncLinuxApp.jar 
I anyone have the script please share it :)

as for content in my jar file I have this
> 
[email]stzi@SEMALWS049:~/.juni[/email]per_networks/test$ jar -xf ../ncLinuxApp.jar 
[email]stzi@SEMALWS049:~/.juni[/email]per_networks/test$ ls -la
totalt 660
drwxr-xr-x 3 stzi stzi   4096 2007-10-28 11:23 .
drwxr-xr-x 4 stzi stzi   4096 2007-10-28 11:22 ..
-rw-r--r-- 1 stzi stzi    735 2006-02-10 22:06 installNC.sh
drwxr-xr-x 2 stzi stzi   4096 2006-02-10 22:06 META-INF
-rw-r--r-- 1 stzi stzi  29096 2006-02-10 22:06 ncdiag
-rw-r--r-- 1 stzi stzi 285344 2006-02-10 22:06 ncsvc
-rw-r--r-- 1 stzi stzi 320140 2006-02-10 22:06 ncui
-rw-r--r-- 1 stzi stzi     14 2006-02-10 22:06 version.txt
-rw-r--r-- 1 stzi stzi    969 2006-02-10 22:06 xlaunchNC.sh
[email]stzi@SEMALWS049:~/.juni[/email]per_networks/test$ 


pileofdirth: I assume you have version 1.2 here is version 1.1 layout

> 
[email]stzi@SEMALWS049:~/.juni[/email]per_networks$ ls -laR *
-rw-r--r-- 1 stzi stzi 269639 2006-02-11 06:06 ncLinuxApp.jar

network_connect:
totalt 660
drwxr-xr-x 2 stzi stzi   4096 2007-10-28 10:57 .
drwxr-xr-x 3 stzi stzi   4096 2007-10-28 10:57 ..
-rw-r--r-- 1 stzi stzi    380 2007-10-28 10:57 installnc.log
-rwxr--r-- 1 stzi stzi    735 2007-10-28 10:57 installNC.sh
-rw-r--r-- 1 stzi stzi      0 2007-10-28 10:57 missing_libs
-rwxr--r-- 1 stzi stzi  29096 2007-10-28 10:57 ncdiag
-rws--s--x 1 root root 285344 2007-10-28 10:57 ncsvc
-rw-r--r-- 1 stzi stzi      0 2007-10-28 10:57 ncsvc.log
-rwxr--r-- 1 stzi stzi 320140 2007-10-28 10:57 ncui
-rw-r--r-- 1 stzi stzi      0 2007-10-28 10:57 ncui.log
-rw-r--r-- 1 stzi stzi     14 2007-10-28 10:57 version.txt
-rwxr--r-- 1 stzi stzi    969 2007-10-28 10:57 xlaunchNC.sh
[email]stzi@SEMALWS049:~/.juni[/email]per_networks$ cat network_connect/version.txt 
Version: 1.1

[email]stzi@SEMALWS049:~/.juni[/email]per_networks$


---

### Post by irotas on 2007-10-28
> **bence8810 said:**
> The problem is that on our Juniper solution, if I authenticate on the website with the token, I will not see the Network Connect, nor the Windows Application Manager unless I am on the AD domain. I guess its the host checker which checks it? Any way to overcome that limitation?


I have the exact same problem! It's frustrating, because I can't even get past Step 0 to attempt the instructions described in this thread.

Has anyone found a solution to this, or at least a satisfactory explanation?


Thanks,
Adam

---

### Post by casuarina on 2007-10-30
Based on the  information in this page, I,
I wrote  a script to instaal on 7.04 and 7.1.10.

Enjoy!

[URL="http://ubuntuforums.org/attachment.php?attachmentid=48315&d=1193675395"]http://ubuntuforums.org/attachment.php?attachmentid=48315&d=1193675395
[/URL]

---

### Post by zingo on 2007-10-30
casuarina:
Really Nice, this will help a lot of people.
Someday you/we might make a .deb package of this and have in a repository maybe.

Here are some improvement ideas...

There is a sun-java6-plugin package If you add it I don't think you need the java plugin stuff (I never needed it at least)

There is also an rpm package if this is installed you have a rpm tool and probably dont need the 

sudo ln -s /bin/true /usr/bin/rpm

you get a few small packages that in this case is not needed but cleaner then a fake rpm.

It would be nice if someone made a nice gnome/KDE front end to the ncscv tool. Is there a shell-calling-gui-toolkit that one could use, like ncurses but for gnome?

---

### Post by madscientist on 2007-10-31
> **zingo said:**
> There is also an rpm package if this is installed you have a rpm tool and probably dont need the 

sudo ln -s /bin/true /usr/bin/rpmI think you'll still need this, because the package name that the netconnect script looks for is the Red Hat package name and isn't the same as the Debian/Ubuntu package name.  So, even if you have rpm installed that lookup will still fail (IIRC).

---

### Post by zingo on 2007-11-01
That is probably correct the RPM stuff seems to not be used in Version 1.1 of the scripts that I have... that why it worked for me :)

---

### Post by Gavin Fowler on 2007-11-10
I've been reading this thread for some time now,  thanks to the original information supplied by madscientist & more recently the script posted casuarina (it was useful to validate the manual steps) I now have Juniper VPN working on my Gutsy 7.10 installation. 

I do have one final question. In the information supplied by madscientist it suggests that i can reset (disable) my root password *but* every time i log into Juniper (which runs network connect) I am challenged for the root/su password (therefore i cannot disable root password  - without compromising Juniper). 

I'm worried that by having su/root enabled is a security risk. Is there anything i can do to work around (and remove) the su/root challenge response from the Juniper network connect, so i can disable the root account?

Gavin. 

Here's some information that may help diagnose my problem. 

The terminal style message i receive when starting network connect is: 

```

/home/{username}/.uniper_networks/network_connect/installNC.sh: 9: cannot open 1: No such file
/home/{username}/.uniper_networks/network_connect/installNC.sh: 9: 1: not found
Service needs to be reinstalled.
Please enter the root/su password.
Password:

```

I can confirm the file (installNC.sh) reported as missing (above) does exist prior to connecting to Juniper. A simple ls -l in the ./network_connect/ directory returns: 

```

-rw-r--r-- 1 fowler fowler   1421 2007-11-10 08:05 installnc.log
-rwxr--r-- 1 fowler fowler    716 2007-11-10 07:58 installNC.sh
-rw-r--r-- 1 fowler fowler 493328 2007-11-10 07:58 libncui.so
-rw-r--r-- 1 fowler fowler      0 2007-11-10 08:05 missing.info
-rwxr--r-- 1 fowler fowler  24888 2007-11-10 07:58 ncdiag
-rw-r--r-- 1 fowler fowler   4523 2007-11-10 07:19 ncdiag.log
-rw-r--r-- 1 fowler fowler  45470 2007-11-10 07:58 NC.jar
-rws--s--x 1 root   root   330988 2007-11-10 07:57 ncsvc
-rw-r--r-- 1 fowler fowler      0 2007-11-10 07:05 ncsvc.log
-rw-r--r-- 1 fowler fowler      0 2007-11-10 07:05 ncui.log
-rw-r--r-- 1 fowler fowler     14 2007-11-10 07:46 version.txt
-rwxr--r-- 1 fowler fowler   1637 2007-11-10 07:28 xlaunchNC.sh
-rwxr--r-- 1 root   root     1632 2007-11-10 07:25 xlaunchNC.sh.back

```

I thought perhaps the symbolic links were cause of the issue. I re ran the script supplied by casuarina, which reported: 

```

ln: creating symbolic link `./libjavaplugin_oji.so' to `/usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so': File exists
ln: creating symbolic link `/usr/bin/rpm' to `/bin/true': File exists
ln: creating symbolic link `/usr/lib/i686/cmov/libssl.so' to `libssl.so.0.9.8': File exists

```

---

### Post by Gavin Fowler on 2007-11-10
As an after thought, I've been looking at the ls -l listing from the /network_connect/ directory (see previous post). Is there any issue with 'ncsvc' being owned by root? Could this be the reason why the 'installNC.sh' script logic reports 'the service doesn't exist' and forces me through a reinstall and therefore the su/root password challenge persists on every use of Juniper?

These thoughts/ideas were realised after looking at the contents/logic of 'installNC.sh'. Apologies if this is newbe thought process :confused:

---

### Post by adamtog on 2007-11-10
Hi Gavin Fowler,

I got the same problem with root login prompt. I got rid of it by redefining the default shell (changed in Ubuntu 6.06 from /bin/bash to /bin/dash for performance).

root@ubuntu-desktop:/# ls -l /bin/sh
lrwxrwxrwx 1 root root 9 2007-11-11 07:37 /bin/sh -> /bin/dash

root@ubuntu-desktop:/# rm /bin/sh && ln -s /bin/bash /bin/sh

I haven't made up my mind if I will keep it, or just live with the prompt, because if you hit ctrl-c, ENTER (or ENTER, n, ENTER) it will work anyhow.

---

### Post by harryman01 on 2007-11-13
Thanks Guys


It work, the script works as I wanted

many thanks!!:popcorn:

---

### Post by darrenleeweber on 2007-11-16
HOWTO set up Juniper Network Connect VPN on Ubuntu Gutsy-Gibbon amd64

I used all the tricks in the original post, but gutsy-amd64 needs some modifications.

After the first installation failed, I used ldd to check the config, ie:

```

sudo ldd ~/.juniper_networks/network_connect/ncsvc

```

That helped to identify what was missing.  I had already installed some 32bit packages for gutsy-amd64, eg:

```
sudo apt-get install ia32-libs
sudo apt-get install ia32-sun-java5-bin
sudo apt-get install ia32-sun-java6-bin

```

(There is no equivalent for the ia32-sun-javaX-jre.)

For libstdc++2.10-glibc2.2, I did the following (maybe not the best way to do this, but it worked for me):

```

sudo -i
cd /usr/src
wget http://debian.oregonstate.edu/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb
dpkg-deb -x libstdc++2.10-glibc2.2_2.95.4-27_i386.deb   libstdc++2.10-glibc2.2_2.95.4-27_i386
mv libstdc++2.10-glibc2.2_2.95.4-27_i386/usr/lib/* /usr/lib32/
mv libstdc++2.10-glibc2.2_2.95.4-27_i386/usr/share/doc/libstdc++2.10-glibc2.2 /usr/share/doc/
rm -rf libstdc++2.10-glibc2.2_2.95.4-27_i386
rm libstdc++2.10-glibc2.2_2.95.4-27_i386.deb

```

For libssl symbolic links, I used:

```

sudo ln -s /usr/lib32/libssl.so.0.9.8  /usr/lib32/libssl.so.0
sudo ln -s /usr/lib32/i686/cmov/libssl.so.0.9.8 /usr/lib32/i686/cmov/libssl.so.0

```

After that, it works, hurrah!

Thanks so much for the original post, it was a life saver for me!  I still hate their flaky installation scripts that have not been updated now in years!

---

### Post by darrenleeweber on 2007-11-16
> **puntium said:**
> Did anyone manage to get this working in some form on an amd64 feisty install?

I created a 32bit chroot for firefox anyways.. and followed the instructions there. I can get it to install, but it can't ever connect. Probably something that the ncsvc service is trying to do that doesn't work because it's a 32bit chroot running on a 64bit kernel?


I just posted on how it works for me with gutsy-amd64, maybe that will help.

---

### Post by beltratc on 2007-12-02
Mad Scientist, et al,

Thanks for the great info.  I've been able to connect, but can only access servers on the vpn by IP address:  DNS doesn't seem to work.  Any ideas? 

Thanks,

beltratc

---

### Post by madscientist on 2007-12-02
Your DNS servers are managed through the /etc/resolv.conf file.  When Network Connect comes up, it should overwrite your standard /etc/resolv.conf file with a new one, that points towards the DNS server on the other side of the VPN, inside the private network: presumably that DNS server has all the local hostnames that you can't resolve outside.

So, if you can't resolve the remote hostnames that means your /etc/resolv.conf file is not being set up properly in the first place, or else is being overwritten.  Take a look at what that file looks like before you've brought up the connection (or after you take it down), then again right after the connection is made.  Compare the timestamps to see whether the VPN is overwriting this file.

It's also possible that netconnect IS writing this file, but something else is changing it again: see post #5 in this thread for some info on my situation which was similar.  But in my situation my lease expired rarely so I didn't see it that often.  It's possible yours expires more often.

---

### Post by foresto on 2007-12-11
After some fiddling, I got it working on my Gutsy installation.  I'm using sun-java6-bin instead of sun-java5-bin.  I didn't bother with the libssl or rpm symlinks.  (Actually, the latter would have been problematic because I happen to have a real copy of rpm installed, for unrelated reasons.)  I do not have a password set for root.

The first time I tried to log in, I got the xterm window asking me for a root password.  I just pressed enter, told it not to retry, and dismissed the rpm error message box.  This created and mostly populated the ~/.juniper_networks/network_connect directory.

Next, I changed to the .juniper_networks directory, and ran:
sudo install -m 6711 tmp/ncsvc network_connect/

I then edited network_connect/xlaunchNC.sh, adding an "exit 0" line near the top, followed by chmod -w network_connect/xlaunchNC.sh to keep my change from being overwritten.  (In hindsight, this may not have done anything after all.)

I had to load the "tun" kernel module by hand, like so:
sudo modprobe tun

After all this, I returned to my company's Network Connect web page, and pressed the Start button.  This time, the java app window stayed open and said I connected successfully.


I think the keys for me were manually installing ncsvc as setuid root, and manually loading the tun kernel module.  I still get prompted for the root password at login, but just pressing enter and letting that part of the script fail seems to do no harm.  I'll probably edit the scripts to skip that step, and chattr +i them as previously suggested, to get rid of the nagging.

---

### Post by cheahk on 2007-12-16
I had this working on an old notebook running Gutsy.  Then all of a sudden today, I could log in and connect, but I could not get to any of the resources at the company.  I checked everything like "netstat -rn" and "/etc/resolv.conf", and sure enough, they were correct.

I finally found the problem.  It was the "~/.juniper_networks/network_conenct/ncsvc.log" file that had grown too big, about 2.4 GB in size (or something).  I just did a "> ncsvc.log" to zero it out, and everything is working fine again.

Does anyone know of an elegant way to rotate this file, or even to turn off debugging/logging to this file?  

-K

---

### Post by QettoE on 2007-12-19
I'm kinda late, but have your administrator change your IVE box application from Windows to Java and everything will work.

---

### Post by Matt Waddell on 2008-01-04
Perhaps nobody cares anymore, but i was wondering if anyone has had any luck getting the Secure Application Manager (part of IVE) to work under wine.  I've had some limited success logging into the vpn https gateway with IE + wine, as well as getting the SAM installed and running (under wine as well).  Although the SAM loads and connects to the VPN, it doesn't appear to tunnel any traffic generated by other apps run under wine (i.e. remote desktop).  I'm unable to resolve internal DNS registered names, nor am I able to connect directly to IP addresses.  My guess is that this has something to do with wine's winsock implementation.

When I try to enable DNS tunneling (I forget what the button is called) (enabled in one of the "Advanced" tabs of the SAM config systray program), I see this being printed to stdout by wine:

BTW: I'm using wine-0.9.33

fixme:winsock:WSCInstallNameSpace (L"Juniper Secure DNS (Top)" L"c:\\Program Files\\Juniper Networks\\Secure Application Manager\\gapsp.dll" 0x0000000c 0x00000000 {e90a7329-700e-4312-abc0-9b384bbb53bf}) Stub!

It's possible that this is wine-unimplemented winsock function is essential.  

I've also noticed some other differences between running the SAM in windows and through wine.  For one, the Protocol Catalog list (again in one of the Advanced tabs of the SAM config systray program) is completely empty when run under wine.  When run under windows this list is populated with protocols which are implemented in the following DLLs:

mswsock.dll
rsvpsp.dll
winrnr.dll
samnsp.dll


Anyhow...  That's all I've been able to figure out for now.  Perhaps someone else has had luck with this.  I want my company to support the linux client too :-((((

---

### Post by flovo77 on 2008-01-04
Hi all, 'Installation check failed' took me about an hour to figure out...

[LIST]
[*]fresh Feisty/Gutsy (won't matter anyway) installation
[*]Network Connect is unable to connect and ends up with 'connection failed'
[*]The diagnosis message contains 'Installation check failed', as reported in post 36 and post 99
[/LIST]

In my case, not using a /tmp symlink pointing to a directory at my crypto fs anymore is the woraround, see [http://www.juniperforum.com/index.php/topic,5454.0.html](http://www.juniperforum.com/index.php/topic,5454.0.html) and [http://www.juniperforum.com/index.php/topic,5455.0.html](http://www.juniperforum.com/index.php/topic,5455.0.html).

=> Network Connect fails if /tmp and /etc are mounted on different partitions!
Florian

see
> **arecibo said:**
> Hi, I am trying to get network connect working on Debian and found this page. I followed the instructions. The network connect dialog popped up but I couldn't connect. The diagnosis message indicates the NC installation check failed. The NC service is not running. Anyone has idea how to fix this problem?

Thanks!

---

### Post by theanswriz42 on 2008-01-14
> **darrenleeweber said:**
> HOWTO set up Juniper Network Connect VPN on Ubuntu Gutsy-Gibbon amd64

I used all the tricks in the original post, but gutsy-amd64 needs some modifications.

After the first installation failed, I used ldd to check the config, ie:

```

sudo ldd ~/.juniper_networks/network_connect/ncsvc

```

That helped to identify what was missing.  I had already installed some 32bit packages for gutsy-amd64, eg:

```
sudo apt-get install ia32-libs
sudo apt-get install ia32-sun-java5-bin
sudo apt-get install ia32-sun-java6-bin

```

(There is no equivalent for the ia32-sun-javaX-jre.)

For libstdc++2.10-glibc2.2, I did the following (maybe not the best way to do this, but it worked for me):

```

sudo -i
cd /usr/src
wget http://debian.oregonstate.edu/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb
dpkg-deb -x libstdc++2.10-glibc2.2_2.95.4-27_i386.deb   libstdc++2.10-glibc2.2_2.95.4-27_i386
mv libstdc++2.10-glibc2.2_2.95.4-27_i386/usr/lib/* /usr/lib32/
mv libstdc++2.10-glibc2.2_2.95.4-27_i386/usr/share/doc/libstdc++2.10-glibc2.2 /usr/share/doc/
rm -rf libstdc++2.10-glibc2.2_2.95.4-27_i386
rm libstdc++2.10-glibc2.2_2.95.4-27_i386.deb

```

For libssl symbolic links, I used:

```

sudo ln -s /usr/lib32/libssl.so.0.9.8  /usr/lib32/libssl.so.0
sudo ln -s /usr/lib32/i686/cmov/libssl.so.0.9.8 /usr/lib32/i686/cmov/libssl.so.0

```

After that, it works, hurrah!

Thanks so much for the original post, it was a life saver for me!  I still hate their flaky installation scripts that have not been updated now in years!

Works like a charm on my Gutsy 64 bit install. Thanks man!

---

### Post by techno-wiz on 2008-01-17
Any chance we could get a script for the amd64 install like the one posted for 32 bit? :)

---

### Post by wiryu on 2008-02-04
> **darrenleeweber said:**
> HOWTO set up Juniper Network Connect VPN on Ubuntu Gutsy-Gibbon amd64

I used all the tricks in the original post, but gutsy-amd64 needs some modifications.

After the first installation failed, I used ldd to check the config, ie:

```

sudo ldd ~/.juniper_networks/network_connect/ncsvc

```

That helped to identify what was missing.  I had already installed some 32bit packages for gutsy-amd64, eg:

```
sudo apt-get install ia32-libs
sudo apt-get install ia32-sun-java5-bin
sudo apt-get install ia32-sun-java6-bin

```

(There is no equivalent for the ia32-sun-javaX-jre.)

For libstdc++2.10-glibc2.2, I did the following (maybe not the best way to do this, but it worked for me):

```

sudo -i
cd /usr/src
wget http://debian.oregonstate.edu/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb
dpkg-deb -x libstdc++2.10-glibc2.2_2.95.4-27_i386.deb   libstdc++2.10-glibc2.2_2.95.4-27_i386
mv libstdc++2.10-glibc2.2_2.95.4-27_i386/usr/lib/* /usr/lib32/
mv libstdc++2.10-glibc2.2_2.95.4-27_i386/usr/share/doc/libstdc++2.10-glibc2.2 /usr/share/doc/
rm -rf libstdc++2.10-glibc2.2_2.95.4-27_i386
rm libstdc++2.10-glibc2.2_2.95.4-27_i386.deb

```

For libssl symbolic links, I used:

```

sudo ln -s /usr/lib32/libssl.so.0.9.8  /usr/lib32/libssl.so.0
sudo ln -s /usr/lib32/i686/cmov/libssl.so.0.9.8 /usr/lib32/i686/cmov/libssl.so.0

```

After that, it works, hurrah!

Thanks so much for the original post, it was a life saver for me!  I still hate their flaky installation scripts that have not been updated now in years!

Thanks a lot man! It works for me.

---

### Post by HardDisc on 2008-02-10
OK... I'm running Gutsy AMD64 and followed all the instructions in this post  (and then some!!!). The question I have is how are you folks getting Java5/6 running in the first place???? I install them and my Firefox can't find the plugins so when I bring up the company VPN site I can't even get the Juniper stuff to download because "JRE is missing/Java not installed". I Googled all over and everyone has problems with Java5/6 on Gusty-64; according to those posts the only solution is IcedTea.  I tried IcedTea and even though that seems to be working in Firefox (Java test at Sun's website comes up just fine) Juniper - at least the ver my co. uses - won't launch with IcedTea. How are you folks getting Java5/6 to run Firefox 64-bit in the first place??? - BTW, I do have the ia32-libs installed.

Any ideas!?!?!?!?!?!?

I had Juniper working just fine on my old notebook running i386 Feisty but since the boss approved a new NB with Core2Dual I figured I'd upgrade to Gutsy AMD64. Everything else is working... this is my last hurdle!!!!!! AAAAARRRRRGGGGGGHHHHHHH.

---

### Post by cheahk on 2008-02-13
I got this working with no issues on Gutsy.

I did everything the OP did, but added:

sudo ln -s /usr/lib/i686/cmov/libssl.so.0 /lib/libssl.so.0

For some reason, it didn't work until I added the symlink.

Basically, it's:
```
# sudo -s
# aptitude install openssl libstdc++2.10-glibc2.2 sun-java5-bin sun-java5-jre
# ln -s /bin/true /usr/bin/rpm
# ln -s libssl.so.0.9.8 /usr/lib/i686/cmov/libssl.so.0
# ln -s /usr/lib/i686/cmov/libssl.so.0 /lib/libssl.so.0
# passwd
(enter your su password)
# exit
```

It's just a matter restarting firefox and logging in.

-K

---

### Post by HardDisc on 2008-02-13
Yep... I already tried that (I think it was mentioned earlier on in the post)... I also tried:

sudo ln -s /usr/lib32/libcrypto.so.0.9.8  /usr/lib32/libcrypto.so.0
sudo ln -s /usr/lib32/i686/cmov/libcrypto.so.0.9.8 /usr/lib32/i686/cmov/libcrypto.so.0

because I saw that in this or some other post (my head is swimming from all the posts I've searched).

---

### Post by zefew on 2008-02-14
Where do you obtain "ncsvc"  or access "network connect" in the first place?
I installed all the necessary packages and symlinks, but I don't see any "network connect" button/link even after having logged-in through firefox. It just tries to launch up the SAM just like on windows ie6...

---

### Post by muellthos on 2008-02-27
@zefew,

it's a matter of rights you have on the Juniper Secure Access system, to which you connect. There are 2 methods, SAM (Secure Access Manager) and NC (Network Connect). SAM is for allowing a particular Client Server application to be tunneled thru SSL (think of a kind of port forwarding), NC is more like an IPSEC tunnel, but over SSL. The administrator of the Juniper SA decides on your access rights. So If you haven't granted permission for NC, but for SAM, you can't use it. I don't know if someone has implemented SAM on Linux, but I don't think so.

Thomas

---

### Post by zefew on 2008-02-28
> **muellthos said:**
> @zefew,

it's a matter of rights you have on the Juniper Secure Access system, to which you connect. There are 2 methods, SAM (Secure Access Manager) and NC (Network Connect). SAM is for allowing a particular Client Server application to be tunneled thru SSL (think of a kind of port forwarding), NC is more like an IPSEC tunnel, but over SSL. The administrator of the Juniper SA decides on your access rights. So If you haven't granted permission for NC, but for SAM, you can't use it. I don't know if someone has implemented SAM on Linux, but I don't think so.

Thomas

Though your post pretty much closes my hopes to be able to connect to one of the the company VPNs (it has many..) on linux, at least I'm clear on the issues. Thanks, Thomas.

---

### Post by aguevarra on 2008-03-19
I've had trouble getting this working in gutsy amd64. To get this working, I did:

[LIST]
[*]...not use the installed firefox. I downloaded one from [http://getfirefox.com](http://getfirefox.com)
[*]Installed the java5 packages
```
sudo apt-get install ia32-sun-java5-bin sun-java5-bin sun-java5-jdk sun-java5-jre
```
[*]linked the java plugin to the mozilla plugin directory
```
cd ~/.mozilla/plugins
ln -sf /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.13/jre/plugin/i386/ns7/libjavaplugin_oji.so .
```
[/LIST]

---

### Post by beltratc on 2008-03-23
PoD,

Did you ever figure out your timeout issue?

Thanks,

beltratc

---

### Post by beltratc on 2008-03-24
> **casuarina said:**
> Based on the  information in this page, I,
I wrote  a script to instaal on 7.04 and 7.1.10.

Enjoy!

[URL="http://ubuntuforums.org/attachment.php?attachmentid=48315&d=1193675395"]http://ubuntuforums.org/attachment.php?attachmentid=48315&d=1193675395
[/URL]

Everyone - thanks for the fine work on this thread! 

I've made a fresh install of 7.10  and used this script to setup Juniper.  It works great - for 20 minutes then times out. 

Prior to it timing out I noticed that the Network Connect dialog box shows COMPRESSION=NULL.  Right at the 20 minute mark, the COMRESSION=DEFLATE and I no longer can access the VPN.

Any ideas?  

Thanks, 

Beltratc

---

### Post by madscientist on 2008-04-01
I got tired of messing with my browser to enable/disable the VPN so, based on my own investigation and some info posted by others, I created a shell script that invokes the VPN.  I put a Hardy beta release up into a VMWare instance and wrote a how-to guide for getting it working, with a few screenshots.

I've used my script on Gutsy (Ubuntu 7.10) as well, although I did it by hand rather than follow those directions.

Find the directions here: [http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html)

Let me know if you have problems!

---

### Post by TheFluffyOne on 2008-04-12
Great how-to, madscientist. Nicely summarises all of the information needed to get things running.

Unfortunately after upgrading my laptop from Gutsy to the current beta of Hardy, Network Connect stopped working.

All of the components are in place, but ncsvc reports an error:

```
./ncsvc: symbol lookup error: ./ncsvc: undefined symbol: __builtin_new
```

I'm guessing there's a shared library that's been updated/modified in Hardy. Anyone else seeing this issue?

---

### Post by jcpowermac on 2008-04-26
Yeah I had the exact same issue.  

I tried to just link the new library but that didn't work.

I don't know if it was wise but this is how I fixed it.

Download libstdc++2.10-glibc2.2_2.95.4-27_i386.deb get it from [here]("http://http.us.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb")

```
sudo dpkg -i libstdc++2.10-glibc2.2_2.95.4-27_i386.deb
```

---

### Post by tc7 on 2008-04-28
Excellent how-to, madscientist. However ... no joy for me after Gutsy upgrade to Hardy 8.04.

I think my VPN host requires a cookie or something else from the browser as I couldn't get the authentication to work using your script. I'm reasonably confident my: HOST/USER/CERT/REALM parameters are correct as the applet loads (it doesn't if REALM is incorrect for example), but authentication fails, eg:

> ncapp> Failed to connect/authenticate with IVE. Error 104
ncapp> Incorrect credentials. Please check the username/password/realm.


The following borrows from the past few posts.

Initially I had the same issue as fluffy (above), eg:
```
./ncsvc: symbol lookup error: ./ncsvc: undefined symbol: __builtin_new

```

The suggestion from powermac worked fine, eg:
```
sudo dpkg -i libstdc++2.10-glibc2.2_2.95.4-27_i386.deb

```

At this point I get:
```
~/.juniper_networks/network_connect/ncsvc --version
Juniper Network Connect Server for Linux.
Version         : 1.2
Release Version : 5.3-0-Build10197
Build Date/time : Feb 15 2006 18:21:55 
Copyright 2002-2006 Juniper Networks

```

The problem now is the incompatible shell scripts provided. I overcame this by modifying the originals and using chattr to prevent nc from overwriting with the originals (I think from an earlier post).

I created modified "source" copies in: ~/.juniper_networks/ and created a new shell script to update them, eg:

1) ~/.juniper_networks/src_installNC.sh 

```
echo "Ubuntu compatible version of installNC.sh"

# Install the service

echo "executing $0 with params: $*" 

#if(("$#"<"1"))
if [ "$#" -lt "1" ]
then
        echo "Insufficiant number of parameters"
        echo "$0 <install dir>"
        exit;
fi

if [ -e "$1/ncsvc" ] 
then
        echo "Service already installed"
        ok="done"
else
        echo "Service needs to be installed for the first time."
        ok="try"
fi

until [ "$ok" = "done" ]
do
        echo "Please enter the root/su password"
        su root -c "install -m 6711 -o root $1/../tmp/ncsvc $1/ncsvc"
        if [ "$?" -eq "0" ] 
        then
                cp $1/../tmp/version.txt $1/
                ok="done"
                rm -rf $1/../tmp
        else 
                echo "Invalid su password and/or Unable to install ncsvc"
                echo -n "Do you want to try again (enter y to try again):";
                read choice;
                if [ "$choice" != "y" ]
                then 
                        ok="done"
                fi
        fi
done
chmod 744 $1/ncdiag

```

2) ~/.juniper_networks/src_xlaunchNC.sh 
```
#!/bin/sh
# launch to install the service
# 20051220 : Javeed : Added -n to modprobe for dry run. We dont want to insmod, just check if tun
#                                               is available.

echo "Ubuntu compatible version of xlaunchNC.sh"

echo "executing $0 with params: $*"

#if(("$#"<"1"))
if [ "$#" -lt "1" ]
then
        echo "Insufficient number of params"
        echo "$0 <install dir> "
        echo "$*";
        exit
fi

#echo "$*";

#moved code from installNC.sh to here so that we call xterm only if needed.
flag=1

if [ -e "$1/ncsvc" ] 
then
        if [ -e "$1/version.txt" ] 
        then 
                old_version=`grep -i "Version" $1/version.txt | cut -f 2 -d " "`;
                new_version=`grep -i "Version" $1/../tmp/version.txt | cut -f 2 -d " "`;
#               echo "$old_version == $new_version"
                if [  "$old_version" \< "$new_version"  ]
                then
                        echo "Need to install the new service"
                else
                        flag=0;
                        echo "No difference found"
                fi
        fi
else
        echo "Service needs to be installed for the first time"
fi
if [ "$flag" -eq "1" ]
then
    echo "calling $1/installNC.sh" >> $0.log
    chmod 744 $1/installNC.sh
    `xterm -e $1/installNC.sh $1`
fi

#export LD_LIBRARY_PATH=/usr/X11R6/lib

# no need to check for ncui. Have to check for openssl package and tun driver.
#ldd $1/ncui | grep "not found" | tr -d "\t" | cut -d " " -f 1 | tee $1/missing_libs
# check if modprobe can locate the tun module. 
#Adding dry run option we dont want to insmod, just check if tun is available

rm -rf $1/missing.rpt
/sbin/modprobe -n tun 1> $1/missing.info
if [ "$?" -ne "0" ]
then
    echo "Modprobe for Tun driver failed." > $1/missing.rpt
#    rpm -q tun 1> $1/missing.rpt
fi
#check if openssl is installed
rpm -q openssl 1>> $1/missing.info
if [ "$?" -ne "0" ]
then
    echo "RPM query for openssl failed." >> $1/missing.rpt
fi

```
3) ~/bin/juniper_update:
```
#:!/bin/bash

ncpath="$HOME/.juniper_networks/network_connect"
src_installNCsh="${ncpath}/../src_installNC.sh"
src_xlaunchNCsh="${ncpath}/../src_xlaunchNC.sh"

if [ -d ${ncpath} ];
then
  if [ -f ${src_installNCsh} ] && [ -f ${src_launchNCsh} ];
  then
    if [ -x "${ncpath}/ncsvc" ];
    then
      # display ncsvc version
      ${ncpath}/ncsvc --version
      # enable access to scripts
      sudo chattr -V -i ${ncpath}/installNC.sh
      sudo chattr -V -i ${ncpath}/xlaunchNC.sh
      if [ -w "${ncpath}/installNC.sh" ] && [ -w "${ncpath}/xlaunchNC.sh" ];
      then
        # overwrite with dummy version
        cp -v ${src_xlaunchNCsh} ${ncpath}/installNC.sh
        cp -v ${src_installNCsh} ${ncpath}/xlaunchNC.sh
        # prevent dummy scripts being overwritten
        sudo chattr -V +i ${ncpath}/installNC.sh ${ncpath}/xlaunchNC.sh
      else
        echo "unable to overwrite: ${ncpath}/installNC.sh, OR: ${ncpath}/xlaunchNC.sh"
        echo "must run using: sudo $0"
      fi
    else
      echo "Could not execute: ${ncpath}/ncsvc. Please ensure juniper network connect is \"installed\" first"
    fi
  else
    echo "Could not find: ${src_installNCsh}, OR: ${src_xlaunchNCsh}"
  fi
else
  echo "ncpath is invalid: ${ncpath}"
fi

```

I tried to modify the originals just enough to make it work.

Now the network connect applet loads as it always used to with Gutsy (via Firefox 3 beta5 and using a similar approach).

Thanks again to all the above - it's quite a relief to have VPN access once again!

---

### Post by Kethinov on 2008-04-29
For people who upgraded to Hardy and stuff is now broken (app will not init): disable the GCJ mozilla plugin and install the official java mozilla plugin instead.

---

### Post by TheoGB on 2008-05-04
> **madscientist said:**
> I got tired of messing with my browser to enable/disable the VPN so, based on my own investigation and some info posted by others, I created a shell script that invokes the VPN.  I put a Hardy beta release up into a VMWare instance and wrote a how-to guide for getting it working, with a few screenshots.

I've used my script on Gutsy (Ubuntu 7.10) as well, although I did it by hand rather than follow those directions.

Find the directions here: [http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html)

Let me know if you have problems!

Hi,

I am a big newbie here but I need to set this up so I can home work from my Vista x64 box. I.e. I'm running Ubuntu on VirtualBox and having issues.

I'm running the Version 8 (Hardy something?) of Ubuntu. Now reading that I am totally unable to Google up a way to make sense of this bit:

> So, first download the junipernc script and put it somewhere on your PATH; I typically create ~/bin and add that to my PATH for these sorts of things but it's up to you.

So, I discovered from the Ubuntu manual that scripts are normally in /etc. I went into there and found a bash_completion file that looked similar so I 

sudo cp bash_completion junipernc

then I 
sudo gedit junipernc

deleted the existing stuff and copied in all the junipernc code found at that link.

However, the line about changing the path totally confuses me. I can't work out how to do that bit.

Cheers
Theo

**Edit:** Hmm. I tried just running the junipernc script with sudo sh inside the etc folder and it ran as expected but when I put in my password in the 'SecureID' bit it just says the VPN is exiting then asks me if I want to try it again. This just seems to be a looping situation now.

This is all really rather depressing... :(

---

### Post by madscientist on 2008-05-04
> **TheoGB said:**
> Hi,

I am a big newbie here but I need to set this up so I can home work from my Vista x64 box. I.e. I'm running Ubuntu on VirtualBox and having issues.Wow.  You're really jumping in on the deep end.  Networking using virtual machines is not always straightforward, even for people who are very knowledgeable about it.

Before we spend a lot of time on this, can you give us more general information about what you want to be able to do if everything were working correctly?  If what you really want to do is have your Vista system talk to your work environment via the VPN, then setting up the VPN in Ubuntu in a virtual machine on Vista will not really get you there.  Not without a LOT of very tricky work with routing etc. that I'm certainly not prepared to describe to you, especially on Windows (I haven't owned a machine running Windows since Windows 3.1 back in the 90's).  If that's what you want to do the only realistic way of doing it is to run Ubuntu as the main OS, then use VMWare or similar to run Vista as the virtual, or guest, OS.  In this mode you can set up Vista to share the network connection of the host OS (Ubuntu), so when Ubuntu is connected to VPN, Vista can share that connection.

If, instead, what you want to do is use Ubuntu to connect to the VPN at work but you don't need the host OS (Vista) to connect, then we can hopefully get you going.

It may still be a bit tricky though: VPNs on virtual machines can suffer from a variety of issues.

My advice is this: I'll tell you what you've done wrong so far and get you set up right.  If it still doesn't work I recommend that you use a LiveCD or Wubi install of Ubuntu and see if you can get that working just to prove that it can be done.

> **TheoGB said:**
> So, I discovered from the Ubuntu manual that scripts are normally in /etc. I went into there and found a bash_completion file that looked similar so I 

sudo cp bash_completion junipernc

then I 
sudo gedit junipernc

deleted the existing stuff and copied in all the junipernc code found at that link.Hrm.  That's really... not right :-).  I think you must have misread/misunderstood the comment in the Ubuntu manual.  Configuration files (and sometimes scripts) are normally found in /etc.  However, scripts that you would run as commands (like this one) are not in /etc.  The system commands live in one of the directories /bin, /usr/bin, /sbin, or /usr/sbin (it's not worthwhile at this point to explain the differences between these, which are all down to convention rather than requirements anyway).

In this case, though, the most important thing you've missed is that the script does NOT need to be run as root (the administrative account; using sudo).  You should run it as yourself (not using sudo).  It really doesn't belong in a system directory such as /etc, /usr/bin, etc.  It should live in your own home directory (/home/<username>).

My web page recommends making a /home/<username>/bin directory and putting it in there, then adding that to your PATH.  Don't worry about that if you don't understand it.  Instead, do this:

[LIST=1]
[*]Download the script from my page and put it on your Desktop.
[*]Right-click on the script icon on your Desktop, and select Properties.
[*]Choose the "Permissions" tab and check the box "Execute: allow executing file as program" (note: be very careful about this in general... only do this for files you trust).
[/LIST]

Now the file is executable (you can run it as a command).  After we get it working we'll make an icon for it, but for now run it by double-clicking on it.  You'll get a dialog asking you what to do; choose "Run in terminal" (so we can see any errors/messages).  You should get a terminal window, followed by the requests for information as described on my page.

Follow the directions and see where you end up.  Post any odd messages that are printed on the terminal window (beware it will go away automatically when you quit the script, so cut/paste them somewhere else first).

---

### Post by TheoGB on 2008-05-04
Hey cheers,

Basically: my computer is at work. If I want to work at home I use an addresses that is extranet.mywork.tld. This runs a bit of Java and then lets me click START for a Juniper Networks connection to put me on the network.

Then I start a remote desktop session to connect to my computer, refering to it by name as if I were on the network (which I now am).

All this would be fine but Vista x64 doesn't support this so in my new computer I thought I'd just run VirtualBox with a Linux flavour and run remote desktop from there; further down the line I want this VB to be my web development machine to more closely match my online sites rather than run stuff in Windows.


Anyway, initially I installed Ubuntu 7 and I got all this working, I think by following the first post in this thread. Y'know, I was going to mark it all down and I just didn't get a chance. :( Anyway, it connected and I got remote desktop fine. BUT, I was locked at 1024x768 and my native res is 1680x1050.

So I attempted to set this and screwed the display up so it didn't even work any more. I deleted that partition then discovered about Guest Additions. I tried again with Ubuntu 7 and used Guest Additions and the following change to the xorg.conf (from a different forum)

> 
Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"VESA driver (generic)"
        Driver      "vboxvideo"
	BusID		"PCI:0:2:0"
	Screen 0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname 	"Monitor 1680x1050"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-76
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes "1680x1050" "1280x1024" "1024x768"
	EndSubSection
EndSection


Note I had to manually do this because there was no way to select using the X-Windows stuff.


Okay...next hell: I got all this working but (and via a few more wipe downs and reinstalls) I have discovered that Guest Additions screws up Firefox. How? It causes every Java initiation to ask if I trust the applet and once I say yes, it seems that it gives up anyway and doesn't do anything.

GRRRRRR.

So I thought I'd give Ubuntu 8 a try. This doesn't exhibit this Firefox problem...it has a different one. The Java runs but Juniper Networks never boots, even after I did the original changes in the start of this thread.


So at the moment I've wiped down that Ubuntu 8 session already and got a bit frustrated. Essentially all I want is:
- Ubuntu to run at my full screen resolution
- extranet.mywork.tld to load up.
- Juniper networks to connect.
- Remote desktop to my work computer so I can work at home from this Vista x64 machine.


When all that's done I'll get around to installing:
- Apache
- MySQL
- PHP
- Ruby on Rails

(Wowsers!)

Any advice on the first phase is much appreciated. For now I'll start a new Ubuntu 8 version and do what you've said.

Cheers
Theo
-

---

### Post by TheoGB on 2008-05-06
Hmm.

Okay, well I did it correctly this time. The script runs, takes in the appropriate details, though having never been asked a 'Service Realm' I just took the default one that was there. I put in the password, it thinks, and then says "VPN has exited successfully" but I see no signs of Juniper Networks connect actually running. 

However, I'm not sure it ever installs on my system anywhere. Odd. I'm going to give this another try from Ubuntu 7 and get back to you, because the way Firefox acts in each system is very different...

---

### Post by Baltazar72 on 2008-05-16
I have the same trouble as TheoGB, I think. Running madscientist's script. Trouble was that I was running it with sudo, i got some java errors.
```
baltazar@baltazar:~/.bin$ sudo sh juniper.sh
Exception in thread "AWT-EventQueue-0" java.lang.ExceptionInInitializerError
	at NC$3.run(NC.java:1282)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
Caused by: java.lang.ArrayIndexOutOfBoundsException: 3
	at JavaNC.<clinit>(NC.java:443)
	... 9 more

```
 running without sudo NetworkConnect starts, but alerts me with "Invalid Credentials"
```
baltazar@baltazar:~/.bin$ ./juniper.sh 
Searching for ncsvc in current working directory
Searching for ncsvc in /home/baltazar/.juniper_networks/network_connect done.
ncapp> Failed to connect/authenticate with IVE. Error 104
ncapp> Incorrect credentials. Please check the username/password/realm.

```

I will have to see why with IT staff I guess....Because NetworkConnect opens, but complains about credentials..

---

### Post by elenctic on 2008-05-16
I just upgraded to 8.04 and am using madscientist's script to connect.  I login and am authenticated just fine, but after about a minute the connection dies.  Has anyone else seen and/or fixed this problem?  Any help would be appreciated.

---

### Post by sauravghosh on 2008-05-16
> **elenctic said:**
> I just upgraded to 8.04 and am using madscientist's script to connect.  I login and am authenticated just fine, but after about a minute the connection dies.  Has anyone else seen and/or fixed this problem?  Any help would be appreciated.

I don't know if this is your problem, but we had a similar problem at our workplace -- but it was on windows systems, and it was caused by the new iTunes, which installed the Bonjour service, which interfered with the Juniper client.  It displayed exactly the same symptoms -- connection began fine, but died within the first minute.

I haven't read through this entire thread yet, but I was looking for some assistance with Juniper on AMD64 Hardy (I've installed the 32-bit Firefox and Java plug-in, and tried the script, but the installNC.sh script keeps saying the service needs to be installed, and if I can get it to go forward by supplying a root password -- after actually making one -- the client complains that it 'Can't find required libraries'.  Any idea which libraries it needs, or how I can find out?  I also installed libstdc++2.10-glibc2.2_2.95.4-27_i386.

---

### Post by psorcerer on 2008-05-18
Hi, everybody. The recent openssl update to Hardy broke the client totally. All hail Juniper!

```

java.io.EOFException
	at java.io.DataInputStream.readInt(DataInputStream.java:375)
	at sun.security.provider.JavaKeyStore.engineLoad(JavaKeyStore.java:628)
	at sun.security.provider.JavaKeyStore$JKS.engineLoad(JavaKeyStore.java:38)
	at java.security.KeyStore.load(KeyStore.java:1185)
	at com.sun.deploy.security.DeploySSLCertStore$1.run(DeploySSLCertStore.java:153)
	at java.security.AccessController.doPrivileged(Native Method)
	at com.sun.deploy.security.DeploySSLCertStore.loadCertStore(DeploySSLCertStore.java:136)
	at com.sun.deploy.security.DeploySSLCertStore.load(DeploySSLCertStore.java:107)
	at com.sun.deploy.security.DeploySSLCertStore.load(DeploySSLCertStore.java:92)
	at com.sun.deploy.security.ImmutableCertStore.load(ImmutableCertStore.java:43)
	at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:324)
	at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:954)
	at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:123)
	at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:516)
	at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:454)
	at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
	at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1096)
	at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1123)
	at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1107)
	at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:405](www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:405))
	at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166](www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166))
	at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:977](www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:977))
	at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234](www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234))
	at com.sun.deploy.net.HttpUtils.followRedirects(HttpUtils.java:45)
	at com.sun.deploy.net.BasicHttpRequest.doRequest(BasicHttpRequest.java:169)
	at com.sun.deploy.net.BasicHttpRequest.doGetRequestEX(BasicHttpRequest.java:63)
	at com.sun.deploy.net.DownloadEngine.isUpdateAvailable(DownloadEngine.java:709)
	at com.sun.deploy.cache.DeployCacheHandler.get(DeployCacheHandler.java:133)
	at sun.net.[www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:681](www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:681))
	at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:158](www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:158))
	at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:977](www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:977))
	at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234](www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234))
	at sun.plugin.PluginURLJarFileCallBack.downloadJAR(PluginURLJarFileCallBack.java:72)
	at sun.plugin.PluginURLJarFileCallBack.access$000(PluginURLJarFileCallBack.java:46)
	at sun.plugin.PluginURLJarFileCallBack$1.run(PluginURLJarFileCallBack.java:106)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.plugin.PluginURLJarFileCallBack.retrieve(PluginURLJarFileCallBack.java:94)
	at sun.net.[www.protocol.jar.URLJarFile.retrieve(URLJarFile.java:186](www.protocol.jar.URLJarFile.retrieve(URLJarFile.java:186))
	at sun.net.[www.protocol.jar.URLJarFile.getJarFile(URLJarFile.java:50](www.protocol.jar.URLJarFile.getJarFile(URLJarFile.java:50))
	at sun.net.[www.protocol.jar.JarFileFactory.get(JarFileFactory.java:68](www.protocol.jar.JarFileFactory.get(JarFileFactory.java:68))
	at sun.net.[www.protocol.jar.JarURLConnection.connect(JarURLConnection.java:104](www.protocol.jar.JarURLConnection.connect(JarURLConnection.java:104))
	at sun.plugin.net.protocol.jar.CachedJarURLConnection.connect(CachedJarURLConnection.java:189)
	at sun.plugin.net.protocol.jar.CachedJarURLConnection.getJarFileInternal(CachedJarURLConnection.java:144)
	at sun.plugin.net.protocol.jar.CachedJarURLConnection.getJarFile(CachedJarURLConnection.java:90)
	at sun.misc.URLClassPath$JarLoader.getJarFile(URLClassPath.java:647)
	at sun.misc.URLClassPath$JarLoader.access$600(URLClassPath.java:538)
	at sun.misc.URLClassPath$JarLoader$1.run(URLClassPath.java:605)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.misc.URLClassPath$JarLoader.ensureOpen(URLClassPath.java:597)
	at sun.misc.URLClassPath$JarLoader.<init>(URLClassPath.java:559)
	at sun.misc.URLClassPath$3.run(URLClassPath.java:331)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.misc.URLClassPath.getLoader(URLClassPath.java:320)
	at sun.misc.URLClassPath.getLoader(URLClassPath.java:297)
	at sun.misc.URLClassPath.getResource(URLClassPath.java:167)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:192)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:155)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:127)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:632)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:786)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:2108)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:715)
	at sun.applet.AppletPanel.run(AppletPanel.java:369)
	at java.lang.Thread.run(Thread.java:619)
```

---

### Post by marcw on 2008-05-18
> **psorcerer said:**
> Hi, everybody. The recent openssl update to Hardy broke the client totally. All hail Juniper!

Sorry to hear of your exception, but I don't think there's necessarily anything wrong with the Juniper client.  My Hardy is up to date with all the recent SSH and SSL updates and doing Network Connect it continues to work fine for me doing 32bit browser and java on 64bit Hardy.

---

### Post by psorcerer on 2008-05-18
> **marcw said:**
> Sorry to hear of your exception, but I don't think there's necessarily anything wrong with the Juniper client.  My Hardy is up to date with all the recent SSH and SSL updates and doing Network Connect it continues to work fine for me doing 32bit browser and java on 64bit Hardy.

Hmm, it indeed works by running NC.jar but doesn't work from Firefox java 1.6 plugin. The most funny thing it was working fine before openssl update, both ways...strange.

---

### Post by stasyan on 2008-05-28
Hi,

I'm trying to connect to my work's VPN from UBUNTU 8.04, Juniper NC 1.2. When i launch  NC it says i'm connected, i get the internal IP but can't access any resource on the VPN. Firewall is disabled.

Diagnostics say ping to Nameservers failed.

I have no problem connecting from computer running windows though.

Both computers connected to the internet the same way.

I spent days trying to figure this out. Really need help!

Thanks

---

### Post by madscientist on 2008-05-28
What diagnostics are you talking about that say "ping to nameservers failed"?

It might be that the DNS server configuration by your VPN provider is wrong.  But it might also be that the VPN is not working, so that's why you can't access the DNS servers.  Here are some debugging steps that will help us discover what's going on.

First, find the IP address of a host on the private network you're trying to connect to and use that instead of the hostname.  You can replace the hostname in a URL ([http://hostname/](http://hostname/)...) or ssh with an IP address and it should work.  If it does, then it's a DNS problem.

If it doesn't, then the VPN itself is not configured properly.  If that's the case it will require more careful examination.

If using the IP address works, then use the "host" command to see if you can resolve hostnames.  Open a terminal (Applications -> Accessories -> Terminal) and run "host gnu.org" for example.  You should *immediately* get back:
```
$ host gnu.org
gnu.org has address 199.232.41.10
```

If you don't get that then you definitely can't access your DNS servers.

If you CAN resolve gnu.org, then try the same trick with one of your internal systems.  Does that resolve?  If not, then somehow the VPN setup is not changing your /etc/resolv.conf file for you or else something is changing it back again.  Does it work for a while but then stop working?  If so then it's almost certainly your DHCP server overwriting your /etc/resolv.conf file when you renew your lease.

Look at the contents of /etc/resolv.conf; you should see IP addresses in there for servers in your private network, rather than for your ISP.  If you don't know for sure, just look at the contents before you start the VPN and after: they should be different.

I guess that's enough for now... we can't do much more trouble-shooting-wise until we find the answers to these questions.

---

### Post by webs05 on 2008-05-28
I got a problem running the script...

So I downloaded the script from Mad Scientist's website. I called it juniper.sh. I run the script using the following command:
> sudo sh junipernc.sh
This brings up this error message:
> Could not unpack Juniper Network Connect!
I left the script I downloaded from MS's site untouched. Was I supposed to change something? Also the terminal window has no error message, it thinks the script ran fine.

I checked my location for the Juniper files and I have the JAR file and other stuff downloaded it seems in the ".juniper_networks" folder. Is there something else I am missing?

The directions on MS's site I followed to a T but I am left with this annoying message.

P.S. I am using the full blown version of Xubuntu 8.04 on a 32bit Intel machine.

Thanks to anyone that can help!!

---

### Post by madscientist on 2008-05-29
Hrm.  Nowhere does it say you need to or should run the script as root (using sudo).

You're at least the second person who's done this, though, so I've created a new version of the script that checks for this and prints a failure.  Unfortunately I left it at home so I haven't uploaded it yet.

However, you should remove the ~/.vpn.cfg file (you might have to be root to do that) then re-run the script WITHOUT the sudo.

---

### Post by webs05 on 2008-05-29
Thanks for the reply Mad Scientist. Here is where I am now at...
```
jonny@LittleBlackWebs:~/Desktop$ ./junipernc
java.io.FileNotFoundException: META-INF/MANIFEST.MF (Permission denied)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
	at sun.tools.jar.Main.extractFile(Main.java:824)
	at sun.tools.jar.Main.extract(Main.java:762)
	at sun.tools.jar.Main.run(Main.java:210)
	at sun.tools.jar.Main.main(Main.java:1022)
jonny@LittleBlackWebs:~/Desktop$

Error message then pops up:
Could not unpack Juniper Network Connect!

```
So is there a problem with my install of Java. Assuming this I uninstalled what I had for Java and ran the command on your site for installing the Java stuff.

I then re-ran the script just as I did in the above output, and again I get the same as what the above output shows. Error message about unpacking the Juniper NC.

I have a ".juniper_*" folder with what appears to be the appropriate files in it. I'm just not sure what else to try.

Thanks

[UPDATE]
I ran "updatedb" and "locate vpn" to look for a ".vpn.cfg" file and did not find one.

---

### Post by weekdaysailor on 2008-05-30
I'm getting this one:

Connecting to xxxxxxx port 443
Generating Certificate .... done.
Exception in thread "AWT-EventQueue-0" java.lang.ExceptionInInitializerError
	at NC$3.run(NC.java:1282)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
Caused by: java.lang.ArrayIndexOutOfBoundsException: 3
	at JavaNC.<clinit>(NC.java:443)
	... 9 more

I do get the login dialog (graphical), but get this after providing credentials. 

I wonder if I need to undo some of the things "did" in the early part of this thread...(I did un-install jre5 and install jre6)

-WDS

---

### Post by madscientist on 2008-05-30
> **webs05 said:**
> ```
java.io.FileNotFoundException: META-INF/MANIFEST.MF (Permission denied)
```
I have a ".juniper_*" folder with what appears to be the appropriate files in it. I'm just not sure what else to try.

[UPDATE]
I ran "updatedb" and "locate vpn" to look for a ".vpn.cfg" file and did not find one.Based on the error message it appears to be a permissions problem.  If you ran the script before as root then when the script unpacked the jar file all the resulting files are probably owned by root; they should be owned by you.

You might want to try deleting everything under ~/.juniper_networks EXCEPT ncLinuxApp.jar (you will probably have to be root again to do this), then re-run the script.

I forgot: you won't have a .vpn.cfg file yet; it doesn't get created until after you set up your username etc.

---

### Post by webs05 on 2008-05-31
Mad Scientist: Thanks so much again for your help and putting up with me :)

I still get the same thing, I run:
```
jonny@LittleBlackWebs:~/Desktop$ ./junipernc
jonny@LittleBlackWebs:~/Desktop$
```
And then,
Error message then pops up:
Could not unpack Juniper Network Connect!

I deleted everything but the JAR file, then followed the directions on your site from scratch. Nothing.

---

### Post by madscientist on 2008-06-02
> **webs05 said:**
> I deleted everything but the JAR file, then followed the directions on your site from scratch. Nothing.Hrm.  Very odd.  OK, please try again (deleting everything but the jar file).  I've posted a newer version of my script on my website at [http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html) so please get a new copy before running it.  This version (a) checks for root and (b) tries to keep a log file for all commands it runs.

Hopefully when it fails it will tell you to look in a log file.  Do that, and/or post it here (suitably anonymized).  Also, please run: ```
ls -alR ~/.juniper_networks
``` so I can see what it unpacked (if anything).

---

### Post by harryman01 on 2008-06-02
I got the same error 

"Cannot unpack juniper network connect"

or if I try using the web interface the Network connect client report that it cannot find the libraries


could you please let me know what i can do to fix the issue

Thanks

---

### Post by jgallen23 on 2008-06-03
I'm getting the same error as well.

---

### Post by weekdaysailor on 2008-06-03
I uninstalled:

```
junipernc.sh -uninstall
```

then logged back into the SA and started the NC service again. This time I did _not_ provide root (whereas previously I had and got the java error posted earlier).

I get the "unpack" error now.

I uninstalled again to test the theory, this time I again provided the root pw in the dialog - and again getting the java error - but that's after the whole setup dialog has completed - so the last step b4 actually connecting.

Running heron. Also, just running ncsvc returns:

.juniper_networks/network_connect/ncsvc
.juniper_networks/network_connect/ncsvc: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

but that's a NOOB talking.

Hopefully this helps debug.

(thx to madscientist for all this work!)

---

### Post by madscientist on 2008-06-03
OK.  First, I tried to change the script so that it keeps all output in a log file.  When the script dies it checks the log file and if there's anything in it, it's supposed to say "see the contents of log file xxxx".  Did anyone see that?  If so, please provide the output from the log file.

If not, what are the contents of the ~/.juniper_networks directory.  Do you have a ~/.juniper_networks/network_connect directory?  If so, what's in it (please use "ls -al" so we can see the owner and permissions).

Regarding the "error while loading shared libraries"; that's because your version of Network Connect is an old build that was created with a very old version of the standard C++ runtime libraries.  That old version is not available on the newest versions of Ubuntu any longer.  There is a newer version of Network Connect that doesn't rely on these older libraries (that's what my VPN server uses); ideally you can convince your provider to upgrade.

If you can't do that, you can get a copy of an older C++ library you can install on Hardy.  You can download it from [http://mad-scientist.us/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb](http://mad-scientist.us/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb) then install it with the command "sudo  dpkg --force-architecture -i libstdc++2.10-glibc2.2_2.95.4-24_i386.deb"

---

### Post by ejjp on 2008-06-03
hello Madscientist

I got the same error

"Cannot unpack juniper network connect"

```

usuario@pc:~$ ls -alR ~/.juniper_networks
/home/usuario/.juniper_networks:
total 1596
drwxr-xr-x  4 usuario usuario      64 2008-06-03 12:12 .
drwxr-xr-x 92 usuario usuario  237568 2008-06-03 12:16 ..
-rwxr-xr-x  1 usuario usuario    5961 2008-06-03 12:12 junipernc.sh
-rw-r--r--  1 usuario usuario       1 2007-10-12 16:15 junipernc.sh~
-rwxr-xr-x  1 usuario usuario 1350501 2008-02-16 08:31 ncLinuxApp.jar
drwxr-xr-x  2 usuario usuario      56 2008-06-03 12:10 network_connect
drwxr-xr-x  3 usuario usuario      72 2008-06-03 12:09 tmp

/home/usuario/.juniper_networks/network_connect:
total 1808
drwxr-xr-x 2 usuario usuario      56 2008-06-03 12:10 .
drwxr-xr-x 4 usuario usuario      64 2008-06-03 12:12 ..
-rwxr--r-- 1 usuario usuario     716 2008-06-03 12:17 installNC.sh
-rwxr-xr-x 1 usuario usuario 1707120 2008-06-03 12:17 libncui.so
-rw-r--r-- 1 usuario usuario       0 2008-06-03 12:17 missing.info
-rwxr-xr-x 1 usuario usuario   74784 2008-06-03 12:17 ncdiag
-rwxr-xr-x 1 usuario usuario   45298 2008-06-03 12:17 NC.jar
-rw-r--r-- 1 usuario usuario       0 2008-06-03 12:10 ncui.log
-rwxr--r-- 1 usuario usuario    1479 2008-06-03 12:17 xlaunchNC.sh

/home/usuario/.juniper_networks/tmp:
total 3060
drwxr-xr-x 3 usuario usuario      72 2008-06-03 12:09 .
drwxr-xr-x 4 usuario usuario      64 2008-06-03 12:12 ..
-rwxr-xr-x 1 usuario usuario     770 2008-06-03 12:17 getx509certificate.sh
-rwxr-xr-x 1 usuario usuario     716 2008-06-03 12:17 installNC.sh
-rwxr-xr-x 1 usuario usuario 1707120 2008-06-03 12:17 libncui.so
drwxr-xr-x 2 usuario usuario      24 2008-06-03 12:09 META-INF
-rwxr-xr-x 1 usuario usuario   74784 2008-06-03 12:17 ncdiag
-rwxr-xr-x 1 usuario usuario   45298 2008-06-03 12:17 NC.jar
-rwxr-xr-x 1 usuario usuario 1270696 2008-06-03 12:17 ncsvc
-rw-r--r-- 1 usuario usuario      14 2008-06-03 12:17 version.txt
-rwxr-xr-x 1 usuario usuario    1479 2008-06-03 12:17 xlaunchNC.sh

/home/usuario/.juniper_networks/tmp/META-INF:
total 16
drwxr-xr-x 2 usuario usuario   24 2008-06-03 12:09 .
drwxr-xr-x 3 usuario usuario   72 2008-06-03 12:09 ..
-rw-r--r-- 1 usuario usuario 2957 2008-06-03 12:17 IMPORTED.RSA
-rw-r--r-- 1 usuario usuario  631 2008-06-03 12:17 IMPORTED.SF
-rw-r--r-- 1 usuario usuario  578 2008-06-03 12:17 MANIFEST.MF


```

and the error message in tmp:


Run as: /home/usuario/.juniper_networks/junipernc.sh
/home/usuario/.juniper_networks/junipernc.sh: 188: jar: not found

---

### Post by harryman01 on 2008-06-03
I got similar directory structure, I also have the script output, that it shows


Reading /home/user/.vpn.cfg...
Run as: /usr/local/bin/junipernc.sh
/usr/local/bin/junipernc.sh: 188: jar: not found

wired, as my jar file exists and is in the correct location accordigly with the script

Thanks for your help

---

### Post by weekdaysailor on 2008-06-03
Seems like it's got to be permissions as the script runs fine (alas, old libs...) when I download the client and provide root login at the shell dialog that comes up. If not I get the same unpack error as everyone else. 

-WDS

---

### Post by weekdaysailor on 2008-06-03
Success with Heron 8.04!!

Turns out I was hitting an old box - we have newer ones**, so tried one of them. Same symptoms as before wrt unpack error, etc. So I provided the root pw when prompted - and darned if it didn't just launch and work! (did not need to run madscientist's script..but have run it before, so this may be a dependency...)

[**elided text - we are running a not-yet-released IVEOS 6.2 on this new box - perhaps 6.1 would work as well if you provide root pw]

---

### Post by virtualscoop on 2008-06-03
> **harryman01 said:**
> I got the same error 

"Cannot unpack juniper network connect"


Thanks

The unpack error went away with "chmod u+x ncsvc".

In the script, there is this line:

 (cd "$_ncpath" && jar xf "$_jarfile" && [ -x "$_svc" ]) >> "$_errlog" 2>&1 \
            || die "Could not unpack Juniper Network Connect!"

Well, the -x was failing due to the ncsvc file in my case being not executable.

Still, with that I get the IVE error:

20080602221611.127751 ncui[9551] dsclient.info <-- 302 [https://***/url_default/welcome.cgi?p=failed](https://***/url_default/welcome.cgi?p=failed) (authenticate.cpp:168)
20080602221611.127865 ncui[9551] dsclient.info state: kStateError (dsclient.cpp:358)
20080602221611.128164 ncui[9551] ncapp.error Failed to connect/authenticate with IVE. Error 104 (ncapp.cpp:174)

The output of the first time run of madscientists script:

irfan@leibniz:~$ ./junipernc
Connecting to sslvpn.vmware.com port 443
Generating Certificate .... done.
Searching for ncsvc in current working directory
Searching for ncsvc in /home/irfan/.juniper_networks/network_connect done.
ncapp> Failed to connect/authenticate with IVE. Error 104
ncapp> Incorrect credentials. Please check the username/password/realm.

Anyone know how to get around the IVE error? I'm completely stuck.

---

### Post by harryman01 on 2008-06-03
> **weekdaysailor said:**
> Success with Heron 8.04!!

Turns out I was hitting an old box - we have newer ones**, so tried one of them. Same symptoms as before wrt unpack error, etc. So I provided the root pw when prompted - and darned if it didn't just launch and work! (did not need to run madscientist's script..but have run it before, so this may be a dependency...)

[**elided text - we are running a not-yet-released IVEOS 6.2 on this new box - perhaps 6.1 would work as well if you provide root pw]

well done, but I still got the same issue as our box still old, hao can I make this work?


Thanks

---

### Post by harryman01 on 2008-06-04
Solved!!

what happed to me was the libssl.so.0 library, what I did was 
sudo ln -s libssl.so.0.9.8 /usr/lib/i686/cmov/libssl.so.0

than i'm able to use the NC java client as I change the root password, however, a rpm message is presente to me and I fixed doing a

sudo ln -s /bin/true /usr/bin/rpm

Thanks to everyone

---

### Post by K0LO on 2008-06-04
**How to get this working on Kubuntu Hardy (8.04):**

Thanks to **madscientist **and the others who contributed, I was finally able to get Juniper Network Connect to work with the KDE-based Kubuntu. Here is what I did:

1. Follow the instructions on []("http://mad-scientist.com/juniper.html")[http://mad-scientist.com/juniper.html](http://mad-scientist.com/juniper.html)
2. Download the latest version of the script from the above site
3. Make the following edit to the script:[INDENT]change:  _sudo=gksudo
to:         _sudo=[COLOR=Red]**kdesudo**[/COLOR]
[/INDENT]4. Install the package **zenity **(not installed in Kubuntu by default)
5. Continue with the instructions referenced in step 2
6. After the installer has run and populated ~/.juniper_networks, change the permissions on the ncsvc file:[INDENT]chmod u+x ncsvc
[/INDENT]7. Run the script and answer all of the questions.

**Madscientist**, perhaps step 6 can be put in your script -- this has tripped up a few posters here, and me too. Thanks to **virtualscoop **(post #164) for this fix, which was key for getting the script to run successfully for me.

---

### Post by madscientist on 2008-06-04
Thanks for the debugging.  I guess older versions of the jar file didn't set the ncsvc application to be executable by default.  In retrospect it's stupid of me to require it, since I do go and change the permissions directly afterwards anyway!

I'll fix this tonight.  I'll also try to add some help for Kubuntu users.

---

### Post by K0LO on 2008-06-04
Following up on post #167:

After a successful install on my laptop running Kubuntu 8.04 I went home and tried this on my server running Kubuntu 6.06. I made sure that I had updated to sun Java version 6 and that all of the other required packages were installed. One difference - I replaced **_sudo=gksudo** with **_sudo=[COLOR=Red]kdesu[/COLOR]** in the script ([COLOR=Red]**kdesudo**[/COLOR] was not used in Kubuntu 6.06; it was **[COLOR=Red]kdesu[/COLOR]** back then).

Using the same approach as before, I ran the mad-scientist script. The script runs, I get prompted for the root password, it is accepted, then nothing further happens and I have to ctrl-c to stop the script execution. Here is the content of the log file from /tmp/junipernc.xxxx after running the script:```
java.io.FileNotFoundException: ncsvc (Permission denied)
      at java.io.FileOutputStream.open(Native Method)
      at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
      at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
      at sun.tools.jar.Main.extractFile(Main.java:824)
      at sun.tools.jar.Main.extract(Main.java:762)
      at sun.tools.jar.Main.run(Main.java:210)
      at sun.tools.jar.Main.main(Main.java:1022)

```I have tried **chmod +x ncsvc** to make the file executable for everyone but that doesn't help.

Contents of ~/juniper_networks/network_connect: ```
mark@server:~/.juniper_networks/network_connect$ ls -al
total 2803
drwxr-xr-x 3 mark mark     400 2008-06-04 20:51 .
drwxr-xr-x 4 mark mark     136 2008-06-04 20:49 ..
-rw-r--r-- 1 mark mark     770 2008-05-06 21:47 getx509certificate.sh
-rwxr--r-- 1 mark mark     716 2008-05-06 21:47 installNC.sh
-rw-r--r-- 1 mark mark 1560752 2008-05-06 21:47 libncui.so
drwxr-xr-x 2 mark mark     144 2008-05-06 21:47 META-INF
-rw-r--r-- 1 mark mark       0 2008-06-04 20:49 missing.info
-rwxr--r-- 1 mark mark   74784 2008-05-06 21:47 ncdiag
-rw-r--r-- 1 mark mark   45299 2008-05-06 21:47 NC.jar
-rwxr-xr-x 1 mark mark 1150856 2008-05-06 21:47 ncsvc
-rw-r--r-- 1 mark mark     132 2008-06-04 20:49 ncuijava.log
-rw-r--r-- 1 mark mark     701 2008-06-04 20:49 ncui.log
-rw-r--r-- 1 mark mark      14 2008-05-06 21:47 version.txt
-rwxr--r-- 1 mark mark    1479 2008-05-06 21:47 xlaunchNC.sh
mark@server:~/.juniper_networks/network_connect$ juniper
```Version info:
cat version.txt
Version: 1.2

Any suggestions?

---

### Post by madscientist on 2008-06-04
You can't just replace kdesudo with kdesu.  They are NOT the same thing.  This is the reason why you get the "hang", and why things don't work afterwards.

I just uploaded a newer copy of my script with a test for gksudo, and if not then kdesudo, and if not then plain sudo.  This means the first time you run the script you MUST run it from a shell prompt.  This is only needed for the very first run though.

It also checks for zenity and fails if it's not found, and it just checks for the file ncsvc, not if it's executable, which should fix some other issues seen here.

Please download this version and see if it works any better.  If you don't have gksudo or kdesudo, you'll be asked for your password in the CLI (via plain sudo).

---

### Post by K0LO on 2008-06-04
madscientist:

Now that's impressive! The new script worked perfectly right off the bat. :KS

I also learned something - I expected sudo to run in the terminal on the first run of the script but instead got a graphical gksudo box. Upon later searching my disk I found /usr/bin/gksudo was present. I didn't know that this was part of a default Kubuntu install because I never tried to run it. So I probably misled us both by starting off modifying your script. I should have just run it first as-is. I guess I outsmarted myself again.

Thank you for your effort on this project. Our sysadmins at work are just in the process of removing their 6-yr old Cisco VPN concentrators and replacing them with the Juniper SSL VPN. I asked them to enable split tunneling on the main Windows profile, which they did. They have left it disabled on the Wireless profiles, however, which is fine with me. This same profile also works on Linux and gives split tunnel operation. Since this box is my home network server, I didn't want it to go invisible on the LAN every time that I'm using the work VPN.

I really appreciate your script - the client authenticates and connects via the script in less than 3 seconds and is so simple to operate without going through a web browser interface.  Many thanks!

---

### Post by madscientist on 2008-06-05
Excellent!  Good to know.  Hopefully some others who have been having issues can get this working now.

The only  missing item is some relief for those who are using older versions of Juniper NC, that are linked with the older libstc++ libraries that are no longer available in Hardy.  I have copies of those but I'm not sure how best to distribute them.

Cheers!

---

### Post by osx424242 on 2008-06-05
> **virtualscoop said:**
> ncapp> Failed to connect/authenticate with IVE. Error 104
ncapp> Incorrect credentials. Please check the username/password/realm.

Anyone know how to get around the IVE error? I'm completely stuck.

Not the best instructions, but I managed to connect after getting that error.  I went back to the webpage I'm supposed to use to connect, logged in (username + RSA key password) there, and when the terminal window popped up and asked for the root password I closed that window.  Then the Network Connect window opened and I was connected (yes I verified it by connecting to an internal computer).

So... give that a shot.  My guess is that the junipernc script by The Wonderful and Amazing madscientist got nearly everything configured, and then the web interface added the final piece to the puzzle.  Tomorrow I'll ask on our internal forums if anyone knows if our Realm is something other than RSA.

Oh, also: when I ran junipernc and entered 123456 for my password, I got the same error.  So my problem might be anything in the username/password realm that is getting translated by the web interface.

---

### Post by osx424242 on 2008-06-05
> **madscientist said:**
> The only  missing item is some relief for those who are using older versions of Juniper NC, that are linked with the older libstc++ libraries that are no longer available in Hardy.  I have copies of those but I'm not sure how best to distribute them.

After skimming this thread, I thought the older libstc++ libraries were only needed for version 1.0, not 1.2?  Yet I apparently have 1.2, but I had to install those libraries to get things to work.

Thanks for making them available :)

I'd recommend sticking a link to them with instructions for installing them on your juniper.html page, probably in the Troubleshooting section.  Also, a link in the Troubleshooting section to this thread would be useful for people (not me) who find your page from some other source (and, if you had a lot of extra time, even a table with error messages in one column and the individual post that showed the solution in the other column ;)).

```
$ pwd
/home/osx424242/.juniper_networks/network_connect
$ ls -al
total 976
drwxr-xr-x 3 osx424242 osx424242   4096 2008-06-05 01:10 .
drwxr-xr-x 4 osx424242 osx424242   4096 2008-06-05 01:10 ..
-rw-r--r-- 1 osx424242 osx424242    770 2008-02-15 08:30 getx509certificate.sh
-rw-r--r-- 1 osx424242 osx424242   1173 2008-06-05 01:10 installnc.log
-rwxr--r-- 1 osx424242 osx424242    716 2008-06-05 01:10 installNC.sh
-rw-r--r-- 1 osx424242 osx424242 493680 2008-06-05 01:10 libncui.so
drwxr-xr-x 2 osx424242 osx424242   4096 2008-02-15 08:30 META-INF
-rw-r--r-- 1 osx424242 osx424242      0 2008-06-05 01:10 missing.info
-rw-r--r-- 1 osx424242 osx424242     30 2008-06-05 01:10 missing.rpt
-rwxr--r-- 1 osx424242 osx424242  24888 2008-06-05 01:10 ncdiag
-rw-r--r-- 1 osx424242 osx424242   4256 2008-06-05 00:30 ncdiag.log
-rw-r--r-- 1 osx424242 osx424242  45475 2008-06-05 01:10 NC.jar
-rws--s--x 1 root     root     332044 2008-02-15 08:30 ncsvc
-rw-r--r-- 1 osx424242 osx424242     61 2008-06-05 01:10 ncsvc.log
-rw-r--r-- 1 osx424242 osx424242   3637 2008-06-05 01:13 ncuijava.log
-rw-r--r-- 1 osx424242 osx424242  26058 2008-06-05 01:13 ncui.log
-rw-r--r-- 1 osx424242 osx424242     14 2008-02-15 08:30 version.txt
-rwxr--r-- 1 osx424242 osx424242   1632 2008-06-05 01:10 xlaunchNC.sh
$ ./ncsvc --version
Juniper Network Connect Server for Linux.
Version         : 1.2
Release Version : 5.5-0-Build12781
Build Date/time : Feb 15 2008 16:15:25 
Copyright 2002-2006 Juniper Networks
$ 
```

---

### Post by madscientist on 2008-06-05
I certainly don't pretend to understand how Juniper does their versioning--it seems pretty complex.  However, the "main" version number (1.0, 1.2) apparently relates to different functionality, while the "Release Version" apparently relates to different builds of the same version.  On my system I have this output:```
~$ ./.juniper_networks/network_connect/ncsvc -v
Juniper Network Connect Server for Linux.
Version         : 1.2
Release Version : 6.0-0-Build12023
Build Date/time : Aug  9 2007 21:15:09 
Copyright 2002-2007 Juniper Networks
```This version does not need special versions of libstdc++.  In fact, using ldd shows that no libstdc++ is needed at all: ```
~$ sudo ldd ./.juniper_networks/network_connect/ncsvc
        linux-gate.so.1 =>  (0xb7f64000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f49000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7f34000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f1b000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ef6000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7da7000)
        /lib/ld-linux.so.2 (0xb7f65000)
```So, maybe in these newer builds they're linking libstdc++ statically.

Of course, the odd things about this are that even though my "Release Version" is newer than yours (6.0 to 5.5), my "BuildXXXX" number is lower than yours.  Also my Build Date is before yours; I think that must be something to do with when your VPN server was set up or something.  But on the other hand, your copyright date is 2006 while mine is 2007.

It seems pretty clear that you need at least Version 1.2, Release Version 6.0-*, in order to avoid the shared library problem.

Can you run the above ldd command and let me know what you get?  Maybe I can get my script to detect this issue and give some advice.

---

### Post by osx424242 on 2008-06-06
Here you go, hope it's useful:
```
$ sudo ldd ~/.juniper_networks/network_connect/ncsvc
	linux-gate.so.1 =>  (0xb7f57000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f3a000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb7f25000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f0c000)
	libstdc++-libc6.2-2.so.3 => /usr/lib/libstdc++-libc6.2-2.so.3 (0xb7ec4000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e9f000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d50000)
	/lib/ld-linux.so.2 (0xb7f58000)
$ 
```

---

### Post by K0LO on 2008-06-08
**madscientist:**

What a difference a few days make. Recall my comment that the network guys are in the process of bringing up the Juniper SSL VPN, so things are still changing. After having success with your script (see posts 167, 169, and 171) the network guys have now added Juniper's Host Checker to the SSL VPN. This intrusive little app downloads to your PC and runs each time you attempt to connect to the VPN. It checks the operating system in use, the browser name/version, whether you are running antivirus software and which brand, and whether your antivirus definitions are up-to-date. If your machine fails the criteria established by the network admins then it is not allowed to connect.

I am wondering if you have run into Juniper SSL VPNs with Host Checker before and if you can help getting it working with your script. Here's how far I've gotten to date. First I used your script to uninstall everything, then connected to the VPN site with Firefox and let it download everything again. Of course the Juniper installer fails just like before, so after logging out I ran your script. The script finished the installation just like before. However, now when I try to connect the Juniper Host Checker starts to run and, of course, fails, and probably for the same reasons that the main Network Connect script fails.

However, if I now go back to the VPN site with Firefox and click on "Network Connect" it all works. Host Checker runs, my machine passes the criteria, and a dialog box pops up for the Java installer, which concludes with the error message "Installation failed; Sorry". But the client connects and works fine anyway.

So I **can** connect successfully from a web browser but not from the script. When the script runs I get a Java popup with the message "Unable to connect to IVE" and everything halts. So I think that it can be made to work since it does work when run from Firefox.

Here are some details obtained from the console.
```
Juniper SSL VPN client troubleshooting
8 June 2008  MJW

Before updating client software:
=========================================================================
mark@marconi:~/.juniper_networks$ ls -al
total 1213
drwxr-xr-x  4 mark mark    1024 2008-06-04 15:05 .
drwxr-xr-x 49 mark mark    2048 2008-06-05 08:31 ..
-rw-r--r--  1 mark mark 1230080 2008-05-07 00:47 ncLinuxApp.jar
drwxr-xr-x  3 mark mark    1024 2008-06-04 15:17 network_connect
drwxr-xr-x  3 mark mark    1024 2008-06-04 15:06 tmp

mark@marconi:~/.juniper_networks$ cd network_connect/
mark@marconi:~/.juniper_networks/network_connect$ ls -al
total 2981
drwxr-xr-x 3 mark mark    1024 2008-06-04 15:17 .
drwxr-xr-x 4 mark mark    1024 2008-06-04 15:05 ..
-rw-r--r-- 1 mark mark     770 2008-06-04 15:07 getx509certificate.sh
-rw-r--r-- 1 mark mark     380 2008-06-04 15:05 installnc.log
-rwxr--r-- 1 mark mark     716 2008-06-04 15:07 installNC.sh
-rw-r--r-- 1 mark mark 1560752 2008-06-04 15:07 libncui.so
drwxr-xr-x 2 mark mark    1024 2008-06-04 15:07 META-INF
-rw-r--r-- 1 mark mark       0 2008-06-04 15:05 missing.info
-rwxr--r-- 1 mark mark   74784 2008-06-04 15:07 ncdiag
-rw-r--r-- 1 mark mark   16136 2008-06-05 07:57 ncdiag.log
-rw-r--r-- 1 mark mark   45299 2008-06-04 15:07 NC.jar
-rws--s--x 1 root root 1150856 2008-06-04 15:07 ncsvc
-rw-r--r-- 1 root root  130218 2008-06-05 08:31 ncsvc.log
-rw-r--r-- 1 mark mark    3404 2008-06-08 21:56 ncuijava.log
-rw-r--r-- 1 mark mark   38200 2008-06-08 21:56 ncui.log
-rw-r--r-- 1 mark mark      14 2008-06-04 15:07 version.txt
-rwxr--r-- 1 mark mark    1479 2008-06-04 15:07 xlaunchNC.sh

mark@marconi:~/.juniper_networks/network_connect$ ./ncsvc -v
Juniper Network Connect Server for Linux.
Version         : 1.2
Release Version : 6.1-0-Build13103
Build Date/time : May  6 2008 21:34:46
Copyright 2001-2008 Juniper Networks
==========================================================================
==========================================================================
After uninstalling then downloading latest client software:

mark@marconi:~/.juniper_networks/network_connect$ ~/bin/junipernc.sh
Connecting to sslvpn.[COLOR=Green]xxxx.xxx.xxx[/COLOR] port [COLOR=Green]xxx[/COLOR]
Generating Certificate .... done.
Searching for ncsvc in current working directory done
ncapp> Failed to connect/authenticate with IVE. Error 10

mark@marconi:~/.juniper_networks$ ls -al
total 1455
drwxr-xr-x  4 mark mark    1024 2008-06-08 22:15 .
drwxr-xr-x 49 mark mark    2048 2008-06-08 22:18 ..
-rw-r--r--  1 mark mark   50877 2008-06-08 22:16 dsHCLauncher_linux1.log
-rw-r--r--  1 mark mark   14515 2008-06-08 22:16 HttpNAR_linux1.log
-rw-r--r--  1 mark mark       6 2008-06-08 22:15 narport.txt
-rw-r--r--  1 mark mark 1230080 2008-05-07 00:47 ncLinuxApp.jar
drwxr-xr-x  3 mark mark    1024 2008-06-08 22:17 network_connect
drwxr-xr-x  3 mark mark    1024 2008-06-08 22:16 tmp
-rw-r--r--  1 mark mark  176148 2008-05-07 00:58 tncc.jar

mark@marconi:~/.juniper_networks$ cd network_connect/
mark@marconi:~/.juniper_networks/network_connect$ ls -al
total 2796
drwxr-xr-x 3 mark mark    1024 2008-06-08 22:17 .
drwxr-xr-x 4 mark mark    1024 2008-06-08 22:15 ..
-rw-r--r-- 1 mark mark     770 2008-06-08 22:17 getx509certificate.sh
-rw-r--r-- 1 mark mark     380 2008-06-08 22:16 installnc.log
-rwxr--r-- 1 mark mark     716 2008-06-08 22:17 installNC.sh
-rw-r--r-- 1 mark mark 1560752 2008-06-08 22:17 libncui.so
drwxr-xr-x 2 mark mark    1024 2008-06-08 22:17 META-INF
-rw-r--r-- 1 mark mark       0 2008-06-08 22:16 missing.info
-rwxr--r-- 1 mark mark   74784 2008-06-08 22:17 ncdiag
-rw-r--r-- 1 mark mark   45299 2008-06-08 22:17 NC.jar
-rws--s--x 1 root root 1150856 2008-06-08 22:17 ncsvc
-rw-r--r-- 1 mark mark     264 2008-06-08 22:18 ncuijava.log
-rw-r--r-- 1 mark mark    2936 2008-06-08 22:18 ncui.log
-rw-r--r-- 1 mark mark      14 2008-06-08 22:17 version.txt
-rwxr--r-- 1 mark mark    1479 2008-06-08 22:17 xlaunchNC.sh

Note that META-INF is moved here

mark@marconi:~/.juniper_networks/network_connect$ cd META-INF/
mark@marconi:~/.juniper_networks/network_connect/META-INF$ ls -al
total 7
drwxr-xr-x 2 mark mark 1024 2008-06-08 22:17 .
drwxr-xr-x 3 mark mark 1024 2008-06-08 22:17 ..
-rw-r--r-- 1 mark mark 2957 2008-06-08 22:17 IMPORTED.RSA
-rw-r--r-- 1 mark mark  631 2008-06-08 22:17 IMPORTED.SF
-rw-r--r-- 1 mark mark  578 2008-06-08 22:17 MANIFEST.MF

Note that the old location for META-INF is now empty:

mark@marconi:~/.juniper_networks/network_connect/META-INF$ cd ..
mark@marconi:~/.juniper_networks/network_connect$ cd ..
mark@marconi:~/.juniper_networks$ cd tmp
mark@marconi:~/.juniper_networks/tmp$ ls -l
total 1
drwxr-xr-x 2 mark mark 1024 2008-06-08 22:16 META-INF
mark@marconi:~/.juniper_networks/tmp$ cd META-INF/
mark@marconi:~/.juniper_networks/tmp/META-INF$ ls -l
total 0

Note that the ncsvc version is still the same:

mark@marconi:~/.juniper_networks/network_connect$ ./ncsvc -v
Juniper Network Connect Server for Linux.
Version         : 1.2
Release Version : 6.1-0-Build13103
Build Date/time : May  6 2008 21:34:46
Copyright 2001-2008 Juniper Networks

=================================================================================
Log contents:

mark@marconi:~/.juniper_networks/network_connect$ cat ncui.log
20080608221828.983448 ncui[5365] ncapp.info New ncapp log level set to 3 (nccommon.cpp:75)
20080608221828.983497 ncui[5365] ncapp.info Version         : 1.2
Release Version : 6.1-0-Build13103
Build Date/Time : May  6 2008
Copyright 2001-2008 Juniper Networks
 (ncapp.cpp:152)
20080608221829.124692 ncui[5365] dsclient.info state: kStateSignin (dsclient.cpp:233)
20080608221829.124805 ncui[5365] dsclient.info --> GET / (authenticate.cpp:136)
20080608221829.158901 ncui[5365] dsclient.info <-- 302 https://sslvpn.xxxx.xxx.xxx/dana-na/auth/url_default/welcome.cgi (authenticate.cpp:168)
20080608221829.158987 ncui[5365] dsclient.info state: kStateWelcome (dsclient.cpp:241)
20080608221829.159012 ncui[5365] dsclient.info --> GET /dana-na/auth/url_default/welcome.cgi (authenticate.cpp:136)
20080608221829.377957 ncui[5365] dsclient.info <-- 200  (authenticate.cpp:168)
20080608221829.378062 ncui[5365] dsclient.info state: kStateLogin (dsclient.cpp:273)
20080608221829.378096 ncui[5365] dsclient.info --> POST /dana-na/auth/url_default/login.cgi (authenticate.cpp:136)
20080608221829.591983 ncui[5365] dsclient.info <-- 302 https://sslvpn.[COLOR=Green]xxxx.xxx.xxx[/COLOR]/dana-na/auth/url_default/welcome.cgi?p=preauth&id=state_[COLOR=Green]{16 byte hex ID removed}[/COLOR]&signinRealmId=2 (authenticate.cpp:168)
20080608221829.592063 ncui[5365] dsclient.info state: kStatePostAuth (dsclient.cpp:313)
20080608221829.592103 ncui[5365] dsclient.info --> GET /dana-na/auth/url_default/welcome.cgi?p=preauth&id=state_[COLOR=Green]{16 byte hex ID removed}[/COLOR]&signinRealmId=2 (authenticate.cpp:136)
20080608221829.798500 ncui[5365] dsclient.info <-- 200  (authenticate.cpp:168)
20080608221829.798585 ncui[5365] dsclient.info state: kStatePostCacheCleaner (dsclient.cpp:329)
20080608221829.798608 ncui[5365] dsclient.info --> POST /dana-na/cc/ccupdate.cgi (authenticate.cpp:136)
20080608221829.971385 ncui[5365] dsclient.info <-- 200  (authenticate.cpp:168)
20080608221829.971456 ncui[5365] dsclient.error state post auth cache cleaner failed, error 10 (dsclient.cpp:331)
20080608221829.971555 ncui[5365] ncapp.error Failed to connect/authenticate with IVE. Error 10 (ncapp.cpp:174)
20080608221845.77453 ncui[5365] ncui.info Sending kill signal (SIGQUIT) to ncsvc...  (ncapp.cpp:445)

```

---

### Post by webs05 on 2008-06-09
New script works great! Thanks

I am using Xubuntu 8.04

---

### Post by madscientist on 2008-06-09
Sorry, K0LO, I've never heard of this "Host Checker" thing before.  Sounds very *1984* :(

I agree it probably may be possible to get it working, given that it works via your web browser.  However, without the software myself I doubt I'd be able to do it.  You would need to do something like trace the browser operation to see what commands it's running, etc.

And, if "Host Checker" want to check the browser version, I suppose it's possible that it expects to be run from a browser.  Maybe the "Host Checker" is written in JS or similar, rather than as a standalone program.

I just don't know.

---

### Post by K0LO on 2008-06-09
**madscientist**:
 
It **is** very 1984. I tried logging on from Windows and was politely refused a connection because my antivirus definitions were 10 days old. I had to update before being allowed on the network.
 
On the other hand, I can see reasons for these policies. I'm at a major University with 80,000 students and 30,000 faculty and staff people on a geographically-diverse network spread across the state of Pennsylvania. If only a few people create problems on the network then policies like this end up being put in place.
 
Fortunately I am on good terms with the network admins. This Juniper Host Checker has no requirements to check for on Linux machines, so it does no good to run it. One of the admins is checking with Juniper to see if they can disable this for clients connecting from Linux PCs.
 
I will try further troubleshooting and will let you know if I can figure anything else out. Or, with luck, the admins will disable it!

---

### Post by madscientist on 2008-06-09
I can understand it as well but that doesn't make it any less frustrating.  I suppose if Juniper had any clue whatsoever when it comes to Linux support it wouldn't be such a big deal.

If you're on good terms with the admins, and you guys have significant purchasing power from Juniper (which it sounds like you do), maybe you can try to get your admins to file some bugs and/or put pressure on Juniper to make their system work better on Linux.  What they have now is, frankly, and embarrassment (anyway, I'd be embarrassed if I worked there).  They don't have to officially support Ubuntu (although if they're smart they will since it's been the #1 desktop distro for almost 2 years now), but they could take a few small steps that would greatly increase the portability of their product.  I'd dearly love to replace my page with a link to the Juniper product page, like I did with Amazon's MP3 downloader when they finally got that ported to Linux.

---

### Post by weekdaysailor on 2008-06-11
Host Checker can be administratively disabled. From Juniper's Knowledge Base:


> 
Host Checker Policies contain rules for three OS's: Windows, MAC, and Linux. 

To allow a MAC or Linux user to connect, a custom rule must be defined for each respective operating system.

If no rule is desired for users of another OS, you may configure a "dummy" rule for their OS.  To configure a "dummy" rule:

   1. Navigate to Endpoint Security > Host Checker, select your Host Checker policy
   2. Then select "Custom: File:" in the Rule settings drop down box and choose "Add".
   3. Assign a new Rule Name
   4. Enter a File Name which will never be found on the guest operating system (for example, "/Not-Exist"). 
   5. Finally, set the criteria for this file to "Deny".

Talk to your admin about deploying. This is from KB9048 (support login required)

Cheers,

-WDS

---

### Post by madscientist on 2008-06-11
Hi all; I got a private message pointing out that the latest Juniper SSL VPN version, 6.2, was just released a couple of days ago, and it has official support for Ubuntu 7.10.  I haven't tested this or even seen it in action so I can't say much about it, although a quick zoom through the docs seems to imply it's shipped as an RPM, that you are to use alien to install on Ubuntu *shrug*.

If you're interested in finding out more, I located a bunch of documentation here: [http://www.juniper.net/techpubs/software/ive/6.x/6.2/](http://www.juniper.net/techpubs/software/ive/6.x/6.2/)

---

### Post by weekdaysailor on 2008-06-12
That's the mysterious version I was running a few posts ago. I am running Hardy and just set a root password to enable the install. That seems to do it, but I have monkeyed with my system a bit with earlier attempts - YMMV

I did not do a package/rpm install, just clicked the button. 

-WDS

---

### Post by krammer on 2008-06-13
Hello madscientist,

Our Juniper does not have a hostname, it is just an IP address that I browse to.  When putting in the IP address with the script, it says it cannont resolve the hostname and to try again.

I am able to connect fine with firefox, although I get the sudo/root issue where it asks me for my password and errors with the rpm, but it still connects.
*   Edit**fixed this issue by putting your updated files in place, no more su/root and rpm errors*

Do you have any suggestions?

Here's my version info:

```

root@mybox:~/.juniper_networks/network_connect# ./ncsvc --version
Juniper Network Connect Server for Linux.
Version         : 1.2
Release Version : 5.5-0-Build11711
Build Date/time : Apr 10 2007 17:57:49 
Copyright 2002-2006 Juniper Networks
root@mybox:~/.juniper_networks/network_connect# ldd ncsvc
        linux-gate.so.1 =>  (0xffffe000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f4c000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7f38000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f20000)
        libstdc++-libc6.2-2.so.3 => /usr/lib/libstdc++-libc6.2-2.so.3 (0xb7ed8000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7eb1000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d70000)
        /lib/ld-linux.so.2 (0xb7f63000)
root@mybox:~/.juniper_networks/network_connect#
```

---

### Post by rajkumarc2000 on 2008-06-14
hi, 

i have the ubuntu version 8.04 on my laptop and i am trying to configure the juniper networks on my machine to enable me to connect to my company's network. 

whenever i try to launch the network connect client from the page, i get a error message stating that Applet SecureNCLauncher not found, and my firefox just stops responding. 

does anyone has faced this problem before and has fixed this?

let me know. 

my system details 
firefox 32 bit version 
jre -1.6

thanks
rajkumar

---

### Post by gfa on 2008-06-17
> **madscientist said:**
> Find the directions here: [http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html)

Let me know if you have problems!

Hi mad-scientist... thanks for that great script, unfortunattely, I have a problem with my Juniper connection, I think because my **company's server hasn't a valid certificate** (every time a connect with Fx get a warning about it).

If I run your script from CLI, get these warnings

```
$ ./junipernc 
Searching for ncsvc in current working directory
Searching for ncsvc in /home/gfa/.juniper_networks/network_connect done.
ncapp> Failed to connect/authenticate with IVE. Error 2
ncapp> Please check the ive hostname/ip and the ive certificate.
```

In the Juniper GUI, I can see an error about "**Failed to connect with IVE**", after closing both windows (dialog and main juniper window), got a question about restarting the VPN connection.

From Fx I have no problem connecting to my VPN (just the shell asking for root password every time).

Is there any way to disable the certificate validation?

Any help would be appreciated.

Thanks
gFa

---

### Post by cds03900 on 2008-06-18
I have recently bought a Eee PC900 with Linux on it.
Being new to Linux I run into a lot of new things to learn.

One of the problems I had was connecting to my company network through Juniper VPN.

I googled a lot a the best route to go follow looked the Mad Scientist script.

When I try to run the script I get the following error "Cannot resolve hostname $HOST".
I am 100% sure the host is correct and I can visit it through Firefox without a problem.

I tried in a terminal window to ping to the host and that didn't work.
Ping to update.eeepc.asus.com gives normal reaction.

Maybe this strange ping behavor has something to do with it?

Does anybody has some ideas what can be wrong?

---

### Post by madscientist on 2008-06-23
> **krammer said:**
> Hello madscientist,

Our Juniper does not have a hostname, it is just an IP address that I browse to.  When putting in the IP address with the script, it says it cannont resolve the hostname and to try again.Hi; thanks for the bug report.  I uploaded a modified version of the script that won't try to resolve hostnames if you give an IP address.  I hope :-).  Give it a whirl.

---

### Post by madscientist on 2008-06-23
> **rajkumarc2000 said:**
> whenever i try to launch the network connect client from the page, i get a error message stating that Applet SecureNCLauncher not found, and my firefox just stops responding.Hm, I'm not sure.  Have you tried getting the version of NC you have installed?  Try running: ```
~/.juniper_networks/network_connect/ncsvc --version
```What do you get?

> **gfa said:**
> Hi mad-scientist... thanks for that great script, unfortunattely, I have a problem with my Juniper connection, I think because my **company's server hasn't a valid certificate** (every time a connect with Fx get a warning about it).Hrm.  Well, my script doesn't use FireFox or even HTTP at all, so I don't think your company not having a valid SSL certificate for HTTPS (which is what I assume you mean by the above) will have any impact there.  But, I really am not an expert on Juniper VPN so I suppose I could be wrong about that.

> **gfa said:**
> If I run your script from CLI, get these warnings

```
$ ./junipernc 
Searching for ncsvc in current working directory
Searching for ncsvc in /home/gfa/.juniper_networks/network_connect done.
ncapp> Failed to connect/authenticate with IVE. Error 2
ncapp> Please check the ive hostname/ip and the ive certificate.
```

In the Juniper GUI, I can see an error about "**Failed to connect with IVE**", after closing both windows (dialog and main juniper window), got a question about restarting the VPN connection.

From Fx I have no problem connecting to my VPN (just the shell asking for root password every time).

Is there any way to disable the certificate validation?I don't think so: that's a basic part of the VPN setup.

It might be worthwhile to try removing the entire ~/.juniper_networks directory, plus the ~/.vpn* files, and try reinstalling from scratch (or, if you're cautious, you can rename these files or move them somewhere else in case you need to move them back again).  I had to do that when my company deployed a new version, because the old certificate didn't work anymore.

---

### Post by madscientist on 2008-06-23
> **cds03900 said:**
> I have recently bought a Eee PC900 with Linux on it.
Being new to Linux I run into a lot of new things to learn.

One of the problems I had was connecting to my company network through Juniper VPN.

When I try to run the script I get the following error "Cannot resolve hostname $HOST".
I am 100% sure the host is correct and I can visit it through Firefox without a problem.Does it really use the literal string "$HOST" in the message?  Or does it use the hostname you entered as the server host?

I'm really not familiar with the distro of linux that comes on this system; it's not Ubuntu is it?  If it really prints "$HOST" here, that means that the shell on this system is behaving oddly (unless you typed "$HOST" when it asked you for a hostname).  You can remove the .vpn.cfg and .vpn.crt files in your home directory if you want to try starting over.

---

### Post by cds03900 on 2008-06-24
> **madscientist said:**
> Does it really use the literal string "$HOST" in the message?  Or does it use the hostname you entered as the server host?

I'm really not familiar with the distro of linux that comes on this system; it's not Ubuntu is it?  If it really prints "$HOST" here, that means that the shell on this system is behaving oddly (unless you typed "$HOST" when it asked you for a hostname).  You can remove the .vpn.cfg and .vpn.crt files in your home directory if you want to try starting over.

Yes it uses the term $HOST which I didn't enter when it asked me for a hostname.
You are correct, the distro it uses is not Ubunto but Xandros.
Any sugestions?

---

### Post by elenctic on 2008-06-25
I am using Ubuntu 8.04 an madscientist's script to connect to a vpn.  It works for awhile (usually 30s or so) and then the connection dies.  My ssh session freezes.  Below is the packet sequence that I captured using Wireshark.  Everything looks good until the TCP Retransmissions and the TCP CHECKSUM INCORRECT errors start around packet 7914.  Could someone please look at this and give me some insight?  I am really stumped.  Thank you!

The Wireshark logs: (see attached screenshot, too)

```
No.     Time        Source                Destination           Protocol Info
   7905 38.299327   192.168.74.16         172.20.49.156         TCP      33472 > ssh [ACK] Seq=5241 Ack=1600384 Win=171264 Len=0 TSV=15622614 TSER=4170538983
   7906 38.301442   208.70.66.53          192.168.1.103         TLSv1    Application Data
   7907 38.301491   172.20.49.156         192.168.74.16         SSHv2    Encrypted response packet len=208
   7908 38.301507   192.168.74.16         172.20.49.156         TCP      33472 > ssh [ACK] Seq=5241 Ack=1600592 Win=171264 Len=0 TSV=15622615 TSER=4170538986
   7909 38.305724   208.70.66.53          192.168.1.103         TLSv1    Application Data
   7910 38.305772   192.168.1.103         208.70.66.53          TCP      53441 > https [ACK] Seq=64738 Ack=1772123 Win=694144 Len=0
   7911 38.305822   172.20.49.156         192.168.74.16         SSHv2    Encrypted response packet len=288
   7912 38.305845   192.168.74.16         172.20.49.156         TCP      33472 > ssh [ACK] Seq=5241 Ack=1600880 Win=171264 Len=0 TSV=15622616 TSER=4170538991
   7913 38.390166   Cisco-Li_19:e0:b6                           ARP      Who has 192.168.1.103?  Tell 192.168.1.1
   7914 38.556029   192.168.1.103         208.70.66.53          TLSv1    [TCP Retransmission] Application Data, Application Data, Application Data, Application Data
   7915 39.091052   192.168.1.103         208.70.66.53          TLSv1    [TCP Retransmission] Application Data, Application Data, Application Data, Application Data
   7916 39.311862   Cisco-Li_19:e0:b6                           ARP      Who has 192.168.1.103?  Tell 192.168.1.1
   7917 39.579176   127.0.0.1             127.0.0.1             TCP      33405 > 4242 [PSH, ACK] Seq=1080 Ack=10781 Win=49536 [TCP CHECKSUM INCORRECT] Len=20 TSV=15622935 TSER=15622435
   7918 39.579292   127.0.0.1             127.0.0.1             TCP      4242 > 33405 [PSH, ACK] Seq=10781 Ack=1100 Win=33920 [TCP CHECKSUM INCORRECT] Len=186 TSV=15622935 TSER=15622935
   7919 39.579322   127.0.0.1             127.0.0.1             TCP      33405 > 4242 [ACK] Seq=1100 Ack=10967 Win=49536 Len=0 TSV=15622935 TSER=15622935
   7920 40.164047   192.168.1.103         208.70.66.53          TLSv1    [TCP Retransmission] Application Data, Application Data, Application Data, Application Data
   7921 40.336134   Cisco-Li_19:e0:b6                           ARP      Who has 192.168.1.103?  Tell 192.168.1.1
   7922 41.579175   127.0.0.1             127.0.0.1             TCP      33405 > 4242 [PSH, ACK] Seq=1100 Ack=10967 Win=49536 [TCP CHECKSUM INCORRECT] Len=20 TSV=15623435 TSER=15622935
   7923 41.579297   127.0.0.1             127.0.0.1             TCP      4242 > 33405 [PSH, ACK] Seq=10967 Ack=1120 Win=33920 [TCP CHECKSUM INCORRECT] Len=186 TSV=15623435 TSER=15623435
   7924 41.579323   127.0.0.1             127.0.0.1             TCP      33405 > 4242 [ACK] Seq=1120 Ack=11153 Win=49536 Len=0 TSV=15623435 TSER=15623435
   7925 41.651754   192.168.1.103         72.14.223.19          TLSv1    Encrypted Alert
   7926 41.651786   192.168.1.103         72.14.223.19          TCP      39213 > https [FIN, ACK] Seq=1375 Ack=13630 Win=37632 Len=0 TSV=15623453 TSER=2375551429
   7927 41.652012   192.168.1.103         64.233.167.83         TLSv1    Encrypted Alert
   7928 41.652030   192.168.1.103         64.233.167.83         TCP      53046 > https [FIN, ACK] Seq=2301 Ack=14385 Win=40448 Len=0 TSV=15623453 TSER=1775196206
   7929 41.652190   192.168.1.103         209.85.133.136        TCP      43192 > http [FIN, ACK] Seq=1 Ack=1 Win=69 Len=0 TSV=15623453 TSER=2446663484
   7930 41.769660   Cisco-Li_19:e0:b6                           ARP      Who has 192.168.1.103?  Tell 192.168.1.1
   7931 41.891032   192.168.1.103         209.85.133.136        TCP      43192 > http [FIN, ACK] Seq=1 Ack=1 Win=69 Len=0 TSV=15623513 TSER=2446663484
   7932 41.915023   192.168.1.103         72.14.223.19          TLSv1    [TCP Retransmission] Encrypted Alert
   7933 42.308053   192.168.1.103         208.70.66.53          TLSv1    [TCP Retransmission] Application Data, Application Data, Application Data, Application Data
   7934 42.375116   192.168.1.103         209.85.133.136        TCP      43192 > http [FIN, ACK] Seq=1 Ack=1 Win=69 Len=0 TSV=15623633 TSER=2446663484
   7935 42.443120   192.168.1.103         72.14.223.19          TLSv1    [TCP Retransmission] Encrypted Alert
   7936 42.793741   Cisco-Li_19:e0:b6                           ARP      Who has 192.168.1.103?  Tell 192.168.1.1
   7937 43.331053   192.168.1.103         209.85.133.136        TCP      43192 > http [FIN, ACK] Seq=1 Ack=1 Win=69 Len=0 TSV=15623873 TSER=2446663484
   7938 43.500368   192.168.1.103         72.14.223.19          TLSv1    [TCP Retransmission] Encrypted Alert
   7939 43.579107   127.0.0.1             127.0.0.1             TCP      33405 > 4242 [PSH, ACK] Seq=1120 Ack=11153 Win=49536 [TCP CHECKSUM INCORRECT] Len=20 TSV=15623935 TSER=15623435
   7940 43.579185   127.0.0.1             127.0.0.1             TCP      4242 > 33405 [PSH, ACK] Seq=11153 Ack=1140 Win=33920 [TCP CHECKSUM INCORRECT] Len=186 TSV=15623935 TSER=15623935
   7941 43.579201   127.0.0.1             127.0.0.1             TCP      33405 > 4242 [ACK] Seq=1140 Ack=11339 Win=49536 Len=0 TSV=15623935 TSER=15623935
   7942 43.715411   Cisco-Li_19:e0:b6                           ARP      Who has 192.168.1.103?  Tell 192.168.1.1
   7943 45.251051   192.168.1.103         209.85.133.136        TCP      43192 > http [FIN, ACK] Seq=1 Ack=1 Win=69 Len=0 TSV=15624353 TSER=2446663484
   7944 45.353940   Cisco-Li_19:e0:b6                           ARP      Who has 192.168.1.103?  Tell 192.168.1.1
   7945 45.580189   127.0.0.1             127.0.0.1             TCP      33405 > 4242 [PSH, ACK] Seq=1140 Ack=11339 Win=49536 [TCP CHECKSUM INCORRECT] Len=20 TSV=15624435 TSER=15623935
   7946 45.580491   127.0.0.1             127.0.0.1             TCP      4242 > 33405 [PSH, ACK] Seq=11339 Ack=1160 Win=33920 [TCP CHECKSUM INCORRECT] Len=186 TSV=15624435 TSER=15624435
   7947 45.580527   127.0.0.1             127.0.0.1             TCP      33405 > 4242 [ACK] Seq=1160 Ack=11525 Win=49536 Len=0 TSV=15624435 TSER=15624435
   7948 45.611054   192.168.1.103         72.14.223.19          TLSv1    [TCP Retransmission] Encrypted Alert
   7949 46.378063   Cisco-Li_19:e0:b6                           ARP      Who has 192.168.1.103?  Tell 192.168.1.1
   7950 46.595129   192.168.1.103         208.70.66.53          TLSv1    [TCP Retransmission] Application Data, Application Data, Application Data, Application Data
   7951 47.299602   Cisco-Li_19:e0:b6                           ARP      Who has 192.168.1.103?  Tell 192.168.1.1
   7952 47.580164   127.0.0.1             127.0.0.1             TCP      33405 > 4242 [PSH, ACK] Seq=1160 Ack=11525 Win=49536 [TCP CHECKSUM INCORRECT] Len=20 TSV=15624935 TSER=15624435
   7953 47.580283   127.0.0.1             127.0.0.1             TCP      4242 > 33405 [PSH, ACK] Seq=11525 Ack=1180 Win=33920 [TCP CHECKSUM INCORRECT] Len=640 TSV=15624935 TSER=15624935
   7954 47.580318   127.0.0.1             127.0.0.1             TCP      33405 > 4242 [PSH, ACK] Seq=1180 Ack=12165 Win=49536 [TCP CHECKSUM INCORRECT] Len=20 TSV=15624935 TSER=15624935
   7955 47.580383   127.0.0.1             127.0.0.1             TCP      4242 > 33405 [PSH, ACK] Seq=12165 Ack=1200 Win=33920 [TCP CHECKSUM INCORRECT] Len=186 TSV=15624935 TSER=15624935
   7956 47.619122   127.0.0.1             127.0.0.1             TCP      33405 > 4242 [ACK] Seq=1200 Ack=12351 Win=49536 Len=0 TSV=15624945 TSER=15624935
```

---

### Post by elenctic on 2008-06-26
I finally found out the problem.  Its fix was pretty simple.  My home network had an IP address collision with the VPN's remote network, so I set my home network to use a new RFC 1918 private IP range.  All packets that were supposed to go to my home router were being routed straight to a machine at the other end of the VPN.  It took a while for the routing table to enable the routes that the VPN adds, so that might explain why the VPN worked for a few seconds then died.  I'm puzzled why this problem just showed up after I upgraded to 8.04 from 7.10 though.

---

### Post by madscientist on 2008-06-27
> **cds03900 said:**
> Yes it uses the term $HOST which I didn't enter when it asked me for a hostname.
You are correct, the distro it uses is not Ubunto but Xandros.
Any sugestions?I really don't have any.  I've looked at the script and it's bog-standard POSIX sh scripting as far as I can see.  I can't figure out any way you'd be seeing that text, if your /bin/sh is a valid POSIX shell.

If you type "/bin/sh --version" what do you get?

Please also paste the output of "cat ~/.vpn.cfg" (feel free to anonymize it if necessary but please tell us which fields seemed to have correct data).

---

### Post by bornjcan on 2008-07-01
I am completely new to linux Ubuntu and am having the same problem as everyone else, it seems with the same error (ncsvc fails to install) and terminal can't connect to ip address

The script by Mad Scientist seems to be the fix, however I dont seem to see either a link to the file or even a how to as to a fix. 

Can someone please post an easily found solution?

I am quite willing to do the work, however sorting through 20+ pages of threads which may or may not relate to my situation only to then pull up a terminal window and ruin my machine will not make my day..

I mean seriously !!!

:lolflag:

---

### Post by madscientist on 2008-07-02
> **bornjcan said:**
> The script by Mad Scientist seems to be the fix, however I dont seem to see either a link to the file or even a how to as to a fix.You can find my howto at [http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html)

If you still have problems after that, tell us where things went wrong for you: what you typed, what happened, what messages you got, etc.

---

### Post by bornjcan on 2008-07-06
i did all (i think correctly) at the end tho i get an invalid credentials msg after i input my password for vpn..
however the script loads and runs 
i think its my jobs network 


any help would be appreciated

---

### Post by madscientist on 2008-07-07
bornjcan: unfortunately I'm only a NetworkConnect user and don't have any idea about the kinds of errors you can get; I don't know how the tool is administered and I don't have any documentation that might describe various error messages and what they mean.

Where do you see this message?  Can you be sure to quote the message _exactly_ rather than paraphrasing it?  Too often paraphrasing changes the meaning enough to make it impossible to determine the problem.

I'm assuming that you're able to log in via the web service and maybe even Windows, so you're sure that your SecurID fob is synced up, your PIN is right (do you use a PIN + SecurID code?), and your username is valid.

Beyond that the only thing I'm aware of that could be an issue is the realm setting.  Did the folks managing your remote site tell you what to use for the realm value?  If not, how did you determine it?

If that's all correct then I suggest you email your server admins and ask if they have any ideas.

---

### Post by newsrg on 2008-07-13
Thanks madscientist.  I followed your recommendations.  Your script asks for Pin+SecurID and when i Type my password I get this:

"Searching for ncsvc in current working directory
Searching for ncsvc in /home/fidelio/.juniper_networks/network_connect done.
gij: unrecognized option -- `-h'
Try `gij --help' for more information."

It looks a java issue. Any idea how to solve this? 

NEWSRG

---

### Post by madscientist on 2008-07-13
I don't think NC works well with the "free" gij Java implementation that comes with Ubuntu by default.  You should install Sun's Java instead.  Use Synaptic to search for sun-java6-jre and install it, or else from the command line use:
```
sudo aptitude install sun-java6-jre
```
(enter your password when asked).  Hopefully when you do this it will become the default Java install.  If you continue to get the same error, post and I'll tell you have to change the default using the "alternatives" feature of the system.

---

### Post by w.kazimierczak on 2008-07-14
> **elenctic said:**
> I am using Ubuntu 8.04 an madscientist's script to connect to a vpn. It works for awhile (usually 30s or so) and then the connection dies. My ssh session freezes.
[...]
I finally found out the problem.  Its fix was pretty simple.  My home network had an IP address collision with the VPN's remote network, so I set my home network to use a new RFC 1918 private IP range.  All packets that were supposed to go to my home router were being routed straight to a machine at the other end of the VPN.  It took a while for the routing table to enable the routes that the VPN adds, so that might explain why the VPN worked for a few seconds then died.  I'm puzzled why this problem just showed up after I upgraded to 8.04 from 7.10 though.

I have a similar issue, but with a few differences and I can't find any solution:
[LIST]
[*]VPN connection hangs after 20-40 seconds
[*]same results when using madscientist script and normal (web) network connect access, but it works under Windows on the same machine
[*]the problem appears _only_ if I'm behind my home firewall (Asus wireless router, but I've observed it also once with another type of cheap wireless router)
[*]my LAN is in RFC 1918 private range (i've tried two different ranges), but corporate network isn't (it's 166.30/8)
[*]I couldn't find any interesting logs (nor system, neither ncsvc.log) at the moment when the other side stops responding to pings
[*]the problem appeared just after upgrading from 7.10 to 8.04
[/LIST]

After 10-20 additional seconds there's only keep-alive restart in ncsvc.log:
> 
ipsec.info Restarting keep-alives (engine.cpp:336)
ipsec.warn keep alive failed for ESP tunnel in:0x...
ipsec.warn Cleaning up sa 0x... (esp.cpp:58)
ipsec.info Switching to NCP mode (tunnel.cpp:552)


Any ideas?

---

### Post by newsrg on 2008-07-15
Thanks madscientist.  Unfortunately, I get the exact same message.  Any further suggestion? Thanks.

---

### Post by w.kazimierczak on 2008-07-16
> **w.kazimierczak said:**
> I have a similar issue, but with a few differences and I can't find any solution:
[LIST]
[*]VPN connection hangs after 20-40 seconds
...
[/LIST]



I found the solution: I've downloaded again network connect components from VPN SSL page by pressing network connect button and typing root password when prompted by 'su'.

---

### Post by Baltazar72 on 2008-07-17
First Thank you madscientist for your big effort on this subject.
I had some trouble getting things to work. 

After a fresh install of Ubuntu hardy :

```
sudo aptitude install sun-java6-plugin sun-java6-jdk sun-java6-jre

```
Installed libstdc++2.10-glibc2.2_2.95.4-22_i386.deb (due to  from error running madscientists script
: 
```
Exception in thread "AWT-EventQueue-0" java.lang.ExceptionInInitializerError
	at NC$3.run(NC.java:1282)

```
[HTML]http://debian.mirror.inra.fr/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb[/HTML]

So restarting, and running madscientists script, tunnel closes immediatly.

I did : ```
sudo passwd 
```

And started network connect from my companys website, and HEY PRESTO .. working :) I'm a happy puppy.

What I cannot understand is why the script cannot start the tunnel.

I'm not an expert in linux, but doing "sudo passwd" what do I risk with that ?

The log from ncsvc when using junipernc is attached.

thank you for all effort:)

my version :
Juniper Network Connect Server for Linux.
Version         : 1.2
Release Version : 5.5-0-Build11905
Build Date/time : Jun 22 2007 13:26:55 
Copyright 2002-2006 Juniper Networks

---

### Post by gmcauley on 2008-07-31
FOA, thanks madscientist for your contribution.

I was looking at the main loop in your script and wondering if this is possible:

I would like to mount a network share from a vpn after the connection is made (but obviously not before).

My scripting knowledge is small, but it seems you need to asynchronously call to connect, wait for a message of 'connected', and finally run the mount command.

Can anyone think of a way to do this with JNC?

(Sorry if this is slightly off topic)

---

### Post by b0red@werk on 2008-08-12
> **elenctic said:**
> I finally found out the problem.  Its fix was pretty simple.  My home network had an IP address collision with the VPN's remote network, so I set my home network to use a new RFC 1918 private IP range.  All packets that were supposed to go to my home router were being routed straight to a machine at the other end of the VPN.  It took a while for the routing table to enable the routes that the VPN adds, so that might explain why the VPN worked for a few seconds then died.  I'm puzzled why this problem just showed up after I upgraded to 8.04 from 7.10 though.

I'm having the same problem too.  I'm trying to understand your fix and I don't know if it'll work for me.  My home ip is 10.100.x.x/28 and the vpn tunnel is 192.168.x.x/24.  I don't know if I have to change my IP range at home.  I do get the TCP retransmission from wireshark.

---

### Post by kasulstyls on 2008-08-18
Thanks in advanced Madscientist.

I am having the same issue as bornjcan on post #198.

when log in via the website with my username and credentials it will start the Juniper service and connect fine.  When I use your script ( which is awsome ) i receive invalid credentials.  In your post #199, you mentioned that bornjcan may have used a the wrong realm.  once the script info is entered how can you go back and change the realm settings?  

Kas

---

### Post by madscientist on 2008-08-18
> **kasulstyls said:**
> once the script info is entered how can you go back and change the realm settings?

Unfortunately there's no handy GUI way to do this.  Zenity only gets you so far :-?.  To rerun the configuration, you should "rm ~/.vpn.cfg" from any terminal, then restart the script.

---

### Post by K0LO on 2008-08-18
You can also just manually edit the ~/.vpn.cfg file to change the REALM value.

---

### Post by kasulstyls on 2008-08-18
Thanks for the quick reply from you both.  

I did the rm of the file and redid the script.  I reused the default value of RSA as I do have an RSA fob. I still received invalid credentials, so I guess i will check and see if I am missing something on the REALM part at work tomorrow.

kas

---

### Post by kasulstyls on 2008-08-19
I forgot to ask in previous post but what other realms are there?

---

### Post by K0LO on 2008-08-19
That's a question that you need to ask your network admin. They can define any number of "realms" and give them any name. Here at work we have "Remote Access" and "Full Tunnel" realms defined; one does split tunneling and the other tunnels all traffic through the VPN. You need to know exactly what your admins have named the realm (hate that word; I think "profile" is a better choice of words).

---

### Post by fladnag on 2008-08-19
I've tried everything but still get the invalid credentials error.  Here's my environment:
1. Ubuntu Hardy Heron  8.04.1
2. OpenSSL 0.9.8g 19 Oct 2007

3. Juniper Network Connect Server for Linux.

   Version         : 1.2

   Release Version : 6.0-0-Build12507

   Build Date/time : Dec 27 2007 17:32:48 

   Copyright 2002-2007 Juniper Networks

4. java version "1.6.0_06"
   Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
   Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

ncapp> Failed to connect/authenticate with IVE. Error 104
ncapp> Incorrect credentials. Please check the username/password/realm.

The junipernc script works great but I always get the above error.

Any thoughts?

Problem has been resolved.  The system admin had the wrong realm name.

---

### Post by fladnag on 2008-08-20
Is there anyway to login to a server that has an invalid security certificate?  We have a test server for a new fiber line that we haven't gotten the cert for yet but would like to access via Juniper using Ubuntu Hardy Heron 8.04.

Thanks in advance!

---

### Post by kasulstyls on 2008-08-21
Thanks madscientist & K0LO!  After getting the correct realm name, the scripts connects like a charm.

---

### Post by lauraannq on 2008-08-25
:confused:to mad scientist and all those here i humbly beg your forgiveness...

i have read all 22 pages of this and honestly am "flumuxed'  

here's the bottom line

i have and asus (yes i know is xandros but hope prevails), and need to log into a juniper ssl network...

what script do i run, what info do i need.,  

please help,, my little brain hurts after installing all this unix software (i'm usally an xp user but i hate microsoft) and on top of the ssl issue i still cant get the asus to connect to my xp machine (but xp filemanager connects to my asus...)

so for us slow... tired... weak... nubies (yes i know we are a pain ) can i get a recap?

do i just read [http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html) and follow it.. are their fixes other then that?  

again thank you "oh, great and knowlegable ones":lolflag:

laura-ann
[http://biscuitq.blogspot.com](http://biscuitq.blogspot.com)

---

### Post by lauraannq on 2008-08-25
I just installed your script found on that link (the sun failed as i don't have the right repositories set up)

but i have jre 6.

i am getting a tun error...

any ideas on how to fix the tun problem...

:confused::confused::confused::confused::confused:

my head hurts....   :(

thanks

---

### Post by madscientist on 2008-08-26
Sorry lauraannq, but I'm having trouble following what you are trying to do and what the problems are.  When describing what doesn't work, please be very explicit, and be sure to quote (verbatim, or just cut and paste if possible) all error messages.  And, no need to apologize for being lost; we've all been there!

Asus is a company and they make a lot of different computer parts... do you mean you're using an Asus Eee PC?

What version of the Juniper Network Connect are you using (you can run ```
~/.juniper_networks/network_connect/ncsvc --version
``` to get this info)?

It's fine to use JRE 6; that's what I use as well.

I don't know what "the sun failed as i don't have the right repositories set up" means... is "the sun" meant to be the Sun JRE package install?  Does this mean you're NOT using those packages?  The JRE is only used for the graphical connection monitor tool; you don't need it to use the VPN itself.  Just run my script with the -nogui flag.  You won't be able to tell much about the state of the connection but if that works then at least you know it's just a problem with Java.

What errors did you get regarding tun, and where did you see them?  It's always just worked for me but maybe there are some extra packages you'd need to install on the Eee PC to get it working.  I'm afraid I don't know much about those.

---

### Post by lauraannq on 2008-08-28
okay this is solved!

my dh asked his juniper se and he got the fix.. it is SO simple

open a terminal window (ctl alt t)
login as root ==>  su

type  mkdir /dev/net
type mknod /dev/net/tun c 10 200

it will complain about the mod prob, but don't worry it is built into the kernel directory
version is 6.2

we tested and it worked!:KS

---

### Post by jasondrane on 2008-08-30
Hello, I first want to thank mad scientist for his tutorial on Juniper. I think i have it installed correctly but im kind of a noob to ubuntu. here is a copy of my error (with my vpn link removed of course) Any thoughts on this error would be appreciated.
Thanks in Advance

Jason

************************************error*********************************

Connecting to XXX.XXXXXXXX.com port 443
Generating Certificate .... done.
Exception in thread "AWT-EventQueue-0" java.lang.ExceptionInInitializerError
	at NC$3.run(NC.java:1282)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
Caused by: java.lang.ArrayIndexOutOfBoundsException: 3
	at JavaNC.<clinit>(NC.java:443)
	... 9 more

---

### Post by joshtt on 2008-09-04
> **gfa said:**
> Hi mad-scientist... thanks for that great script, unfortunattely, I have a problem with my Juniper connection, I think because my **company's server hasn't a valid certificate** (every time a connect with Fx get a warning about it).

If I run your script from CLI, get these warnings

```
$ ./junipernc 
Searching for ncsvc in current working directory
Searching for ncsvc in /home/gfa/.juniper_networks/network_connect done.
ncapp> Failed to connect/authenticate with IVE. Error 2
ncapp> Please check the ive hostname/ip and the ive certificate.
```

In the Juniper GUI, I can see an error about "**Failed to connect with IVE**", after closing both windows (dialog and main juniper window), got a question about restarting the VPN connection.

From Fx I have no problem connecting to my VPN (just the shell asking for root password every time).

Is there any way to disable the certificate validation?

Any help would be appreciated.

Thanks
gFa

I'm having the exact same issue here in Ubuntu Feisty.
Is there really no solution yet?

---

### Post by mmartin on 2008-09-26
I am trying to get this going on Hardy and have had no luck so far. 

I am running into the issue below. Is it not finding the libncui.so file located in the active directory?

$ ./junipernc 
Failed to load the ncui library.
Quitting.

Im on 64bit Hardy

---

### Post by hugoprado on 2008-10-02
Hi all. Mad Scientist, thank you for your page an tutorials on the matter.
I've followed all the steps and now I am connecting successfully using Juniper 1.2.

The problem I'm facing now is every time a try to download or upload a file using scp, the connection stalls and become useless.

Something more or less as described in previous posts, but for network problems. My connection remains correctly for hours, always same problem: once I use scp (I even tried gftp and is the same) the connection is broken.

Have any of you experienced this problem? Can you use scp without problems?

I'm using ubuntu Hardy Heron 8.04 on a 32 bits DELL laptop.


Thanks.

---

### Post by madscientist on 2008-10-02
> **mmartin said:**
> I am trying to get this going on Hardy and have had no luck so far. 

$ ./junipernc 
Failed to load the ncui library.
Quitting.

Im on 64bit HardyI've never tried this on 64bit.  Have you installed the 32bit compatibility packages?

---

### Post by madscientist on 2008-10-02
> **hugoprado said:**
> The problem I'm facing now is every time a try to download or upload a file using scp, the connection stalls and become useless.Very odd.  I've never had any problems using scp over the network link.  Having it bring the link down is extremely strange: from a network protocol perspective it's just bytes; why those particular bytes should cause a problem I have no idea.

I wonder if there's some way that your server is trying to block scp?

If you do the copy with ssh, does it work then?  Try something like:

```
tar cf - mydir | ssh remotehost tar -xBp -C /tmp -f -
```

and see if that works.

---

### Post by hugoprado on 2008-10-03
Hi mad scientist.
I've tried what you recommend, but the same results.
Apparently, my problem is unrelated to juniper.
Instead, it has to do with my wireless device and the drivers i have.

I have a Studio Laptop Dell - S1535. When i installed Hardy, it didn't detect wireless device, but on making an update, it worked fine. The problem is it installed the 'wl' driver, which is a restricted driver.

I'm reading this thread in case someone has the same problem

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/237894](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/237894)

I'm posting here again in case i solve the problem.

---

### Post by kasulstyls on 2008-10-31
Hi,

  Has anyone tried Juniper in 8.10?  I followed instructions on madscientist web page and successfully ran it in 8.04.  I did a fresh install of 8.10 and the scripts is working fine and I do see the Network connect java connection start but I get a popup of " Cannot find required libraries."  I ran the script in a terminal and see this 

" Searching for ncsvc in current working directory
Searching for ncsvc in /home/marn/.juniper_networks/network_connect done.
ncapp> DSSSL_load_so failed "

which looks like same issues on the 64bit version in the previous posts, although I am running the 32bit version.  Any help is greatly appreciated.

Kas

---

### Post by madscientist on 2008-10-31
I haven't tried 8.10 and I'm not sure when I will.  It turns out that my system at home (an older box) has an nVidia GeForce 5500 FX, which is considered obsolete by nVidia and not supported by their new 3D drivers.  So, my choices are (a) get a new video card that has supported drivers, (b) fall back to 2D mode and use the free nv driver, or (c) stay with Hardy until or unless something changes somewhere.

I haven't decided what to choose yet :-(

---

### Post by alf.hogemark on 2008-11-01
Hi

I am running 64 bit Ubuntu 8.10, and I got the same problem "loading ncui library".

I got it working by running 
"sudo update-java-alternatives -s ia32-java-6-sun"

So I think the problem is that 64 bit java is not working for the juniper network connect, you need to use 32 bit java.

Anyway, thanks a lot for the script mad-scientist, I finally got vpn working with your script.

Regards
Alf

---

### Post by kasulstyls on 2008-11-01
Ok got it.   to resolve the DSSSL_load_so failed I ran the command on the first post by Madscientiest sudo ln -s libssl.so.0.9.8 /usr/lib/i686/cmov/libssl.so.0   and now I connect fine.

I would also like to point out that when you first install, the java network connect window didn't popup. I looked through the posts and installed  [http://debian.mirror.inra.fr/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb](http://debian.mirror.inra.fr/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb)  thanks to  post #205 Baltazar72.   


Thanks again Madscientist and thanks to all within this forum.

---

### Post by insanity213 on 2008-11-06
I was getting the following error when executing the junipernc script on Ubuntu 8.10...

Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at java.awt.Component.<clinit>(Component.java:568)
Could not find the main class: NC. Program will exit.

It seemed pretty obvious why - I didn't have an xawt directory under that path, but did have that file in another path.  Did a quick ln -s as follows...

user@host:/usr/lib/jvm/java-6-openjdk/jre/lib/i386$ sudo mkdir xawt
user@host:/usr/lib/jvm/java-6-openjdk/jre/lib/i386$ cd xawt
user@host:/usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt$ sudo ln -s /usr/lib/jvm/java-6-openjdk/jre/lib/i386/headless/libmawt.so libmawt.so


Now I get a shiny new error...  Have no idea how to fix this one.  Perhaps I need to link more parts of JRE into the folder I created?
user@host:/$ junipernc
Xlib:  extension "RANDR" missing on display ":0.0".
Exception in thread "main" java.lang.UnsatisfiedLinkError: java.awt.Component.initIDs()V
	at java.awt.Component.initIDs(Native Method)
	at java.awt.Component.<clinit>(Component.java:571)
Could not find the main class: NC. Program will exit.
Xlib:  extension "RANDR" missing on display ":0.0".
Xlib:  extension "RANDR" missing on display ":0.0".
user@host:/$ 

Many thanks for any help that can be offered...

---

### Post by insanity213 on 2008-11-06
Update - Fixed my own problem. I hope this can help someone else someday. I removed the symlink I created and ran the following command to get Java straightened out.

sudo update-java-alternatives -s java-6-sun

---

### Post by buellman on 2008-11-10
Is this howto obsolete since network-manager has a "plugin" called network-management-vpnc?
"This package provides a VPN plugin for vpnc, providing easy access Cisco Concentrator based VPN's."
If yes: is there a way to figure out how to access the VPN-Server from my [university]("https://vpn.serv.uni-osnabrueck.de/dana-na/auth/url_default/welcome.cgi")?

Greets. Buellman

---

### Post by madscientist on 2008-11-10
> **buellman said:**
> Is this howto obsolete since network-manager has a "plugin" called network-management-vpnc?
"This package provides a VPN plugin for vpnc, providing easy access Cisco Concentrator based VPN's."Since this howto is for setting up Juniper Network Connect VPNs and the comment you quote is for setting up Cisco Concentrator VPNs, no, I don't think this howto is obsolete due to network-management-vpnc.

However, I don't know much about Cisco VPNs and I know even less about network-management-vpnc, so I can't say 100%.

---

### Post by buellman on 2008-11-10
Ok :-)
I didn't know there was a difference :-)

Thanks. Buellman

---

### Post by jeremygude on 2008-11-11
All,

For people who have upgraded to 8.10 and have lost a previously working client try epiphany (a browser).  I was able to get MadScientist's scripts to work for FireFox, but if you want to just use a browser try that one.



```
sudo aptitude install epiphany-browser
```

There is a game called epiphany, so make sure you use epiphany-browser

then just call the browser and go to your VPN website.

```
epiphany
```


Jeremy

---

### Post by jnkvbk on 2008-11-12
Who's got this working in 8.10? What client do you use, and what changes did you do it (if any)?

In Firefox I get to the point where it is supposed to install the client, and after that the browser just hangs and I have to kill it.

I am using ncui_1.2-2 and Java 1.6.0_10

---

### Post by jpborges on 2008-11-13
Hi, have Juniper Network Connect working on Ubuntu 8.10.

I've upgrade from 8.04 and after the upgrade it was still working.

---

### Post by realflash on 2008-12-08
I have this working in 8.10. It was working in 8.04 (no manual changes necessary), then I upgraded to 8.10 and it hung like yours.

I fixed it by rolling back from Sun JRE 6u10 to 6u7 (the previous version - there wasn't a u8 or u9 it seems). 

I proved it worked by using apt to remove sun-java6-bin etc and then dpkg -i on the same packages from 8.04. However, that meant that every apt-get upgrade took the JRE back to 6u10. I think you can 'pin' certain packages so they don't get upgraded, but in the end I overrode FireFox's plugin. By default the plugins in /usr/lib/mozilla/plugins will get used, but $HOME/.mozilla/plugins also gets read. The /usr one seems to override the /home one, weirdly. So I:

[LIST=1]
[*]Removed the package sun-java6-plugin 
[*]Downloaded 6u7 JRE from sun
[*]Extracted it to a directory in my $HOME
[*]linked jre/plugin/i386/ns7/libjavaplugin_oji.so in my $HOME/.mozilla/plugins
[/LIST]

Next time you start FF, it will use the Java linked in your $HOME rather than /usr/lib. You can verify your Java version in use at [http://www.javatester.org/version.html]("http://www.javatester.org/version.html")

Ian

---

### Post by elduderino23 on 2008-12-17
Outstanding work, mad scientist!

It seems I have one last hurdle.  The login form through my browser has *two* password fields (one for the network pw, and one for an rsa-key), but the command-line client only accepts one (to my knowledge).  
Does anyone know of a solution? 

Thanks!!!

---

### Post by Darrena on 2008-12-22
An easier solution for people on 8.10 might be to remove Sun-java6 and install sun-java5 rather than try to find an old package of JRE6.7

If you need to use both you could install both and use update-alternatives to switch which one you want to use.

---

### Post by robhauge on 2008-12-29
> **tmai said:**
> madscientist,

I followed the instructions on the first page and am getting partial sucess.  Basically,I am still prompted for the su password.  I'm running Feisty btw.

The error: 
```
/home/username/.juniper_network/network_connect/installNC.sh: 9: cannot open such file
/home/username/.juniper_network/network_connect/installNC.sh: 9: 1: not found 
Service needs to be reinstalled.
```

When I enter the root/su passowrd, it connects fine.  If I cancel this (CNTRL-D) and 'N' to try again, I still get connected.

I tried:
[LIST]
[*]deleting ~/.juniper_networks
[*]Start netconnect
[*]Cancel password prompt
[*]deteting ~/.juniper_networks/network_connect
[*]cp -R ~/.juniper_networks/tmp to ~/.juniper_networks/network_connect/
[*]extracted your installNC.sh and xlaunchNC.sh to the network_connect directory
[*]chmod +x ~/.juniper_networks/network_connect/*.sh
[*]Login to the juniper box and start netconnect
[*]Still prompted for su password
[/LIST]

I noticed that ~/.juniper_networks/network_connect/ncsvc was owned by root:root

I tried chown'ing it to myself and it still prompts for su password.

Do you (or anyone who have had my problem) know what I'm missing?

Regards and thanks for the post!




Hello. Does anyone have a solution for this issue ?

Regards Robert.

---

### Post by gtg694t on 2008-12-29
Note: I have had no luck getting Juniper Network Connect to work with Ubuntu 8.10 (AMD64).

However, I just installed Fedora 10 and it works practically out of the box. 

- Installed xterm (sudo yum install xterm)
- Downloaded & installed the latest Java JRE from the Sun website
- Copied the Java plugin to the Firefox directory 
- Logged into VPN via website
- Enter root password at xterm prompt
- Network Connect applet appeared and connected

Thanks,
Chris

---

### Post by ChuckV on 2008-12-31
I want to give big thanks to mad scientist and every one else who posted on this thread.  After a bit of trial and error and looking at what others have done I am successfully connecting to my company's VPN!

I did go back to sun Java 5, though I'm not sure that did anything.  My main issues were libstdc++ (I downloaded the package libstdc++2.10-glibc2.2_2.95.4-27_i386.deb) and DSSSL_load_so failed (I did sudo ln -s libssl.so.0.9.8 /usr/lib/i686/cmov/libssl.so.0).

Woot!

---

### Post by MikeSubtle on 2009-01-07
I just wanted to reply here to confirm that JRE 5 is required for Juniper Networks VPN SSL to install. 
I'm not using Ubuntu, I happen to be trying to get it to work under virtualbox running Windows XP but I had the same problems. I installed Sun Java JRE 5 and deleted all the browser cache (Delete All in IE), logged into the VPN SSL via the browser and let it install everything. It finally worked. 
Before installing Sun Java JRE 5 the error that I continued to get each time was simply 'You are not allowed to login. Please contact your administrator.'

---

### Post by flovo77 on 2009-01-26
No, for me this does not depend on Java 5.

I got it up running in Intrepid AMD64. I
- installed ia32-java-6-sun
- set JAVA6_32_HOME=/usr/lib/jvm/ia32-java-6-sun/bin
- in madscientist's junipernc.sh: replaced java="${JDK_HOME:+$JDK_HOME/bin
  /}java" with java="${JAVA6_32_HOME}/java"

---

### Post by tdelbecque on 2009-02-10
Hello all,

I can get a connection with Connect Network; /etc/resolv.conf is ok, with the new DNS ip's well set; but it seems that the DNS is not reachable : in fact none of the ip adresses in the other side or the VPN are pingable (so for the DNS). There is no collision problem in the adresses domains. Doe's someone has already meet such an issue ? Thanks a lot.

---

### Post by mikhmv on 2009-02-20
Hi, 
I tried this script on ubuntu 8.1 with x64. 
without changing Java to ia32-java it didn't run completely (from post #247). 
After changes: it run but I received message "Invalid Credentials".
Server, user name and password are correct.

Does anybody know how to fix it?
And Doew anybody know how to connect to Pitt.edu vpn?

my .vpn.cfg:
HOST="****.pitt.edu"
USER="****"
CERT="/home/max/.vpn.crt"
REALM="RSA"

and when I connected from firefox was downloaded this file:
/home/max/.juniper_networks/network_connect/META-INF/IMPORTED.RSA
I don't know how to use it.

Thanks advance

---

### Post by EdocI on 2009-02-25
Hello All,

I saw just about every error that has been mentioned here.

I finally got my system working. I am running Ubuntu 8.04.

I was able to use MadSci. instructions & script in order to get the Network Connect app running, however, like others in this thread, I could not login because of the Host Checker. I found a very easy solve though.. Use Firefox 2! For some reason, FF 3 does not execute the app correctly.

Also, for those that are having issues with the Realm. I found the realm as a hidden html field in the web access VPN page. For my company, it is "Secure ID". After using the IP (since my DNS lookup didn't work), I was able to see the Host Checker block.

Good luck all!

..EdocI

---

### Post by amylase on 2009-02-25
Just want to say "thank you so much!" for this post. 

I am running Ubuntu 8.1 on SONY Vaio notebook and ran into juniper issue as well. On approaching IT support they told me "Sorry we only support Windows and Mac" (we are talking about a major engineering university here...). Anyway, a friend passed me your article ([http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html)) and it solved my problem.  Your article and script are great. Thanks.

Just a couple of minor points if other people have similar questions like I did:

(1) sudo chmod a+x <filename>
This will make the script executable.

(2) If you need libstdc++2.10-glibc2.2_2.95.4-24_i386, it can be obtained and installed in this fashion:

wget mirrors.kernel.org/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
sudo dpkg --install libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
sudo apt-get install libstdc++2.10-glibc2.2

[http://myjavanotebook.blogspot.com/2008/04/libstdc210-glibc22-on-ubuntu-hardy-804.html](http://myjavanotebook.blogspot.com/2008/04/libstdc210-glibc22-on-ubuntu-hardy-804.html)

(3) I installed Java components (namely sun-java6-jdk and sun-java6-plugin) through System -> Administration -> Synaptic Package Manager.

[B]
Addendum[/B]
Just something about UnMHT (the Mozilla plug-in that allows you to open .mht pages or save webpages as single .mht). For some reason after installing UnMHT, java refused to work with the juniper script. After I disabled UnMHT (Tools -> Add-on -> Extension -> click "Disable" for UnMHT), java and juniper worked well again. Hope this piece of information is useful for someone in similar situations.

---

### Post by Dandapani on 2009-03-22
> **flovo77 said:**
> 
=> Network Connect fails if /tmp and /etc are mounted on different partitions!


BLESS YOU!  My working configuration (Intrepid on EEE PC) quit after I had made /tmp a tmpfs.  I didn't put the two events together until after I read your post.  Thanks!

---

### Post by binukavumkal on 2009-03-27
I have not done any set up. My Company uses Juniper SSL. They use Elusiva Everywhere session Java RDP.

---

### Post by brownbear on 2009-03-29
Whenever I click the start button to download networkconnect my firefox hangs and it never downloads.

OS:
Ubuntu 8.10

uname -a:
Linux xx 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

JVM:
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)

Firefox:
3.0.8

Firefox java plugin
1.6.0_10-b33

---

### Post by kloper on 2009-04-02
> **brownbear said:**
> Whenever I click the start button to download networkconnect my firefox hangs and it never downloads.

First do this (Ubuntu 8.10):

sudo apt-get install openssl libmotif3 libstdc++2.10-glibc2.2
sudo ln -s /usr/lib/libssl.so.0.9.8 /usr/lib/libssl.so.2
sudo ln -s /usr/lib/libcrypto.so.0.9.8 /usr/lib/libcrypto.so.2
sudo ln -s libssl.so.0.9.8 /usr/lib/i686/cmov/libssl.so.0

Then try downgrading to Java5 and use Opera instead of Firefox. That worked for me.
Now I am stuck with another error:

```
/bin/bash: ./getx509certificate.sh: No such file or directory

```

I got Network Connect 1.0 from my company's server. How can I get hold of version 1.2? Or just this file "getx509certificate.sh"... 

Cheers!

---

### Post by titantux on 2009-05-01
Hello,
It seems for a kind of restrictions from my company site, I'm not able to download completely Juniper Network Connect, so is incomplete as follow:

[email]titantux@titantux-desktop:~/.junipe[/email]r_networks$ ls -lrt

total 332

-rw-r--r-- 1 titantux titantux 190789 2009-03-26 20:31 tncc.jar

-rw-r--r-- 1 titantux titantux      6 2009-05-01 14:29 narport.txt

-rw-r--r-- 1 titantux titantux 104052 2009-05-01 14:29 dsHCLauncher_linux1.log

-rw-r--r-- 1 titantux titantux  24683 2009-05-01 14:34 dsHostChecker_linux1.log

[email]titantux@titantux-desktop:~/.junipe[/email]r_networks$ 


I was wondering if is possible to get from other place whole “.juniper_networks” directory content included “network_connect” directory and all inside files.

I took a look for previous post and found that should be like following:

/home/osx424242/.juniper_networks/network_connect

$ ls -al

total 976

drwxr-xr-x 3 osx424242 osx424242   4096 2008-06-05 01:10 .

drwxr-xr-x 4 osx424242 osx424242   4096 2008-06-05 01:10 ..

-rw-r--r-- 1 osx424242 osx424242    770 2008-02-15 08:30 getx509certificate.sh

-rw-r--r-- 1 osx424242 osx424242   1173 2008-06-05 01:10 installnc.log

-rwxr--r-- 1 osx424242 osx424242    716 2008-06-05 01:10 installNC.sh

-rw-r--r-- 1 osx424242 osx424242 493680 2008-06-05 01:10 libncui.so

drwxr-xr-x 2 osx424242 osx424242   4096 2008-02-15 08:30 META-INF

-rw-r--r-- 1 osx424242 osx424242      0 2008-06-05 01:10 missing.info

-rw-r--r-- 1 osx424242 osx424242     30 2008-06-05 01:10 missing.rpt

-rwxr--r-- 1 osx424242 osx424242  24888 2008-06-05 01:10 ncdiag

-rw-r--r-- 1 osx424242 osx424242   4256 2008-06-05 00:30 ncdiag.log

-rw-r--r-- 1 osx424242 osx424242  45475 2008-06-05 01:10 NC.jar

-rws--s--x 1 root     root     332044 2008-02-15 08:30 ncsvc

-rw-r--r-- 1 osx424242 osx424242     61 2008-06-05 01:10 ncsvc.log

-rw-r--r-- 1 osx424242 osx424242   3637 2008-06-05 01:13 ncuijava.log

-rw-r--r-- 1 osx424242 osx424242  26058 2008-06-05 01:13 ncui.log

-rw-r--r-- 1 osx424242 osx424242     14 2008-02-15 08:30 version.txt

-rwxr--r-- 1 osx424242 osx424242   1632 2008-06-05 01:10 xlaunchNC.sh


Is it possible ,just for example, something taring the whole “.juniper_networks” directory in order to I'm able to untaring to  mine ? Or where can I download it ?

Regards,
titantux

---

### Post by caseyboardman on 2009-05-04
Two posts I'd like to quote:

I'm in the same boat as #1:
> **elduderino23 said:**
> Outstanding work, mad scientist!

It seems I have one last hurdle.  The login form through my browser has *two* password fields (one for the network pw, and one for an rsa-key), but the command-line client only accepts one (to my knowledge).  
Does anyone know of a solution? 

Thanks!!!

And #2 just worked for me:
> **jeremygude said:**
> All,

For people who have upgraded to 8.10 and have lost a previously working client try epiphany (a browser).  I was able to get MadScientist's scripts to work for FireFox, but if you want to just use a browser try that one.



```
sudo aptitude install epiphany-browser
```

There is a game called epiphany, so make sure you use epiphany-browser

then just call the browser and go to your VPN website.

```
epiphany
```


Jeremy

I don't know what epiphany-browser is doing differently from firefox, but I wish firefox would do it.

Thanks all!

*EDIT:* I am using kubuntu 9.04 (Jaunty Jackalope) and Sun Java 6.

*EDIT 2 circa June 3, 2009:* This doesn't work for me anymore, even after a reboot and nothing else (firefox, kopete, vuze) running.  My only consistent workaround is virtual box and an instance of XP.  Could try it with a Red Hat install if you want to keep it free.  I've read a lot saying that juniper tested on that.

---

### Post by titantux on 2009-05-05
> **kloper said:**
> First do this (Ubuntu 8.10):

sudo apt-get install openssl libmotif3 libstdc++2.10-glibc2.2
sudo ln -s /usr/lib/libssl.so.0.9.8 /usr/lib/libssl.so.2
sudo ln -s /usr/lib/libcrypto.so.0.9.8 /usr/lib/libcrypto.so.2
sudo ln -s libssl.so.0.9.8 /usr/lib/i686/cmov/libssl.so.0

Then try downgrading to Java5 and use Opera instead of Firefox. That worked for me.
Now I am stuck with another error:

```
/bin/bash: ./getx509certificate.sh: No such file or directory

```

I got Network Connect 1.0 from my company's server. How can I get hold of version 1.2? Or just this file "getx509certificate.sh"... 

Cheers!
I foud it !! thank you very much for Sriraman's blog !!!! :guitar:


---------------start of getx509certificate.sh ----------------
#!/bin/bash

if [ -z "$1" ] || [ -z "$2" ] 
then
	echo "Insufficient number of args"
	echo "$0 <ive_ip_address> <output_file>"
	exit
fi
echo Connecting to $1 port 443
openssl s_client -connect $1:443 < /dev/null 1>out.txt 2>err.txt
if [ "$?" -ne "0" ] 
then
	cat err.txt
	exit
fi
echo -n Generating Certificate
grep -in "\-----.*CERTIFICATE-----"  out.txt | cut -f 1 -d ":" 1> out1.txt
let start_line=`head -n 1 out1.txt`
let end_line=`tail -n 1 out1.txt`
if [ -z "$start_line" ]
then
	echo "error"
	exit
fi
let nof_lines=$end_line-$start_line+1
#echo "from $start_line to $end_line total lines $nof_lines"
echo -n " .... "
head -n $end_line out.txt | tail -n $nof_lines 1> out1.txt
openssl x509 -in out1.txt -outform der -out $2 
echo done.
rm out.txt out1.txt err.txt
-----------------end of  getx509certificate.sh ---------------

So lets... try it....

here is the link blog ... [http://junipper-ssl-vpn-ubuntu.blogspot.com/2008/01/connecting-to-junipper-ssl-vpn-from.html]("http://junipper-ssl-vpn-ubuntu.blogspot.com/2008/01/connecting-to-junipper-ssl-vpn-from.html")


Regards,
titantux

---

### Post by dsmex on 2009-05-12
Hi,

I am trying to get juniper connect to work on Kubuntu 9.04 amd64.

I have tried before on various ubuntu distros with no success.

This time I manage to get the software running using Mad Scientist's script. The java applet pops up and tries to connect, but there it fails...

I seems to me that the software setup is OK, and the problem is in the settings.

I'm trying to connect to a company that delivers virtualization and online disk space to companies. Because of this, the URL is different for each company/client. The URL I type in for the login page is something like:

ssl.company.com/client_company

It gets redirected to something like:
[https://ssl.company.com/something/auth/(client_company)url_default/welcome.cgi](https://ssl.company.com/something/auth/(client_company)url_default/welcome.cgi)

- Can anybody tell me which URL I should use as HOST?

- If I use just 'ssl.company.com' I get this message:
ncapp> Failed to connect/authenticate with IVE. Error 2
ncapp> Please check the ive hostname/ip and the ive certificate.

- If I use 'ssl.company.com/' (added slash) I get this messsage:
ncapp> Failed to connect/authenticate with IVE. Error 104
ncapp> Incorrect credentials. Please check the username/password/realm.

I found the realm 'Domain Users' in the source of the login page:
<input type="hidden" name="realm" value="Domain Users">

I would appreciate any hints on the following:
- If this is a problem with the settings or the software setup
- Which URL to use for host
- Any steps I can do to debug it..

Some info:
I am using ia32-java-6-sun
I downloaded the java code using firefox 64-bit. I tried using opera and got the exact same files.
Would it matter if I use firefox 32-bit to get the code?
I never got any prompt from the browser. A window pops up, downloads, installs, and says something like 'Failed, sorry..' and quits.

Thanks,

---

### Post by Shekibobo on 2009-05-14
So, I'm pretty new to all this, but I'm trying to access the VPN at my school.  Seems like everything is working just fine, until I get to the part where I enter my password.  After the password is entered I get a popup that says: "VPN Failed!", and the terminal echoes back:

```

Failed to load the ncui library.
Quitting.

```

I'm using Jaunty 9.04 64 Bit.  I tried installing ia32-sun-java-bin, but that didn't seem to help.  I haven't seen really seen anything referencing the ncui library with a solution in this thread yet other than the ones talking about ia32 java.  Has anybody tried to figure this out yet?  **Do we know why it can't load the ncui library?**

---

### Post by Shekibobo on 2009-05-14
Alright, nevermind.  I tried Alf's suggestion again and ran:


```
sudo update-java-alternatives -s ia32-java-6-sun
```


one more time, and it worked this time.  Juniper starts up now, but now I get an error saying invalid credentials.  Probably that realm issue he was talking about, but my IT department doesn't seem to have ever heard of Juniper asking for a realm.  So at this point, I'm just at a loss.  All my other information is correct.  Unless maybe I'm supposed to connect to a specific port on the server?  Probably not.  The program's working, though.  So, I got that far.  Only took me a couple days to get me this far.

---

### Post by MoreThanBits on 2009-05-17
> **binukavumkal said:**
> I have not done any set up. My Company uses Juniper SSL. They use Elusiva Everywhere session Java RDP.
Very little is required of the Linux client when setting up a VPN Terminal Services session via Juniper with javaRDP and Elusiva Everywhere.  Review "How do I download and install Java for my Linux computer?" at <http://www.java.com/en/download/help/5000010500.xml>. 

Using Firefox 3.0.10  and Kubuntu/Ubuntu 8.04.2, the link in  /usr/lib/firefox-addons/plugins  was
ln -s /usr/lib/jvm/java-6-sun-1.6.0.07/jre/plugin/i386/ns7/libjavaplugin_oji.so

My VPN preparation was complete after a successful test at <http://www.java.com/en/download/installed.jsp>.

search terms:
Ubuntu
Kubuntu
Firefox
Juniper
VPN
Terminal Services
Java Remote Desktop
javaRDP
Elusiva Everywhere

---

### Post by dsmex on 2009-05-18
Shekibobo:

Did you have a look at the HTML source of the log-in page?

On my juniper log-in page, I found the following:

<input type="hidden" name="realm" value="REALMNAME">

Search for name="realm" in the HTML. This should be fixed. The value parameter is the name of the realm. (In this case REALMNAME)

I'm also on ubuntu 9.04 64-bit. I manage to get the juniper java applet running from shell (not using browser), but I cannot connect.

I'm not sure if it's my setup or I just use wrong parameters for the connection. And... unfortunately I'm afraid the IT-guys at the company have no idea..

---

### Post by buellman on 2009-05-19
Could someone pls explain in detail how to get this to work on a jaunty 64-bit cleaninstall?

TY. Buellman

Edit: This is where I am so far:
- installed ia32-java-6-sun
- installed Opera as Epiphany and Firefox didn't dl the things that are in .juniper_networks. With Opera I now have the content in this hidden folder
- I tried starting ncui with Opera over the Webinterface of the VPN I would like to use. The popup comes where I get asked for my root-pass. I hit 2 times Enter. The dialogue disapears but ncui doesn't start
- I tried the script from the Topic-Starter. All I get is:
"Could not unpack Juniper Network Connect!
Check the error log file '/tmp/junipernc.10976' for more information."
The log tells me:
"Run as: ./junipernc 
./junipernc: 228: jar: not found"

So what do I do wrong?

---

### Post by Shekibobo on 2009-05-19
> **dsmex said:**
> Shekibobo:

Did you have a look at the HTML source of the log-in page?

On my juniper log-in page, I found the following:

<input type="hidden" name="realm" value="REALMNAME">

Search for name="realm" in the HTML. This should be fixed. The value parameter is the name of the realm. (In this case REALMNAME)

I'm also on ubuntu 9.04 64-bit. I manage to get the juniper java applet running from shell (not using browser), but I cannot connect.

I'm not sure if it's my setup or I just use wrong parameters for the connection. And... unfortunately I'm afraid the IT-guys at the company have no idea..

That did the trick.  I appear to be connected, and.... awesome.  I can now print to school computers directly from my laptop.  

Thanks a ton, dsmex.

---

### Post by Riverside on 2009-05-24
Somewhat to my surprise (and disappointment), I have been unable to get the Juniper Network Connect client working properly on 9.04, despite having used it successfully on 6.06, 7.10 & 8.04.

For completeness, the method I use is:

```
$ sudo aptitude install sun-java6-bin
$ sudo aptitude install sun-java6-plugin
$ sudo aptitude install sun-java6-jre

$ sudo aptitude install libmotif3

$ sudo dpkg -i libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

(libstdc++2.10-glibc2.2_2.95.4-24_i386.deb is a package originally supplied with 7.10)

$ sudo ln -s /usr/lib/libssl.so.0.9.8 /usr/lib/libssl.so.2
$ sudo ln -s /usr/lib/libcrypto.so.0.9.8 /usr/lib/libcrypto.so.2
$ sudo ldconfig

sudo passwd root (to enable root account for first client installation)
```

This works perfectly, as previously mentioned, on 6.06, 7.10 & 8.04.

On 9.04 it works up to a point in that after connecting to the SSL VPN gateway using Firefox and clicking "Network Connect Start" the Java applet runs, the Network Connect client connects, establishes a connection and is allocated a VPN IP address (confirmed by the presence of a tun0 interface with that IP address allocated to it in the output of the ifconfig command).

However, the Network Connect VPN connection remains connected for 5-10 seconds only then the connection drops out.

My guess is that Network Manager is being too clever (for want of a better term) and is dropping the Network Connect VPN connection because it didn't initiate it.  That is only a guess though since there is nothing in the various log files in /var/log, nor ~/.juniper_networks/network_connect/ncui.log (nor runnc.log) to indicate what is actually happening.

Has anyone managed to get the Juniper SSL VPN Network Connect client working properly on a new installation of 9.04?  If so, a detailed, specific, point by point step by step guide would be helpful.

---

### Post by buellman on 2009-05-24
@ Riverside:
Have you tried it with Opera? I tried to get it work with a cleaninstall of 9.04 (32bit) and didn't even get the Network-Connect client to start with firefox nor epiphany. With Opera it worked for me. Maybe you try that?

Greets. Buellman

---

### Post by Riverside on 2009-05-24
> **buellman said:**
> @ Riverside:
Have you tried it with Opera? I tried to get it work with a cleaninstall of 9.04 (32bit) and didn't even get the Network-Connect client to start with firefox nor epiphany. With Opera it worked for me. Maybe you try that?I'm fairly certain that wouldn't help with my issue, since my issue doesn't concern installation and launch of the Network Connect client but rather keeping an active SSL VPN connection active once the Network Connect client has successfully launched.

---

### Post by ihristov on 2009-05-30
1) Can someone post a tar.gz (after deleting log files, etc) of his ~/.juniper_networks folder. I can't install the client on my machine, because my corporate network is forcing a policy via the "Host Checker" facility and I don't get an option to install "Network Connect". I need a copy of the "Network Connect" client for Linux. I am using Ubuntu 9.04 (32-bit)

2) For those trying to use split tunneling.
  a) The split tunneling is normally setup on the server side, i.e. the server administrator determines if they want to allow it
[http://forums.juniper.net/jnet/board/message?board.id=SSL_VPN&message.id=505](http://forums.juniper.net/jnet/board/message?board.id=SSL_VPN&message.id=505)
  b) Even if the server side is not allowing split tunneling and it's pushing all the traffic trough the VPN, it is still possible to workaround the problem. The issue is with the client — probably based on server-side policy - it aggressively shuts down all other network connections and forces the exclusive use of the VPN connection. Manual changes to the routing table are quickly reverted by a daemon, who deletes the changes.

I have found a way around this by not adding a default gateway, but instead add add multiple specific roting rules. 

For start I would suggest that you try it with only one specific host. Ultimately you will need a script that will add all the appropriate networks that should be going trough the VPN first, then add the more generic rule at the end. 

Let me know if you need more specific information. I have this working under Windows.

---

### Post by epostma on 2009-05-30
Thanks all, in particular MadScientist.

I think I have a new issue to report; for me, running MadScientist's junipernc script made /etc/resolv.conf owned by root and mode 0640, i.e., -rw-r-----, meaning I could not read it. This prevented any host (inside and outside the VPN) from being resolved. It is easily repaired by running sudo chmod a+r /etc/resolv.conf after logging in, or by editing the script. This is with juniper version 6.3.0 (that's what ~/.juniper_networks/network_connect/version.txt says, anyway).

Erik.

---

### Post by lakerol on 2009-06-18
Agreed: #1 is quite a pain.  Anyone with an idea for the two password (pw + securID) problem?  The obvious things (concatenating them, etc) don't work...


> **caseyboardman said:**
> Two posts I'd like to quote:

I'm in the same boat as #1:


And #2 just worked for me:


I don't know what epiphany-browser is doing differently from firefox, but I wish firefox would do it.

Thanks all!

*EDIT:* I am using kubuntu 9.04 (Jaunty Jackalope) and Sun Java 6.

*EDIT 2 circa June 3, 2009:* This doesn't work for me anymore, even after a reboot and nothing else (firefox, kopete, vuze) running.  My only consistent workaround is virtual box and an instance of XP.  Could try it with a Red Hat install if you want to keep it free.  I've read a lot saying that juniper tested on that.

---

### Post by ejjp on 2009-07-02
In feisty the script of madscientist worked ok. Now I have a eee-pc with debian lenny (with lxde) and an user with the sudo power. Iceweseal, sunjava6, ... I think that I follow the how-to to perfectly as before, however I do not able to dowload the .juniper_network folder. I have tarred my .juniper folder from feisty and put in the debian system and when run junipernc.sh (the first time ask me the sudo password, I fill the fields with my user, host...password, a new .vpn.crt is generated, the file .vpn.cfg is correct according to the new location and then appears this message:

:~$ junipernc.sh 
Searching for ncsvc in current working directory
Searching for ncsvc in /home/ejjp/.juniper_networks/network_connect done.
ncsvc> Failed to setuid to root. Error 1: Operation not permitted
java: ncui.cpp:262: void NCUI::run(): Assertion `m_conn->isConnected()' failed.
/usr/bin/junipernc.sh: line 265:  3064 Abortado                "$java" -jar "$_ncpath/NC.jar" -h "$HOST" -u "$USER" -p "$password" -f "$CERT" -r "$REALM"


Also, when I have logged in the vpn juniper web page and push the start button, the terminal NCinstall.sh does not appear as in feisty. Any idea?

---

### Post by cpepera on 2009-07-20
I was able to get the applet to run after I switched to 32bit Java using Madscientist's script however I am getting the "Invalid Credentials" error.  I am assuming this is an issue with the VPN Service Realm that was specified.  I just used the default in the Junipernc script.  I asked my IT department what the VPN Service Realm was and they had not heard that name so I searched the source of my login page and again (as suggested on this thread), no luck.  What is the VPN Service Realm?  Are there typical values that I can try or would it be specific to each institution/company?  Where else might I be able to find it?

Thanks everyone for all the helpful work thus far!

---

### Post by madscientist on 2009-07-20
Hi all.  Sorry I've been out of touch: work was (still is) crazed.  Unfortunately I'm still using my old system which is a 32bit system, running Ubuntu 8.04 (old nvidia card so I can't upgrade ATM), so I don't have a lot of advice for folks trying to work out problems with newer systems.

cpepera; I'm not sure exactly what you looked for when you searched the source of the login page.  You should look for an "input" field something like this: <input type="hidden" name="realm" value="RSA">  The string after the value is the one you want.

Did you not find anything like this in the page source?

Also, what version of NC are you using?  I think there are newer versions than the one I'm using, which appear to have changed.

---

### Post by cpepera on 2009-07-20
Madscientist, I could not find any line in the login page like you described.  I login to get to a web interface from which I can select from a variety of different VPN access modes one of which is NC -- not sure if this is different than most users.  I checked the source at the access mode web interface and also at the page displayed when NC is being launched but I could not find any indication of the realm.

Version 6.3.0

---

### Post by cpepera on 2009-07-20
Interestingly I can launch the applet no problem on my desktop at work (Ubuntu 8.10) through the web interface.  All I had to do was create a root password.  The rpm line in my xlaunchNC script is commented out (by default, not by me).  

```

# check if modprobe can locate the tun module. 
#Adding dry run option we dont want to insmod, just check if tun is available

rm -rf $1/missing.rpt
/sbin/modprobe -n tun 1> $1/missing.info
if [ "$?" -ne "0" ]
then
    echo "Modprobe for Tun driver failed." > $1/missing.rpt
#    rpm -q tun 1> $1/missing.rpt
fi

```

But, of course I don't need to use NC at work :(

edit: I should say that I run 8.10 32bit at work and 9.4 64bit at home.

---

### Post by cpepera on 2009-07-20
Ok, I was able to use Network Connect via madscientist's script (thanks!) after I figured out the realm.  I can login specifying a number of realms so it wasn't explicit in the login page source.  I also had to switch to 32bit java but now NC is running on 64bit 9.04.  Still need to work out some some firewall issues. I lost my internet connection and couldn't ping the nameservers on my work's network if I didn't disable firestarter, but I'll need to learn some more about networking first.

Thanks again.  This thread is great, what a relief! :D

---

### Post by GreyKnight on 2009-07-28
First, I want to thank madscientist, who has shown great patience throughout the many pages of this topic (all of which I've at least skimmed :) ).

I want to add to the list of symptoms and remedies that there seems to be a conflict caused by Firefox 3.5 on Ubuntu 9.04/Jaunty Jackalope.  Specifically, changing the Privacy setting to anything other than the default "Remember history" prevents Network Connect from loading.  It throws the following Java error.

```
load: class SecureNCLauncher.class not found.
java.lang.ClassNotFoundException: SecureNCLauncher.class
    at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:151)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Plugin2ClassLoader.java:429)
    at sun.plugin2.applet.Plugin2Manager.createApplet(Plugin2Manager.java:2866)
    at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1395)
    at java.lang.Thread.run(Thread.java:619)
Caused by: java.io.IOException: open HTTP connection failed:https://vpn-ssl.bloodstockwww.com/dana-cached/nc/SecureNCLauncher/class.class
    at sun.plugin2.applet.Applet2ClassLoader.getBytes(Applet2ClassLoader.java:459)
    at sun.plugin2.applet.Applet2ClassLoader.access$000(Applet2ClassLoader.java:46)
    at sun.plugin2.applet.Applet2ClassLoader$1.run(Applet2ClassLoader.java:126)
    at java.security.AccessController.doPrivileged(Native Method)
    at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:123)
    ... 6 more
Exception: java.lang.ClassNotFoundException: SecureNCLauncher.class
```It took me a very long time to figure this one out.  Why would disabling third-party cookies create what looks like a Java path issue?  It wasn't until post #255, where kloper suggested Opera (which worked), that I began to investigate Firefox itself.

I had already tried reverting to Firefox 3, but used the same FF3.5-upgraded profile (specifically, prefs.js).  I did discover that the break isn't permanent: setting the Privacy back to the default will restore NC access.  I also don't see this on Windows XP, FWIW.

---

### Post by sevenths on 2009-08-07
I thought I'd add some notes I gathered while playing around with the NC client in Linux.

To use the network connect client on Linux without having to install or use Java (which is a silly requirement, if you ask me), you need the ncsvc binary and the IVE's public certificate in DER format:

[LIST]
[*]Install network connect either by executing it in the IVE interface with a browser, or fetch the RPM from the IVE admin interface (Maintentance -> System -> Installers -> Network Connect for Linux.
[*]RPM: *Extract* the RPM (don't *install* it unless you really want to) to get the ncsvc binary.
[*]Web: The ncsvc binary is found in ~/.juniper_networks/network_connect/
[/LIST]

To set up the certificate file, the client executes the ncLinuxApp.jar/getx509certificate.sh script, which does some pretty silly things to fetch the certificate from the IVE server. A more concise way of getting the certificate would be:

```

echo | \
openssl s_client -connect ive.example.com:443 2>&1 | \
sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' | \
openssl x509 -outform der -out ive.crt

```

The binary can now be executed. It is setuid root (another somewhat silly solution), so a normal user can run it directly without sudo or any passwords.

The *full* list of ncsvc parameters is below. Different versions of the binary report different usage/args, and there are some differences in Juniper's documentation. These are the currently supported parameters for the 6.3 version (found in the binary -- several of them are not shown in the command help/usage):
```

-h|--host         <arg> - Hostname of IVE
-u|--username     <arg> - Username
-p|--password     <arg> - Password
-r|--realm        <arg> - Realm
-f|--certificate  <arg> - Certificate in DER format
-m|--md5hash      <arg> - Hash of what? Not used?
-P|--Port         <arg> - IVE service port. Not generally used?
-L|--log-level    <arg> - Log level
-v|--version            - Print version info
-x|--???                - unknown. In the code, but not documented.
-K|--Kill               - Kill ncsvc
-y|--proxy        <arg> - Proxy address
-z|--proxy-port   <arg> - Proxy port
-s|--proxy-user   <arg> - Proxy username
-a|--proxy-pass   <arg> - Proxy password
-d|--proxy-domain <arg> - Proxy domain
-g|--upload-log         - Upload client logs

```

The ncsvc binary logs to ~/.juniper_networks/network_connect/. To change this, the binary can be edited to use /opt/jnc/ or /var/log/.

It would be great to have the Network Connect client work with Ubuntu/Gnome's [NetworkManager]("http://projects.gnome.org/NetworkManager/"). It should be fairly simple to modify the [vpnc plugin for NetworkManager]("http://git.gnome.org/cgit/network-manager-vpnc/") to work with ncsvc. This would be a major advantage over the Java GUI.

Another option would be to reverse engineer the communication used by ncsvc. It shouldn't be too difficult to do. On Windows, the SSL communication can be intercepted using [KAPIMON]("http://gilisa.free.fr/outils/kapimon/")'s ssclear.cmd plugin. (Pretty much the only other alternative, [HTTP Analyzer]("http://www.ieinspector.com/httpanalyzer/index.html"), doesn't work since it cannot open hidden processes.)

After authenticating and negotiating the tunnel parameters over HTTPS, an IPSec ESP tunnel is set up. By default it falls back to use NCP if the ESP packets time out. The NC protocol is most likely ESP/IPSec encapsulated in HTTPS.

A few things I haven't figured out:
[LIST]
[*]Can the NC client use other factors than username+password for auth? For example a client certificate or SecurID/PIN. When I try it, the ncsvc binary exits due to an unexpected authentication step (the SecurID/PIN prompt). I haven't tried to use a client certificate, and don't really know how to try it either.
[*]The NC client is rather brutal with /etc/resolv.conf. It doesn't seem to support resolvconf for proper management, so split tunneling can suffer.
[*]Getting connection statistics from the ncsvc daemon seems to require some form of authentication. The GUI app does this, but it should be possible to do from the command line as well if the right protocol is used.
[/LIST]

Lastly, I tried getting a root shell on the IVE by trying various tricks at the LILO 22 boot prompt (using a serial console). No matter what I tried (init=/bin/sh, various kernel parameters, other kernel images), it booted as normal.

Do any of you have access to an out-of-warranty Juniper SA of any model? It would be really interesting to remove the disk and put it into another computer to see what it contains. That should also reveal the encryption key used for the [upgrade images]("http://www.juniper.net/techpubs/software/ive/6.x/6.3/#sw").

---

### Post by configt on 2009-08-11
> **buellman said:**
> Could someone pls explain in detail how to get this to work on a jaunty 64-bit cleaninstall?

TY. Buellman

Edit: This is where I am so far:
- installed ia32-java-6-sun
- installed Opera as Epiphany and Firefox didn't dl the things that are in .juniper_networks. With Opera I now have the content in this hidden folder
- I tried starting ncui with Opera over the Webinterface of the VPN I would like to use. The popup comes where I get asked for my root-pass. I hit 2 times Enter. The dialogue disapears but ncui doesn't start
- I tried the script from the Topic-Starter. All I get is:
"Could not unpack Juniper Network Connect!
Check the error log file '/tmp/junipernc.10976' for more information."
The log tells me:
"Run as: ./junipernc 
./junipernc: 228: jar: not found"

So what do I do wrong?

You need to put junipernc in a directory in your path.  Then run junipernc from the ~/.juniper_networks/network_connect/ directory.

---

### Post by configt on 2009-08-11
Alright, so the junipernc script has enabled me to get further than before (thank you MadScientist!).   The cert, realm, uid, pw, token, ia32-sun-java, etc., etc., are all working great on my clean install of ubuntu 9.04 amd64.

Now, the connection process is aborting due to being unable to run the "host checker" that wants to run a "cache cleaner" among other useless windows and browser oriented things.  The IT folks have the server configured so it will reject the connection if it doesn't pass this step, and they won't change the server setting such that Linux users bypass the useless "host checker" script.

```

20090811153019.855492 ncsvc[11209] dsclient.info --> POST /dana-na/cc/ccupdate.cgi (authenticate.cpp:136)
20090811153019.965600 ncsvc[11209] dsclient.info <-- 200  (authenticate.cpp:168)
20090811153019.965635 ncsvc[11209] dsclient.error state post auth cache cleaner failed, error 10 (dsclient.cpp:336)
20090811153019.965749 ncsvc[11209] ncapp.error Failed to authenticate with IVE. Error 10 (ncsvc.cpp:187)

```I found some mention of this problem here (starting at post #177):
[http://ohioloco.ubuntuforums.org/showthread.php?t=232607&page=18](http://ohioloco.ubuntuforums.org/showthread.php?t=232607&page=18)


Does anyone have a hack to get around this "host checker" issue?

Before I upgraded my PC from a P4 to an I7 (32 bit -> 64 bit arch) I was able to connect using firefox with no issues ever.  I used it very frequently.  Now that I am running 64bit, I can no longer connect using the firefox browser (apparently due to an incompatibility between ncsvc and java 64 bit).  You can't use a 32 bit plug in, in 64 bit firefox, and I don't want to use a 32 bit version of firefox just to connect to the vpn, if I even knew how to install a 32 bit version on a 64 bit arch in the first place.

This is extremely frustrating.

:confused:

---

### Post by stomic on 2009-08-19
> **insanity213 said:**
> Update - Fixed my own problem. I hope this can help someone else someday. I removed the symlink I created and ran the following command to get Java straightened out.

sudo update-java-alternatives -s java-6-sun

thanks!!!
this solved my problems too! (on Ubuntu 9.04)

Cheers!

---

### Post by jellevictoor on 2009-08-27
Hi,

We connect with our E-Id to the vpn. I can start it from my browser and I'm connected, but i would rather use the standalone version.
So i should log in with the certificate of my e-id, i think. When i start the application from our site, everything is allready configure.

Second question, when i startup my vpn, I'm not able to connect via ssh. I can browse the web addresses, but I can't connect to the servers over ssh, this does work under windows.
I executed the route commando and found that the subnet of the vpn forwards to the tun0 istead of eth0.
Any ideas?

---

### Post by ooshlablu on 2009-09-08
Hey Guys,
I had to do this earlier today for work on ubuntu jaunty. It will work if you log in to your juniper vpn through firefox, otherwise there are no guarantees. I put all of the steps into this script, so if you give it a "sudo setup_vnp.sh", you should be all set.


To get services working beside your browser, you have to copy the last few "nameserver" fields in /etc/resolv.conf to the top. If you have 2 nameservers in your vpn, copy the last 2 lines. If you have 3, copy the last 3, etc. Then, ssh, Apache Directory Studio, etc. should work over the vpn.

---

### Post by frriction on 2009-09-24
Thank you mad scientist. 

I am running Ubuntu 9.04.

well your script on the this site [http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html) didnt work for me. In error it says jar not found. 

But I run the script given in this post [http://ubuntuforums.org/showpost.php?p=7918839&postcount=284](http://ubuntuforums.org/showpost.php?p=7918839&postcount=284), Then Enabling root account as per [https://help.ubuntu.com/community/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d](https://help.ubuntu.com/community/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d) this page.

and follow the step given in first post and I am connected. 

After first connection I disable the root account. When I connect next time it asked root password so I just pressed enter twice and Network connector launched and I am online. 

Note : Is there any solution for the problem jar not found ?

---

### Post by jcbnica on 2009-10-09
I am a new Ubuntu user and it has been a humbling experience learning Ubuntu.

This has been really frustrated for me also trying to get Juniper's Network Connect.

I am running Ubuntu 8.04 

After having installed sun-java6-bin, sun-java6-fonts, sun-java6-jre, and sun-java6-plugin I was still experiencing problems. 

I was still getting this message.

/home/username/.juniper_networks/network_connect/installNC.sh:9: cannot open 1:
Please enter the root/su password
Password:
su:Authentication failure
Invalid su password and/or Unable to install ncsvc

Solution: I had to setup the root password to match the sudo password.
then when i entered my "sudo" password it worked. 

I wish I knew there was a way. so that I don't have to re-enter the password. Maybe one of the more experienced Ubuntu users can share.

---

### Post by SoCalWizard on 2009-10-25
I too just set my root password to my sudo password and it no prompts me every time to enter the password at startup, but it at least works.  I can also just control c, and exit the terminal screen after disabling the root account and it still works (after dismising the terminal window).  Is there a way to automate this or disable the check for *installINC.sh*: Since it's not needed and it is there as other posts have pointed out.

Obviously I'm new to ubuntu, and like others it's been humbling learning a new OS after using windows since it's inception, but linux it starting to grow on me, rather slowly however.

---

### Post by frriction on 2009-11-04
I have working juniper client in Ubuntu 9.10 
Step I followed

1. First I installed java.
2. Then I try to connect with juniper client but I am unsuccessful as I need root password and I checked this step created .juniper_network folder in my home folder. ( I check with crtl+h)
3. Then I created root account with ```
sudo -i
```
```
sudo passwd root
``` more information look at 
[HTML]https://help.ubuntu.com/community/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d[/HTML]
4. ```
sudo ln -s /bin/true /usr/bin/rpm
```
5. ```
sudo ln -s libssl.so.0.9.8 /usr/lib/i686/cmov/libssl.so.0
```
   for more information on step 4 and 5 look at first post of this forum.
6. I tried to connect with juniper client, when it prompt password I provided the root password set in step 3.
7. I am connect with internet.
8. Then I disable the root password ```
sudo usermod -p '!' root
```
9. Then I remove the rpm link ```
sudo rm -f /usr/bin/rpm
```
10. I tried to connect with juniper client I connected without any password requirement.

Thank you mad scientist.:lolflag::popcorn:

---

### Post by dmflad on 2009-11-08
I really prefer Ubuntu over the other distros I run but crap! I hate updating/upgrading to new Ubuntu animal - every time I have done so I end up with Juniper not working. Yesterday I went from 9.04 to 9.10 and Juniper now broken - and of all the apps I run this is the only one work absolutely requires I be able to run.  

In the past the only sane fix that ever worked was a complete LT wipe and fresh install of the new animal - but of course that means setting up (again) all the config files for all the other software I run plus installing the stuff I own that comes not from Ubuntu or linked parties.

And to make things more painful today is one of best weekend days in awhile and I really NEED to go flyfishing. So fixing Juniper on the LT has to wait until tonite.

---

### Post by TomtheWombat on 2009-11-08
> **dmflad said:**
> I really prefer Ubuntu over the other distros I run but crap! I hate updating/upgrading to new Ubuntu animal - every time I have done so I end up with Juniper not working. Yesterday I went from 9.04 to 9.10 and Juniper now broken - and of all the apps I run this is the only one work absolutely requires I be able to run.  

In the past the only sane fix that ever worked was a complete LT wipe and fresh install of the new animal - but of course that means setting up (again) all the config files for all the other software I run plus installing the stuff I own that comes not from Ubuntu or linked parties.

And to make things more painful today is one of best weekend days in awhile and I really NEED to go flyfishing. So fixing Juniper on the LT has to wait until tonite.
Linux is at fault for many things, but this is not one of them.  It is simply ignorance on the part of the Juniper developers.  Logging in as root is outdated.

---

### Post by TomtheWombat on 2009-11-08
This may have been said before, but for amd64 use the junipernc script from madscientist but make the following changes when you install it:

Install ia32-sun-java6-bin (along with other java things mentioned on his site) and set it as the default java:

```
sudo aptitude install sun-java6-plugin sun-java6-jdk sun-java6-jre
ia32-sun-java6-bin
sudo update-java-alternatives -s java-6-sun
```

Then run the junipernc script as you usually would.  Juniper network connect will not run in 64bit java.  YOu won't be able to connect using your browser (it only supports 64bit plugins.)

---

### Post by chazn85 on 2009-11-10
i am getting the Error 10 cannot connect to NVE error with version 6.4.  i feel this is the last step in getting this working so any pointers would be appreciated!

---

### Post by Sigma47 on 2009-11-12
> Then run the junipernc script as you usually would. Juniper network connect will not run in 64bit java. YOu won't be able to connect using your browser (it only supports 64bit plugins.)

TomdaWombat can you clarify this statement? I recently started a job which requires JNC. I am running 9.10 64bit and plan to do the mad scientist install with the redirect to the 64bit java files; is that a correct approach? and for the question then... Running the script will connect me to the VPN right? so I don't actually have to go to the "web sign-in" page that usually starts JNC with firefox?

Thanks for the help...I am finally over the hump of Linux frustration and beginning to appreciate it! :D

---

### Post by mynk on 2009-11-18
I get the following error when I try

$ sudo update-java-alternatives -s java-6-sun
update-alternatives: error: no alternatives for java-rmi.cgi.

> Then run the junipernc script as you usually would. Juniper network connect will not run in 64bit java. YOu won't be able to connect using your browser (it only supports 64bit plugins.)

I realized that my colleagues are using 32 bit Karmic and it works for them. They get a final popup window which I don't see. I believe it is because I am using a 64 bit Karmic.

The juniperrc script constantly gives me -

Failed to load the ncui library.

The RSA string I found to be - 

<input type="hidden" name="realm" value="RSA Secure ID">

No luck so far!

---

### Post by madscientist on 2009-11-18
A simple solution is to run my juniperrc script with the "-nogui" option; that avoids the need for Java at all IIRC.  However, it's a bummer because you can't see the status of your connection.

However, it's not hard (at least it wasn't for me) to get it working on 64bit Karmic.

Unfortunately my detailed information on this is at home; I keep meaning to find the time to update the website.  But, you need to install a 32bit version of Java, which is easy: run "sudo aptitude install ia32-sun-java6-bin" from the command line, or use Synaptic or whatever to install it.

Next you need to modify the juniperrc script so it uses the 32bit version of java by setting JDK_HOME appropriately.

---

### Post by mynk on 2009-11-24
I tried the -nogui option -

$ junipernc -nogui
Connecting to xxx-xxx.xxx.xxx port 443
Generating Certificate .... done.
Connecting to xxx-xxx.xxx.xxx : 443
$ echo $JDK_HOME

$

What should I set the JDK_HOME value to? I have installed the 32 bit java as instructed.

I see the dialog VNC has exited and it keeps looping in the same.

---

### Post by madscientist on 2009-11-24
??

In Network Connect, the graphical connection monitor applet is written in Java.  If you invoke my script with the "-nogui" option, then this connection applet will not be invoked: hence, you do not need Java at all (and thus you don't need to set JDK_HOME).  The actual VPN software, that handles the network, is not written in Java and can run without the monitor applet (although it's gross because you can't tell what the status of the connection is, very easily).  The -nogui flag is a workaround to get the connection running, when you can't get Java working.

Setting JDK_HOME is necessary only if (a) the default Java is not correct (for example the default java on your system is 64bit and the Java app is a 32bit app), **AND** (b) you don't use the -nogui flag.

On my 64bit system I need to set:
```
JDK_HOME=/usr/lib/jvm/ia32-java-6-sun/jre
```

Note that you have to be sure this is set in the environment and exported *before* you run my script.

---

### Post by fatmcgav on 2009-11-26
Hi there, 

I'm trying to get NetConnect installed on Ubuntu 9.10 x64. 

I've managed to get the GUI run up by installing ia32 java6, then using mad-scientist's script, with a quick tweak to set the JDK_HOME to be JAVA6_32_HOME, which get's set at the start of the script... 

I can run the script, and it compeltes the install, and then opens the NetConnect GUI. I then enter my user Password at the RSA Code prompt, and it appears to be working. 

However it then fails with:
> ncapp> Failed to connect/authenticate with IVE. Error 104
ncapp> Incorrect credentials. Please check the username/password/realm.

Now the only thing different about our VPN to the others i've read about in this thread is that we've got an additional authentication step in the form of a Client Certificate verification... 

Is anybody familiar with this? Any tips on how to set it up?

Cheers
Gavin

---

### Post by madscientist on 2009-11-27
Hi all.

I've updated [my page]("http://mad-scientist.net/juniper.html") and also added a new version of the script.  This version handles 32bit/64bit versions better (if it can't find the right bit size java to run things with it will ask you for a location).  It also has some enhancements suggested by others, including support for KDE and the ability to connect to multiple servers.  It will also try to figure out the correct "realm" value by checking the connection page, rather than assuming "RSA".

Hopefully this will work (it works for me but...)

Note that I really can't help anyone with questions about failures that occur after the connection is made: I am simply someone who uses the service on the client side.  I don't have a lot of understanding of the intricacies of IPSEC/VPN, or how the Juniper server is configured (never even seen one), etc.  Hopefully others reading this list are more knowledgeable in that area...

---

### Post by LoneStarKen on 2009-12-01
I'm so bummed.  I had it all working fine with the junipernc script.  Then they replaced their certificate with a godaddy certificate and I can't get connected.  Getting:
```
ncapp> Failed to connect/authenticate with IVE. Error 5
```

From the ncui.log:
```
ncui[19701] dsclient.info state: kStateSignin (dsclient.cpp:233)
ncui[19701] dsclient.info --> GET / (authenticate.cpp:136)
ncui[19701] dsclient.info <-- 302 https://xxx.xxx.com/auth/url_default/welcome.cgi (authenticate.cpp:168)
ncui[19701] dsclient.info state: kStateWelcome (dsclient.cpp:241)
ncui[19701] dsclient.info --> GET /auth/url_default/welcome.cgi (authenticate.cpp:136)
ncui[19701] dsclient.info <-- 200  (authenticate.cpp:168)
ncui[19701] dsclient.info state: kStateLogin (dsclient.cpp:273)
ncui[19701] dsclient.info --> POST /auth/url_default/login.cgi (authenticate.cpp:136)
ncui[19701] dsclient.info <-- 302 https://xxx.xxx.com/auth/url_default/welcome.cgi?p=passwordExpiration&seconds=Server:250717 (authenticate.cpp:168)
ncui[19701] dsclient.info state: kStateError (dsclient.cpp:358)
ncui[19701] ncapp.error Failed to connect/authenticate with IVE. Error 5 (ncapp.cpp:174)
ncui[19701] ncui.info Sending kill signal (SIGQUIT) to ncsvc...  (ncapp.cpp:445)
```

I think it's related to the security certificate.  Anyone got any ideas?

---

### Post by LoneStarKen on 2009-12-02
Ok ... wasted hours on that.  Their interface had an intermediate page saying the password would expire in X that was throwing everything off.  Once I reset the password, that got rid of the nag screen and now everything is working again.

---

### Post by fatmcgav on 2009-12-04
Ok, i've managed to get one step further through my issues now... 

I changed the Realm configured in junipernc to be correct for our setup. 
Now, instead of an *Error 104* as below, i'm now getting the following:
> 
gavinw@Prometheus:~$ junipernc
Searching for ncsvc in current working directory
Searching for ncsvc in /home/gavinw/.juniper_networks/network_connect done.
ncapp> Failed to connect/authenticate with IVE. Error 5


NCUI.log shows:
> 20091202220455.202082 ncui[14829] dsclient.info <-- 302 [https://vpn.card.co.uk/dana-na/auth/url_0/welcome.cgi?p=no-cert](https://vpn.card.co.uk/dana-na/auth/url_0/welcome.cgi?p=no-cert) (authenticate.cpp:168)
20091202220455.202402 ncui[14829] dsclient.info state: kStateError (dsclient.cpp:363)
20091202220455.202932 ncui[14829] ncapp.error Failed to connect/authenticate with IVE. Error 5 (ncapp.cpp:174) 
The issue now appears to be that it's not picking up the necessary client certificate, and getting rejected by the IVE... 

Will have to raise a call with JTAC when I can... 

Cheers
Gavin 

> **fatmcgav said:**
> Hi there, 

I'm trying to get NetConnect installed on Ubuntu 9.10 x64. 

I've managed to get the GUI run up by installing ia32 java6, then using mad-scientist's script, with a quick tweak to set the JDK_HOME to be JAVA6_32_HOME, which get's set at the start of the script... 

I can run the script, and it compeltes the install, and then opens the NetConnect GUI. I then enter my user Password at the RSA Code prompt, and it appears to be working. 

However it then fails with:

Now the only thing different about our VPN to the others i've read about in this thread is that we've got an additional authentication step in the form of a Client Certificate verification... 

Is anybody familiar with this? Any tips on how to set it up?

Cheers
Gavin

---

### Post by lordmundi on 2009-12-08
well, i'm not sure if I follow everything in this thread, but I've just updated to 64 bit ubuntu for the first time and according to this thread (as best I can tell), the only way to connect to the vpn in 64 bit is to use madscientist's script? because the browser won't launch a 64 bit plugin?

regardless, I think I'm close to getting the junipernc script working, but like lakerol said, our server requires two (2) passwords... one regular password and one PIN+RSA_token... since the junipernc script only prompts me once, I'm assuming this is why it is failing with the error:

ncapp> Failed to connect/authenticate with IVE. Error 10

any idea on how to log into a 2 password server on 64 bit? I don't mind using the web browser instead of junipernc if I can get it to work.

---

### Post by krzychosz on 2009-12-13
Hi All

I'm attaching to this thread as I have some issue at the very end when running 'junippernc' script from madscientist.

First big thanks to **madscientist** for this really great job.

I went through this thread and also googled for information but couldn't find anything useful.

With **'junippernc'** script I am able go to the point where the Network Connect GUI starts and attempts to connect to the VPN. After a few seconds I get such error:

[SIZE=2]**[FONT=Courier New]ncapp> Failed to connect/authenticate with IVE. Error 10[/FONT]**[/SIZE]

I see some error when I look in the: [B][FONT=Courier New].juniper_networks/network_connect$ cat ncsvc.log
[/FONT][/B]
[FONT=Courier New]20091213155006.501908 ncsvc[6811] dsclient.info <-- 200  (authenticate.cpp:168)
20091213155006.502012 ncsvc[6811] dsclient.info state: kStatePostCacheCleaner (dsclient.cpp:334)
20091213155006.502053 ncsvc[6811] dsclient.info --> POST /dana-na/cc/ccupdate.cgi (authenticate.cpp:136)
20091213155007.353933 ncsvc[6811] dsclient.info <-- 200  (authenticate.cpp:168)
**20091213155007.354012 ncsvc[6811] dsclient.error state post auth cache cleaner failed, error 10 (dsclient.cpp:336)**[/FONT]


_**Additional Info:**_
1) My VPN site requires user/realm/password.

2) I am using Kubuntu 9.10 (Karmic)

3) **ncsvc** version is:

[FONT=Courier New]krzysiek@delta:~/.juniper_networks/network_connect$ ./ncsvc -v
Juniper Network Connect Server for Linux.
Version         : 6.3
Release Version : 6.3-0-Build14121
Build Date/time : Mar 26 2009 19:06:48
Copyright 2001-2008 Juniper Networks[/FONT]

If anyone had similar issue please share your solutions on that. Thanks in advance.

krzychosz

---

### Post by mynk on 2009-12-16
I am getting similar errors -

[~]$ junipernc -nogui
Connecting to bng-access.juniper.net : 443
[~]$ junipernc
Searching for ncsvc in current working directory
Searching for ncsvc in /home/mayankr/.juniper_networks/network_connect done.
ncapp> Failed to connect/authenticate with IVE. Error 104
ncapp> Incorrect credentials. Please check the username/password/realm.

For -nogui it simply restarts with the dialog box VPN quit successfully. Without it the Network Connect window opens and I get the unable to connect to IVE dialog box.

The logs are as below -

[~/.juniper_networks/network_connect]$ cat ncui.log 
20091216195523.339723 ncui[6548] ncapp.info New ncapp log level set to 3 (nccommon.cpp:75)
20091216195523.339784 ncui[6548] ncapp.info Version         : 6.3 
Release Version : 6.3-0-Build13881
Build Date/Time : Jan 22 2009
Copyright 2001-2008 Juniper Networks
 (ncapp.cpp:152)
20091216195523.348358 ncui[6548] dsclient.info state: kStateSignin (dsclient.cpp:238)
20091216195523.348406 ncui[6548] dsclient.info --> GET / (authenticate.cpp:136)
20091216195523.349309 ncui[6548] dsclient.info <-- 302 [https://xxx-xxxxxx.xxxx/auth/url_default/welcome.cgi](https://xxx-xxxxxx.xxxx/auth/url_default/welcome.cgi) (authenticate.cpp:168)
20091216195523.349348 ncui[6548] dsclient.info state: kStateWelcome (dsclient.cpp:246)
20091216195523.349368 ncui[6548] dsclient.info --> GET /xxx/auth/url_default/welcome.cgi (authenticate.cpp:136)
20091216195523.362383 ncui[6548] dsclient.info <-- 200  (authenticate.cpp:168)
20091216195523.362560 ncui[6548] dsclient.info state: kStateLogin (dsclient.cpp:278)
20091216195523.362587 ncui[6548] dsclient.info --> POST /xxx/auth/url_default/login.cgi (authenticate.cpp:136)
20091216195528.893456 ncui[6548] dsclient.info <-- 302 [https://xxxxxxxxxxxxxx.xxx/xxx/auth/url_default/welcome.cgi?p=preauth&id=state_24&signinRealmId=4](https://xxxxxxxxxxxxxx.xxx/xxx/auth/url_default/welcome.cgi?p=preauth&id=state_24&signinRealmId=4) (authenticate.cpp:168)
20091216195528.893614 ncui[6548] dsclient.info state: kStatePostAuth (dsclient.cpp:318)
20091216195528.893685 ncui[6548] dsclient.info --> GET /xxx/auth/url_default/welcome.cgi?p=preauth&id=state_218aa74&signinRealmId=4 (authenticate.cpp:136)
20091216195528.910979 ncui[6548] dsclient.info <-- 200  (authenticate.cpp:168)
20091216195528.911061 ncui[6548] dsclient.info state: kStatePostCacheCleaner (dsclient.cpp:334)
20091216195528.911108 ncui[6548] dsclient.info --> POST /xxx/cc/ccupdate.cgi (authenticate.cpp:136)
20091216195528.920852 ncui[6548] dsclient.info <-- 200  (authenticate.cpp:168)
20091216195528.920921 ncui[6548] dsclient.error state post auth cache cleaner failed, error 10 (dsclient.cpp:336)
20091216195528.921088 ncui[6548] ncapp.error Failed to connect/authenticate with IVE. Error 10 (ncapp.cpp:174)

I am not sure what Realm ID it is taking. The source showed - "RSA Secure ID". How can this be checked/reset?

It appears from the script this is fetched automatically so don't know what I am missing.

---

### Post by madscientist on 2009-12-16
Unfortunately I'm no expert in Juniper software so there's little I can say once the application starts up... if it doesn't connect after that then you'll need someone who knows a lot more about Juniper's VPN solution and the various ways that the server side can be configured.

I will say that my login also requires 3 items: my username, the realm, and a passcode... which in my case is a PIN plus a 6-digit number provided by a RSA SecurID fob/card.  But, I suppose this could also just be a plain password, if you don't want to go to the time/expense of integrating with RSA (I have no idea if this is an option).

In previous posts, people have said they need "two" passwords, but then they list username/realm/password... what's the "other" password?

Is anyone in this situation able to connect at all, even with the web interface?  If you can then one thing you can try is replacing the ncsvc application with a simple shell script that just prints its arguments to a temporary file... that's a simple way to find out how the command is being invoked, and how the passwords/etc. you are entering into the web interface are being passed to the command.  If you can connect via the web and want more help with this, let me know.

---

### Post by mynk on 2009-12-16
Thanks a lot for the effort madscientist.

We have a similar login like yours with 6 digit RSA SecureID. It works like a charm on 32 bit karmic/mint through web interface. I need to check if junipernc works on that. It might give some clues.

Will check at work about it also.

---

### Post by mynk on 2009-12-16
Thanks a lot for the effort madscientist.

We have a similar login like yours with 6 digit RSA SecureID. It works like a charm on 32 bit karmic/mint through web interface. I need to check if junipernc works on that. It might give some clues.

Will check at work about it also.

---

### Post by krzychosz on 2009-12-16
Hi again

I was desperate to get it running so I decided to reinstall my kubuntu to a 32bit. Previously I had x86_64. Of course first I checked it in Virtualbox.

The observations are as follows:

1. I can connect to the VPN using regular web based interface. It starts Network Connect and everything works perfect.



2. Next I tried the 'junippernc' script. I was supprised but it doesn't work the same way as in my previous x86_64 (post #304).

3. I have done a parameters sniffer scrpt as suggested by *madscientist*. The script is as follows:

~/.juniper_networks/network_connect/ncsvc

```
#!/bin/bash
echo  "junipper parameters:" > /tmp/junipper-options.txt
while (($#)); do
        echo $1 >> /tmp/junipper-options.txt
        shift
done

```

Unfortunately the expected file /tmp/junipper-options.txt is not created. Perhaps the Network Connect checks whether the ncsvc is a correct binary to call (some CRC check?) - just guessing.

Let me know if you have any suggestions about the 3-rd

krzychosz

---

### Post by NightStorm on 2009-12-19
> **madscientist said:**
> Hi all.

I've updated [my page]("http://mad-scientist.net/juniper.html") and also added a new version of the script.

There is a small error in this script at line 303:

  jbit=`file -L -b "$java" | sed -n 's/.*ELF \([0-9]*\).*/\1/'p`

needs to be:
  jbit=`file -L -b "$JAVA" | sed -n 's/.*ELF \([0-9]*\).*/\1/'p`

(Make the "$java" uppercase).

        - Bruce

---

### Post by madscientist on 2009-12-19
Thanks Bruce; I fixed that and a couple of other small issues.

---

### Post by FoldEm on 2009-12-21
Has anyone been able to get this working on 9.10. When I start network-connect on the webpage it works (so I know it works). But with the junipernc script or CLI it doesn't work. I have to get this working with a script (so no logging into the website).

I always get the "cannot connect to IVE (error 10)"


ncapp> Failed to connect/authenticate with IVE. Error 10



Any help is welcome.

---

### Post by cocoa117 on 2009-12-23
hi, I got the "Invalid Credentials" error message when I am trying to connect. The Java GUI showed the connection is to the right server, but the program never asked me about the username. It simply ask me the password for the VPN access.

the ncui.log is showing here:
Release Version : 6.5-0-Build14599
Build Date/Time : Aug 12 2009
Copyright 2001-2008 Juniper Networks
 (ncapp.cpp:153)
20091223152442.63497 ncui[p19344.t19366] dsclient.info state: kStateSignin (dsclient.cpp:248)
20091223152442.63572 ncui[p19344.t19366] dsclient.info --> GET / (authenticate.cpp:162)
20091223152442.89981 ncui[p19344.t19366] dsclient.info <-- 302 [https://webvpn.reading.ac.uk/dana-na/auth/url_default/welcome.cgi](https://webvpn.reading.ac.uk/dana-na/auth/url_default/welcome.cgi) (authenticate.cpp:194)
20091223152442.90055 ncui[p19344.t19366] dsclient.info state: kStateWelcome (dsclient.cpp:256)
20091223152442.90078 ncui[p19344.t19366] dsclient.info --> GET /dana-na/auth/url_default/welcome.cgi (authenticate.cpp:162)
20091223152442.253143 ncui[p19344.t19366] dsclient.info <-- 200  (authenticate.cpp:194)
20091223152442.253330 ncui[p19344.t19366] dsclient.info state: kStateLogin (dsclient.cpp:288)
20091223152442.253357 ncui[p19344.t19366] dsclient.info --> POST /dana-na/auth/url_default/login.cgi (authenticate.cpp:162)
20091223152442.393092 ncui[p19344.t19366] dsclient.info <-- 302 [https://webvpn.reading.ac.uk/dana-na/auth/url_default/welcome.cgi?p=failed](https://webvpn.reading.ac.uk/dana-na/auth/url_default/welcome.cgi?p=failed) (authenticate.cpp:194)
20091223152442.393154 ncui[p19344.t19366] dsclient.error state login failed, error 104 (dsclient.cpp:290)
20091223152442.393323 ncui[p19344.t19366] ncapp.error Failed to connect/authenticate with IVE. Error 104 (ncapp.cpp:179)


I am using 64-bit 9.10, and my question is 
1) how do i get the junipernc script to ask me all the question about the username, server and etc... 
2) where is those volumes stored?

thanks

---

### Post by cpepera on 2009-12-23
cocoa117, the login information is stored in a configuration file named .vpn.default.cfg in your home directory.

---

### Post by Liux on 2009-12-23
Hi all; I recently started a new job with juniper and I need help!!
I use this guide <http://mad-scientist.us/juniper.html>to connect with VPN , I am working on Ubuntu 9.04, 32.

when I run the Junipernc everything works fine, I added

*Network connect server
*vpn account user name
*password 
*VPN service realm

and the VPN connect! but around 5 o 6 seconds falls, the diagnostic show 'ping failed' and always I can see that the NC service is 'not running' , I don't know if I need kill some process's linux.  

thx for all.
regards.

---

### Post by cocoa117 on 2009-12-23
> **cpepera said:**
> cocoa117, the login information is stored in a configuration file named .vpn.default.cfg in your home directory.

thanks, I found it, and after I deleted it worked.

---

### Post by koba101 on 2009-12-31
i'm working on karmic 64 bit....works fine

thanks

---

### Post by dizzythinks on 2010-01-05
> **madscientist said:**
> In previous posts, people have said they need "two" passwords, but then they list username/realm/password... what's the "other" password?

Is anyone in this situation able to connect at all, even with the web interface?  If you can then one thing you can try is replacing the ncsvc application with a simple shell script that just prints its arguments to a temporary file... that's a simple way to find out how the command is being invoked, and how the passwords/etc. you are entering into the web interface are being passed to the command.  If you can connect via the web and want more help with this, let me know.

Hi, I've just updated the kernel on Karmic along with other packages and Juniper has failed, all I get from the GUI is "Config Failed". It happened once before but I got a new laptop and it went away until updates. Have tried most of the things in here, however I am one of those extra password people so here's the answer to your question.

I use:

Username, Password (Active Directory auth), Pin+SecureID to log into the Web interface then Network Connect launches. Have just tried to replace the ncsvc binary with a script that echo $@ to a file but it doesn't seem to work as the install and xlaunch still run. Help appreciated.

---

### Post by draki on 2010-01-10
Hi - I'm also getting this "Failed to connect/authenticate with IVE. Error 10". Very frustrating

I'm on Karmic 9.10 64bit

any help much appreciated

---

### Post by DevinD on 2010-01-19
I've also been having problems with Juniper Network Connect on Ubuntu 9.10.

It installs fine, and runs fine, and seems to connect fine (it says 'connected'). However, the vpn seems to not be working - i'm connecting to my university vpn and it can not resolve the hostname of the server i'm trying to ssh into. I thought this could be a dns problem, so checked /etc/resolv.conf and made sure all the correct nameservers were at the top (as the it department told me to do), but still nothing. Oddly the internet works perfectly (i presume this is my work connection) EXCEPT for sites on my university domain (which i guess it tries to go through the vpn for).

I've managed to find out the ip address of the server and tried to ssh directly to that, but it doesn't manage to connect and times out. On the network connect applet it constantly says 'bytes sent 0' and 'bytes received 0' so i guess there's nothing going to or from the vpn when i try to ssh.

I have tried everything in the forums and nothing works :( I've also tried using madscientist's code but it tells me "This program requires the program 'jar'", however this is nowhere to be seen in my package manager. I guess this is a java thing, but i have all the latest java runtime things installed.

Any help would be much appreciated!

---

### Post by WockaNation on 2010-01-19
very new to Linux, trying to get my works Juniper VPN working.  found this [http://mad-scientist.net/junipernc](http://mad-scientist.net/junipernc) (very helpful, btw)  but I am still having issues.  I saw a comment from a few months back that you updated the script to not check hostname - my work doesn't have a hostname, just an IP that I browse to - but whenever I try to run the script it says "Cannot resolve hostname xx.xxx.xxx.xxx. Please try again."  anyone have any idea?

---

### Post by DevinD on 2010-01-20
Ah ha, i worked out that the 'jar' program not installed was becaused i forgot to install the sun-java6-jdk package. I've now managed to get it working in that it opens network connect and connects me to the vpn, however i seem to be nothing more than 'connected' on the network connect applet - i still can not do anything over the vpn.

I've tried ssh-ing to the server i need to get into, and i've tried looking it up using 'host', but it can't find the hostname. I've fiddled with resolv.conf again to see if it'll fix it, it didn't. I've tried again to ssh using the ip address directly, but still no joy..and still it says 0 bytes sent and received.

---

### Post by DevinD on 2010-01-20
Oh, in the end i seem to have answered my own questions. I noticed that I couldn't ping anyone in the vpn either, so i had a scout to see if there were any forum topics about ping not working, and there were. Basically my iptables was a bit strict. If anyone has the same problem, see [http://www.issociate.de/board/post/16853/Kernel_seems_to_be_blocking_messages.html](http://www.issociate.de/board/post/16853/Kernel_seems_to_be_blocking_messages.html)
Sorry for my seemingly pointless input into this topic...i guess 3 days of trying to get something to work sometimes pays off :)

---

### Post by madscientist on 2010-01-21
> **WockaNation said:**
> very new to Linux, trying to get my works Juniper VPN working.  found this [http://mad-scientist.net/junipernc](http://mad-scientist.net/junipernc) (very helpful, btw)  but I am still having issues.  I saw a comment from a few months back that you updated the script to not check hostname - my work doesn't have a hostname, just an IP that I browse to - but whenever I try to run the script it says "Cannot resolve hostname xx.xxx.xxx.xxx. Please try again."  anyone have any idea?

The script looks at the hostname and if it contains any characters other than numbers or periods, it assumes it's a hostname.  I've tested this and it works for me.  If you double-check this and it still doesn't work let me know and I'll tell you how to get more debugging information out.

---

### Post by WockaNation on 2010-01-21
> **madscientist said:**
> The script looks at the hostname and if it contains any characters other than numbers or periods, it assumes it's a hostname.  I've tested this and it works for me.  If you double-check this and it still doesn't work let me know and I'll tell you how to get more debugging information out.
Thanks, I'll try to do this again when I get home from work today, and I'll post the results.

---

### Post by WockaNation on 2010-01-22
I have attached a screenshot of the message I get when I enter the IP address of my VPN connection.  Still not working unfortunately.

---

### Post by PerJ on 2010-02-02
> **madscientist said:**
> In previous posts, people have said they need "two" passwords, but then they list username/realm/password... what's the "other" password?

Is anyone in this situation able to connect at all, even with the web interface?  If you can then one thing you can try is replacing the ncsvc application with a simple shell script that just prints its arguments to a temporary file... that's a simple way to find out how the command is being invoked, and how the passwords/etc. you are entering into the web interface are being passed to the command.  If you can connect via the web and want more help with this, let me know.

As a couple of others have reported, I am also able to use the web interface to connect, but not by invoking Network Connect from your script (getting the "Incorrect credentials" error).
I use username, password (AD password) and securetoken + PIN to connect on the web. I'm sure the realm from the webpage gets passed along as an argument as well.

Replacing the ncsvc application with a script for logging the arguments being passed to it, does not work, as a new application seems to be installed when invoking Network Connect.
If there are any alternative methods of getting the parameters passed to the ncsvc, I would happily try them out...

---

### Post by PerJ on 2010-02-03
Okay, so searching for more information on this subject, led me to this site: [juniper-vpn-64-bit-linux-an-unsolved-mystery]("http://makefile.com/.plan/2009/10/27/juniper-vpn-64-bit-linux-an-unsolved-mystery").

It seems that the information one uses to log in to the webservice, gets validated and subsequently stored as a DSID cookie. And it is this cookie that is passed along when invoking Network Connect.

Unfortunately it is not straight forward to pass on the information from this cookie when starting Network Connect manually. The short story is that libncui.so needs to be converted to an executable, where you can pass this argument with the -c flag.
The bonus is that this can also enable NC to be utilized directly from a 64-bit environment.

Alas, I am not succesful in my attempts to run the executable.
It fails with the following errormessage: ```
./ncui: error while loading shared libraries: libncui.so: cannot open shared object file: No such file or directory
```

If anyone more adept in the fine art of C hacking, than I am myself, were to take a stab at making this work. I would appreciate if they would post their findings in this thread.

---

### Post by josephellengar on 2010-02-03
I just did everything exactly as instructed: [http://mad-scientist.net/juniper.htmlpam_authenticate:](http://mad-scientist.net/juniper.htmlpam_authenticate:) Conversation error

I received the following error and it failed:
```

Run as: /usr/bin/junipernc.sh 
sudo: pam_authenticate: Conversation error

```
Any ideas?  Thanks for the great script.  I really needed to get this set up.  I'm on 64bit karmic.

---

### Post by josephellengar on 2010-02-03
> **rossholley said:**
> I just did everything exactly as instructed: [http://mad-scientist.net/juniper.htmlpam_authenticate:](http://mad-scientist.net/juniper.htmlpam_authenticate:) Conversation error

I received the following error and it failed:
```

Run as: /usr/bin/junipernc.sh 
sudo: pam_authenticate: Conversation error

```
Any ideas?  Thanks for the great script.  I really needed to get this set up.  I'm on 64bit karmic.

Ok, I figured this out, but now I'm getting another error: unable to connect to IVE.  I've followed all of the directions to the letter.

---

### Post by PerJ on 2010-02-04
Got it working! :cool:

I followed the steps from my previous link, but did not chown the produced ncui executable to root, and adittionally I had to ```
export LD_LIBRARY_PATH=$HOME/.juniper_networks/network_connect
```

I supplied the host, cookie and ssl-cert as arguments to ncui, and was additionally asked my password (AD pass).
The vpn-client then succesfully connected, two-phase authentication and all.

Now to try and automate the whole process somewhat.
Thanks to everyone who has done the dirtywork on this one!

---

### Post by josephellengar on 2010-02-04
> **rossholley said:**
> Ok, I figured this out, but now I'm getting another error: unable to connect to IVE.  I've followed all of the directions to the letter.

So, anybody have any idea what could be causing this?  Everything else seems to work.  When I browse the internet works but I can't get behind the firewall of my university, which is what I need to be able to do.

---

### Post by tles on 2010-02-16
Hi,

I've encountered a problem with mad scientist's juniperc

On my juniper server, I need to specify the Sign In Url as a parameter of ncsvd 

So I've adapted the script :)

HOST is used to get $HOST and $SIGNURL

Please consider to add this feature to the main script



Christophe Colombier

---

### Post by bbdimitriu on 2010-02-27
Has anyone managed to configure madscientist's script with a client certificate as well in the end?

---

### Post by ThomasNovin on 2010-03-10
Has anyone got an idea on how to bypass the local route monitoring? After I connect I can no longer can my printer on my lan for example.

If I try to remove the route that creates this problem I get a popup from ncgui "Route monitoring alarm" and then my VPN drops and it also clears my entire routing table!

This is what I get every time I disconnect too, my routing table is completely emptied.

Edit: The disconnect-problem (signout) cleared after removing all related cookies from Firefox + removing (thus reinstalling) ~/.juniper_networks.

---

### Post by ThomasNovin on 2010-03-12
> **ThomasNovin said:**
> Has anyone got an idea on how to bypass the local route monitoring? After I connect I can no longer can my printer on my lan for example.

If I try to remove the route that creates this problem I get a popup from ncgui "Route monitoring alarm" and then my VPN drops and it also clears my entire routing table!

This is what I get every time I disconnect too, my routing table is completely emptied.

Edit: The disconnect-problem (signout) cleared after removing all related cookies from Firefox + removing (thus reinstalling) ~/.juniper_networks.


I came up with a workaround. If you don't add but instead "replace" a route, it will work.

Let's say you are on network 10.0.0.0/24 and have a default route pointing to 10.0.0.254. Your routing table will look like this:

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     1     0        0 wlan0
0.0.0.0         10.0.0.254      0.0.0.0         UG    1     0        0 wlan0

After you are connected to your SSL-VPN network juniper nc will have changed your routes to have a metric of 10 and instead inserted better routes matching the tunnel with metric 1.

If you just add a route to '10.0.0.0/24 dev wlan0 metric 0' this will be the best route and you will be able to reach the clients on your LAN again. However, this will trigger the route monitor alarm.

So, instead of just adding one you can "replace" the one that NC has changed to metric 10.

sudo route del -net 10.0.0.0/24 dev wlan0 ; sudo route add -net 10.0.0.0/24 dev wlan0 metric 0

This way you bypass the route monitor alarm as it won't detect just a change in metric!

You could do this for the default route as well if you don't want all your traffic to go into the tunnel (split tunneling).

---

### Post by ThomasNovin on 2010-03-12
> **ThomasNovin said:**
> I came up with a workaround. If you don't add but instead "replace" a route, it will work.

Let's say you are on network 10.0.0.0/24 and have a default route pointing to 10.0.0.254. Your routing table will look like this:

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     1     0        0 wlan0
0.0.0.0         10.0.0.254      0.0.0.0         UG    1     0        0 wlan0

After you are connected to your SSL-VPN network juniper nc will have changed your routes to have a metric of 10 and instead inserted better routes matching the tunnel with metric 1.

If you just add a route to '10.0.0.0/24 dev wlan0 metric 0' this will be the best route and you will be able to reach the clients on your LAN again. However, this will trigger the route monitor alarm.

So, instead of just adding one you can "replace" the one that NC has changed to metric 10.

sudo route del -net 10.0.0.0/24 dev wlan0 ; sudo route add -net 10.0.0.0/24 dev wlan0 metric 0

This way you bypass the route monitor alarm as it won't detect just a change in metric!

You could do this for the default route as well if you don't want all your traffic to go into the tunnel (split tunneling).

To further explain how to achieve split tunneling without any side effects:

1. Add a route to the network you want to connect to. For example, you need to reach 172.30.0.0/24 through your SSL-VPN.

```
sudo route add -net 172.30.0.0/24 dev wlan0

```
(just add it pointing to any active interface, it won't be used)

2. Connect with Juniper NC

3. Note how NC has added a better-metric route to 172.30.0.0/24 pointing to the tunnel.

4. Replace your default route (change 10.0.0.254 to whatever your default gw is)

```
sudo route del default gw 10.0.0.254 ; sudo route add default gw 10.0.0.254 metric 0
```

5. Done!

You now have VPN access to 172.30.0.0/24 and the rest of the traffic will go out through your Internet connection as usual!

If you need local access to hosts on your network, you will need to do a replace on that route too.

---

### Post by hadynd88 on 2010-03-14
> **WockaNation said:**
> I have attached a screenshot of the message I get when I enter the IP address of my VPN connection.  Still not working unfortunately.

Did you ever get this sorted? I am having the same issue.

---

### Post by currentoccupant on 2010-03-17
Simple question. I keyed in a parameter incorrectly and need to change it. Where do the server/user/etc... reside so I can change/clear them?

---

### Post by DocDavid on 2010-03-21
I'm using Ubuntu 9.10 64-bit Server and have used mad scientiest's junipernc script to try to connect to my work's VPN.  I get the following error, any ideas?

Failed to connect/authenticate with IVE. Error 10

Thanks

---

### Post by khaki54 on 2010-03-26
I've been fighting will this error for well over a year now, and I stll haven't found a resolution.  It ends with "Failed to connect/authenticate with IVE. Error 10" It's preceded by "dsclient.error state select role failed, error 10 (dsclient.cpp:322)"

20100326130405.708365 ncui[p13674.t13695] ncapp.info New ncapp log level set to 3 (nccommon.cpp:75)
20100326130405.708462 ncui[p13674.t13695] ncapp.info Version         : 6.5 
Release Version : 6.5-0-Build14951
Build Date/Time : Dec  9 2009
Copyright 2001-2008 Juniper Networks
 (ncapp.cpp:153)
20100326130405.929961 ncui[p13674.t13695] dsclient.info state: kStateSignin (dsclient.cpp:248)
20100326130405.930001 ncui[p13674.t13695] dsclient.info --> GET / (authenticate.cpp:162)
20100326130405.976170 ncui[p13674.t13695] dsclient.info <-- 302 [https://connect.boeing.com/dana-na/auth/url_default/welcome.cgi](https://connect.boeing.com/dana-na/auth/url_default/welcome.cgi) (authenticate.cpp:194)
20100326130405.976213 ncui[p13674.t13695] dsclient.info state: kStateWelcome (dsclient.cpp:256)
20100326130405.976234 ncui[p13674.t13695] dsclient.info --> GET /dana-na/auth/url_default/welcome.cgi (authenticate.cpp:162)
20100326130406.215728 ncui[p13674.t13695] dsclient.info <-- 200  (authenticate.cpp:194)
20100326130406.215919 ncui[p13674.t13695] dsclient.info state: kStateLogin (dsclient.cpp:288)
20100326130406.215949 ncui[p13674.t13695] dsclient.info --> POST /dana-na/auth/url_default/login.cgi (authenticate.cpp:162)
20100326130406.511419 ncui[p13674.t13695] dsclient.info <-- 302 [https://connect.boeing.com/dana-na/auth/url_default/welcome.cgi?p=select-role&id=state_4a26c645612a1439bb09c0326a42af58](https://connect.boeing.com/dana-na/auth/url_default/welcome.cgi?p=select-role&id=state_4a26c645612a1439bb09c0326a42af58) (authenticate.cpp:194)
20100326130406.511484 ncui[p13674.t13695] dsclient.info state: kStateSelectRole (dsclient.cpp:312)
20100326130406.511515 ncui[p13674.t13695] dsclient.info --> GET /dana-na/auth/url_default/welcome.cgi?p=select-role&id=state_4a26c645612a1439bb09c0326a42af58 (authenticate.cpp:162)
20100326130406.676220 ncui[p13674.t13695] dsclient.info <-- 200  (authenticate.cpp:194)
20100326130406.676282 ncui[p13674.t13695] dsclient.info state: kStateSelectRole (dsclient.cpp:320)
20100326130406.676369 ncui[p13674.t13695] dsclient.error state select role failed, error 10 (dsclient.cpp:322)
20100326130406.676669 ncui[p13674.t13695] ncapp.error Failed to connect/authenticate with IVE. Error 10 (ncapp.cpp:179)

---

### Post by iponeverything on 2010-03-26
hope this helps..

[http://kb.juniper.net/index?page=content&id=KB15890&cat=SA_5000&actp=LIST](http://kb.juniper.net/index?page=content&id=KB15890&cat=SA_5000&actp=LIST)

---

### Post by currentoccupant on 2010-03-30
If you fat finger a parameter while setting up the script, you can change them in the .vpn.default.cfg

---

### Post by Retski on 2010-04-15
After looking through about 100 different threads, reading several new and old blogs about getting Juniper working and trying ubuntu 9.10 and openSuse 11.2 I give up......

It seems that I fail after the host checker launches, installs and then kicks me back to the VPN sign in screen with the message - You are not allowed to sign in. Please contact your administrator.

The network connect software never actually installs. Here is the last several lines of my dsHostChecker_linux1.log file:

         HCUtil:000 (04/15 16:04:36.038)[            main] TNCoHTTP: periodic check interval 10 min.
          HCUtil:000 (04/15 16:04:36.039)[            main] TNCoHTTP: last session status `'
          HCUtil:000 (04/15 16:04:36.040)[            main] HostCheckerIMC: connection state changed to 3
          HCUtil:000 (04/15 16:04:36.041)[            main] TncHandshake: recevied integrity result: 3
          HCUtil:000 (04/15 16:04:36.043)[            main] HttpNAR: wait for connection to port 50745

Any suggestions?

---

### Post by Izzin on 2010-06-15
I saw a post above about using this script and client auth certs. Has anyone gotten this to work?

I can auth fine using firefox and the auth cert, but I cant with the junipernc script. 

Of course firefox wont work for me because of 64bit Ubuntu.

--izz

---

### Post by mynk on 2010-06-16
I tried with 64 bit for a long time and couldn't get it to work (a lot of colleagues confirmed it doesn't work for 64 bit) so I migrated to 32 bit and it works fine now via Firefox & Chromium-browser. I still need to get it work with mad scientist's script.

Thx,
Mynk

---

### Post by amirmku on 2010-06-20
Hi mad scientist,
I tried installing juniper network on my ubuntu 10.04 using commands given below:-

> amir@amir-laptop:~$ wget -q -O /tmp/junipernc http://mad-scientist.net/juniperncamir@amir-laptop:~$ chmod 755 /tmp/junipernc
amir@amir-laptop:~$ sudo cp /tmp/junipernc /usr/bin
[sudo] password for amir: 
Sorry, try again.
[sudo] password for amir: 
Sorry, try again.
[sudo] password for amir: 
Sorry, try again.
sudo: 3 incorrect password attempts
amir@amir-laptop:~$ junipernc
amir@amir-laptop:~$


but i didnt get any errors as was expected acc to tutrial [http://mad-scientist.net/juniper.html ]("http://mad-scientist.net/juniper.html")
but instead i didnt get any error.
And when tried running junipernc command in terminal it says "juniper not installed".

Please help me to sort it out, I am newbie to ubuntu, therefore know not much, to run script other way.

---

### Post by DevinD on 2010-06-20
amirmku - I can see two issues here. The first is that when you typed 
> wget -q -O /tmp/junipernc http://mad-scientist.net/juniperncamir@amir-laptop:~$ chmod 755 /tmp/junipernc
that was to download the junipernc script from madscientist's website and change the permissions of the file so that you can execute it. The script is NOT the same as Juniper Network Connect - it is a shell script that enables you to use Juniper Network Connect in Linux.

The other issue is that when you typed "sudo cp /tmp/junipernc /usr/bin", here you SHOULD HAVE entered your sudo password - all this does is copy the script you've just downloaded from the tmp file to /usr/bin so you don't have to be in the same folder as the script to execute it.

Try reading through the tutorial on madscientist's website again, and follow each step - you'll notice that, after downloading the script, setting permissions and copying it to /usr/bin (do enter your password and do copy it) you will now have to go to the vpn server on your network, which will try to download and run the network connect software. This is where the password/error thing comes into play - Linux used to be based around having a root profile and user profiles, and this is what NC assumes - so it asks you to enter your root password. But, using ubuntu, you don't have a root password (root password and sudo password are different things). So let it install, and when it prompts for root password, this is where you keep pressing enter until it comes up with the SSL error. THEN go back to the terminal and type "junipernc". From here you should be all set.

Keep battling, i had so many problems with Juniper (and it still gives me no end of grief), but following madscientist's tutorial and any other forums I found, I've managed to get it working pretty well :)

Good luck,

Devin

---

### Post by amirmku on 2010-06-21
> **DevinD said:**
> amirmku - I can see two issues here. The first is that when you typed 

that was to download the junipernc script from madscientist's website and change the permissions of the file so that you can execute it. The script is NOT the same as Juniper Network Connect - it is a shell script that enables you to use Juniper Network Connect in Linux.

The other issue is that when you typed "sudo cp /tmp/junipernc /usr/bin", here you SHOULD HAVE entered your sudo password - all this does is copy the script you've just downloaded from the tmp file to /usr/bin so you don't have to be in the same folder as the script to execute it.

Try reading through the tutorial on madscientist's website again, and follow each step - you'll notice that, after downloading the script, setting permissions and copying it to /usr/bin (do enter your password and do copy it) you will now have to go to the vpn server on your network, which will try to download and run the network connect software. This is where the password/error thing comes into play - Linux used to be based around having a root profile and user profiles, and this is what NC assumes - so it asks you to enter your root password. But, using ubuntu, you don't have a root password (root password and sudo password are different things). So let it install, and when it prompts for root password, this is where you keep pressing enter until it comes up with the SSL error. THEN go back to the terminal and type "junipernc". From here you should be all set.

Keep battling, i had so many problems with Juniper (and it still gives me no end of grief), but following madscientist's tutorial and any other forums I found, I've managed to get it working pretty well :)

Good luck,

Devin
  

Hi Devin,
I tried following the tutorial by mad scientist but on connecting to VPN server using browser I dont get any pop up for password. but yes ysterday when i was trying to do the same that pop up did appear. but its not poping up now. 
Any suggestion ?

---

### Post by amirmku on 2010-06-21
Hi
Even getting a popup for password, I closed the browser and TYPED junipernc in terminal
using which Iwas able to add server, userid and REALM but after that i got following message
> This program requires the program 'jar'.
Use your package manager to install it.

Check the error log file '/tmp/junipernc.2750' for more information.

---

### Post by amirmku on 2010-06-21
> **amirmku said:**
> Hi
Even getting a popup for password, I closed the browser and TYPED junipernc in terminal
using which Iwas able to add server, userid and REALM but after that i got following message


Hey DEVIN,
Thanks I got to read your post where u had similar problem I too downloaded java6-jdk package, and now i could log in hey thanks again................

But I hav one small problem every time I start juniper it ask me only password  but no user id. 
If I want to login with different user id how to do that?
Any suggestion.

---

### Post by DevinD on 2010-06-23
Hey amirmku,

Sorry I meant to get back before - I would've suggested making sure java is updated (the popup window etc and junipernc needs java), but it seems you've done that now. When you run the script, it creates a profile. If you open the script in the editor, you'll see on the first few lines after the comments (comment lines are preceded by a "#" in shell scripts)
> _profile=default
You can actually change this if you want to (i've got it set up so i have 2 profiles for the 2 vpn's i use). The way the script works is that it prompts you for vpn settings the first time it runs, then saves all that info in a config file, and after that it'll always launch with the settings from the config file, saving you from entering them again. This is a problem if you typed them wrong the first time though. However, all you have to do is edit the config file. In your home directory (this is the default location) type
> ls -a | grep vpn
and you should see at least the two files .vpn.default.cfg and .vpn.default.crt (a "." at the beginning of the filename means it's a hidden file). The .cfg file is the config file, .crt is the certificate. Open the .cfg file in a text editor (or with "less") and it should look something like
> HOST="host.domain"
USER="username"
CERT="/home/user/.vpn.default.crt"
REALM="realm"
JAVA=/usr/bin/java
You can simply edit the settings directly, or delete the config file (or, for safety, rename it .vpn.default.cfg.bak or something of the like in case you need it back) and when you rerun the script it should prompt you for everything again.

I hope this helps, let me know if anything else bugs you.

Devin

---

### Post by DevinD on 2010-06-23
I realised my mind was wondering and the first part of my response may not connect so well to the second - my point was that, where it says "_profile=default", then the config file will be .vpn.default.cfg, if i set it to "_profile=anothervpn", the config file would be .vpn.anothervpn.cfg and so forth, this is how i had different profiles.

---

### Post by hhwangbo on 2010-07-02
> **WockaNation said:**
> I have attached a screenshot of the message I get when I enter the IP address of my VPN connection.  Still not working unfortunately.

I have the exact same problem when using an IP address.  I don't have a hostname - only an IP address for my VPN.

Any thoughts on addressing this?

---

### Post by CodeFooTyping on 2010-07-08
> **khaki54 said:**
> I've been fighting will this error for well over a year now, and I stll haven't found a resolution.  It ends with "Failed to connect/authenticate with IVE. Error 10" It's preceded by "dsclient.error state select role failed, error 10 (dsclient.cpp:322)"

20100326130405.708365 ncui[p13674.t13695] ncapp.info New ncapp log level set to 3 (nccommon.cpp:75)
20100326130405.708462 ncui[p13674.t13695] ncapp.info Version         : 6.5 
Release Version : 6.5-0-Build14951
Build Date/Time : Dec  9 2009
Copyright 2001-2008 Juniper Networks
 (ncapp.cpp:153)
20100326130405.929961 ncui[p13674.t13695] dsclient.info state: kStateSignin (dsclient.cpp:248)
20100326130405.930001 ncui[p13674.t13695] dsclient.info --> GET / (authenticate.cpp:162)
20100326130405.976170 ncui[p13674.t13695] dsclient.info <-- 302 [https://connect.boeing.com/dana-na/auth/url_default/welcome.cgi](https://connect.boeing.com/dana-na/auth/url_default/welcome.cgi) (authenticate.cpp:194)
20100326130405.976213 ncui[p13674.t13695] dsclient.info state: kStateWelcome (dsclient.cpp:256)
20100326130405.976234 ncui[p13674.t13695] dsclient.info --> GET /dana-na/auth/url_default/welcome.cgi (authenticate.cpp:162)
20100326130406.215728 ncui[p13674.t13695] dsclient.info <-- 200  (authenticate.cpp:194)
20100326130406.215919 ncui[p13674.t13695] dsclient.info state: kStateLogin (dsclient.cpp:288)
20100326130406.215949 ncui[p13674.t13695] dsclient.info --> POST /dana-na/auth/url_default/login.cgi (authenticate.cpp:162)
20100326130406.511419 ncui[p13674.t13695] dsclient.info <-- 302 [https://connect.boeing.com/dana-na/auth/url_default/welcome.cgi?p=select-role&id=state_4a26c645612a1439bb09c0326a42af58](https://connect.boeing.com/dana-na/auth/url_default/welcome.cgi?p=select-role&id=state_4a26c645612a1439bb09c0326a42af58) (authenticate.cpp:194)
20100326130406.511484 ncui[p13674.t13695] dsclient.info state: kStateSelectRole (dsclient.cpp:312)
20100326130406.511515 ncui[p13674.t13695] dsclient.info --> GET /dana-na/auth/url_default/welcome.cgi?p=select-role&id=state_4a26c645612a1439bb09c0326a42af58 (authenticate.cpp:162)
20100326130406.676220 ncui[p13674.t13695] dsclient.info <-- 200  (authenticate.cpp:194)
20100326130406.676282 ncui[p13674.t13695] dsclient.info state: kStateSelectRole (dsclient.cpp:320)
20100326130406.676369 ncui[p13674.t13695] dsclient.error state select role failed, error 10 (dsclient.cpp:322)
20100326130406.676669 ncui[p13674.t13695] ncapp.error Failed to connect/authenticate with IVE. Error 10 (ncapp.cpp:179)

I am using Xubuntu 10.04 having the same issue. And it is not related to this issue ->[http://kb.juniper.net/index?page=content&id=KB15890&cat=SA_5000&actp=LIST](http://kb.juniper.net/index?page=content&id=KB15890&cat=SA_5000&actp=LIST).  Just to test this i set up a fedora32 bit VM and it worked automatically.  So it is not a setting on the server side.  Everything else seems right.  

Is there something that i have missed?

---

### Post by CodeFooTyping on 2010-07-09
I have never been able to get this to work and I have intensified my efforts over the last week.  After continual failure and internet research, I started testing with different configurations on my main computer. I decided to try a baseline test, so I installed Fedora 11 32bit VM in Virtualbox.  For this the only hiccup was that I needed to install xterm.  Otherwise, it worked directly from the VPN portal.  Next I set up a new plain vanilla, Ubuntu 9.10 64bit VM in VirtualBox. After install I updated my system, but left it 9.10  Then used the following steps from the Mad Scientists blog (Thanks!!).


I executed the following on the commandline

```

sudo aptitude install sun-java6-plugin sun-java6-jdk sun-java6-jre
sudo aptitude install ia32-sun-java6-bin
wget -q -O /tmp/junipernc http://mad-scientist.net/junipernc
chmod 755 /tmp/junipernc
sudo cp /tmp/junipernc /usr/bin

```
Then I logged into the server and when the option became available I started Network Connect.  Just as expected from all that I have read I got the terminal popup.  As instructed I hit enter twice and logged out.

Then I ran junipernc from the command line.  
I entered the VPN server URL at the prompt. I entered the username when prompted. and also entered the realm (my company has more than one so I entered the one I normally choose here). Then I entered my password.

After watching the blinking lights for a little while thinking that it might work I got a "Failed to connect/authenticate with IVE. Error 10" response on the command line along with a popup that says "Unable to connect to IVE".

What am I missing???

I am going to try Ubuntu32 next, I am beginning to doubt that this will work in 64bits.

---

### Post by configt on 2010-07-20
> **CodeFooTyping said:**
> 
After watching the blinking lights for a little while thinking that it might work I got a "Failed to connect/authenticate with IVE. Error 10" response on the command line along with a popup that says "Unable to connect to IVE".

What am I missing???

I am going to try Ubuntu32 next, I am beginning to doubt that this will work in 64bits.


Sounds like it could be a UID and PW authentication issue, OR, you have the 'cache cleaner' issue that I have with running this junipernc script.    (see post [http://ubuntuforums.org/showthread.php?p=7771894#post7771894](http://ubuntuforums.org/showthread.php?p=7771894#post7771894)) 

After attempting to connect using the junipernc script, get the last several lines of your ~/.juniper_networks/network_connect/ncui.log

Here is what mine looks like:
```

tail ~/.juniper_networks/network_connect/ncui.log

20100719224332.961443 ncui[p16023.t16051] dsclient.info <-- 200  (authenticate.cpp:194)
20100719224332.961498 ncui[p16023.t16051] dsclient.info state: kStatePostCacheCleaner (dsclient.cpp:344)
20100719224332.961540 ncui[p16023.t16051] dsclient.info --> POST /dana-na/cc/ccupdate.cgi (authenticate.cpp:162)
20100719224333.51895 ncui[p16023.t16051] dsclient.info <-- 200  (authenticate.cpp:194)
20100719224333.51955 ncui[p16023.t16051] dsclient.error state post auth cache cleaner failed, error 10 (dsclient.cpp:346)
20100719224333.52114 ncui[p16023.t16051] ncapp.error Failed to connect/authenticate with IVE. Error 10 (ncapp.cpp:179)

```As you can see, there is some sort of 'cache cleaner' failure that prevents correct authentication.  If this is also your issue, I am sad to say that there is no solution to the problem (yet) other than asking your VPN admin to disable this checker function.

Here is a link from Juniper's support page that explains what this cache cleaner thing does, and there is further information on their website about how to disable it on the VPN server:
[http://www.juniper.net/techpubs/en_US/nsm2009.1/topics/task/configuration/endpoint-security-secure-access-global-cache-cleaner-option-configuring-nsm.html](http://www.juniper.net/techpubs/en_US/nsm2009.1/topics/task/configuration/endpoint-security-secure-access-global-cache-cleaner-option-configuring-nsm.html)

---

### Post by ssottile70 on 2010-07-20
Hello,

I have the same issue using Kubuntu 64bit. The madscientist script gives me the following error:


[FONT="Courier New"]

20100720172911.832802 ncui[p5580.t5607] dsclient.info <-- 200  (authenticate.cpp:194)
20100720172911.832876 ncui[p5580.t5607] dsclient.error state host checker failed, error 10 (dsclient.cpp:282)
20100720172911.832996 ncui[p5580.t5607] ncapp.error Failed to connect/authenticate with IVE. Error 10 (ncapp.cpp:179)
20100720172949.473851 ncui[p5580.t5601] ncui.info Sending kill signal (SIGQUIT) to ncsvc...  (ncapp.cpp:454)
[/FONT]


Anybody knows how to fix the problem?

Same error using jvm 32bit.

Thx
Salvo

---

### Post by ElectricKetchup on 2010-07-26
So I'm getting the same errors as the previous people.  Here's what I did as a work around so that I can get network connect working:

1) Removed all firefox and java related packages with aptitude remove
2) Downloaded 32 bit firefox and 32bit java from mozilla and sun.
3) Unpacked the two downloads.
4) sudo ln -s /home/jacob/Downloads/jre1.6.0_21/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/
5) Go to my company's VPN website with the firefox I downloaded

Also note that before I did that, I had also tried running the mad scientist juniper script.  I have never gotten that script to successfully get the network connect client running, but it does seem to set the file permissions for the client, so it's handy for that.

Yes, this solution does suck.  I would rather have the mad scientist script working so that I don't have to run a web browser.  Luckily I don't use Firefox as my primary web browser because if I did, it would be a pain in the *** to have multiple versions of firefox coexisting at once.

---

### Post by madscientist on 2010-07-26
Just want to say that I don't have any great ideas as to why this is happening, but FYI, I'm using my script along with Juniper Network Connect 1.2 (Release Version 6.1-0-Build13103) on my Ubuntu 10.04 64bit system, and I didn't need to run any special version of FireFox, etc.

I did install ia32-sun-java6-bin to get a 32bit version of Java, but my script should be testing Java to be sure it's 32bit and warning you if not, so I'm assuming all of you are already using a 32bit java.

My script doesn't use FireFox at all (that's the point ;)) so I'm not sure why one would need a 32bit firefox.

So, other than that I don't have any ideas about this, but it WOULD be helpful if you'd all post the version of Network Connect you're using when you report problems.  Maybe there's an issue with older (or newer!) versions.

---

### Post by ssottile70 on 2010-07-26
I have actually installed java downloading the software from Sun because I run command  [FONT="Courier New"]sudo apt-get install ia32-sun-java6-bin[/FONT] and get the following error:

[FONT="Courier New"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-sun-java6-bin
[/FONT]

Am i missing something?

Network Connect version is: 6.5R2

Thanks
Salvo

---

### Post by ElectricKetchup on 2010-07-26
> **madscientist said:**
> Just want to say that I don't have any great ideas as to why this is happening, but FYI, I'm using my script along with Juniper Network Connect 1.2 (Release Version 6.1-0-Build13103) on my Ubuntu 10.04 64bit system, and I didn't need to run any special version of FireFox, etc.

I did install ia32-sun-java6-bin to get a 32bit version of Java, but my script should be testing Java to be sure it's 32bit and warning you if not, so I'm assuming all of you are already using a 32bit java.

My script doesn't use FireFox at all (that's the point ;)) so I'm not sure why one would need a 32bit firefox.

So, other than that I don't have any ideas about this, but it WOULD be helpful if you'd all post the version of Network Connect you're using when you report problems.  Maybe there's an issue with older (or newer!) versions.

It's not that your script has a problem with the 32/64bit...  When I ran your script, it was able to load the java client, which was something that wasn't working at all in 64bit firefox.  The problem, though, when I ran your script was the GUI would say "Can't connect to IVE" and the log had the same stuff everyone else is getting about "dsclient.error state host checker failed, error 10 (dsclient.cpp:282)".  I thought that I might be able to run strace -f on it to see what the "host checker" was failing on, but the output was way too long for me to deal with last night, so I ended up just downloading a 32bit firefox since I needed it to work that moment.

---

### Post by madscientist on 2010-07-26
> **ssottile70 said:**
> I have actually installed java downloading the software from Sun because I run command  [FONT="Courier New"]sudo apt-get install ia32-sun-java6-bin[/FONT] and get the following error:

[FONT="Courier New"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-sun-java6-bin
[/FONT]What version of Ubuntu do you have?  Maybe you need to enable multiverse or similar?  I don't know how to figure out which repository a package came from or is contained in (I've tried aptitude show and also Synaptic properties but I don't see anything telling me about the repo) so I can't tell you which one you need to enable.

I have main, universe, multiverse, and restricted enabled in my repository list, along with lucid-backports, lucid-updates, and lucid-proposed.

---

### Post by madscientist on 2010-07-26
> **ElectricKetchup said:**
> It's not that your script has a problem with the 32/64bit...  When I ran your script, it was able to load the java client, which was something that wasn't working at all in 64bit firefox.  The problem, though, when I ran your script was the GUI would say "Can't connect to IVE" and the log had the same stuff everyone else is getting about "dsclient.error state host checker failed, error 10 (dsclient.cpp:282)".  I thought that I might be able to run strace -f on it to see what the "host checker" was failing on, but the output was way too long for me to deal with last night, so I ended up just downloading a 32bit firefox since I needed it to work that moment.Gotcha.

Well, as I mentioned it would be useful if those seeing this error would give information about what version of Network Connect they have.  Maybe the newer (or older) versions don't work, or don't work the same way.

---

### Post by ElectricKetchup on 2010-07-26
You need to edit your /etc/apt/sources.list and add in the "partner" repository.

> **ssottile70 said:**
> I have actually installed java downloading the software from Sun because I run command  [FONT="Courier New"]sudo apt-get install ia32-sun-java6-bin[/FONT] and get the following error:

[FONT="Courier New"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-sun-java6-bin
[/FONT]

Am i missing something?

Network Connect version is: 6.5R2

Thanks
Salvo

---

### Post by ElectricKetchup on 2010-07-26
> **madscientist said:**
> Gotcha.

Well, as I mentioned it would be useful if those seeing this error would give information about what version of Network Connect they have.  Maybe the newer (or older) versions don't work, or don't work the same way.


This is in my ncui.log file:
20100725224334.692534 ncui[13442] ncapp.info Version         : 6.4
Release Version : 6.4-0-Build14063
Build Date/Time : Mar 11 2009
Copyright 2001-2008 Juniper Networks

---

### Post by ssottile70 on 2010-07-26
Same repos that I have. I have also enabled repositories "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner" but again no luck.

salvo

---

### Post by ssottile70 on 2010-07-26
I have Kubuntu 10.04 with kernel:

2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux


Network connect version is:


20100726123306.391821 ncui[p9252.t9280] ncapp.info Version         : 6.5 
Release Version : 6.5-0-Build14951
Build Date/Time : Dec  9 2009
Copyright 2001-2008 Juniper Networks

Thanks
salvo

---

### Post by ElectricKetchup on 2010-07-26
> **ssottile70 said:**
> Same repos that I have. I have also enabled repositories "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner" but again no luck.

salvo


Yep, that's the same one I had to uncomment.  Also, I think I went through and made sure all the others were uncommented as well.
Did you run "sudo apt-get update" after enabling it?

---

### Post by ssottile70 on 2010-07-26
No and I've just done it and it worked!! I can now see the pkg and will try to install it.

Thanks a lot !!
salvo

---

### Post by ssottile70 on 2010-07-26
Unfortunately, I'm still having the same issue. Installed java 32 bit and run the command
[FONT="Courier New"]./ncsvc -h "$MYHOST" -u "$MYUSER" -p "$Mypassword" -f "$CERT" -r " Full Access" -L 4[/FONT]


and still get the following error in the ncsvc.log log file:

[FONT="Courier New"]20100726134243.607379 ncsvc[p11909.t11909] dsclient.info <-- 200  (authenticate.cpp:194)
20100726134243.607401 ncsvc[p11909.t11909] dsclient.error state host checker failed, error 10 (dsclient.cpp:282)
20100726134243.607528 ncsvc[p11909.t11909] ncapp.error Failed to authenticate with IVE. Error 10 (ncsvc.cpp:192)[/FONT]



Thanks for your help anyway,
Salvo

---

### Post by madscientist on 2010-07-26
> **ssottile70 said:**
> Unfortunately, I'm still having the same issue. Installed java 32 bit and run the command
[FONT="Courier New"]./ncsvc -h "$MYHOST" -u "$MYUSER" -p "$Mypassword" -f "$CERT" -r " Full Access" -L 4[/FONT]


and still get the following error in the ncsvc.log log file:

[FONT="Courier New"]20100726134243.607379 ncsvc[p11909.t11909] dsclient.info <-- 200  (authenticate.cpp:194)
20100726134243.607401 ncsvc[p11909.t11909] dsclient.error state host checker failed, error 10 (dsclient.cpp:282)
20100726134243.607528 ncsvc[p11909.t11909] ncapp.error Failed to authenticate with IVE. Error 10 (ncsvc.cpp:192)[/FONT]I was pretty sure this wasn't your problem; if you had the wrong Java (and it mattered) you likely wouldn't have been able to start the GUI at all.

Unfortunately it seems (based on a couple of reports) that the Network Connect version 6.5 has some problem that's causing this.  I don't have this version and I don't have any good ideas about what the problem is.  I'd be very interested to hear from anyone with this version which *does* work.

I heard that Juniper was going to start supporting Ubuntu directly, but as you can see my company is way behind (although in this case I guess that's a good thing...) so I don't know if they've done that.  Maybe filing a support request with Juniper directly might give some joy?

---

### Post by eschlenz on 2010-08-06
So, I too was getting the "Failed to connect/authenticate with IVE" error. What fixed it for me was simply running it in "no gui" mode: **junipernc -nogui**

I really hope it's as simple as that for everyone else.

My environment:

Linux xxxxxxxx 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)

**The error I was getting (note, mine is Error 5 which is different than most of you guys):**
 
Searching for ncsvc in current working directory
Searching for ncsvc in /home/eric/.juniper_networks/network_connect done.
ncapp> Failed to connect/authenticate with IVE. Error 5

---

### Post by eschlenz on 2010-08-06
> **eschlenz said:**
> So, I too was getting the "Failed to connect/authenticate with IVE" error. What fixed it for me was simply running it in "no gui" mode: **junipernc -nogui**

I really hope it's as simple as that for everyone else.

My environment:

Linux xxxxxxxx 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)

**The error I was getting (note, mine is Error 5 which is different than most of you guys):**
 
Searching for ncsvc in current working directory
Searching for ncsvc in /home/eric/.juniper_networks/network_connect done.
ncapp> Failed to connect/authenticate with IVE. Error 5

I wanted to mention too, that when you run it with -nogui, it will simply sit there with a message that says:

"Connecting to xxx.com : 443" - At this point, it is connected for me. I'm was able to verify that in another terminal by connecting to a server that is only available from my VPN. :)

---

### Post by Sudheesh on 2010-08-10
I have ubuntu 10.04 Lucid, and network connect 6.5. I am also getting the IVE  error 8 ( Failed to connect/authenticate with IVE. Error 8) .  

But I can connect via web interface ( because I had set a password for root ). 

I would like to  avoid this web interface.  Following is the command that gets executed when I am using the web interface...

/xxx/java -classpath /home/xxx/.juniper_networks/network_connect/NC.jar NC -h vpn.xxxxxxx.com -n  -t  -x


If I directly run this command on a terminal I get a message saying the 'reading from stdin' and then gets an error after some time..

Any help is appreciated.

---

### Post by Sudheesh on 2010-08-17
Any one wants to help here?

---

### Post by madscientist on 2010-08-17
> **Sudheesh said:**
> I have ubuntu 10.04 Lucid, and network connect 6.5. I am also getting the IVE  error 8 ( Failed to connect/authenticate with IVE. Error 8) .  

I would like to  avoid this web interface.  Following is the command that gets executed when I am using the web interface...

/xxx/java -classpath /home/xxx/.juniper_networks/network_connect/NC.jar NC -h vpn.xxxxxxx.com -n  -t  -x

If I directly run this command on a terminal I get a message saying the 'reading from stdin' and then gets an error after some time..

Hm.  I expect that the web interface is sending password information over a pipe to the stdin of the Java application, rather than sending it on the command line or environment, which are easier to monitor.

If you run: 'echo <passphrase> | /xxx/java -classpath ...' does that work?

If not you'll have to get trickier in order to understand what the expected stdin values are.  One possibility is to replace your /xxx/java command (for the duration of this debugging, not permanently of course) with a script that captures stdin.  Try something like this:

First, open a terminal and run "sudo -s" to get a root shell.  Then, try pasting this to your terminal:

```
mv /xxx/java /xxx/java-keepme
cat > /xxx/java <<EOF
#!/bin/sh
exec 2>/tmp/java.err.$$
tee /tmp/java.out.$$ | /xxx/java-keepme "$@"
EOF
chmod 755 /xxx/java
```

(Please note, I didn't try this... I just wrote it right here... if you have problems let me know).

After you do this, try connecting via the web.  If it succeeds, then you want to look in /tmp for files like java.* and see what they contain (of specific interest will be the java.out.*, most likely).  See if you can recognize the content as your passphrase or similar.

If you succeed (or give up #-o) you can get back your original setup with:

```
mv /xxx/java /xxx/java-tee
mv /xxx/java-keepme /xxx/java
```

(again as root of course)

---

### Post by Sudheesh on 2010-08-17
Hi madscientist
Thanks for your reply..

> If you run: 'echo <passphrase> | /xxx/java -classpath ...' does that work?

What should be the passphrase here?. Hope it is not obvious question!

I quickly tried the remaining part. But web interface hangs while invoking network connect. Seems to be an issue with our new java script.
The new java executable looks like below.

#!/bin/sh
exec 2> /tmp/java.err.7885
tee /tmp/java.out.7885 | /usr/lib/jvm/java-6-sun-1.6.0.20/jre/bin/java-keepme ""

Any issues here?. Sorry I couldn't figure it out,as I am not good at scripts.

---

### Post by madscientist on 2010-08-17
> **Sudheesh said:**
> 
The new java executable looks like below.

#!/bin/sh
exec 2> /tmp/java.err.7885
tee /tmp/java.out.7885 | /usr/lib/jvm/java-6-sun-1.6.0.20/jre/bin/java-keepme ""

Any issues here?. Sorry I couldn't figure it out,as I am not good at scripts.

Sorry, that was my fault.  I should have tested it ;)  You need to single-quote the EOF; the variables are being expanded when you create the script instead of when it's run.

Please try it like this:

```
cat > /xxx/java <<'EOF'
#!/bin/sh
exec 2>/tmp/java.err.$$
tee /tmp/java.out.$$ | /xxx/java-keepme "$@"
EOF
```

Then run the "chmod 755 /xxx/java" just to be safe.

The 3-line /xxx/java script should look exactly like it does above between the "cat" and EOF lines, including the "$$" and the "$@" etc.

---

### Post by Sudheesh on 2010-08-17
OK.. Situation improved. I can see the network launching progress bar in the firefox , and even though the progress bar reaches the end, network connect is not getting launched.

Script looks like this now.

#!/bin/sh
exec 2>/tmp/java.err.$$
tee /tmp/java.out.$$ | /xxx/java-keepme "$@"


I see a new process like the below.
/usr/lib/jvm/java-6-openjdk/jre/
lib/i386/../../bin/java sun.applet.PluginMain /tmp/icedteaplugin-sudhi/7970-iced
teanp-plugin-to-appletviewer /tmp/icedteaplugin-sudhi/7970-icedteanp-appletviewe
r-to-plugin

which was missing when the network connect is running properly?

---

### Post by Sudheesh on 2010-08-17
I made a mistake. Let me correct that..

---

### Post by madscientist on 2010-08-17
> **Sudheesh said:**
> OK.. Situation improved. I can see the network launching progress bar in the firefox , and even though the progress bar reaches the end, network connect is not getting launched.

Script looks like this now.

#!/bin/sh
exec 2>/tmp/java.err.$$
tee /tmp/java.out.$$ | /xxx/java-keepme "$@"That's good.

> **Sudheesh said:**
> 
I see a new process like the below.
/usr/lib/jvm/java-6-openjdk/jre/
lib/i386/../../bin/java sun.applet.PluginMain /tmp/icedteaplugin-sudhi/7970-iced
teanp-plugin-to-appletviewer /tmp/icedteaplugin-sudhi/7970-icedteanp-appletviewe
r-to-plugin

which was missing when the network connect is running properly?

Hm.  Well, we're on the bleeding edge here so in a way I'm not surprised that it's having problems.  However, have you looked at the content of the /tmp/java.err* and /tmp/java.out* files?  That's really what we're trying to get here.  Even if the system doesn't come up we might find some interesting stuff there.  Anything?

Be sure you're looking at the right ones; there may be more than one.

---

### Post by Sudheesh on 2010-08-17
All the java .err and .out files are empty ( size 0 ).

When I execute java-keep-me  from command prompt, it runs propery and exit after showing the command line options..

When I run java ( script ), it runs properly by showing command line options but doesn't exit on its own. I need to press enter for exit..

---

### Post by madscientist on 2010-08-17
> **Sudheesh said:**
> All the java .err and .out files are empty ( size 0 ).

When I execute java-keep-me  from command prompt, it runs propery and exit after showing the command line options..

When I run java ( script ), it runs properly by showing command line options but doesn't exit on its own. I need to press enter for exit..

Well, my assumption might have been wrong in the first place.  Maybe it's not waiting for something from stdin.

One thing you can try is changing the script like this:

```
#!/bin/sh
tee /tmp/java.out.$$ | (sleep 2; /xxx/java-keepme "$@")
```

I'm not saying that will be any better but it might be (based on some experiments I performed here).  See if you get any content in the .out file in this case.

Unfortunately, if you don't then I don't know what it's waiting for.  Since I don't have that version of the software, I don't really have any good ideas about where to go next.

---

### Post by alaaji on 2010-08-18
I'd love to try this but once I try to connect to the VPN in order to download Juniper Connect, I get this message:

"You do not have permission to login. Please contact your administrator."

Well, I contacted my administrator and he said that we don't support Linux distributions.  They suggested I just use a dual boot system with Windows on it.

Is there any way that I can get the software to install on Ubuntu besides the one outlined in the directions?

---

### Post by Sudheesh on 2010-08-18
Dear madscientist,

Some additional info, which I should have given earlier.

As I mentioned earlier this is the command that gets executed successfully if I launch then network connect from web interface.

 /usr/lib/jvm/java-6-sun-1.6.0.20/jre/bin/java -classpathhome/sudhi/.juniper_networks/network_connect/NC.jar NC -h vpn.tridentmicro.com -n  -t  -x

When I run the above, I get the following messages in the terminal. I get a  network connect GUI also.  

"Searching for ncsvc in current working directory
Searching for ncsvc in /home/sudhi/.juniper_networks/network_connect done.
[>/home/sudhi/.juniper_networks/network_connect/ncsvc<] [>-l<] [>3<] [>-n<] [>-t<] [>-x<] indx = 4 
reading form stdin .. 
No data within 30 seconds.
Password:" 

After 30 seconds if I enter the vpn password, I get the following error messages ( a window will get popped up saying invalid parametsrs )  

"usage: ncui -h host -u user -p passwd -r realm -f cert_file [-l log_level] [-L log_level]
       ncui -h host -c cookies -f cert_file [-l log_level] [-L log_level] [-U sign_in_url]
       ncui -v
    log_level : 0 : Log Critical messages only
                1 : Log Critital and Error messages
                2 : Log Critital, Error and Warning messages
                3 : Log Critital, Error, Warning and Info messages(default)
                4 : Log All Verbose messages
                5 : Log All messages"



I tried with the new script which is given below. I do not any java.out and err files now in /tmp.

#!/bin/sh
tee /tmp/java.out.$$ | (sleep 2; /usr/lib/jvm/java-6-sun-1.6.0.20/jre/bin/java-k
eepme "$@")

regards,
Sudheesh.

---

### Post by gkirlik on 2010-08-18
Dear All,

I am using Ubuntu 10.04 (32 bit). I tried to use Juniper Network Connect VPN. Although, I implement all necessary steps such as Java installation, I could not figure out to run the NC, properly. Every time, I start the NC, I am getting "Session timeout" error. How can I solve this problem?

Best regards.

---

### Post by gkirlik on 2010-08-20
I have solved the problem with the following way. For more details see the webpage [http://www.juniperforum.com/index.php?topic=10394.0](http://www.juniperforum.com/index.php?topic=10394.0)

Uninstall OpenJDK. Because OpenJDK/Juniper incompatibility causing "Session timed out" error.
Install Sun-Java.

> **gkirlik said:**
> Dear All,

I am using Ubuntu 10.04 (32 bit). I tried to use Juniper Network Connect VPN. Although, I implement all necessary steps such as Java installation, I could not figure out to run the NC, properly. Every time, I start the NC, I am getting "Session timeout" error. How can I solve this problem?

Best regards.

---

### Post by yellowking on 2010-08-24
Bah.  This has been working fine for me on 8.04 and NC 6.5 for the longest time, but sometime after 10.04, it has stopped working for me.  I'm not sure if it was just the upgrade or something else I've done.  Here's the error message I'm getting:

"A version conflict occured [sic] between the target application and the applet.  Please contact your system administrator.  (Error condition SL0x12)"

I don't really understand the error message-- what's the target application?  Is this a java version issue?  I did have OpenJDK on there, but have removed it.

---

### Post by lordhaworth on 2010-08-27
Hi,

I had been getting the "session timeout" error under 9.04. WIth not much to lose I recently upgraded to 9.10, now I get a "setup failed, sorry" in the bottom left of the browser when I try and launch. I am going to try the steps posted above (this is a very useful thread), but does anyone know what is responsible for the setup error?


I also decided to try and just download the software and set it up myself so I get a bit more control/can see errors. 
I downloaded ncui-6.5R2.i386.rpm and unpacked all ok. However when I try and run ncsvc I get the following:
```

mkdir(/root/.juniper_networks) failed: Permission denied

```
I should point out that I am su at this point.

ncdiag gives output which I can post if need be

Any help much appreciated - I will try the steps in above posts tonight

---

### Post by torspo on 2010-08-27
The server I'm connecting to first requires me to log in without a password after which I get an SMS to my phone including a temporary one time password for the next stage.

I can also use the ncsvc with an empty password and get the SMS, but where can I input the password for the second phase? Using it instead of the empty password does not work (as it's not the password but a response to the challenge).

---

### Post by lordhaworth on 2010-08-27
> 
Bah. This has been working fine for me on 8.04 and NC 6.5 for the longest time, but sometime after 10.04, it has stopped working for me. I'm not sure if it was just the upgrade or something else I've done. Here's the error message I'm getting:

"A version conflict occured [sic] between the target application and the applet. Please contact your system administrator. (Error condition SL0x12)"

I don't really understand the error message-- what's the target application? Is this a java version issue? I did have OpenJDK on there, but have removed it.




I uninstalled openJDK... I now get the same error as yellowking

---

### Post by fermor on 2010-08-29
This is working for me on Ubuntu server 10.04 fresh install 'with "Ubuntu desktop" installed via tasksel' and forgetting all about openJDK and icedtea, as apparently this has an incompatibility....

Add these to your repo's:-
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

Then install sun-java6
apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Then using firefox to login worked fine for me... haven't worked out yet how to get it to work without need for firefox yet... but this doesn't really bother me.

---

### Post by lordhaworth on 2010-08-29
> 
This is working for me on Ubuntu server 10.04 fresh install 'with "Ubuntu desktop" installed via tasksel' and forgetting all about openJDK and icedtea, as apparently this has an incompatibility....

Add these to your repo's:-
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

Then install sun-java6
apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Then using firefox to login worked fine for me... haven't worked out yet how to get it to work without need for firefox yet... but this doesn't really bother me. 


Interesting... I just upgraded to 10.04 (figure I may as well get right up to date while I am having issues) but am still getting exactly the same error as I mentioned above "Sl0x12". I don't think I have ever been given an error code that has no documentation whatsoever online.

---

### Post by lordhaworth on 2010-08-29
What about wine? I think that the error I was getting might be due to unrecognised certification which is picked up on in firefox 3.6 but apparently not in 3.0. I am running 3.0 in wine with java but not quite got there yet. It asks if I want to run setup and then redirects me to the main page... Is there anything else I need/has anyone else got it working under wine?


Cheers

---

### Post by lordhaworth on 2010-08-30
Got it working eventually... If you want to know how: midlessly upgrade as much as possible and try a mix & match of the advice in the above posts, turn it on and off lots of times, spend all evening working on it, turn it off again, go to bed, designate the next day to work on it, turn it on, think "ok ill start by seeing what err message its giving me now" and then be pleasantly surprised when it works...

Cheers all for the bits of info throughout thread

---

### Post by torspo on 2010-09-01
> **torspo said:**
> The server I'm connecting to first requires me to log in without a password after which I get an SMS to my phone including a temporary one time password for the next stage.

I can also use the ncsvc with an empty password and get the SMS, but where can I input the password for the second phase? Using it instead of the empty password does not work (as it's not the password but a response to the challenge).

Sorry to bump, but any tips on this?

---

### Post by torspo on 2010-09-01
> **torspo said:**
> Sorry to bump, but any tips on this?

I managed to get it working, it's a bit difficult to use. 

I can find out the DSID cookie from browser using firebug console (document.cookie) and supply it as an argument -c DSID=xxxx to ncui.

---

### Post by howanu on 2010-09-08
It's been almost a week, and I think I'm making progress ... does anyone know how to get more diagnostic information (besides -L 5)?

I'm executing the following (or junipernc, which gives me the same result):

> /usr/lib/jvm/ia32-java-6-sun/jre/bin/java -jar $HOME/.juniper_networks/network_connect/NC.jar -h my.companys.VPNurl -u 'myUsername' -p MyPasswd -f certificate.der -r 'myRealm' -L 5
My logs tell me that I failed to authenticate with error 10, but I'm not sure what this means ... there are plenty of others seeing the same message, but as far as I can tell no one seems to have gotten beyond it.

My logs are not much help, at least to my untrained eye:

[SIZE=3]ncsvc.log:[/SIZE]
> DSHttp.debug state_reading_response_body - copying 0 buffered bytes (http_requester.cpp:800)
DSHttp.debug state_reading_response_body - recv'd 0 bytes data (http_requester.cpp:833)
DSHttp.debug state_reading_response_body - copying 0 buffered bytes (http_requester.cpp:800)
DSHttp.debug state_reading_response_body - recv'd 0 bytes data (http_requester.cpp:833)
DSHttp.debug state_reading_response_body - copying 0 buffered bytes (http_requester.cpp:800)
DSHttp.debug state_reading_response_body - recv'd 4096 bytes data (http_requester.cpp:833)
DSHttp.debug state_reading_response_body - copying 4096 buffered bytes (http_requester.cpp:800)
DSHttp.debug state_reading_response_body - recv'd 0 bytes data (http_requester.cpp:833)
DSHttp.debug state_reading_response_body - copying 0 buffered bytes (http_requester.cpp:800)
DSHttp.debug state_reading_response_body - recv'd 0 bytes data (http_requester.cpp:833)
DSHttp.debug state_reading_response_body - copying 0 buffered bytes (http_requester.cpp:800)
DSHttp.debug state_reading_response_body - recv'd 4533 bytes data (http_requester.cpp:833)
DSHttp.debug state_reading_response_body - copying 4533 buffered bytes (http_requester.cpp:800)
DSHttp.debug state_reading_response_body - recv'd 0 bytes data (http_requester.cpp:833)
dsclient.info <-- 200  (authenticate.cpp:194)
dsclient.info state: kStatePostCacheCleaner (dsclient.cpp:344)
dsclient.info --> POST /my-path-to/ccupdate.cgi (authenticate.cpp:162)
http_connection.para Entering state_start_connection (http_connection.cpp:282)
http_connection.para Entering state_continue_connection (http_connection.cpp:299)
http_connection.para Entering state_ssl_connect (http_connection.cpp:468)
dsssl.para SSL connect ssl=0x8ee4de8/sd=4 connection using cipher RC4-MD5 (DSSSLSock.cpp:656)
http_connection.para Returning DSHTTP_COMPLETE from state_ssl_connect (http_connection.cpp:476)
DSHttp.debug state_reading_response_body - copying 0 buffered bytes (http_requester.cpp:800)
DSHttp.debug state_reading_response_body - recv'd 0 bytes data (http_requester.cpp:833)
dsclient.info <-- 200  (authenticate.cpp:194)
dsclient.error state post auth cache cleaner failed, error 10 (dsclient.cpp:346)
ncapp.error Failed to authenticate with IVE. Error 10 (ncsvc.cpp:197)
dsncuiapi.para DsNcUiApi::~DsNcUiApi (dsncuiapi.cpp:72)
[SIZE=3]ncui.log:[/SIZE]
> Release Version : 6.5-0-Build15255
Build Date/Time : Feb 18 2010
Copyright 2001-2008 Juniper Networks
 (ncapp.cpp:153)
dsclient.info state: kStateSignin (dsclient.cpp:248)
dsclient.info --> GET / (authenticate.cpp:162)
dsclient.info <-- 302 [https://my.companys.VPNurl/my-path-to/welcome.cgi](https://my.companys.VPNurl/my-path-to/welcome.cgi) (authenticate.cpp:194)
dsclient.info state: kStateWelcome (dsclient.cpp:256)
dsclient.info --> GET /my-path-to/welcome.cgi (authenticate.cpp:162)
dsclient.info <-- 200  (authenticate.cpp:194)
dsclient.info state: kStateLogin (dsclient.cpp:288)
dsclient.info --> POST /my-path-to/login.cgi (authenticate.cpp:162)
dsclient.info <-- 302 [https://my.companys.VPNurl/my-path-to/welcome.cgi?p=preauth&id=state_1234&signinRealmId=3](https://my.companys.VPNurl/my-path-to/welcome.cgi?p=preauth&id=state_1234&signinRealmId=3) (authenticate.cpp:194)
dsclient.info state: kStatePostAuth (dsclient.cpp:328)
dsclient.info --> GET /my-path-to/welcome.cgi?p=preauth&id=state_1234&signinRealmId=3 (authenticate.cpp:162)
dsclient.info <-- 200  (authenticate.cpp:194)
dsclient.info state: kStatePostCacheCleaner (dsclient.cpp:344)
dsclient.info --> POST /my-path-to/ccupdate.cgi (authenticate.cpp:162)
dsclient.info <-- 200  (authenticate.cpp:194)
dsclient.error state post auth cache cleaner failed, error 10 (dsclient.cpp:346)
ncapp.error Failed to connect/authenticate with IVE. Error 10 (ncapp.cpp:179)
[SIZE=3]Environment:[/SIZE]

[LIST]
[*]Ubuntu 10.04 LTS Lucid Lynx
[*]Amd 64bit (thank you madscientist for the 64bit instructions!)
[*]Juniper  6.5-0-Build15255
[/LIST]
Does anyone with a similar error message have a success story they can share?

---

### Post by kernel01 on 2010-09-10
Hello,

I'm using Debian lenny but I also tried with testing. My system is a 64bit one but I also tried with a 32bit chroot.
No matter what I try, I'm getting this in ncsvc.log:
20100908204950.22171 ncsvc[p22330.t22330] dsclient.error state post auth cache cleaner failed, error 10 (dsclient.cpp:346)
20100908204950.22280 ncsvc[p22330.t22330] ncapp.error Failed to authenticate with IVE. Error 10 (ncsvc.cpp:192)
20100908204950.22306 ncsvc[p22330.t22330] dsncuiapi.para DsNcUiApi::~DsNcUiApi (dsncuiapi.cpp:72)

I have read somewhere that having a realm string with a space in it might be troublesome, can you confirm or disprove this somehow?

$ ncsvc -v
Juniper Network Connect Server for Linux.
Version         : 6.5
Release Version : 6.5-0-Build14599
Build Date/time : Aug 12 2009 14:35:22 
Copyright 2001-2008 Juniper Networks

Java plugin is:
**Java(TM) Plug-in 1.6.0_21**

Installed via the sun-java6-plugin [6-20-0lenny1]

I also sent you an email to the address listed here: [http://mad-scientist.net](http://mad-scientist.net)

Let me know if you require additional info and of course, thanks in advance :)


Jess

---

### Post by howanu on 2010-09-10
> **kernel01 said:**
> 
I have read somewhere that having a realm string with a space in it might be troublesome, can you confirm or disprove this somehow?


Hi Jess,

I also have space in my realm, and I also get IVE error 10! Coincidence? ...

---

### Post by shoreview on 2010-09-30
Hi

I'm on Ubuntu 10.04 and I use the sun java 32 bit libs, and  with that can connect to the secure server and install Juniper Net  connect. But then the problem is that I have to enter an ldap user name,  a password and then a Securid number.  I can't see how to map those to  -u username and -p password. The realm is SecureLDAP.

Has anyone solved the same problem?

C

---

### Post by CodeFooTyping on 2010-10-06
I have been trying at this for months, always getting the 'cannot connect to IVE error'. After much research and discussing this with our network folks, I think the issue is caused by Host Checker.  Apparently this cannot be disabled on a per OS basis. What it looks for, can be configured, or even turned off, on a per OS basis.  But IT MUST RUN, if it is enabled at all.  This component allows automated checking for virus software (among other things) and so it must be enabled for certain OSes that are vulnerable to that sort of issue ;).

Host Checker is a Java applet and must be started by the browser. There is a call during the Network connect phase that fails if it is not running. Here is the stack trace from where it failed on my machine...
```
java.lang.Exception: Cound not find null/narport.txt; cannot send null action to Host Checker
	at SecureHCLauncher.openCommandSocket(SecureHCLauncher.java:405)
	at SecureHCLauncher.sendAction(SecureHCLauncher.java:433)
	at SecureHCLauncher.start(SecureHCLauncher.java:187)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1639)
	at java.lang.Thread.run(Thread.java:619)
```

The script that Mad Scientist was so good to create does not start this component (I am sure that his or her network does not require it). So the script fails.

Given that constraint I have a few roads to try, I can try one on my own as it fits within my current level of skill.  The other will require skills I have not had to acquire yet...

1. Try with firefox in a 32bit jail.
 a. there is plenty of info on this so I can do this myself. I am not sure however if 64bit apps will be able to use the tun interface.
2. Create a 32bit Ubuntu VM in Virtual box and use it as a router.
 a. I have this VM up and connected, it actually works better than Fedora at this.  I will be learning a lot in this endeavor.  Also seems like a giant kludge.
3. Extend Mad Scientists script to start Host Checker before it starts Network Connect.
 a. totally out of my element here, I am not even sure it is possible.

If anyone has any comments or advice it would be much appreciated.

Thanks,

---

### Post by deakblue on 2010-10-06
Hi CodeFooTyping,

I'm in exactly the same boat, many hours wasted on this.  My sysadmin watched a trace on his side and said,"oh HostChecker is running and fails, I didn't think this needed to run."

Anyway, I'm also contemplating creating a 'clean' 32-bit installation, but I'll wait to hear how it works for you.

Good luck,
-Will

EDIT UPDATE: I had an old spare desktop, so I tried a full 32 bit installation.  It works now.  I don't regard this as a solution as much as a problematic workaround.

---

### Post by CodeFooTyping on 2010-10-06
Thanks, deakblue.

I did get it to work on 32bit Ubuntu right away.  Just be sure to install Sun Java and the Sun Java plugin.  Also Juniper recommends that you install network connect using alien and an rpm that they provide for Network Connect on Redhat.  I actually found getting connected on Ubuntu to be easier and faster than getting connected on Fedora 13.  But find that to be true about Ununtu anyway.

---

### Post by alberto1976 on 2010-10-30
> **yellowking said:**
> Bah.  This has been working fine for me on 8.04 and NC 6.5 for the longest time, but sometime after 10.04, it has stopped working for me.  I'm not sure if it was just the upgrade or something else I've done.  Here's the error message I'm getting:

"A version conflict occured [sic] between the target application and the applet.  Please contact your system administrator.  (Error condition SL0x12)"

I don't really understand the error message-- what's the target application?  Is this a java version issue?  I did have OpenJDK on there, but have removed it.

I had the exactly the same problem (working on 8.04 and no more on 10.04) and exactly the same error. In my case, it was a java issue. Java6 was not supported by the Network Connect applet that was being launched on my machine. First, I had to remove java6-jre and java6-plugin (I did this from Package manager) and then install java5 (this is done after adding the jaunty multiverse repositories to /etc/apt/sources.list). 

```
sudo aptitude install sun-java5-jre sun-java5-plugin 
```Note that Firefox 3.6 (the one that comes with Lucid) does not support the java5 plugin, so, if you VPN connection was done via firefox, you will also need to downgrade to firefox 3.5.

---

### Post by madscientist on 2010-11-01
You don't need to install sun-java5-*.  Anyway, I don't have those installed and my network connect (Release Version : 6.1-0-Build13103 / Build Date/Time : May 6 2008) works fine.

What you DO have to have is the 32bit version of Java, if you're running a 64bit OS.  So, you can remove the sun-java5* packages again and add this one:

```
sudo aptitude install ia32-sun-java6-bin
```

and that should do it.

---

### Post by corentin.barbu on 2010-11-06
Had the same (time-out) in maverick, reconfiguring through
sudo update-alternatives --config java
was not enough. I had to remove openjdk, now working fine.

Corentin

---

### Post by hotmanta on 2010-11-06
Thanks for the great work Mad Scientist!

I installed your script and with the help of my trusty network admin colleague was able to get it working!

I first experienced the painful *dsclient.info state: kStateSelectRol*e and *dsclient.error state select role failed, error 10* situation mentioned in an earlier post on 26th March 2010.

My colleague and I worked together to solve this error. From the Juniper admin interface, he had to clone the general network connect role to one specifically for my Linux client. He disabled the customised role selection post logon page so it would autoload the network connect role for me upon connection. Then he made a few tweaks as the clone command doesn't clone all the settings like ACLs for example.

I am using Kubuntu 10.10 64bit release. I also grabbed the later Linux client via file from a site I found via a google search, [http://www.tcnj.edu/~nts/downloads/NetworkConnect/ncui-6.5R2.i386.rpm](http://www.tcnj.edu/~nts/downloads/NetworkConnect/ncui-6.5R2.i386.rpm). I extracted the files from this rpm and use these in my ~/.juniper_networks/network_connect directory to get away from the dependency on older library files like libstdc++2.10-glibc2.2 for example. My company has an old network connect client and server side IVE OS on offer, will be upgrading next year.
 
Thanks again for enabling me to use my latest 64bit distro with this painful piece of Juniper software!

Cheers,
HotManta

---

### Post by gosen on 2010-12-07
[FONT=Arial][FONT=Comic Sans MS]Hi all:)
I can't enter my SecurID value... 
I was enter a personal PIN and the value provided by the SecurID fob in one win, but[/FONT][FONT=Comic Sans MS] junipernc doesn't connect.. 
It's work normally only if I connect to vpn by click "Start" button next to "Network Connect" on web page of VPN server..[/FONT]
[/FONT][FONT=Arial]How the program read SecurID value?[/FONT]

Thanks, and sorry for my bad english:P

---

### Post by polarbug on 2010-12-12
Still struggling.

I am using a old P-III computer running Ubuntu 10.10 maverick, I followed the exact procedures provided by Mad-scientist:

1. create a password for root;
2. install java stuff;
3.restart firefox 3.6.10

My problem is installNC.sh is not runing when start firefox, but I am able to log into my company's VPN network and check email which is located under "web bookmarks". But when I click on the icon under "terminal sessions", it gives me "The terminal session is not supported on your computer".

Any ideas?

---

### Post by N3M3BasaT on 2010-12-27
Hi, juniper freak's!

Ahm...I want to use a network connect on my Ubuntu 10.10. I have install a Mad Scientist script in run it, but nothing happend... see the screenshot! 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=179430&stc=1&d=1293441524[/IMG]

i don't have any idea, why does it not worK! :D

p.s.: sorry for my english....

---

### Post by madscientist on 2010-12-27
> **N3M3BasaT said:**
> Hi, juniper freak's!

Ahm...I want to use a network connect on my Ubuntu 10.10. I have install a Mad Scientist script in run it, but nothing happend... see the screenshot! 

i don't have any idea, why does it not worK! :D


Not sure what you mean by "nothing happened"... it looks to me like the connection started.  You have the GUI application visible and the status is "Connected" and you have an IP address.  It's a bit odd that your send/receive bytes are zero but... can you be more clear as to what you mean by "it does not work"?  What are you trying to do, that doesn't work?

---

### Post by N3M3BasaT on 2010-12-28
> **madscientist said:**
> Not sure what you mean by "nothing happened"... it looks to me like the connection started.  You have the GUI application visible and the status is "Connected" and you have an IP address.  It's a bit odd that your send/receive bytes: are zero but... can you be more clear as to what you mean by "it does not work"?  What are you trying to do, that doesn't work?

:D I'm a newbie in this water....but....I get it work now. I thought that will pop-up some Java window with some remote desktop viewer and connect to my office PC in that way, but then I found out that is just a connection with my pc and my job network. Then I extra lunch a Terminal Server Client and enter my office pc IP and connect. :D

p.s.: ok, my english sux! :D **** it! if I'm drunk I speak very well! :D

THANX ANYWAY!!!!

madscientist - I respect you! :)

---

### Post by Joe Ker1086 on 2011-01-06
I also am having problems. I have tried all of the procedures mad scientist has provided but everytime I try to connect i get an IVE error 10......any ideas?

---

### Post by DigitalSymphony on 2011-01-11
MadScientist,Thank you SO MUCH for your script. Also a big thanks to all the other contributors to this thread. I tried a number of different suggestions on this thread and initially did not want to use MadScientist's script (I'm a newbie to Linux/Ubuntu and really wanted to do this by myself). However, after trying a number of different solutions from this and other threads, I ended up caving in and using the script. Works perfect!

I can't be sure this will work for everyone, but for the record here is my config:
Using 64-bit Ubuntu
Firefox (64 or 32 bit doesn't matter) 3.6.13
Java 32-bit
MadScientist's script.
network Connect 6.4.0

My 1st attempt with pre-installed Firefox, OpenSDK updated to Sun's 32-bit JRE did not work. A clean install of everything worked. So, for me, the turning point was completely getting rid of (via Synaptic Manager remove) OpenSDK, my previous unsuccessful attempt at installing SunJava and Firefox.

With none of these installed, I downloaded and installed firefox from the mozilla website
I then installed Sun JRE
(sudo aptitude install sun-java6-plugin sun-java6-jdk sun-java6-jre
sudo aptitude install ia32-sun-java6-bin)
Type 'about: plugins' in Firefox address bar to ensure Sun's java plugins are listed. Javascript is enabled (pop-ups from the site are enabled ...not taking any chances)
Download NC 6.4.0 (via your VPN website)
Download the script and follow steps from MadScientist's site ([http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html))

---

### Post by nitecon on 2011-01-18
Ok I've tried this several times over many distros.  On Fedora 14 32bit I get it to work without any problem what so ever.  I however can't get it to run on any 64bit arch what so ever.  Following directions to the "T" I get the java error 10.  It appears to be related to the C/C++ cache cleaner 32bit lib that is missing... please see the attached screenshot...  I'm currently testing this on a brand new Ubuntu 64bit 10.10 install, perhaps there is some library I forgot to install that you guys naturally have on your systems?


[IMG]http://www.nitecon.com/extra/images/vpn_cache.jpg[/IMG]

List of everything I have installed / run includes...
Enable Canonical Repo for sun-java...
sudo yum install build-essentials
sudo yum install g++ gcc
sudo yum install make automake autoconf autoconf2.13 autoconf-archive gnu-standards autoconf-doc libtool gettext gettext-doc libtool-doc gcj
sudo apt-get install ia32-sun-java6-bin
sudo apt-get install sun-java6-plugin sun-java6-jdk sun-java6-jre
sudo install rpm (With Alien tools etc)
and then finally after connecting the the VPN site and downloading the files etc as per the manual I go to run junipernc, and get the error as in the image above.

These errors show up on both a clean physical install of 10.10 64bit, and also on 10.10 64bit vmware virtual machine.  Anyone able to help on what I can do to fix this issue?

---

### Post by soljin on 2011-01-22
> **nitecon said:**
> Ok I've tried this several times over many distros.  On Fedora 14 32bit I get it to work without any problem what so ever.  I however can't get it to run on any 64bit arch what so ever.  Following directions to the "T" I get the java error 10.  It appears to be related to the C/C++ cache cleaner 32bit lib that is missing... please see the attached screenshot...  I'm currently testing this on a brand new Ubuntu 64bit 10.10 install, perhaps there is some library I forgot to install that you guys naturally have on your systems?


[IMG]http://www.nitecon.com/extra/images/vpn_cache.jpg[/IMG]

List of everything I have installed / run includes...
Enable Canonical Repo for sun-java...
sudo yum install build-essentials
sudo yum install g++ gcc
sudo yum install make automake autoconf autoconf2.13 autoconf-archive gnu-standards autoconf-doc libtool gettext gettext-doc libtool-doc gcj
sudo apt-get install ia32-sun-java6-bin
sudo apt-get install sun-java6-plugin sun-java6-jdk sun-java6-jre
sudo install rpm (With Alien tools etc)
and then finally after connecting the the VPN site and downloading the files etc as per the manual I go to run junipernc, and get the error as in the image above.

These errors show up on both a clean physical install of 10.10 64bit, and also on 10.10 64bit vmware virtual machine.  Anyone able to help on what I can do to fix this issue?

I was getting the same error FOREVER.  I've never been able to connect from 64 bit linux.  I have done the mad scientist thing tons of times and never could stay connected.

UTIL!!
I found out that your realm is very important and cannot be blank!

To find out your realm name:
1) Go to the website you use to login and install NC (the actual login page with the user name and password fields)
2) View source on the page and ctrl+f for realm.
3) You should see and input or option field with name="realm".
4) If it's a hidden input just look for the value="<your-ream-name>" Thats your realm name enter it when using mad scientist's script.  If it's an option field find the one you would select from and again look for the value=.

Worked like charm finally have access from my preferred OS!!!

---

### Post by MikeG0 on 2011-01-23
> **ejjp said:**
> In feisty the script of madscientist worked ok. Now I have a eee-pc with debian lenny (with lxde) and an user with the sudo power. Iceweseal, sunjava6, ... I think that I follow the how-to to perfectly as before, however I do not able to dowload the .juniper_network folder. I have tarred my .juniper folder from feisty and put in the debian system and when run junipernc.sh (the first time ask me the sudo password, I fill the fields with my user, host...password, a new .vpn.crt is generated, the file .vpn.cfg is correct according to the new location and then appears this message:

:~$ junipernc.sh 
Searching for ncsvc in current working directory
Searching for ncsvc in /home/ejjp/.juniper_networks/network_connect done.
ncsvc> Failed to setuid to root. Error 1: Operation not permitted
java: ncui.cpp:262: void NCUI::run(): Assertion `m_conn->isConnected()' failed.
/usr/bin/junipernc.sh: line 265:  3064 Abortado                "$java" -jar "$_ncpath/NC.jar" -h "$HOST" -u "$USER" -p "$password" -f "$CERT" -r "$REALM"


I also was getting ...

```
ncsvc> Failed to setuid to root. Error 1: Operation not permitted
```


This error only started after I moved my home directory over to a new partition as described here ...
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I realized it had to do with the mounting parameters set in /etc/fstab.  Changed nosuid to suid ...

UUID=????   /home    ext4          nodev,nosuid   0       2

to 

UUID=????   /home    ext4          nodev,suid   0       2

I'm back to working again.

---

### Post by jnelson11 on 2011-01-24
After a span of almost a year and countless different ways of trying to get ubuntu 64 bit to connect to my juniper VPN, I have finally gotten it to work and the solution was something I would have never though of trying.  For those of you who are still unsuccessful with the mad-scientist script or get IVE errors, then you need to try the directions here: [http://wireless.siu.edu/install-ubuntu-64.htm](http://wireless.siu.edu/install-ubuntu-64.htm)

This has been the only solution that has worked for me and i think I almost jumped out of my chair when i was able to get network connect to work!

let me know if anyone needs any help.

good luck everyone!

---

### Post by jwingy on 2011-02-14
I've modified the script to accept hardcoded passwords from a profile if you choose to do so.  This is handy if you're using the -nogui option and need the script to automate connections.

Of course this isn't the most secure method of authenticating, but I'm sure some use cases will find this useful.

---

### Post by GolanTrevize on 2011-02-22
My solution for the problem: 

to cut a long story short: I can connect again. What I did was stopping apparmor:
```

sudo /etc/init.d/apparmor teardown

```Next step will be of course configuring apparmor correctly.

My problem was the same as described multiple times here on this thread. Error "SL0x12" while connecting via browser, no narport.txt when using the junipernc script.

So propably it is **not** a problem of the used jdk - which explains, why there was no difference in using openjdk, sun1.6.0.22 and now sun1.6.0.24.

So - if you got a "SL0x12" try disabling apparmor.

golan

---

### Post by kees on 2011-02-22
Please, never use "teardown". You should have ample details in "dmesg" to see which specific profile in AppArmor is causing you problems, and you can just disable that one profile itself without compromising your entire system's security. You cannot recover from "teardown" without restarting apparmor and every single program that has profiles defined (i.e. you might as well reboot).

---

### Post by sambrightman on 2011-02-26
I haven't yet tried the script from madscientist, but I have a couple of questions:

1) Is there something particular about the Juniper setup that requires the proprietary binaries and non-integrated setup? Why can't one add the right settings to built-in VPN support?
2) If the use of proprietary programs *is* required, can the necessary commands at least be integrated better with the existing system/desktop so that the VPN connection can be brought up and down as other connections are?

---

### Post by islanddancer on 2011-03-22
> **virtualscoop said:**
> The unpack error went away with "chmod u+x ncsvc".

In the script, there is this line:

 (cd "$_ncpath" && jar xf "$_jarfile" && [ -x "$_svc" ]) >> "$_errlog" 2>&1 \
            || die "Could not unpack Juniper Network Connect!"

Well, the -x was failing due to the ncsvc file in my case being not executable.

Still, with that I get the IVE error:

20080602221611.127751 ncui[9551] dsclient.info <-- 302 [https://***/url_default/welcome.cgi?p=failed](https://***/url_default/welcome.cgi?p=failed) (authenticate.cpp:168)
20080602221611.127865 ncui[9551] dsclient.info state: kStateError (dsclient.cpp:358)
20080602221611.128164 ncui[9551] ncapp.error Failed to connect/authenticate with IVE. Error 104 (ncapp.cpp:174)

The output of the first time run of madscientists script:

irfan@leibniz:~$ ./junipernc
Connecting to sslvpn.vmware.com port 443
Generating Certificate .... done.
Searching for ncsvc in current working directory
Searching for ncsvc in /home/irfan/.juniper_networks/network_connect done.
ncapp> Failed to connect/authenticate with IVE. Error 104
ncapp> Incorrect credentials. Please check the username/password/realm.

Anyone know how to get around the IVE error? I'm completely stuck.

I am seeing the same  error here and couldn't find how to fix, pls help!

---

### Post by islanddancer on 2011-03-22
> **osx424242 said:**
> Not the best instructions, but I managed to connect after getting that error.  I went back to the webpage I'm supposed to use to connect, logged in (username + RSA key password) there, and when the terminal window popped up and asked for the root password I closed that window.  Then the Network Connect window opened and I was connected (yes I verified it by connecting to an internal computer).

So... give that a shot.  My guess is that the junipernc script by The Wonderful and Amazing madscientist got nearly everything configured, and then the web interface added the final piece to the puzzle.  Tomorrow I'll ask on our internal forums if anyone knows if our Realm is something other than RSA.

Oh, also: when I ran junipernc and entered 123456 for my password, I got the same error.  So my problem might be anything in the username/password realm that is getting translated by the web interface.


I see the same IVE error 104,

how did you use junipernc script in your case here? did u use that
script?

---

### Post by nsk7even on 2011-04-20
Hello guys,

how can I use this junipernc_password_hack.sh script with proxy?

The system (Ubuntu Maverick) is configured to use the company proxies for all protocols, but I already encountered the necessity for application specific configuration (e. g. wget I think.. cannot remember for sure).

So do I have to configure the proxy somewhere else?


Other question: what is realm and what do I have to enter there?

Thanks in advance,
7even

---

### Post by CodeFooTyping on 2011-04-27
> **islanddancer said:**
> I see the same IVE error 104,

how did you use junipernc script in your case here? did u use that
script?

In the case of error 104, it could just be that you entered the relm incorrectly.  This seems to be case sensitive.  In my case there is a drop down with two choices and I have to enter the right one all UPPERCASE.

Of course when I get past that I still get error 10.

---

### Post by gsker on 2011-05-06
> **CodeFooTyping said:**
> In the case of error 104, it could just be that you entered the relm incorrectly.  This seems to be case sensitive.  In my case there is a drop down with two choices and I have to enter the right one all UPPERCASE.

Of course when I get past that I still get error 10.

I got error 10 until I added a -U option to the ncsvc lines in the junipernc file.  I got the url from the HTML code, 
[FONT="Courier New"]<form name="frmLogin" action="login.cgi"[/FONT]
I just made it the complete URL to the "login.cgi"

---

### Post by mynk on 2011-06-07
@gsker - I am not sure I understood you fully. I am getting the following error -

[FONT="Courier New"]$ junipernc 
Searching for ncsvc in current working directory
Searching for ncsvc in /home/mayankr/.juniper_networks/network_connect done.
Password: 
ncapp> Failed to connect/authenticate with IVE. Error 10
[/FONT]

I am assuming you are talking about the same issue here. I checked the junipernc file but could not figure out where you changed and what exactly you changed. Can you kindly elaborate?

I am hoping this is the last hurdle to get this script working on a 64 bit environment (11.04). I have been using 32 bit just because the vpn doesn't work. Never got the junipernc script to work on either 32 bitor 64 bit. Please advice.

Thanks in advance,
Mayank

---

### Post by LdK on 2011-06-08
Anyone knows how to set up proxy settings with mad scientist' script ?
thanks for helping me

---

### Post by LdK on 2011-06-08
> **LdK said:**
> Anyone knows how to set up proxy settings with mad scientist' script ?
thanks for helping me

I found a solution :
Add ```
-y "$PROXY" -z "$PROXYPORT"
``` at line 515 and 520 to  the mad scientist' script and add these informations to your profile file.
:D

ps: if you need you can add these following informations (obtained by this command '.juniper_networks/network_connect/ncsvc -help')

```
Proxy Options:
	-y, -proxy: 		Proxy server hostname or IP
	-z, -proxy-port: 	Proxy server port number
	-s, -proxy-user: 	Proxy server username
	-a, -proxy-pass: 	Proxy server password
	-d, -proxy-domain: 	Proxy server domain
```

---

### Post by backibaxter on 2011-06-08
In our company we need 3 things to login to the VPN
1. LDAP Username
2. LDAP Password
3. Pincode + Passcode

Is there anyone that knows how to do this with junipernc?

---

### Post by BoomerBrian on 2011-06-30
Hello,

I am trying to connect to our Juniper and it appears it can't handle the /its in the URL properly.

Below is the error I am getting. I have changed the domain name to protect the innocent.:D

Any help would be appreciated.


20110630105010.526731 ncsvc[4187] ncsvc.info New ncsvc log level set to 3 (nccommon.cpp:75)
20110630105010.533465 ncsvc[4187] ncsvc.error gethostbyname failed for host connect.acme.com/its
 (ncsvc.cpp:442)
Unable to connect to connect.acme.com/its

---

### Post by maclocke on 2011-07-01
Wow ... the script is awesome and works very well! I have an issue with it that I was able to resolve, but not in a "nice" way.

Once I'm logged in to the VPN, have network connect up and running, I can see the machines I need to work on via IP. Great! I thought to get DNS working as well, so I modified my dhclient.conf file.

The interesting thing that happens is that (it seems) the script causes resolv.conf to be overwritten with nameservers from the connected website. For a lot of people, that's probably fine. For me, I need many more nameservers (this connection spans many, many sites), a specific domain, and search. It's all in my dhclient.conf, but it doesn't get written to resolv.conf with the new connection. It does get the search field in, but that's useless without the domain and extra nameservers.

I wrote a resolv.conf by hand and put it in place. After that, everything works. If I log out and log back in, however (to the vpn), that gets reset, so I have to replace my resolv.conf any time I use this.

Ideas why it's not taking the info in the dhclient.conf? Maybe I don't know enough about that configuration file and there's a way to tell it specifically to use the information for this connection type?

Thanks for the script! I have a workaround for this problem and thought I'd post it for others (manually setting resolv.conf ... don't forget to back it up as dhclient.conf will overwrite it!), but thought I'd ask in case I'm missing something that would make everything better :)

---

### Post by Goliash on 2011-08-10
I have the same problem as Mynk. Running on Kubuntu 11.04 64bit.
```
ncapp> Failed to connect/authenticate with IVE. Error 10
```

---

### Post by Goliash on 2011-08-10
I will answer to myself. Luckily I have found a solution. It has to be added one parameter to ncsvc. Description is here: [http://kb.juniper.net/InfoCenter/index?page=content&id=KB15890](http://kb.juniper.net/InfoCenter/index?page=content&id=KB15890)
I modified my junipernc script and added this to command: -U “https://$HOST/launcher”

Code snippet:
```
 if $_java; then
        echo "$password" | "$JAVA" -jar "$_ncpath/NC.jar" -h "$HOST" -u "$USER" -f "$CERT" -r "$REALM" -U "https://$HOST/launcher" \
            || ok=false

    else
        # No GUI?  Just let the thing run in the background
        echo "$password" | "$_ncpath/ncsvc" -h "$HOST" -u "$USER" -r "$REALM" -f "$CERT" -U "https://$HOST/launcher" \
            || ok=false
    fi

```

---

### Post by ryan-au on 2011-08-17
Hi Guys,

My 'single click VPN' solution.

I tried many things from this thread a while back and never had much luck, so I went off on my own and figured out another solution which 'Just Works' (tm) for me.  I haven't wrapped it up and made it all pretty, but it may help someone.  I've used this on 10.04 upwards with NC 7.0R1 as delivered by default from our Juniper SA.

In our case, we have a Juniper SA2500 and multiple roles for most users in our default Active Directory realm.  Using NC.jar via CLI only works when one role is available, so I made a new realm for this purpose.  Once this realm is created, it provides another login URL such as [https://host.company.com/realm/](https://host.company.com/realm/)

On the SA under Users -> User Realms: I created a new realm called ncsvc with all the necessary mappings to AD to put users only in to one role.

I've then installed kdocker and gtk-led-askpass and have a small script which asks for my password, launches and then docks the window to the notification tray so it's out of the way.

To do this:
[LIST]
[*]Access the login page of your Juniper with firefox and export the SSL certificate to a local file.  Process: click the padlock -> View Certificate -> Details -> Export -> DER
[*]Login as normal and launch Network Connect to install the NC client
[*]Install kdocker and gtk-led-askpass
[*]Customise the script below and use it for connecting in the future.
[/LIST]
```
#!/bin/sh
# ncsvc is the single role realm created for this purpose
/usr/bin/java -jar ~/.juniper_networks/network_connect/NC.jar -h host.company.com -u 'username' -f ~/ssl-certificate.der  -r "ncsvc" -L 5 -p `gtk-led-askpass` -U https://host.company.com/ncsvc/ &
sleep 8
kdocker -i /usr/share/icons/gnome/16x16/categories/applications-internet.png -w `xwininfo -name "Network Connect" | grep "Window id" | awk '{print $4}'`

```

* only gotcha is don't drag the NC window around once it loads, as kdocker ain't the sharpest tool in the shed.  Just load it and click the new globe icon in the notification area to show/hide the NC window - it will hide itself initially though after a delay.

---

### Post by david lang on 2011-08-22
on ubuntu 11.04 and firefox 6 I've installed the 32 bit java and set update-alturnatives to use it (and restarted firefox), but when I go to the juniper and activate network connect from there a ps ax |grep java shows that it's running the openjdk java that's tied to the icedtea plugin. If I don't have this plugin I can't get the web page to start the java app.

I tried using the junipernc script, but in my case I have token authentication (on the Juniper web screen, there is no password entered on the first screen, then a second screen gives me a challenge that I type into the token and then type the response from the token into the we page before I am able to get logged in to the Juniper)

Is there any way to do this from the command line with something like juniperrc?

David Lang

---

### Post by david lang on 2011-08-24
It's very ugly, but you can create a 32 bit chroot sandbox and start the VPN from inside the sandbox and then use it on the main system

the steps to do this are ugly, so here is a close-to-right script to implement them all (this is taking what I did and making it into a script, there may be typos or such in it that I have not yet found, testing and feedback would be appreciated, as would any ideas of how to reduce the size of the sandbox and the time to create it)

first, use a normal 64 bit browser to login to the juniper and attempt to start the network connect, this will do the
installation (where it prompts you for a sudo password) and should create a directory tree, the key to checking that
this installed correctly it to look for the file .juniper_networks/network_connect/ncsvc and see that it is setuid
root.

this script creates a chroot sandbox with a minimal ubuntu installation in it. It then installes a handful of
additional packages that are needed (and the large number of dependancies for those files)

it does a bunch of mounts into the sandbox (these mounts would need to be done on every boot)

it then creates a script to work around firefox being dependant on DBUS (firefox still complains about not being able
to reach DBUS, but without this script it dies instead) and then it starts firefox

in firefox connect to the juniper, sign in, and launch network connect. there is one error prompt about being unable
to modprobe the tun drier, just click Ok and the tunnel should start.

the tunnel can be used by any software on the box, it doesn't hae to be inside the sandbox (that is the reason for
making /etc/resolv.conf be a symlink into the sandbox.

there are a number of times in the process that the user will be prompted for things, so it is not an unattended
install.



#!/bin/bash
export SANDBOX=sandbox2
export INSALL_USER=dlang
debootstrap --arch=i386 natty $SANDBOX

mount -B /dev $SANDBOX/dev
mount -B /var/run/dbus $SANDBOX/var/run/dbus
mount none -t proc $SANDBOX/proc
mount none -t devpts $SANDBOX/dev/pts
if [ -e /etc/resolve.conf.juniper.save ]
then
  echo "already saved resolv.conf"
else
  mv /etc/resolv.conf /etc/resolve.conf.juniper.save
  ln -s /home/$INSALL_USER/$SANDBOX/etc/resolv.conf /etc/resolv.conf
fi
cd $SANDBOX
chroot . bash -
export LANG=C
adduser --uid 1000 $INSALL_USER
adduser $INSALL_USER adm
adduser $INSALL_USER sudo
exit
cp -pR /home/$INSALL_USER/.juniper_networks/ home/$INSALL_USER
cp /etc/apt/sources.list $SANDBOX/etc/apt
chroot . bash -
export LANG=C
apt-get update
apt-get install firefox
apt-get install libcanberra-gtk-module
apt-get install sun-java6-plugin
su - $INSALL_USER
cat <<EOF >fixdbus
#!/bin/bash

exportDbus () {
    # Get the pid of nautilus
    nautilus_pid=\$(pgrep -u \$LOGNAME -n firefox-bin)

    # If nautilus isn't running, just exit silently
    if [ -z "\$nautilus_pid" ]; then
echo "exiting"
    exit 0
    fi

    # Grab the DBUS_SESSION_BUS_ADDRESS variable from nautilus's environment
    eval \$(tr '\0' '\n' < /proc/\$nautilus_pid/environ | grep '^DBUS_SESSION_BUS_ADDRESS=')

    # Check that we actually found it
    if [ -z "\$DBUS_SESSION_BUS_ADDRESS" ]; then
    echo "Failed to find bus address" >&2
    exit 1
    fi

    # export it so that child processes will inherit it
    export DBUS_SESSION_BUS_ADDRESS
}


exportDbus
\$@
EOF
chmod 700 fixdbus 
./fixdbus firefox -no-remote --display=localhost:0 &

---

### Post by dvo on 2011-08-26
I also had quite some trouble getting Juniper to run on a new 64-bit Linux installation (Ubuntu 11.04 "Natty").
Using a 32-bit chroot works, but is quite cumbersome.

After a lot of investigation and trial and error, I realized that the - *only* - problem is that [FONT="Courier New"]~/.juniper_networks/network_connect/libncui.so[/FONT] is a 32-bit library, thus it cannot be used by 64-bit Java.
**Shame on Juniper** that they do not provide a 64-bit version of the library! This would be the only thing they'd need to do to support 64-bit Linux systems out-of-the box.

First note that JNC will only work with the Java Runtime Environment from Sun/Oracle. In case your installation uses another JRE as default, you may use the command [FONT="Courier New"]sudo update-alternatives --config java[/FONT] to switch to java-6-sun. 

My workaround for a 64-bit installation is as follows.

Additionally install the 32-bit variant of Java: [FONT="Courier New"]aptitude install ia32-sun-java6-bin[/FONT] .
Assuming that Java is installed at [FONT="Courier New"]/usr/lib/jvm/java-6-sun/jre/bin/[/FONT] and at [FONT="Courier New"]/usr/lib/jvm/ia32-java-6-sun/jre/bin/[/FONT] ,
rename [FONT="Courier New"]/usr/lib/jvm/java-6-sun/jre/bin/java[/FONT] as [FONT="Courier New"]/usr/lib/jvm/java-6-sun/jre/bin/java.orig[/FONT] and 
save the following shell script as [FONT="Courier New"]/usr/lib/jvm/java-6-sun/jre/bin/java[/FONT] : 

```

#!/bin/bash
if [ $3x = "NCx" ]
then
    /usr/lib/jvm/ia32-java-6-sun/jre/bin/java "$@"
else
    /usr/lib/jvm/java-6-sun/jre/bin/java.orig "$@"
fi

```

This script should be readable and executable for all. It will call the 32-bit variant of Java when launching Network Connect (and otherwise call the default 64-bit variant).

---

### Post by david lang on 2011-08-26
that works and is MUCH easier than dealing with the chroot.

thanks

---

### Post by PhartSmellah on 2011-08-28
@dvo,

You are an angel from above. So simple, and it just works now.

I'd like to ask for one more thing: at the moment, the ncLinuxApp.jar file only executes properly if I run it through the browser plugin.
When I try:
```
java -jar ncLinuxApp.jar
```
I get:
```
Failed to load Main-Class manifest attribute from
ncLinuxApp.jar
```

Have any idea what's missing?

---

### Post by dvo on 2011-08-28
> **PhartSmellah said:**
> @dvo,

You are an angel from above. So simple, and it just works now.


Pleased to hear!

> 
I'd like to ask for one more thing: at the moment, the ncLinuxApp.jar file only executes properly if I run it through the browser plugin.
When I try:
```
java -jar ncLinuxApp.jar
```
I get:
```
Failed to load Main-Class manifest attribute from
ncLinuxApp.jar
```

Have any idea what's missing?

I also tried this, and I'd guess that ncLinuxApp.jar is simply not intended to be called independently. 
Yet NC.jar is; it is called for instance as follows, where the "ia32-" part is due to my above little script:
```

/usr/lib/jvm/ia32-java-6-sun/jre/bin/java -classpath /home/david/.juniper_networks/network_connect/NC.jar NC -h ura-emea.siemens.com -L 0 -l 0 -n -t -x

```

---

### Post by PhartSmellah on 2011-08-28
@dvo,

Thanks for the quick reply once more!

Here's what happened when I tried your script:
```
ak@ak-desktop:~$ /usr/lib/jvm/ia32-java-6-sun/jre/bin/java -classpath /home/ak/.juniper_networks/network_connect/NC.jar NC -h vpn.companyvpn.com -L 0 -l 0 -n -t -x
Searching for ncsvc in current working directory
Searching for ncsvc in /home/ak/.juniper_networks/network_connect done.
[>/home/ak/.juniper_networks/network_connect/ncsvc<] [>-l<] [>0<] [>-L<] [>0<] [>-n<] [>-t<] [>-x<] indx = 6 
reading form stdin .. 
No data within 30 seconds.
Password: *<TYPED MY PASSWORD FOR THE VPN>*
usage: ncui -h host -u user -p passwd -r realm -f cert_file [-l log_level] [-L log_level]
       ncui -h host -c cookies -f cert_file [-l log_level] [-L log_level] [-U sign_in_url]
       ncui -v
    log_level : 0 : Log Critical messages only
                1 : Log Critital and Error messages
                2 : Log Critital, Error and Warning messages
                3 : Log Critital, Error, Warning and Info messages(default)
                4 : Log All Verbose messages
                5 : Log All messages
ak@ak-desktop:~$
```

Received "Invalid parameters" error.

As an eager Linux n00b :) I'd really like to understand what's going on here.
I'm trying to understand the switches you used, can you explain them? Maybe through that I will find what's missing.

---

### Post by dvo on 2011-08-28
> **PhartSmellah said:**
> @dvo,

Thanks for the quick reply once more!

Here's what happened when I tried your script:
[...]

```

reading form stdin .. 
No data within 30 seconds.

```

[...]

As an eager Linux n00b :) I'd really like to understand what's going on here.
I'm trying to understand the switches you used, can you explain them? Maybe through that I will find what's missing.

My switch script simply forwards the parameters that it receives (apparently being called from ncLinuxLauncher.jar). 
AFAICS, the NC.jar waits for credential input from the browser to be provided via a socket or STDIN.
Sorry, since I am not a JNC expert, I cannot provide more detail.

---

### Post by Eccentric.Ash on 2011-08-29
> **dvo said:**
> I also had quite some trouble getting Juniper to run on a new 64-bit Linux installation (Ubuntu 11.04 "Natty").
Using a 32-bit chroot works, but is quite cumbersome.

After a lot of investigation and trial and error, I realized that the - *only* - problem is that [FONT=Courier New]~/.juniper_networks/network_connect/libncui.so[/FONT] is a 32-bit library, thus it cannot be used by 64-bit Java.
**Shame on Juniper** that they do not provide a 64-bit version of the library! This would be the only thing they'd need to do to support 64-bit Linux systems out-of-the box.


dvo, you are a lifesaver!!!

I was using the method mentioned  **_*[by Scott Deming]("http://makefile.com/.plan/2009/10/juniper-vpn-64-bit-linux-an-unsolved-mystery/")*_** and it was working fine until my company decided to upgrade to "Junos Pulse Secure Access Service". That upgrade broke the little workaround by Scott.

Your method is elegant, simple and flawless!! It works for me. Thanks a lot for your efforts, I am sure it will help a lot of people!!

---

### Post by toey on 2011-09-21
THANKS! :) works a treat

---

### Post by jayanm on 2011-09-26
Thanks.. this worked great for me too. The java 32/64 script just did the magic.

---

### Post by Vithal K on 2011-09-27
Angel is absolutely right! Thanks a lot, dvo

---

### Post by madscientist on 2011-10-31
Hi all; I'm surprised that you were seeing an issue with 32bit/64bit with my script (or were you not using my script)?

A while ago I added code to my script to detect this problem and suggest the solution; if you try to invoke the script and it can only find a 64bit java it will give you an error message:

```
The Network Connect GUI needs a 32-bit Java
Ignoring 64-bit Java from $PATH (/usr/bin/java)
```

Then it will give you a file chooser dialog asking you to find a 32bit java.  If you quit or cancel it will say:

```
Cannot locate valid 32-bit Java.
Please install it with your package manager
or run junipernc with the '-nojava' flag.
```

So, at least for junipernc, you don't need to replace the java application.  Once the script finds a 32bit java it will remember where it is and always use it when invoking Network Connect.

The problem with replacing the java binary with a script like this is that when your package updates it will overwrite that binary and you'll have to do it again.  Personally I don't like that solution.

Also I just put up a new version of the script that allows a special URL for connections, for those that need it.

---

### Post by Rkcrawl on 2011-10-31
Anyone have any success with this script on 11.10 and Firefox 7.0.1?
I had jnc working well until the 11.10 upgrade and am now having trouble getting it working again.

The script is called and uses the 32 bit version of java, but I don't get the nc dialog, nor a tunnel.

---

### Post by madscientist on 2011-10-31
> **Rkcrawl said:**
> Anyone have any success with this script on 11.10 and Firefox 7.0.1?
I had jnc working well until the 11.10 upgrade and am now having trouble getting it working again.

The script is called and uses the 32 bit version of java, but I don't get the nc dialog, nor a tunnel.If you use my script then you don't use FireFox at all so the version of FireFox should not be an issue.  I'm not using the latest Ubuntu yet but so far I've never seen a new version of Ubuntu break things.

What exactly happens?  The script seems to be running (you don't get an exit dialog) but you don't have a tunnel?  Or something else?

I've just uploaded a new version 1.16 which dumps the Network Connect output to a log file in /tmp.

Also you can try running it from the CLI and see if anything is printed.  And you can try running with the "-nojava" and/or "-nogui" options (-nogui implies -nojava) and see if you get any more information on what the issue is.

---

### Post by Rkcrawl on 2011-10-31
> **madscientist said:**
> If you use my script then you don't use FireFox at all so the version of FireFox should not be an issue.  I'm not using the latest Ubuntu yet but so far I've never seen a new version of Ubuntu break things.

What exactly happens?  The script seems to be running (you don't get an exit dialog) but you don't have a tunnel?  Or something else?

I've just uploaded a new version 1.16 which dumps the Network Connect output to a log file in /tmp.

Also you can try running it from the CLI and see if anything is printed.  And you can try running with the "-nojava" and/or "-nogui" options (-nogui implies -nojava) and see if you get any more information on what the issue is.

By script, I was referring to the script posted by dvo one page back.  However I did try your script earlier today, I'll give it another spin and provide feedback.  Thanks.

---

### Post by Rkcrawl on 2011-10-31
> **Rkcrawl said:**
> By script, I was referring to the script in the original post.  However I did try your script earlier today, I'll give it another spin and provide feedback.  Thanks.

SOLVED:  The script in this thread posted by dvo works on ubuntu 11.10, AFTER, I installed ia32-libs:

"sudo apt-get install ia32-libs"

32-bit java was unhappy about a library in the wrong ELF format: libXtst.

Madscientist, I did give your script a try and it is what clued me into the library issue.  It still failed after I updated the library, but that is likely because I hadn't configured the realm.

---

### Post by dvo on 2011-11-03
> **madscientist said:**
> Hi all; I'm surprised that you were seeing an issue with 32bit/64bit with my script (or were you not using my script)?

A while ago I added code to my script to detect this problem and suggest the solution;

Hi Madscientist, I was not aware that your your script solved the 32-/64-bit issue in essentially the same way as I did with my simple switcher script. 

> **madscientist said:**
> if you try to invoke the script and it can only find a 64bit java it will give you an error message:

```
The Network Connect GUI needs a 32-bit Java
Ignoring 64-bit Java from $PATH (/usr/bin/java)
```

Then it will give you a file chooser dialog asking you to find a 32bit java.

I just downloaded the latest version of your script and gave it a try again. At first, I tried giving the full path of the Java binary itself, but then I found the file chooser disabling the "Ok" button, until I realized that one is supposed to provide the path of the 32-bit JRE, which in my case is /usr/lib/jvm/ia32-java-6-sun/jre .

> **madscientist said:**
> So, at least for junipernc, you don't need to replace the java application.  Once the script finds a 32bit java it will remember where it is and always use it when invoking Network Connect.

Correct. Yet your script does not work in cases like mine where the user is not authenticated by username, realm and password, but using a hardware token (smart card). In such cases, the co-operation of the browser is needed, in order to access the smart card. (Ok, in principle one could access the smart card also directly, e.g. using an openssl plugin, but this is non-trivial.)

> **madscientist said:**
> The problem with replacing the java binary with a script like this is that when your package updates it will overwrite that binary and you'll have to do it again.  Personally I don't like that solution.

I am aware of this minor drawback of my script, but on the other hand this is the only solution I found that both supports smart card based user authentication and is straightforward to implement.

Regards, David
 
[http://ddvo.net/](http://ddvo.net/)

---

### Post by AutoStatic on 2011-11-18
Hello all,

Anybody any idea where these errors come from?

```
20111118202721.627033 ncsvc[p4263.t4264] worker.error connect to myhostname:443 failed. IVE returned error 20001069 (ncp_dsssl.cpp:1062)
20111118202721.627267 ncsvc[p4263.t4263] ncphandler.info control channel disconnected due to error 20001069, reconnecting (ncphandler.cpp:335)
```

These errors appear on both 10.04 and 11.10 with Sun Java 6 (10.04) and Oracle Java 7 (11.10) when using the junipernc script or running ncsvc/NC.jar directly.

> ./ncsvc --version
Juniper Network Connect Server for Linux.
Version         : 7.1
Release Version : 7.1-0-Build19525
Build Date/time : Oct 11 2011 00:51:15 
Copyright 2001-2010 Juniper Network

Thanks in advance!

Jeremy

Edit: JSAM is disabled so I'm not allowed to use the Network Connect functionality.

---

### Post by joseluisbcn on 2011-11-21
Hello.

I am the system administrator in one university.

We would need to use the Network Connect with Ubuntu 10.04 clients. In certain machines it works without problems but in others, it fails. When I use the script Mad Scientist the popup says "Connecting to NCSVC" but doesn't say anymore. The timeout arrives at 22 seconds and it disappears, saying "Aborted". No log to the user, and the last lines in "~/.juniper-networks/ncui.log" are:

 20111121205922.185223 ncui[p6343.t6366] dsclient.info --> GET /dana/home/starter0.cgi?check=yes (authenticate.cpp:179)
20111121205922.600307 ncui[p6343.t6366] dsclient.info <-- 200  (authenticate.cpp:211)
20111121205922.600501 ncui[p6343.t6366] authStateLogin.info starter0.cgi has asked for tz_offset parameter (authenticate.cpp:372)
20111121205922.600637 ncui[p6343.t6366] authStateLogin.info starter0.cgi has asked for clienttime parameter (authenticate.cpp:379)
20111121205922.600802 ncui[p6343.t6366] dsclient.info --> POST /dana/home/starter0.cgi?check=yes (authenticate.cpp:179)
20111121205922.948673 ncui[p6343.t6366] dsclient.info <-- 302 /dana/home/starter.cgi (authenticate.cpp:211)
20111121205922.948778 ncui[p6343.t6366] dsclient.info --> GET /dana/home/starter.cgi (authenticate.cpp:179)
20111121205923.300980 ncui[p6343.t6366] dsclient.info <-- 200  (authenticate.cpp:211)
20111121205923.301123 ncui[p6343.t6366] dsclient.info state: kStateAuthenticated (dsclient.cpp:376)
20111121205946.352102 ncui[p6343.t6366] IpcConn.error connect failed with error 110 (ncipc.cpp:199)

However, we can see the connection is opened (for exemple, we can do the logout or if we try another, the system says there is another connection).

We have also tested with several browsers (Firefox, Chrome and Chromium), with several users in the same client, with differents versions of Java, and the result is the same. But if we test with one Windows in the same machine, it works.

Can you help us?

Thanks in advance.

---

### Post by userdce on 2011-11-23
This is also good way to install on 64bit:

[http://wireless.siu.edu/install-ubuntu-64.htm](http://wireless.siu.edu/install-ubuntu-64.htm)

---

### Post by jittopjose on 2011-12-02
Hi,
I also strugling to configure this in my Ubuntu 11.10 netbook. any body please send me the file libstdc++2.10-glibc2.2_2.95.4-24_i386.deb via mail. I searched in many places. but couldnt get. Plese help. My id  is jittopjose[at]gmail.com

thanks.
Jitto P.Jose

---

### Post by rebelbuttmunch on 2011-12-14
Not sure if this is the correct place to ask but frequently my juniper client seems to hang. I only notice when my connections (skype/ssh) fail. Then I have a look and the Bytes Received is static and there is a small increase in the Bytes Sent. I have to 'sign out' and sign in again.

I dont know how to even diagnose the problem.

Anyone with advice?

Thanks!

Sorry: some more information:
Im on Debian 6.0.3 
NC V7.1
jkd 1.6.0_26

I had the same problems when I was on Ubuntu

---

### Post by SimonSaysYes on 2011-12-15
Hello everyone,
I recently installed Ubuntu 11.10 (32-bit) and would like to log into my computer at work. Whenever I go to connect however, I am prompted to install "NetworkConnectClientInstall.exe" which is obviously not what I want. But I have been unable to locate ncLinuxApp.jar anywhere online and without that I feel like I am stuck.
So I was hoping someone could post a link to a download or maybe attach it in a post. I have looked the script made by madscientist and hopefully I can get it to work if I can get that Network Connect Client for linux.

Thanks!

Edit: I was able to get the ncLinuxApp.jar (thanks to [http://www.rz.uni-karlsruhe.de/~iwr91/juniper/](http://www.rz.uni-karlsruhe.de/~iwr91/juniper/)) but when I run it, it won't do anything. Frustrating.

---

### Post by Vithal K on 2011-12-20
I know this thread is more than 4 years old! However, it saved the day for me now. Thank you, mad scientist

---

### Post by mynk on 2012-01-17
I have finally been able to get the darn thing work on 64 bit Linux. I figured that the IVE 10 error was due to a host checker enabled and recently this has been enabled across all sites making it impossible to get mad scientist's script work. A colleague got it working wit 32 bit broswer and 32 bit plug in just like it works on 32 bit Linux. I followed his advice and got it working.

I have jotted it down here -

[http://techydodo.wordpress.com/2012/01/17/cracking-the-juniper-network-connect-problem-on-linux-64-bit/](http://techydodo.wordpress.com/2012/01/17/cracking-the-juniper-network-connect-problem-on-linux-64-bit/)

Hope this helps,
Mynk

---

### Post by dankegel on 2012-01-22
mynk's solution looks good, though it relies on setting up a strange browser to get around the fact that browsers aren't biarch.

Here's a script that sets up a 32 bit Firefox with 32 bit Sun Java in a chroot jail just to make Juniper Network Connect happy on 64 bit Ubuntu 11.10.
It takes up 832 MB of hard drive space, which is a bit much, but it does seem to work.

[http://kegel.com/linux/web32.sh.txt](http://kegel.com/linux/web32.sh.txt)

---

### Post by frankencat on 2012-01-26
I have set up Juniper and Java according to posts by mad scientist mynk and others (thanks) and I still can't get it connected. It runs but when I attempt to login I get "Server Disconnected" message. Anybody else see this? Thanks -Frank

---

### Post by boy18nj on 2012-02-20
Most of the posts on google say how to access VPN using juniper network connect. They assume every company would provide jar files required to setup juniper network connect.
They say you go to your VPN site, it would by default install in your home directory you should now have “.juniper_networks”.

At least not in my case, basically i am looking how to install juniper network connect on my ubuntu 11.10 machine. Rest things later how to connect. First i want to know how to get all necessary stuff to install “.juniper_networks” on my machine and from which site should i download?

Thanks

---

### Post by maclocke on 2012-03-01
First off ... awesome. This has me up and running in Ubuntu 11.10 perfectly (had to install ia32-libs first, but no other hiccups).

Only issue I'm having is figuring out resolv.conf issues. 

For my company, I have to add "supersede domain-name" and "prepend domain-name-servers" to my dhclient.conf for things to work nicely.

However, when NetworkConnect gets the network settings, it appears to ignore dhclient.conf and rewrites resolv.conf ... presumably from the information retrieved from the VPN DNS.

Why is it not looking at dhclient.conf, and how can I get it to add these extra domain names and DNS's to the resolv.conf?

Copying my old resolv.conf over the new one generated by NetworkConnect works just fine, but is certainly an annoyance.

---

### Post by jonimalabarea on 2012-03-06
I've tried dankegel solution with web32.sh shell scripts and it works partially. I mean, I'm able to start the VPN but I can only access web pages using the same web browser that starts Network Connect (in this case firefox).
For example, I need to connect to a server via ssh/telnet but even though the tun interface is configured the routing table and resolv.conf are not modified.

My question is, are you able to open the VPN over ubuntu64 and use the VPN outside from the web browser?



> **dankegel said:**
> mynk's solution looks good, though it relies on setting up a strange browser to get around the fact that browsers aren't biarch.

Here's a script that sets up a 32 bit Firefox with 32 bit Sun Java in a chroot jail just to make Juniper Network Connect happy on 64 bit Ubuntu 11.10.
It takes up 832 MB of hard drive space, which is a bit much, but it does seem to work.

[http://kegel.com/linux/web32.sh.txt](http://kegel.com/linux/web32.sh.txt)

---

### Post by jonimalabarea on 2012-03-14
I discovered why the web32 didn't work fully. The file /etc/resolv.conf is not updated because the one that web32 script update is the <chroot-home>/etc/resolv.conf (in my case /var/chroot/web32/etc/resolv.con). After applying the same changes to /etc/resolv.conf the vpn works perfectly.

> **jonimalabarea said:**
> I've tried dankegel solution with web32.sh shell scripts and it works partially. I mean, I'm able to start the VPN but I can only access web pages using the same web browser that starts Network Connect (in this case firefox).
For example, I need to connect to a server via ssh/telnet but even though the tun interface is configured the routing table and resolv.conf are not modified.

My question is, are you able to open the VPN over ubuntu64 and use the VPN outside from the web browser?

---

### Post by poomalairaj on 2012-03-28
recently posted an article about juniper on ubuntu 11.10.
Hope this helps [http://blog.poomalairaj.com/juniper-network-connect-ubuntu-11-10/](http://blog.poomalairaj.com/juniper-network-connect-ubuntu-11-10/)

---

### Post by david lang on 2012-03-28
In Ubuntu 12.10 there are a couple of things that have happened that have broken dvo's fix.

1. due to a java vunerability that Oracle is not going to fix, they have removed the real sun java and only have openjdk

2. the mulitlib transition has eliminated the ia32-* packages

any ideas on how to get things working again?

---

### Post by vivace on 2012-04-08
I had it working in like 10.04 but then something happened and it stopped. According to the documentation i am reading the -nojava option should work but it doesnt i just get a prompt asking for my passcode and then immediately
 
VPN has exited successfully.

    Would you like to restart the VPN connection?

i hate having to boot into windows to use remote desktop.

---

### Post by ariva on 2012-05-06
> **david lang said:**
> In Ubuntu 12.10 there are a couple of things that have happened that have broken dvo's fix.

1. due to a java vunerability that Oracle is not going to fix, they have removed the real sun java and only have openjdk

2. the mulitlib transition has eliminated the ia32-* packages

any ideas on how to get things working again?

I could install gcc-multilib even with ia32-libs package installed. Which package brokes the multilib transition?
As  from PPA you can get old version (i don't remember exactly, but  propably update 26), I have downloaded and installed latest java (update  32) manually (both 64 and 32bit) and put them in separate folders.
Then i just invoke update-alternatives for java binary and java plugin for mozilla.
  Java 32bit: /usr/bin/java java /serwis/jre1.6.0_32_32bit/
  Java 64bit: /usr/bin/java java /serwis/jre1.6.0_32/

[COLOR=Navy][I]sudo update-alternatives --install /usr/bin/java java /serwis/jre1.6.0_32/bin/java 100
sudo update-alternatives --install /usr/lib/mozilla/plugins/libnpjp2.so  mozilla_java_plugin /serwis/jre1.6.0_32/lib/amd64/libnpjp2.so 100[/I][/COLOR]

And then ive switched dvo's script with 64bit java binary:

[COLOR=Navy][I]#!/bin/bash
if [ $3x = "NCx" ]
then
    /serwis/jre1.6.0_32_32bit/bin/java "$@"
else
    /serwis/jre1.6.0_32/bin/java.orig "$@"
fi
  [/I][/COLOR]
Hope, that helps.
Thanks MadScientist and dvo for solution!

---

### Post by ETecoli on 2012-05-07
Hey everyone... I've been ghosting this thread for a while, trying to find a method to get Juniper's network connect to run on Ubuntu 10.11 (I shudder what will happen after I update to the LTS).

Anyway, my problem is that, unlike most of you, my employer's web page doesn't prompt me to install Juniper's software via a java prompt. Instead I just get directed to an internal web site after a login. So there's still the option of doing a manual install from Juniper's ncui RPM package. Though they don't support linux.

I'm trying to install network connect manually via alien and its even listed in the software manager. But, this doesn't create the  ~/.juniper_networks/ directory. And I'm not sure how [or what] to execute. I feel like I'm missing some crucial component here.

Any tips for getting net connect to work without the browser?

Thanks!

---

### Post by acardona on 2012-05-12
> **vivace said:**
> I had it working in like 10.04 but then something happened and it stopped. According to the documentation i am reading the -nojava option should work but it doesnt i just get a prompt asking for my passcode and then immediately
 
VPN has exited successfully.

    Would you like to restart the VPN connection?

i hate having to boot into windows to use remote desktop.
I have the same error that vivace sees, but in Ubuntu 12.04 LTS: the remote server logs me out immediately. Is there any known solution?

If the error is related to the resolv.conf being rewritten, does editing /etc/dhcp/dhclient.conf help, as described earlier in this thread but for dhcp3? Ubuntu has changed a bit its files under /etc. (EDIT: I tried removing the domain-name and the domain-name-servers, restarting the wireless, and it didn't work).

Thank you for any hints!

EDIT: found more info here:
[http://holyarmy.org/2009/06/vpn-on-ubuntu-linux-with-juniper-network-connect/](http://holyarmy.org/2009/06/vpn-on-ubuntu-linux-with-juniper-network-connect/)
... but now I get "Unable to connect to IVE". Any hint on what that means?

Apparently the -U "https://$HOST" has to be modified with a /launcher, but it is not clear to me where or how in the junipernc script. Help appreciated.

---

### Post by madscientist on 2012-05-12
If you are having failures connecting, look at the log file (~/.juniper_networks/network_connect/ncsvc.log) and see if anything interesting is there.

If you need a URL instead of a simple hostname, just type the full URL into the dialog box (that's why it asks for "**URL** or server", not just the server) starting with http...

---

### Post by madscientist on 2012-05-13
Sigh.  After hours and hours of frustration I've figured out why my new installation on Ubuntu 12.04 was not working.

I've uploaded a new version (1.30) of the script to [my website]("http://mad-scientist.net/juniper.html").  In addition to some defensive programming to avoid the problem I had I've also added support for creating a new menu item to invoke Network Connect VPN in any desktop that supports the Freedesktop standard (which is pretty much all of them these days I believe).  After you run the new version of the script for the first time you should see a new menu item under "Internet" or "Networking" or similar in your menu hierarchy.  You can drag it to your Panel or Launcher etc. and use that to start your VPN.

There is also a new command-line option, [FONT="Courier New"]--kill[/FONT], which lets you bring down the VPN from the CLI.  And, if your WM supports it, there's an alternate action on the menu item to stop the VPN.

Have fun, and let me know if I broke anything...

---

### Post by netplumbers on 2012-05-18
I'm having incredible difficulty getting the juniper client to run on one of my machines.  It works fine on my laptop (also, fully up-to-date kubuntu precise 64 bit) but fails on my main desktop.

I'm using the current version of madscientist's script (Thank you).  And have installed and configured to use the 32 bit java 7 jdk from oracle.

My network connect version is:

Juniper Network Connect Server for Linux.
Version         : 6.5
Release Version : 6.5-0-Build15551
Build Date/time : Apr 10 2010 11:14:05 
Copyright 2001-2008 Juniper Networks

In the ncsvc.log I see:

20120516153254.912380 ncsvc[p10000.t10000] dsclient.info state: kStateAuthenticated (dsclient.cpp:368)
20120516153254.912475 ncsvc[p10000.t10000] IpcConn.error bind failed to port 4242. Error 98 (ncipc.cpp:64)
20120516153254.914075 ncsvc[p10000.t10000] IpcConn.error recv failed with errno 98 (ncipc.cpp:259)

I've spent hours on this and I can't figure it out.  Help!!
Thanks,
Jon

---

### Post by madscientist on 2012-05-18
Hm.  I don't know what "Error 98" means.

Maybe that port is used by something else?  Run: ```
sudo netstat -lntp | grep 4242
``` and see if some other program is bound to/listening on that port already.

---

### Post by netplumbers on 2012-05-18
> **madscientist said:**
> Hm.  I don't know what "Error 98" means.

Maybe that port is used by something else?  Run: ```
sudo netstat -lntp | grep 4242
``` and see if some other program is bound to/listening on that port already.

Thank you for the kick in the head.  That should have occurred to me.  Crashplan was also listening on that port (probably a java default).
Now it works - at least for a brief test.
Thanks again.

---

### Post by tagarap on 2012-05-25
First of all THANK You very much for your effort. :guitar:

I managed to get it working on Ubuntu 12.04 32.

But there is one catch...

Is it possible to use your script from behind proxy ? :confused:

If the connection in direct, no problem at all...
But my network must be routed through proxy and I can't get the script to work...:P

Thanks for your attention.

---

### Post by yopology on 2012-06-01
I try to set up juniper vpn following Mad scientist's instruction in Ubuntu 12.04 64-bit but running into problem.  I got an error message "Invalid Credentials" when connecting. The ncui.log gives the following error message: 

20120601162348.464931 ncui[p6632.t6655] dsclient.info state: kStateSignin (dscli
ent.cpp:248)
20120601162348.465032 ncui[p6632.t6655] dsclient.info --> GET /dana-na/auth/%28p
ublic%29url_default/welcome.cgi (authenticate.cpp:162)
20120601162348.480670 ncui[p6632.t6655] dsclient.info <-- 302 [https://vpn.unh.ed](https://vpn.unh.ed)
u/dana-na/auth/welcome.cgi (authenticate.cpp:194)
20120601162348.480771 ncui[p6632.t6655] dsclient.info state: kStateWelcome (dscl
ient.cpp:256)
20120601162348.480836 ncui[p6632.t6655] dsclient.info --> GET /dana-na/auth/welc
ome.cgi (authenticate.cpp:162)
20120601162348.565937 ncui[p6632.t6655] dsclient.info <-- 302 [https://vpn.unh.ed](https://vpn.unh.ed)
u/ (authenticate.cpp:194)
20120601162348.566078 ncui[p6632.t6655] dsclient.info state: kStateLogin (dsclie
nt.cpp:288)
20120601162348.566150 ncui[p6632.t6655] dsclient.info --> POST /dana-na/auth/log
in.cgi (authenticate.cpp:162)
20120601162348.656109 ncui[p6632.t6655] dsclient.info <-- 302 [https://vpn.unh.ed](https://vpn.unh.ed)
u/dana-na/auth/url_default/welcome.cgi?p=failed (authenticate.cpp:194)
20120601162348.656265 ncui[p6632.t6655] dsclient.error state login failed, error
 104 (dsclient.cpp:290)
20120601162348.656717 ncui[p6632.t6655] ncapp.error Failed to connect/authentica
te with IVE. Error 104 (ncapp.cpp:179)

I am a newbie in Ubuntu, and any help will be greatly appreciated.

---

### Post by xwilliam on 2012-06-03
thanks a lot mad scientist...I was becoming mad too.

And my co-worker is still not able to use juniper on his mac. Loving this

For those who have a 64bit like me. Follow this instruction for java i386 installation (I am not sure that someone have already post it....I was too nervous in reading the post):

[http://askubuntu.com/questions/126682/install-32bit-java-openjdk-on-64bit-ubuntu-12-04](http://askubuntu.com/questions/126682/install-32bit-java-openjdk-on-64bit-ubuntu-12-04)

cheers

---

### Post by yopology on 2012-06-03
Thanks for the input. I actually have the 32-bit java installed, both OpenJDK and Oracle give the same error. :(

---

### Post by yopology on 2012-06-04
After googling around, the method in this post works:

[http://ubuntuforums.org/showthread.php?p=11189826#post11189826%22](http://ubuntuforums.org/showthread.php?p=11189826#post11189826%22)

---

### Post by tonyuprm on 2012-06-06
Hi all,

I have successfully used Network Connect based on DVO's script in Ubuntu 12.04 Precise Pangolin 64 bit.

First of all one needs Sun Java 1.6 32 and 64 bit versions. These versions are no longer supported ny Ubuntu but one can find them through oracle.

[http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u32-downloads-1594644.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u32-downloads-1594644.html)

The files to download are: 
jdk-6u32-linux-i586.bin
jdk-6u32-linux-x64.bin

Now place them in /usr/lib/jvm
[I]sudo cp jdk-6u32-linux-i586.bin /usr/lib/jvm
sudo cp jdk-6u32-linux-x64.bin /usr/lib/jvm[/I]

Now one must install the 32 bit version and change the name of the directory:
[I]cd /usr/lib/jvm
sudo chmod a+x jdk-6u32-linux-i586.bin
sudo ./jdk-6u32-linux-i586.bin
sudo mv jdk1.6.0_32/ i32jdk1.6.0_32
sudo chmod a+x jdk-6u32-linux-x64.bin
sudo ./jdk-6u32-linux-x64.bin[/I]

Now both java versions are installed. Now based on DVO go to:
[I]cd jdk1.6.0_32/jre/bin/
sudo mv java java.orig[/I]

Now add the java file with:
*sudo vi java*

```

#!/bin/bash
if [ $3x = "NCx" ]
then
    /usr/lib/jvm/i32jdk1.6.0_32/jre/bin/java "$@"
else
    /usr/lib/jvm/jdk1.6.0_32/jre/bin/java.orig "$@"
fi

```The last thing is to set the firefox plugin:

[I]rm ~/.mozilla/plugins/libnpjp2.so
ln -s /usr/lib/jvm/jdk1.6.0_32/jre/lib/amd64/libnpjp2.so ~/.mozilla/plugins/[/I]

This should get NC to work on your Ubuntu 12.04 64 bit!
 
Great job DVO!

Thanks,

Tony

---

### Post by stupid_for_a_file on 2012-06-26
Dear All,

I have tried to get this working on 10.04, 64-bit. The config looks as follows:

```
$ java -version
java version "1.6.0_33"
Java(TM) SE Runtime Environment (build 1.6.0_33-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.8-b03, mixed mode)

```
```
$ /home/juzer/.juniper_networks/network_connect/ncdiag -A
NC Diagnostics for Linux. 
Version 1.0.
Release Date/Time: Sep  7 2011 22:16:41
+==============================================================================+
|   Tests:			|    	 Results:		               |
+==============================================================================+

       o  NC Installation Check 	 Failed
       o  NC Diagnostics 			
             NC Service 		 Not Running
             NC Driver Test 		 Passed
             NC Tunnel Test 		 Not established

       o  Host Details  			
             Hostname 			 inox
             Domainname 		 (none)
             IP Routing Enabled 	 No
             IP Loopback test 		 Error 2: Address already in use
Passed
             Nameserver Details 	
               192.168.100.1 		 Ping Passed
             Gateway Ping Test 			 
               192.168.100.1 		 Ping Passed

       o  Network Connection Diagnostics  			

	     Interface:   		 lo
	     IP Address:  		 127.0.0.1
	     Netmask:     		 255.0.0.0
	     MTU:         		 16436

	     Interface:   		 eth0
	     IP Address:  		 192.168.100.100
	     Netmask:     		 255.255.255.0
	     Broadcast:   		 192.168.100.255
	     MTU:         		 1500
      o  Route Info 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.100.1   0.0.0.0         UG    0      0        0 eth0

       Finished running tests 
+==============================================================================+
```

I have NC Version: 7.1R4 in ~/.juniper_networks/network_connect/ and an NCLinuxApp.jar in ~/.juniper_networks/

When I start ~/junpiernc (after --deconfig), it asks for the necessary entries and then shows the following information: "The Network Connect GUI needs a 32-bit Java - Ignoring 64-bit Java from $PATH (usr/bin/java)."

As I have tried to get this working for hours (partially becuase not reading some instructions carefully, I have to admit), I have no ideas anymore.

I see that NC seems to be not installed, but I have no idea what I should do in order to correct that. When I start junipernc I get a java window, and the first error I see in the GUI log viewer is like:

"ncp.error ncpEstablish ive xxxxxx with context 0x8a125b0"

I am not sure if I have the right java, or if the NC is installed but honestly I am very confused by the many information I gathered so far. I would very much appreciate if someone could point me to the right direction from this point, if possible based on the information I provided above.

Many thanks.

---

### Post by tonyuprm on 2012-06-26
You are missing 32 bit java.

You need to have both (64 and 32).

The instructions on my previous post should work for 10.04 as well.

---

### Post by free1proxy on 2012-06-30
Did you follow the directions in the very first post on this thread?  If you had you wouldn't be getting this error :wink:

---

### Post by basarix on 2012-07-21
after finally getting the java working, i get the juniper applet popup thingy up, it connects but immediately after it exits, that is both thru the junipernc script from madscientist and from the firefox plugin, the error i am getting is the following:

20120721135121.507201 ncui[p4463.t4493] ncapp.info New ncapp log level set to 3 (nccommon.cpp:75)
20120721135121.507269 ncui[p4463.t4493] ncapp.info Version         : 7.1 
Release Version : 7.1-0-Build18853
Build Date/Time : Jul 13 2011
Copyright 2001-2010 Juniper Networks
 (ncapp.cpp:153)
20120721135121.553874 ncui[p4463.t4493] dsclient.info state: kStateSignin (dsclient.cpp:256)
20120721135121.553913 ncui[p4463.t4493] dsclient.info --> GET / (authenticate.cpp:179)
20120721135121.568433 ncui[p4463.t4493] dsclient.info <-- 302 [https://as.afip.gov.ar/dana-na/auth/url_0/welcome.cgi](https://as.afip.gov.ar/dana-na/auth/url_0/welcome.cgi) (authenticate.cpp:211)
20120721135121.568465 ncui[p4463.t4493] dsclient.info state: kStateWelcome (dsclient.cpp:264)
20120721135121.568477 ncui[p4463.t4493] dsclient.info --> GET /dana-na/auth/url_0/welcome.cgi (authenticate.cpp:179)
20120721135121.687170 ncui[p4463.t4493] dsclient.info <-- 200  (authenticate.cpp:211)
20120721135121.687263 ncui[p4463.t4493] dsclient.info state: kStateLogin (dsclient.cpp:296)
20120721135121.687338 ncui[p4463.t4493] dsclient.info --> POST /dana-na/auth/url_0/login.cgi (authenticate.cpp:179)
20120721135121.978096 ncui[p4463.t4493] dsclient.info <-- 302 [https://as.afip.gov.ar/dana/home/starter0.cgi?check=yes](https://as.afip.gov.ar/dana/home/starter0.cgi?check=yes) (authenticate.cpp:211)
20120721135121.978134 ncui[p4463.t4493] dsclient.info --> GET /dana/home/starter0.cgi?check=yes (authenticate.cpp:179)
20120721135122.128123 ncui[p4463.t4493] dsclient.info <-- 200  (authenticate.cpp:211)
20120721135122.128195 ncui[p4463.t4493] authStateLogin.info starter0.cgi has asked for tz_offset parameter (authenticate.cpp:372)
20120721135122.128220 ncui[p4463.t4493] authStateLogin.info starter0.cgi has asked for clienttime parameter (authenticate.cpp:379)
20120721135122.128256 ncui[p4463.t4493] dsclient.info --> POST /dana/home/starter0.cgi?check=yes (authenticate.cpp:179)
20120721135122.222343 ncui[p4463.t4493] dsclient.info <-- 302 /dana/home/starter.cgi (authenticate.cpp:211)
20120721135122.222392 ncui[p4463.t4493] dsclient.info --> GET /dana/home/starter.cgi (authenticate.cpp:179)
20120721135122.303964 ncui[p4463.t4493] dsclient.info <-- 200  (authenticate.cpp:211)
20120721135122.304034 ncui[p4463.t4493] dsclient.info state: kStateAuthenticated (dsclient.cpp:376)
20120721135124.511130 ncui[p4463.t4493] IpcConn.error recv failed with errno 22 (ncipc.cpp:273)
20120721135124.534406 ncui[p4463.t4493] ncui.error Got signal 17 (ncui.cpp:278)



any help with this would be greately appreciated

---

### Post by gdw2 on 2012-07-24
I was getting the following errors in my NCSVC and NCUI logs respectively when trying to connect via the command line:

```
20120723150831.208316 ncsvc[p15348.t15348] ncapp.error Failed to authenticate with IVE. Error 2 (ncsvc.cpp:225)

20120724101941.496299 ncui[p22588.t22613] ncapp.error Failed to connect/authenticate with IVE. Error 10 (ncapp.cpp:179)
```

I came across [this page]("http://kb.juniper.net/InfoCenter/index?page=content&id=KB20490&actp=RSS"), which indicates that in some cases, the policy is set up so that you _must_ connect through a browser.  

I found this to be the case.

I'm running Archlinux, not ubuntu, so ymmv, but here's what I had to do: 

[LIST]
[*]Install 32-bit jre
[*]Install 32-bit firefox
[*]Symlink the 32-bit jre browser plugin so to the right directory
[/LIST]

Hope that helps someone!

---

### Post by Hamrag on 2012-07-26
Hi,

I'm having problems connecting to my employers network using MadScientist's script. Network Connect Version is 7.0 and Ubuntu is 12.04 (64bit). In the logs I can see the following, but I have no idea what that means or how to fix it:

[...]
20120726110102.832623 ncsvc[p13984.t13984] ncp.error ncpEstablish for IVE abc.cde.de with context 0x8f709a8 (ncp.cpp:410)
20120726110102.832886 ncsvc[p13984.t13985] main.info Setting DSSSL to use Default ciphers (ncp.cpp:1635)
20120726110102.833167 ncsvc[p13984.t13985] main.info Setting NCP certificate hash for DSSSL certificate verification (ncp.cpp:1644)
20120726110102.833213 ncsvc[p13984.t13985] main.info Using DSSSL to connect to IVE (ncp.cpp:1705)
20120726110102.833242 ncsvc[p13984.t13985] connect.info creating a new HTTP connection... (ncp_dsssl.cpp:168)
20120726110102.981348 ncsvc[p13984.t13985] connect.info compression is enabled (ncp_dsssl.cpp:392)
20120726110102.981461 ncsvc[p13984.t13985] connect.info IVE ncp_version = 2 (ncp_dsssl.cpp:402)
20120726110102.981726 ncsvc[p13984.t13985] conn.info cleanup 0 (ncp.cpp:1393)
20120726110102.981782 ncsvc[p13984.t13985] ncp.error NCP_ESTABLISH_DONE for IVE abc.cde.de (ncp.cpp:1748)
20120726110102.981917 ncsvc[p13984.t13984] ncphandler.info establish done (ncphandler.cpp:238)
20120726110102.982034 ncsvc[p13984.t13984] ncp.info connect to myComputer:443 svc 4 (ncp.cpp:760)
20120726110102.982092 ncsvc[p13984.t13984] connect.info creating a new HTTP connection... (ncp_dsssl.cpp:168)
20120726110103.125932 ncsvc[p13984.t13985] connect.info compression is enabled (ncp_dsssl.cpp:392)
20120726110103.126043 ncsvc[p13984.t13985] connect.info IVE ncp_version = 2 (ncp_dsssl.cpp:402)
20120726110103.126191 ncsvc[p13984.t13985] connect.error deflateInit2 returned 0 (ncp_dsssl.cpp:478)
20120726110103.152979 ncsvc[p13984.t13985] worker.error connect to myComputer:443 failed. IVE returned error 20001069 (ncp_dsssl.cpp:1054)
20120726110103.153222 ncsvc[p13984.t13984] ncphandler.info control channel disconnected due to error 20001069 (ncphandler.cpp:286)
20120726110103.153299 ncsvc[p13984.t13984] session.info initial connection to IVE is lost. (session.cpp:550)
20120726110103.153332 ncsvc[p13984.t13984] session.info disconnecting from ive abc.cde.de with reason 5 (session.cpp:486)
20120726110103.153358 ncsvc[p13984.t13984] adapter.info closing tun adapter FFFFFFFF (adapter.cpp:781)
20120726110103.153385 ncsvc[p13984.t13984] sysdeps.info restoring DNS settings... (sysdeps.cpp:796)
20120726110103.153418 ncsvc[p13984.t13984] sysdeps.error rename /etc/jnpr-nc-resolv.conf => /etc/resolv.conf failed wirh error 2 (sysdeps.cpp:799)
20120726110103.153447 ncsvc[p13984.t13984] sysdeps.error rename /etc/jnpr-nc-hosts.bak => /etc/hosts failed wirh error 2 (sysdeps.cpp:803)
20120726110103.153486 ncsvc[p13984.t13984] ncp.error ncpTearDown for IVE abc.cde.de (ncp.cpp:482)
20120726110103.153639 ncsvc[p13984.t13985] worker.error NCP worker has been requested to stop (ncp_dsssl.cpp:641)
20120726110103.153889 ncsvc[p13984.t13985] conn.info cleanup 0 (ncp.cpp:1393)

Any help would be appreciated.

Hamrag

---

### Post by mdwy62 on 2012-07-28
I have 2 12.04 (32bit) systems. Both have been able to use network connect (NC), until about a week ago. I am using the browser approach. My employer's vpn website has a "Start" button for Network Connect. This opens a new window with the network connect process. On both systems it connects, but now, on one of them I immediately get a "Config Failed" window.

The ncui.log and ncsvc.log on the failing system are both empty. The only difference between the systems is that the one where NC is NOT working has been kept up to date. I have 247 pending updates on the other system (where NC is working) and I am afraid to apply any of them for fear of breaking NC. 

Both systems have sun java installed
    NC is broken          vs NC is working
    FF 14.0.1             vs FF 13.0.1
kernel 3.2.0-27-generic   vs 3.2.0-26-generic-pae
Java.com Ver 6 update 30  vs Ver 6 update 30

Any help on what log I should look in for hints as to what is broken would be appreciated, or what other package versions I should compare.

Another symptom is that on the system where NC fails, when I plug into my employers LAN, I can no longer connect via smb://machine_name/share, I have to specify smb://user@machine_name.business.corp/share or smb://machine_ip_address.

---

### Post by mdwy62 on 2012-07-30
I suppose everyone probably knows this, but I solved my problem by reading the info entry for resolvconf. Seems that due to some other WIFI network problems I was having, I moved /etc/resolv.conf to a backup file. Under 12.04 this is a bad idea, as /etc/resolv.conf is supposed to be a symbolic link to /run/resolvconf/resolv.conf. On my broken system, /run/resolvconf/resolv.conf did not exist. Nevertheless, I created /etc/resolv.conf as a symlink to this and rebooted. Immediately, names were resolved when I had an ethernet connection to the network. 

More pertinent to this thread, Network Connect (from outside the LAN) now works fine as well. :)

---

### Post by tewth on 2012-08-07
Post #441:
You sir, are a hero.
Thank you.

---

### Post by tewth on 2012-08-07
And also, @mdwy62 in post #494, you need to update your java. Java 6 update 30 is banned in firefox now, only 31 and above work now. Same thing goes for java 7 updates 1 and 2.
(This is due to security vulnerabilities)[]("http://ubuntuforums.org/showpost.php?p=12136077&postcount=494")[]("http://ubuntuforums.org/showpost.php?p=12136077&postcount=494")[]("http://ubuntuforums.org/showpost.php?p=12136077&postcount=494")

---

### Post by teust on 2012-08-07
I've been trying to get this working for over a month :confused:.

When I run the following I get

java -classpath /home/tom/.juniper_networks/network_connect/NC.jar NC -h <url> -L 5 -l 5 -n  -t  -x

I get

failed to load ncui library.  I am running a 64 bit system, 12.04 with oracle java 6 installed.

I have tried mad scientist script but I get a failure for NC when running diagnostics. 

Please someone put me out of my misery!!

---

### Post by madscientist on 2012-08-20
Hi all.  First the good news.  I decided to completely rework the script that I have, and write it in Perl/GTK2 as a complete and separate UI to the Juniper Network Connect that replaces the Java UI that comes from Juniper.

This will allow you to forget all requirements for Java of any aspect.  Additionally it has some extra features not found in the NC UI, such as automatically retrying on timeout (if you use a password) and storing multiple VPN profiles which you can select from.

I added simplistic support for proxy services, but I don't have any access to a system that uses proxy so I have no idea if what I've done works well or not.

Please go visit my [Juniper Network Connect]("http://mad-scientist.net/juniper.html") page for some more details and a download link.

Here's the bad news: later this week (on Thursday Aug 23 2012) I will lose access to my Juniper NC server, as my company is switching to a different VPN service.  After that I won't be able to test any changes to the script.

So I recommend that you grab a copy now and try it out!

---

### Post by madscientist on 2012-08-21
It turns out I may have a bit longer access to Juniper Network Connect, rather than losing it this Wednesday.  But even if I do my last day of access is coming soon (within weeks at most).

I created a [mailing list]("mailto:msjnc@mad-scientist.net") you can [subscribe to]("http://mad-scientist.net/mailman/listinfo/msjnc_mad-scientist.net"), as well, if you want to be kept up-to-date with news or info.

---

### Post by jayhags on 2012-08-28
Awesome work, I have been using your script for the past year and am really glad to have a version without the need for java.

I would like to note that a fresh install of Ubuntu 12.04.1 already includes the libgtk2-perl package.  However I did need to install the libwww-perl package after seeing the following message:

[INDENT]Can't locate LWP/Simple.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at ./msjnc line 53.
BEGIN failed--compilation aborted at ./msjnc line 53.[/INDENT]

---

### Post by aperomsik on 2012-09-02
> **madscientist said:**
> Hi all.  First the good news.  I decided to completely rework the script that I have, and write it in Perl/GTK2 as a complete and separate UI to the Juniper Network Connect that replaces the Java UI that comes from Juniper.

I had been using an older version of the script until about last Wednesday, but then it stopped working. Before that it was working fine for me on both 32-bit and 64-bit 12.04 systems.

So I tried the new version of the script. I like the fact that it gets Java out of the loop. It works fine on the 64-bit system, but for the 32-bit system it is getting stuck somehow. It says "connecting." 

In .juniper_networks/network_connect/ncsvc.log I see:

IpcConn.error bind failed to port 443. Error 98 (ncipc.cpp:75)

and then a bunch of 


20120902110504.536907 ncsvc[p26863.t26863] dsncuiapi.error sendMesage failed (dsncuiapi.cpp:180)


Any ideas?  Firefox is able to connect.

---

### Post by dvo on 2012-09-11
> **tonyuprm said:**
> 
This should get NC to work on your Ubuntu 12.04 64 bit!
 
Great job DVO!

Thanks,


You're welcome! Here is an update of my original post for Ubuntu 12.04
with a more convenient way of installing Oracle Java 7 for amd64 systems in both the 64-bit and 32-bit variant:

```
sudo apt-get install oracle-java7-installer
sudo add-apt-repository "deb http://download.tuxfamily.org/arakhne/ubuntu precise-arakhne universe"
wget http://download.tuxfamily.org//arakhne/public.key -O - | sudo apt-key add -
sudo apt-get install ia32-oracle-java7-jre 
```

Then create/install the wrapper script as follows: 
```
sudo mv /usr/lib/jvm/java-7-oracle/jre/bin/java{,.orig}
sudo cat >/usr/lib/jvm/java-7-oracle/jre/bin/java << EOI
#!/bin/bash
if [ "$3" = "NC" ]
then
  /usr/lib/jvm/ia32-java-7-oracle/jre/bin/java "\$@"
else
  /usr/lib/jvm/java-7-oracle/jre/bin/java.orig "\$@"
fi
EOI
sudo chmod ugo+x /usr/lib/jvm/java-7-oracle/jre/bin/java

```

Note that this method works independently of how the user authentication is done, i.e., using passwords, smartcards, etc.

Regards,
[INDENT]David von Oheimb[/INDENT]

---

### Post by dvo on 2012-09-11
> **madscientist said:**
> Hi all.  First the good news.  I decided to completely rework the script that I have, and write it in Perl/GTK2 as a complete and separate UI to the Juniper Network Connect that replaces the Java UI that comes from Juniper.

Nice, but it is worth noting that this script, like its predecessors, is not applicable in cases where the user needs to authenticate with a smart card (rather than with a password). 
Or do you see a chance of integrating smart card libraries and pcscd?

---

### Post by karlstad on 2012-09-16
Is it possible that the network-manager-vpnc package will support the Juniper Secure Access VPN sometime in the future? It would be nice to be able to be able to set this up in NM.

---

### Post by ianmac on 2012-09-17
> **basarix said:**
> after finally getting the java working, i get the juniper applet popup thingy up, it connects but immediately after it exits, that is both thru the junipernc script from madscientist and from the firefox plugin, the error i am getting is the following:

20120721135121.507201 ncui[p4463.t4493] ncapp.info New ncapp log level set to 3 (nccommon.cpp:75)
20120721135121.507269 ncui[p4463.t4493] ncapp.info Version         : 7.1 
Release Version : 7.1-0-Build18853
Build Date/Time : Jul 13 2011
Copyright 2001-2010 Juniper Networks
 (ncapp.cpp:153)
20120721135121.553874 ncui[p4463.t4493] dsclient.info state: kStateSignin (dsclient.cpp:256)
20120721135121.553913 ncui[p4463.t4493] dsclient.info --> GET / (authenticate.cpp:179)
20120721135121.568433 ncui[p4463.t4493] dsclient.info <-- 302 [https://as.afip.gov.ar/dana-na/auth/url_0/welcome.cgi](https://as.afip.gov.ar/dana-na/auth/url_0/welcome.cgi) (authenticate.cpp:211)
20120721135121.568465 ncui[p4463.t4493] dsclient.info state: kStateWelcome (dsclient.cpp:264)
20120721135121.568477 ncui[p4463.t4493] dsclient.info --> GET /dana-na/auth/url_0/welcome.cgi (authenticate.cpp:179)
20120721135121.687170 ncui[p4463.t4493] dsclient.info <-- 200  (authenticate.cpp:211)
20120721135121.687263 ncui[p4463.t4493] dsclient.info state: kStateLogin (dsclient.cpp:296)
20120721135121.687338 ncui[p4463.t4493] dsclient.info --> POST /dana-na/auth/url_0/login.cgi (authenticate.cpp:179)
20120721135121.978096 ncui[p4463.t4493] dsclient.info <-- 302 [https://as.afip.gov.ar/dana/home/starter0.cgi?check=yes](https://as.afip.gov.ar/dana/home/starter0.cgi?check=yes) (authenticate.cpp:211)
20120721135121.978134 ncui[p4463.t4493] dsclient.info --> GET /dana/home/starter0.cgi?check=yes (authenticate.cpp:179)
20120721135122.128123 ncui[p4463.t4493] dsclient.info <-- 200  (authenticate.cpp:211)
20120721135122.128195 ncui[p4463.t4493] authStateLogin.info starter0.cgi has asked for tz_offset parameter (authenticate.cpp:372)
20120721135122.128220 ncui[p4463.t4493] authStateLogin.info starter0.cgi has asked for clienttime parameter (authenticate.cpp:379)
20120721135122.128256 ncui[p4463.t4493] dsclient.info --> POST /dana/home/starter0.cgi?check=yes (authenticate.cpp:179)
20120721135122.222343 ncui[p4463.t4493] dsclient.info <-- 302 /dana/home/starter.cgi (authenticate.cpp:211)
20120721135122.222392 ncui[p4463.t4493] dsclient.info --> GET /dana/home/starter.cgi (authenticate.cpp:179)
20120721135122.303964 ncui[p4463.t4493] dsclient.info <-- 200  (authenticate.cpp:211)
20120721135122.304034 ncui[p4463.t4493] dsclient.info state: kStateAuthenticated (dsclient.cpp:376)
20120721135124.511130 ncui[p4463.t4493] IpcConn.error recv failed with errno 22 (ncipc.cpp:273)
20120721135124.534406 ncui[p4463.t4493] ncui.error Got signal 17 (ncui.cpp:278)



any help with this would be greately appreciated

I don't know if you got this sorted out or not.  I ran into this problem today and seemed to be because my resolv.conf file was missing.  I must have done something to it when trying to fix it after disconnecting from the VPN.  To fix it, I re-touched the resolv.conf file and tried again and it worked.

---

### Post by davejef on 2012-09-18
Hi, I am not really a linux expert but I am trying to get this to work so that I can ditch my work Windows laptop so any help would be much appreciated.

Here is what I have in my log file:

20120918081805.26750 ncsvc[p2729.t2729] ncsvc.info New ncsvc log level set to 3 (nccommon.cpp:75)
20120918081805.26853 ncsvc[p2729.t2729] sysdeps.info restoring DNS settings... (sysdeps.cpp:796)
20120918081805.26890 ncsvc[p2729.t2729] sysdeps.error rename /etc/jnpr-nc-resolv.conf => /etc/resolv.conf failed wirh error 2 (sysdeps.cpp:799)
20120918081805.26909 ncsvc[p2729.t2729] sysdeps.error rename /etc/jnpr-nc-hosts.bak => /etc/hosts failed wirh error 2 (sysdeps.cpp:803)
20120918081807.40143 ncsvc[p2729.t2729] ncsvc.info Connecting to user2.uk.daiwacm.com:443 (ncsvc.cpp:494)
20120918081809.234122 ncsvc[p2729.t2729] dsclient.info state: kStateSignin (dsclient.cpp:248)
20120918081809.234199 ncsvc[p2729.t2729] dsclient.info --> GET / (authenticate.cpp:162)
20120918081809.274148 ncsvc[p2729.t2729] dsclient.info <-- 302 [https://xxxxx.xx.xxxxxx.com/xxxxx/auth/url_24/welcome.cgi](https://xxxxx.xx.xxxxxx.com/xxxxx/auth/url_24/welcome.cgi) (authenticate.cpp:194)
20120918081809.274203 ncsvc[p2729.t2729] dsclient.info state: kStateWelcome (dsclient.cpp:256)
20120918081809.274218 ncsvc[p2729.t2729] dsclient.info --> GET /dana-na/auth/url_24/welcome.cgi (authenticate.cpp:162)
20120918081810.790846 ncsvc[p2729.t2729] dsclient.info <-- 200  (authenticate.cpp:194)
20120918081810.790926 ncsvc[p2729.t2729] dsclient.info state: kStatePreAuth (dsclient.cpp:264)
20120918081810.790941 ncsvc[p2729.t2729] dsclient.info --> GET /dana-na/auth/url_24/welcome.cgi (authenticate.cpp:162)
20120918081811.31548 ncsvc[p2729.t2729] dsclient.info <-- 200  (authenticate.cpp:194)
20120918081811.31628 ncsvc[p2729.t2729] dsclient.info state: kStateCacheCleaner (dsclient.cpp:280)
20120918081811.31652 ncsvc[p2729.t2729] dsclient.info --> POST /dana-na/cc/ccupdate.cgi (authenticate.cpp:162)
"ncsvc.log" [readonly] 38L, 4106C                                                                                        1,1         

Is the root of the problem the failed renames? I cannot find the jnpr-nc-resolve.conf or jnpr-nc-hosts.bak files anywhere. Where should they be obtained from?

Thanks,
Dave

---

### Post by stl314159 on 2012-10-20
Has anyone had success with this on 12.10?  It was working fine on 12.04 but I can not connect after upgrading.

Thanks

---

### Post by aperomsik on 2012-10-21
> **stl314159 said:**
> Has anyone had success with this on 12.10?  It was working fine on 12.04 but I can not connect after upgrading.

Thanks

I can connect after upgrading. I didn't do anything special.

---

### Post by karlstad on 2012-10-25
Neither do I. I get this message when running **~/.juniper_networks/network_connect/ncsvc**:

```
ncsvc> Failed to setuid to root. Error 1: Operation not permitted
```

My /home is not mounted with *nosuid* or anything, bit it is encrypted with ecryptfs though, and I think that might be the problem.

---

### Post by deezer on 2012-10-25
I get the following error after upgrading from Ubuntu 12.04 to 12.10:

```

ncsvc> Failed to setuid to root. Error 1: Operation not permitted
java: ncui.cpp:262: void NCUI::run(): Assertion `m_conn->isConnected()' failed.
Aborted (core dumped)

```

I am using jdk1.6.0_33_ia32

It worked fine before the upgrade.

---

### Post by deezer on 2012-10-25
> **deezer said:**
> I get the following error after upgrading from Ubuntu 12.04 to 12.10:

```

ncsvc> Failed to setuid to root. Error 1: Operation not permitted
java: ncui.cpp:262: void NCUI::run(): Assertion `m_conn->isConnected()' failed.
Aborted (core dumped)

```

I am using jdk1.6.0_33_ia32

It worked fine before the upgrade.

Running the Mad Scientist script as sudo in 12.10 works and I don't get the above error.
$sudo ./junipernc.sh --root

Therfore, I believe the entire problem is ```
ncsvc> Failed to setuid to root.
```

I'm not sure why this fails in Ubuntu 12.10, I believe I have the permissions set correctly on ncsvc as far as I know:

```

-rws--s--x 1 root     root     1281948 Oct 25 16:40 ncsvc
```

---

### Post by ariva on 2012-10-27
In quantal, after apllying all patches, new problem appears. Cannot launch network connect any more. When launching NC.jar manually, following errors appears:

[I]* SecureLaunchNCLoader * Error loading message strings: java.lang.Exception: Error reading nclaunchmessages.pl
*** Property [msgNCTitle] with defaultValue [Network Connect] does not exist or may not have been translated ***.
*** Property [msgTabNameSession] with defaultValue [Session] does not exist or may not have been translated ***. ...
[/I] 
Full output in attachement.
Does anyone have similar problem?

---

### Post by ariva on 2012-10-27
Unfortunately some sigfault occured.

```
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xaa9e3bcd, pid=2841, tid=2865249088
#
# JRE version: 7.0_09-b05
# Java VM: Java HotSpot(TM) Server VM (23.5-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [libncui.so+0x9bbcd]  DSClient::setCertHash(char const*)+0x35

```But it's rather question to Juniper Support

---

### Post by karlstad on 2012-10-31
This obviously has something to do with eCryptfs and that it doesn't allow setuid (anymore? - worked in 12.04). I have posted a question at Ask Ubuntu [here]("http://askubuntu.com/questions/210048/error-when-running-binary-with-root-setuid-under-encrypted-home-directory") and I'm hoping to find a way to hack SUID support to ecryptfs again.

I made it work again by copying my **~/.juniper_networks** folder to e.g. **/opt/juniper** and by changing the **$JNPATH** variable on line 1817 in the script to the following:

```
$JNPATH = "/opt/juniper/.juniper_networks";
```

Remember to keep the folder permissions intact (use **cp -a** when copying).

The GUI doesn't seem to be updated and doesn't show any stats or that it's connected at all, but if you run **ifconfig** and the **tun0** interface is up and running with a VPN IP, then it's working.

Disconnecting doesn't work with the GUI, obviously, so you just have to kill the ncsvc process to terminate the connection.

It's not a perfect workaround, but at least it *works*.

---

### Post by aperomsik on 2012-12-05
> **aperomsik said:**
> I had been using an older version of the script until about last Wednesday, but then it stopped working. Before that it was working fine for me on both 32-bit and 64-bit 12.04 systems.

So I tried the new version of the script. I like the fact that it gets Java out of the loop. It works fine on the 64-bit system, but for the 32-bit system it is getting stuck somehow. It says "connecting." 

In .juniper_networks/network_connect/ncsvc.log I see:

IpcConn.error bind failed to port 443. Error 98 (ncipc.cpp:75)

and then a bunch of 


20120902110504.536907 ncsvc[p26863.t26863] dsncuiapi.error sendMesage failed (dsncuiapi.cpp:180)


Any ideas?  Firefox is able to connect.

So, I don't know why Firefox was able to connect, but I seem to have lost that workaround when I moved to 64-bit 12.10. I could have installed 32-bit Firefox, but I wasn't in the mood.

I guess from the error message it should be obvious that the difference between the machine that worked and the one that didn't was that one was running a web server and the other wasn't.

I seem to have got around the problem by adjusting the Listen commands in /etc/apache2/ports.conf to listen on port 443 only on the external interface, not on the local interface.

I changed "Listen 443" to "Listen xx.xx.xx.xx:443" where xx.xx.xx.xx is the address of the network interface, which happens to be eth4.

I don't know why ncsvc needs that port when run from msjnc but not when run from Firefox.

---

### Post by wand3r3r on 2012-12-10
I am trying to connect from a work site to a remote network.  I use an Ubuntu VM (12.04) that must connect to the work network through a proxy.  I successfully get connected but I cannot seem to get to any of the machines.  On the Network connect GUI bytes sent ticks up but bytes received returns 0.  Looks like the VPN host is using Network Connect 7.1.  NC works fine from the Windows environment and both the VM and Windows machine when not behind the proxy.

Has anyone had any experience with this?  I have been having difficulty finding any workaround.

```
/usr/local/jre1.7.0_09/bin/java -jar ~/.juniper_networks/network_connect/NC.jar -h <host> -u <vpn user> -r "<Realy long realm name>" -f <X509 DER Format cert> -y <proxy host> -z 8080 -d <ProxyDomain> -L 5 -l 5 -s <proxy user> -a <proxy pass> -p <vpn pass> &
```

NCUI.log
```
20121210164206.982207 ncui[p6551.t6568] dsclient.debug using supplied proxy settings (<proxy>:8080) (dsclient.cpp:1011)
20121210164206.982382 ncui[p6551.t6568] http_connection.para Starting a timed connect with SSL session 0xad257bb0, proxy <hexcode removed>:8080, and timeout 30 (http_connection.cpp:181)
20121210164206.982404 ncui[p6551.t6568] http_connection.para Entering state_start_connection (http_connection.cpp:293)
20121210164207.1530 ncui[p6551.t6568] http_connection.para Entering state_continue_connection (http_connection.cpp:310)
20121210164207.1592 ncui[p6551.t6568] http_connection.para Starting proxy negotiation (http_connection.cpp:734)
20121210164207.1607 ncui[p6551.t6568] http_connection.para Entering state_proxy_connect (requester state = 0) (http_connection.cpp:343)
20121210164207.1668 ncui[p6551.t6568] http_connection.para Entering state_proxy_get_response (http_connection.cpp:369)
20121210164207.112960 ncui[p6551.t6576] dsio.para poll got return value of 1
 (dsio.cpp:511)
20121210164207.113048 ncui[p6551.t6576] dsncuiapi.para DsNcUiApi::ProcessDisconnectReply (dsncuiapi.cpp:328)
20121210164207.113086 ncui[p6551.t6576] ncui.info received onDisconnect with reason = 0 (ncui.cpp:445)
20121210164207.113152 ncui[p6551.t6576] dsxp.para unregister handle 0x00000015, total 1 (dsio.cpp:355)
20121210164207.113188 ncui[p6551.t6576] dsxp.para unregister handle 0x00000017, total 0 (dsio.cpp:355)
20121210164207.113244 ncui[p6551.t6576] IpcConn.debug unregistering the IPC connection (0xB1328020) IO handler (ncipc.cpp:224)
20121210164207.113428 ncui[p6551.t6576] ncapp.info waiting for NC service to stop! (ncapp.cpp:255)
20121210164207.113471 ncui[p6551.t6576] ncapp.info done... (ncapp.cpp:257)
20121210164207.113551 ncui[p6551.t6576] dsncuiapi.para DsNcUiApi::~DsNcUiApi (dsncuiapi.cpp:80)
20121210164207.360801 ncui[p6551.t6568] http_connection.para Entering state_proxy_get_response (http_connection.cpp:369)
20121210164207.360968 ncui[p6551.t6568] http_connection.para Entering state_proxy_handle_response (http_connection.cpp:409)
20121210164207.361041 ncui[p6551.t6568] http_connection.info CONNECT negotiation complete (http_connection.cpp:445)
20121210164207.361076 ncui[p6551.t6568] http_connection.para Entering state_ssl_connect (http_connection.cpp:481)
20121210164208.212700 ncui[p6551.t6568] dsssl.para SSL connect ssl=0xadfe9978/sd=12 connection using cipher RC4-SHA (DSSSLSock.cpp:1320)
20121210164208.213097 ncui[p6551.t6568] http_connection.para Returning DSHTTP_COMPLETE from state_ssl_connect (http_connection.cpp:489)
20121210164210.201580 ncui[p6551.t6568] ncui.info Sending kill signal (SIGQUIT) to ncsvc...  (ncapp.cpp:454)
```

ncsvc.log
```
20121210163739.214132 ncsvc[p6580.t6580] session.info log level set to 50 (session.cpp:1053)
20121210163739.214645 ncsvc[p6580.t6580] dsio.para poll waiting for 1 fds, max-fd: 5, with timeout : -1
 (dsio.cpp:509)
20121210163739.214771 ncsvc[p6580.t6580] dsio.para poll got return value of 1
 (dsio.cpp:511)
20121210163739.214834 ncsvc[p6580.t6580] session.para received 102 msg from UI (session.cpp:112)
20121210163739.214919 ncsvc[p6580.t6580] session.info ive_host = vpn.<network>.com (session.cpp:195)
20121210163739.221435 ncsvc[p6580.t6580] session.info Using proxy <proxy>:8080 to connect to the IVE (session.cpp:235)
20121210163739.226554 ncsvc[p6580.t6580] rmon.info got system route 0.0.0.0/0.0.0.0 gw <ip>.1 metric 0 via 0x00000000 (routemon.cpp:714)
20121210163739.226686 ncsvc[p6580.t6580] rmon.info got system route <ip>.0/255.255.255.0 gw 0.0.0.0 metric 1 via 0x00000000 (routemon.cpp:714)
20121210163739.226745 ncsvc[p6580.t6580] rmon.info got system route 169.254.0.0/255.255.0.0 gw 0.0.0.0 metric 1000 via 0x00000000 (routemon.cpp:714)
20121210163739.226827 ncsvc[p6580.t6580] rmon.info got system route 208.<ip>.128/255.255.255.255 gw <ip>.1 metric 0 via 0x00000000 (routemon.cpp:714)
20121210163739.226882 ncsvc[p6580.t6580] rmon.info  Collecting latest routes from the system (routemon.cpp:1452)
20121210163739.227118 ncsvc[p6580.t6580] rmon.info best route to 216.<another ip> is 0.0.0.0/0.0.0.0 via 0x00000000 metric: 0 (routemon.cpp:1473)
20121210163739.227225 ncsvc[p6580.t6580] rmon.info best route to gateway: <ip>.0/255.255.255.0 gw 0.0.0.0 via 0x00000000 metric 1 (routemon.cpp:1976)
20121210163739.227284 ncsvc[p6580.t6580] rmon.info attempting to add route to next hop gateway (routemon.cpp:1980)
20121210163739.227320 ncsvc[p6580.t6580] rmon.info adding route to <ip>.1/255.255.255.255 with gw 0.0.0.0, metric 1, if_id 0 (routemon.cpp:872)
20121210163739.231793 ncsvc[p6580.t6580] rmon.info adding server route to the IVE: dest = 216.<another ip>, gw = <ip>.1, if_id = 0, dev = eth0 (routemon.cpp:1547)
20121210163739.232340 ncsvc[p6580.t6580] session.info connecting to ive vpn.<network>.com (session.cpp:362)
20121210163739.238356 ncsvc[p6580.t6580] ncphandler.debug registering the NCP IO handler (ncphandler.cpp:65)
20121210163739.238528 ncsvc[p6580.t6580] dsxp.para register handle 0x00000007, total 2 (dsio.cpp:342)
20121210163739.238644 ncsvc[p6580.t6580] ncp.error ncpEstablish for IVE vpn.<network>.com with context 0x9c15c70 (ncp.cpp:428)
20121210163739.238930 ncsvc[p6580.t6580] dsio.para poll waiting for 2 fds, max-fd: 7, with timeout : 60
 (dsio.cpp:509)
20121210163739.239072 ncsvc[p6580.t6581] main.info Setting DSSSL to use Default ciphers (ncp.cpp:1680)
20121210163739.239587 ncsvc[p6580.t6581] main.info Setting NCP certificate hash for DSSSL certificate verification (ncp.cpp:1689)
20121210163739.239698 ncsvc[p6580.t6581] main.info Using DSSSL to connect to IVE (ncp.cpp:1750)
20121210163739.239741 ncsvc[p6580.t6581] connect.para Starting dsssl timed connect (ncp_dsssl.cpp:69)
20121210163739.239781 ncsvc[p6580.t6581] connect.info creating a new HTTP connection... (ncp_dsssl.cpp:176)
20121210163739.239823 ncsvc[p6580.t6581] http_connection.para Entering state_start_connection (http_connection.cpp:293)
20121210163739.308541 ncsvc[p6580.t6581] http_connection.para Entering state_continue_connection (http_connection.cpp:310)
20121210163739.308738 ncsvc[p6580.t6581] http_connection.para Starting proxy negotiation (http_connection.cpp:734)
20121210163739.308833 ncsvc[p6580.t6581] http_connection.para Entering state_proxy_connect (requester state = 0) (http_connection.cpp:343)
20121210163739.309119 ncsvc[p6580.t6581] http_connection.para Entering state_proxy_get_response (http_connection.cpp:369)
20121210163739.796408 ncsvc[p6580.t6581] http_connection.para Entering state_proxy_get_response (http_connection.cpp:369)
20121210163739.796797 ncsvc[p6580.t6581] http_connection.para Entering state_proxy_handle_response (http_connection.cpp:409)
20121210163739.796938 ncsvc[p6580.t6581] http_connection.info CONNECT negotiation complete (http_connection.cpp:445)
20121210163739.796987 ncsvc[p6580.t6581] http_connection.para Entering state_ssl_connect (http_connection.cpp:481)
20121210163740.271185 ncsvc[p6580.t6581] dsssl.para SSL connect ssl=0xf7305ef0/sd=11 connection using cipher RC4-SHA (DSSSLSock.cpp:1320)
20121210163740.271724 ncsvc[p6580.t6581] http_connection.para Returning DSHTTP_COMPLETE from state_ssl_connect (http_connection.cpp:489)
20121210163740.403764 ncsvc[p6580.t6581] connect.info compression is enabled (ncp_dsssl.cpp:400)
20121210163740.403939 ncsvc[p6580.t6581] connect.info IVE ncp_version = 2 (ncp_dsssl.cpp:410)
20121210163740.404831 ncsvc[p6580.t6581] conn.info cleanup 0 (ncp.cpp:1418)
20121210163740.404945 ncsvc[p6580.t6581] ncp.error NCP_ESTABLISH_DONE for IVE vpn.<network>.com (ncp.cpp:1793)
20121210163740.405026 ncsvc[p6580.t6580] dsio.para poll got return value of 1
 (dsio.cpp:511)
20121210163740.405074 ncsvc[p6580.t6580] ncphandler.para got 1 NCP callback (ncphandler.cpp:255)
20121210163740.405106 ncsvc[p6580.t6580] ncphandler.info establish done (ncphandler.cpp:279)
20121210163740.405409 ncsvc[p6580.t6580] ncp.info connect to MY-VM:443 svc 4 (ncp.cpp:779)
20121210163740.405584 ncsvc[p6580.t6580] connect.info creating a new HTTP connection... (ncp_dsssl.cpp:176)
20121210163740.405634 ncsvc[p6580.t6580] http_connection.para Entering state_start_connection (http_connection.cpp:293)
20121210163740.406329 ncsvc[p6580.t6580] dsio.para poll waiting for 2 fds, max-fd: 7, with timeout : 59
 (dsio.cpp:509)
20121210163740.406507 ncsvc[p6580.t6581] worker.para 1 sockets are ready for read/write. (ncp_dsssl.cpp:622)
20121210163740.407056 ncsvc[p6580.t6581] worker.para intra_ncp_server_sock ready to read. (ncp_dsssl.cpp:632)
20121210163740.466102 ncsvc[p6580.t6581] worker.para 1 sockets are ready for read/write. (ncp_dsssl.cpp:622)
20121210163740.466267 ncsvc[p6580.t6581] http_connection.para Entering state_continue_connection (http_connection.cpp:310)
20121210163740.466314 ncsvc[p6580.t6581] http_connection.para Starting proxy negotiation (http_connection.cpp:734)
20121210163740.466374 ncsvc[p6580.t6581] http_connection.para Entering state_proxy_connect (requester state = 0) (http_connection.cpp:343)
20121210163740.466666 ncsvc[p6580.t6581] http_connection.para Entering state_proxy_get_response (http_connection.cpp:369)
20121210163740.611788 ncsvc[p6580.t6581] worker.para 1 sockets are ready for read/write. (ncp_dsssl.cpp:622)
20121210163740.611982 ncsvc[p6580.t6581] http_connection.para Entering state_proxy_get_response (http_connection.cpp:369)
20121210163740.612071 ncsvc[p6580.t6581] http_connection.para Entering state_proxy_handle_response (http_connection.cpp:409)
20121210163740.612130 ncsvc[p6580.t6581] http_connection.info CONNECT negotiation complete (http_connection.cpp:445)
20121210163740.612293 ncsvc[p6580.t6581] http_connection.para Entering state_ssl_connect (http_connection.cpp:481)
20121210163741.10580 ncsvc[p6580.t6581] dsssl.para SSL connect ssl=0xf7305e60/sd=11 connection using cipher RC4-SHA (DSSSLSock.cpp:1320)
20121210163741.11067 ncsvc[p6580.t6581] http_connection.para Returning DSHTTP_COMPLETE from state_ssl_connect (http_connection.cpp:489)
20121210163741.137251 ncsvc[p6580.t6581] worker.para 1 sockets are ready for read/write. (ncp_dsssl.cpp:622)
20121210163741.137526 ncsvc[p6580.t6581] connect.info compression is enabled (ncp_dsssl.cpp:400)
20121210163741.137620 ncsvc[p6580.t6581] connect.info IVE ncp_version = 2 (ncp_dsssl.cpp:410)
20121210163741.137828 ncsvc[p6580.t6581] connect.error deflateInit2 returned 0 (ncp_dsssl.cpp:486)
20121210163741.137937 ncsvc[p6580.t6581] worker.para 2 sockets are ready for read/write. (ncp_dsssl.cpp:622)
20121210163741.137982 ncsvc[p6580.t6581] worker.para intra_ncp_server_sock ready to read. (ncp_dsssl.cpp:632)
20121210163741.138087 ncsvc[p6580.t6581] worker.para compressed 20 -> 25 bytes: socket 11, host MY-VM (ncp_dsssl.cpp:726)
20121210163741.138491 ncsvc[p6580.t6581] worker.para [conn 0x9c1c548] wrote 27 bytes: socket 11, host MY-VM, DSSSL_has_data_tosend 0 (ncp_dsssl.cpp:771)
20121210163741.275128 ncsvc[p6580.t6581] worker.para 1 sockets are ready for read/write. (ncp_dsssl.cpp:622)
20121210163741.275817 ncsvc[p6580.t6581] worker.para read 121 bytes from connection: socket 11, host MY-VM (ncp_dsssl.cpp:824)
20121210163741.276051 ncsvc[p6580.t6580] dsio.para poll got return value of 1
 (dsio.cpp:511)
20121210163741.276158 ncsvc[p6580.t6580] ncphandler.para got 3 NCP callback (ncphandler.cpp:255)
20121210163741.276201 ncsvc[p6580.t6580] ncphandler.info connect done (ncphandler.cpp:284)
20121210163741.276366 ncsvc[p6580.t6580] session.info Connected to ive vpn.<network>.com (session.cpp:426)
20121210163741.278008 ncsvc[p6580.t6580] adapter.info opened tun adapter 0000000C (adapter.cpp:374)
20121210163741.278322 ncsvc[p6580.t6580] dsio.para poll waiting for 2 fds, max-fd: 7, with timeout : 30
 (dsio.cpp:509)
20121210163741.278527 ncsvc[p6580.t6580] dsio.para poll got return value of 1
 (dsio.cpp:511)
20121210163741.278787 ncsvc[p6580.t6580] ncphandler.para got 5 NCP callback (ncphandler.cpp:255)
20121210163741.278976 ncsvc[p6580.t6580] ipsec.info received kmp message 301 size 160 (tunnel.cpp:210)
20121210163741.279157 ncsvc[p6580.t6580] dsipsec.para received tlv group: group 3, len 28 (tunnel.cpp:220)
20121210163741.279334 ncsvc[p6580.t6580] dsipsec.para received tlv attr: group 3, attr 1, len 1 (tunnel.cpp:228)
20121210163741.279512 ncsvc[p6580.t6580] dsipsec.para received tlv attr: group 3, attr 2, len 1 (tunnel.cpp:228)
20121210163741.279833 ncsvc[p6580.t6580] dsipsec.para received tlv attr: group 3, attr 3, len 8 (tunnel.cpp:228)
20121210163741.280021 ncsvc[p6580.t6580] dsipsec.para received tlv group: group 6, len 10 (tunnel.cpp:220)
20121210163741.280196 ncsvc[p6580.t6580] dsipsec.para received tlv attr: group 6, attr 2, len 4 (tunnel.cpp:228)
20121210163741.280398 ncsvc[p6580.t6580] dsipsec.para received tlv group: group 2, len 52 (tunnel.cpp:220)
20121210163741.280723 ncsvc[p6580.t6580] dsipsec.para received tlv attr: group 2, attr 1, len 4 (tunnel.cpp:228)
20121210163741.280921 ncsvc[p6580.t6580] dsipsec.para received tlv attr: group 2, attr 1, len 4 (tunnel.cpp:228)
20121210163741.281098 ncsvc[p6580.t6580] dsipsec.para received tlv attr: group 2, attr 2, len 16 (tunnel.cpp:228)
20121210163741.281273 ncsvc[p6580.t6580] dsipsec.para received tlv attr: group 2, attr 3, len 4 (tunnel.cpp:228)
20121210163741.283946 ncsvc[p6580.t6580] dsipsec.para received tlv group: group 4, len 10 (tunnel.cpp:220)
20121210163741.284119 ncsvc[p6580.t6580] dsipsec.para received tlv attr: group 4, attr 1, len 4 (tunnel.cpp:228)
20121210163741.284235 ncsvc[p6580.t6580] dsipsec.para received tlv group: group 1, len 30 (tunnel.cpp:220)
20121210163741.284346 ncsvc[p6580.t6580] dsipsec.para received tlv attr: group 1, attr 1, len 4 (tunnel.cpp:228)
20121210163741.284472 ncsvc[p6580.t6580] dsipsec.para received tlv attr: group 1, attr 2, len 4 (tunnel.cpp:228)
20121210163741.284616 ncsvc[p6580.t6580] dsipsec.para received tlv attr: group 1, attr 3, len 4 (tunnel.cpp:228)
20121210163741.284763 ncsvc[p6580.t6580] ProxyConfigManager.info Created an external PAC file (sysdeps.cpp:302)
20121210163741.284883 ncsvc[p6580.t6580] ProxyConfigManager.info Created an dummy internal PAC string (sysdeps.cpp:348)
20121210163741.285015 ncsvc[p6580.t6580] ProxyConfigManager.info Created the merged PAC file (sysdeps.cpp:377)
20121210163741.285131 ncsvc[p6580.t6580] session.info IVE sent DNS server <vpn.ip>.40.54 (session.cpp:1470)
20121210163741.285265 ncsvc[p6580.t6580] session.info IVE sent DNS server <vpn.ip>.40.53 (session.cpp:1470)
20121210163741.285382 ncsvc[p6580.t6580] session.info IVE sent DNS suffix int.<network>.com (session.cpp:1498)
20121210163741.285490 ncsvc[p6580.t6580] session.info IVE DNS has priority over Client DNS (session.cpp:1527)
20121210163741.291184 ncsvc[p6580.t6580] sysdeps.para Inserting search domain: int.<network>.com (sysdeps.cpp:734)
20121210163741.291354 ncsvc[p6580.t6580] sysdeps.para Inserting name server: <vpn.ip>.40.54 (sysdeps.cpp:741)
20121210163741.291464 ncsvc[p6580.t6580] sysdeps.para Inserting name server: <vpn.ip>.40.53 (sysdeps.cpp:741)
20121210163741.291738 ncsvc[p6580.t6580] session.info IVE sent WINS server 255.255.255.255 (session.cpp:1611)
20121210163741.291861 ncsvc[p6580.t6580] session.info IVE sent NC IP <vpn.ip>.60.100 netmask 255.255.255.0 (session.cpp:1219)
20121210163741.291966 ncsvc[p6580.t6580] session.info NC client network is <vpn.ip>.60.0 (session.cpp:1224)
20121210163741.292071 ncsvc[p6580.t6580] adapter.info IVE get DNS server <vpn.ip>.40.54 (adapter.cpp:459)
20121210163741.292182 ncsvc[p6580.t6580] adapter.info IVE get DNS server <vpn.ip>.40.53 (adapter.cpp:459)
20121210163741.292290 ncsvc[p6580.t6580] adapter.para IVE and Client MTU values are same : 1400 (adapter.cpp:521)
20121210163741.306958 ncsvc[p6580.t6580] adapter.info deleting route: /sbin/route del -net <vpn.ip>.60.0 netmask 255.255.255.0 dev tun0 (adapter.cpp:563)
20121210163741.332941 ncsvc[p6580.t6580] adapter.info cip = <vpn.ip>.60.100, mask = 255.255.255.0, gw = <vpn.ip>.60.50, domain = int.<network>.com (adapter.cpp:580)
20121210163741.333012 ncsvc[p6580.t6580] dsxp.para register handle 0x0000000c, total 3 (dsio.cpp:342)
20121210163741.333033 ncsvc[p6580.t6580] adapter.para Sending MTU (1400) to IVE (adapter.cpp:738)
20121210163741.333050 ncsvc[p6580.t6580] ipsec.info send kmp message 303 size 16 (tunnel.cpp:202)
20121210163741.333087 ncsvc[p6580.t6580] session.info adapter is configured (session.cpp:1251)
20121210163741.333111 ncsvc[p6580.t6580] session.info Deny route count = 0 (session.cpp:1284)
20121210163741.333157 ncsvc[p6580.t6580] rmon.info modifying the metric for a conflicting route to 0.0.0.0/0.0.0.0 gw <ip>.1 metric 10 (routemon.cpp:837)
20121210163741.333185 ncsvc[p6580.t6580] rmon.info adding a conflicting route with a lower metric to 0.0.0.0/0.0.0.0 gw <vpn.ip>.60.100 metric 1 (routemon.cpp:861)
20121210163741.333215 ncsvc[p6580.t6580] rmon.info adding route to 0.0.0.0/0.0.0.0 with gw <vpn.ip>.60.100, metric 1, if_id 0 (routemon.cpp:872)
20121210163741.333243 ncsvc[p6580.t6580] session.info added route to dest = 0.0.0.0, mask = 0.0.0.0 (session.cpp:1336)
20121210163741.333265 ncsvc[p6580.t6580] session.info route count = 1 (session.cpp:1340)
20121210163741.333359 ncsvc[p6580.t6580] rmon.info system routes:  (routemon.cpp:257)
20121210163741.333383 ncsvc[p6580.t6580] rmon.info 0.0.0.0/0.0.0.0 gw <vpn.ip>.60.100 via 0x00000000 metric 1 (routemon.cpp:1864)
20121210163741.333397 ncsvc[p6580.t6580] rmon.info 0.0.0.0/0.0.0.0 gw <ip>.1 via 0x00000000 metric 10 (routemon.cpp:1864)
20121210163741.333406 ncsvc[p6580.t6580] rmon.info <ip>.0/255.255.255.0 gw 0.0.0.0 via 0x00000000 metric 1 (routemon.cpp:1864)
20121210163741.333425 ncsvc[p6580.t6580] rmon.info <ip>.1/255.255.255.255 gw 0.0.0.0 via 0x00000000 metric 1 (routemon.cpp:1864)
20121210163741.333444 ncsvc[p6580.t6580] rmon.info 169.254.0.0/255.255.0.0 gw 0.0.0.0 via 0x00000000 metric 1000 (routemon.cpp:1864)
20121210163741.333464 ncsvc[p6580.t6580] rmon.info 208.<ip>.128/255.255.255.255 gw <ip>.1 via 0x00000000 metric 0 (routemon.cpp:1864)
20121210163741.333475 ncsvc[p6580.t6580] rmon.info 216.<another ip>/255.255.255.255 gw <ip>.1 via 0x00000000 metric 1 (routemon.cpp:1864)
20121210163741.333494 ncsvc[p6580.t6580] rmon.info monitored routes:  (routemon.cpp:259)
20121210163741.333505 ncsvc[p6580.t6580] rmon.info <ip>.1/255.255.255.255 gw 0.0.0.0 via 0x00000000 metric 1 (routemon.cpp:1864)
20121210163741.333523 ncsvc[p6580.t6580] rmon.info 216.<another ip>/255.255.255.255 gw <ip>.1 via 0x00000000 metric 1 (routemon.cpp:1864)
20121210163741.333535 ncsvc[p6580.t6580] rmon.info 0.0.0.0/0.0.0.0 gw <vpn.ip>.60.100 via 0x00000000 metric 1 (routemon.cpp:1864)
20121210163741.333553 ncsvc[p6580.t6580] rmon.info Excluded Routes:  (routemon.cpp:261)
20121210163741.333565 ncsvc[p6580.t6580] rmon.info starting the route monitor... (routemon.cpp:316)
20121210163741.333599 ncsvc[p6580.t6580] dsxp.para register handle 0x0000000d, total 4 (dsio.cpp:342)
20121210163741.333621 ncsvc[p6580.t6580] session.info Tunnel setup done (session.cpp:489)
```

---

### Post by sowelie on 2012-12-13
> **dvo said:**
> I also had quite some trouble getting Juniper to run on a new 64-bit Linux installation (Ubuntu 11.04 "Natty").
Using a 32-bit chroot works, but is quite cumbersome.

After a lot of investigation and trial and error, I realized that the - *only* - problem is that [FONT="Courier New"]~/.juniper_networks/network_connect/libncui.so[/FONT] is a 32-bit library, thus it cannot be used by 64-bit Java.
**Shame on Juniper** that they do not provide a 64-bit version of the library! This would be the only thing they'd need to do to support 64-bit Linux systems out-of-the box.

First note that JNC will only work with the Java Runtime Environment from Sun/Oracle. In case your installation uses another JRE as default, you may use the command [FONT="Courier New"]sudo update-alternatives --config java[/FONT] to switch to java-6-sun. 

My workaround for a 64-bit installation is as follows.

Additionally install the 32-bit variant of Java: [FONT="Courier New"]aptitude install ia32-sun-java6-bin[/FONT] .
Assuming that Java is installed at [FONT="Courier New"]/usr/lib/jvm/java-6-sun/jre/bin/[/FONT] and at [FONT="Courier New"]/usr/lib/jvm/ia32-java-6-sun/jre/bin/[/FONT] ,
rename [FONT="Courier New"]/usr/lib/jvm/java-6-sun/jre/bin/java[/FONT] as [FONT="Courier New"]/usr/lib/jvm/java-6-sun/jre/bin/java.orig[/FONT] and 
save the following shell script as [FONT="Courier New"]/usr/lib/jvm/java-6-sun/jre/bin/java[/FONT] : 

```

#!/bin/bash
if [ $3x = "NCx" ]
then
    /usr/lib/jvm/ia32-java-6-sun/jre/bin/java "$@"
else
    /usr/lib/jvm/java-6-sun/jre/bin/java.orig "$@"
fi

```

This script should be readable and executable for all. It will call the 32-bit variant of Java when launching Network Connect (and otherwise call the default 64-bit variant).

Thank you so much! I have been messing with this for about an hour...

---

### Post by roquesao on 2013-01-15
I don't know what happened but from linux (ubuntu 12.04 64bits) I couldn't connect anynome , from 3 months ago It was working but now i get this error:

ui[p11089.t11112] DSInet.error failed to get HTTP response headers. Error 1 (dsinet.cpp:674)
20130114150513.147042 ncui[p11089.t11112] dsclient.error unable to send HTTP login request, error -8 (authenticate.cpp:184)
20130114150513.147069 ncui[p11089.t11112] dsclient.error state login failed, error 8 (dsclient.cpp:298)
20130114150513.147207 ncui[p11089.t11112] ncapp.error Failed to connect/authenticate with IVE. Error 8 (ncapp.cpp:179)


does it sound familiar to you?

Please help me , I really appreciate your help

---

### Post by narco_snow on 2013-01-30
I was still having problems with this after following this doc:
[http://kb.juniper.net/InfoCenter/index?page=content&id=KB25230](http://kb.juniper.net/InfoCenter/index?page=content&id=KB25230)

It was the same segmentation fault shenanigans that avira was experiencing. After much research, I found that manually supplying the ssl certificate and realm from the command line made everything happy. 

I even came across an excellent tutorial for using network connect in an entirely non-gui way at this link:

[http://makefile.com/.plan/2009/10/juniper-vpn-64-bit-linux-an-unsolved-mystery/](http://makefile.com/.plan/2009/10/juniper-vpn-64-bit-linux-an-unsolved-mystery/)
many props to scott for being a genius

I personally like the gui window and thus have created this bash script to make it cooperate:

```
#!/bin/bash
#
# 01-30-2013 RobertKempton
# this script will launch the juniper network connect java client with the given paramters
# if you don't know your realm, open your juniper site in your browser (don't log in)
# right click on the page, choose view source
# search for realm. The value field in the same html tag is your realm
#
# This script will also automatically download the ssl certificate for you
##

#make sure network connect is actually installed
if [ ! -f $HOME/.juniper_networks/network_connect/NC.jar ]; then
    echo "Juniper Network Connect is not installed for the current user"
    exit
fi

#check if 32bit java is installed
if [ ! -d /usr/lib/jvm/ia32-java-6-sun ]; then
    echo "32bit java does not appear to be installed"
    echo "check if /usr/lib/jvm/ia32-java-6-sun exists"
    exit
fi

#make sure we got all our options
if [ $# -ne 6 ]; then
    echo "Usage:"
    echo "launcNC.sh -h HOST -u USERNAME -r REALM"
    exit
fi
while getopts :h:u:r: opt ; do
    case $opt in
        h)
            nchost=$OPTARG;;
        u)
            ncuser=$OPTARG;;
        r)
            ncrealm=$OPTARG;;
        :)
            echo "$opt requires an argument"
            exit;;
        ?)
            echo "$opt is an invalid option"
            exit;; 
    esac
done

#get the ssl certificate
if [ ! -f $HOME/.juniper_networks/network_connect/ssl.crt ];then
    echo "downloading ssl certificate"
    echo | openssl s_client -connect $nchost:443 2>&1 | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p'| openssl x509 -outform der > $HOME/.juniper_networks/network_connect/ssl.crt
fi

#launch the application
/usr/lib/jvm/ia32-java-6-sun/bin/java -jar $HOME/.juniper_networks/network_connect/NC.jar -h "$nchost" -r "$ncrealm" -u "$ncuser" -f $HOME/.juniper_networks/network_connect/ssl.crt


#non gui http://makefile.com/.plan/2009/10/juniper-vpn-64-bit-linux-an-unsolved-mystery/
# if javascript:alert(document.cookie) does not work for you, 
# install the view cookies addon, then right click -> view page info
#$HOME/.juniper_networks/network_connect/ncui -h $nchost -c DSID=<dsid value> -f ssl.crt
```


if you have questions/issues/etc let me know. 

This script assumes the 32bit java is installed at /usr/lib/jvm/ia32-java-6-sun, which is the location it lands in when installed via apt. Feel free to use/modify/distribute this script.

---

### Post by ooboonter on 2013-02-04
I had my vpn set up and running perfectly using mad scientist's msjnc script until one day when I had to change my wifi router. I maybe wrong,  but thats when the problem started. At one point I had two routers, new and old connected on my network and somehow the DNS got messed up. At that point I was on VPN. I added a new router along with the old router and a few hours into it, I could not browse anymore. I started debugging and slowly i found that the VPN UI would simply say connected but there was no exchange of data. I killed the VPN session to find out that I still had no connection to the n/w. I could ping an IP address but could not ping the server name as google.com. Thats when I realized the /etc/resolv.conf somehow got messed up. Reading through forums I deleted /etc/resolv.conf and I was now able to connect back to the n/w and browse but the VPN is still broken. The ncsvc.logs dont show anything happening either, absolutely no prints except for a whole bunch of kill pid. Not sure when the kill happens because there is no time stamp next to it, but I am thinking it probably happens when I shut down the machine. And since then, when I open the msjnc script the GUI says its connected since then with 0 bytes of data going thru. And obviously ifconfig shows local ip address. 
Any thoughts on what might be happening?

---

### Post by fatdunky on 2013-02-13
Hi All,

I was receiving the error

20120721135124.534406 ncui[p4463.t4493] ncui.error Got signal 17 (ncui.cpp:278).

Basically the java connect applet was starting the crashing after 2 seconds.

But the i found juniper had wiped out my /etc/resolv.conf. So ran the following line to fix the issue.

sudo cp /etc/jnpr-nc-hosts.bak /run/resolvconf/resolv.conf

---

### Post by jdthood on 2013-02-14
It is known that Juniper Network Connect VPN client sometimes screws up /etc/resolv.conf.

After disconnecting from the VPN, run "sudo dpkg-reconfigure resolvconf" to restore the symbolic link /etc/resolv.conf -> ../run/resolvconf/resolv.conf and update the contents.

Ref: [http://askubuntu.com/questions/156154/how-to-prevent-juniper-network-connect-breaking-dns-resolutions](http://askubuntu.com/questions/156154/how-to-prevent-juniper-network-connect-breaking-dns-resolutions)

---

### Post by dft99 on 2013-03-04
Has anyone got this working on Ubuntu 12.04, network_connect 7.4 using two factor authentication(PIN+RSA key and ldap password).  I've managed to get the client to run using junipernc(tnx MS) and properly prompts me for my PIN+RSA key number.  However it continually fails with the following IVE error:

20130304220920.536039 ncui[p16215.t16240] dsclient.error state welcome state failed, error 2 (dsclient.cpp:284)
20130304220920.536496 ncui[p16215.t16240] ncapp.error Failed to connect/authenticate with IVE. Error 2 (ncapp.cpp:179)

---

### Post by vindolin on 2013-03-13
Today the juniper client stopped working on my 12.10 64bit system.
Until now, I've started a VPN connection with the ncsvc command like:
sudo /home/tsc/.juniper_networks/network_connect/ncsvc -h vpn.company.com -u tsc -p secret -r "Company User" -f /home/tsc/saved.crt -L 5
It worked perfectly until today.
Now the command runs without an error message but returns to the prompt after 2 seconds and VPN doesn't work.
On my other notebook I have the same setup and juniper VPN works  :confused:

---

### Post by santhoshsram on 2013-03-17
Many thanks. That's an ingenious shell script, no mucking with the update alternatives stuff (which did not work for me anyway). The script worked like a charm.

---

### Post by warci on 2013-05-03
Hello y'all

i've been trying to get the juniper client working on mint 14 and fedora for a long time now, with and without mad scientist's script (which rocks btw!), but still: no success....
The furthest i get is: i launch the script and it connects fine. Up until 1 minute or so i am able to connect and ping any server, but then the connection just stalls. I can still see bytes being sent out, but nothing comes back. Weird.
If i connect through chrome 32 bits (on my 64 bit machine), i get the same result, but the connection ends up lasting a bit longer, 5 minutes or so.

anyone has any ideas? If this persist i'll be forced to convert my work-laptop to windows again NOOOOOOOOOooooooooooo....

---

### Post by mdwy62 on 2013-05-05
I use Ubuntu 12.04 (32-bit). I have been able to use a Juniper client ever since I switched to Sun Java. Here are the directions I follow every time there is a Java update. So far (fingers crossed) I continue to be able to connect. 

[https://sites.google.com/site/easylinuxtipsproject/java/#TOC-How-to-for-Oracle-Sun-Java-JRE](https://sites.google.com/site/easylinuxtipsproject/java/#TOC-How-to-for-Oracle-Sun-Java-JRE)

Sounds though like you may have a deeper issue in that you can initially establish a connection, that then degrades. I needed Sun Java just to establish a connection at all.

---

### Post by bandyo on 2013-05-07
The latest version of openjdk and icedtea plugin work with Juniper VPN. Removing older and other versions of Java may also help.

See [Could anyone provide a step by step for getting juniper netconnect and citrix?]("http://askubuntu.com/questions/130473/could-anyone-provide-a-step-by-step-for-getting-juniper-netconnect-and-citrix-up")

This is one place where I found command line works better than the Ubuntu Software Center

First remove older versions of Java, both Oracle (Sun) and OpenJDK. For example, if you have OpenJDK 6 installed, type in a terminal:

```
sudo apt-get remove openjdk-6-jdk icedtea-6-plugin
```
Remove the Sun Java as well. If you have installed just the JRE, rather than JDK change the commands accordingly. Then install the OpenJDK-7 and corresponding plugin by:

```
sudo apt-get install openjdk-7-jdk icedtea-7-plugin
```
Open Firefox and test the version of Java is being used by going to this site [http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp)

If you see version 7 is running, you are ready to try Juniper VPN. If not you may have to remove the other version of Java. Hope this helps.

**For 64bit Ubuntu**

From 7.3 onwards, Juniper SA devices support 64-bit Ubuntu for Network Connect.

**First**, install the 64bit jre/jdk and icedtea

```
sudo apt-get install openjdk-7-jre icedtea-7-plugin
```

**Second**, install the 32bit jre

```
sudo apt-get install openjdk-7-jre:i386
```

Note, do not install the 32bit icedtea. Make sure the 64bit is the default java. As long as the 32bit jre exists, Juniper will find the files it needs and run.

Tested on Ubuntu 13.04 64bit.

See [Juniper Network Knowledge-base for details]("http://www.juniper.net/techpubs/en_US/sa7.3/topics/reference/general/secure-access-nc-64-bit-linux-support.html").

Also see [Juniper setup in Ask Ubuntu]("http://askubuntu.com/questions/136194/juniper-setup-on-12-04")

---

### Post by China Diapers on 2013-06-11
I have am having difficulties with this for some reason. I followed the instructions on Mad Scientists website, when it comes to running msjnc in the terminal I click connect and am prompted for my password, status briefly shows as connecting then disconnected.

I setup a profile, entering only three pieces of info:

Username: username I use to log into the web page where I downloaded the jar file from
Server/url: url for the web page where I downloaded the jar file from (or should this be the name of the machine I am trying to connect to? Tried that too)
Realm: I viewed the source for above webpage and search for realm, and copied and pasted the relevent text into this field, don't know if that's correct.

I also ticked securid.

Then I click OK, enter password when prompted and connect, but get a status of disconnected, 

I am using Lubuntu 13.04.

Anybody have any ideas?

---

### Post by cparlette on 2013-07-05
I was having problems connecting, the client would crash with setuid errors and core dumps.  Ultimately, my problem was that my home dir is encrypted, so once I moved ncsvc outside of my home dir and created a symlink, it worked fine.

---

### Post by single29 on 2013-09-01
Last week at VMworld in SF. I spoke with Juniper rep, I was told Juniper is not interested in supporting 64 bit linux because lack of demand. 
For those spent too many hours figuring out this, it might be the time to ask your company just to buy gear from Cisco or Huawei.
For sure there is a way to figure it out but it might not worth if your time is valuable.

---

### Post by TerryHowe on 2013-09-04
I don't use Java on my Ubuntu box at the moment so as a completely easy hack to get it working, I did this:

```

sudo mv /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java.save
sudo echo 'if echo "$*" | grep NC.jar >/dev/null
then
  /usr/java/java32/bin/java $*
else
  /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java.save $*
fi' >/usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java
sudo chmod 775 /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java

```

where /usr/java/java32 is where I installed my 32 bit Java library from Oracle.  Edit to update script.

---

### Post by jazzyflute on 2013-09-12
Hey All,

I recently got a new job and am working on getting my remote setup. My company uses this Juniper Network Connecter, and I have been running into some problems. Both my host and remote desktop are running Ubuntu 13.04. I have been working on getting the network connecter functioning by following the steps found here: mad-scientist.us/juniper.html    I then found my way to these forums and read through the last couple dozen posts regarding 13.04. Unfortunately, when I run the script msjnc, it does either 1 of the following things:

1. Nothing
2. Launches a window with no text, and prompty crashes. 

I have been unable to get any farther than this. I have tried uninstalling the network connected via my secureID login page, and rebooting and uninstalling/reinstalling all the java dependencies.

Thanks for your assistance!

---

### Post by karumiku on 2013-12-08
Hello all,

I've been trying to figure this out, and haven't found any better place to ask (the Juniper Networks forums seem to be more directed towards those who are administrating the VPN, whereas I'm just one of the clients).

For some reason, I can't even get to the Network Connect on Ubuntu, as Host Checker keeps complaining that I don't have an antivirus. I figured it was some weird requirement and grabbed one off of the Ubuntu Wiki page (Avast for Linux), but even installing that did nothing to change Host Checker. Is there something I missed from these posts, or is my VPN just flat-out blocking me?

Thanks in advance!

---

### Post by bandyo on 2013-12-10
Karumiku,

I don't know why Host Checker is complaining about no antivirus. I don't have any antivirus and it works fine for me. My guess is your juniper setup  is screwed up. You may want to delete the .juniper_networks folder in your Home folder. This is a hidden folder. You can reveal the hidden folders in Nautilus by pressing Ctrl+H. This folder will be recreated when you try to connect again.

If this does not work, please indicate how you are trying to connect. Are you using a 32bit or a 64bit version of Ubuntu? Are you using the OpenJVM Java 7 that is available in the Ubuntu Software Center? If you are in 64bit version of Ubuntu you will need both 64bit and 32bit versions of Java installed. See my earlier post on this.

Hope this helps

If this does

---

### Post by karumiku on 2013-12-10
> **bandyo said:**
> Karumiku,

I don't know why Host Checker is complaining about no antivirus. I don't have any antivirus and it works fine for me. My guess is your juniper setup  is screwed up. You may want to delete the .juniper_networks folder in your Home folder. This is a hidden folder. You can reveal the hidden folders in Nautilus by pressing Ctrl+H. This folder will be recreated when you try to connect again.

If this does not work, please indicate how you are trying to connect. Are you using a 32bit or a 64bit version of Ubuntu? Are you using the OpenJVM Java 7 that is available in the Ubuntu Software Center? If you are in 64bit version of Ubuntu you will need both 64bit and 32bit versions of Java installed. See my earlier post on this.

Hope this helps

If this does

I completely deleted the ~/.juniper_networks folder and followed the steps at [http://ubuntuforums.org/showthread.php?t=232607&page=53&p=12637969#post12637969](http://ubuntuforums.org/showthread.php?t=232607&page=53&p=12637969#post12637969) (I have a 64-bit Ubuntu), and the issue still arises. If it helps any, I get the following text:
> Your computer does not meet the following security requirements. Please follow the instructions below to fix these problems. When you are done click **Try Again**.
____________
**1. Antivirus**
Instructions: Does it get this far?


Also, java -version reports OpenJDK 1.7.0.

---

### Post by Jakob Lundberg on 2013-12-11
The Host Checker is setup differently for Windows, Mac and Linux clients. And  as far as I know, only the Host Checker for Windows as support for antivirus checks. This, I suspect, means that the Host Checker configuration on the gateway does not have the Linux profile enabled and will therefore attempt to appy the Windows profile instead.

If Host Checker is enabled on the gateway, the Linux profile must also be enabled for it to work.

---

### Post by karumiku on 2013-12-11
So I'm assuming there's no workaround? I suppose I'll have to see if my IT department will enable the profile for me otherwise. At least I have a direction to move towards, though.

Thanks for your help!

---

### Post by vsrikarunyan on 2014-01-04
Thanks a lot, dvo. And also to [Scott's]("http://makefile.com/.plan/2009/10/juniper-vpn-64-bit-linux-an-unsolved-mystery/") valueable article, else I would have never been able to get this done. 

In my case, it was on RHEL6 that I was facing an issue with. After getting the java thingy in [place]("http://www.if-not-true-then-false.com/2010/install-sun-oracle-java-jdk-jre-7-on-fedora-centos-red-hat-rhel/"); I had to install the following packages before using your suggestion

sudo yum install xterm.x86_64
sudo yum install glibc-devel.i686
sudo yum install libXtst.i686

I faced the following issues while getting the Network Connect started

Issue #1
Here is the standard output of the command:

Service needs to be installed for the first time
calling /home/vsrikarunyan/.juniper_networks/network_connect/installNC.sh
Here is the standard error of the command (if any):

/home/vsrikarunyan/.juniper_networks/network_connect/xlaunchNC.sh: line 56: xterm: command not found  

Issue #2
java.lang.UnsatisfiedLinkError: 
    /usr/local/java/jre1.7.0_25/lib/i386/xawt/libmawt.so: libXtst.so.6: cannot open shared object file: No such file or directory

---

### Post by l-f-kempe on 2014-01-09
Is there anyway to get this to work with 2-way-auth?

When i login to my companies vpn via their website i first enter my Username, then after a while i get a sms with password i enter that in to the site and pair with my personal-pin  and then I am logged in and can start the client.

When i try to use the script i get prompted for a password directly when i try to login, so i guess no request is sent to the server so I dont get any password sms, but if i enter a "fake" password i get the password sms, but now i cant enter a password becouse i already used a fake one. So it seams to be kind of working but I would need the script to send a login request before password prompt and after that send the real login request.

Anyone got this working with a simular setup?

---

### Post by parruc on 2014-08-20
> **cparlette said:**
> I was having problems connecting, the client would crash with setuid errors and core dumps.  Ultimately, my problem was that my home dir is encrypted, so once I moved ncsvc outside of my home dir and created a symlink, it worked fine.

Man you saved my life!!!! Weird solution but definitly solved my issue!!!

---

### Post by dezzie on 2014-10-21
Upon establishing a VPN tunnel using Network Connect, how might I be able to check the tunnel's status? I need to feed a return value back into a bash script that first checks if the VPN is connected, and if not, connects it.
Any leads, anyone? Help is appreciated!

---

### Post by dezzie on 2014-10-21
> **dezzie said:**
> Upon establishing a VPN tunnel using Network Connect, how might I be able to check the tunnel's status? I need to feed a return value back into a bash script that first checks if the VPN is connected, and if not, connects it.
Any leads, anyone? Help is appreciated!


[COLOR=#000000][FONT=Arial]Using grep, you can do the following:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/sbin/ifconfig tun0|grep -ci 'UP'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]to check if your tunnel is running or not.[/FONT][/COLOR]

---

### Post by bpodgursky on 2014-11-19
Hi all,

I've been fighting the juniper VPN client on Linux many, many years.  Recently we shifted to two factor authentication, and that completely broke all the scripts / etc I've ever seen on this thread.  So I took another look at getting the normal web-ui-launched client working, and finally got it working (two factor authentication and all) with help from this KB article:

[http://kb.juniper.net/InfoCenter/index?page=content&id=KB25230](http://kb.juniper.net/InfoCenter/index?page=content&id=KB25230)

the key for me (YMMV) was installing 32 bit java (obv) but also

- adding 32 bit java to alternatives 
- sudo ln -s /usr/bin/update-alternatives /usr/sbin/

---

### Post by zikona2 on 2015-02-27
Did anyone had any luck recently with **Juniper networks Network Connect 8.0 **client on **Ubuntu 14.04.1 LTS** and using a certificate? I am not sure if people gave up on this issue or is perhaps Juniper providing some assistance on how to authenticate with their VPN from linux client. I have tried original isntructions from madscientist page but no luck yet.

---

### Post by aperomsik on 2015-02-27
> **zikona2 said:**
> Did anyone had any luck recently with **Juniper networks Network Connect 8.0 **client on **Ubuntu 14.04.1 LTS** and using a certificate? I am not sure if people gave up on this issue or is perhaps Juniper providing some assistance on how to authenticate with their VPN from linux client. I have tried original isntructions from madscientist page but no luck yet.

Yes, but not with msjnc, at least not for two-factor. First I tried the link from the post before yours and got it working with FireFox. Then I found a command line tool called [jvpn]("https://github.com/samm-git/jvpn") which had an open pull request adding support for two-factor. So I grabbed that and also hacked in some basic [indicator]("https://github.com/aperomsik/jvpn/tree/indicator-wip") support.

---

### Post by zikona2 on 2015-02-28
I am trying jvpn and looks like a its a pretty nice script to get this going. Unfortunately I am getting stuck at "Unable to get DSID, exiting". My employer is using a cert which I downloaded and installed through firefox. What is a two-factor that you are referring to?

---

### Post by el_sordo on 2015-11-16
Greetings msjnc users. So it looks like Network Manager in Ubuntu 15.10 breaks VPN connections. I can connect using msjnc, obtain an IP, but then immediately disconnects. I'm using the juniper network connect client 7.2R4. If disable network-manager and use /etc/network/intefaces (via dhcp), then VPN/msjnc works.

I'm not aware of any bug report submitted for network-manager in relation to this, so if anyone knows of such a report, please post it. The version of network-manager on my Ubuntu 15.10 is 1.0.4-0ubuntu5.1

---

### Post by aperomsik on 2015-11-16
> **el_sordo said:**
> Greetings msjnc users. So it looks like Network Manager in Ubuntu 15.10 breaks VPN connections. I can connect using msjnc, obtain an IP, but then immediately disconnects. I'm using the juniper network connect client 7.2R4. If disable network-manager and use /etc/network/intefaces (via dhcp), then VPN/msjnc works.

I'm not aware of any bug report submitted for network-manager in relation to this, so if anyone knows of such a report, please post it. The version of network-manager on my Ubuntu 15.10 is 1.0.4-0ubuntu5.1

Just as an additional data point, I have not had issues with ncsvc in 15.10. I am using ncsvc version 8.0-6-Build32195. I did have problems similar to what you describe when 15.04 first came out, which were eventually resolved by Ubuntu kernel updates... but 15.10 has worked fine for me.

FWIW as mentioned above, I am not using msjnc anymore; instead I am using jvpn because it seems to play nicer with my employer's 2-factor setup.  But it seems unlikely that the difference between jvpn and msjnc would affect the behavior you describe.

---

### Post by rakesh_roshan on 2016-02-12
> **m0rev said:**
> Good for you ;) Reboot didn't help me :(

```
ncapp.panic Failed to read password from prompt (nccommon.cpp:614)
```

It used to work couple days ago, so I wonder if some package I've installed recently broke that. Or IT changed something...

Does anybody has similar experience?

mv ~/.mozilla/firefox/profiles.ini ~/.mozilla/firefox/profiles.old
mv ~/.mozilla/firefox/<randomstring>.default/ ~/.mozilla/firefox/old_profile

It solved the problem

---

### Post by dwmw2 on 2016-12-15
The OpenConnect VPN client now has support for Juniper, fully integrated with NetworkManager: [https://www.infradead.org/openconnect/juniper.html](https://www.infradead.org/openconnect/juniper.html)

---

### Post by nabz0r on 2016-12-15
I have no idea if someone else has posted this before or not, but anyway I will post it and it works perfectly fine with 2-way auth. 

[https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB25230](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB25230)

If you have encrypted your HDD you need to run the web browser as root when you want to login to your vpn.

In terminal:
gksu firefox

In firefox:
[https://portal.company.com](https://portal.company.com)
username
password

then your rsa/sms code

first time it will ask you for your root password, after this guide you're good to go. We are almost 10 people that uses Linux full time at work and this guide from Pulse Secure works great for us.

---

### Post by pettenuz on 2017-01-10
guys I am not sure this is the right place for what I am asking but I'd like to ask your help to solve an issue I am experiencing with my VPN connection. I use Ubuntu 16.04 and I can connect successfully using the script. However after exactly 20 minutes the VPN drops.
Here is the log I get  :

20170109130548.853221 ncsvc[p3289.t3289] ipsec.warn ESP tunnel expired in:0x3149BF24, out:0xCD33F361 (engine.cpp:377)
20170109130548.853308 ncsvc[p3289.t3289] ipsec.warn Cleaning up sa 0x3149BF24 (esp.cpp:66)
20170109130548.853328 ncsvc[p3289.t3289] ipsec.info Switching to NCP mode (tunnel.cpp:661)
20170109130548.853347 ncsvc[p3289.t3289] ipsec.info send kmp message 303 size 13 (tunnel.cpp:235)

(obtained with Juniper)

No matter which client I use to connect, after 20 minutes I get kicked out. Is there a way to modify the settings to try to void this behavior? Any idea of what could be going on?

---

