---
title: "OVH Dedi Server language / locale problems - they're still using 8.04 beta!"
date: 2008-07-02
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-07-02
Hello every1, 

Well I recently got myself a dedicated 100mbit [OVH]("http://www.ovh.co.uk")server. The package is great by the way but there's 1 problem.

The datacentre is in France and I have an option in the control panel to install in english ( i choose Ubuntu of course ).
You have the option of 8.04 LTS or 6.06 LTS. I chose Hardy, it does say beta next to it but I assumed that meant the control panel was still in beta for that distro.

I've done a total of 3 reinstalls and every time I get some language / local errors. It doesn't seem to affect me in anyway ( althougth it may have caused problems that I blamed on something else ) but it obviously needs sorting.
I called up the techies and they told me that Hardy was still in beta and I should use the previous LTS release. I informed him that Hardy had been out of beta for a while now and the next release is now taking form.
I also told him that these errors were probably not due to a beta hardy and I'm sure they can be fixed with a bit of reconfiguring. Guess what he told me to do.... got to ubuntuforums.org ](*,). I know that it's a dedi server and I don't pay for support but this is something that should've been working in the first place!
I was gonna come here anyway lol. Here's the errors I recieve:
```


root@ks361402:~# apt-get install mc
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libglib2.0-0 libpcre3
Suggested packages:
  arj unzip
Recommended packages:
  libglib2.0-data
The following NEW packages will be installed:
  libglib2.0-0 libpcre3 mc
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 3067kB of archives.
After this operation, 8237kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 ftp://mir1.ovh.net hardy/main libpcre3 7.4-1ubuntu2 [206kB]
Get:2 ftp://mir1.ovh.net hardy-updates/main libglib2.0-0 2.16.3-1ubuntu3 [752kB]
Get:3 ftp://mir1.ovh.net hardy/universe mc 1:4.6.1-8ubuntu1 [2109kB]
Fetched 3067kB in 0s (4737kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously deselected package libpcre3.
(Reading database ... 22361 files and directories currently installed.)
Unpacking libpcre3 (from .../libpcre3_7.4-1ubuntu2_i386.deb) ...
Selecting previously deselected package libglib2.0-0.
Unpacking libglib2.0-0 (from .../libglib2.0-0_2.16.3-1ubuntu3_i386.deb) ...
Selecting previously deselected package mc.
Unpacking mc (from .../mc_1%3a4.6.1-8ubuntu1_i386.deb) ...
Setting up libpcre3 (7.4-1ubuntu2) ...

Setting up libglib2.0-0 (2.16.3-1ubuntu3) ...

Setting up mc (1:4.6.1-8ubuntu1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
root@ks361702:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:65:23:65
          inet addr:91.121.169.150  Bcast:91.121.169.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:39878521 (38.0 MB)  TX bytes:4163591 (3.9 MB)
          Interrupt:16 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:18151 (17.7 KB)  TX bytes:18151 (17.7 KB)

root@ks361702:~# Get:1 ftp://mir1.ovh.net hardy/main libpcre3 7.4-1ubuntu2 [206kB]
Get:2 ftp://mir1.ovh.net hardy-updates/main libglib2.0-0 2.16.3-1ubuntu3 [752kB]
Get:3 ftp://mir1.ovh.net hardy/universe mc 1:4.6.1-8ubuntu1 [2109kB]
Fetched 3067kB in 0s (4737kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously deselected package libpcre3.
(Reading database ... 22361 files and directories currently installed.)
Unpacking libpcre3 (from .../libpcre3_7.4-1ubuntu2_i386.deb) ...
Selecting previously deselected package libglib2.0-0.
Unpacking libglib2.0-0 (from .../libglib2.0-0_2.16.3-1ubuntu3_i386.deb) ...
Selecting previously deselected package mc.
Unpacking mc (from .../mc_1%3a4.6.1-8ubuntu1_i386.deb) ...
-bash: Get:1: command not found
root@ks361702:~# Get:2 ftp://mir1.ovh.net hardy-updates/main libglib2.0-0 2.16.3-1ubuntu3 [752kB]
Setting up libpcre3 (7.4-1ubuntu2) ...

Setting up libglib2.0-0 (2.16.3-1ubuntu3) ...

Setting up mc (1:4.6.1-8ubuntu1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

I've copied the whole lot so you can see the context of when this appears. as you can see I was installing midnight commander ( this is a fresh install ).

I'm sure just reinstalling language packs / locale settings will fix this but don't know how.
The tech said he will pass on the info that Hardy is out of beta but we probably wont see updates for a while. Surely running dist-upgrade has taken my Hardy out of the beta version? Or do I need to update the kernel to have a true upgrade release?

Thanks every1,
Gareth

p.s. by the way the tech said that Ubuntu was one of the most popular distro on their dedi servers so Kudos to the devs

---

### Post by hyper_ch on 2008-07-02
[http://ubuntuforums.org/showthread.php?t=265715](http://ubuntuforums.org/showthread.php?t=265715)

and no, they are not using beta anymore if you have done an upgrade ;)

---

### Post by windependence on 2008-07-02
Gareth, those are just warnings. Nothing to be too concerned about.

-Tim

---

### Post by garethsimpsonuk on 2008-07-03
thanx guys. yea i was just concerend about it that's all. I followed ur link hyper and run the command in the post and i recieve this:
> 
root@ks381702:~# dpkg-reconfigure localeconf
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Package `localeconf' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: localeconf is not installed


even though it's not causing problems it looks like 

 >    LANGUAGE = (unset),
        LC_ALL = (unset),

is all that needs to be fixed. I'll have a look around to find out how to set language and LC_ALL whatever that is.

By the way you 2 were both right about not using a GUI! I remember just 2 months ago I wouldn't listen and insisted on having a GUI. Now I have a home server and a dedi server both without a GUI and I'm getting on fine! I conquered samba, it's just sFTP that's giving me trouble now.
Wouldn't have got past the installer if it weren't for these forums so thanks guys!

Cheers 4 the replies, and that avaters funny windependence!

---

### Post by hyper_ch on 2008-07-03
if reconfigre lokale doesn't work... hmmme... you'll have to google then ;)

for sftp/scp I use mysecureshell to limit my "guests" very tightly ;)

---

### Post by garethsimpsonuk on 2008-07-03
yea i've just installed winscp just to download files fromthe server.

is it much slower than ftp? I guess that way all traffic is encryted, meaning it's slower ( i'll be downloading like 40GB files sometimes ). I only really need the authentication bit encrypted ( i.e. when username / password is sent )  I guess I'd have to setup FTP for that. I'm doing it right now.

I need the default FTP directory to be /home/torrents/downloads. I could therefore download my files each night. That's where it gets me because ftp sets it's own directory. I'm in hte process of setting it all up right now, just running through a few how to's first.

Yeah I think I'll leave the language thing for now. I'm sure english users have had this problem with OVH so I'll check out there forum about that.

Thanks for the reply

---

### Post by hyper_ch on 2008-07-03
it will only be slower if the pipe on the server and your pipe are bigger than the cpu(s) can uncrypt on the fly ;)

---

### Post by garethsimpsonuk on 2008-07-03
ok thanks, I'm running a 3.0GHZ P4 512MB ram MS XP. Is this quick enough to unencrypt faster than the connection? My home connection is 4.5mb/s down ( not sure about up ) and my server is 100mb/s both ways. 

I'm having an absoloute nightmare with FTP again, it's got to the point where I'm gonna have to reinstall again because I've messed up all my users etc. So I'm gonna do a reinstall again. At least I haven't setup everything else up yet.

I don't know how big of a speed benefit unencrypted traffic has but if it's only a little, on big files it's still gonna make a difference.

Do canonical provide one off tele support? i.e. a premium rate number? or maybe even someone else that provides phone support. if not that would be something good to get into for experirenced support techs.

---

### Post by hyper_ch on 2008-07-03
when I had my server with OHV I chose Debian and not Ubuntu...

I think there isn't much slowdown when you encrypt the download to your place... so I'd rather use SSH/SSHFS/SCP/SFTP ;) very simple to setup ;)

---

### Post by garethsimpsonuk on 2008-07-03
i've just given winscp a go and you can only download one file at a time. would I have to open a second instance of the program to download more? if it's only a frontend for an SSH terminal then it shouldn't take up too much resources? That's another thing with FTP some clients make multipal connections to speed it up. I suppose I can always give SCP a go and if it's too slow then I'll have another look at FTP.

This is samba all over again..

---

### Post by hyper_ch on 2008-07-03
well, downloading more than one file concurrently does not make any sense... there is a max output the server has and there's a max download rate you have... yuo can't go over it...

---

### Post by garethsimpsonuk on 2008-07-03
really? i didn't think I'd max out my connection. if i do max out my connection then there's no reason not to use SHH / SCP. That was the only reason - speed. I didn't think I'd utilise my bandwidth.

I'm doing a reinstall now for the last time and I will just use WinSCP. I've wasted over 3 paid server days on this and it's not worth it, if even FTP did give me a little bit of an increase.

Thanks for your advice once again m8, you've been really helpful :-)

---

### Post by hyper_ch on 2008-07-03
well, you can test yourself how much download speed you get over winscp and lets say multiple http downloads

---

### Post by cariboo on 2008-07-03
To reconfigure your locale have a look here:

[http://people.debian.org/~schultmc/locales.html](http://people.debian.org/~schultmc/locales.html)

Jim

---

### Post by scobiwan on 2011-09-13
Well for me (running 9.10 on a vps) the following worked

#locale-gen en_GB.UTF-8
then
#dpkg-reconfigure locales

hope it's of help!

---

### Post by nothingspecial on 2011-09-13
Necromancy

---

